---
title: "Webmin outside access??"
date: 2006-06-05
forum: Server Platforms
---

### Post by heldmar on 2006-06-05
Greetings,

I've installed the new Ubuntu 6.06 and then I installed webmin, it was great and with no problems BUT, now I'm trying to access webmin from my workplace (my server is at home) and it says it doesn't found it. I was wondering how could I open external connections of webmin into my server. My webserver is open, even my ssh server is up and running (in fact I can connect remotely via SSH). Please help me. Thanks!

---

### Post by bluenova on 2006-06-05
Do you have port 10000 open?

---

### Post by Tortanick on 2006-06-05
I'd be suprised if webmin defaults arn't local host only, can't you tunnel your browser though SSH and connect to webmin like that?

---

### Post by heldmar on 2006-06-06
[QUOTE=bluenova]Do you have port 10000 open?[/QUOTE]
Yes, my 10000 port is open in my gateway.

---

### Post by heldmar on 2006-06-06
I just need to know how to access it via browser from outside, I can access my server via SSH but I would like to access it via web interface

---

### Post by bluenova on 2006-06-06
Last time I used webmin was on Fedora, and apart from opening ports everything worked. Can you access a normal webpage like an index.htm file in /var/www or wherever it goes in ubuntu?

---

### Post by DirtDart on 2006-06-29
Check your hosts.deny file to make sure it's not being blocked, as its a non-local IP address (your work).

There is also the chance that port 10000 is be blocked on the other end (your work).

---

### Post by nameiwantistaken on 2006-06-30
There seems to be an issue with webmin on Ubuntu where it does not restart after a reboot even if you set it up to do so.  This could be your problem.  Of couse, I can't find any help anywhere online so hopefully your research is more fruitful.

---

### Post by Randomskk on 2006-07-01
[QUOTE=heldmar]I just need to know how to access it via browser from outside, I can access my server via SSH but I would like to access it via web interface[/QUOTE]
No, what they mean is that you can use this SSH connection to tunnel port 10000 from your pc to your server, which should make it work right out.
Add something like this to the end of your SSH command (or if you use puTTY, you can tell that to forward ports in it's config options):
-L 10000:<SERVER IP>:10000
Then connect to [http://localhost:10000](http://localhost:10000) and it should load your webmin.

---

