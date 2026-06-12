---
title: "Virtual Box only on 64bit ubuntu?"
date: 2018-12-08
forum: Virtualisation
---

### Post by iamtheeggman2 on 2018-12-08
Hi,

I wanted to install virtual box but I think as I understand their sife [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) that I cant run it o my 686 install of ubuntu, I chose to avoid the 64 bit version because in the past I had issues with flash or something, anyway, this is surprising then, though curiously virtual box appeared as avaiable in the software repository but upon trying to install it I got an error message saying it was unavailable. Do I really have to install ubuntu 64 then to use this? Thanks in advance.

---

### Post by howefield on 2018-12-08
What version of Ubuntu are you using ?

```
cat /etc/os-release
```
```
uname -a
```

---

### Post by iamtheeggman2 on 2018-12-08
18.04 but pretty sure i got the 686 one

---

### Post by howefield on 2018-12-08
What is the output from the above 2 terminal commands ?

I don't think a [32 bit 18.04 ]("http://releases.ubuntu.com/bionic/")was released.

---

### Post by iamtheeggman2 on 2018-12-08
cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic


4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:43:58 UTC 2018 i686 athlon i686 GNU/Linux



defo 686!

---

### Post by springshades on 2018-12-10
I think you're stuck in a weird software version. If you look on the Ubuntu 18.04 version download page (even the alternative links), they only have a 64 bit version. So my guess is that you were only able to get a 32 bit version by installing an older version and then updating to 18.04.

The problem with that is that on the Virtual Box download page, you'll see they are still making 32 bit versions for Linux. But since there isn't apparently an official 64 bit 18.04 release, Virtual Box is only releasing a 64 bit for that version. 16.04 is still getting 32 bit versions. So are the most recent versions of Debian and Fedora. There is a decent chance that in the future all the software companies will stop making 32 bit versions for Ubuntu since there isn't an official release (i.e. drivers and third party apps).

---

### Post by iamtheeggman2 on 2018-12-23
Well I dont imagine how I managed that then, is it possible to upgrade this to a 64 bit version without much hastle?

---

### Post by deadflowr on 2018-12-23
> **iamtheeggman2 said:**
> Well I dont imagine how I managed that then, is it possible to upgrade this to a 64 bit version without much hastle?

The least hassle is to backup what you need and reinstall a fresh clean version.

There are other methods around (Do a web search for switching Ubuntu from 32 to 64 will give a number of results) that can do it without a reinstall, but those too almost always posit backing up your data first, 
so if you're going to backup your data, which you should be doing regularly anyway (right?), then might as well reinstall clean and not deal with the fallout of what can happen if the outlier methods to switch archs goes kaput.

---

### Post by iamtheeggman2 on 2019-06-01
Hi,

So I just installed virtual box o n my ubuntu i installed recently, 64bit, however i wonder if i follow these instructions would it installed guest additions or might these not work a they refer to linux mint?

[https://www.tecmint.com/install-virtualbox-guest-additions-in-ubuntu/](https://www.tecmint.com/install-virtualbox-guest-additions-in-ubuntu/)

---

### Post by kpatz on 2019-06-01
Virtualbox Guest additions are installed on the guest OS (running in the VM), not the host OS.

But Mint is Ubuntu based, so installing Virtualbox (and guest additions) on either should be similar if not the same.

---

### Post by iamtheeggman2 on 2019-06-01
oh,

Does this mean the guest OS must have internet access then?

i found the iso but when i go to attach it as an optical drive it says:

Failed to open the disk image file /home/home/Downloads/VBoxGuestAdditions_2.2.0.iso.

Could not get the storage format of the medium '/home/home/Downloads/VBoxGuestAdditions_2.2.0.iso' (VERR_NOT_SUPPORTED).

Result Code: VBOX_E_IPRT_ERROR (0x80BB0005)
Component: MediumWrap
Interface: IMedium {4afe423b-43e0-e9d0-82e8-ceb307940dda}
Callee: IVirtualBox {9570b9d5-f1a1-448a-10c5-e12f5285adad}
Callee RC: VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)

---

### Post by kpatz on 2019-06-01
Your path shows /home/home... is this correct?  Is your username "home" on your host OS?

The correct Guest Additions ISO should have been included with Virtualbox.

On the guest's menu bar, click Devices, then select Insert Guest Additions CD Image...  This will automatically attach the ISO, and the guest OS should mount it automatically and prompt you through the installation.

Also, I think based on your error message, you tried to attach the ISO as a hard disk image, not as an optical drive.

You don't need internet access on the guest OS to install the guest additions, but it's good to have internet to download other updates and files into your VM.  Virtualbox gives you a NAT network automatically so your VM gets its own IP behind a virtual router, but you can change this in the guest settings.

---

### Post by iamtheeggman2 on 2019-06-01
i loaded up the machine, found the devices menu, chose for the optical drive, ticked the box for additions and it came up with the same message

Failed to open the disk image file /home/home/Downloads/VBoxGuestAdditions_2.2.0.iso.

Could not get the storage format of the medium '/home/home/Downloads/VBoxGuestAdditions_2.2.0.iso' (VERR_NOT_SUPPORTED).

Result Code: VBOX_E_IPRT_ERROR (0x80BB0005)
Component: MediumWrap
Interface: IMedium {4afe423b-43e0-e9d0-82e8-ceb307940dda}
Callee: IVirtualBox {9570b9d5-f1a1-448a-10c5-e12f5285adad}
Callee RC: VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)

---

### Post by kpatz on 2019-06-01
2.2.0 is a really old version.  If you installed Virtualbox from the repositories, the guest additions iso should be in /usr/share/virtualbox/VBoxGuestAdditions.iso.  The version of the guest additions should match the version of VirtualBox you're running.

What version of Virtualbox *are* you running?  (Help->About from the Virtualbox manager, or **VBoxManage --version** from a shell prompt).

Try attaching that iso, or downloading it from [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/) -- navigate to the version of VirtualBox you're on (latest 5.2 version is 5.2.30).

---

### Post by cruzer001 on 2019-06-01
VBoxGuestAdditions_2.2.0.iso ??

Where is this coming from?

[https://packages.ubuntu.com/bionic/virtualbox-guest-additions-iso](https://packages.ubuntu.com/bionic/virtualbox-guest-additions-iso)

Edit
never mind kpatz is on it

---

### Post by iamtheeggman2 on 2019-06-01
I cant copy and paste stuff into either, and yes i did check the feature was on bidirectional.

---

### Post by kpatz on 2019-06-01
Copy & paste between home & guest won't work until your guest additions are installed and the same version as your Virtualbox.

---

### Post by iamtheeggman2 on 2019-06-01
> **kpatz said:**
> 2.2.0 is a really old version.  If you installed Virtualbox from the repositories, the guest additions iso should be in /usr/share/virtualbox/VBoxGuestAdditions.iso.  The version of the guest additions should match the version of VirtualBox you're running.

What version of Virtualbox *are* you running?  (Help->About from the Virtualbox manager, or **VBoxManage --version** from a shell prompt).

Try attaching that iso, or downloading it from [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/) -- navigate to the version of VirtualBox you're on (latest 5.2 version is 5.2.30).


no guest addition in the virtual box folder.

it came from the ubuntu installer.

however in trying to access the newer iso i now get another problem lol


 Unable to insert the virtual optical disk /home/home/Downloads/VBoxGuestAdditions_5.2.18.iso into the machine xyz

 Would you like to try to force insertion of this disk?


 Could not mount the media/drive '/home/home/Downloads/VBoxGuestAdditions_5.2.18.iso' (VERR_PDM_MEDIA_LOCKED).
 

 [TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] [FONT=monospace]NS_ERROR_FAILURE (0x80004005)[/FONT]
[/TD]
[/TR]
 [TR]
 [TD] Component: 
[/TD]
 [TD] ConsoleWrap
[/TD]
[/TR]
 [TR]
 [TD] Interface: 
[/TD]
 [TD] IConsole {872da645-4a9b-1727-bee2-5585105b9eed}
[/TD]
[/TR]
 [TR]
 [TD] Callee: 
[/TD]
 [TD] IMachine {85cd948e-a71f-4289-281e-0ca7ad48cd89}
[/TD]
[/TR]
[/TABLE]

---

### Post by SeijiSensei on 2019-06-01
I suggest starting over and following the method described at the VirtualBox site to use the Oracle repositories. I get prompted to install the extensions automatically using that method.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

This will give you the most recent version of VirtualBox and keep it updated alongside all the other software on your system.

I find I need to use
```
deb **[arch=amd64]** https://download.virtualbox.org/virtualbox/debian <mydist> contrib
```
to avoid getting warnings about the 32-bit version.

---

### Post by cruzer001 on 2019-06-01
> it came from the ubuntu installer.
Please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by iamtheeggman2 on 2019-06-01
```
home@home-System-Product-Name:~$ cat /etc/apt/sources.list
# deb cdrom:[Lubuntu 18.04 LTS _Bionic Beaver_ - Release i386 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu bionic main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu bionic-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu bionic universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic universe
deb http://archive.ubuntu.com/ubuntu bionic-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu bionic multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://archive.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://archive.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://archive.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

---

### Post by cruzer001 on 2019-06-01
Ok, its all good.

I would go with SeijiSensei suggestion.  vBox 6.0 has been released.

How much ram do you have?
```

free -g
```

---

### Post by iamtheeggman2 on 2019-06-01
also id like to utilize more of my cpu, its currently set to 1 but it said you need hardware stuff installed first, is that easy to install?

12gb ram - i let vobx use 3gb for the guest box

---

### Post by cruzer001 on 2019-06-01
There is a fairly heavy learning curve to vBox, but IMO its worth it.

One core will be slow, two core for the guest is far better for a GUI.

---

### Post by iamtheeggman2 on 2019-06-01
wiow i tried one mor time and it work! no idea why.

i still need o get more cpu usage though.

---

### Post by cruzer001 on 2019-06-01
vBox manager will allow you to up it to 2core, the guest must be shut down first.

---

### Post by cruzer001 on 2019-06-01
Been here yet?

[https://www.virtualbox.org/manual/ch01.html#gui-createvm](https://www.virtualbox.org/manual/ch01.html#gui-createvm)

---

### Post by TheFu on 2019-06-03
If the host OS is 32-bit, then virtualbox will only use software-based virtualization and it is limited to 4G RAM for the entire guest and all support RAM use like video RAM.
Hardware acceleration will not work without a 64-bit host OS.

IME, virtualbox is the slowest of all the hypervisors.  I've never had issues with allocating just 1 vCPU to a VM, unless the VM was running lots and lots of processes.  My everyday desktop runs inside a VM with 1 vCPU and 3G of RAM.  If you run a heavy desktop or Zimbra server, then a case that 2 vCPUs could be made.  I have webservers running in separate VMs with 10+ virtual domains. These all share 1 vCPU and 1G of RAM and less than 5G of storage total.

Still relevant virtualbox tuning article: [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

BTW, flash is dead.

---

### Post by cruzer001 on 2019-06-03
Yes, vBox can suck up some resources. Gaming on two core can hit 100%, stay at times at 80 to 90%.  Ended up giving 4core/4G ram to that VM.  And this is not high level gaming, VB is just not designed for this.

Same with ram, 2G minimum (3G can provide a better experience) and storage I usually set to 12G.

---

### Post by TheFu on 2019-06-03
For gaming, either VT-g (intel iGPUs) or VGA passthru are really the only options.  Without access to a real GPU, then the CPU has to handle all that rendering.  I support virtualbox is the best option for gaming in a VM without using passthru or VT-g.  I haven't tried SPICE on KVM for gaming. My KVM servers aren't for gaming.
Plus, the guestOS matters greatly.  A Linux VM is much, much, lighter than Windows.  Windows VMs tend to use 30% of the CPU inside the guest _just because_. I've never figured out why this is and it doesn't happen all the time, but once it does happen, reasons unknown, the Windows VM will keep sucking more and more CPU.

I have lots of VMs that have less than 1G of RAM allocated. These aren't desktops.  Desktop virtualization is a 5% thing for me - 5% are desktops, 95% are servers - no GUI.

In the link above, I do mention switching from virtualbox to KVM some years ago. Can't imagine going back.  virt-manager makes using KVM pretty much just like virtualbox, but with much more flexibility.

---

