---
title: "Accessing Host files from KVM Machine"
date: 2017-06-08
forum: Virtualisation
---

### Post by alistairgerrard on 2017-06-08
Hi,

I set up a VM which can access a share on the underlying host machine and then cloned it. Both machines worked and I used this to setup the second machine as my PlexServer.

Moved house and somehow the second machine can no longer see the host share. But the original machine can, as can a new clone of it.

As far as I can recall, I added a Fileshare to the KVM, changed some permissions, and added commands to /etc/fstab and /etc/rc.local

I've tried a number of things but in vain so far. The main issues, beyond the fundamental of it not working, are:
1) I can't find the original instructions I used to simply re-follow them
2) I can't find what's wrong despite using a virt-diff command
3) I don't want to have to move my Plex licence (and reconfigure) but I think that may be easier - again, needs decent instructions though

Let me know if more information is required please.

Alistair

---

### Post by KillerKelvUK on 2017-06-08
Hey Alistair, do you know what the share solution was i.e. is/was it a filesystem passthrough using kvm or possible a samba/nfs share off your host?  Need a starting point if you can help narrow it down?

Also please can you confirm if the affected guest is connected to the network i.e. has an IP address that is pingable, anything to rule out something else being the cause of the sharing issues?

Please can you also confirm the OS for host and guest as well as the contents of the /etc/fstab and /etc/rc.local files that you mention, this will help if you aren't certain?

---

