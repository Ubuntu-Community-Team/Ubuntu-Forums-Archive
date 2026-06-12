---
title: "I will never ever dist-upgrade again"
date: 2013-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by romeqjanoosh on 2013-11-02
I just want to share my frustration in this post. 

I tried to upgrade my distribution to 13.10 from 13.04. During installation of new packages the upgrade application hanged (window grayed out), never came back to life and after at least 15 minutes everything that I could do is reboot. After that my system is completely broken and unusable. Unity crashes when I try to do anything, icons on launcher are missing, buttons on the toolbar are missing, networking doesn't work.

I'm absolutely speechless. This is utterly ridiculous.

---

### Post by Irihapeti on 2013-11-02
Moved to Ubuntu, Linux and OS Chat as it's not a request for help.

If you want help with specific problems, feel free to start a thread giving details in the relevant forum.

---

### Post by rrnbtter on 2013-11-02
Greetings,
If /boot and /root are on separate partitions you are in luck. On the install choose "other",  and in the partition manager choose to reuse Swap as is, use and reformat "boot", use and reformat /root, use and D0 NOT format /usr and /home. Make sure the correct flags are set on boot and root. You may have to reinstall a few of your self installed programs but your settings should be retained. I went from 13.04 to 1310 to 14.04 with no problems.

---

### Post by deadflowr on 2013-11-02
15 minutes doesn't seem to be an excruciatingly long time. An hour, maybe.
Sometimes it grays out if an action is required by you and another window is opened somewhere, either in another workspace or under the greyed out window.
You might be able to fix it by going to the recovery section at boot and then running the fix broken packages.

Also, dist-upgrade and upgrading versions are not the same thing.

dist-upgrade is a command to update the existing systems packages.
It does not upgrade the version you are using.

---

### Post by Frogs Hair on 2013-11-02
An upgrade to a new version via the Internet can take hours , first the download of about 900 Mb of packages and then unpacking, replacement, and setup. After installation there is cleanup process as well. If you choose to upgrade be sure not to use the computer during the upgrade or the process it may freeze . I have done one just to see what it was like and preformed a clean installation later anyway .

---

### Post by rrnbtter on 2013-11-02
Greetings,
FYI deadflowr make a good point. Both Raring and Saucy have a bug that keeps a "dialog" window under the active window instead of bringing it to the foreground.  You litterly sit there waiting without knowing that the dialog window has opened. If you keep an eye on the launcher you should see a "hint" that there is a new window open, or even reduce the size of the installation windows so that you can see if another window opens.  This will most often occur when the installer wants to update fonts and needs your permission to proceed due to license restrictions.

---

### Post by romeqjanoosh on 2013-11-02
Thank you guys for your help. Unfortunately, it will be very hard to convince me that an application completely freezing and not responding for at least 15 minutes (with no CPU usage, so it's clearly just blocked on something) is normal and I should just wait longer.

Now, is there a way to install fresh Ubuntu 13.10 while preserving contents of my home directory (everything is on the same partition)?

---

### Post by tgalati4 on 2013-11-02
Your best recourse is to back up your data to a flash drive (boot up using a LiveDVD) and then wipe and perform a clean installation.  When your system is hopelessly mangled, trying to fix it can take hours when a clean install can be done in 20 minutes--once you have burned a disk or USB stick.

---

### Post by buzzingrobot on 2013-11-02
> **romeqjanoosh said:**
> ... after at least 15 minutes ...

It might well be that the necessary downloads, much less their installation, had not completed in that 15 minutes.

I'm on a reasonably fast broadband connection. Downloading all files in a distribution upgrade in only 15 minutes would please me. 

In any case, in-place upgrades have a better chance for success if the user has returned the system as closely as possible to the original post-install state, including purging all PPA's.

---

### Post by craig10x on 2013-11-02
As they mentioned, it's very important to uncheck any ppas you have installed from the software sources list (they will likely get taken out anyway)...but assuming you run only 1 ubuntu, if you download and run a live 13.10 disc, it SHOULD offer you the option to upgrade 13.04 to 13.10 using the INSTALLER...this is the method i have been using (you can read about my results in the link below) and it has been working very well for me...it is FAST and seems to be more reliable then using either Software Updater or Terminal to do the upgrade...mine took about 25 minutes total...and it doesn't have to go to the internet...everything done right from the iso....I keep telling people about it here but sometimes i feel like "banging my head against the wall" because very few seem to use it...;) :D
[http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade](http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade)

You might try doing it again, using this method instead...not sure if it will be able to compensate for what you did so far, but perhaps worth a try....back up your important stuff on an external drive if possible and then do it...worse case is you may have to install 13.10 clean....but in the future TRY this method, i think you will likely find it works sooo much better...

---

### Post by oldos2er on 2013-11-02
> **romeqjanoosh said:**
> I just want to share my frustration in this post. 

I tried to upgrade my distribution to 13.10 from 13.04. During installation of new packages the upgrade application hanged (window grayed out), never came back to life and after at least 15 minutes everything that I could do is reboot. After that my system is completely broken and unusable. Unity crashes when I try to do anything, icons on launcher are missing, buttons on the toolbar are missing, networking doesn't work.

I'm absolutely speechless. This is utterly ridiculous.

If you mean you changed your sources.list from raring to saucy then ran *apt-get dist-upgrade*, I'm fairly sure that's not a supported method of upgrading, although I have heard of people doing it.

Personally I've had much better luck doing a clean install rather than upgrading, for what it's worth.

---

### Post by cariboo on 2013-11-02
Probably the best thing to do to rescue your upgrade is to start in recovery mode, select networking from the menu, and than when a network connection is established, select the root prompt, then run:

```
sudo apt-get -f install
```

to continue downloading and installing the packages that were missed when you aborted the upgrade. I'd suggest that almost all failed upgrades, are because the process was never finished.

---

### Post by lykwydchykyn on 2013-11-02
I tend to prefer using the command-line updater (sudo do-release-upgrade), so that I can get constant feedback about the progress rather than just a meaningless progress bar.  I've had to rescue a bad upgrade now and then with a little command-line dpkg-fu; you can fix pretty much any upgrade issue with a handful of apt/dpkg commands if you're just persistent and read the error output.

---

### Post by craig10x on 2013-11-02
The thing i love about doing the upgrade from the live iso installer is i have noticed that everything seems to happen in a very smooth manner...if you didn't know better, you would think it was doing a totally clean install...i realize it isn't an option in all situations (once again, i think it is only offered if you are running 1 ubuntu on your set-up)...but if it is available, and you like things to go pretty smoothly, i would suggest it is the best way to go...

---

### Post by craig10x on 2013-11-03
> **oldos2er said:**
> If you mean you changed your sources.list from raring to saucy then ran *apt-get dist-upgrade*, I'm fairly sure that's not a supported method of upgrading, although I have heard of people doing it.

Personally I've had much better luck doing a clean install rather than upgrading, for what it's worth.

 LOL...A bit off the topic but when i saw the "line" near your avatar i knew where THAT came from: (and an old favorite of mine from 1963)
[http://www.youtube.com/watch?v=7Un-bOi8HjQ](http://www.youtube.com/watch?v=7Un-bOi8HjQ)

---

### Post by oldos2er on 2013-11-03
Just a bit OT, yes! No one makes music like that anymore.

---

