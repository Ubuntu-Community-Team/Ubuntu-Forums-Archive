---
title: "Java doesn't work on Chrome or Chromium!"
date: 2014-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by Murong_Yao on 2014-08-31
OK, I still stick to Firefox as my main browser, but can Google Chrome or Chromium do better than not having java?

---

### Post by ThatBum on 2014-08-31
Chrome for Linux has had [NPAPI support dropped]("https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/xEbgvWE7wMk"), the API that the Java plugin uses. They think "NPAPI&#8217;s 90s-era architecture has become a leading cause of hangs, crashes, security incidents, and code complexity." Eventually this will carry over to the Windows version too. I Suppose it's slowly being supplanted by HTML5 and the like.

So. If you want to use Java in-browser you need another browser. Sorry. Not up to us.

---

### Post by diepnguyen on 2014-09-01
If you use Firefox as default browse, you should disable Java by default. It has many 0-day exploit on the wild.

---

### Post by Murong_Yao on 2014-09-01
[QUOTE=diepnguyen][COLOR=#000000]If you use Firefox as default browse, you should disable Java by default. It has many 0-day exploit on the wild.[/COLOR][/QUOTE]

Or you can use Chrome/Chromium for websites that doesn't use java scripts.

---

