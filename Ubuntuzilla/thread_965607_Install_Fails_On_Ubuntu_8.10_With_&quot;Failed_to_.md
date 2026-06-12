---
title: "Install Fails On Ubuntu 8.10 With &quot;Failed to determine plug-in path&quot;"
date: 2008-10-31
forum: Ubuntuzilla
---

### Post by war59312 on 2008-10-31
Hi,

Well, I upgraded from Ubuntu 8.04 to Ubuntu 8.10.

Then I tried running this script and here is what I get:

```
will@will-linux:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.5.4

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.3. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. bn-IN     
  4. ca           5. cs           6. da           7. de        
  8. el           9. en-GB       10. en-US       11. es-AR     
 12. es-ES       13. eu          14. fi          15. fr        
 16. fy-NL       17. ga-IE       18. gl          19. gu-IN     
 20. he          21. hi-IN       22. hu          23. id        
 24. is          25. it          26. ja          27. ka        
 28. kn          29. ko          30. ku          31. lt        
 32. mk          33. mn          34. mr          35. nb-NO     
 36. nl          37. nn-NO       38. pa-IN       39. pl        
 40. pt-BR       41. pt-PT       42. ro          43. ru        
 44. si          45. sk          46. sl          47. sq        
 48. sr          49. sv-SE       50. te          51. th        
 52. tr          53. uk          54. zh-CN       55. zh-TW     

Enter your choice of localization (integer, from 0 to 55): 10
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
[sudo] password for will: 
Get:1 http://archive.linux.duke.edu intrepid Release.gpg [189B]
Ign http://archive.linux.duke.edu intrepid/main Translation-en_US              
Ign http://archive.linux.duke.edu intrepid/restricted Translation-en_US        
Ign http://archive.linux.duke.edu intrepid/universe Translation-en_US          
Ign http://archive.linux.duke.edu intrepid/multiverse Translation-en_US        
Get:2 http://archive.linux.duke.edu intrepid-updates Release.gpg [189B]        
Ign http://archive.linux.duke.edu intrepid-updates/main Translation-en_US      
Ign http://archive.linux.duke.edu intrepid-updates/restricted Translation-en_US
Ign http://archive.linux.duke.edu intrepid-updates/universe Translation-en_US  
Ign http://archive.linux.duke.edu intrepid-updates/multiverse Translation-en_US
Get:3 http://archive.linux.duke.edu intrepid-security Release.gpg [189B]       
Ign http://archive.linux.duke.edu intrepid-security/main Translation-en_US     
Ign http://archive.linux.duke.edu intrepid-security/restricted Translation-en_US
Ign http://archive.linux.duke.edu intrepid-security/universe Translation-en_US 
Ign http://archive.linux.duke.edu intrepid-security/multiverse Translation-en_US
Get:4 http://archive.linux.duke.edu intrepid Release [65.9kB]                  
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Get:5 http://archive.linux.duke.edu intrepid-updates Release [44.0kB]       
Hit http://archive.canonical.com intrepid Release.gpg                
Ign http://archive.canonical.com intrepid/partner Translation-en_US  
Get:6 http://archive.linux.duke.edu intrepid-security Release [44.0kB]         
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Get:7 http://archive.linux.duke.edu intrepid/main Packages [1256kB]            
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Get:8 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Hit http://archive.canonical.com intrepid Release                              
Get:9 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://packages.medibuntu.org intrepid/free Translation-en_US             
Ign http://ppa.launchpad.net intrepid/main Packages                           
Ign http://ppa.launchpad.net intrepid/main Sources                             
Hit http://archive.canonical.com intrepid/partner Sources                      
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Sources                             
Hit http://ppa.launchpad.net intrepid/main Packages                            
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Hit http://ppa.launchpad.net intrepid/main Sources      
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Sources                             
Get:10 http://archive.linux.duke.edu intrepid/restricted Packages [8408B]      
Get:11 http://archive.linux.duke.edu intrepid/main Sources [505kB]
Get:12 http://archive.linux.duke.edu intrepid/restricted Sources [3113B]       
Get:13 http://archive.linux.duke.edu intrepid/universe Packages [4542kB]
Hit http://packages.medibuntu.org intrepid Release                            
Get:14 http://packages.medibuntu.org intrepid/free Packages [3518B]
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Hit http://packages.medibuntu.org intrepid/free Sources                        
Hit http://packages.medibuntu.org intrepid/non-free Sources
Get:15 http://archive.linux.duke.edu intrepid/universe Sources [1981kB]        
Get:16 http://archive.linux.duke.edu intrepid/multiverse Packages [199kB]      
Get:17 http://archive.linux.duke.edu intrepid/multiverse Sources [95.8kB]      
Get:18 http://archive.linux.duke.edu intrepid-updates/main Packages [723B]     
Get:19 http://archive.linux.duke.edu intrepid-updates/restricted Packages [14B]
Get:20 http://archive.linux.duke.edu intrepid-updates/main Sources [488B]      
Get:21 http://archive.linux.duke.edu intrepid-updates/restricted Sources [14B] 
Get:22 http://archive.linux.duke.edu intrepid-updates/universe Packages [14B]  
Get:23 http://archive.linux.duke.edu intrepid-updates/universe Sources [14B]   
Get:24 http://archive.linux.duke.edu intrepid-updates/multiverse Packages [14B]
Get:25 http://archive.linux.duke.edu intrepid-updates/multiverse Sources [14B] 
Get:26 http://archive.linux.duke.edu intrepid-security/main Packages [723B]    
Get:27 http://archive.linux.duke.edu intrepid-security/restricted Packages [14B]
Get:28 http://archive.linux.duke.edu intrepid-security/main Sources [488B]     
Get:29 http://archive.linux.duke.edu intrepid-security/restricted Sources [14B]
Get:30 http://archive.linux.duke.edu intrepid-security/universe Packages [14B] 
Get:31 http://archive.linux.duke.edu intrepid-security/universe Sources [14B]  
Get:32 http://archive.linux.duke.edu intrepid-security/multiverse Packages [14B]
Get:33 http://archive.linux.duke.edu intrepid-security/multiverse Sources [14B]
Fetched 8751kB in 11s (779kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  blubuntu-gdm-theme tango-icon-theme blubuntu-wallpapers
  blubuntu-session-splashes
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.3.tar.bz2

Downloading Firefox archive from the Mozilla site

--2008-10-31 17:30:53--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.3/linux-i686/en-US/firefox-3.0.3.tar.bz2
           => `firefox-3.0.3.tar.bz2'
Resolving releases.mozilla.org... 204.246.0.136, 202.177.202.154, 204.152.184.196, ...
Connecting to releases.mozilla.org|204.246.0.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.3/linux-i686/en-US ... done.
==> SIZE firefox-3.0.3.tar.bz2 ... 9088358
==> PASV ... done.    ==> RETR firefox-3.0.3.tar.bz2 ... done.
Length: 9088358 (8.7M)

100%[======================================>] 9,088,358    839K/s   in 11s     

2008-10-31 17:31:05 (818 KB/s) - `firefox-3.0.3.tar.bz2' saved [9088358]


Downloading Firefox signature from the Mozilla site

--2008-10-31 17:31:05--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.3/linux-i686/en-US/firefox-3.0.3.tar.bz2.asc
           => `firefox-3.0.3.tar.bz2.asc'
Resolving releases.mozilla.org... 204.152.184.113, 204.246.0.136, 202.177.202.154, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... failed: Connection refused.
Connecting to releases.mozilla.org|204.246.0.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.3/linux-i686/en-US ... done.
==> SIZE firefox-3.0.3.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.3.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.009s  

2008-10-31 17:31:06 (19.8 KB/s) - `firefox-3.0.3.tar.bz2.asc' saved [186]

tru::1:1211018108:0:3:1:5
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

gpg: Signature made Fri 26 Sep 2008 03:37:53 AM EDT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
sudo dpkg -L firefox |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'
Failed to determine plugin path. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1106, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 546, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 714, in linkPlugins
    self.pluginPath = self.util.getSystemOutput(executionstring="sudo dpkg -L " + self.aptPackage + " |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'", errormessage="Failed to determine plugin path. Exiting.")
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/

```

Simple enough to fix..

```
gksudo gedit /usr/local/bin/ubuntuzilla.py
```

Replace Line 711 with: 

```
if re.search('8\.04||8\.10', issue) != None:
```

Take Care,

Will

---

### Post by nanotube on 2008-11-01
Hi,
Thanks for the post!
I have made an updated release (v 4.5.5) fixing this issue.
See project site for downloads.

---

