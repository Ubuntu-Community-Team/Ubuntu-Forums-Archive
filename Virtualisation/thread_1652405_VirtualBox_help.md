---
title: "VirtualBox help"
date: 2010-12-24
forum: Virtualisation
---

### Post by goshxjosh on 2010-12-24
Hello Ubuntu Community,
I am in need of some help, about an hour ago I setup my laptop to run ubuntu as its primary OS. However before I did this I ran a few test with VirtualBox and it worked fine. Now I am getting an error:

"The VirtualBox Linux Kernel driver (vboxdrv) is either not laoded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

When I enter '/etc/init.d/vboxdrv setup' in the command prompt it tells me it is missing DKMS. I just cant get this to work for some reason. If someone could please point me in the right direct direction or help me solve this problem I will be forever grateful. Also I have looked at the VirtualBox manual and im just not sure where to look.

---

### Post by leclerc65 on 2010-12-25
Open Synaptic, search for DKMS, install it.
Then do the second.

---

### Post by goshxjosh on 2010-12-26
I tried that and its not working. I have uninstalled and re installed it several times. I don't understand what I did different with this install.

---

### Post by moma on 2010-12-26
Hello,

Install dependencies.
$ [COLOR="DarkGreen"]sudo aptitude install build-essential linux-headers-generic libqtgui4 python2.6 [/COLOR]

Remove all old VirtualBox installations. List installed packages.
$ [COLOR="DarkGreen"]dpkg -l | grep virtualbox[/COLOR]

And remove the old packages. Study your listing.
$ [COLOR="DarkGreen"]sudo apt-get remove virtualbox-*  [/COLOR]

Browse to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and download the very recent VirtualBox package.

Install the package by clicking on it or run (replace the package name with correct value. it's in the ~/Downloads folder).
$ [COLOR="DarkGreen"]sudo dpkg -i packagename[/COLOR]

Just to make sure all dependencies have been installed.
$ [COLOR="DarkGreen"]sudo aptitude install -f [/COLOR]

Add your username to vboxusers group.
$ [COLOR="DarkGreen"]sudo usermod -a -G vboxusers $USER[/COLOR]

You should now logout/re-login so the group assignment takes effect.

Start the VirtualBox and enjoy.
$ [COLOR="DarkGreen"]VirtualBox[/COLOR]

Documentation
[http://www.virtualbox.org/wiki/Documentation](http://www.virtualbox.org/wiki/Documentation)

---

### Post by goshxjosh on 2010-12-26
Thank you Moma!
Unfortunately I literally just figured it out. My way was slightly more simple but Im sure it would have worked out and just so you can see what I did end up doing ill post it!

running in root:

"apt-get install linux-headers-2.6.35-24-generic"

That will make it so you can run:

"/etc/init.d/vboxdrv setup"

which will fix the link with the DKMS! And VIOLA! it worked.  :D

Thank both of you for the brainstorming and the help.

---

### Post by penguin_crayons on 2010-12-31
Hi,

I am having a similar issue with Virtual Box install.  I used moma's post to resolve most of the dependency issues, but now I am getting this error during the installation:

Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)

and the only libqtcore4 I can find in the package manager is 4.6

Thanks

---

### Post by stmiller on 2010-12-31
> **penguin_crayons said:**
> Hi,

I am having a similar issue with Virtual Box install.  I used moma's post to resolve most of the dependency issues, but now I am getting this error during the installation:

Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)

and the only libqtcore4 I can find in the package manager is 4.6

Thanks

libqtcore 4.6 is in Ubuntu 10.04. What version of Ubuntu are you using?

---

