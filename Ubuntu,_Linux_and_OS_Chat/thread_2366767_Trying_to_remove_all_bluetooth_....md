---
title: "Trying to remove all bluetooth ..."
date: 2017-07-21
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2017-07-21
Bit of a rant here.

Bluetooth is a huge security issue.  Got hacked through it last fall in a freshly installed, patched the day prior, Ubuntu system. No network services were running, but BT was installed and enabled by default.

Finally getting around to removing. It has been disabled since I traced the root cause for the hack.

Removed blueman, no issues, but 

```
$ sudo apt purge libbluetooth3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brltty* brltty-x11* kodi* kodi-bin* libbluetooth3* qemu* qemu-kvm*
  qemu-system* qemu-system-arm* qemu-system-mips* qemu-system-misc*
  qemu-system-ppc* qemu-system-sparc* qemu-system-x86*

```
is going to remove my hypervisor and media center software?  Really?  Seems like a huge bug to have either of those tied to a bluetooth library.

---

### Post by vocx on 2017-07-21
> **TheFu said:**
> Bit of a rant here.

Bluetooth is a huge security issue.  Got hacked through it last fall in a freshly installed, patched the day prior, Ubuntu system. No network services were running, but BT was installed and enabled by default.

Finally getting around to removing. It has been disabled since I traced the root cause for the hack.

Removed blueman, no issues, but 

```
$ sudo apt purge libbluetooth3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brltty* brltty-x11* kodi* kodi-bin* libbluetooth3* qemu* qemu-kvm*
  qemu-system* qemu-system-arm* qemu-system-mips* qemu-system-misc*
  qemu-system-ppc* qemu-system-sparc* qemu-system-x86*

```
is going to remove my hypervisor and media center software?  Really?  Seems like a huge bug to have either of those tied to a bluetooth library.

You are obviously a power user. Did you already contact the maintainers of "qemu"? You could explain your reasons for not putting the bluetooth library as dependency.

Another thing you could do is create a fake debian package that "provides" the bluetooth library, but actually does nothing to your system. This is a way of tricking the APT package manager. Basically, create an empty package that has a higher version of the bluetooth library than the one provided in the repositories, so it won't try to override it. In this way, you are satisfying the requirements for "qemu" without actually installing the bluetooth libraries. I did this for Latex, which pulls many, many packages, like 1 GB in total. Instead of installing all those dependencies, I created a fake deb with all the dependencies satisfied, and installed that.

```

sudo apt install equivs
equivs-control fake_bluetooth
equivs-build fake_bluetooth
sudo dpkg -i fake_bluetooth_1000-ubuntu1.deb

```

---

### Post by ajgreeny on 2017-07-21
I have no bluetooth hardware anywhere so I also remove all the bluetooth packages that do not take with them packages that I need.

I have also in the past used bum (boot-up-manager) as a simple way to stop the bluetooth service from starting at boot.

---

### Post by yoshii on 2017-07-22
Some great tips in here!  

You can also very carefully submit to apt-get purge "bluetooth*"  (with the asterisk wildcard).  Then see the list that comes up and CANCEL.  
Then cherry pick from the list of which other things to purge out.  

I hate bluetooth also.  I've been hacked thru it also in the past.  I also disable the hardware these days.  It's such a waste.  
It's nice to hear of others who are similar-minded on this topic.

---

### Post by mc4man on 2017-07-22
So your saying you can get hacked when your bluetooth device is not visible?
(- and what vulnerability is there to having a lib installed?

---

### Post by montag dp on 2017-07-24
> **vocx said:**
> Another thing you could do is create a fake debian package that "provides" the bluetooth library, but actually does nothing to your system. This is a way of tricking the APT package manager. Basically, create an empty package that has a higher version of the bluetooth library than the one provided in the repositories, so it won't try to override it. In this way, you are satisfying the requirements for "qemu" without actually installing the bluetooth libraries. I did this for Latex, which pulls many, many packages, like 1 GB in total. Instead of installing all those dependencies, I created a fake deb with all the dependencies satisfied, and installed that.

```

sudo apt install equivs
equivs-control fake_bluetooth
equivs-build fake_bluetooth
sudo dpkg -i fake_bluetooth_1000-ubuntu1.deb

```But I wonder if qemu, kodi, etc. would actually fail to run if he were to remove the bluetooth libraries? In that case, your solution would get him around the package manager problem but still leave him with non-functioning software. The only solution would be to rebuild those packages without linking against libbluetooth.

---

### Post by TheFu on 2017-07-24
> **mc4man said:**
> So your saying you can get hacked when your bluetooth device is not visible?
(- and what vulnerability is there to having a lib installed?

I had a default Ubuntu install. Had not touched anything related to bluetooth.
There are many how-to guides for hacking any bluetooth.  People just don't realize how trivial it is.

What vulnerability just having the library?  When it remains on the system, other programs that use it wouldn't let me know of the dependency during their installation, so I'm less likely to deal with them as harshly as I would if unaware of the use of bluetooth.

Whether any dependent programs fail to run or not would be dependent on how they load the shared library.  If they do it the easy way, automatically at link+run time, then the programs will fail. 
OTOH, if they use dlopen() to dynamically load the library only when needed, there won't be any ill effects.  I've written code like this before.

---

### Post by vocx on 2017-07-24
> **montag dp said:**
> But I wonder if qemu, kodi, etc. would actually fail to run if he were to remove the bluetooth libraries? In that case, your solution would get him around the package manager problem but still leave him with non-functioning software. The only solution would be to rebuild those packages without linking against libbluetooth.
Correct, thus why I mentioned that he should talk to the qemu developers and maintainers and ask them why they would need the bluetooth libraries in the first place.

Also, the way dynamic libraries work, it is possible that a library is missing and nevertheless the program still run. Only when a particular function from that missing library is required, then you may see an error. So, maybe if he is not using the bluetooth functions, he may not need to have the library present at runtime, that was basically my idea with the suggestion of installing the fake package.

---

### Post by poorguy on 2017-07-24
Please Remove.

Thanks

---

