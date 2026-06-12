---
title: "Goodbye VM, Welcome Back Dual Boot"
date: 2008-09-15
forum: Virtualisation
---

### Post by twoseids on 2008-09-15
I tried. I really tried. I was so determined to make it work that when I installed Hardy, I totally wiped my drive clean and went single-boot. No fallback. It's VM or bust.

Bust.

I tried VMWare Player and VMWare Server. I tried VirtualBox OSE and PUEL. But I can't run a Windows VM on my Dell Latitude D520 that works as well as a native installation.

I have yet to establish a successful USB connection. I have yet to establish a connection between my host and guest so I can share files between the two. Bluetooth? Forget about it (although I can't do that in Ubuntu either).

I have spent so many hours installing these VM clients, updating from XP Service Pack 1 all the way to current (it's an old CD), trying fixes I've found here, all to no avail. The few times I've tried to get help, I dunno, maybe everyone's busy, but you never know when you'll get great response on the Forums and when you'll get crickets chirping.

I finally realized that with all the hours I've spent trying to get VM working on my box, I could have dual-booted a bazillion times (with none of the tinkering).

I'll be back. Maybe not for a release or two. But I'll be back.

---

### Post by xeo_pt on 2008-09-15
> **twoseids said:**
> But I can't run a Windows VM on my Dell Latitude D520 that works as well as a native installation.
Can you be more specific?
I'm just installing another Dell server in Ubuntu and XP virtualization to run a special program of my client.

---

### Post by binbash on 2008-09-16
I am using closed source virtual box.I als&#305; tried VMware 6.5 beta and i am using a notebook which has 4gb ram.Virtualization is better then dual boot (if you do not play games of course) in my opinion.I dont agree with any part you wrote (bluetooth etc) and it takes 40 minutes including installation of xp to run a perfect box.

---

### Post by timjohn7 on 2008-09-16
It's a pity the community response wasn't what it normally is.

I have XP SP2 running perfectly in VirtualBox with 4 USB devices connected and 2 folders on my HDD shared through Windows networking and accessible to my VM and normal Ubuntu file activity.

If you reconsider, I am more than happy to help where I can.

---

### Post by killer_d76 on 2008-09-16
same here.. i have a Virtual Box with Windows XP, network, usb and printer connected to it, running perfectly on Hardy 8.04.. 

here's a link wherein you can download Virtual Box [http://www.virtualbox.org/]("http://www.virtualbox.org/")

hope this help!

here's a screenshot of my set-up

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=84547&d=1220860424[/IMG]

---

### Post by ubuwatson on 2008-09-16
I have one of the newer HP notebooks and everything out of the box with 8.04 worked right from the start with no tweaking (in fact everything worked off the live cd including wireless networking !) - in fact some thing that didn't work well under Vista work (problems with the SD card reader, bluetooth, etc) perfectly under Ubuntu - makes me wonder if HPs were built for linux and not windows....

I run windows XP inside of virtual box and it seems faster than XP did when I dual booted, I expect the reason is due to the fact that virtual box drivers are rather light weight, it works flawlessly thus far.

---

### Post by tuxxy on 2008-09-16
If your into heavy virtualisation you should be using 64-Bit! :)

---

### Post by mike1234 on 2008-09-16
> **twoseids said:**
> I tried. I really tried. I was so determined to make it work that when I installed Hardy, I totally wiped my drive clean and went single-boot. No fallback. It's VM or bust.

Bust.

I tried VMWare Player and VMWare Server. I tried VirtualBox OSE and PUEL. But I can't run a Windows VM on my Dell Latitude D520 that works as well as a native installation.

I have yet to establish a successful USB connection. I have yet to establish a connection between my host and guest so I can share files between the two. Bluetooth? Forget about it (although I can't do that in Ubuntu either).

I have spent so many hours installing these VM clients, updating from XP Service Pack 1 all the way to current (it's an old CD), trying fixes I've found here, all to no avail. The few times I've tried to get help, I dunno, maybe everyone's busy, but you never know when you'll get great response on the Forums and when you'll get crickets chirping.

I finally realized that with all the hours I've spent trying to get VM working on my box, I could have dual-booted a bazillion times (with none of the tinkering).

I'll be back. Maybe not for a release or two. But I'll be back.

 I see your point about VM. I installed Sun closed version just to try out Google chrome. VM isn't the same as a HD install. It has it's limits. Mostly the hardware hassles ruin it for me. But it's just an option. Something to do.

M.

---

### Post by xeo_pt on 2008-09-17
I use Ubuntu in Dell server (SC440), the main purpose is to have redundancy,
internet filtering and file sharing, from 1 year ago the customer need to run
a software made with .NET and MS SQL Server, so I start to install vmplayer
with a appliance pre-made with a XP. then install in the XP a VNC server (tightvncserver) in order the guys from the software can configure the XP.
And everything works perfectly including the UBS devices, if I have the focus in the VMmachine and plug the pen, windows will get the pen
 but if the focus is in the Linux host, the virtual machine don't reclaim the device.

---

### Post by twoseids on 2008-09-20
Well I wasn't exactly surprised to get mostly responses of "Well it works for me!" That's what makes it so frustrating to not experience the same rapturous joy of virtualization that you all have. :^(

On Monday I'll get back under the hood and post my specific issues with VirtualBox and VMWare. I suppose it would be most productive and most pertinent to the thread if I just do it as a fresh thread? One last chance with each one!

---

