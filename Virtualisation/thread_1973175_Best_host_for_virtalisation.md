---
title: "Best host for virtalisation?"
date: 2012-05-04
forum: Virtualisation
---

### Post by OliverHaslam on 2012-05-04
I am currently using Ubuntu 11.10 as my VM server's host, and am noticing that the machine is not as quick as it should be, even with no VMs running. The machine runs an Intel E6600 Core2Duo 2.4GHz chip and 8GB of DDR 3 RAM. Moving windows around is laggy, and apps don't load as quick as I would expect.

I suspect some of this is down to Nvidia drivers, and some of the speed issues are also affecting my VMs.

What I am wondering is this: would I be better moving to another host OS for Virtualbox, or is the issue something that is fixable?

I am happy to move to Debian etc, or I also have licenses for Windows XP/Vista/7 and 2k8 Server if anyone things that the driver support would be better here?

I just want a stable/fast host for the VMs.

Cheers.

---

### Post by cmont899 on 2012-05-04
I have been using Proxmox for the last couple years and have loved it. It's a rebuild of Debian and supports KVM and OpenVM VMs. There is no "Desktop" GUI, administration is done through the builtin web interface.

[http://proxmox.com/products/proxmox-ve](http://proxmox.com/products/proxmox-ve)

---

### Post by CharlesA on 2012-05-04
I'm guessing you are using this box from the console via a GUI?

I've been running 10.04 as my VM host for a year or so and haven't had any problems with sluggishness. Recently upgraded to 12.04 and no problems either.

When I was running 10.04, I was using Core2Duo E8500, 6GB RAM and 500GB HDD.

After upgrading the hardware to something more beefy - i7 2600K, 16GB DDR3 and 500GB HDD, I'm running 12.04 with no problems.

It also depends on what VM software you are using. KVM is the native hypervisor for *nix, but you can use others.

---

### Post by OliverHaslam on 2012-05-04
> **CharlesA said:**
> I'm guessing you are using this box from the console via a GUI?

I've been running 10.04 as my VM host for a year or so and haven't had any problems with sluggishness. Recently upgraded to 12.04 and no problems either.

When I was running 10.04, I was using Core2Duo E8500, 6GB RAM and 500GB HDD.

After upgrading the hardware to something more beefy - i7 2600K, 16GB DDR3 and 500GB HDD, I'm running 12.04 with no problems.

It also depends on what VM software you are using. KVM is the native hypervisor for *nix, but you can use others.

I'm using Virtualbox at the moment, as it is free and supports snapshots/multiple VMs running at once.

To be honest, it is possibly an issue with the Ubuntu host more than the VMs, as just dragging this Chrome window around results in a little lag and quite a bit of screen tearing. I suspect graphics drivers, and I assume this is what is causing the same - often multiplied - results in my VMs.

The machine feels sluggish to use at times, too, with Chrome often taking around 5-10 seconds to load.

I may upgrade the host to 12.04 first and see if that helps, but the machine just feels.....sticky, if that makes any sense.

---

### Post by CharlesA on 2012-05-04
If you run top from a terminal, what does it say?

---

### Post by OliverHaslam on 2012-05-04
> **CharlesA said:**
> If you run top from a terminal, what does it say?

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
 1127 root      20   0  172m  36m  13m S    4  0.5   2:29.43 Xorg                                  
 1785 oli       20   0  628m 176m  35m S    3  2.2   1:38.78 compiz                                
14557 oli       20   0  312m  16m  10m S    1  0.2   0:00.30 gnome-terminal                        
 1749 oli       20   0 27424 3256  856 S    0  0.0   0:06.54 dbus-daemon                           
 1947 oli       20   0  327m  22m  10m S    0  0.3   0:05.05 unity-panel-ser                       
 3767 root      20   0  507m 120m  58m S    0  1.5   0:38.86 precise                               
14618 oli       20   0 21468 1392  988 R    0  0.0   0:00.04 top                                   
    1 root      20   0 24192 2204 1272 S    0  0.0   0:00.59 init                                  
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                              
    3 root      20   0     0    0    0 S    0  0.0   0:00.36 ksoftirqd/0                           
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                           
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                           
    9 root      20   0     0    0    0 S    0  0.0   0:00.27 ksoftirqd/1                           
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                               
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                 
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:1                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                           
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                           
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                           
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                               
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                               
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                 
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                    
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                            
   24 root      20   0     0    0    0 S    0  0.0   0:08.13 kswapd0                               
   25 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                  
   26 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                            
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                         
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                       
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                              
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                             
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
```

---

### Post by CharlesA on 2012-05-04
It looks normal.

See if 12.04 runs any better, as driver support has improved somewhat.

If that still doesn't work, you could always try Debian Squeeze or even Fedora/CentOS.

---

### Post by OliverHaslam on 2012-05-04
> **CharlesA said:**
> It looks normal.

See if 12.04 runs any better, as driver support has improved somewhat.

If that still doesn't work, you could always try Debian Squeeze or even Fedora/CentOS.

Thing is, will the driver support be any better in them, or is that possibly not the reason for the poor performance?

An example - if I use my Windows 7 VM, I can sit and watch it redraw the window when I maximise it. The VM has been given 256MB of video ram and 4GB of RAM.

---

### Post by CharlesA on 2012-05-04
> **OliverHaslam said:**
> Thing is, will the driver support be any better in them, or is that possibly not the reason for the poor performance?

An example - if I use my Windows 7 VM, I can sit and watch it redraw the window when I maximise it. The VM has been given 256MB of video ram and 4GB of RAM.
It's probably having issues with the video driver if it's running that poorly. Try a livecd before doing anything to see if it exhibits the same problems or not.

I've run a Win7 VM with 1GB of RAM and 32MB of video and it runs fine on my box.

---

### Post by OliverHaslam on 2012-05-04
> **CharlesA said:**
> It's probably having issues with the video driver if it's running that poorly. Try a livecd before doing anything to see if it exhibits the same problems or not.

I've run a Win7 VM with 1GB of RAM and 32MB of video and it runs fine on my box.

I guess the big question is: is the Windows 7 VM suffering because of Ubuntu's poor Nvidia driver, or is it Oracle's poor driver that Windows 7 is using?

That said, moving windows around in all of my VMs results in lag.

---

### Post by CharlesA on 2012-05-04
> **OliverHaslam said:**
> I guess the big question is: is the Windows 7 VM suffering because of Ubuntu's poor Nvidia driver, or is it Oracle's poor driver that Windows 7 is using?

That said, moving windows around in all of my VMs results in lag.
They both deal with the physical hardware, so if the OS is having issues with it, the software you run on it will have those same problems.

---

### Post by OliverHaslam on 2012-05-04
The last 15  seconds or so are a good example of what I am seeing.

[http://www.youtube.com/watch?v=MxGonn3N1T8](http://www.youtube.com/watch?v=MxGonn3N1T8)

---

### Post by CharlesA on 2012-05-04
> **OliverHaslam said:**
> The last 15  seconds or so are a good example of what I am seeing.

[http://www.youtube.com/watch?v=MxGonn3N1T8](http://www.youtube.com/watch?v=MxGonn3N1T8)
Yeah, that looks like either the CPU is trying to process or the video card is trying to play catch-up.

See if it does the same thing from a livecd and go from there.

---

### Post by OliverHaslam on 2012-05-04
> **CharlesA said:**
> Yeah, that looks like either the CPU is trying to process or the video card is trying to play catch-up.

See if it does the same thing from a livecd and go from there.

I've been thinking about giving Debian a go, so I may install that as the host and then just use my Ubuntu VM as I do now. Hopefully that will improve things, though I wonder if it will still use the same drivers?

---

### Post by CharlesA on 2012-05-04
> **OliverHaslam said:**
> I've been thinking about giving Debian a go, so I may install that as the host and then just use my Ubuntu VM as I do now. Hopefully that will improve things, though I wonder if it will still use the same drivers?
No idea. The last time I used Debian, it ran fine for me, but my RAID drivers wouldn't compile, so I ended up using Ubuntu.

Give it a shot and see.

---

