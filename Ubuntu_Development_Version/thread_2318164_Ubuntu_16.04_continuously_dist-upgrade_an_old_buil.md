---
title: "Ubuntu 16.04: continuously dist-upgrade an old build  or install each new build?"
date: 2016-03-23
forum: Ubuntu Development Version
---

### Post by siggi2 on 2016-03-23
Hi,

I am using Ubuntu Xenial Xerus (development branch) (16.04) to be prepared for the final version in April. Now I wonder:

*** 1 ***
Is it enough to install some build, say from [http://cdimage.ubuntu.com/daily-live/20160304/]("http://cdimage.ubuntu.com/daily-live/20160304/"), and do "dist-upgrade" every day to get the newest build, or 

*** 2 ***
is it necessary to install each day the latest build, e.g. as of today, from [http://cdimage.ubuntu.com/daily-live/20160323/]("http://cdimage.ubuntu.com/daily-live/20160323/") 

to have the final version in April?

Thanks,

linuxcub

---

### Post by QIII on 2016-03-23
Moved to Ubuntu Development Version.

---

### Post by sammiev on 2016-03-23
Hi,

It's not necessary to download and install a fresh build each day.

Just along you keep it updated you will always have the latest.

---

### Post by grahammechanical on 2016-03-23
Unless, you want to share in testing the ISO images and the installer and report bugs so that the final release is verified to install on all kinds of hardware. In that case. download a daily image every day and test it.

Regards.

---

### Post by vasa1 on 2016-03-23
> **grahammechanical said:**
> .... download a daily image every day and test it.
...

Or you could download a daily image once and subsequently keep the image updated using zsync .... 

I understand from previous posts on the subject, that dist-upgrades of early images *can* have unwanted consequences. So be prepared if you go that route.

---

### Post by Bucky Ball on 2016-03-23
> sudo apt-get update
sudo apt-get dist-upgrade

Don't bother running dist-upgrade without update first ... no point. They should always be run in tandem. 

But yes, those two commands are all you need, an you don't need to do it every day. If you wait until the day after release and run them you will be there.

I like to keep my 16.04 updated though. About all I do with it at the moment and that is probably about twice a week.

Will start playing with it more over the coming weeks as I have some pressing things out of the way as of yesterday. :D

---

### Post by siggi2 on 2016-03-24
> **vasa1 said:**
> ...I understand from previous posts on the subject, that dist-upgrades of early images *can* have unwanted consequences. So be prepared if you go that route.

Do you remember what could go wrong?

---

### Post by oldfred on 2016-03-24
In the old days, there often were versions that added new packages without updating at same time dependencies or vice versa. Only the alpha/beta versions were normally in sync.
But last few years where Ubuntu stopped releasing alpha, the daily almost always works. Sometimes minor breakage, and often lots of bugs to report or issues where new version of something is missing major feature.

The main advantage of a new clean install is that there have been so many updates that your log files & old versions of .debs downloaded are large. A clean install then is like a major house clean. Or you can do the major houseclean.

I notice now the system is putting old kernels into whatever list it is so sudo apt autoremove cleans it out.
I also notice that now it is apt not apt-get, although apt-get still works. Man page seems identical.

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by vasa1 on 2016-03-24
> **siggi2 said:**
> Do you remember what could go wrong?
[http://ubuntuforums.org/showthread.php?t=2316260&p=13451320#post13451320](http://ubuntuforums.org/showthread.php?t=2316260&p=13451320#post13451320) and quoting from there:> We can use Software Updater. Or we can run apt-get update & apt-get upgrade. It is up to us. But we should be aware that apt-get dist-upgrade will bring in packages that are being held back. And they are being held back for a reason. I have twice used dist-upgrade to bring in a new kernel that I was too impatient to wait for. And nothing was broken. But as with a partial upgrade there is always an element of risk when using dist-upgrade.

---

### Post by Doug S on 2016-03-24
When the change from the Ubuntu Software Center to gnome software came down, a few of us found that we had to do a fresh installation from the daily for things to end up O.K.

---

### Post by vasa1 on 2016-03-24
> **oldfred said:**
> ...

The main advantage of a new clean install is that there have been so many updates that your log files & old versions of .debs downloaded are large. A clean install then is like a major house clean. ...
I like this ^^^.

---

### Post by Cavsfan on 2016-03-24
> **Doug S said:**
> When the change from the Ubuntu Software Center to gnome software came down, a few of us found that we had to do a fresh installation from the daily for things to end up O.K.


I did it the hard way! :lol: [http://ubuntuforums.org/showthread.php?t=2317907&p=13458572#post13458572](http://ubuntuforums.org/showthread.php?t=2317907&p=13458572#post13458572)

[http://ubuntuforums.org/showthread.php?t=2317907&p=13458619#post13458619](http://ubuntuforums.org/showthread.php?t=2317907&p=13458619#post13458619)

---

### Post by siggi2 on 2016-04-06
Thanks to all of you :D I will remember to do a clean install with the final version.

Till then, it is fun to watch how the Development version is developing.

---

