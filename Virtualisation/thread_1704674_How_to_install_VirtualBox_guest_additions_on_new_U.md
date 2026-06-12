---
title: "How to install VirtualBox guest additions on new Ubuntu hosts"
date: 2011-03-11
forum: Virtualisation
---

### Post by travlemon on 2011-03-11
Hello,

Forgive me if this has already been covered somewhere in the forums, but I had some trouble with this issue for a while and finally found a solution.

_**Introduction:**_ I use Virtual Box a lot, to test out new and different Linux distributions.  Lately, when hosting the newer version of Ubuntu and its derivatives, I just kept having issues when trying to run the installation for the guest additions.

Here's how it went, when installing guest additions on an older Ubuntu (or derivative) host.. I run the installation file (usually VBoxLinuxAdditions-x86.run) with root privileges.  The installation then runs, I may have to say "yes" to a prompt or two, and it finishes.  I reboot the virtual machine, and guest additions work!  

New versions of Ubuntu and its derivatives just don't seem to be that easy.  However, I finally realized what does need to be done to make it work, and it's not much more difficult, it's really just a little bit different work flow. 

_**Issues when installing:**_ When trying to install guest additions on newer Ubuntu hosts, you may receive errors during the installation, the installation doesn't complete, or the screen may reset and give you strange colors and a an extremely low and awkward resolution.  This happens if you're presumably using the work flow of simply running the guest additions installation from the desktop.

_**The way I got it to work:**_ 
First, boot up your virtual machine with Ubuntu installed on it. This seems strange to me, but you must install VirtualBox on your Ubuntu guest machine.  The regular, non-OSE version from the repository should do just fine.  Open VirtualBox one time so that it creates a configuration file.  Then, just close it.

Next, run 
```
sudo /etc/init.d/vboxdrv setup
```If you get an error message about DKMS when trying to run the above command, simply install the package DKMS from Synaptic.  You can also run ```
sudo apt-get install dkms
``` to install it.

Once the setup has completed, we're now ready to install the guest additions.  In VirtualBox, click Devices>Install guest additions.  This mounts a virtual CD-ROM drive to the guest OS, and contains the guest additions drivers on it.  

Now, stop your desktop completely.  Typically, the command would be:
LXDE desktop: ```
sudo /etc/init.d/lxdm stop
```Gnome Desktop:  ```
sudo /etc/init.d/gdm stop
```KDE Desktop:  ```
sudo /etc/init.d/kdm stop
```This brings you to a command line.  Sign in as root, and navigate to the guest additions CD-ROM drive, as a folder should be mounted for it in /media (from when we clicked "Install guest additions" before killing the desktop).  Then, try running the guest additions installation.  The command should be:

```
sudo sh VBoxLinuxAdditions-x86.run
```With any luck, it should complete just fine! Then, restart your guest OS completely, and you should be greeted with mouse integration and auto resizing resolution! I still do have trouble with this in LXDE, specifically, Lubuntu.

Please remember a few things about these instructions, I'm just a simple Linux user, not an expert.  So, please don't criticize whatever technical skills this post may be lacking.  I'm just trying to give some tips for anyone out there who may be having trouble with the guest additions on newer Ubuntu hosts.

Hope this helps, and feel free to make corrections to my work flow!

EDIT:  If you're still having trouble installing the drivers by running the VBoxLinuxAdditions-x86.run file, try running:

```
sudo apt-get install virtualbox-ose-guest-x11
```

This worked perfectly for me.  You may even be able to just install that package right from the get go.  Here is the link to the source where I found that tip:  [http://lockergnome.net/questions/88857/install-virtualbox-guest-additions-in-ubuntu-10-10](http://lockergnome.net/questions/88857/install-virtualbox-guest-additions-in-ubuntu-10-10)

---

### Post by CharlesA on 2011-03-11
Nice write up. :)

One thing, you don't need to login as root, if you are using sudo. Also note that the root account is disabled by default on Ubuntu.

---

### Post by travlemon on 2011-03-12
> **CharlesA said:**
> Nice write up. :)

One thing, you don't need to login as root, if you are using sudo. Also note that the root account is disabled by default on Ubuntu.

Thanks!  I had some problems in the past with installing them even with sudo.  I cheat on my Ubuntu systems and use "sudo passwd" to set a custom password for root.   Is that bad?? haha.

---

### Post by CharlesA on 2011-03-12
Not bad as long as you know the risks. :)

---

### Post by travlemon on 2011-03-12
> **CharlesA said:**
> Not bad as long as you know the risks. :)

Of course!  Anything really risky, I test out in a vbox first! I usually don't tinker too much though

---

