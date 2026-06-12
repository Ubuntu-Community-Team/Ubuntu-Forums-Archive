---
title: "[Ubuntuzilla] Failed to retrieve Mozilla Software Releases Public key"
date: 2009-07-10
forum: Ubuntuzilla
---

### Post by irshad86 on 2009-07-10
Hi!

I'm trying to install firefox 3.5 and I'm getting this error:

$ sudo ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. as           3. be        
  4. bg           5. bn-BD        6. bn-IN        7. ca        
  8. cs           9. cy          10. da          11. de        
 12. el          13. en-GB       14. en-US       15. eo        
 16. es-AR       17. es-CL       18. es-ES       19. es-MX     
 20. et          21. eu          22. fa          23. fi        
 24. fr          25. fy-NL       26. ga-IE       27. gl        
 28. gu-IN       29. he          30. hi-IN       31. hr        
 32. hu          33. id          34. is          35. it        
 36. ja          37. ka          38. kk          39. kn        
 40. ko          41. ku          42. lt          43. lv        
 44. ml          45. mn          46. mr          47. nb-NO     
 48. nl          49. nn-NO       50. oc          51. or        
 52. pa-IN       53. pl          54. pt-BR       55. pt-PT     
 56. rm          57. ro          58. ru          59. si        
 60. sk          61. sl          62. sq          63. sv-SE     
 64. ta-LK       65. ta          66. te          67. th        
 68. tr          69. uk          70. vi          71. zh-CN     
 72. zh-TW     
Enter your choice of localization (integer, from 0 to 72): 14
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://www.linuxacessivel.org](http://www.linuxacessivel.org) jaunty/ Release.gpg
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports Release.gpg
Ign [http://www.linuxacessivel.org](http://www.linuxacessivel.org) jaunty/ Translation-en_US                    
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/main Translation-en_US       
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/universe Translation-en_US   
Ign [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US 
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty Release
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/universe Sources                       
Ign [http://www.linuxacessivel.org](http://www.linuxacessivel.org) jaunty/ Release                              
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty/multiverse Sources 
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/multiverse Packages          
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/main Sources                 
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/restricted Sources           
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/universe Sources             
Hit [http://mz.archive.ubuntu.com](http://mz.archive.ubuntu.com) jaunty-backports/multiverse Sources           
Ign [http://www.linuxacessivel.org](http://www.linuxacessivel.org) jaunty/ Packages                             
Hit [http://www.linuxacessivel.org](http://www.linuxacessivel.org) jaunty/ Packages
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-07-10 21:30:40--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2)
           => `firefox-3.5.tar.bz2'
Resolving releases.mozilla.org... 131.188.12.212, 216.165.129.141, 204.152.184.196, ...
Connecting to releases.mozilla.org|131.188.12.212|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US ... done.
==> SIZE firefox-3.5.tar.bz2 ... 9908255
==> PASV ... done.    ==> REST 9908255 ... done.    
==> RETR firefox-3.5.tar.bz2 ... done.
Length: 9908255 (9.4M), 0 (0) remaining

100%[+++++++++++++++++++++++++++++++++++++++] 9,908,255   --.-K/s   in 0s      

2009-07-10 21:30:44 (0.00 B/s) - `firefox-3.5.tar.bz2' saved [9908255]


Downloading Firefox signature from the Mozilla site

--2009-07-10 21:30:44--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2.asc)
           => `firefox-3.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US ... done.
==> SIZE firefox-3.5.tar.bz2.asc ... 194
==> PASV ... done.    ==> REST 194 ... done.    
==> RETR firefox-3.5.tar.bz2.asc ... done.
Length: 194, 0 remaining

100%[+++++++++++++++++++++++++++++++++++++++] 194         --.-K/s   in 0s      

2009-07-10 21:30:49 (0.00 B/s) - `firefox-3.5.tar.bz2.asc' saved [194]

gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
tru::1:1247251171:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgp.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver wwwkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgp.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver wwwkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgp.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver wwwkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgp.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver wwwkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver pgp.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver wwwkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.

---

### Post by drs305 on 2009-07-10
That's quite a list!

Here are two things that stand out:
> gpg: WARNING: unsafe ownership on configuration file `/home/irshad/.gnupg/gpg.conf'

Normally the "unsafe ownership" message means the permissions are set incorrectly, usually with write permissions for others or something of that nature. Run this to change the properities:
```

sudo chown -R irshad $HOME/.gnupg  # Makes sure you own the file
chmod 750 -R $HOME/.gnupg

```

Then to import the public key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 812347DD
```

You may still have problems with the repositories but this should help clear up the public key issues.

---

### Post by irshad86 on 2009-07-11
Hi drs305,

About:
```
unsafe ownership on configuration file
```

I already did the commands you gave.
The file owner was root. And I changed to irshad, thats why it is giving that warning.

I ran the command to import the public key and the output:
```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 812347DD
gpg: requesting key 812347DD from hkp server keyserver.ubuntu.com
gpg: key 812347DD: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

Than I ran the ubuntuzilla again but still giving all that errors I listed.

---

### Post by drs305 on 2009-07-11
Are you still getting this error, followed by all the rest as it tries to download each package?
> 
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2


Try running this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0E3606D9 812347DD

```

---

### Post by Fintan on 2009-07-12
I am getting the same on  Kubuntu KK. JJ works fine.

---

### Post by Michael%S on 2009-07-12
I had the exact same problem, and none of the solutions helped. Since I already had the keys from using the apt-key command suggested here, I figure the problem is that the script is failing to get something that I already have, and I rand the script with the -g argument to make it skip that step. Worked like a charm. :)
```
sudo ubuntuzilla.py -g
```
Good luck!

---

### Post by pjalegria on 2009-07-17
Same problem:(

---

### Post by Fintan on 2009-07-17
```
sudo ubuntuzilla.py -g
```

Worked for me. Thank you :)

---

### Post by jlh68 on 2009-07-23
I am also having the same problem.  I was able to get it to work on my laptop a few days after 3.5 was released.  On my PC I get the same problem as a previous poster identified.  I wonder if the upgrade from 3.5 to 3.5.1 has caused the problem with script?

---

### Post by jlh68 on 2009-07-23
OK I used the code in **Fintan's** post *"sudo ubuntuzilla.py -g"* which worked for me.

---

### Post by Guilden_NL on 2009-08-02
All of my other Ubuntu systems upgraded like a flash, but for some reason, my main system didn't, so I had to use Ubuntuzilla and that didn't work either until I added Michael%S' suggestion of adding the -g switch, then I got success!

Thanks Michael%S, I think it would have taken me a day away to come up with that.  Just what I needed!

---

### Post by pjalegria on 2009-08-03
what about fonts... they look very ugly

---

### Post by nanotube on 2009-08-03
> **pjalegria said:**
> what about fonts... they look very ugly

known issue: [http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

---

