---
title: "Web based interface for Qemu/ Virsh ?"
date: 2012-11-21
forum: Virtualisation
---

### Post by Philip_Clarke on 2012-11-21
Hi,

For a couple of years I've been running Xubuntu with qemu/ virsh and using virt-manager but recently instability in the Host and zombie processes caused by upgrades from 10.10 through to 12.04 led me just install the server version and then put my vm's back.

I installed headless because I want the minimum resource taken up by the Host and because of the former issues with zombie processes. (lightDM even seemed to be a problem). I've searched the threads and had a look at the Qemu website and I cannot seem to find a web interface to virsh. There is a phpVirtualBox and VirtualBox headless, and then RedHat has Ovirt which seems at an enterprise level rather than what I want which is just a basic interface. One thread here mentioned that it would be good to have a webmin module (couple of years ago and now I believe there is a licensing issue with web min).

I can use virt-manager on an old laptop with ubuntu on it, but my main development machines are macs, so does a web interface exist ? Just a simple PHP version would be nice, my system comprises of 4 persistent VM's (file server, database backup server, apple time machine and a web server that is cloned then destroyed many times a month depending on my clients). I am well aware that I could use the command line, but being able to click on the webserver, clone it then delete it (in virt-manager) was rather nice,

Thank you in advance
Philip.

---

### Post by personalpc on 2012-11-25
Zentyal or landscape both offer you vm management. I prefer ssh with x forwarding using virt-manager. Also look into tomcat guacamole for web based vnc to the vms. good luck!

---

### Post by Philip_Clarke on 2012-11-25
But SSH with x forwarding requires running an X server on the host and I try and avoid bloat. I thought landscape was now pay for, which seems overkill for a home system, I will investigate Zentyal, but I suspect that I should probably have installed proxmox as a base OS.

Thank you
Philip

---

### Post by Philip_Clarke on 2012-11-26
> **personalpc said:**
> Zentyal or landscape both offer you vm management. I prefer ssh with x forwarding using virt-manager. Also look into tomcat guacamole for web based vnc to the vms. good luck!
I may be looking at the wrong site ([http://www.zentyal.com](http://www.zentyal.com)) but it isn't immediately apparent how that can give me a web user interface to manage my virtual machines on a headless server.

---

