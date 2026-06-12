---
title: "Alt-SysRq-K is broken in QQ 12.10"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by The Cog on 2012-10-02
I have found that Alt-SysRq-K (to kill the current X session) is broken in 12.10. Does anyone know how to recover this functionality?

---

### Post by mc4man on 2012-10-02
read here on how to re-enable in kernel
[http://ubuntuforums.org/showpost.php?p=12267738&postcount=6](http://ubuntuforums.org/showpost.php?p=12267738&postcount=6)

---

### Post by The Cog on 2012-10-03
Thanks for the link, I wasn't aware of that setting. But /proc/sys/kernel/sysrq is already 1, and other SysRq sequences (e.g. B) still work. So I can brutally reboot the box easily, but cannot just kill X.

Edit:
This is rubbish. I forget myself and tried ot on a 12.04 system, not a 12.10 system.

---

### Post by philinux on 2012-10-03
Not at my box but I seem to remember the ctrl alt del might log out.

---

### Post by The Cog on 2012-10-03
Thanks, but Ctrl-Alt-Del doesn't seem to work either. I have a feeling that even when it did, years ago, it was voluntary by X. Alt-SysRq-K is better because it works (used to) even when X was completely frozen.

---

### Post by mc4man on 2012-10-03
Have tried as Bazon posted & for the most part works here
(haven't had a lock up to try on  & in one test attempt didn't get back to login screen, just a black screen

The default here is 176 - 
$ uname -a && cat /proc/sys/kernel/sysrq
Linux doug-XPS-M1330 3.5.0-16-generic #25-Ubuntu SMP Fri Sep 28 22:31:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
176

---

### Post by funicorn on 2012-10-03
It seems gnome3 refrains KBD from sending a XKB terminate signal to Xserver through  terminate:ctrl_alt_bksp.

But in the gnome-tweak-tool version 3.6.0-0ubuntu1~1 all, there is in the 'typing' tab a setting for 'terminate' action, click on the drop down list and u can find Ctrl + Alt + Bksp. 

I haven't tried it myself. Maybe later.

Yeah, it works now. It seems gnome-tweak-tool is nicely making up for gnome3's xkb shortness

---

### Post by The Cog on 2012-10-03
Solved.
Sorry, mc4man. You were right. I was forgetting myself and trying it on a 12.04 machine. 

ON th e12.10 machine, /proc/sys/kernel/sysrq is indeed defaulted to 172, and setting it to 1 re-enables SysRq-K to kill the X server. Perfick.

---

### Post by mc4man on 2012-10-03
> **funicorn said:**
> It seems gnome3 refrains KBD from sending a XKB terminate signal to Xserver through  terminate:ctrl_alt_bksp.

But in the gnome-tweak-tool version 3.6.0-0ubuntu1~1 all, there is in the 'typing' tab a setting for 'terminate' action, click on the drop down list and u can find Ctrl + Alt + Bksp. 

I haven't tried it myself. Maybe later.

Yeah, it works now. It seems gnome-tweak-tool is nicely making up for gnome3's xkb shortness

If one wants to enable ctrl+alt+backspace it's avail. in system settings
(keyboard > keyboard layout or keyboard layout directly > options ...

---

### Post by funicorn on 2012-10-03
No. keyboard layout setting is removed in gnome 3.60

---

### Post by philinux on 2012-10-03
> **The Cog said:**
> Solved.
Sorry, mc4man. You were right. I was forgetting myself and trying it on a 12.04 machine. 

ON th e12.10 machine, /proc/sys/kernel/sysrq is indeed defaulted to 172, and setting it to 1 re-enables SysRq-K to kill the X server. Perfick.


Does that interfere with reisub at all?

---

### Post by The Cog on 2012-10-03
I don't think so. 1 was the default value in 12.04 anyway.
In 12.10 with the value set to 1, I just confirmed that K, B and O all have the expected effect. E dropped me back to a tty, which I don't remember happening before but I could be wrong there. U seems to do what it's supposed to (lots of read-only filesystem errors until I rebooted). I didn't try I or S, and I don't think R ever did anything visible anyway.

---

### Post by WorLord on 2012-10-03
> **funicorn said:**
> No. keyboard layout setting is removed in gnome 3.60

No, it is not.  I just used it.

And re-eneabled CTRL+ALT+BACKSPACE.

---

### Post by mc4man on 2012-10-03
> **WorLord said:**
> No, it is not.  I just used it.

And re-eneabled CTRL+ALT+BACKSPACE.

What he was referring to I believe was g-c-c 3.6 & gkbd-capplet, ect. In that case there isn't any layout/options available anymore.
12.10 (default) won't be using g-c-c 3.6, what Ubuntu decides to do for 13.04 I've no clue

---

### Post by funicorn on 2012-10-03
can you paste your gkbd-capplet version and gnome-control-center version?

Mine is: 
gkbd-capplet: 3.6.0-0ubuntu1
gnome-control-panel: 
1:3.6.0-0ubuntu1

> **WorLord said:**
> No, it is not.  I just used it.

And re-eneabled CTRL+ALT+BACKSPACE.

---

### Post by funicorn on 2012-10-03
can you paste your gkbd-capplet version and gnome-control-center version?

Mine is: 
gkbd-capplet: 3.6.0-0ubuntu1
gnome-control-center: 1:3.6.0-0ubuntu1

> **WorLord said:**
> No, it is not.  I just used it.

And re-eneabled CTRL+ALT+BACKSPACE.

---

### Post by funicorn on 2012-10-03
can you paste your gkbd-capplet version and gnome-control-center version?

Mine is: 
gkbd-capplet: 3.6.0-0ubuntu1
gnome-control-center: 1:3.6.0-0ubuntu1


Thanks to your message, I downgraded to gnome-control-center 1:3.4.2-0ubuntu18, it's OK now.

> **WorLord said:**
> No, it is not.  I just used it.

And re-eneabled CTRL+ALT+BACKSPACE.

---

### Post by philinux on 2012-10-04
help.

I've tried using all means to edit /proc/sys/kernel/sysrq. gedit says it cant save as it cant create a backup ans save anyway doesn't work. Nano seems to work but on reboot it's back to 176.

How are you guys editing this file?

---

### Post by The Cog on 2012-10-04
> **philinux said:**
> help.

I've tried using all means to edit /proc/sys/kernel/sysrq. gedit says it cant save as it cant create a backup ans save anyway doesn't work. Nano seems to work but on reboot it's back to 176.

How are you guys editing this file?

With a command like this:
```
sudo sh -c 'echo 1 > /proc/sys/kernel/sysrq'
```
Writing to this pseudo-file is always overwritten by a reboot. The entire /proc directory tree is in the OS's imagination, they are not files on disk they are a view into the OS's inner workings.

As described by this post: [http://ubuntuforums.org/showpost.php?p=12267738&postcount=6](http://ubuntuforums.org/showpost.php?p=12267738&postcount=6)
You can set to reconfigure on reboot by editing /etc/sysctl.conf and adding the line:
```
kernel.sysrq = 1
```

---

### Post by philinux on 2012-10-04
Doh, of course. Memory lapse. Cheers.

Worky now.

---

