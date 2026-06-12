---
title: "New Ubuntuzilla apt repository. Ubuntuzilla users, update your sources.list!"
date: 2009-11-11
forum: Ubuntuzilla
---

### Post by nanotube on 2009-11-11
New ubuntuzilla apt repository has been created for your convenience.

Now, instead of installing the script, then using the script to install, you can add the ubuntuzilla repository to your sources.list and use apt-get install to directly install firefox, thunderbird, and seamonkey.

For more details, see the ubuntuzilla website, in the "installation" section:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

Current users of ubuntuzilla should run "ubuntuzilla.py -a remove -p yourpackage" before installing these packages, to undo the local diversion of /usr/bin/(package) links.

Please let me know if you run into any trouble with it.

...Edited to reflect the latest info.

---

### Post by JBAlaska on 2009-11-11
Guest axx: ```
http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Repository_method
```

---

### Post by nanotube on 2009-11-11
> **JBAlaska said:**
> Guest axx: ```
http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Repository_method
```

err, that's the same page, two lines further down... ?

---

### Post by kansasnoob on 2009-11-11
I'm in!

I'm also fighting a mold problem (yuck, I know, stupid shaded north walls) so it may take me about 2 days to complete this.

But I'd just updated my Karmic to Lucid and intended to repartition anyway to reinstall a fresh Karmic for continued testing.

How about if I start with Hardy? I'd think that would be practical.

---

### Post by nanotube on 2009-11-11
> **kansasnoob said:**
> I'm in!

great! :)

> 
I'm also fighting a mold problem (yuck, I know, stupid shaded north walls) so it may take me about 2 days to complete this.

grr mold...

> 
But I'd just updated my Karmic to Lucid and intended to repartition anyway to reinstall a fresh Karmic for continued testing.

How about if I start with Hardy? I'd think that would be practical.
any version is fine. the actual .deb has not changed, just that i put it into an apt repo. ;)

---

### Post by kansasnoob on 2009-11-11
I can delay some of my other stuff, so I plan to do this (I'm disgusted with Karmic boot problems anyway):

[ATTACH]135802[/ATTACH]

sda11 will be Hardy
sda12 will be Intrepid (if needed, I seem to recall you use Intrepid)
sda13 will be whatever (we'll know what it should be when we get that far)!

Does that sound good?

I'm thinking we should know what direction to go in each step along the way.

Bravo for taking this step!

Feel free to PM.

PS, about the Karmic boot problems:

[http://ubuntuforums.org/showthread.php?t=1323232](http://ubuntuforums.org/showthread.php?t=1323232)

---

### Post by nanotube on 2009-11-11
heh that's a lot of partitions - have you considered just using virtualbox for all those? :)

as to karmic: i'm still on intrepid, so... doesn't bother me :P

---

### Post by kansasnoob on 2009-11-12
Went great in Hardy:

> lance@lance-desktop:~$ echo "deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null
lance@lance-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for lance: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
lance@lance-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Get:1 [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release.gpg [197B]                  
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Get:2 [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release [1632B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Get:3 [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages [595B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 2424B in 1s (2103B/s)
Reading package lists... Done
lance@lance-desktop:~$ sudo apt-get install ubuntuzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic linux-headers-2.6.24-24
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnotify-bin
The following NEW packages will be installed:
  libnotify-bin ubuntuzilla
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.7kB of archives.
After this operation, 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libnotify-bin 0.4.4-3build1 [19.6kB]
Get:2 [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main ubuntuzilla 4.7.8-0ubuntu1 [21.0kB]
Fetched 40.7kB in 0s (56.5kB/s)                                    
Selecting previously deselected package libnotify-bin.
(Reading database ... 115255 files and directories currently installed.)
Unpacking libnotify-bin (from .../libnotify-bin_0.4.4-3build1_i386.deb) ...
Selecting previously deselected package ubuntuzilla.
Unpacking ubuntuzilla (from .../ubuntuzilla_4.7.8-0ubuntu1_i386.deb) ...
Setting up libnotify-bin (0.4.4-3build1) ...
Setting up ubuntuzilla (4.7.8-0ubuntu1) ...
lance@lance-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.7.8

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.5.

Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af         Afrikaans [Afrikaans]         
  1. ar         Arabic [&#1593;&#1585;&#1576;&#1610;]             
  2. as         Assamese [&#2437;&#2488;&#2478;&#2496;&#2479;&#2492;&#2494;]
  3. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  4. bg         Bulgarian [&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;]
  5. bn-BD      Bengali (Bangladesh) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2476;&#2494;&#2434;&#2482;&#2494;&#2470;&#2503;&#2486;)]
  6. bn-IN      Bengali (India) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2477;&#2494;&#2480;&#2468;)]
  7. ca         Catalan [català]             
  8. cs         Czech [&#268;eština]             
  9. cy                                       
 10. da         Danish [Dansk]                
 11. de         German [Deutsch]              
 12. el         Greek [&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;]      
 13. en-GB      English (British) [English (British)]
 14. en-US      English (US) [English (US)]   
 15. eo         Esperanto [Esperanto]         
 16. es-AR      Spanish (Argentina) [Español (de Argentina)]
 17. es-CL      Spanish (Chile) [Español (de Chile)]
 18. es-ES      Spanish (Spain) [Español (de España)]
 19. es-MX      Spanish (Mexico) [Español (de México)]
 20. et         Estonian [Eesti keel]         
 21. eu         Basque [Euskara]              
 22. fa         Persian [&#1601;&#1575;&#1585;&#1587;&#1740;]          
 23. fi         Finnish [suomi]               
 24. fr         French [Français]            
 25. fy-NL      Frisian [Frysk]               
 26. ga-IE      Irish [Gaeilge]               
 27. gl         Galician [Galego]             
 28. gu-IN      Gujarati [&#2711;&#2753;&#2716;&#2736;&#2750;&#2724;&#2752;]
 29. he         Hebrew [&#1506;&#1489;&#1512;&#1497;&#1514;]           
 30. hi-IN      Hindi (India) [&#2361;&#2367;&#2344;&#2381;&#2342;&#2368; (&#2349;&#2366;&#2352;&#2340;)]
 31. hr         Croatian [Hrvatski]           
 32. hu         Hungarian [Magyar]            
 33. id         Indonesian [Bahasa Indonesia] 
 34. is         Icelandic [íslenska]         
 35. it         Italian [Italiano]            
 36. ja         Japanese [&#26085;&#26412;&#35486;]          
 37. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 38. kk         Kazakh [&#1178;&#1072;&#1079;&#1072;&#1179;]           
 39. kn         Kannada [&#3221;&#3240;&#3277;&#3240;&#3233;]     
 40. ko         Korean [&#54620;&#44397;&#50612;]            
 41. ku         Kurdish [Kurdî]              
 42. lt         Lithuanian [lietuvi&#371; kalba]  
 43. lv         Latvian [Latviešu]           
 44. mk         Macedonian [&#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;]
 45. ml         Malayalam [&#3374;&#3378;&#3375;&#3390;&#3379;&#3330;]
 46. mn         Mongolian [&#1052;&#1086;&#1085;&#1075;&#1086;&#1083;]      
 47. mr         Marathi [&#2350;&#2352;&#2366;&#2336;&#2368;]     
 48. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 49. nl         Dutch [Nederlands]            
 50. nn-NO      Norwegian (Nynorsk) [Norsk nynorsk]
 51. oc         Occitan (Lengadocian) [occitan (lengadocian)]
 52. or         Oriya [&#2835;&#2849;&#2876;&#2879;&#2822;]       
 53. pa-IN      Punjabi [&#2602;&#2672;&#2588;&#2622;&#2604;&#2624;]  
 54. pl         Polish [Polski]               
 55. pt-BR      Portuguese (Brazilian) [Português (do Brasil)]
 56. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 57. rm         Romansh [rumantsch]           
 58. ro         Romanian [român&#259;]           
 59. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 60. si         Sinhala [&#3523;&#3538;&#3458;&#3524;&#3517;]     
 61. sk         Slovak [sloven&#269;ina]          
 62. sl         Slovenian [slovensko]         
 63. sq         Albanian [Shqip]              
 64. sr         Serbian [&#1057;&#1088;&#1087;&#1089;&#1082;&#1080;]        
 65. sv-SE      Swedish [Svenska]             
 66. ta-LK      Tamil (Sri Lanka) [&#2980;&#2990;&#3007;&#2996;&#3021; (&#2951;&#2994;&#2969;&#3021;&#2965;&#3016;)]
 67. ta         Tamil [&#2980;&#2990;&#3007;&#2996;&#3021;]       
 68. te         Telugu [&#3108;&#3142;&#3122;&#3137;&#3095;&#3137;]   
 69. th         Thai [&#3652;&#3607;&#3618;]              
 70. tr         Turkish [Türkçe]            
 71. uk         Ukrainian [&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;]
 72. vi         Vietnamese [Ti&#7871;ng Vi&#7879;t]   
 73. zh-CN      Chinese (Simplified) [&#20013;&#25991; (&#31616;&#20307;)]
 74. zh-TW      Chinese (Traditional) [&#27491;&#39636;&#20013;&#25991; (&#32321;&#39636;)]

Enter your choice of localization (integer, from 0 to 74): 14
You have chosen localization en-US, English (US) [English (US)]. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release.gpg                           
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic linux-headers-2.6.24-24
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.5.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--03:56:52--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2)
           => `firefox-3.5.5.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.5.5.tar.bz2 ... done.
Length: 9,924,119 (9.5M) (unauthoritative)

100%[====================================>] 9,924,119    599.53K/s    ETA 00:00

03:57:10 (592.48 KB/s) - `firefox-3.5.5.tar.bz2' saved [9924119]


Downloading Firefox signature from the Mozilla site

--03:57:10--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2.asc](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2.asc)
           => `firefox-3.5.5.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.5.5.tar.bz2.asc ... done.
Length: 194 (unauthoritative)

100%[====================================>] 194           --.--K/s             

03:57:11 (21.98 KB/s) - `firefox-3.5.5.tar.bz2.asc' saved [194]

tru::1:1258015379:0:3:1:5
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

gpg: Signature made Mon 02 Nov 2009 09:51:42 PM CST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8

Extracting archive

Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/xulrunner-addons/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.5 has been installed successfully.

Make sure to completely quit the old version of Firefox for the change to take effect.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
no crontab for lance
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 



---

### Post by nanotube on 2009-11-12
Great! so the repository works not just for me, that's all i needed to confirm :)

Thanks a lot! No need to test this further at the moment, since the actual .deb is the same as before.

By the way, for the future, for next time we're testing stuff, when you paste output, put it in 'code' tags rather than 'quote' tags, that way it will get a scrollbar, and won't get smileys parsed and all that. :)

---

### Post by kansasnoob on 2009-11-12
I went ahead and tried this on Mint 6 (based on Intrepid) just to see and it works fine there too.

I figured it would since Mint uses Ubuntu repos.

I appreciate you handling the GPG key in the manner you did, much simpler than trying to explain to someone how create and import the text file :)

Very good work!

Now back to the glorious mess that is Karmic. Shhhh, don't tell anyone I said that. It really has been problematic though.

---

### Post by nanotube on 2009-11-12
> **kansasnoob said:**
> I went ahead and tried this on Mint 6 (based on Intrepid) just to see and it works fine there too.

I figured it would since Mint uses Ubuntu repos.

cool :) 

> 
I appreciate you handling the GPG key in the manner you did, much simpler than trying to explain to someone how create and import the text file :)

Very good work!

thanks! ;)

> 
Now back to the glorious mess that is Karmic. Shhhh, don't tell anyone I said that. It really has been problematic though.

heh, i'm waiting for lucid. :P

---

### Post by krakos2 on 2009-12-05
hi everyone,

i get some problems to get the key for the ubuntuzilla packet. How can i fix it please?



$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CCC158AFC1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring/etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com CCC158AFC1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by nanotube on 2009-12-05
> **krakos2 said:**
> hi everyone,

i get some problems to get the key for the ubuntuzilla packet. How can i fix it please?



$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CCC158AFC1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring/etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com CCC158AFC1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Hi,
are you by any chance behind a firewall of some sort?

also, i see you're using 'CCC158AFC1289A29' instead of 'C1289A29' for key id request...?

---

### Post by crisnoh on 2009-12-08
I'm having trouble with the script when trying to install Thunderbird.  My issue also seems to be related to gpg.

```
tru::1:1259964036:1417643949:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1259964036:1417643949:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2011-07-20::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2011-07-20:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2011-07-20:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Sat 05 Dec 2009 03:23:40 PM EST using RSA key ID 6CE2996F
gpg: Can't check signature: public key not found
Key verification failed. This is most likely due to a corrupt download. You should delete files ' thunderbird-3.0.tar.bz2.asc ' and ' thunderbird-3.0.tar.bz2 ' and run the script again.
```

---

### Post by nanotube on 2009-12-08
Hi

thanks for pointing this out!

the thunderbird3 release is signed with a new mozilla messaging gpg key
i have now added this key to ubuntuzilla key checks, so please upgrade to the latest ubuntuzilla (ubuntuzilla 4.8.2), and give it another try!

---

### Post by ronewolf on 2009-12-27
the repository method doesn't work for me (Hardy) some sort of lpia conflict or lack of support for.... 

working off of the instructions in [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Repository_method](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Repository_method)

[INDENT]sudo apt-get update [/INDENT]

eventually results in

[INDENT]W: Failed to fetch [http://switch.dl.sourceforge.net/project/ubuntuzilla/apt/dists/all/Release](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)[/INDENT]

see the attachment for the complete story (let me know if this is not the right way to post this stuff)

off topic ---> if anyone can tell me how to get a better repository list (like getting away from the Dell madness, i would welcome the lead)

---

### Post by nanotube on 2009-12-28
i take it you are using a dell mini, with the stock 'dell-buntu' install?

well, yea, i didn't add the 'lpia' architecture to the ubuntuzilla repo, because i didn't realize there was a separate arch listing for that... afaik, it should run i386 stuff just fine.

well, so, for now, just grab the .deb manually and install it... and maybe at some point later i'll get around to adding the lpia arch to the repo :)

(btw, did you by any chance happen to get that dell vostro a90 at the recent black friday/cyber monday sale? )

---

### Post by nskipper1 on 2010-01-17
Added the repository in Synaptic (Karmic). Installed Firefox-Mozilla-Build 3.5.6 no problem. BUT, when 3.5.7 became available, it did not show up in "Installed (upgradable)" section of Synaptic. The new version was displayed in the entry in the "ALL" section and I was able to upgrade to 3.5.7 no problem. 

Any idea why it did not show up in "Installed (upgradable)" section of Synaptic?

---

### Post by nanotube on 2010-01-18
> **nskipper1 said:**
> Added the repository in Synaptic (Karmic). Installed Firefox-Mozilla-Build 3.5.6 no problem. BUT, when 3.5.7 became available, it did not show up in "Installed (upgradable)" section of Synaptic. The new version was displayed in the entry in the "ALL" section and I was able to upgrade to 3.5.7 no problem. 

Any idea why it did not show up in "Installed (upgradable)" section of Synaptic?

no idea... are you sure you installed the correct package before? package "firefox-mozilla-build" ?

---

### Post by bug67 on 2010-01-18
Forgive my n00bness.  I'm sure I'm missing something elementary.  

When I copy and paste this code to the terminal:

```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

I get the following reply:

```
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found

```

:confused:  ](*,)

**_EDIT_**:

Duh!  That's 'cause it doesn't *go* in the terminal!  It goes in "software sources."  Where's the signing key so I don't get the error:

```
W: GPG error: http://downloads.sourceforge.net all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
```

?

---

### Post by nanotube on 2010-01-18
> **bug67 said:**
> 
Duh!  That's 'cause it doesn't *go* in the terminal!  It goes in "software sources."  
glad you figured it out :)

> 
Where's the signing key so I don't get the error:

```
W: GPG error: http://downloads.sourceforge.net all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
```

?

there's a command given in the installation instructions on the ubuntuzilla website for retrieving the key:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

out of curiosity: where are you getting the instructions from, that it's missing this info?

---

### Post by nskipper1 on 2010-01-18
> **nanotube said:**
> no idea... are you sure you installed the correct package before? package "firefox-mozilla-build" ?

Positive. Strange nobody else has reported this, although you wouldn't know unless you were looking for an upgrade to a specific package.

---

### Post by bug67 on 2010-01-18
> **nanotube said:**
> glad you figured it out :)



there's a command given in the installation instructions on the ubuntuzilla website for retrieving the key:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

out of curiosity: where are you getting the instructions from, that it's missing this info?

From here:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

But, I found it.  Didn't look hard enough before.  It didn't jump right out at me.  :P

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

Thanks!

---

### Post by nanotube on 2010-01-18
> **bug67 said:**
> From here:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

But, I found it.  Didn't look hard enough before.  It didn't jump right out at me.  :P

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

Thanks!

ah ok cool :)

---

### Post by nanotube on 2010-01-18
> **nskipper1 said:**
> Positive. Strange nobody else has reported this, although you wouldn't know unless you were looking for an upgrade to a specific package.

wait, so just to clarify - did it show up in the update manager? just not in synaptic when you look for 'upgradeable' packages? 

i've seen it show up in update manager myself, and others have reported the same - but i haven't tried looking at what synaptic specifically does... so you're reporting specifically the synaptic thing, not the update manager thing?

---

### Post by nskipper1 on 2010-01-19
> **nanotube said:**
> wait, so just to clarify - did it show up in the update manager? just not in synaptic when you look for 'upgradeable' packages? 

i've seen it show up in update manager myself, and others have reported the same - but i haven't tried looking at what synaptic specifically does... so you're reporting specifically the synaptic thing, not the update manager thing?


Yes. I don't use Update Manager normally. I fired it up and thunderbird-mozilla-build showed up as upgradable. Closed it and fired up Synaptic and thunderbird-mozilla-build shows that a new version is available but is not listed under Installed (upgradable). However, it does display the star in the box indicating that it is upgradable. Very strange.

---

### Post by nanotube on 2010-01-19
> **nskipper1 said:**
> Yes. I don't use Update Manager normally. I fired it up and thunderbird-mozilla-build showed up as upgradable. Closed it and fired up Synaptic and thunderbird-mozilla-build shows that a new version is available but is not listed under Installed (upgradable). However, it does display the star in the box indicating that it is upgradable. Very strange.

indeed, very strange... which version of ubuntu is it? 

thunderbird 3.0.1 is coming out tomorrow, i'll ask people to give it a test-look in synaptic...

---

### Post by nskipper1 on 2010-01-19
> **nanotube said:**
> indeed, very strange... which version of ubuntu is it? 

thunderbird 3.0.1 is coming out tomorrow, i'll ask people to give it a test-look in synaptic...


Ubuntu 9.10 (karmic) 2.6.31-17-generic

Thanks for your help and the repository.

---

### Post by nanotube on 2010-01-20
> **nskipper1 said:**
> Ubuntu 9.10 (karmic) 2.6.31-17-generic

Thanks for your help and the repository.

well... i tested it on karmic, after i pushed out tbird 3.0.1 update.

thing is... it shows up just fine in synaptic, when i go to 'custom filters' -> 'upgradeable (upstream)', there it is, with a green box with a star in it, showing up.

edit: screenshot

---

### Post by nskipper1 on 2010-01-20
> **nanotube said:**
> well... i tested it on karmic, after i pushed out tbird 3.0.1 update.

thing is... it shows up just fine in synaptic, when i go to 'custom filters' -> 'upgradeable (upstream)', there it is, with a green box with a star in it, showing up.

edit: screenshot

I don't know what 'upgradeable (upstream)' is. It should show up in 'Status' -> 'Installed (upgradable)' like all of the other packages that are installed and upgradable.

I did notice that your packages have a 'Priority' (found under package properties) of 'extra' while every other package I looked at had a Priority of 'optional' or 'required'. Might be freaking out Synaptic somehow.

---

### Post by nanotube on 2010-01-20
> **nskipper1 said:**
> I don't know what 'upgradeable (upstream)' is. It should show up in 'Status' -> 'Installed (upgradable)' like all of the other packages that are installed and upgradable.

I did notice that your packages have a 'Priority' (found under package properties) of 'extra' while every other package I looked at had a Priority of 'optional' or 'required'. Might be freaking out Synaptic somehow.

ah, ok, i don't usually use synaptic to check for updates... sorry. 

but i took a look at status -> installed (upgradeable), and it's showing up there too, without any difficulties. 

see attached screenshot.
does it still not show up for you in there, after an apt-get update (or synaptic reload)?

i'll investigate the 'priority' bit...

---

### Post by nanotube on 2010-01-20
as to priority... 'extra' /is/ an officially defined priority level, so it should not be causing any problems:

[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-priority](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-priority)

according to the description of the categories, both 'optional' and 'extra' would technically be appropriate for these... but since this is a 'third-party' repository, i figure it's ok to leave it as 'extra'.

---

### Post by nanotube on 2010-01-21
nskipper1:
well, firefox 3.6 came through today, i made sure to take a look at it in synaptic first - it showed up in 'installed (upgradeable)' section, both on karmic and on intrepid.

also, i got confirmation from others over in the testing thread that the updates show up in synaptic.

so it seems that it's a problem specific to your machine/configuration, which i cannot reproduce. 

play around with it, and let me know if you discover anything interesting.

---

### Post by petitchevalroux on 2010-01-22
Big mess in my repository :
```

sudo apt-get install firefox-mozilla-build
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances
Lecture des informations d'état... Fait
Les NOUVEAUX paquets suivants seront installés*:
  firefox-mozilla-build
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/10,9Mo dans les archives.
Après cette opération, 0o d'espace disque supplémentaires seront utilisés.
Sélection du paquet firefox-mozilla-build précédemment désélectionné.
(Lecture de la base de données... 264155 fichiers et répertoires déjà installés.)
Dépaquetage de firefox-mozilla-build (à partir de .../firefox-mozilla-build_3.6-0ubuntu1_i386.deb) ...
dpkg-divert: «*diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build*» entre en conflit avec «*local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu*»
dpkg*: erreur de traitement de /var/cache/apt/archives/firefox-mozilla-build_3.6-0ubuntu1_i386.deb (--unpack)*:
 le sous-processus nouveau script pre-installation a retourné une erreur de sortie d'état 2
dpkg-divert: erreur de correspondance sur paquet
  lors de la suppression de «*diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build*»
  «*local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu*» trouvé
dpkg*: erreur lors du nettoyage*:
 le sous-processus nouveau script post-removal a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution*:
 /var/cache/apt/archives/firefox-mozilla-build_3.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Unable to get standard firefox or ubuntuzilla one ... 

If someone can help me it will be nice :D.

---

### Post by nanotube on 2010-01-22
as specified in the ubuntuzilla instructions, you have to remove the local diversion that is present from the old ubuntuzilla script install.

please run ```
ubuntuzilla.py -a remove -p firefox
```, and /then/ run ```
sudo apt-get install firefox-mozilla-build
```

---

### Post by petitchevalroux on 2010-01-25
> **nanotube said:**
> as specified in the ubuntuzilla instructions, you have to remove the local diversion that is present from the old ubuntuzilla script install.

please run ```
ubuntuzilla.py -a remove -p firefox
```, and /then/ run ```
sudo apt-get install firefox-mozilla-build
```

I was lazzy sorry :???:. Thanks a lot for your help

---

### Post by TBerk on 2010-01-25
Worked for me!

(I was really tripp'n about getting the new version into the same directories as 3.5.7 w/ the manual download I had sitting in .../documents/downloads...).


Thx for this, makes life easier.

berk

---

### Post by nanotube on 2010-01-25
> **petitchevalroux said:**
> I was lazzy sorry :???:. Thanks a lot for your help

heh no problem, glad it all worked out. :)

---

### Post by nskipper1 on 2010-01-30
> **nanotube said:**
> nskipper1:
well, firefox 3.6 came through today, i made sure to take a look at it in synaptic first - it showed up in 'installed (upgradeable)' section, both on karmic and on intrepid.

also, i got confirmation from others over in the testing thread that the updates show up in synaptic.

so it seems that it's a problem specific to your machine/configuration, which i cannot reproduce. 

play around with it, and let me know if you discover anything interesting.


Sorry, I didn't notice that your response flipped over to pg. 4 of the thread and I missed it until now.

I went ahead and upgraded Firefox 3.6 and the new Thunderbird but neither one showed up in 'installed (upgradeable)' section. I have a pretty vanilla installation of Karmic so can't imagine what the problem is. I don't seem to have the problem with any other package so I can't agree that it's solely a problem with my setup. It's a minor problem compared to the benefits of the repository and is easily worked around - more of a curiosity at this point.

I'll keep my eye on it with future releases and report anything new.

---

### Post by nanotube on 2010-01-30
> **nskipper1 said:**
> Sorry, I didn't notice that your response flipped over to pg. 4 of the thread and I missed it until now.

I went ahead and upgraded Firefox 3.6 and the new Thunderbird but neither one showed up in 'installed (upgradeable)' section. I have a pretty vanilla installation of Karmic so can't imagine what the problem is. I don't seem to have the problem with any other package so I can't agree that it's solely a problem with my setup. It's a minor problem compared to the benefits of the repository and is easily worked around - more of a curiosity at this point.

I'll keep my eye on it with future releases and report anything new.

ok, sounds good... i'll try to remember to give you a ping when the next release comes out so you can take a look. :)

---

### Post by flabdablet on 2010-02-07
Nice work, nanotube!

Having been mildly irritated by yet another Windows-centric blogger whining about being unable to download and double-click some random executable from somewhere to get a new Firefox into his Ubuntu, and concluding from his inability to do this that "Linux isn't ready for the desktop" (yawn): I just wrote [this little script]("http://flabdablet.nfshost.com/linux-scripts/install-latest-firefox-release") to give him what he said he wanted. 

It installs the Ubuntuzilla signing key and repository, trying downloads.sourceforge.net first and then dl.switch.sourceforge.net if it fails, and then apt-get installs firefox-mozilla-build.

I've used it on my Hardy desktop and my Gutsy laptop and it worked fine on both.

---

### Post by rudihawk on 2010-02-07
Thanks for the update - will definitely run this on my Karmic install and then later on my Lucid once I upgrade :)

flabdablet - thaks for the script, will try it out :)

---

### Post by nskipper1 on 2010-02-26
> **nanotube said:**
> ok, sounds good... i'll try to remember to give you a ping when the next release comes out so you can take a look. :)

nanotube:

Got the new thunderbird-mozilla-build in "Synaptic > Status > Installed (Upgradable)". I did not change anything. Did you do something different? Anyway, it's working now (at least for Tbird) - good job and thanks.

---

### Post by nanotube on 2010-02-27
> **nskipper1 said:**
> nanotube:

Got the new thunderbird-mozilla-build in "Synaptic > Status > Installed (Upgradable)". I did not change anything. Did you do something different? Anyway, it's working now (at least for Tbird) - good job and thanks.

Hi,
nope, didn't change a thing!
but hey, it works, so... good :)

---

### Post by Levis 1 on 2010-06-17
What will show up is every name you've given law enforcement, courts, or  corrections - as long as they made the connection between your old name  and your new name.  If nobody realized that John Doe was also Bill Doe,  then there would be two different records and neither name would show.

---

### Post by fzerorubigd on 2010-06-18
> **nanotube said:**
> New ubuntuzilla apt repository has been created for your convenience.

Now, instead of installing the script, then using the script to install, you can add the ubuntuzilla repository to your sources.list and use apt-get install to directly install firefox, thunderbird, and seamonkey.

For more details, see the ubuntuzilla website, in the "installation" section:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

Current users of ubuntuzilla should run "ubuntuzilla.py -a remove -p yourpackage" before installing these packages, to undo the local diversion of /usr/bin/(package) links.

Please let me know if you run into any trouble with it.

...Edited to reflect the latest info.

Its a good idea and I use this , BUT since new policy , they (sf.net) deny US (Iran and several other country) to access their files (They provide "hosting" or "owning" the files? I can't understand) :confused:
And now, we can't use this method anymore. 
Is this possible to change this to another hosting service? 

Some ppl say there is an option in project admin to change this and allow us to download files with no problem, if there is any, please do this :) (and I don't know its true or not)

Thanks a lot, and sorry if my English is not good.

---

### Post by nanotube on 2010-06-18
fzerorubigd, try again now.

---

### Post by fzerorubigd on 2010-06-19
> **nanotube said:**
> fzerorubigd, try again now.
Thanks, its ok now.

---

### Post by nanotube on 2010-06-19
> **fzerorubigd said:**
> Thanks, its ok now.

cool :)

---

### Post by jasmines on 2010-12-10
I am receiving an update message from both Firefox and Thunderbird, but nothing new can be found on Ubuntuzilla repositories. Could you update them, please?

However, how can I disable Firefox and Thunderbird integrated update checker, without disabling the extensions update checker?
Thanks a lot!

---

### Post by nanotube on 2010-12-10
> **jasmines said:**
> I am receiving an update message from both Firefox and Thunderbird, but nothing new can be found on Ubuntuzilla repositories. Could you update them, please?


just uploaded the new debs earlier today. :)

> 
However, how can I disable Firefox and Thunderbird integrated update checker, without disabling the extensions update checker?
Thanks a lot!

edit -> preferences -> advanced -> update
uncheck the 'firefox' box, leave the addons box checked. i think that should do it.

similar in thunderbird.

---

### Post by linuxball on 2011-01-04
The details of the "installation" section for Ubuntu Intrepid (8.10) or earlier (8.04 in my case) on the Ubuntuzilla website are out of date. The repository
```
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```
does not contain any of the mentioned packages (firefox-mozilla-build, thunderbird-mozilla-build, seamonkey-mozilla-build). I changed the repository to
```
deb http://ignum.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```
to get it working.

Searching the net I found [alternative instructions on Ubuntu Geek]("http://www.ubuntugeek.com/how-to-install-thunderbird-3-in-ubuntu-9-109-048-108-04.html") to install recent versions of firefox/thunderbird.

I didn't try it because my "solution" solved the problem for now. May be that this thread and the Ubuntuzilla repository became obsolete and the repository specified in the ubuntu geek instructions is the replacement for the Ubutuzilla repository?

---

### Post by nanotube on 2011-01-04
Hi linuxball

maybe the switch.dl mirror was temporarily down? i just checked and it does show all the files, as expected.

the instructions on ubuntugeek are a different beast altogether, they're for the mozilla-daily repository, with daily builds, not the releases.

---

### Post by witeshark17 on 2011-03-02
There seems to be some confusion. In IRC the thinking seems to be that it's now time to use the Software Sources from System menu to update FF. Can someone please make clear whether or not Ubuntuzilla is still in use? The command ```
ubuntuzilla.py -a install -p firefox
``` is not working

---

### Post by auh2o on 2011-03-03
Is Ubuntuzilla dead? Granted it seems the point of Ubuntuzilla is moot now that Ubuntu has apparently started updating Firefox between distro upgrades.

---

### Post by witeshark17 on 2011-03-03
> **auh2o said:**
> Is Ubuntuzilla dead? Granted it seems the point of Ubuntuzilla is moot now that Ubuntu has apparently started updating Firefox between distro upgrades. It sure seems like an internet ghost town. And now all updates from the normal repos don't really work; they show in Synaptic, but only 3.6.13 launches. How can we get the Ubuntuzilla build removed?
here's some similar info:

[http://ubuntuforums.org/archive/index.php/t-1371378.html](http://ubuntuforums.org/archive/index.php/t-1371378.html)

---

### Post by auh2o on 2011-03-06
Actually, I got the Ubuntuzilla Firefox 3.6.15 update today, so apparently it's not abandoned after all. The official Ubuntu repo is still on 3.6.14 (which has a Java problem).

---

### Post by Karlchen on 2011-03-06
Hello, auh2o. 
> Actually, I got the Ubuntuzilla Firefox 3.6.15 update today, so apparently it's not abandoned after all.You may have missed nanotube's announcement here:                                                    [Ubuntuzilla ceasing operation]("http://ubuntuforums.org/showthread.php?t=1700967").

Kind regards,
Karl

---

### Post by Karlchen on 2011-03-06
Hello, witeshark17.
> There seems to be some confusion. [...] The command ```
ubuntuzilla.py -a install -p firefox
``` is not workingThis commandline has been superseded for  more than 12 months now.
When I started getting the Mozilla builds of Firefox and Thunderbird through Ubuntuzilla about a year ago, the official instruction for doing so was this one already: [**Installation**]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation"). I.e. the Mozilla builds could/can be installed/updated with the help of Synaptic and the Update Administration after the Ubuntuzilla repository has been added to the repository list.

But beware, this repository may be no longer maintained in the near future. Please, read nanotube's announcement                                                     **[Ubuntuzilla ceasing operation]("http://ubuntuforums.org/showthread.php?t=1700967")**.

Kind regards,
Karl
--

---

### Post by witeshark17 on 2011-03-06
I tried the new installation to Software Sources; it didn't work. I'm in a FF limbo with no way yet to fix the Ubuntuzilla removal and return to normal repos as a source for FF. I'm looking for CLI commands or scripts to clean that up. :confused:

---

### Post by auh2o on 2011-03-09
> **Karlchen said:**
> Hello, auh2o. 
You may have missed nanotube's announcement here:                                                    [Ubuntuzilla ceasing operation]("http://ubuntuforums.org/showthread.php?t=1700967").
l

Well, it was posted after my last post, so indeed I had. Thanks for the heads up.

---

### Post by tom king on 2011-08-13
Ok I will update the Ubuntuzilla repos.....is it going out of biz or not?

---

### Post by tom king on 2011-08-13
how come my avatar picture I uploaded does not appear?

---

### Post by witeshark17 on 2011-08-13
> **tom king said:**
> how come my avatar picture I uploaded does not appear? I see your avatar... :popcorn:

---

