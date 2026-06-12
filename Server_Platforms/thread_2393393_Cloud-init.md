---
title: "Cloud-init?"
date: 2018-06-02
forum: Server Platforms
---

### Post by DigiAngel on 2018-06-02
With a brand new fresh 18 server installed from the live iso I'm about to config the network.  My /etc/network/interfaces shows:

```
# ifupdown has been replaced by netplan(5) on this system.  See
# /etc/netplan for current configuration.
# To re-enable ifupdown on this system, you can run:
#    sudo apt install ifupdown

```

.....ok.  I see that I can reinstall ifupdown, but hey...let's go with what's installed be default ya?  So going to /etc/netplan I see one file, 50-cloud-init.yaml which contains:

```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp0s31f6:
            addresses: []
            dhcp4: true
            optional: true
    version: 2

```

So uh.....where/how do you configure cloud-init?  Going to [https://help.ubuntu.com/lts/serverguide/network-configuration.html.en]("https://help.ubuntu.com/lts/serverguide/network-configuration.html.en") there's no mention of cloud-init at all.  Why isn't this mentioned on the official docs page?  Thank you.

---

### Post by LHammonds on 2018-06-03
There are two different installers for server now.  The default "live" ISO is completely new and designed to mimic how the desktop is installed (from my understanding).  The "alternative" ISO is how prior versions of server was installed which also gives you the ability to configure the hard drives how you need (LVM/RAID).  But there are more differences between just having a different way to install...you also get a different end-result and I [started a thread]("https://ubuntuforums.org/showthread.php?t=2390785") to for people to discuss the differences found (however I will not use the "live" version since it is useless to me).

When using the "alternative" ISO to install, there is not a 50-cloud-init.yaml file in netplan.  Instead, there is a 01-netcfg.yaml and I [documented how to setup a static IP](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p616) in case you are interested.

LHammonds

---

### Post by DigiAngel on 2018-06-04
Appreciate that...a difference you can add to that discussion is the fact that cloud-init package isn't installed with the alternative iso.

---

