---
title: "Recover passwords through proxy"
date: 2007-06-27
forum: Server Platforms
---

### Post by grendelkhan on 2007-06-27
I've got my son set up on Ubuntu and we're using the firehol/tinyproxy/dansguardian combo to do parental controls on his internet.  My son's had a problem with subscribing to porn emails in the past and when I had him on windows, I used a keylogger to recover his passwords.  I have the problem on Unbuntu that there's no keylogger for usb keyboards.  Making sure there's nothing going on in his myspace and email accounts are pretty crucial for us.

Is there any way I can set up tinyproxy to records passwords sent to websites?  I've been googling all morning and I can't find anything.

---

### Post by yota on 2007-06-27
Hi, you can use
[http://www.wireshark.org/](http://www.wireshark.org/)
or
[http://ettercap.sourceforge.net/](http://ettercap.sourceforge.net/)
(both are in repositories) to sniff what passes through your network connection.

By the way, doesn't lkl work with usb keyboards?

---

### Post by timcredible on 2007-06-27
why not just ask him what his password is?

---

