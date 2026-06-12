---
title: "VBox: Kernel driver not installed (rc=-1908)"
date: 2011-11-24
forum: Virtualisation
---

### Post by lads on 2011-11-24
***UPDATE**: Jump to [the solution]("http://ubuntuforums.org/showpost.php?p=11487796&postcount=9").*

Hello everyone,

The following is from a Ubuntu 11.10 64-bit install, that has been running VBox without trouble for a month.

This morning as I tried to start a Win7 virtual machine (that I've used every day) I got a window with these messages:

> 
**VirtualBox - Error**

Failed to open a session for the virtual machine Windows7.
The virtual machine 'Windows7' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}

And a second window with this:

> 
**VirtualBox - Error in suplibOsInit**

Kernel driver not installed (rc=-1908)

Please install the virtualbox-dkms package and execute 'modprobe vboxdrv' as root.

So I tried to run what it suggested:

```
$ sudo apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

$ sudo modprobe vboxdrv
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Module vboxdrv not found.
```

Googling about it I found [a closed thread with the same error on Maverick]("http://ubuntuforums.org/showthread.php?t=1574582"), but it is marked as solved without providing any fix.

I have to use VBox everyday because Oneiric doesn't run one of the programs I use the most. Can someone help? Thank you.

---

### Post by BC59 on 2011-11-24
As I remember when I was using VirtualBox, in every kernel update I had to recompile, so check here if this helps you:

[https://www.virtualbox.org/ticket/8143](https://www.virtualbox.org/ticket/8143)
[http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

If not consider reinstall VirtualBox from Ubuntu Software Center.

---

### Post by BC59 on 2011-11-24
And a suggestion, Win7 is very slow and sluggish in a Virtual Machine, WinXP works perfectly and almost all Win programs work fluently on it.

---

### Post by lads on 2011-11-24
Thanks for the reply. I couldn't sort out how to make the command to change the .h files working on my machine so I opted for a re-install. Here's the result of dpkg:

```
# dpkg -i virtualbox-4.1_4.1.6-74713~Ubuntu~oneiric_amd64.deb 
Selecting previously deselected package virtualbox-4.1.
dpkg: considering removing virtualbox in favour of virtualbox-4.1 ...
dpkg: yes, will remove virtualbox in favour of virtualbox-4.1.
(Reading database ... 347746 files and directories currently installed.)
Unpacking virtualbox-4.1 (from virtualbox-4.1_4.1.6-74713~Ubuntu~oneiric_amd64.deb) ...
 * Stopping VirtualBox kernel modules                                              [ OK ] 
Setting up virtualbox-4.1 (4.1.6-74713~Ubuntu~oneiric) ...
Installing new version of config file /etc/init.d/vboxdrv ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
 * Stopping VirtualBox kernel modules                                              [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                                        Error! Could not locate dkms.conf file.
File:  does not exist.
                                                                                   [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                     [ OK ] 
 * Starting VirtualBox kernel modules                                              [ OK ] 
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-central ...
```

This was run as superuser. Right now I have no Virtual Box, please help me, I'm really in trouble. 

Thanks.

---

### Post by lads on 2011-11-24
Ok I managed to get VBox back by installing from the software centre. Problem is: the errors reported at the opening of this thread are also back.

Any other suggestions? I really need this working. Thanks?

---

### Post by BC59 on 2011-11-24
Sometimes Oracle who owns Virtualbox is late to prepare fixes for the new kernels, so if the machine is working just wait.

If not there is another solution to boot and choose the old kernel. That fixes everything.

---

### Post by lads on 2011-11-25
> **BC59 said:**
> If not there is another solution to boot and choose the old kernel. That fixes everything.

How can I do that? I've been tweaking with /etc/default/grub but so far I haven't managed to get the kernel selection menu at start up.

Thanks.

---

### Post by BC59 on 2011-11-25
From Grub Menu Screen while booting you choose **Previous Linux Versions**

If you cannot see the Grub Menu Screen, you have to hold down SHIFT during boot.

---

### Post by lolpenguin on 2011-11-25
Did you upgrade your kernel? Virtualbox depends on kernel modules so you have to recompile them:
```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by BC59 on 2011-11-25
> **lolpenguin said:**
> Did you upgrade your kernel? Virtualbox depends on kernel modules so you have to recompile them:
```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

This is the correct procedure but as I see from his first post, he already did it.

---

### Post by lads on 2011-11-25
Thank you lolpenguin that did it!

I believe there was a kernel update 2 days ago. Why can't this sort of recompiling be triggered automatically? For a basic user things stopping working overnight poses serious difficulties in adopting Ubuntu.

I was also far from realizing that remove/install would trigger a recompilation.

Thanks once again.

---

### Post by lads on 2011-12-14
There was another kernel update yesterday, to release 3.0.0-14-generic, and VirtualBox became inoperable once again. Luckily removing and installing the virtualbox-dkms package solves the issue, since it triggers the re-build against the new kernel. For future reference here it is again the recipe:

```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by jcoles on 2011-12-14
> apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualbox-dkms


Any suggestions?

---

### Post by kaosent on 2011-12-24
Setting up a 10.04 LTS box for a  family member, encountered this same error (error loading, then, install virtualbox-ose-dkms and run modprobe vboxdrv)... after banging my head  against the wall, what worked was to simply add "vboxdrv" to /etc/modules and  run update-initramfs.

Rebooted, VirtualBox-OSE loaded up the WinXP instance without error.  Hope this helps somebody.

---

### Post by lads on 2011-12-27
> **jcoles said:**
> Any suggestions?

You're probably missing the Virtualbox repository. Add this entry to /var/apt/sources.list:

```
deb http://download.virtualbox.org/virtualbox/debian oneiric non-free
```

Hope it helps.

---

### Post by mashedbear on 2011-12-29
> **lads said:**
> There was another kernel update yesterday, to release 3.0.0-14-generic, and VirtualBox became inoperable once again. Luckily removing and installing the virtualbox-dkms package solves the issue, since it triggers the re-build against the new kernel. For future reference here it is again the recipe:

```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```
Thanks lads. Just came across the Kernel driver not installed rc=-1908 error. Removing and installing the virtualbox-dkms package has solved the issue for me as well.

cheers

---

### Post by lads on 2012-01-25
Another kernel update (3.0.0-15-generic) another VBox mess up. Luckily the recipe continues working.

Is there any way to trigger the recompiling of VBox whenever there's a kernel update? Or is this something that should be filed as a bug?

---

### Post by LordVeovis on 2012-02-06
> **lads said:**
> Another kernel update (3.0.0-15-generic) another VBox mess up. Luckily the recipe continues working.

Is there any way to trigger the recompiling of VBox whenever there's a kernel update? Or is this something that should be filed as a bug?

That is specifically what DKMS is supposed to do for you.  When you update you kernel DKMS recompiles all modules registered with it.

---

### Post by Rebelli0us on 2012-02-06
I have the latest version Oracle VirtualBox running in host Ubu 10.10 and guest Win7 runs flawless in VM (also Windows 8 Preview, and Win2000). Oracle's installation instructions on their download page work very well if you follow them.

---

### Post by lads on 2012-02-07
> **Rebelli0us said:**
> I have the latest version Oracle VirtualBox running in host Ubu 10.10 and guest Win7 runs flawless in VM (also Windows 8 Preview, and Win2000). Oracle's installation instructions on their download page work very well if you follow them.

Hi Rebellious. I also never had trouble until I upgraded to Ubuntu 11.04, this issue seems to be restricted to the 11 series, both .04 and .10.

---

### Post by lads on 2012-02-10
> **LordVeovis said:**
> That is specifically what DKMS is supposed to do for you.  When you update you kernel DKMS recompiles all modules registered with it.

Hi LordVeovies, I had missed your comment. If this is what DKMS is supposed to do, then it is not doing it:

```


$ ls -lah /usr/src/vir*
/usr/src/virtualbox-4.1.2:
total 56K
drwxr-xr-x 12 root root 4.0K 2012-01-25 10:50 .
drwxrwsr-x 12 root src  4.0K 2012-01-25 10:50 ..
drwxr-xr-x 10 root root 4.0K 2012-01-25 10:50 common
**-rw-r--r--  1 root root  503 2011-09-02 18:04 dkms.conf**
drwxr-xr-x  2 root root 4.0K 2012-01-25 10:50 generic
drwxr-xr-x  5 root root 4.0K 2012-01-25 10:50 include
-rw-r--r--  1 root root   65 2011-08-29 17:46 Makefile
drwxr-xr-x  3 root root 4.0K 2012-01-25 10:50 math
drwxr-xr-x  4 root root 4.0K 2012-01-25 10:50 r0drv
drwxr-xr-x  2 root root 4.0K 2012-01-25 10:50 VBox
drwxr-xr-x  3 root root 4.0K 2012-01-25 10:50 vboxdrv
drwxr-xr-x  3 root root 4.0K 2012-01-25 10:50 vboxnetadp
drwxr-xr-x  3 root root 4.0K 2012-01-25 10:50 vboxnetflt
drwxr-xr-x  3 root root 4.0K 2012-01-25 10:50 vboxpci

/usr/src/virtualbox-guest-4.1.2:
total 36K
drwxr-xr-x  7 root root 4.0K 2011-10-24 10:18 .
drwxrwsr-x 12 root src  4.0K 2012-01-25 10:50 ..
**-rw-r--r--  1 root root  402 2011-09-02 18:04 dkms.conf**
drwxr-xr-x  5 root root 4.0K 2011-10-24 10:18 include
-rw-r--r--  1 root root   53 2011-08-29 17:46 Makefile
drwxr-xr-x  4 root root 4.0K 2011-10-24 10:18 r0drv
drwxr-xr-x  5 root root 4.0K 2011-10-24 10:18 vboxguest
drwxr-xr-x  2 root root 4.0K 2011-10-24 10:18 vboxsf
drwxr-xr-x  2 root root 4.0K 2011-10-24 10:18 vboxvideo

$ dkms add virtualbox/4.1.2
Error! DKMS tree already contains: virtualbox-4.1.2
You cannot add the same module/version combo more than once.

$ dkms add virtualbox-guest/4.1.2
Error! DKMS tree already contains: virtualbox-guest-4.1.2
You cannot add the same module/version combo more than once.


```

Best.

---

### Post by lads on 2012-02-15
Another kernel update yesterday, and guess what? 

But this morning I got a little scare since the recipe didn't work on the first try. Only after recompiling it twice did VBox came back to life.

Of all the kind people that bothered to answer this thread no one ever mentioned the question on filling a bug. It seems this should be the case, but I'm a bit weary of doing it if it is not the case. Any thoughts?

---

### Post by lads on 2012-03-29
And here we are again; it is becoming like some sort of occult ritual. Let's hope this issue gets dealt with in Pangolin.

---

### Post by marsanyi on 2012-05-14
Thanks, guys: same problem, virtualbox-dkms uninstall-reinstall solution worked.

---

### Post by lads on 2012-06-20
And we are back!

After almost 3 months without trouble and with an Ubuntu upgrade in between I though this issue was gone for good. But today here it is, my favourite Ubuntu bug strikes again! Good thing the same [old solution]("http://ubuntuforums.org/showpost.php?p=11487796&postcount=9") still works.

---

### Post by CharlesA on 2012-06-20
> **lads said:**
> And we are back!

After almost 3 months without trouble and with an Ubuntu upgrade in between I though this issue was gone for good. But today here it is, my favourite Ubuntu bug strikes again! Good thing the same [old solution]("http://ubuntuforums.org/showpost.php?p=11487796&postcount=9") still works.
Was that on the host? I don't think I've ever had to install that particular package..

I don't even have that package installed on my guest:

```
ii  virtualbox-guest-dkms                  4.1.12-dfsg-2                           x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                 4.1.12-dfsg-2                           x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                   4.1.12-dfsg-2                           x86 virtualization solution - X11 guest utilities

```

---

### Post by lads on 2012-06-21
> **CharlesA said:**
> Was that on the host? I don't think I've ever had to install that particular package..

Which bears the question: if it is not triggering the automatic recompile, then why does it exists in the first place?

I just tried to remove it and indeed VBox functions as usual without it. We shall see what happens in the next kernel update.

---

### Post by CharlesA on 2012-06-21
> **lads said:**
> Which bears the question: if it is not triggering the automatic recompile, then why does it exists in the first place?

I just tried to remove it and indeed VBox functions as usual without it. We shall see what happens in the next kernel update.
Did you install vbox from the repos or from virtualbox.org? I've always installed it from virtualbox.org.

---

### Post by lads on 2012-06-22
I don't really get this. Yesterday, after removing the virtualbox-dkms package VBox continued working as before, but this morning there was no way the Windows virtual machine could start up. I had to re-install the package to get it back.

In conclusion: at least Winblows virtual machines seems to need this package, but its automatic recompilation is not succeeding when the kernel gets upgraded. 

> **CharlesA said:**
> Did you install vbox from the repos or from virtualbox.org? I've always installed it from virtualbox.org.

VBox was already installed when this laptop was assigned to me. Anyway I can know which method was used?

I had several issues in the past installing VBox from the repos, this is one of the apps I always install from the official site.

Thanks for answering.

---

### Post by CharlesA on 2012-06-22
> **lads said:**
> 
VBox was already installed when this laptop was assigned to me. Anyway I can know which method was used?

You can check /etc/apt/sources.list

I have a feeling it's the version from the repos, as the virtualbox.org version just got updated to 4.1.18 yesterday or the day before.

---

### Post by lads on 2012-06-23
> **CharlesA said:**
> You can check /etc/apt/sources.list

I have a feeling it's the version from the repos, as the virtualbox.org version just got updated to 4.1.18 yesterday or the day before.

It seems so:

```
$ cat /etc/apt/sources.list | grep box
# Virtualbox SUN repository
# deb http://download.virtualbox.org/virtualbox/debian precise non-free # disabled on upgrade to natty disabled on upgrade to precise
```

The version I have installed is 4.1.12_Ubuntu.

Best.

---

### Post by CharlesA on 2012-06-23
Yeah, it's a version from the Ubuntu repos.

I wonder if that is why it pulled in those other packages.

The virtualbox repo hasn't used non-free since 3.x, With 4.0 they moved to contrib.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

According to [https://launchpad.net/ubuntu/+source/virtualbox](https://launchpad.net/ubuntu/+source/virtualbox) the version you have matches the version from the repos for Precise.

EDIT:

Yep, the version of virtualbox from the repos pulls in those extra packages:

```
charles@Tardis:~$ dpkg -l | grep virtual
ii  virtualbox                         4.1.12-dfsg-2ubuntu0.1     x86 virtualization solution - base binaries
ii  virtualbox-dkms                    4.1.12-dfsg-2ubuntu0.1     x86 virtualization solution - kernel module sources for dkms
ii  virtualbox-qt                      4.1.12-dfsg-2ubuntu0.1     x86 virtualization solution - Qt based user interface

```

The package from virtualbox.org reads as this:

```
charles@Thor:~$ dpkg -l | grep virtual
ii  virtualbox-4.1                       4.1.18-78361~Ubuntu~precise         Oracle VM VirtualBox

```

---

### Post by deepakhw on 2012-08-13
Thanks, this is the correct solution!

---

### Post by lads on 2012-08-24
Today I got a new kernel version: 3.2.0-29-generic. Guess what happened :)

---

### Post by jcllings on 2012-08-26
Fix works for me but since my machine rarely ever gets turned off, the module eventually unloads. How can I load it automagically or not unload it. Some kind of conf in /etc having to do with dkms or modprobe, right?

jcllings

---

### Post by CharlesA on 2012-08-26
The module shouldn't automatically unload. Check your logs to see what is causing it to unload.

---

### Post by desch on 2012-09-06
> **lads said:**
> Today I got a new kernel version: 3.2.0-29-generic. Guess what happened :)

I just tried to install virtualbox on a 12.04 with kernel 3.2.0-29 for the first time. Installing from the ubuntu repos gives an error installing modules eventually causing the rc=-1908 error. Downloading and installing the DEB-file from the virtualbox website doesn't work either for me. It will try to compile the modules but without success. 

Can you tell me what the exact way should be to install virtualbox?

the virtualbox-dkms remove/install sequence does not work in my case.

Many thanks in advance.

Cheers.

---

### Post by phord2 on 2012-10-01
> **lads said:**
> And here we are again; it is becoming like some sort of occult ritual. Let's hope this issue gets dealt with in Pangolin.

I haven't had this problem before in spite of using VirtualBox and Ubuntu for several years now.  But today it appeared on my system after 
 1. I updated to 3.2.0-31 last weekend (Saturday 2012-09-22), and
 2. I rebooted my laptop this weekend (Saturday 2012-09-29). 

Up until the 2nd event (the reboot) I was able to use VirtualBox just fine.  I think that means the kernel update caused the problem, but the symptom was hidden until after the next reboot. Anyway, the prescribed ritual did indeed fix the problem.

I went to investigate the dkms package a bit more so I could explain the problem correctly when I file a bug report.  I see there is a way to get dkms to show the current status for any supported modules.  Since I did the reinstall dance, though, my dkms-supported modules are all up-to-date.

So, if you have this problem and you have not corrected it yet, please try this command first and post the results here to help diagnose the issue:

```

$ dkms status

```


Also, you might try this update method before you try the apt-get remove/install dance.  If this triggers a rebuild of the virtualbox drivers for you, then maybe the problem lies in the dkms config somewhere.

```

$ sudo dkms autoinstall

```

Here's what the status command shows for me now that my virtualbox has been corrected:

```

$ dkms status
nvidia-current, 295.40, 3.2.0-27-generic, x86_64: installed
nvidia-current, 295.40, 3.2.0-29-generic, x86_64: installed
nvidia-current, 295.40, 3.2.0-30-generic, x86_64: installed
nvidia-current, 295.40, 3.2.0-31-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-27-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-29-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-30-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-31-generic, x86_64: installed
virtualbox, 4.1.12, 3.2.0-31-generic, x86_64: installed

```

It seems that my nvidia drivers have successfully updated across several versions since my OS reinstall in July.  I think I lost the VirtualBox history when I removed the dkms-virtualbox package.

I was able to build the virtualbox drivers for an older kernel with this command:

```

$ sudo dkms autoinstall -k 3.2.0-30-generic

```


:redface: One more note:  I may have run out of disk space on /usr during one of the recent updates.  I freed up space and reattempted the update.  I didn't appear to have any problems after that.  Not sure if it's related.  Did this also happen to anyone else here?

---

### Post by lads on 2012-10-02
Hi phord, thank you for your advice. Personally this issue hasn't haunted me since late August, which is the longest span of time since it came; I imagine the new  release is keeping a lot of people busy at the time. Nevertheless, others have reported the issue in the meantime and this thread now counts over 22 k visits, half of which in the past 2 months alone.

If you happen to open a bug report please post the link here. Thanks.

---

### Post by crayor on 2012-10-15
I do have the problems described for VirtualBox and re-installation did not work for me.

Any idea?

jr@jr-ThinkCentre-A57:~$ dkms status
nvidia-173, 173.14.35, 3.2.0-31-generic-pae, i686: installed
nvidia-173, 173.14.35, 3.2.0-32-generic, i686: installedError! Could not locate dkms.conf file.
File:  does not exist.

nvidia-173, 173.14.35, 3.2.0-32-generic-pae, i686: installed
nvidia-current, 295.40, 3.2.0-26-generic-pae, i686: installed
nvidia-current, 295.40, 3.2.0-31-generic, i686: installed
nvidia-current, 295.40, 3.2.0-32-generic, i686: installed
nvidia-current, 295.40, 3.2.0-32-generic-pae, i686: installed
jr@jr-ThinkCentre-A57:~$ dkms status
nvidia-173, 173.14.35, 3.2.0-31-generic-pae, i686: installed
nvidia-173, 173.14.35, 3.2.0-32-generic, i686: installed
nvidia-173, 173.14.35, 3.2.0-32-generic-pae, i686: installed
nvidia-current, 295.40, 3.2.0-26-generic-pae, i686: installed
nvidia-current, 295.40, 3.2.0-31-generic, i686: installedError! Could not locate dkms.conf file.
File:  does not exist.

nvidia-current, 295.40, 3.2.0-32-generic, i686: installed
nvidia-current, 295.40, 3.2.0-32-generic-pae, i686: installed
jr@jr-ThinkCentre-A57:~$ sudo dkms autoinstall
Error! Could not locate dkms.conf file.
File:  does not exist.
jr@jr-ThinkCentre-A57:~$ 

> **phord2 said:**
> I haven't had this problem before in spite of using VirtualBox and Ubuntu for several years now.  But today it appeared on my system after 
 1. I updated to 3.2.0-31 last weekend (Saturday 2012-09-22), and
 2. I rebooted my laptop this weekend (Saturday 2012-09-29). 

Up until the 2nd event (the reboot) I was able to use VirtualBox just fine.  I think that means the kernel update caused the problem, but the symptom was hidden until after the next reboot. Anyway, the prescribed ritual did indeed fix the problem.

I went to investigate the dkms package a bit more so I could explain the problem correctly when I file a bug report.  I see there is a way to get dkms to show the current status for any supported modules.  Since I did the reinstall dance, though, my dkms-supported modules are all up-to-date.

So, if you have this problem and you have not corrected it yet, please try this command first and post the results here to help diagnose the issue:

```

$ dkms status

```


Also, you might try this update method before you try the apt-get remove/install dance.  If this triggers a rebuild of the virtualbox drivers for you, then maybe the problem lies in the dkms config somewhere.

```

$ sudo dkms autoinstall

```

Here's what the status command shows for me now that my virtualbox has been corrected:

```

$ dkms status
nvidia-current, 295.40, 3.2.0-27-generic, x86_64: installed
nvidia-current, 295.40, 3.2.0-29-generic, x86_64: installed
nvidia-current, 295.40, 3.2.0-30-generic, x86_64: installed
nvidia-current, 295.40, 3.2.0-31-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-27-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-29-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-30-generic, x86_64: installed
nvidia-current-updates, 295.49, 3.2.0-31-generic, x86_64: installed
virtualbox, 4.1.12, 3.2.0-31-generic, x86_64: installed

```

It seems that my nvidia drivers have successfully updated across several versions since my OS reinstall in July.  I think I lost the VirtualBox history when I removed the dkms-virtualbox package.

I was able to build the virtualbox drivers for an older kernel with this command:

```

$ sudo dkms autoinstall -k 3.2.0-30-generic

```


:redface: One more note:  I may have run out of disk space on /usr during one of the recent updates.  I freed up space and reattempted the update.  I didn't appear to have any problems after that.  Not sure if it's related.  Did this also happen to anyone else here?

---

### Post by aga021 on 2012-10-20
Hi, I'm new to Virtual Box and came across this problem today.  I've tried the fix, but am getting this message:


$ sudo apt-get remove virtualbox-dkms
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualbox-dkms

I see somebody else had this problem, but I did not understand the solution offered, please can somebody put it in layman's terms?

I'm using Ubuntu 11.04.

Thanks.

---

### Post by CharlesA on 2012-10-20
That package is only installed if you have the version of virtualbox that is in the ubuntu repos, not the one from virtualbox.org installed.

---

### Post by aga021 on 2012-10-21
Thanks for your reply, I did install from virtualbox.org - is there another fix for this?

---

### Post by CharlesA on 2012-10-21
Run this:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Chuck Glenn on 2012-10-25
Here's what my newly-installed VirtualBox says a day after installing 12.10:

Error! Your kernel headers for kernel 3.5.0-17-generic cannot be found.
Please install the linux-headers-3.5.0-17-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

And as for the suggestion to run sudo /etc/init.d/vboxdrv setup...

sudo: /etc/init.d/vboxdrv: command not found

So I guess I wait for... something???

---

### Post by CharlesA on 2012-10-25
Install the kernel headers:

```
sudo apt-get install linux-headers-3.5.0-17-generic
```

Unless something has change between 12.04 and 12.10, there should be vboxdrv in /etc/init.d/

---

### Post by deymos34 on 2012-10-26
Faced that situation with new 12.10 as well (clean installation, Virtualbox installed from repo, tried to reinstall both VirtualBox and Ubuntu itself).

 Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/etc/init.d/vboxdrv setup'
as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Failed to open a session for the virtual machine Ubuntu.
The virtual machine 'Ubuntu' has terminated unexpectedly during startup with exit code 1.
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}

But there is no /etc/init.d/vboxdrv, only [COLOR=#0000ff][COLOR=Black][COLOR=#0000ff][COLOR=Black]/etc/init.d/virtualbox. I tried to install [/COLOR][/COLOR][/COLOR][/COLOR]linux-headers-3.5.0-17-generic, and installation was a success, but that changed nothing.

Would be interesting to hear a word from a person, who use Virtualbox in 12.10, so we'll now things are not completely broken.

---

### Post by emrys on 2012-10-31
> **CharlesA said:**
> Install the kernel headers:

```
sudo apt-get install linux-headers-3.5.0-17-generic
```

Unless something has change between 12.04 and 12.10, there should be vboxdrv in /etc/init.d/

OK, problem solved. With 12.10 I had to:

sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

And then, in VBox, go to Settings, System, Acceleration, and disable the option "Enable VT-x/AMD-V" - This might be a specific problem of my setup though.

Thanks!

---

### Post by deymos34 on 2012-10-31
> **emrys said:**
> 
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
Confirm, reinstallation of virtualbox-dkms after installation of linux-headers-3.5.0-17-generic solved problem for me as well. Happily there was no need to disable option "Enable VT-x/AMD-V" in my case.

---

### Post by undoIT on 2012-11-03
> **emrys said:**
> 
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms


This worked perfectly for me with Virtualbox installed from repos. Didn't have to reboot or disable anything. There was an error with the network connection on the Appliance I had imported. I set Network to "Not Attached" and then back to "Bridged" and now Virtualbox is working just fine.

Thanks for sharing.

---

### Post by rondre on 2012-11-03
> **emrys said:**
> OK, problem solved. With 12.10 I had to:

sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms


This worked for me as well - no other config needed - thanks so much!

---

### Post by twipley on 2012-11-06
If you had installed VirtualBox FROM THE WEBSITE DEB FILE:

Simply run the website-downloaded deb file, and select "reinstall," which will be fixing the issue in addition to keeping all of the virtual machines that you already had before.


Source: I just had this problem.

---

### Post by deymos34 on 2012-11-07
After upgrade of Linux kernel problem returned, and was solved by the same commands, except that linux headers version was updated to match new kernel version:

sudo apt-get install linux-headers-3.5.0-18-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

You should restart after executung this commands.

---

### Post by CharlesA on 2012-11-07
> **deymos34 said:**
> After upgrade of Linux kernel problem returned, and was solved by the same commands, except that linux headers version was updated to match new kernel version

Easier fix:


```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by projectrk on 2012-11-11
> **CharlesA said:**
> Easier fix:


```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```


thank you very much for this, been looking for this solutions for months googling and reading the each topic here in the forum. now its working great.

---

### Post by Kooster on 2012-11-16
Make sure your kernel headers is installed. Use synaptic and search linux-kernel-headers-generic (-pae) It worked like a charm. With the error the installation cannot find the script file for the kernel. Easy peasy.:guitar:

---

### Post by brunomicas on 2012-11-24
Hello,

I had the same problem and yesterday i solve following this topic. I worked fine in VirtualBox and all works fine. Thanks!

However, today, when i restart my pc (asus k55v) unity bar disappeared. I'm newbie in Ubuntu so i can't do nothing without unity bar and top bar.

I'm writing this reply from another pc :(

I try reinstall VBox in terminal, with "Ctrl+Alt+t" and using code* in this topic, restart but didn't work.

I searched on google but without success.
Someone can help me?

thanks

*
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

---

### Post by brunomicas on 2012-11-24
> **brunomicas said:**
> Hello,

I had the same problem and yesterday i solve following this topic. I worked fine in VirtualBox and all works fine. Thanks!

However, today, when i restart my pc (asus k55v) unity bar disappeared. I'm newbie in Ubuntu so i can't do nothing without unity bar and top bar.

I'm writing this reply from another pc :(

I try reinstall VBox in terminal, with "Ctrl+Alt+t" and using code* in this topic, restart but didn't work.

I searched on google but without success.
Someone can help me?

thanks

*
sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

I'm reply now in my pc again :)

What i do:
Search in google how i can access software center by terminal, so,
"Ctrl+Alt+t" and i insert: sudo software-center

Then i search "dkms" and uninstall it.

Unity come back after restart,
i reinstall VirtualBox and working too.

I restart pc, everything is ok

I hope everything continues ok tomorrow :P

---

### Post by jds340 on 2012-12-25
the above solution didn't work for me. Any ideas?

---

### Post by lads on 2012-12-28
> **jds340 said:**
> the above solution didn't work for me. Any ideas?

Hi jds340, in Ubuntu 12.10 the solution [appears to be slightly different]("http://ubuntuforums.org/showpost.php?p=12329084&postcount=48"). Have you tried it that way?

---

### Post by johnkaranjaM on 2013-01-28
Just install the latest version of VirtualBox (4.2.6) from this link,
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by lads on 2013-01-30
> **johnkaranjaM said:**
> Just install the latest version of VirtualBox (4.2.6) from this link,
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Hi John, that way you get two versions of VBox installed, and without getting updates for the one you suggest.

---

### Post by Wobbo on 2013-01-30
Thanks, "Kernel driver not installed (rc=-1908)" is solved!

---

### Post by CharlesA on 2013-01-30
> **lads said:**
> Hi John, that way you get two versions of VBox installed, and without getting updates for the one you suggest.

Not exactly. You cannot have both versions of VirtualBox installed at the same time as they conflict with each other and have different dependencies. If you are going to use the one from virtualbox.org, you need to purge the OSE edition that was installed from the Ubuntu repos.

After it is purged, I recommend adding the VirtualBox repo to your sources.list instead of just installing the deb, that way your version of VirtualBox is kept up-to-date.

---

### Post by dibuntux on 2013-02-01
Same problem here: I checked with 
ttdave@ttbunt:~$ dkms status
fglrx, 8.960, 3.2.0-36-generic, x86_64: installed
fglrx, 8.960, 3.2.0-37-generic, x86_64: installed

so...no virtualbox marked installed in dkms 

then I found this on the net:

I have been having this same problem and I think I fixed it today. Turns out that the virtualbox update never deleted the old directory from /var/lib/dkms/vboxhost. In my case the old version was 4.1.4. I'm currently running 4.1.8 but I swear I was running 4.1.4, then 4.1.6, and now 4.1.8. So I think the problem actually began between the 4.1.4 and 4.1.6 releases.

To resolve this simply delete the old directory and then run the setup again:

Code: Select all   Expand view
    $ cd /var/lib/dkms/vboxhost
    $ sudo rm -rf 4.1.4
    $ sudo /etc/init.d/vboxdrv setup

So I moved all the stuff I had from /var/lib/dkms/vboxhost in another place (just in case...) and then did the usual dance:

sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

checked fi virtualbox was working, and it was so I checked again dkms:
ttdave@ttbunt:~$ dkms status
fglrx, 8.960, 2.6.32-44-generic, x86_64: installed
fglrx, 8.960, 3.2.0-32-generic, x86_64: installed
fglrx, 8.960, 3.2.0-33-generic, x86_64: installed
fglrx, 8.960, 3.2.0-34-generic, x86_64: installed
fglrx, 8.960, 3.2.0-35-generic, x86_64: installed
fglrx, 8.960, 3.2.0-36-generic, x86_64: installed
fglrx, 8.960, 3.2.0-37-generic, x86_64: installed
virtualbox, 4.1.12, 3.2.0-37-generic, x86_64: installed

Now virtualbox is listed as installed in dkms! Hopefully at next kernel release it will compile automatically as it should (and was in 10.04 lts)

---

### Post by P05TMAN on 2013-02-12
> **emrys said:**
> OK, problem solved. With 12.10 I had to:

sudo apt-get install linux-headers-3.5.0-17-generic
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

And then, in VBox, go to Settings, System, Acceleration, and disable the option "Enable VT-x/AMD-V" - This might be a specific problem of my setup though.

Thanks!

Yeah, this solved my issue too. Excellent! Thank you!

---

### Post by lads on 2013-02-14
After 6 months without trouble this issue is back on 12.04. Good thing the old solution still does it.

This thread has now over 50 k visits, which is about 2.5 times what the Ubuntu Phone thread has, pretty impressive.

---

### Post by lads on 2013-02-19
Back again after only 5 days running... and this time the old solution doesn't seem to work.

Can anyone help?

---

### Post by lads on 2013-02-20
> **lads said:**
> Back again after only 5 days running... and this time the 

After a reboot and a second try it worked. VBox getting the MS syndrome?

---

### Post by CharlesA on 2013-02-20
> **lads said:**
> After a reboot and a second try it worked. VBox getting the MS syndrome?
Only the OSE edition in the Ubuntu repos, apparently.

I've only had problems with the version from virtualbox.org when I decided to migrate my VMs to another user and screwed up the permissions.

---

### Post by ElijahLynn on 2013-04-11
> **lolpenguin said:**
> Did you upgrade your kernel? Virtualbox depends on kernel modules so you have to recompile them:
```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

Thanks for this, I set this as a *fixvm* alias in .bash_aliases and passed the yes argument in addition to concatenating the commands.

```
alias fixvm='sudo apt-get remove virtualbox-dkms -y && sudo apt-get install virtualbox-dkms -y' 
```

Now I just type ```
fixvm
``` and it takes care of it!

---

### Post by yyli on 2013-10-21
> **lads said:**
> There was another kernel update yesterday, to release 3.0.0-14-generic, and VirtualBox became inoperable once again. Luckily removing and installing the virtualbox-dkms package solves the issue, since it triggers the re-build against the new kernel. For future reference here it is again the recipe:

```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

thanks lads, this solution works for me

---

### Post by lads on 2013-12-19
This error is back again on Ubuntu 12.04 (kernel 3.2.0-57-generic). The old solution is so far not producing any results. Updates to follow.

---

### Post by JKyleOKC on 2013-12-19
Have you installed the newest update, 4.3.6? I've not yet done so and my 12.04.3 systems are both working properly, but when I did the previous update I found that "saved" VMs would not load until I discarded the saved data. Once the VM was back to powered-down state, it loaded properly and all data in the virtual drives was in good shape. Apparently changes are happening in the saved-data metadata, causing problems unless the VM was saved with the same vbox version that is attempting to restore it...

---

### Post by lads on 2013-12-21
With VBox out of order on my main 12.04 system, I proceeded to try it out on 13.10. I installed VBox 4.3 from the Oracle PPA following [this guide]("http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/"). Right on the first run VBox complains with this same error (Kernel driver not installed). This happens with VMs without saved state.

What is going on?

---

### Post by JKyleOKC on 2013-12-22
Do you have the linux-headers-generic, build-essentials, and dkms packages installed on 13.10? All three packages are required in order to install any version of vbox, or any updates to it...

---

### Post by lads on 2013-12-29
> **JKyleOKC said:**
> Do you have the linux-headers-generic, build-essentials, and dkms packages installed on 13.10?

I was missing *linux-headers-generic*. Thanks.

---

### Post by lads on 2014-02-05
Two years and 100 00 views later this problem still goes on. Right now [the fix provided by CharlesA]("http://ubuntuforums.org/showthread.php?t=1885936&p=12342002#post12342002") seems to be the only one working properly on Ubuntu 12.04.

---

### Post by CharlesA on 2014-02-05
Glad that still works, but it sucks that there seem to be so many people running into the same problems. Kinda makes me glad I moved from Vbox to KVM.

I'm not sure if it'll work on the newer versions though.

---

### Post by Koray_Bilgin on 2014-04-28
Thanks so much. That did it :).

---

### Post by lads on 2014-07-17
32 months, 5 releases and 120 000 views later, this bug is back!

On 14.04 I am trying to solve it this way:

sudo apt-get install linux-headers-generic dkms
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

But it has no effect. There is no *build-essentials* package for 14.04, could that be the cause?

---

### Post by QIII on 2014-07-17
Is that a typo?

Do you mean "build-essential" (sans the "s" at the end)?

---

### Post by lads on 2014-07-17
Yes it is a typo, the package is *build-essential* and I already have it installed ... meaning that the exact 13.10 fix does not work at all.

---

### Post by lads on 2014-07-17
The fix for 14.04 is indeed different, but not that different:

sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms

The *install virtualbox-dkms* command was actually failing using the 13.10 fix. By fully purging the package things got back to normal.

See you in a few months ;)

---

### Post by andrew69 on 2014-07-23
None of these helped.

Ubuntu update ****ed up my system.

I havent been able to work for 2 days because of this ****.

---

### Post by CoreyRuhno on 2014-07-31
So I can now load Virtual Box but my virtual machine is not recognized. Its like I never made it. I do still have the folder so the files are still there. . .

Im on 13.10 and did:

sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

---

### Post by milovan2 on 2014-08-22
> **andrew69 said:**
> None of these helped.

Ubuntu update ****ed up my system.

I havent been able to work for 2 days because of this ****.

Same goes for me... I lost **[COLOR=#ff0000]6 months of research[/COLOR]**!!! :evil:  God knows how many hours I was working on it. And now, there is no f*** way to return all that data. Coz I can't access my virtual OS! True, I do have copy of unprocessed data... But it'll take me months to do everything all over again. In meantime, I can easily **[COLOR=#ff0000]lost founds for project[/COLOR]**... Thanks alot, f***king VirtualBox! :evil: And you too, Ubuntu's research team. Thanks alot! :evil: 


I don't understand you developers. ](*,)If you know that new thing isn't going to work well (which is understandable, we all make some new things which doesn't work at the beginning as they are supposed to), why suggest/force your users to update into that version in a first place? Why? Why did you do such a stupid thing? Take your time! Make things right, but give us good product. Not some stupid cosmetical update, which makes mess (and when I say "mess" I mean f*** up everything). Now my [COLOR=#0000ff]whole system is unstable[/COLOR]. I can't do a whole list of things... But, I'll manage that somehow... Problem is that you from time to time do f****ups. Don't do that. Please! [-o< I started using Linux/Ubuntu because Windows was doing that sh**. 
:arrow: Understand this. As an User, I was [COLOR=#0000ff]happy with old version which was working just fine[/COLOR]. 
:arrow: I don't need some small tweaks  which will eventually make system unstable, and I definitely don't need something that will destroy my data. Don't do that. 
**Sit down, take your time and do things right. **Don't hurry. All of us are using Linux because we like it! Never forget that! 
Yes... We all know that on the other side, it has its own downsizes too. But we still choosed to use it! 
Even when you do this kind of f***ups, we will continue to use Linux. Coz we like it! Call us crazy, call us stupid... Whatever! But we like it! :) 
So, please. **Try not to do more damage than good with these updates which you are making. **Thank you  in advance.

---

### Post by CharlesA on 2014-08-22
Considering the developers don't read these forums, you are just shouting at your fellow users. :)

Do you not have backups? If you do not, you can try to copy the entire VirtualBox VMs folder and the .VirtualBox folder to another machine (with virtualbox installed) and see if the VM will load or not. I have used that method to move VMs between machines before, but only on Windows - there is no reason it shouldn't work on Linux as well. If you are using VirtualBox for mission critical appliances, I would suggest moving to KVM or something else that is built into the base kernel so you don't have to deal with third party kernel modules breaking things.

FWIW: I moved off on VirtualBox on Linux a while ago - ended up converting the virtual hard drive to qcow2 via this [method.]("http://cheznick.net/main/content/converting-a-virtual-machine-from-virtualbox-to-kvm")

Hope that helps.

---

### Post by milovan2 on 2014-08-25
They don't?! :| 8-[ Ups... :oops: I'm very sorry my fellow users. Please accept my apologies. :oops: I was out of my mind, because I was thinking that I lost research...

Thanks for advice CharlesA. :)
Even without reading your post, I have done that. :D I found on some russian website similar suggestion so I went for it. And it worked! :) 
Nevertheless, thanks for the advice friend. :)

---

### Post by Asalle_Kim on 2014-10-20
You just saved my life!
Worked for
Ubuntu 14.04 on x64

The incorrect kernel compilation and installation caused this problem.

kind regards, 
Asalle

---

### Post by lads on 2015-01-16
Well, here we are again. I am still using Ubuntu 14.04, and yet again the previous fix is not working:

```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

After this this error message is still showing up. Any ideas?

---

### Post by mcoyle on 2015-01-30
> **lads said:**
> ***UPDATE**: Jump to [the solution]("http://ubuntuforums.org/showpost.php?p=11487796&postcount=9").*

Hello everyone,

The following is from a Ubuntu 11.10 64-bit install, that has been running VBox without trouble for a month.

This morning as I tried to start a Win7 virtual machine (that I've used every day) I got a window with these messages:

```
VirtualBox - Error

Failed to open a session for the virtual machine Windows7.
The virtual machine 'Windows7' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
```
And a second window with this:

```
VirtualBox - Error in suplibOsInit

Kernel driver not installed (rc=-1908)

Please install the virtualbox-dkms package and execute 'modprobe vboxdrv' as root.
```


For many people, the supplied solution of rebuilding the kernel modules works (virtualbox-dkms), but it didn't work for me and many others. I think I may have addition info to finally put this puppy to bed. This solution is based on the following: I initially installed 14.04 (Trusty) and upgraded to 14.10 (Utopic), but this problem is older than these versions and I think can happen anytime you perform an upgrade from one version to another causing the installed kernel to get out of sync with the installed headers. 

First, use synapic to fully uninstall virtualbox.

For me, the problem seems to be that the kernel (3.13-43) didn't have matching headers installed (I had 3.16!). My solution was to use [this page]("http://packages.ubuntu.com/") to hunt down the disto that contained the headers I needed. I then added the appropriate repository to my /etc/apt/sources.list. In my case it was 14.04, trusty tar:

```
deb http://security.ubuntu.com/ubuntu trusty-security main
```

Now you can use synaptic to install the missing headers, and then reinstall Virtualbox. 

Virtualbox will now be able to build its modules since the correct kernel headers are installed. 

Good luck!
Michael

---

### Post by lads on 2015-03-30
And here we are 3 and an half years later. On Ubuntu 14.04 it is already the fourth time VirtualBox stops functioning due to this issue. At this stage I am only aware of one solution, that may not work at the first try:

```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo reboot
sudo apt-get install virtualbox-dkms
```

---

### Post by toby_1_kenobi on 2015-10-12
In 15.04 I got the same problem, but it turned out it was the result of running a kernel that was older then the ones in the repository. I had upgraded from a previous distribution, but the kernel did not get upgraded (don't know why) so `uname -r` showed me I was running linux 3.16 and `apt-cache search linux-headers-` showed the repositories only held headers for linux 3.19. That was why virtualbox-dkms couldn't configure for the running kernel.

The solution was just to `sudo apt-get install linux-generic` and reboot. Virtualbox worked fine after that.

---

