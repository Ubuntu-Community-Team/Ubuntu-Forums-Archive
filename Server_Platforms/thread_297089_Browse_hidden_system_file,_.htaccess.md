---
title: "Browse hidden system file, .htaccess"
date: 2006-11-10
forum: Server Platforms
---

### Post by Jong on 2006-11-10
I have installed SAMBA on my Ubuntu 6.10 server for network access with Windows XP. However I've learned .htaccess files are treated as system files in Linux, why it's not visible when accessing from Windows.

I can turn on "view hidden system files" in Windows. That brings though a 1000 other files and directories to the surface in Windows system.

Is it possible to make hidden system files in Ubuntu visible? Or better, only turn on visibility for .htaccess files?

---

### Post by SoggyCornflake on 2006-11-10
> **Jong said:**
> <snipped>I can turn on "view hidden system files" in Windows. That brings though a 1000 other files and directories to the surface in Windows system.

Is it possible to make hidden system files in Ubuntu visible? Or better, only turn on visibility for .htaccess files?

In a command line type ```
ls -a 
```.  If you're using KDE there's and option and I'm pretty sure Gnome does too.  Just hunt around the menu/configure options and you'll find it.

---

### Post by Jong on 2006-11-10
Thanks. From your answer I can see I haven't expressed my question correctly.

What I meant was, make hidden system files in Ubuntu visible for Windows, regarding to network access.

---

### Post by cotn on 2006-11-11
You should do this only temporary, chmod .htacces to 0775.
Then you can acces youre file anywhere. Do what you wan't to do and when youre done, chmod it back.  

Or you can chown it to the user account from your client pc.

---

### Post by Jong on 2006-11-14
Thanks for the tips, I'll try your last suggestion.

---

