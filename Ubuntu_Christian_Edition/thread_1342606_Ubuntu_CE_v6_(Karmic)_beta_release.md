---
title: "Ubuntu CE v6 (Karmic) beta release"
date: 2009-11-30
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-11-30
One problem with Ubuntu Karmic release is a bug in dansguardian.
But don't worry, Ubuntu CE v6, based on Karmic, comes with dansguardian enable and fully functional.

In addition to that, now dansguardian gui makes internet and filtering sharing easy.
With just a few clicks, you would be able to share internet connection to your LAN, with or without internet filtering.

There is a major change in e-Sword installer as well, it now uses wine stable (1.0.1) instead of wine development (beta).
This would make e-Sword run even more stable than before.

Wine stable would also make it possible to support wine christian
repository easily.

In addition to the desktop edition, we have also released a server
edition. Three important packages included in the server edition are 
Churchinfo(church management software), Christian Website in a Box (webhosting),
and prayerboard (software to manage prayer requests). The server
edition is released as a live cd to facilitate easy installation.

For details of server edition, check below post:

[http://ubuntuforums.org/showthread.php?t=1240859](http://ubuntuforums.org/showthread.php?t=1240859)

Now the desktop version is available in 32 bit and 64 bit versions!!!!

[Download Here]("http://ubuntuce.com/download.htm")
[Installation Instructions Here]("http://ubuntuce.com/convert.htm")

Start from this release, the desktop version would be live DVD instead of live CD.
This is to include OpenOffice as it is the most popular linux office suite.

---

### Post by david_kt on 2009-12-04
Somebody with nickname beginlinux has written a review about Ubuntu CE 

[http://beginlinux.wordpress.com/2009/12/03/ubuntu-ce-dansguardian-fi/](http://beginlinux.wordpress.com/2009/12/03/ubuntu-ce-dansguardian-fi/)


It is a positive review overall.

I would like to hear negative reviews as well if happen to have, or happen to read somewhere, so as to make more improvements in the future.

DK

---

### Post by ericd8027 on 2010-01-02
I have converted from generic Karmic to Karmic CE.  Upon doing so, when I try to set up DG through DG GUI, I go through the following process and am unable to connect to the internet through Firefox or Chrome.

1) Click on System
2) Click on Administration
3) Click on Dansguardian GUI

*When GUI is open, I 
4) Click Autoconfigure/Reset Dansguardian and Tinyproxy.  
5) Click on both "ok" prompts.

*At this point, whenever I try to load any web page it perpetually spins unable to load anything.

This is immaterial of changing "Filter Setting" to any of the presets or custom setting or any other changes.  

Beyond this, when I try to enter into any of the lists for further enhancement of DG, all the fields are blank.

Lastly, when viewing the GUI the Status of the different options are:

Redirection: ON
Tinyproxy: ON
Dansguardian: OFF
Internet Sharing: OFF


Any and all help is greatly appreciated.

Thanks

Eric

---

### Post by david_kt on 2010-01-02
> **ericd8027 said:**
> I have converted from generic Karmic to Karmic CE.  Upon doing so, when I try to set up DG through DG GUI, I go through the following process and am unable to connect to the internet through Firefox or Chrome.

1) Click on System
2) Click on Administration
3) Click on Dansguardian GUI

*When GUI is open, I 
4) Click Autoconfigure/Reset Dansguardian and Tinyproxy.  
5) Click on both "ok" prompts.

*At this point, whenever I try to load any web page it perpetually spins unable to load anything.

This is immaterial of changing "Filter Setting" to any of the presets or custom setting or any other changes.  

Beyond this, when I try to enter into any of the lists for further enhancement of DG, all the fields are blank.

Lastly, when viewing the GUI the Status of the different options are:

Redirection: ON
Tinyproxy: ON
Dansguardian: OFF
Internet Sharing: OFF


Any and all help is greatly appreciated.

Thanks

Eric

Try:
```

sudo apt-get update
sudo apt-get upgrade
```

and then restart your computer.

DK

---

### Post by stlsaint on 2010-01-03
YYEESSS....downloading now/testing soon!! thanks as always DK!!! hoping to put this in church system if all goes well with it!

---

### Post by ericd8027 on 2010-01-03
I ran the code in terminal.  Had both updates and upgrades.  After reseting my computer, there is still no change.  Both Google Chrome AND Firefox are unable to reach any webpage after running "autoconfigure".  Only able to reach pages after turning off DG.

---

### Post by david_kt on 2010-01-03
> **ericd8027 said:**
> I ran the code in terminal.  Had both updates and upgrades.  After reseting my computer, there is still no change.  Both Google Chrome AND Firefox are unable to reach any webpage after running "autoconfigure".  Only able to reach pages after turning off DG.

What is the out put of:
```

cat /etc/apt/sources.list.d/ubuntuce.list
```

DK

---

### Post by ericd8027 on 2010-01-03
Output is:

deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_i386/

# PPA for Crosswire Packaging Team
deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main

---

### Post by david_kt on 2010-01-03
> **ericd8027 said:**
> Output is:

deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_i386/

# PPA for Crosswire Packaging Team
deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) karmic main

Try to download and install below manually:
```

http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian_2.11.9.7-2ubuntu1_i386.deb
```

The dansguardian status should be on if it is running.

DK

---

### Post by ericd8027 on 2010-01-05
Reinstalled Dansguardian and then restarted, searched for upgrades and updates and still having the same problem.  Everything else runs amazing and I love it.  Is there a way to go back to the clean 9.10 without rebuilding the OS and trying again?  Or do you still have tricks up your sleeve?

---

### Post by stlsaint on 2010-01-05
considering i have never done it...theoretically all you need to do is remove the uce repos and key and you should only be left with karmic...again i have never done this myself so i cant speak on experience and i have no idea if it will work.

---

### Post by Anastasis on 2010-01-29
Any hopes of ever getting a Ubuntu CE NBR?

Just a hope of mine for a while now. I pretty much have my Netbook Remix tweeked out following CE, but it would be really nice to have a LiveCD of CE NBR. 

:)

please..

---

### Post by oneinch on 2010-01-29
I have though about trying trying to do a netbook remix of ubuntuCE but between work and school I really do not have a lot of time to mess with it.

---

### Post by Anastasis on 2010-01-29
> **oneinch said:**
> I have though about trying trying to do a netbook remix of ubuntuCE but between work and school I really do not have a lot of time to mess with it.

I do understand your plight. I'm really gonna try to see what I can put together this year on a NBR CE. I think it would be interesting. And as I use NBR now almost exclusively for day to day work, I might be able to fit it in some how.

BUT, I'm a total n00b. So don't have high hopes. I am but a learner.

:o

---

### Post by oneinch on 2010-01-30
Thats awesome man. It really would be nice to see a netbook remix of UbuntuCE

---

