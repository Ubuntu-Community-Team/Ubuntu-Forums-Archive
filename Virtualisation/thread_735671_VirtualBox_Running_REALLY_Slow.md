---
title: "VirtualBox Running REALLY Slow"
date: 2008-03-25
forum: Virtualisation
---

### Post by deejross on 2008-03-25
I just installed the free (not open source) version of VirtualBox and set up an XP machine in there. I totally removed everything i didn't need, disabled unneeded services, turned off themes, set up paging file properly, etc. It runs ok until I load MixMeister up. I read a blog where someone was able to run it on relatively slow machine compared to mine with no problem, yet it runs REALLY slow on mine. Audio is skipping all the time, regardless of the buffer settings, screen updates only happen ever 5 seconds or so, so it's impossible to use.

The host machine is a Pentium D 3.4Ghz with 4GB Ram, and I set the guest to use 64 MB of Video RAM, and 1.5GB of system RAM. At first, I had the VM's audio output set to ALSA, but I changed it to OSS after reading somewhere that it causes problems, but I haven't noticed any change. It's slow either way.

Does anyone have any ideas? Anyone else run audio applications in a VirtualBox VM?

Thanks, Ross

EDIT: And before you ask, yes I tried running it in WINE, and no it doesn't work at all :)

---

### Post by deejross on 2008-03-25
I should also mention that the audio files are stored on a file server, and I mapped the two drives that contain all the music. So maybe it has something to do with the networking? It's set up for NAT right now.

---

### Post by flo6320 on 2008-04-20
Hey,

I have also performance problems. Do you use the 64Bit version of ubuntu?

In my case the performance on 64Bit ubuntu is very bad. Then I tried it on a slower computer but 32Bit ubuntu and it is faster than on the more powerful PC! :)

So the reason is maybe the 64Bit version!

I will wait for Hardy and hope not to have any performance problems there. 

Thanks, Flo

---

### Post by deejross on 2008-04-20
Actually, I was using 32-bit Ubuntu. But I also noticed that it's not just Ubuntu, and it's not just me. I have a dual-core Xeon Mac Pro at work running Windows (through bootcamp) and I'm running VMware Workstation on it so I can have Ubuntu at work. Whenever I start up the VM at work on that monster machine, the login sound skips like crazy too.

So I think it has to do with VM audio in general, regardless of host platform, computing power, and virtualizer. The VM's themselves run fine (and fast sometimes), but the second you play audio with it, they all start to slow to a crawl. Especially, if you use an audio editor (like SoundForge, ACID, MixMeister, etc).

---

### Post by svk on 2008-07-03
I can confirm I'm having a similar problem.  I'm running on an HP dv6000 laptop.  My host is a 32 bit Ubuntu, and my guest is Windows XP.  I have Guest Additions enabled.

I've tried all the sound drivers available: PulseAudio, ALSA, and OSS.  The audio is slow on all of them, skips often, etc.  In my case, I'm trying to use Finale, which is a program for music composition, but the performance is not just bad, but completely unacceptable.

Is there anything I could do?

---

### Post by deejross on 2008-07-03
I actually got pissed off by the whole thing and built a new AMD machine from scrap parts laying around and installed XP on it. So I guess there's another usage case for keeping a Windows box around. Everyone always said the only thing holding you back from moving away from a dedicated Windows machine was gaming, but now it's gaming and audio/video. :(

---

### Post by Enav on 2009-08-10
:KS PROBLEM SOLVED FOR ME :KS
(VirtualBox 3.0.4  and Ubuntu 9.04 - the Jaunty Jackalope- 

If u want to do a new fresh install use Method 1
If u want to save your previous "virtualdisks" use Method 2

Method 1
----------------
1- Goto System --> Administration --> Synaptic Pakage Manager
2- Write on the search box "virtualbox"
3- Select and "complete remove" all virtualbox related packages
4- Goto your "home" folder 
5- Press "Control + H" to show hidden files
6- Look for the folder ".VirtualBox"
7- Delete the entire folder ".VirtualBox"
8- Download and install Virtualbox from your prefered source
11- Create a new virtual machine 
12- Enjoy


Method 2
----------------
1- Take a note about your current "virtualdisk" mode (IDE or SATA) 
2- Goto System --> Administration --> Synaptic Pakage Manager
3- Write on the search box "virtualbox"
4- Select and "complete remove" all virtualbox related packages
5- Goto your "home" folder 
6- Press "Control + H" to show hidden files
7- Look for the folder ".VirtualBox/HardDisks"
8- Move the folder "HardDisks" to another location to save all "virtualdisks" that have been created
9- Delete the entire folder ".VirtualBox"
10- Download and install Virtualbox from your prefered source
11- Replace the current ".VirtualBox/HardDisks" folder with the previous saved "HardDisks" folder 
12- Create a new virtual machine and attach the saved "virtualdisk" using the correct drive mode (remember step 1)
13- Enjoy

The guest worked for me in full speed whitout any processor or load problem.
    
Many thanks for "Sun Microsystems" and "junkfer" for the solution
I just wrote this tutorial with more clarity

---

### Post by ltwinner on 2009-08-22
> **Enav said:**
> :KS PROBLEM SOLVED FOR ME :KS
(VirtualBox 3.0.4  and Ubuntu 9.04 - the Jaunty Jackalope- 

If u want to do a new fresh install use Method 1
If u want to save your previous "virtualdisks" use Method 2

Method 1
----------------
1- Goto System --> Administration --> Synaptic Pakage Manager
2- Write on the search box "virtualbox"
3- Select and "complete remove" all virtualbox related packages
4- Goto your "home" folder 
5- Press "Control + H" to show hidden files
6- Look for the folder ".VirtualBox"
7- Delete the entire folder ".VirtualBox"
8- Download and install Virtualbox from your prefered source
11- Create a new virtual machine 
12- Enjoy


Method 2
----------------
1- Take a note about your current "virtualdisk" mode (IDE or SATA) 
2- Goto System --> Administration --> Synaptic Pakage Manager
3- Write on the search box "virtualbox"
4- Select and "complete remove" all virtualbox related packages
5- Goto your "home" folder 
6- Press "Control + H" to show hidden files
7- Look for the folder ".VirtualBox/HardDisks"
8- Move the folder "HardDisks" to another location to save all "virtualdisks" that have been created
9- Delete the entire folder ".VirtualBox"
10- Download and install Virtualbox from your prefered source
11- Replace the current ".VirtualBox/HardDisks" folder with the previous saved "HardDisks" folder 
12- Create a new virtual machine and attach the saved "virtualdisk" using the correct drive mode (remember step 1)
13- Enjoy

The guest worked for me in full speed whitout any processor or load problem.
    
Many thanks for "Sun Microsystems" and "junkfer" for the solution
I just wrote this tutorial with more clarity

I dont see how that answers the problems of slow performance, basically you just reinstalled.

---

### Post by tenghoward on 2009-08-26
If your CPU supports hardware virtualization (VT-X/AMD-V), enable it in VirtualBox and BIOS. It might help to boost the speed. If it also supports Nested Pagin, enable that as well.

I am using Ubuntu x64 with guest as XP x64. It is running fast on my computer (With AMD-V enabled).

CPU - AMD 64 X2 2200 MHZ
RAM - 4GB (1 GB for Guest)

---

### Post by UltraParadigm on 2010-01-20
Using Ubuntu AMD64 9.10, and VB vs 3.1.2
My system is quad core 1.6, 8GB RAM, 3GB for guest
I have virtualization and Hardware acceleration on
Guest OS is Win7 64bit

The system flew at first but after installing the Realtec audio driver in the guest Win7 OS, it started going a bit slower and the sound is very choppy.  The system lags whenever there is sound playing.  

:-(

-------------------------------
Update
-------------------------------
I tried increasing the CPUs up to my limit, and the more processor cores I used the worse it got.  Then I brought it all the way back down to one, and it's working perfectly fast like lightning now!

YAY!

---

### Post by d3v1150m471c on 2011-03-26
open virtualbox and change the audio driver from it's original <also driver, oss driver, pulseaudio driver, null driver>. I changed mine from alsa and it oddly goes way faster...strange but works 
also [http://www.niccolofavari.com/virtualbox-make-windows-xp-guest-more-than-50-faster-with-these-tips](http://www.niccolofavari.com/virtualbox-make-windows-xp-guest-more-than-50-faster-with-these-tips)

---

### Post by Richie086 on 2012-02-28
> **UltraParadigm said:**
> Using Ubuntu AMD64 9.10, and VB vs 3.1.2
My system is quad core 1.6, 8GB RAM, 3GB for guest
I have virtualization and Hardware acceleration on
Guest OS is Win7 64bit
 
The system flew at first but after installing the Realtec audio driver in the guest Win7 OS, it started going a bit slower and the sound is very choppy. The system lags whenever there is sound playing. 
 
:-(
 
-------------------------------
Update
-------------------------------
I tried increasing the CPUs up to my limit, and the more processor cores I used the worse it got. Then I brought it all the way back down to one, and it's working perfectly fast like lightning now!
 
YAY!
 
 
I agree, when you decrease the number of cores allocated to a VM in virtualbox the performance actually seems to increase.  I figured since I was running a x64 guest on a x64 host I would need to allocate at least two cores to the guest VM.  It works much better when you allocate a single core (for some reason)..

---

