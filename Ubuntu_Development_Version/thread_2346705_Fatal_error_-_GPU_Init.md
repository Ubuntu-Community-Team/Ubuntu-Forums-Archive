---
title: "Fatal error - GPU Init"
date: 2016-12-17
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-12-17
Hello,
when I try to run a live DVD of 17.04 the following error appears. It can't detect the correct resolution of my monitor.
```
[drm:radeon_get_bios [radeon]] *ERROR* unable to locate a BIOS RO _[trunked row]_ 
radeon 0000:01:00.0: Fatal error during GPU init
[TTM] Memory type 2 has not been initialized

```

I've got a AMD Radeon™ HD 7610M Graphics (1GB dedicated memory). Where should I report this bug (if it can be considered a bug)?

---

### Post by ventrical on 2016-12-18
Perhaps you can still use 'nomodeset' during live/install

and see what happens.

---

### Post by enricobe on 2016-12-18
> **ventrical said:**
> Perhaps you can still use 'nomodeset' during live/install

and see what happens.

Is it an option that I should add at boot?

---

### Post by Bashing-om on 2016-12-18
enricobe; Hello;

short answer:
> 
Is it an option that I should add at boot? 

Yes;

Longer response:
Boot the liveUSB;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) [legacy boot }-> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line are also  now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works to boot the liveUSB, once installed to the hard drive you might have to also implement "nomodeset" initially to get to the desktop to here also install a graphic's driver .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by enricobe on 2016-12-18
> **Bashing-om said:**
> enricobe; Hello;

short answer:

Yes;

Longer response:
Boot the liveUSB;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) [legacy boot }-> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line are also  now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works to boot the liveUSB, once installed to the hard drive you might have to also implement "nomodeset" initially to get to the desktop to here also install a graphic's driver .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

Thank you very much. Unfortunately it didn't work. I've tried with nomodeset first and with all the other options you can find in the F6 menu then, but no one worked. I'm still using 16.04 because all the newer versions have this problem on my PC.

---

### Post by Bashing-om on 2016-12-18
enricobe; Well !

In this case we back up another step or so .
Did you verify the .iso file with md5sum ? How did you make the liveUSB ?

Did you verify the copy to the USB ? ( in the liveUSB boot options is " check disk for defects" )

As we must have a solid foundation before we look for other reasons why not .

[INDENT][INDENT]still just a process
[/INDENT][/INDENT]

---

### Post by enricobe on 2016-12-18
> **Bashing-om said:**
> enricobe; Well !

In this case we back up another step or so .
Did you verify the .iso file with md5sum ? How did you make the liveUSB ?

Did you verify the copy to the USB ? ( in the liveUSB boot options is " check disk for defects" )

As we must have a solid foundation before we look for other reasons why not .

[INDENT][INDENT]still just a process
[/INDENT][/INDENT]
Hello, I didn't checked this particular DVD but there are some reasons why. 
1) I was a beta tester of the 16.10 and it worked fine for months until an update I did about 1 month before the official release. This update (but unfortunately I haven't checked which packages had been updated) broke my screen resolution. This happened with an installed and working Kubuntu system. 
2) In the following months I've downloaded and tried the stable DVD of 16.10 (both Xubuntu and Ubuntu) and at least 3 daily builds of 17.04. Everytime I got a 800*600 monitor resolution. 

So I could check the DVD I'm using in this moment but I'm pretty sure this is not the root of the problem :-) with 16.04 I have no problems

---

### Post by Bashing-om on 2016-12-18
enricobe; Hey;

Your knowledge and skills are the greater than I had "assumed" :)
Maybe try a directed boot parameter ?
radeon.modeset=0
In 16.10 or 17.04 it does not make sense that the ATI HD 7610M Graphics card is not recognized and the system configures for that card.
Depending on your exact graphics hardware, Ubuntu 16.04 and later will use either the open-source AMDGPU driver or the open-source Radeon driver, both of which are included in the default Ubuntu 16.04+ installation. The amdgpu driver, pre-installed in 16.04+, is used for AMD's newest graphics cards. The radeon driver, also pre-installed in 16.04+, is used for older AMD graphics cards that the amdgpu driver doesn't support.

Looking now to see what I can find out about the 7610M card .

[INDENT][INDENT][INDENT]gotta be a way
[/INDENT][/INDENT][/INDENT]

---

### Post by enricobe on 2016-12-18
With nomodeset or Radeon.modeset =0 I see a new error.

ERROR no UMS support in Radeon module

someone on another forums suggests to remove nomodeset to solve this problem :lolflag:

---

### Post by zika on 2016-12-18
> **enricobe said:**
> With nomodeset or Radeon.modeset =0 I see a new error.```
ERROR no UMS support in Radeon module
```As You should since (for a quite some time) radeon needs modesetting i.e. UMS...

---

### Post by ventrical on 2016-12-18
> **Bashing-om said:**
> enricobe; Hey;

Your knowledge and skills are the greater than I had "assumed" :)
Maybe try a directed boot parameter ?
radeon.modeset=0
In 16.10 or 17.04 it does not make sense that the ATI HD 7610M Graphics card is not recognized and the system configures for that card.
Depending on your exact graphics hardware, Ubuntu 16.04 and later will use either the open-source AMDGPU driver or the open-source Radeon driver, both of which are included in the default Ubuntu 16.04+ installation. The amdgpu driver, pre-installed in 16.04+, is used for AMD's newest graphics cards. The radeon driver, also pre-installed in 16.04+, is used for older AMD graphics cards that the amdgpu driver doesn't support.

Looking now to see what I can find out about the 7610M card .
[INDENT][INDENT][INDENT]gotta be a way
[/INDENT]
[/INDENT]
[/INDENT]


I am curious if you had recently switch the video adapter card into another PC.

Sometimes removing/reinserting the card will unlock the memory.

Can you give us results of :

```

inxi -Fxz


```

?

regards..

---

### Post by Yellow Pasque on 2016-12-19
[https://bugzilla.kernel.org/show_bug.cgi?id=141741](https://bugzilla.kernel.org/show_bug.cgi?id=141741)
It should really be fixed in Ubuntu 17.04, unless you're using an old .iso

> someone on another forums suggests to remove nomodeset to solve this problem

nomodeset is a good workaround if you can't boot to a GUI, but it's not going to help in your case. As you've discovered, you just trade one error message for another with the same result (low resolution).

---

### Post by enricobe on 2016-12-20
> **ventrical said:**
> I am curious if you had recently switch the video adapter card into another PC.

Sometimes removing/reinserting the card will unlock the memory.

Can you give us results of :

```

inxi -Fxz


```

?

regards..

Here it is (sorry for the delay in my reply)
```

System:    Host: enrico-linux Kernel: 4.4.0-53-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA product: SATELLITE C855-2J5 v: PSCBYE-04F00RIT
           Mobo: Intel model: PLCSF8 v: Type2 - Board Version
           Bios: Insyde v: 6.80 date: 10/01/2013
CPU:       Dual core Intel Core i5-3230M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10376
           clock speeds: max: 3200 MHz 1: 1352 MHz 2: 1336 MHz 3: 1490 MHz
           4: 1378 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Whistler LE [Radeon HD 6610M/7610M]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.07hz
           GLX Renderer: Gallium 0.4 on AMD TURKS (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Advanced Micro Devices [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-53-generic
Network:   Card-1: Realtek RTL8723AE PCIe Wireless Network Adapter
           driver: rtl8723ae port: 3000 bus-ID: 08:00.0
           IF: wlp8s0 state: up mac: <filter>
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 09:00.0
           IF: enp9s0 state: down mac: <filter>
Drives:    HDD Total Size: 750.2GB (10.0% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD0 size: 750.2GB
Partition: ID-1: / size: 110G used: 4.9G (5%) fs: ext4 dev: /dev/sda5
           ID-2: /home size: 440G used: 65G (16%) fs: ext4 dev: /dev/sda6
           ID-3: swap-1 size: 1.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda7
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 41.0C mobo: N/A gpu: 31.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 231 Uptime: 2 min Memory: 760.2/3902.7MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 


```

I have never removed the Video Card because my PC is a notebook. 

> **Temüjin said:**
> [https://bugzilla.kernel.org/show_bug.cgi?id=141741](https://bugzilla.kernel.org/show_bug.cgi?id=141741)
It should really be fixed in Ubuntu 17.04, unless you're using an old .iso


nomodeset is a good workaround if you can't boot to a GUI, but it's not going to help in your case. As you've discovered, you just trade one error message for another with the same result (low resolution).
Thank you. Happy to see that it's a known issue. If I was the only one with this problem I think it wouldn't ever be fixed :)

---

### Post by zika on 2016-12-20
> **enricobe said:**
> Happy to see that it's a known issue. If I was the only one with this problem I think it wouldn't ever be fixed :)Dependency of radeon driver on UMS is not an issue it is a feature. :)

---

### Post by enricobe on 2016-12-20
> **zika said:**
> Dependency of radeon driver on UMS is not an issue it is a feature. :)

Yes, of course. To be honest, I have no idea of what UMS is. I'll do an online search. 

I hope they will solve this problem quickly. With 16.04 LTS I have only 4 years of support left :biggrin:

---

### Post by MikeMecanic on 2016-12-20
[FONT=Ubuntu]Hello Enricobe,[/FONT]
 
 [FONT=Ubuntu]Did you try Kernel 4.9 to see how your mobo reacts?  Maybe there is (no) relation but [4.9 is the only Kernel]("https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable") in ZZ now.[/FONT]
 
 [FONT=Ubuntu]ZZ 20161219 ISO image (out of the box):[/FONT]
 ```
[FONT=Ubuntu]lsb_release -a && uname -r[/FONT]
 [FONT=Ubuntu]No LSB modules are available.[/FONT]
 [FONT=Ubuntu]Distributor ID:    Ubuntu[/FONT]
 [FONT=Ubuntu]Description:    Ubuntu Zesty Zapus (development branch)[/FONT]
 [FONT=Ubuntu]Release:    17.04[/FONT]
 [FONT=Ubuntu]Codename:    zesty[/FONT]
 [FONT=Ubuntu]4.9.0-11-generic[/FONT]
  
 [FONT=Ubuntu]dpkg -l xserver-xorg-video-ati [/FONT] 
 [FONT=Ubuntu]ii  xserver-xorg-v 1:7.8.0-1    amd64        X.Org X server -- AMD/ATI display[/FONT]
 [FONT=Ubuntu]dpkg -l xserver-xorg-video-amdgpu[/FONT]
 [FONT=Ubuntu]ii  xserver-xorg-v 1.2.0-1      amd64        X.Org X server -- AMDGPU display[/FONT]

```  
 
 [FONT=Ubuntu]Out of Proposed:[/FONT]

 ```
[FONT=Ubuntu]dpkg -l mesa-vdpau-drivers[/FONT]

 [FONT=Ubuntu]ii  mesa-vdpau-dri 13.0.2-1ubun amd64        Mesa VDPAU video acceleration dri[/FONT]
 [FONT=Ubuntu]dpkg -l libllvm3.9[/FONT]
 [FONT=Ubuntu]ii  libllvm3.9:amd 1:3.9.1-1ubu amd64        Modular compiler and toolchain te[/FONT]

``` 
 
 [FONT=Ubuntu]Regards,
P.S. In order to eliminate noise, the #1 suspect to consider is a defective installer.

[/FONT]

---

### Post by Yellow Pasque on 2016-12-20
It seems the OP posted this in the wrong subforum (since inxi output shows Ubuntu 16.04).

> I hope they will solve this problem quickly.

The fix was included in Ubuntu's 4.8.0-31.33 (or later) kernel. You should be able to easily install it using lts-kernel package. Maybe someone using Ubuntu 16.04 can give you more specific instructions if you don't know what that means.

> I have no idea of what UMS is. I'll do an online search.

Userspace ModeSetting. It's not relevant to your issue.

---

### Post by mc4man on 2016-12-20
> **Temüjin said:**
> It seems the OP posted this in the wrong subforum (since inxi output shows Ubuntu 16.04).



The fix was included in Ubuntu's 4.8.0-31.33 (or later) kernel. You should be able to easily install it using lts-kernel package. Maybe someone using Ubuntu 16.04 can give you more specific instructions if you don't know what that means.



Userspace ModeSetting. It's not relevant to your issue.
For 16.04 the upcoming lts kernel can be used/tested with - 
```
sudo apt install linux-generic-hwe-16.04-edge
```
That should provide at least - 
> $ uname -a
Linux doug-Lenovo-IdeaPad-Y510P 4.8.0-31-generic #33~16.04.1-Ubuntu SMP Wed Dec 7 16:16:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
Otherwise in a couple of weeks or so should show up in -proposed.

or use a mainline build..

---

### Post by zika on 2016-12-21
> **Temüjin said:**
> It seems the OP posted this in the wrong subforum (since inxi output shows Ubuntu 16.04).INXI output is from OP's installed system and his question, that opened this thread, is about 17.04 DVD...

---

### Post by slickymaster on 2016-12-21
Moved to the **Hardware** sub-forum since the OP is under 16.04
> **enricobe said:**
> Here it is (sorry for the delay in my reply)
```

System:    Host: enrico-linux Kernel: 4.4.0-53-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) [COLOR=#ff0000]Distro: Ubuntu 16.04 xenial[/COLOR]
......
```


---

### Post by zika on 2016-12-21
> **slickymaster said:**
> Moved to the **Hardware** sub-forum since the OP is under 16.04> **enricobe said:**
> Hello,
[SIZE=5]when I try to run a live DVD of [SIZE=6]17.04[/SIZE] the following error appears.[/SIZE] It can't detect the correct resolution of my monitor.
```
[drm:radeon_get_bios [radeon]] *ERROR* unable to locate a BIOS RO _[trunked row]_ 
radeon 0000:01:00.0: Fatal error during GPU init
[TTM] Memory type 2 has not been initialized

```I've got a AMD Radeon&#8482; HD 7610M Graphics (1GB dedicated memory). Where should I report this bug (if it can be considered a bug)?At the time error occurs HW is not under 16.04...;)

---

### Post by Yellow Pasque on 2016-12-21
> **zika said:**
> INXI output is from OP's installed system and his question, that opened this thread, is about 17.04 DVD...

Are you sure it's not a typo? If user complains about an issue using the LiveUSB/DVD, why would s/he not give output from it?

---

### Post by zika on 2016-12-21
> **Temüjin said:**
> 1. Are you sure it's not a typo? 
2. If user complains about an issue using the LiveUSB/DVD, why would s/he not give output from it?ad. 1. Of course not. I can not be sure for myself let alone someone else... ;)
ad. 2. I've seen much worse errors than that... ;)
Update&#8321;: [https://ubuntuforums.org/showthread.php?t=2337948&p=13564065#post13564065](https://ubuntuforums.org/showthread.php?t=2337948&p=13564065#post13564065) leads me to think that above there was not a typo...

---

### Post by enricobe on 2016-12-23
Hello,
the error is about **17.04**.

I've posted a 16.04 output because I'm currently stuck on 16.04 because of this problem. I thought the output was needed for more specific hardware info, so I've run it on 16.04.

@zika Yes! I didn't remember that I've already asked for this question :confused:

---

### Post by slickymaster on 2016-12-23
> **enricobe said:**
> Hello,
the error is about **17.04**.

I've posted a 16.04 output because I'm currently stuck on 16.04 because of this problem. I thought the output was needed for more specific hardware info, so I've run it on 16.04.

@zika Yes! I didn't remember that I've already asked for this question :confused:

And moved back to the **Ubuntu Development Version** sub-forum.

---

### Post by Yellow Pasque on 2016-12-24
My apologies to the staff for creating extra work. :\
Back to the question(s) at hand...

> Where should I report this bug (if it can be considered a bug)? 
First, I would try the latest .iso of 17.04 and verify the install, as others have suggested. If you still get the error, I think the best place to report it is:
[https://bugzilla.kernel.org/enter_bug.cgi?product=Drivers](https://bugzilla.kernel.org/enter_bug.cgi?product=Drivers)  (and select 'Video - DRI(non-Intel)' as the component)
Don't be surprised if they ask you to do advanced troubleshooting, such as a git bisect of the kernel.
You could also report it to Ubuntu/Launchpad. They will probably ask you to try the latest generic mainline kernel.

---

### Post by enricobe on 2016-12-25
> **Temüjin said:**
> My apologies to the staff for creating extra work. :\
Back to the question(s) at hand...


First, I would try the latest .iso of 17.04 and verify the install, as others have suggested. If you still get the error, I think the best place to report it is:
[https://bugzilla.kernel.org/enter_bug.cgi?product=Drivers](https://bugzilla.kernel.org/enter_bug.cgi?product=Drivers)  (and select 'Video - DRI(non-Intel)' as the component)
Don't be surprised if they ask you to do advanced troubleshooting, such as a git bisect of the kernel.
You could also report it to Ubuntu/Launchpad. They will probably ask you to try the latest generic mainline kernel.
Thank you for your help.

I'll do a full check of the Image and the DVD following this guide:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Considering that I'm pretty sure that the error is not due to a bad installation disk and my English is not perfect, could you please help me to write a good bug-report? The problem is simple: i can't use the full resolution of my monitor. Max resolution is 1366x768 but I can only use 800x600 (or 1024x768, i don't remember but I'll check when I'll try the lastest Ubuntu 17.04 ISO). I'll need about 2h to download and check the DVD

EDIT: the problem seems SOLVED. With the lastest 17.04 build the screen resolution is OK. It's not an error in the installer DVD but some update in the last days which fixed the problem. I've downloaded the 16.10 and verified it: the screen resolution is still broken. It seems that the developers did some updates in the last week and fixed the issue. Thank you everyone for the help! I hope the problem is fixed forever :)

---

