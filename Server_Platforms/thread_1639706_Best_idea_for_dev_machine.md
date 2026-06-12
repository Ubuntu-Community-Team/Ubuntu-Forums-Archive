---
title: "Best idea for dev machine"
date: 2010-12-07
forum: Server Platforms
---

### Post by sptrsn on 2010-12-07
I have one machine set up as my web server. Really the only thing I run is a sugarcrm instance for me personally with my real estate stuff. It's ubuntu server 8.04 lts. I followed a great recipe for building it. mysql/php/apache2. It was a perfect install. No errors, no problems. I LOVE this machine. It just runs. 

My Ubuntu desktop just died, so I'm building another. One of the requirements is to have a web server running for the little bit of web development that I do. My old machine had Xampp on it, which was fine. 

So, my question is this. On my new machine, should I build another web server on Ubuntu server, then add the gui, (never done that) or should I just install desktop, at which point, should I use Xampp or should I install the full mysql/php/apache2 apps? What would you do?

---

### Post by James78 on 2010-12-07
The server edition is basically the desktop edition without a GUI. So if you're using it as a desktop and are gonna add a GUI after, I say just install the desktop edition. As for the apps, I suggest just doing a full install; it may be a little harder and take slightly more time, but it really is more worthit. To ease your process, you could do "sudo tasksel" and select LAMP (Linux-Apache-MySQL-PHP) to install.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by sptrsn on 2010-12-07
Good advice. Thanks.
For some reason I was under the impression that there was some difference (other than the gui) between desktop and server.
Thanks again.

---

### Post by arrrghhh on 2010-12-07
> **sptrsn said:**
> Good advice. Thanks.
For some reason I was under the impression that there was some difference (other than the gui) between desktop and server.
Thanks again.

There's differences in the kernel and how *certain* programs are configured... but for the most part there isn't a huge difference... Server edition is obviously pretty stripped compared to the desktop edition, it's meant to run with the lowest overhead possible.

---

### Post by James78 on 2010-12-07
> **sptrsn said:**
> Good advice. Thanks.
For some reason I was under the impression that there was some difference (other than the gui) between desktop and server.
Thanks again.
Well, there is a slight difference, as arrrghhh said, kernel differences and how certain programs are confrigured, but for the most part it's very similar and close, except for being stripped to run with the lowest overhead. :) Makes the machines much faster.

---

