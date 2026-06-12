---
title: "Extremely slow 3D in Ubuntu guest on VBox"
date: 2011-11-15
forum: Virtualisation
---

### Post by orrorin on 2011-11-15
Hello,

I'm trying to enable/use 3D acceleration in a Ubuntu guest running in VirtualBox with Guest Additions on a Windows host. Although I think the 3D acceleration is being enabled, the performance of my guest takes a nosedive; the machine almost comes to a crawl.

Is this a known issue? Is there a known fix/workaround?
How can I verify the status of 3D acceleration in my Ubuntu guest? What commands to run? What log files can I look at?

My setup ...

ATI Radeon 6770M graphics card (2GB)
Windows 7 Home Premium (64-bit)
VBox 4.1.6 (with Guest Additions)
Ubuntu 11.10 (32-bit) (The problem exists on 64-bit Ubuntu as well.)

Thanks.

---

### Post by An Sanct on 2011-11-15
Did you enable 3D acceleration and have the VB Add-ons for the guest OS installed? (install via Devices>Install Guest Additions [HOST+D], while the machine is running)

---

### Post by orrorin on 2011-11-15
> **An Sanct said:**
> Did you enable 3D acceleration and have the VB Add-ons for the guest OS installed? (install via Devices>Install Guest Additions [HOST+D], while the machine is running)
Yes. I enabled 3D Acceleration support in VBox and have the Guest Additions installed as well.

---

### Post by An Sanct on 2011-11-16
Did you provide enough GPU memory?

Anyhow, Virtualization is not intended for gaming and other heavy 3D actions, and a VM, to my knowledge, is powered with a simulated GPU, it is a "VirtualBox Graphics Adapter".

People in the gaming forums are also complaining about this, there was [this guy]("https://forums.virtualbox.org/viewtopic.php?f=9&t=18365&start=15"), who said it could be mended with a hack of the '.vbox' configuration file, every machine has one.

note: The VB has to be shut down and the manager also may not run!
```
Change from:
<Display VRAMSize="128" monitorCount="1" accelerate3D="true" accelerate2DVideo="true"/>

To:
<Display VRAMSize="256" monitorCount="1" accelerate3D="true" accelerate2DVideo="true"/>
```
If you decide to try this hack, make sure to do a backup of at least the configuration file, if not the whole machine!

The VB manager is just a GUI front-end...

PS. ... Let me stress this again: Virtualization is *_not_* meant for gaming ...

---

### Post by Randymanme on 2011-11-16
In [http://ubuntuforums.org/showthread.php?t=1881101](http://ubuntuforums.org/showthread.php?t=1881101), Copper Bezel said: "Virtualbox doesn't support hardware-accelerated video for Linux guests. You're stuck using Unity 2D and Gnome Fallback that way."

My attempt at running Oneiric in Virtualbox a complete waste of 7 hours.

---

### Post by An Sanct on 2011-11-16
2D is not supported by non-Windows guests, but 3D is... VB warns you about this if you want to set 2D to checked on a non-Windows guest system.

---

### Post by orrorin on 2011-11-16
> **An Sanct said:**
> Did you provide enough GPU memory?

Anyhow, Virtualization is not intended for gaming and other heavy 3D actions, and a VM, to my knowledge, is powered with a simulated GPU, it is a "VirtualBox Graphics Adapter".

People in the gaming forums are also complaining about this, there was [this guy]("https://forums.virtualbox.org/viewtopic.php?f=9&t=18365&start=15"), who said it could be mended with a hack of the '.vbox' configuration file, every machine has one.

note: The VB has to be shut down and the manager also may not run!
```
Change from:
<Display VRAMSize="128" monitorCount="1" accelerate3D="true" accelerate2DVideo="true"/>

To:
<Display VRAMSize="256" monitorCount="1" accelerate3D="true" accelerate2DVideo="true"/>
```
If you decide to try this hack, make sure to do a backup of at least the configuration file, if not the whole machine!

The VB manager is just a GUI front-end...

PS. ... Let me stress this again: Virtualization is *_not_* meant for gaming ...
Thanks for the tip. I was previously using 128MB video RAM. Increasing video RAM to 256MB improves the performance marginally, but no cigar. VBox does not allow you to increase it beyond that, irrespective of how much graphics memory you have on the host.

BTW, I'm trying to use 3D acceleration for Google Earth. But even with 256MB RAM, the overall performance (for ordinary operations like browsing and moving windows) is slower than normal. I was barely able to start firefox and could only goto the home page. Even clicking on links does not seem to work. System manager shows fairly low CPU utilization.

---

### Post by haqking on 2011-11-16
> **Randymanme said:**
> In [http://ubuntuforums.org/showthread.php?t=1881101](http://ubuntuforums.org/showthread.php?t=1881101), Copper Bezel said: "Virtualbox doesn't support hardware-accelerated video for Linux guests. You're stuck using Unity 2D and Gnome Fallback that way."

My attempt at running Oneiric in Virtualbox a complete waste of 7 hours.

Rubbish.

I run 11.10 in virtual box with 3d enabled running Unity 3D

---

### Post by An Sanct on 2011-11-16
Me2 :) I have Unity 3D and all the other glitter under VB.

---

### Post by orrorin on 2011-11-16
> **haqking said:**
> Rubbish.

I run 11.10 in virtual box with 3d enabled running Unity 3D
True. If VirtualBox didn't support 3D acceleration for Linux guest, it would warn just like it does for 2D acceleration.

It's just that in my case, by enabling 3D acceleration, I'm getting Total Deceleration.

Can you please post your host details? i.e. what (graphics) hardware and OS you are running on the host machine?

---

### Post by haqking on 2011-11-16
> **orrorin said:**
> True. If VirtualBox didn't support 3D acceleration for Linux guest, it would warn just like it does for 2D acceleration.

It's just that in my case, by enabling 3D acceleration, I'm getting Total Deceleration.

Can you please post your host details? i.e. what (graphics) hardware and OS you are running on the host machine?

Think pad R61 with 4GB Ram
Nvidia Quadro NVS 140M 512Mb Ram

Running Debian Testing (wheezy) x64

I have a 11.10 VM running all the time minimised so i can troubleshoot the usual unity blah blah rants on here, the VM has 768Mb ram and runs with no worries at all with Unity 3D.

I also currently have a centOS server VM running with 512, and a XP VM with 512. I never assign more than 24 MB video memory to my VM's. i am not a game player but i do use Adobe alot in my XP and i also use skype video conferencing

Also clementine is running playing music and signed in to Xchat.

All running seemlessly and i have over 2 gb spare ram, no swap being used and CPU % is low on both.

Why run google earth in a VM anyways ? why dont you run it natively, it works as well on Linux and Windows why virtualise it ?

Peace

---

### Post by orrorin on 2011-11-16
> **haqking said:**
> Think pad R61 with 4GB Ram
Nvidia Quadro NVS 140M 512Mb Ram

Running Debian Testing (wheezy) x64

I have a 11.10 VM running all the time minimised so i can troubleshoot the usual unity blah blah rants on here, the VM has 768Mb ram and runs with no worries at all with Unity 3D.

I also currently have a centOS server VM running with 512, and a XP VM with 512. I never assign more than 24 MB video memory to my VM's. i am not a game player but i do use Adobe alot in my XP and i also use skype video conferencing

Also clementine is running playing music and signed in to Xchat.

All running seemlessly and i have over 2 gb spare ram, no swap being used and CPU % is low on both.

Why run google earth in a VM anyways ? why dont you run it natively, it works as well on Linux and Windows why virtualise it ?

Peace

Thanks for the host/hardware information. Looks like you are getting a lot of juice out of your hardware. (Professional software engineer??)

In my non-3D-accelerated VM, it falls back to Unity 2D. However, it does show some the 3D effects. e.g. When I run glxgears in this VM, I get a frame rate of around 650FPS.

But, when I enable 3D acceleration in my VM, the entire system seems to slow down. After increasing the video RAM from 128MB to 256MB, I was able to get marginally better performance but could barely open websites. When I run glxgears in this VM, I get a frame rate of about 900FPS. Still the system performance is abysmal.

No particular reason for running google-earth in VM. Some people like to play computer games, I like to see software work. :)

---

### Post by An Sanct on 2011-11-16
> **orrorin said:**
> True. If VirtualBox didn't support 3D acceleration for Linux guest, it would warn just like it does for 2D acceleration.

It's just that in my case, by enabling 3D acceleration, I'm getting Total Deceleration.

Can you please post your host details? i.e. what (graphics) hardware and OS you are running on the host machine?

My host machine info:
Proc: i5 750 (quad @ 2.67 GHz)
Ram: 4 * 2Gb dual channel @ 1333MHz
GPU: ATI Radeon 4300/4500 (4350 if I'm not mistaking), 512MB passive
Main disk: SSD 64GB
uname:  Linux drak 2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 17:52:57 UTC 2011 x86_64 GNU/Linux

So the GPU is really the lamest one I could buy, but cuts the mustard for me, very well actually. ;) As a developer and a non-gamer :) its enough, altho I must say, that I played Trine, the Linux version and the Wine version and both acted pretty good.

---

### Post by orrorin on 2011-11-16
Thank you everyone for your tips and info; I was able to fix/get a work around for the problem.

The problem was there 2 graphics cards on my HP laptop, one from Intel (which is used for power save mode) and another from AMD/ATI (for performance mode) and the laptop supports dynamic graphics switching. Ideally, a user should be able to specify (through the Catalyst app from AMD) what graphics card should be used for a named Windows application. In my case, after some googling around, I set VirtualBox to use the performance mode. For some reason, this was not working. So, I had to disable the Dynamic Graphic Switching feature from the BIOS and now it works fine.

Here's the original thread from HP's support forum...

[http://h30434.www3.hp.com/t5/Notebook-Display-and-Video/quot-Switchable-graphics-quot-BIOS-setting-or-support-via/td-p/327018/page/2](http://h30434.www3.hp.com/t5/Notebook-Display-and-Video/quot-Switchable-graphics-quot-BIOS-setting-or-support-via/td-p/327018/page/2)

Thanks again everyone for sharing your CPU cycles on this.

---

### Post by haqking on 2011-11-16
> **orrorin said:**
> Thank you everyone for your tips and info; I was able to fix/get a work around for the problem.

The problem was there 2 graphics cards on my HP laptop, one from Intel (which is used for power save mode) and another from AMD/ATI (for performance mode) and the laptop supports dynamic graphics switching. Ideally, a user should be able to specify (through the Catalyst app from AMD) what graphics card should be used for a named Windows application. In my case, after some googling around, I set VirtualBox to use the performance mode. For some reason, this was not working. So, I had to disable the Dynamic Graphic Switching feature from the BIOS and now it works fine.

Here's the original thread from HP's support forum...

[http://h30434.www3.hp.com/t5/Notebook-Display-and-Video/quot-Switchable-graphics-quot-BIOS-setting-or-support-via/td-p/327018/page/2](http://h30434.www3.hp.com/t5/Notebook-Display-and-Video/quot-Switchable-graphics-quot-BIOS-setting-or-support-via/td-p/327018/page/2)

Thanks again everyone for sharing your CPU cycles on this.

Cool, glad you got it sorted.

remember to use thread tools to mark the thread as solved.

Cheers

---

