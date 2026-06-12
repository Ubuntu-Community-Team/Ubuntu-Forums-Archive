---
title: "server upgrade"
date: 2008-07-17
forum: Server Platforms
---

### Post by expatCM on 2008-07-17
My server is running 7.10.  I was thinking it might be an interesting idea to upgrade to 8.04.

Is the process simply 

apt-get update

apt-get dist-upgrade

Or is that a reflection of total trust and innocence?

---

### Post by Titan8990 on 2008-07-17
If this was just a desktop computer I would say go ahead and upgrade. If this is a production server IMO if it is not broke don't fix it.

I don't know what command will upgrade to ubuntu 8.x but I know apt-get update is not is. That will only update your package index files.

See man apt-get.

---

### Post by silverglade00 on 2008-07-17
I tried that with my server and it blew up on me. I had to reinstall from scratch. My advice would be to back up everything that is important to you and give it a try. If it doesn't work, you can install the update from scratch and restore your backed up stuff. Now, mine might have blown up because I originally installed the server and then installed ubuntu-desktop on it.

So, your commands should work, but better safe than sorry.

---

### Post by cdtech on 2008-07-17
Titan8990 is right, if it aint broke I wouldn't fix it. Although, it is possible to upgrade to Hardy as I did.

I copied my /etc/apt/sources.list file to a backup file and edited my existing sources.list changing every line with the name gutsy to the name hardy and deleted every line that had a comment on it.

It ended up looking like this:

```
deb http://archive.ubuntu.com/ubuntu/ hardy universe main
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main

deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-security universe main
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

Then I updated the source list using the following command:
sudo apt-get update

Then performed the upgrade with the following command:
sudo apt-get dist-upgrade

And to make sure that everything was installed, I issued the command:
sudo dpkg &#8211;configure -a

finaly it was time to Reboot and make my new Ubuntu Hardy installation take effect with all changes.

Before I did the Reboot I checked my /etc/fstab file and the /boot/grub/menu.lst file to verify that I would be able to boot to a proper kernel image and that all of my drives were still in tact in my fstab file.

Once I rebooted my system I tested my upgrade with the following command:
```
sudo lsb_release -a
```
The output looked like this:
```
Distributor ID: Ubuntu
Description: Ubuntu 8.04
Release: 8.04
Codename: hardy
```

**P.S.**
But remember, what works for some may not work for others........

---

### Post by expatCM on 2008-07-18
So it sounds a bit like the commands are fine but the outcome is not certain.

Not too refreshing.

I would like to run 8.04 since it is LTS for three years but it took me quite a while to set up what is there so perhaps I would be best to leave it alone.  At present it works and has only ever crashed once (ran out of drive space). 

So perhaps I should leave things be and look forward to the future day that I want to set up from scratch and then do just that ........

Thank you everyone for your comments though :)

---

### Post by cdtech on 2008-07-18
I know the feeling. I had the exact same issues with mine as well; lots of configuration and installed programs that I didn't want to have to re install.

After thinking about the way the command line works, by changing the sources file from Gutsy to Hardy, it would upgrade every program I had installed ( in theory ). All of the programs installed are saved in the repository so the sudo apt-get update command will update, first, all of the programs already installed to the Hardy version and the sudo apt-get dist-upgrade command will upgrade the distribution.

During the upgrade it ask about saving the original config's or replace, I chose to keep the originals (on most) until after the upgrade.

It's a lot more encouraging if you have a backup though. :)

---

### Post by koenn on 2008-07-18
apt is **not** the recommended way to upgrade to a newer release. 
[http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197](http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197)

---

