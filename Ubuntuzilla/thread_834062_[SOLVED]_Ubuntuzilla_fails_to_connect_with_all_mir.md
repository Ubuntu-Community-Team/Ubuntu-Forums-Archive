---
title: "[SOLVED] Ubuntuzilla fails to connect with all mirrors"
date: 2008-06-19
forum: Ubuntuzilla
---

### Post by bfo on 2008-06-19
Hello
I'm trying to get FF3 with Ubuntuzilla, but it fails to download the package. However, when I try to enter mirrors through browser, I can manage to get the package manually. Output of "ubuntuzilla.py":
```

bartek@pokoj-bartka:~$ ubuntuzilla.py 

Welcome to the Ubuntuzilla Firefox script version 4.4.7

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. ca        
  4. cs           5. da           6. de           7. el        
  8. en-GB        9. en-US       10. es-AR       11. es-ES     
 12. eu          13. fi          14. fr          15. fy-NL     
 16. ga-IE       17. gu-IN       18. he          19. hu        
 20. id          21. it          22. ja          23. ka        
 24. ko          25. ku          26. lt          27. mk        
 28. mn          29. nb-NO       30. nl          31. nn-NO     
 32. pa-IN       33. pl          34. pt-BR       35. pt-PT     
 36. ro          37. ru          38. si          39. sk        
 40. sl          41. sq          42. sr          43. sv-SE     
 44. tr          45. uk          46. zh-CN       47. zh-TW     

Enter your choice of localization (integer, from 0 to 47): 33
You have chosen localization pl. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Pob: 1 http://pl.archive.ubuntu.com gutsy Release.gpg [191B]
Pob: 2 http://pl.archive.ubuntu.com gutsy/main Translation-pl [22,3kB]                                                      
Pob: 3 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                                                             
Ign http://wine.budgetdedicated.com gutsy/main Translation-pl                                                               
Ign http://download.skype.com stable Release.gpg                                                                            
Pob: 4 http://packages.medibuntu.org gutsy Release.gpg [189B]                                                               
Pob: 5 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                                         
Ign http://security.ubuntu.com gutsy-security/main Translation-pl                                                           
Pob: 6 http://dl.google.com stable Release.gpg [189B]                                                                       
Ign http://dl.google.com stable/non-free Translation-pl                                                                     
Pob: 7 http://archive.ubuntu.com gutsy Release.gpg [191B]                                                                   
Pob: 8 http://archive.canonical.com gutsy Release.gpg [191B]                                                                
Ign http://archive.canonical.com gutsy/partner Translation-pl                                                               
Ign http://ppa.launchpad.net gutsy Release.gpg                                                                              
Ign http://ppa.launchpad.net gutsy/main Translation-pl                                                                      
Ign http://download.skype.com stable/non-free Translation-pl                                                                
Traf http://wine.budgetdedicated.com gutsy Release                                                                          
Ign http://packages.medibuntu.org gutsy/free Translation-pl                                                                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-pl                                                             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-pl                                                     
Ign http://security.ubuntu.com gutsy-security/universe Translation-pl                                                       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-pl                                                     
Ign http://apt.wicd.net gutsy Release.gpg                                                                                   
Ign http://apt.wicd.net gutsy/extras Translation-pl                                                                         
Traf http://security.ubuntu.com gutsy-security Release                                                                      
Traf http://dl.google.com stable Release                                                                                    
Traf http://archive.ubuntu.com gutsy Release                                                                                
Traf http://archive.canonical.com gutsy Release                                                                             
Ign http://ppa.launchpad.net gutsy Release.gpg                                                                              
Ign http://ppa.launchpad.net gutsy/main Translation-pl                                                                      
Traf http://ppa.launchpad.net gutsy Release                                                                                 
Pob: 9 http://pl.archive.ubuntu.com gutsy/restricted Translation-pl [2311B]                                                 
Pob: 10 http://pl.archive.ubuntu.com gutsy/universe Translation-pl [17,8kB]                                                 
Ign http://download.skype.com stable Release                                                                                
Ign http://wine.budgetdedicated.com gutsy/main Packages                                                                     
Traf http://packages.medibuntu.org gutsy Release                                                                            
Traf http://security.ubuntu.com gutsy-security/main Packages                                                                
Traf http://dl.google.com stable/non-free Packages                                                                          
Traf http://archive.ubuntu.com gutsy/main Sources                                                                           
Traf http://archive.canonical.com gutsy/partner Packages                                                                    
Pob: 11 http://pl.archive.ubuntu.com gutsy/multiverse Translation-pl [1253B]                                                
Pob: 12 http://pl.archive.ubuntu.com gutsy-updates Release.gpg [191B]                                                       
Ign http://pl.archive.ubuntu.com gutsy-updates/main Translation-pl                                                          
Ign http://pl.archive.ubuntu.com gutsy-updates/restricted Translation-pl                                                    
Ign http://pl.archive.ubuntu.com gutsy-updates/universe Translation-pl                                                      
Ign http://pl.archive.ubuntu.com gutsy-updates/multiverse Translation-pl                                                    
Traf http://ppa.launchpad.net gutsy Release                                                                                 
Traf http://apt.wicd.net gutsy Release                                                                                      
Traf http://pl.archive.ubuntu.com gutsy Release                                                                             
Traf http://download.skype.com stable/non-free Packages                                                                     
Traf http://wine.budgetdedicated.com gutsy/main Packages                                                                    
Traf http://packages.medibuntu.org gutsy/free Packages                                                                      
Traf http://security.ubuntu.com gutsy-security/restricted Packages                                                          
Traf http://security.ubuntu.com gutsy-security/restricted Sources                                                           
Traf http://security.ubuntu.com gutsy-security/main Sources                                                                 
Traf http://archive.ubuntu.com gutsy/restricted Sources                                                                     
Traf http://archive.canonical.com gutsy/partner Sources                                                                     
Ign http://ppa.launchpad.net gutsy/main Packages                                                                            
Traf http://pl.archive.ubuntu.com gutsy-updates Release                                                                     
Traf http://packages.medibuntu.org gutsy/non-free Packages                                                                  
Traf http://security.ubuntu.com gutsy-security/multiverse Sources                                                           
Traf http://security.ubuntu.com gutsy-security/universe Sources                                                             
Traf http://security.ubuntu.com gutsy-security/universe Packages                                                            
Traf http://security.ubuntu.com gutsy-security/multiverse Packages                                                          
Ign http://ppa.launchpad.net gutsy/main Packages                                                                            
Traf http://apt.wicd.net gutsy/extras Packages                                                                              
Traf http://pl.archive.ubuntu.com gutsy/main Packages                                                               
Traf http://pl.archive.ubuntu.com gutsy/restricted Packages                                                         
Traf http://pl.archive.ubuntu.com gutsy/restricted Sources                              
Traf http://pl.archive.ubuntu.com gutsy/main Sources                                    
Traf http://pl.archive.ubuntu.com gutsy/multiverse Sources                                                          
Traf http://pl.archive.ubuntu.com gutsy/universe Sources                                                            
Traf http://pl.archive.ubuntu.com gutsy/universe Packages                               
Traf http://pl.archive.ubuntu.com gutsy/multiverse Packages                             
Traf http://ppa.launchpad.net gutsy/main Packages                                       
Traf http://pl.archive.ubuntu.com gutsy-updates/main Packages                           
Traf http://pl.archive.ubuntu.com gutsy-updates/restricted Packages                                                 
Traf http://pl.archive.ubuntu.com gutsy-updates/restricted Sources                                                  
Traf http://pl.archive.ubuntu.com gutsy-updates/main Sources                            
Traf http://pl.archive.ubuntu.com gutsy-updates/multiverse Sources                      
Traf http://pl.archive.ubuntu.com gutsy-updates/universe Sources                        
Traf http://pl.archive.ubuntu.com gutsy-updates/universe Packages                       
Traf http://pl.archive.ubuntu.com gutsy-updates/multiverse Packages                                                 
Traf http://ppa.launchpad.net gutsy/main Packages                                                                   
B&#322;&#261;d http://mirror2.ubuntulinux.nl gutsy-seveas Release.gpg                             
  Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z mirror2.ubuntulinux.nl:80 (64.22.94.134). - connect (113 No route to host)
B&#322;&#261;d http://mirror2.ubuntulinux.nl gutsy-seveas/all Translation-pl
  Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z mirror2.ubuntulinux.nl:80 (64.22.94.134). - connect (113 No route to host)
Ign http://mirror2.ubuntulinux.nl gutsy-seveas Release                                                                      
Ign http://mirror2.ubuntulinux.nl gutsy-seveas/all Packages                                                                 
B&#322;&#261;d http://mirror2.ubuntulinux.nl gutsy-seveas/all Packages                                                                
  Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z mirror2.ubuntulinux.nl:80 (64.22.94.134). - connect (113 No route to host)
Pobrano 43,8kB w 15s (2912B/s)                              
Nie uda&#322;o si&#281; pobra&#263; http://mirror2.ubuntulinux.nl/dists/gutsy-seveas/Release.gpg  Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z mirror2.ubuntulinux.nl:80 (64.22.94.134). - connect (113 No route to host)
Nie uda&#322;o si&#281; pobra&#263; http://mirror2.ubuntulinux.nl/dists/gutsy-seveas/all/i18n/Translation-pl.bz2  Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z mirror2.ubuntulinux.nl:80 (64.22.94.134). - connect (113 No route to host)
Nie uda&#322;o si&#281; pobra&#263; http://mirror2.ubuntulinux.nl/dists/gutsy-seveas/all/binary-i386/Packages.gz  Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z mirror2.ubuntulinux.nl:80 (64.22.94.134). - connect (113 No route to host)
Czytanie list pakietów... Gotowe
E: Nie uda&#322;o si&#281; pobra&#263; niektórych plików indeksu, zosta&#322;y one zignorowane lub zosta&#322;a u&#380;yta ich starsza wersja.
It looks like repository updates have not finished successfully. This is most likely due to some repositories being temporarily down, or to a missing GPG key for a third-party repository (see detailed output above). If the main repositories look like they have been updated successfully, you may just proceed without worrying about this.
Would you like to proceed with installation [y/n]? 
Please enter 'y' or 'n': y

OK, Proceeding with installation.
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Reading state information... Gotowe
firefox jest ju&#380; w najnowszej wersji.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.

Backing up old Firefox preferences


Downloading Firefox archive from the Mozilla site

--11:57:35--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
           => `firefox-3.0.tar.gz'
Translacja releases.mozilla.org... 204.152.184.196, 129.101.198.62, 64.50.236.52, ...
&#321;&#261;czenie si&#281; z releases.mozilla.org|204.152.184.196|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/pl ... zrobiono.
==> PASV ... nie mo&#380;na po&#322;&#261;czy&#263; si&#281; z 204.152.184.196 port 56882: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--11:57:39--  ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
           => `firefox-3.0.tar.gz'
Translacja mozilla.isc.org... 204.152.184.113
&#321;&#261;czenie si&#281; z mozilla.isc.org|204.152.184.113|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/pl ... zrobiono.
==> PASV ... zrobiono.    ==> RETR firefox-3.0.tar.gz ... 
Nie ma pliku `firefox-3.0.tar.gz'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--11:57:44--  ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
           => `firefox-3.0.tar.gz'
Translacja mozilla.ussg.indiana.edu... 156.56.247.196
&#321;&#261;czenie si&#281; z mozilla.ussg.indiana.edu|156.56.247.196|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/pl ... zrobiono.
==> PASV ... zrobiono.    ==> RETR firefox-3.0.tar.gz ... 
Nie ma pliku `firefox-3.0.tar.gz'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--11:57:48--  ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
           => `firefox-3.0.tar.gz'
Translacja ftp.osuosl.org... 64.50.238.52, 64.50.236.52
&#321;&#261;czenie si&#281; z ftp.osuosl.org|64.50.238.52|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/pl ... zrobiono.
==> PASV ... zrobiono.    ==> RETR firefox-3.0.tar.gz ... 
Nie ma pliku `firefox-3.0.tar.gz'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--11:57:52--  ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
           => `firefox-3.0.tar.gz'
Translacja mozilla.cs.utah.edu... 155.98.64.83
&#321;&#261;czenie si&#281; z mozilla.cs.utah.edu|155.98.64.83|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/pl ... zrobiono.
==> PASV ... zrobiono.    ==> RETR firefox-3.0.tar.gz ... 
Nie ma pliku `firefox-3.0.tar.gz'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--11:57:56--  ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
           => `firefox-3.0.tar.gz'
Translacja mozilla.mirrors.tds.net... 204.246.0.136
&#321;&#261;czenie si&#281; z mozilla.mirrors.tds.net|204.246.0.136|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/pl ... zrobiono.
==> PASV ... zrobiono.    ==> RETR firefox-3.0.tar.gz ... 
Nie ma pliku `firefox-3.0.tar.gz'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.0/linux-i686/pl/firefox-3.0.tar.gz
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.

```
And the code repeats for all mirrors. Look at the lines 
```
Nie ma pliku `firefox-3.0.tar.gz'
```
It says there is no such file as firefox-3.0.tar.gz, despite the script has succesfully logged in on a server and I can go to ftp through browser and download it myself. Strange. Any suggestions?

---

### Post by bfo on 2008-06-19
Oh sorry, I didn't notice the thread below mine :oops:. Mod, could you please delete my post?

---

### Post by nanotube on 2008-06-20
hey, no big deal - it's a big problem, what with everyone being excited about ff3 release, so what's a dupe thread or two? :)

reposting my reply and fix here for your benefit: 

it looks like they changed the archive type for ff3, so ubuntuzilla was failing at installing it.
i have updated the code to take care of this, the latest release candidate is attached to this bug report thread on sourceforge:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990](http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990)
please feel free to give it a try and let me know if it works as it should.
thanks for your feedback!

---

### Post by errold32 on 2008-07-03
I am having the same problem with handy and ff3

i am using ubuntuzilla 4.5.0

It fails to connect to all mirrors.

i have already downloaded ff3 into /tmp, but it doesn't seem to see that.

Google bookmark problems....sigh

thanks

---

### Post by nanotube on 2008-07-04
> **errold32 said:**
> I am having the same problem with handy and ff3

i am using ubuntuzilla 4.5.0

It fails to connect to all mirrors.

i have already downloaded ff3 into /tmp, but it doesn't seem to see that.

Google bookmark problems....sigh

thanks

hmm... try again? seems to work for me...

---

### Post by errold32 on 2008-07-09
try again with the download or what? It shouldn't even try to re download Firefox should it?
Does it check the /tmp directory after it connects to those servers? It detects the right current version. 

I will try again.

---

### Post by nanotube on 2008-07-09
> **errold32 said:**
> try again with the download or what? It shouldn't even try to re download Firefox should it?
Does it check the /tmp directory after it connects to those servers? It detects the right current version. 

I will try again.

yes, i mean try again, running ubuntuzilla and see if it works.

are you by any chance running through a proxy? if it still fails, could you please post the complete transcript of the ubuntuzilla session, so i can take a look?

---

### Post by errold32 on 2008-07-14
It worked! yay! 

Thanks

---

### Post by nanotube on 2008-07-14
> **errold32 said:**
> It worked! yay! 

Thanks

nice :)

---

