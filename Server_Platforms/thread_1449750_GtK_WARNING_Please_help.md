---
title: "GtK WARNING/ Please help"
date: 2010-04-08
forum: Server Platforms
---

### Post by M-ManLA on 2010-04-08
I am still learning the ropes on Ubuntu server. I am trying to set up samba, but when I use the "gedit" command, I get this error:

> 
GtK-WARNING **: cannot open display
I had installed the gedit command by using apt-get and aptitude, but still no luck. Please help men

PS I am using virtualbox to test Ubuntu Server 9.10. All help is very appreciated.

---

### Post by CharlesA on 2010-04-08
Does the machine have a GUI? That error usually means that you haven't installed or launched an X session (since gedit is a graphical program, not text based)

---

### Post by cdenley on 2010-04-08
"nano" is a text-based text editor.
```

sudo nano /etc/samba/smb.conf

```

---

### Post by M-ManLA on 2010-04-09
Oh Thank you guys. I was reading and every site I read said use gedit. But I'm using command lines. Thanks. That was frustrating. Now, to create files on it...

---

