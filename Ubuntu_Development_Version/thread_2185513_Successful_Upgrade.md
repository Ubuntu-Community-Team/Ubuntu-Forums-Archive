---
title: "Successful Upgrade"
date: 2013-11-03
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-11-03
I just did a successful upgrade to my netbook from Saucy to Trusty using:

```
do-release-upgrade -d
```

I had to try a couple of time, because the Canadian mirror doesn't seem to be completely up to date. Once I changed to the Main mirror, the upgrade went off without a hitch. I also changed the mirror from Canada to Main on my desktop system and found several updates that weren't showing previously.

For those not using the Main mirror, it may be an idea to switch to it, to benefit from all the latest updates.

---

### Post by sammiev on 2013-11-03
I just finish doing one on the Canadian Server about 30 min ago. I switched to the Main Server after reading your post and it showed I was fully updated. The one I upgraded was Ubuntu-Gnome.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
sudo update-manager -d
```

I will try this on my other install of Xubuntu to see if it upgrades from 13.10 to 14.04 tomorrow.

---

### Post by cariboo on 2013-11-03
Using:

```
sudo update-manager -d
```

gave me the same message, but it was just saying that 13.10 was up-to-date.

The do-release-upgrade command is what got me from 13.10 to 14.04, I'm running Ubuntu Gnome on my netbook. This is my experimental system.

---

### Post by zika on 2013-11-03
For UpdateManager to show/offer new version with switch &#8222;-d&#8220; You have to change its settings so that new version is allowed to be offered...

---

### Post by cariboo on 2013-11-03
From what I can see, update-mangler doesn't give you a choice to upgrade to a development version.

---

### Post by craig10x on 2013-11-03
> **cariboo907 said:**
> From what I can see, update-mangler doesn't give you a choice to upgrade to a development version.

However, the iso installer does (if you run a daily build iso and you are running only 1 ubuntu)...that is how i moved from 13.04 final into 13.10 development) it would work the same for moving from 13.10 to 14.04 development as well...

---

### Post by sammiev on 2013-11-03
Ok just upgraded Xubuntu from 13.10 to 14.04 and took screen shots as I was updating with the commands shown. Then I switched the the Canada server to the Main server. Works great for me. :)

```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
sudo update-manager -d
```

Then I switch to the Main serverr after I rebooted and ran this to see if any other updates were held back.

```
sudo apt-get update && sudo apt-get upgrade
```

Sorry the first 2 pictures are reversed.

---

### Post by craig10x on 2013-11-03
It's interesting...looking at your screenshots i see a window (picture #4) with information that i saw when i used the iso installer upgrade method... although with mine it also mentioned about installing previous applications and data...

So how did it turn out? everything carry over ok and is it running properly?

---

### Post by sammiev on 2013-11-03
> **craig10x said:**
> It's interesting...looking at your screenshots i see a window (picture #4) with information that i saw when i used the iso installer upgrade method... although with mine it also mentioned about installing previous applications and data...

So how did it turn out? everything carry over ok and is it running properly?

I never had trouble with this method and everything carried over with no problems. It just works.

---

### Post by zika on 2013-11-03
> **cariboo907 said:**
> From what I can see, update-mangler doesn't give you a choice to upgrade to a development version.
It does on my 13.10 install...

Update&#8321;: Mea culpa, I was going from the top down through the thread and I did not read [http://ubuntuforums.org/showthread.php?t=2185513&p=12837539#post12837539](http://ubuntuforums.org/showthread.php?t=2185513&p=12837539#post12837539) before I answered...

---

### Post by cariboo on 2013-11-03
> **zika said:**
> It does on my 13.10 install...

Update&#8321;: Mea culpa, I was going from the top down through the thread and I did not read [http://ubuntuforums.org/showthread.php?t=2185513&p=12837539#post12837539](http://ubuntuforums.org/showthread.php?t=2185513&p=12837539#post12837539) before I answered...

I learn something new every day :-), I refuse to use update-mangler any more, so I wasn't aware that it was possible to update to a Development Release.

---

### Post by sammiev on 2013-11-03
> **cariboo907 said:**
> I learn something new every day :-), I refuse to use update-mangler any more, so I wasn't aware that it was possible to update to a Development Release.

After reading that you refuse to use update-mangler any more I was thinking about using the method you use but again I was fully updated on the Canadian Server and you had to use the Main Server. Can the server issue be explained between the two methods? :)

---

### Post by Redalien0304 on 2013-11-03
got Cinnamon DE to to install & work on 14.04 used nightly

---

### Post by ventrical on 2013-11-04
By default all my installs go to Main Server. If I use Canada I have to set it manually.

---

### Post by Elfy on 2013-11-04
> **cariboo907 said:**
> I learn something new every day :-), I refuse to use update-mangler any more, so I wasn't aware that it was possible to update to a Development Release.

About the only reason I can see for using update mangler is to check that it works - which is about all I do with it :)

---

### Post by QDR06VV9 on 2013-11-04
> **Elfy said:**
> About the only reason I can see for using update mangler is to check that it works - which is about all I do with it :)

I tried update-mangler(lol) witch went off without a hitch_ except_ it changed the branding on a saucy partition (was not mounted) to Ubuntu Trusty Tahr (development branch)
Everything is still saucy but calls itself Trusty:o
All CLI from now on..
Regards

---

### Post by craig10x on 2013-11-04
update manager seems to work fine for final release versions, but perhaps can be tricky sometimes on development versions...

---

### Post by zika on 2013-11-04
> **craig10x said:**
> update manager seems to work fine for final release versions, but perhaps can be tricky sometimes on development versions...And we should admit that it was not conceived and developed for U+1 testing usage... ;)

---

### Post by xc3RnbFO8P on 2013-11-04
> **cariboo907 said:**
> I learn something new every day :-), I refuse to use update-mangler any more, so I wasn't aware that it was possible to update to a Development Release.

Not a native English speaking person, but with the help of Urban Dictionary I understand it completely  :)

---

### Post by cariboo on 2013-11-04
> **ventrical said:**
> By default all my installs go to Main Server. If I use Canada I have to set it manually.

I always set my location and Time Zone as Vancouver, and get the Canadian mirror by default. I'm sure geoip may have something to do with it, as I'm actually about 560Km (350 miles) north of Vancouver.

---

### Post by SurfaceUnits on 2013-11-05
I've used update-manger -d and -c for every upgrade since Gnome Shell Remix 12.04 and have found it to be very stable with no issues. Works with Studio as well.

---

### Post by kevpan8152 on 2013-11-05
> **cariboo907 said:**
> I just did a successful upgrade to my netbook from Saucy to Trusty using:```
do-release-upgrade -d
```I had to try a couple of time, because the Canadian mirror doesn't seem to be completely up to date. Once I changed to the Main mirror, the upgrade went off without a hitch. I also changed the mirror from Canada to Main on my desktop system and found several updates that weren't showing previously.For those not using the Main mirror, it may be an idea to switch to it, to benefit from all the latest updates.I all ready have switched to the main mirror Cariboo907, but thanks for suggesting it anyways. :-)

---

### Post by kevpan8152 on 2013-11-05
Upgrade was successful here too, although Sudo apt-get update and Sudo apt-get Dist-Upgrade left me at Saucy. Had to do an Update Manager -D to get it to Upgrade.

---

### Post by zika on 2013-11-05
> **kevpan8152 said:**
> Upgrade was successful here too, although Sudo apt-get update and Sudo apt-get Dist-Upgrade left me at Saucy. Had to do an Update Manager -D to get it to Upgrade.At this stage of U+1 development simple change in sources should leave You at Saucy... Remember magic words: &#8222;Debian way&#8220;... ;)

---

### Post by ventrical on 2013-11-05
> **cariboo907 said:**
> I always set my location and Time Zone as Vancouver, and get the Canadian mirror by default. I'm sure geoip may have something to do with it, as I'm actually about 560Km (350 miles) north of Vancouver.

  I always set my location for Toronto, ON and sometimes for Detroit, MI and I always get  Main Server by default. Also , when I  do a fresh install  Ubiquity usually chooses Rany River, ON Canada by default and that would put me in CST. In the past, if things have been rough, I have dowloaded my .isos from University of Waterloo and I have no idea if that would be a Canadian mirror. It seems to vary ... at times the Canadian servers will be ahead of main server and vis a versa.

---

### Post by Doug S on 2013-11-16
I have read this thread, a few times. I have my locale set as Vancouver, Canada. I thought I might save some time by trying the methods of this thread. For me, the upgrade to 14.04 development fails for both of the methods mentioned herein, both with the default download server and the main download server.

---

### Post by craig10x on 2013-11-16
Doug S: If you only run one version of ubuntu, there is another method of upgrading you can try...that would be to run a daily build iso live session of 14.04 and on the automatic options of the installer, it should offer you the option to UPGRADE instead of clean install...It does it directly from the iso and NOT through the internet like doing it on the update manager...it is also very fast (takes same time as a normal clean install)...
Again, the option would only be offered by the installer if you are just running one ubuntu...worth a try!

---

### Post by zika on 2013-11-17
> **Doug S said:**
> I have read this thread, a few times. I have my locale set as Vancouver, Canada. I thought I might save some time by trying the methods of this thread. For me, the upgrade to 14.04 development fails for both of the methods mentioned herein, both with the default download server and the main download server.
Did You try simply turning off extras and then indulge into upgrade?

---

### Post by Doug S on 2013-11-17
> **zika said:**
> Did You try simply turning off extras and then indulging into upgrade?No I didn't. Additionally, it is not clear to me what you mean. ? I searched for "extras" with additional guessed at key words on google, and extras on the desktop help. On the one installation, I only have added Ubtunu packages to be able to compile the official Ubuntu documentation. On another VM GNOME installation, I don't think I have anything other than a bare up to date 13.10 install.

@criag10x: Thanks for the suggestion, but my purpose was to try the methods given in this thread. However, I have now downloaded the daily ISO from yesterday, but will just create a new VM instead.

---

### Post by zika on 2013-11-17
> **Doug S said:**
> No I didn't. Additionally, it is not clear to me what you mean. ?I mean exactly what I've wrote. This early in testing that branch of repos is not available. There is a whole thread about thta. So, it is wise to turn them off in order to avoid any trouble possible. Not more, not less than that.

---

### Post by Doug S on 2013-11-17
Hi Zika: Sorry for being a little dense on this one. I understand your point. What I do not know is how to "turn them off".

---

### Post by howefield on 2013-11-17
Open a terminal and type the following..

```
gksudo gedit /etc/apt/sources.list
```

Put a # sign in front of the lines that contain the "extras" repository, save and close.

For me that would look like...
> ## deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
## deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

---

### Post by zika on 2013-11-17
> **Doug S said:**
> Hi Zika: Sorry for being a little dense on this one. I understand your point. What I do not know is how to "turn them off".A lot of ways to do that.
One is already given in a message above. Any editor would work.
Second is software-properties-gtk.
Third is...
And so on.

---

### Post by kansasnoob on 2013-11-17
> **Doug S said:**
> Hi Zika: Sorry for being a little dense on this one. I understand your point. What I do not know is how to "turn them off".

[http://ubuntuforums.org/showthread.php?t=2181769&page=2&p=12847285#post12847285](http://ubuntuforums.org/showthread.php?t=2181769&page=2&p=12847285#post12847285)

---

### Post by Doug S on 2013-11-17
O.K thanks for the replies. After editing sources.list as mentioned, the upgrade to 14.04 worked fine on both VMs, the regular desktop and GNOME.

---

