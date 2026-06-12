---
title: "Using without Monitor"
date: 2012-05-05
forum: Ubuntu One (CLOSED)
---

### Post by Geffers on 2012-05-05
I have an old computer in my network that does not have a monitor connected, it is used merely as a printer, scanner and file server.

I'd love to be able to use this machine with UbuntuOne so I could upload larger files off peak at night, can UbuntuOne be used via command line or has anyone an idea how I could use the machine as an upload server.

Geffers

---

### Post by thnewguy on 2012-05-05
I don't think Ubuntu One will work without a graphical interface. You might try Fish-Sync, which will work with or without a GUI. It's designed to let you sync multiple folders across multiple machines on your network.
[http://fishsync.sourceforge.net/](http://fishsync.sourceforge.net/)

---

### Post by Geffers on 2012-05-05
> **thnewguy said:**
> I don't think Ubuntu One will work without a graphical interface. You might try Fish-Sync, which will work with or without a GUI. It's designed to let you sync multiple folders across multiple machines on your network.
[http://fishsync.sourceforge.net/](http://fishsync.sourceforge.net/)

Thanks for input but it is the file sharing options that are or interest to me, allowing others to access files.

Trouble is I have a slow upload speed so it would be handy to schedule the old computer to upload overnight.

Geffers

---

### Post by Merciless on 2012-05-06
I have the same problem.  I use a small low power sever (Fit-pc2) and use ssh/screen to manage it.  

If I use the offical Fit-pc2 release 8.04 or Mint 9, Ubuntu One will connect without ever logging in graphically.  Those are too old for my taste and I upgraded to 12.04, and am working through those issues.  

I don't use the graphical interface Ubuntu One will not sync, older version supported this set-up. Is there anyway to restore that functionality?

---

### Post by mparillo on 2012-05-11
> **thnewguy said:**
> I don't think Ubuntu One will work without a graphical interface.

Drop box will work from a command line:
[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

To activate you will need access to a browser. In your case, either Lynx, or a GUI browser on some other computer.

---

