---
title: "VM's and the like"
date: 2018-08-11
forum: Windows
---

### Post by Shibblet on 2018-08-11
I am set up for dual-booting into Kubuntu or Windows 10.

Can you use a VM to boot into a already loaded Windows 10 Partition?

---

### Post by deadflowr on 2018-08-12
Do you mean can you convert a window 10 partition into a vm?
I guess it's confusing as to what constitutes loaded.

---

### Post by Shibblet on 2018-08-12
I guess that would work.

---

### Post by Shibblet on 2018-08-12
I am currently dual-booting.  Each OS has it's own HD.  Windows 10 on one HD, and Kubuntu on the other.

What I would like to do, is be able to boot the Windows 10 partition into a VM, because there are a few programs in Windows 10, that just will not work in Linux under Wine, but will work in a VM.

And since performance isn't really necessary for these programs, It would be nice to not have to re-boot my computer just to run a couple of programs.  It would also be nice, to not have to load up an OS on a VM, since it is already loaded up and all of the programs are installed.

I do have a Macrium Reflect Image of the drive already saved (As backup).

---

### Post by ajgreeny on 2018-08-12
Windows 10, if pre-installed will be totally locked to the hardware it was installed on and can not be reinstalled on any other hardware including a virtual installation, so unless you have a retail copy of Win 10, I don't think you can do what you want.

I have no idea if you can move an installation of any OS from a hard drive to a VM as you are asking but wait for others to reply as there may be a way to do so that I'm unaware of.

---

### Post by westie457 on 2018-08-12
[https://forums.virtualbox.org/viewtopic.php?f=28&t=57692](https://forums.virtualbox.org/viewtopic.php?f=28&t=57692)

This is for Windows 7 with UEFI and GPT.

I have never tried this and probably never will, there is a lot of warnings about failing and no guarantee of success.

---

### Post by yancek on 2018-08-14
There are some explanations of doing something similar on the microsoft site which you should be able to find by doing an online search for "convert windows 10 from hard drive install to virtual".  The site at the link below discusses doing this and apparently it isn't that problematic if you have the windows iso

[https://community.spiceworks.com/how_to/148559-windows-10-physical-to-virtualbox](https://community.spiceworks.com/how_to/148559-windows-10-physical-to-virtualbox)

THe link below also gives an explanation of doing this.

[https://www.howtogeek.com/213145/how-to%C2%A0convert-a-physical-windows-or-linux-pc-to-a-virtual-machine/](https://www.howtogeek.com/213145/how-to%C2%A0convert-a-physical-windows-or-linux-pc-to-a-virtual-machine/)

I've never tried any of this myself so can't speak to how well it might work.  As pointed out above, windows is tied to specific hardware and almost all windows user buy pre-installed systems.  When you pay for windows you are paying them a licensing fee to use one and only one instance of their software on one and only one set of hardware.  You can have a backup but you cannot use both the VM install and the install on hardware.  From your post, I would not expect that to be  problem in this case as you want to move not copy.  Good luck.

---

### Post by Shibblet on 2018-08-15
Yep, you're all correct.  There is no way to do this with Windows 10.  Instead I did a VMWare Machine of Windows 7, which I do own a copy of.  Installed great in Kubuntu.  Downloaded the "tools" and I was up and running.

I need this for Adobe Software that I use on a weekly basis, and don'r really like doing the dual boot thing.  

On a whim though, I threw my steam account into the VM, and loaded up a couple of DX9 games for Windows.  Not perfect, but definitely playable.  Got 60fps for the most part with a few slowdowns here and there.  Like I said, not as good as a Windows boot, but still acceptable.

VMWare has come a long way in this endeavor.  Looks like 7 is going to be my option for the time being.

Thanks for the help, even though it didn't quite pan out the way I'd hoped.  I still have a solution that works.

---

### Post by ajgreeny on 2018-08-15
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

