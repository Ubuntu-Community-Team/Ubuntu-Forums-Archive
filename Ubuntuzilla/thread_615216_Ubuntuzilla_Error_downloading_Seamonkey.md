---
title: "Ubuntuzilla Error downloading Seamonkey"
date: 2007-11-16
forum: Ubuntuzilla
---

### Post by rungss on 2007-11-16
The Problem I am facing is pretty close to the one at the thread [http://ubuntuforums.org/showthread.php?t=586113](http://ubuntuforums.org/showthread.php?t=586113)

But I couldn't figure out how to resolve it.

I just started the Ubuntuzilla installation by following the terminal approach instruction at the main Ubuntuzilla Home Page 

[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

I checked my machine by the code 
```
uname -m
```
and it was 32 bit as in the instructions so I downloaded the file and saved it to the following location 
/home/rungss/storage/downloads/ubuntuzilla/ubuntuzilla-4.4.3-0ubuntu1-i386.deb

then I run 
```
sudo dpkg -i /home/rungss/storage/downloads/ubuntuzilla/ubuntuzilla-4.4.3-0ubuntu1-i386.deb
sudo apt-get install -f
```

When this was done I started to install the three Products in the order by entering the commands
```

ubuntuzilla.py -a install -p firefox
 
ubuntuzilla.py -a install -p thunderbird
 
ubuntuzilla.py -a install -p seamonkey
```

The installation of firefox and thunderbird worked fine but at Seamonkey When it asked to confirm that the latest version is 1.1.6 I made a mistake I had just been to teh SeaMonkey Site and I somehow had the version 1.1.7 in my mind as the latest version so I choose n on the Prompt and entered the version manually as 1.1.7 

I am copying the terminal output here but its not the entire content from the first step but I hope you'lll be able to figure out ther Problem.

```

12. fi          13. fr          14. ga-IE       15. he        
 16. hu          17. it          18. ja          19. ko        
 20. lt          21. mk          22. nb-NO       23. nl        
 24. nn-NO       25. pa-IN       26. pl          27. pt-BR     
 28. pt-PT       29. ru          30. sk          31. sl        
 32. sv-SE       33. tr          34. zh-CN       35. zh-TW     

Enter your choice of localization (integer, from 0 to 35): 8
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN                                          
Get:1 http://dl.google.com stable Release.gpg [189B]                                                                                                                  
Ign http://dl.google.com stable/non-free Translation-en_IN                                                                                                            
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                                      
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN                        
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN                                                    
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN                                              
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN                                                
Hit http://dl.google.com stable Release                                                                                 
Hit http://security.ubuntu.com gutsy-security Release                                                                   
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                                      
Hit http://dl.google.com stable/non-free Packages                                                                
Hit http://security.ubuntu.com gutsy-security/main Packages                                                      
Hit http://security.ubuntu.com gutsy-security/multiverse Packages                                                
Hit http://security.ubuntu.com gutsy-security/universe Packages                      
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                             
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_IN                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources                     
Hit http://security.ubuntu.com gutsy-security/main Sources                           
Hit http://security.ubuntu.com gutsy-security/multiverse Sources                     
Hit http://security.ubuntu.com gutsy-security/universe Sources                       
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_IN                     
Ign http://archive.ubuntu.com gutsy/universe Translation-en_IN 
Ign http://archive.ubuntu.com gutsy/main Translation-en_IN     
Get:4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_IN
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_IN
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_IN
Get:5 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_IN
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_IN
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_IN
Get:6 http://archive.ubuntu.com gutsy-proposed Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-proposed/restricted Translation-en_IN
Ign http://archive.ubuntu.com gutsy-proposed/main Translation-en_IN
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy-proposed/universe Translation-en_IN
Hit http://archive.ubuntu.com gutsy Release                    
Hit http://archive.ubuntu.com gutsy-updates Release            
Hit http://archive.ubuntu.com gutsy-backports Release                               
Hit http://archive.ubuntu.com gutsy-proposed Release                                
Hit http://archive.ubuntu.com gutsy/restricted Sources                              
Hit http://archive.ubuntu.com gutsy/main Sources               
Hit http://archive.ubuntu.com gutsy/multiverse Sources         
Hit http://archive.ubuntu.com gutsy/universe Sources           
Hit http://archive.ubuntu.com gutsy/multiverse Packages        
Hit http://archive.ubuntu.com gutsy/restricted Packages        
Hit http://archive.ubuntu.com gutsy/universe Packages          
Hit http://archive.ubuntu.com gutsy/main Packages              
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages      
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages  
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources 
Hit http://archive.ubuntu.com gutsy-updates/main Sources       
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources 
Hit http://archive.ubuntu.com gutsy-updates/universe Sources   
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://archive.ubuntu.com gutsy-backports/main Packages    
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://archive.ubuntu.com gutsy-backports/main Sources     
Hit http://archive.ubuntu.com gutsy-backports/multiverse Sources
Hit http://archive.ubuntu.com gutsy-backports/universe Sources 
Hit http://archive.ubuntu.com gutsy-proposed/restricted Packages
Hit http://archive.ubuntu.com gutsy-proposed/main Packages     
Hit http://archive.ubuntu.com gutsy-proposed/multiverse Packages               
Hit http://archive.ubuntu.com gutsy-proposed/universe Packages                 
Hit http://archive.ubuntu.com gutsy-proposed/restricted Sources                
Hit http://archive.ubuntu.com gutsy-proposed/main Sources                      
Hit http://archive.ubuntu.com gutsy-proposed/multiverse Sources                
Hit http://archive.ubuntu.com gutsy-proposed/universe Sources
Get:7 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_IN
Hit http://archive.canonical.com gutsy Release
Ign http://archive.canonical.com gutsy/partner Packages
Ign http://archive.canonical.com gutsy/partner Sources
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 7B in 5s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  comerr-dev libpcre3-dev libsqlite3-dev libkrb5-dev libapr1-dev libldap2-dev libdb4.4-dev uuid-dev libpq-dev libkadm55 libexpat1-dev libaprutil1-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mozilla-thunderbird
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 59.8kB of archives.
After unpacking 106kB of additional disk space will be used.
Get:1 http://security.ubuntu.com gutsy-security/main mozilla-thunderbird 2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10 [59.8kB]
Fetched 59.8kB in 2s (25.6kB/s)             
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 143372 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10_all.deb) ...
Setting up mozilla-thunderbird (2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10) ...

A Thunderbird profile has been found at ~/.mozilla-thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.mozilla-thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': n

OK, proceeding without backup.

Downloading Thunderbird archive from the Mozilla site

--04:43:31--  ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.9/linux-i686/en-US/thunderbird-2.0.0.9.tar.gz
           => `thunderbird-2.0.0.9.tar.gz'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.52, 64.50.238.52, ...
Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.9/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.9.tar.gz ... done.
Length: 1,14,48,335 (11M) (unauthoritative)

100%[===========================================================================================================================>] 1,14,48,335   32.97K/s    ETA 00:00

04:49:30 (31.66 KB/s) - `thunderbird-2.0.0.9.tar.gz' saved [11448335]


Downloading Thunderbird signature from the Mozilla site

--04:49:30--  ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.9/linux-i686/en-US/thunderbird-2.0.0.9.tar.gz.asc
           => `thunderbird-2.0.0.9.tar.gz.asc'
Resolving releases.mozilla.org... 130.239.18.158, 130.239.18.159, 155.98.64.83, ...
Connecting to releases.mozilla.org|130.239.18.158|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.9/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.9.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[===========================================================================================================================>] 186           --.--K/s             

04:49:38 (9.15 KB/s) - `thunderbird-2.0.0.9.tar.gz.asc' saved [186]

tru::1:1195254525:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1195254525:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2009-07-16::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2009-07-16:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2009-07-16:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Tuesday 13 November 2007 05:10:16 AM IST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8

Linking dictionaries


Linking launcher to new thunderbird

Adding `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'

The new Thunderbird version 2.0.0.9 has been installed successfully.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.

Would you like to set up automatic update checking for the official Mozilla build of Thunderbird (recommended)? This feature will regularly check for updates to Thunderbird, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.
rungss@rungss-ubuntu:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.4.3

This script installs the latest release of the official Mozilla build of Seamonkey on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be <li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': n

If no version shows, or it does not agree with the latest version as listed on http://www.mozilla.org, please visit our website at http://ubuntuzilla.sourceforge.net/ and let us know.
In the meantime, if you want to proceed with installation, you have the option of looking up the latest version yourself on the http://www.mozilla.org/ website, and entering it here by hand.

Please enter the latest version of Seamonkey: 1.1.7

Backing up old Seamonkey preferences


Downloading Seamonkey archive from the Mozilla site

--04:52:45--  ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
           => `seamonkey-1.1.7.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.52, 64.50.238.52, ...
Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.7 ... 
No such directory `pub/mozilla.org/seamonkey/releases/1.1.7'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--04:52:49--  ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
           => `seamonkey-1.1.7.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 216.165.129.141, 64.12.204.21, 64.50.236.52, ...
Connecting to releases.mozilla.org|216.165.129.141|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.7 ... 
No such directory `pub/mozilla.org/seamonkey/releases/1.1.7'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--04:52:54--  ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
           => `seamonkey-1.1.7.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 216.165.129.134, 216.165.129.141, 64.12.204.21, ...
Connecting to releases.mozilla.org|216.165.129.134|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.7 ... 
No such directory `pub/mozilla.org/seamonkey/releases/1.1.7'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--04:52:59--  ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
           => `seamonkey-1.1.7.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 207.200.66.54, 216.165.129.134, 216.165.129.141, ...
Connecting to releases.mozilla.org|207.200.66.54|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.7 ... 
No such directory `pub/mozilla.org/seamonkey/releases/1.1.7'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--04:53:04--  ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
           => `seamonkey-1.1.7.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 207.200.66.54, 216.165.129.134, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.7 ... 
No such directory `pub/mozilla.org/seamonkey/releases/1.1.7'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
rungss@rungss-ubuntu:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.4.3

This script installs the latest release of the official Mozilla build of Seamonkey on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be <li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences


Downloading Seamonkey archive from the Mozilla site

/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
rungss@rungss-ubuntu:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.4.3

This script installs the latest release of the official Mozilla build of Seamonkey on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be <li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences


Downloading Seamonkey archive from the Mozilla site

/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
rungss@rungss-ubuntu:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.4.3

This script installs the latest release of the official Mozilla build of Seamonkey on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be <li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences


Downloading Seamonkey archive from the Mozilla site

/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
rungss@rungss-ubuntu:~$ sudo gedit /ext/apache2/apache2.conf
[sudo] password for rungss:
rungss@rungss-ubuntu:~$ ls -la /ext/apache2
ls: /ext/apache2: No such file or directory
rungss@rungss-ubuntu:~$ sudo gedit /etc/apache2/apache2.conf
rungss@rungss-ubuntu:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.4.3

This script installs the latest release of the official Mozilla build of Seamonkey on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be <li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences


Downloading Seamonkey archive from the Mozilla site

/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
/bin/sh: Syntax error: redirection unexpected
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6/seamonkey-<li id="download-win" class=""><a href="http://download.mozilla.org/?product=seamonkey-1.1.6.en-US.linux-i686.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Error downloading. Trying again, hoping for a different mirror.
Download failed. This may be due to transient network problems, so try again later. Exiting.
rungss@rungss-ubuntu:~$ sudo gedit /etc/X11/xorg.conf
[sudo] password for rungss:
rungss@rungss-ubuntu:~$ sudo gedit /etc/X11/xorg.conf
rungss@rungss-ubuntu:~$ sudo gedit /etc/X11/xorg.conf

rungss@rungss-ubuntu:~$ 



```


FYI, I had IceApe installed in my System but not SeaMonkey. unlike Firefox and Thunderbird which was already installed in my system and I just upgraded through UbuntuZilla.

One more feedback. I lost all my Themes in Firefox... and I can't see the get Ubuntu ad-Ons in teh AdOns window in Firefox..

---

### Post by nanotube on 2007-11-17
so... run it again, but /dont/ say "y" when it asks if the version is correct. say "n", and enter "1.1.6" without the quotes.
then seamonkey will be installed properly.

(seamonkey recently changed website layout, and i need to update ubuntuzilla to fix...)

---

### Post by nanotube on 2007-11-18
i just released an update to ubuntuzilla, v 4.4.4, so if you want you could also install that one and try installing seamonkey again, instead of manually entering the version number. (either way will work, but i just wanted to let you know that you have options. :) ).

---

### Post by rungss on 2007-11-28
Hi nano,
Thanks for the reply.
I got to this Thread only today coz I was new here and my setting in the forum was not set to subscribe to threads I post in at that time.
generally I keep that as my settings in all my forums using vBulletin.
Now I have changed the setting so it wont happen again. :)

**_The SeaMonkey initial Problem:_**

I actually kept on trying the same command from time to time and I was able to install SeaMonkey.

but I am noit sure what actually worked..

I had installed the beta 1 version of FF3 so I think I had uninstalled UbuntuZilla while doing that..

But as I couldnt use any of my FF adons on FF3 I switched back to FF2 and perhaps reinstalled UbuntuZilla and I suppose thats the reason the SeaMonkey installation worked.

But am not sure What actually Worked..

**_v 4.4.4:_**
1) How do I install that. Do I need to download the new version and follow the same Installation instructions at [http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net) to upgrade.
2) What happens to my earlier FF, TB, SM installation and updater installed from UbuntuZilla if I install the new version.

Thanks

---

### Post by nanotube on 2007-11-29
well, if everything works for you, then maybe you don't need to do anything else :)

so before you do anything, run the following commands and post the output here:
```
ubuntuzilla.py --version
```

```
crontab -l
```

this will tell me what version of ubuntuzilla you have, and whether you have update notifications enabled. :)

---

