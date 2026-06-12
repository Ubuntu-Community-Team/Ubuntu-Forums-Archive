---
title: "[SOLVED] Ubuntuzilla can't download Firefox"
date: 2007-10-22
forum: Ubuntuzilla
---

### Post by IanVonSpeedfreak on 2007-10-22
I keep getting this error message when I try to install Firefox with Ubuntuzilla.  
> Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
I really don't get it, I can't find any other problem like this on the forums.  So is this something that I'll actually be able to try again later, or could there be any other reason why this is happening?

Any help is appreciated.

---

### Post by nanotube on 2007-10-22
> **IanVonSpeedfreak said:**
> I keep getting this error message when I try to install Firefox with Ubuntuzilla.  

I really don't get it, I can't find any other problem like this on the forums.  So is this something that I'll actually be able to try again later, or could there be any other reason why this is happening?

Any help is appreciated.

at what point is the failure coming up? downloading firefox? downloading firefox gpg signature? just post the complete output of the script here, and we'll go from there... :)

---

### Post by IanVonSpeedfreak on 2007-10-22
```
Welcome to the Ubuntuzilla Firefox script version 4.4.3

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 2.0.0.8. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': y
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
 40. sv-SE       41. tr          42. zh-CN       43. zh-TW

Enter your choice of localization (integer, from 0 to 43): 10
You have chosen localization en-US. Is that correct [y/n]?
Please enter 'y' or 'n': y
Password:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://mirror.noreply.org](http://mirror.noreply.org) dapper Release.gpg [189B]
Get:7 [http://www.virtualbox.org](http://www.virtualbox.org) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://mirror.noreply.org](http://mirror.noreply.org) dapper Release
Hit [http://www.virtualbox.org](http://www.virtualbox.org) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://mirror.noreply.org](http://mirror.noreply.org) dapper/main Packages
Ign [http://www.virtualbox.org](http://www.virtualbox.org) dapper/non-free Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://www.virtualbox.org](http://www.virtualbox.org) dapper/non-free Packages
Ign [http://mirror.noreply.org](http://mirror.noreply.org) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://mirror.noreply.org](http://mirror.noreply.org) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://mirror.noreply.org](http://mirror.noreply.org) dapper/main Sources
Fetched 7B in 4s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  firefox-gnome-support latex-xft-fonts libthai0
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7970kB of archives.
After unpacking 23.6MB of additional disk space will be used.
Selecting previously deselected package firefox.
(Reading database ... 307523 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1_i386.deb) ...
Setting up firefox (1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1) ...


Old firefox preferences not found. Nothing to back up. Proceeding with installation.


Downloading Firefox archive from the Mozilla site

--23:48:07--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.214, 64.50.238.52, ...Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9674559 ... done.
==> RETR firefox-2.0.0.8.tar.gz ... done.
firefox-2.0.0.8.tar.gz: Permission denied
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--23:48:10--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 64.12.204.21, 64.50.236.214, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9674559 ... done.
==> RETR firefox-2.0.0.8.tar.gz ... done.
firefox-2.0.0.8.tar.gz: Permission denied
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--23:48:13--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 156.56.247.196, 204.152.184.113, 64.12.204.21, ...
Connecting to releases.mozilla.org|156.56.247.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9674559 ... done.
==> RETR firefox-2.0.0.8.tar.gz ... done.
firefox-2.0.0.8.tar.gz: Permission denied
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--23:48:16--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 64.50.238.52, 156.56.247.196, 204.152.184.113, ...
Connecting to releases.mozilla.org|64.50.238.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9674559 ... done.
==> RETR firefox-2.0.0.8.tar.gz ... done.
firefox-2.0.0.8.tar.gz: Permission denied
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--23:48:20--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 64.50.236.214, 64.50.238.52, 156.56.247.196, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9674559 ... done.
==> RETR firefox-2.0.0.8.tar.gz ... done.
firefox-2.0.0.8.tar.gz: Permission denied
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
```

Sorry, usually I'm a bit more investigative, but I'm just really tired and really want this to work, haha.  So yeah, that's the entire output from the script.  I just wish I knew how to put all that script in a table so you could just scroll through and it wouldn't take up so much space.  Thank you, by the way ^__^,

---

### Post by nanotube on 2007-10-22
aha, so the problem appears to be a "permission denied" error... now the question is whether it's permission denied at the remote server, or locally... let's try to cover all bases here:

what happens if you run this command from your home dir:
```
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz
```

and, what happens if you run these commands:
```
cd /tmp
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz

```

and what's your output of 
```
 ls -ald /tmp
```

oh, and btw, to put things into a nice scrollable box, put it into  tags (the # button in the toolbar of the edit box for the post will do it for you, too).

---

### Post by IanVonSpeedfreak on 2007-10-22
output of wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)

```
--00:22:34--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.214, 64.50.238.52, ...Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.8.tar.gz ... done.
Length: 9,674,559 (9.2M) (unauthoritative)

100%[====================================>] 9,674,559    600.70K/s    ETA 00:00

00:22:50 (598.13 KB/s) - `firefox-2.0.0.8.tar.gz' saved [9674559]
```

output of /tmp$ wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz)

```
--00:23:40--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.214, 64.50.238.52, ...Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-US ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9674559 ... done.
==> RETR firefox-2.0.0.8.tar.gz ... done.
firefox-2.0.0.8.tar.gz: Permission denied
```

output of ls -ald /tmp

```
drwxrwxrwt 13 root root 552960 2007-10-21 23:48 /tmp
```

So, I'm guessing this means I'll have to change the permissions of said tmp folder?

edit: so okay, I think I've fixed it, the script completed successfully when I changed the ownership of "/tmp/firefox-2.0.0.8.tar.gz" and "/tmp/firefox-2.0.0.8.tar.gz.asc" to myself rather than root.  If I have any further problems, I'll be sure to let you know.  Once again, I must thank you for your assistance nanotube, I also must thank for this useful little script you've provided us all with (in that case I guess thanks are also an order for aysiu?).

---

### Post by nanotube on 2007-10-22
well, this is kind of weird... it seems the problem is with /tmp permissions, but the output of ls -ald shows that permissions are as they should be...

when you are in /tmp, can you create a new file? run command:
```
touch anewfile
```
and see if it gets created.

also, just for the hell of it, try running
```
sudo chmod 1777 /tmp
```
and see if that helps...

---

### Post by IanVonSpeedfreak on 2007-10-22
> well, this is kind of weird... it seems the problem is with /tmp permissions, but the output of ls -ald shows that permissions are as they should be...

when you are in /tmp, can you create a new file? run command:

```
touch anewfile
```

and see if it gets created.

The file was created... I'm wondering if it was the individual permissions of Fx and the Fx key that caused the problem.  In any case, changing those permissions solved the problem, in fact, I'm running the newly installed Fx right this minute.  All seems to be well, I just wish I knew where aysiu put all those recommended extensions for Fx he had on his page :confused:.

---

### Post by nanotube on 2007-10-22
hmm, so that chmod command did the trick? that's cool. :) that was a pretty weird problem, though... 

as to useful extensions...
don't know if aysiu ever had a list like that on his page (maybe he'll chime in?), but you could take a look at the list on the ubuntuzilla page: [http://ubuntuzilla.wiki.sourceforge.net/#tochome16](http://ubuntuzilla.wiki.sourceforge.net/#tochome16)

---

### Post by IanVonSpeedfreak on 2007-10-22
Not to harsh your buzz or anything, but once I noticed the output of one of your earlier commands, I decided to take matters in my own hands and chown both the firefox tarball and its key to myself.  I'm guessing your solution would probably have worked just as well :).  I suppose I'll try those add-ons, I'll have to remember what pages to whitelist, though, haha.  I also found aysiu's recommended add-ons, they're on his other blog (not the Ubuntu one).
[http://ubuntucat.wordpress.com/category/web-browsers/page/2/](http://ubuntucat.wordpress.com/category/web-browsers/page/2/)
Oh yeah, and thank you once again!

---

### Post by nanotube on 2007-10-22
enjoy your firefox! :)

---

