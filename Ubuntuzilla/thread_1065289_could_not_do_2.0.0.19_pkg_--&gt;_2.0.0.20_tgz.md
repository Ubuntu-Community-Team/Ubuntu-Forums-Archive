---
title: "could not do 2.0.0.19 pkg --&gt; 2.0.0.20 tgz"
date: 2009-02-09
forum: Ubuntuzilla
---

### Post by SaintDanBert on 2009-02-09
I needed to update to 2.0.0.20 -- deliberately avoiding v3x -- and tried UbuntuZilla without success.

I answered "no" to the default update selection of v3.0.6.  As stated in the HOWTO, I had firefox-2.0.0.20.tar.gz (named as downloaded) in /tmp. 

After my answer, I was asked to name my own version when I typed "2.0.0.20".

The script ran and asked if I wanted to proceed with v3.0.6 without mention of the 2.0.0.20 that I had named.  When I said, "no" I got errors instead of a clean exit.
QUESTION: How to clean-up after a script failure?
COMMENTARY: I know that you need the messages. Sorry, they flashed off screen before I could catch them. (You should have enough to repeat without my reprise, but I will if you must have that.)

Running "dpkg --list | grep firefox" reports that firefox-3.0.6 has a "residual config" status.
As a minimum, I thought "no" meant "NO."
QUESTION: Why did the script do anything with this revision when I said "no" twice when asked?
QUESTION: What to do about hanging package install?

Perhaps I needed to type the package name instead of just the version numbers:  "firefox-2.0.0.20" rather than "2.0.0.20"?

SUGGESTION: Perhaps the script might look in the current folder for package tar balls in addition to /tmp. ADDITIONAL: Perhaps the script might prompt and ask, "Path(s) to search for update tar ball?"

Comments and suggestions would be welcome.

---

### Post by nanotube on 2009-02-10
Hi,
Well... i just to double check, i just ran it and told it "no" for the version, and entered 2.0.0.20, and everything went smoothly. it picked up the ff2, downloaded it, verified signature, etc.

so... my guess is that either you did something weird with the input, or are misinterpreting the output.

please try running it again, and post the complete output of your session. (increase the terminal's scrollback buffer if you don't have enough, to make sure you get it all).

also please tell me what version of ubuntu you are running and what firefox packages you have installed prior to running ubuntuzilla.

also note that it will install the mozilla build /next to/ the ubuntu build, and /will/ make sure that the ubuntu firefox package is installed. so it will try to install ff3 from the repos if it's not installed. ignore that, let it do it's thing, and then enjoy your mozilla-build ff2 after it is done.

---

### Post by SaintDanBert on 2009-02-11
So I tried again and did not get any errors, but
things are still not quite right.

In /usr/bin, I have several firefox images:

"firefox" links to /opt/firefox/firefox

"firefox-2" links to ../lib/firefox/firefox-2

"firefox-3.0" links to ../lib/firefox-3.0.6/firefox,sh

"firefox.ubuntu" links to firefox-3.0

From a shell, I can query -version and each reports exactly as I would expect. Specifically:

localhost $ firefox  -version
Mozilla Firefox 2.0.0.20, Copyright ...
... (c) 1998 - 2008 mozilla.org

If I then arrange a desktop launcher using:
"/usr/bin/firefox %u" as the command, even though
I get a browser window, Help-->About continues to report  "Firefox v2.0.0.19"

Also, I cannot launch the -ProfileManager option.

~~~ 0;-/

---

### Post by SaintDanBert on 2009-02-11
Here is the log of ubuntuzilla running:

=====================================================
==============================================================================
root@mumbles: # /usr/local/bin/ubuntuzilla.py

Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.6. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))



If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': n



If no version shows, or it does not agree with the latest version as listed on [http://www.mozilla.org](http://www.mozilla.org), please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) and let us know.
In the meantime, if you want to proceed with installation, you have the option of looking up the latest version yourself on the [http://www.mozilla.org/](http://www.mozilla.org/) website, and entering it here by hand.

Please enter the latest version of Firefox: 2.0.0.20



Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. bg
  4. ca           5. cs           6. da           7. de
  8. el           9. en-GB       10. en-US       11. es-AR
 12. es-ES       13. eu          14. fi          15. fr
 16. fy-NL       17. ga-IE       18. gu-IN       19. he
 20. hu          21. it          22. ja          23. ka
 24. ko          25. ku          26. lt          27. mk
 28. mn          29. nb-NO       30. nl          31. nn-NO
 32. pa-IN       33. pl          34. pt-BR       35. pt-PT
 36. ro          37. ru          38. sk          39. sl
 40. sv-SE       41. tr          42. uk          43. zh-CN
 44. zh-TW
Enter your choice of localization (integer, from 0 to 44): 10
You have chosen localization en-US. Is that correct [y/n]?
Please enter 'y' or 'n': y




Updating repositories information with apt-get update. You may be prompted for your password.

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://users.fulladsl.be](http://users.fulladsl.be) hardy-printing Release.gpg
Ign [http://users.fulladsl.be](http://users.fulladsl.be) hardy-printing/bugtriage Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Get:1 [http://users.fulladsl.be](http://users.fulladsl.be) hardy-printing Release [1303B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Ign [http://users.fulladsl.be](http://users.fulladsl.be) hardy-printing/bugtriage Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Hit [http://users.fulladsl.be](http://users.fulladsl.be) hardy-printing/bugtriage Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 1B in 2s (0B/s)
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  firefox-3.0
Suggested packages:
  firefox-3.0-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed:
  firefox firefox-3.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1137kB of archives.
After this operation, 3793kB of additional disk space will be used.

Do you want to continue [Y/n]? y



Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-3.0 3.0.6+nobinonly-0ubuntu0.8.04.1 [1071kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox 3.0.6+nobinonly-0ubuntu0.8.04.1 [66.0kB]
Fetched 1137kB in 2s (419kB/s)
Selecting previously deselected package firefox-3.0.
(Reading database ... 312776 files and directories currently installed.)
Unpacking firefox-3.0 (from .../firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb) ...
Setting up firefox-3.0 (3.0.6+nobinonly-0ubuntu0.8.04.1) ...
Please restart all running instances of Firefox-3.0, or you will experience problems.

Setting up firefox (3.0.6+nobinonly-0ubuntu0.8.04.1) ...

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-2.0.0.20.tar.gz

Downloading Firefox archive from the Mozilla site

--17:03:07--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz)
           => `firefox-2.0.0.20.tar.gz'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.20.tar.gz ... done.
Length: 9,710,348 (9.3M) (unauthoritative)

100%[==============================================>] 9,710,348    228.28K/s    ETA 00:00

17:03:44 (263.74 KB/s) - `firefox-2.0.0.20.tar.gz' saved [9710348]

Downloading Firefox signature from the Mozilla site

--17:03:44--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc)
           => `firefox-2.0.0.20.tar.gz.asc'
Resolving releases.mozilla.org... 129.101.198.59, 64.50.236.52, 204.246.0.136, ...
Connecting to releases.mozilla.org|129.101.198.59|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US ...

No such directory `pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--17:03:47--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc)
           => `firefox-2.0.0.20.tar.gz.asc'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.20.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[==============================================>] 186           --.--K/s

17:03:48 (5.01 KB/s) - `firefox-2.0.0.20.tar.gz.asc' saved [186]

tru::1:1217537640:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: key 812347DD: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 2
gpg:               imported: 2
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Thu 18 Dec 2008 02:09:52 AM CST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
Trying to determine firefox plugin path...

Linking plugins

Linking dictionaries

Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 2.0.0.20 has been installed successfully.



Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n]
Please enter 'y' or 'n': y



no crontab for root
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.

root@mumbles: # 
=================================================================

---

### Post by SaintDanBert on 2009-02-11
I'm dashed if I can find why I get one version string from an image launched from the shell and a different version string from the Help->About dialog.

Is this a bug within Firefox 2.0.0.20?

Really REALLY **REALLY** troubled,
~~~ 0;-/

---

### Post by nanotube on 2009-02-12
> **SaintDanBert said:**
> I'm dashed if I can find why I get one version string from an image launched from the shell and a different version string from the Help->About dialog.

Is this a bug within Firefox 2.0.0.20?

Really REALLY **REALLY** troubled,
~~~ 0;-/

unlikely that they forgot to update the version string... more likely is that you already have ff .19 running, and that's why it just opens a new window of existing process.

make sure that you have exited all other firefoxes before starting it! otherwise it will just open a new window of already-open firefox, and if you happen to have .19 already open, that's what you'll get!

that would also explain why -ProfileManager doesn't work, if you already have firefox open, it will just open a new window.

---

### Post by SaintDanBert on 2009-02-18
I could not find a running FF process, but a reboot cleared things up.
Now I get v2.0.0.20 everywhere I expect it.

Now if it were not so hard to find and use v2x add-ins on the FF v3x
oriented web site, I'd be happier still.

Thanks,
~~~ 0;-D

---

### Post by nanotube on 2009-02-24
cool. :)

---

