---
title: "Expanding Disc Space in Oracle Virtual Box (Win XP guest system)"
date: 2013-08-16
forum: Virtualisation
---

### Post by Shallowmind on 2013-08-16
My Win XP virtual machine is close to using all of the disc space it has been given.  I have Googled what to do and have come away more confused than anything.  I have tried this command in the terminal:

VBoxManage modifyhd./home/myname/VirtualBox VMs/WXP/WXP.vdi --resize 20000  

The /home/myname/VirtualBox VMs/WXP/WXP.vdi is what I found in the VirtualBox program, maybe I am using the wrong terms here?

Also what is the best way to expand the partition in Win XP once I have given it more to use?

Thanks

Matt

---

### Post by zeljkojagust on 2013-08-17
You are using the correct command IIRC, but how did you create your initial disk? Did you use *fixed* size or *variable* option. What that means is if you used fixed and dedicated 10 GB of space to your disk when you were creating your WinXP virtual machine, a 10 GB disk image was created right away. If you used variable option and also dedicated 10 GB of space, than a small disk image was created which will eventually expand as you add data to your WinXP virtual machine. I don't know how well did I explain this, but the point is the following: If you used fixed method, you're stuck. That means you cannot resize your VM virtual disk, period. If you used variable method, the command you used should resize your disk, and to resize a partition, boot your WinXP machine and use Disk Management tool located in Control Panel to resize a partition. Should be simple.

---

### Post by Shallowmind on 2013-08-20
Thanks for the reply.  I think I used the fixed method!  So I have to create a new VM with larger capacity and start over?

---

### Post by Kevin_Arnold on 2013-08-20
Sounds like you can try creating a new vdi with the proper size and then clone the current disk over to the new one. (I haven't tested this, so who knows if it'll actually work but it is work a shot.)


```
[FONT=Monaco]vboxmanage createhd --filename new.vdi --size 76800[/FONT]
[FONT=Monaco]vboxmanage clonehd "/home/jon/VirtualBox VMs/eCS_21/eCS_21.vdi" new.vdi --existing
```

Taken from: [/FONT]https://forums.virtualbox.org/viewtopic.php?f=7&t=52693#p241325
[FONT=Monaco]

[/FONT][COLOR=#2E8B57][FONT=Monaco]
[/FONT][/COLOR]

---

