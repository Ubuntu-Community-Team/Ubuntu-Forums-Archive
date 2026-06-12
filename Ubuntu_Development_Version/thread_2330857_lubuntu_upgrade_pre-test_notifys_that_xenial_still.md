---
title: "lubuntu upgrade pre-test notifys that xenial still in development"
date: 2016-07-15
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-07-15
I am doing testing on virgin installs from iso lubuntu i386/amd64 14.04.1 to 14.04.4 to xenial and when I go to upgrade to xenial I get the below notification. - and so I will continue upgrade.

---

### Post by ventrical on 2016-07-15
Filed a bug anyways..

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1603576](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1603576)

Regards..

---

### Post by ventrical on 2016-07-16
This also happens on i386  lubuntu when upgrading to xenial.

Also get the same type of verbose messages after grub:

```

dev/sda1/clear orphaned inode... etc..

```


but otherwise a smoother upgrade. I chose not to remove obsoleted packages.
regards..

---

### Post by kansasnoob on 2016-07-19
> **ventrical said:**
> Filed a bug anyways..

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1603576](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1603576)

Regards..

Thank you. Saved me some typing :)

---

### Post by kansasnoob on 2016-07-19
> **ventrical said:**
> This also happens on i386  lubuntu when upgrading to xenial.

Also get the same type of verbose messages after grub:

```

dev/sda1/clear orphaned inode... etc..

```


but otherwise a smoother upgrade. I chose not to remove obsoleted packages.
regards..

Does that happen only on the first boot after upgrade?

---

### Post by ventrical on 2016-07-20
> **kansasnoob said:**
> Does that happen only on the first boot after upgrade?

In successive boots..

```

dev/sda1/clean

```

 etc... it is systemic with many install of wily and xenial of all flavours, many different types of hdds. It works just fine with 14.04.1 install and upgrade to 14.04.4 .. but as soon as I upgrade to xenial it is there. I am assuming it is systemd problem.

 I can virgin install xenial release with no verbose.

regards..

---

### Post by ventrical on 2016-07-20
> **kansasnoob said:**
> Thank you. Saved me some typing :)

I personally do not think that it is stressed enough that these are not 'leave unattended" upgrades. They have to be guided manually through to full reboot. This is serious instructional development bug.

---

### Post by kansasnoob on 2016-07-21
> **ventrical said:**
> I personally do not think that it is stressed enough that these are not 'leave unattended" upgrades. They have to be guided manually through to full reboot. This is serious instructional development bug.

Same basic reasoning is why I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1573250](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1573250)

We shouldn't expect that a user will know that they need to click-n-hold the title bar to drag a window upwards so you can read what it says, and then we shouldn't assume that the user will know to use the tab and enter keys to make a decision, or even know which decision is correct. It's quite possible that a user could assume the upgrade is frozen and just do a hard reset :(

---

### Post by ventrical on 2016-07-22
A week into testing and those bugs do not even have importance assigned.

---

### Post by ventrical on 2016-07-22
ok.. both bugs now getting some attention.

my bad for not posting attachment of screenshot on lp.

---

### Post by ventrical on 2016-07-29
> **ventrical said:**
> Filed a bug anyways..

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1603576](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1603576)

Regards..

This bug is now fixed. If you install a version of Lubuntu Trusty 14.04.1 and then reboot it will automatically notify on logon that the 16.04.1 LTS is available for upgrade. You have to open proposed and update/upgrade to 14.04.4.. other wise it will not work.

Regards..

---

