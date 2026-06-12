---
title: "Catastrophic problem after apt-get update, please help"
date: 2010-06-06
forum: Server Platforms
---

### Post by jimwillsher on 2010-06-06
Hello,

I'm running Lucid x64 server version. I've just checked for updated packages as I like to be up to date. My update script does this:

```

echo Checking for updates...
echo ...
apt-get update
apt-get dist-upgrade
apt-get clean
apt-get autoclean

```


4 packages (including a kernel) were listed as available, and I chose to update. I then get this:


```

dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-22-server_2.6.32-22.36_amd64.deb (--unpack):
 unable to create updated files list file for package linux-image-2.6.32-22-server: Invalid argument
Preparing to replace linux-headers-2.6.32-22 2.6.32-22.35 (using .../linux-headers-2.6.32-22_2.6.32-22.36_all.deb) ...
dpkg: unrecoverable fatal error, aborting:
 unable to create `/var/lib/dpkg/updates/tmp.i': Invalid argument
E: Sub-process /usr/bin/dpkg returned an error code (2)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

running the dpkg command as suggested just gives a different error:

```

root@curlew:~#
root@curlew:~# sudo dpkg --configure -a
dpkg: failed to open `/var/lib/dpkg/status' for writing status information: Invalid argument

```

Rebooting the machine (bad idea) tells me that the filesystem is corrupt and it hangs.

I've reverted to a backup and it's running again, but I'm now somewhat scared to use apt-get. I'm running under Hyper-V and I have the vmbus additions:

```

Add the following to /etc/initramfs-tools/modules

hv_vmbus
hv_storvsc
hv_blkvsc
hv_netvsc

update-initramfs &#8211;u


```

Please, can anyone help?

Many thanks,



Jim

EDIT: I just tried the same on my restored copy, and (unsurprisingly) the same happened. Perhaps I'm now stuck with this version of the packages, or perhaps I need to wipe and start again?

---

### Post by jimwillsher on 2010-06-07
Ok, no help from anyone it seems......but I found the answer my self.


For Hyper-V support I've just enabled these modules:
hv_vmbus
hv_netvsc

instead of

hv_vmbus
hv_storvsc
hv_blkvsc
hv_netvsc

and it's now working.

In case this helps anyone else......



Jim

---

