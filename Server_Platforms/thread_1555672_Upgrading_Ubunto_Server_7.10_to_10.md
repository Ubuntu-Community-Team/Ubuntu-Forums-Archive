---
title: "Upgrading Ubunto Server 7.10 to 10"
date: 2010-08-18
forum: Server Platforms
---

### Post by faster4233 on 2010-08-18
Hi,

We have an Old 7.10 server which i want to upgrade to 10 but i cant work out how to do it, or if its still possible.

I ran this:

**sudo apt-get install update-manager-core ** (Which says its up to date)

and then

**sudo do-release-upgrade**

which i found here:

[https://help.ubuntu.com/community/HardyUpgrades#Network Upgrade from 7.10 for Ubuntu Servers (Recommended)]("https://help.ubuntu.com/community/HardyUpgrades#Network Upgrade from 7.10 for Ubuntu Servers (Recommended)")


But all it comes back with is:

No new release found.

From what i gather i need to go to 8 before i can go to 10.  Does anyone have any idea what im doing wrong?

Thanks very much

---

### Post by stlsaint on 2010-08-18
Yes you will have to go to 8.04 then you can jump to 10.04. 
See notes here: [Upgrade]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade")

Also see here on [7.10 upgrade]("https://help.ubuntu.com/community/UpgradeNotes#From%207.10%20or%206.06%20LTS%20to%208.04%20LTS")

---

### Post by faster4233 on 2010-08-18
Hi,

Thanks for the reply, i literally just worked out what went wrong.  I had to recover the server on our VMware infrastructure and i now have a Ghost Ethernet controller (eth0), and a new one which was un configured (eth1).

Basically i didn't have Internet access.  Doh!

If anyone knows how to remove Ghost Ethernet cards that would be handy though.

Thanks

---

### Post by arrrghhh on 2010-08-18
> **faster4233 said:**
> If anyone knows how to remove Ghost Ethernet cards that would be handy though.

Check your /etc/udev/rules.d/70-persistent-net.rules file.

---

