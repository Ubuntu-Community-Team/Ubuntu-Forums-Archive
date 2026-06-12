---
title: "Access to headless server which won't boot ?"
date: 2005-07-27
forum: Server Platforms
---

### Post by erland on 2005-07-27
Is there a way to setup a headless server so it will be possible to access it over the network if it doesn't boot ?

The server is already configured so it is possible to access with ssh and X11 when it has successfully booted. The problem is when it doesn't boot successfully for some reason. When it doesn't boot today it just stops with a root prompt on the local console and the network is not enabled so it is impossible to see what happens.
The solution today is to turn off the power switch after a while when I feel something is wrong, move the server to another room and connect a monitor, keyboard and mouse and start it up and then make required changes to make it boot again. However, I feel that there must be a better solution for this.

Maybe it is possible to configure the server so it is possible to access it using ssh when it doesn't boot ?
Maybe it is possible to use some LiveCD to boot it and enable network ssh access so it is possible to see what happens ?

Is there anyone that has a solution for this problem ?

---

### Post by Shiven on 2005-07-27
you could run a livecd on it and ssh in... 

on the other hand, if you have a terminal you should be able to /etc/init.d/sshd (or just sshd, i don't know how this runs on ubuntu) which would re-enable ssh connections from the terminal... although i'm not sure if that is what you meant.

---

### Post by erland on 2005-07-27
[QUOTE=Shiven]you could run a livecd on it and ssh in... [/QUOTE]
Do you know any live CD which boots and launch sshd automatically so all I have to do is insert the CD in the server and then go back to my laptop and connect to the server ?
I understand that it is possible to create a customized Live CD which does this but do you know if there already exists one ?

[QUOTE=Shiven]
if you have a terminal you should be able to /etc/init.d/sshd (or just sshd, i don't know how this runs on ubuntu) which would re-enable ssh connections from the terminal... although i'm not sure if that is what you meant.[/QUOTE]
The problem is that the server is headless, so the server does neither have keyboard/mouse nor monitor. Sshd is already configured so it runs when the boot success, the problem is when the boot fails and the server stops in some recovery mode without network enabled (runlevel 1 ?)

More suggestions are welcome

---

### Post by LordHunter317 on 2005-07-27
I'm confused as to what happened.  The server isn't configured to start up networking at boot at all, or did it have an error in the init process (like a bad filesystem) and dump you to the emergency console as a result?

More details, but it sounds like you need iLO or a network KVM to be connected to the box.

---

### Post by erland on 2005-07-27
Some clarifications:
- The server is configured to startup both networking and sshd when everything works as it should, so the normal case is no problem at all.

The problem is when when something goes wrong during the boot for some reason, then the boot process exits to the local emergency console which I of course cannot access since there are no keyboard/mouse/monitor connected to the server.

Network KVM would be a solution, but I am afraid it would be to expensive because this is just my personal server at home and this happens maximum a few times per year. 
It would be preferable if it was possible to solve this only with software in some way.

---

### Post by LordHunter317 on 2005-07-27
[QUOTE=erland]It would be preferable if it was possible to solve this only with software in some way.[/QUOTE]You umm, can't, unless you run everything off like a rescue CD with a known good, nonchanging configuration.  And even then, depending on what it does on startup, you're not assured.

---

### Post by erland on 2005-07-27
It does not have to solve every possible situation, in the worst case I can always move the server to another room and connect a keyboard, mouse and monitor. But it would be good if I at least could solve some situations completely from a remote computer, today I have to move the server every time this happens.

The most frequent situations where I have got boot failures so far:
- Power break, boot stops and shows an emergency console and request that fsck is executed on all partitions. 
- Kernel upgrade and some kernel module hasn't been recompiled before the reboot. This happend with every kernel upgrade 
with my previous Suse installation with the nvidia nvnet driver module, but the network works out of the box with ubuntu so it will hopefully work better.
- New kernel modules added and the boot configuration for them is incorrect in some way.

Does anyone of if there are some rescue CD's /live CD's available which can startup without user interaction and also launch sshd or something simliar that allow me to connect from a remote machine ?

---

### Post by LordHunter317 on 2005-07-27
[QUOTE=erland]It does not have to solve every possible situation,[/quote]The problem is, there is no real software solution for the situations you're having, besides what I outlined above.

>  in the worst case I can always move the server to another room and connect a keyboard, mouse and monitor.The cases you describe are all considered worse cases, from a production point-of-view.

> The most frequent situations where I have got boot failures so far:
- Power break, boot stops and shows an emergency console and request that fsck is executed on all partitions. What filesystem(s) are you using?  If you're using a journaled filesystem and this happens regularly, that points to a hardware problem

> - Kernel upgrade and some kernel module hasn't been recompiled before the reboot. This happend with every kernel upgrade 
with my previous Suse installation with the nvidia nvnet driver module, but the network works out of the box with ubuntu so it will hopefully work better.This shouldn't ever be an issue if you're not compiling your kernel yourself, provided the kernel provdies the drivers you need.

And if it doesn't, you compile the drivers you need before the reboot.  That's more than doable, and what I do for the 3rd party drives on my systems.

---

### Post by erland on 2005-07-27
[QUOTE=LordHunter317]What filesystem(s) are you using?  If you're using a journaled filesystem and this happens regularly, that points to a hardware problem[/QUOTE]
I was using reiserfs with Suse and now with ubuntu I'm using ext3. It has accutally not happend with ubuntu yet, but it happend several times with Suse earlier. If I remember correct it happend every time I had to stop the computer with the power switch(due to the fact that I could reach it over the network) and also every time a power break occured. Do you mean linux should be able to automatically reboot in these situations if ext3 or reiser is used ?


[QUOTE=erland] - Kernel upgrade and some kernel module hasn't been recompiled before the reboot. This happend with every kernel upgrade
with my previous Suse installation with the nvidia nvnet driver module, but the network works out of the box with ubuntu so it will hopefully work better.
[QUOTE=LordHunter317]This shouldn't ever be an issue if you're not compiling your kernel yourself, provided the kernel provdies the drivers you need.

And if it doesn't, you compile the drivers you need before the reboot.  That's more than doable, and what I do for the 3rd party drives on my systems.[/QUOTE]
[/QUOTE]
Do you know how to do this ?
Because I tried some times but since 'uname -r' is used in the makefiles and reports the previous kernel until it has been rebooted with the new kernel I never succeeded. I thought it had to be possible to recompile the modules before rebooting with the new kernel but I never found out how.

---

