---
title: "Ovirt:Anyone using it?, DEB/Alienized packages?"
date: 2009-06-29
forum: Virtualisation
---

### Post by juancarlospaco on 2009-06-29
**[SIZE="3"][http://ovirt.org/download.html]("http://ovirt.org/download.html")[/SIZE]**

Anyone using it?, 
DEB / Alien*[SIZE="1"]ized[/SIZE]* packages?
I want to try it on Ubuntu Server.

*thanks...*

---

### Post by bodhi.zazen on 2009-06-29
Looking at it briefly it appears to be quite the package. On the installation page they even advise installing on a virtual machine to take Ovirt for a test drive.

I would advise you test it on Fedora 10 and my guess is it would be difficult to install on Ubuntu as it appears to be very Fedora specific.

In my experience virtualization is quite complex and looking at the package list and requirements I think you will find it very very difficult on Ubuntu ;

> 

[LIST=1]
[*]**Fedora 10**: installed with latest updates.
[*]**Passwordless Sudo**: The user running the build does not         need to be root, however it does need to have passwordless sudo as         root access.  This is because the ovirt-appliance and ovirt-node-image         repositories use livecd-creator which presently requires root.
[*]**Hardware Virtualization Support**: The oVirt Node         and oVirt Appliance require hardware assisted virtualization.  A         processor with either Intel VT or AMD AMD-V is required to run         oVirt.  The build process does not require hardware virtualization.
[*]**rpmmacros**: The user must have valid          ~/.rpmmacros set up.  A minimal rpmmacro file should          contain: %_topdir      %(echo $HOME)/rpmbuild         This will put your rpmbuild directory in ~/rpmbuild.         Adjust the destination to your liking.
[*]**SELinux**The Node is built with SELinux enabled by         default.  This requires build host to also have SELinux enabled in         Permissive mode.  If SELinux is not enabled, the build will fail.         If it is enabled but in Enforcing mode the build will temporarily         put the host into Permissive mode and then toggle back to         Enforcing

         NOTE: The Node does not require SELinux to be enabled, though it         is by default.  This behavior can be toggled in the Node kickstart         file in the ovirt-node-image repository.
[*]**Additional Computers**: These computers should be         cabled to a private LAN that will be bridged to the oVirt          Appliance.  These computers will run the oVirt Node and will          be managed by the oVirt Server.
[/LIST]
I am not sure about rpmmacros, but SELinux will almost certainly be difficult. You would need to install selinux on Ubuntu, probably then need Ubutnu 8.04, and you will almost certainly have conflicts with versions of libvirt. Updating the selinux rules may also be problematic.

---

### Post by freakalad on 2009-07-08
tried going down that route a while back, but if I recall, it didn't end well. At all.

An alternative system you may wan to consider is [Enomaly]("http://src.enomaly.com/"), but I think it's only available/stable on Hardy LTS. Tried using it on my Jaunty-64, but the installer threw all sorts of errors

In Jaunty, you have tools such as [Eucalyptus]("http://open.eucalyptus.com/") & [OpenNebula]("http://www.opennebula.org") to admin you cloud servers.

If you look closely, you'll see that all of these systems where RHEL/RPM-based tools when they started out, including libvirt, so you may expect to see many of them ported to Ubuntu. Eventually

---

