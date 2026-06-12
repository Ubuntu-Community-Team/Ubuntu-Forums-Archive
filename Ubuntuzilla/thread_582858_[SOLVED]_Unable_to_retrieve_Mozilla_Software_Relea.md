---
title: "[SOLVED] Unable to retrieve Mozilla Software Releases Public key"
date: 2007-10-20
forum: Ubuntuzilla
---

### Post by tonyc2001 on 2007-10-20
I'm having problems using the script to install the latest firsfox. It exits with the message: 
"Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later."

My connection is fine. Hopefully this is something simple....

[UPDATE: same happens with thunderbird update. starting to think it's me...]

I've attached the o/p as requested:

> tony@phoenix:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.4.3

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 2.0.0.8. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. bg        
  4. ca           5. cs           6. da           7. de        
  8. el           9. en-GB       10. en-US       11. es-AR     
 12. es-ES       13. eu          14. fi          15. fr        
 16. fy-NL       17. ga-IE       18. gu-IN       19. he        
 20. hu          21. it          22. ja          23. ka        
 24. ko          25. ku          26. lt          27. mk        
 28. mn          29. nb-NO       30. nl          31. nn-NO     
 32. pa-IN       33. pl          34. pt-BR       35. pt-PT     
 36. ro          37. ru          38. sk          39. sl        
 40. sv-SE       41. tr          42. zh-CN       43. zh-TW     

Enter your choice of localization (integer, from 0 to 43): 9
You have chosen localization en-GB. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_AU                                   
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg                                                   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_AU                             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_AU                         
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_AU                                    
Ign [http://download.skype.com](http://download.skype.com) stable Release                                                      
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_AU                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_AU                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_AU                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_AU                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_AU                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_AU                           
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                                              
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]                                     
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                                             
Ign [http://www.symfony-project.com](http://www.symfony-project.com) debian/ Release.gpg                                            
Ign [http://www.symfony-project.com](http://www.symfony-project.com) debian/ Translation-en_AU                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages                                  
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                                             
Ign [http://www.symfony-project.com](http://www.symfony-project.com) debian/ Release                                                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_AU                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_AU                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources                                 
Ign [http://www.symfony-project.com](http://www.symfony-project.com) debian/ Packages                                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                                                  
Hit [http://www.symfony-project.com](http://www.symfony-project.com) debian/ Packages                                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty Release.gpg [191B]                                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/multiverse Sources
Fetched 192B in 31s (6B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences


Downloading Firefox archive from the Mozilla site

--19:15:04--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-GB/firefox-2.0.0.8.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-GB/firefox-2.0.0.8.tar.gz)
           => `firefox-2.0.0.8.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 207.200.66.54, 156.56.247.196, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-GB ... done.
==> SIZE firefox-2.0.0.8.tar.gz ... done.
==> PASV ... done.    ==> REST 9441662 ... done.    
==> RETR firefox-2.0.0.8.tar.gz ... done.
Length: 9,441,662 (9.0M), 0 (0) remaining

100%[++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 9,441,662     --.--K/s             

19:15:09 (0.00 B/s) - `firefox-2.0.0.8.tar.gz' saved [9441662]


Downloading Firefox signature from the Mozilla site

--19:15:09--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-GB/firefox-2.0.0.8.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-GB/firefox-2.0.0.8.tar.gz.asc)
           => `firefox-2.0.0.8.tar.gz.asc'
Resolving releases.mozilla.org... 204.152.184.113, 207.200.66.54, 156.56.247.196, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.8/linux-i686/en-GB ... done.
==> SIZE firefox-2.0.0.8.tar.gz.asc ... done.
==> PASV ... done.    ==> REST 186 ... done.    
==> RETR firefox-2.0.0.8.tar.gz.asc ... done.
Length: 186, 0 remaining

100%[++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 186           --.--K/s             

19:15:24 (0.00 B/s) - `firefox-2.0.0.8.tar.gz.asc' saved [186]

tru::1:1180265187:0:3:1:5
gpg: can't open `/home/tony/.gnupg/pubring.gpg'
gpg: keydb_search failed: file open error
gpg: error reading key: file open error
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: can't open `/home/tony/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: requesting key 812347DD from hkp server pgpkeys.mit.edu
gpg: can't open `/home/tony/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...

[many repeats snipped]

Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.


---

### Post by nanotube on 2007-10-20
maybe a permissions problem.?.. what's the output of:
```
ls -al /home/tony/.gnupg
```

---

### Post by tonyc2001 on 2007-10-20
D'oh... that was it. one of the .gpg files was root access only. Changed to match the others and reran. All ok now. 

Thanks for the heads up!

---

### Post by nanotube on 2007-10-21
> **tonyc2001 said:**
> D'oh... that was it. one of the .gpg files was root access only. Changed to match the others and reran. All ok now. 

Thanks for the heads up!

great! :)

---

### Post by sfraser on 2007-10-21
I had a similar problem - fresh install of Kubuntu 7.10. First thing I did was go get ununtuzilla, install, and run this:

> ubuntuzilla.py -a install -p firefox

Right away I was getting those gpg errors. First I tried this:

> sudo chown sfraser.sfraser .gnupg/

However then I started getting errors like this:

> gpg: can't access `/home/sfraser/.gnupg/trustdb.gpg': Permission denied
gpg: fatal: can't init trustdb: trust database error


So then I made the chown recursive to make sure I got all the files in the .gpg dir:

> sudo chown -R sfraser.sfraser .gnupg/ 

And that did the trick.

I am going to guess that ubuntizilla is running as root, and if it is the first process to try and initialize gpg for the user, the files end up being owned by root. I know absolutely nothing about gpg or ubuntizilla though, so as I said that is just a guess.

The recursive chown back to my user account did the trick, and I was able to install firefox with ubuntizilla.

Hope this helps,

-Scott

---

### Post by nanotube on 2007-10-22
thanks for the notes!

no, ubuntuzilla does not run gpg as root, so i'm guessing that this problem must be coming from the default install of 7.10...

---

### Post by KongKNoob on 2007-10-29
Thanks, ppl! :KS

---

### Post by Kohhal on 2007-11-16
Thanks for the help, I had the same issues on a default installation of GG 7.10 and changing the permissions as described by sfraser did the trick

sudo chown -R username.username .gnupg/

---

### Post by sonicdread on 2008-01-16
Hi there,

I have exactly the same problem on Ununtu Dapper but it doesn't seem to be the permissions on the .gnupg directory. Here's the output of ls -la .gnupg/

```

sonicdread@sonicdreaddev:~$ ls -la .gnupg/
total 24
drwx------  2 sonicdread sonicdread 4096 2008-01-16 16:27 .
drwxr-xr-x 67 sonicdread sonicdread 4096 2008-01-16 16:27 ..
-rw-------  1 sonicdread sonicdread 8084 2007-01-09 14:16 gpg.conf
-rw-r--r--  1 sonicdread sonicdread    0 2007-11-13 16:49 .#lk0x8124710.sonicdreaddev.6241
-rw-r--r--  1 sonicdread sonicdread    0 2007-11-13 16:49 .#lk0x8126920.sonicdreaddev.6245
-rw-------  1 sonicdread sonicdread 1185 2007-05-24 15:27 pubring.gpg
-rw-------  1 sonicdread sonicdread    0 2007-01-09 14:16 pubring.gpg~
-rw-------  1 sonicdread sonicdread    0 2007-05-24 15:27 secring.gpg
-rw-------  1 sonicdread sonicdread 1200 2007-05-24 15:27 trustdb.gpg
sonicdread@sonicdreaddev:~$

```


Here's the output from the ubuntuzilla install command:

```

Welcome to the Ubuntuzilla Firefox script version 4.4.5

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 2.0.0.11. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. bg
  4. ca           5. cs           6. da           7. de
  8. el           9. en-GB       10. en-US       11. es-AR
 12. es-ES       13. eu          14. fi          15. fr
 16. fy-NL       17. ga-IE       18. gu-IN       19. he
 20. hu          21. it          22. ja          23. ka
 24. ko          25. ku          26. lt          27. mk
 28. mn          29. nb-NO       30. nl          31. nn-NO
 32. pa-IN       33. pl          34. pt-BR       35. pt-PT
 36. ro          37. ru          38. sk          39. sl
 40. sv-SE       41. tr          42. uk          43. zh-CN
 44. zh-TW
Enter your choice of localization (integer, from 0 to 44): 9
You have chosen localization en-GB. Is that correct [y/n]?
Please enter 'y' or 'n': y
Password:
Get:1 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://archive.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://blognux.free.fr unstable Release.gpg
Ign http://medibuntu.sos-sts.com dapper Release.gpg
Get:4 http://ie.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://ie.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:6 http://archive.canonical.com dapper-commercial Release [5999B]
Get:7 http://ie.archive.ubuntu.com dapper-backports Release.gpg [191B]
Ign http://medibuntu.sos-sts.com dapper Release
Hit http://ie.archive.ubuntu.com dapper Release
Get:8 http://ie.archive.ubuntu.com dapper-updates Release [50.9kB]
Ign http://medibuntu.sos-sts.com dapper/free Packages
Hit http://ie.archive.ubuntu.com dapper-backports Release
Ign http://medibuntu.sos-sts.com dapper/non-free Packages
Ign http://medibuntu.sos-sts.com dapper/free Sources
Get:9 http://apt.mackers.com unstable Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-security/main Packages
Ign http://medibuntu.sos-sts.com dapper/non-free Sources
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Err http://medibuntu.sos-sts.com dapper/free Packages
  302 Found
Err http://medibuntu.sos-sts.com dapper/non-free Packages
  302 Found
Hit http://apt.mackers.com unstable Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Err http://medibuntu.sos-sts.com dapper/free Sources
  302 Found
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://ie.archive.ubuntu.com dapper/main Packages
Err http://medibuntu.sos-sts.com dapper/non-free Sources
  302 Found
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Err http://apt.mackers.com unstable Release

Ign http://download.skype.com stable Release.gpg
Get:10 http://apt.mackers.com unstable Release [1226B]
Get:11 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Ign http://free.linux.hp.com dapper-seveas Release.gpg
Ign http://download.skype.com stable Release
Ign http://getswiftfox.com unstable Release.gpg
Hit http://www.getautomatix.com dapper/main Packages
Ign http://apt.mackers.com unstable Release
Ign http://blognux.free.fr unstable Release
Hit http://download.skype.com stable/non-free Packages
Ign http://free.linux.hp.com dapper-seveas Release
Ign http://apt.mackers.com unstable/contrib Packages
Hit http://apt.mackers.com unstable/contrib Packages
Ign http://getswiftfox.com unstable Release
Hit http://ie.archive.ubuntu.com dapper/restricted Packages
Hit http://ie.archive.ubuntu.com dapper/universe Packages
Hit http://ie.archive.ubuntu.com dapper/multiverse Packages
Hit http://ie.archive.ubuntu.com dapper/main Sources
Hit http://ie.archive.ubuntu.com dapper/restricted Sources
Hit http://ie.archive.ubuntu.com dapper/universe Sources
Hit http://ie.archive.ubuntu.com dapper/multiverse Sources
Get:12 http://ie.archive.ubuntu.com dapper-updates/main Packages [261kB]
Ign http://free.linux.hp.com dapper-seveas/freenx Packages
Ign http://getswiftfox.com unstable/non-free Packages
Get:13 http://ie.archive.ubuntu.com dapper-updates/restricted Packages [6378B]
Get:14 http://ie.archive.ubuntu.com dapper-updates/universe Packages [98.0kB]
Ign http://free.linux.hp.com dapper-seveas/freenx Sources
Hit http://getswiftfox.com unstable/non-free Packages
Err http://free.linux.hp.com dapper-seveas/freenx Packages
  404 Not Found
Get:15 http://ie.archive.ubuntu.com dapper-updates/multiverse Packages [11.2kB]
Get:16 http://ie.archive.ubuntu.com dapper-updates/main Sources [71.4kB]
Get:17 http://ie.archive.ubuntu.com dapper-updates/restricted Sources [983B]
Get:18 http://ie.archive.ubuntu.com dapper-updates/universe Sources [14.6kB]
Ign http://blognux.free.fr unstable/main Packages
Err http://free.linux.hp.com dapper-seveas/freenx Sources
  404 Not Found
Get:19 http://ie.archive.ubuntu.com dapper-updates/multiverse Sources [2278B]
Hit http://ie.archive.ubuntu.com dapper-backports/main Packages
Hit http://ie.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ie.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ie.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ie.archive.ubuntu.com dapper-backports/main Sources
Hit http://ie.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://ie.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ie.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://blognux.free.fr unstable/main Packages
Fetched 524kB in 2s (256kB/s)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz  302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz  302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz  302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz  302 Found
Failed to fetch http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/source/Sources.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://apt.mackers.com unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F18E90BDEFA9630B
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
It looks like repository updates have not finished successfully. This is most likely due to some repositories being temporarily down, or to a missing GPG key for a third-party repository (see detailed output above). If the main repositories look like they have been updated successfully, you may just proceed without worrying about this.
Would you like to proceed with installation [y/n]?
Please enter 'y' or 'n': y

OK, Proceeding with installation.
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

Backing up old Firefox preferences


Downloading Firefox archive from the Mozilla site

--16:27:50--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/en-GB/firefox-2.0.0.11.tar.gz
           => `firefox-2.0.0.11.tar.gz'
Resolving releases.mozilla.org... 131.188.12.212, 155.98.64.83, 207.200.66.54, ...
Connecting to releases.mozilla.org|131.188.12.212|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/en-GB ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.11.tar.gz ... done.
Length: 9,444,649 (9.0M) (unauthoritative)

100%[====================================>] 9,444,649      3.36M/s

16:27:53 (3.35 MB/s) - `firefox-2.0.0.11.tar.gz' saved [9444649]


Downloading Firefox signature from the Mozilla site

--16:27:53--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/en-GB/firefox-2.0.0.11.tar.gz.asc
           => `firefox-2.0.0.11.tar.gz.asc'
Resolving releases.mozilla.org... 131.188.12.212, 155.98.64.83, 207.200.66.54, ...
Connecting to releases.mozilla.org|131.188.12.212|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/en-GB ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.11.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s

16:27:53 (13.64 MB/s) - `firefox-2.0.0.11.tar.gz.asc' saved [186]

tru::1:1168352163:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg --keyserver subkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 812347DD from hkp server pgpkeys.mit.edu
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg --keyserver pgpkeys.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 812347DD from hkp server pgp.mit.edu
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg --keyserver pgp.mit.edu --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: requesting key 812347DD from hkp server wwwkeys.pgp.net
gpg: requesting key 0E3606D9 from hkp server wwwkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg --keyserver wwwkeys.pgp.net --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from wwwkeys.pgp.net . Trying again...
gpg: requesting key 812347DD from hkp server keymaster.veridis.com
gpg: requesting key 0E3606D9 from hkp server keymaster.veridis.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net

ect......

```

Could anyone please enlighten me on the subject? I've been at this for a whole day.

Cheers,

SonicDread

---

### Post by nanotube on 2008-01-17
well, that problem does not appear to be caused by permissions, but by connectivity to the gpg keyservers.

are you using any proxies to access the net, by any chance? are your outgoing connections filtered by some firewall?

---

### Post by jvanvolk on 2008-01-24
I am having the same issue trying to install Thunderbird 2.0.0.9.  I am using Gutsy.
I changed my permissions and the owner of the directory and files.  It did not seem to resolve the problem.  The installer is not able to contact the keyserver.  I am receiving the same error as everyone above.

Does anyone know of a resolution?

Thanks,
Jared

---

### Post by mf-linux on 2008-04-17
:lolflag: Hey! I did not know how to manage permissions with gpg files, so I tried "sudo ubuntuzilla.py -a install -p firefox", and it worked!
Anyway, to avoid problems later, should I change permissions? If yes, how?
Thank you!:)

---

### Post by nanotube on 2008-04-17
> **mf-linux said:**
> :lolflag: Hey! I did not know how to manage permissions with gpg files, so I tried "sudo ubuntuzilla.py -a install -p firefox", and it worked!
Anyway, to avoid problems later, should I change permissions? If yes, how?
Thank you!:)

from your home dir, run command:

```
sudo chown -R yourusername.yourusername .gnupg/
```

(replase "yourusername" with your actual username, of course)

---

