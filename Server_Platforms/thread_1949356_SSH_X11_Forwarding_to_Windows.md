---
title: "SSH X11 Forwarding to Windows"
date: 2012-03-30
forum: Server Platforms
---

### Post by createdcreature on 2012-03-30
How could I access X11 GUI apps through SSH on Windows 7 using putty.

I access CLI apps all the time using windows, any way to access GUI apps?

---

### Post by hawkmage on 2012-03-30
You will first need an xserver running on your Win 7 box.  I use X Ming.  

If you use pre-configured  putty sessions for your connections you will need to edit them to enable X11 forwarding.

Since I make most of my connections through putty via the command line I have also edited the default putty session to enable X11 forwarding.  Or also when you launch putty from the command line you can add the parameter -X (that is a uppercase X) to turn on X11 tunneling.  

Now when you run an X11 GUI app it should appear on your win 7 box.

---

### Post by createdcreature on 2012-04-04
Works great! :)

---

