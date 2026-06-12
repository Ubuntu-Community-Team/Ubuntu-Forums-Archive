---
title: "VMware Player 4.0 and Kernel 3.2.0 - Small Kernel modules fixes needed for PPVMware P"
date: 2011-11-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-25
For the people that use VMWare for testing PP or test PP and use VMWare for other stuff:

VMWare Player 4.0 fails to compile 2 of it's modules: vmmon and vmsock on Kernel 3.2.1 (latest PP updates). Previous patches and commonly found workarounds doesn't seem to work. 

I gave up the installer and went straight to manually building the modules. 
For vmmon I found out we are failing at iommu.c/h in two functions. It's an easy one and I already have iommu.o. I haven't had the time to check vsock module. I'll work around it later today if I can find the time or on the weekend and, hopefully, publish a working patch here by Monday, for Ubuntu+1 testers.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-11-25
**EDIT: **These patches **do not work** with recent VMWare updates - they are not updated to it. To continue updating patches at every VMware update started to sound a little pointless to me. It's not a decent solution. Also, even perfect patches don't work if VMWare Kernel modules have been previously patched by end-users.  To go on with it creates more support demand, instigates thread necromancy and teaches users nothing. It's time bad spent. Therefore I wont be publishing patches and patching scripts anymore until I can find the time to develop a better solution. We need something that can automatically detect if previous patches were applied, if there's a mix of kernel module sources versions, if there are manual editions to kernel modules sources,etc, and fixes all that before patching. It's harder than it sounds. I'll probably continue developing something in this sense, but future VMWare projects will be added to **Ubuntu Wiki,** and not to UF, according to the current policy for tutorials.
[B]
Thanks,
Effenberg 
[/B]





I managed to patch it, it's working here. I basically took advantage of some VM workstation code, had some linux exports that were not included and a couple missing casts.

[ATTACH]207952[/ATTACH]

The patches are:
iommu.c.patch
iommu.h.patch
kmap_skb.h.patch
vmnet-filter.c.patch
vmnet-netif.c.patch
vmnet-userif.c.patch

Standard procedure:
```

mkdir /tmp/vmpatches
cp $HOME/Downloads/*patch.zip /tmp/vmpatches
unzip /tmp/vmpatches/*.zip /tmp/vmpatches
mkdir $HOME/vmware-backup
sudo -s
cd /usr/lib/vmware/modules/source
cp *.tar $HOME/vmware-backup
for file in `find . -maxdepth 1 -name "vm*tar"`; do tar xvf $file; done
rm -rf *.tar

(if no error message, repeat each cmd without the dry run)
patch --dry-run -p1 -i /tmp/vmpatches/iommu.c.patch
/usr/lib/vmware/modules/source/vmmon-only/linux/iommu.c

patch --dry-run -p1 -i /tmp/vmpatches/iommu.h.patch
/usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h

patch --dry-run -p1 -i /tmp/vmpatches/vmnet-filter.c.patch
 /usr/lib/vmware/modules/source/vmnet-only/filter.c

patch --dry-run -p1 -i /tmp/vmpatches/vmnet-netif.c.patch
  /usr/lib/vmware/modules/source/vmnet-only/netif.c
 
patch --dry-run -p1 -i /tmp/vmpatches/vmnet-userif.c.patch
   /usr/lib/vmware/modules/source/vmnet-only/userif.c
  
patch --dry-run -p1 -i /tmp/vmpatches/kmap_skb.h.patch
    /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h

for file in `find . -maxdepth 1 -name "*only"`; do tar -cf `echo ${file} | sed 's|-only||'`.tar $file; done

rm -rf *only
exit
(run vmplayer via GUI, it will successfully compile the kernel modules, load and start)

```Not sure if it will continue to work for the next kernel. If not I'll update into this thread.

---

### Post by Einder on 2011-11-26
Even after attempting all your steps with the patches, I am unable to get VMPlayer past not being able to build the kernel module. If you have any more ideas or would like the error log then let me know. I'd appreciate help in getting vmplayer working as I use it when I need to access Windows for whatever reason.

---

### Post by effenberg0x0 on 2011-11-26
If you don't need specific features of VMware, I'd advise you to go VirtualBox. Installation, update and maintenance are simpler, VirtualBox auto rebuilds its kernel modules easily and successfully at every kernel update and provides a little more speed IMO. You can convert machines from VirtualBox to VMware and the opposite way easily, just Google for it.

If you really need to run VMWare with this particular version of the kernel, the only possible way is to patch the module sources while there is no update from VMware. 

The easiest way would be for you to extract all tars and try to build it manually. Looking at gcc errors, you'll see in which sources/headers you are getting errors and warnings.

In my case, I am running the default VMWare 4.0.1 (not a pre-patched version or a previous version that was updated) downloaded from VMware website (not the community edition download or a install from Ubuntu repos).

The issues I had when checking the manual build procedure are solved with these patches I posted. After applying them, VMware builds ok.

---

### Post by fjgaude on 2011-11-28
Say, effenberg, did your patch work for the latest kernel 3.2.0-2?

---

### Post by effenberg0x0 on 2011-11-28
> **fjgaude said:**
> Say, effenberg, did your patch work for the latest kernel 3.2.0-2?

I believe it may work, cause changes in headers and libs wouldn't be that great in a minor update, but I haven't had to time to test it. I'm on 3.2.0-1 still for lack of a couple minutes to install 3.2.0-2... Actually, more than a couple minutes, as I usually config the kernel with some settings I like and rebuild. But I'm hoping to test it soon, probably Wednesday. 

If there's any problem, changes are probably very small and I'll post a new patch. I was thinking about putting all the necessary procedures into 1 single script, and include one single patch for all changes files. The way I posted previously is not too user-friendly, I know...

No promises :) But I will probably check 3.2.0-2 and patch soon. Keep an eye in this thread.

---

### Post by dino99 on 2011-11-28
are you sumitting this upstream ?

because i've filled a report bug #892506 due to "implicit declaration of function ‘iommu_found’ " with virtualbox too.

---

### Post by fjgaude on 2011-11-28
Thanks, effenberg, I'll wait for your easy-patch...

---

### Post by effenberg0x0 on 2011-11-28
> **dino99 said:**
> are you sumitting this upstream ?

because i've filled a report bug #892506 due to "implicit declaration of function ‘iommu_found’ " with virtualbox too.

I didn't get this one in Virtualbox, but I think I know where it would be and how to fix it. 

Anyway, I friend here at work mailed his contact in kernel.org, so I didn't wanted to duplicate. I was waiting for feedback from him.

Which version of VirtualBox are you trying to compile? Let me know so can I can give a try to a patch.

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2011-11-28
@dino99 @fjgaude

I have just managed to update to Kernel 3.2.0-2 from repos and confirmed that my patched version of VMware  is capable of building its kernel modules just fine. VirtualBox is running OK too.

[ATTACH]208172[/ATTACH]

As a side note, I just updated to NVidia 290.10 and it seems to make things a little more fluid then previous release. Let's see...

Regards,
Effenberg

---

### Post by fjgaude on 2011-11-28
Thanks, but I'm gonna wait until Thursday morning and if your integrated script doesn't show I'll then use your previous set of patches. <smile>

---

### Post by fjgaude on 2011-12-01
Well, Thursday is here... I've tried to patch vmware 4.0.1 per your instructions but to no-go.

All files are in the right place, but when I try to manually patch (because the unzip *.zip didn't work):

```
frank@cutie:/tmp/vmpatches$ patch -p1 -i /tmp/vmpatches/iommu.c.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|*** iommu.c.old	2011-11-25 13:59:37.063380942 -0200
|--- iommu.c	2011-11-25 06:28:45.000000000 -0200
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.c
/usr/lib/vmware/modules/source/vmmon-only/linux/iommu.c/usr/lib/vmware/modules/source/vmmon-only/linux/iommu.c: Not a directory
Skip this patch? [y] 
```

Don't understand, for iommu.c file is there and it should not be a directory.

Any ideas?

---

### Post by fjgaude on 2011-12-04
I finally got your patches to work. All the elements compile now.

The modules have to be re-compiled each time I restart vmware player. I think something in PP is still not registering the player and thus doesn't save the modules.

Any ideas?

---

### Post by Atre on 2012-01-13
> **fjgaude said:**
> I finally got your patches to work. All the elements compile now.

The modules have to be re-compiled each time I restart vmware player. I think something in PP is still not registering the player and thus doesn't save the modules.

Any ideas?

I can confirm also that the patches work. Also I see the same behavior for VMWare Player, when it's restarted.

No ideas...

[Edit] The second time the player is started and needed to re-compile the modules, the compilation fails due to the fact that it is unable to stop vmware services.
[I]
service vmware stop
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family                            done
   Virtual machine communication interface                            failed
   Virtual machine monitor                                            failed
   Blocking file system                                                done
ERROR: Removing 'vmnet': Device or resource busy
[/I]
Also, if I try to manually unload the modules, it fails as well:

[I]rmmod -f vmnet
ERROR: Removing 'vmnet': Device or resource busy
[/I]
uname -a:[I] uname -a
Linux atre 3.2.0-030200-generic #201201042035 SMP Thu Jan 5 01:44:33 UTC 2012 i686 i686 i386 GNU/Linux[/I]

---

### Post by effenberg0x0 on 2012-01-13
It doesn't happen with me. Once the files are patched and you run vmware from dash, it will pop a dialog saying the kernel modules must be compiled. At this point, you have to close vmware and patch it.

After the modules are compiled successfully, vmware will launch normally. Next times you launch it from the dash, it will go straight to the interface, as the kernel module is already compiled / loaded. I have updated kernel some times in the 3.2.x series and had no need to recompile it. 

I need some info in order to try to help:

How did you download/install vmware-player? Using apt/repos or directly running a setup file from vmware website? Do you have vmware-workstation also installed?

Whats your output for:
```
sudo modinfo vmblock
sudo modinfo vmmon           
sudo modinfo vmwgfx          
sudo modinfo vmci
sudo modinfo vmnet 
```After a normal boot, do you have vmware modules loaded? Check with...
```
$ lsmod | grep vmw*

```...and paste the output here.

In case you don't see any feedback with the command above, try this...
```
sudo modprobe vmmon
sudo modprobe vmci
sudo modprobe vmnet
sudo modprobe vsock
```...and launch vmware-player via dash. Do you still see a message about modules or does it go straight to the normal interface?

---

### Post by effenberg0x0 on 2012-01-13
> **Atre said:**
> I can confirm also that the patches work. Also I see the same behavior for VMWare Player, when it's restarted.

No ideas...

[Edit] The second time the player is started and needed to re-compile the modules, the compilation fails due to the fact that it is unable to stop vmware services.
[I]
service vmware stop
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family                            done
   Virtual machine communication interface                            failed
   Virtual machine monitor                                            failed
   Blocking file system                                                done
ERROR: Removing 'vmnet': Device or resource busy
[/I]
Also, if I try to manually unload the modules, it fails as well:

[I]rmmod -f vmnet
ERROR: Removing 'vmnet': Device or resource busy
[/I]
uname -a:[I] uname -a
Linux atre 3.2.0-030200-generic #201201042035 SMP Thu Jan 5 01:44:33 UTC 2012 i686 i686 i386 GNU/Linux[/I]

When you get to this situation, please copy the output of...
```
ps ax | grep -i vmware
sudo service vmware status

```... to here.

---

### Post by Atre on 2012-01-13
> **effenberg0x0 said:**
> When you get to this situation, please copy the output of...
```
ps ax | grep -i vmware
sudo service vmware status

```... to here.

Here is my output in this situation:

```
 ps ax | grep -i vmware
 1592 ?        Ss     0:00 /usr/bin/vmware-usbarbitrator
 5107 ?        Ssl    0:00 /usr/lib/vmware/bin/vmware-vmblock-fuse -o subtype=vmware-vmblock,default_permissions,allow_other /var/run/vmblock-fuse
 5172 ?        Ss     0:00 /usr/bin/vmnet-dhcpd -s 6 -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1
 5175 ?        S      0:00 /usr/bin/vmnet-natd -s 6 -m /etc/vmware/vmnet8/nat.mac -c /etc/vmware/vmnet8/nat/nat.conf
 5182 ?        Ss     0:00 /usr/bin/vmnet-dhcpd -s 6 -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
 5198 ?        Ss     0:00 /usr/sbin/vmware-authdlauncher
 5790 pts/3    S+     0:00 grep -i vmware
atre (atre): ~> sudo service vmware status
Module vmmon loaded
Module vmnet loaded

```

---

### Post by Atre on 2012-01-13
> **effenberg0x0 said:**
> It doesn't happen with me. Once the files are patched and you run vmware from dash, it will pop a dialog saying the kernel modules must be compiled. At this point, you have to close vmware and patch it.

After the modules are compiled successfully, vmware will launch normally. Next times you launch it from the dash, it will go straight to the interface, as the kernel module is already compiled / loaded. I have updated kernel some times in the 3.2.x series and had no need to recompile it. 

I need some info in order to try to help:

How did you download/install vmware-player? Using apt/repos or directly running a setup file from vmware website? Do you have vmware-workstation also installed?


I have downloaded this file: vmware-workstation-full-8.0.1-528992.i386.bundle. It did not originated from the VMWare site :)
> 

Whats your output for:
```
sudo modinfo vmblock
sudo modinfo vmmon           
sudo modinfo vmwgfx          
sudo modinfo vmci
sudo modinfo vmnet 
``````

atre (atre): ~> sudo modinfo vmblock
filename:       /lib/modules/3.2.0-030200-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-030200-generic SMP mod_unload modversions 686 
parm:           root:The directory the file system redirects to. (charp)
atre (atre): ~> sudo modinfo vmmon           
filename:       /lib/modules/3.2.0-030200-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     2F3714077B5D9E59CCB7D5D
depends:        
vermagic:       3.2.0-030200-generic SMP mod_unload modversions 686 
atre (atre): ~> sudo modinfo vmwgfx          
filename:       /lib/modules/3.2.0-030200-generic/kernel/drivers/gpu/drm/vmwgfx/vmwgfx.ko
version:        2.3.0.0
license:        GPL and additional rights
description:    Standalone drm driver for the VMware SVGA device
author:         VMware Inc. and others
srcversion:     31AEE5CF718C9490BF20C83
depends:        ttm,drm
intree:         Y
vermagic:       3.2.0-030200-generic SMP mod_unload modversions 686 
parm:           enable_fbdev:Enable vmwgfx fbdev (int)
atre (atre): ~> sudo modinfo vmci
filename:       /lib/modules/3.2.0-030200-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-030200-generic SMP mod_unload modversions 686 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
atre (atre): ~> sudo modinfo vmnet
filename:       /lib/modules/3.2.0-030200-generic/misc/vmnet.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Networking Driver.
author:         VMware, Inc.
srcversion:     AC92E4F1B35079A3BB6DE88
depends:        
vermagic:       3.2.0-030200-generic SMP mod_unload modversions 686 

```> 

After a normal boot, do you have vmware modules loaded? Check with...
```
$ lsmod | grep vmw*

```...and paste the output here.

In case you don't see any feedback with the command above, try this...
```
sudo modprobe vmmon
sudo modprobe vmci
sudo modprobe vmnet
sudo modprobe vsock
```...and launch vmware-player via dash. Do you still see a message about modules or does it go straight to the normal interface?```
After reboot:
lsmod | grep vm
vmnet                  50331  13 [permanent]
vmci                   71370  0 [permanent]
vmmon                  74860  0 [permanent]
atre (atre): ~> 

sudo service vmware status
Module vmmon loaded
Module vmnet loaded

```If I launch vmware-player, it does show the message about the modules.

One thing that might be worth mentioning: during patching, I've got one error message:

```
 patch -p1 -i /tmp/vmpatches/iommu.h.patch /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
patching file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
Hunk #1 FAILED at 54.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h.rejects 
```Other than that, patching was ok and I managed to compile the modules (one time).

Thank you!

---

### Post by effenberg0x0 on 2012-01-13
Hey, 

About this:
```
sudo service vmware status
Module vmmon loaded
Module vmnet loaded
```

I fyou manually load all modules...
```
sudo modprobe vmmon
sudo modprobe vmci
sudo modprobe vmnet
sudo modprobe vsock
```
...and then launch vmware-player, do you still have the error message?

It's weird you had a patch failure, it shouldn't happen. Anyway, I'm trying to put the whole thing into an automated script:

1.Stop services / Kill vmware instances, if any
2.Find / interactively backup vmware VMs
3.Completely remove vmware and modules
4.Get vmware from vmware web to a known good location
5.Install vmware
6.Backup module sources to a known good location
7.Download patches to a known good location
8.Untar vmware module sources to a known tmp location
9.Unzip pathes to a known temp location
10.Apply patches
11.If patching not equal to 100% OK, exit with a meaningful / usable error message
12.Else create new tars at tmp location and move new tars to default location
13.Remove temp remains
14.Check modules loading
15.If all is OK, launch vmware
 
I'm about 33% on it using a couple pre-made general bash functions I re-use everyday. As soon as I finish the script and test it a couple times in a fresh VM, I'll probably post it here. It'll take me a couple days though. If I touch the PC too much during the weekend, my wife is likely to shoot me.

---

### Post by fjgaude on 2012-01-13
The issue I was having with having to re-compile the modules each time I started Player was because there were no patches to vsock I left vsock.tar out of the modules source folder. After I put the original back it all works as it should. I should have told you earlier. Sorry about that!

---

### Post by effenberg0x0 on 2012-01-13
> **fjgaude said:**
> The issue I was having with having to re-compile the modules each time I started Player was because there were no patches to vsock I left vsock.tar out of the modules source folder. After I put the original back it all works as it should. I should have told you earlier. Sorry about that!

Ah, ok, good to know. All sources are needed. I'll keep this in mind when people see the same problem in the future. 

Man, I was really starting to worry about it: I need vmware to work and things can't get out of hand at every kernel release. I'll continue to develop something to automate the patching at future releases. 

Thanks for the info.

Regards,
Effenberg

---

### Post by fjgaude on 2012-01-13
I've been using VMware either Server or Player for many years. I've noticed that the company fixed the Player sometime after the last Beta comes out. So their version works with any Ubuntu formal release.

It would be nice to have an easy to alter script to take care of changes as new kernels come out.

Thank you for your conscientious attitude and sincere work.

---

### Post by effenberg0x0 on 2012-01-13
> **fjgaude said:**
> I've been using VMware either Server or Player for many years. I've noticed that the company fixed the Player sometime after the last Beta comes out. So their version works with any Ubuntu formal release.

It would be nice to have an easy to alter script to take care of changes as new kernels come out.

Thank you for your conscientious attitude and sincere work.

That's sort of the idea. So far it hasn't been really hard to manually patch vmware kernel module sources. When it starts with that default "need to build module" dialog and it fails, it gives you the path to a temp log file. Looking at that log, you can see where it failed to compile. Then if you untar the related tar file and try to run gcc yourself, you will get exactly the point in which building fails. The errors, the warnings, in which source or header, etc. With that info in hands, generally is not hard to think of some workaround, do a little research, trial and error, etc. 

Getting up to this point sounds kind of simple to us, but it is a nightmare for users that just need the to get the damn thing to work. Now, being honest, I don't think anyone will create such a smart app that would be capable of understanding why the code fails to compile and thus create a diff/patch for it... I certainly don't have what it takes to do that. 

But if the script can a) Put the relevant sources/errors in front of us quickly; and b) Act as a bulletproof patcher that does all the steps I outlined previously (download tars, backup tars, untar, download and apply a pre-made patch, rebuild and load modules, tar sources back again, etc) in a couple seconds, it would probably be helpful for all users, even the pro ones.

---

### Post by Atre on 2012-01-14
> **fjgaude said:**
> The issue I was having with having to re-compile the modules each time I started Player was because there were no patches to vsock I left vsock.tar out of the modules source folder. After I put the original back it all works as it should. I should have told you earlier. Sorry about that!

:)
It should have been obvious, but I have left it out as well (scary...).
Anyways, now is seems that it is working for me as well, without having to re-compile.

Thanks!

---

### Post by Atre on 2012-01-14
> **effenberg0x0 said:**
> Hey, 

About this:
```
sudo service vmware status
Module vmmon loaded
Module vmnet loaded
```I fyou manually load all modules...
```
sudo modprobe vmmon
sudo modprobe vmci
sudo modprobe vmnet
sudo modprobe vsock
```...and then launch vmware-player, do you still have the error message?

It's weird you had a patch failure, it shouldn't happen. Anyway, I'm trying to put the whole thing into an automated script:

1.Stop services / Kill vmware instances, if any
2.Find / interactively backup vmware VMs
3.Completely remove vmware and modules
4.Get vmware from vmware web to a known good location
5.Install vmware
6.Backup module sources to a known good location
7.Download patches to a known good location
8.Untar vmware module sources to a known tmp location
9.Unzip pathes to a known temp location
10.Apply patches
11.If patching not equal to 100% OK, exit with a meaningful / usable error message
12.Else create new tars at tmp location and move new tars to default location
13.Remove temp remains
14.Check modules loading
15.If all is OK, launch vmware
 
I'm about 33% on it using a couple pre-made general bash functions I re-use everyday. As soon as I finish the script and test it a couple times in a fresh VM, I'll probably post it here. It'll take me a couple days though. If I touch the PC too much during the weekend, my wife is likely to shoot me.

Thanks for your effort. Whenever you have the time, no pressure in any ways! :)

---

### Post by fjgaude on 2012-01-14
Atre, amazing, how things work out, eh?

---

### Post by Atre on 2012-01-14
> **fjgaude said:**
> Atre, amazing, how things work out, eh?

Well, yes, as long as people share their experience. 

Thanks! :)

---

### Post by skibler on 2012-01-16
> **effenberg0x0 said:**
> That's sort of the idea. So far it hasn't been really hard to manually patch vmware kernel module sources. When it starts with that default "need to build module" dialog and it fails, it gives you the path to a temp log file. Looking at that log, you can see where it failed to compile. Then if you untar the related tar file and try to run gcc yourself, you will get exactly the point in which building fails. The errors, the warnings, in which source or header, etc. With that info in hands, generally is not hard to think of some workaround, do a little research, trial and error, etc. 

Getting up to this point sounds kind of simple to us, but it is a nightmare for users that just need the to get the damn thing to work. Now, being honest, I don't think anyone will create such a smart app that would be capable of understanding why the code fails to compile and thus create a diff/patch for it... I certainly don't have what it takes to do that. 

But if the script can a) Put the relevant sources/errors in front of us quickly; and b) Act as a bulletproof patcher that does all the steps I outlined previously (download tars, backup tars, untar, download and apply a pre-made patch, rebuild and load modules, tar sources back again, etc) in a couple seconds, it would probably be helpful for all users, even the pro ones.

I am trying to use your patches with PP and kernel "Linux gnubuntu 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux". I have downloaded/installed vmware player 4.01 just today from the vmware website. Some issues. . .

```

root@gnubuntu:/usr/lib/vmware/modules/source# patch --dry-run -p1 -i /tmp/vmpatches/iommu.h.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|*** iommu.h.old        2011-11-25 14:01:01.823378932 -0200
|--- iommu.h    2011-11-25 14:00:33.739379596 -0200
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
patching file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
Hunk #1 FAILED at 54.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h.rej

root@gnubuntu:/usr/lib/vmware/modules/source# patch --dry-run -p1 -i /tmp/vmpatches/kmap_skb.h.patch 
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- kmap_skb.h
|+++ kmap_skb.h
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h
/usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h: No such file or directory
Skip this patch? [y]
Skipping patch.
1 out of 1 hunk ignored

```

I am not smart enough to figure out what was wrong with the iommu.h, but I can confirm that there is nothing matching /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h on my system.

After these patches and following your instructions in post #2 vmplayer proceeds much farther in installing the kernel modules.

The end of the log file:
```

2012-01-16T13:53:34.116-05:00| vthread-3| I120: Your GCC version: 4.6
2012-01-16T13:53:34.127-05:00| vthread-3| I120: Your GCC version: 4.6
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-9-generic/build/include for kernel release 3.2.0-9-generic is valid.
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Building module vmci.
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-01-16T13:53:34.170-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-9-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-01-16T13:53:34.742-05:00| vthread-3| I120: Building module vsock.
2012-01-16T13:53:34.743-05:00| vthread-3| I120: Source file does not exist at /usr/lib/vmware/modules/source/vsock.tar
2012-01-16T13:53:34.743-05:00| vthread-3| I120: Could not extract source for module vsock!

```

Thank you for any help, and thank you for taking the time to make these patches.

---

### Post by Atre on 2012-01-16
> **skibler said:**
> I am trying to use your patches with PP and kernel "Linux gnubuntu 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux". I have downloaded/installed vmware player 4.01 just today from the vmware website. Some issues. . .

```

root@gnubuntu:/usr/lib/vmware/modules/source# patch --dry-run -p1 -i /tmp/vmpatches/iommu.h.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|*** iommu.h.old        2011-11-25 14:01:01.823378932 -0200
|--- iommu.h    2011-11-25 14:00:33.739379596 -0200
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
patching file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
Hunk #1 FAILED at 54.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h.rej

root@gnubuntu:/usr/lib/vmware/modules/source# patch --dry-run -p1 -i /tmp/vmpatches/kmap_skb.h.patch 
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- kmap_skb.h
|+++ kmap_skb.h
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h
/usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h: No such file or directory
Skip this patch? [y]
Skipping patch.
1 out of 1 hunk ignored

```I am not smart enough to figure out what was wrong with the iommu.h, but I can confirm that there is nothing matching /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h on my system.

After these patches and following your instructions in post #2 vmplayer proceeds much farther in installing the kernel modules.

The end of the log file:
```

2012-01-16T13:53:34.116-05:00| vthread-3| I120: Your GCC version: 4.6
2012-01-16T13:53:34.127-05:00| vthread-3| I120: Your GCC version: 4.6
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-9-generic/build/include for kernel release 3.2.0-9-generic is valid.
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Building module vmci.
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-01-16T13:53:34.170-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-9-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-01-16T13:53:34.742-05:00| vthread-3| I120: Building module vsock.
2012-01-16T13:53:34.743-05:00| vthread-3| I120: Source file does not exist at /usr/lib/vmware/modules/source/vsock.tar
2012-01-16T13:53:34.743-05:00| vthread-3| I120: Could not extract source for module vsock!

```Thank you for any help, and thank you for taking the time to make these patches.

What's the output of the following (on your system):

```
 ls -rtla /usr/lib/vmware/modules/source 
```

Did you have all the .tar files in this directory (to begin with)?

---

### Post by skibler on 2012-01-16
> **Atre said:**
> What's the output of the following (on your system):

```
 ls -rtla /usr/lib/vmware/modules/source 
```

Did you have all the .tar files in this directory (to begin with)?

```

patrick@gnubuntu:~$  ls -rtla /usr/lib/vmware/modules/source
total 3772
drwxr-xr-x 1 root root      46 Jan 16 13:08 ..
-rw-r--r-- 1 root root 1126400 Jan 16 13:52 vmci.tar
-rw-r--r-- 1 root root  839680 Jan 16 13:52 vmnet.tar
-rw-r--r-- 1 root root  727040 Jan 16 13:52 vmblock.tar
-rw-r--r-- 1 root root 1167360 Jan 16 13:52 vmmon.tar
drwxr-xr-x 1 root root      74 Jan 16 13:53 .

```

I believe they were all there. Would that be the current contents of the vmware-backup dir in my home dir?

```

patrick@gnubuntu:~$ ls -rtla vmware-backup/
total 4696
-rw-r--r-- 1 root    root     727040 Jan 16 13:48 vmblock.tar
-rw-r--r-- 1 root    root    1157120 Jan 16 13:48 vmmon.tar
-rw-r--r-- 1 root    root    1126400 Jan 16 13:48 vmci.tar
-rw-r--r-- 1 root    root     839680 Jan 16 13:48 vmnet.tar
drwxrwxr-x 1 patrick patrick      92 Jan 16 13:48 .
-rw-r--r-- 1 root    root     952320 Jan 16 13:48 vsock.tar
drwxr-xr-x 1 patrick patrick    1076 Jan 16 14:04 ..

```

---

### Post by Atre on 2012-01-16
> **skibler said:**
> ```

patrick@gnubuntu:~$  ls -rtla /usr/lib/vmware/modules/source
total 3772
drwxr-xr-x 1 root root      46 Jan 16 13:08 ..
-rw-r--r-- 1 root root 1126400 Jan 16 13:52 vmci.tar
-rw-r--r-- 1 root root  839680 Jan 16 13:52 vmnet.tar
-rw-r--r-- 1 root root  727040 Jan 16 13:52 vmblock.tar
-rw-r--r-- 1 root root 1167360 Jan 16 13:52 vmmon.tar
drwxr-xr-x 1 root root      74 Jan 16 13:53 .

```I believe they were all there. Would that be the current contents of the vmware-backup dir in my home dir?

```

patrick@gnubuntu:~$ ls -rtla vmware-backup/
total 4696
-rw-r--r-- 1 root    root     727040 Jan 16 13:48 vmblock.tar
-rw-r--r-- 1 root    root    1157120 Jan 16 13:48 vmmon.tar
-rw-r--r-- 1 root    root    1126400 Jan 16 13:48 vmci.tar
-rw-r--r-- 1 root    root     839680 Jan 16 13:48 vmnet.tar
drwxrwxr-x 1 patrick patrick      92 Jan 16 13:48 .
-rw-r--r-- 1 root    root     952320 Jan 16 13:48 vsock.tar
drwxr-xr-x 1 patrick patrick    1076 Jan 16 14:04 ..

```


So, you need to have vsock.tar also in [I]/usr/lib/vmware/modules/source.
[/I]At least one error is ruled-out. 

About patching *kmap_skb.h* : you should have that file, if you have untar-ed all the tar files correctly (inside vmnet.tar).

---

### Post by effenberg0x0 on 2012-01-16
The log is telling us vsock.tar is not at /usr/lib/vmware/modules/source.
Use ```
sudo tar -cf vsock.tar vsock-only
``` to recreate it.

The task of decompressing VMWare sources to some known location, as well as the patches, applying the patches and restoring the tar'ed sources to a usable state creates too much space for confusion. I'm working on something automated for it plus some Other things. But meanwhile, you have to understand this:

- VMWare needs the 5 v*.tar files inside of /usr/lib/vmware/modules/source.
- We need to decompress them and change their contents, and it's ok as long as we get back to their original states when we are done.
- Untar the 5 tars. For each of them, a directory named **v<something>-only** will be created.
- Look at line 3 of each of the patches I provided. The lines points out the path/target for each file the patches will change. Change these line in any way you need to, as long as these line does make sense as to where each target file is located. 
- Apply the patch with the -i (interactive) and dry-run options. If everything is OK, apply without --dry-run.
- If you don't have /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h, just touch it before applying the patch. It doesn't really matter.
```
sudo touch /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h

```Once you're done patching, it's absolutely mandatory that you transform each of the v<something>-only directories into the original tars. 
```
sudo tar -cf v<something>.tar v<something>-only
```
And only at this point if you start VMWare it should successfully build the modules.

> **skibler said:**
> I am trying to use your patches with PP and kernel "Linux gnubuntu 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux". I have downloaded/installed vmware player 4.01 just today from the vmware website. Some issues. . .

```

root@gnubuntu:/usr/lib/vmware/modules/source# patch --dry-run -p1 -i /tmp/vmpatches/iommu.h.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|*** iommu.h.old        2011-11-25 14:01:01.823378932 -0200
|--- iommu.h    2011-11-25 14:00:33.739379596 -0200
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
patching file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h
Hunk #1 FAILED at 54.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/vmware/modules/source/vmmon-only/linux/iommu.h.rej

root@gnubuntu:/usr/lib/vmware/modules/source# patch --dry-run -p1 -i /tmp/vmpatches/kmap_skb.h.patch 
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- kmap_skb.h
|+++ kmap_skb.h
--------------------------
File to patch: /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h
/usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h: No such file or directory
Skip this patch? [y]
Skipping patch.
1 out of 1 hunk ignored

```I am not smart enough to figure out what was wrong with the iommu.h, but I can confirm that there is nothing matching /usr/lib/vmware/modules/source/vmnet-only/kmap_skb.h on my system.

After these patches and following your instructions in post #2 vmplayer proceeds much farther in installing the kernel modules.

The end of the log file:
```

2012-01-16T13:53:34.116-05:00| vthread-3| I120: Your GCC version: 4.6
2012-01-16T13:53:34.127-05:00| vthread-3| I120: Your GCC version: 4.6
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Header path /lib/modules/3.2.0-9-generic/build/include for kernel release 3.2.0-9-generic is valid.
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Building module vmci.
2012-01-16T13:53:34.153-05:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-01-16T13:53:34.170-05:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-9-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-01-16T13:53:34.742-05:00| vthread-3| I120: Building module vsock.
2012-01-16T13:53:34.743-05:00| vthread-3| I120: Source file does not exist at /usr/lib/vmware/modules/source/vsock.tar
2012-01-16T13:53:34.743-05:00| vthread-3| I120: Could not extract source for module vsock!

```Thank you for any help, and thank you for taking the time to make these patches.

---

### Post by skibler on 2012-01-16
> **Atre said:**
> So, you need to have vsock.tar also in [I]/usr/lib/vmware/modules/source.
[/I]At least one error is ruled-out. 

About patching *kmap_skb.h* : you should have that file, if you have untar-ed all the tar files correctly (inside vmnet.tar).

Copied vsock over, not sure how that was missed before! Now the only thing that fails when starting vmware services is virtual ethernet.

I swear there is no kmap_skb.h file (or anything similar) in either of my vmnet.tar files (or any of the others)!



edit: Just read effenberg0x0's reply. After creating the empty kmap file vmware player runs flawlessly! Woo hoo!

Thanks very much to the both of you!

---

### Post by effenberg0x0 on 2012-01-16
> **skibler said:**
> Copied vsock over, not sure how that was missed before! Now the only thing that fails when starting vmware services is virtual ethernet.

I swear there is no kmap_skb.h file (or anything similar) in either of my vmnet.tar files (or any of the others)!



edit: Just read effenberg0x0's reply. After creating the empty kmap file vmware player runs flawlessly! Woo hoo!

Thanks very much to the both of you!

Congrats :)

---

### Post by fredhuk on 2012-03-06
Just used the automated patch script for 3.2 kernel from this page in it works fine in 12.04 beta

[https://wiki.archlinux.org/index.php/VMware#VMware_module_patches_and_installation](https://wiki.archlinux.org/index.php/VMware#VMware_module_patches_and_installation)

---

### Post by mesolithic on 2012-03-11
> **effenberg0x0 said:**
> ...Once you're done patching, it's absolutely mandatory that you transform each of the v<something>-only directories into the original tars. 
```
sudo tar -cf v<something>.tar v<something>-only
```
And only at this point if you start VMWare it should successfully build the modules.

spent a whole morning not reading this line =/. for some reason the shell script wasn't working right. ran the commands manually but forgot this impt step. now it works. THANKS!

---

### Post by STARDOUSER on 2012-03-31
> **fredhuk said:**
> Just used the automated patch script for 3.2 kernel from this page in it works fine in 12.04 beta

[https://wiki.archlinux.org/index.php/VMware#VMware_module_patches_and_installation](https://wiki.archlinux.org/index.php/VMware#VMware_module_patches_and_installation)

Yeah, I think this is the way to go right now. I just applied this patch and it updated vmnet, which is the only module that doesn't compile out of the box. At least for Precise beta 2 and VMware-Player-4.0.2-591240.x86_64. I did try patching just vmnet with the diffs provided in this thread, but it didn't compile.

---

