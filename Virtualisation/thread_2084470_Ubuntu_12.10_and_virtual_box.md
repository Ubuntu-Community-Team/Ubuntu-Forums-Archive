---
title: "Ubuntu 12.10 and virtual box?"
date: 2012-11-15
forum: Virtualisation
---

### Post by ytkuser12 on 2012-11-15
HI all so here is my system specs before virtual box and Ubuntu 12.10 i had a question going off my system specs how much video ram and how much memory and processor cores can i safely give Ubuntu without slowing down windows behind it. system specs are as followed.

I have a Alienware X51 with Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz 
I have 2 video cards as this is a Optimus machine no its not a laptop its a small form factor PC my in built video card is a Intel(R) HD Graphics 4000 <---- i don't use this never have. I use the dedicated NVIDIA GeForce GTX 555 1 GB video card. and I have 8 GIGS ram. 

Please let me know how much stuff i can safely give my virtual machine without compromising my windows 7 performance thanks all.

---

### Post by NikTh on 2012-11-15
Hi , 
VirtualBox has this option. Generally you can use almost the half , eg: memory , cpu(s) ... etc . 
If something exceeds the suggested values , then VB will inform you with a red-orange message. (that you will slow down your system)

Thanks

---

### Post by ytkuser12 on 2012-11-15
> **NikTh said:**
> Hi , 
VirtualBox has this option. Generally you can use almost the half , eg: memory , cpu(s) ... etc . 
If something exceeds the suggested values , then VB will inform you with a red-orange message. (that you will slow down your system)

Thanks
ok so i can give like 2 cpus and would 1 gig ram work or should i give it 2. now on video memory what is satisfactory to give Ubuntu. 
also i havent installed it yet virtual box but should i install all the stuff it wants me to install. I also had seen people having issues with resizing the screen i have a native HD screen that dose. 1920x1080 will i get ubuntu that high? is there any special stuff i need to do to V-box?.

---

### Post by pkadeel on 2012-11-15
> **ytkuser12 said:**
> ok so i can give like 2 cpus and would 1 gig ram work or should i give it 2. now on video memory what is satisfactory to give Ubuntu. 
also i havent installed it yet virtual box but should i install all the stuff it wants me to install. I also had seen people having issues with resizing the screen i have a native HD screen that dose. 1920x1080 will i get ubuntu that high? is there any special stuff i need to do to V-box?.
If you have not already install vbox then i would suggest installation of the current version directly from virtualbox repository by following their easy to follow steps.
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

They have not added the quantal repository on that page but it exists so use quantal as your platform name in the source url.

As far the screen resolution, USB access and other useful stuff you shall also manually download the guest extenssion pack from
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
and install it through vbox preference settings.

---

### Post by ytkuser12 on 2012-11-15
> **pkadeel said:**
> If you have not already install vbox then i would suggest installation of the current version directly from virtualbox repository by following their easy to follow steps.
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

They have not added the quantal repository on that page but it exists so use quantal as your platform name in the source url.

As far the screen resolution, USB access and other useful stuff you shall also manually download the guest extenssion pack from
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
and install it through vbox preference settings.

UM i'm on windows 7 the link you posted to is for linux i need the windows 7 vbox to install linux inside it. also what is quantal repository? and i dont see quest extenssions on there? is that something i need to search for inside v-box?

---

### Post by ytkuser12 on 2012-11-15
ok i found the extension pack there but still not sure what this other quantal repository is i cant find it. anyhow i think i have all i need will try it in a few min.

---

### Post by pkadeel on 2012-11-15
> **ytkuser12 said:**
> ok i found the extension pack there but still not sure what this other quantal repository is i cant find it. anyhow i think i have all i need will try it in a few min.
I misread the OP due to its title "Ubuntu 12.10 and virtual box"

If host is windows 7 then forget about quantal repository
windows installers are on main download page. Choose your architecture 32bit or 64 bit
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Extenssion pack is same for both linux and windows

---

### Post by NikTh on 2012-11-15
> **ytkuser12 said:**
> ok so i can give like 2 cpus and would 1 gig ram work or should i give it 2. now on video memory what is satisfactory to give Ubuntu. 
also i havent installed it yet virtual box but should i install all the stuff it wants me to install. I also had seen people having issues with resizing the screen i have a native HD screen that dose. 1920x1080 will i get ubuntu that high? is there any special stuff i need to do to V-box?.

Give to video memory all the MBs . I think the maximum value is 128MB. 

When you install VB , you have to install the Guest Additions as well , for full-screen support and some other stuff. 

Extension pack is not needed , but you can install it if (for example) you want USB 2.0 Support. 

Please change your title (edit the first post) to a more accurate , eg : "Ubuntu 12.10 and virtual box - Windows Host" . 

Thanks

---

### Post by ytkuser12 on 2012-11-15
> **NikTh said:**
> Give to video memory all the MBs . I think the maximum value is 128MB. 

When you install VB , you have to install the Guest Additions as well , for full-screen support and some other stuff. 

Extension pack is not needed , but you can install it if (for example) you want USB 2.0 Support. 

Please change your title (edit the first post) to a more accurate , eg : "Ubuntu 12.10 and virtual box - Windows Host" . 

Thanks

ok are the quest additions included in virtual box? or do i need to do a command once inside ubuntu?

---

### Post by ytkuser12 on 2012-11-15
ok i changed my heading but its not changing in the forum not sure why. also i forgot one important thing should i use 64 bit ubuntu or 32 bit?

---

### Post by NikTh on 2012-11-15
Guest additions included in VB program. Not needed to download them separately. Once you install your Virtual Ubuntu , click the "Devices" and last in list you will see "Guest Additions" . Click and installation will begin. You have to reboot (your Virtual OS) for the changes to take effect (and you will have full-screen VB)

Better to install the same architecture as host , but this is not a requirement. 

Thanks

---

### Post by ytkuser12 on 2012-11-16
ok got guest additions inst stalled rebooted but i  can do full screen but i cant select the auto re-size quest display ? how do i get that to work.

---

### Post by NikTh on 2012-11-17
> **ytkuser12 said:**
> ok got guest additions inst stalled rebooted but i  can do full screen but i cant select the auto re-size quest display ? how do i get that to work.

Most of resize methods , configured with Host+F (host=right Ctrl). Alternatively you can click on "View" and see what allows you to select. 

Thanks

---

### Post by zeon777 on 2013-04-28
complete cure for ubuntu 13.04 and virtualbox 4.2.12
graphic/performa fix for ubuntu os
part of this solution applies where aero / transperancy is used including d3d games




recommended graphic memory or virtual ram for aero base operating system is 256mbs
min.ram -768mb for 13.04




1.enable 3d support invirtual box 3d settings
2.terminal commands..
.../usr/lib/nux/unity_support_test -p   *(Not software rendered:no, unity 3d support:No)*
...uname -r
...sudo apt-get install linux-headers-$(uname -r)
...sudo apt-get autoremove
...sudo apt-get install build-essential
>>now insert vitualbox guest iso from devices and to install manually follow
...cd /media
...ls
...cd username
...ls
...cd VBOX*
...ls
...sudo ./VBoxLinuxAdditions.run
...sudo gedit /etc/modules
>>add "vboxvideo" *in the next line after lp  means  loop>lp>vboxvideo like this* click save and file quit
3.restart the machine
4.now open the terminal to checkunity 3d is enabled or not
.../usr/lib/nux/unity_support_test -p 
5.after this shut down the machine lets raise the virtual ram
6.close virtual machine and virtual box
7.follow this path C:\Users\Username\VirtualBox VMs\ubuntu 13.04
8.now look for ".vbox" extension file and open it with temporarily with wordpad
9.look for the following lines and replace these in following manner
...Display VRAMSize="128" monitorCount="1" accelerate3D="true" accelerate2DVideo="false"/>
>><Display VRAMSize="256" monitorCount="1" accelerate3D="true" accelerate2DVideo="false"/>
10.now u can set 256 mb virtual memory for this operating system.
11.any os can be provided with desired vram this way






reference and sources::


babarehner @ e-wrench.com and youtube


An sanct on ubuntuforums.org


rpxmac on forums.virtualbox.org

thanks everyone who supported

---

