---
title: "can't install firefox: file system error???"
date: 2009-10-02
forum: Ubuntuzilla
---

### Post by tw11 on 2009-10-02
When I try to install firefox using ubuntuzilla.py -a install -p firefox, I get relating to my file system and I'm not exactly sure how to interpret it or solve it. I'm using 8.10

```
horatiu@rawr:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.7.4

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.3. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
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

Hit http://mirror.anl.gov intrepid Release.gpg
Ign http://mirror.anl.gov intrepid/main Translation-en_US
Ign http://mirror.anl.gov intrepid/restricted Translation-en_US
Ign http://mirror.anl.gov intrepid/universe Translation-en_US
Ign http://mirror.anl.gov intrepid/multiverse Translation-en_US
Hit http://mirror.anl.gov intrepid-updates Release.gpg
Ign http://mirror.anl.gov intrepid-updates/main Translation-en_US
Ign http://mirror.anl.gov intrepid-updates/restricted Translation-en_US
Ign http://mirror.anl.gov intrepid-updates/universe Translation-en_US
Ign http://mirror.anl.gov intrepid-updates/multiverse Translation-en_US
Hit http://mirror.anl.gov intrepid-security Release.gpg
Ign http://mirror.anl.gov intrepid-security/main Translation-en_US
Ign http://mirror.anl.gov intrepid-security/restricted Translation-en_US
Ign http://mirror.anl.gov intrepid-security/universe Translation-en_US
Ign http://mirror.anl.gov intrepid-security/multiverse Translation-en_US
Hit http://mirror.anl.gov intrepid Release
Hit http://mirror.anl.gov intrepid-updates Release
Hit http://mirror.anl.gov intrepid-security Release
Hit http://mirror.anl.gov intrepid/main Packages
Hit http://mirror.anl.gov intrepid/restricted Packages
Hit http://mirror.anl.gov intrepid/main Sources
Hit http://mirror.anl.gov intrepid/restricted Sources
Hit http://mirror.anl.gov intrepid/universe Packages
Hit http://mirror.anl.gov intrepid/universe Sources
Hit http://mirror.anl.gov intrepid/multiverse Packages
Hit http://mirror.anl.gov intrepid/multiverse Sources
Hit http://mirror.anl.gov intrepid-updates/main Packages
Hit http://mirror.anl.gov intrepid-updates/restricted Packages
Hit http://mirror.anl.gov intrepid-updates/main Sources
Hit http://mirror.anl.gov intrepid-updates/restricted Sources
Hit http://mirror.anl.gov intrepid-updates/universe Packages
Hit http://mirror.anl.gov intrepid-updates/universe Sources
Hit http://mirror.anl.gov intrepid-updates/multiverse Packages
Hit http://mirror.anl.gov intrepid-updates/multiverse Sources
Hit http://mirror.anl.gov intrepid-security/main Packages
Hit http://mirror.anl.gov intrepid-security/restricted Packages
Hit http://mirror.anl.gov intrepid-security/main Sources
Hit http://mirror.anl.gov intrepid-security/restricted Sources
Hit http://mirror.anl.gov intrepid-security/universe Packages
Hit http://mirror.anl.gov intrepid-security/universe Sources
Hit http://mirror.anl.gov intrepid-security/multiverse Packages
Hit http://mirror.anl.gov intrepid-security/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 744, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 905, in backupProfile
    self.checkDiskSpaceForBackup("~/.mozilla")
  File "/usr/local/bin/ubuntuzilla.py", line 522, in checkDiskSpaceForBackup
    availableForBackup = int(self.util.getSystemOutput(executionstring="df -k "+target+" | grep '[0-9]%' | awk '{ NN = NF - 2; print $NN }'"))
ValueError: invalid literal for int() with base 10: 'df: Warning: cannot read table of mounted file systems: Stale NFS file handle'

```

any help?

---

### Post by sisco311 on 2009-10-02
what's the output of:
```
df -h
```

---

### Post by tw11 on 2009-10-02
actually nvm, i got it to work somehow. i'm still not sure what was wrong but after i installed flash player and java, it magically worked. i dont know if they're related

---

### Post by nanotube on 2009-10-02
huh weird...

---

