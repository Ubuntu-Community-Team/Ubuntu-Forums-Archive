---
title: "How do I install OSX Snow Leopard (bought CD) in VirtualBox 4.1.2"
date: 2011-09-14
forum: Virtualisation
---

### Post by charleswb on 2011-09-14
**My Background**:

Sadly, I am only moderately computer literate, and less than that with Ubuntu. I am fairly new to Ubuntu. I have mastered the GUI well, but only a beginner at Terminal Window. I am also a beginner to OSX.

What I do know some more about is Windows and also VirtualBox, but I'm fed up with Windows and trying to learned more about Ubuntu, VirtualBox, and now also OSX. I do have several version of Windows installed in VirtualBox. So I have some experience with VBox there.

[B]
Here are my problems and goals:[/B]

I have Ubuntu 64-bit V11.04 on a Dell with 1 Intel processor, 4 cores.

I have VirtualBox 4.1.2 installed.

I want to install OSX Snow Leopard as a guest operating system in VirtualBox.
[COLOR=DarkRed]
**I do NOT want to install the Hackintosh by Hazard version of OSX.**[/COLOR]
[COLOR=Navy][B]
I want to install my OSX Snow Leopard CD that I purchased.[/B][/COLOR][INDENT]I have tried the instructions I found at [http://www.sysprobs.com/install-mac-snow-leopard-1063-oracle-virtualbox-32-apple-intel-pc](http://www.sysprobs.com/install-mac-snow-leopard-1063-oracle-virtualbox-32-apple-intel-pc)[INDENT]It got Empire boot loader loaded. I wasn't sure if I should use the Intel or AMD version for my 64 bit Intel. So I tried both versions of Empire boot loader. Both successfully started boot loader, but then failed to do anything after I put in the OSX CD and pressed F5.
The AMD version of Empire did nothing after putting OSX CD. 

The Intel version of Empire gave lots of EBIOS error messages on-screen in Empire boot loader program. Then installation stops.
[/INDENT]I also tried the instructions given by Geeknizer, but those failed as well. I don't remember the details now, but I do remember that those instructions were for PC host computer, not Ubuntu host.

[/INDENT][B]
Summary:

Can anyone please give me some step-by-step instructions?[/B] For how to install my Snow Leopard CD as a Guest OS in VirtualBox 4.1.2. My host OS is Ubuntu 64-bit V11.04.

---

### Post by Mr.Deek on 2011-10-03
Hello,

I am trying the same With MAC OSX 10.6.6 retail dvd.

My Speck: 
VBox 4.1.2
Intel i7 x32/x64 (Win7x64 root OS)
and
Intel Core2 Duo x32/x64 (Ubuntu x64 root OS)

1. First turn off the EFI in vbox settings
2. Have only the boot iso (empireEFIv1085.iso) loaded in the cd-rom and HDD.
3. Boot the Empire.ISO
4. When the Black screen loads with f5, swap the empire.iso for the real DVD using vbox settings, wait 5 secconds. 
5. Note that the cd image will change to OSX from Empire.
6. Press enter to start!
7. Press enter at (x32 / x64) detection message... wait 1 min and you should have the OSX install screen. 

This is where I am stuck, and will update you as I get futher.

Thank you.

---

### Post by sisco311 on 2011-10-03
It's against the EULA for Mac OS X 10.6 to run the OS in a virtual machine.

The EULA for Mac OS X Server 10.5 and 10.6 and Mac OS X Server/Client 10.7 allows you to run the OS in a virtual machine, but only inside OS X on an Apple hardware.

Thread Closed.

---

