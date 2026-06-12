---
title: "AMD APU  and Virutal Box - use AMDGPU instead of Radeon?"
date: 2020-01-22
forum: Virtualisation
---

### Post by kellyvotrenom on 2020-01-22
I have recently been having problems with video in Virtualbox that suddenly developed, in that I didn't make any changes to the system other than required updates.  I am curious if it could have anything to do with the video on the host system. I was running VBox 6.1 and everything was fine for a while and then problems started where video wouldn't play and the machine would bog down.  

The only thing I can guess right now is some update caused conflicts with the driver being used, which appears to be Radeon.  I have re-installed VBox, installed an earlier version, tried different distros and results are all pretty similar.  I just installed Manjaro and it is the least affected but tells me I do not have hardware acceleration enabled when I start the machine, even though I do have it ticked in the 'Settings'. (Note: this is my first attempt at Manjaro so it may be that I need to change things in Manjaro - fairly steep learning curve with my first jump into Arch).

Guest additions are installed, it gets worse the longer the virtual machine is on and processes in the host can make things really slow.  The only reason suspect the video setup is that the audio is still being processed while the video freezes.  Host system is fine and I have tried all sorts of memory, processor and video combinations.

Ubuntu 16.04 with Cinnamon desktop.  Here are some outputs from commands suggested from other posts. If someone could suggest where else to look for clues, it would be much appreciated.  BTW, I have read some post regarding the use of AMDGPU in 16.04 but I still don't understand which is the best driver to use.

Thanks

```
 lspci -k | grep -EA3 'VGA|3D|Display'
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics] (rev d6)
    Subsystem: ASRock Incorporation Kaveri [Radeon R7 Graphics]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu
```

```
$ lsmod | grep amdgpu
amdgpu               2740224  0
chash                  16384  1 amdgpu
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   106496  2 amdgpu,radeon
drm_kms_helper        172032  2 amdgpu,radeon
drm                   401408  8 drm_kms_helper,amdgpu,radeon,ttm
```

```
$ lsmod | grep radeon
radeon               1466368  17
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   106496  2 amdgpu,radeon
drm_kms_helper        172032  2 amdgpu,radeon
drm                   401408  8 drm_kms_helper,amdgpu,radeon,ttm
```

---

### Post by QIII on 2020-01-22
Are those results from the host or the VM?

(I already know.  This is an exercise in understanding how the VM communicates with the host through a hardware abstraction layer.)

---

### Post by kellyvotrenom on 2020-01-23
OK - let's see how I do :)

Yes, that's the host machine. However, your reply made me go back and check something I did earlier and forgot about.  I believe that I am the wrong track with video, I ran htop in the guest machine and host machine at the same time and watched the results.  The CPU usage goes over 100% when the video freezes; the process that is hogging the CPU in the guest machine is either the browser, or in the case of Manjaro, the Cinnamon desktop.  The process in the host machine is, of course, Virtualbox.

So, for some reason, the Virtualbox installation is using a lot of CPU power because of high CPU usage in the guest.

Just so you know, I have installed well over a dozen virtual machines on this computer and had them all running well. In the past month I have installed and re-installed several machines as well as a few new installs of Virtualbox; so not a complete noob.  It was not long after the upgrade to 6.1 that this started to happen but not directly.  I downgraded to 5.2 thinking that my machine was not powerful enough for the upgrade but that didn't change the behavior.

So I guess my real question is: what caused VBox to start becoming so resource heavy? What do I look for?

Thanks, hope my additional info is on helpful and on target
.

---

### Post by kellyvotrenom on 2020-01-24
I posted this -  [https://ubuntuforums.org/showthread.php?t=2435587](https://ubuntuforums.org/showthread.php?t=2435587) - but it's the wrong question.

My problem is that Virualbox's performance on my computer continues to worsen.  What I noticed at first was that trying to record the screen became jerky, then the browser performance started to slow down, having multiple tabs slowed the browser down to unusable.  Now it seems to be taking longer to start a machine as well.  What's most interesting is that it seems to be a gradual decline, even with re-installations.

I have tried multiple distros, multiple processor, memory & video settings for the Guest machine (all distros were versions of Ubuntu except a recent install of Manjaro) - all results show similar performance. Nested pages has been turned on and off; AMD VT is enabled; 2D &3D acceleration have been turned on and off.  I have completely un-installed and re-installed Virtualbox 6.1 and lastly loaded 5.2 back on to see if was just because my computer could not handle 6.1, even though 6.1 had been running fine for several months.  Previously, I had been running 5.x for a couple of years with no problems.  All on the same machine, no major changes to the system other than required updates.

My system is an AMD A10-7860K Radeon R7, 12 Compute Cores 4C+8G  with 8Gb of memory, with a 250Gb SSD.  I am running Ubuntu 16.04 LTS with Cinnamon desktop.  Other than the problems with the Virtualbox installation, the system runs flawlessly.

I have run htop on the host and can see the CPU percentage jump to over 100% when the guest freezes; monitoring the guest with htop shows similar activity.  

Thanks, any help would be appreciated.

---

### Post by howefield on 2020-01-24
Duplicate threads merged and moved to the "*Virtualisation*" forum for a better fit.

---

### Post by kellyvotrenom on 2020-01-24
Thanks - I'll follow it there

---

### Post by QIII on 2020-01-24
Ignore what your host machine sports as its GPU.  A VM in VirtualBox has access only to a virtual GPU provided by the Hardware Abstraction Layer in VirtualBox.

If you run the three commands above in your VM, you might find something interesting.

---

### Post by kellyvotrenom on 2020-02-08
Just wanted to follow up on this, it took a while to track down.  The problem ended up being a problem with the browser installation on the virtual machine.  It took me a while to ascertain this because of multiple issues with different VMs.  At first it seemed like it was consistent across all VMs with any browser.  Further testing showed that certain browsers worked in certain VMs and that the Manjaro VM got corrupted somehow and became slow to load and exhibited the problems with all browsers.  The LXLE VM wouldn't run flash in my main browser (Vivaldi) but I found other browsers that did work in that VM.

I finally got Vivaldi working with no problems on an Xubuntu installation. The final piece of the puzzle was installing Vivaldi Snapshot that seemed to re-install the Flash Plug and now is continuing to run fine.

---

