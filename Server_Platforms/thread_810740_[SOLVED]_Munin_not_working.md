---
title: "[SOLVED] Munin not working"
date: 2008-05-28
forum: Server Platforms
---

### Post by The Devil Is A Squirrel on 2008-05-28
Hi guys,

I try to run Munin on Ubuntu 8.04 LTS Server Edition. I was able to install it (following this [guide]("http://tombuntu.com/index.php/2007/07/16/monitor-your-linux-server-with-munin/")), but when I try to access Munin with 'lynx [http://localhost/munin](http://localhost/munin)' I get only the directory listing of the folder (definitions.html, logo.png, style.css).

On my Debian 4 Server this worked without a hitch...what did I do wrong?

---

### Post by NateMan on 2008-05-28
Well I tried the install from that guide and I was able to get it to work the first time. You did change the hostname and ip address to match your server and then restart correct?

---

### Post by The Devil Is A Squirrel on 2008-05-28
> **NateMan said:**
> Well I tried the install from that guide and I was able to get it to work the first time. You did change the hostname and ip address to match your server and then restart correct?

No because I want access it with localhost.

---

### Post by NateMan on 2008-05-28
where did you place your munin directory you created?

---

### Post by The Devil Is A Squirrel on 2008-05-28
Actually it creates the folder itself on '/var/www/munin/' I just chown the folder with munin:munin.

---

### Post by The Devil Is A Squirrel on 2008-05-29
Does anyone have an idea what's wrong? I tried a lot without any luck. I even installed the image again...

---

### Post by The Devil Is A Squirrel on 2008-05-29
Ok, I got it.

I had to create a folder within '/var/www/munin' named 'localdomain' (and chown it) and change the htmldir	from the munin.conf (/etc/munin) to '/var/www/munin/localdomain'.

Now it works.

---

