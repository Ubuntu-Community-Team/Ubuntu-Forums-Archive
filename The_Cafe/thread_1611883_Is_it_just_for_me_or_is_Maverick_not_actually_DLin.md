---
title: "Is it just for me or is Maverick not actually DLing updates at install?"
date: 2010-11-02
forum: The Cafe
---

### Post by MasterNetra on 2010-11-02
I've played around tested other things and came back. Reinstalled Maverick multiple times and not once has Maverick actually downloaded the updates when checked at install. Everytime I do updates it has to download every one of them post install. Is this happening for anyone else?

**Update**
Filed bug for this:
[https://bugs.launchpad.net/ubuntu/+bug/670031](https://bugs.launchpad.net/ubuntu/+bug/670031)

---

### Post by user1397 on 2010-11-02
> **MasterNetra said:**
> I've played around tested other things and came back. Reinstalled Maverick multiple times and not once has Maverick actually downloaded the updates when checked at install. Everytime I do updates it has to download every one of them post install. Is this happening for anyone else?
same here, tested on multiple installs as well

---

### Post by MasterNetra on 2010-11-02
> **ubuntuman001 said:**
> same here, tested on multiple installs as well

A side note, have you tryed installing it without encrypting the home directory, atm I've done that and no matter what I do it will not go to the login screen at start-up, keeps bypassing login & password and auto-loads into admin account despite the option for Don't ask for pass isn't selected. Checked the CD from Shippit and it was given a clean bill of health. I have filed a bug report in launchpad and trying to work with them on it.

---

### Post by CharlesA on 2010-11-02
I noticed the same thing with the installer not downloading updates.

---

### Post by kaldor on 2010-11-02
I confirm this as well in a virtualbox install.

---

### Post by MisterGaribaldi on 2010-11-02
Yep, did a fresh clean install, and it didn't download any updates, either. Updates after-the-fact work, of course, but nothing at installation.

---

### Post by user1397 on 2010-11-02
> **MasterNetra said:**
> A side note, have you tryed installing it without encrypting the home directory, atm I've done that and no matter what I do it will not go to the login screen at start-up, keeps bypassing login & password and auto-loads into admin account despite the option for Don't ask for pass isn't selected. Checked the CD from Shippit and it was given a clean bill of health. I have filed a bug report in launchpad and trying to work with them on it.

i've only tried installing it without encrypting the home dir, and have had 0 login issues

---

### Post by MasterNetra on 2010-11-02
Filed bug for this:
[https://bugs.launchpad.net/ubuntu/+bug/670031](https://bugs.launchpad.net/ubuntu/+bug/670031)

---

### Post by MasterNetra on 2010-11-02
> **ubuntuman001 said:**
> i've only tried installing it without encrypting the home dir, and have had 0 login issues

hmm yea I just more recently checked custom.conf in /etc/gdm for some reason Ubuntu decided to set my admin account to autologin. I'm 100% sure I didn't select that option, though that said I suppose it is possible I may of accidently hit my laptops touch pad and tap click might of selected it without me realizing it, who knows. either way I changed the .conf file and now Ubuntu is behaving as should.

---

### Post by Oxwivi on 2010-11-02
I second the bug. I installed on my sister's netbook with connection to wireless and wired LAN (shared from a desktop) only to download updates after install. However, on my desktop's install, the first time I installed from normal Live CD it did download *something* - I say something because I saw it download something, took a long time to install, but still download some updates later. But at reinstall it was the same no-download case.

---

### Post by MasterNetra on 2010-11-02
> **Oxwivi said:**
> I second the bug. I installed on my sister's netbook with connection to wireless and wired LAN (shared from a desktop) only to download updates after install. However, on my desktop's install, the first time I installed from normal Live CD it did download *something* - I say something because I saw it download something, took a long time to install, but still download some updates later. But at reinstall it was the same no-download case.

It will download and install that mp3 plugin you can choose to have install ,*which gets booted if you later install the restricted extras, as such I don't bother with that*, that might of been what you seen downloaded and installed? They should at least add the download & install of the restricted extras preferably it replacing that single mp3 option. I know Kubuntu does that. Which I give it props for. 
 After all one of my biggest complaints is that Ubuntu hasn't really made any effort to even have the ubuntu-restricted-extras package made known let alone present the option to install it for new users. I mean unless someone does their install for them or lets them know about it how are they suppose to know they can get the bulk of their codecs + flash (and I think java) in one package selection?

---

### Post by grahammechanical on 2010-11-02
I did not check download updates during install. I checked download restricted drivers and something happened.

When I went on to the BBC website to check the news the videos on the pages began playing. I could also use BBC iplayer to watch TV programs that had already been shown on terrestrial TV. This did not happen before because I did not have 64 bit installed. So, I guess 64 bit flash was one of the things downloaded.  It was a nice surprise. It is a nice touch to the installation process although I am not sure if a first time user would know what they were being asked to approve of unless they had already done some research about Linux and Ubuntu.

Regards.

---

### Post by The Real Dave on 2010-11-02
Perhaps this doesn't belong in the Cafe?

---

### Post by lisati on 2010-11-02
Hmmmm, interesting. 

It has been a while since I've done a complete fresh install (the last was with a pre Maverick release), but don't recall *any* installations downloading updates as part of the installation. Unless, of course, I blinked and missed something. :)

---

### Post by NightwishFan on 2010-11-02
I think the single mp3 option is free of patent issues where the other is not.

Edit: Lisati, there is a new checkbox to do so as part of Maverick.

---

### Post by _outlawed_ on 2010-11-02
It does download updates for me at the end like usual, as that is when my ethernet light on my laptop starts going blinking crazy with activity.

---

### Post by MasterNetra on 2010-11-02
> **grahammechanical said:**
> I did not check download updates during install. I checked download restricted drivers and something happened.

When I went on to the BBC website to check the news the videos on the pages began playing. I could also use BBC iplayer to watch TV programs that had already been shown on terrestrial TV. This did not happen before because I did not have 64 bit installed. So, I guess 64 bit flash was one of the things downloaded.  It was a nice surprise. It is a nice touch to the installation process although I am not sure if a first time user would know what they were being asked to approve of unless they had already done some research about Linux and Ubuntu.

Regards.

The "restricted driver" Ubuntu's offers is only a mp3 driver. The stuff you get from restricted extras removes this in favor of the driver(s) it selects.

---

### Post by MasterNetra on 2010-11-02
> **lisati said:**
> Hmmmm, interesting. 

It has been a while since I've done a complete fresh install (the last was with a pre Maverick release), but don't recall *any* installations downloading updates as part of the installation. Unless, of course, I blinked and missed something. :)

Maverick gives you a option to download updates as apart of the installation. Installation is different in Maverick then its predecessors. Though they removed the "use the largest continuous free space" option when handling the partitioning. A wag of the finger at them for that.

---

### Post by Khakilang on 2010-11-02
I install Maverick on another hard disk for testing and I have to do updates manually. Everything works fine for me.

---

### Post by Oxwivi on 2010-11-03
> **MasterNetra said:**
> It will download and install that mp3 plugin you can choose to have install ,*which gets booted if you later install the restricted extras, as such I don't bother with that*, that might of been what you seen downloaded and installed? They should at least add the download & install of the restricted extras preferably it replacing that single mp3 option. I know Kubuntu does that. Which I give it props for. 
 After all one of my biggest complaints is that Ubuntu hasn't really made any effort to even have the ubuntu-restricted-extras package made known let alone present the option to install it for new users. I mean unless someone does their install for them or lets them know about it how are they suppose to know they can get the bulk of their codecs + flash (and I think java) in one package selection?
No, I did not check the box to get the codecs, it installs OpenJDK, which I do not like. I'd rather download the codecs on the go, when they're needed then deal with removing and installing Java things. ZI think I should make a new thread about ubuntu-restricted-extras installing OpenJDK instead of Sun Java.

---

### Post by MasterNetra on 2010-11-05
> **Oxwivi said:**
> No, I did not check the box to get the codecs, it installs OpenJDK, which I do not like. I'd rather download the codecs on the go, when they're needed then deal with removing and installing Java things. ZI think I should make a new thread about ubuntu-restricted-extras installing OpenJDK instead of Sun Java.

Well you could remove OpenJDK and install SunJava, the package still makes it easier to install the codecs even inspite of OpenJDK.

---

