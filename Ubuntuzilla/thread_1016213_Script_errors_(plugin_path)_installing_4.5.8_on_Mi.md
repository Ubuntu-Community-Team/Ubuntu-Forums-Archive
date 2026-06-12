---
title: "Script errors (plugin path) installing 4.5.8 on Mint 6"
date: 2008-12-19
forum: Ubuntuzilla
---

### Post by kansasnoob on 2008-12-19
I was having trouble with Flash and specifically Flashblock after updating Firefox yesterday in Intrepid and then today in Linux Mint 6, so I decided to give Ubuntuzilla a whirl!

Things went flawlessly in Intrepid, but in Mint 6 I got the errors at the bottom of this script:

> lance@lance-desktop ~ $ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.5.8

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

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
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release.gpg                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Translation-en_US     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release [7817B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 7817B in 4s (1587B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2008-12-19 15:54:05--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 155.98.64.83, 156.56.247.196, 204.152.184.113, ...
Connecting to releases.mozilla.org|155.98.64.83|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9112341 (8.7M)

100%[======================================>] 9,112,341    266K/s   in 36s     

2008-12-19 15:54:43 (245 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--2008-12-19 15:54:43--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 149.20.20.5, 128.61.111.9, 64.50.238.52, ...
Connecting to releases.mozilla.org|149.20.20.5|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.01s   

2008-12-19 15:54:44 (18.4 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1229711353:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1229711353:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2009-07-16::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2009-07-16:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2009-07-16:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Mon 15 Dec 2008 08:55:38 PM CST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
sudo dpkg -L firefox |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'
Failed to determine plugin path. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1110, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 546, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 716, in linkPlugins
    self.pluginPath = self.util.getSystemOutput(executionstring="sudo dpkg -L " + self.aptPackage + " |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'", errormessage="Failed to determine plugin path. Exiting.")
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
lance@lance-desktop ~ $ 

So I ended up installing manually and now the Flash and Flashblock problems are resolved but I'm not linked to the vlc plugin.

Hope you can help! Thanks in advance!

---

### Post by kansasnoob on 2008-12-20
I did find an acceptable alternative. I installed the gecko-mediaplayer. Still inferior to vlc IMHO, but acceptable. Certainly better than the mplayer plugins packaged with Mint 6.

Other things I tried:

1: I restored Mint 6 to it's virgin Firefox state. Even removing all the backups, the .mozilla folder entirely and starting fresh. the Flash problem (I think because Flashblock would no longer work) still persisted.

This may be due to limited CPU capacity: VIA 1500 MHZ (very, very energy efficient but weak on performance). I do have 2GB of RAM.

2: I then once again installed the Ubuntuzilla version of Firefox (same errors) and completely deleted .mozilla and replaced it with a copy of the .mozilla from the perfectly working Intrepid with the Ubuntuzilla install of Firefox. (Quite easy since they're on the same machine).

Anyway the bottom line is that Ubuntuzilla worked flawlessly on Intrepid and solved my flash/flashblock problems, I can still link the vlc and totem plug-ins on Intrepid! So your project is AWESOME!

Now for a Mintzilla:P

Just joking!

I'll wait a few days before marking this solved in case anyone has any ideas about how to link the vlc plug-in in Mint (which I also couldn't do in the manual install).

Also I like to play, as time allows, so if you have some specific testing that needs to be done I have a spare hard drive. But as my moniker indicates I'm a noob! I started out with gOS and Freespire only about 10 months ago.

Don't let the project die! It's awesome!

---

### Post by nanotube on 2008-12-23
hi
well, ubuntuzilla has pretty specific versionstring checking for ubuntu (because with each ubuntu release they keep changing where they store the plugins for firefox, basically), and i bet linux mint doesn't keep ubuntu's version string. 

so... could you tell me what it says on your linux mint in the file 
/etc/issue
?

and could you tell me where the plugins are located? (on recent ubuntu versions, its in /usr/lib/xulrunner-addons/plugins )

---

### Post by kansasnoob on 2008-12-24
I'll have to do some more studying, probably not until Saturday or Sunday.

So far this:

> lance@lance-desktop ~ $ cat /etc/issue
Linux Mint 6 Felicia \n \l

I love Ubuntuzilla in Intrepid! I tried the Ubuntu repo version updated on my test drive and still horrible Flash and no Flashblock. With Ubuntuzilla all is good!

Great work! Excellent project!

---

### Post by kansasnoob on 2008-12-25
Two possibly interesting things here:

> lance@lance-desktop ~ $ apt contains addons/plugins
**xulrunner-1.9: /usr/lib/xulrunner-addons/plugins/libnullplugin.so**
totem-mozilla: /usr/lib/xulrunner-addons/plugins/libtotem-gmp-plugin.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-rm.so
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-dvx.so
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-wmp.xpt
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-rm.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-rm.xpt
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer.xpt
rhythmbox: /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-dvx.xpt
xulrunner-1.9, rhythmbox, totem-mozilla, gecko-mediaplayer, mozilla-plugin-vlc, mozilla-mplayer, adobe-flashplugin, sun-java6-plugin: /usr/lib/xulrunner-addons/plugins
totem-mozilla: /usr/lib/xulrunner-addons/plugins/libtotem-mully-plugin.so
xulrunner-1.9: /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
**firefox-3.0: /usr/lib/firefox-addons/plugins**
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-rm.xpt
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-wmp.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-qt.so
mozilla-plugin-vlc: /usr/lib/xulrunner-addons/plugins/libvlcplugin.so
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in.xpt
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-dvx.xpt
totem-mozilla: /usr/lib/xulrunner-addons/plugins/libtotem-narrowspace-plugin.so
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-qt.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-qt.xpt
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-wmp.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-wmp.xpt
totem-mozilla: /usr/lib/xulrunner-addons/plugins/libtotem-basic-plugin.so
gecko-mediaplayer: /usr/lib/xulrunner-addons/plugins/gecko-mediaplayer-dvx.so
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in.so
mozilla-mplayer: /usr/lib/xulrunner-addons/plugins/mplayerplug-in-qt.xpt
lance@lance-desktop ~ $ 



---

### Post by nanotube on 2008-12-26
Hi
ok, so... mint looks like it's ubuntu with a few bells and whistles on top, so it should be possible to include it.

currently, the only reason there are version checks is because of the changes in the location of firefox plugins over time, and changes in the name of the default firefox package over time. i think i can do this without relying on version checks, so i'll try to implement that properly, and then ask you to test the new version on both ubuntu and mint, to see if everything works ok.

keep an eye out for it. :)

---

### Post by kansasnoob on 2008-12-26
> **nanotube said:**
> Hi
ok, so... mint looks like it's ubuntu with a few bells and whistles on top, so it should be possible to include it.

currently, the only reason there are version checks is because of the changes in the location of firefox plugins over time, and changes in the name of the default firefox package over time. i think i can do this without relying on version checks, so i'll try to implement that properly, and then ask you to test the new version on both ubuntu and mint, to see if everything works ok.

keep an eye out for it. :)

Sounds good!

---

### Post by nanotube on 2009-01-01
Hi,

Well, I have made the code generic, and independent of hard-coded ubuntu version checks. So if things go well, it should now work on any ubuntu/debian derivative distro.

I am attaching the latest release-candidate package, please give it a test and see if it works for you on ubuntu, mint, ubuntu older versions (feisty?, gutsy, hardy), anything else you can throw at it. 

let me know if you run into any errors. :)

I have done some testing myself, on my intrepid system, but I don't have any other linuxes sitting around...

---

### Post by kansasnoob on 2009-01-01
Great work!

I popped in my testing hard drive which had "virgin" 8.10 and Mint 6 installed. After updating both I verified that the flash (actually flashblock) problem persisted and it did.

To be specific the version of flashblock in the repos is 1.3.10a, whereas the current version of flashblock provided by Mozilla is 1.5.7.1. One of those packages that wasn't updated along with Firefox 3.05!

Anyway the changes you made resulted in Ubuntuzilla running flawlessly on both 8.10 (Intrepid), and Mint 6. All plug-ins work great. 

I'll next try 8.04 (I have an 8.04.2 daily build disc from 12-27), then 7.10, and finally Mint 5, just to be on the safe side.

I may try to dig up a 6.06 disc but I've always found Dapper to be very fiddly to get running on my hardware.

BTW, I'm sure there might be some other way of installing only the needed newer version of Flashblock, just running gksudo firefox doesn't get-r-done in the installed version of Firefox, but the point is you've taken out all the guess work!

Super great project!

---

### Post by nanotube on 2009-01-01
Hi,
Thanks for testing, sounds great. :)

about solving just the flashblock issue without ubuntuzilla: if you want to try it, all you need to do is:

1. uninstall flashblock from the repos
2. then go to mozilla addons site for flashblock [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433), click on add to firefox, and when the dialog pops up, say 'install', and it will be installed to your profile. 

no need for sudo or anything like that, since it gets installed to your user profile.

---

### Post by kansasnoob on 2009-01-01
nanotube, I'll try that later. I really hadn't isolated the flashblock problem until today.

Anyway, I completed the 8.04.2 install and I was shocked (after installing the Ubuntuzilla version of Firefox and the newest flashblock) I had a great working flash! And it was still Flash 9.0r152. I did however DL the Flash 10 .deb and it also worked perfectly.

Anyway, the script ran perfectly. Well there was one "hang-up":

> Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.5.tar.bz2

But your script obviously did what it was supposed to do and found a different mirror!

Bottom line: SUCCESS!

7.10 next!

This should be faster since I spent time resizing the 8.10 and Mint 6 partitions for future testing. Now I'll just overwrite the 8.04.2 partition.

---

### Post by kansasnoob on 2009-01-02
Well,not so good with Gutsy (7.10):

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

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
Please enter 'y' or 'n': 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

[sudo] password for lance:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--22:56:59--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 202.177.202.154, 129.101.198.59, 64.50.236.52, ...
Connecting to releases.mozilla.org|202.177.202.154|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 202.177.202.154 port 63081: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--22:57:02--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9,112,341 (8.7M) (unauthoritative)

100%[====================================>] 9,112,341    301.25K/s    ETA 00:00

22:57:34 (291.99 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--22:57:34--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.236.214, 131.188.12.212, 216.165.129.141, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

22:57:34 (19.83 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1230871348:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1230871348:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2009-07-16::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2009-07-16:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2009-07-16:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Mon 15 Dec 2008 08:55:38 PM CST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
Trying to determine firefox plugin path...
Unable to determine firefox plugin path. Please determine the directory where firefox looks for plugins, and enter that directory manually here: 



Where it says, "Please determine the directory where firefox looks for plugins, and enter that directory manually here" I have no idea what to enter!

Maybe I convinced you to break your sript????????

Anyway I'm too tired tonight to continue but I'll be back tomorrow!

---

### Post by nanotube on 2009-01-02
Hi,

Thanks for the testing :)

indeed, the mirrors sometimes go down, that's why i have multiple mirrors coded in. so that's nothing to worry about.

another thing: you can test this with a livecd, so you don't have to resize partitions or install stuff to disk, that might be easier.

about the gutsy problem... hmm... that should be simple to troubleshoot. just tell me your complete output on gutsy of the following command:
```
find /usr/lib -name 'libnullplugin.so'
```

i'll see what's there and how i should change my detection to accommodate.

---

### Post by kansasnoob on 2009-01-02
> **nanotube said:**
> Hi,

Thanks for the testing :)

indeed, the mirrors sometimes go down, that's why i have multiple mirrors coded in. so that's nothing to worry about.

another thing: you can test this with a livecd, so you don't have to resize partitions or install stuff to disk, that might be easier.

about the gutsy problem... hmm... that should be simple to troubleshoot. just tell me your complete output on gutsy of the following command:
```
find /usr/lib -name 'libnullplugin.so'
```

i'll see what's there and how i should change my detection to accommodate.

lance@lance-desktop:~$ find /usr/lib -name 'libnullplugin.so'
/usr/lib/xulrunner-1.9a8/plugins/libnullplugin.so
lance@lance-desktop:~$ 

I should add that I ran that command after attempting to install the repo version of Firefox 3.0. So, holdon ........... I'm going to get back to a "virgin" 7.10 and repeat that command.

---

### Post by kansasnoob on 2009-01-02
Hmmmm, without the 3.0 and associated xulrunner that command returns nothing?

> lance@lance-desktop:~$ find /usr/lib -name 'libnullplugin.so'
lance@lance-desktop:~$ find /usr/lib -name 'libnullplugin.so'
lance@lance-desktop:~$ 


---

### Post by nanotube on 2009-01-02
> **kansasnoob said:**
> lance@lance-desktop:~$ find /usr/lib -name 'libnullplugin.so'
/usr/lib/xulrunner-1.9a8/plugins/libnullplugin.so
lance@lance-desktop:~$ 



aha, ok, interesting. i'll have to take that into account. :)

> 
I should add that I ran that command after attempting to install the repo version of Firefox 3.0. So, holdon ........... I'm going to get back to a "virgin" 7.10 and repeat that command.

please do, and let me know if that's any different.

once i know what possibilities to expect from that find command for the various versions, it will be a cinch to adjust. 

Thanks again for your help! :)

---

### Post by nanotube on 2009-01-02
> **kansasnoob said:**
> Hmmmm, without the 3.0 and associated xulrunner that command returns nothing?

wait, is firefox installed at all, on your "clean" 7.10? or did you just uninstall ff3, and are thus left without a firefox completely? 

if the latter, please install whatever default firefox version is in the repos first, then try again. if the former, then please do a 
```
find / -name 'libnullplugin.so'
```

---

### Post by kansasnoob on 2009-01-02
Just to recap:

I never uninstalled FF2. Using synaptic (safest way I've found for fiddling) choosing to uninstall FF2 shows you'd be removing essential Ubuntu-desktop stuff. I just decided to check synaptic this morning and noticed that FF3 was in the repos, which requires the newest repo version of xulrunner, and I was surprised that NO xulrunner at all is installed by default for FF2.

Anyway I just decided to install FF3 and the newer xulrunner and try the Ubuntuzilla script again. Same result!

Anyway what I get with FF3 and the newest repo version of xulrunner:

> lance@lance-desktop:~$ find /usr/lib -name 'libnullplugin.so'
/usr/lib/xulrunner-1.9a8/plugins/libnullplugin.so


Just fiddling I tried with only FF2 and the older version of xulrunner (same script errors BTW):

> lance@lance-desktop:~$ find /usr/lib -name 'libnullplugin.so'

/usr/lib/xulrunner/plugins/libnullplugin.so



Just thought you might want to see that. Now what you requested (with FF2 only - no xulrunner - true default state - which does work as a browser BTW):

> lance@lance-desktop:~$ find / -name 'libnullplugin.so'
find: /lost+found: Permission denied
/opt/firefox/plugins/libnullplugin.so
find: /root/.gconf: Permission denied
find: /root/.gnome2_private: Permission denied
find: /root/.gnome2: Permission denied
find: /root/.gconfd: Permission denied
find: /root/.mozilla: Permission denied
find: /root/.hplip: Permission denied
find: /root/.synaptic: Permission denied
find: /etc/ssl/private: Permission denied
find: /etc/cups/ssl: Permission denied
find: /media/hda7/lost+found: Permission denied
find: /media/hda7/lance/.qt: Permission denied
/media/hda1/opt/firefox/plugins_2009-01-01T15:04:35-0600/libnullplugin.so
find: /media/hda1/root/.gconfd: Permission denied
find: /media/hda1/root/.hplip: Permission denied
find: /media/hda1/root/.config: Permission denied
find: /media/hda1/root/.synaptic: Permission denied
find: /media/hda1/root/.gnome2_private: Permission denied
find: /media/hda1/root/.mozilla: Permission denied
find: /media/hda1/root/.dbus: Permission denied
find: /media/hda1/root/.aptitude: Permission denied
find: /media/hda1/root/.gnome2: Permission denied
find: /media/hda1/root/.gconf: Permission denied
find: /media/hda1/var/lib/PolicyKit: Permission denied
find: /media/hda1/var/lib/gdm: Permission denied
find: /media/hda1/var/spool/cron/atjobs: Permission denied
find: /media/hda1/var/spool/cron/atspool: Permission denied
find: /media/hda1/var/spool/cron/crontabs: Permission denied
find: /media/hda1/var/spool/cups: Permission denied
find: /media/hda1/var/cache/ldconfig: Permission denied
find: /media/hda1/var/cache/system-tools-backends: Permission denied
/media/hda1/usr/lib/xulrunner-addons/plugins/libnullplugin.so
find: /media/hda1/etc/cups/ssl: Permission denied
find: /media/hda1/etc/firestarter/inbound: Permission denied
find: /media/hda1/etc/firestarter/outbound: Permission denied
find: /media/hda1/etc/ssl/private: Permission denied
find: /media/hda1/lost+found: Permission denied
find: /media/hda6/root/.gnome2_private: Permission denied
find: /media/hda6/root/.synaptic: Permission denied
find: /media/hda6/root/.gconf: Permission denied
find: /media/hda6/root/.gnome2: Permission denied
find: /media/hda6/root/.gconfd: Permission denied
find: /media/hda6/root/.mozilla: Permission denied
find: /media/hda6/root/.aptitude: Permission denied
find: /media/hda6/root/.hplip: Permission denied
find: /media/hda6/root/.dbus: Permission denied
find: /media/hda6/var/spool/cron/crontabs: Permission denied
find: /media/hda6/var/spool/cron/atspool: Permission denied
find: /media/hda6/var/spool/cron/atjobs: Permission denied
find: /media/hda6/var/spool/cups: Permission denied
find: /media/hda6/var/cache/system-tools-backends: Permission denied
find: /media/hda6/var/cache/ldconfig: Permission denied
find: /media/hda6/var/log/samba/cores: Permission denied
find: /media/hda6/var/lib/samba/usershares: Permission denied
find: /media/hda6/var/lib/gdm: Permission denied
find: /media/hda6/var/lib/PolicyKit: Permission denied
/media/hda6/usr/lib/xulrunner-addons/plugins/libnullplugin.so
find: /media/hda6/etc/firestarter/outbound: Permission denied
find: /media/hda6/etc/firestarter/inbound: Permission denied
find: /media/hda6/etc/cups/ssl: Permission denied
find: /media/hda6/etc/ssl/private: Permission denied
find: /media/hda6/lost+found: Permission denied
find: /media/hda6/tmp/orbit-root: Permission denied
/media/hda6/opt/firefox/plugins_2009-01-01T16:00:21-0600/libnullplugin.so
find: /proc/tty/driver: Permission denied
find: /proc/1/task/1/fd: Permission denied
find: /proc/1/task/1/fdinfo: Permission denied
find: /proc/1/fd: Permission denied
find: /proc/1/fdinfo: Permission denied
find: /proc/2/task/2/fd: Permission denied
find: /proc/2/task/2/fdinfo: Permission denied
find: /proc/2/fd: Permission denied
find: /proc/2/fdinfo: Permission denied
find: /proc/3/task/3/fd: Permission denied
find: /proc/3/task/3/fdinfo: Permission denied
find: /proc/3/fd: Permission denied
find: /proc/3/fdinfo: Permission denied
find: /proc/4/task/4/fd: Permission denied
find: /proc/4/task/4/fdinfo: Permission denied
find: /proc/4/fd: Permission denied
find: /proc/4/fdinfo: Permission denied
find: /proc/5/task/5/fd: Permission denied
find: /proc/5/task/5/fdinfo: Permission denied
find: /proc/5/fd: Permission denied
find: /proc/5/fdinfo: Permission denied
find: /proc/6/task/6/fd: Permission denied
find: /proc/6/task/6/fdinfo: Permission denied
find: /proc/6/fd: Permission denied
find: /proc/6/fdinfo: Permission denied
find: /proc/7/task/7/fd: Permission denied
find: /proc/7/task/7/fdinfo: Permission denied
find: /proc/7/fd: Permission denied
find: /proc/7/fdinfo: Permission denied
find: /proc/26/task/26/fd: Permission denied
find: /proc/26/task/26/fdinfo: Permission denied
find: /proc/26/fd: Permission denied
find: /proc/26/fdinfo: Permission denied
find: /proc/27/task/27/fd: Permission denied
find: /proc/27/task/27/fdinfo: Permission denied
find: /proc/27/fd: Permission denied
find: /proc/27/fdinfo: Permission denied
find: /proc/28/task/28/fd: Permission denied
find: /proc/28/task/28/fdinfo: Permission denied
find: /proc/28/fd: Permission denied
find: /proc/28/fdinfo: Permission denied
find: /proc/118/task/118/fd: Permission denied
find: /proc/118/task/118/fdinfo: Permission denied
find: /proc/118/fd: Permission denied
find: /proc/118/fdinfo: Permission denied
find: /proc/137/task/137/fd: Permission denied
find: /proc/137/task/137/fdinfo: Permission denied
find: /proc/137/fd: Permission denied
find: /proc/137/fdinfo: Permission denied
find: /proc/138/task/138/fd: Permission denied
find: /proc/138/task/138/fdinfo: Permission denied
find: /proc/138/fd: Permission denied
find: /proc/138/fdinfo: Permission denied
find: /proc/139/task/139/fd: Permission denied
find: /proc/139/task/139/fdinfo: Permission denied
find: /proc/139/fd: Permission denied
find: /proc/139/fdinfo: Permission denied
find: /proc/190/task/190/fd: Permission denied
find: /proc/190/task/190/fdinfo: Permission denied
find: /proc/190/fd: Permission denied
find: /proc/190/fdinfo: Permission denied
find: /proc/1998/task/1998/fd: Permission denied
find: /proc/1998/task/1998/fdinfo: Permission denied
find: /proc/1998/fd: Permission denied
find: /proc/1998/fdinfo: Permission denied
find: /proc/1999/task/1999/fd: Permission denied
find: /proc/1999/task/1999/fdinfo: Permission denied
find: /proc/1999/fd: Permission denied
find: /proc/1999/fdinfo: Permission denied
find: /proc/2002/task/2002/fd: Permission denied
find: /proc/2002/task/2002/fdinfo: Permission denied
find: /proc/2002/fd: Permission denied
find: /proc/2002/fdinfo: Permission denied
find: /proc/2003/task/2003/fd: Permission denied
find: /proc/2003/task/2003/fdinfo: Permission denied
find: /proc/2003/fd: Permission denied
find: /proc/2003/fdinfo: Permission denied
find: /proc/2041/task/2041/fd: Permission denied
find: /proc/2041/task/2041/fdinfo: Permission denied
find: /proc/2041/fd: Permission denied
find: /proc/2041/fdinfo: Permission denied
find: /proc/2042/task/2042/fd: Permission denied
find: /proc/2042/task/2042/fdinfo: Permission denied
find: /proc/2042/fd: Permission denied
find: /proc/2042/fdinfo: Permission denied
find: /proc/2482/task/2482/fd: Permission denied
find: /proc/2482/task/2482/fdinfo: Permission denied
find: /proc/2482/fd: Permission denied
find: /proc/2482/fdinfo: Permission denied
find: /proc/2687/task/2687/fd: Permission denied
find: /proc/2687/task/2687/fdinfo: Permission denied
find: /proc/2687/fd: Permission denied
find: /proc/2687/fdinfo: Permission denied
find: /proc/3626/task/3626/fd: Permission denied
find: /proc/3626/task/3626/fdinfo: Permission denied
find: /proc/3626/fd: Permission denied
find: /proc/3626/fdinfo: Permission denied
find: /proc/3757/task/3757/fd: Permission denied
find: /proc/3757/task/3757/fdinfo: Permission denied
find: /proc/3757/fd: Permission denied
find: /proc/3757/fdinfo: Permission denied
find: /proc/3987/task/3987/fd: Permission denied
find: /proc/3987/task/3987/fdinfo: Permission denied
find: /proc/3987/fd: Permission denied
find: /proc/3987/fdinfo: Permission denied
find: /proc/3988/task/3988/fd: Permission denied
find: /proc/3988/task/3988/fdinfo: Permission denied
find: /proc/3988/fd: Permission denied
find: /proc/3988/fdinfo: Permission denied
find: /proc/3989/task/3989/fd: Permission denied
find: /proc/3989/task/3989/fdinfo: Permission denied
find: /proc/3989/fd: Permission denied
find: /proc/3989/fdinfo: Permission denied
find: /proc/4227/task/4227/fd: Permission denied
find: /proc/4227/task/4227/fdinfo: Permission denied
find: /proc/4227/fd: Permission denied
find: /proc/4227/fdinfo: Permission denied
find: /proc/4228/task/4228/fd: Permission denied
find: /proc/4228/task/4228/fdinfo: Permission denied
find: /proc/4228/fd: Permission denied
find: /proc/4228/fdinfo: Permission denied
find: /proc/4232/task/4232/fd: Permission denied
find: /proc/4232/task/4232/fdinfo: Permission denied
find: /proc/4232/fd: Permission denied
find: /proc/4232/fdinfo: Permission denied
find: /proc/4233/task/4233/fd: Permission denied
find: /proc/4233/task/4233/fdinfo: Permission denied
find: /proc/4233/fd: Permission denied
find: /proc/4233/fdinfo: Permission denied
find: /proc/4234/task/4234/fd: Permission denied
find: /proc/4234/task/4234/fdinfo: Permission denied
find: /proc/4234/fd: Permission denied
find: /proc/4234/fdinfo: Permission denied
find: /proc/4239/task/4239/fd: Permission denied
find: /proc/4239/task/4239/fdinfo: Permission denied
find: /proc/4239/fd: Permission denied
find: /proc/4239/fdinfo: Permission denied
find: /proc/4413/task/4413/fd: Permission denied
find: /proc/4413/task/4413/fdinfo: Permission denied
find: /proc/4413/fd: Permission denied
find: /proc/4413/fdinfo: Permission denied
find: /proc/4450/task/4450/fd: Permission denied
find: /proc/4450/task/4450/fdinfo: Permission denied
find: /proc/4450/fd: Permission denied
find: /proc/4450/fdinfo: Permission denied
find: /proc/4519/task/4519/fd: Permission denied
find: /proc/4519/task/4519/fdinfo: Permission denied
find: /proc/4519/fd: Permission denied
find: /proc/4519/fdinfo: Permission denied
find: /proc/4575/task/4575/fd: Permission denied
find: /proc/4575/task/4575/fdinfo: Permission denied
find: /proc/4575/fd: Permission denied
find: /proc/4575/fdinfo: Permission denied
find: /proc/4577/task/4577/fd: Permission denied
find: /proc/4577/task/4577/fdinfo: Permission denied
find: /proc/4577/fd: Permission denied
find: /proc/4577/fdinfo: Permission denied
find: /proc/4598/task/4598/fd: Permission denied
find: /proc/4598/task/4598/fdinfo: Permission denied
find: /proc/4598/fd: Permission denied
find: /proc/4598/fdinfo: Permission denied
find: /proc/4614/task/4614/fd: Permission denied
find: /proc/4614/task/4614/fdinfo: Permission denied
find: /proc/4614/task/4748/fd: Permission denied
find: /proc/4614/task/4748/fdinfo: Permission denied
find: /proc/4614/fd: Permission denied
find: /proc/4614/fdinfo: Permission denied
find: /proc/4628/task/4628/fd: Permission denied
find: /proc/4628/task/4628/fdinfo: Permission denied
find: /proc/4628/fd: Permission denied
find: /proc/4628/fdinfo: Permission denied
find: /proc/4641/task/4641/fd: Permission denied
find: /proc/4641/task/4641/fdinfo: Permission denied
find: /proc/4641/fd: Permission denied
find: /proc/4641/fdinfo: Permission denied
find: /proc/4642/task/4642/fd: Permission denied
find: /proc/4642/task/4642/fdinfo: Permission denied
find: /proc/4642/fd: Permission denied
find: /proc/4642/fdinfo: Permission denied
find: /proc/4661/task/4661/fd: Permission denied
find: /proc/4661/task/4661/fdinfo: Permission denied
find: /proc/4661/fd: Permission denied
find: /proc/4661/fdinfo: Permission denied
find: /proc/4662/task/4662/fd: Permission denied
find: /proc/4662/task/4662/fdinfo: Permission denied
find: /proc/4662/fd: Permission denied
find: /proc/4662/fdinfo: Permission denied
find: /proc/4713/task/4713/fd: Permission denied
find: /proc/4713/task/4713/fdinfo: Permission denied
find: /proc/4713/fd: Permission denied
find: /proc/4713/fdinfo: Permission denied
find: /proc/4719/task/4719/fd: Permission denied
find: /proc/4719/task/4719/fdinfo: Permission denied
find: /proc/4719/fd: Permission denied
find: /proc/4719/fdinfo: Permission denied
find: /proc/4720/task/4720/fd: Permission denied
find: /proc/4720/task/4720/fdinfo: Permission denied
find: /proc/4720/fd: Permission denied
find: /proc/4720/fdinfo: Permission denied
find: /proc/4721/task/4721/fd: Permission denied
find: /proc/4721/task/4721/fdinfo: Permission denied
find: /proc/4721/fd: Permission denied
find: /proc/4721/fdinfo: Permission denied
find: /proc/4722/task/4722/fd: Permission denied
find: /proc/4722/task/4722/fdinfo: Permission denied
find: /proc/4722/fd: Permission denied
find: /proc/4722/fdinfo: Permission denied
find: /proc/4723/task/4723/fd: Permission denied
find: /proc/4723/task/4723/fdinfo: Permission denied
find: /proc/4723/fd: Permission denied
find: /proc/4723/fdinfo: Permission denied
find: /proc/4732/task/4732/fd: Permission denied
find: /proc/4732/task/4732/fdinfo: Permission denied
find: /proc/4732/fd: Permission denied
find: /proc/4732/fdinfo: Permission denied
find: /proc/4794/task/4794/fd: Permission denied
find: /proc/4794/task/4794/fdinfo: Permission denied
find: /proc/4794/fd: Permission denied
find: /proc/4794/fdinfo: Permission denied
find: /proc/4980/task/4980/fd: Permission denied
find: /proc/4980/task/4980/fdinfo: Permission denied
find: /proc/4980/fd: Permission denied
find: /proc/4980/fdinfo: Permission denied
find: /proc/4998/task/4998/fd: Permission denied
find: /proc/4998/task/4998/fdinfo: Permission denied
find: /proc/4998/task/4999/fd: Permission denied
find: /proc/4998/task/4999/fdinfo: Permission denied
find: /proc/4998/task/5000/fd: Permission denied
find: /proc/4998/task/5000/fdinfo: Permission denied
find: /proc/4998/task/5001/fd: Permission denied
find: /proc/4998/task/5001/fdinfo: Permission denied
find: /proc/4998/task/5002/fd: Permission denied
find: /proc/4998/task/5002/fdinfo: Permission denied
find: /proc/4998/task/5022/fd: Permission denied
find: /proc/4998/task/5022/fdinfo: Permission denied
find: /proc/4998/task/5023/fd: Permission denied
find: /proc/4998/task/5023/fdinfo: Permission denied
find: /proc/4998/task/5025/fd: Permission denied
find: /proc/4998/task/5025/fdinfo: Permission denied
find: /proc/4998/task/5026/fd: Permission denied
find: /proc/4998/task/5026/fdinfo: Permission denied
find: /proc/4998/task/5033/fd: Permission denied
find: /proc/4998/task/5033/fdinfo: Permission denied
find: /proc/4998/task/5034/fd: Permission denied
find: /proc/4998/task/5034/fdinfo: Permission denied
find: /proc/4998/task/5035/fd: Permission denied
find: /proc/4998/task/5035/fdinfo: Permission denied
find: /proc/4998/task/5036/fd: Permission denied
find: /proc/4998/task/5036/fdinfo: Permission denied
find: /proc/4998/task/5037/fd: Permission denied
find: /proc/4998/task/5037/fdinfo: Permission denied
find: /proc/4998/task/5044/fd: Permission denied
find: /proc/4998/task/5044/fdinfo: Permission denied
find: /proc/4998/task/5045/fd: Permission denied
find: /proc/4998/task/5045/fdinfo: Permission denied
find: /proc/4998/task/5046/fd: Permission denied
find: /proc/4998/task/5046/fdinfo: Permission denied
find: /proc/4998/task/5047/fd: Permission denied
find: /proc/4998/task/5047/fdinfo: Permission denied
find: /proc/4998/task/5048/fd: Permission denied
find: /proc/4998/task/5048/fdinfo: Permission denied
find: /proc/4998/task/5052/fd: Permission denied
find: /proc/4998/task/5052/fdinfo: Permission denied
find: /proc/4998/task/5053/fd: Permission denied
find: /proc/4998/task/5053/fdinfo: Permission denied
find: /proc/4998/task/5054/fd: Permission denied
find: /proc/4998/task/5054/fdinfo: Permission denied
find: /proc/4998/task/5055/fd: Permission denied
find: /proc/4998/task/5055/fdinfo: Permission denied
find: /proc/4998/task/5056/fd: Permission denied
find: /proc/4998/task/5056/fdinfo: Permission denied
find: /proc/4998/task/5057/fd: Permission denied
find: /proc/4998/task/5057/fdinfo: Permission denied
find: /proc/4998/task/5058/fd: Permission denied
find: /proc/4998/task/5058/fdinfo: Permission denied
find: /proc/4998/task/5059/fd: Permission denied
find: /proc/4998/task/5059/fdinfo: Permission denied
find: /proc/4998/task/5060/fd: Permission denied
find: /proc/4998/task/5060/fdinfo: Permission denied
find: /proc/4998/task/5061/fd: Permission denied
find: /proc/4998/task/5061/fdinfo: Permission denied
find: /proc/4998/task/5062/fd: Permission denied
find: /proc/4998/task/5062/fdinfo: Permission denied
find: /proc/4998/task/5063/fd: Permission denied
find: /proc/4998/task/5063/fdinfo: Permission denied
find: /proc/4998/task/5064/fd: Permission denied
find: /proc/4998/task/5064/fdinfo: Permission denied
find: /proc/4998/task/5065/fd: Permission denied
find: /proc/4998/task/5065/fdinfo: Permission denied
find: /proc/4998/task/5066/fd: Permission denied
find: /proc/4998/task/5066/fdinfo: Permission denied
find: /proc/4998/task/5067/fd: Permission denied
find: /proc/4998/task/5067/fdinfo: Permission denied
find: /proc/4998/task/5068/fd: Permission denied
find: /proc/4998/task/5068/fdinfo: Permission denied
find: /proc/4998/task/5069/fd: Permission denied
find: /proc/4998/task/5069/fdinfo: Permission denied
find: /proc/4998/task/5070/fd: Permission denied
find: /proc/4998/task/5070/fdinfo: Permission denied
find: /proc/4998/task/5071/fd: Permission denied
find: /proc/4998/task/5071/fdinfo: Permission denied
find: /proc/4998/task/5072/fd: Permission denied
find: /proc/4998/task/5072/fdinfo: Permission denied
find: /proc/4998/task/5073/fd: Permission denied
find: /proc/4998/task/5073/fdinfo: Permission denied
find: /proc/4998/task/5074/fd: Permission denied
find: /proc/4998/task/5074/fdinfo: Permission denied
find: /proc/4998/task/5075/fd: Permission denied
find: /proc/4998/task/5075/fdinfo: Permission denied
find: /proc/4998/task/5076/fd: Permission denied
find: /proc/4998/task/5076/fdinfo: Permission denied
find: /proc/4998/task/5077/fd: Permission denied
find: /proc/4998/task/5077/fdinfo: Permission denied
find: /proc/4998/task/5078/fd: Permission denied
find: /proc/4998/task/5078/fdinfo: Permission denied
find: /proc/4998/task/5079/fd: Permission denied
find: /proc/4998/task/5079/fdinfo: Permission denied
find: /proc/4998/task/5080/fd: Permission denied
find: /proc/4998/task/5080/fdinfo: Permission denied
find: /proc/4998/task/5081/fd: Permission denied
find: /proc/4998/task/5081/fdinfo: Permission denied
find: /proc/4998/task/5082/fd: Permission denied
find: /proc/4998/task/5082/fdinfo: Permission denied
find: /proc/4998/task/5083/fd: Permission denied
find: /proc/4998/task/5083/fdinfo: Permission denied
find: /proc/4998/task/5084/fd: Permission denied
find: /proc/4998/task/5084/fdinfo: Permission denied
find: /proc/4998/task/5085/fd: Permission denied
find: /proc/4998/task/5085/fdinfo: Permission denied
find: /proc/4998/task/5086/fd: Permission denied
find: /proc/4998/task/5086/fdinfo: Permission denied
find: /proc/4998/task/5087/fd: Permission denied
find: /proc/4998/task/5087/fdinfo: Permission denied
find: /proc/4998/task/5088/fd: Permission denied
find: /proc/4998/task/5088/fdinfo: Permission denied
find: /proc/4998/task/5089/fd: Permission denied
find: /proc/4998/task/5089/fdinfo: Permission denied
find: /proc/4998/task/5090/fd: Permission denied
find: /proc/4998/task/5090/fdinfo: Permission denied
find: /proc/4998/task/5091/fd: Permission denied
find: /proc/4998/task/5091/fdinfo: Permission denied
find: /proc/4998/task/5092/fd: Permission denied
find: /proc/4998/task/5092/fdinfo: Permission denied
find: /proc/4998/task/5093/fd: Permission denied
find: /proc/4998/task/5093/fdinfo: Permission denied
find: /proc/4998/task/5203/fd: Permission denied
find: /proc/4998/task/5203/fdinfo: Permission denied
find: /proc/4998/fd: Permission denied
find: /proc/4998/fdinfo: Permission denied
find: /proc/5043/task/5043/fd: Permission denied
find: /proc/5043/task/5043/fdinfo: Permission denied
find: /proc/5043/fd: Permission denied
find: /proc/5043/fdinfo: Permission denied
find: /proc/5094/task/5094/fd: Permission denied
find: /proc/5094/task/5094/fdinfo: Permission denied
find: /proc/5094/fd: Permission denied
find: /proc/5094/fdinfo: Permission denied
find: /proc/5127/task/5127/fd: Permission denied
find: /proc/5127/task/5127/fdinfo: Permission denied
find: /proc/5127/fd: Permission denied
find: /proc/5127/fdinfo: Permission denied
find: /proc/5139/task/5139/fd: Permission denied
find: /proc/5139/task/5139/fdinfo: Permission denied
find: /proc/5139/fd: Permission denied
find: /proc/5139/fdinfo: Permission denied
find: /proc/5140/task/5140/fd: Permission denied
find: /proc/5140/task/5140/fdinfo: Permission denied
find: /proc/5140/fd: Permission denied
find: /proc/5140/fdinfo: Permission denied
find: /proc/5146/task/5146/fd: Permission denied
find: /proc/5146/task/5146/fdinfo: Permission denied
find: /proc/5146/fd: Permission denied
find: /proc/5146/fdinfo: Permission denied
find: /proc/5176/task/5176/fd: Permission denied
find: /proc/5176/task/5176/fdinfo: Permission denied
find: /proc/5176/fd: Permission denied
find: /proc/5176/fdinfo: Permission denied
find: /proc/5179/task/5179/fd: Permission denied
find: /proc/5179/task/5179/fdinfo: Permission denied
find: /proc/5179/fd: Permission denied
find: /proc/5179/fdinfo: Permission denied
find: /proc/5184/task/5184/fd: Permission denied
find: /proc/5184/task/5184/fdinfo: Permission denied
find: /proc/5184/fd: Permission denied
find: /proc/5184/fdinfo: Permission denied
find: /proc/5209/task/5209/fd: Permission denied
find: /proc/5209/task/5209/fdinfo: Permission denied
find: /proc/5209/fd: Permission denied
find: /proc/5209/fdinfo: Permission denied
find: /proc/5243/task/5243/fd: Permission denied
find: /proc/5243/task/5243/fdinfo: Permission denied
find: /proc/5243/fd: Permission denied
find: /proc/5243/fdinfo: Permission denied
find: /proc/5257/task/5257/fd: Permission denied
find: /proc/5257/task/5257/fdinfo: Permission denied
find: /proc/5257/fd: Permission denied
find: /proc/5257/fdinfo: Permission denied
find: /proc/5458/task/5458/fd: Permission denied
find: /proc/5458/task/5458/fdinfo: Permission denied
find: /proc/5458/fd: Permission denied
find: /proc/5458/fdinfo: Permission denied
find: /proc/6948/task/6948/fd: Permission denied
find: /proc/6948/task/6948/fdinfo: Permission denied
find: /proc/6948/fd: Permission denied
find: /proc/6948/fdinfo: Permission denied
find: /var/lib/slocate: Permission denied
find: /var/lib/gdm: Permission denied
find: /var/spool/cron/atjobs: Permission denied
find: /var/spool/cron/crontabs: Permission denied
find: /var/spool/cron/atspool: Permission denied
find: /var/spool/cups: Permission denied
find: /var/run/sudo: Permission denied
find: /var/run/cups/certs: Permission denied
find: /tmp/gconfd-root: Permission denied
find: /tmp/orbit-root: Permission denied
lance@lance-desktop:~$ 



I know that's long but thought you'd want to see it all.

---

### Post by nanotube on 2009-01-02
Hi,
aha ok i see

i looked up the default firefox package contents on gutsy, it looks like it doesn't even come with a libnullplugin.so. that's ok though, because it does come with a libunixprintplugin.so, so i can use that instead if there's no libnullplugin.so.

well, thanks for your help, i now know what to do to make this work on gutsy (without breaking anything else). man, is gutsy a mess or what... :)

i'm away from my main comp right now, will post a new version on monday.

in the meantime, if you care to, you can try putting in the plugin path manually. with the default firefox install on gutsy, it should be in /usr/lib/firefox/plugins :)

---

### Post by kansasnoob on 2009-01-03
> **nanotube said:**
> Hi,
aha ok i see

i looked up the default firefox package contents on gutsy, it looks like it doesn't even come with a libnullplugin.so. that's ok though, because it does come with a libunixprintplugin.so, so i can use that instead if there's no libnullplugin.so.

well, thanks for your help, i now know what to do to make this work on gutsy (without breaking anything else). man, is gutsy a mess or what... :)

i'm away from my main comp right now, will post a new version on monday.

in the meantime, if you care to, you can try putting in the plugin path manually. with the default firefox install on gutsy, it should be in /usr/lib/firefox/plugins :)

That worked!

I'm now trying your new script on an installed, fully updated Mint 5 (which is based on Hardy). Although it seems they have evrything right there at this time.

It would still be good to know if it works!

I just hope you don't think I'm pushing you to get this done.

I'm just testing, and IMHO the best way is with an installed updated OS.

And I actually enjoy doing it!

OTOH if I ever do something stupid or just wrong don't hesitate to tell me! I have a thick skin.

Bottom line: Ubuntuzilla deserves kudos on Distrowatch!

And stop thanking me! You're doing all the work! So thank you!

---

### Post by kansasnoob on 2009-01-03
Your new installation script worked perfectly on Mint 5 (which is based on Hardy).

I'm going to look for a DL of the freshest Dapper (which won't be very fresh) but I'm sure Ubuntu did daily builds that are archived for Dapper just as they are for Hardy.

The only other thing left would be Mint 4 which is based on Gutsy! We know about Gutsy and there's only a few months left there for general support!

---

### Post by kansasnoob on 2009-01-03
OK, I've now tested your new installer in everything still supported by Ubuntu or Mint.

In Intrepid, Hardy, Mint 6 and Mint 5 it installs FF3.0.5 flawlessly.

In both Gutsy and Mint 4 I have to manually enter the plugin path "/usr/lib/firefox/plugins". That's also for installing FF3.0.5.

In Dapper, even though I installed FF2.0.0.20, I still had to manually enter the plugin path - still: "/usr/lib/firefox/plugins".

I hope that helps.

I'll check back later on next week and test the newest version again if you'd like. I might skip Dapper though. I know it was great in it's time but wow .......... Ubuntu's come a long ways since then!

---

### Post by nanotube on 2009-01-04
Hi,
Thanks for the detailed test results! :)

Yea the dapper problem is the same as the gutsy problem, so should be fixed with the same fix.

Not to worry, i'm actually keen on getting this fixed myself, so that i don't have to keep updating the version-check code with every new ubuntu release. so you're not pushing me to do anything i don't want :)

also, testing is quite an important part of any software operation, so... i think i'm quite justified in thanking you. :)

---

### Post by kansasnoob on 2009-01-04
I'm glad to help.

This is an awesome project!

I'll probably be gone most of tomorrow (Monday) but I'd be happy to retest the final changes.

You do great work!

BTW, this testing gave me time to try some xorg testing too which should prove useful in the future.

But, wow ............. I'll be glad when Dapper desktop is officially retired in June!

---

### Post by nanotube on 2009-01-06
Hi
ok, i posted the latest version to test in the testing thread, here:
[http://ubuntuforums.org/showthread.php?p=6504115](http://ubuntuforums.org/showthread.php?p=6504115)

should now work on dapper, gutsy, and all the rest of them.
please try and let me know if it does what it should. :)

indeed, supporting older versions is a pain... imagine ubuntu doing that for the whole distro. :) but then again, they have different versions of the packages for the ubuntu versions, whereas i'm trying to support them all with one version of ubuntuzilla. so maybe they're onto something with that idea. :)

---

### Post by kansasnoob on 2009-01-06
> **nanotube said:**
> Hi
ok, i posted the latest version to test in the testing thread, here:
[http://ubuntuforums.org/showthread.php?p=6504115](http://ubuntuforums.org/showthread.php?p=6504115)

should now work on dapper, gutsy, and all the rest of them.
please try and let me know if it does what it should. :)

indeed, supporting older versions is a pain... imagine ubuntu doing that for the whole distro. :) but then again, they have different versions of the packages for the ubuntu versions, whereas i'm trying to support them all with one version of ubuntuzilla. so maybe they're onto something with that idea. :)

I may be able to get to that later this evening, more likely tomorrow. I'll start with the most recent distros and work backwards.

Sorry for the delay but I'm dealing with a sick dog. Thanks again!

---

### Post by nanotube on 2009-01-06
> **kansasnoob said:**
> I may be able to get to that later this evening, more likely tomorrow. I'll start with the most recent distros and work backwards.

Sorry for the delay but I'm dealing with a sick dog. Thanks again!

Hi,
No hurry, tomorrow's good.
my best wishes towards your dog's quick recovery!

---

### Post by kansasnoob on 2009-01-06
I had a break so I completed the first test. Ubuntu 8.10 went great. I'll post the results at the new script download site so it'll be easier to compare results!

As far as the dog being sick, he's always sick! He was a rescue from a puppy-mill! I can't say what I think about puppy-mills here!

I have two, can't afford more than two, that and my aging fainting goats keep me broke! But the vet gives me a free cap once a year:D

---

### Post by nanotube on 2009-01-06
> **kansasnoob said:**
> I had a break so I completed the first test. Ubuntu 8.10 went great. I'll post the results at the new script download site so it'll be easier to compare results!


sounds good. :)

> 
As far as the dog being sick, he's always sick! He was a rescue from a puppy-mill! I can't say what I think about puppy-mills here!

I have two, can't afford more than two, that and my aging fainting goats keep me broke! But the vet gives me a free cap once a year:D

well... best wishes all the more so. :)

---

