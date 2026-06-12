---
title: "Two thumbs up on Crunchbang 8.10.2"
date: 2009-01-26
forum: Ubuntuzilla
---

### Post by kansasnoob on 2009-01-26
I thought about posting this in the testing thread but it's been a while!

A friend got me looking at lighter weight desktops and I'd hoped to properly test Fluxbuntu but I can't get a desktop with Fluxbox that allows my visual acuity to even see what the hell I'm looking at.

Anyway I tested the the latest script with Crunchbang 8.10.2:

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. bg        
  4. bn-IN        5. ca           6. cs           7. cy        
  8. da           9. de          10. el          11. en-GB     
 12. en-US       13. eo          14. es-AR       15. es-ES     
 16. et          17. eu          18. fi          19. fr        
 20. fy-NL       21. ga-IE       22. gl          23. gu-IN     
 24. he          25. hi-IN       26. hu          27. id        
 28. is          29. it          30. ja          31. ka        
 32. kn          33. ko          34. ku          35. lt        
 36. lv          37. mk          38. mn          39. mr        
 40. nb-NO       41. nl          42. nn-NO       43. oc        
 44. pa-IN       45. pl          46. pt-BR       47. pt-PT     
 48. ro          49. ru          50. si          51. sk        
 52. sl          53. sq          54. sr          55. sv-SE     
 56. te          57. th          58. tr          59. uk        
 60. zh-CN       61. zh-TW     
Enter your choice of localization (integer, from 0 to 61): 12
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

[sudo] password for lance: 
Get: 1 [http://crunchbang.net](http://crunchbang.net) 8.10.xx Release.gpg [72B]
Ign [http://crunchbang.net](http://crunchbang.net) 8.10.xx/main Translation-en_GB                       
Get: 2 [http://crunchbang.net](http://crunchbang.net) 8.10.xx Release [1237B]                           
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB] 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Get: 5 [http://crunchbang.net](http://crunchbang.net) 8.10.xx/main Packages [11.0kB]                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg [189B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release [51.2kB]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [57.4kB]     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages [280kB]
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [17.5kB]     
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [571B] 
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [24.5kB]
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [4473B]  
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B] 
Get: 17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages [5770B]
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources [86.5kB]
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources [1701B]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages [43.5kB]
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources [10.4kB]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B]
Fetched 648kB in 4s (149kB/s)                         
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
firefox set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-01-26 22:02:46--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 156.56.247.196, 204.152.184.113, 149.20.20.5, ...
Connecting to releases.mozilla.org|156.56.247.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9112341 (8.7M)

100%[======================================>] 9,112,341    311K/s   in 29s     

2009-01-26 22:03:16 (307 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--2009-01-26 22:03:16--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.238.52, 64.50.236.214, 131.188.12.212, ...
Connecting to releases.mozilla.org|64.50.238.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.01s   

2009-01-26 22:03:17 (18.2 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

gpg: directory `/home/lance/.gnupg' created
gpg: new configuration file `/home/lance/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/lance/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/lance/.gnupg/pubring.gpg' created
gpg: /home/lance/.gnupg/trustdb.gpg: trustdb created
tru::1:1233028997:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: keyring `/home/lance/.gnupg/secring.gpg' created
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

gpg: Signature made Mon 15 Dec 2008 20:55:38 CST using DSA key ID 17785FE8
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

The new Firefox version 3.0.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
no crontab for lance
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 



No problems! And it's installed to the hard drive! Very cool!

Thought you'd like to know!

I hope I can figure out how to get a Fluxbuntu resolution I can actually see!

---

### Post by nanotube on 2009-01-27
Hi,
Thanks for the info! 
I didn't even know of the existence of this distro... it seems that new ubuntu-based distros are popping up like mushrooms! :)

---

### Post by snowpine on 2009-01-27
Crunchbang is a tasty mushroom indeed! ;)
I predict you will never go back to Fluxbuntu...

---

