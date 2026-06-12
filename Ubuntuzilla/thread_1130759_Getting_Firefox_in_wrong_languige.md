---
title: "Getting Firefox in wrong languige"
date: 2009-04-20
forum: Ubuntuzilla
---

### Post by padu on 2009-04-20
I did the steps to install firefox 3 using unbuntuzilla with the last i386 version and i got it installed successfully but in a language I cannot read, probably Russian.
When I had to choose the location for the download I chose UK, this was the only place that speaks English on the offered list, the rest was pl de ect...
I use unbuntu 7.10 in English.
Thanks in advance for your help.
Padu

---

### Post by nanotube on 2009-04-20
Hi
Could you please copy and paste and post the complete install session of ubuntuzilla from the terminal, so I can take a look? 

if you don't have that terminal open anymore, just run ubuntuzilla install again, check that the problem persists (that firefox is again installed in the wrong language), and copy-paste the entire ubuntuzilla output here. 

my first guess is, though, that you're choosing the wrong language. english localization for firefox is either "en-US" or "en-GB" (for us or uk english, respectively), which are options 11 and 12 or thereabouts.

---

### Post by padu on 2009-04-20
In the meantime I uninstalled ff using unbuntuzilla and installed the one from the ubuntu repository that worked fine without any error messages like by installing using ubuntuzilla.
After shutting down it starts again ff3 which should be uninstalled.
whereis firefox returns:
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz
I am confused
Padu

---

### Post by nanotube on 2009-04-20
which version did you install from the repositories? what does the /usr/bin/firefox link point to? (run "ls -al /usr/bin/firefox" to see)

---

### Post by padu on 2009-04-20
ok I installed again and choose us eng... I thoght I did not have this choice last time this is wy I choose uk which was the only choice that sound english.

Here the output:
Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.8. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
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

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                         
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                   
Ign [http://download.skype.com](http://download.skype.com) stable Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources              
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                        
Get:2 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy Release
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Fetched 3B in 10s (0B/s)                                                       
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  texlive-base texlive-fonts-recommended xulrunner-1.9 texlive-doc-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 127 not upgraded.

Old firefox preferences not found. Nothing to back up. Proceeding with installation.

Retrieving package name for Firefox ...
Success!: firefox-3.0.8.tar.bz2

Downloading Firefox archive from the Mozilla site

--17:38:00--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.8/linux-i686/en-US/firefox-3.0.8.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.8/linux-i686/en-US/firefox-3.0.8.tar.bz2)
           => `firefox-3.0.8.tar.bz2'
Resolving releases.mozilla.org... 64.50.236.52
Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.8/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.8.tar.bz2 ... done.
Length: 9,118,459 (8.7M) (unauthoritative)

100%[====================================>] 9,118,459     25.22K/s    ETA 00:00

17:44:26 (23.61 KB/s) - `firefox-3.0.8.tar.bz2' saved [9118459]


Downloading Firefox signature from the Mozilla site

--17:44:26--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.8/linux-i686/en-US/firefox-3.0.8.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.8/linux-i686/en-US/firefox-3.0.8.tar.bz2.asc)
           => `firefox-3.0.8.tar.bz2.asc'
Resolving releases.mozilla.org... 128.61.111.9, 64.50.238.52, 64.50.236.214, ...
Connecting to releases.mozilla.org|128.61.111.9|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.8/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.8.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

17:44:44 (12.24 MB/s) - `firefox-3.0.8.tar.bz2.asc' saved [186]

tru::1:1240158969:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1240158969:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2009-07-16::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2009-07-16:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2009-07-16:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Fri 27 Mar 2009 03:36:46 PM EET using DSA key ID 17785FE8
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

The new Firefox version 3.0.8 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.

---

### Post by padu on 2009-04-20
> **nanotube said:**
> which version did you install from the repositories? what does the /usr/bin/firefox link point to? (run "ls -al /usr/bin/firefox" to see)

after reinstalling now:
 ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2009-04-20 17:44 /usr/bin/firefox -> /opt/firefox/firefox

and whereis firefox:
 whereis firefox
firefox: /usr/bin/firefox.ubuntu /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

but thank you now I have it in English I hope tomorow also ;)
Padu

---

### Post by nanotube on 2009-04-20
ok, after ubuntuzilla install, it should be pointing to /opt/firefox, just as it does, and from your install session i see that everything went through just fine.

by the way, 'uk' language code is ukranian. that explains everything. :)

---

### Post by padu on 2009-04-23
Yeah Working Perfect Now!
Thanks a lot for this good tool and the great support.
Padu

---

### Post by nanotube on 2009-04-23
you're welcome :) enjoy :)

---

### Post by lesmorton on 2009-08-13
I seem to have a similar problem.  Installed FF 3.5.2 using Ubuntuzilla and selected the wrong language (uk instead of en-gb).  Uninstalled FF using Synaptic package manager, re-started my PC and then re-installed FF using Ubuntuzilla in the Terminal window.  It's in English now however when I go to my Bookmarks manager it's in Ukranian.

Do I need to do another uninstall/re-install using Terminal rather than Synaptic - if so how?

---

### Post by nanotube on 2009-08-13
probably something messed up in your profile
just start with a fresh profile, and restore your bookmarks manually.

---

