---
title: "When to reboot server after update/upgrade?"
date: 2009-10-07
forum: Server Platforms
---

### Post by SoundFriend on 2009-10-07
Hi,

After I update the Jaunty server (headless) using apt-get update and apt-get upgrade, how do I know whether a reboot is required - is it only after a new kernel version is to be installed?  

A message to this effect would be useful :)

John

---

### Post by dragos2 on 2009-10-07
If it says "x not upgraded" then you need a reboot but before
dist-upgrade.

---

### Post by SoundFriend on 2009-10-07
Hi Dragos, what do you mean 'but before dist-upgrade' ?

John

---

### Post by shaggy999 on 2009-10-07
I think what dragos meant is that if you do a "sudo apt-get upgrade" and afterwards it says "the following packages were not upgraded" it means there are packages that still need updating that will necessitate running "sudo apt-get dist-upgrade" followed by a reboot.

However, I don't think it's that simple. If you get an update of apache, for example, your system does not need to be rebooted but apache will continue to run as the old version until you restart that service. Now, if you're upgrading apache it should automatically restart apache but I know there are situations where you need to restart programs & services to get the benefits of updates but you will not be notified.

---

### Post by cariboo on 2009-10-08
The only time I reboot my server is when I have to shut it off to physically work on it eg: If I add or remove hardware. My server is a inward facing server with nothing open to the internet.

Usually the only time you should need to reboot is if there is a new kernel, as all services can be stopped and restarted without having to reboot.

In a lot of cases, the service is stopped and restarted while doing the update, so there is no need to reboot.

---

### Post by SoundFriend on 2009-10-08
> **shaggy999 said:**
> I think what dragos meant is that if you do a "sudo apt-get upgrade" and afterwards it says "the following packages were not upgraded" it means there are packages that still need updating that will necessitate running "sudo apt-get dist-upgrade" followed by a reboot.

Thanks, I am sorry to say I have never used apt-get dist-upgrade, until now. It offered to install a new kernel that was withheld when using just apt-get upgrade. Interesting, you learn something all the time :)


John

---

### Post by scorp123 on 2009-10-09
> **dragos2 said:**
> If it says "x not upgraded" then you need a reboot The only time you need to reboot a Linux system is if the kernel is being upgraded. That's it.

Besides: Ubuntu 9.04 server will tell you if needs a reboot. Simply login via SSH and then pay a close look at the messages that fly over the terminal. If the server needs a reboot it will clearly say:

**"* * *  System needs to be restarted * * *"**

I saw this yesterday when I installed a Ubuntu 9.04 server. After "apt-get dist-upgrade" which downloaded the 2.6.28-15 kernel my next SSH login had this message in the terminal.

---

### Post by slakkie on 2009-10-09
Kernel upgrades, libc6 upgrades and network-manager upgrades often require a reboot. All other packages usually don't require a reboot, just a simple restart command (which is often performed by the upgrade process itself).

---

### Post by dragos2 on 2009-10-09
> **scorp123 said:**
> The only time you need to reboot a Linux system is if the kernel is being upgraded. That's it.

Besides: Ubuntu 9.04 server will tell you if needs a reboot. Simply login via SSH and then pay a close look at the messages that fly over the terminal. If the server needs a reboot it will clearly say:

**"* * *  System needs to be restarted * * *"**

I saw this yesterday when I installed a Ubuntu 9.04 server. After "apt-get dist-upgrade" which downloaded the 2.6.28-15 kernel my next SSH login had this message in the terminal.

I never saw the "x not upgraded" message unless there were kernel upgrades, so
my statemet is consistent as long as I don't know the particular case :)

---

