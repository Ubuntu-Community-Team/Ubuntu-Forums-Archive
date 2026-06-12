---
title: "USB and Virtualbox"
date: 2008-06-24
forum: Virtualisation
---

### Post by bren21 on 2008-06-24
I have tried every tutorial I could find for getting usb support for Virtualbox in Hardy, however I still get same the following error:

```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.
```

I uncommented the lines in my mountdevsubfs.sh file, and done various other things but it still gets an error. Any help is appreciated. Here are some of the tutorials I have tried:

[http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/]("http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/")
[http://forum.notebookreview.com/showthread.php?t=242936]("http://forum.notebookreview.com/showthread.php?t=242936")
[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox+usb]("http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox+usb")

---

### Post by dje on 2008-06-24
try [this one]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") its always worked for me

hope that helps
dje

---

### Post by bren21 on 2008-06-24
Tried that one as well, still get the same error.

---

### Post by philinux on 2008-06-24
Are you using vbox from synaptic or from their website.

Dumb question but has to asked. Have you enable usb under settings for the guest.

---

### Post by bren21 on 2008-06-24
Edit: I did some fiddling and somehow got it to work. Not sure what I did, but I'm not complaining.

---

### Post by all2ez on 2008-06-24
I was having lots of problems with virtualbox causing my computer to just freeze up and drop my network connection.  Someone suggested disabling the io apic and usb.  so i did that and it has been working way better.

Anyway, to access my usb devices I just let them auto mount in Ubuntu and I have set up the /media directory as a virtualbox shared folder and mounted that as a network drive in the XP guest.

Not sure what you are doing, but this works great for accessing usb hard drives.

---

