---
title: "Upgrading/installing newer libvirt"
date: 2020-05-29
forum: Virtualisation
---

### Post by jruden on 2020-05-29
Is it simple/feasible to install or upgrade libvirt to a newer version?

I am on ubuntu 18.04/20.04 primarily.

I use this suite of packages to allow for a nice virtualization environment

[LIST]
[*]libguestfs-tools
[*]virtinst
[*]python-libvirt
[*]python-lxml
[*]libvirt-daemon-system
[*]virt-manager
[*]libnss-libvirt
[/LIST]
What exactly from these packages that correspond to what is called "libvirt" in common tongue I'm not totally sure. However my understanding is that 18.04 gives me libvirt 4.0.0 and 20.04 gives me libvirt 6.0.0.

So to my question. Would it be hard to upgrade on say 20.04 the libvirt 6.0.0 to libvirt 6.3.0 which is now released according to [https://libvirt.org/news.html](https://libvirt.org/news.html) ? I fail to find any information about a PPA or some other way to reach newer libvirt version.

Any ideas?

$ virsh -v
6.0.0

---

### Post by TheFu on 2020-05-29
```
$ dpkg -l|grep libvirt
```
will show all the libvirt stuff and the versions.

If there isn't a PPA, I wouldn't attempt any changes.

Are there specific features in the newer version that you seek?  Really, libvirt should be used to create, change hardware and delete VMs.  All the day-to-day management of the OSes running inside a VM should be done using ssh.

---

### Post by jruden on 2020-05-29
This is how it looks on my 20.04:

```
$ dpkg -l|grep libvirt
ii  gir1.2-libvirt-glib-1.0:amd64                               3.0.0-1                                    amd64        GObject introspection files for the libvirt-glib library
ii  libnss-libvirt:amd64                                        6.0.0-0ubuntu8                             amd64        nss plugins providing IP address resolution for virtual machines
ii  libsys-virt-perl                                            5.0.0-1build1                              amd64        Perl module providing an extension for the libvirt library
ii  libvirt-clients                                             6.0.0-0ubuntu8                             amd64        Programs for the libvirt library
ii  libvirt-daemon                                              6.0.0-0ubuntu8                             amd64        Virtualization daemon
ii  libvirt-daemon-driver-qemu                                  6.0.0-0ubuntu8                             amd64        Virtualization daemon QEMU connection driver
ii  libvirt-daemon-driver-storage-rbd                           6.0.0-0ubuntu8                             amd64        Virtualization daemon RBD storage driver
ii  libvirt-daemon-system                                       6.0.0-0ubuntu8                             amd64        Libvirt daemon configuration files
ii  libvirt-daemon-system-systemd                               6.0.0-0ubuntu8                             amd64        Libvirt daemon configuration files (systemd)
ii  libvirt-glib-1.0-0:amd64                                    3.0.0-1                                    amd64        libvirt GLib and GObject mapping library
ii  libvirt0:amd64                                              6.0.0-0ubuntu8                             amd64        library for interfacing with different virtualization systems
ii  python-libvirt                                              5.0.0-1                                    amd64        libvirt Python bindings
ii  python3-libvirt                                             6.1.0-1                                    amd64        libvirt Python 3 bindings
```

I actually found a PPA ([https://launchpad.net/~jacob/+archive/ubuntu/virtualisation](https://launchpad.net/~jacob/+archive/ubuntu/virtualisation)). Think I will try that out, however it seems to contain only up to 6.2.0 at the moment.

There is a specific new feature that I desire which came in v6.3.0:
[LIST]
[*]Lease time option included for network DHCP settings
Users can now configure expiry time for leases for networks where libvirt manages DHCP. The time can be specified for whole range and/or fine tuned per individual host.
[/LIST]

---

### Post by TheFu on 2020-05-29
I don't use DHCP for any of my guests.  Sorry.  If I did, I'd let the LAN DHCP server handle it, not libvirt.

---

### Post by jruden on 2020-05-29
Yeah, I use it for short lived test VMs. Typically they live a couple of hours of some days. Problem is the default leasetime is 1 hour or so so if I stop the VMs and start them the next day the IP numbers are changed causing for example a nomad cluster to get completely messed up... Yes for a longer lived environment static IPs would be the preferred choice. Maybe it could be an option for this as well however it would be convenient to just  set <leasetime>30d</leasetime> :-)

---

### Post by TheFu on 2020-05-29
On my guest network, I use a lease of 7 days.  As long as the device is online when the lease expires, it keeps the same IP.  You could force the lease to be renewed via cron if you like.  1 hour seems abusive.  I'd expect 24hr to be the default, but I really don't know.  DHCP is something I avoid.  

You could setup DHCP reservations, if you want. I have that for network devices that are connected to different networks or don't have easy ways to control the network settings.  Mainly for Android, Roku and network TV tuners.  It works as well as the DHCP server works, which is usually fine, but not always.

---

