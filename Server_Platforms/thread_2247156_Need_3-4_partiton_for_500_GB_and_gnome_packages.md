---
title: "Need 3-4 partiton for 500 GB and gnome packages"
date: 2014-10-06
forum: Server Platforms
---

### Post by gurusamy2 on 2014-10-06
Hi I am new to ubuntu and i downloaded ubuntu 14.04 amd64 server version and i installed properly and got Black window and asking login prompt and there is no gnome also and i am able to ping google.com and ping 8.8.8.8 with my lan connection.
Note:ubuntu 14.04 server file only 576 Mb, using ubootnetin software i converted as bootable format in USB.

I did [COLOR=#000000][FONT=Consolas]sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install its not working out for me.


My question.

1.Can you please share me any link for necessary packages install properly like gnome etc.
2.I installed auto partiton mode for my 500GB harddisk and took totally.i need to do atleast 3-4 partition,can you please guide for 3-4 partition.
In future i need to install windows also.

Thanks
Saravanan

[/FONT][/COLOR]

---

### Post by JKyleOKC on 2014-10-06
The server versions do not have any sort of window interface; if you want Gnome, you need to use the "desktop" version instead.

Also, if you plan to dual-boot eventually, it's best to install Windows first. When it's installed, it's quite likely to wipe out any existing Linux system on the disk (although recent versions may be a bit more polite about it, the older ones would wipe the disk without pausing to ask permission).

If you want to tweak the number of partitions, choose the "Something else" option on the installer screen. It's the only one that lets you define the number and size of partitions to be created.

---

### Post by nerdtron on 2014-10-06
> **gurusamy2 said:**
> Hi I am new to ubuntu and i downloaded ubuntu 14.04 amd64 server version and i installed properly and got Black window and asking login prompt and there is no gnome also and i am able to ping google.com and ping 8.8.8.8 with my lan connection.
Note:ubuntu 14.04 server file only 576 Mb, using ubootnetin software i converted as bootable format in USB.

I did [COLOR=#000000][FONT=Consolas]sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install its not working out for me.


My question.

1.Can you please share me any link for necessary packages install properly like gnome etc.
2.I installed auto partiton mode for my 500GB harddisk and took totally.i need to do atleast 3-4 partition,can you please guide for 3-4 partition.
In future i need to install windows also.

Thanks
Saravanan

[/FONT][/COLOR]

You should manually start the GUI if you installed it.
```
startx
```

Also, if this is a fresh install, it would be better to do the partitioning on the installation part of the OS. This is a server right? Better learn how to do the manual partitioning.
And why would you like a GUI? Is there any application that you use that requires a GUI?

---

