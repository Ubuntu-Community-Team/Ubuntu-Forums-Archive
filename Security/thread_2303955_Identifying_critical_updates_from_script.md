---
title: "Identifying critical updates from script"
date: 2015-11-23
forum: Security
---

### Post by 9-launchpad-l on 2015-11-23
Hi all,

I manage several Ubuntu servers and have monitoring on all these servers as well. As part of the monitoring, I have a plugin checking for pending upgrades.
The plugin currently distinguishes between security upgrades and 'normal' upgrades based on the repository (e.g.: trusty-security).

When I log in to a server my motd shows I have pending security upgrades that aren't found by my plugin. Having looked around a bit, I found the script /usr/lib/update-notifier/apt-check.
In this script, a method isSecurityUpgrade seems to check multiple parameters to determine if an upgrade is a security upgrade.

Right now I have a bash script that parses the output of apt-get -s dist-upgrade -y to identify the pending upgrades and their originating repository.

I'm happy to rewrite my script in Python if this makes for easier  integration, however I'm not that familiar with Python or the packaging  system internals.

How should I best integrate the logic of the apt-check script in my plugin?

Regards, Paul

---

### Post by fugu2 on 2015-12-10
I'm not sure if this identifies if the update is critical or not, but you can use the "simulate" feature with an apt-get upgrade and maybe get the info you need. ```
$ apt-get upgrade --simulate -y | grep '^Inst ' | awk '{ print $2 }'
``` This will display the package name for everything that would be upgraded

---

### Post by ian-weisser on 2015-12-10
> **9-launchpad-l said:**
> When I log in to a server my motd shows I have pending security upgrades that aren't found by my plugin.
I consider motd to be a reminder to do regular updates, but not a reliable list of what needs to be updated.

Cron/anacron updates the apt package database and motd daily (or soon after  boot), so the accuracy of motd depends upon when before/after  that update you login.

motd does NOT check the network for updates at boot or login, as that would significantly delay login - in some cases by minutes. A delay of that magnitude is unacceptable for a two-line login notification, so motd instead uses the last known package updates...which might be from yesterday or perhaps last week. Rather stale.

Only you can decide what a 'Critical' update is. I think your criteria of "Source = Security Repo" is well considered and wise.

---

### Post by 9-launchpad-l on 2015-12-11
> **fugu2 said:**
> I'm not sure if this identifies if the update is critical or not, but you can use the "simulate" feature with an apt-get upgrade and maybe get the info you need. ```
$ apt-get upgrade --simulate -y | grep '^Inst ' | awk '{ print $2 }'
``` This will display the package name for everything that would be upgraded

My current solution determines updates with this command: 
```
# /usr/bin/apt-get -o Debug::NoLocking=yes -s dist-upgrade -y |awk '/^Inst/ { print $2 " " $5}'
```

This works for identifying security updates *if* they are provided through the <dist>-Security channel ($5 prints the channel, for example: Ubuntu:12.04/precise-updates)


> **ian-weisser said:**
> I consider motd to be a reminder to do  regular updates, but not a reliable list of what needs to be updated.

I totally get what you're saying. Perhaps I didn't phrase my question the right way.

I currently use apt-get dist-upgrade (see above) to determine what packages should be upgraded. For a random server, this currently lists that 375 packages are pending an upgrade. Applying the rule with the filter for security channel shows that there are no security upgrades pending.
When I look at the output of the motd however, is lists that 300 (of 350) packages are security updates. For that reason, I'm thinking that just checking for the update channel is insufficient.

Because of this, I'm looking for a way to apply the logic of the apt-check script on every pending upgrade I find through apt-get dist-upgrade.

---

