---
title: "Kernel rebuilt, not booting properly!"
date: 2012-08-03
forum: Server Platforms
---

### Post by mikeatvillage on 2012-08-03
Hi, I've just recompiled the kernel for my 10.04LTS Server to include usbfs. That was the only change I made. The system now doesn't complete the boot sequence, but stops with "Starting apache web server".
 
However, I can ssh/putty/WinSCP into the system and everything appears to be running fine! I can also access the webserver and webmin which I'd installed.
 
Any ideas what I should look at?  I've never performed a kernel rebuild before and followed the instructions I found at [http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/) and it all appeared to be going OK.

---

### Post by Doug S on 2012-08-03
I have not seen that method for compiling the kernel before.
You might want to try this method: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
And on that page, there will be a link to (for 10.04): [http://blog.avirtualhome.com/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/how-to-compile-a-ubuntu-lucid-kernel/)
 
A suggestion, for any method, is at first not to make any changes at all, just to satify yourself that you can compile and load and run the kernel. Then proceed to making changes.
 
You might get better replies over on the "Development & Programming > Packaging and Compiling Programs" forum (maybe a moderator will move this thread).

---

### Post by mikeatvillage on 2012-08-03
Many thanks Doug, I'll try that when back in the office on Monday.

---

### Post by mikeatvillage on 2012-08-07
Thanks again Doug,
 
That all seemed to go OK. I made the mistake of compiling the kernel for all ARCHs so it took all day :-))  It boots OK now but it's not cured my problem.  I bought some new UPSs (Eaton NV800) and they need USBFS to operate with the O/S - it's not compiled into Ubuntu's kernel by default these days as it's "not modern"!  I'll have to go to my "Plan B" and use Debian 6 on my servers as that works fine.
 
Regards
 
Mike

---

### Post by Doug S on 2012-08-07
In the directory structure you created when you created your build enviroment, have a look at the file ???/debian.master/config/config.common.ubuntu
in that file is this line present:```
# CONFIG_USB_FILE_STORAGE is not set
```and might that be the compile time configuration option you are looking for? If yes, try it. Note: I always save the original configuration before making any changes.

---

### Post by mikeatvillage on 2012-08-10
Thanks Doug,
 
sorry for the late reply but I took a day off :-)
 
I did see something similar, I think it was
 
# CONFIG_USB_FILESYSTEM Is not set
 
and I changed that to
 
CONFIG_USB_FILESYSTEM = y
 
Then compiled. Webmin was then showing USBFS as there, but not in use. The system was pausing on boot with a "Skip or manual ..." message until I installed Gnome. All seemed to be OK then but the GUI caused everything to run very slowly. I gave up and installed Debian 6.0 & Gnome and all was well, and good enough for my requirements.
 
However, I'll knock up another system with Ubuntu and see if I can find the config line you've given and see if I can get it working.
 
ATB
 
Mike

---

### Post by Doug S on 2012-08-10
I should have mentioned, I was using a 12.04 system. Maybe some names have changed since 10.04.

---

### Post by bakegoodz on 2012-08-11
Was there any filesystem or mount points changed too?

---

