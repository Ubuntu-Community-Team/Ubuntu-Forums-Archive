---
title: "Phased updates and multiple desktop type systems"
date: 2022-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by &amp;KyT$0P# on 2022-08-31
Is anyone else administering multiple systems that you would like to have receive exactly the same set of phased updates?

I do, and I use the [official recommended method]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345") -
> To have all your machines phase the same, set the [FONT=Courier New]APT::Machine-ID[/FONT] option to a UUID like /etc/machine-id (the format is not being checked right now, but that might change);

But it means I can't use Software Updater, because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1979238").

If anyone else can confirm that bug, it would be appreciated if you would please mark it as affecting you too :KS

While waiting for that bug to be fixed, has anyone found a more convenient workaround than [FONT=Courier New]sudo apt-get update && sudo apt-get dist-upgrade[/FONT] ?

I don't necessarily need a GUI for updating, but I would prefer a nicer listing than given by [FONT=Courier New]apt-get dist-upgrade[/FONT], and to not have to type my sudo password until actually accepting to perform the upgrade.  I did find [FONT=Courier New]aptdcon[/FONT] and can avoid typing my sudo password for [FONT=Courier New]apt-get update[/FONT] by running
```
aptdcon --refresh
```
But I couldn't find a way to list the packages to be upgraded in a nice format.  The output format of [FONT=Courier New]apt list --upgradable[/FONT] would be perfect, but that command is not a solution, because it no longer takes phased updates into account.

Thanks for any help :)

---

### Post by ajgreeny on 2022-08-31
I found out yesterday that updating packages by using synaptic seems to bypass the phased upgrades system.
The package ubuntu-advantage-tools did not upgrade using **apt upgrade** but immediately using synaptic to see what happened, it upgraded with no difficulty.

I can't promise this is always the case but it was at that specific moment so may be worth investigating further.

---

### Post by &amp;KyT$0P# on 2022-09-07
> **ajgreeny said:**
> I found out yesterday that updating packages by using synaptic seems to bypass the phased upgrades system.
The package ubuntu-advantage-tools did not upgrade using **apt upgrade** but immediately using synaptic to see what happened, it upgraded with no difficulty.

How did you do the upgrade with Synaptic?  I was unable to reproduce this behavior using the "Mark all upgrades" button, it does not mark for upgrade the phased update of dmidecode that my system is not yet phased into.

---

### Post by ajgreeny on 2022-09-07
I'm sorry but I now think I spoke too soon with my last post and the phased upgrades are not bypassed in synaptic; I must have just used it at the very moment that the package moved out from being phased and became available.

I have now found, as you did, that synaptic also will not upgrade the phased packages, so apologies for my mistake.

---

### Post by &amp;KyT$0P# on 2022-09-27
Just noticed another phased update related discrepancy between Software Updater and apt.  If a phased update that my system is not yet phased into has new dependencies, Software Updater (and Synaptic too) will install those dependencies *even though the package they're for is not slated to be installed*.

apt behaves as expected: does not even offer to install the dependency.

Currently there is a systemd phased update, phased at 0% as of this writing, that has a new dependency [FONT=Courier New]systemd-hwe-hwdb[/FONT] .  After fully updating my system with apt, if I run Software Updater it offers to install [FONT=Courier New]systemd-hwe-hwdb[/FONT] as the only update listed.

Same if I open Synaptic and select "Mark all upgrades": what it actually wants to mark is *only* to install [FONT=Courier New]systemd-hwe-hwdb[/FONT] , no other changes.

Is this behavior of Software Updater and Synaptic intentional?

* Update: it was [filed as a bug]("https://bugs.launchpad.net/ubuntu/+bug/1991139").

---

### Post by &amp;KyT$0P# on 2022-10-19
Initial testing indicates the following gets Software Updater to just use apt's phased updates implementation -

[FONT=Courier New]/etc/apt/apt.conf.d/90update-manager-use-apt-phasing[/FONT]
```
Update-Manager {
  Always-Include-Phased-Updates true;
}
APT {
  Get {
    Always-Include-Phased-Updates false;
  }
}
```

---

### Post by ajgreeny on 2022-10-19
> **halogen2 said:**
> Initial testing indicates the following gets Software Updater to just use apt's phased updates implementation -

[FONT=Courier New]/etc/apt/apt.conf.d/90update-manager-use-apt-phasing[/FONT]
```
Update-Manager {
  Always-Include-Phased-Updates true;
}
APT {
  Get {
    Always-Include-Phased-Updates false;
  }
}
```
I believe that file, if present, allows updating by any means, not just software-updater to ignore the phased updates system and all packages to be updated.
Is that actually a package? It's not in the repos and I always use the terminal.

However, the more I read about this phased update system, the more I intend to keep using it as and when the packages really arrive.

---

### Post by &amp;KyT$0P# on 2022-10-19
> **ajgreeny said:**
> I believe that file, if present, allows updating by any means, not just software-updater to ignore the phased updates system and all packages to be updated.

On my systems, it only turns off Software Updater's phased updates implementation, while keeping apt's phased updates enabled -
```
$ cat /etc/apt/apt.conf.d/90update-manager-use-apt-phasing 
Update-Manager {
  Always-Include-Phased-Updates true;
}
APT {
  Get {
    Always-Include-Phased-Updates false;
  }
}
$ apt-get -s dist-upgrade
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libpulse-mainloop-glib0 libpulse0 libpulsedsp pulseaudio-utils sudo
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
$ apt-cache policy sudo
sudo:
  Installed: 1.9.9-1ubuntu2
  Candidate: 1.9.9-1ubuntu2.1
  Version table:
     1.9.9-1ubuntu2.1 500 (phased 20%)
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
 *** 1.9.9-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

It does make all updates visible in Software Updater, but the ones that are not yet phased in are un-checked.

> Is that actually a package? It's not in the repos and I always use the terminal.

Sorry, I'm not clear what you're asking about?  If Software Updater, [installing Software Updater requires two packages]("https://ubuntuforums.org/showthread.php?t=2478588&p=14110358&viewfull=1#post14110358").

---

