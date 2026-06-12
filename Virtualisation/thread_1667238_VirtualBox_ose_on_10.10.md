---
title: "VirtualBox ose on 10.10"
date: 2011-01-14
forum: Virtualisation
---

### Post by Emanuele_Z on 2011-01-14
Hi,

is it possible to install VirtualBox ose 3.2.10 (or next versions) on Ubuntu 10.10?

Because 3.2.8 is without X-Server support and it does suck a bit...

Cheers,

---

### Post by Dutch70 on 2011-01-14
> **Emanuele_Z said:**
> Hi,

is it possible to install VirtualBox ose 3.2.10 (or next versions) on Ubuntu 10.10?

Because 3.2.8 is without X-Server support and it does suck a bit...

Cheers,

Not OSE that I'm aware of, but...
You can download & install Virtualbox 4.0 from here...
[*_[COLOR="Red"]Virtualbox 4.0[/COLOR]_*]("http://www.virtualbox.org/wiki/Linux_Downloads")

You have to completely remove ose or it will conflict with the latest version.

---

### Post by Emanuele_Z on 2011-01-15
> **Dutch70 said:**
> Not OSE that I'm aware of, but...
You can download & install Virtualbox 4.0 from here...
[*_[COLOR="Red"]Virtualbox 4.0[/COLOR]_*]("http://www.virtualbox.org/wiki/Linux_Downloads")

You have to completely remove ose or it will conflict with the latest version.

Will I be able to go back when 3.2.12 comes out with 11.04?
Why has no-one thought about this issue?
It is a bit like if canonical/Ubuntu community wanted people to switch to the *closed* Oracle version.

Cheers,

---

### Post by CharlesA on 2011-01-15
Just install 3.2.12 if that's the case.

---

### Post by Emanuele_Z on 2011-01-15
> **CharlesA said:**
> Just install 3.2.12 if that's the case.

Cool, how can I do it?
Is there a repo for 10.10?

Cheers,

---

### Post by CharlesA on 2011-01-15
I was able to install the ose version on 10.04, not sure about 10.10.

Try this:

```
apt-cache search virtualbox
```

---

### Post by CharlesA on 2011-01-15
I was able to install the ose version on 10.04, not sure about 10.10.

Try this:

```
apt-cache search virtualbox
```

---

### Post by Emanuele_Z on 2011-01-15
This is the output:

```

ema@scv:/disk2/NZB/tmp3$ apt-cache search virtualbox
libvirt-bin - the programs for the libvirt library
libvirt-dev - development files for the libvirt library
libvirt-doc - documentation for the libvirt library
libvirt0 - library for interfacing with different virtualization systems
libvirt0-dbg - library for interfacing with different virtualization systems
python-libvirt - libvirt Python bindings
imvirt - detects several virtualizations
libimvirt-perl - Perl module for detecting several virtualizations
testdrive-cli - run the daily Ubuntu ISO in a virtual machine (command line)
testdrive-common - run the daily Ubuntu ISO in a virtual machine (common files)
testdrive-gtk - run the daily Ubuntu ISO in a virtual machine (GTK Front-end)
virtualbox-ose - x86 virtualization solution - base binaries
virtualbox-ose-dbg - x86 virtualization solution - debugging symbols
virtualbox-ose-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-ose-fuse - x86 virtualization solution - virtual filesystem
virtualbox-ose-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-ose-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-ose-guest-x11 - x86 virtualization solution - X11 guest utilities
virtualbox-ose-qt - x86 virtualization solution - Qt based user interface
xmount - tool to crossmount between multiple input and output harddisk images
virtualbox-guest-additions - guest additions iso image for VirtualBox
virtualbox-4.0 - Oracle VM VirtualBox

```
I can't find the specific version.
I'm running Ubuntu 10.10.

Cheers,

---

### Post by Emanuele_Z on 2011-01-15
<removed because of double posting>

---

### Post by ert69 on 2011-01-15
Just go to Ubuntu Software Center and search for virtualbox and install it. Its OSE.

---

### Post by Emanuele_Z on 2011-01-15
> **ert69 said:**
> Just go to Ubuntu Software Center and search for virtualbox and install it. Its OSE.

There's only version 3.2.8, which has the wrong X-server addons.
I'd like to install 3.2.10 or 3.2.12 OSE for Ubuntu Maverick (10.10).

Are you sure should be there?

---

### Post by CharlesA on 2011-01-15
Hrm. I've only used the PUEL version. If you need to upgrade the guest additions to get X to work, see here: [http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

Post 1.

---

### Post by Emanuele_Z on 2011-01-16
> **CharlesA said:**
> Hrm. I've only used the PUEL version. If you need to upgrade the guest additions to get X to work, see here: [http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

Post 1.

I guess I'll do the following on the virtualized host then:

```

sudo apt-get remove virtualbox-ose-guest-x11

```
reinstall the additions, and finally
```

sudo apt-get install virtualbox-ose-guest-x11

```

I'll let you know!

Cheers,

---

### Post by Emanuele_Z on 2011-01-16
Indeed now it works!

Thanks again!

Cheers,

---

