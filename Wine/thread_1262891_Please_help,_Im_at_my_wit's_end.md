---
title: "Please help, Im at my wit's end"
date: 2009-09-10
forum: Wine
---

### Post by Cloudkookoo on 2009-09-10
Ok, so after moving to linux from Vista I can honestly say I love it. Except for one thing that's had me going crazy. Im an absolute noob to linux in general, Im using Ubuntu 9.04. My problem is, I would like to install world of warcraft from my DVD using Wine. I installed wine using sudo apt-get install wine, like every guide told me to do.

 As far as I know it's configured correctly, though I didnt mess with any of the configurations.

I've tried to follow many guides I've found online and none have been able to help me out.

I've made absolutely no progress in getting this installed, so please if someone could help me out, I'd be extremely gratefull.

Thank you, I eagerly wait for some help. :confused:

---

### Post by jasonditz on 2009-09-10
> **Cloudkookoo said:**
> Ok, so after moving to linux from Vista I can honestly say I love it. Except for one thing that's had me going crazy. Im an absolute noob to linux in general, Im using Ubuntu 9.04. My problem is, I would like to install world of warcraft from my DVD using Wine. I installed wine using sudo apt-get install wine, like every guide told me to do.

 As far as I know it's configured correctly, though I didnt mess with any of the configurations.

I've tried to follow many guides I've found online and none have been able to help me out.

I've made absolutely no progress in getting this installed, so please if someone could help me out, I'd be extremely gratefull.

Thank you, I eagerly wait for some help. :confused:

What sort of problem are you running into? If it's the EULA acceptance thing you need to update to a newer version of wine.

---

### Post by Cloudkookoo on 2009-09-10
Well, my problem is really just getting the installer to work, and Im running the latest stable version of wine which is 1.0.1. I guess Im just asking for someone to explain to me exactly what I have to do in order to run WoW in a way that a complete newbie to ubuntu and wine could understand. I've heard people say that if you're a noob to linux, you shouldn't try to install Wow on it, so none of that please, I really just want to get it going, as going back to Windows is pretty much not an option.

---

### Post by Cloudkookoo on 2009-09-10
Here is what I see when viewing the contents of the DVD.

[[IMG]http://img185.imageshack.us/img185/372/screenshotof.th.png[/IMG]]("http://img185.imageshack.us/i/screenshotof.png/")

If I right click and select open with wine, nothing happens. Am I doing something wrong, because I figured this would work.

And in properties/ permissions it says Im not the owner so I cant change the permissions, is that what the orange x means?

Im sorry if Im asking for too much by wanting to be walked through this process, but I've followed as many guides as I could find, and nothing was able to help me out.

---

### Post by ainsworth_t on 2009-09-10
Try the following from a terminal

Change to your CD directory:
```
cd /media/cdrom0
```

Verify this is the directory your installer is located by running:
```
ls -al
```

If it is the correct directory, run the following command:
```
wine Installer.exe
```
or
```
sudo wine Installer.exe
```
Not sure if sudo is necessary, but wouldn't hurt.

---

### Post by Cloudkookoo on 2009-09-10
Tried it and this is what I get,

jason@jason-desktop:~$ cd /media/cdrom0
jason@jason-desktop:/media/cdrom0$ ls -al
total 1418
drwxr-xr-x 3  503 dialout     592 2008-11-07 14:23 .
drwxr-xr-x 4 root root       4096 2009-09-10 09:09 ..
drwx------ 2  503 dialout     492 2008-11-07 14:23 DirectX
-rwx------ 1  503 dialout 1442088 2008-11-07 14:23 Installer.exe
jason@jason-desktop:/media/cdrom0$ sudo wine Installer.exe
[sudo] password for jason: 
wine: /home/jason/.wine is not owned by you
jason@jason-desktop:/media/cdrom0$

---

### Post by ainsworth_t on 2009-09-10
Try running it without sudo, just ```
wine Installer.exe
```

---

### Post by Cloudkookoo on 2009-09-10
without sudo, I get this

jason@jason-desktop:/media/cdrom0$ wine Installer.exe
wine: could not load L"D:\\Installer.exe": Module not found

---

### Post by bear54 on 2009-09-10
I am no expert on the program wine but I went to the wine web site and it says that the wine program in Ubuntu 9.04 is out of date and should be updated to the latest version. Go here to get it...
[COLOR="RoyalBlue"]** [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")** [/COLOR]
You will have to uninstall the version you have already installed on your computer before installing the newer version. On the wine web site it does say that WOW works. :cool:

---

### Post by ainsworth_t on 2009-09-10
Try going to Applications >> Wine >> Configure Wine, then click the Drives tab. Verify that optical drive (/media/cdrom0) is mapped to the D drive. If it isn't try mapping it. If it is, I'm not sure I can be much help.

---

### Post by hikaricore on 2009-09-10
Actually it is a problem with the way the DVD was mastered.
ALOT of users including those on MacOS and ***dows had trouble with this disc.

Search the WINE forum as there are tons of threads on installing wotlk telling how to properly mount this disc.
If I have time later I'll link you to one or post the needed info but atm I'm busy as hell.

---

### Post by Cloudkookoo on 2009-09-10
Alright I uninstalled wine, and reinstalled, and have made some slight progress, the optical drive is mapped to D, but when I try to open the installer.exe I get an error notification saying access denied. Not good, but at least it's telling me something now. Any suggestions?

---

### Post by hikaricore on 2009-09-10
Read my last post.

---

### Post by gogamaru on 2009-09-10
> **Cloudkookoo said:**
> I keep getting PM's from a user named 'gogamaru' who claims he know's how to fix the problem, yet is unwilling to post the process in the forum. I found this suspicious and just thought it was worth mentioning.

And by the way, after searching the Wine forums, still haven't found anything helpful  :[

I hear the funeral march...

---

### Post by hikaricore on 2009-09-10
Ugghhh....

[http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)
[http://ubuntuforums.org/showthread.php?t=1064891&highlight=wotlk](http://ubuntuforums.org/showthread.php?t=1064891&highlight=wotlk)
[http://ubuntuforums.org/showthread.php?t=1205825&highlight=wotlk](http://ubuntuforums.org/showthread.php?t=1205825&highlight=wotlk)
[http://ubuntuforums.org/showthread.php?t=980629&highlight=wotlk](http://ubuntuforums.org/showthread.php?t=980629&highlight=wotlk)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

Your answer is in there stop being lazy.

---

### Post by Nostalos on 2009-09-10
Did this a few months ago playing with wine.  Never had the media to install from.  The WoW client Downloader worked quiet well other than the fact I had to DL the entire game over torrent *shudder*

---

### Post by Cloudkookoo on 2009-09-10
I've downloaded the universal installer from blizzard and it appears to be working, albeit extremely slow. Is this common when running through Wine?

---

### Post by Nostalos on 2009-09-10
I honestly can't say.  Don't use wine much and don't play WoW.   Was just bored one day at work and tinkered around with a buddies account.

---

### Post by hikaricore on 2009-09-10
> **Cloudkookoo said:**
> I've downloaded the universal installer from blizzard and it appears to be working, albeit extremely slow. Is this common when running through Wine?

You completely ignored the part where I said it was an issue with the DVD..
Your problem thus far has not been a WINE issue.
If you mean your torrent is slow that's because you haven't got your ports configured correctly for the blizzard p2p, this occurs on windows as well, I'm assuming you have a router?

[http://eu.blizzard.com/en/wow/faq/bittorrent.html](http://eu.blizzard.com/en/wow/faq/bittorrent.html)

---

### Post by Cloudkookoo on 2009-09-10
No, I didn't ignore it, I tried to figure out getting it to work from the DVD, but couldn't, so I jumped to my last resort... downloading.

And no, Im not behind a router, Im connected directly to modem.

---

### Post by hikaricore on 2009-09-10
And does your modem have an http interface in which you can setup port forwarding?
Look into this if you're concerned about slow downloads from blizz.

---

