---
title: "KOTOR 2 help?"
date: 2009-06-04
forum: Wine
---

### Post by superhaus on 2009-06-04
After seeing the recent trailer for The Old Republic, I got excited about Star Wars again and dug out my old KOTOR 2 disks. Unfortunately, I cannot get it running under WINE.

It installs and launches fine, but at the configuration screen on the start menu, it scans my systems and gives this error:

Error --[] 64 MB
Graphics required: 32 MB OpenGL 1.4 compatible PCI or AGP 3D Hardware accelerator with Hardware Transform and Lighting (T&L) Capability required

I know that my video card will run this game, and WoW runs fine under WINE.

Any suggestions? I'm a bit of a newbie with WINE. I did try it with Emulate a Virtual Desktop both checked and unchecked with the same result.

---

### Post by Dark Aspect on 2009-06-04
> **superhaus said:**
> After seeing the recent trailer for The Old Republic, I got excited about Star Wars again and dug out my old KOTOR 2 disks. Unfortunately, I cannot get it running under WINE.

It installs and launches fine, but at the configuration screen on the start menu, it scans my systems and gives this error:

Error --[] 64 MB
Graphics required: 32 MB OpenGL 1.4 compatible PCI or AGP 3D Hardware accelerator with Hardware Transform and Lighting (T&L) Capability required

I know that my video card will run this game, and WoW runs fine under WINE.

Any suggestions? I'm a bit of a newbie with WINE. I did try it with Emulate a Virtual Desktop both checked and unchecked with the same result.

Ignore the launcher, cd to the directory and use:

```
wine swkotor2.exe WINEDEBUG=-all
```

You'll be happy to know though that both kotor games run rather well with newer versions of wine, be sure to get the most up to date version [here]("http://www.winehq.org/download/deb"). The "WINEDEBUG=-all" is not necessary but as a general rule can increase the speed of applications/games. I usually write a script file to change to the games directory, disable compiz and than load the game with the necessary command line arguments. Something like

```
metacity --replace --sm-disable &
done
exit 0
cd /home/{USERNAME}/.wine/etc
wine File.exe WINEDEBUG=-all -opengl
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering
```

---

### Post by superhaus on 2009-06-05
> **Dark Aspect said:**
> Ignore the launcher, cd to the directory and use:

```
wine swkotor2.exe WINEDEBUG=-all
```




Thanks for your help. Using that command, I got this error:

err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)

So I tried it with sudo and got:

wine: /home/richard/.wine is not owned by you

---

### Post by Dark Aspect on 2009-06-05
> **superhaus said:**
> Thanks for your help. Using that command, I got this error:

err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)

So I tried it with sudo and got:

wine: /home/richard/.wine is not owned by you

[QUOTE=YokoZar]# Never run Wine with sudo - Do not run Wine as root or by using sudo. Doing so doesn't help anything and will break your fake Windows installation entirely.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111")

Ok two more questions, is ALSA audio enabled in winecfg and are you using the absolute latest wine version? Use winecfg to tell under the about tab.

---

### Post by superhaus on 2009-06-05
> **Dark Aspect said:**
> [http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111")

Ok two more questions, is ALSA audio enabled in winecfg and are you using the absolute latest wine version? Use winecfg to tell under the about tab.

ALSA is enabled, and I am using 1.0.1

---

### Post by Dark Aspect on 2009-06-05
> **superhaus said:**
> ALSA is enabled, and I am using 1.0.1

[Update here]("http://www.winehq.org/download/deb")

Also, I forget that not everyone runs every game they own through a NO-CD crack. Use winecfg and click on devices and click autodetect that can help with cd protection issues.

---

### Post by superhaus on 2009-06-05
> **Dark Aspect said:**
> [Update here]("http://www.winehq.org/download/deb")

Also, I forget that not everyone runs every game they own through a NO-CD crack. Use winecfg and click on devices and click autodetect that can help with cd protection issues.

Do you think it is a protection issue?

I updated WINE and clicked autodetect. I also tried a chmod to fix the permission denied problem.

richard@richard-laptop:~$ cd .wine/drive_c/Program\ Files/LucasArts/SWKotOR2/
[email]richard@richard-laptop:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$ wine swkotor2.exe WINEDEBUG=-all
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
[email]richard@richard-laptop:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$ ls -al /dev/sg0
crw-rw---- 1 root disk 21, 0 2009-06-05 16:03 /dev/sg0
[email]richard@richard-laptop:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$ sudo chmod o+rw /dev/sg0
[sudo] password for richard: 
[email]richard@richard-laptop:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$ ls -al /dev/sg0
crw-rw-rw- 1 root disk 21, 0 2009-06-05 16:03 /dev/sg0
[email]richard@richard-laptop:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$ wine swkotor2.exe WINEDEBUG=-all
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
[email]richard@richard-laptop:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$

---

### Post by Dark Aspect on 2009-06-05
> **superhaus said:**
> Do you think it is a protection issue?

Could be since I don't know what /dev/sg0 is exactly on your computer. Unfortunately I am at a lost as to what to try next, sorry. You could try a clean wine directory but I don't know how much that would help, especially if you don't have a lot of applications installed on wine to begin with. I apologize for not being very helpful, perhaps someone can pick up where I left off?

On a side note, here are some things you can try. Post you problem and your terminal output [here at the Wine forums]("http://forum.winehq.org/viewforum.php?f=2&sid=5993208db62e6e2a0487e064e34f1e5d") and try to update the game to version 2.10.

---

### Post by NightMKoder on 2009-06-05
Hate to break it to you guys, but the way you're using WINEDEBUG, it's not actually doing anything. You have to put it before your command or as an export (you're setting a variable, its not a wine command). Two choices:

export WINEDEBUG=-all
wine bla.exe

OR

WINEDEBUG=-all wine bla.exe

but NOT after. And certainly, if you're having problems, do NOT do WINEDEBUG=-all, since that hides any useful messages.

---

### Post by Dark Aspect on 2009-06-05
> **NightMKoder said:**
> Hate to break it to you guys, but the way you're using WINEDEBUG, it's not actually doing anything. You have to put it before your command or as an export (you're setting a variable, its not a wine command).

Thanks NightMKoder, I didn't realize.

---

