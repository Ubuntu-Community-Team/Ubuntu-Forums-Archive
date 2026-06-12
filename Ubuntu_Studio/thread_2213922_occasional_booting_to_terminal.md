---
title: "occasional booting to terminal"
date: 2014-03-29
forum: Ubuntu Studio
---

### Post by BrianSwatton on 2014-03-29
Occasionally, my main studio (12.04) boots to a terminal login prompt instead of the xfce login screen.  I have found that if I login and issue "sudo shutdown -r now" it will then reboot correctly.

2 questions really:

1. Why might this be happening?  Some piece of hardware not ready perhaps?

2. Is my login/reboot the best way of recovering from it?

---

### Post by jejeman on 2014-03-29
Is it boots on tty1? What's on tty7? Check for lightdm process, is it running?

---

### Post by Bashing-om on 2014-03-29
BrianSwatton; Hi !


See  jejeman's input, good thought .

Not starting the GUI could be caused by any number of things, and yeah, a disk drive - or other hardware - not ready may certainly be a causation.

What ya can do is disable the pretty graphics during the boot process to see the boots messages on-screen. Maybe get an idea of what is going on.
For a single time poke for testing purposes, how about booting to the grub menu, 'e' key for edit mode -> This similar line :
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff
and remove "quiet splash" -> control x to continue the boot process. - a more permanent thing is to edit "/etc/default/grub" - 

On my system key combo ctl+0 will pause the screen and ctl+s will resume, YMMV. Looking for error conditions.

One might also have a look in the various log files, and see what the system reports.
> 
 Is my login/reboot the best way of recovering from it?

I think so, I too have some glitches sometimes booting up cold, and that is what I do in the event I start up in a crippled condition.

[INDENT]we be in the process
[INDENT][INDENT]of gathering information
[/INDENT][/INDENT][/INDENT]

---

### Post by BrianSwatton on 2014-03-29
Thanks for the input both, I'm now trying to read up on some of the terms here.  I understand nothing of jejeman's post whatsoever I'm afraid.

At least I know the reboot is the thing to do anyway. 

Thanks again.

---

### Post by Bashing-om on 2014-03-29
BrianSwatton; Hey ;

Reading is good.

Let us know when you are ready to proceed and how we can help you over any rough spots.

Help is
[INDENT][INDENT]keyboard away
[/INDENT][/INDENT]

---

### Post by jejeman on 2014-03-31
> **BrianSwatton said:**
> I'm now trying to read up on some of the terms here.  I understand nothing of jejeman's post whatsoever I'm afraid.Tty is a virtual console. We have 7 of them tty1-7. X server is running on tty7, so thats why I asked on wich tty it boots (there is always a note on which tty you are logging in), and what is on tty7. You change consoles by keyboard shortcut CTRL+ALT+F1-7.
Lightdm is Desktop Manager for Ubuntu. It must be running in order to have GUI. So, it is logical to see if it is running. If it is not, then that s is the reason you are in text mode. Probbably on tty1. If it is running then it is another problem etc. You can check it simply with
```
pgrep lightdm
``` It should list a PID.
Is it clear now?

---

### Post by BrianSwatton on 2014-03-31
Thanks jejeman, that's a lot clearer.  The next time it happens I'll investigate as you suggested.

I've been converting other machines from XP to Ubuntu this weekend, including my business admin.  I have seen this happen a couple times on other machines too, usually after some config change I believe.

I'm not too concerned anyway, as it is quite rare normally and easily recovered from.  It would be nice to work out what's going on though, as it is stopping me from recommending Ubuntu to others (not so computer minded) as an alternative to XP for web, mail, office etc.

Thanks again, I'll update this thread if I find out more.

---

