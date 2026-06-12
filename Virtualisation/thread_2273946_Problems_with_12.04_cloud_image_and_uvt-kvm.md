---
title: "Problems with 12.04 cloud image and uvt-kvm"
date: 2015-04-16
forum: Virtualisation
---

### Post by tom-dean on 2015-04-16
I'be been using uvt-kvm for a while without many problems. I have a ubuntu server set up
with network bridging (no DNS on the network, static addresses only). I've been using the following
command without any problems to build a new vm

[FONT=Menlo]uvt-kvm create machine_name release=trusty --bridge br0 --memory 2048 --disk 20 --password xyzzy

I know that the --password is not secure, but I'm the only one with access to the server machine.

I log in ont the console via vnc using the account ubuntu and the password from the command line
and set the ip addresses, etc, change to a new secure password as well.

The problem is when I build a 12.04 machine (release=precise).  The new domain will not let me log in from
the vnc console.  Since there is no DNS and the network is on the main bridge, the other documented
ways of connecting do not work either. Looking in the -ds second disk image and the password is correct.

So for some reason it seems like the 12.04 cloud image doesn't set the ubuntu account password?

The server is running 14.04 lts in server mode, and I access it remotely.

Thanks..

Tom.



[/FONT]

---

