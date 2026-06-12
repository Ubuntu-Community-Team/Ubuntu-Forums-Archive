---
title: "Improve sound quality for a Windows guest"
date: 2012-10-05
forum: Virtualisation
---

### Post by Stonecold1995 on 2012-10-05
I'm trying to run Windows 7 in VirtualBox (host is Kubuntu 12.04), but the sound quality is atrocious.  Even simple beeps sounds broken up and crackly.  Is there any way I can fix this?  I've tried adjusting settings on the Windows guest, but nothing is working...

---

### Post by Habitual on 2012-10-05
Guest Extensions/Pack installed?

What Vbox version?

---

### Post by Stonecold1995 on 2012-10-05
Oh yes, I forgot.  My VirtualBox version is "4.1.12_Ubuntu".  And yes, I have the Guest Extensions Pack installed.  [Here]("http://www.pictureshack.us/images/21171_vb.png") are the settings for VirtualBox, btw.

---

### Post by Stonecold1995 on 2012-10-13
bump

---

### Post by kow777 on 2012-10-14
What are your PC's specs?

---

### Post by Stonecold1995 on 2012-10-14
> **kow777 said:**
> What are your PC's specs?

It's a laptop, but it's a gaming laptop, so it's pretty powerful.  It's a [MainGear ex-L 15 SuperStock]("https://www.maingear.com/custom/notebooks/exl-15/index.php").

CPU: 64-bit [Intel Core i7-2760QM]("http://ark.intel.com/products/53474/Intel-Core-i7-2760QM-Processor-6M-Cache-up-to-3_50-GHz") @ 2.4 GHz (3.5 GHz Turbo)
GPU: [Nvidia GeForce GTX 675m]("http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-675m/specifications")
Memory: 2x [Corsair Vengeance 8 GB DDR3]("http://www.corsair.com/vengeance-16gb-dual-channel-ddr3-memory-kit-cmz16gx3m4a1600c9.html") @ 1600MHz

So I doubt it's that my computer is unable to run Windows virtualized.  In fact, I've been able to get away with running Kubuntu 12.04, Windows 7, PC-BSD, and more than 5 clones of Tails (a debian-based hardened OS) at once.  Then I tried opening Fedora 16 and my computer crashed instantly (I had no swap enabled at the time so maybe that's why).

I also have Intel's VT-x (?) virtualization enabled in the BIOS.

---

### Post by kow777 on 2012-10-14
> **Stonecold1995 said:**
> It's a laptop, but it's a gaming laptop, so it's pretty powerful.  It's a [MainGear ex-L 15 SuperStock]("https://www.maingear.com/custom/notebooks/exl-15/index.php").

CPU: 64-bit [Intel Core i7-2760QM]("http://ark.intel.com/products/53474/Intel-Core-i7-2760QM-Processor-6M-Cache-up-to-3_50-GHz") @ 2.4 GHz (3.5 GHz Turbo)
GPU: [Nvidia GeForce GTX 675m]("http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-675m/specifications")
Memory: 2x [Corsair Vengeance 8 GB DDR3]("http://www.corsair.com/vengeance-16gb-dual-channel-ddr3-memory-kit-cmz16gx3m4a1600c9.html") @ 1600MHz

So I doubt it's that my computer is unable to run Windows virtualized.  In fact, I've been able to get away with running Kubuntu 12.04, Windows 7, PC-BSD, and more than 5 clones of Tails (a debian-based hardened OS) at once.  Then I tried opening Fedora 16 and my computer crashed instantly (I had no swap enabled at the time so maybe that's why).

I also have Intel's VT-x (?) virtualization enabled in the BIOS.

Do you have this issue with any other OS? Maybe it is just Windows being weird, as it tends to be sometimes. 
I would try to decrease the number of "cores" the VM has. Try setting it to four.

---

### Post by Insomn1a on 2012-10-14
Do you have this issue in other software? like viewing video's in a browser, playing games, etc. (in the host OS (ubuntu, etc) instead of the guest (win 7)
It could be audio drivers on the host (the laptop)

Also, try changing the audio settings on the guest OS settings page, before starting the virtualbox session go to settings -> audio and change it, mine is set to PulseAudio, there are also settings for which audio controller to use.

---

### Post by kow777 on 2012-10-14
> **Insomn1a said:**
> 
Also, try changing the audio settings on the guest OS settings page, before starting the virtualbox session go to settings -> audio and change it, mine is set to PulseAudio, there are also settings for which audio controller to use.
Derp... Didn't think about that...

---

### Post by Stonecold1995 on 2012-10-14
> **Insomn1a said:**
> Do you have this issue in other software? like viewing video's in a browser, playing games, etc. (in the host OS (ubuntu, etc) instead of the guest (win 7)
It could be audio drivers on the host (the laptop)

Also, try changing the audio settings on the guest OS settings page, before starting the virtualbox session go to settings -> audio and change it, mine is set to PulseAudio, there are also settings for which audio controller to use.

I haven't tried videos in a browser, although videos work fine in WMP (the audio doesn't).  The games I've tried worked, and I've tried Touhou Project 7.5, BlankBlood, CrackleCradle, and Demonophobia, and they've all played at normal speeds, but with messed up audio (with the exception of Demonophobia, which has no audio at all).  The Windows Experience Index is 6.7 (processor), 7.9 (memory), 2.9 (graphics), 2.2 (gaming graphics), 6.7 (hard disk), and 2.2 (total).

I tried changing the audio settings, and only "Intel HD Audio" worked.  The others caused Windows to tell me there's an error with the audio device.

---

### Post by Stonecold1995 on 2012-10-14
> **kow777 said:**
> Do you have this issue with any other OS? Maybe it is just Windows being weird, as it tends to be sometimes. 
I would try to decrease the number of "cores" the VM has. Try setting it to four.

Reducing the number of cores worked!  So far allocating only one core seems to do the job well, and the audio isn't glitchy anymore.  Thank you!

Also, reducing the cores to one changed my Windows Experience Index so that the graphics are now 4.8, and gaming graphics are now 2.3.

---

### Post by kow777 on 2012-10-14
> **Stonecold1995 said:**
> Reducing the number of cores worked!  So far allocating only one core seems to do the job well, and the audio isn't glitchy anymore.  Thank you!

Also, reducing the cores to one changed my Windows Experience Index so that the graphics are now 4.8, and gaming graphics are now 2.3.
Since your CPU is a quad core with 4 hyperthreads, I wouldn't allocate that many cores to any one machine. I am sure that you could use 4 cores just fine.

---

### Post by Stonecold1995 on 2012-10-16
> **kow777 said:**
> Since your CPU is a quad core with 4 hyperthreads, I wouldn't allocate that many core to any one machine. I am sure that you could use 4 cores just fine.

Yeah, you're right.  I wasn't aware of the purpose of making multiple cores available to the virtualized OS, I thought it was just to allow the guest to use 100% of the CPU, and I didn't know of the overhead it caused.  Currently using one core works just fine, and I'm not making use of any programs in Windows that benefit enough from being multi-threaded for me to enable multiple cores.

---

