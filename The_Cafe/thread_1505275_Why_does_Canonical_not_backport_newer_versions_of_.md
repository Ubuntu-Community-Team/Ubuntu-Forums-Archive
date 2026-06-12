---
title: "Why does Canonical not backport newer versions of linux-restricted-modules?"
date: 2010-06-08
forum: The Cafe
---

### Post by Shining Arcanine on 2010-06-08
I am doing some undergraduate work in a professor's lab over the summer and I had a meeting with him and his graduate students today. One of them is writing a kernel module. He told me that doing kernel development on kernel versions newer than 2.6.32 is not possible for him because of driver issues. I asked about the issues he mentioned and apparently, the latest version of nvidia's drivers available for his system are too old to support anything newer than 2.6.32 without patching and recompiling the Kernel Compatiblity Layer and packages for more recent drivers that support kernels newer than 2.6.33 are not available from Canonical.

I believe he is running Ubuntu Linux 9.10 and I assume that he cannot upgrade his system to Ubuntu Linux 10.04 because of the down-time dealing with the inevitable breakage would cause, so I spent an hour or two trying to figure out how to backport newer/patched drivers to his version of Ubuntu and sent instructions to him via an email.

Why does Canonical not backport newer versions of linux-restricted-modules to older versions of Ubuntu? Failing to backport newer versions of linux-restricted-modules to older versions of Ubuntu makes kernel development harder because every time a new kernel version is released that breaks binary compatibility with drivers designed for previous versions, people need to dig around for ways to install new/patched drivers not available in the Canonical's repositories. Also, while some would say that "kernel developers should upgrade", that idea is fine until a major system upgrade goes horribly wrong, forcing people to spend exorbitant amounts of time fixing the damage.

---

### Post by cariboo on 2010-06-09
For most people, the upgrade to Lucid went pretty well. To do a successful upgrade, you just have to take your time. Make sure all packages installed from a ppa are removed, and the ppa's are disabled. Then make sure the system is completely up-to-date. Once the system is up-to-date, you can then start the upgrade process. One of the biggest problems I've seen is that people are rebooting before making sure that the upgrade has completed. I usually open a terminal and type:

```
sudo apt-get -f install
```

then:

```
sudo aptitude-update && sudo aptitude safe-upgrade
```

just to make sure the upgrade has finished, then I reboot.

I have an HP laptop that has been upgraded from Hardy to Lucid without a hint of a problem using the above method.

There is nothing to stop your guy from using a newer kernel with the version he's using now, have a look at this [wiki]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") page.

To answer your question about Ubuntu backporting restricted modules, Once a version is released, the only updates are for security. With a 6 month release cycle, there really isn't a need to backport the drivers.

---

