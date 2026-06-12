---
title: "Virtualbox performance issues on Lucid"
date: 2010-06-02
forum: Virtualisation
---

### Post by mydoghasworms on 2010-06-02
I have upgraded (reinstalled really) to Lucid a few days ago.
(My /home is on a separate partition, so I just reinstalled on the / partition).

Now I find that VirtualBox is using up lots of CPU, and this is causing lots of lags in my guest OS.

I am running a dual core machine, and I can see VirtualBox mostly using 100% of one core.

Has anyone had the same experience? I'm thinking of reinstalling 9.10, as it ran smoothly there.

---

### Post by John Bean on 2010-06-02
Which version (exactly) are you using? The current non-free version that I use (3.2.12 I think - I'm on a XP box at the moment so I can't check it) works faster and smoother on Lucid than any previous version did on Jaunty. I didn't use Karmic, it gave me all sorts of problems so I skipped it.

---

### Post by mydoghasworms on 2010-06-02
Well, after installing 10.04, I installed VirtualBox 3.2.0-61806 (the deb from the VirtualBox site). That's when I first noticed the problem, so I reverted back to 3.1.4-57640 (which I was using before on 9.10).

But you are making me wonder whether I should not perhaps try create a brand new VM with the same VDI and see how that works. I'm going to try that and report back here.

---

### Post by mydoghasworms on 2010-06-02
Just as a matter of interest: Are you using VirtualBox from the Ubuntu repositories, or the .deb from the VirtualBox website?

---

### Post by John Bean on 2010-06-02
> **mydoghasworms said:**
> Just as a matter of interest: Are you using VirtualBox from the Ubuntu repositories, or the .deb from the VirtualBox website?

Neither. I'm using the Virtualbox repository:
```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
``` I just checked and I do have the same version you quoted (3.2.0 r61806) and my XP client is the same one I ran with 3.1 on Jaunty. Odd.

---

### Post by mydoghasworms on 2010-06-02
Odd indeed. Are you running the 64-bit version? What is your kernel version? I've got 2.6.32-21-generic.

---

### Post by John Bean on 2010-06-02
> **mydoghasworms said:**
> Odd indeed. Are you running the 64-bit version? What is your kernel version? I've got 2.6.32-21-generic.

Mine is on a quite low powered laptop: dual core 1.9GHz Athlon, 32-bit Linux 2.6.32.22-generic, 3GB RAM.

I give the XP guest a lot of RAM (2GB) because of resource-intensive applications I use like Photoshop and Lightroom, and although CPU demand is sometimes very high it's not that much greater than it would be running natively on the same hardware. It all runs very smoothly and without drama.

---

### Post by mydoghasworms on 2010-06-02
Thanks, I have pretty much the same hardware setup as you, dual core Intel with 4GB RAM running on a laptop. My problem is that there are frequent lags even when the guest is not doing anything.

I wonder if updating my kernel will perhaps resolve the issue, because creating a new VM certainly didn't. Thanks for the info.

---

### Post by mydoghasworms on 2010-06-03
Since yesterday, it seems that VirtualBox developed a memory leak. The VM (running XP) would abort after a while, due to exhausting the host memory.

Now here's the twist: It seems the guest is responsible for this.

Out of desperation I reverted back to an old copy of the same VDI which I had been running. This one is running fine!

The part that still confuses me is that the VM/VDI which is behaving badly was running fine on Karmic, prior to me installing Lucid.

---

### Post by John Bean on 2010-06-03
I found I need to configure XP swap use with care; I always change the default to a fixed size paging file (set max and min to the same value) which had a dramatic affect on performance in a VT because it has the important side effect of creating a fixed, permanent paging file instead of creating it from scratch on boot and changing size on demand. 

My XP applications tend to push RAM to the limits and into swap so I do this even on physical installations, but in VMs it's even more important.

There must be something more fundamentally different in our two installations though, since mine actually works *better* in Lucid and yours worse.

Edit: Afterthought: did you update the guest additions in your XP client when you changed to 3.2? It caused me some grief initially until I remembered to do it.

---

### Post by mydoghasworms on 2010-06-03
Well, that's the odd thing: In my XP VM, there is no abnormal memory usage. In my Ubuntu host though, it uses more and more until it exceeds the limit set for the VM! It doesn't even swap it out, it just keeps going until the physical memory is exhauseted, then aborts the VM.
But like I said: (oddly enough) I simply created a new VM with my old vopy of the same VDI, and that is running fine. I will try update my Linux kernel, and if that doesn't help, I'm going to reinstall Karmic to see what it does.

---

### Post by mydoghasworms on 2010-06-03
Well, that's the odd thing: In my XP VM, there is no abnormal memory usage. In my Ubuntu host though, it uses more and more until it exceeds the limit set for the VM! It doesn't even swap it out, it just keeps going until the physical memory is exhauseted, then aborts the VM.
But like I said: (oddly enough) I simply created a new VM with my old vopy of the same VDI, and that is running fine. I will try update my Linux kernel, and if that doesn't help, I'm going to reinstall Karmic to see what it does.
But to answer your question: I tried both versions of the guest additions, with the same effect.

---

### Post by John Bean on 2010-06-03
> **mydoghasworms said:**
> Well, that's the odd thing: In my XP VM, there is no abnormal memory usage. In my Ubuntu host though, it uses more and more until it exceeds the limit set for the VM! It doesn't even swap it out, it just keeps going until the physical memory is exhauseted, then aborts the VM.

That's clearly broken behaviour by VB and something I've simply never seen in any version I've used. There's been a flurry of "important" updates (fixes) this morning which included the kernel (although it's still 2.6.32.22-generic) and Virtualbox which is now  3.2.2 r62298. Made no difference to mine but it must be worth a try.

PS: this is the first time I've seen a change to an existing kernel rather than waiting for the next one. Must be critical to somebody even if I don't see a difference.

---

### Post by mydoghasworms on 2010-06-03
Well, that's the odd thing: In my XP VM, there is no abnormal memory usage. In my Ubuntu host though, it uses more and more until it exceeds the limit set for the VM! It doesn't even swap it out, it just keeps going until the physical memory is exhauseted, then aborts the VM.
But like I said: (oddly enough) I simply created a new VM with my old vopy of the same VDI, and that is running fine. I will try update my Linux kernel, and if that doesn't help, I'm going to reinstall Karmic to see what it does.
But to answer your question: I tried both versions of the guest additions, with the same effect.

---

### Post by mydoghasworms on 2010-06-03
Oops! This whole time I thought my posts weren't updating. Sorry! Seems like I have a few dups there!

---

### Post by John Bean on 2010-06-03
> **mydoghasworms said:**
> Oops! This whole time I thought my posts weren't updating. Sorry! Seems like I have a few dups there!

Thank goodness for that; I thought I was in Groundhog Day :-)

---

### Post by mydoghasworms on 2010-06-03
Well, I just ran Update Manager and got the new kernel etc., but the problem still persists. However, I'm just going to stick to my older Win XP VM, because it's just too much hassle to downgrade Ubuntu :-)
Anyway, thanks for the input!

---

### Post by mydoghasworms on 2010-06-07
Well, here's something else: I don't know how I missed this, but I found that VBoxService.exe in the guest was using up nearly 100% CPU. I'm not sure whether this is related to using up memory on the host, but I see that it's quite an old problem on VirtualBox, apparently.
Anyway, just thought it's worth a mention.

---

### Post by John Bean on 2010-06-07
> **mydoghasworms said:**
> Well, here's something else: I don't know how I missed this, but I found that VBoxService.exe in the guest was using up nearly 100% CPU. I'm not sure whether this is related to using up memory on the host, but I see that it's quite an old problem on VirtualBox, apparently.
Anyway, just thought it's worth a mention.

I've certainly seen this (and various other issues) when there's been a mismatch between guest additions version and the version of the VB host, which is why I mentioned it earlier. I have to say though that I've never seen anything similar on my system with recent versions, I can only speculate that something in your guest is broken and making the VB driver misbehave, especially if you have another similar Windows VM that doesn't cause the same problem. 

I've had many physical Windows installations that were broken to the point that a reinstall was the only way to make them behave so it's not hard to visualise this happening to a VM. From bitter experience (with XP, not VB!) I now take a "baseline" snapshot of my XP system immediately after a new installation and core applications have been installed, then when I make important changes I take a snapshot before and after. Finally I back up "Documents and Settings" every time I use it.

I can recover from any XP problem in a couple of minutes (or less) no matter how badly it breaks and the only maintenance needed is weeding out some of the "just in case" snapshots from time to time to conserve disk space. 

So far I've had to "reinstall" XP once (after two years or so) when it broke after installing some (Microsoft) software. It took 15 seconds :-)

---

### Post by jrose999 on 2010-06-07
I had a question my main os is lucid 10.4. 8gig of ddr3 quadcore i5 2.67ghz and a nvidia 250gtx. two screens.

im running oracle vm 3.2 with xp on it and i am having alot of lag issues regaurding the mouse any ideas? i have oracle assigned 2 cores and 2.5gigs of ram.

---

### Post by mydoghasworms on 2010-06-08
Thanks for the info. I think I will have to start making use of the snapshot feature as well. I previously just made a copy of the actual VDI file. 
jrose999, I wonder if you have the same issues as me. I am still very tempted to downgrade to 9.10, and see how that runs. If I do, I will post here and let you know.

---

### Post by maxpoweron on 2010-06-14
I've installed VirtualBox 3.2.4 on several computers with different hardware specs.  My home notebook is a Sager NP8690 running Intel Core i7-820QM with 6GB of RAM and 1 GB Nvidia GX280 card.  One of my work computers runs Linux Mint 9 with a Intel P4 3.40 Dual Core on 2GB RAM with an Intel video card.

Both computers are running Windows 7 as a VM with my home notebook running Vista SP2 and XP SP3.  All are running the VMs well, and I use the VM of Win 7 on my work PC to connect to another AD for machine and user account creation/modifications.

What I found strange was my new Dell Latitude M6400 with 4 GB RAM and with an Intel Core 2 Duo P8700 and Intel video having problems running VirtualBox.  I wiped out the HDD, installed Ubuntu 10.04 installed the patches/updates and installed VirtualBox.  Poor performance with any VM I tried to create.  I checked the BIOS, Vitalization was enabled.  

The settings in Virtualbox was set for 1 processor 8MB video RAM, and 512MB RAM.  I bumped up the RAM to 2 GB to install Windows 7, but installation was painfully slow.  I created an ISO image of my Windows 7 DVD to see if that would increase performance.  No luck.  I had to reload my Windows image back on the Dell so I can work today.

---

### Post by TheFu on 2010-06-14
I'm seeing my x64 Ubuntu 10.04 host get REALLY, REALLY busy (appears to lock up) after a few days running a low utilization WinXP x32 vbox client.  I'm using the OSE version from the ubuntu repository - vbox 3.1.6 is current.

In the first installation, the host OS would completely lock up (waiting 30 min) before I'd press the big red power switch.  Then there was a kernel update and the system improved as releated to both graphics programs AND vbox client audio and video. Audio stutters are mostly gone.

Current kernel is [I]2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux.
[/I]
It could be an interaction issue with nVidia X/Windows drivers, since they are showing up in the syslog, but I'm happier that it isn't really locking up anymore. It does appear to eat CPU and disk IO which makes no sense - I'm using less than 50% of the RAM in the system, so there's no need to swap anything out to disk and there's no programs running using the disk.  I'm at a loss to explain why the vbox processes start eating CPU. I expect an vbox update will correct the problems, but I'm unwilling to leave the repository safety for another unapproved repository at this point.

When the WinXP VM is fist started, it runs faster than native, but over time (days), it gets slower and slower. I use it for video editing. The same video editing program on WinXP physical machines never behaved that way without going over a month between reboots.  For now, I'll just start, use and shutdown the VM daily to keep good performance.

---

### Post by mydoghasworms on 2010-06-24
My problem seems to eventually have been solved. As suggested in this thread and went back and looked at the guest additions again. I've upgraded VirtualBox in the meantime, and made sure I now had the corresponding guest additions. Previously this didn't solve the problem (maybe because I didn't reboot the guest?). At any rate, I'm working quite happily now with my XP guest. I did notice a few threads relating to high CPU usage on the VirtualBox forums though.

---

### Post by John Bean on 2010-06-24
Glad you got there in the end. I always reboot XP after changing guest additions (or any other NT "kernel" driver for that matter) so perhaps that was the only difference that mattered.

---

