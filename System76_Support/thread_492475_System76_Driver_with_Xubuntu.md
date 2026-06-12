---
title: "System76 Driver with Xubuntu"
date: 2007-07-04
forum: System76 Support
---

### Post by harun on 2007-07-04
I have a Pangolin Value. I started with a clean install (full format) and installed Xubuntu. After downloading the System76 driver .deb I try to install it and get the following:

```

$ sudo dpkg -i system76-driver-2.0.5.deb
(Reading database ... 99522 files and directories currently installed.)
Unpacking system76-driver (from system76-driver-2.0.5.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing system76-driver-2.0.5.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/system76/system76-driver/src/tifm/.tifm_sd.mod.o.cmd')
Errors were encountered while processing:
 system76-driver-2.0.5.deb

```

Anybody seen this with Xubuntu?

---

### Post by thomasaaron on 2007-07-05
I think the driver should install and run in Xubuntu (although we do not testing with Xubuntu).

So, did the install abort, or did it continue the install? Does it appear in your menu?
If it continued the install, you should be good-to-go. It will produce some error messgaes, but that's generally expected and OK.

---

### Post by harun on 2007-07-05
Interestingly enough, it appeared to die right away and not continue, but when looking in the menu the System76 driver option is there. My sound and the rest of the things I have tried also appear to be working fine.

When running Synaptic it says I have a broken package though. Would like to get it to stop doing that.

If you would like any assistance with testing this on Xubuntu I would be glad to help.

Thanks for the quick reply.

---

### Post by thomasaaron on 2007-07-05
Go to System > Administration > Synaptic Package Manager.
Then go to Edit > Fix Broken Packages.

---

### Post by Rowan187 on 2007-07-06
> **thomasaaron said:**
> Go to System > Administration > Synaptic Package Manager.
Then go to Edit > Fix Broken Packages.

or just "sudo apt-get update -f" in the Terminal (it happens to me a lot)

---

### Post by mrbones on 2008-04-09
Does this possibly work with the Gazell Value?

---

### Post by thomasaaron on 2008-04-10
Does what work with the Gazelle Value? Do you mean Xubuntu? Or that command? I guess the answer to both would be yes, though.

---

