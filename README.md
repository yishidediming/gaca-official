<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8" />
  <title>GACA - 全球异常收容协会</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <style>
    body{background:#111;color:#0af;font-family:monospace;margin:0;padding:2em}
    h1{font-size:2.5em;text-align:center}
    .warn{background:#000;border-left:3px solid #f00;padding:1em;margin:1em 0}
    .card{margin:1em 0;padding:1em;border:1px solid #0af;border-radius:4px}
    img{max-width:100%;height:auto;border-radius:4px}
  </style>
</head>
<body>
  <h1>GACA</h1>
  <div class="warn">⚠ Ⅴ级权限以下人员请立即退出</div>
  <h2>最新档案</h2>
  <div id="list"></div>
  <hr>
  <a href="submit.html" style="color:#0af;font-size:1.2em">发布异常档案 →</a>

  <script>
    // 动态读取 posts.json 并渲染
    fetch('posts.json').then(r => r.json()).then(data => {
      const list = document.getElementById('list');
      data.forEach(p => {
        const div = document.createElement('div');
        div.className = 'card';
        div.innerHTML = `
          <strong>${p.title}</strong><br>
          ${p.desc}<br>
          ${p.img ? `<img src="https://raw.githubusercontent.com/yourname/gaca-images/main/${p.img}" alt="异常图片">` : ''}
        `;
        list.appendChild(div);
      });
    });
  </script>
</body>
</html>
