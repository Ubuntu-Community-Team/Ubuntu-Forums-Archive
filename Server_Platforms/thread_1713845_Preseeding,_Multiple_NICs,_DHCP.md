---
title: "Preseeding, Multiple NICs, DHCP"
date: 2011-03-24
forum: Server Platforms
---

### Post by OffbeatAdam on 2011-03-24
Greetings Everyone,

I am fighting an issue that seems to carry amongst deb-installer itself, and not just in ubuntu... and across a few versions.

In preseeding Ubuntu 10, 9, 8, and 7... as well as Debian Squeeze, Lenny, and Etch... we have a desire to have the installation proceed without a single question being asked. This is the obvious intention of preseeding in general.

I am able to make this happen when two situations are true:

1) The device used is eth0, and eth0 has a cable plugged into it.
2) I forcefully set the interface within the init lines in the pxe target config, as well as within the preseed file.

I can also FORCE it to happen with a NON-WORKING preseed by executing the following command in a terminal:

udhcpc -i eth1

I am unable to make this happen when these situations are true:

1) eth0 is not the primary interface
2) eth1 is the device with copper plugged in
3) Certain onboard NICs, even when BIOS/Jumper Disabled

Again - I can make THESE situations work with udhcpc -i eth1.

I have attempted varying degrees of options, including setting the DHCP timeout to 1000.

In actuality, setting DHCP to 1000 only caused the installer to attempt to connect eth0 for 1000 seconds, even though eth0 had no cable plugged into it and eth1 did.

Here are the various preseed/kernel settings I have attempted:

1)

Preseed: d-i netcfg/choose_interface select auto
Kernel: 
APPEND auto=true lang=en_US locale=en_US console-setup/layoutcode=us priority=critical  url=url_to_preseed vga=normal initrd=debian/squeeze/amd64/initrd.gz ramdisk_size=10882 root=/dev/ram0 netcfg/choose_interface=auto devfs=mount,dall netcfg/dhcp_timeout=1024 DEBCONF_DEBUG=5 rw --

2) [WORKS]

Preseed: d-i netcfg/choose_interface select eth1
Kernel: 
APPEND auto=true lang=en_US locale=en_US console-setup/layoutcode=us priority=critical  url=url_to_preseed vga=normal initrd=debian/squeeze/amd64/initrd.gz ramdisk_size=10882 root=/dev/ram0 netcfg/choose_interface=eth1 devfs=mount,dall netcfg/dhcp_timeout=1024 DEBCONF_DEBUG=5 rw --

3)

Preseed: d-i netcfg/choose_interface select auto
Kernel: 
APPEND auto=true lang=en_US locale=en_US console-setup/layoutcode=us priority=critical  url=url_to_preseed vga=normal initrd=debian/squeeze/amd64/initrd.gz ramdisk_size=10882 root=/dev/ram0 netcfg/choose_interface=auto devfs=mount,dall DEBCONF_DEBUG=5 rw --


Honestly there really isn't many other configs I can try... but I've tried varying degrees of timeouts, no timeouts, etc.


Anyone have any ideas?

I don't really have any easy way of determining when a machine will or will not be using eth0... I really need auto to work like it is supposed to.

If you would like to see, a squeeze syslog is here:

[http://www.x-zen.cx/syslog.txt](http://www.x-zen.cx/syslog.txt)

The squeeze syslog and all the others are ESSENTIALLY identical.

If you would like, I can put up an ubuntu syslog as well.

---

### Post by koenn on 2011-03-24
yep; multiple NICs can be troublesome.
Here's some info: [http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)
and I heard a fem months ago Fedora was working on something to deal with this but I don't remember the details. 

Yeah, d-i netcfg/choose_interface select auto should work, but you may want to look up what d-i considers a "useble" NIC : driver loaded ? cable plugged in ?

I can imagine things failing when the installer image doesn't have a module for an obscure (onboard?) NIC, so that would explain part of the problem.

What happens if you just plug in all NICs so that at least your preseed runs, and reconfigure the interfaces afterwards, after the OS install, using plain DHCP or MAC/hostname based IP address assignments, etc. Is that an option or am I missing something ?

---

### Post by OffbeatAdam on 2011-03-29
> **koenn said:**
> yep; multiple NICs can be troublesome.
Here's some info: [http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)
and I heard a fem months ago Fedora was working on something to deal with this but I don't remember the details. 

Yeah, d-i netcfg/choose_interface select auto should work, but you may want to look up what d-i considers a "useble" NIC : driver loaded ? cable plugged in ?

I can imagine things failing when the installer image doesn't have a module for an obscure (onboard?) NIC, so that would explain part of the problem.

What happens if you just plug in all NICs so that at least your preseed runs, and reconfigure the interfaces afterwards, after the OS install, using plain DHCP or MAC/hostname based IP address assignments, etc. Is that an option or am I missing something ?

Edit:

I should know that the name has nothing to do with it. I know when its eth1 and I know when it's eth0. I'm well aware of the naming switching, the problem is that only one NIC has the cable plugged in. So, this would logically mean that "auto" should select that, as I'm not using a static name. It would seem silly to me for auto to select an inactive nic, when an active one is available. Thanks for the info though. I've read that about fedora as well - they're going to be changing the naming schema. I believe it looked more like freebsd... where a nic is named for it's identifying properties (vendor, for example).

Being a datacenter where automation is significant, and ports are normally limited in a full rack, and time is of the essence, the last solution doesn't blend well.

Currently, the accepted way is, we hit enter and select the nic - then everything else is automated. This is particularly faster than that last option, however I would like to eliminate that last step.

The problem is that, this isn't an obscure NIC - this is all NICs that we have. Whether it be an opteron board with a marvell, or a broadcom, or even a nVidia - or an intel system with any array of those as well as any long list of others, the NIC range is neither obscure nor selective.

This is a 100% of all systems problem. It never selects the NIC that is plugged in, unless that NIC is iterated as eth0. Any other case yields the same situation.

In the system I'm currently looking at, it's a normal Intel NIC that comes with the 5520 chipset. These are Intel NICs, 82768 I believe. They are 10/100/1000 nics, and they are supported by the ever so common e1000 driver.

Another system I'm working on is a Dell with Broadcom NICs.

Another system I'm working on is an older Intel, with older Intel NICs supported by the same e1000 driver.

Ultimately they all have one thing in common: the problem. Everything else is different... and this has been happening for a long time. I have absolutely no success in isolating it to a certain platform.

---

### Post by koenn on 2011-03-30
I think you're right abut that "auto" should select the usable NIC, and i guess it is supposed to (if I understand the documentation correctly), so maybe you could check with debian (devel mailing list, bug tracker, ...).



I suppose there's no way to have a preseed do something like
- Q:"which NIC ?"
- select eth0
- try DHCP
- if it fails, ask the question again
- select eth1
-try DHCP (and now it shouldn't fail)


Other than that, I don't really see a solution; I'd think "auto-select the working, connected NIC" *is* the solution - if that doesn't work, it's a bug.

---

### Post by OffbeatAdam on 2011-03-31
> **koenn said:**
> I think you're right abut that "auto" should select the usable NIC, and i guess it is supposed to (if I understand the documentation correctly), so maybe you could check with debian (devel mailing list, bug tracker, ...).



I suppose there's no way to have a preseed do something like
- Q:"which NIC ?"
- select eth0
- try DHCP
- if it fails, ask the question again
- select eth1
-try DHCP (and now it shouldn't fail)


Other than that, I don't really see a solution; I'd think "auto-select the working, connected NIC" *is* the solution - if that doesn't work, it's a bug.


I have been searching rather heavily in the need to find a resolution to this, even if it is patchy.

I've seen the following bug:

[https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/713385](https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/713385)

That pointed me to this:

[https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/56679](https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/56679)

This gives the pointer to a PXELINUX option:

ipappend 2

Which adds BOOTIF=<macaddr> to the end of the kernel line. (for the interface which dhcp was booted).

By using this, and adding a script to deb-installer-startup.d that runs prior to the install, I should be able to pass a debconf of the utilized interface.

However, this will require rebuild of the initrd every time we update our release, so it is not optimal (though for the issue it does provide a resolution).

---

### Post by OffbeatAdam on 2011-03-31
After testing with Ubuntu 10, and Debian Lenny as well as Squeeze, the solutions outlined in the bug reports listed above yielded satisfactory results, and will be the method that I go with for now.

I would still like to see the 'auto' functionality work as it was intended.

---

