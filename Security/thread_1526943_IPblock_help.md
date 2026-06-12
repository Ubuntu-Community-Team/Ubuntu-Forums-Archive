---
title: "IPblock help"
date: 2010-07-08
forum: Security
---

### Post by swaydoll on 2010-07-08
I installed IPlist earlier today on my main/admin account (which I only use for installing programs. I don't use this account daily.) and everything was fine. When I logged into my every day account and tried to load the program, it prompted me for my password. When I entered it, I got this message:

> Failed to run /usr/sbin/ipblock start_gui as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.Does this mean I am not able to use this program on this account, or is there a way around it? I'm new to Ubuntu so forgive me if I'm asking the obvious. I looked around and couldn't find an answer. I really don't want to use my admin account for daily activities, but I also really want to be able to use IPlist.

Any help is very appreciated!

---

### Post by mikewhatever on 2010-07-08
Well, you can't start or stop the program from that account, nor can you configure it. That said, you might be able to autorun it with the desired configurations by editing /etc/ipblock.conf.
[http://iplist.sourceforge.net/documentation.html](http://iplist.sourceforge.net/documentation.html)

---

### Post by swaydoll on 2010-07-08
Thank you very much!

---

