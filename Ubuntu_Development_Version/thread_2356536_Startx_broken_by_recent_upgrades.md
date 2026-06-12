---
title: "Startx broken by recent upgrades"
date: 2017-03-24
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-03-24
Just post that WARNING as i have no time to investigate right now

Have got about ~ 100 upgrades today, including lightdm/apparmor/systemd; The result, one reboot later, is X does not start neither directly nor via tty.
I have reconfigured lightdm, but that does not solve the problem. Tried also gdm3, but same result.

I'm usually opening a gnome-shell session with a nvidia-378 driver (unique gtx750 card)
Can't find which package(s) has broken X, but apparmor changes is probably faulty.

---

### Post by fthx on 2017-03-24
gdm works at the moment

---

### Post by P-I H on 2017-03-24
This created a lot of work.
Made today's upgrades.
Made some BIOS changes
Booted to black screen. Tried to understand what happend. Decided to reinstall.
The reinstallation went OK. Made today's update. Booted to black screen. 
I think I wait for the upgrade.

---

### Post by jbicha on 2017-03-24
This was my fault. You need unity-settings-daemon [15.04.1+17.04.20170322-0ubuntu1.1           ]("https://launchpad.net/ubuntu/+source/unity-settings-daemon/15.04.1+17.04.20170322-0ubuntu1.1")

---

### Post by dino99 on 2017-03-24
Thanks Jeremy

i've tried to use again that broken ZZ; first X failed again, update/upgrade via tty, reconfigured apparmor/systemd/udev and rebooted.
Result: X start normally that time.

---

### Post by wgarcia on 2017-03-24
I got also the black screen. I had accepted the upgrades, update-manager finished and asked me to reboot, and I went into a black screen with a mouse arrow. I logged in remotedly with ssh, I restarted lightdm, and no joy, still a black screen with the arrow. Then I  "apt update" and  more packages were set to upgrade, after upgrading and rebooting, everything back to normal. This last step I still did remotedly with ssh, because from the computer screen I wasn't able to get into the console either.

---

### Post by P-I H on 2017-03-24
Tried to install gdm3, but that didn't work.
Managed to get to a terminal, updated and upgraded and now it's working again.

---

### Post by howefield on 2017-03-25
> **jbicha said:**
> This was my fault. You need unity-settings-daemon [15.04.1+17.04.20170322-0ubuntu1.1           ]("https://launchpad.net/ubuntu/+source/unity-settings-daemon/15.04.1+17.04.20170322-0ubuntu1.1")

Thanks for posting jbicha, I deliberately held off from updating as was waiting for the "pending" daily image to catch up with the updates but unattended-upgrades decided 
otherwise, easy enough to switch to a console and install the missing package.

---

### Post by Cavsfan on 2017-03-25
> **howefield said:**
> Thanks for posting jbicha, I deliberately held off from updating as was waiting for the "pending" daily image to catch up with the updates but unattended-upgrades decided 
otherwise, easy enough to switch to a console and install the missing package.

Just curious plus I haven't kept up with the latest updates to 17.04 but, these unattended-upgrades are going on in the background right?

I booted into Xubuntu 17.04 and had no problems. I tried to do an update via cli and it initially said there were 11 updates but, I got the dpkg is busy error.
Then after a few minutes, Cairo Dock informed me that I needed to do a reboot and at that time there were no updates. So, I rebooted and everything was good.

This is sounding a bit like a rhetorical question but, I prefer to control the updates myself. Which is why I ask.
Thanks

---

### Post by #&amp;thj^% on 2017-03-25
> **Cavsfan said:**
> Just curious plus I haven't kept up with the latest updates to 17.04 but, these unattended-upgrades are going on in the background right?

I booted into Xubuntu 17.04 and had no problems. I tried to do an update via cli and it initially said there were 11 updates but, I got the dpkg is busy error.
Then after a few minutes, Cairo Dock informed me that I needed to do a reboot and at that time there were no updates. So, I rebooted and everything was good.

This is sounding a bit like a rhetorical question but, I prefer to control the updates myself. Which is why I ask.
Thanks

Turn off Ubuntu automatic updates:
You can disable automatic updates through command line. Open Terminal and edit the file **"/etc/apt/apt.conf.d/10periodic**" and edit the line : ```
_APT::Periodic::Update-Package-Lists "1"; _
```to ```
APT::Periodic::Update-Package-Lists "0";
``` to turn off the automatic updates in Ubuntu.

---

### Post by Cavsfan on 2017-03-25
> **1fallen said:**
> Turn off Ubuntu automatic updates:
You can disable automatic updates through command line. Open Terminal and edit the file **"/etc/apt/apt.conf.d/10periodic**" and edit the line : ```
_APT::Periodic::Update-Package-Lists "1"; _
```to ```
APT::Periodic::Update-Package-Lists "0";
``` to turn off the automatic updates in Ubuntu.

Thank you very much! I like to be in control of my updates; nothing automagical going on anywhere. :)

---

### Post by howefield on 2017-03-26
> **Cavsfan said:**
> Just curious plus I haven't kept up with the latest updates to 17.04 but, these unattended-upgrades are going on in the background right?

Indeed they do, as far as I know they take care of package updates to those that are already installed in the system. 

I used an alternative, slightly nuclear method to that which ifallen posted :)

```
sudo apt purge unattended-upgrades
```

---

### Post by Cavsfan on 2017-03-26
> **howefield said:**
> Indeed they do, as far as I know they take care of package updates to those that are already installed in the system. 

I used an alternative, slightly nuclear method to that which ifallen posted :)

```
sudo apt purge unattended-upgrades
```

Thanks for that, I like the nuclear method myself. Didn't have time to do it yesterday so I'm glad I got to see this before I did it.
There were a couple of log files left in the directory so it could not delete it and what I seen in those log files seems unreal to me. Stuff I'd see in terminal during CLI updates.
So, I deleted the log files and the directory to clean it up.
No more unattended-upgrades!  
Thanks ifallen for your suggestion too!

---

