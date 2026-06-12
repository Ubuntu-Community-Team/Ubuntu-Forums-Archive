---
title: "How do I reinstall wine?"
date: 2009-04-18
forum: Wine
---

### Post by wolfyking2 on 2009-04-18
Ok, I decided to get rid of wine.  So I just deleted the folder.  I'm trying to reinstall, but nothing happens.  I only have the files that are in the hidden folder.  What I'm saying is, when I try to install it, there are no problems installing, but it doesn't fully install it.  I tried installing it through .debs, package manager, everything!  I can't get it to install.  Help?

---

### Post by hikaricore on 2009-04-18
You know better than to provide next to no information, we've been through this 100 times.
Please be more specific, provide terminal output of any errors.  Without errors no one can possibly know what's wrong.

---

### Post by wolfyking2 on 2009-04-19
Well, that's what I kinda mean't.  I can't provide any information, because the installation goes fine!  it only installs the dos_devices, drive_c, system reg, user reg, .update-timestamp, and inside the drive_c is windows, and inside windows there is system 32, and win.in, nothing in the system 32 folder. dos_devices has c: and z:, z: just leads me to my filesystem, and c: just leads me to the windows folder.  So basically, when I try to install these things, it only installs what I posted up there!

---

### Post by NightMKoder on 2009-04-19
How is that a problem? What are you expecting in there?

Wine doesn't come with an entire windows packaged in, and most of wine is actually outside your wine prefix.

---

### Post by hikaricore on 2009-04-19
> sudo apt-get remove --purge wine
rm -R ~/.wine
sudo apt-get install wine

This is all you need to guarantee that WINE is completely removed and reinstalled.
I don't know what else you could possibly want and with you being so vague I can't help you further.

---

### Post by wolfyking2 on 2009-04-20
bump

---

### Post by wolfyking2 on 2009-04-20
Well...It's hard to explain.  I mean, it gives me no errors, and I can't put something into the terminal.  When I first installed WINE, it came with ALOT of things. like the system folder, gecko folder, bunch of executables, documents, had a folder called program folder, downloads, etc.  But now when I try to install wine...It doesn't have anything.  And when I try to execute a .exe nothing happens, and when I put it into a terminal (I'll use mabinogi .exe for an example) it gives me an error like this

user@ubuntu:~$ '/home/user/Documents/MabinogiDownloaderV39R.exe' 
bash: /home/user/Documents/MabinogiDownloaderV39R.exe: Permission denied
user@ubuntu:~$ '/home/user/Documents/MabinogiDownloaderV39R.exe' 
wine: created the configuration directory '/home/user/.wine'
'/home/user/Documents/MabinogiDownloaderV39R.exe' 
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/user/.wine' has been updated.
Log file is being written to C:\windows\temp\\PMBInst.log
user@ubuntu:~$ '/home/user/Documents/MabinogiDownloaderV39R.exe' 
Log file is being written to C:\windows\temp\\PMBInst.log
user@ubuntu:~$ 

But I just followed all the commands hikaricore said... Am I doing something wrong?

---

### Post by NightMKoder on 2009-04-20
You can't just run windows programs in bash... you have to put wine before them. Like
```

wine '/home/user/Documents/MabinogiDownloaderV39R.exe' 

```

And that's not wine's fault - its just that the program might not necessarily work. To make sure wine works, make sure you can start winecfg and check that
```

wine notepad

```
indeed opens notepad. Other than that, its an application problem

---

### Post by wolfyking2 on 2009-04-20
oops, I tried the other mabinogi downloader worked.  And I guess wine did fully install.  But when I first installed wine, and I deleted the whole folder, I got 7GB back of space???  That's why I was confused.

---

### Post by NightMKoder on 2009-04-20
I'm guessing you installed other things on wine and then deleted them.

---

