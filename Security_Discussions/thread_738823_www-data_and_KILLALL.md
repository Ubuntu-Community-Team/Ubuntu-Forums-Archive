---
title: "www-data and KILLALL?"
date: 2008-03-29
forum: Security Discussions
---

### Post by astrosoft on 2008-03-29
Hi guys!
I need to ru the following script via PHP:

        killall -v pppd
so that i could remotely disconnect my server from the internet.

However, when I try to run the script, nothing happens.

Moreover, when i try to execute
sudo -u www-data killall -v pppd ,
i get a response "permission denied".

I have also tried editing sudo visudo:
www-data (ALL) ALL, but that didn't help.

The only thing that works from command line is 
sudo -u root killall pppd

Can anyone help me?!!
Thanks.

---

### Post by Dr Small on 2008-03-29
In visudo, try:
```
www-data *hostname* = NOPASSWD: /usr/bin/killall
```

---

