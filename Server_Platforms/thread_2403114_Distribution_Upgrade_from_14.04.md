---
title: "Distribution Upgrade from 14.04"
date: 2018-10-07
forum: Server Platforms
---

### Post by mattlach on 2018-10-07
Hey all,

I'm currently having a little bit of an odd problem.

I have some time on my hands this week, so I thought it might be time to upgrade a bunch of my old 14.04 servers.

update-manager-core is installed.

The config file looks good:

```

~$ cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=lts
```

I have all the latest packages installed, and I'm on the latest point release:

```

~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
```

Yet still, when I try to execute the distribution upgrade, it doesn't find any updates:

```
~$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found
```

At first I thought this might be because the latest point release of 18.04 is not yet available, but even so, at least there should be a 16.04 release available, right?

Is it relevant that this is running inside an LXC container?

Does anyone know what is going on, or have any suggestions I might try?

Much obliged,
Matt

---

### Post by PaulW2U on 2018-10-07
> **mattlach said:**
> Does anyone know what is going on, or have any suggestions I might try?
Try without the -d switch which would upgrade you to the current development release (18.10) from the latest supported release (18.04).

---

### Post by Bashing-om on 2018-10-07
mattlach; Hello :

" sudo do-release-upgrade -d" : the 'd' is for development version.
How about trying as:
```

sudo do-release-upgrade

```
which I expect to bring you to 16.04. then make sure 16.04 is fully updated and repeat the "sudo do-release-upgrade" to bring you to 18.04.

Be aware there are a lot of changes in 18.04 , particularly in systemd and networking (netplan).
[https://netplan.io/](https://netplan.io/)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mattlach on 2018-10-07
> **Bashing-om said:**
> mattlach; Hello :

" sudo do-release-upgrade -d" : the 'd' is for development version.
How about trying as:
```

sudo do-release-upgrade

```
which I expect to bring you to 16.04. then make sure 16.04 is fully updated and repeat the "sudo do-release-upgrade" to bring you to 18.04.

Be aware there are a lot of changes in 18.04 , particularly in systemd and networking (netplan).
[https://netplan.io/](https://netplan.io/)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

Ugh.  I don't understand why everyone hates on and wants to replace ifup/down.

I love configuring everything in my simple /etc/network/interfaces file.

What could possibly be better?  Why can't they just stop changing things for the sake of changing them :(

Maybe I'll have to switch to Debian for my servers if Ubuntu is getting rid of ifupdown.

---

### Post by Bashing-om on 2018-10-07
mattlach; Well,

Me, I was real partial to 10.04 - did not want the change to upstart :)

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

[INDENT]'buntu - a fast moving target
[/INDENT]

---

### Post by mattlach on 2018-10-07
> **Bashing-om said:**
> mattlach; Well,

Me, I was real partial to 10.04 - did not want the change to upstart :)

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

[INDENT]'buntu - a fast moving target
[/INDENT]

I didn't like that change either at first.  I miss my eth0.  Nice and clean

I changed my mind after my debian based KVM server imploded, and I had to manually reassign all the Ethernet device names from mac addresses in /etc/udev/rules.d/70-persistent-net.rules to fix everything, made worse by the fact that I had to do it from local console without any copy/paste....
I do 
So, while I miss my eth0/eth1/eth2, etc, I understand that change.   This one, and the move to systemd-resolved I do not understand at all.   It appears to me like replacing something simple and effective, with something else with way too much abstraction and over-complication.

One of the things I love about Linux is the simplicity of its text file configuration.   With things like Gnome's network-manager it feels like they are trying to turn the whole thing into Windows...   There is a reason I don't use Windows...

---

### Post by Bashing-om on 2018-10-07
mattlach; Hey ..

We are drifting too far from the topic of this thread . We can continue in Linux and OS Chat sub-forum.

For now I will end with an agreement of KISS. All I can think of is the movement to support mobile and cloud initiatives. Desktop days are ending :(

[INDENT][INDENT]The times they are a-change'n
[/INDENT][/INDENT]

---

