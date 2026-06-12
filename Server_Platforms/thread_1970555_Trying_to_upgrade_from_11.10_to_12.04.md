---
title: "Trying to upgrade from 11.10 to 12.04"
date: 2012-05-01
forum: Server Platforms
---

### Post by Pacane on 2012-05-01
When I logged in on my Ubuntu server I got the "new version available message", so I chose to upgrade. The process went fine and then I rebooted.

However, after the reboot, I still have the message about the "new version available". When I type do-release-upgrade (-d) it tells me there's no new version available.

Now, when I look at uname -r, I thought it should be something like 3.xxxx but I'm still at 2.6.39.1-x86_64

When I do:

lsb_release -a                                                [11:40:17]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric
But when I do a sudo apt-get update it checks the sources on "precise" instead of "oneirc"

Did the upgrade go fine, or I'm still missing something?

And yes, I tried sudo apt-get update and upgrade.

Thanks.

---

### Post by jerrrys on 2012-05-01
A long shot, but maybe your mirror has yet to update.  Try another one.

And that (-d) wont work, just:

do-release-upgrade

---

### Post by Pacane on 2012-05-01
Yeah well the (-d) meant that I tried with and without -d... Maybe it wasnt explicit enough :P

---

### Post by jerrrys on 2012-05-01
> **Pacane said:**
> Yeah well the (-d) meant that I tried with and without -d... Maybe it wasnt explicit enough :P

Actually I was not explicit enough; -d don't work.  Or don't think you will get offered 12.10 yet:)

---

### Post by Pacane on 2012-05-01
Well, here's the output:

```
sudo do-release-upgrade                                                                                                                                                                              [15:46:32]
Checking for a new Ubuntu release
No new release found

```

---

### Post by jerrrys on 2012-05-01
You have looked at your sources.list and its all precise?

That kernel looks like a leftover from several upgrades ago.

Maybe you should try doing a full upgrade.

sudo apt-get dist-upgrade

But as you know Im sure, kernel upgrades can break things.

---

### Post by Pacane on 2012-05-01
Well I tried that too, here's the output : 


```
o bin -> sudo apt-get dist-upgrade                                                                         [23:18:43]
[sudo] password for joel:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-dbg libboost-dev libboost-iostreams-dev libboost-python-dev libboost-serialization-dev libboost-test-dev
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

---

