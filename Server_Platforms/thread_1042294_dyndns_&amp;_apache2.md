---
title: "dyndns &amp; apache2"
date: 2009-01-17
forum: Server Platforms
---

### Post by Nitewalker on 2009-01-17
I have been trying to get apache2 and dyndns to work without luck, have read almost all posts on web and seem to be not having luck.  I have placed "ddclient.conf" in dir /etc/ddclient as per installation guide, and moved the "ddclient" dir into /usr/sbin/ as per guide [had to move the entire directory as every time I tried the "cp" command it would not move it from where it had been extracted to. Guide says "cp sample-etc_rc.d_init.d_ddclient /etc/rc.d/init.d/ddclient", but when I try I get an error saying "cp: cannot stat `sample-etc_rc.d_init.d_ddclient': No such file or directory", and when I look in /etc/ I see about 6 different "rc*.d" folders, all with a rc0.d to rc6.d, but no plain rc.d???.  also guide says to enable automatic startup when booting /sbin/chkconfig  --add ddclient, but when I look in /sbin I don't see "chkconfig"?????
I am lost at this point, any help appriciated](*,)

I am canceling this post as I am going to remove and reload all files and then retry as I am finding problems with my own post...sorry for tiem:confused:

---

### Post by robsablah on 2010-07-01
but but but...........


i wanted to know if it worked.........................

---

### Post by tgalati4 on 2010-07-01
You are using sudo cp otherwise the files won't be copied.

---

### Post by cariboo on 2010-07-02
This thread doesn't make any sense. If anyone wants to create a new thread, go ahead, because this one is Closed.

---

