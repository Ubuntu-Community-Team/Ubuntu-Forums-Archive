---
title: "[SOLVED] Automated  installation of the newest TB"
date: 2007-09-03
forum: Ubuntuzilla
---

### Post by jamere on 2007-09-03
Hi folks nice job on the automated TB script. 

I was trying to get to the latest TB (2.0.0.6) from version 2.0.0.4 (20070604) feisty. The script seemed to run fine until the download integrity check failed several times and then quit. "thunderbird-2.0.0.6.tar.gz.asc" is in my "/tmp" directory as it should be (I think). Also used Ubuntuzilla 4.4.0.

Can this script be restarted where it left off somehow without having to repeat the previous steps?

Should I include the terminal output for you to have a look at?

Thanks for any help on this and your work is much appreciated.

Jim M

---

### Post by nanotube on 2007-09-03
well... the previous steps are "agreeing to the latest version", and "choosing localization"... i don't see why you'd particularly care to not repeat those, since they take a couple of seconds each. :)

so just run it again from the beginning. 

if the integrity check keeps failing, then post the terminal output and i'll take a look. but chances are, it was just a corrupt download of the tb tar.gz archive, and another run through will go as normal.

edit: btw, what exactly do you mean by "download integrity check"? was the script running the gpg signature verification, or was it trying to download something? i guess posting script output wouldn't hurt. :)

---

### Post by jamere on 2007-09-03
nano, thanks for the quick reply. Looks like it was trying to do the gpg signature verification.  My terminal output...

> this is the output of install script (it failed trying to get Mozilla Software Releases public key)...

jim@jim-desktop:~$ ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.4.0

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.6. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Thunderbird ...
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. be           1. bg           2. ca           3. cs        
  4. da           5. de           6. el           7. en-GB     
  8. en-US        9. es-AR       10. es-ES       11. eu        
 12. fi          13. fr          14. ga-IE       15. hu        
 16. it          17. ja          18. ko          19. lt        
 20. mk          21. nb-NO       22. nl          23. nn-NO     
 24. pa-IN       25. pl          26. pt-BR       27. pt-PT     
 28. ru          29. sk          30. sl          31. sv-SE     
 32. tr          33. zh-CN       34. zh-TW     
Enter your choice of localization (integer, from 0 to 34): 8
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                        
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]              
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US            
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US                
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                           
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US                   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US            
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                               
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Fetched 9B in 2s (4B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev linux-headers-2.6.20-15-generic
  x11proto-kb-dev libkexif1 cdda2wav libnspr4-0d ntp-simple libxdmcp-dev xtrans-dev
  x11proto-core-dev libgphoto2-2-dev libusb-dev libxt-dev libxext-dev libxul0d ntp
  x11proto-input-dev libxau-dev linux-headers-2.6.20-15 libmozjs0d libpq4 libx11-dev
  libxul-common libimlib2 libnss3-0d
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector
  mozilla-thunderbird-enigmail
The following NEW packages will be installed:
  mozilla-thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.9MB of archives.
After unpacking 30.5MB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main mozilla-thunderbird 1.5.0.13-0ubuntu0.7.04 [10.9MB]
Fetched 10.9MB in 2m29s (73.1kB/s)                                                   
Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 129042 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.5.0.13-0ubuntu0.7.04_i386.deb) ...
Setting up mozilla-thunderbird (1.5.0.13-0ubuntu0.7.04) ...
Please restart any running Thunderbirds, or you will experience problems.


A Thunderbird profile has been found at ~/.mozilla-thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.mozilla-thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': y

Backing up old thunderbird preferences


A Thunderbird profile has been found at ~/.thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': y

Backing up old thunderbird preferences

You seem to have two Thunderbird profiles, one in ~/.thunderbird and one in ~/.mozilla-thunderbird. Please choose among the following options. (If you need more information, please see our FAQ on this on our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) in the 'help on multiple profiles' section, prior to making this choice.)
1. use ~/.thunderbird directory as your profile for the new installation.
2. use ~/.mozilla-thunderbird directory as your profile for the new installation (~/.thunderbird is moved out of the way, and a link to ~/.mozilla-thunderbird is created)
3. exit the script now, take your time and figure out which profile you want to use, and then try running this script again later when you are ready.
Enter the number for your choice [1/2/3]: 1

Using ~/.thunderbird as your profile directory with no changes.


Downloading Thunderbird archive from the Mozilla site

--15:42:40--  [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US/thunderbird-2.0.0.6.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US/thunderbird-2.0.0.6.tar.gz)
           => `thunderbird-2.0.0.6.tar.gz'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.214, 130.239.18.158, ...
Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.6.tar.gz ... done.
Length: 11,442,355 (11M) (unauthoritative)

100%[==========================================>] 11,442,355   121.94K/s    ETA 00:00

15:43:58 (144.48 KB/s) - `thunderbird-2.0.0.6.tar.gz' saved [11442355]


Downloading Thunderbird signature from the Mozilla site

--15:43:58--  [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US/thunderbird-2.0.0.6.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US/thunderbird-2.0.0.6.tar.gz.asc)
           => `thunderbird-2.0.0.6.tar.gz.asc'
Resolving releases.mozilla.org... 64.12.204.21, 64.50.236.214, 156.56.247.196, ...
Connecting to releases.mozilla.org|64.12.204.21|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.6.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[==========================================>] 186           --.--K/s             

15:43:59 (10.28 KB/s) - `thunderbird-2.0.0.6.tar.gz.asc' saved [186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.



---

### Post by nanotube on 2007-09-03
aha, so it was having trouble retrieving the mozilla releases signing key. 
usually this is a transient network problem... i'm surprised that all 3 keyservers were down, though. (i just tried, and it worked for me).

try running it again, and if it still errors out at that point, just run it with option -g (skipgpg), and it will skip gpg sig verification step.

---

### Post by jamere on 2007-09-04
nano,

The -g option worked great! Thanks for your work. I tried again the original way with the same results several hours later. I kinda wonder if firewall could be interfering? I'm using Firestarter. 

Thanks again,
Jim M

---

### Post by nanotube on 2007-09-04
> **jamere said:**
> nano,

The -g option worked great! Thanks for your work. I tried again the original way with the same results several hours later. I kinda wonder if firewall could be interfering? I'm using Firestarter. 

Thanks again,
Jim M

hm, could be... not sure what port the gpg keyservers use... but if it's not port 80, and your firestarter doesn't allow outbound connections on random ports, then could be. :)
anyway, glad it worked. :)

---

### Post by HyRax on 2009-07-04
> **nanotube said:**
> hm, could be... not sure what port the gpg keyservers use... but if it's not port 80, and your firestarter doesn't allow outbound connections on random ports, then could be. :)
anyway, glad it worked. :)

I know this is resurrecting a very old thread, but it still comes up on Google searches, so I'll just add that the keyservers DO use a different port to port 80.

You must allow port 11371 out and you will instantly lose the "gpgkeys: HTTP fetch error 7: couldn't connect to host" error.

Cheers!

---

### Post by nanotube on 2009-07-04
Thanks for posting that helpful bit of info! :)

---

