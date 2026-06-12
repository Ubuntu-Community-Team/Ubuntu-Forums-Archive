---
title: "VirtualBox Guest Additions Installer Script"
date: 2009-03-26
forum: Virtualisation
---

### Post by schmidtbag on 2009-03-26
[SIZE="5"][ATTACH]107712[/ATTACH][/SIZE]


I wrote this script during class that automatically installs the guest additions for Ubuntu.  Just move to the current directory of the script and run "bash gai.sh" and it does all the work for you, and tells you what to do if something is wrong.


Instructions are included in the file.


Please help promote this and feel free to edit it.

---

### Post by Jose Catre-Vandis on 2009-03-28
Good work, though makes a few assumptions:

1. That the Virtual Additions CD actually mounts when you got to Devices
(having done countless VM installs i can tell you it doesn't)
2. That you have installed "build essential" on your installation
(this installs make and gcc to allow VBox Additions to compile)

:)

---

### Post by binbash on 2009-03-28
Additions :  This will not work on jaunty since guest additions installer script can't detect 1.6.0 xorg

---

### Post by schmidtbag on 2009-03-29
> **Jose Catre-Vandis said:**
> Good work, though makes a few assumptions:

1. That the Virtual Additions CD actually mounts when you got to Devices
(having done countless VM installs i can tell you it doesn't)
2. That you have installed "build essential" on your installation
(this installs make and gcc to allow VBox Additions to compile)

:)


It tells you if you haven't selected "Install Guest Additions" from the Devices menu and unless you are installing an older version of Ubuntu, the "build essential" doesn't need to be installed - I've tried this script on brand new installations of Ubuntu 8.10.  I have heard of build essential and I didn't think 8.10 came with it pre-installed but I guess it does.  I'll look into adding that.

---

### Post by schmidtbag on 2009-03-29
> **binbash said:**
> Additions :  This will not work on jaunty since guest additions installer script can't detect 1.6.0 xorg

Not really my problem - I like the original xorg as do many other linux users.  Its either up to Canonical or Sun to  fix that issue, not me

---

