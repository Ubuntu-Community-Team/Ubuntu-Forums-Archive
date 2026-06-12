---
title: "Anyone read this?"
date: 2007-06-19
forum: The Cafe
---

### Post by LookTJ on 2007-06-19
[http://www.pcworld.com/article/id,133042-c,onlinesecurity/article.html](http://www.pcworld.com/article/id,133042-c,onlinesecurity/article.html)

Does it affect Ubuntu/Linux?

---

### Post by Johnsie on 2007-06-19
You will not get infected if you are on Linux. However, if you have a webserver that allows iframes then someone may be abe to use yur webserver to spread this, especially iif you do free web hosting.

---

### Post by Johnsie on 2007-06-19
You will not get infected if you are on Linux. However, if you have a web server that allows iframes then someone may be abe to use your web server to spread this, especially if you offer free web hosting

---

### Post by LookTJ on 2007-06-19
I run apache2 on my pc...problem for me?

---

### Post by Disstress on 2007-06-19
Possibly, the only way to tell is what you have on your website. Most likely this is a XSS hole exploit, or just a standard injection. 

Secure your code, always double, triple check all points of entry. Every single area where someone can dynamically change your website (IE forums, shoutboxes,etc) is a potential entry point for an exploit, or as the media likes to call it a "hack".

Backends for popular portals have well known exploits, some get fixed quickly, some never get fixed.

---

