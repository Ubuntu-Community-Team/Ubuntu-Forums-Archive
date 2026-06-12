---
title: "Can't install VBox Linux Addons in OpenSUSE+VirtualBox"
date: 2008-02-07
forum: Virtualisation
---

### Post by geo909 on 2008-02-07
Hello everybody.
I am trying to install the VBox Linux Add ons in a virtual box machine with OpenSuse 10.3 installed.

When the machine boots, I go:
"Devices"->"Install guest additions" and the cd is mounted.
OK. There is a shell script in the cd named VBoxLinuxAdditions.run

I do (as root)
```
sh VBoxLinux Additions.run
```

and here's what I get:

[CENTER][IMG][[IMG]http://www.imageshack.gr/files/d1mt5lhnkxad8ltz5l5w.png[/IMG]](http://www.imageshack.gr/view.php?file=d1mt5lhnkxad8ltz5l5w.png)[/IMG][/CENTER]

I need to install the addons in order to have full screen and make OpenSuse usable under VirtualBox...

Does anyone have any ideas, please?

---

### Post by p_quarles on 2008-02-07
Well, I'm not sure about OpenSUSE, but in Ubuntu you would be able to find the kernel header files by searching for linux-header in your package manager. Similarly, the make tools in Ubuntu are in the "build-essential" metapackage, but I don't know what it's called here. 

I would use your package search tool of choice to search for the packages it mentions, but you may have to try different combinations.

---

### Post by dennis333 on 2008-05-05
I've struggeled with this same problem with a Vista host and openSUSE guest on VirtualBox.

After several hours I've found the solution:

On SUSE and OpenSUSE Linux, you must install the right versions of the kernel-source and kernel-syms packages.

You do this by first installing additional repos. I installed all repos found in the Community Sources.

After a reboot type the following commando in a terminal:
sudo zypper install gcc make automake autoconf kernel-source

After that Suse needs a little tweaking. You do this by disabling concurrency for init scripts by changing RUN_PARALLEL=”yes” to “no” in /etc/sysconfig/boot file.

After that (and maybe another reboot) you can build, compile and install the Additions for VirtualBox using the normal command:
sudo sh ./VBoxLinuxAdditions.run


I hope this helps. It worked like a charm for me...!   :KS

---

