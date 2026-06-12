---
title: "Redshark don't install"
date: 2011-01-02
forum: Wine
---

### Post by brunodahora on 2011-01-02
Hi, I've been trying to install Redshark on my Ubuntu.
I followed this post: [http://www.pokebeach.com/forums/archive/index.php/thread-55146.html](http://www.pokebeach.com/forums/archive/index.php/thread-55146.html).
I installed everything within wine, but when I try to install Redshark-3.80 it says that I don't have the Windows Scripting Host.
Tecnically I installed it with winetricks.
If anyone can help I would be thankful.
I'm running a Ubuntu 10.10 x64.
See ya!

---

### Post by cogadh on 2011-01-03
I hope you didn't follow the "how-to" to the letter, it full of errors in the commands and such that might make it not work at all:

- The package commands for Ubuntu are different, but I'll assume you knew that (apt-get instead of yum).
- You don't need to install cabextract, it is already installed by default when you install Wine
- The correct command to use winetricks is "sh **winetricks** wsh56 vcrun6" NOT "sh **winetools** wsh56 vcrun6"
- The overrides do not need to be applied at all, winetricks should do that for you
- Don't use "wine start" to install it, use "wine msiexec /i <name of install file>"

If it still doesn't install after that, post the terminal output that Wine produced during the install, it might explain what is happening.

---

### Post by brunodahora on 2011-01-03
Hi, I've managed to correct all those errors except for the correct way to install at wine.
I changed but got the same answer from Redshark.
Here goes the terminal output:
dahora@fairytail:~/Aplicativos$ wine msiexec /i Redshark-3.80.msi 
fixme:advapi:LookupAccountNameW (null) L"dahora" (nil) 0x32f150 (nil) 0x32f154 0x32f148 - stub
fixme:advapi:LookupAccountNameW (null) L"dahora" 0x15fa20 0x32f150 0x1632c8 0x32f154 0x32f148 - stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 20/02/2011, dlt (d/m/y): 16/10/2011
err:msi:ITERATE_Actions Execution halted, action L"LaunchConditions" returned 1603

Thnx!

---

### Post by mihawk_88 on 2011-08-07
I'm trying to install Redshark 4 and I'm having the same problem. Output from terminal is the one posted by brunodahora. Any solution?

---

