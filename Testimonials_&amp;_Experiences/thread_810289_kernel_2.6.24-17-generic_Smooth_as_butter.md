---
title: "kernel 2.6.24-17-generic: Smooth as butter"
date: 2008-05-28
forum: Testimonials &amp; Experiences
---

### Post by prshah on 2008-05-28
Just a note to all those considering the latest offered kernel update:  2.6.24-17-generic

After upgrading, my already superb Hardy installation is now running smooth as butter. No benchmarks (glxgears, compiz benchmark) show any measureable improvement, but the user experience has become Superb from Excellent.

Hope no one elses' milage varies!

---

### Post by Joeb454 on 2008-05-28
To be honest, the only reason I realised I'd got .24-17 was because I happened to spot it on the GRUB boot options ;)

---

### Post by Kowalski_GT-R on 2008-05-28
no probs updating here too...

roll on.

---

### Post by Antman on 2008-05-28
+1

---

### Post by brigux on 2008-05-28
Had to recompile the video drivers as usual each time the kernel is upgraded but apart from that: +1 too.

---

### Post by nantax on 2008-05-28
> **Joeb454 said:**
> To be honest, the only reason I realised I'd got .24-17 was because I happened to spot it on the GRUB boot options ;)

Me too... Do I need to remove the old entries?

```
nante@ubuntu:~$ glxgears
4882 frames in 5.0 seconds = 976.382 FPS
5604 frames in 5.0 seconds = 1120.276 FPS
5494 frames in 5.0 seconds = 1097.872 FPS
5472 frames in 5.0 seconds = 1094.014 FPS
4373 frames in 5.0 seconds = 874.298 FPS
5356 frames in 5.0 seconds = 1070.868 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 40 requests (40 known processed) with 0 events remaining.
nante@ubuntu:~$ glxgears

```

Is the XIO: line normal?

---

### Post by RedMartin on 2008-05-28
I'm a proper Ubuntu noob so I was dreading it but it went without any problems at all on my two machines.

If I could run FEAR in Ubuntu my life would now be complete.

---

### Post by saratchandra on 2008-05-28
> **nantax said:**
> Me too... Do I need to remove the old entries?

```
nante@ubuntu:~$ glxgears
4882 frames in 5.0 seconds = 976.382 FPS
5604 frames in 5.0 seconds = 1120.276 FPS
5494 frames in 5.0 seconds = 1097.872 FPS
5472 frames in 5.0 seconds = 1094.014 FPS
4373 frames in 5.0 seconds = 874.298 FPS
5356 frames in 5.0 seconds = 1070.868 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 40 requests (40 known processed) with 0 events remaining.
nante@ubuntu:~$ glxgears

```

Is the XIO: line normal?

Don't close the gears window. Just hit the esc key.

---

### Post by wipeout140 on 2008-05-28
i was building a network install for a dell i got given and it when as smooth as everything i also did not notice the new kernel till opened up conky and showed the kernel also showing the custom ubuntu is only using 32mb RAM on start-up

---

### Post by stchman on 2008-05-28
I notice no difference in the -16 and the -17 kernel from a user standpoint.

I usually keep the old kernel in case there is a compatibility issue.  After a few weeks I delete the old kernel.

---

### Post by Pausanias on 2008-05-28
Yes!! Absolutely. The difference is amazing. Everything is ultra-smooth, X seems faster, video/audio stuttering is gone.

Kernel 24-17 made a huge difference for me!

> **prshah said:**
> Just a note to all those considering the latest offered kernel update:  2.6.24-17-generic

After upgrading, my already superb Hardy installation is now running smooth as butter. No benchmarks (glxgears, compiz benchmark) show any measureable improvement, but the user experience has become Superb from Excellent.

Hope no one elses' milage varies!

---

### Post by ukripper on 2008-05-29
> **prshah said:**
> Just a note to all those considering the latest offered kernel update:  2.6.24-17-generic

After upgrading, my already superb Hardy installation is now running smooth as butter. No benchmarks (glxgears, compiz benchmark) show any measureable improvement, but the user experience has become Superb from Excellent.

Hope no one elses' milage varies!

My experience was different with the latest kernel revision. 24-17

On my hardware 24-16 worked just perfectly. 

See my below posts on [http://ubuntuforums.org/showthread.php?t=768200&page=53](http://ubuntuforums.org/showthread.php?t=768200&page=53)

"
Upgraded from Gutsy to Hardy.I am having lockups under 2.6.24.17 kernel with compiz enabled. Disabling compiz doesn't lockup my machine but not running compiz really makes my machine living hell without compiz as typing gets very slow. I am probably going to give kde a try. Perhaps it is just locking up under gnome.

It could be my ndiswrapper drivers which I manually installed and blacklisted in modprobe and loading from rc.local(due to system hanging at boot, if i don't blacklist ndiswrapper during boot then system fails to go past init). This locckup is bizarre on my machine as it is completely freezing up the whole system, not just the xserver. Only hard reboot recovers the xserver back, no other key combination works.

My next step would be to try KDE and if it doesn't work, i am going to compile the latest .25 kernel.

I still have to say Ubuntu devs done a great job with Hardy LTS, everything just runs much quicker than gutsy on my machine except freezing issue which i know will be fixed soon otherwise I have to hunt it down to fix it.




NEXT POST:---
Switched back to 2.6.24.16 kernel revision and no lock up so far. So I guess there was something latest in 24.17 rev which didn't like my hardware.

happy so far...going to give 2.6.25 a go if I get any freezes in .24"



Still no problems with 24-16 .I am happy bunny!

---

### Post by glennric on 2008-05-29
I also had some issues with the 2.6.24-17-generic kernel.  I can no longer suspend/hibernate and resume/thaw.  To be honest I can suspend or hibernate, but it doesn't come back.  When I try to wake the computer (from either one) it stops at a black screen before it even runs any of the resume scripts (according to /var/log/pm-suspend.log).  

I should point out that this happens on two out of the three computers I have tried this on.  On a rather old laptop suspend and resume still work fine.

Does anyone know how to fix the suspend/hibernate resume issue?  It still works fine with the 2.6.24-16-generic kernel.  

I did notice that everything else about the new kernel was really nice and smooth.

---

### Post by prshah on 2008-05-29
Any doubts I might have had that the improvement was purely psychological have now been dispelled with the installation of 24-17 on my laptop as well. Smoooooooth, though, again not measurable against any benchmarks.

---

### Post by Joeb454 on 2008-05-29
I have heard of a couple of issues, though kernel updates always have the potential to cause major issues. Luckily this was just a suspend issue, nothing *too* drastic :)

---

### Post by imbjr on 2008-05-30
The only downside of the update was the loss of my VirtualBoxed XP, but a sniff in the proposed updates revealed the upgraded packages to run VirtualBox with the new kernel. 

Glad that the update allowed both 16 and 17 to be booted to - last time that happened was during Feisty.

---

### Post by Joeb454 on 2008-05-30
That's nothing to do with kernel updates - it depends on your GRUB's menu.lst :)

---

### Post by imbjr on 2008-05-30
> **Joeb454 said:**
> That's nothing to do with kernel updates - it depends on your GRUB's menu.lst :)

I understand that in respect of 16 and 17 sitting together, either selectable, but it definitely was a kernel update that b0rked VirtualBox for a moment.

---

### Post by himikeb on 2008-06-04
My Notes:
  I have had the same resume problem as glennric when I was trying a previous -17 kernel, so I'm still using 16.

To un-bork VBox after changing the kernel, you have to run:
  sudo /etc/init.d/VBoxDrv setup
This will recompile the VBox kernel driver for the new kernel - If you get an error during that step, you probably need to install the corresponding new kernel headers so the compile will complete.

---

### Post by MilesRdz on 2008-06-04
My desktop video acceleration is soo much better than before.

---

### Post by jimv on 2008-06-04
Noobz.  17 was so last week.  I just got my hands on 18 and I'm lovin' it.

---

### Post by Joeb454 on 2008-06-04
That's why the thread was created before the release of -18 ;)

---

