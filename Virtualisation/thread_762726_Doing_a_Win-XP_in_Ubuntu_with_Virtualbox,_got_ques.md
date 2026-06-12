---
title: "Doing a Win-XP in Ubuntu with Virtualbox, got questions !"
date: 2008-04-22
forum: Virtualisation
---

### Post by Browser_ice on 2008-04-22
I am currently using Virtualbox for the first time and installing Windows XP. I haven't finished doing it. Still in progress and this is a test to see if I can go all the way.

I have a few questions that probably everyone will go through. Some I will probably find the answer on my own, but others no. If you have any comments, go ahead.

1) In the Windows XP installation when it asks if my PC is connected to internet via network or directly, which one should I choose ?
==>> I am assuming directly.. Finished installing XP and since its updating itself, then looks like Internet access is ok. Will have to test IE7.

2) Lets say one day I want to have my VM XP to be using a 2nd monitor to itself (full screen) and my main monitor for Ubuntu. **How would I do this ?**

3) How do I enable XP auto updates ?
==>> never mind after I finished installing XP, seams they are enabled. In fact, I am updating XP right now.

4) This installation is only a test for me to see if I can use my XP softwares in a virtual way. But lets say everything works and I DO want to go VM all the way, then I will reformat my PC, install Ubuntu as the main OS but when it will be time to re-install XP. **How can I use my current XP in my test to be backed up and inserted into my full PC install ? **So I don't go through the whole XP installation again (so many updates to do !).

5) I asked in a previous thread how to use a fixed disk instead of a dynamic one. Someone answered it can mess up my whole system and pointed me to the Virtualbox PDF file. But I checked that PDF and it doesn't say how. **So how can I do it ?** I want specific partitions created for all my VM O/S to really isolate them and increase time response.

5.1) Lets say I want to do like 5) but use the file in 4), **can I import a dynamic space created VM O/S file into a fixed space VM ?**

6) to allow better graphic performance due to games or graphic programs like 3dmax, I have to install the Windows Guest Addition files ? But will it allow those kind of softwares to run normally or do I have to expect bugs (OpenGL, DirectX, ...) ? Instructions found on Virtualbox User guide section 4.2.1
==>> To my surprise, Virtualbox v1.5.6 had created/mounted a CD drive in XP pointing to this file. Cool. Installing it now and will have to install games and software to test the VM devices. Installed it but haven't tested it yet. It created an icon in the System Tray but I cannot do anything with it.
==>> Hummm, when I initialy created XP in Virtualbox, I had mounted a CD and was able to use it. Now in my VM XP, the CD Rom is only pointing at the Windows Guest Addition files. So to instally anything from a CD, I have to mount again a CD Rom...

7) Since XP will be on a virtual file, can I still do a defrag with XP's own software or from any other companies ? This is XP so I expect to have alot of fragmentations.
==>> Doing a defrag right now with Window's own defrag tool. So the answer is Yes.

8 ) **I'm using Ubuntu 7.10 right now, what will happen if I upgrade to the new 8.04 ? Will I have to change things to my VM WIn-XP or Virtualbox ?**

9) Gota figure out how to enable sounds in VM XP. Right now the Audio devise is set to a Null device.
==>> I shutdown my VM XP then changed the Audio Driver in Virtualbox to Alsa and now I have sounds (including games).

10) I will now test intalling games : low end graphics and high end graphics
10-1) Low end graphics : I installed Starcraft. Installation went without problems and I am playing it. Except, graphic isn't full screen (wasn't using XP at full screen anyway). Hiting the HOST+F key for full screen created mostly a back screen with small parts of the Ubuntu desktop. Hiting HOST+F again, returned me to Starcraft screen but its totaly black. Hiting ALT+Tab brought me back to XP and clicking Starcraft again, switched to a visible game screen in windowed mode. Gota figure out how to have a decent full screen without problems. Tried drag resizeing the window while Starcraft in it, screen resized but black screen again. **So is there a fix for this ?**

10-2) High end graphics : will try to install Half-Lif 2 (meaning installing Steam first). Installed Steam and connected to my account. I installed HL2. Upon starting HL2 it died right away. I suspect it is DirectX related. Will do a DirectX test and search for game logs.
==>> ran a Direct Diagnostic and ran all graphic and sound tests. They all ran ok.
==>> Found no log files with any informations in it about why HL2 didn't start. NO other files with infos at the time I started HL2. I even checked the system event messages and foudn nothing. I have no clues !!! **Anyone know ? If HL2 will not work, chances alot of high end graphic games will not.**
==>> I tried installing HL1 and when I ran it with OpenGL, it says it was reverting back to Sofware Mode saying it couldn't run in that mode. I tried Direct3D and it seamed to work but when I wanted to reduce resolution due to lagging, HL1 crashed.

If I have other questions, I'll add them as I go.

---

### Post by lswest on 2008-04-22
i'm kind of pressed for time, so i'll answer what i can, quickly.

1. to "back up" your XP drive, just copy the virtual disk from (i believe) /home/<your username>/.VirtualBox/machines (could be wrong about the path) and then, when setting up a new VM, choose "existing Hard Drive" and choose the old XP drive.  (Unless you mean you want to back it up and restore it on the actual hard drive in a dual-boot, then it's trickier)

2. upgrading Ubuntu will in no way affect you XP VM

3. Graphics will not be sufficient for a game of any kind really, because a VM runs on virtual hardware, usually generic, so that means, no matter what graphics card you have, the performance is not what you expect.  That's the whole point of a VM, running software in an area where it cannot harm any part of your system (including Hardware).

---

### Post by pseudo-random on 2008-04-22
1) Network
2) Nvidia Twinview. Just drag your vbox to fill out one of the monitors.
4) There is a hidden folder in your home folder called .virtualbox. Copy the contents of that to a backup drive. Then drop it into your New install's .virtualbox folder.
5) Don't know.
6) Software rendering/emulation only. Don't expect to play COD4 on it!
7) Yes
8) I didn't.
9) Don't know.
10) see 6.

---

### Post by pseudo-random on 2008-04-22
Half life 2 has a 'Gold' rating in WINE.
[http://appdb.winehq.org/appview.php?iAppId=2095](http://appdb.winehq.org/appview.php?iAppId=2095)

---

