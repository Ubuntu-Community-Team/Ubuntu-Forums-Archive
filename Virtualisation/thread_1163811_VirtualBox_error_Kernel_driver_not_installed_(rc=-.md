---
title: "VirtualBox error: Kernel driver not installed (rc=-1908)"
date: 2009-05-19
forum: Virtualisation
---

### Post by yemaya on 2009-05-19
Hi all,

Let me first say that this is my final resort after googling this issue for the last several hours. None of the solutions that I have found are working for me.

My VirtualBox (PUEL, not OSE) was working fine until about three hrs ago. I am receiving the following error:

 p, li { white-space: pre-wrap; }  > Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

[COLOR=#0000FF]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


By searching other threads, I ran the following:

```
sudo /etc/init.d/vboxdrv setup
```

I received the following  output:

sudo: /etc/init.d/vboxdrv: command not found


I have removed VB several times and reinstalled using the following:
```
sudo apt-get remove dkms
sudo apt-get remove virtualbox-2.2

sudo apt-get install virtualbox-2.2
```

Each time I also rebooted my PC.


I have received no joy. I want the PUEL version and not the OSE because I need to be able to load my USB devices in VirtualBox and the OSE version apparently does not have that capability. I still have two virtual machines (one XP.vdi and one Vista.vdi) saved. I thought that maybe they needed to be removed also (which I didn't want to do since the process of loading a Windows VM is time-consuming), so I created a new VM to test whether it would load, however, same problem occurred.

I also found [this]("http://74.125.47.132/search?q=cache:jpxSLyVp0CEJ:forums.virtualbox.org/viewtopic.php%3Ff%3D7%26t%3D13413+sudo:+/etc/init.d/vboxdrv:+command+not+found&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a") thread which was someone who had the same problem and found a hint from [here]("http://mandrivausers.org/lofiversion/index.php/t49504.html") and solved this problem, however, I had a really hard time applying the Mandriva instructions to Ubuntu. Btw, I am using Jaunty kernel 2.6.28-11-generic.

Thanks

---

### Post by tim_wright on 2009-05-19
Run this command in the /etc/init.d/ folder and paste in the output:

ls | grep vbox

---

### Post by caver1 on 2009-05-19
Try running it without the sudo.
caver1

---

### Post by milesnapue on 2009-06-08
I have the exact same problem and have searched with no results. How do I go about running that command in that directory so I can post an output?

---

### Post by lin-lin_224 on 2009-06-20
I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:     	 	 	 	 	 	  [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
[FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
 The commands are:
  	 	 	 	 	 	  [FONT=AR PL UMing TW, serif]
[/FONT]
[FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]
 
Good luck&#65281;
;)
> **yemaya said:**
> Hi all,

Let me first say that this is my final resort after googling this issue for the last several hours. None of the solutions that I have found are working for me.

My VirtualBox (PUEL, not OSE) was working fine until about three hrs ago. I am receiving the following error:

 p, li { white-space: pre-wrap; }  


By searching other threads, I ran the following:

```
sudo /etc/init.d/vboxdrv setup
```I received the following  output:

sudo: /etc/init.d/vboxdrv: command not found


I have removed VB several times and reinstalled using the following:
```
sudo apt-get remove dkms
sudo apt-get remove virtualbox-2.2

sudo apt-get install virtualbox-2.2
```Each time I also rebooted my PC.


I have received no joy. I want the PUEL version and not the OSE because I need to be able to load my USB devices in VirtualBox and the OSE version apparently does not have that capability. I still have two virtual machines (one XP.vdi and one Vista.vdi) saved. I thought that maybe they needed to be removed also (which I didn't want to do since the process of loading a Windows VM is time-consuming), so I created a new VM to test whether it would load, however, same problem occurred.

I also found [this]("http://74.125.47.132/search?q=cache:jpxSLyVp0CEJ:forums.virtualbox.org/viewtopic.php%3Ff%3D7%26t%3D13413+sudo:+/etc/init.d/vboxdrv:+command+not+found&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a") thread which was someone who had the same problem and found a hint from [here]("http://mandrivausers.org/lofiversion/index.php/t49504.html") and solved this problem, however, I had a really hard time applying the Mandriva instructions to Ubuntu. Btw, I am using Jaunty kernel 2.6.28-11-generic.

Thanks

---

### Post by lin-lin_224 on 2009-06-20
I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

---

### Post by hilltop on 2009-06-20
I ran into the same problem today 20-June-2009 after a recent kernel update to jaunty 64bit.  Vbox aborted upon trying to start a vm and I followed its own instructions to run '/etc/init.d/vboxdrv setup' as root.  This worked, but I am confused as to why this is required?  VirtualBox has a very clear warning about Ubuntu users needing to have the dkms package installed so that Vbox gets recompiled with kernel updates.  I already had and still have dkms installed.  Will this step be necessary after every kernel update?  What is still missing?

---

### Post by BrMBr on 2009-06-22
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
[FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
 The commands are:
                                 [FONT=AR PL UMing TW, serif]
[/FONT]
[FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]
 
Good luck&#65281;
;)

Worked for me! Thanks!!!

---

### Post by Stickee on 2009-06-23
Me as well, thank you. :)

---

### Post by betteberg on 2009-06-24
I have also this problem, and i have tried the solution in this thread, but it just do not work. I use the PUEL version of virtualbox and i have also tried with the OSE version. None of them work. 

I have tried the 

```
sudo /etc/init.d/vboxdrv setup
```But this is what comes out. 


bash: /etc/init.d/vboxdrv: No such file or directory


Do anybody have some solutions on my problem?

---

### Post by picuru on 2009-06-25
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)


This worked for me Thanks!!

---

### Post by aki300 on 2009-07-30
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
[FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
 The commands are:
                                 [FONT=AR PL UMing TW, serif]
[/FONT]
[FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]
 
Good luck&#65281;
;)

Worked for me, thanks!

Ubuntu 9.04

---

### Post by kouchris on 2009-07-31
i also getting bash: 

/etc/init.d/vboxdrv: No such file or directory

using the command

> /etc/init.d/vboxdrv setup
any ideas?

---

### Post by asai on 2009-08-02
My solution described here:
[http://ubuntuforums.org/showthread.php?p=7721420#post7721420]("http://ubuntuforums.org/showthread.php?p=7721420#post7721420")

---

### Post by hotrod02 on 2009-08-19
This fixed my Virtual Box issue.  Thank you very much!:)

> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

---

### Post by dandav101 on 2009-08-26
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)


This worked for me!! Good one. Thanks!
:P:P

---

### Post by rinocom on 2009-10-20
> **kouchris said:**
> i also getting bash: 

/etc/init.d/vboxdrv: No such file or directory

using the command


any ideas?

Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```
I seem to be good now.

Rhino

---

### Post by defiledatheart on 2009-10-25
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

that worked for me too! thanks! :)

---

### Post by atomicben on 2009-10-25
[lin-lin_224]("http://ubuntuforums.org/member.php?u=859698")'s solution worked for me.  THANKS!

---

### Post by time_bomb on 2009-11-11
> **betteberg said:**
> I have also this problem, and i have tried the solution in this thread, but it just do not work. I use the PUEL version of virtualbox and i have also tried with the OSE version. None of them work. 

I have tried the 

```
sudo /etc/init.d/vboxdrv setup
```But this is what comes out. 


bash: /etc/init.d/vboxdrv: No such file or directory


Do anybody have some solutions on my problem?
haha,the same to me.

i have reinstall the vbox,now everything goes well...

---

### Post by giutax on 2009-11-11
rinocom's solution worked fine for me...thank you!

---

### Post by enimen0 on 2009-11-18
to those who still have problems using the command "sudo /etc/init.d/vboxdrv setup", should try this:

sudo /etc/init.d/vboxdrv.dpkg-bak setup

it worked fine for me!
Ubuntu 9.10
VirtualBox 3.0.12

---

### Post by ajdthekid on 2009-11-29
this worked for me thanks!!!

---

### Post by nessakairi on 2009-11-30
Thanks! This works for me, except that I have to do this each time I boot the computer. Do you know how to make it so it works every time? Thanks.

---

### Post by btgroup on 2009-12-02
this worked for me Thanks very much

---

### Post by mjones41 on 2009-12-05
sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

Fixed my virtual box great, but why did the dkms remove my google earth and skype?

---

### Post by m42h31 on 2009-12-30
```
**sudo /etc/init.d/vboxdrv setup**
```  this solution is work for me. but i got same error after rebooting my computer.

```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

virtualbox say i need to **/etc/init.d/vboxdrv setup** again after reboot my computer :( :(, i'm using ubuntu karmic koala kernel 2.6.31-17-generic. virtualbox version 3.1.2, i found same problem on virtualbox 3.0.1 
click here to see the [screenshot]("http://farm3.static.flickr.com/2669/4229013939_86be5c5af6_b.jpg")

this is the log :
```
00:00:00.800 VirtualBox 3.1.2 r56127 linux.x86 (Dec 17 2009 13:41:09) release log
00:00:00.800 Log opened 2009-12-30T11:09:11.105377000Z
00:00:00.800 OS Product: Linux
00:00:00.800 OS Release: 2.6.31-17-generic
00:00:00.800 OS Version: #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009
00:00:00.800 Host RAM: 3023MB RAM, available: 2636MB
00:00:00.800 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.800 Process ID: 5256
00:00:00.800 Package type: LINUX_32BITS_UBUNTU_9_10
00:00:00.853 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf89b9060 - ModuleInit at 00000000f89cc860 and ModuleTerm at 00000000f89cc820
00:00:00.853 SUP: VMMR0EntryEx located at 00000000f89cc700, VMMR0EntryFast at 00000000f89cba30 and VMMR0EntryInt at 00000000f89cb850
00:00:00.949 VBoxSharedClipboard mode: Bidirectional
00:00:00.962 ************************* CFGM dump *************************
00:00:00.962 [/] (level 0)
00:00:00.962   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:00.962   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:00.962   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:00.962   Name            <string>  = "bt4" (cb=4)
00:00:00.962   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:00.962   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:00.962   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:00.962   RamSize         <integer> = 0x0000000018000000 (402653184)
00:00:00.962   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:00.962   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:00.962   SyntheticCpu    <integer> = 0x0000000000000000 (0)
00:00:00.962   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:00.962   UUID            <bytes>   = "b4 25 b6 a3 01 4a c5 4f b9 91 a3 26 a4 b2 3d 4e" (cb=16)
00:00:00.962 
00:00:00.962 [/Devices/] (level 1)
00:00:00.962 
00:00:00.962 [/Devices/8237A/] (level 2)
00:00:00.962 
00:00:00.962 [/Devices/8237A/0/] (level 3)
00:00:00.962   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.962 
00:00:00.962 [/Devices/AudioSniffer/] (level 2)
00:00:00.963 
00:00:00.963 [/Devices/AudioSniffer/0/] (level 3)
00:00:00.963 
00:00:00.963 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:00.963 
00:00:00.963 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:00.963   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:00.963 
00:00:00.963 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:00.963   Object <integer> = 0x00000000097c56c8 (159143624)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/] (level 2)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/0/] (level 3)
00:00:00.963   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:00.963   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.963   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/0/Config/] (level 4)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:00.963   Driver <string>  = "HGCM" (cb=5)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:00.963   Object <integer> = 0x00000000097c6560 (159147360)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:00.963   Driver <string>  = "MainStatus" (cb=11)
00:00:00.963 
00:00:00.963 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:00.963   First   <integer> = 0x0000000000000000 (0)
00:00:00.963   Last    <integer> = 0x0000000000000000 (0)
00:00:00.963   papLeds <integer> = 0x00000000097c59b0 (159144368)
00:00:00.963 
00:00:00.963 [/Devices/acpi/] (level 2)
00:00:00.963 
00:00:00.963 [/Devices/acpi/0/] (level 3)
00:00:00.963   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:00.963   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.963   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.963 
00:00:00.963 [/Devices/acpi/0/Config/] (level 4)
00:00:00.963   FdcEnabled  <integer> = 0x0000000000000001 (1)
00:00:00.963   HpetEnabled <integer> = 0x0000000000000000 (0)
00:00:00.963   IOAPIC      <integer> = 0x0000000000000000 (0)
00:00:00.963   NumCPUs     <integer> = 0x0000000000000001 (1)
00:00:00.963   RamHoleSize <integer> = 0x0000000020000000 (536870912)
00:00:00.963   RamSize     <integer> = 0x0000000018000000 (402653184)
00:00:00.963   ShowCpu     <integer> = 0x0000000000000000 (0)
00:00:00.963   ShowRtc     <integer> = 0x0000000000000000 (0)
00:00:00.963 
00:00:00.963 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:00.963   Driver <string>  = "ACPIHost" (cb=9)
00:00:00.963 
00:00:00.963 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:00.963 
00:00:00.963 [/Devices/apic/] (level 2)
00:00:00.963 
00:00:00.963 [/Devices/apic/0/] (level 3)
00:00:00.963   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.963 
00:00:00.963 [/Devices/apic/0/Config/] (level 4)
00:00:00.963   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:00.963   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:00.963 
00:00:00.963 [/Devices/e1000/] (level 2)
00:00:00.963 
00:00:00.963 [/Devices/i82078/] (level 2)
00:00:00.964 
00:00:00.964 [/Devices/i82078/0/] (level 3)
00:00:00.964   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.964 
00:00:00.964 [/Devices/i82078/0/Config/] (level 4)
00:00:00.964   DMA       <integer> = 0x0000000000000002 (2)
00:00:00.964   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:00.964   IRQ       <integer> = 0x0000000000000006 (6)
00:00:00.964   MemMapped <integer> = 0x0000000000000000 (0)
00:00:00.964 
00:00:00.964 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:00.964   Driver <string>  = "Block" (cb=6)
00:00:00.964 
00:00:00.964 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:00.964   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.964   Type      <string>  = "Floppy 1.44" (cb=12)
00:00:00.964 
00:00:00.964 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:00.964   Driver <string>  = "MainStatus" (cb=11)
00:00:00.964 
00:00:00.964 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:00.964   First   <integer> = 0x0000000000000000 (0)
00:00:00.964   Last    <integer> = 0x0000000000000000 (0)
00:00:00.964   papLeds <integer> = 0x00000000097c58c0 (159144128)
00:00:00.964 
00:00:00.964 [/Devices/i8254/] (level 2)
00:00:00.964 
00:00:00.964 [/Devices/i8254/0/] (level 3)
00:00:00.964 
00:00:00.964 [/Devices/i8254/0/Config/] (level 4)
00:00:00.964 
00:00:00.964 [/Devices/i8259/] (level 2)
00:00:00.964 
00:00:00.964 [/Devices/i8259/0/] (level 3)
00:00:00.964   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.964 
00:00:00.964 [/Devices/i8259/0/Config/] (level 4)
00:00:00.964 
00:00:00.964 [/Devices/ichac97/] (level 2)
00:00:00.964 
00:00:00.964 [/Devices/ichac97/0/] (level 3)
00:00:00.964   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:00.964   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.964   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.964 
00:00:00.964 [/Devices/ichac97/0/Config/] (level 4)
00:00:00.964 
00:00:00.964 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:00.964   Driver <string>  = "AUDIO" (cb=6)
00:00:00.964 
00:00:00.964 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:00.964   AudioDriver <string>  = "pulse" (cb=6)
00:00:00.964   StreamName  <string>  = "bt4" (cb=4)
00:00:00.964 
00:00:00.964 [/Devices/mc146818/] (level 2)
00:00:00.964 
00:00:00.964 [/Devices/mc146818/0/] (level 3)
00:00:00.964 
00:00:00.964 [/Devices/mc146818/0/Config/] (level 4)
00:00:00.964 
00:00:00.964 [/Devices/parallel/] (level 2)
00:00:00.964 
00:00:00.964 [/Devices/pcarch/] (level 2)
00:00:00.965 
00:00:00.965 [/Devices/pcarch/0/] (level 3)
00:00:00.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.965 
00:00:00.965 [/Devices/pcarch/0/Config/] (level 4)
00:00:00.965 
00:00:00.965 [/Devices/pcbios/] (level 2)
00:00:00.965 
00:00:00.965 [/Devices/pcbios/0/] (level 3)
00:00:00.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.965 
00:00:00.965 [/Devices/pcbios/0/Config/] (level 4)
00:00:00.965   BootDevice0    <string>  = "FLOPPY" (cb=7)
00:00:00.965   BootDevice1    <string>  = "DVD" (cb=4)
00:00:00.965   BootDevice2    <string>  = "IDE" (cb=4)
00:00:00.965   BootDevice3    <string>  = "NONE" (cb=5)
00:00:00.965   FloppyDevice   <string>  = "i82078" (cb=7)
00:00:00.965   HardDiskDevice <string>  = "piix3ide" (cb=9)
00:00:00.965   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:00.965   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:00.965   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:00.965   RamHoleSize    <integer> = 0x0000000020000000 (536870912)
00:00:00.965   RamSize        <integer> = 0x0000000018000000 (402653184)
00:00:00.965   UUID           <bytes>   = "b4 25 b6 a3 01 4a c5 4f b9 91 a3 26 a4 b2 3d 4e" (cb=16)
00:00:00.965 
00:00:00.965 [/Devices/pci/] (level 2)
00:00:00.965 
00:00:00.965 [/Devices/pci/0/] (level 3)
00:00:00.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.965 
00:00:00.965 [/Devices/pci/0/Config/] (level 4)
00:00:00.965   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/] (level 2)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/] (level 3)
00:00:00.965   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/Config/] (level 4)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:00.965   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.965   Driver <string>  = "MainKeyboard" (cb=13)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.965   Object <integer> = 0x00000000097c5c98 (159145112)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:00.965   QueueSize <integer> = 0x0000000000000040 (64)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:00.965   Driver <string>  = "MouseQueue" (cb=11)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:00.965   Driver <string>  = "MainMouse" (cb=10)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:00.965   Object <integer> = 0x00000000097c5d70 (159145328)
00:00:00.965 
00:00:00.965 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:00.965   QueueSize <integer> = 0x0000000000000080 (128)
00:00:00.965 
00:00:00.965 [/Devices/pcnet/] (level 2)
00:00:00.966 
00:00:00.966 [/Devices/pcnet/0/] (level 3)
00:00:00.966   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.966   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.966 
00:00:00.966 [/Devices/pcnet/0/Config/] (level 4)
00:00:00.966   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:00.966   CableConnected <integer> = 0x0000000000000001 (1)
00:00:00.966   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:00.966   MAC            <bytes>   = "08 00 27 73 8b 47" (cb=6)
00:00:00.966 
00:00:00.966 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:00.966   Driver <string>  = "NAT" (cb=4)
00:00:00.966 
00:00:00.966 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:00.966   BootFile   <string>  = "bt4.pxe" (cb=8)
00:00:00.966   TFTPPrefix <string>  = "/home/h3lmy/.VirtualBox/TFTP" (cb=29)
00:00:00.966 
00:00:00.966 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:00.966   Driver <string>  = "MainStatus" (cb=11)
00:00:00.966 
00:00:00.966 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:00.966   papLeds <integer> = 0x00000000097c5990 (159144336)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/] (level 2)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/] (level 3)
00:00:00.966   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:00.966   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:00.966   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/Config/] (level 4)
00:00:00.966   Type <string>  = "PIIX4" (cb=6)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:00.966   Driver <string>  = "Block" (cb=6)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.966   Driver <string>  = "VD" (cb=3)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.966   Format <string>  = "VDI" (cb=4)
00:00:00.966   Path   <string>  = "/media/Data/Virtual-OS/bt4.vdi" (cb=31)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:00.966   Mountable <integer> = 0x0000000000000000 (0)
00:00:00.966   Type      <string>  = "HardDisk" (cb=9)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:00.966   Driver <string>  = "Block" (cb=6)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#2/AttachedDriver/] (level 5)
00:00:00.966   Driver <string>  = "VD" (cb=3)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#2/AttachedDriver/Config/] (level 6)
00:00:00.966   Format   <string>  = "RAW" (cb=4)
00:00:00.966   Path     <string>  = "/media/Data/ISO_Files/bt4-pre-final.iso" (cb=40)
00:00:00.966   ReadOnly <integer> = 0x0000000000000001 (1)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:00.966   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.966   Type      <string>  = "DVD" (cb=4)
00:00:00.966 
00:00:00.966 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:00.967   Driver <string>  = "MainStatus" (cb=11)
00:00:00.967 
00:00:00.967 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:00.967   First   <integer> = 0x0000000000000000 (0)
00:00:00.967   Last    <integer> = 0x0000000000000003 (3)
00:00:00.967   papLeds <integer> = 0x00000000097c58c8 (159144136)
00:00:00.967 
00:00:00.967 [/Devices/serial/] (level 2)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/] (level 2)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/0/] (level 3)
00:00:00.967   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:00.967   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.967   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:00.967   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:00.967   Driver <string>  = "MainStatus" (cb=11)
00:00:00.967 
00:00:00.967 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:00.967   First   <integer> = 0x0000000000000000 (0)
00:00:00.967   Last    <integer> = 0x0000000000000000 (0)
00:00:00.967   papLeds <integer> = 0x00000000097c59b8 (159144376)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/] (level 2)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/0/] (level 3)
00:00:00.967   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:00.967   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.967   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:00.967   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:00.967   Driver <string>  = "MainStatus" (cb=11)
00:00:00.967 
00:00:00.967 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:00.967   First   <integer> = 0x0000000000000000 (0)
00:00:00.967   Last    <integer> = 0x0000000000000000 (0)
00:00:00.967   papLeds <integer> = 0x00000000097c59b4 (159144372)
00:00:00.967 
00:00:00.967 [/Devices/vga/] (level 2)
00:00:00.967 
00:00:00.967 [/Devices/vga/0/] (level 3)
00:00:00.967   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:00.967   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.967   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.967 
00:00:00.967 [/Devices/vga/0/Config/] (level 4)
00:00:00.967   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:00.967   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:00.967   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:00.968   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:00.968   LogoFile         <string>  = "" (cb=1)
00:00:00.968   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:00.968   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:00.968   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:00.968   VRamSize         <integer> = 0x0000000000c00000 (12582912)
00:00:00.968 
00:00:00.968 [/Devices/vga/0/LUN#0/] (level 4)
00:00:00.968   Driver <string>  = "MainDisplay" (cb=12)
00:00:00.968 
00:00:00.968 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:00.968   Object <integer> = 0x00000000097c5e48 (159145544)
00:00:00.968 
00:00:00.968 [/Devices/virtio-net/] (level 2)
00:00:00.968 
00:00:00.968 [/HWVirtExt/] (level 1)
00:00:00.968   64bitEnabled       <integer> = 0x0000000000000000 (0)
00:00:00.968   EnableNestedPaging <integer> = 0x0000000000000000 (0)
00:00:00.968   EnableVPID         <integer> = 0x0000000000000000 (0)
00:00:00.968   Enabled            <integer> = 0x0000000000000001 (1)
00:00:00.968   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:00.968 
00:00:00.968 [/PDM/] (level 1)
00:00:00.968 
00:00:00.968 [/PDM/Drivers/] (level 2)
00:00:00.968 
00:00:00.968 [/PDM/Drivers/VBoxC/] (level 3)
00:00:00.968   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:00.968 
00:00:00.968 [/TM/] (level 1)
00:00:00.968   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:00.968 
00:00:00.968 ********************* End of CFGM dump **********************
00:00:00.968 MM: cbHyperHeap=0x140000 (1310720)
00:00:00.969 Logical host processors: 2, processor active mask: 0000000000000003
00:00:00.969 ************************* CPUID dump ************************
00:00:00.969          RAW Standard CPUIDs
00:00:00.969      Function  eax      ebx      ecx      edx
00:00:00.969 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:00.969 Hst:           00000006 756e6547 6c65746e 49656e69
00:00:00.969 Gst: 00000001  00000f64 00000800 00000009 078bf1bf
00:00:00.969 Hst:           00000f64 01020800 0000e49d bfebfbff
00:00:00.969 Gst: 00000002  605b5101 00000000 00000000 007d7040
00:00:00.969 Hst:           605b5101 00000000 00000000 007d7040
00:00:00.969 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:00.969 Hst:           00000000 00000000 00000000 00000000
00:00:00.969 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:00.969 Hst:           04000121 01c0003f 0000001f 00000000
00:00:00.969 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:00.969 Hst:           00000040 00000040 00000000 00000000
00:00:00.969 Name:                            GenuineIntel
00:00:00.969 Supports:                        0-5
00:00:00.969 Family:                          15  	Extended: 0 	Effective: 15
00:00:00.969 Model:                           6  	Extended: 0 	Effective: 6
00:00:00.969 Stepping:                        4
00:00:00.969 Type:                            0
00:00:00.969 APIC ID:                         0x00
00:00:00.969 Logical CPUs:                    0
00:00:00.969 CLFLUSH Size:                    8
00:00:00.969 Brand ID:                        0x00
00:00:00.969 Mnemonic - Description                 = guest (host)
00:00:00.970 FPU - x87 FPU on Chip                  = 1 (1)
00:00:00.970 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:00.970 DE - Debugging extensions              = 1 (1)
00:00:00.970 PSE - Page Size Extension              = 1 (1)
00:00:00.970 TSC - Time Stamp Counter               = 1 (1)
00:00:00.970 MSR - Model Specific Registers         = 1 (1)
00:00:00.970 PAE - Physical Address Extension       = 0 (1)
00:00:00.970 MCE - Machine Check Exception          = 1 (1)
00:00:00.970 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:00.970 APIC - APIC On-Chip                    = 0 (1)
00:00:00.970 Reserved                               = 0 (0)
00:00:00.970 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:00.970 MTRR - Memory Type Range Registers     = 1 (1)
00:00:00.970 PGE - PTE Global Bit                   = 1 (1)
00:00:00.970 MCA - Machine Check Architecture       = 1 (1)
00:00:00.970 CMOV - Conditional Move Instructions   = 1 (1)
00:00:00.970 PAT - Page Attribute Table             = 1 (1)
00:00:00.970 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:00.970 PSN - Processor Serial Number          = 0 (0)
00:00:00.970 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:00.970 Reserved                               = 0 (0)
00:00:00.970 DS - Debug Store                       = 0 (1)
00:00:00.970 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:00.970 MMX - Intel MMX Technology             = 1 (1)
00:00:00.970 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:00.970 SSE - SSE Support                      = 1 (1)
00:00:00.970 SSE2 - SSE2 Support                    = 1 (1)
00:00:00.970 SS - Self Snoop                        = 0 (1)
00:00:00.970 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:00.970 TM - Thermal Monitor                   = 0 (1)
00:00:00.970 30 - Reserved                          = 0 (0)
00:00:00.970 PBE - Pending Break Enable             = 0 (1)
00:00:00.970 Supports SSE3 or not                   = 1 (1)
00:00:00.970 Reserved                               = 0 (0)
00:00:00.970 DS Area 64-bit layout                  = 0 (1)
00:00:00.970 Supports MONITOR/MWAIT                 = 1 (1)
00:00:00.970 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:00.970 VMX - Virtual Machine Technology       = 0 (0)
00:00:00.970 SMX - Safer Mode Extensions            = 0 (0)
00:00:00.970 Enhanced SpeedStep Technology          = 0 (1)
00:00:00.970 Terminal Monitor 2                     = 0 (0)
00:00:00.970 Supports Supplemental SSE3 or not      = 0 (0)
00:00:00.970 L1 Context ID                          = 0 (1)
00:00:00.970 FMA                                    = 0 (0)
00:00:00.970 Reserved                               = 0 (0)
00:00:00.970 CMPXCHG16B                             = 0 (1)
00:00:00.970 xTPR Update Control                    = 0 (1)
00:00:00.970 Perf/Debug Capability MSR              = 0 (1)
00:00:00.970 Reserved                               = 0x0 (0x0)
00:00:00.970 Direct Cache Access                    = 0 (0)
00:00:00.970 Supports SSE4_1 or not                 = 0 (0)
00:00:00.970 Supports SSE4_2 or not                 = 0 (0)
00:00:00.970 Supports the x2APIC extensions         = 0 (0)
00:00:00.970 Supports MOVBE                         = 0 (0)
00:00:00.970 Supports POPCNT                        = 0 (0)
00:00:00.970 Reserved                               = 0x0 (0x0)
00:00:00.970 Supports XSAVE                         = 0 (0)
00:00:00.970 Supports OSXSAVE                       = 0 (0)
00:00:00.970 Reserved                               = 0x0 (0x0)
00:00:00.970 
00:00:00.970          RAW Extended CPUIDs
00:00:00.970      Function  eax      ebx      ecx      edx
00:00:00.970 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:00.970 Hst:           80000008 00000000 00000000 00000000
00:00:00.970 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:00.970 Hst:           00000000 00000000 00000001 20100000
00:00:00.970 Gst: 80000002  20202020 20202020 20202020 6e492020
00:00:00.970 Hst:           20202020 20202020 20202020 6e492020
00:00:00.970 Gst: 80000003  286c6574 50202952 69746e65 52286d75
00:00:00.970 Hst:           286c6574 50202952 69746e65 52286d75
00:00:00.970 Gst: 80000004  20442029 20555043 30342e33 007a4847
00:00:00.970 Hst:           20442029 20555043 30342e33 007a4847
00:00:00.970 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:00.970 Hst:           00000000 00000000 00000000 00000000
00:00:00.970 Gst: 80000006  00000000 00000000 08006040 00000000
00:00:00.970 Hst:           00000000 00000000 08006040 00000000
00:00:00.970 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:00.970 Hst:           00000000 00000000 00000000 00000000
00:00:00.970 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:00.970 Hst:           00003024 00000000 00000000 00000000
00:00:00.970 Gst: 80000009  00000000 00000000 00000000 00000000*
00:00:00.970 Hst:           00000000 00000000 00000000 00000000
00:00:00.970 Ext Name:                        
00:00:00.970 Ext Supports:                    0x80000000-0x80000008
00:00:00.970 Family:                          0  	Extended: 0 	Effective: 0
00:00:00.970 Model:                           0  	Extended: 0 	Effective: 0
00:00:00.970 Stepping:                        0
00:00:00.970 Brand ID:                        0x000
00:00:00.970 Mnemonic - Description                 = guest (host)
00:00:00.970 FPU - x87 FPU on Chip                  = 0 (0)
00:00:00.970 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:00.970 DE - Debugging extensions              = 0 (0)
00:00:00.970 PSE - Page Size Extension              = 0 (0)
00:00:00.970 TSC - Time Stamp Counter               = 0 (0)
00:00:00.970 MSR - K86 Model Specific Registers     = 0 (0)
00:00:00.970 PAE - Physical Address Extension       = 0 (0)
00:00:00.970 MCE - Machine Check Exception          = 0 (0)
00:00:00.970 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:00.970 APIC - APIC On-Chip                    = 0 (0)
00:00:00.970 10 - Reserved                          = 0 (0)
00:00:00.970 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:00.970 MTRR - Memory Type Range Registers     = 0 (0)
00:00:00.970 PGE - PTE Global Bit                   = 0 (0)
00:00:00.970 MCA - Machine Check Architecture       = 0 (0)
00:00:00.970 CMOV - Conditional Move Instructions   = 0 (0)
00:00:00.970 PAT - Page Attribute Table             = 0 (0)
00:00:00.970 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:00.970 18 - Reserved                          = 0 (0)
00:00:00.970 19 - Reserved                          = 0 (0)
00:00:00.970 NX - No-Execute Page Protection        = 0 (1)
00:00:00.970 DS - Debug Store                       = 0 (0)
00:00:00.970 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:00.970 MMX - Intel MMX Technology             = 0 (0)
00:00:00.970 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:00.970 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:00.970 26 - 1 GB large page support           = 0 (0)
00:00:00.970 27 - RDTSCP instruction                = 0 (0)
00:00:00.970 28 - Reserved                          = 0 (0)
00:00:00.970 29 - AMD Long Mode                     = 0 (1)
00:00:00.970 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:00.970 31 - AMD 3DNow                         = 0 (0)
00:00:00.970 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:00.970 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:00.970 SVM - AMD VM Extensions                = 0 (0)
00:00:00.970 APIC registers starting at 0x400       = 0 (0)
00:00:00.970 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:00.970 Advanced bit manipulation              = 0 (0)
00:00:00.970 SSE4A instruction support              = 0 (0)
00:00:00.970 Misaligned SSE mode                    = 0 (0)
00:00:00.970 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:00.970 OS visible workaround                  = 0 (0)
00:00:00.970 Instruction based sampling             = 0 (0)
00:00:00.970 SSE5 support                           = 0 (0)
00:00:00.970 SKINIT, STGI, and DEV support          = 0 (0)
00:00:00.970 Watchdog timer support.                = 0 (0)
00:00:00.970 31:14 - Reserved                       = 0x0 (0x0)
00:00:00.970 Full Name:                                     Intel(R) Pentium(R) D CPU 3.40GHz
00:00:00.970 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:00.970 TLB 2/4M Data:                   res0     0 entries
00:00:00.971 TLB 4K Instr/Uni:                res0     0 entries
00:00:00.971 TLB 4K Data:                     res0     0 entries
00:00:00.971 L1 Instr Cache Line Size:        0 bytes
00:00:00.971 L1 Instr Cache Lines Per Tag:    0
00:00:00.971 L1 Instr Cache Associativity:    res0  
00:00:00.971 L1 Instr Cache Size:             0 KB
00:00:00.971 L1 Data Cache Line Size:         0 bytes
00:00:00.971 L1 Data Cache Lines Per Tag:     0
00:00:00.971 L1 Data Cache Associativity:     res0  
00:00:00.971 L1 Data Cache Size:              0 KB
00:00:00.971 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:00.971 L2 TLB 2/4M Data:                off       0 entries
00:00:00.971 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:00.971 L2 TLB 4K Data:                  off       0 entries
00:00:00.971 L2 Cache Line Size:              0 bytes
00:00:00.971 L2 Cache Lines Per Tag:          0
00:00:00.971 L2 Cache Associativity:          off   
00:00:00.971 L2 Cache Size:                   0 KB
00:00:00.971 APM Features:                   
00:00:00.971 Physical Address Width:          36 bits
00:00:00.971 Virtual Address Width:           48 bits
00:00:00.971 Physical Core Count:             0
00:00:00.971 
00:00:00.971          RAW Centaur CPUIDs
00:00:00.971      Function  eax      ebx      ecx      edx
00:00:00.971 Gst: c0000000  00000000 00000000 00000000 00000000
00:00:00.971 Hst:           00000000 00000000 00000000 00000000
00:00:00.971 Gst: c0000001  00000000 00000000 00000000 00000000*
00:00:00.971 Hst:           00000000 00000000 00000000 00000000
00:00:00.971 Gst: c0000002  00000000 00000000 00000000 00000000*
00:00:00.971 Hst:           00000000 00000000 00000000 00000000
00:00:00.971 Gst: c0000003  00000000 00000000 00000000 00000000*
00:00:00.971 Hst:           00000000 00000000 00000000 00000000
00:00:00.971 Centaur Supports:                0xc0000000-0x00000000
00:00:00.971 
00:00:00.971 ******************** End of CPUID dump **********************
00:00:00.991 REM: VBoxREM32
00:00:00.996 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:01.028 TM: cTSCTicksPerSecond=0xc9d764f9 (3 386 336 505) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:01.028 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:01.028 CoreCode: R3=008c8000 R0=f8290000 RC=a0345000 Phys=0000000031bd2000 cb=0x2000
00:00:01.055 AIOMgr: Cache successfully initialised. Cache size is 5242880 bytes
00:00:01.105 [SMP] BIOS with 1 CPUs
00:00:01.126 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf8b63060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:01.139 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf82aa060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:01.139 Activating Local APIC
00:00:01.139 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:01.139 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:01.139 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.155 Shared Folders service loaded.
00:00:01.192 VDInit finished
00:00:01.193 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 16777216
00:00:01.193 PIIX3 ATA: LUN#1: no unit
00:00:01.193 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 680484, passthrough disabled
00:00:01.193 PIIX3 ATA: LUN#3: no unit
00:00:01.193 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.193 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:01.195 NAT: value of BindIP has been ignored
00:00:01.195 Audio: Trying driver 'pulse'.
00:00:01.203 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:01.203 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:01.223 Pulse: buffer settings: max=26460 tlength=17640 prebuf=15876 minreq=1764
00:00:01.223 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:01.305 Pulse: buffer settings: max=26460 tlength=17640 prebuf=15876 minreq=1764
00:00:01.307 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:01.307 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:01.320 HWACCM: No VT-x or AMD-V CPU extension found. Reason VERR_VMX_NO_VMX
00:00:01.320 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=0
00:00:01.335 VM: Halt method global1 (5)
00:00:01.335 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:01.336 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:01.336 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:01.344 Guest Log: BIOS: VirtualBox 3.1.2
00:00:01.344 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.402 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.403 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:01.406 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:01.407 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.407 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.407 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:01.412 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:03.885 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.887 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:03.888 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:03.907 Guest Log: BIOS: Booting from CD-ROM...
00:00:03.947 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=81
00:00:03.948 Guest Log: BIOS: int13_harddisk: function 08, unmapped device for ELDL=81
00:00:04.058 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=640 h=480 bpp=0 cbLine=0x140
00:00:11.380 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:14.966 Guest Log: BIOS: KBD: unsupported int 16h function 03
00:00:14.969 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=81
00:00:14.969 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=81
00:00:14.969 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=82
00:00:14.970 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=82
00:00:14.970 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=83
00:00:14.970 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=83
00:00:14.970 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=84
00:00:14.970 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=84
00:00:14.970 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=85
00:00:14.971 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=85
00:00:14.971 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=86
00:00:14.971 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=86
00:00:14.971 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=87
00:00:14.971 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=87
00:00:14.972 Guest Log: BIOS: int13_harddisk: function 41, ELDL out of range 8c
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 02, ELDL out of range 8c
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 41, ELDL out of range 8d
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 02, ELDL out of range 8d
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 41, ELDL out of range 8e
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 02, ELDL out of range 8e
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 41, ELDL out of range 8f
00:00:14.973 Guest Log: BIOS: int13_harddisk: function 02, ELDL out of range 8f
00:00:15.008 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=1024 h=768 bpp=16 cbLine=0x800
00:00:17.365 PIT: mode=2 count=0xf89 (3977) - 300.02 Hz (ch=0)
00:00:17.866 PIT: mode=0 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:22.043 EHCI: Hardware reset
00:00:22.043 EHCI: Hardware reset
00:00:22.043 EHCI: USB Operational
00:00:22.124 OHCI: Software reset
00:00:22.124 OHCI: USB Operational
00:00:22.786 PATM: Disable block at c0954739 - write c09547a2-c09547a6
00:00:22.787 PATM: Disable block at c095544f - write c09554b5-c09554b9
00:00:22.789 PATM: Disable block at c096962a - write c0969647-c096964b
00:00:22.790 PATM: Disable block at c097b310 - write c097b36d-c097b371
00:00:23.340 OHCI: USB Suspended
00:01:01.966 Audio: set_record_source ars=0 als=0 (not implemented)
00:01:01.967 Audio: set_record_source ars=0 als=0 (not implemented)
00:01:01.981 Audio: set_record_source ars=0 als=0 (not implemented)
00:03:04.462 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=800 h=600 bpp=32 cbLine=0xC80
00:34:44.848 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=1024 h=768 bpp=16 cbLine=0x1000
00:34:46.875 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=1024 h=768 bpp=16 cbLine=0x800
00:35:07.148 EHCI: USB Suspended
00:35:07.148 OHCI: USB Reset
00:35:07.159 Changing the VM state from 'RUNNING' to 'RESETTING'.
00:35:07.235 CPUMSetGuestCpuIdFeature: Enabled APIC
00:35:07.235 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:35:07.235 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:35:07.250 Audio: set_record_source ars=0 als=0 (not implemented)
00:35:07.250 PIIX3 ATA: Ctl#1: finished processing RESET
00:35:07.250 PIIX3 ATA: Ctl#0: finished processing RESET
00:35:07.250 Changing the VM state from 'RESETTING' to 'RUNNING'.
00:35:07.253 Guest Log: BIOS: VirtualBox 3.1.2
00:35:07.253 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:35:07.305 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0xe7 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:35:07.305 PIIX3 ATA: Ctl#0: finished processing RESET
00:35:07.307 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:35:07.309 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:35:07.309 PIIX3 ATA: Ctl#1: finished processing RESET
00:35:07.310 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:35:07.321 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b47af000 w=640 h=480 bpp=32 cbLine=0xA00
00:35:08.017 Changing the VM state from 'RUNNING' to 'SUSPENDING'.
00:35:08.018 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.
00:35:09.734 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:35:09.734 Changing the VM state from 'SUSPENDED' to 'POWERING_OFF'.
00:35:09.734 ****************** Guest state at power off ******************
00:35:09.743 Guest CPUM (VCPU 0) state: se
00:35:09.743 eax=00000000 ebx=00000000 ecx=00120004 edx=00000012 esi=fee00360 edi=0000ffd8
00:35:09.743 eip=00001180 esp=0000ffc8 ebp=0000ffdc iopl=0         nv up ei nt zr ac po cy
00:35:09.743 cs={f000 base=00000000000f0000 limit=0000ffff flags=0000009a} dr0=00000000 dr1=00000000
00:35:09.743 ds={0000 base=0000000000000000 limit=0000ffff flags=00000092} dr2=00000000 dr3=00000000
00:35:09.743 es={0080 base=0000000000000800 limit=0000ffff flags=00000092} dr4=00000000 dr5=00000000
00:35:09.743 fs={0000 base=0000000000000000 limit=0000ffff flags=00000092} dr6=ffff0ff0 dr7=00000400
00:35:09.743 gs={0000 base=0000000000000000 limit=0000ffff flags=00000092} cr0=60000010 cr2=00000000
00:35:09.743 ss={0000 base=0000000000000000 limit=0000ffff flags=00000092} cr3=00000000 cr4=00000000
00:35:09.743 gdtr=00000000000fc81f:0030  idtr=0000000000000000:ffff  eflags=00000297
00:35:09.743 ldtr={0000 base=00000000 limit=0000ffff flags=00000082}
00:35:09.743 tr  ={0000 base=00000000 limit=0000ffff flags=00000083}
00:35:09.743 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:35:09.743 FCW=037f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001f80 MXCSR_MASK=00000000
00:35:09.743 FPUIP=00000000 CS=0000 Rsvrd1=0000  FPUDP=00000000 DS=0000 Rsvrd2=0000
00:35:09.743 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:35:09.743 XMM0 =00000000'00000000'00000000'00000000  XMM1 =00000000'00000000'00000000'00000000
00:35:09.743 XMM2 =00000000'00000000'00000000'00000000  XMM3 =00000000'00000000'00000000'00000000
00:35:09.743 XMM4 =00000000'00000000'00000000'00000000  XMM5 =00000000'00000000'00000000'00000000
00:35:09.743 XMM6 =00000000'00000000'00000000'00000000  XMM7 =00000000'00000000'00000000'00000000
00:35:09.743 XMM8 =00000000'00000000'00000000'00000000  XMM9 =00000000'00000000'00000000'00000000
00:35:09.743 XMM10=00000000'00000000'00000000'00000000  XMM11=00000000'00000000'00000000'00000000
00:35:09.743 XMM12=00000000'00000000'00000000'00000000  XMM13=00000000'00000000'00000000'00000000
00:35:09.743 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
00:35:09.743 EFER         =0000000000000000
00:35:09.743 PAT          =0007040600070406
00:35:09.743 STAR         =0000000000000000
00:35:09.743 CSTAR        =0000000000000000
00:35:09.743 LSTAR        =0000000000000000
00:35:09.743 SFMASK       =0000000000000000
00:35:09.743 KERNELGSBASE =0000000000000000
00:35:09.743 ***
00:35:09.743 Guest paging mode:  Real, changed 3 times, A20 enabled
00:35:09.743 Shadow paging mode: 32-bit
00:35:09.743 Host paging mode:   32-bit+G
00:35:09.743 ***
00:35:09.743 Active Timers (pVM=b5bb6000)
00:35:09.743 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:35:09.743 01865200 00008460 00000000 00000000 Real  000000000003745909 000000000003744192 2-ACTIVE                  VGA Refresh Timer
00:35:09.743 0186d660 00000000 ffff7ba0 00000000 Real  000000000003745909 000000000003744206 2-ACTIVE                  EMT Yielder
00:35:09.743 018699e0 00000000 00000000 00000000 Virt  000002106680950126 000002106690299579 2-ACTIVE                  Audio timer
00:35:09.743 018536b0 000003a0 00000000 00000000 VrSy  000002106673785606 000002106689410213 2-ACTIVE                  i8254 Programmable Interval Timer
00:35:09.743 01853a50 00019230 fffffc60 00000000 VrSy  000002106673785606 000002106990000000 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:35:09.743 0186cc80 00000000 fffe6dd0 00000000 VrSy  000002106673785606 000003305776265643 2-ACTIVE                  ACPI Timer
00:35:09.743 ***
00:35:09.743 Shadow GDT (GCAddr=fef48000):
00:35:09.743 0030 - 76b0ffff b7dff3f2 - base=b7f276b0 limit=ffffffff dpl=3 DataRW Accessed Present Page 32-bit 
00:35:09.743 0060 - 0000ffff 00cfbb00 - base=00000000 limit=ffffffff dpl=1 CodeER Accessed Present Page 32-bit 
00:35:09.743 0068 - 0000ffff 00cfb300 - base=00000000 limit=ffffffff dpl=1 DataRW Accessed Present Page 32-bit 
00:35:09.743 0070 - 0000ffff 00cffb00 - base=00000000 limit=ffffffff dpl=3 CodeER Accessed Present Page 32-bit 
00:35:09.743 0078 - 0000ffff 00cff300 - base=00000000 limit=ffffffff dpl=3 DataRW Accessed Present Page 32-bit 
00:35:09.743 0090 - 0000ffff 0040bb00 - base=00000000 limit=0000ffff dpl=1 CodeER Accessed Present 32-bit 
00:35:09.743 0098 - 0000ffff 0000bb00 - base=00000000 limit=0000ffff dpl=1 CodeER Accessed Present 16-bit 
00:35:09.743 00a0 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:35:09.744 00a8 - 00000000 0000b300 - base=00000000 limit=00000000 dpl=1 DataRW Accessed Present 16-bit 
00:35:09.744 00b0 - 00000000 0000b300 - base=00000000 limit=00000000 dpl=1 DataRW Accessed Present 16-bit 
00:35:09.744 00b8 - 0000ffff 0040bb00 - base=00000000 limit=0000ffff dpl=1 CodeER Accessed Present 32-bit 
00:35:09.744 00c0 - 0000ffff 0000bb00 - base=00000000 limit=0000ffff dpl=1 CodeER Accessed Present 16-bit 
00:35:09.744 00c8 - 0000ffff 0040b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 32-bit 
00:35:09.744 00d0 - 00000000 00c0b300 - base=00000000 limit=00000fff dpl=1 DataRW Accessed Present Page 32-bit 
00:35:09.744 00d8 - a000ffff 008fb395 - base=0095a000 limit=ffffffff dpl=1 DataRW Accessed Present Page 16-bit 
00:35:09.744 ffd8 - 80d80087 fe0089c0 - base=fec080d8 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:35:09.744 ffe0 - 80500087 fe008bc0 - base=fec08050 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:35:09.744 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:35:09.744 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:35:09.744 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:35:09.744 ***
00:35:09.744 ***
00:35:09.744 ss:sp=0000:ffc8 0000:ffc0 TO 0000:100bf:
00:35:09.744 b5d6f13c 0000: 1a 11 00 f0 46 02 2e 12-86 02 00 00 84 bd 12 00 ....F...........
00:35:09.749 b5d6f14c 0010: 84 bd 12 00 01 00 00 00-61 00 00 00 f4 ff 93 15 ........a.......
00:35:09.749 b5d6f15c 0020: 7d 00 01 00 d0 07 00 02-01 01 00 00 11 00 bb 66 }..............f
00:35:09.749 b5d6f16c 0030: 00 00 c0 9f fa ff ff 17-00 00 f6 ff 9b e2 00 00 ................
00:35:09.749 b5d6f17c 0040: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f18c 0050: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f19c 0060: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1ac 0070: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1bc 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1cc 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1dc 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1ec 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1fc 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f20c 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f21c 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f22c 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 2000:0000 TO 2000:01ff:
00:35:09.749 b5d6f13c 0000: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f14c 0010: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f15c 0020: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f16c 0030: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f17c 0040: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f18c 0050: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f19c 0060: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1ac 0070: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1bc 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1cc 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1dc 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1ec 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f1fc 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f20c 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f21c 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f22c 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.749 b5d6f23c 0100: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f24c 0110: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f25c 0120: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f26c 0130: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f27c 0140: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f28c 0150: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f29c 0160: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f2ac 0170: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f2bc 0180: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f2cc 0190: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f2dc 01a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f2ec 01b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f2fc 01c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f30c 01d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f31c 01e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 b5d6f32c 01f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:35:09.750 ************** End of Guest state at power off ***************
00:35:09.750 Changing the VM state from 'POWERING_OFF' to 'OFF'.
00:35:09.903 Changing the VM state from 'OFF' to 'DESTROYING'.
00:35:09.903 ************************* Statistics *************************
00:35:09.903 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
00:35:09.903 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
00:35:09.903 /Devices/IDE0/ATA0/Unit0/DMA       104506 times
00:35:09.903 /Devices/IDE0/ATA0/Unit0/PIO           41 times
00:35:09.903 /Devices/IDE0/ATA0/Unit0/ReadBytes 458192384 bytes
00:35:09.903 /Devices/IDE0/ATA0/Unit0/WrittenBytes 5602550784 bytes
00:35:09.903 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
00:35:09.903 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
00:35:09.903 /Devices/IDE0/ATA0/Unit1/DMA            0 times
00:35:09.903 /Devices/IDE0/ATA0/Unit1/PIO            0 times
00:35:09.903 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
00:35:09.903 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
00:35:09.903 /Devices/IDE0/ATA1/Unit0/AtapiDMA    82822 times
00:35:09.903 /Devices/IDE0/ATA1/Unit0/AtapiPIO      544 times
00:35:09.903 /Devices/IDE0/ATA1/Unit0/DMA            0 times
00:35:09.903 /Devices/IDE0/ATA1/Unit0/PIO            0 times
00:35:09.903 /Devices/IDE0/ATA1/Unit0/ReadBytes 1847842816 bytes
00:35:09.903 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
00:35:09.903 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
00:35:09.903 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
00:35:09.903 /Devices/IDE0/ATA1/Unit1/DMA            0 times
00:35:09.903 /Devices/IDE0/ATA1/Unit1/PIO            0 times
00:35:09.903 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
00:35:09.903 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
00:35:09.903 /Devices/PCNet0/ReceiveBytes            0 bytes
00:35:09.903 /Devices/PCNet0/TransmitBytes           0 bytes
00:35:09.903 /GVMM/EMTs                              1 calls
00:35:09.903 /GVMM/Sum/HaltBlocking             326323 calls
00:35:09.903 /GVMM/Sum/HaltCalls               9938216 calls
00:35:09.903 /GVMM/Sum/HaltNotBlocking         9611893 calls
00:35:09.903 /GVMM/Sum/HaltTimeouts             150797 calls
00:35:09.903 /GVMM/Sum/HaltWakeUps                   0 calls
00:35:09.903 /GVMM/Sum/PokeCalls                 84933 calls
00:35:09.903 /GVMM/Sum/PokeNotBusy                 735 calls
00:35:09.903 /GVMM/Sum/PollCalls                  2278 calls
00:35:09.903 /GVMM/Sum/PollHalts                     0 calls
00:35:09.903 /GVMM/Sum/PollWakeUps                   0 calls
00:35:09.903 /GVMM/Sum/WakeUpCalls              223899 calls
00:35:09.903 /GVMM/Sum/WakeUpNotHalted          103835 calls
00:35:09.903 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:35:09.903 /GVMM/VM/HaltBlocking              326323 calls
00:35:09.903 /GVMM/VM/HaltCalls                9938216 calls
00:35:09.903 /GVMM/VM/HaltNotBlocking          9611893 calls
00:35:09.903 /GVMM/VM/HaltTimeouts              150797 calls
00:35:09.903 /GVMM/VM/HaltWakeUps                    0 calls
00:35:09.903 /GVMM/VM/PokeCalls                  84933 calls
00:35:09.903 /GVMM/VM/PokeNotBusy                  735 calls
00:35:09.903 /GVMM/VM/PollCalls                   2278 calls
00:35:09.903 /GVMM/VM/PollHalts                      0 calls
00:35:09.903 /GVMM/VM/PollWakeUps                    0 calls
00:35:09.903 /GVMM/VM/WakeUpCalls               223899 calls
00:35:09.903 /GVMM/VM/WakeUpNotHalted           103835 calls
00:35:09.903 /GVMM/VM/WakeUpWakeUps                  0 calls
00:35:09.903 /GVMM/VMs                               1 calls
00:35:09.903 /MM/HyperHeap/cbFree              1026608 bytes
00:35:09.903 /MM/HyperHeap/cbHeap              1310464 bytes
00:35:09.903 /PDM/AsyncCompletion/File/cbCached        0 bytes
00:35:09.903 /PDM/AsyncCompletion/File/cbCachedFru        0 bytes
00:35:09.903 /PDM/AsyncCompletion/File/cbCachedMruIn        0 bytes
00:35:09.903 /PDM/AsyncCompletion/File/cbCachedMruOut        0 bytes
00:35:09.903 /PDM/AsyncCompletion/File/cbMax   5242880 bytes
00:35:09.903 /PDM/CritSects/ATA0/ContentionR3        0 times
00:35:09.903 /PDM/CritSects/ATA0/ContentionRZLock       12 times
00:35:09.903 /PDM/CritSects/ATA0/ContentionRZUnlock        0 times
00:35:09.903 /PDM/CritSects/ATA1/ContentionR3        0 times
00:35:09.903 /PDM/CritSects/ATA1/ContentionRZLock       16 times
00:35:09.903 /PDM/CritSects/ATA1/ContentionRZUnlock        3 times
00:35:09.904 /PDM/CritSects/EM-REM/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/IOM EMT Lock/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/IOM EMT Lock/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/IOM EMT Lock/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/PCNet#0/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/PCNet#0/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/PCNet#0/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/PDM/ContentionR3         0 times
00:35:09.904 /PDM/CritSects/PDM/ContentionRZLock      339 times
00:35:09.904 /PDM/CritSects/PDM/ContentionRZUnlock       79 times
00:35:09.904 /PDM/CritSects/PGM/ContentionR3         0 times
00:35:09.904 /PDM/CritSects/PGM/ContentionRZLock   419964 times
00:35:09.904 /PDM/CritSects/PGM/ContentionRZUnlock   475754 times
00:35:09.904 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/REM-Register/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/VGA/ContentionR3         0 times
00:35:09.904 /PDM/CritSects/VGA/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/VGA/ContentionRZUnlock        0 times
00:35:09.904 /PDM/CritSects/VMMDev/ContentionR3        0 times
00:35:09.904 /PDM/CritSects/VMMDev/ContentionRZLock        0 times
00:35:09.904 /PDM/CritSects/VMMDev/ContentionRZUnlock        0 times
00:35:09.904 /PDM/Queue/DevHlp/AllocFailures         0 times
00:35:09.904 /PDM/Queue/DevHlp/Flush                 0 calls
00:35:09.904 /PDM/Queue/DevHlp/FlushLeftovers        0 times
00:35:09.904 /PDM/Queue/DevHlp/Insert                0 calls
00:35:09.904 /PDM/Queue/DevHlp/cItems                8 count
00:35:09.904 /PDM/Queue/DevHlp/cbItem               32 bytes
00:35:09.904 /PDM/Queue/Keyboard/AllocFailures        0 times
00:35:09.904 /PDM/Queue/Keyboard/Flush               0 calls
00:35:09.904 /PDM/Queue/Keyboard/FlushLeftovers        0 times
00:35:09.904 /PDM/Queue/Keyboard/Insert             64 calls
00:35:09.904 /PDM/Queue/Keyboard/cItems             64 count
00:35:09.904 /PDM/Queue/Keyboard/cbItem             16 bytes
00:35:09.904 /PDM/Queue/Mouse/AllocFailures          0 times
00:35:09.904 /PDM/Queue/Mouse/Flush                  0 calls
00:35:09.904 /PDM/Queue/Mouse/FlushLeftovers         0 times
00:35:09.904 /PDM/Queue/Mouse/Insert              1821 calls
00:35:09.904 /PDM/Queue/Mouse/cItems               128 count
00:35:09.904 /PDM/Queue/Mouse/cbItem                32 bytes
00:35:09.904 /PDM/Queue/PCNet-Rcv/AllocFailures        0 times
00:35:09.904 /PDM/Queue/PCNet-Rcv/Flush              0 calls
00:35:09.904 /PDM/Queue/PCNet-Rcv/FlushLeftovers        0 times
00:35:09.904 /PDM/Queue/PCNet-Rcv/Insert             0 calls
00:35:09.904 /PDM/Queue/PCNet-Rcv/cItems             1 count
00:35:09.904 /PDM/Queue/PCNet-Rcv/cbItem            16 bytes
00:35:09.904 /PDM/Queue/PCNet-Xmit/AllocFailures        0 times
00:35:09.904 /PDM/Queue/PCNet-Xmit/Flush             0 calls
00:35:09.904 /PDM/Queue/PCNet-Xmit/FlushLeftovers        0 times
00:35:09.904 /PDM/Queue/PCNet-Xmit/Insert            0 calls
00:35:09.904 /PDM/Queue/PCNet-Xmit/cItems            1 count
00:35:09.904 /PDM/Queue/PCNet-Xmit/cbItem           16 bytes
00:35:09.904 /PGM/CPU0/cGuestModeChanges             3 times
00:35:09.904 /PGM/ChunkR3Map/c                     385 count
00:35:09.904 /PGM/ChunkR3Map/cMax             4294967295 count
00:35:09.904 /PGM/Page/cAllPages                102607 count
00:35:09.904 /PGM/Page/cHandyPages                  33 count
00:35:09.904 /PGM/Page/cMonitoredPages               0 count
00:35:09.904 /PGM/Page/cPrivatePages              4480 count
00:35:09.904 /PGM/Page/cReadLockedPages              0 count
00:35:09.904 /PGM/Page/cSharedPages                  0 count
00:35:09.904 /PGM/Page/cWriteLockedPages             0 count
00:35:09.904 /PGM/Page/cWrittenToPages               0 count
00:35:09.904 /PGM/Page/cZeroPages                98127 count
00:35:09.904 /PGM/cRelocations                       1 times
00:35:09.904 /PROF/CPU0/EM/ForcedActions       9647634 times
00:35:09.904 /PROF/CPU0/EM/Halted               192113 times
00:35:09.904 /PROF/CPU0/EM/RAWTotal            3382134 times
00:35:09.904 /PROF/CPU0/EM/REMTotal            2828162 times
00:35:09.904 /PROF/CPU0/EM/Total              7162382944906 ticks/call (7162382944906 ticks,       1 times, max 7162382944906, min 7162382944906)
00:35:09.904 /PROF/VM/CPU0/Halt/Block           348099 ticks/call (3459486699149 ticks, 9938209 times, max 122691108, min    4794)
00:35:09.904 /PROF/VM/CPU0/Halt/Timers            4276 ticks/call ( 51460053133 ticks, 12032245 times, max   7958924, min    3179)
00:35:09.904 /PROF/VM/CPU0/Halt/Yield            12214 ticks/call (    27825005 ticks,    2278 times, max     52768, min    5593)
00:35:09.904 /REM/TbFlushCount                     749 times
00:35:09.904 /REM/TbPhysInvldCount              378068 times
00:35:09.904 /REM/TlbFlushCount                1212930 times
00:35:09.904 /TM/R3/1nsSteps                   7862192 times
00:35:09.904 /TM/RC/1nsSteps                   1097488 times
00:35:09.904 /TM/TSC/offCPU0                         0 ticks
00:35:09.904 /TM/VirtualSync/CurrentOffset     3451408 ns
00:35:09.904 /VUSB/0/cUrbsInPool                     0 count
00:35:09.904 /VUSB/1/cUrbsInPool                     0 count
00:35:09.904 ********************* End of statistics **********************
00:35:09.909 Changing the VM state from 'DESTROYING' to 'TERMINATED'.

```

how to solve this ??

---

### Post by herkots on 2009-12-30
Hi,

I found a solution for the reboot problem from here: [http://ubuntuforums.org/showthread.php?t=1313989](http://ubuntuforums.org/showthread.php?t=1313989)

You just have to log in as a root and add one line code in a file:  /etc/modules

The line is: vboxdrv

Then save, reboot and log in a usual. Worked for me.

---

### Post by m42h31 on 2010-01-05
thanks, i will try it..

---

### Post by m42h31 on 2010-01-05
adding **vboxdrv** to /etc/modules is not work for me..
please see the screen shot:
[[IMG]http://img685.imageshack.us/img685/1895/vboxerror.png[/IMG]]("http://img19.imageshack.us/img19/1895/vboxerror.png")

---

### Post by slibuntu on 2010-01-06
If you are having this problema nd the previous solutions don't work for you, try this - 

Run (in a terminal)

```
sudo ls /etc/init.d
```

Look for somethis like vbox, or virtualbox (on mine it was virtualbox-ose)

Then run 

```
sudo /etc/init.d/*whatever-it-is-in-yours* restart
```

If you get errors there, post them here

---

### Post by lordmundi on 2010-01-08
I can't seem to fix this after performing an update today.  The error instructs me to install the virtualbox-ose-source package, which I did.  I've reinstalled virtualbox-ose from the repository.  I've rebooted.

No matter what I've tried, upon restarting the service:

```

> sudo /etc/init.d/virtualbox-ose restart
 * Stopping VirtualBox kernel modules                                                                    [ OK ] 
 * Starting VirtualBox kernel modules                                                                            
* No suitable module for running kernel found
                                                                                                         [fail]

```

I know I can go install the closed source version, but I would really like to get what I had working again.

some more info in case it is useful:

```

> uname -a
Linux kramer 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

> vboxmanage --version
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-source package and the appropriate
	 headers, most likely  linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.
3.0.8_OSEr53138

```

---

### Post by slibuntu on 2010-01-08
That's very strange, I'm using the exact same kernel and sudo /etc/init.d/wirtualbox-ose restart works fine for me...

---

### Post by lordmundi on 2010-01-08
> **slibuntu said:**
> That's very strange, I'm using the exact same kernel and sudo /etc/init.d/wirtualbox-ose restart works fine for me...

interesting indeed... have you done an update through the update-manager today?

---

### Post by slibuntu on 2010-01-08
I don't really pay a huge amount of attention, but I'm pretty sure the kernel updated last night. Come to think of it, it could have been the reason that I needed a fix for this problem (and hence found this post).

Maybe bite the bullet and give the non-free version a go to see if it works?

It looks like for some reason Virtualbox is confused about what kernel you are running and seems to think that it doesn't support it for some reason.

---

### Post by lordmundi on 2010-01-08
> **slibuntu said:**
> I don't really pay a huge amount of attention, but I'm pretty sure the kernel updated last night. Come to think of it, it could have been the reason that I needed a fix for this problem (and hence found this post).

Maybe bite the bullet and give the non-free version a go to see if it works?

It looks like for some reason Virtualbox is confused about what kernel you are running and seems to think that it doesn't support it for some reason.

thanks for the reply.  i think you're right.  I did bite the bullet and go to the closed source version, and it seems to work fine.

I suppose if you are brave, you can go to the Update Manager and do a check and a upgrade on everything and see if it breaks you :)

---

### Post by wightman.p on 2010-01-11
I'm running 9.10/64.  Everytime I reboot, I have to do the *sudo /etc/init.d/vboxdrv setup* Kinda irritating, especially after I had a similar problem with VMPlayer & then got rid of it and installed VitrualBox (3.1.2).

On 9.04/32, I had no such issues.

---

### Post by dewsworld on 2010-01-12
Hi
Today I've upgraded the Karnel today on my Karmic 9.10. Then installed Virtual Box and found that error. After restarting I found that massage 


 [LEFT][I]shishir@DewsWorld:~$ sudo /etc/init.d/vboxdrv restart
 * Stopping VirtualBox kernel module                                            
 *  done.
 * Starting VirtualBox kernel module                                            
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why
[/I]*shishir@DewsWorld:~$*



I'm afraid I dont khow how to do then. Any help please ?
[/LEFT]

---

### Post by justpaff on 2010-01-14
I have been through this forum with a fine tooth comb and executed the recommendation therein with no avail.
I am still getting the following:
* Look at /var/log/vbox-install.log to find out what went wrong
I have no idea what to do. Recently updated to ubuntu 9.10

Furthermore: There is an update for the virtual box to version 3.1 but everytime i try to run it there is Error: Conflicts with the installed package 'virtualbox-2.2' How do I uninstal the current verson for the new one. Also will I loose all of my windows virtual machine currently installed therefore having to re-install it?

Thanks for any and all help.

---

### Post by taff99 on 2010-01-17
Running Ubuntu 9.10 x64

Did an update this morning and VBox failed.

Followed the instructions and it all worked for me.

Looks like this is a common fault, shame its still out there.

Beware all those that accept the latest updates for 9.10 !

:popcorn:

---

### Post by jayantkumble on 2010-01-22
> **justpaff said:**
> I have been through this forum with a fine tooth comb and executed the recommendation therein with no avail.
I am still getting the following:
* Look at /var/log/vbox-install.log to find out what went wrong
I have no idea what to do. Recently updated to ubuntu 9.10

Furthermore: There is an update for the virtual box to version 3.1 but everytime i try to run it there is Error: Conflicts with the installed package 'virtualbox-2.2' How do I uninstal the current verson for the new one. Also will I loose all of my windows virtual machine currently installed therefore having to re-install it?

Thanks for any and all help.

Launch Synaptic and mark virtualbox for removal, then download the latest version and install it. You don't have to worry about your virtual machines, they'll remain intact.

---

### Post by Rev_melissa_lane on 2010-01-24
I have done this and it still didnt work. Is there anything else you suggest? This is the error log
[B]Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-18-generic-pae cannot be found at
/lib/modules/2.6.31-18-generic-pae/build or /lib/modules/2.6.31-18-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
[/B]

---

### Post by maugarta on 2010-01-28
Hi,
I solve this problem in my kubuntu 9.10 whith virtualbox-ose version 3.0.8-dfsg-1ubuntu1 installing linux-headers (linux-headers-server or linux-headers-generic depending on linux-kernel)

try it, I hope it helps you

 My kernel is linux-server so I run:

```
#sudo aptitude install linux-headers-server virtualbox-ose-guest-source
```Paste log:

```

#uname -a 
2.6.31-17-server #54-Ubuntu SMP Thu Dec 10 18:06:56 UTC 2009 x86_64 GNU/Linux

# sudo aptitude install linux-headers-server 

S'està llegint la llista de paquets... Fet                      
S'està construint l'arbre de dependències                       
S'està llegint la informació de l'estat... Fet                  
S'està llegint la informació d'estat estesa                     
S'estan inicialitzant els estats dels paquets... Fet            
Els paquets nous següents s'instal·laran:                       
  linux-headers-2.6.31-17-server{a} linux-headers-server        
Els paquets parcialment instal·lats següents es configuraran:   
  virtualbox-ose-guest-source                                   
0 paquets a actualitzar, 2 a instal·lar, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 699kB d'arxius. Després del desempaquetat s'utilitzaran 8864kB.
Esteu segur de voler continuar? [Y/n/?]                                             
S'està escrivint la informació d'estat estesa... Fet                                
Obté:1 http://es.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-17-server 2.6.31-17.54 [696kB]
Obté:2 http://es.archive.ubuntu.com karmic-updates/main linux-headers-server 2.6.31.17.30 [3332B]          
S'han obtingut 699kB en 0s (4309kB/s)                                                                      
S'està seleccionant el paquet linux-headers-2.6.31-17-server prèviament no seleccionat.                    
(S'està llegint la base de dades ... hi ha 268368 fitxers i directoris instal·lats actualment.)            
S'està desempaquetant linux-headers-2.6.31-17-server (de .../linux-headers-2.6.31-17-server_2.6.31-17.54_amd64.deb) ...                                                                                                         
S'està seleccionant el paquet linux-headers-server prèviament no seleccionat.                                   
S'està desempaquetant linux-headers-server (de .../linux-headers-server_2.6.31.17.30_amd64.deb) ...             
S'està configurant linux-headers-2.6.31-17-server (2.6.31-17.54) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-17-server
 *  vboxdrv (3.0.8)...                                                                                          vboxdrv (3.0.8): Installing module.
...........
.......
                                                                                                         [ OK ]
 *  vboxnetadp (3.0.8)...                                                                                       vboxnetadp (3.0.8): Installing module.
..........
......
                                                                                                         [ OK ]
 *  vboxnetflt (3.0.8)...                                                                                       vboxnetflt (3.0.8): Installing module.
..........
......
                                                                                                         [ OK ]
 *  virtualbox-ose-guest (3.0.8)...                                                                             virtualbox-ose-guest (3.0.8): Installing module.
...........
......
                                                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

S'està configurant virtualbox-ose-guest-source (3.0.8-dfsg-1ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

S'està configurant linux-headers-server (2.6.31.17.30) ...
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
S'està llegint la informació de l'estat... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet

# sudo /etc/init.d/virtualbox-ose restart
 * Stopping VirtualBox kernel modules    [ OK ]
 * Starting VirtualBox kernel modules     [ OK ]

# sudo /etc/init.d/virtualbox-ose status
VirtualBox kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are loaded.


```

---

### Post by ray setiawan on 2010-02-23
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)      this work!!! Excelent!!!

---

### Post by Gonzalo_VC on 2010-02-23
[COLOR="Navy"]I am running Ub. 8.04 LTS and had VirtualBox OSE 1.5.6 or so. I created a vm with some other $ystem :P and it was fine... until a normal system update this days (kernel included).
Then the vm did not open any more and VBoxOSE complained about some modules, kernell and whatever.

Y tried to get them with synaptic but didn't work (eventhough I don't like to have 2 kernels and header, etc.). Anyway got to reboot and my PC does some hda1 (or 2) checking!!?? maybe because it detects pieces of 2 different versions of the kernel...

I got aVirtualBox .DEB from their "org" page and installed it, after removing everything else in synaptic. It was no good (I guess the OSE version needs less stuff and works better.

Following step: I got to install it again, now an older OSE version in he repositories, and it worked until it was jut opening the vm... then said something about me not being in the users group, what I tried to remediate as usual (adduser...) but still got the nasty message bellow. 
Any clues? :confused:
Thanks![/COLOR]


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Código de Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by xcrunner78 on 2010-03-05
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)


Right on, this worked for me as well for the same problem.

---

### Post by filmdc on 2010-03-15
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```I seem to be good now.

Rhino


good call!:popcorn:

---

### Post by rrazian on 2010-05-12
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```I seem to be good now.

Rhino:P

You rule.  Finally worked for me.

---

### Post by ktechman on 2010-05-20
Here is my solution:

Open Synaptic and reinstall the following "dkms" all of the "linux-header" files then do "sudo /etc/init.d/vboxdrv setup" in the terminal 
 I know no other way of re-installing via the command line so I used Synaptic. In my situation "/dev/vboxdrv" and "/dev/vboxnetctl" did not even exist so the sudo /etc/init.d/vboxdrv setup script was not working because "dkms" was not part of my kernel headers, I think.  If someone has a more informed explanation please give it but the reason is secondary to getting a working vbox especially with all of the improvements in 3.2... dual monitor support with just a few ticks is impressive to say the least. This issue is (Solved) for me 

Ktechman

---

### Post by nortexoid on 2010-05-22
> **mjones41 said:**
> sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

Fixed my virtual box great, but why did the dkms remove my google earth and skype?

Fixed mine just great too! Cheers.

---

### Post by Kanna2412 on 2010-05-22
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

Hi,

Thanks for the above information.
I tried the above three commands in terminal. First two worked fine but the third on **[FONT=AR PL UMing TW, serif]sudo /etc/init.d/vboxdrv setup[/FONT]** did not work. I got the below result.

[I][B]jayaswaroop@jayaswaroop-desktop:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found[/B][/I]

Please help me how to execute the command.

---

### Post by DPic on 2010-05-27
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```
I seem to be good now.

Rhino

THANK YOU! 

This is the ONLY solution that has worked for me.

---

### Post by freakrz on 2010-06-17
I had the same issue on Ubuntu 9.10 & Virtual Box 3.2 , this worked for me..

Thank You


> **enimen0 said:**
> to those who still have problems using the command "sudo /etc/init.d/vboxdrv setup", should try this:

sudo /etc/init.d/vboxdrv.dpkg-bak setup

it worked fine for me!
Ubuntu 9.10
VirtualBox 3.0.12

---

### Post by Sulo111 on 2010-06-26
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)


THANK YOU!!!!  I had the same problem as you guys and i just looked it up and bam!! ubuntu forums rocks !!Thank you guys.

---

### Post by freakrz on 2010-07-07
> **freakrz said:**
> I had the same issue on Ubuntu 9.10 & Virtual Box 3.2 , this worked for me..

Thank You

I had the virtual box working,but everytime i boot up i get the same error and i would need to run "sudo /etc/init.d/vboxdrv.dpkg-bak setup" to get it working again.is there a permanant fix for this.

Thank You

---

### Post by dima206 on 2010-07-07
I have the same problem, after reboot the error come back!
Is there is any permanent solution?

---

### Post by RottNKorpse on 2010-07-07
I have done the last line before to reset the drivers and it worked that time and today it started doing the same error so if it continues after this time I will have no idea what to do as I just did the three sudo lines as posted in this thread so hopefully this will fix whatever is going one.

---

### Post by fja0568 on 2010-07-26
Whenever you install a new kernel, you must rebuild the kernel module for virtualbox (vboxdrv).  You can do this as follows:

1) Bust open a prompt and determine your linux version:
 uname -r

(In my case: 2.6.32-24-preempt)

2) Install the linux headers for your version from Synaptic:

(In my case: linux-headers-2.6.32-24, linux-headers-2.6.32-24-preempt, and linux-headers-2.6.32-24-generic)

3) Reinstall virtualbox from Synaptic:

(virtualbox-ose, virtualbox-ose-dkms, virtualbox-ose-qt)

---

### Post by derlok on 2010-07-30
> **fja0568 said:**
> Whenever you install a new kernel, you must rebuild the kernel module for virtualbox (vboxdrv).  You can do this as follows:

1) Bust open a prompt and determine your linux version:
 uname -r

(In my case: 2.6.32-24-preempt)

2) Install the linux headers for your version from Synaptic:

(In my case: linux-headers-2.6.32-24, linux-headers-2.6.32-24-preempt, and linux-headers-2.6.32-24-generic)

3) Reinstall virtualbox from Synaptic:

(virtualbox-ose, virtualbox-ose-dkms, virtualbox-ose-qt)


Thank you very very much. its worked!!

---

### Post by LeeTheEarthling on 2010-08-07
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

Had the same problem and this worked for me! Thanx.

---

### Post by francois138 on 2010-08-13
> **LeeTheEarthling said:**
> Had the same problem and this worked for me! Thanx.

Worked for me too! :D

---

### Post by ausome on 2010-08-19
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```
I seem to be good now.

Rhino

Thanks Rhino, that is what worked for me.

I had installed VBoxManage via virtualbox-ose which removed my Virtualbox installation.

So when I reinstalled Virtualbox it suggested to run the /etc/init.d/vboxdrv setup command when I tried to startup any of my systems.

As you found - that file had been renamed so copying it back got me up and running again.

Cheers

---

### Post by kendisk on 2010-08-21
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

THX. it worked for me.

---

### Post by kristaga on 2010-08-27
Hello!

If someone with Fedora 13 comes across this thread these commands might help you with the same problem:

As root (or sudo/super user):

```
yum install kmod-VirtualBox-OSE
```This solved the problem for me.

---

### Post by rupakg on 2010-09-10
Hi,
   I tried the following commands:

sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

I get the following output:

* Stopping VirtualBox kernel module                                             *  done.
* Removing old VirtualBox netadp kernel module                                  *  done.
* Removing old VirtualBox netflt kernel module                                  *  done.
* Removing old VirtualBox kernel module                                         *  done.
* Recompiling VirtualBox kernel module                                          *  done.
* Starting VirtualBox kernel module                                            
* modprobe vboxdrv failed. Please use 'dmesg' to find out why

I am on Ubuntu 10.4 64-bit, and using virtualbox 3.2

Any help will be greatly appreciated?

Thanks,
Rupak

---

### Post by gsak1100sc on 2010-10-16
Just upgraded to 10.10 and got the same error when starting Virtualbox, tried the following entries

sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup
  
The second line i got "missing destination file operend after 'dkms' "

After the third line I got an error message when it tried to reinstall virtualbox.

The error log is as follows. Sorry if too long, I am new at this.

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.1.2

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.31-20-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.32-23-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.32-25-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod......

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.31-19-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.32-21-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.32-22-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.32-24-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.31-21-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.31-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 3.1.2
Kernel:  2.6.31-17-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 3.1.2
completely from the DKMS tree.
------------------------------
Done.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.
  removing old DKMS module vboxdrv version  3.1.2

Error! There are no instances of module: vboxdrv
3.1.2 located in the DKMS tree.

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-22-generic -C /lib/modules/2.6.35-22-generic/build M=/var/lib/dkms/vboxdrv/3.1.2/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/3.1.2/build/ for more information.
0
0
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-3.1.0.crash'
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -I/lib/modules/2.6.35-22-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)"  -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/include/VBox/types.h:34,
                 from /tmp/vbox.0/linux/../SUPDrvInternal.h:39,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:37:
/tmp/vbox.0/include/iprt/types.h:100: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxdrv] Error 2

Unquote



Thanks in advance for any help generated.
Peter @ Gladstone

---

### Post by denfio on 2010-10-18
just upgraded to 10.10 and receiving the same erro

---

### Post by waterboy0911 on 2010-10-26
I got the same error too..

I'm using Ubuntu 10.10


before I update the kernel @ first it was okay and it works fine..

after the update.. I can't run my vm anymore.. 

I already tried the suggestions but the problem is still there.

any help is greatly appreciate


thanks

---

### Post by ignisuti on 2010-11-07
None of the solutions here seem to be resolving my seemingly similar issue. 

Please help me trouble-shoot. Here is a command output that might help us get started:
```
data@data:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.32-21-generic cannot be found at
/lib/modules/2.6.32-21-generic/build or /lib/modules/2.6.32-21-generic/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
data@data:~$ sudo aptitude install virtualbox-ose-modules-generic
Couldn't find any package whose name or description matched "virtualbox-ose-modules-generic"
Couldn't find any package whose name or description matched "virtualbox-ose-modules-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 329 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by ignisuti on 2010-11-11
Bump... Anyone...?

---

### Post by CharlesA on 2010-11-11
You have the kernel headers installed, right?

Same with DKMS?

---

### Post by AlexanderDGreat on 2010-11-11
I think everyone needs to *think twice* before upgrading to a new version of Ubuntu, specially if it's not yet LTS, or if you're using it for your productivity.

It's such a pain to see people, having troubles with a completely good and stable running system just yesterday, then it's broken all of a sudden.

My advice: Downgrade your VirtualBox'es to older versions, if NOT, don't upgrade Ubuntu yet.

Sorry that's all I can think of.

---

### Post by ignisuti on 2010-11-12
> **CharlesA said:**
> You have the kernel headers installed, right?

Same with DKMS?

I goggled how to upgrade my kernel headers and got the following errors when I attempted this step. Please help.

```
root@data:~# sudo apt-get update
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US             
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                            
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                 
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                                
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en          
Get:3 http://extras.ubuntu.com maverick Release [57.3kB]                                     
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US          
Get:4 http://security.ubuntu.com maverick-security Release [27.2kB]                          
Ign http://extras.ubuntu.com maverick Release                                                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US         
Hit http://us.archive.ubuntu.com maverick Release                           
Hit http://packages.medibuntu.org maverick Release.gpg                                       
Ign http://packages.medibuntu.org/ maverick/free Translation-en                              
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US           
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en          
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US       
Ign http://extras.ubuntu.com maverick/main i386 Packages/DiffIndex           
Hit http://us.archive.ubuntu.com maverick-updates Release                    
Hit http://packages.medibuntu.org maverick Release                                           
Hit http://extras.ubuntu.com maverick/main i386 Packages                                     
Hit http://us.archive.ubuntu.com maverick/main Sources                       
Hit http://us.archive.ubuntu.com maverick/restricted Sources                 
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://packages.medibuntu.org maverick/free i386 Packages                
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources 
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Get:5 http://security.ubuntu.com maverick-security/main Sources [12.7kB]
Hit http://packages.medibuntu.org maverick/non-free i386 Packages            
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages   
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Get:6 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:7 http://security.ubuntu.com maverick-security/universe Sources [3,279B]
Get:8 http://security.ubuntu.com maverick-security/multiverse Sources [651B]
Get:9 http://security.ubuntu.com maverick-security/main i386 Packages [36.3kB]
Get:10 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:11 http://security.ubuntu.com maverick-security/universe i386 Packages [13.1kB]
Get:12 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,660B]
Fetched 95.2kB in 1s (58.6kB/s)     
Reading package lists... Done
W: GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
root@data:~# 
root@data:~# 
root@data:~# apt-cache search linux-headers-$(uname -r)
root@data:~# 
root@data:~# sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-2.6.32-21-generic
E: Couldn't find any package by regex 'linux-headers-2.6.32-21-generic'

```

---

### Post by CharlesA on 2010-11-12
Do you have the latest kernel? Maverick should be on 2.6.35.x

The PGP key error is probably due to having extras.ubuntu.com in yer sources.list.

---

### Post by ignisuti on 2010-11-12
> **CharlesA said:**
> Do you have the latest kernel? Maverick should be on 2.6.35.x

Hmmm... This shows 2.6.32.x....

```
root@data:~# uname -a
Linux data 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```

That's odd because I could swear I upgraded to Maverick. Check this out:
```
root@data:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

Did I screw-up the upgrade? What can I do to fix this?

---

### Post by CharlesA on 2010-11-12
Yeah, that's strange.

I don't know how to fix it outside of just doing a clean install of maverick.

Maybe make a thread asking about in in General Help.

---

### Post by ignisuti on 2010-11-13
> **AlexanderDGreat said:**
> I think everyone needs to *think twice* before upgrading to a new version of Ubuntu, specially if it's not yet LTS, or if you're using it for your productivity.

It's such a pain to see people, having troubles with a completely good and stable running system just yesterday, then it's broken all of a sudden.

My advice: Downgrade your VirtualBox'es to older versions, if NOT, don't upgrade Ubuntu yet.

Sorry that's all I can think of.


Yep, you're right. I had no business leaving version 10.4. I reinstalled that and then reinstalled my headers. VirtualBox works fine once again.

Thanks for the help fellas.

---

### Post by fja0568 on 2010-11-29
Whenever you install a new kernel, you must rebuild the kernel module for virtualbox (vboxdrv).  You can do this as follows:

1) Bust open a prompt and determine your linux version:
 uname -r

(In my case: 2.6.32-24-preempt)

2) Install the linux headers for your version from Synaptic:

(In my case: linux-headers-2.6.32-24, linux-headers-2.6.32-24-preempt, and linux-headers-2.6.32-24-generic)

3) Reinstall virtualbox from Synaptic:

(virtualbox-ose, virtualbox-ose-dkms, virtualbox-ose-qt)

---

### Post by archolman on 2010-12-11
[B]Lucid Lynx.  2.6.32-27-generic #49-Ubuntu SMP i686 GNU/Linux


[/B]I seem to have the same problem.

 After installing[SIZE=1] [SIZE=2]VBox 3.2.12 for Linux[/SIZE][/SIZE] from VBox's page, I couldn't find the icon on my desktop, so, in a terminal:

> ****@linux-studio:~$ VirtualBox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.32-27-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

Running this returned:

> Failed to create the VirtualBox COM object.
The application will now terminate.
Start tag expected, '<' not found.
Location: '/home/****/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.
/home/vbox/vbox-3.2.12/src/VBox/Main/VirtualBoxImpl.cpp[535] (nsresult VirtualBox::init()).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {3f36e024-7fed-4f20-a02c-9158a82b44e6}So I loaded the module, via Synaptic, re-booted, & tried:
        
> ****@linux-studio:~$ sudo /etc/init.d/vboxdrv setupwhich returned:

> sudo: /etc/init.d/vboxdrv: command not found????Duh????
What next? Do I need to install other kernel modules? If so, which ones?
 And where, if necessary, do I insert the [start tag '<']?

---

### Post by mayfield1814 on 2010-12-13
Try taking a look at the Virtualbox.xml file in you "user"/.Virtualbox directory.  Mine was blank.  I could only start it as root.  So i copied the Virtualbox.xml from roots folder to mine and was able to start it.

---

### Post by DarthOpto on 2011-01-04
I had an update this morning and then Vbox popped this error. I did as suggested and the solution worked. I need to ask, why was this necessary as VBox was working prior to the update? Will this be necessary after every kernel update?

---

### Post by chartter9 on 2011-01-12
It's a free OS...dems the brakes, I'm just happy the community has solutions to most issues and failing that will work with us to find the solution. :)

---

### Post by DarthOpto on 2011-01-12
> **chartter9 said:**
> It's a free OS...dems the brakes, I'm just happy the community has solutions to most issues and failing that will work with us to find the solution. :)
Oh I am not complaining, I am grateful that there was a simple solution.

---

### Post by b0b138 on 2011-01-12
> **DarthOpto said:**
> I had an update this morning and then Vbox popped this error. I did as suggested and the solution worked. I need to ask, why was this necessary as VBox was working prior to the update? Will this be necessary after every kernel update?

vbox (and some other software, like my nvidia drivers for example) have kernel modules. So if your innocent looking update happens to include a kernel update, all kernel modules have to be recompiled for the new kernel.

DKMS (dynamic kernel module support) is supposed to automate this by keeping track of kernel modules, and recompiling them as needed. This also means you have to have to correct headers package too. This also should keep itself up to date with the linux-headers-generic package, which is just a meta-package that points to the latest headers.

---

### Post by JKyleOKC on 2011-01-20
> **b0b138 said:**
> This also means you have to have to correct headers package too. This also should keep itself up to date with the linux-headers-generic package, which is just a meta-package that points to the latest headers.And unfortunately, the last couple of kernel updates for Lucid have NOT included the header packages as part of the update. Thus when you reboot after installing all of the updates, your system is no longer fully functional if you use VirtualBox or Nvidia video cards. With 2.6.32-26, only vbox was affected. With 2.6.32-27, Nvidia also bit the dust, making it a bit difficult to do an immediate repair. Fortunately, rebooting to -26 allowed me to grab the new headers...

---

### Post by Nisse79 on 2011-01-30
I have the same problem, the solution to boot an earlier version is however not something I do not know how to do. Could someone explain in beginners terms how to do it?

It will be much appreciated.

---

### Post by ikt on 2011-01-30
> **Nisse79 said:**
> I have the same problem, the solution to boot an earlier version is however not something I do not know how to do. Could someone explain in beginners terms how to do it?

It will be much appreciated.

Hold shift down while you boot, then you get a menu of all your linux kernels.

---

### Post by Schwerzenheimen on 2011-02-02
> **BrMBr said:**
> Worked for me! Thanks!!!

Using Ubuntu 10.10, Maverick Meerkat, and the solution still works.

Thanks!

---

### Post by Blabry on 2011-02-03
```
root@blabry-madrfakr:/etc/init.d# sudo /etc/init.d/vboxdrv.dpkg-bak setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.
```

This worked for me ;)

Ubuntu 11.04 GO (Ubuntu 10.10, Maverick Meerkat)

Thanks :)

---

### Post by foxruns on 2011-02-09
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```I seem to be good now.

Rhino


this worked for me
ubuntu forums are amazing.

---

### Post by Lampa74 on 2011-03-02
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```I seem to be good now.

Rhino

Thank you VERY much, Rinocom!
It **finally** works for me, after 15 days try...

---

### Post by Wangberg on 2011-04-19
> **lin-lin_224 said:**
> I met the same problem after updating UBUNTU9.04 . Now, I found the solution on the following address:                                    [FONT=AR PL UMing TW, serif]https://answers.launchpad.net/ubuntu/+source/virtualbox-ose/+question/64190[/FONT]
 [FONT=AR PL UMing TW, serif]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]
  The commands are:                    [FONT=AR PL UMing TW, serif]
[/FONT]
 [FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]


  Try it&#65281;
Good luck&#65281;
;)

works for me also.

---

### Post by tmratwork on 2011-05-21
after updating to ubuntu 11.04, i ran into error posted in previous messages.  tried everything above, still got same error.  then i re-installed gcc and gcc related packages through synaptic and virtualbox 4.08 now works.

thank you everybody for posting advice.

---

### Post by sloosley on 2011-05-22
I'm also attempting to install VB 4.08 on Natty 11.04, and I keep getting the kernel diver error discussed above. 

When I run **sudo /etc/init.d/vboxdrv setup** it returns: 
* Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.32.26+drm33.12 cannot be found at
/lib/modules/2.6.32.26+drm33.12/build or /lib/modules/2.6.32.26+drm33.12/source.

I've tried numerous solutions discussed above, but nothing works. I've installed the generic Natty kernels, DKMS, and re-installed gcc. 

If anyone has advice, or even encouragement, I'd be appreciative! Thank you.

---

### Post by adipramono on 2011-05-22
I had the same problem. I installed VirtualBox 4.0.8.r71778 Windows XP SP3 as the guest OS and my Ubuntu 10.04 (2.6.32 kernel) as the host OS. After I upgrade the kernel into 2.6.38 my XP on the VirtualBox didn't work, I don't exactly remember the error was. But after I reinstalled the VirtualBox, I found that my XP works normal like before!

---

### Post by sloosley on 2011-05-22
It finally hit me: I'm running Ubuntu 11.04 as a secondary OS on a Cr-48, Google's test Chromebook. The Chrome OS is curently based on Ubuntu's 2.6.32 kernel, which is also the kernel that my installation of Ubuntu is using. When VirtualBox attempts to install, it can't find the kernel headers for my 2.6.32 kernel, because the kernel headers loaded with 11.04 are based on 2.6.38. 

If I was a lot smarter, I'm sure that there's a way to work around the issue. So, it looks like I'm dead in the water until Google begins using the updated kernel. 

I'm not sure how to "force" 11.04 to use/install the necessary 2.6.32 kernel files to make VB install.

---

### Post by CharlesA on 2011-05-22
I'm not sure if you can "force" it either. If you are booted into 2.6.38, it should find the headers for that kernel.

---

### Post by franz.linz on 2011-05-23
This Link may be helpfull for you!

[http://ubuntuforums.org/showthread.php?t=1747766](http://ubuntuforums.org/showthread.php?t=1747766)

Franz

---

### Post by aveeshkumar on 2011-08-22
> **Wangberg said:**
> works for me also.

As posted above, the following worked with a slight modification - ubuntu natty, vbox 4.1.2

replace aptitude with apt-get

sudo apt-get update (OK)
sudo apt-get install dkms (already latest)
sudo /etc/init.d/vboxdrv setup (error about conf file not in good format but WORKED)

Thanks all - HTH

my level - advanced noob!

---

### Post by AlexanderDGreat on 2011-08-23
Ever since my last post in this thread 5 months ago? I switched to VMware Player (it's also free)

---

### Post by DPic on 2011-08-24
> **AlexanderDGreat said:**
> Ever since my last post in this thread 5 months ago? I switched to VMware Player (it's also free)

It is gratis (free of charge) but it is not free software (open source).

---

### Post by adelani on 2011-12-23
Thanks 
I tried

sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

and its works good

---

### Post by Anish3190 on 2012-05-25
anish@anish-Aspire-4930:~$ sudo aptitude update
[sudo] password for anish: 
sudo: aptitude: command not found
anish@anish-Aspire-4930:~$ 

hi i'm getting this error
please help?

---

### Post by Anish3190 on 2012-05-25
anish@anish-Aspire-4930:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
anish@anish-Aspire-4930:~$ 

where is this log?

---

### Post by CharlesA on 2012-05-25
> **Anish3190 said:**
> anish@anish-Aspire-4930:~$ sudo aptitude update
[sudo] password for anish: 
sudo: aptitude: command not found
anish@anish-Aspire-4930:~$ 

hi i'm getting this error
please help?

aptitude is not installed by default. You would have to apt-get it.

> **Anish3190 said:**
> anish@anish-Aspire-4930:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
anish@anish-Aspire-4930:~$ 

where is this log?

It says where the log is: /var/log/vbox-install.log :)

---

### Post by Anish3190 on 2012-05-26
Hi
I used adelani's post's instructions and it works fine
thanks CharlesA and every one at the forum for your valuable contribution!!
regards,
Anish3190

---

### Post by Hulipill on 2012-06-17
Ok so this worked for almost all Ubuntu, Kubuntu 12.04, Kubuntu 12.04, Ubuntu 12.04, FAILED with Lubuntu 12.04,
Required Steps:
1. Install aptitude :guitar:
2. Install DMKS (With Aptitude) :lolflag:
3. Install VBOX Additions :popcorn:
Steps to succeed:
1. Sudo -s (Be sure You're at Root In The Terminal)
2. sudo apt-get install aptitude
3. sudo aptitude install DKMS (Rebuild DMKS)
4. cd /VirtualBoxGuestAddtions (or whatever the mounted VboxAddtions disk name is)
5. sudo sh VirtualBoxGuestAdditions.run (Or Whatever the .run file is on the cd drive
 :) Enjoy :popcorn::popcorn::popcorn::lolflag:

---

### Post by CharlesA on 2012-06-17
> **Hulipill said:**
> Ok so this worked for almost all Ubuntu, Kubuntu 12.04, Kubuntu 12.04, Ubuntu 12.04, FAILED with Lubuntu 12.04,
Required Steps:
1. Install aptitude :guitar:
2. Install DMKS (With Aptitude) :lolflag:
3. Install VBOX Additions :popcorn:
Steps to succeed:
1. Sudo -s (Be sure You're at Root In The Terminal)
2. sudo apt-get install aptitude
3. sudo aptitude install DKMS (Rebuild DMKS)
4. cd /VirtualBoxGuestAddtions (or whatever the mounted VboxAddtions disk name is)
5. sudo sh VirtualBoxGuestAdditions.run (Or Whatever the .run file is on the cd drive
 :) Enjoy :popcorn::popcorn::popcorn::lolflag:

1. You don't need a root shell.
2. Using apt-get works completely fine to install dkms.
3. You only install the guest additions on the guest, not the host.

EDIT: I just checked a 12.04 guest, with the guest additions installed via "additional drivers" and the guest has dkms installed:

```
charles@Precise:~$ dpkg -l | grep dkms
ii  dkms                                   2.2.0.3-1ubuntu3                        Dynamic Kernel Module Support Framework
ii  virtualbox-guest-dkms                  4.1.12-dfsg-2                           x86 virtualization solution - guest addition module source for dkms

```

The Kernel module not loaded error has nothing to do with guest additions because it occurs on the **host** not the guest.

---

### Post by coffeecat on 2012-06-17
+1 to CharlesA's comments, and...

> **Hulipill said:**
> 
1. Sudo -s (Be sure You're at Root In The Terminal)

No! That's inadvisable. Please see:

[https://help.ubuntu.com/community/RootSudo#Special_notes_on_sudo_and_shells](https://help.ubuntu.com/community/RootSudo#Special_notes_on_sudo_and_shells)

And:

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

The correct command for getting a root shell is "sudo -i", but as CharlesA says, you don't need a root shell - just prepend all commands with sudo. And besides, "Sudo -s" would fail. Linux is case sensitive.

---

### Post by lads on 2012-06-20
> **Anish3190 said:**
> anish@anish-Aspire-4930:~$ sudo aptitude update
[sudo] password for anish: 
sudo: aptitude: command not found
anish@anish-Aspire-4930:~$ 

hi i'm getting this error
please help?

You can check [this thread]("http://ubuntuforums.org/showthread.php?t=1885936"). Good luck.

---

### Post by elsetherock on 2012-08-19
> **rinocom said:**
> Try tabbing out the vboxdrv portion of 'sudo /etc/init.d/vboxdrv' and see if it has been moved...  I say this because I found that I had a file called '/etc/init.d/vboxdrv.dpkg-bak'.  I executed ```

laptop:~$ sudo cp /etc/init.d/vboxdrv.dpkg-bak /etc/init.d/vboxdrv
laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


```I seem to be good now.

Rhino


very good, it's work for me.

Thanks

---

### Post by Chuck Glenn on 2012-11-05
here's what has worked for me.. after reading the full message, and paying attention to the fact that it's saying something about kernel headers... drum roll please

I go to software center, enter "kernel headers". I remember something about "generic" from the last time I had this same issue, so I install the linux-headers-3.5.18-generic, then restart my machine. VOILA.

SO I guess VirtualBox needs the "generic headers" for whatever kernel you're running. Any time the kernel updates (pay attention to the updates window), you gotta re-install the headers and restart. Worked for me.

---

### Post by mutified on 2012-12-10
Error! Bad return status for module build on kernel: 3.2.6 (x86_64) Consult the make.log in the build directory /var/lib/dkms/virtualbox-ose/3.1.6/build/ for more information. dpkg: error processing virtualbox-ose-dkms (--configure):  subprocess installed post-installation script returned error exit status 10 Errors were encountered while processing:  virtualbox-ose-dkms  is a persistent error. The same line occurs during:  aptitude install synaptic  or other install commands. I was still able to start synaptic and then selected all of the upgrades. One of them was virtualbox-ose-dkms.  Installing...brb [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by mutified on 2012-12-10
At the end of my Synaptic applications upgrade these are the results:     &quot;E: virtualbox-ose-dkms: subprocess installed post-installation script returned error exit status 10&quot;   This error repeats throughout the upgrades and just following the python compatibility check. I'm at a loss. Sorry for not generating the upgrade script report.

---

### Post by bbkudk on 2013-01-25
[Thats]("https://www.virtualbox.org/wiki/Linux_Downloads") helped for me:
aptitude purge virtualbox

```
echo "deb http://download.virtualbox.org/virtualbox/debian $(uname -r) contrib" | sudo tee -a /etc/apt/sources.list 
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add - 
sudo apt-get update

sudo apt-get install linux-headers
sudo aptitude install virtualbox-4.2
```

---

### Post by XBMC old School on 2013-01-27
Sorry i have the same problem and booting into the default generic kernel didn't fix the VMmachine issue

---

### Post by Gwaro on 2013-02-18
I downloaded the .deb file from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) , installed it with gdebi and I have had brighter days since then:D!

---

### Post by corswors on 2013-02-21
Hi Guys. 

VirtualBox error: Kernel driver not installed (rc=-1908)

This is what i did to get the error above fixed 

apt-get install linux-headers

apt-get install linux-headers-3.5.0-24-generic

sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

Working !!!:p

---

### Post by XBMC old School on 2013-02-23
> **corswors said:**
> Hi Guys. 

VirtualBox error: Kernel driver not installed (rc=-1908)

This is what i did to get the error above fixed 

apt-get install linux-headers

apt-get install linux-headers-3.5.0-24-generic

sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

Working !!!:p

I tried the above method and got back errors.

```
                      P { margin-bottom: 0.21cm; }   Brock@Gonad:~$ apt-get install linux-headers  
 E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)  
 E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?  
 Brock@Gonad:~$ sudo apt-get install linux-headers  
 [sudo] password for Brock:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Package linux-headers is a virtual package provided by:  
   linux-headers-3.7.4-lld-bfs-bfq 3.7.4-lld-bfs-bfq-10.00.Custom  
   linux-headers-3.6.6-low-latency-desktop 3.6.6-low-latency-desktop-10.00.Custom  
   linux-headers-3.6.6-lld+bfq 3.6.6-lld+bfq-10.00.Custom  
   linux-headers-3.6.6-crazyass-fast 3.6.6-crazyass-fast-10.00.Custom  
   linux-headers-3.2.0-38-lowlatency 3.2.0-38.40  
   linux-headers-3.2.0-37-lowlatency 3.2.0-37.37  
   linux-headers-3.2.0-36-lowlatency 3.2.0-36.36  
   linux-headers-3.2.0-35-lowlatency 3.2.0-35.34  
   linux-headers-3.2.0-33-lowlatency 3.2.0-33.33  
   linux-headers-3.2.0-38-virtual 3.2.0-38.61  
   linux-headers-3.2.0-38-generic 3.2.0-38.61  
   linux-headers-3.2.0-38 3.2.0-38.61  
   linux-headers-3.2.0-37-virtual 3.2.0-37.58  
   linux-headers-3.2.0-37-generic 3.2.0-37.58  
   linux-headers-3.2.0-37 3.2.0-37.58  
   linux-headers-3.2.0-36-virtual 3.2.0-36.57  
   linux-headers-3.2.0-36-generic 3.2.0-36.57  
   linux-headers-3.2.0-36 3.2.0-36.57  
   linux-headers-3.2.0-35-virtual 3.2.0-35.55  
   linux-headers-3.2.0-35-generic 3.2.0-35.55  
   linux-headers-3.2.0-35 3.2.0-35.55  
   linux-headers-3.2.0-34-virtual 3.2.0-34.53  
   linux-headers-3.2.0-34-generic 3.2.0-34.53  
   linux-headers-3.2.0-34 3.2.0-34.53  
   linux-headers-3.2.0-33-virtual 3.2.0-33.52  
   linux-headers-3.2.0-33-generic 3.2.0-33.52  
   linux-headers-3.2.0-33 3.2.0-33.52  
   linux-headers-3.2.0-32-virtual 3.2.0-32.51  
   linux-headers-3.2.0-32-generic 3.2.0-32.51  
   linux-headers-3.2.0-32 3.2.0-32.51  
   linux-headers-3.2.0-31-virtual 3.2.0-31.50  
   linux-headers-3.2.0-31-generic 3.2.0-31.50  
   linux-headers-3.2.0-31 3.2.0-31.50  
   linux-headers-3.2.0-30-virtual 3.2.0-30.48  
   linux-headers-3.2.0-30-generic 3.2.0-30.48  
   linux-headers-3.2.0-30 3.2.0-30.48  
   linux-headers-3.2.0-29-virtual 3.2.0-29.46  
   linux-headers-3.2.0-29-generic 3.2.0-29.46  
   linux-headers-3.2.0-29 3.2.0-29.46  
   linux-headers-3.2.0-27-virtual 3.2.0-27.43  
   linux-headers-3.2.0-27-generic 3.2.0-27.43  
   linux-headers-3.2.0-27 3.2.0-27.43  
   linux-headers-3.2.0-26-virtual 3.2.0-26.41  
   linux-headers-3.2.0-26-generic 3.2.0-26.41  
   linux-headers-3.2.0-26 3.2.0-26.41  
   linux-headers-3.2.0-25-virtual 3.2.0-25.40  
   linux-headers-3.2.0-25-generic 3.2.0-25.40  
   linux-headers-3.2.0-25 3.2.0-25.40  
   linux-headers-3.2.0-24-virtual 3.2.0-24.39  
   linux-headers-3.2.0-24-generic 3.2.0-24.39  
   linux-headers-3.2.0-24 3.2.0-24.39  
   linux-headers-3.2.0-23-lowlatency 3.2.0-23.31  
   linux-headers-3.2.0-23-virtual 3.2.0-23.36  
   linux-headers-3.2.0-23-generic 3.2.0-23.36  
   linux-headers-3.2.0-23 3.2.0-23.36  
 You should explicitly select one to install.  
 

 E: Package 'linux-headers' has no installation candidate  
 Brock@Gonad:~$ sudo apt-get install linux-headers-3.5.0-24-generic  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   libsdl-ttf2.0-0 linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic  
   language-pack-kde-zh-hans-base language-pack-kde-en kde-l10n-engb  
   language-pack-zh-hans-base kde-l10n-zhcn language-pack-zh-hans  
   language-pack-kde-zh-hans language-pack-kde-en-base  
 Use 'apt-get autoremove' to remove them.  
 The following extra packages will be installed:  
   linux-headers-3.5.0-24  
 The following NEW packages will be installed:  
   linux-headers-3.5.0-24 linux-headers-3.5.0-24-generic  
 0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.  
 Need to get 13.1 MB of archives.  
 After this operation, 70.0 MB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.5.0-24 all 3.5.0-24.37~precise1 [12.1 MB]  
 Get:2 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.5.0-24-generic amd64 3.5.0-24.37~precise1 [972 kB]  
 Fetched 13.1 MB in 5s (2,572 kB/s)                       
 Selecting previously unselected package linux-headers-3.5.0-24.  
 (Reading database ... 446325 files and directories currently installed.)  
 Unpacking linux-headers-3.5.0-24 (from .../linux-headers-3.5.0-24_3.5.0-24.37~precise1_all.deb) ...  
 Selecting previously unselected package linux-headers-3.5.0-24-generic.  
 Unpacking linux-headers-3.5.0-24-generic (from .../linux-headers-3.5.0-24-generic_3.5.0-24.37~precise1_amd64.deb) ...  
 Setting up linux-headers-3.5.0-24 (3.5.0-24.37~precise1) ...  
 Setting up linux-headers-3.5.0-24-generic (3.5.0-24.37~precise1) ...  
 Examining /etc/kernel/header_postinst.d.  
 run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic  
 Error! Bad return status for module build on kernel: 3.5.0-24-generic (x86_64)  
 Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information.  
 Brock@Gonad:~$ sudo aptitude update  
 Hit http://download.virtualbox.org precise InRelease  
 Ign http://extras.ubuntu.com precise InRelease                                   
 Ign http://security.ubuntu.com precise-security InRelease            
 Ign http://ppa.launchpad.net precise InRelease                        
 Ign http://ppa.launchpad.net precise InRelease                        
 Ign http://ppa.launchpad.net precise InRelease  
 Ign http://ca.archive.ubuntu.com precise InRelease                               
 Ign http://ca.archive.ubuntu.com precise-updates InRelease            
 Ign http://ca.archive.ubuntu.com precise-backports InRelease  
 Get: 1 http://extras.ubuntu.com precise Release.gpg [72 B]            
 Get: 2 http://security.ubuntu.com precise-security Release.gpg [198 B]           
 Ign http://ppa.launchpad.net precise InRelease                                   
 Ign http://ppa.launchpad.net precise InRelease  
 Hit http://ppa.launchpad.net precise Release.gpg  
 Hit http://ppa.launchpad.net precise Release.gpg  
 Hit http://ca.archive.ubuntu.com precise Release.gpg  
 Get: 3 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]  
 Hit http://extras.ubuntu.com precise Release                          
 Get: 4 http://security.ubuntu.com precise-security Release [49.6 kB]  
 Hit http://ppa.launchpad.net precise Release.gpg                                 
 Hit http://ppa.launchpad.net precise Release.gpg                                
 Hit http://ppa.launchpad.net precise Release.gpg  
 Hit http://ppa.launchpad.net precise Release  
 Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                   
 Hit http://ca.archive.ubuntu.com precise Release                                
 Hit http://extras.ubuntu.com precise/main Sources                                
 Hit http://ppa.launchpad.net precise Release                                    
 Hit http://ppa.launchpad.net precise Release                                    
 Hit http://ppa.launchpad.net precise Release  
 Hit http://ppa.launchpad.net precise Release  
 Get: 5 http://ca.archive.ubuntu.com precise-updates Release [49.6 kB]            
 Hit http://extras.ubuntu.com precise/main amd64 Packages                         
 Hit http://extras.ubuntu.com precise/main i386 Packages                          
 Hit http://ppa.launchpad.net precise/main Sources                                
 Ign http://extras.ubuntu.com precise/main TranslationIndex                       
 Hit http://ppa.launchpad.net precise/main amd64 Packages                        
 Hit http://ppa.launchpad.net precise/main i386 Packages                         
 Ign http://ppa.launchpad.net precise/main TranslationIndex  
 Hit http://ppa.launchpad.net precise/main Sources  
 Hit http://ppa.launchpad.net precise/main amd64 Packages  
 Hit http://ppa.launchpad.net precise/main i386 Packages                         
 Ign http://ppa.launchpad.net precise/main TranslationIndex  
 Hit http://ppa.launchpad.net precise/main Sources  
 Get: 6 http://security.ubuntu.com precise-security/main Sources [63.1 kB]        
 Hit http://ppa.launchpad.net precise/main amd64 Packages                         
 Hit http://ppa.launchpad.net precise/main i386 Packages                          
 Ign http://ppa.launchpad.net precise/main TranslationIndex                       
 Hit http://ppa.launchpad.net precise/main Sources                                
 Hit http://ppa.launchpad.net precise/main amd64 Packages  
 Hit http://ppa.launchpad.net precise/main i386 Packages  
 Ign http://ppa.launchpad.net precise/main TranslationIndex  
 Hit http://ppa.launchpad.net precise/main Sources                                
 Hit http://ppa.launchpad.net precise/main amd64 Packages                         
 Hit http://ppa.launchpad.net precise/main i386 Packages  
 Ign http://ppa.launchpad.net precise/main TranslationIndex                       
 Hit http://ca.archive.ubuntu.com precise-backports Release                       
 Get: 7 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]  
 Get: 8 http://security.ubuntu.com precise-security/universe Sources [22.2 kB]    
 Get: 9 http://security.ubuntu.com precise-security/multiverse Sources [1,382 B]  
 Get: 10 http://security.ubuntu.com precise-security/main amd64 Packages [228 kB]  
 Hit http://ca.archive.ubuntu.com precise/main Sources                            
 Hit http://ca.archive.ubuntu.com precise/restricted Sources                     
 Hit http://ca.archive.ubuntu.com precise/universe Sources  
 Hit http://ca.archive.ubuntu.com precise/multiverse Sources  
 Hit http://ca.archive.ubuntu.com precise/main amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise/restricted amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise/universe amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise/multiverse amd64 Packages               
 Hit http://ca.archive.ubuntu.com precise/main i386 Packages                      
 Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages  
 Hit http://ca.archive.ubuntu.com precise/universe i386 Packages                  
 Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages                
 Hit http://ca.archive.ubuntu.com precise/main TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex               
 Get: 11 http://ca.archive.ubuntu.com precise-updates/main Sources [367 kB]       
 Get: 12 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]  
 Get: 13 http://security.ubuntu.com precise-security/universe amd64 Packages [68.2 kB]  
 Ign http://ppa.launchpad.net precise/main Translation-en_CA                      
 Ign http://ppa.launchpad.net precise/main Translation-en                         
 Get: 14 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,193 B]  
 Get: 15 http://security.ubuntu.com precise-security/main i386 Packages [237 kB]  
 Ign http://extras.ubuntu.com precise/main Translation-en_CA                      
 Ign http://ppa.launchpad.net precise/main Translation-en_CA                      
 Ign http://ppa.launchpad.net precise/main Translation-en  
 Ign http://ppa.launchpad.net precise/main Translation-en_CA                      
 Ign http://ppa.launchpad.net precise/main Translation-en                         
 Ign http://ppa.launchpad.net precise/main Translation-en_CA  
 Ign http://ppa.launchpad.net precise/main Translation-en  
 Ign http://extras.ubuntu.com precise/main Translation-en                         
 Get: 16 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]  
 Get: 17 http://security.ubuntu.com precise-security/universe i386 Packages [69.9 kB]  
 Get: 18 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,368 B]  
 Hit http://security.ubuntu.com precise-security/main TranslationIndex            
 Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex  
 Hit http://security.ubuntu.com precise-security/restricted TranslationIndex  
 Hit http://security.ubuntu.com precise-security/universe TranslationIndex  
 Ign http://ppa.launchpad.net precise/main Translation-en_CA                     
 Ign http://ppa.launchpad.net precise/main Translation-en                      
 Hit http://security.ubuntu.com precise-security/main Translation-en           
 Hit http://security.ubuntu.com precise-security/multiverse Translation-en  
 Hit http://security.ubuntu.com precise-security/restricted Translation-en  
 Hit http://security.ubuntu.com precise-security/universe Translation-en  
 Get: 19 http://ca.archive.ubuntu.com precise-updates/restricted Sources [5,135 B]  
 Get: 20 http://ca.archive.ubuntu.com precise-updates/universe Sources [79.2 kB]  
 Get: 21 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [4,725 B]  
 Get: 22 http://ca.archive.ubuntu.com precise-updates/main amd64 Packages [582 kB]  
 Get: 23 http://ca.archive.ubuntu.com precise-updates/restricted amd64 Packages [9,565 B]  
 Get: 24 http://ca.archive.ubuntu.com precise-updates/universe amd64 Packages [182 kB]  
 Get: 25 http://ca.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,421 B]  
 Get: 26 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [593 kB]  
 Get: 27 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [9,503 B]  
 Get: 28 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [184 kB]  
 Get: 29 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]  
 Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex           
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex     
 Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-backports/main Sources  
 Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources  
 Hit http://ca.archive.ubuntu.com precise-backports/universe Sources  
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources  
 Hit http://ca.archive.ubuntu.com precise-backports/main amd64 Packages           
 Hit http://ca.archive.ubuntu.com precise-backports/restricted amd64 Packages     
 Hit http://ca.archive.ubuntu.com precise-backports/universe amd64 Packages       
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages            
 Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages        
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex         
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex   
 Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex     
 Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA  
 Hit http://ca.archive.ubuntu.com precise/main Translation-en  
 Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en               
 Hit http://ca.archive.ubuntu.com precise/restricted Translation-en               
 Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA              
 Hit http://ca.archive.ubuntu.com precise/universe Translation-en  
 Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA          
 Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en             
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en  
 Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en       
 Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA  
 Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en     
 Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en       
 Fetched 2,840 kB in 16s (172 kB/s)                                               
 W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/InRelease  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)  
 

 E: Some index files failed to download. They have been ignored, or old ones used instead.  
 

 Brock@Gonad:~$ sudo aptitude install dkms  
 No packages will be installed, upgraded, or removed.  
 0 packages upgraded, 0 newly installed, 0 to remove and 16 not upgraded.  
 Need to get 0 B of archives. After unpacking 0 B will be used.  
                                           
 Brock@Gonad:~$ sudo /etc/init.d/vboxdrv setup  
 Brock@Gonad:~$ sudo apt-get install linux-headers-3.5.0-24-generic  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 linux-headers-3.5.0-24-generic is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.  
 Brock@Gonad:~$ sudo apt-get update  
 Hit http://download.virtualbox.org precise InRelease  
 Ign http://security.ubuntu.com precise-security InRelease                       
 Hit http://security.ubuntu.com precise-security Release.gpg                     
 Ign http://extras.ubuntu.com precise InRelease                                  
 Ign http://ppa.launchpad.net precise InRelease                        
 Ign http://ppa.launchpad.net precise InRelease                        
 Ign http://ppa.launchpad.net precise InRelease                        
 Ign http://ca.archive.ubuntu.com precise InRelease                              
 Ign http://ca.archive.ubuntu.com precise-updates InRelease                      
 Ign http://ca.archive.ubuntu.com precise-backports InRelease          
 Hit http://security.ubuntu.com precise-security Release               
 Hit http://extras.ubuntu.com precise Release.gpg                                
 Hit http://security.ubuntu.com precise-security/main Sources          
 Ign http://ppa.launchpad.net precise InRelease                        
 Ign http://ppa.launchpad.net precise InRelease                        
 Hit http://ppa.launchpad.net precise Release.gpg                      
 Hit http://ppa.launchpad.net precise Release.gpg                      
 Hit http://ca.archive.ubuntu.com precise Release.gpg                  
 Hit http://ca.archive.ubuntu.com precise-updates Release.gpg                    
 Hit http://security.ubuntu.com precise-security/restricted Sources              
 Hit http://security.ubuntu.com precise-security/universe Sources                
 Hit http://security.ubuntu.com precise-security/multiverse Sources              
 Hit http://security.ubuntu.com precise-security/main amd64 Packages             
 Hit http://security.ubuntu.com precise-security/restricted amd64 Packages       
 Hit http://security.ubuntu.com precise-security/universe amd64 Packages         
 Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages  
 Hit http://security.ubuntu.com precise-security/main i386 Packages    
 Hit http://security.ubuntu.com precise-security/restricted i386 Packages        
 Hit http://security.ubuntu.com precise-security/universe i386 Packages          
 Hit http://extras.ubuntu.com precise Release                                    
 Hit http://ppa.launchpad.net precise Release.gpg                                
 Hit http://ppa.launchpad.net precise Release.gpg                      
 Hit http://ppa.launchpad.net precise Release.gpg                      
 Hit http://ppa.launchpad.net precise Release                          
 Hit http://security.ubuntu.com precise-security/multiverse i386 Packages        
 Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                  
 Hit http://security.ubuntu.com precise-security/main TranslationIndex           
 Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex     
 Hit http://security.ubuntu.com precise-security/restricted TranslationIndex     
 Hit http://security.ubuntu.com precise-security/universe TranslationIndex       
 Hit http://extras.ubuntu.com precise/main Sources                               
 Hit http://ppa.launchpad.net precise Release                          
 Hit http://ppa.launchpad.net precise Release                                    
 Hit http://ppa.launchpad.net precise Release                                    
 Hit http://ppa.launchpad.net precise Release                                    
 Hit http://security.ubuntu.com precise-security/main Translation-en             
 Hit http://security.ubuntu.com precise-security/multiverse Translation-en       
 Hit http://security.ubuntu.com precise-security/restricted Translation-en       
 Hit http://ca.archive.ubuntu.com precise Release                                
 Hit http://security.ubuntu.com precise-security/universe Translation-en         
 Hit http://ppa.launchpad.net precise/main Sources                               
 Hit http://ca.archive.ubuntu.com precise-updates Release              
 Hit http://extras.ubuntu.com precise/main amd64 Packages                        
 Hit http://extras.ubuntu.com precise/main i386 Packages               
 Ign http://extras.ubuntu.com precise/main TranslationIndex            
 Hit http://ppa.launchpad.net precise/main amd64 Packages              
 Hit http://ppa.launchpad.net precise/main i386 Packages  
 Ign http://ppa.launchpad.net precise/main TranslationIndex            
 Hit http://ppa.launchpad.net precise/main Sources                     
 Hit http://ppa.launchpad.net precise/main amd64 Packages  
 Hit http://ppa.launchpad.net precise/main i386 Packages  
 Ign http://ppa.launchpad.net precise/main TranslationIndex            
 Hit http://ppa.launchpad.net precise/main Sources                     
 Hit http://ca.archive.ubuntu.com precise-backports Release  
 Hit http://ca.archive.ubuntu.com precise/main Sources                           
 Hit http://ca.archive.ubuntu.com precise/restricted Sources                     
 Hit http://ca.archive.ubuntu.com precise/universe Sources              
 Hit http://ca.archive.ubuntu.com precise/multiverse Sources            
 Hit http://ca.archive.ubuntu.com precise/main amd64 Packages                    
 Hit http://ppa.launchpad.net precise/main amd64 Packages                        
 Hit http://ppa.launchpad.net precise/main i386 Packages               
 Ign http://ppa.launchpad.net precise/main TranslationIndex            
 Hit http://ppa.launchpad.net precise/main Sources                     
 Hit http://ppa.launchpad.net precise/main amd64 Packages              
 Hit http://ppa.launchpad.net precise/main i386 Packages               
 Ign http://ppa.launchpad.net precise/main TranslationIndex            
 Hit http://ca.archive.ubuntu.com precise/restricted amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise/universe amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise/multiverse amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise/main i386 Packages  
 Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages     
 Hit http://ca.archive.ubuntu.com precise/universe i386 Packages       
 Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages     
 Hit http://ca.archive.ubuntu.com precise/main TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex  
 Hit http://ppa.launchpad.net precise/main Sources                     
 Hit http://ppa.launchpad.net precise/main amd64 Packages              
 Hit http://ppa.launchpad.net precise/main i386 Packages               
 Ign http://ppa.launchpad.net precise/main TranslationIndex            
 Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex    
 Hit http://ca.archive.ubuntu.com precise-updates/main Sources         
 Hit http://ca.archive.ubuntu.com precise-updates/restricted Sources   
 Hit http://ca.archive.ubuntu.com precise-updates/universe Sources     
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse Sources   
 Hit http://ca.archive.ubuntu.com precise-updates/main amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/restricted amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/universe amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/main i386 Packages   
 Hit http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/universe i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-backports/main Sources       
 Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources  
 Hit http://ca.archive.ubuntu.com precise-backports/universe Sources   
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources  
 Hit http://ca.archive.ubuntu.com precise-backports/main amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/restricted amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/universe amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse amd64 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages  
 Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex  
 Ign http://ppa.launchpad.net precise/main Translation-en_CA           
 Ign http://ppa.launchpad.net precise/main Translation-en              
 Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex  
 Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA       
 Hit http://ca.archive.ubuntu.com precise/main Translation-en          
 Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en    
 Hit http://ca.archive.ubuntu.com precise/restricted Translation-en  
 Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA  
 Hit http://ca.archive.ubuntu.com precise/universe Translation-en      
 Ign http://ppa.launchpad.net precise/main Translation-en_CA           
 Ign http://ppa.launchpad.net precise/main Translation-en  
 Ign http://extras.ubuntu.com precise/main Translation-en_CA  
 Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA  
 Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en  
 Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en  
 Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en  
 Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA  
 Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en  
 Ign http://ppa.launchpad.net precise/main Translation-en_CA           
 Ign http://ppa.launchpad.net precise/main Translation-en              
 Ign http://ppa.launchpad.net precise/main Translation-en_CA  
 Ign http://ppa.launchpad.net precise/main Translation-en  
 Ign http://ppa.launchpad.net precise/main Translation-en_CA  
 Ign http://ppa.launchpad.net precise/main Translation-en  
 Ign http://extras.ubuntu.com precise/main Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en  
 Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en  
 W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/InRelease  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)  
 

 E: Some index files failed to download. They have been ignored, or old ones used instead.  
 Brock@Gonad:~$ sudo apt-get install linux-headers-3.5.0-24-generic  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 linux-headers-3.5.0-24-generic is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.  
 Brock@Gonad:~$ sudo aptitude install dkms  
 No packages will be installed, upgraded, or removed.  
 0 packages upgraded, 0 newly installed, 0 to remove and 16 not upgraded.  
 Need to get 0 B of archives. After unpacking 0 B will be used.  
                                           
 Brock@Gonad:~$ sudo /etc/init.d/vboxdrv setup  
 Brock@Gonad:~$  
  
```There is something wrong with my sources or my virtual box Key and i don't know how to fix it.

---

### Post by CharlesA on 2013-02-23
It should be either:

```
linux-headers-generic
```

**OR**

```
linux-headers-server
```

Depending if you have the server or desktop version of Ubuntu installed.

---

### Post by corswors on 2013-02-25
Dont worry about the sources for VB mine does the same the uwstion is is your VB working now ? This is what this forum question is all about ! :P):P

---

### Post by aeb105 on 2013-02-25
I am having the same problems.  It can't find the vbox directory like those above.   After I try the Linux headers as suggested, I get this error.:
[B]
"Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Error! Bad return status for module build on kernel: 3.5.0-24-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information."[/B]

---

### Post by CharlesA on 2013-02-25
Check the make.log for more info. It's likely something is broken.

---

### Post by aeb105 on 2013-02-25
Can you tell me what is wrong?   This is what I get:

[B]DKMS make.log for virtualbox-4.1.12 for kernel 3.5.0-24-generic (x86_64)
Mon Feb 25 09:36:46 EST 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-24-generic'
  LD      /var/lib/dkms/virtualbox/4.1.12/build/built-in.o
  LD      /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/linux/SUPDrv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/SUPDrv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/SUPDrvSem.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/alloc-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/initterm-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/memobj-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/mpnotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/powernotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/assert-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/alloc-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/initterm-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o
/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c: In function &#8216;rtR0MemObjLinuxDoMmap&#8217;:
/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1150:9: error: implicit declaration of function &#8216;do_mmap&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/virtualbox/4.1.12/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-24-generic'[/B]

---

### Post by CharlesA on 2013-02-25
You could try purging and reinstalling virtualbox and seeing if the error message goes away.

If the problem still persists, you might want to make a thread on virtualbox.org.

---

### Post by aeb105 on 2013-02-26
I get same response.   Does that output above give any clue as to what is going on or what I need to do?

---

### Post by CharlesA on 2013-02-26
> **aeb105 said:**
> I get same response.   Does that output above give any clue as to what is going on or what I need to do?

Purge the ose edition and install the version from virtualbox.org.
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

4.1.12 was released in April of last year, so it's probably not compatibly with 3.5.x kernels.

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1129474](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1129474)

EDIT: It looks like there was a patch released via PPA for the version of vbox in the Precise repos, you can find it in comment 3 and 4:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1081307](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1081307)

---

### Post by aeb105 on 2013-02-27
Thanks Charles!   Downloaded the package from the site per your liink above.   That worked!:p

---

### Post by biometricstu on 2013-03-19
Many thanks Lin-Lin_224, I updated my Ubuntu 12.04 today and my Virtualbox stopped working, you are a life (well time) saver as I thought a re-install was going to be my only solution, but your info fixed the problem.

Thanks again

Stu :-)

---

### Post by Mickoush on 2013-05-19
> **lin-lin_224 said:**
> 
 The commands are:
                                 [FONT=AR PL UMing TW]
[/FONT]
[FONT=AR PL UMing TW]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]
 
Good luck&#65281;
;)

Worked perfect for me! THX a lot! :)

---

### Post by stegfeld on 2013-06-25
hey,

all of your tips didnt help for me.. the command
```
/etc/init.d/vboxdrv setup
```

works as long as I don't restart my PC.. after the reboot I have to do the same again..

if I hit
```
[FONT=AR PL UMing TW]sudo aptitude update
[/FONT]
```
I get
```
Treffer http://ftp.de.debian.org wheezy Release.gpg
Treffer http://ftp.de.debian.org wheezy Release                                                   
Treffer http://ftp.de.debian.org wheezy/main Sources                                              
Treffer http://ftp.de.debian.org wheezy/non-free Sources        
Treffer http://ftp.de.debian.org wheezy/contrib Sources         
Treffer http://download.virtualbox.org wheezy Release.gpg       
Treffer http://ftp.de.debian.org wheezy/main amd64 Packages     
Treffer http://ftp.de.debian.org wheezy/non-free amd64 Packages 
Treffer http://ftp.de.debian.org wheezy/contrib amd64 Packages  
Treffer http://ftp.de.debian.org wheezy/main i386 Packages      
Treffer http://download.virtualbox.org wheezy Release           
Treffer http://ftp.de.debian.org wheezy/non-free i386 Packages  
Treffer http://ftp.de.debian.org wheezy/contrib i386 Packages   
Treffer http://ftp.de.debian.org wheezy/contrib Translation-en  
Treffer http://download.virtualbox.org wheezy/contrib amd64 Packages
Treffer http://ftp.de.debian.org wheezy/main Translation-de_DE  
Treffer http://ftp.de.debian.org wheezy/main Translation-de     
Treffer http://ftp.de.debian.org wheezy/main Translation-en     
Treffer http://download.virtualbox.org wheezy/contrib i386 Packages
Treffer http://ftp.de.debian.org wheezy/non-free Translation-en 
Treffer http://security.debian.org wheezy/updates Release.gpg   
Treffer http://security.debian.org wheezy/updates Release
Treffer http://security.debian.org wheezy/updates/main Sources
Treffer http://security.debian.org wheezy/updates/main amd64 Packages
Treffer http://security.debian.org wheezy/updates/main i386 Packages
Treffer http://security.debian.org wheezy/updates/main Translation-en
Ign http://download.virtualbox.org wheezy/contrib Translation-de_DE
Ign http://download.virtualbox.org wheezy/contrib Translation-de
Ign http://download.virtualbox.org wheezy/contrib Translation-en

```

after this I hit
```
[FONT=AR PL UMing TW]sudo aptitude install dkms[/FONT]
```
and I get
0 updated, 0 added, 0 deleted

then I hit
```
[FONT=AR PL UMing TW]sudo /etc/init.d/vboxdrv setup[/FONT]
```
and I get
```
[ ok ] Stopping VirtualBox kernel modules:.
[ ok ] Uninstalling old VirtualBox DKMS kernel modules:.
[ ok ] Trying to register the VirtualBox kernel modules using DKMS:.
[ ok ] Starting VirtualBox kernel modules:.

```

well, as I already said, it works, as long as I don't restart my PC..

whats wrong? could it be a rights-problem?

---

### Post by stegfeld on 2013-06-26
heelp!! :confused:

---

### Post by CharlesA on 2013-06-26
I don't use virtualbox anymore but you could check to see if the kernel modules are actually loaded or not after a reboot.

What do you get back if you run this after a reboot:

```
lsmod | grep vbox
```

---

### Post by stegfeld on 2013-06-26
after a reboot there is no output,

when I execute this command
```

/etc/init.d/vboxdrv setup
```

I get

```
vboxpci                19096  0 
vboxnetadp             25443  0 
vboxnetflt             23608  0 
vboxdrv               217233  3 vboxnetflt,vboxnetadp,vboxpci

```

what can I do?

---

### Post by CharlesA on 2013-06-26
OK, it might be a problem with Vbox on Wheezy. I would suggest making a thread on the virtualbox forums and seeing what they say.
[https://forums.virtualbox.org/](https://forums.virtualbox.org/)

---

### Post by stegfeld on 2013-06-27
they seem to be on vacation.. no answer after two days.. :(
I tried to add 
```
@reboot .../vbox.sh
```
this on /etc/crontab

in this vbox.sh script there is only

```
#!/bin/sh
#
/etc/init.d/vboxdrv setup

```

but it doesn't work as well.. I still have to execute this vboxdrv setup after every reboot/logon

---

### Post by stegfeld on 2013-06-27
solution:
change line #32 at /etc/init.d/virtualbox (as root)

```
test -d /usr/share/doc/virtualbox -a -x /usr/bin/VBoxHeadless || exit 0
```

to

```
test -d /usr/share/doc/virtualbox-4.2 -a -x /usr/bin/VBoxHeadless || exit 0
```

---

### Post by CharlesA on 2013-06-27
You'd need to run it in a root crontab and reference it via full path. If that still doesn't work, you could try purging vbox *and* all the extra junk it pulls in and then reinstalling it to see if that fixes it.

EDIT: I guess the uninstall script didn't clean up after itself. >.<

---

### Post by one-up on 2013-08-03
I had the same problem and I tried to reinstall virtualbox, the 'dkms' package, run '/etc/init.d/vboxdrv setup' or add 'vboxdrv' to '/etc/modules' but nothing worked. For me the solution was to install the 'virtualbox-dkms' package by running 'sudo apt-get install virtualbox-dkms'

---

### Post by Steve H on 2014-01-19
> **herkots said:**
> Hi,

I found a solution for the reboot problem from here: [http://ubuntuforums.org/showthread.php?t=1313989](http://ubuntuforums.org/showthread.php?t=1313989)

You just have to log in as a root and add one line code in a file:  /etc/modules

The line is: vboxdrv

Then save, reboot and log in a usual. Worked for me.

That worked for me on Debian Wheezy. Many thanks.

---

### Post by Burley_Gwaltney on 2014-03-03
> **slibuntu said:**
> If you are having this problema nd the previous solutions don't work for you, try this - 

Run (in a terminal)

```
sudo ls /etc/init.d
```

Look for somethis like vbox, or virtualbox (on mine it was virtualbox-ose)

Then run 

```
sudo /etc/init.d/*whatever-it-is-in-yours* restart
```

If you get errors there, post them here

This worked for me! Thanks for this.

---

### Post by _SoNiC_ on 2014-03-19
Thanks bro it's worked for me ;)

---

### Post by marsanyi on 2014-04-25
For those for whom /etc/init.d/vboxdrv doesn't exist, you might try this:

[FONT=Ubuntu Mono]sudo apt-get install --reinstall virtualbox-dkms

Even though I had virtualbox-dkms installed, I had to force a reinstall to trigger the rebuild of the kernel module, which fixed things.  I'm running 12.04LTS, did the normal update today (April 25)[/FONT]

---

### Post by Sagar_Gorijala on 2014-05-28
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

Solved my problem.

---

### Post by ryan-arnold-k on 2014-07-21
i juast started getting this error after a suggested software update.

i ran:
[COLOR=#000000]udo apt-get remove virtualbox-dkms[/COLOR]
[COLOR=#000000]sudo apt-get install virtualbox-dkms

removal worked fine, reinstall ended with the following error:
[/COLOR]Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.6_all.deb) ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.6) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-32-generic
Building initial module for 3.13.0-32-generic
Error! Bad return status for module build on kernel: 3.13.0-32-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.1.12/build/make.log for more information.

what did i break?
[COLOR=#000000]
[/COLOR]

---

### Post by oldpilsbury on 2014-08-27
> I have also this problem, and i have tried the solution in this thread, but it just do not work. I use the PUEL version of virtualbox and i have also tried with the OSE version. None of them work. 



I have tried the 



 	Code:
 	sudo /etc/init.d/vboxdrv setup 
But this is what comes out. 


bash: /etc/init.d/vboxdrv: No such file or directory


Do anybody have some solutions on my problem? 				

In Linux Mint 17 I received the same error. I had a looksee and there is no vboxdrv in /etc/init.d/. There is a script called virtualbox.

> sudo ./virtualbox force-reload

Success.

---

### Post by ahmad10 on 2014-10-08
Well, just use these commands

```
cd /etc/init.d
```
```
sudo ./vboxdrv setup
```

And that's it

---

### Post by steve186 on 2015-02-04
So I had this issue and nothing here worked. I had tried to reinstall virtualbox without success. So here is what worked for me:

sudo apt-get remove --purge virtualbox
--- I rebooted, not sure if I needed to.
--- here I went to root, not sure if I needed to but I did it anyway
su
apt-get install virtualbox
--- rebooted again and works fine now.  The reason I just 'su' over 'sudo' was per the permission errors and in the past sudo sometimes hasn't made the cut.


hope this helps someone.

---

### Post by javier38 on 2015-02-19
try this command:

apt-get install dkms

sudo /etc/init.d/vboxdrv setup

good luck

---

### Post by uRock on 2015-02-20
I'm having the same issue. Totally regretting installing the latest release from Oracle. ```
sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMSError! Your kernel headers for kernel 3.13.0-35-generic cannot be found.
Please install the linux-headers-3.13.0-35-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

```**Edit:** Went into Synaptic and installed linux-headers-3.13.0-35-generic, then reran the above command.```
sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...done.
```Fixed the issue. Virtualbox now runs with no problems.

---

### Post by monkeyman2 on 2015-04-24
[COLOR=#000000][FONT=Lucida Grande]**SOLUTION**[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]Took me a long time to solve this issue. Had this problem with vBox across 2 distros (Ubuntu and Arch).[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]I had dkms and all the modules already installed and compiled into my kernel, yet I still got a module related error message when I tried to run a vBox virtual machine.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]**If your vBox GUI starts without a hitch but get an error telling you to install the VBoxDrv kernel module (or any other modules) when you try to run a virtual machine, your problems are not related to installing the modules into your kernel but ACTIVATING THEM in modprobe which the module installation script fails to do.**[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]To load a module manually (such as vboxdrv), open a terminal prompt and put in :[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]sudo modprobe vboxdrv[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]if your error message is telling you that your missing another module, be sure to activate it as well.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]If you Virtual Machine runs after that without giving you an error message, you've found the solution. Then you can activate the vboxdrv module permanently by going to /etc/modules-load.d/ (or whatever .d directory your modprobe uses) and making a .conf file within it (such as vbox.conf). In the .conf file, put in the names of the vbox kernel modules you want to add, such as: vboxdrv and optionally vboxnetadp, vboxnetflt and vboxpci. If you don't know what they do, see the excerpt below that I took out of vBox's wiki. Save the .conf file and reboot[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]**From Vbox's wiki:**[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]vboxnetadp and vboxnetflt are both needed when you intend to use the "Host-only networking" feature. More precisely, vboxnetadp is needed to create the host interface in the VirtualBox global preferences, and vboxnetflt is needed to launch a virtual machine using that network interface.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]vboxpci is needed when your virtual machine needs to pass through a PCI device on your host.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]Note: If the VirtualBox kernel modules were loaded in the kernel while you updated the modules, you need to reload them manually to use the new updated version. To do it, run vboxreload as root.[/FONT][/COLOR]

---

### Post by ruvapost on 2015-10-28
> **lin-lin_224 said:**
> 
....[FONT=AR PL UMing TW][/FONT]
 [FONT=AR PL UMing TW]And I just typed the three lines commands one by one, then the Virtualbox worked.
[/FONT]The commands are:                    [FONT=AR PL UMing TW]
[/FONT][FONT=AR PL UMing TW]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]

..
;)

This work for me... yehaa!

---

### Post by Manuel_G_Leon on 2016-02-07
Thanks! I just used [FONT=AR PL UMing TW]sudo /etc/init.d/vboxdrv setup
It recompiles the drivers and works again

[/FONT]

---

