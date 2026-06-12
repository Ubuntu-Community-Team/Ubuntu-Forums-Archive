---
title: "Why &quot;*** System restart required ***&quot;"
date: 2013-03-13
forum: Server Platforms
---

### Post by wlraider70 on 2013-03-13
My 12.04 server seems to always say *** System restart required ***
So Last week, I updated and restarted. I stayed logged off for a week, it was in use though.

Now *** System restart required ***. Is there a log to tell me why the server needs to restart?
edit: I have NOT installed or updated anything

---

### Post by papibe on 2013-03-13
Hi wlraider70.

That message usually appears after an important update, like a security update, or a kernel update.

Did you set your server with automatic updates?

Regards.

---

### Post by wlraider70 on 2013-03-13
I'm not sure about auto updates, I don't recall any such option. 
I manually use apt-get and I do get prompts like...

13 packages can be updated.
0 updates are security updates.

The reason I left it alone for a week was to make sure i didn't install any updates, but if there is an auto feature that would invalidate my test.

---

### Post by papibe on 2013-03-13
Let's make sure. Could you post the result of these commands?
```
apt-cache policy unattended-upgrades

cat /etc/apt/apt.conf.d/10periodic 

cat /etc/apt/apt.conf.d/50unattended-upgrades
```
Regards.

---

### Post by wlraider70 on 2013-03-13
```


server@philo:~$ apt-cache policy unattended-upgrades
unattended-upgrades:
  Installed: 0.76ubuntu1
  Candidate: 0.76ubuntu1
  Version table:
 *** 0.76ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     0.76 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

```

server@philo:~$ cat /etc/apt/apt.conf.d/10periodic
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";

```

```

server@philo:~$ cat /etc/apt/apt.conf.d/50unattended-upgrades
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";

// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed.
//Unattended-Upgrade::Mail "root@localhost";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION* if a
// the file /var/run/reboot-required is found after the upgrade
//Unattended-Upgrade::Automatic-Reboot "false";


// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";
server@philo:~$


```




Am I reading the 4th line of the last group that I am allowing security packages to auto-update?

---

### Post by papibe on 2013-03-13
You seem to **NOT** be using auto updates.

My guess would be that the last time you upgraded, you didn't realize you needed to restart.

After big updates, I usually disconnect and log again to check if there's a message recommending restart.

Regards.

---

### Post by wlraider70 on 2013-03-13
I'm pretty sure that's not it. 
That was my first thought, so I was quite careful to make sure last time.

---

### Post by thnewguy on 2013-03-13
The system will recommend a restart any time a major or kernel update is installed. The message saying a system restart is required just means one (or more) of those updates won't take effect until you reboot the machine. If none of the updates you applied are urgent fixes (eg a security flaw in the kernel) then you can just leave it. Quite often updates come down the pipe which will recommend a restart, but I often wait until something important gets upgraded before I'll perform the actual update.

---

### Post by wlraider70 on 2013-03-13
I haven't installed or updated since my last reboot.

---

### Post by thnewguy on 2013-03-13
It could be a cached message then. The update notification messages aren't real time, they are generated periodically. You may just be looking at a message which was relevant prior to your last reboot.

---

### Post by wlraider70 on 2013-03-25
I'm considering the cached message explanation. So here is a login from today.
I won't update or install anything for a few weeks.



Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-39-generic-pae i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Mon Mar 25 19:46:49 EDT 2013

  System load:  0.0               Processes:           89
  Usage of /:   7.3% of 72.63GB   Users logged in:     0
  Memory usage: 13%               IP address for eth0: 10.10.10.2
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Last login: Mon Mar 25 19:29:54 2013 from cryo.local
server@philo:~$

---

### Post by Vegan on 2013-03-25
I use Linux in virtual machines all the time and I always enable automatic updates. So far its not been a problem. I simply create a new VM when a new CD surfaces.

Its safer to enable automatic updates.

---

### Post by CharlesA on 2013-03-25
> **Vegan said:**
> I use Linux in virtual machines all the time and I always enable automatic updates. So far its not been a problem. I simply create a new VM when a new CD surfaces.

Its safer to enable automatic updates.

+1.

I've got unattended-upgrades set up on both my home server and my VPS. I am also running apticron on my VPS, so I know what updates are available and a list of what they affect.

---

