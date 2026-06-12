---
title: "ubuntuzilla has problems"
date: 2009-12-03
forum: Ubuntuzilla
---

### Post by jlh68 on 2009-12-03
*I get the following message:*   File "/usr/local/bin/ubuntuzilla.py", line 147, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

*I am told to get help on this site. So please help me.*

---

### Post by nanotube on 2009-12-04
Hi
could you please post the complete output of your ubuntuzilla session?
with just the info you have provided, i can't tell where exactly the error is occurring...

---

### Post by ChaosData on 2009-12-04
hi, i also got this type of message just now. Found this post, thought I'd at least submit my problem on this one.
---
i am running karmic x86_64. i just installed linux after I put this computer together. Everything else works fine with it, no driver issues whatsoever. I used the repo method for installing ubuntuzilla.

```
CD@CD-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.8.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.5.

Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install a different release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
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

Hit http://switch.dl.sourceforge.net all Release.gpg
Ign http://switch.dl.sourceforge.net all/main Translation-en_US
Hit http://switch.dl.sourceforge.net all Release
Ign http://switch.dl.sourceforge.net all/main Packages
Ign http://switch.dl.sourceforge.net all/main Packages
Hit http://switch.dl.sourceforge.net all/main Packages
Hit http://mirror.cc.columbia.edu karmic Release.gpg
Ign http://mirror.cc.columbia.edu karmic/main Translation-en_US
Ign http://mirror.cc.columbia.edu karmic/restricted Translation-en_US
Ign http://mirror.cc.columbia.edu karmic/universe Translation-en_US
Ign http://mirror.cc.columbia.edu karmic/multiverse Translation-en_US
Hit http://mirror.cc.columbia.edu karmic-updates Release.gpg
Ign http://mirror.cc.columbia.edu karmic-updates/main Translation-en_US
Ign http://mirror.cc.columbia.edu karmic-updates/restricted Translation-en_US
Ign http://mirror.cc.columbia.edu karmic-updates/universe Translation-en_US
Ign http://mirror.cc.columbia.edu karmic-updates/multiverse Translation-en_US
Hit http://mirror.cc.columbia.edu karmic-security Release.gpg
Ign http://mirror.cc.columbia.edu karmic-security/main Translation-en_US
Ign http://mirror.cc.columbia.edu karmic-security/restricted Translation-en_US
Ign http://mirror.cc.columbia.edu karmic-security/universe Translation-en_US
Ign http://mirror.cc.columbia.edu karmic-security/multiverse Translation-en_US
Hit http://mirror.cc.columbia.edu karmic Release
Hit http://mirror.cc.columbia.edu karmic-updates Release
Hit http://mirror.cc.columbia.edu karmic-security Release
Hit http://mirror.cc.columbia.edu karmic/main Packages
Hit http://mirror.cc.columbia.edu karmic/restricted Packages
Hit http://mirror.cc.columbia.edu karmic/main Sources
Hit http://mirror.cc.columbia.edu karmic/restricted Sources
Hit http://mirror.cc.columbia.edu karmic/universe Packages
Hit http://mirror.cc.columbia.edu karmic/universe Sources
Hit http://mirror.cc.columbia.edu karmic/multiverse Packages
Hit http://mirror.cc.columbia.edu karmic/multiverse Sources
Hit http://mirror.cc.columbia.edu karmic-updates/main Packages
Hit http://mirror.cc.columbia.edu karmic-updates/restricted Packages
Hit http://mirror.cc.columbia.edu karmic-updates/main Sources
Hit http://mirror.cc.columbia.edu karmic-updates/restricted Sources
Hit http://mirror.cc.columbia.edu karmic-updates/universe Packages
Hit http://mirror.cc.columbia.edu karmic-updates/universe Sources
Hit http://mirror.cc.columbia.edu karmic-updates/multiverse Packages
Hit http://mirror.cc.columbia.edu karmic-updates/multiverse Sources
Hit http://mirror.cc.columbia.edu karmic-security/main Packages
Hit http://mirror.cc.columbia.edu karmic-security/restricted Packages
Hit http://mirror.cc.columbia.edu karmic-security/main Sources
Hit http://mirror.cc.columbia.edu karmic-security/restricted Sources
Hit http://mirror.cc.columbia.edu karmic-security/universe Packages
Hit http://mirror.cc.columbia.edu karmic-security/universe Sources
Hit http://mirror.cc.columbia.edu karmic-security/multiverse Packages
Hit http://mirror.cc.columbia.edu karmic-security/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.5.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-12-04 01:03:49--  ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2
           => `firefox-3.5.5.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US ... done.
==> SIZE firefox-3.5.5.tar.bz2 ... 9924119
==> PASV ... done.    ==> REST 9924119 ... done.    
==> RETR firefox-3.5.5.tar.bz2 ... done.
Length: 9924119 (9.5M), 0 (0) remaining

100%[+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 9,924,119   --.-K/s   in 0s      

2009-12-04 01:03:50 (0.00 B/s) - `firefox-3.5.5.tar.bz2' saved [9924119]


Downloading Firefox signature from the Mozilla site

--2009-12-04 01:03:50--  ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US/firefox-3.5.5.tar.bz2.asc
           => `firefox-3.5.5.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.5/linux-i686/en-US ... done.
==> SIZE firefox-3.5.5.tar.bz2.asc ... 194
==> PASV ... done.    ==> REST 194 ... done.    
==> RETR firefox-3.5.5.tar.bz2.asc ... done.
Length: 194, 0 remaining

100%[+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 194         --.-K/s   in 0s      

2009-12-04 01:03:52 (0.00 B/s) - `firefox-3.5.5.tar.bz2.asc' saved [194]

tru::1:1259906493:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1259906493:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2011-07-20::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2011-07-20:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2011-07-20:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Mon 02 Nov 2009 10:51:42 PM EST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8

Extracting archive


bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: Broken pipe
    Input file = (stdin), output file = (stdout)
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
sudo tar -C /opt -xjf firefox-3.5.5.tar.bz2
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1319, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 304, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 347, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 767, in install
    self.extractArchive()
  File "/usr/local/bin/ubuntuzilla.py", line 643, in extractArchive
    self.util.execSystemCommand(executionstring="sudo tar -C " + self.options.targetdir + " " + self.tar_flags + " " + self.packageFilename)
  File "/usr/local/bin/ubuntuzilla.py", line 147, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/

```

---

### Post by nanotube on 2009-12-04
well seems like something's wrong with your bzip2...

could you download the firefox tar.bz2 manually, and try extracting it manually with the command: 
```

sudo tar -C /opt -xjf firefox-3.5.5.tar.bz2

```

and see if that gives you any trouble?

since the file gpg sig verified, we know the file's ok... maybe you have no space on your partition which contains /opt?

---

### Post by jlh68 on 2009-12-06
Here is the output from my terminal when trying to do a ubuntuzilla.py.
> john@Eagle:~$ ubuntuzilla.py

Welcome to the Ubuntuzilla Firefox script version 4.8.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.5.

Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install a different release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
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

[sudo] password for john: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release.gpg                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release [57.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [211kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2604B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [620B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [58.7kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [24.9kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [90.8kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages [123kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages [2604B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources [620B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources [32.0kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Sources [588B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources [15.2kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages [62.8kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages [1662B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Fetched 754kB in 3s (199kB/s)                  
Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  python-pycurl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9 (1.9.0.15+nobinonly-0ubuntu0.9.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.postinst: 5: /usr/bin/xulrunner-1.9: not found
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.15+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                               No apport report written because the error message indicates its a followup error from a previous failure.
                    No apport report written because MaxReports is reached already
                                                                                  No apport report written because MaxReports is reached already
                                                                                                                                                unner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.15+nobinonly-0ubuntu0.9.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
sudo apt-get install firefox
Package installation failed. Cannot proceed.
Process returned code 100
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1319, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 304, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 347, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 758, in install
    self.aptgetMeasures()
  File "/usr/local/bin/ubuntuzilla.py", line 528, in aptgetMeasures
    self.util.execSystemCommand(executionstring="sudo apt-get install " + self.aptPackage, errormessage="Package installation failed. Cannot proceed.")
  File "/usr/local/bin/ubuntuzilla.py", line 147, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
john@Eagle:~$

---

### Post by jlh68 on 2009-12-06
I also get this when using the Update Manager:
> exit status 127
E: firefox-3.0: dependency problems - leaving unconfigured
E: firefox-3.0-branding: dependency problems - leaving unconfigured
E: firefox: dependency problems - leaving unconfigured
E: xulrunner-1.9-gnome-support: dependency problems - leaving unconfigured

So it appears that there is a big Firefox problem when upgrading.

---

### Post by nanotube on 2009-12-07
> **jlh68 said:**
> I also get this when using the Update Manager:


So it appears that there is a big Firefox problem when upgrading.

It appears there's something wrong with either your packages or your repositories. (note also the warning message about duplicate entries in your sources.list).

so... fix up your repos (maybe remove the duplicate entries from your sources.list), try fixing up the package dependencies by running:
```
sudo apt-get install -f
```

and see what happens.

---

### Post by nanotube on 2009-12-07
> **ChaosData said:**
> hi, i also got this type of message just now. Found this post, thought I'd at least submit my problem on this one.
---
i am running karmic x86_64. i just installed linux after I put this computer together. Everything else works fine with it, no driver issues whatsoever. I used the repo method for installing ubuntuzilla.

```

bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: Broken pipe
    Input file = (stdin), output file = (stdout)
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
sudo tar -C /opt -xjf firefox-3.5.5.tar.bz2
Previous command has failed to complete successfully. Exiting.

```

Hi
well, i just got a patch for this specific problem (the broken pipe bit) on the tracker, seems that it's due to an implementation flaw in python's subprocess module. right now the latest code is in the git repository - if you can, please give it a whirl.  but i'll push out a release soon-ish which you can also test.

---

### Post by jlh68 on 2009-12-07
I ran apr-get install -f and this is the result

> john@Eagle:~$ sudo apt-get install -f
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9 (1.9.0.15+nobinonly-0ubuntu0.9.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.postinst: 5: /usr/bin/xulrunner-1.9: not found
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.15+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-brandingNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                             is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-dev:
 xulrunner-1.9-dev depends on xulrunner-1.9 (>= 1.9.0.15+nobinonly); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.15+nobinonly-0ubuntu0.9.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-dev
 xulrunner-1.9-gnome-support
E: Sub-process /

---

### Post by jlh68 on 2009-12-07
To insatll Firefox 3.5.x do I need these?

xulrunner-1.9
firefox-3.0
firefox-3.0-branding
firefox
xulrunner-1.9-dev
xulrunner-1.9-gnome-support

---

### Post by nanotube on 2009-12-07
jlh68:

well, it looks like you xulrunner-1.9 is somehow hosed.

strictly speaking, you don't really need ff3.0 and xulrunner if you're planning on running ff3.5, but as part of the install ubuntuzilla makes sure that your ff3.0 is installed, just so you have a failover in case the ubuntuzilla-installed version goes weird.

so, you have ... three choices. :)

choice 1: fix the xulrunner package. read this forum thread for a howto fix a messed up package:
[http://ubuntuforums.org/showthread.php?t=1188517](http://ubuntuforums.org/showthread.php?t=1188517)
then use ubuntuzilla again.

choice 2: use the somewhat more manual method of installing the ubuntu build of firefox, which will not try to install firefox from the repos if it's already installed. here's the link to that install method:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

choice 3: modify ubuntuzilla.py and comment out the apt-get install firefox bit (around line 535 in the file), then run ubuntuzilla install again.

i'd probably recommend trying to fix your xulrunner package, regardless of what you decide to do, since it's not good to have a borked up package on your system.

---

