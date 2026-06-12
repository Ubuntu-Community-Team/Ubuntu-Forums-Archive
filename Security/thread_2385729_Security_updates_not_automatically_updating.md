---
title: "Security updates not automatically updating"
date: 2018-02-23
forum: Security
---

### Post by cam17 on 2018-02-23
I have Ubuntu desktop 16.4.03 LTS and my software & updates is set to automatically update and install security updates. I perform the sudo apt-get update and apt-get dist-upgrade to update my system. When I SSH into my workstations sometimes I see the following security updates which I though would install automatically.

Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.13.0-36-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

0 packages can be updated.
4 updates are security updates.

 My "software & updates" the "update" tab is configured for "When there are security updated" download and install automatically.

Why is the security updates not automatically installing?

---

### Post by ubname on 2018-02-24
You may run

```

apt list --upgradable
```

to see what they are, maybe they are proposed and eventually will make their way to the system.

---

### Post by tinylagarto on 2018-02-24
There is also one more option for other updates that you have to apply manually or via the update manager. You can also find it in the software updates and sources GUI.

---

### Post by deadflowr on 2018-02-24
That's quite an unusual update message.
So you have zero updates, but also four for security?
I'm not sure I've seen a message like that.
I do see messages were the security packages updates are a part of all package updates.
But not sure if I've ever seen it where it tells you no updates and then also tells you there are some updates.
Then again maybe I need to pay more attention to my updates messages sometimes.

As posted apt list --upgradable will tell you what those 4 are, maybe.
Probably moot at this point though. Not sure if the OP simply installed them or waited it out.
Could also be those updates came in after the last time the auto-updater ran, in which case they might have gotten updated later.

---

### Post by cam17 on 2018-02-24
I have already updated using the standard apt-get update and apt-get dist-upgrade. I will check the updates next time as something is indeed sttrange. I noticed at one point updates where pending but SSH showed no updates pending. Thanks ubname for the command.

I did notice that on another Ubuntu Desktop that Ubuntu software updater appears automatically to notify me of updates even though I am using SSH I have never noticed the software updater before.

---

### Post by tinylagarto on 2018-02-25
Not sure how you configured your system and if you use that as a server or desktop but you could post the exact output of apt doing the updates.

If I remember correctly this message on your machine:

```
* Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

0 packages can be updated.
4 updates are security updates.
```

would be the output from unattended upgrades from a terminal. At least on one of my Debian servers where I do not have a GUI but unattended upgrades installed. 
That means that you applied all the updates but some are still pending that you have to do manually. I think you cannot have all updates applied without user intervention or at least you have to configure it properly.

I am just guessing because on Debian I occasionally execute the update commands from apt and I do not use SSH but on Ubuntu I let it do its job without opening the terminal but I will still see some updates (via a GUI) that I have to confirm the updates. 

Maybe this link can clarify:

[https://wiki.debian.org/UnattendedUpgrades](https://wiki.debian.org/UnattendedUpgrades)

---

### Post by cam17 on 2018-03-05
A example of the security updates failing to perform the automatic update and install of the security updates.

Security update not automatically updating

```
apt list --upgradable
Listing... Done
bamfdaemon/xenial-updates 0.5.3~bzr0+16.04.20180209-0ubuntu1 amd64 [upgradable from: 0.5.3~bzr0+16.04.20160824-0ubuntu1]
fwupd/xenial-updates 0.8.3-0ubuntu2 amd64 [upgradable from: 0.7.0-0ubuntu4.3]
gnome-accessibility-themes/xenial-updates,xenial-updates 3.18.0-2ubuntu2 all [upgradable from: 3.18.0-2ubuntu1]
isc-dhcp-client/xenial-updates,xenial-security 4.3.3-5ubuntu12.9 amd64 [upgradable from: 4.3.3-5ubuntu12.7]
isc-dhcp-common/xenial-updates,xenial-security 4.3.3-5ubuntu12.9 amd64 [upgradable from: 4.3.3-5ubuntu12.7]
libbamf3-2/xenial-updates 0.5.3~bzr0+16.04.20180209-0ubuntu1 amd64 [upgradable from: 0.5.3~bzr0+16.04.20160824-0ubuntu1]
libdfu1/xenial-updates 0.8.3-0ubuntu2 amd64 [upgradable from: 0.7.0-0ubuntu4.3]
libfwupd1/xenial-updates 0.8.3-0ubuntu2 amd64 [upgradable from: 0.7.0-0ubuntu4.3]
libsnmp-base/xenial-updates,xenial-updates 5.7.3+dfsg-1ubuntu4.1 all [upgradable from: 5.7.3+dfsg-1ubuntu4]
libsnmp30/xenial-updates 5.7.3+dfsg-1ubuntu4.1 amd64 [upgradable from: 5.7.3+dfsg-1ubuntu4]
linux-firmware/xenial-updates,xenial-updates 1.157.17 all [upgradable from: 1.157.16]
sensible-utils/xenial-updates,xenial-updates,xenial-security,xenial-security 0.0.9ubuntu0.16.04.1 all [upgradable from: 0.0.9]
ubuntu-drivers-common/xenial-updates,xenial-security 1:0.4.17.7 amd64 [upgradable from: 1:0.4.17.6]
```

---

### Post by tinylagarto on 2018-03-05
Can you post the exact output of:

```
 
sudo apt update
```

followed by:

```
sudo apt dist-upgrade
```

in [CODE] tags. 

I mean you should be able to update your system regardless if there is nothing wrong.

---

### Post by deadflowr on 2018-03-05
What do the files
```
/etc/apt/apt.conf.d/10periodic
and
/etc/apt/apt.conf.d/20auto-upgrades
```
show.
It might be that the auto updater is set to download only.

---

### Post by cam17 on 2018-03-08
10periodic shows
cat 10periodic
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";


and 20auto-upgrades shows
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

---

### Post by cam17 on 2018-03-15
The Ubuntu desktop GUI is set to install security updates but it is not being performed. is this a known bug? ](*,)

---

### Post by cam17 on 2018-03-21
I am still getting updates for security pending for update instead of automatically installing. The GUI is configured to update security packages automatically.

Is there a problem with the GUI? below is the update pending for March-21-2018

Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.13.0-37-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

6 packages can be updated.
1 update is a security update.

apt list --upgradable
Listing... Done
apt/xenial-updates 1.2.26 amd64 [upgradable from: 1.2.25]
apt-transport-https/xenial-updates 1.2.26 amd64 [upgradable from: 1.2.25]
apt-utils/xenial-updates 1.2.26 amd64 [upgradable from: 1.2.25]
libapt-inst2.0/xenial-updates 1.2.26 amd64 [upgradable from: 1.2.25]
libapt-pkg5.0/xenial-updates 1.2.26 amd64 [upgradable from: 1.2.25]
libpam-systemd/xenial-updates 229-4ubuntu21.2 amd64 [upgradable from: 229-4ubuntu21.1]
libsystemd0/xenial-updates 229-4ubuntu21.2 amd64 [upgradable from: 229-4ubuntu21.1]
libtiff5/xenial-updates,xenial-security 4.0.6-1ubuntu0.3 amd64 [upgradable from: 4.0.6-1ubuntu0.2]
libudev1/xenial-updates 229-4ubuntu21.2 amd64 [upgradable from: 229-4ubuntu21.1]
systemd/xenial-updates 229-4ubuntu21.2 amd64 [upgradable from: 229-4ubuntu21.1]
systemd-sysv/xenial-updates 229-4ubuntu21.2 amd64 [upgradable from: 229-4ubuntu21.1]
udev/xenial-updates 229-4ubuntu21.2 amd64 [upgradable from: 229-4ubuntu21.1]

---

