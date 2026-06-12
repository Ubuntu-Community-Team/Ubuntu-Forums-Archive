---
title: "kubuntu-desktop installs postfix"
date: 2008-06-10
forum: Security
---

### Post by eniel on 2008-06-10
hello,

I've installed the kubuntu-desktop on ubuntu hardy. This automatically installed postfix. I always thought that running a mailserver was a potential security risk and that if you install (K)ubuntu no such services would be running by default. Further more I do not understand what's the use of a mailserver in connection with a desktop. I only need a mailclient (seamonkey in my case) to read my mail.

---

### Post by acrostic on 2008-06-10
Eniel,

It is not a problem as postfix should be listening on loopback address, you can verify it by running "sudo netstat -pant|grep -i master". Check for entry like this.

 tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     2448/master

Listening on loopback address means that external machines can't connect to this service and is for internal use only.

Hope this helps

---

### Post by eniel on 2008-06-10
Thanks for the answer. It works as you said, so I know the configuration is safe.
Still I'm a little astonished that a mailserver gets installed by default with kubuntu desktop since I would expect a normal desktop user to only need a mail client

---

