---
title: "Grub/Kernel inconsistencies"
date: 2017-09-22
forum: Server Platforms
---

### Post by daniel.lawler on 2017-09-22
Hello all,

Team member started an upgrade from 14.04 to 16.04 (LTS), and all I've heard is that "it did not complete successfully".

Upon further investigation, it appears the server is running 16.04LTS, but the kernel version is still 3.x

Looking into the matter deeper, I see that the dpkg -l | grep linux-version shows that the 4.4.x kernels have been installed. This is good. Where it gets weird is, GRUB menu is showing 4.4.x as the only bootable options so it's definitely not booting into the correct kernel. Unsure of the best course of action going forward. I've yet to update-grub as I'm unsure if this will resolve anything.

Any/all help appreciated. 

Thanks!

---

### Post by Bucky Ball on 2017-09-22
Welcome. Please open a terminal and

```
uname -a
```

What kernel does it show? Then

```
lsb_release -a
```

Which release are you using? 16.04.3? The default kernel there is 4.4.0-93 (at least that's what I'm running at the moment, but haven't updated for a couple of days, so ...).

Try this:

```
sudo apt update
sudo apt full-upgrade
```

Run the first two commands again. Do they now show you are running 16.0.3 and the 4.4.0-93 kernel? They should if you are intending to be upgraded to 16.04.3.

---

### Post by daniel.lawler on 2017-09-22
Thanks for the reply. I'm going to have to hand type the outputs as it's a VM without copy/paste set up

uname -r outputs:
```
3.13.0-129-generic

```

lsb_release -a outputs:
```

No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.3 LTS
Release: 16.04
Codename: xenial

```

I'll try the full-upgrade command shortly. I wasn't sure if starting the entire "upgrade" process again would overwrite and re-apply what was necessary or not.

---

### Post by daniel.lawler on 2017-09-22
Interestingly, just did a reboot as I wanted to check GRUB directly, and when I attempt to boot into the 4.4.x kernel, I receive a kernel panic: 

```
kernel panic not syncing vfs unable to mount root fs on unknown block 0,0
```

---

### Post by daniel.lawler on 2017-09-22
Please note, the server does boot back into the old kernel successfully.

---

### Post by darkod on 2017-09-22
If the release upgrade got interrupted, you should try continuing it. The system already has parts of 16.04 and "thinks" it is on 16.04 (the lsb_release shows that). As suggested earlier, try what you would do for standard update (not release upgrade).
```
sudo apt-get update (notice if it pulls from xenial repositories)
sudo apt-get dist-upgrade
```

I don't know what is the difference between dist-upgrade and full-upgrade, but dist-upgrade should also do the job.

Try it and let us know...

---

### Post by daniel.lawler on 2017-09-22
Hello Darko! 

Thanks for the suggestion. 

Went ahead and ran your suggested update/dist-upgrade to no avail. 

update pulled some things from xenial, and dist-upgrade just states that currently there is nothing to install/remove/upgrade.

---

### Post by darkod on 2017-09-22
OK, next step. How about fixing any broken dependencies and configuring any unconfigured packages.
```
sudo apt-get install -f
sudo dpkg --configure -a
```

Better results?

---

### Post by daniel.lawler on 2017-09-22
What's actually pretty interesting, is I noted that the grub splash wasn't actually for 4.4.0-96-generic, but for 4.4.0-93-generic and the previous kernel.

So I removed the previous 4.4.0-93 kernel via apt-get purge, and installed linux-generic for 4.4.0-96-generic.

What I'm currently running into is that GRUB does not seem to be updating any of it's configuration at boot. 

I've run update-grub and also made backups of /boot/grub/grub.cfg and remade the config via grub-mkconfig. I can even cat the file and validate that the 4.4.0-96-generic kernel is listed. However at boot, I'm presented with this:



For some reason I cannot figure out why, but GRUB is not updating. Again, I'm mildly safe as I can boot into 3.13.0-129-generic.

---

### Post by darkod on 2017-09-22
Hmmm, if only grub is confused, it should be quite safe to uninstall it and reinstall it on a booted system. There is slight danger if it doesn't install correctly, but that rarely happens. If you want to try, you first purge it and then install it again recreating new config.
```
sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc   (it installs all related packages)
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda   (install it to the correct drive where you want it)
```

Something like that should get grub going again. It should detect all present kernels and create new, good config.

---

### Post by daniel.lawler on 2017-09-22
Yup. While really not wanting to, I just gave in and reinstalled grub. 

worked like a charm. Thanks!

---

