---
title: "should l do a clean install for 9.04"
date: 2009-04-23
forum: System76 Support
---

### Post by eddietours on 2009-04-23
or a upgrade l have the Gazelle Ultra

---

### Post by arepaking on 2009-04-23
I would like to extend this question for the Daru3 as well.

---

### Post by thomasaaron on 2009-04-23
It's a matter of personal preference.

Some people prefer to upgrade via update manager. If you choose to go that route, my advice is to wait for a few days. Ubuntu's servers always get bogged down with every new release. Inevitably, there are a number of hosed and corrupted upgrades.

Personally, I like a fresh install. It just... smells good. Like a clean sheet of paper. (But that's just me.)

Upgrade instructions...
[http://knowledge76.com/index.php/JauntyUpgrade](http://knowledge76.com/index.php/JauntyUpgrade)
...and make sure Intrepid is fully updated first.

Fresh install instructions...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by ctsdownloads on 2009-04-24
> **thomasaaron said:**
> It's a matter of personal preference.

Some people prefer to upgrade via update manager. If you choose to go that route, my advice is to wait for a few days. Ubuntu's servers always get bogged down with every new release. Inevitably, there are a number of hosed and corrupted upgrades.

Personally, I like a fresh install. It just... smells good. Like a clean sheet of paper. (But that's just me.)

Upgrade instructions...
[http://knowledge76.com/index.php/JauntyUpgrade](http://knowledge76.com/index.php/JauntyUpgrade)
...and make sure Intrepid is fully updated first.

Fresh install instructions...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)


...adding in my own thoughts, a dedicated Home partition is your friend. :)

---

### Post by bill516 on 2009-04-25
> **eddietours said:**
> or a upgrade l have the Gazelle Ultra

I have done it both ways, in fact, and both have worked.  Given a Home Partition I believe a clean install is easy and it poses a very minimal risk to any data.  And in my experience it has been nearly as quick.  Waiting a week or two is very good advice and, of course, check the integrity of the downloaded iso file using MD5sum.  That done a clean installation should go easily.

---

### Post by eddietours on 2009-04-27
Thanks everything is ok with the new clean install:guitar:

---

### Post by alexisbellido on 2009-04-27
Agree, a home partition is a must. I've never had a problem upgrading my Pangolin but prefer a clean install approach for the same reason Thomas mentioned :)

For Jaunty I'm going the clean install way once again and I'll take the change to downgrade from 64 to 32 bits as well. Really need Skype and Adobe AIR working this time.

---

### Post by jml on 2009-04-27
Just to add my two cents worth.  One of the things I really like about Debian based distros is the fact that you only have to install it once.  Its designed from the ground up to be a "rolling distro".  So if everything goes as it should, you have a shiny new install with a minimum of hassle.

Joe

---

### Post by ProfDecoy on 2009-04-28
I did a Dist upgrade for my Wild Dog system and it went through just fine.  I just had to reinstall the ATI Proprietary drivers (for Eve Online, which is still a bit flaky in Wine/Crossover, but I don't play much anymore anyway).

However, I've been planning to do a clean rebuild of my desktop anyway, because I've been fiddling around with a whole bunch of different things on it and looking to purge it all out at some point.  Though, I guess it's also a bit related to my old habit of rebuilding my Windows boxes every 6 to 9 months... :-)

---

### Post by riseringseeker on 2009-04-29
> **alexisbellido said:**
> Agree, a home partition is a must. I've never had a problem upgrading my Pangolin but prefer a clean install approach for the same reason Thomas mentioned :)

For Jaunty I'm going the clean install way once again and I'll take the change to downgrade from 64 to 32 bits as well. Really need Skype and Adobe AIR working this time.

I run 64 bit on both my Darter and Wild Dog, and have no trouble with skype (once initial settings are right), what kind of problems have you been having?  We could start another thread to see if we can get you going.

Never heard of Adobe AIR, so can't help there.

---

### Post by werewolves on 2009-04-30
Did an upgrade (Kubuntu) last night on my Daru2, and it is semi-broken.  It doesn't recognize the wifi card, so I can't do much.  A couple of other things seem a little flaky as well, so I think I'll just do a fresh install tonight.  Thank goodness I have a separate /home partition!

---

### Post by thomasaaron on 2009-04-30
You may want to try this before re-imaging...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   


---

### Post by werewolves on 2009-04-30
> **thomasaaron said:**
> Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little computer monitor). 
Well, unfortunately that's one of the little things that seem to have gone wrong, there is no Network Manager icon...

I'll try your other suggestion though and see if that brings it back.

---

### Post by thomasaaron on 2009-04-30
Do you see your batter/ac indicator? If not, it could be that your notification area got deleted. To add it, right-click on the upper panel and select "Add to Panel." In the resulting window, scroll down to notification area, highlight it and click the "Add" button.

Did that fix it?

---

### Post by werewolves on 2009-04-30
> **thomasaaron said:**
> Do you see your batter/ac indicator? If not, it could be that your notification area got deleted. To add it, right-click on the upper panel and select "Add to Panel." In the resulting window, scroll down to notification area, highlight it and click the "Add" button.

Did that fix it?
Nope, my system tray is there, just no network icon.  Also my /etc/network/interfaces looks just like your example.


EDIT: Disregard, I reinstalled anyway from scratch and everything seems to be working now.

---

### Post by werewolves on 2009-05-01
> **werewolves said:**
> 
EDIT: Disregard, I reinstalled anyway from scratch and everything seems to be working now.

Except I don't have a battery monitor in my system tray... I can manually add one to the taskbar or desktop, but there isn't one that comes up automatically in the tray.  Weird...

---

