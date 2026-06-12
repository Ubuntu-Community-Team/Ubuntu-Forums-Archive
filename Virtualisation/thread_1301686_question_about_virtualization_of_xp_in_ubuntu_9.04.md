---
title: "question about virtualization of xp in ubuntu 9.04"
date: 2009-10-26
forum: Virtualisation
---

### Post by smokyink on 2009-10-26
I am a noob to virtualization and I have been using ubuntu for a couple of months now...

But I still miss gaming and I'm not keen on rebooting my machine every time I want to play a game.

I tried wine a couple of times but it doesn't seem to work properly...maybe because I don't have the ati drivers installed (but every time I install video drivers it leads to some buggy screen, so I decided that I wont bother with it any more)

:PSo I am considering gaming on a virtual XP machine.

The games I play are not necessarily the newest nor the heaviest,
I play mostly adventure games...so here is an example of system requirements of still life 2:

  [html]  Windows®  XP/VistaTM
    1,5 GHz Intel Pentium® 4
    RAM 512 MB
    Video Card 128 MB DirectX® 9 Compatible
    Disk Space 4 GB Free
    CR-ROM 16x
    Sound Card, Mouse, Keyboard  DirectX® 9 Compatible[/html]And my machine spec:
    
     [html] Ubuntu 9.04 (jaunty)
      Asus P5LD2-FM/S
      Intel pentium D 930 3GHz (dual core, so collective 6GHz)
      RAM 2GB DDR2
      video: Ati Radeon X1600(or 1650 dont remember which) - 512MB (ATI Technologies Inc RV516 XT   Radeon X1600 Series)
      2 monitors[/html] -----------------------------------------------------------------------------------------------------------------------------------------     
:popcorn: Now my question:

 Which virtualization would you recommend (I am mostly interested in free solutions), which program?
 
Can I install drivers (video, sound...etc.) on the virtual machine?

---

### Post by stlsaint on 2009-10-26
I recommend [VirtualBox ]("http://gwos.org/udsf/doku.php/software:virtualbox")and yes its free!:)

---

### Post by smokyink on 2009-10-26
Thanks for the reply: [stlsaint]("http://ubuntuforums.org/member.php?u=814785")

Would I be able to install drivers in the XP for the video card??

And would I be able to play games on it?

---

### Post by howefield on 2009-10-26
You would have to go with the drivers supplied by Virtualbox, which hava experimental 3D Acceleration implementation.

Whether that is good enough for your game(s) I don't know. If no one can help you here, try the virtualbox forums as well.

---

### Post by chipper_farley on 2009-10-26
Make sure to enable virtualization support on your CPU.  Usually, it is disable in the BIOS by default so reboot and go into the BIOS and turn it on.  You should check and see if your CPU supports nested paging as some of the newer ones do.  When you configure Virtualbox, enable the VT-x support and, if it is supported by your CPU, nested paging.  These settings will improve performance, possibly significantly.  Still, you're going to take a hit since you're running in a VM.  Another major performance booster is setup your VM's hard drive on an external drive, like a USB drive. This will eliminate contingency between the host and guess as they access the disk.

---

### Post by smokyink on 2009-10-26
> Make sure to enable virtualization support on your CPU. Usually, it is disable in the BIOS by default so reboot and go into the BIOS and turn it on. You should check and see if your CPU supports nested paging as some of the newer ones do. When you configure Virtualbox, enable the VT-x support and, if it is supported by your CPU, nested paging. These settings will improve performance, possibly significantly. Still, you're going to take a hit since you're running in a VM. Another major performance booster is setup your VM's hard drive on an external drive, like a USB drive. This will eliminate contingency between the host and guess as they access the disk.

Thanks. I did enable Hyper threading which I think is for virtualization...



> **howefield said:**
> You would have to go with the drivers supplied by Virtualbox, which hava experimental 3D Acceleration implementation.

Whether that is good enough for your game(s) I don't know. If no one can help you here, try the virtualbox forums as well.


Hmm...I will try it but, Is there any other program with which I can install XP in Ubuntu?

One that actually uses the XP drivers?

---

### Post by shaggy999 on 2009-10-27
> **smokyink said:**
> Thanks. I did enable Hyper threading which I think is for virtualization...

Hyperthreading has nothing to do with virtualization. Modern CPUs have multi-stage instruction execution, meaning an instruction is broken down into chunks and seperated into different tasks. Some instructions involve tasks that take a long time, slowing down the instruction pipeline. Hyperthreading allows the unused portions of the CPU to execute parts of instructions that are coming up behind the instruction that's blocking everything. It is done in a way such that there "appears" to be 2 CPUs when there's really only one, so the operating system allocates different threads to each CPU when in reality there is only one. It sometimes results in a performance boost, sometimes it's detrimental. At least during the P4 era it was mostly a gimmick. It went away and then Intel brought this feature back with the core i7's, and apparently the new version of hyper-threading on these processors gives a decent performance boost.




> 
Hmm...I will try it but, Is there any other program with which I can install XP in Ubuntu?

One that actually uses the XP drivers?

When you install XP in virtualbox you are installing into an emulated environment. There is no nVidia card or ATI card for XP to talk to. It talks to a "virtual" graphics card that is really just a software program that translates instructions into something that the host OS can understand. The host OS then passes instructions along to the graphics card using the Host OS drivers. If linux doesn't see the graphics card or doesn't have the proper drivers loaded, that means the guest OS isn't going to be able to utilize it.

---

### Post by smokyink on 2009-10-27
Originally posted by: [shaggy999]("http://ubuntuforums.org/member.php?u=319156")

> When you install XP in virtualbox you are installing into an emulated environment. There is no nVidia card or ATI card for XP to talk to. It talks to a "virtual" graphics card that is really just a software program that translates instructions into something that the host OS can understand. The host OS then passes instructions along to the graphics card using the Host OS drivers. If linux doesn't see the graphics card or doesn't have the proper drivers loaded, that means the guest OS isn't going to be able to utilize it.

About the virtualization I was asking because I read in wikipedia that there were two methods of virtualization ([wikipedia]("http://http://en.wikipedia.org/wiki/Virtual_machine#Techniques")):Type 1 and Type 2

Where in type 1 (native) the hardware is directly used(or did I misunderstand?), so I thought if it is listed in wikkipedia maybe Linux has it?

Well then I need to think about ati drivers...again...I tried with Envy last time and it didn't work properly. 

How do I check which driver is currently in use? (I haven't installed any so it should be the binary provided with ubuntu 9.04, but just  in case...) 


Would anyone recommend a method for installing, and  driver to install (I have two monitors as twin view)?

---

