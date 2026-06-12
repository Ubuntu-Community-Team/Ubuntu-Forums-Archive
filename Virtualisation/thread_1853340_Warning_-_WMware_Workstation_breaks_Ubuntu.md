---
title: "Warning - WMware Workstation breaks Ubuntu"
date: 2011-10-02
forum: Virtualisation
---

### Post by dcstar on 2011-10-02
I started having major problems with my 10.04 Ubuntu system recently with dirty filesystems having to be checked at each boot up slowing things down and I have finally found the culprit - VMware Workstation Version 8.

The problem is that the VMware install process renames ALL the file links in /etc/rc0.d & /etc/rc6.d. The end result is that Ubuntu no longer shuts down correctly and the system closes before all filesystems are cleanly unmounted.

As an example this is what /etc/rc0.d should have in it:

```
K20boinc-client
K20clamav-freshclam
K20hddtemp
K20postfix
K20samba4
K20xrdp
K31atieventsd
K50pcscd
K74bluetooth
K80openvpn
K99policycoreutils
README
S10unattended-upgrades
S15wpa-ifupdown
S20sendsigs
S30urandom
S31umountnfs.sh
S35networking
S40umountfs
S60umountroot
S90halt
```
And this is what is is after the VMware install:
```
K01bluetooth
K01boinc-client
K01hddtemp
K01openvpn
K01pcscd
K01policycoreutils
K01postfix
K01samba4
K01vmware-workstation-server
K01xrdp
K02atieventsd
K02vmware
K05clamav-freshclam
README
S01halt
S01networking
S01sendsigs
S01umountfs
S01umountnfs.sh
S01umountroot
S01unattended-upgrades
S02urandom
S02wpa-ifupdown
```

As you can see, the critical digits which determine what order each script is executed in are now totally changed.

Here is what a correct /etc/rc6.d folder should contain:
```
K20boinc-client
K20clamav-freshclam
K20hddtemp
K20postfix
K20samba4
K20xrdp
K31atieventsd
K50pcscd
K74bluetooth
K80openvpn
K99policycoreutils
README
S10unattended-upgrades
S15wpa-ifupdown
S20sendsigs
S30urandom
S31umountnfs.sh
S35networking
S40umountfs
S60umountroot
S90reboot

```

If you have installed VMware Workstation/Player you may want to check your system for this problem and manually rename the relevant file links (ignore links that do not apply to your system).

I have posted this in the relevant VMware forum so hopefully it will be resolved by them.

---

### Post by bodhi.zazen on 2011-10-03
Vmware (workstation) does not support Ubuntu

[http://www.vmware.com/support/ws5/doc/intro_supguest_ws.html](http://www.vmware.com/support/ws5/doc/intro_supguest_ws.html)

Most people are migrating to Virtualbox or KVM, although to run KVM you need the hardware and honestly you probably should run RHEL or Scientific.

Proxmox is IMO the best debian solution:

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

[http://www.redhat.com/virtualization/rhev/](http://www.redhat.com/virtualization/rhev/)

---

### Post by lcman on 2011-10-05
> **bodhi.zazen said:**
> Vmware (workstation) does not support Ubuntu

[http://www.vmware.com/support/ws5/doc/intro_supguest_ws.html](http://www.vmware.com/support/ws5/doc/intro_supguest_ws.html)

Most people are migrating to Virtualbox or KVM, although to run KVM you need the hardware and honestly you probably should run RHEL or Scientific.

Proxmox is IMO the best debian solution:

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

[http://www.redhat.com/virtualization/rhev/](http://www.redhat.com/virtualization/rhev/)

Why RHEL? Doesn't Ubuntu Server come with full KVM support? :confused: Thought Ubuntu was better than RH!

---

### Post by bodhi.zazen on 2011-10-05
> **lcman said:**
> Why RHEL? Doesn't Ubuntu Server come with full KVM support? :confused: Thought Ubuntu was better than RH!

Because RHEL is pushing the Virtualization envelope, the kvm packages lag (significantly) in Ubuntu.

For example, spice (client) has not been fully ported to Debian or Ubuntu yet.

Also RHEL has selinux , which is extremely helpful for zero day exploits.

[https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf](https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf)

[http://danwalsh.livejournal.com/#post-danwalsh-45194](http://danwalsh.livejournal.com/#post-danwalsh-45194)

---

### Post by collisionystm on 2011-10-05
That link is a list of Supported Guest Operating Systems. Ubuntu is not a supported guest.

I have never had problems with 11.10 and Vmware Workstation 8.

---

### Post by lcman on 2011-10-05
> **bodhi.zazen said:**
> Because RHEL is pushing the Virtualization envelope, the kvm packages lag (significantly) in Ubuntu.

For example, spice (client) has not been fully ported to Debian or Ubuntu yet.

Also RHEL has selinux , which is extremely helpful for zero day exploits.

[https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf](https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf)

[http://danwalsh.livejournal.com/#post-danwalsh-45194](http://danwalsh.livejournal.com/#post-danwalsh-45194)

Yea RHEL basically owns kvm, that's why! But, ubuntu server is going to reintroduce xen in 11.10 and i'm really looking forward to that!

What about apparmor? I couldn't find enough documentation describing many benefits of SElinux over apparmor. I find it more complex to configure though! How else do they compare?

---

### Post by Dangertux on 2011-10-06
The major difference between Apparmor and SELinux is how they set access controls. Apparmor is based on paths, where SELinux is dependent on labeling files individually. The obvious drawback here is that Apparmor can be compromised by hardlinking outside the path of control. This can be countered in various ways, including making key applications or files immutable (see chattr). The largest drawback to SELinux is that it  doesn't deal with NFS file systems very well, thus can not control them, whereas Apparmor is file system agnostic.

Hope that helps.

---

### Post by bodhi.zazen on 2011-10-06
> **lcman said:**
> Yea RHEL basically owns kvm, that's why! But, ubuntu server is going to reintroduce xen in 11.10 and i'm really looking forward to that!

What about apparmor? I couldn't find enough documentation describing many benefits of SElinux over apparmor. I find it more complex to configure though! How else do they compare?

Apparmor and selinux basically accomplish similar goals. Apparmor is easier to understand and learn, but often as an end user you need to then review and modify the profiles.

Selinux is default on fedora / rhel. you can either run fedora in a VM or read about selinux

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/)

It takes longer to learn but is, IMO, a bit more comprehensive, at least out of the box. It needs a few tweaks (confining users for example) and it does not lock down /home as much or as easily as apparmor, but system files are servers are a bit more confined.

---

### Post by lcman on 2011-10-06
> **bodhi.zazen said:**
> Apparmor and selinux basically accomplish similar goals. Apparmor is easier to understand and learn, but often as an end user you need to then review and modify the profiles.

Selinux is default on fedora / rhel. you can either run fedora in a VM or read about selinux

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/)

It takes longer to learn but is, IMO, a bit more comprehensive, at least out of the box. It needs a few tweaks (confining users for example) and it does not lock down /home as much or as easily as apparmor, but system files are servers are a bit more confined.

It's default on rhel, but I can install it on ubuntu from the official repos right? Or is it some debian ported version?

What if I use an Ubuntu 11.10 dom0 with selinux installed? Would it be a viable solution for say, enterprise use?

P.S Really sorry for thread hijacking btw

---

### Post by Dangertux on 2011-10-06
EDIT : Nevermind , probably not the right place for it.

SELinux is great for confinement in an enterprise environment.

---

### Post by bodhi.zazen on 2011-10-06
> **lcman said:**
> It's default on rhel, but I can install it on ubuntu from the official repos right? Or is it some debian ported version?

What if I use an Ubuntu 11.10 dom0 with selinux installed? Would it be a viable solution for say, enterprise use?

P.S Really sorry for thread hijacking btw

You really should start a new thread. If you want to use selinux, use Fedora. Installing selinux on Debian or Ubuntu is not for users new to either Ubuntu or selinux.

---

### Post by lcman on 2011-10-06
> **bodhi.zazen said:**
> You really should start a new thread. If you want to use selinux, use Fedora. Installing selinux on Debian or Ubuntu is not for users new to either Ubuntu or selinux.

Oh I've got it a little figured out already, got a detailed explanation from dangertux in my pm! :p 

Decided to use apparmor for now. Thanks anyway, community help is always awesome!

---

### Post by dcstar on 2011-10-07
> **bodhi.zazen said:**
> Vmware (workstation) does not support Ubuntu

[http://www.vmware.com/support/ws5/doc/intro_supguest_ws.html](http://www.vmware.com/support/ws5/doc/intro_supguest_ws.html)
......

I don't see how quoting a link for Workstation 5 is relevant for Workstation 8.

The VMware Workstation 8 Release Notes even mentions issues with Ubuntu 10.10 & 11.04, so if that does not imply "support" I don't really know what does:

[http://www.vmware.com/support/ws80/doc/releasenotes_workstation_80.html#Installation_Requirements](http://www.vmware.com/support/ws80/doc/releasenotes_workstation_80.html#Installation_Requirements)

I had manually fixed my scripts and then VMware Player offered me another version 4 upgrade - which installed **and broke my scripts again**..... sigh....

---

### Post by bodhi.zazen on 2011-10-07
> **dcstar said:**
> I don't see how quoting a link for Workstation 5 is relevant for Workstation 8.

The VMware Workstation 8 Release Notes even mentions issues with Ubuntu 10.10 & 11.04, so if that does not imply "support" I don't really know what does:

[http://www.vmware.com/support/ws80/doc/releasenotes_workstation_80.html#Installation_Requirements](http://www.vmware.com/support/ws80/doc/releasenotes_workstation_80.html#Installation_Requirements)

I had manually fixed my scripts and then VMware Player offered me another version 4 upgrade - which installed **and broke my scripts again**..... sigh....

That is true, but your link is equally irrelevant. Where is the list of supported OS , host and guest, for WS8 ?

Personally I have converted over to KVM many years ago and have not looked back.

---

### Post by Dangertux on 2011-10-07
I'm just really excited for returning Xen support in 11.10 without having to recompile my kernel :-)

I'm so glad Canonical is giving Xen another chance, it really is an awesome product.

---

### Post by dcstar on 2011-10-09
> **bodhi.zazen said:**
> That is true, but your link is equally irrelevant. Where is the list of supported OS , host and guest, for WS8 ?

Personally I have converted over to KVM many years ago and have not looked back.

Good for you, now for some relevant information in that the people at VMware are now looking into this bug as **they** seem to believe that their products are supposed to run on Ubuntu.

---

### Post by dcstar on 2011-10-10
> **bodhi.zazen said:**
> That is true, but your link is equally irrelevant. Where is the list of supported OS , host and guest, for WS8 ?


If you go to: [http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software](http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software)

Select the "Compatibility Guides" feature and you can download a full PDF file that says that Workstation 7.1.4 is supported on a Ubuntu 10.04 host, and other versions of Ubuntu up to 9.10 seem to have been verified as hosts for Workstation 8, so it does clearly seem to be a supported platform.

---

### Post by dcstar on 2011-10-14
Still broken in 4.0.1

---

