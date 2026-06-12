---
title: "apt-get update vs update manager and packages kept back"
date: 2009-06-26
forum: Server Platforms
---

### Post by Pro_D on 2009-06-26
Hello,

I have an Ubuntu 8.04 LTS server that I have been running for some time now (largely since 8.04 released).  It has the Desktop installed on top for programs that are graphical and that I need to be persistent across connections (vnc).  It recently had a hard drive failure (primary system) and I restored from backup and altered the grub/fstab files to get things going on the new drive (uuid stuff).  btw: LOVING this thing right now, also new motherboard as old one's chipset fried about the same time, cheap hardware, now not so much.

I have noticed that when I do 'apt-get update' followed by 'apt-get upgrade' I have several packages that are held back, excerpt:
The following packages have been kept back:
  linux-headers-generic linux-image-server linux-server


I didn't explore this much until recently when I finally got around to really using the Desktop portion and noticed the update manager listing those packages and more as available for update.

Is there a reason for them to be held back?  Should I opt out of installing those packages?  I tend to prefer to use the command line (putty or ssh depending on the machine I am at) on the server so what would I use to make sure those packages get installed via apt-get?

---

### Post by Cheesemill on 2009-06-26
If you do a
```
 
apt-get dist-upgrade

```it will update the held back packages as well. Or you can do
```
 
apt-get install [packagename1] [packagename2] etc...

```for the packages in question.
 
In my experience it's usually only kernel packages that get held.

---

### Post by Thingymebob on 2009-06-26
The reason those packages are kept back is because they depend  on extra packages not already installed. apt-get upgrade doesn't pull in  those extra packages, while apt-get dist-upgrade does.

---

### Post by Pro_D on 2009-06-26
mkay.  I think I see.

I long thought dist-upgrade actually caused you to upgrade to the latest version (ie 8.04 to 8.10 or 9.04) which is something I did NOT want to do.

Thanks much!

---

### Post by Luke has no name on 2009-06-26
> **Pro_D said:**
> mkay.  I think I see.

I long thought dist-upgrade actually caused you to upgrade to the latest version (ie 8.04 to 8.10 or 9.04) which is something I did NOT want to do.

Thanks much!

That's what I thought.

---

### Post by Thingymebob on 2009-06-26
```
man apt-get
```> 
upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.
> 
dist-upgrade 
           in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.


---

### Post by mcduck on 2009-06-26
> **Pro_D said:**
> mkay.  I think I see.

I long thought dist-upgrade actually caused you to upgrade to the latest version (ie 8.04 to 8.10 or 9.04) which is something I did NOT want to do.

Thanks much!

No, it doesn't. "apt-get upgrade" can upgrade packages and add new ones if required. "apt-get dist-upgrade" does the same, but can also remove packages if required.

And to compare them with the GUI tools, Update manager works like "apt-get upgrade", while synaptic handles upgrades like "apt-get dist-upgrade" does.

Removing packages can be required for upgrade in certain situations. For example if current version of some program has two packages, and the new version of the program has combined them into one package the now-useless extra package has to be removed during the upgrade. Trying to do the upgrade with Update manager or "apt-get upgrade" would not be able to do this and instead report the update as being kept back.

(to upgrade to new release with apt-get you'd have to first edit your sources.list to use repositories for the new release, and *then* run "apt-get update" and "apt-get dist-upgrade")

---

### Post by Kareeser on 2009-06-26
mcduck, are you completely sure? In my experience, update-manager ran dist-upgrade, since it would download and install new versions of the kernel. (Thereby breaking my video driver in the process)

---

