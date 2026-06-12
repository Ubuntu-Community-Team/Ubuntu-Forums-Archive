---
title: "firefox update??"
date: 2005-09-22
forum: Server Platforms
---

### Post by John.Michael.Kane on 2005-09-22
Has the firefox update been added to the repo's??

---

### Post by KingBahamut on 2005-09-22
I dont think so. 
no.

---

### Post by John.Michael.Kane on 2005-09-22
Thanks KingBahamut.......

---

### Post by Technoviking on 2005-09-22
I imagine there will be either an offical updated version of Firefox 1.0.6 with the IDN patched or new version of Firefox 1.0.7. I tried to make a backport of 1.0.7 but it is too dependent on Cario for me to work around.

Mike

---

### Post by jimcooncat on 2005-09-22
I guess I was confused by this in thinking this new vulnerability was taken care of. I was living in the past?

 [USN-181-1] Mozilla products vulnerability
================================================== =========
Ubuntu Security Notice USN-181-1 September 12, 2005
mozilla, mozilla-thunderbird, mozilla-firefox vulnerabilities
CAN-2005-2871
================================================== =========

[http://ubuntuforums.org/showthread.php?t=64868](http://ubuntuforums.org/showthread.php?t=64868)

---

### Post by XDevHald on 2005-09-22
I'm running 1.0.7 from the ubuntu archives in breezy, anyone else running breezy that has these updates for firefox?

P.S it's stable but a little laggy on a few edges of the menu list drop down in firefox, everything else is pretty much clean and it loads faster with a faster response to the websites.

---

### Post by John.Michael.Kane on 2005-09-23
Firefox 1.07 has been added to the 5.04 repo's

---

### Post by brentroos on 2005-09-23
*

---

### Post by TristanMike on 2005-09-23
Here's what I ended up doing:

First I opened my System Monitor and ended all instances of firefox, there was only 1.

Then I commented out my Backports with a "#" in front of each line(in my case I only had 2) by editing my sources.list ```
sudo gedit /etc/apt/sources.list
```Then I did a```
sudo apt-get update
```Next I opened Synaptic and searched for "firefox" and I had 5 entries (I know some who only have 3). So I```
sudo apt-get remove --purge firefox firefox-gnome-support mozilla-firefox mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
```These were all the five entries that I had.

Next I did a ```
sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
```And everything worked fine, all my bookmarks cookies, etc. even my extentions and themes. That is, because I believe they are contained in your home folder and this doesn't touch those. I can't say it will work for everyone, but it already has helped 2 people and hopefully it puts you on the right track. :) 

Hope this helped.

---

### Post by brentroos on 2005-09-24
*

---

### Post by Agent86 on 2005-09-24
I wanted to add that I had almost exactly the same problem as brentroos after trying to upgrade Firefox using the Ubuntu Update Manager (I actually had two errors instead of brentroos's one), and Firefox would not open.

TristanMike's fix worked perfectly! Thanks!

---

### Post by niobe_logos on 2005-09-24
> Hope this helped.
It sure did. Another thank you from a frustrated Firefox user. When folks say they want Linux applications to behave more like Windows apps, I don't think this is what they had in mind...

---

### Post by Indigo2 on 2005-09-24
[QUOTE=TristanMike]Here's what I ended up doing:

First I opened my System Monitor and ended all instances of firefox, there was only 1.

Then I commented out my Backports with a "#" in front of each line(in my case I only had 2) by editing my sources.list ```
sudo gedit /etc/apt/sources.list
```Then I did a```
sudo apt-get update
```Next I opened Synaptic and searched for "firefox" and I had 5 entries (I know some who only have 3). So I```
sudo apt-get remove --purge firefox firefox-gnome-support mozilla-firefox mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
```These were all the five entries that I had.

Next I did a ```
sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
```And everything worked fine, all my bookmarks cookies, etc. even my extentions and themes. That is, because I believe they are contained in your home folder and this doesn't touch those. I can't say it will work for everyone, but it already has helped 2 people and hopefully it puts you on the right track. :) 

Hope this helped.[/QUOTE]

I tried your method and the problem is that when I try to remove firefox, it tried to remove the following packages:

epiphany-browser
epiphany-browser-dev
epiphany-extensions
firefox
firefox-gnome-support
gnome-core
gnome-desktop-environment
gnome-fifth-toe
mozilla-firefox-gnome-support
ubuntu-desktop
yelp

Is there a way to get around this?

Secondly, when I try to upgrade it through the ubuntu update I get the following error message:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

Has anyone been able to get around these two things to upgrade firefox?

---

### Post by GriMsb on 2005-09-24
[QUOTE=TristanMike]
Hope this helped.[/QUOTE]

Thanks a lot.  I had the same problem and now it works.

---

### Post by TristanMike on 2005-09-24
[QUOTE=Indigo2]I tried your method and the problem is that when I try to remove firefox, it tried to remove the following packages:

epiphany-browser
epiphany-browser-dev
epiphany-extensions
firefox
firefox-gnome-support
gnome-core
gnome-desktop-environment
gnome-fifth-toe
mozilla-firefox-gnome-support
ubuntu-desktop
yelp

Is there a way to get around this?[/QUOTE]Hmm, I'm not sure. Are you using Gnome or KDE? At what stage did were you informed that these packages were going to be removed? Did you copy/paste the code in the terminal? > Secondly, when I try to upgrade it through the ubuntu update I get the following error message:........Those errors generated seem to be linked to the fact that firefox won't start. After I applied the fix, the updates went away and thus I no longer get those errors. What did you get when you searched "firefox" in Synaptic.

TM

---

### Post by Greyhair on 2005-09-24
[QUOTE=TristanMike]Here's what I ended up doing:

First I opened my System Monitor and ended all instances of firefox, there was only 1.

Then I commented out my Backports with a "#" in front of each line(in my case I only had 2) by editing my sources.list ```
sudo gedit /etc/apt/sources.list
```Then I did a```
sudo apt-get update
```Next I opened Synaptic and searched for "firefox" and I had 5 entries (I know some who only have 3). So I```
sudo apt-get remove --purge firefox firefox-gnome-support mozilla-firefox mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
```These were all the five entries that I had.

Next I did a ```
sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
```And everything worked fine, all my bookmarks cookies, etc. even my extentions and themes. That is, because I believe they are contained in your home folder and this doesn't touch those. I can't say it will work for everyone, but it already has helped 2 people and hopefully it puts you on the right track. :) 

Hope this helped.[/QUOTE]
 Worked a treat..............many thanks

---

### Post by mcarter on 2005-09-24
Ok, I installed the Firefox 1.0.7 (and the firefox-gnome-support update as well), and now my Firefox doesn't work at all.

Here's the error:
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

E:/var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

I tried deleting both of those files, it still reports the same error.

Two questions:  How do I fix this (aka how close to yesterday is a non-broken security update going to be released), and what is the source of the problem?

Mark

---

### Post by Indigo2 on 2005-09-25
[QUOTE=TristanMike]Hmm, I'm not sure. Are you using Gnome or KDE?[/quote]

Gnome

> At what stage did were you informed that these packages were going to be removed?

When I did it through the command line, it started removing the list I posted above.  When I did it through Synaptic, it warned me that the packages I mentioned above will be removed.

> Did you copy/paste the code in the terminal?

yes.

> Those errors generated seem to be linked to the fact that firefox won't start.

I didn't even get a chance to upgrade the package for firefox to see if it's going to start or not.

> After I applied the fix, the updates went away and thus I no longer get those errors. What did you get when you searched "firefox" in Synaptic.


it brought me up several entries of firefox (e.g. firefox, mozilla-firefox, firefox-gnome), including the 1.0.6 that I had installed with 1.0.7 as the one available.

---

### Post by Abd-al-Karim on 2005-09-25
Firstly thanks a lot to TristanMike for the fix it has (basically) fixed my system again :).

I had the following error messages:

> **Error**

The following problems were found on your system:

```
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  
trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which
is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-
support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-
firefox/components/libmozgnome.so', which is also in package firefox-
gnome-support
```
so then I applied TM's fix instead of removing them by command line I tried synaptic but this gave me the error that the packages mentioned above (and quoted below) in Indigo2's post would have to be removed also.

[QUOTE=Indigo2]I tried your method and the problem is that when I try to remove firefox, it tried to remove the following packages:

epiphany-browser
epiphany-browser-dev
epiphany-extensions
firefox
firefox-gnome-support
gnome-core
gnome-desktop-environment
gnome-fifth-toe
mozilla-firefox-gnome-support
ubuntu-desktop
yelp

Has anyone been able to get around these two things to upgrade firefox?[/QUOTE]
So instead I used the command line, just like TM said because I thought this would be better since he had done it it that way, but none the less the aforementioned packages were also removed, although firefox was back in v. 1.0.7 :). So I went and installed the packages again through synaptic and now everything works fine, except that when I uncomment my backports again I get the following error when I go into synaptic:

> **Warning**

The following problems were found on your system:

```
W: Couldn't stat source package list http://ubuntu-
backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/
lists/ubuntu-backports.mirrormax.net_dists_hoary-
backports_main_binary-i386_Packages) - stat (2 No such file or
directory)
W: Couldn't stat source package list http://ubuntu-
backports.mirrormax.net hoary-backports/universe Packages (/var/lib/
[...]

```
It goes on, I get that for every repo I think so no need to post it all here, is there any problem with leaving my two backports commented out so I do not get this error?

---

### Post by TristanMike on 2005-10-01
[QUOTE=Abd-al-Karim]So I went and installed the packages again through synaptic and now everything works fine, except that when I uncomment my backports again I get the following error when I go into synaptic:
It goes on, I get that for every repo I think so no need to post it all here, is there any problem with leaving my two backports commented out so I do not get this error?[/QUOTE]This is because the "mirrormax" backports address has been completely removed, instead, you are to use ```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse
``` instead of ```
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
``` and as for the extra's it's recomended that you use a different mirror. Of course all that information can be found on the ["Backports"](http://www.ubuntuforums.org/forumdisplay.php?f=47) threads

---

### Post by kewa on 2005-10-13
Still very new to all this but learning all the time.

Followed TristanMike's excellent instructions to the letter but confused when the problem persisted e.g. the browser window wouldn't open.  However a system restart and all was well again and as you can tell I'm back on the net.  Brilliant!

Thanks a lot TristanMike!

Kewa

---

