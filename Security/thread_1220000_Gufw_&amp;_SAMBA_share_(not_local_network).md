---
title: "Gufw &amp; SAMBA share (not local network)"
date: 2009-07-22
forum: Security
---

### Post by frogotronic on 2009-07-22
Hi,

  Using Ibex and Gufw.  Local network works fine with windows shares.  What I'd like to do is to be able to connect to my works netdisk space.  Before using ufw/Gufw this wasn't a problem on Hardy.  Since upgrading to Ibex and using Gufw, I have been able to achieve this from home.  From work, its no problem.

What command do I need to pass to the UFW to permit this?

- CH

---

### Post by bodhi.zazen on 2009-07-22
You have to allow the samba ports. I would caution you though, over the internet ssh is probably better. Or vsftp or just about anything but samba =)

[http://troy.jdmz.net/samba/fw/](http://troy.jdmz.net/samba/fw/)

You can mount a share with ssh (sshfs on Linux and winscp on windows).

vsftp would be #2 , use a chroot (home) jail if you can.

---

