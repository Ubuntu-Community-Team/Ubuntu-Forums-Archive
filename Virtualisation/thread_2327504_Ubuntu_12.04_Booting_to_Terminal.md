---
title: "Ubuntu 12.04 Booting to Terminal"
date: 2016-06-11
forum: Virtualisation
---

### Post by Quarkrad on 2016-06-11
Running Ubuntu 16.04 host - Virtualbox 5.0.20    Never had this one before - installing ubuntu 12.04 guest.  Guest install ok to desktop, then install guest editions.  install ubuntu-extras and restart - ubuntu 12.04 guest boots to terminal.   Installed desktop (instructions from Askubuntu) and rebooted.  Booted again to terminal but now says 'could not write bytes: Broken pipe'.  Any advice appreciated - install guest twice now and same result.

---

### Post by MAFoElffen on 2016-06-16
Okay--

Ubutnu 16.04 Host > VirtualBox 5.0.20 (like in main repo for Xenial) <> Virtualbox Extension pack 5.0.20 

Virtualbox started using the Extension Pack instead of Guest Additions starting back from versons 4.3 and up... Insure that you used the correct version of the Extension Pack and open that file with virtualbox to install it globally to Virtualbox itself, instead of how the guest additions, that installed to each vm guest, individually.

Next, a "Could not write bytes: Broken pipe" error, back with Ubuntu version 12.04 was an X11 error that meant it didn't have the authority somewhere to open the XSession. go to grub menu > Rescue Meneu > Networking (which will mount the filesystem as rw) > Drop to Root Prompt ... and do
```

cd /home/YourUserName
ls -l ./.Xauthority

```
It should be there and owned by you, not by root...

To correct (while still in your user directory as root):
```

rm ./.Xauthority
touch ./XAuthority
chmod 660 ./Xautohrity
chown YourUserName ./.Xauthority

```
In both those, substitute your own user name for any instance of YourUserName in the above commands...

---

### Post by Quarkrad on 2016-06-16
That did it - many thanks, and sorry for not replying sooner.

---

