---
title: "No video output after install"
date: 2011-12-07
forum: Server Platforms
---

### Post by fnadde42 on 2011-12-07
I have a problem with my server (HP ProLiant DL145 G1). I installed Ubuntu server 11.10 without problems or warnings, then after I installed it and the server had started it went blank and my screen said "*Analog input. Cannot Display This Video Mode*"

I have tried to open up GRUB and try with something I read about but when I hold down shift it says Starting Grub... and the screen goes blank and says "*Cannot Display This Video Mode*".

I have access to the server via OpenSSH. It's just that I wan't the graphic card to work in some situations...

---

### Post by donniezazen on 2011-12-07
I was going to post something similar. I did a Ubuntu-Server install on Dell Inspiron E1505 and on top of that i have xbmc installed. When i connect to 42" TV it loads up xbmc but when i press Fn+F1 for console, their is none. It hangs up at the blank screen and Fn+F7 won't return back to XBMC.

---

### Post by Vegan on 2011-12-07
for some reason some rigs have unorthodox BIOS setups that cause the OS to not recognize certain display setups

I use a plain vanilla PC which works the best, most major vendors work fine

---

### Post by RobFromLafayette on 2011-12-09
I had the same issue with two older Dell PowerEdge server installs (both 11.10)

From [http://ubuntuforums.org/showthread.php?t=1892534#5](http://ubuntuforums.org/showthread.php?t=1892534#5)
[INDENT]In my case, the VGA timings were sending a 75hz refresh rate, and my LCD only goes to 70 (and prefers 60hz)

I found and attached an old CRT, and it works just dandy.

I *think* that you can pass a kernel argument from Grub2 that will force a VGA mode, but I'm still reading up on that.
[/INDENT]
I'm motivated to find a fix so it'll work at 60Hz and let me use generic LCD monitors, but given that I use the box on the network, it's not at the top of my TODO list.

---

### Post by RobFromLafayette on 2011-12-09
> **RobFromLafayette said:**
> I had the same issue with two older Dell PowerEdge server installs (both 11.10)

From [http://ubuntuforums.org/showthread.php?t=1892534#5](http://ubuntuforums.org/showthread.php?t=1892534#5)[INDENT]In my case, the VGA timings were sending a 75hz refresh rate, and my LCD only goes to 70 (and prefers 60hz)

I found and attached an old CRT, and it works just dandy.

I *think* that you can pass a kernel argument from Grub2 that will force a VGA mode, but I'm still reading up on that.
[/INDENT]I'm motivated to find a fix so it'll work at 60Hz and let me use generic LCD monitors, but given that I use the box on the network, it's not at the top of my TODO list.

Followup:  I followed the instructions from here: [http://askubuntu.com/questions/45071/how-do-i-set-the-refresh-rate-used-by-kms-on-the-foss-ati-driver](http://askubuntu.com/questions/45071/how-do-i-set-the-refresh-rate-used-by-kms-on-the-foss-ati-driver) 
and now I'm all set, displaying an old-LCD-friendly 60Hz console.

---

### Post by donniezazen on 2011-12-10
Well, XBMC loads up fine but no tty.

---

