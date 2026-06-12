---
title: "ubuntuzilla fails to install firefox behind proxy"
date: 2009-10-08
forum: Ubuntuzilla
---

### Post by shankhs on 2009-10-08
hi,
uzilla fails to install firefox behind proxy.I am trying for past 1 hr but with no success.

I googled and got a few stuffs:
```
/* w3m doesnt work*/
 w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/
w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
/*not even with proxy specified though it works with google.com!!! I tried with every mirror*/
 w3m -pauth user:pass ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/
w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
```

Here is the debug info from ubuntuzilla:

```

shankhs@shankhs-desktop:~/sources/ubuntuzilla$ ubuntuzilla.py -a install -p firefox -d
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

I think its because I am behind proxy which requires username and password.
Is there any workaround.
Thanx for your help.

---

### Post by nanotube on 2009-10-08
Hi

try setting the ftp_proxy variable in the ~/.w3m/config file, as
```
ftp_proxy=http://user:pass@host:port
```

assuming your proxy allows ftp... which you could test by pointing your firefox to some ftp:// location (such as [ftp://mozilla.isc.org/](ftp://mozilla.isc.org/) )

hope that helps :)

---

### Post by shankhs on 2009-10-09
No help dude i dont think w3m can download using ftp though http is working in w3m so any workaround in the script to download ff using http and not ftp?
Can anybody please tell me where is ubuntuzilla.py installed

---

### Post by nanotube on 2009-10-12
hey
well, there's nothing built-in... but i suppose you could try editing the script and changing ftp:// to [http://.](http://.)..

the script lives in /usr/local/bin/ubuntuzilla.py
(which you can confirm by running "which ubuntuzilla.py")

---

### Post by KoZo on 2009-12-21
Hi,

I have the same problem (under KK) with latest version of Ubunzilla.
I have tried changing every "ftp" by "http" in the script but then I got "Download error".

For info I installed Ubunzilla with the deb file as I was not able to get the gpg file from server. Error was:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requête de la clé C1289A29 du serveur hkp keyserver.ubuntu.com
gpgkeys: key C1289A29 not found on keyserver
gpg: aucune donnée OpenPGP valide n'a été trouvée.
gpg: Quantité totale traitée: 0
```

It's in French but I think you will understand ;)

I don't think the issue is related to Ubunzilla, but if someone has an idea...

Cheers,

KoZo

---

### Post by nanotube on 2009-12-21
well, if your proxy server prohibits anything but port 80, your best bet would be to just use a more manual method of installing firefox. here is a good set of instructions:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by nanotube on 2009-12-31
Update: now ubuntuzilla has a repository of actual mozilla builds of firefox, thunderbird, and seamonkey. so you can just add the repository and its signing key, then install the mozilla-build packages using standard methods.

---

