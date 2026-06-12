---
title: "VMWare Server very slow in Hardy"
date: 2008-04-27
forum: Virtualisation
---

### Post by rogeriovinhal on 2008-04-27
I have installed VMware Server 1.0.5 on Hardy and installed Windows XP in a guest machine with 512 MB RAM. But it is painfully slow.

The HD is acessed heavily everytime the VM is doing anything, and some simple tasks may take a lot of time to accomplish.

I have used a patch to install it, since it wouldn't compile the vmmon modules by default. I have also freed some memory. free -m show about 400 mb used and 600 mb cached. (I have 1GB)

What else could it be? In gusty it was a lot faster. Could it be the patch?
I've tried some of the tips with no luck, still slow.

---

### Post by Divan Santana on 2008-04-27
my friend has reported having the same problem on the new kubuntu 8.04 . says vmware was much faster before.

I'm still trying to install vmware on 8.04 64 bit...

---

### Post by Kokopelli on 2008-04-27
I have not noticed a slowdown for VMWare guests in Hardy.  I have had hard drive thrashing like you describe where I forgot to shutdown a VM and Gutsy terminated the guest before it completed shutting down.  It would thrash for quite a while but once it got done I rebooted the guest and performance was fine.

One other thing you might try is change the Additional Memory value found in Host settings to "Fit All virtual Memory into reserved Host RAM" and see if that makes a difference.  If it does not make a difference I generally would not recommend keeping that setting.  It will bump other applications out of RAM if you have allocated most of your memory to VMWare.

---

### Post by manoj_paul_joseph on 2008-04-29
I see the same behaviour as well. I was on gutsy before I upgraded to Hardy.

VMWare Server boots up 2.6.18 kernel extremely slowly. `sleep 1` takes minutes to complete.

I have tried the following with the same result.
VMware-server-1.0.5-80187.tar.gz
VMware-server-1.0.4-56528.tar.gz 

VMware-server-1.0.4 used to work fine on Gutsy.

---

### Post by toolchest on 2008-05-05
Same here... just upgraded to hardy and my xp vm will not keep time accurately (for every minute in the real world, 5 seconds passes in the virtual... would be nice for other things in life but not this) and is running exceedingly slow.

---

### Post by keymoo on 2008-05-06
I'm finding that Windows 2003 Server is still very fast on 1.0.5 build-80187. Windows XP does suck the mutt's nuts though. Maybe it's because VMWare Server was designed to host server OSes and not desktop OSes?

---

### Post by baronKarza on 2008-05-09
The problem is that kernel 2.6.24 does not support the parameter max_cstate.
So it is impossible to set a lower value (as in 7.10) in order to speed up virtual machines.
In Gutsy I used 

```
sudo echo 1 > /sys/module/processor/parameters/max_cstate
```

Now I tried to set the max_cstate value from GRUB line 

```
kernel  /vmlinuz-2.6.24-16-generic root=UUID=cac268f0-bda3-4633-9453-754fcc5f3690 ro quiet splash processor.max_cstate=1
```

but it does not works.
Any help is welcome.

---

### Post by saumilshah on 2008-05-10
I ended up being very frustrated after upgrading to Ubuntu 8.04. I used to run VMWare server 1.0.4 on Gutsy 7.10 with no hiccups. The performance of the guest VMs was very fast (I have a Dell D620 with 2.16 GHz Core Duo and 2GB RAM).

I tried VMWare server 1.0.4 and 1.0.5 with the any-any-115 and any-any-116 update combinations, but no luck.

Today I uninstalled VMWare server completely and installed VMWare Player 2.0.3 instead. After following the instructions for the any-any-116 patch as detailed [here on Czarism]("http://czarism.com/easy-peasy-vmwareplayer-vmplayer-ubuntu-hardy-804") things are working again. Granted I don't have the luxury of the remote console or the web based MUI but atleast the VMs are working fast as before.

I do hope VMware looks into this issue with Kernel 2.6.24 or Ubuntu 8.04, or I do wish the Ubuntu folks look into this pretty soon. I'm waiting for VMware server 1.0.6 which fixes this issue so I can move back to server again.

On a completely aside note, I noticed that Hardy Heron 8.04 hogs 1 GB of main memory, as compared to the same config on Gutsy where only 500-600MB was used. Vista, you have competition.

---

### Post by bc90021 on 2008-06-08
I am having the same issue on my desktop (Vostro 200).  VMware workstation is RIDICULOUSLY slow since upgrading to Hardy Heron.  It takes ten minutes to boot, took almost half a day to defrag, and it is just painful to use at this point.  I have tried VMware Workstation 6.0.3, 6.0.4, and Workstation 6.5 beta.  All of them are so slow as to make it unusable.

On my laptop (Thinkpad T61) VMware workstation 6.0.3 works just fine with Hardy.

Strange...

---

### Post by hariprs on 2008-06-08
I am also having similar issue in VMware workstation after upgrading to hardy.

---

### Post by CloneSan on 2008-06-10
I had some install issues with vmware server 1.05 (you need a patch etc). These seem to have disappeard with 1.06. However, if I boot windows XP as a guest in hardy with 1.06 it's still very slow (takes minutes to boot for instance). This was not the case in 7.04.

I have searched on the web but haven't found any fix for this problem other than some sysctl tweaks for slightly better overall perfomance which in this case are not speeding things up significantly.

If there is no fix, can someone enlighten me _why_ vmware is performing so bad in 8.04?

---

### Post by CloneSan on 2008-06-10
Found something on [https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

that seems to speed up vmware (still not great, but it's usable now):

edit /etc/vmware/config and add:

host.cpukHz = 1000000 
host.noTSC = TRUE
ptsc.noTSC = TRUE

I have a 1000Mhz cpu, so change the host.cpukHz to match the speed from 

# cat /proc/cpuinfo

---

### Post by baronKarza on 2008-06-11
Guys, one possible solution to solve "slow VMware" in hardy is a dirty trick.
While using vmware (especially at boot and shutdown time) you must have a process using 100% CPU. For example you can run the following line:
```
while (`true`) do echo vmware; done
```
This way you are cheating the ACPI controller, allowing VMware to run at a reasonable speed. 
When the guest system is started, you can stop the 100% CPU process: you can re-run it every time your virtualized applications are too slow.
It worked for me.

---

### Post by issue2k on 2008-06-14
same problem here...running ubuntu 7.04 with vmware server 1.0.4 everything was fine. after upgrade to gutsy and then hardy, running vmware server 1.0.6, the virtual machines are very slow and host load is incredible high...

i solved the problem by a complete clean reinstall...

---

### Post by CloneSan on 2008-06-16
issue2k: Did you reinstall ubuntu & vmware or only vmware?

---

### Post by issue2k on 2008-06-17
oh sorry i didn't say...i reinstalled ubuntu (amd64) & vmware (1.0.6), now everything is fine. host load is normal and vm's are faster than bevore on ubuntu 7.04. another point: i changed from i386 to amd64, don't know if this is important but you have to know. anyway, i think this is really curious :-/...

---

### Post by notanumber67890 on 2008-08-25
I had many of the same guest OS timing issues running Vmware under Hardy on a 64 bit Core2Duo host, but had zero luck solving the problem with the various kernel boot options, Vmware server config, or guest OS config options suggested in these forums.

But I SOLVED the problem by changing the BIOS settings to disable "Intel C-STATE Tech".  After that all timing issues were fixed.

I hope that helps all those people experiencing this issue. 

I guess this change means each core won't be able to set its C-state separately, or maybe both cores will lose the ability to set C-state altogether, I don't know.  But it solves the timing issue which is good enough for now.

Can anyone explain the implications of disabling "Intel C-STATE Tech" on a Core2Duo proc?  That information would help the rest of us implement this workaround with 'eyes open'.  

Also, I bet this will help the Ubuntu developers address the issue directly, anyone know how to bring this to their attention, or will this forum post get the message across?

---

### Post by shahgols on 2008-10-08
I'm having the same issue on Ubuntu 8.0.4 and vmware server 2.0.  Has anyone found a solution to this problem?

---

### Post by pdwOnline on 2009-11-28
Had the same problem with VMplayer 2.x.  
I modified the VMware .VMX file adding these lines:

vmotion.checkpointFBSize = "134217728"
mainMem.useNamedFile=FALSE


(make sure these are not already declared somewhere else in the file) and it worked extremely well for me: VM images with XP, Vista and Windows 7 ran fine. Even unther the updated Ubuntu 9.10 Karmic Koala.

BUT: yesterday I updated VMware player to 3.0. Too bad. It takes over 45 minutes to only get logged in in a VM image. It is even worse; VM seems to eat all CPU power in intervals of apprx 2 minutes. Then the VM images takes some action for a second and the system freezes again for a couple of minutes. It sucks.

Anyone?

---

### Post by fjgaude on 2009-11-28
VMware Player 3.0 works beautifully for me on 9.10 and with all my VMs, very fast. Everything was a new install except the VMs were carried over from another OS.

---

