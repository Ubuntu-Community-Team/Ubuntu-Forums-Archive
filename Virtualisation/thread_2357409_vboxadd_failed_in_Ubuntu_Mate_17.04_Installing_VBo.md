---
title: "vboxadd failed in Ubuntu Mate 17.04 Installing VBox Guest additions."
date: 2017-04-01
forum: Virtualisation
---

### Post by nettobr on 2017-04-01
Hi all,

I'm trying Ubuntu Mate 17.04 Beta 2 Guest Under Ubuntu 14.04 in my Dell I5 Note.

I'm using VBox 5.1.6 and when installing VBox Guest additions appears this error:

"failed to set up service vboxadd, please check log file"

After a fresh install I think I've made all prereqs:

sudo apt-get update
                   upgrade
                   dist-upgrade
sudo apt-get install build-essential
                   make
                   gcc
                   kernel-headers

and after running ./VBoxLinuxAdditions.run  I get the error above. 

Have any one successfully installed Guest Additions.

Cheers,

NettoBr
from Brazil

---

### Post by Paddy Landau on 2017-04-03
Two things occur to me, although I don't know if they'll help.

First, the Guest Additions module needs dkms:
```
sudo apt install dkms
```

Second, it might help to install the latest version of VirtualBox. I always do, and it seems to be stable. Do as follows.

[LIST=1]
[*]Uninstall VirtualBox:```
sudo apt remove 'virtualbox*'
```
[*]Go to the [download instructions for Linux]("https://www.virtualbox.org/wiki/Linux_Downloads"). *Don't* download the package. Instead…
[*]Scroll down to "Debian-based Linux distributions" and follow the instructions. Or just do the following, which is the easy way.```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
sudo add-apt-repository 'deb http://download.virtualbox.org/virtualbox/debian zesty contrib'
sudo apt update
sudo apt install virtualbox-5.1
```
[/LIST]
Thereafter, VirtualBox will automatically update soon after each release.

Once you have done this, try again.

Because you are using a development version, VB isn't officially supported on your box.

---

### Post by nettobr on 2017-04-06
Hi Paddy,

Thanks a lot for your answer. Updating Vbox made a kind of diference.

In meanwhile, Ive changed to Ubuntu Gnome 17.04 B2.

After Updating Vbox I got "successfuly" installed Vbox GA.

But after reboot the initialization freezes in initial terminal screen saying 
.........."A start job is running for Hold for boot processes to finish up"

Well, Im almost giving up testing B2.

Thanks,

Nettobr

---

### Post by Morbius1 on 2017-04-06
The only way I could install the guest additions in a Xubuntu 17.04 Beta guest was to install VBox 5.1.18.

---

### Post by Paddy Landau on 2017-04-06
Sorry. As I say, VB doesn't yet support 17.04, so it might be that the Guest Additions mess it up.

---

### Post by Morbius1 on 2017-04-06
Since there is a VBox 5.1.18 download for Ubuntu 17.04 I assume it will support 17.04 as a guest in the 5.1.18 download for an Ubuntu 14.04 host.

It does for Xubuntu. There may be something peculiar about MATE as a guest.

---

### Post by Paddy Landau on 2017-04-06
> **Morbius1 said:**
> Since there is a VBox 5.1.18 download for Ubuntu 17.04 I assume it will support 17.04 as a guest in the 5.1.18 download for an Ubuntu 14.04 host.

It does for Xubuntu. There may be something peculiar about MATE as a guest.
Yes, that's also possible.

---

### Post by Habitual on 2017-04-06
dkms is no longer required for the Virtualbox5 series.

[https://forums.virtualbox.org/viewtopic.php?f=15&t=77998](https://forums.virtualbox.org/viewtopic.php?f=15&t=77998)

---

### Post by Paddy Landau on 2017-04-06
> **Habitual said:**
> dkms is no longer required for the Virtualbox5 series.

[https://forums.virtualbox.org/viewtopic.php?f=15&t=77998](https://forums.virtualbox.org/viewtopic.php?f=15&t=77998)
That's useful to know, thank you.

---

### Post by lammert-nijhof on 2017-04-07
There is a more simple method to get Virtualbox installed: Download the deb file from the Virtualbox website using the browser and do: sudo dpkg -i <downloaded deb-file>. If you get errors about missing dependencies "apt-get install" those packages and dpkg again. Your Virtualbox will not be updated automatically, but Virtualbox will inform you about new versions and that has also two advantages:
- You do not have to update the guest additions on all virtual machines, in my case around 20. You only do it, when the release notes come up with something interesting for you. 
- Any patch remains valid and is not destroyed automatically. I downloaded a patched module from the Internet for flickering of the video in my guests. As long as that problem is not solved, I did not change my video card or a new patched module becomes available, I have to stay on 5.1.18.

I installed quest additions without problems in the Ubuntu 17.04 beta. I have downloaded Ubuntu Gnome Beta and the Ubuntu Mate Beta and in the weekend I will try those two distros and report back on it.

---

### Post by wildmanne39 on 2017-04-07
I wonder what is used to rebuild the modules now instead of DKMS?

---

### Post by &amp;KyT$0P# on 2017-04-07
> **wildmanne39 said:**
> I wonder what is used to rebuild the modules now instead of DKMS?
Guest Additions now installs a script [FONT=Courier New]/etc/kernel/postinst.d/vboxadd[/FONT] which, like the other scripts in that directory, gets run at every kernel upgrade.  That script tells Guest Additions to rebuild the kernel modules.

---

### Post by lammert-nijhof on 2017-04-07
OK I had the same problem, but the vboxadd log showed that the program "make" was missing. To avoid this type of problems in the future, I installed the compilers, linkers etc.
> sudo apt-get install build-essential
After this the Guest Additions installed without problems.

---

### Post by wildmanne39 on 2017-04-07
> **halogen2 said:**
> Guest Additions now installs a script [FONT=Courier New]/etc/kernel/postinst.d/vboxadd[/FONT] which, like the other scripts in that directory, gets run at every kernel upgrade.  That script tells Guest Additions to rebuild the kernel modules.
Thanks, that is awesome because DKMS has not been working for me for a long time and it is harder to install with secure boot.

---

### Post by nettobr on 2017-04-16
Hi all,

Now I am trying Ubuntu Gnome 17.04 **Final** and problems are still there after installing VBox GA.

My Host is a Dell Note I5 running VBox 5.1.18 

Host Ubuntu 14.04 and Windows 10 (both shows same issue)

After a reboot of a fresh Install of Gnome 17.04 I install VBox GA, and after a new reboot  I get the boot screen (attached).

And gnome stalls for approximately half an hour and shows an abnormal termination screen for "plymouth".

Kubuntu 17.04 also have problems. After installing VBox GA and rebooting If I change window size, I get a black window for ever.

Oh, my God...  Is Ubuntu 17.04 compatible with VBox???

Thanks,

NettoBr

---

### Post by Paddy Landau on 2017-04-17
> **nettobr said:**
> Is Ubuntu 17.04 compatible with VBox?
I have been testing.

**Ubuntu 17.04**: Works perfectly.

**Ubuntu Gnome 17.04**: Booting fails as soon as Guest Additions are installed, whether using the default way ("Insert Guest Additions CD image") or via the package manager ([FONT=lucida console]virtualbox-guest-utils[/FONT] and dependencies). I have tried this both with EFI and without EFI.

As Ubuntu Gnome is to be the new default for Ubuntu (replacing Unity), this should be [reported as a bug]("https://help.ubuntu.com/community/ReportingBugs") otherwise it probably won't be fixed. When you have reported the bug, please post the link here so that I can star it and confirm it.

As a workaround, of course, simply don't install Guest Additions until this has been solved.

---

### Post by nettobr on 2017-04-17
Hi Paddy,

> **Paddy Landau said:**
> I have been testing.

**Ubuntu 17.04**: Works perfectly.

**Ubuntu Gnome 17.04**: Booting fails as soon as Guest Additions are installed, whether using the default way ("Insert Guest Additions CD image") or via the package manager ([FONT=lucida console]virtualbox-guest-utils[/FONT] and dependencies). I have tried this both with EFI and without EFI.

Vbox GA installed using default way (CD Image) without EFI.

I'll try to report the bug.

Thanks,

NettoBr

---

### Post by Paddy Landau on 2017-04-17
> **nettobr said:**
> I'll try to report the bug.
If you don't manage, let me know and I'll do it.

---

### Post by YordanGeorgiev on 2017-09-07
Enable fully read,write access to a shared folder on the host from the guest

This is the most error prone section, as your mileage will vary.
This step will enable you to access a certain root dir on your Windows host machine from the Linux guest terminal.
In this example the name of the share from the OVB perspective will be vshare ( which is the default ) , the full dir path to the Windows OS ( the host OS ) will be "C:\var\" and the full file path to access it from the guest vm will be "/vagrant", and finally the name of the user to enable the full rea/write access will be "you".
# how-to add a shared folder on the host
VBoxManage sharedfolder add "host-name" -name "vshare" -hostpath "C:\var" -automount

1. Install the Guest Additions prerequisites
Install the Guest Additions prerequisites by issuing the following command:
sudo apt-get install -y build-essential make gcc  linux-headers-$(uname -r) linux-headers-generic make linux-source  linux-generic linux-signed-generic
2. Install the Guest Additions
Do not use the .iso file to download and the installer from there - it will simply not work
sudo apt-get install virtualbox-guest-dkms 3. Change your for the share dir to be automounted on vm boot
Change your for the share dir to be automounted on vm boot by addding the folowing lines to the end of your fstab file
#/media/sf_vshare /vagrant bind defaults,bind 0 0
/media/sf_vshare /vagrant vboxsf bind,uid=10001,rw,umask=0000 0 0

# eof file: /etc/fstab 4. add yourself to the vboxsf group
You need to add yourself to the vboxsf group in order to be able to edit as non-root from your vm the files on your host machine.
# run the fooll
sudo mount -a

sudo usermod -G vboxsf -a you 5. reboot and verify
Reboot the vm and login via ssh to verify the file sharing.
# ssh to the vm
ssh you@host-name

# check as yourself that you have 
find /vagrant

---

