---
title: "Server stuck at GRUB menu after 12.04 update/upgrade"
date: 2012-07-02
forum: Server Platforms
---

### Post by RicardoEscobar on 2012-07-02
Hello there. I'm a sysadmin at a local lawer firm. And I have a problem: the website is down. 
I'm using Ubuntu server 12.04 for 64 bit on an HP proliant ml110 g6 server. 
What happened? Well everything was just alright. Then I logged on via SSH (remote unix terminal) into the server to check for updates (I do this once a week) with the command:
```
sudo apt-get update
```
After that I found a number of available updates hen I entered this command:
```
sudo apt-get upgrade
```
After that it upgraded as usual. I'm also a teacher (I was at school at the time) so I went to class. After class was done, I logged back into the server via SSH and the welcome screen told me that the server needed a restart. So I used this command:
```
sudo reboot now
```
The server never came back up after that. The website is down. As I'm writing this, I'm on my way back to my office to see what happened. On my unix terminal on my laptop I used this command:
```
Ping myServerHostName.zapto.org
```
And my server actually responds to this ip ping, so is not a network issue, my server is connected to Internet and 
Is pinging back. Maybe something happened on reboot. I'll describe more as soon as I get there.
---
I finally get back to the office (after a one and a half hour trip). I plugged in a keyboard and a monitor into the server. And I found this:
the server rebooted but statyed at the GRUB menu and never moved from there. Looks like the new update changed how GRUB behaves at boot time. And this is a problem, now I can't restart the server via SSH. I NEED to be in front of the server with a physically attached keyboard and monitor, everytime I need to reboot the system.

I asked google and seems like this is a permanent change. Bad luck for me, I guess I can just keep the server up all the time ane reboot it only when I'm there.

I need to rant a little: I feel retarded to have to connect a keyboard and a monitor to the server just to turn it on, I don't know who is behind this decision, but I hope he corrects this mistake.

If not, does anyone of you know a work around this? is there a way to make the server autoboot again? 

By the way, the server halts at GRUB menu everytime, and this happened after the last update, so I'm pretty sure is because the update/upgrade.
---
A colleague just told me that he just reinstalled ubuntu server back to 11.04 and the problem fixed. I rather don't do that, but If this change was not a mistake, I'm afraid, it was on purpose, then it wont be fixed soon.

I cannot express how stupid I feel everytime I attach a keyboard and a monitor to the server just to turn it on. I feel very frustrated now.

See you around.

---

### Post by rubylaser on 2012-07-02
I'm sorry you are experiencing this. But, this is not the default behavior and should be able to be fixed.  I'm running the newest 12.04 Server here at work on a couple servers and they all will automatically boot after GRUB times out and will allow remote SSH.  I suspect that something got messed up in the upgrade process.  

What does GRUB say exactly when it's stuck? For example, is it waiting for a drive to become available to mount, is there an error, etc?
```
dmesg
```
```
cat /etc/default/grub
```

In regards to SSH, is it running?
```
ps aux | grep ssh
```

You should see output like this.
```
**root       738  0.0  0.1  49948  2872 ?        Ss   14:06   0:00 /usr/sbin/sshd -D**
root      1207  0.0  0.1  73352  3584 ?        Ss   14:06   0:00 sshd: zack [priv]   
zack      1362  0.0  0.0  73352  1680 ?        S    14:07   0:00 sshd: zack@pts/1    
zack      1539  0.0  0.0   8096   936 pts/1    S+   14:09   0:00 grep --color=auto ssh
```

The sshd daemon is the line you want to see.  This will tell you if it's running.

---

### Post by Hadesdarklord on 2012-07-02
If his server is as mine, it is stuck in the grub prompt


just:

grub>

---

### Post by RicardoEscobar on 2012-07-03
After an entire day trying with the recovery cd, It seems like after updating to 12.04, the system gets a lot of problems, I will number the ones I found:

[LIST=1]
[*]The fstab no longer works, so it needs to be edited and add UUID="veryLargeNumberHere" instead of "/dev/sdb1".
[*]noip2 (dns resolve program) no longer works, and cannot be installed anymore, so I have no way to publish my websites over the internet anymore. Tried myDNS but have a lot of problems too.
[*]GRUB needs you to press some key, it no longer auto-choose the first option,  this seems  like a permanent change and is working as intended, a workaround is to only reboot the server when you are physically in front of the server with a monitor and a keyboard attached to it (remote reboots are out of the question)
[/LIST]

My colleague suggested me to do implement the next solution, and so I did:

First we need to create a mount point to save a backup of my websites files.

```
sudo mkdir /media/usbBackup
```

Then we need an USB drive, plug it in the server and mount it with this command:

```
sudo mount -t vfat /dev/sdb2 /media/usbBackup
```

Now we need to backup the websites:

```
sudo cp -r /var/www /media/usbBackup
```

After that it's done, we need to backup all databases:

```
mysqldump --user=root --password=myPassword -A > /media/usbBackup/respaldo.sql
```

After that's done you need to eject the usb:

```
sudo umount /media/usbBackup
```

Congratulations you have a system backup now!

now we need to restore the system.

First download this ISO and burn it: 

[64-bit PC (AMD64) server install CD]("http://releases.ubuntu.com/natty/ubuntu-11.04-server-amd64.iso")

If you have a 32 bit server download this one:

[PC (Intel x86) server install CD]("http://releases.ubuntu.com/natty/ubuntu-11.04-server-i386.iso")

After download is complete, burn the image ISO into a CD.

Open the cd tray of the server and put the CD inside, then reboot the system with:

```
sudo reboot now
```

It's important that the BIOS boots from cd first, if you see a GRUB menu, then you need to edit your BIOS to do so, check your server's documentation.

After you boot with the cd, just install the server as you would normally do, erase everything and do a clean install, don't worry about your databases and websites, since you have a backup.
--- edited
at this point, DO NOT run this command EVER!: 

do-release-upgrade

this will corrupt GRUB, noip and fstab, we need to wait until ubuntu team comes with a patch to fix this, but my colleague and I  recommend that you just use the stable version of ubuntu server, the one I linked.
--- edited
After you reinstalled the server, GRUB no longer waits at GRUB menu, you may reboot via SSH as you would like and everything is fixed.

But now we need to mount and restore the backup, do the next after logging in the server:

```
sudo mkdir /media/usbBackup
sudo mount -t vfat /dev/sdb2 /media/usbBackup
sudo cp -r /media/usbBackup /var/www
mysqldump --user=root --password=myPassword mysql < /media/usbBackup/respaldo.sql
```

After that, all databases are restores and all websites are up.

Thanks to Rodrigo Gonzales for helping me with the entire process. Peace.

---

### Post by darkod on 2012-07-03
I feel for your problems but I think you are jumping to conclusions a little bit.

First, using UUID in /etc/fstab and in grub2 is standard in ubuntu since few versions ago. Precisely to avoid the problem of disks "changing places" and sda becoming sdb, etc. Not sure what has happened during your upgrade, but if sdb1 is no longer sdb1 that would explain a lot.
Of course /etc/fstab will not be correct any more. And grub2 can stop booting precisely because of this. If you are using fstab with /dev/sdXY instead of UUID, it's your responsibility to keep it correct.

Did you confirm whether sdb1 is still sdb1 and what is grub2 actually trying to boot?

As for noip2, I haven't used that package but I have seen people using it even with 12.04 LTS so maybe something got corrupted during the upgrade or it works slightly differently, but it should be able to work.

The grub2 needing you to press a key to boot is probably related to the wrong fstab. It might have been asking to skip mounting a partition it can't find or similar.

I understand that installing 11.04 instead of 12.04 LTS worked, and it is expected it would work, but it's not really a solution, especially since the problem was never fully diagnosed and mainly because it will be supported much shorter than 12.04 LTS.

Yes, you did have some issues after upgrading to 12.04 LTS but being so adamant to not ever run do-release-upgrade is little bit over exaggerating. Because other people might find and read this thread in the future, there is no reason to try to make it sound that this will happen every time you do an upgrade, just because it happened once.
There are plenty successful upgrades done.

---

### Post by rubylaser on 2012-07-03
> **darkod said:**
> I feel for your problems but I think you are jumping to conclusions a little bit.

First, using UUID in /etc/fstab and in grub2 is standard in ubuntu since few versions ago. Precisely to avoid the problem of disks "changing places" and sda becoming sdb, etc. Not sure what has happened during your upgrade, but if sdb1 is no longer sdb1 that would explain a lot.
Of course /etc/fstab will not be correct any more. And grub2 can stop booting precisely because of this. If you are using fstab with /dev/sdXY instead of UUID, it's your responsibility to keep it correct.

Did you confirm whether sdb1 is still sdb1 and what is grub2 actually trying to boot?

As for noip2, I haven't used that package but I have seen people using it even with 12.04 LTS so maybe something got corrupted during the upgrade or it works slightly differently, but it should be able to work.

The grub2 needing you to press a key to boot is probably related to the wrong fstab. It might have been asking to skip mounting a partition it can't find or similar.

I understand that installing 11.04 instead of 12.04 LTS worked, and it is expected it would work, but it's not really a solution, especially since the problem was never fully diagnosed and mainly because it will be supported much shorter than 12.04 LTS.

Yes, you did have some issues after upgrading to 12.04 LTS but being so adamant to not ever run do-release-upgrade is little bit over exaggerating. Because other people might find and read this thread in the future, there is no reason to try to make it sound that this will happen every time you do an upgrade, just because it happened once.
There are plenty successful upgrades done.

+1.  Also, since you aren't using an LTS anymore, with 11.04, you will only have updates until [October of 2012]("https://wiki.ubuntu.com/").  You would have been better served going with 10.04 Server LTS which is supported until April 2015.

When faced with a situation like you had, it's often better to backup your data, and upgrade the OS from a fresh install, and then restore your data.

---

### Post by darkod on 2012-07-03
> **rubylaser said:**
> Also, since you aren't using an LTS anymore, with 11.04, you will only have updates until [October of 2012]("https://wiki.ubuntu.com/").

Only 18 months? Isn't it 3yrs for server version even for non-LTS?

---

### Post by hawkmage on 2012-07-03
According to the release support page:
> Normal Ubuntu releases are supported for 18 months. Previous Ubuntu LTS (Long Term Support) releases are supported for 3 years on the desktop and 5 years on the server. Starting with Ubuntu 12.04 LTS, LTS releases will be supported for 5 years on both the desktop and the server. 

---

### Post by RicardoEscobar on 2012-07-03
> **rubylaser said:**
> +1.  Also, since you aren't using an LTS anymore, with 11.04, you will only have updates until [October of 2012]("https://wiki.ubuntu.com/").  You would have been better served going with 10.04 Server LTS which is supported until April 2015.

When faced with a situation like you had, it's often better to backup your data, and upgrade the OS from a fresh install, and then restore your data.

Can you confirm this? Where did you see or read it?

---

### Post by oldfred on 2012-07-03
See this for support dates:

Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

---

### Post by rubylaser on 2012-07-03
> **RicardoEscobar said:**
> Can you confirm this? Where did you see or read it?

The October 2012 that I linked to in my previous post has the release and support schedule at the bottom.  Here is is again.

[https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")
or here.
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by rogejohnser on 2013-05-10
I would not categorize this thread as SOLVED. All you have done is backup, install and restore. This is not a solution for "getting stuck at grub" bug. Anybody with a real solution if any to this?

---

### Post by saconswl on 2014-03-05
Hi,
I am having this problem for long time almost for couple of months. Workaround was by pressing ENTER after few minutes of server reboot, solved!. My problem was with Ubuntu server 12.04 LTS in IBM but started same as with a clean 
> sudo apt-get upgrade.
With a successive problem in ssh and open port (last cradle of hope to run this server), I given attention to solve the problem. This is how I solved.
One of the option to resolve grub struck problem is edit the grub2 options in file /etc/default/grub, to my surprise in the server there is no such file. 
So I re installed grub in the server using the command
> sudo apt-get update; sudo apt-get install --reinstall grub
Based on: [http://askubuntu.com/questions/418666/update-grub-command-not-found](http://askubuntu.com/questions/418666/update-grub-command-not-found)
While doing this I got error of this kind in update 
> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                 Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

Though this error was not killing the installation processes, I resolved this error by changing the name server based on [http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors](http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors).
and done a sudo apt-get update, without any such this error. After reboot there is NO hanging at grub menu, the server with monitor logged smoothly into the console. So I suspect this name server error problem made the earlier sudo apt-get upgrade and made into this problem of removing grub etc.

---

