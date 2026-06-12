---
title: "SELINUX and Hardy 8.04.1"
date: 2008-07-24
forum: Security
---

### Post by justs0me on 2008-07-24
Hello
    Well i came from fedora which had selinux and i really enjoyed it, so i installed selinux on kubuntu hardy 8.04.1 (i used the apt-get install so that it removed apparmor).  for one i dunno how to get to a gui where i can configure or edit selinux. second i goto system settings and under system services it says selinux is set to run at bootup, but under status it is "not running".  how do i fix  

thanks

---

### Post by PmDematagoda on 2008-07-25
Perhaps [this]("https://wiki.ubuntu.com/HardySELinux") may help.

As it points out, you need to add the following kernel parameters:-
```
apparmor.enabled=0
selinux=1
```

---

### Post by justs0me on 2008-07-25
Thanks, i have read that; and while i didnt put that code in myself (ah just looked under /boot/grub/menu.lst and under my kernal options it has "apparmor.enabled=0 selinux=1"), im looking at my system logs and it says:

```
Security Framework initialized
SELinux: Initializing.
SELinux: Starting in permissive mode.
AppArmor: ApprArmor disabled by boottime parameter.
```

so i suppose its working right; i installed SElinux through terminal of sudo apt-get install selinux*   where it removed apparmor.  im trying to get to what fedora would call "system-config-selinux" the gui where i can tell it to be permissive or enforcing, where enforcing it what i would prefer.

---

### Post by PmDematagoda on 2008-07-25
You may need to add the kernel parameter:-
```
setenforce=1
```
as well.

About the SELinux GUIs, I don't think they can be found on Ubuntu mainly because they are a product of Fedora, but perhaps you could obtain the source code of the GUIs and then compile them on Ubuntu.

---

### Post by justs0me on 2008-08-02
Well I haven't tried to compile a GUI, I'm not that good with this stuff, yet, but i do have another question or concert.  When I shutdown it shows some text that it will display (kind of like fedora does on shutdown, the text progresses downward), in it say: 

```
"mount: can't find /selinux in /etc/fstab or /etc/mtab"
```

should i be concerned about this error/problem?



Also I found the command "sestatus" which helped I suppose to see what state the selinux was in:
```
@laptop:~$ sestatus
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   enforcing
Mode from config file:          enforcing
Policy version:                 21
Policy from config file:        refpolicy
```

---

### Post by PmDematagoda on 2008-08-04
To be completely honest, I am not that competent in SELinux, but I do know that there is such a mount point called /selinux, though I have no idea what it is for, perhaps you might find some help in the SELinux documentation or mailing lists?

---

### Post by YyYo on 2008-08-25
Hi There...

If you are interesting on SeLinux GUI for Ubuntu, I would like to inform you that I am starting to develop on as a project for required for getting my academic degree.

It should be intended for Ubuntu and will execute all SeLinux operation, but I think I will manage it to be general for all other Linux distributions.

---

