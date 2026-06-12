---
title: "Anyone got this to work? ubuntu-cleaner on Ubuntu 22.10 Kinetic Kudu"
date: 2022-09-05
forum: Ubuntu Development Version
---

### Post by KingHanco on 2022-09-05
I got it to run by using the command on the source. ./ubuntu-cleaner

But it get stuck on the cleaning. There is noway to install it.

[https://github.com/gerardpuig/ubuntu-cleaner](https://github.com/gerardpuig/ubuntu-cleaner)

Is there anything better than this?

BleachBit doesn't have these options. I use both on the 22.04.1.

---

### Post by Impavidus on 2022-09-06
I don't use any cleaning tools. It doesn't look like Ubuntu needs them and it's easy to clean too much, in particular if the cleaning tool isn't perfectly made for exactly your version of Ubuntu. Ubuntu 22.10 is still in development, so it's still a moving target, so I'm not surprised if this cleaning tool has some difficulties with it.

---

### Post by coffeecat on 2022-09-06
Ubuntu 22.10 not yet released.

*Thread moved to **Ubuntu Development Version**.*

---

### Post by mIk3_08 on 2022-09-06
> **KingHanco said:**
> I got it to run by using the command on the source. ./ubuntu-cleaner

But it get stuck on the cleaning. There is noway to install it.

[https://github.com/gerardpuig/ubuntu-cleaner](https://github.com/gerardpuig/ubuntu-cleaner)

Is there anything better than this?

BleachBit doesn't have these options. I use both on the 22.04.1.
I prefer cleaning using the regular commands in terminal. Its is way more safer than using some applications. Regards and cheers.

---

### Post by MAFoElffen on 2022-09-06
To install and use:
[https://www.imaginelinux.com/install-and-use-ubuntu-cleaner/](https://www.imaginelinux.com/install-and-use-ubuntu-cleaner/)

But there are no guarantees. The last maintained (Git Commit) in that Git was 2 years ago, and last written for Gtk 3.0. Current is Gtk4.x. User's seem to have problems with Current (Ubuntu  22.04) with this app.

I think "mlk3_08" and I answered another thread on this same thing, where we both just use the terminal commands themselves.

I could certainly write a script of the commands we both use, and put the script in one of my server maintenance gits, or in the Git for my Ama-Gi Project... I am the author of the UbuntuForums 'system-info' script in my Signature line...

---

### Post by KingHanco on 2022-09-07
I can't tell these are working. Doesn't show what been removed, sudo apt-get clean -y && sudo apt-get autoclean -y && sudo apt-get autoremove --purge -y

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Only showing these.

On the Bleachbit (as root) showing the Clean deleted some files. Which is odd because the commands should've worked. Very confused.

Would be nice if Ubuntu have a cleaning program added. Have it set to full cleaning. Click to clean. Show what been removed at the end.

============================================================================================ Don't use this. See why.

sudo add-apt-repository ppa:gerardpuig/ppa

Repository: 'deb [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/) kinetic main'
Description:
Official Ubuntu Cleaner stable repository
More info: [https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa](https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa)
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-kinetic.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-kinetic.list
Adding key to /etc/apt/trusted.gpg.d/gerardpuig-ubuntu-ppa.gpg with fingerprint E2CBBCC339FED83BCAE8E4B55F841B74A892A73C
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) kinetic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) kinetic-security InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) kinetic-updates InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) kinetic-backports InRelease
Ign:5 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) kinetic InRelease
Err:6 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) kinetic Release
  404  Not Found [IP: 2620:2d:4000:1::3e 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

============================================================================================ Fix below.

On the Software & Updates > Other Software just add deb [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy main 

Remove the [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/) Not needed anyway.

Remove Gerard Puig from Authentication Not needed.

Now it can install.

Ignore this error below.
Hit:5 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease   
Err:5 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5F841B74A892A73C

After it is installed then you can remove [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy main (Reason: The program isn't on the server 22.10 yet. This server shouldn't be added on the 22.10 anyway.)

---

