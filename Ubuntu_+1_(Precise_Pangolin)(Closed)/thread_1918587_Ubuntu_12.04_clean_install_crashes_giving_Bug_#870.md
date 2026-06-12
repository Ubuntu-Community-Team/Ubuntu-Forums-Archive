---
title: "Ubuntu 12.04 clean install crashes giving Bug #870643 - Package flashplugin-nonfree"
date: 2012-02-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by alex150668 on 2012-02-01
I am completely new to Linux and Ubuntu.
 
I am trying a clean installation of Ubuntu 12.04 (latest version) by using a .ISO file on Oracle VM Virtualbox 4.1.8 (virtualized environment). I decided to select all the boxes 3rd party vendor included.
 
At the very end of the process, installation crashes resulting in the bug #870643 "package flashplugin-downloader 11.0.1.152ubuntu1 failed to install/upgrade: wget: unable to resolve host address 'archive.canonical.com' - package name: Flashplugin-nonfree -
For details click on the link below:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/870643]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/870643")
 
:confused:
What is the possible cause of the problem?
How can I successfully clean install Ubuntu 12.04 on my Virtualbox?
:confused:
 
Thank you in advance for your help and support... :KS

---

### Post by kazztan0325 on 2012-02-01
Hi alex150668,

I have installed **Ubuntu 12.04 LTS (Precise Pangolin) Daily Build ISO** in Virtualbox 4.1.8 a week ago, and there was no problem.

I would like to suggest you might want to try again with **Ubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO** which will be released on 02 Feb.

---

### Post by uRock on 2012-02-01
> **alex150668 said:**
> I am trying a clean installation of Ubuntu 12.04 (latest version)

Please note that 12.04 is not yet the latest version. It is still being developed and may be full of bugs.

As for your issue, have you tried installing without clicking to install 3rd party packages, so the installer doesn't install the flashplugin-downloader package?

---

### Post by uRock on 2012-02-01
Moved to *"Ubuntu +1 (Precise Pangolin)"*

---

### Post by alex150668 on 2012-02-01
> **kazztan0325 said:**
> Hi alex150668,

I have installed **Ubuntu 12.04 LTS (Precise Pangolin) Daily Build ISO** in Virtualbox 4.1.8 a week ago, and there was no problem.

I would like to suggest you might want to try again with **Ubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO** which will be released on 02 Feb.
Thanks a lot for your advise. I've appreciated it...

---

### Post by alex150668 on 2012-02-01
> **kazztan0325 said:**
> Hi alex150668,

I have installed **Ubuntu 12.04 LTS (Precise Pangolin) Daily Build ISO** in Virtualbox 4.1.8 a week ago, and there was no problem.

I would like to suggest you might want to try again with **Ubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO** which will be released on 02 Feb.
Thanks for your help and support to you as well. I will try to do as you advised me to...

---

### Post by Baldrick_NZ on 2012-02-01
> **alex150668 said:**
> Thanks for your help and support to you as well. I will try to do as you advised me to...

I had the same problem, but got around it by unticking the 'Install 3rd party software' box when first installing Ubuntu.

Once installed, I installed 'Ubuntu restricted extras' from the repo using USC.

No complaints since... :-)

---

### Post by alex150668 on 2012-02-02
> **Baldrick_NZ said:**
> I had the same problem, but got around it by unticking the 'Install 3rd party software' box when first installing Ubuntu.

Once installed, I installed 'Ubuntu restricted extras' from the repo using USC.

No complaints since... :-)
Thanks a lot for your help and support. I assume that what you mean is to avoid 3rd Party software triggering the Flashplayer Plugin (which wouldn't be there in case of a clean installation) I should not install them at the beginning.
Only a question: can I install them anyway, once Ubuntu 12.04 LTS is up and running? And how?
You were mentioning about 'Ubuntu restricted extras' to be installed from the repo using USC.
But I have no idea at all about how can I access all of those things. Could you please explain me how? And how can I install the Flash Player plugin which I will do as a first thing?
Thank you in advance...

---

### Post by bmbaker on 2012-02-02
USC is short for "ubuntu software center" though i prefer cil or synaptic! sudo apt-get install synaptic and then look for the ubuntu restricted extra

---

### Post by MountainX on 2012-02-06
> **kazztan0325 said:**
> Hi alex150668,

I have installed **Ubuntu 12.04 LTS (Precise Pangolin) Daily Build ISO** in Virtualbox 4.1.8 a week ago, and there was no problem.

I would like to suggest you might want to try again with **Ubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO** which will be released on 02 Feb.

FYI, it still happens on  **Ubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO**

---

### Post by kazztan0325 on 2012-02-07
> **MountainX said:**
> FYI, it still happens on  **Ubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO**

Hi MountainX,
I also confirmed it still happens when I installed **Xubuntu 12.04 LTS (Precise Pangolin) Alpha 2 ISO** in VirtualBox a few days ago.
However it had not happened for sure when I installed Ubuntu 12.04 LTS Daily Build ISO, it is very strange..., I don't know why.

---

### Post by cariboo on 2012-02-07
The work around until the bug is fixed, is not to enable third party software installation during the initial installation. Install what you need, flash, extra codecs, etc after the installation has finished. I personally install ubuntu-restricted-extras as part of the packages I need to make Ubuntu usable for me.

---

### Post by jackuk1 on 2012-04-06
I've installed ubuntu 12.04 form cd & usb total clean install, when i install the amd radeon hd 5870 graphics driver it fine.then i restart pc, and it's still working fine..but then i install 52mb of updates restart pc, then a black screen with a white box saying..( your pc is running on low graphics you need to configure this yourself ) i cant restart i have no mouse pointer there is no keys i can press nothing will work..i have to hard boot...i've installed  this distro 5 times now and exactally the same happened all the time..so now i have had to remove it from my pc..HELP! would be appreciated.

---

### Post by Pilot6 on 2012-04-06
That was a mistake to install BETA version, if you can't even solve a simple problem with proprietary driver. Just boot into safe mode and remove fglrx

sudo apt-get purge fglrx*

---

