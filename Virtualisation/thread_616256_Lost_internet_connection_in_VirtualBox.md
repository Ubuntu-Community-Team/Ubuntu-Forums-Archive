---
title: "Lost internet connection in VirtualBox"
date: 2007-11-18
forum: Virtualisation
---

### Post by timzak on 2007-11-18
I've been using Virtual Box for awhile (all evening) with Win2k guest OS and all was well with internet.  I don't know if this is a coincidence or not, but while the guest OS was running, I went Machine dropdown menu and selected Take Snapshot and saved a snapshot.  Immediatedly after doing this, I lost internet in the guest OS (it still works fine in the host--Gutsy).  I shutdown and rebooted the guest OS and the problem persists.

Any ideas?  I checked the network icon in the guest OS and it says all is okay.  Just no internet.  I guest "Server not found" no matter which site I attempt to load.

Thanks.

Edit:  After rebooting the host OS, the internet connection is fixed in the guest OS.  Weird.  Sorry for the trouble.

---

### Post by kavoura on 2008-12-28
I am having this problem intermittently, in various guests running in Virtual Box on Ubuntu 8.04. Now the latest to be affected is Windows XP Pro, all of a sudden its internet connection is gone. It is still there in the host though. I checked that it was not the firewall in Windows by closing it, but still there was no connection to any websites.
This has also happened in some other guests, mostly Linux. 
The problem sometimes just goes away. But how to fix it quickly without rebooting the guest? Anyone know?

---

### Post by Dedoimedo on 2008-12-29
Try restarting the network in guest/host:

```

sudo service networking restart

```

Or:

```

sudo /etc/init.d/networking restart

```

Try one, try the other, see if it helps.

Cheers,
Dedoimedo

---

