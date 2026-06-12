---
title: "VirtualBox groups problem"
date: 2008-02-18
forum: Virtualisation
---

### Post by Havok_CR on 2008-02-18
:popcorn::popcorn:

Hello there... someone can help me? This is not a VIRTUALIZATION problem... but is related... 
Well I just installed VirtualBox directly from the .deb ... Like everybody know I need to add myself to the "vboxusers" group... well...
"sudo usermod -G vboxusers havok"
Restarted X ... And the sound wasn't working...

havok@fireshield:~$ id
uid=1000(havok) gid=1000(havok) grupos=1000(havok),1001(vboxusers)

...
I really screw it up isn't it? ... where is audio, adm, dialout, cdrom, floppy, audio, dip, video, plugdev, scanner, lpadmin, admin, netdev, powerdev and all the others groups I can not remember? ... well now I can't do "sudo" ...

](*,) ](*,) ](*,)

I'm using Ubuntu 7.10.
Thanks in advance and sorry for my english xD
(I think this machine have no root anymore.. this should be possible? ... just thinking ... )

---

### Post by merlinDwizzard on 2008-02-18
you could have went to system/administration/users and groups to add user to vbox. Have you tried rebooting yet? sometimes when x restarts, it kinda freaks out.

---

### Post by sisco311 on 2008-02-18
reboot in recovery mode(select it from the grub menu)

add your user to the administrator group:
```
usermod -a -G admin username
```reboot in normal mode and use the GUI: Users and Groups to add your user to the other groups or this command:

```
sudo usermod -a -G adm,dialout,cdrom,floppy,audio,dip,video,fuse,plugdev,scanner,netdev,lpadmin,powerdev username
```*replace the username from the commands with your user name
** -a  =  append

---

### Post by Havok_CR on 2008-02-18
Thank you very much!
That was fast and effective, like everything in Ubuntu Community, again, thanks :D

---

