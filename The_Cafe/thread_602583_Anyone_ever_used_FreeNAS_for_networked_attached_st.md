---
title: "Anyone ever used FreeNAS for networked attached storage??"
date: 2007-11-04
forum: The Cafe
---

### Post by kevdog on 2007-11-04
Just wondering if anyone has ever used the FreeNAS distro for configuration of a NAS device.  Would windows or ubuntu have any problems accessing this device??

Thanks.

---

### Post by spamzilla on 2007-11-04
My co worker uses Nas and has installed Nas on several small schools servers and he says it's amazingly stable and will run on virtually any machine. That's all I know about this, sorry.

---

### Post by kevdog on 2007-11-04
Might try this on one of the old machines that I have in the basement.  I wonder if it works with a wireless connection???

---

### Post by chris86wm on 2007-11-05
I used freenas for about a year. It worked perfectly with ubuntu and windows ans was very stable. The only time it was down was when the electricity was out.

Ended up unplugging the machine and opting for an external usb drive........

---

### Post by HermanAB on 2007-11-05
FreeNAS is just Samba.  Any Linux distro can do that.  

Here is how: 
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by songshu on 2007-11-05
it is samba indeed, and nfs and ftp and some other as i remember corectley, but it is NOT linux..

it runs on FreeBSD, it works, its simple, its stable and can be a really good solution in my opinion,

BUT! unless something changed since i have used it, the samba performance on BSD and thus FreeNAS is not so great.
i can definetley recomend you to give it a try, but if it is huge performance with samba you are looking for i must warn you to try it to see if it lives up to your expectations.

---

### Post by kevdog on 2007-11-05
Im disappointed so far with samba and linux so I really doubt it would be different -- wish there was an alternative for windows<-->Linux/bsd comunication.

---

### Post by adam.tropics on 2007-11-05
> **kevdog said:**
> Im disappointed so far with samba and linux so I really doubt it would be different -- wish there was an alternative for windows<-->Linux/bsd comunication.

Well I guess there's always [SSHfs]("http://en.wikipedia.org/wiki/Sshfs") 

More [here]("http://fuse.sourceforge.net/sshfs.html"), [here,]("http://www.linuxjournal.com/article/8904")(guide) and if you'll forgive windows shareware link (!), [here!]("http://www.sftpdrive.com/")

---

### Post by kevdog on 2007-11-05
Excuse my ignorance

but is sshfs any different than ssh,sftp??  Or are these commands transparent for example if I dragged and dropped files from nautilus?

---

### Post by adam.tropics on 2007-11-05
> **kevdog said:**
> Excuse my ignorance

but is sshfs any different than ssh,sftp??  Or are these commands transparent for example if I dragged and dropped files from nautilus?

To be entirely honest, haven't tried this myself yet, but from what I can see, sshfs allows you to mount a remote ssh or sftp server, as if it were a local drive, so if running (could add to startup), yes, it would integrate into nautilus.

---

