---
title: "failing to install Firefox from downloaded into /tmp tar.bz2"
date: 2009-10-14
forum: Ubuntuzilla
---

### Post by vanbak on 2009-10-14
Hello,

I am having a problem similar to the one [here]("http://ubuntuforums.org/showthread.php?t=834062"), updating Firefox 3.0.14 to version 3.5.3 using Ubuntuzilla 4.7.4.

I am behind a proxy, I have not even the slightest chance of changing. I can not connect to any ftp, whatsoever. Therefore, I downloaded the "firefox-3.5.3.tar.bz2", from the official Firefox site and put it in /tmp.

It seems, the script couldn't recognize the archive and unsuccessfully tried to connect to the mirrors.

As mentioned in another [thread]("http://ubuntuforums.org/showthread.php?t=832600"), I tried changing all "tar.gz" with "tar.bz2" in the "/usr/local/bin/ubuntuzilla.py", considering the difference in the tar call.

Another unsuccessful attempt, after reinstalling Ubuntuzilla, included downloading "firefox-3.5.3.linux-i686.en-US.tar.gz" and renaming it in /tmp to "firefox-3.5.3.tar.gz".
 
I would be very thankful for any piece of advice on this issue!
Van

P.S. The complete transcript of the ubuntuzilla session:
```
xyz@abc:~$ ubuntuzilla.py -a install -p firefox -d
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'install', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.

Welcome to the Ubuntuzilla Firefox script version 4.7.4

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Apt package name: firefox 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.3. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
[]
Retrieving list of available localizations for Firefox ...
w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
Failed to retrieve list of localizations. This may be due to transient network problems, so try again later. If the problem persists, please seek help on our website, http://ubuntuzilla.sourceforge.net/
```

---

### Post by nanotube on 2009-10-15
Hi
In that case, suggest you try the slightly more manual method as described here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

it basically does the same thing that ubuntuzilla does for you, the only thing that would be missing is auto update notifications (which you can use ubuntuzilla for anyway, since that's done over http.)

---

### Post by vanbak on 2009-10-15
nanotube,

thanks a lot for the quick response and for the flawlessly working solution!

all the best,
van

---

### Post by Niko Johnson on 2009-10-15
You can also try the add/remove section under your applications drop down menu. fire fox is in the internet section. or if you perfer the synatpic package manager, that can also be done to install firefox. but like all open source softwear its hard to pick your favorite, try using opera, its free and in my opinion a great browser. dont get me wrong firefox is great as well... but its always good to keep your eyes open to new things

---

### Post by nanotube on 2009-10-15
> **vanbak said:**
> nanotube,

thanks a lot for the quick response and for the flawlessly working solution!

all the best,
van

you're very welcome :)

---

### Post by vanbak on 2009-10-16
> **Niko Johnson said:**
> You can also try the add/remove section under your applications drop down menu. fire fox is in the internet section. or if you perfer the synatpic package manager, that can also be done to install firefox. but like all open source softwear its hard to pick your favorite, try using opera, its free and in my opinion a great browser. dont get me wrong firefox is great as well... but its always good to keep your eyes open to new things

Niko Johnson,

thank you for the alternative solution!

Firstly, I didn't really appreciate it. I spent so much time trying to get this update working - it felt like I wasted it. 

However, on the first place I wanted the update Firefox so badly, hoping it would fix some issues I had, playing videos. Sadly this was not the case and well... installing Opera, was actually a fine thing.

I still consider some of the Firefox' add-ons much better, than the widgets in Oper... nevertheless watching videos in Opera works perfect for me.

I suppose I would just use them both for now...

Thanks again,
Van

---

### Post by fencer on 2009-11-14
I do have the same issue here so bumping this message looking for someone to help us with this lil trouble

---

### Post by nanotube on 2009-11-15
> **fencer said:**
> I do have the same issue here so bumping this message looking for someone to help us with this lil trouble

does the solution proposed in the second post in this thread work for you?

---

### Post by dsmithnc on 2009-11-24
I'm curious to know whether or not this same approach would work with Thunderbird?

Dick

---

### Post by nanotube on 2009-11-24
> **dsmithnc said:**
> I'm curious to know whether or not this same approach would work with Thunderbird?

Dick

Hi
Yes you could use the psychocats firefox method for thunderbird just as well - just edit the actual command text to substitude 'thunderbird' for 'firefox' everywhere you see it.

But unless you have trouble with ftp access, you can also just use ubuntuzilla to install.

---

