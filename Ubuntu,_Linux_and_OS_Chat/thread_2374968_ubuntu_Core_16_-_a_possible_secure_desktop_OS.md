---
title: "ubuntu Core 16 - a possible secure desktop OS?"
date: 2017-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2017-10-20
I am posting in response to a request from Chanath which is in a closed thread in the development version section.

Ubuntu Core 16 is a command line snappy based OS built on 16.04 code. It can be downloaded from here

[https://developer.ubuntu.com/core/get-started/kvm](https://developer.ubuntu.com/core/get-started/kvm)

I use Disks>Restore image to put the ubuntu-core-16-amd64.img.xz image onto a USB memory stick or a hard drive. The process will take up all the space on the hard drive. Grub on a standard Ubuntu install will not detect Ubuntu Core. So, it has to be loaded by selecting the hard drive in the BIOS utility. I do not have UEFI. 

The drive will have GPT partitioning with a 1.0MB BIOS boot partition; a 52 MB EFI system partition and a Ext4 partition called Writable. On first boot the Writable partition will be expanded to take up all available free space on the drive.

Again, on first boot the system will load with the usual Linux messages and then all that clears and we press enter to run a set up routine where we setup an Internet connection. We need a Single Sign On account on Launchpad and a SSH key uploaded to our account.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Once we have created a SSH key we open our Launchpad account and use it upload the SSH key onto our Launchpad account.

The Ubuntu Core setup process will require us to put in our Launchpad user name and email address combination. The set up process then goes to our Launchpad account and use our SSH key to create a ubuntu-core-16 user. We will be told that we can log in to ubuntu core using 

```
<launchpad user name>@<Ip address>
```

And away we go. Or, not, as is in my case. I suspect that reinstalling ubuntu-core-16 does not wipe user data out of the Writable partition. I have yet to test this.

This web site will reveal what snap apps are available.

[https://uappexplorer.com/snaps](https://uappexplorer.com/snaps)

I have been able to shrink the Writable partition  and create new partitions in which to install standard versions of Ubuntu & its flavours. Make sure that Grub is not installed in the MBR of the hard drive that ubuntu-core-16 is installed to. Otherwise you will lose the ability to boot ubuntu-core-16.

As I have yet to actually login to ubuntu-core I have not been able to test updating and the installation of snaps. I am interested in seeing if GUI snap apps will work on ubuntu-core.


Regards

---

### Post by ventrical on 2017-10-21
This link: [https://developer.ubuntu.com/core/get-started/kvm](https://developer.ubuntu.com/core/get-started/kvm)  is providing a redundant download command.

It is reporting:

Download 'core' and uncompress with he following commands:

```

wget http://cdimage.ubuntu.com/ubuntu-core/16/stable/current/ubuntu-core-16-amd64.img.xz
unxz ubuntu-core-16-amd64.img.xz


```

which does the same thing and gives you two images- xz and xz1.

what a waste  of bandwidth..

---

### Post by ventrical on 2017-10-21
Loads up well,. No option to install to hdd. locks up on USB  with blinking cursor under: Personalize your account at [https://login.ubuntu.com](https://login.ubuntu.com)

Regards..

edit:

When going to the above link it wants to override your current SSO. This is a known bug atm I think. So if you add stuff to your SSo it may bork your other access to SSO sign ons elsewhere. This is an old bug back from when we were testing snappy in the early days.. uh .. the old unity8.img thingy.

---

