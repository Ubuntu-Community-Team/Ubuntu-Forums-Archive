---
title: "Ubuntuzilla testing: please help if you can :)"
date: 2007-06-08
forum: Ubuntuzilla
---

### Post by nanotube on 2007-06-08
I have initiated the use of CVS for revision control for ubuntuzilla. So, you can get the latest "beta" versions of ubuntuzilla out of the [ubuntuzilla module on CVS]("http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/")
just pull the latest version, tagged "HEAD".

anyone who can spare some time to play around with the beta versions on, say, on a livecd (so as to avoid potential mishaps with your production system).

once the "beta" has seen and passed some testing, i will tag it with a release-version tag, and post the release on the file release servers. 

note that if you just want the stable release and don't want to help with testing, you should just visit the [Ubuntuzilla project site]("http://ubuntuzilla.sourceforge.net") and get the stable release from there.

i will post messages to this thread when a new beta is available, so that you will know when and what to test. ;)

---

### Post by nanotube on 2007-06-08
a new testing version is [available in CVS]("http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/"). 
it implements the "unattended" mode (command line option -u)
there is also a new -l option to supply the desired localization through command line (otherwise, how would it run unattended?).
run ubuntuzilla with '-h' to get the help info for all command line options.

so, please test the unattended installs, uninstalls, updates for all three packages, and see if everything works as expected.

test also the "regular" interactive mode functionality, to make sure nothing is broken.

thanks in advance to all testers!

---

### Post by nanotube on 2007-06-15
The latest revision in CVS now has some more new features. I can see that in the week or so that this thread has existed, nobody actually got around to testing anything, but hey, i figure, why not pretend someone is listening. :)

a new automatic update checker has been implemented. it's really cool, really! 

See the revision log for details.

please test this thing backwards and forwards, and see if anything falls out. :)

---

### Post by nanotube on 2007-08-02
i should have learned better than to expect someone to actually test something after reading this thread, but... here i go again. :)

ubuntuzilla version 4.2.0 is ready for release, but i'd like to get some independent testing to make sure things work. 

a lot of changes made. the most notable ones being that ubuntuzilla now comes in a .deb for easier and more consistent installation/removal, as well as with a built-in self-updater. 

for more detailed change list, see the [CVS changelogs]("http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/ubuntuzilla.py?view=log") for revisions 1.17 - 1.19.

if anyone finds something amiss, please let me know. :)

the 4.2.0 .deb file is attached to this message.

---

### Post by aysiu on 2007-08-10
Here's what I get: ```
username@ubuntu:~/Desktop$ sudo dpkg -i ubuntuzilla-4.2.0-0ubuntu1.deb 
Password:
Sorry, try again.
Password:
Selecting previously deselected package ubuntuzilla.
(Reading database ... 120708 files and directories currently installed.)
Unpacking ubuntuzilla (from ubuntuzilla-4.2.0-0ubuntu1.deb) ...
dpkg: dependency problems prevent configuration of ubuntuzilla:
 ubuntuzilla depends on libnotify-bin; however:
  Package libnotify-bin is not installed.
dpkg: error processing ubuntuzilla (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntuzilla
username@ubuntu:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libnotify-bin
The following NEW packages will be installed:
  libnotify-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 18.3kB of archives.
After unpacking 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com feisty/universe libnotify-bin 0.4.3-1 [18.3kB]
Fetched 18.3kB in 0s (18.9kB/s)    
Selecting previously deselected package libnotify-bin.
(Reading database ... 120712 files and directories currently installed.)
Unpacking libnotify-bin (from .../libnotify-bin_0.4.3-1_i386.deb) ...
Setting up libnotify-bin (0.4.3-1) ...
Setting up ubuntuzilla (4.2.0-0ubuntu1) ...
username@ubuntu:~/Desktop$ u
ubuntu-bug                ulimit                    unset                     update-default-ispell     update-locale             update-xmlcatalog
ubuntuzilla.py            umask                     unstr                     update-default-wordlist   update-manager            uptime
ucf                       umount                    until                     update-desktop-database   update-mime               usbmodules
ucfq                      unalias                   unzip                     update-dictcommon-aspell  update-mime-database      usb_printerid
ucfr                      uname                     unzipsfx                  update-fonts-alias        update-modules            useradd
ucs2any                   unattended-upgrade        update-alternatives       update-fonts-dir          update-ms-fonts           userdel
udevcontrol               uncompress                update-anthy-dics         update-fonts-scale        update-notifier           usermod
udevd                     unexpand                  update-app-install        update-gconf-defaults     update-openoffice-dicts   users
udevinfo                  unicode_start             update-binfmts            update-gdkpixbuf-loaders  update-pangox-aliases     users-admin
udevmonitor               unicode_stop              update-ca-certificates    update-grub               update-passwd             usplash
udevsettle                uniq                      update-catalog            update-gtk-immodules      update-pciids             usplash_down
udevtest                  unix_chkpwd               updatedb                  update-inetd              update-python-modules     usplash_write
udevtrigger               unlink                    updatedb.notslocate       update-initramfs          update-rc.d               uuidgen
ul                        unpack200                 update-default-aspell     update-java-alternatives  update-usbids             uxterm
username@ubuntu:~/Desktop$ ubuntuzilla.py 

Welcome to the Ubuntuzilla Firefox script version 4.2.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 2.0.0.6. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla for steps you can take to resolve this problem.]
  0. awk: warning: escape sequence `\/' treated as plain `/'   1. af           2. ar           3. be        
  4. bg           5. ca           6. cs           7. da        
  8. de           9. el          10. en-GB       11. en-US     
 12. es-AR       13. es-ES       14. eu          15. fi        
 16. fr          17. fy-NL       18. ga-IE       19. gu-IN     
 20. he          21. hu          22. it          23. ja        
 24. ka          25. ko          26. ku          27. lt        
 28. mk          29. mn          30. nb-NO       31. nl        
 32. nn-NO       33. pa-IN       34. pl          35. pt-BR     
 36. pt-PT       37. ro          38. ru          39. sk        
 40. sl          41. sv-SE       42. tr          43. zh-CN     
 44. zh-TW     
Enter your choice of localization (integer, from 0 to 44): 11
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Get:1 http://packages.medibuntu.org feisty Release.gpg [189B]
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]                        
Ign http://security.ubuntu.com feisty-security/main Translation-en_US                             
Get:3 http://archive.ubuntu.com feisty-updates Release.gpg [191B]    
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US                         
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://packages.medibuntu.org feisty/free Translation-en_US      
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US  
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US  
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Hit http://archive.ubuntu.com feisty-updates Release                 
Hit http://security.ubuntu.com feisty-security Release                                    
Hit http://packages.medibuntu.org feisty Release                                          
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                              
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                           
Hit http://archive.ubuntu.com feisty-updates/restricted Packages                         
Hit http://security.ubuntu.com feisty-security/main Packages         
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Get:5 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]                       
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US                     
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US               
Ign http://packages.medibuntu.org feisty/free Packages                                     
Hit http://archive.ubuntu.com feisty-updates/main Packages                                 
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages     
Hit http://archive.ubuntu.com feisty-updates/universe Packages       
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/universe Packages     
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Ign http://packages.medibuntu.org feisty/non-free Packages          
Hit http://packages.medibuntu.org feisty/free Packages              
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Fetched 193B in 2s (76B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
libstdc++5 is already the newest version.
libgtk2.0-0 is already the newest version.
libgtk2.0-0 set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences


Downloading Firefox archive from the Mozilla site

--07:20:10--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/en-US/firefox-2.0.0.6.tar.gz
           => `firefox-2.0.0.6.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 207.200.66.54, 152.163.212.246, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.6.tar.gz ... done.
Length: 9,671,806 (9.2M) (unauthoritative)

100%[===========================================================================================================================>] 9,671,806    618.52K/s    ETA 00:00

07:20:28 (568.15 KB/s) - `firefox-2.0.0.6.tar.gz' saved [9671806]


Downloading Firefox signature from the Mozilla site

--07:20:28--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/en-US/firefox-2.0.0.6.tar.gz.asc
           => `firefox-2.0.0.6.tar.gz.asc'
Resolving releases.mozilla.org... 204.152.184.113, 207.200.66.54, 130.239.18.159, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.6.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[===========================================================================================================================>] 186           --.--K/s             

07:20:28 (13.49 KB/s) - `firefox-2.0.0.6.tar.gz.asc' saved [186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: directory `/home/alan/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/alan/.gnupg/secring.gpg' created
gpg: keyring `/home/alan/.gnupg/pubring.gpg' created
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: /home/alan/.gnupg/trustdb.gpg: trustdb created
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Successfully retrieved Mozilla Software Releases Public key from pgpkeys.mit.edu .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Sun 29 Jul 2007 08:55:41 PM PDT using DSA key ID 0E3606D9
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: F57F 372A 8C6D 4F55 72DE  C9B9 696E 3431 0E36 06D9
Password:

Linking plugins


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 2.0.0.6 has been installed successfully. Thank you for using Ubuntuzilla.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y

Making sure package libnotify-bin (necessary to produce notifications) is installed.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnotify-bin is already the newest version.
libnotify-bin set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
no crontab for alan
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.
``` Pretty much successful. It's a little weird that I was prompted for a password in the middle of the installation. I don't *think* fifteen minutes had passed (for the sudo timeout).

Also, the script checks that *libnotify-bin* is installed, but the .deb won't install without *libnotify-bin*. I think it'd make sense to not have *libnotify-bin* be a dependency (a simple .deb that installs by itself would be good) and then have the script check for that package only if you want the update feature.

---

### Post by nanotube on 2007-08-10
hey, nice, so it works after all, eh. :)

as to libnotify-bin - well, that extra check is left over from when ubuntuzilla wasn't in a .deb yet. i think i'd rather leave it as a dependency, and remove the manual check. i feel better using an "official" method of keeping track of dependencies, rather than the ad-hoc method i had before.

same thing goes for libstdc++5 and libgtk. 

what do you think?

also, by the way, if you use "gdebi -i" instead of "dpkg -i", it will automatically take care of dependencies for you. using gdebi will be the method i recommend in the instructions (or just doubleclicking the .deb, which uses gdebi-gtk).

---

### Post by aysiu on 2007-08-10
Well, is it really a dependency if it's needed only for the "yes" option on self-updating Firefox? Perhaps it could be a recommended package? Doesn't *dpkg* allow for recommended packages?

Thanks for the tip about gdebi, by the way.

---

### Post by nanotube on 2007-08-10
it is a dependency to do update checking, for firefox, tbird, and seamonkey. it comes into play both when doing automatic update checking through a cron job, as well as when doing a manual update checking (with -a 'checkforupdategui'). if i leave it out, then i'll have to put in the apt-get check when doing the update check itself, and that means the cron job will need sudo rights, and that would mess everything up.

i am pretty sure it is a general practice to include all dependencies for built in program features, even for features that may not be the "main" part of the program. so i think i'll just keep it as a dependency. it will let me avoid doing manual libnotify-bin checking, and keep things nice and clean.

i did not put firefox or thunderbird main packages into the dependency list, because the need for those depends on what the person is using ubuntuzilla for, but libnotify-bin is needed for all of them.

does that seem reasonable to you?

---

### Post by aysiu on 2007-08-10
Thanks for the explanation. That makes sense.

---

### Post by nanotube on 2007-08-10
let me know if you think of anything else. discussing things with you always seems to make them clearer in my mind. :)

i'm in the process of moving the CVS repository and the file releases over to ubuntuzilla project space (made a request to the admins and waiting to hear from them). I will make the 4.2 release once the ubuntuzilla project is all set up.

---

### Post by aysiu on 2007-08-10
Another thing I was thinking of as a feature request (I know you already have a lot of things you're thinking of, but I'll just throw this out there): *man* page?

Right now, you do ```
ubuntuzilla.py -help
``` which is fine, but I think it may help some veterans (or even relative beginners) to know that ```
man ubuntuzilla
``` would work.

---

### Post by nanotube on 2007-08-10
that's a good idea - the thought has crossed my mind, but then i realized i don't know how to make man pages. :)

i'll look into it when i have some time - man pages /are/ nice.

---

### Post by michael37 on 2007-08-14
Hi Nanotube,

Thanks for creating the ThunderbirdNewVersion page and keeping the Tbird pages updated.  I based my Wiki updates on the Thunderbird discussed from the x86_64 forums.  I didn't know about existence of this forum on Tbird.

I have a question about the 64-bit Ubuntuzilla script.  As far as I can see, the script installs only the 32-bit binaries from release.mozilla.org and, per [http://ubuntuzilla.wiki.sourceforge.net/#tochome23](http://ubuntuzilla.wiki.sourceforge.net/#tochome23), requires 32-bit libraries to work.  However, the repository supports native 64-bit binaries.  Am I missing something?

---

### Post by nanotube on 2007-08-14
> **michael37 said:**
> Hi Nanotube,

Thanks for creating the ThunderbirdNewVersion page and keeping the Tbird pages updated.  I based my Wiki updates on the Thunderbird discussed from the x86_64 forums.  I didn't know about existence of this forum on Tbird.

I have a question about the 64-bit Ubuntuzilla script.  As far as I can see, the script installs only the 32-bit binaries from release.mozilla.org and, per [http://ubuntuzilla.wiki.sourceforge.net/#tochome23](http://ubuntuzilla.wiki.sourceforge.net/#tochome23), requires 32-bit libraries to work.  However, the repository supports native 64-bit binaries.  Am I missing something?

hi michael!
i wanted to contact you to discuss the wiki updates, but you didn't have a wiki user page with contact info, so i had no choice but to just jump in and edited on top of your edits. :) thanks for adding that third-party repo, it's a pretty good alternative method. 

as to the 32bit vs 64bit, yes, you're right, ubuntuzilla only installs the 32bit binary, because those are the only binaries that are provided by mozilla itself. but since they work on 64bit using the 32bit compatibility libraries, i titled the ubuntuzilla method as "32bit and 64bit"... it isn't supposed to imply that it installs native 64bit binaries, only that it will work on 64bit systems. 
what do you think?

thanks for seeking out these forums and posting! :)

---

### Post by michael37 on 2007-08-16
> **nanotube said:**
> hi michael!
i wanted to contact you to discuss the wiki updates, but you didn't have a wiki user page with contact info, so i had no choice but to just jump in and edited on top of your edits. :) thanks for adding that third-party repo, it's a pretty good alternative method. 

as to the 32bit vs 64bit, yes, you're right, ubuntuzilla only installs the 32bit binary, because those are the only binaries that are provided by mozilla itself. but since they work on 64bit using the 32bit compatibility libraries, i titled the ubuntuzilla method as "32bit and 64bit"... it isn't supposed to imply that it installs native 64bit binaries, only that it will work on 64bit systems. 
what do you think?

thanks for seeking out these forums and posting! :)

Well, you now know who I am.  Please to meet you too,

Actually, I think this 64 vs 32bit stuff is fairly confusing.  First of all, the 64-bit Ubuntu that I installed with all defaults doesn't have most of the needed 32-bit libraries.  I struggled some tracking the right libraries before I got 32-bit Ubuntuzilla install to work.

Also, this 64-bit vs 32-bit stuff is very confusing for Lightning users.  There have been quite a few discussions on the subject on x86_64 board.  Lightning extension is binary, so it is arch specific and must match the Thunderbird arch.  The 32-bit Lightning is officially released, and 64-bit Lightning is also available in contribs (see my ThunderbirdLightning page).  Oddly enough, 64-bit Thunderbird is not available in contribs :confused:  Anyway, I struggled a bit trying to explain on the Lightning page how to install the right version of Lightning.

---

### Post by nanotube on 2007-08-16
> **michael37 said:**
> Well, you now know who I am.  Please to meet you too,

Actually, I think this 64 vs 32bit stuff is fairly confusing.  First of all, the 64-bit Ubuntu that I installed with all defaults doesn't have most of the needed 32-bit libraries.  I struggled some tracking the right libraries before I got 32-bit Ubuntuzilla install to work.

Also, this 64-bit vs 32-bit stuff is very confusing for Lightning users.  There have been quite a few discussions on the subject on x86_64 board.  Lightning extension is binary, so it is arch specific and must match the Thunderbird arch.  The 32-bit Lightning is officially released, and 64-bit Lightning is also available in contribs (see my ThunderbirdLightning page).  Oddly enough, 64-bit Thunderbird is not available in contribs :confused:  Anyway, I struggled a bit trying to explain on the Lightning page how to install the right version of Lightning.

well, this issue of missing ia32 libs is going to be moot starting with ubuntuzilla 4.3.0, since i will be releasing two .debs, one for i386, and one for amd64. the only difference between the two will be that the amd64 will have the ia32 and other 32bit compatibility libraries as dependencies, which should minimize any problems for 64bit users...

but yes, it is all pretty confusing - and i don't even run 64bit ubuntu! :)

by the way, just to be certain - what is your output on your 64bit ubuntu install of command
```
uname -m
```
it is "x86_64", right?

---

### Post by nanotube on 2007-08-17
hey aysiu,

ok, so the man page is now in existence. :)

try out the latest version (4.3.0) of ubuntuzilla - install the .deb, then try
```
man ubuntuzilla
```

fancy, eh? :)

---

### Post by aysiu on 2007-08-17
Just tested it out. The man page looks great!

---

### Post by nanotube on 2007-08-17
> **aysiu said:**
> Just tested it out. The man page looks great!

i'm glad you like it :) thanks for prompting me to make it - i learned how to make manpages, and learning something new is always nice. 

let me know if you think of any other nifty things i could add. :)

---

### Post by michael37 on 2007-08-17
> **nanotube said:**
> well, this issue of missing ia32 libs is going to be moot starting with ubuntuzilla 4.3.0, since i will be releasing two .debs, one for i386, and one for amd64. the only difference between the two will be that the amd64 will have the ia32 and other 32bit compatibility libraries as dependencies, which should minimize any problems for 64bit users...

but yes, it is all pretty confusing - and i don't even run 64bit ubuntu! :)

by the way, just to be certain - what is your output on your 64bit ubuntu install of command
```
uname -m
```
it is "x86_64", right?

Yes, it is x86_64. The .debs are called amd64, just for confusion.  

In my experience, the ia32linux libs were not enough.  I also needed some gtk libraries at al.  How are you going to test the amd64 package? I'd love to volunteer, but I use this 64-bit computer for "production" so I can't experiment with removing libraries etc.

Also, what are your thoughts on integrating Lightning in ubuntuzilla?

---

### Post by nanotube on 2007-08-17
> **michael37 said:**
> Yes, it is x86_64. The .debs are called amd64, just for confusion.  

In my experience, the ia32linux libs were not enough.  I also needed some gtk libraries at al.  How are you going to test the amd64 package? I'd love to volunteer, but I use this 64-bit computer for "production" so I can't experiment with removing libraries etc.

Also, what are your thoughts on integrating Lightning in ubuntuzilla?

hm, well, the testing for the supporting libraries has been done before by others - which resulted it the "help" item for 64bit users on the ubuntuzilla site (check it out, it's there toward the end)
i just added those dependencies into the .deb - everything else stays exactly the same as the i386 version.

about lightning - my understanding is that it is just an extension for thunderbird... so once you install thunderbird using ubuntuzilla, you can just go and download the lightning extension, and install it on thunderbird like any other extension? why would ubuntuzilla need to do anything about it?

i appreciate your willingness to help with testing, and i totally understand your reluctance to mess with a production machine. thanks for the thought, anyway. :)

---

### Post by michael37 on 2007-08-18
> **nanotube said:**
> about lightning - my understanding is that it is just an extension for thunderbird... so once you install thunderbird using ubuntuzilla, you can just go and download the lightning extension, and install it on thunderbird like any other extension? why would ubuntuzilla need to do anything about it?

They packaged lightning as an extension to the thunderbird, but it's really an embedded binary application that is architecture dependent (e.g. lightning also requires dynamic libraries).  Most extensions are truly XUL-based architecture independent.  The tricky part here is that lightning must match the architecture of parent Thunderbird application.  Thunderbird doesn't check for this level of details, so it's entirely possible to install 32-bit Lightning into 64-bit Thunderbird and pull one's hair our trying to make it work.  Check our more details at this page: [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning).  So, I had to differentiate between the repository method and ubuntuzilla method since they result in Thunderbird binaries of different architectures.

---

### Post by nanotube on 2007-08-18
ah-ha... i will have to make that clear in my instructions, then, since my amd64 version installs the 32bit thunderbird, along with the compatibility libraries, not a native 64bit thunderbird (which is not available from mozilla).

thanks for pointing that out. :)

---

### Post by manij on 2007-08-28
Alright, newbie here,

did a dual boot install on tpad r51 with dapper. install went fi ne and i'm able use the basic functions

wanted to run the script so i can upate firefox

double click,

first error say libnotify-bin not satifsfied

downlaoded libnotify-bin package fro debian.org

second error

libc6 depency not satisfied

dowloaded that
 third error

libgllib2.00 blah blah depency not satisfied

dowloaded that and i get the message

fourht error 

failed to satisfy all dependencies (broken cache)

What on earth does this mean and how do i fix it?


thanks
Mani

---

### Post by Dark Star on 2007-08-28
What can I do .:) Plz lemme know :D

---

### Post by nanotube on 2007-08-28
> **manij said:**
> Alright, newbie here,

did a dual boot install on tpad r51 with dapper. install went fi ne and i'm able use the basic functions

wanted to run the script so i can upate firefox

double click,

first error say libnotify-bin not satifsfied

downlaoded libnotify-bin package fro debian.org

second error

libc6 depency not satisfied

dowloaded that
 third error

libgllib2.00 blah blah depency not satisfied

dowloaded that and i get the message

fourht error 

failed to satisfy all dependencies (broken cache)

What on earth does this mean and how do i fix it?


thanks
Mani

hi,
ehrm... if you use gdebi to install, it should automatically take care of the dependencies and all that... what are you using to install the package? dpkg?

also, if you're getting packages manually, don't get them from debian.org, get them from packages.ubuntu.com

debian packages are frequently incompatible with ubuntu.

so... uninstall all those debian packages you got,
then run "apt-get install -f"
then run "sudo gdebi -i /path/to/ubuntuzillapackage.deb"

see how that goes. :)

---

### Post by nanotube on 2007-08-28
> **Dark Star said:**
> What can I do .:) Plz lemme know :D

thanks for your offer to help! are you looking to code, or to test? :)

if you're up for doing some python coding, then we can discuss possible new features, etc. 

if you're up for testing, then i'll just pm you whenever there's a new release that needs some testing.

---

### Post by manij on 2007-08-28
Hi nano,

Thanks for helping this newb. I reinsatlled ubuntu dapper (didn't know how to uninstall the other packges) and tried the gdebi command. I have the ubuntuzilla file stored on my desktop and executed the gdebi command as sown below and you can see the error message i get. help please!

Thanks

XXX@XXX-laptop:~/Desktop$ sudo gdebi -i ubuntuzilla-4.4.0-0ubuntu1-i386.deb
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: -i
XXX@XXX-laptop:~/Desktop$

---

### Post by manij on 2007-08-28
when i run the apt -get install command, i get the follwowing error! like I said this is probbaly some rookie stuff. thanks for your help!

xxx@xxx-laptop:~/Desktop$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by nanotube on 2007-08-28
the apt-get error is because it needs to be run as root (with sudo).

also, my bad: gdebi doesn't need a '-i', you should just run a 
```
sudo gdebi ubuntuzillapackage.deb
```

if that still doesn't work, then you can try the following:

first command:
```
sudo dpkg -i ubuntizillapackagename.deb
```

second command;
```
sudo apt-get install -f
```

and that should take care of the installation...

don't know what's up with gdebi.. maybe the dapper version is substantially different than the one in feisty...?

---

### Post by aysiu on 2008-06-20
Okay, nanotube. I tested it on Hardy, and it works (as in, it gets Firefox installed), but there seems to be a weird error the first time it tries to get localizations and the package name: ```
username@username-desktop:~/Desktop$ python ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.4.9

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
[b]w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1[/b]
Download error. Trying again, hoping for a different mirror.
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

Enter your choice of localization (integer, from 0 to 47): 9
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
[sudo] password for username: 
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://archive.canonical.com hardy Release
Hit http://us.archive.ubuntu.com hardy Release.gpg      
Hit http://archive.canonical.com hardy/partner Packages
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy/partner Sources
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-security Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Reading package lists... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 libnotify-bin gcc-3.3-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
[b]w3m -dump ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{print $1}'
w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US.[/b]
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.tar.bz2

Downloading Firefox archive from the Mozilla site

--13:25:51--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
           => `firefox-3.0.tar.bz2'
Resolving releases.mozilla.org... 130.239.18.158, 130.239.18.159, 149.20.20.5, ...
Connecting to releases.mozilla.org|130.239.18.158|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.tar.bz2 ... done.
Length: 9,083,705 (8.7M) (unauthoritative)

100%[=====================================================>] 9,083,705    333.07K/s    ETA 00:00

13:26:21 (315.74 KB/s) - `firefox-3.0.tar.bz2' saved [9083705]


Downloading Firefox signature from the Mozilla site

--13:26:21--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2.asc
           => `firefox-3.0.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.238.52, 129.101.198.62, 130.239.18.158, ...
Connecting to releases.mozilla.org|64.50.238.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[=====================================================>] 186           --.--K/s             

13:26:22 (18.26 KB/s) - `firefox-3.0.tar.bz2.asc' saved [186]

tru::1:1209155865:0:3:1:5
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

gpg: Signature made Wed 11 Jun 2008 05:22:04 AM EDT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8


Linking plugins

Linking dictionaries

Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'

Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0 has been installed successfully.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
no crontab for username
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.
username@username-desktop:~/Desktop$ firefox &
[1] 5679
```

---

### Post by nanotube on 2008-06-20
thanks for testing! :)

(by the way, for the benefit of others reading this, we're testing the latest release candidate, attached to this bug report thread: [http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990](http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990) )

[ftp://releases.mozilla.org](ftp://releases.mozilla.org) is having some problems. (well was a few minutes ago - but just tried again now, it's back up.

try again if you'd like. 

hey, that's the beauty of having many mirrors to try, it just rips right past the error. heh. :) 

so it installs... did you try to see if it runs, detects the plugins, if the link is correct (after installation, if you launch /usr/bin/firefox, does it launch the right one, the mozilla build?)

---

### Post by nanotube on 2008-06-20
by the way, could you also please test this ubuntuzilla .deb, to make sure it installs on hardy ok? (attached)

---

### Post by aysiu on 2008-06-20
> **nanotube said:**
> by the way, could you also please test this ubuntuzilla .deb, to make sure it installs on hardy ok? (attached)
Works on Hardy: ```
username@ubuntu-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.4.9

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

Enter your choice of localization (integer, from 0 to 47): 9
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Hit http://archive.canonical.com hardy Release.gpg
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.canonical.com hardy/partner Sources
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-security Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.tar.bz2

Downloading Firefox archive from the Mozilla site

--14:56:18--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
           => `firefox-3.0.tar.bz2'
Resolving releases.mozilla.org... 204.152.184.196, 216.165.129.141, 64.50.236.52, ...
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 204.152.184.196 port 52794: Connection timed out
Retrying.

--14:59:28--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
  (try: 2) => `firefox-3.0.tar.bz2'
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 204.152.184.196 port 64678: Connection timed out
Retrying.

--15:02:39--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
  (try: 3) => `firefox-3.0.tar.bz2'
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 204.152.184.196 port 44099: Connection timed out
Retrying.

--15:05:51--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
  (try: 4) => `firefox-3.0.tar.bz2'
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 204.152.184.196 port 30857: Connection timed out
Retrying.

--15:09:04--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
  (try: 5) => `firefox-3.0.tar.bz2'
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 204.152.184.196 port 54845: Connection timed out
Giving up.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--15:12:15--  ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
           => `firefox-3.0.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.tar.bz2 ... done.
Length: 9,083,705 (8.7M) (unauthoritative)

100%[=====================================================>] 9,083,705      1.19M/s    ETA 00:00

15:12:22 (1.29 MB/s) - `firefox-3.0.tar.bz2' saved [9083705]


Downloading Firefox signature from the Mozilla site

--15:12:22--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2.asc
           => `firefox-3.0.tar.bz2.asc'
Resolving releases.mozilla.org... 156.56.247.196, 204.152.184.196, 216.165.129.141, ...
Connecting to releases.mozilla.org|156.56.247.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[=====================================================>] 186           --.--K/s             

15:12:23 (1.29 KB/s) - `firefox-3.0.tar.bz2.asc' saved [186]

tru::1:1213982785:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1213982785:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2009-07-16::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2009-07-16:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2009-07-16:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Wed 11 Jun 2008 05:22:04 AM EDT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
[sudo] password for username: 

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0 has been installed successfully.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.
username@ubuntu-desktop:~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 20 2008-06-20 15:14 /usr/bin/firefox -> /opt/firefox/firefox
username@ubuntu-desktop:~$ firefox &
[1] 5740
username@ubuntu-desktop:~$ 
(firefox-bin:5757): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox-bin:5757): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox-bin:5757): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox-bin:5757): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

[1]+  Done                    firefox
username@ubuntu-desktop:~$ ls /opt/firefox/plugins -l
lrwxrwxrwx 1 root root 33 2008-06-20 15:14 /opt/firefox/plugins -> /usr/lib/xulrunner-addons/plugins
username@ubuntu-desktop:~$ 
```

---

### Post by nanotube on 2008-06-20
cool, i'll make the release!

thanks for testing - you are as ever prompt and effective. :)

---

### Post by aysiu on 2008-06-20
> **nanotube said:**
> cool, i'll make the release!

thanks for testing - you are as ever prompt and effective. :)
Glad to have been of help.

Do you think future releases (whenever you have time, of course) might have a GUI frontend?

---

### Post by nanotube on 2008-06-20
> **aysiu said:**
> Glad to have been of help.

Do you think future releases (whenever you have time, of course) might have a GUI frontend?

it doesn't seem very likely to happen in the near future, as i have been rather busy lately.
maybe if someone else steps in to make a gui on top of the current ubuntuzilla...

---

### Post by aysiu on 2008-06-20
Cool.

---

### Post by nanotube on 2008-06-30
Hey aysiu,

so, there appears to be an issue trying to run firefox3 on ubuntu dapper.
see the discussion between me and user 'stig' on this thread:
[http://ubuntuforums.org/showthread.php?t=832407&page=2](http://ubuntuforums.org/showthread.php?t=832407&page=2)

our attempt to avoid compiling gtk2.10 appears a failure (but maybe you could give it a try on dapper yourself and see if this is the same for you)

so i wonder if you could help me out in getting ff3 running on dapper?

let me know if you have the time (and if you think it is even worth it to worry about dapper at the moment. true, it's "supported" for another year, but... )

---

### Post by aysiu on 2008-06-30
Unfortunately, right now I don't have easy access to a Dapper installation. I'm hoping a dedicated Dapper user can step up to the task.

---

### Post by nanotube on 2008-06-30
> **aysiu said:**
> Unfortunately, right now I don't have easy access to a Dapper installation. I'm hoping a dedicated Dapper user can step up to the task.

ok, no problem... 
maybe i'll get to booting with a dapper livecd and testing it out myself one of these days... ;)

---

### Post by wkitty42 on 2008-07-03
> **aysiu said:**
> Unfortunately, right now I don't have easy access to a Dapper installation. I'm hoping a dedicated Dapper user can step up to the task.

yeah, i'm on it... we'll have to see how far it goes...

PS: don't let the post count confuse you... i've been running Dapper since it first appeared on the streets... i just haven't even had the need to post anything in these forums until now ;)

---

### Post by Zajeec5u on 2008-09-30
Is testing under Dapper still an issue?
I'm about to setup a vm for a test of something else.

     Michael.

> **nanotube said:**
> Hey aysiu,

so, there appears to be an issue trying to run firefox3 on ubuntu dapper.
see the discussion between me and user 'stig' on this thread:
[http://ubuntuforums.org/showthread.php?t=832407&page=2](http://ubuntuforums.org/showthread.php?t=832407&page=2)

our attempt to avoid compiling gtk2.10 appears a failure (but maybe you could give it a try on dapper yourself and see if this is the same for you)

so i wonder if you could help me out in getting ff3 running on dapper?

let me know if you have the time (and if you think it is even worth it to worry about dapper at the moment. true, it's "supported" for another year, but... )

---

### Post by nanotube on 2008-10-01
well no, not really - ff3 on dapper is a dead cause, i have not found any way to make it work.

but thanks for offering :)

---

### Post by Sef on 2008-10-01
> Is testing under Dapper still an issue?

The desktop version of Dapper end of life is June 2009.  If you are using it, it would be best to start thinking about upgrading.

---

### Post by Zajeec5u on 2008-10-02
> **nanotube said:**
> well no, not really - ff3 on dapper is a dead cause, i have not found any way to make it work.
but thanks for offering :)

okie dokie - just asking since I needed an installation for a test setup anyay.

  :-) Michael.

---

### Post by Zajeec5u on 2008-10-02
> **Sef said:**
> The desktop version of Dapper end of life is June 2009.  If you are using it, it would be best to start thinking about upgrading.

Thanks for pointing out! It's just a testing environment I needed to set up.

   :-) Michael. (eagerly waiting for intrepid)

---

### Post by nanotube on 2008-10-28
4.5.4 rc attached to this thread.

The changelog is here:
[http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/CHANGELOG.TXT?view=markup](http://ubuntuzilla.cvs.sourceforge.net/ubuntuzilla/ubuntuzilla/CHANGELOG.TXT?view=markup)

Please test if you can.

---

### Post by Zajeec5u on 2008-11-10
Hi, I just installed FF 3.0.3 w/ v 4.5.5 on a test system running 7.10 without any problems.
Thanks a lot and a big sorry for the delay!

   Michael.

---

### Post by nanotube on 2008-11-15
Next release candidate:
testing a bugfix in process-list walkthrough to find the dbus session bus address.

---

### Post by kansasnoob on 2008-12-20
I just recently tried Ubuntuzilla on Intrepid and Mint 6 and was quite impressed, although I had a minor problem in Mint. Anyway, I'm available, as time allows, for testing (I have a spare hard drive).

So feel free to message me if you want me to give something a test drive! My internet is fairly quick: 2500 KB/s DL and 400+ KB/s UL and unlimited downloads so if I can help please give me a shout!

I should add that I never could get Dapper to run on this machine.

---

### Post by pete25r on 2008-12-22
Ubunuzilla, sounds cool. What makes it different for the other releases? Somewhere I can find info on it?

How do I test? Ok I have done like 5-6 Ubuntu installs, different releases on different PCs. I haven't really gotten down into it just yet though. Like a feature of the PC won't work (ie wireless) and I'll get fustrated and with tale tucked between legs crawl back to windows. I'm learning more commands and how stuff works in Ubuntu/Debian. I dig it.

What exactly do you want as far as info after the install attempt?
Just a yeh it worked, or it stopped at point ??? in the install?


I don't have a problem at all throwing down on some live cds. I've got like 3 PCs to that I can do that on. I even have a spare PC I don't mind going full install all.

---

### Post by nanotube on 2008-12-23
> **kansasnoob said:**
> I just recently tried Ubuntuzilla on Intrepid and Mint 6 and was quite impressed, although I had a minor problem in Mint. Anyway, I'm available, as time allows, for testing (I have a spare hard drive).

So feel free to message me if you want me to give something a test drive! My internet is fairly quick: 2500 KB/s DL and 400+ KB/s UL and unlimited downloads so if I can help please give me a shout!

I should add that I never could get Dapper to run on this machine.

thanks, appreciate the offer! will be sure to send you a pm when i put out new releases. :)

---

### Post by nanotube on 2008-12-23
> **pete25r said:**
> Ubunuzilla, sounds cool. What makes it different for the other releases? Somewhere I can find info on it?

How do I test? Ok I have done like 5-6 Ubuntu installs, different releases on different PCs. I haven't really gotten down into it just yet though. Like a feature of the PC won't work (ie wireless) and I'll get fustrated and with tale tucked between legs crawl back to windows. I'm learning more commands and how stuff works in Ubuntu/Debian. I dig it.

What exactly do you want as far as info after the install attempt?
Just a yeh it worked, or it stopped at point ??? in the install?


I don't have a problem at all throwing down on some live cds. I've got like 3 PCs to that I can do that on. I even have a spare PC I don't mind going full install all.

Hi!
ubuntuzilla is not a flavor of ubuntu - it is just a program to automatically download and install the latest mozilla software builds on ubuntu. for more info, please visit the project homepage, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2008-12-23
Hi,
well, hot on the heels of you offering to test, here's something to test. :)
Please see this thread:
[http://ubuntuforums.org/showthread.php?t=1013724](http://ubuntuforums.org/showthread.php?t=1013724)

in particular, post #5 in it. need to test whether seamonkey installation properly links the plugins. 

thanks :)

---

### Post by nanotube on 2009-01-01
Hi,
Another version to test, please see this post
[http://ubuntuforums.org/showpost.php?p=6474668&postcount=8](http://ubuntuforums.org/showpost.php?p=6474668&postcount=8)

I have made the package and plugin path detection generic, not depending on hard-coded ubuntu version checks. should be both more "future-proof", as well as usable on any debian/ubuntu derivative distro, not just ubuntu.

Would appreciate some testing and feedback, before I release it into the wild.

Attaching the latest release candidate to this post, for easy access.

---

### Post by PierreDeKat on 2009-01-01
Okay, running Intrepid, and I just
1) downloaded ubuntuzilla-4.6.0-0ubuntu1-i386.deb to my /home/ directory
1) uninstalled Seamonkey 1.1.14 via earlier ubuntuzilla-4.5.9-0ubuntu1-i386.deb
2) uninstalled ubuntuzilla-4.5.9-0ubuntu1-i386.deb via Synaptic
3) installed ubuntuzilla-4.6.0-0ubuntu1-i386.deb by double-clicking on the downloaded file
4) reinstalled Seamonkey 1.1.14 via new ubuntuzilla-4.6.0-0ubuntu1-i386.deb

And everything went well. My Seamonkey plugins are linked to my Firefox plugins, just like in 4.5.9. Flash and Flashblock work perfectly.

Lookin' good from my end.

---

### Post by PierreDeKat on 2009-01-01
While we're on the subject, nanotube, have you thought about setting up a reasonably secure mail list to announce new versions? If you do, I would be happy to sign up for notifications.

---

### Post by nanotube on 2009-01-02
> **PierreDeKat said:**
> While we're on the subject, nanotube, have you thought about setting up a reasonably secure mail list to announce new versions? If you do, I would be happy to sign up for notifications.

Hi,
That's already in existence, it's part of sourceforge release monitoring functionality. so... go to this page:
[https://sourceforge.net/project/showfiles.php?group_id=202789](https://sourceforge.net/project/showfiles.php?group_id=202789)

and click on the "monitor" button next to ubuntuzilla. you will then get notified by email every time a new release is made.

you have to have an account on sourceforge for this to work, of course, but those are free and no-hassle to create.

---

### Post by nanotube on 2009-01-02
> **PierreDeKat said:**
> Okay, running Intrepid, and I just
1) downloaded ubuntuzilla-4.6.0-0ubuntu1-i386.deb to my /home/ directory
1) uninstalled Seamonkey 1.1.14 via earlier ubuntuzilla-4.5.9-0ubuntu1-i386.deb
2) uninstalled ubuntuzilla-4.5.9-0ubuntu1-i386.deb via Synaptic
3) installed ubuntuzilla-4.6.0-0ubuntu1-i386.deb by double-clicking on the downloaded file
4) reinstalled Seamonkey 1.1.14 via new ubuntuzilla-4.6.0-0ubuntu1-i386.deb

And everything went well. My Seamonkey plugins are linked to my Firefox plugins, just like in 4.5.9. Flash and Flashblock work perfectly.

Lookin' good from my end.

Hi
sounds good! thanks for testing! just to confirm, i take it you are using intrepid, right?

---

### Post by PierreDeKat on 2009-01-02
> **nanotube said:**
> Hi,
That's already in existence, it's part of sourceforge release monitoring functionality. so... go to this page:
[https://sourceforge.net/project/showfiles.php?group_id=202789](https://sourceforge.net/project/showfiles.php?group_id=202789)

and click on the "monitor" button next to ubuntuzilla. you will then get notified by email every time a new release is made.

you have to have an account on sourceforge for this to work, of course, but those are free and no-hassle to create.
Okay, super. Yeah, I had to login and study that page for about 10 minutes before I finally saw the little "Monitor" button. But I'm monitoring the package now. ;-)

> **nanotube said:**
> Hi
sounds good! thanks for testing! just to confirm, i take it you are using intrepid, right?
Yep, that's me.

---

### Post by nanotube on 2009-01-02
> **PierreDeKat said:**
> Okay, super. Yeah, I had to login and study that page for about 10 minutes before I finally saw the little "Monitor" button. But I'm monitoring the package now. ;-)


Heh, yea, it's not very easy to find... Where do you think would be the best place to put a direct link to that on the homepage somewhere? I.e., if you were a person looking to sign up for email release notifications, where would you look first? (Since you were in that situation just now, I thought I'd ask for your opinion :) )

---

### Post by Hyper Tails on 2009-01-02
i gotta try it

I can't now because i'm going skiing

---

### Post by nanotube on 2009-01-02
> **Hyper Tails said:**
> i gotta try it

I can't now because i'm going skiing

have fun! please do give your feedback after you have a chance to try. :)

---

### Post by nanotube on 2009-01-06
Latest development version
should now properly support dapper, feisty, gutsy, etc. 
thanks to kansasnoob for the testing thus far. :)

please give it a go and let me know how it went.

---

### Post by kansasnoob on 2009-01-06
First test completed successfully with Ubuntu 8.10!

I was running the "test" version Ubuntuzilla so I began by running:

```
ubuntuzilla.py -a remove -p firefox
```

Then I went to synaptic and chose to "completely" remove Ubuntuzilla. (same as purge & remove)

No problems:

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
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
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US    
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [46.1kB]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [269kB]      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [14.4kB]       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [571B]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [17.9kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [2429B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B]  
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [5049B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [83.2kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1696B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [34.2kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [6708B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 585kB in 5s (104kB/s) 
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-01-06 16:51:42--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9112341 (8.7M)

100%[======================================>] 9,112,341    307K/s   in 29s     

2009-01-06 16:52:12 (305 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--2009-01-06 16:52:12--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 204.246.0.136, 155.98.64.83, 156.56.247.196, ...
Connecting to releases.mozilla.org|204.246.0.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.006s  

2009-01-06 16:52:13 (31.9 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1230843862:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1230843862:0:3:1:5
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

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  nvidia-177-modaliases
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.4kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main nvidia-177-modaliases 177.82-0ubuntu0.1 [18.4kB]
Fetched 18.4kB in 0s (29.4kB/s)            
(Reading database ... 115475 files and directories currently installed.)
Preparing to replace nvidia-177-modaliases 177.80-0ubuntu2 (using .../nvidia-177-modaliases_177.82-0ubuntu0.1_i386.deb) ...
Unpacking replacement nvidia-177-modaliases ...
Setting up nvidia-177-modaliases (177.82-0ubuntu0.1) ...
lance@lance-desktop:~$ 



Well, I showed one "not-upgraded" package that was not related.

Not sure if it's important but I always make sure that Firefox is "closed" when I do these installations. Two ways of doing that: #1: Use either Abiword or Open Office so you can still cut-n-paste commands, or #2: Use Opera browser while you're ding this.

Linux Mint 6 is next, then Mint 5, then Ubuntu 8.04.2, hopefully within 24 hours!

Then the rest of the old stuff! (Dreading Dapper!)

---

### Post by kansasnoob on 2009-01-06
Not so good with Mint 6:

> lance@lance-desktop ~ $ ubuntuzilla.py -a remove -p firefox
If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


[sudo] password for lance: 
Rediverting /usr/bin links to point to the Ubuntu repositories version of Firefox...


Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
All your Firefox shortcuts now point to the Ubuntu repositories version of Firefox .
Would you like to completely delete the Mozilla build of Firefox from your hard drive [y/n]? 
Please enter 'y' or 'n': y
Successfully removed the Mozilla build of Firefox.

Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox? [y/n] 
Please enter 'y' or 'n': y
If you change your mind, you can always go back and enable the automatic update checker by running this script with option '-a installupdater'.
Updater successfully removed from your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop ~ $  sudo apt-get --purge remove ubuntuzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntuzilla*
0 upgraded, 0 newly installed, 1 to remove and 16 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 100575 files and directories currently installed.)
Removing ubuntuzilla ...
Purging configuration files for ubuntuzilla ...
Processing triggers for man-db ...
lance@lance-desktop ~ $ ubuntuzilla.py -a remove -p firefox
If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


rm: cannot remove `/usr/bin/mozilla-firefox': No such file or directory
sudo rm /usr/bin/mozilla-firefox
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1136, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 238, in start
    self.remove()
  File "/usr/local/bin/ubuntuzilla.py", line 615, in remove
    self.removeLaunchLink()
  File "/usr/local/bin/ubuntuzilla.py", line 781, in removeLaunchLink
    self.util.execSystemCommand(executionstring="sudo rm /usr/bin/mozilla-firefox")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
lance@lance-desktop ~ $ 



But, I'm tired so maybe I did a goof!

---

### Post by nanotube on 2009-01-06
> **kansasnoob said:**
> Not so good with Mint 6:

```

ubuntuzilla.py -a remove -p firefox

```

But, I'm tired so maybe I did a goof!

it looks like you are trying to /remove/ rather than /install/? is it possible that you are trying to remove without having installed (i.e., there's nothing to remove?)

---

### Post by nanotube on 2009-01-06
Well, that said, it is a bug if ubuntuzilla doesn't recognize when there's nothing to remove, so i added a check to make sure that something was actually installed by ubuntuzilla before trying to remove it.

So, attaching the latest testing .deb, that includes that extra check. :)

---

### Post by kansasnoob on 2009-01-06
> **nanotube said:**
> Well, that said, it is a bug if ubuntuzilla doesn't recognize when there's nothing to remove, so i added a check to make sure that something was actually installed by ubuntuzilla before trying to remove it.

So, attaching the latest testing .deb, that includes that extra check. :)

Cool. As I thought about it, it was odd that no error showed removing the FF build from Ubuntuzilla, but only Ubuntuzilla itself.

And, while the first time I was using Ubuntu 8.10 and now Mint 6, the first time I used synaptic to remove Ubuntuzilla, where as this time I used  "--purge remove".

Another thought comes to mind. Should I also be trying this with a previous version of Ubuntuzilla installed?

Of course that should come later, because most people installing Ubuntuzilla are not going to have a previous version of Ubuntuzilla installed.

One thing at a time! Right?

I think I should retire for the night ............ I'm silly tired!

As I said before, if I'm way off track don't hessitate to shout! I want to help, not hinder, so feel free to criticize!

---

### Post by kansasnoob on 2009-01-06
> **nanotube said:**
> Well, that said, it is a bug if ubuntuzilla doesn't recognize when there's nothing to remove, so i added a check to make sure that something was actually installed by ubuntuzilla before trying to remove it.

So, attaching the latest testing .deb, that includes that extra check. :)

Oh, and we (I) did add that manual plug-in path in some installattions!

---

### Post by nanotube on 2009-01-06
> **kansasnoob said:**
> 
Another thought comes to mind. Should I also be trying this with a previous version of Ubuntuzilla installed?

Of course that should come later, because most people installing Ubuntuzilla are not going to have a previous version of Ubuntuzilla installed.

One thing at a time! Right?

I think I should retire for the night ............ I'm silly tired!

As I said before, if I'm way off track don't hessitate to shout! I want to help, not hinder, so feel free to criticize!

i'd say, don't worry about that. 99% of people who do use ubuntuzilla to install something use it only once per machine per package. further, the only thing that changes in this release is the plugin path detection... and that only inasmuch as the /method/ of detection changes, the path remains the same. so it shouldn't matter. so yea, don't worry about that bit. :)

thanks for the testing, enjoy your sleep :)

---

### Post by nanotube on 2009-01-06
> **kansasnoob said:**
> Oh, and we (I) did add that manual plug-in path in some installattions!

shouldn't matter when removing, since all that changes is the symlink inside /opt/firefox, which get's summarily deleted upon remove anyway.

---

### Post by kansasnoob on 2009-01-07
> **nanotube said:**
> Well, that said, it is a bug if ubuntuzilla doesn't recognize when there's nothing to remove, so i added a check to make sure that something was actually installed by ubuntuzilla before trying to remove it.

So, attaching the latest testing .deb, that includes that extra check. :)

Just tried this version (from post #69) on 8.04.2 and all went perfectly:

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
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

[sudo] password for lance: 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
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
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--03:05:32--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 156.56.247.196, 204.152.184.113, 149.20.20.5, ...
Connecting to releases.mozilla.org|156.56.247.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9,112,341 (8.7M) (unauthoritative)

100%[====================================>] 9,112,341    301.24K/s    ETA 00:00

03:06:01 (304.95 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--03:06:02--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 149.20.20.5, 64.50.238.52, 64.50.236.214, ...
Connecting to releases.mozilla.org|149.20.20.5|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

03:06:03 (27.81 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1231314931:0:3:1:5
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

gpg: Signature made Mon 15 Dec 2008 08:55:38 PM CST using DSA key ID 17785FE8
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



---

### Post by kansasnoob on 2009-01-07
Rechecked 8.10 just to be sure, first removed mozilla build of Firefox, then removed the prior build of Ubuntuzilla, installed the newest version of Ubuntuzilla (from post #69), and reinstalled Firefox from your script.

All went perfectly:

> lance@lance-desktop:~$ ubuntuzilla.py -a remove -p firefox
If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


[sudo] password for lance: 
Rediverting /usr/bin links to point to the Ubuntu repositories version of Firefox...


Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
All your Firefox shortcuts now point to the Ubuntu repositories version of Firefox .
Would you like to completely delete the Mozilla build of Firefox from your hard drive [y/n]? 
Please enter 'y' or 'n': y
Successfully removed the Mozilla build of Firefox.

Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox? [y/n] 
Please enter 'y' or 'n': y
If you change your mind, you can always go back and enable the automatic update checker by running this script with option '-a installupdater'.
Updater successfully removed from your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ sudo apt-get remove --purge ubuntuzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnotify-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntuzilla*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115472 files and directories currently installed.)
Removing ubuntuzilla ...
Purging configuration files for ubuntuzilla ...
dpkg - warning: while removing ubuntuzilla, directory `/usr/local' not empty so not removed.
Processing triggers for man-db ...
lance@lance-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
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

Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [269kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [5049B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [83.2kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1696B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [34.2kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [6708B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 456kB in 5s (90.2kB/s)
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

--2009-01-07 03:52:03--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 216.165.129.141, 204.152.184.196, 202.177.202.154, ...
Connecting to releases.mozilla.org|216.165.129.141|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9112341 (8.7M)

100%[======================================>] 9,112,341    314K/s   in 30s     

2009-01-07 03:52:33 (301 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--2009-01-07 03:52:33--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.009s  

2009-01-07 03:52:34 (20.9 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1230843862:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1230843862:0:3:1:5
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

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 



---

### Post by kansasnoob on 2009-01-07
Retesting Linux Mint 6, first removing the Mozilla build of Firefox, then removing the older version of Ubuntuzilla, then installing the version of Ubuntuzilla from post #69, then installing the Ubuntuzilla build of Firefox.

A few errors during removal, but it all reinstalled OK. Plug-ins linked properly, etc:

> lance@lance-desktop ~ $ ubuntuzilla.py -a remove -p firefox
If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


[sudo] password for lance: 
rm: cannot remove `/usr/bin/firefox': No such file or directory
sudo rm /usr/bin/firefox
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1136, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 238, in start
    self.remove()
  File "/usr/local/bin/ubuntuzilla.py", line 615, in remove
    self.removeLaunchLink()
  File "/usr/local/bin/ubuntuzilla.py", line 780, in removeLaunchLink
    self.util.execSystemCommand(executionstring="sudo rm /usr/bin/firefox")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
lance@lance-desktop ~ $ sudo apt-get remove --purge ubuntuzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntuzilla*
0 upgraded, 0 newly installed, 1 to remove and 16 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 100575 files and directories currently installed.)
Removing ubuntuzilla ...
Purging configuration files for ubuntuzilla ...
Processing triggers for man-db ...
lance@lance-desktop ~ $ ubuntuzilla.py -a install -p firefox

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
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release.gpg                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Translation-en_US               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Translation-en_US           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US            
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg [189B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release [7817B]                    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release [51.2kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages           
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [46.1kB]
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages [269kB]       
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [17.9kB]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages                        
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages [5049B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages [34.2kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Fetched 482kB in 4s (103kB/s)                         
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-01-07 04:16:38--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... failed: Connection refused.
Connecting to releases.mozilla.org|204.246.0.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9112341 (8.7M)

100%[======================================>] 9,112,341    314K/s   in 30s     

2009-01-07 04:17:09 (299 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--2009-01-07 04:17:09--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.006s  

2009-01-07 04:17:09 (30.3 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1230847192:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1230847192:0:3:1:5
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

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop ~ $ 



---

### Post by kansasnoob on 2009-01-07
Mint 5, no prior installation of the Ubuntuzilla build, so just a straight-forward install using the version from post #69. All went flawlessly, plug-ins linked properly, etc:

> lance@lance-desktop ~ $ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
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
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]               
Get:5 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]                       
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release [7873B]                     
Get:8 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages [4127B]              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [114kB]          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages                     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [402kB]           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages                       
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [7487B]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [49.0kB]    
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [9758B]   
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [7487B]     
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [149kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [24.8kB]
Fetched 900kB in 5s (172kB/s)                             
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--05:06:14--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 216.165.129.141, 204.152.184.196, 202.177.202.154, ...
Connecting to releases.mozilla.org|216.165.129.141|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9,112,341 (8.7M) (unauthoritative)

100%[====================================>] 9,112,341    312.29K/s    ETA 00:00

05:06:44 (309.47 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--05:06:44--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.236.214, 131.188.12.212, 216.165.129.141, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

05:06:44 (17.30 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1231056877:0:3:1:5
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

gpg: Signature made Mon 15 Dec 2008 08:55:38 PM CST using DSA key ID 17785FE8
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
lance@lance-desktop ~ $ 



---

### Post by kansasnoob on 2009-01-07
Ubuntu 7.10 worked great (using the version from post #69). This time I happened to think that even though I don't use Thunderbird or Seamonkey I should perhaps just check. All went flawlessly.

(Hmmmm, I didn't realize that terminal eventually "cuts-off text) In the future I won't bother posting the entire install script unless I see even a potential problem.

>   0. af           1. ar           2. be           3. bg        
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
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
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
0 upgraded, 0 newly installed, 0 to remove and 247 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--07:27:09--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 204.152.184.113, 149.20.20.5, 64.50.238.52, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9,112,341 (8.7M) (unauthoritative)

100%[====================================>] 9,112,341    290.22K/s    ETA 00:00

07:27:41 (285.85 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--07:27:41--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 204.152.184.196, 202.177.202.154, 129.101.198.59, ...
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 204.152.184.196 port 18211: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--07:27:44--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

07:27:45 (14.46 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1231333486:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1231333486:0:3:1:5
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

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.6.0

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 2.0.0.19. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Thunderbird ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. be           2. bg           3. ca        
  4. cs           5. da           6. de           7. el        
  8. en-GB        9. en-US       10. es-AR       11. es-ES     
 12. eu          13. fi          14. fr          15. ga-IE     
 16. he          17. hu          18. it          19. ja        
 20. ko          21. lt          22. mk          23. nb-NO     
 24. nl          25. nn-NO       26. pa-IN       27. pl        
 28. pt-BR       29. pt-PT       30. ru          31. sk        
 32. sl          33. sv-SE       34. tr          35. uk        
 36. zh-CN       37. zh-TW     
Enter your choice of localization (integer, from 0 to 37): 9
You have chosen localization en-US. Is that correct [y/n]? 
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
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done

Making sure that the repositories version of Thunderbird is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 247 not upgraded.
Need to get 11.0MB of archives.
After unpacking 32.8MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main thunderbird 2.0.0.19+nobinonly-0ubuntu0.7.10.1 [11.0MB]
Fetched 11.0MB in 35s (310kB/s)                                                
Selecting previously deselected package thunderbird.
(Reading database ... 90717 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.19+nobinonly-0ubuntu0.7.10.1_i386.deb) ...
Setting up thunderbird (2.0.0.19+nobinonly-0ubuntu0.7.10.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Retrieving package name for Thunderbird ...
Success!: thunderbird-2.0.0.19.tar.gz

Downloading Thunderbird archive from the Mozilla site

--07:55:38--  [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-US/thunderbird-2.0.0.19.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-US/thunderbird-2.0.0.19.tar.gz)
           => `thunderbird-2.0.0.19.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 149.20.20.5, 64.50.238.52, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.19.tar.gz ... done.
Length: 11,484,804 (11M) (unauthoritative)

100%[====================================>] 11,484,804   287.67K/s    ETA 00:00

07:56:19 (280.13 KB/s) - `thunderbird-2.0.0.19.tar.gz' saved [11484804]


Downloading Thunderbird signature from the Mozilla site

--07:56:19--  [ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-US/thunderbird-2.0.0.19.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-US/thunderbird-2.0.0.19.tar.gz.asc)
           => `thunderbird-2.0.0.19.tar.gz.asc'
Resolving releases.mozilla.org... 149.20.20.5, 64.50.238.52, 64.50.236.214, ...
Connecting to releases.mozilla.org|149.20.20.5|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/2.0.0.19/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR thunderbird-2.0.0.19.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

07:56:20 (3.88 KB/s) - `thunderbird-2.0.0.19.tar.gz.asc' saved [186]

tru::1:1231333486:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1231333486:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2009-07-16::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2009-07-16:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2009-07-16:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Tue 30 Dec 2008 01:31:48 AM CST using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8

Linking dictionaries


Linking launcher to new thunderbird

Adding `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'
Adding `local diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu'

The new Thunderbird version 2.0.0.19 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Thunderbird (recommended)? This feature will regularly check for updates to Thunderbird, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.6.0

This script installs the latest release of the official Mozilla build of Seamonkey on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be 1.1.14. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y

Old Seamonkey preferences not found. Nothing to back up. Proceeding with installation.


Downloading Seamonkey archive from the Mozilla site

--07:57:43--  [ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.14/seamonkey-1.1.14.en-US.linux-i686.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.14/seamonkey-1.1.14.en-US.linux-i686.tar.gz)
           => `seamonkey-1.1.14.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 149.20.20.5, 64.50.238.52, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.14 ... done.
==> PASV ... done.    ==> RETR seamonkey-1.1.14.en-US.linux-i686.tar.gz ... done.
Length: 14,819,360 (14M) (unauthoritative)

100%[====================================>] 14,819,360   293.47K/s    ETA 00:00

07:58:34 (286.92 KB/s) - `seamonkey-1.1.14.en-US.linux-i686.tar.gz' saved [14819360]


Downloading Seamonkey MD5 sums from the Mozilla site

wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -O - [ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.14/MD5SUMS](ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.14/MD5SUMS) | grep 'linux-i686.tar.gz' > seamonkey-1.1.14.en-US.linux-i686.tar.gz.md5
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.

Verifying Seamonkey MD5 sum

./seamonkey-1.1.14.en-US.linux-i686.tar.gz: OK
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 1.1.14 has been installed successfully.

If you are looking to use Seamonkey in other languages, head over to [http://www.mozilla.org/projects/seamonkey/releases/#l10n](http://www.mozilla.org/projects/seamonkey/releases/#l10n) and download the installable language pack of your choice.

Would you like to set up automatic update checking for the official Mozilla build of Seamonkey (recommended)? This feature will regularly check for updates to Seamonkey, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 



---

### Post by kansasnoob on 2009-01-07
No problem with Mint 4. I did this one from the Live CD. I am going to show the full output from terminal because I specifically want to try the uninstall option afterwards:

> mint@mint:~$ ubuntuzilla.py -a install -p firefox

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
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna Release.gpg                                
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/main Translation-en_US                     
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]               
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/import Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Get:6 [http://www.linuxmint.com](http://www.linuxmint.com) daryna Release [5202B]                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release [58.5kB]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/main Packages                              
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream Packages                          
Ign [http://www.linuxmint.com](http://www.linuxmint.com) daryna/import Packages                            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [130kB]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [11.7kB]                     
Get:10 [http://www.linuxmint.com](http://www.linuxmint.com) daryna/main Packages [1474B]                   
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages [300kB]           
Get:12 [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream Packages [6356B]               
Get:13 [http://www.linuxmint.com](http://www.linuxmint.com) daryna/import Packages [4286B]                 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [5736B]   
Get:15 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages [8443B]               
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [89.6kB]    
Get:17 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages [3731B]           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages [6059B]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [8260B]   
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [114kB]       
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [12.4kB]    
Get:22 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:23 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]
Get:24 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [1650B]
Fetched 834kB in 5s (160kB/s)   
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-gnome-support libpango1.0-0 libpango1.0-common
Suggested packages:
  latex-xft-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-thryomanes ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp
Recommended packages:
  ubufox
The following packages will be upgraded:
  firefox firefox-gnome-support libpango1.0-0 libpango1.0-common
4 upgraded, 0 newly installed, 0 to remove and 253 not upgraded.
Need to get 9694kB of archives.
After unpacking 90.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firefox-gnome-support firefox
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libpango1.0-common 1.18.3-0ubuntu1 [63.5kB]
Get:2 [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream firefox-gnome-support 2.0.16+1nobinonly-1mint1 [91.2kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libpango1.0-0 1.18.3-0ubuntu1 [293kB]
Get:4 [http://www.linuxmint.com](http://www.linuxmint.com) daryna/upstream firefox 2.0.16+1nobinonly-1mint1 [9246kB]
Fetched 9694kB in 1m23s (116kB/s)                                              
(Reading database ... 87073 files and directories currently installed.)
Preparing to replace libpango1.0-common 1.18.2-0ubuntu1 (using .../libpango1.0-common_1.18.3-0ubuntu1_all.deb) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Unpacking replacement libpango1.0-common ...
Preparing to replace libpango1.0-0 1.18.2-0ubuntu1 (using .../libpango1.0-0_1.18.3-0ubuntu1_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
Preparing to replace firefox-gnome-support 2.0.06-mint2 (using .../firefox-gnome-support_2.0.16+1nobinonly-1mint1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox 2.0.06-mint2 (using .../firefox_2.0.16+1nobinonly-1mint1_i386.deb) ...
Unpacking replacement firefox ...
Setting up libpango1.0-common (1.18.3-0ubuntu1) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Updating font configuration of pango...
Cleaning up category xfont..
Updating category xfont..

Setting up libpango1.0-0 (1.18.3-0ubuntu1) ...

Setting up firefox (2.0.16+1nobinonly-1mint1) ...
Please restart any running Firefoxes, or you will experience problems.

Setting up firefox-gnome-support (2.0.16+1nobinonly-1mint1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Backing up old Firefox preferences

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--14:38:27--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 216.165.129.141, 204.152.184.196, 202.177.202.154, ...
Connecting to releases.mozilla.org|216.165.129.141|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9,112,341 (8.7M) (unauthoritative)

100%[====================================>] 9,112,341    312.27K/s    ETA 00:00

14:38:57 (309.32 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--14:38:57--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 202.177.202.154, 129.101.198.59, 64.50.236.52, ...
Connecting to releases.mozilla.org|202.177.202.154|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... couldn't connect to 202.177.202.154 port 6625: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--14:39:01--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

14:39:05 (12.60 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

gpg: directory `/home/mint/.gnupg' created
gpg: new configuration file `/home/mint/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/mint/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/mint/.gnupg/pubring.gpg' created
gpg: /home/mint/.gnupg/trustdb.gpg: trustdb created
tru::1:1231339146:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: keyring `/home/mint/.gnupg/secring.gpg' created
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

gpg: Signature made Tue 16 Dec 2008 02:55:38 AM UTC using DSA key ID 17785FE8
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
no crontab for mint
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
mint@mint:~$ 



---

### Post by kansasnoob on 2009-01-07
No problem reverting in Mint 4 either That's something I want to revisit in Mint 5 & 6. I can't imagine why anyone would want to revert, but just in case:

> mint@mint:~$ ubuntuzilla.py -a remove -p firefox
If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


Rediverting /usr/bin links to point to the Ubuntu repositories version of Firefox...


Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
All your Firefox shortcuts now point to the Ubuntu repositories version of Firefox .
Would you like to completely delete the Mozilla build of Firefox from your hard drive [y/n]? 
Please enter 'y' or 'n': y
Successfully removed the Mozilla build of Firefox.

Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox? [y/n] 
Please enter 'y' or 'n': y
If you change your mind, you can always go back and enable the automatic update checker by running this script with option '-a installupdater'.
Updater successfully removed from your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
mint@mint:~$ 



---

### Post by nanotube on 2009-01-07
Hi
Thanks for all the testing, looks great! :)
It seems that this version is ready for release... what do you think?

---

### Post by kansasnoob on 2009-01-07
And Dapper still works (it still drives me nuts too). I'll try within the next 24 hours or so to check the "remove" option in Mint 5 & 6.

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': n

If no version shows, or it does not agree with the latest version as listed on [http://www.mozilla.org](http://www.mozilla.org), please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) and let us know.
In the meantime, if you want to proceed with installation, you have the option of looking up the latest version yourself on the [http://www.mozilla.org/](http://www.mozilla.org/) website, and entering it here by hand.

Please enter the latest version of Firefox: 2.0.0.20
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
 40. sv-SE       41. tr          42. uk          43. zh-CN
 44. zh-TW
Enter your choice of localization (integer, from 0 to 44): 10
You have chosen localization en-US. Is that correct [y/n]?
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 1s (3B/s)
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-2.0.0.20.tar.gz

Downloading Firefox archive from the Mozilla site

--11:26:55--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz)
           => `firefox-2.0.0.20.tar.gz'
Resolving releases.mozilla.org... 64.50.236.52, 64.50.238.52, 64.50.236.214, ...Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.20.tar.gz ... done.
Length: 9,710,348 (9.3M) (unauthoritative)

100%[====================================>] 9,710,348    312.40K/s    ETA 00:00

11:27:26 (306.22 KB/s) - `firefox-2.0.0.20.tar.gz' saved [9710348]


Downloading Firefox signature from the Mozilla site

--11:27:26--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US/firefox-2.0.0.20.tar.gz.asc)
           => `firefox-2.0.0.20.tar.gz.asc'
Resolving releases.mozilla.org... 64.50.236.52, 64.50.238.52, 64.50.236.214, ...Connecting to releases.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0.0.20/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-2.0.0.20.tar.gz.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s

11:27:27 (24.06 KB/s) - `firefox-2.0.0.20.tar.gz.asc' saved [186]

gpg: directory `/home/lance/.gnupg' created
gpg: new configuration file `/home/lance/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/lance/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/lance/.gnupg/pubring.gpg' created
gpg: /home/lance/.gnupg/trustdb.gpg: trustdb created
tru::1:1231349247:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: keyring `/home/lance/.gnupg/secring.gpg' created
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: key 812347DD: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 2
gpg:               imported: 2
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Thu 18 Dec 2008 02:09:52 AM CST using DSA key ID 17785FE8
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

The new Firefox version 2.0.0.20 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n]
Please enter 'y' or 'n': y
no crontab for lance
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$



---

### Post by nanotube on 2009-01-07
> **kansasnoob said:**
> And Dapper still works (it still drives me nuts too). I'll try within the next 24 hours or so to check the "remove" option in Mint 5 & 6.

sounds good. thanks for being so thorough! :)

---

### Post by nanotube on 2009-01-07
Hi
added a few extra sanity checks during remove
so when you test the removes, could you please use this latest ubuntuzilla version, attached to this post? 
just install this .deb over the old ubuntuzilla, and then use the ubuntuzilla remove command to remove.

---

### Post by kansasnoob on 2009-01-07
> **nanotube said:**
> Hi
added a few extra sanity checks during remove
so when you test the removes, could you please use this latest ubuntuzilla version, attached to this post? 
just install this .deb over the old ubuntuzilla, and then use the ubuntuzilla remove command to remove.

Ah, will do, but I just did a clean install of Mint 6 (it was needed for unrelated reasons anyway) and installed the Ubuntuzilla version of Mozilla Firefox from post #69, then I did a removal and it all worked fine:

> lance@lance-desktop ~ $ ubuntuzilla.py -a remove -p firefox
If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


Rediverting /usr/bin links to point to the Ubuntu repositories version of Firefox...


Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
All your Firefox shortcuts now point to the Ubuntu repositories version of Firefox .
Would you like to completely delete the Mozilla build of Firefox from your hard drive [y/n]? 
Please enter 'y' or 'n': y
Successfully removed the Mozilla build of Firefox.

Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox? [y/n] 
Please enter 'y' or 'n': y
If you change your mind, you can always go back and enable the automatic update checker by running this script with option '-a installupdater'.
Updater successfully removed from your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop ~ $ 


That old Mint 6 had been played with and modified to heck and gone, and at one point after reverting to the Ubuntu/Mint version of Firefox I got a "can't launch ......... blah, blah ..... child process", and I wanted to be sure that was just a glitch related to an over-modified install.

Anyway, reverting worked fine, Firefox launched fine, etc.

I'll try the new one right now though.

---

### Post by kansasnoob on 2009-01-07
I used the newest one both to install and remove. Worked great! Made sure Firefox launched in both scenarios! Plug-ins properly linked, etc.

Great work! I've tried even the previous version (from post #69) to install and remove from Mint 4 and Mint 6. I'll still give Mint 5 a double check a little later, but I think you're good to go!

Dapper was by far the most fiddly to work with, but I've always had heaps of trouble with Dapper!

---

### Post by kansasnoob on 2009-01-07
Oops you might want to see the output:

> lance@lance-desktop ~ $ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

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

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release.gpg                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Translation-en_US               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Translation-en_US           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Translation-en_US             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release [7817B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
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
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages  
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages
Fetched 7817B in 2s (2753B/s)                            
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  localechooser-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-01-07 14:20:44--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 204.152.184.196, 202.177.202.154, 129.101.198.59, ...
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... couldn't connect to 204.152.184.196 port 56802: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--2009-01-07 14:20:46--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2 ... 9112341
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9112341 (8.7M)

100%[======================================>] 9,112,341    223K/s   in 35s     

2009-01-07 14:21:23 (252 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--2009-01-07 14:21:23--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 64.50.236.52, 204.246.0.136, 155.98.64.83, ...
Connecting to releases.mozilla.org|64.50.236.52|:21... failed: Connection refused.
Connecting to releases.mozilla.org|204.246.0.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> SIZE firefox-3.0.5.tar.bz2.asc ... 186
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186

100%[======================================>] 186         --.-K/s   in 0.004s  

2009-01-07 14:21:24 (42.0 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1231358042:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1231358042:0:3:1:5
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

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.0.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop ~ $ ubuntuzilla.py -a remove -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now remove the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


Rediverting /usr/bin links to point to the Ubuntu repositories version of Firefox...


Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
All your Firefox shortcuts now point to the Ubuntu repositories version of Firefox .
Would you like to completely delete the Mozilla build of Firefox from your hard drive [y/n]? 
Please enter 'y' or 'n': y
Successfully removed the Mozilla build of Firefox.

Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox? [y/n] 
Please enter 'y' or 'n': y
If you change your mind, you can always go back and enable the automatic update checker by running this script with option '-a installupdater'.
Updater successfully removed from your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.


I like this bit, "Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)".

---

### Post by nanotube on 2009-01-07
> **kansasnoob said:**
> 
I used the newest one both to install and remove. Worked great! Made sure Firefox launched in both scenarios! Plug-ins properly linked, etc.

Great work! I've tried even the previous version (from post #69) to install and remove from Mint 4 and Mint 6. I'll still give Mint 5 a double check a little later, but I think you're good to go!


excellent :) i'll make the release, then. 

> 
Dapper was by far the most fiddly to work with, but I've always had heaps of trouble with Dapper! 

what happened with dapper? did ubuntuzilla have any problems?

> 
I like this bit, "Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)".
:)

---

### Post by nanotube on 2009-01-07
ubuntuzilla 4.6.0 is released. :)
thanks kansasnoob for all the help with testing!

---

### Post by kansasnoob on 2009-01-07
Sorry I took so long, I got wrapped up in other things.

Mint 5 went flawlessly, both installing and removing!

> lance@lance-desktop ~ $ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
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

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Translation-en_US  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release [7873B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages                    
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages                     
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Fetched 7873B in 7s (993B/s)                                                   
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libdns32 localechooser-data libisc32
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.0.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--18:02:19--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2)
           => `firefox-3.0.5.tar.bz2'
Resolving releases.mozilla.org... 64.50.236.214, 131.188.12.212, 216.165.129.141, ...
Connecting to releases.mozilla.org|64.50.236.214|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2 ... done.
Length: 9,112,341 (8.7M) (unauthoritative)

100%[====================================>] 9,112,341    312.34K/s    ETA 00:00

18:02:48 (309.90 KB/s) - `firefox-3.0.5.tar.bz2' saved [9112341]


Downloading Firefox signature from the Mozilla site

--18:02:48--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US/firefox-3.0.5.tar.bz2.asc)
           => `firefox-3.0.5.tar.bz2.asc'
Resolving releases.mozilla.org... 155.98.64.83, 156.56.247.196, 204.152.184.113, ...
Connecting to releases.mozilla.org|155.98.64.83|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.0.5/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.0.5.tar.bz2.asc ... done.
Length: 186 (unauthoritative)

100%[====================================>] 186           --.--K/s             

18:02:49 (1.94 KB/s) - `firefox-3.0.5.tar.bz2.asc' saved [186]

tru::1:1231365447:0:3:1:5
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

gpg: Signature made Mon 15 Dec 2008 08:55:38 PM CST using DSA key ID 17785FE8
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
lance@lance-desktop ~ $ ubuntuzilla.py -a remove -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now remove the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

If the original Ubuntu repositories version of Firefox is a full version number older than the installed Mozilla build (e.g., 1.5 vs. 2.0), your profile may now be incompatible with the older Firefox version. If that happens, you can restore the backup profile that was made when you installed the Mozilla build.
Are you sure you want to remove the official Mozilla build of Firefox , and revert to the Ubuntu repositories version [y/n]? 
Please enter 'y' or 'n': y
Removing /usr/bin links to the Mozilla build of Firefox...


Rediverting /usr/bin links to point to the Ubuntu repositories version of Firefox...


Removing `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
All your Firefox shortcuts now point to the Ubuntu repositories version of Firefox .
Would you like to completely delete the Mozilla build of Firefox from your hard drive [y/n]? 
Please enter 'y' or 'n': y
Successfully removed the Mozilla build of Firefox.

Are you sure you want to disable automatic update checking for the official Mozilla build of Firefox? [y/n] 
Please enter 'y' or 'n': y
If you change your mind, you can always go back and enable the automatic update checker by running this script with option '-a installupdater'.
Updater successfully removed from your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop ~ $ 



---

### Post by kansasnoob on 2009-01-07
> **nanotube said:**
> excellent :) i'll make the release, then. 


what happened with dapper? did ubuntuzilla have any problems?


:)

No problem with Ubuntuzilla and Dapper. Dapper has always been difficult for me to obtain a readable resolution. I can always get it worked out, but I'm legally blind and it's a major pain in the butt!

That and with both Gutsy and Dapper it always begins with:
"Error: Dependency is not satisfiable: libnotify-bin .....".

Which is easily resolved if you can see what you're doing:)

It's just a matter of enabling another repo or two and then your installer does the rest of the work.

Anyway, thanks for all the hard work. It's great to be able to use this with Ubuntu and Mint!

---

### Post by nanotube on 2009-01-07
thanks for your help with this release. :)
I hope you don't mind if i tag you for some testing if there's need for another release. :)

---

### Post by kansasnoob on 2009-01-08
> **nanotube said:**
> thanks for your help with this release. :)
I hope you don't mind if i tag you for some testing if there's need for another release. :)

Any time!

Many thanks to you for the great new release!

---

### Post by PierreDeKat on 2009-01-09
Okay, running Intrepid, and I just
1) downloaded ubuntuzilla-4.6.1-0ubuntu1-i386.deb to my /home/ directory
2) uninstalled Seamonkey 1.1.14 via earlier ubuntuzilla-4.6.0-0ubuntu1-i386.deb
3) verified /opt/seamonkey folder was gone
4) uninstalled ubuntuzilla-4.6.0-0ubuntu1-i386.deb via Synaptic
5) installed ubuntuzilla-4.6.1-0ubuntu1-i386.deb by double-clicking on the downloaded file
6) reinstalled Seamonkey 1.1.14 via new ubuntuzilla-4.6.1-0ubuntu1-i386.deb

And everything went well. My Seamonkey plugins are linked to my Firefox plugins, just like in the last two versions. And both Flash and Flashblock work perfectly.

---

### Post by nanotube on 2009-01-10
> **PierreDeKat said:**
> Okay, running Intrepid, and I just
1) downloaded ubuntuzilla-4.6.1-0ubuntu1-i386.deb to my /home/ directory
2) uninstalled Seamonkey 1.1.14 via earlier ubuntuzilla-4.6.0-0ubuntu1-i386.deb
3) verified /opt/seamonkey folder was gone
4) uninstalled ubuntuzilla-4.6.0-0ubuntu1-i386.deb via Synaptic
5) installed ubuntuzilla-4.6.1-0ubuntu1-i386.deb by double-clicking on the downloaded file
6) reinstalled Seamonkey 1.1.14 via new ubuntuzilla-4.6.1-0ubuntu1-i386.deb

And everything went well. My Seamonkey plugins are linked to my Firefox plugins, just like in the last two versions. And both Flash and Flashblock work perfectly.

excellent news, thanks for the update! :)

---

### Post by nanotube on 2009-07-23
Just ripped out the old kludgy chunk of code for sending notifications, replaced with code using python dbus interface.

the release candidate for the new version is posted in this bug tracker item:
[https://sourceforge.net/tracker/?func=detail&aid=2825626&group_id=202789&atid=982990](https://sourceforge.net/tracker/?func=detail&aid=2825626&group_id=202789&atid=982990)

Please give it a testing.

Specifically would be nice if someone who hasn't yet upgraded to ff 3.5.1 would install this, and wait and see if the update notification comes up.

---

### Post by nanotube on 2009-07-27
i added the display of actual language names to the localization choice process, since just the codes can be confusing (at least a couple of times people got uk=ukranian instead of en-GB for UK english).

Here are the release candidates for this next version - would appreciate some testing before i push it out to the world.

---

### Post by joes7 on 2009-12-08
I will definitely help. This is a marvelous project, well done.

---

### Post by nanotube on 2009-12-08
> **joes7 said:**
> I will definitely help. This is a marvelous project, well done.

Great, thanks for the help offer! :) I'll be sure to ping you next time some testing is needed. :)

---

### Post by nanotube on 2009-12-23
I am playing around at packaging the actual mozilla binaries into .deb and making them available in a repository.

to that end, I have created a repository with the latest firefox, thunderbird, and seamonkey. 

Would appreciate if it receives some testing. Note that there are only packages for i386 (32bit), and only en-US localization. (try grabbing and installing the non-english .xpis from here:
[ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.6/linux-i686/xpi/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.6/linux-i686/xpi/))

Here are the instructions to test:

Add the repository to your sources.list:
```
echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null

```

Add the package signing key to your keyring: 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

Update the repository database:
```
sudo apt-get update
```

Now you can try installing packages 'firefox', 'thunderbird', and 'seamonkey', which should be coming through as the currently-latest versions (3.5.6, 3.0, and 2.0.1, respectively). 

Give them a try and... see how it goes. 

They should be coming in with the applications menu items, the symlinks in /usr/bin, and the rest of the files located in /opt/<package>/

Thanks in advance to all testers! :)

---

### Post by kansasnoob on 2009-12-23
I had never added a repo in that manner, that's slick:

```
lance@lance-desktop:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
lance@lance-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe
**deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main**
lance@lance-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for lance: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
lance@lance-desktop:~$ 

```

I'll now update and see what happens. Just BTW this is Karmic with no previous version of Ubuntuzilla, only the official repo version of Firefox, no Seamonkey, and no Thunderbird.

---

### Post by kansasnoob on 2009-12-23
No errors running updates. I didn't think at first to check the full version info of Firefox so I went to synaptic afterwards and disabled the Ubuntuzilla repo then:

[ATTACH]140975[/ATTACH]

After enabling the Ubuntuzilla repo:

[ATTACH]140978[/ATTACH]

So 3.5.6-0ubuntu1 (stable) is added to the available versions but no automatic update or change is triggered.

I'll try choosing to force that version just to see what happens. (I'll be sure Firefox is shutdown first).

---

### Post by kansasnoob on 2009-12-23
Trying to force that version produces an error:

> E: /var/cache/apt/archives/firefox_3.5.6-0ubuntu1_i386.deb: trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package firefox-3.5-branding 0

So I still have the official repo version.

---

### Post by kansasnoob on 2009-12-23
Now Seamonkey shows up very nicely:

[ATTACH]140979[/ATTACH]

Installing via terminal worked flawlessly:

```
lance@lance-desktop:~$ sudo apt-get install seamonkey
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  seamonkey
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main seamonkey 2.0.1-0ubuntu1 [14.5MB]
Fetched 14.5MB in 24s (588kB/s)                                                
Selecting previously deselected package seamonkey.
(Reading database ... 159841 files and directories currently installed.)
Unpacking seamonkey (from .../seamonkey_2.0.1-0ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Setting up seamonkey (2.0.1-0ubuntu1) ...
lance@lance-desktop:~$ 

```

Seamonkey launched perfectly and all plugins appear to have linked properly. I actually tried the flash plugin just to see.

Not sure what "libnspr4-dev" is, but I hadn't run "-f install" recently so it may just be a residual from updates, etc. BTW in Karmic I'm testing proposed updates and also using Xorg crack repos to try and solve some bugs.

---

### Post by kansasnoob on 2009-12-23
Thunderbird is also a big winner:

[ATTACH]140980[/ATTACH]

```
lance@lance-desktop:~$ sudo apt-get install thunderbird
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main thunderbird 3.0-0ubuntu1 [12.0MB]
Fetched 12.0MB in 20s (589kB/s)                                                
Selecting previously deselected package thunderbird.
(Reading database ... 160224 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_3.0-0ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Setting up thunderbird (3.0-0ubuntu1) ...
lance@lance-desktop:~$ 

```

I've never actually used Thinderbird so I don't know what else to look for but it appears to have been successful.

---

### Post by kansasnoob on 2009-12-23
Using an 8.04.3 Live CD looks good so far:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
ubuntu@ubuntu:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1) hardy/restricted Translation-en_US
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://archive.ubuntu.com hardy Release.gpg                      
Ign http://archive.ubuntu.com hardy/main Translation-en_US           
Get:2 http://switch.dl.sourceforge.net all Release.gpg [197B]        
Ign http://switch.dl.sourceforge.net all/main Translation-en_US      
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Get:3 http://security.ubuntu.com hardy-security Release [58.5kB]     
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US         
Get:4 http://archive.ubuntu.com hardy-updates Release.gpg [189B]         
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US 
Hit http://archive.ubuntu.com hardy Release                              
Get:5 http://switch.dl.sourceforge.net all Release [961B]                      
Get:6 http://archive.ubuntu.com hardy-updates Release [58.5kB]            
Ign http://switch.dl.sourceforge.net all/main Packages                         
Get:7 http://switch.dl.sourceforge.net all/main Packages [840B]                
Get:8 http://security.ubuntu.com hardy-security/main Packages [219kB]      
Hit http://archive.ubuntu.com hardy/main Packages          
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/main Sources      
Hit http://archive.ubuntu.com hardy/restricted Sources
Get:9 http://archive.ubuntu.com hardy-updates/main Packages [489kB]
Get:10 http://security.ubuntu.com hardy-security/restricted Packages [9949B]
Get:11 http://security.ubuntu.com hardy-security/main Sources [34.1kB]         
Get:12 http://security.ubuntu.com hardy-security/restricted Sources [946B]     
Get:13 http://archive.ubuntu.com hardy-updates/restricted Packages [9914B]     
Get:14 http://archive.ubuntu.com hardy-updates/main Sources [119kB]
Get:15 http://archive.ubuntu.com hardy-updates/restricted Sources [946B]
Fetched 1002kB in 4s (210kB/s)                     
Reading package lists... Done
ubuntu@ubuntu:~$ 


```

Of course I'll report more when I know more :)

---

### Post by kansasnoob on 2009-12-23
It may be tomorrow when I get back to this.

I decided to actually install 8.04.3 because it'll be helpful with testing grub2 (I'm trying to get the devs to bump an update in Karmic) and also I need to check out some proposed updates for 8.04.4 before the iso testing release.

It did appear that going from 3.0 to 3.5 in Hardy was going to work well, but be patient! I also want to see if this helped with the plugin path in Seamonkey.

I think this looks very promising.

---

### Post by nanotube on 2009-12-23
> **kansasnoob said:**
> Trying to force that version produces an error:



So I still have the official repo version.

good to see that thunderbird and seamonkey work without any trouble.

as to the firefox conflict on the icon... well, try uninstalling the branding package and then installing firefox again. if that works, then we'll think about what to do. 

(either rename the file from firefox.desktop to mozilla.firefox.desktop or some such, or have the package conflict with the branding package. i'm kind of leaning toward the first, because then i won't have to do any version-specific conflict resolution. which probably suggests i should make thunderbird and seamonkey .desktop files also mozilla.<package>.desktop...)

> 
I had never added a repo in that manner, that's slick:

glad you like :)

---

### Post by kansasnoob on 2009-12-24
Similar error upgrading Firefox in Hardy:

```
lance@lance-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives.
After this operation, 123kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102220 files and directories currently installed.)
Preparing to replace firefox 3.0.16+nobinonly-0ubuntu0.8.04.1 (using .../firefox_3.5.6-0ubuntu1_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_3.5.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_3.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lance@lance-desktop:~$ 

```

I'll try removing Firefox first and see what happens.

---

### Post by kansasnoob on 2009-12-24
Maybe some helpful info here, I first tried just purging firefox-3.0:

```
lance@lance-desktop:~$ sudo apt-get purge --remove firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox
The following packages will be REMOVED:
  firefox-3.0* firefox-3.0-gnome-support* firefox-gnome-support*
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives.
After this operation, 4088kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102219 files and directories currently installed.)
Removing firefox-gnome-support ...
Removing firefox-3.0-gnome-support ...
(Reading database ... 102213 files and directories currently installed.)
Preparing to replace firefox 3.0.16+nobinonly-0ubuntu0.8.04.1 (using .../firefox_3.5.6-0ubuntu1_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_3.5.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_3.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then:

```
lance@lance-desktop:~$ sudo apt-get purge --remove firefox firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox* firefox-3.0* ubufox*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 4018kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102212 files and directories currently installed.)
Removing ubufox ...
Removing firefox ...
Removing firefox-3.0 ...
Purging configuration files for firefox-3.0 ...
lance@lance-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package firefox.
(Reading database ... 102093 files and directories currently installed.)
Unpacking firefox (from .../firefox_3.5.6-0ubuntu1_i386.deb) ...
Setting up firefox (3.5.6-0ubuntu1) ...
lance@lance-desktop:~$ 


```

So that appears to have succeeded but not so good with plugins maybe:

```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No

```

I'll study this a bit more. I may be in and out quite a bit the rest of today and even tomorrow.

---

### Post by kansasnoob on 2009-12-24
Installing Seamonkey works flawlessly in Hardy. Plugins linked great. Of course I had no prior Seamonkey installed.  

In Firefox it appears that reinstalling ubufox helped with plugins if that tells you anything.

Thunderbird is a different story;

```
lance@lance-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  language-support-en language-support-translations-en
  thunderbird-locale-en-gb
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After this operation, 1032kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

I didn't think removing those language packs would be a good idea.

---

### Post by nanotube on 2009-12-24
ok so... just to avoid any confusion, then, i'll rename the .desktop files.

don't know what's going on with thunderbird and language packs - my thunderbird .deb has no dependencies on anything, so it shouldn't be conflicting with anything... i'll have to take a look at that.

---

### Post by nanotube on 2009-12-24
> **kansasnoob said:**
> 
In Firefox it appears that reinstalling ubufox helped with plugins if that tells you anything.

hrm... guess i could recommend its installation...

> 
Thunderbird is a different story;

```
lance@lance-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  language-support-en language-support-translations-en
  thunderbird-locale-en-gb
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After this operation, 1032kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

I didn't think removing those language packs would be a good idea.

yea, so i tracked this down in the hardy repos.
language-support-en depends on language-support-translations-en
all well and good.

but language-support-translations-en for some reason has a hard-depend on thunderbird-locale-en-gb, and

thunderbird-locale-en-gb has the following:
```

Depends: thunderbird | language-support-en
Conflicts: thunderbird (<< 1.99), thunderbird (>> 2.0.0.z999)

```

and this latter line is what drives the conflict, which propagates all the way up to language-support-en.

no clue why they did that way in hardy (but apparently not in the later versions, at least). but given the hard conflict with thunderbird versions other than 2.0.0.x, there's nothing i can do other than rename the package to something other than 'thunderbird'. which i'm not sure i'm going to do, just to placate the weird (and unnecessary, imho) dependencies and conflicts that seem to be specific to hardy...

well, and that's the news. ...

EDIT: and i also updated the packages to use mozilla.<package>.desktop for the menu item filename, to avoid the conflicts. so give the firefox package another go with that to see if it doesn't complain anymore :)

EDIT2: another possible solution for hardy: i can just stick up a modified language-support-translations-en package just for hardy, which lacks the dependency on that thunderbird-locale-en-gb. so the hardy users would get that package updated along with thunderbird, and all would be fine and dandy. thoughts on this solution?

---

### Post by kansasnoob on 2009-12-25
> EDIT: and i also updated the packages to use mozilla.<package>.desktop for the menu item filename, to avoid the conflicts. so give the firefox package another go with that to see if it doesn't complain anymore

Well in Karmic I backed out of everything just to be sure Seamonkey and Thunderbird still worked properly and they do, but still problems with Firefox.

As I said since it already has Firefox 3.5.6 it actually regards your package as a downgrade and if I try to force install:

```
E: /var/cache/apt/archives/firefox_3.5.6-0ubuntu1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox-3.5 0

```

Now, it will install if I first remove firefox-3.5 which also removes firefox, firefox-3.5-branding, and ubufox. Then after doing so it shows that those packages need to be updated/installed.

> EDIT2: another possible solution for hardy: i can just stick up a modified language-support-translations-en package just for hardy, which lacks the dependency on that thunderbird-locale-en-gb. so the hardy users would get that package updated along with thunderbird, and all would be fine and dandy. thoughts on this solution?

Sounds like it's worth a try.

Reminds me though, I need to make some tweaks to xorg in Hardy. It's funny how these releases we once regarded as great seem downright prehistoric after a year or so.

---

### Post by kansasnoob on 2009-12-25
Oh, something minor I keep forgetting to mention, the icons/launchers look weird with your Firefox package installed. In Karmic the menu icon looks OK, but when dropped to the panel it looks like a red X in a box.

In Hardy the icon looks like a piece of paper with one corner folded up both in the menu and in the panel.

The ones for Seamonkey look normal in both.

---

### Post by nanotube on 2009-12-28
hrm, i'll look into the icons

as to the packages, maybe i should just name the packages "mozilla.org.<package>", or something, so that the existing packages in the repos don't care about them... 

anyway, i'll post back when i have something for you. :)

---

### Post by nanotube on 2009-12-28
ok

i think i've fixed the icons.

also, i renamed all packages to "<package>.mozilla.build", to avoid any conflicts with existing packages, and added the dpkg diversions of ubuntu-repo package /usr/bin links to /usr/bin/<package>.ubuntu.

about the diversion:
so now, if you have ubuntu repos firefox installed, and then install the mozilla version "firefox.mozilla.build" from my repository, it won't touch the ubuntu firefox install, only redirect its /usr/bin/firefox to /usr/bin/firefox.ubuntu, and then put its own /usr/bin/firefox in its place.

same deal for existing ubuntu-repo installs of thunderbird and seamonkey.

please give them all a try and see how it works, and whether you run into any problems. i think staying out of the ubuntu repositories' way is the safest and least-impact approach.

(note that if you already have an ubuntuzilla-install of a package, which has already done a dpkg-divert, it will conflict with the new packages' divert. so have to run ubuntuzilla.py -a remove before these will install - as i learned from my testing. let me know if this is also the case for you, if you happen to run into this.)

hope it all works this time :)

---

### Post by kansasnoob on 2009-12-29
I'll probably get on with the testing this PM.

I'm busy fighting automotive problems at the moment.

---

### Post by nanotube on 2009-12-29
> **kansasnoob said:**
> I'll probably get on with the testing this PM.

sounds good - thanks for all your help!

> 
I'm busy fighting automotive problems at the moment.
that always sucks... best of luck on that...

---

### Post by kansasnoob on 2009-12-29
I'm just going to give this a try but noticed this:

> (note that if you already have an ubuntuzilla-install of a package, which has already done a dpkg-divert, it will conflict with the new packages' divert. so have to run ubuntuzilla.py -a remove before these will install - as i learned from my testing. let me know if this is also the case for you, if you happen to run into this.)

I just wanted to say that during my last testing instead of:

```
ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py -a remove -p thunderbird
ubuntuzilla.py -a remove -p seamonkey

```

I just ran:

```
sudo apt-get --purge remove <each package>
```

Then after removing the existing Ubuntuzilla repo I started fresh. I hope I didn't somehow hose the testing process.

As I'm still learning I'd appreciate a brief explanation regarding the difference between the two when you have time.

Note: I am tired so if I run into trouble you might not hear from me again for about 24 hours.

---

### Post by kansasnoob on 2009-12-29
I may be partially answering my own question:

```
lance@lance-desktop:~$ ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py: command not found
lance@lance-desktop:~$ ubuntuzilla.py -a remove -p thunderbird
ubuntuzilla.py: command not found
lance@lance-desktop:~$ ubuntuzilla.py -a remove -p seamonkey
ubuntuzilla.py: command not found
lance@lance-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
**deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main**
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe
lance@lance-desktop:~$ 

```

You can see that with the last Ubuntuzilla .deb repo still installed running the "py -a remove -p" commands fails.

Stay tuned.

---

### Post by kansasnoob on 2009-12-29
Next i did this:

```
lance@lance-desktop:~$ sudo apt-get --purge remove seamonkey
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  seamonkey*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160567 files and directories currently installed.)
Removing seamonkey ...
Processing triggers for desktop-file-utils ...
lance@lance-desktop:~$ sudo apt-get --purge remove thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  thunderbird*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160185 files and directories currently installed.)
Removing thunderbird ...
Processing triggers for desktop-file-utils ...
lance@lance-desktop:~$ sudo apt-get --purge remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 131kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 159754 files and directories currently installed.)
Removing firefox ...
lance@lance-desktop:~$ 

```

I questioned whether or not to that with Firefox but next I'll use the Software Sources gui to remove the Ubuntuzilla repo and then I'll start over.

Err, well I'll see what kind of Firefox I end up with in Karmic now. I want to be sure I have the Ubuntu version of Firefox. (I'm sure I do anyway)

---

### Post by kansasnoob on 2009-12-29
OK so I removed your repo and gpg key and closed Firefox, then ran update, etc:

```
lance@lance-desktop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://us.archive.ubuntu.com karmic-security Release.gpg                   
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US    
Hit http://deb.opera.com stable Release                                        
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg                   
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US    
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US   
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://archive.canonical.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://us.archive.ubuntu.com karmic-security Release                       
Hit http://us.archive.ubuntu.com karmic-proposed Release                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://us.archive.ubuntu.com karmic-backports Release                      
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org karmic Release                               
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com karmic/main Packages                
Hit http://us.archive.ubuntu.com karmic/restricted Packages        
Hit http://us.archive.ubuntu.com karmic/multiverse Packages        
Hit http://us.archive.ubuntu.com karmic/main Sources               
Hit http://us.archive.ubuntu.com karmic/restricted Sources         
Hit http://us.archive.ubuntu.com karmic/universe Packages          
Hit http://us.archive.ubuntu.com karmic/universe Sources           
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages  
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources         
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources   
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages    
Hit http://packages.medibuntu.org karmic/free Packages               
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://us.archive.ubuntu.com karmic-security/main Packages
Hit http://us.archive.ubuntu.com karmic-security/restricted Packages
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages 
Hit http://us.archive.ubuntu.com karmic-security/main Sources
Hit http://us.archive.ubuntu.com karmic-security/restricted Sources
Hit http://us.archive.ubuntu.com karmic-security/universe Packages
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://us.archive.ubuntu.com karmic-security/universe Sources
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Reading package lists... Done
lance@lance-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lance@lance-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lance@lance-desktop:~$ 

```

Oddly Firefox still seems to work with the firefox package removed so I may need to revisit this with the Live CD just as a double check.

---

### Post by kansasnoob on 2009-12-29
So I reinstalled the repo, etc. odd results with Seamonkey I think:

```
lance@lance-desktop:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
lance@lance-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
lance@lance-desktop:~$ sudo apt-get update
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:1 http://switch.dl.sourceforge.net all Release.gpg [197B]                  
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Hit http://archive.canonical.com karmic Release                                
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://deb.opera.com stable Release                                        
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Hit http://us.archive.ubuntu.com karmic-security Release.gpg                   
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic Release                               
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US    
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg                   
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US    
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US   
Ign http://switch.dl.sourceforge.net all/main Translation-en_US                
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://us.archive.ubuntu.com karmic-security Release                       
Hit http://us.archive.ubuntu.com karmic-proposed Release                       
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com karmic-backports Release                      
Get:2 http://switch.dl.sourceforge.net all Release [961B]           
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources 
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages  
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources   
Hit http://us.archive.ubuntu.com karmic-security/main Packages     
Hit http://us.archive.ubuntu.com karmic-security/restricted Packages
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-security/main Sources      
Hit http://us.archive.ubuntu.com karmic-security/restricted Sources
Hit http://us.archive.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic-security/universe Sources
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Ign http://switch.dl.sourceforge.net all/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages          
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages            
Ign http://switch.dl.sourceforge.net all/main Packages                         
Get:3 http://switch.dl.sourceforge.net all/main Packages [850B]
Fetched 2,008B in 3s (596B/s)
Reading package lists... Done
lance@lance-desktop:~$ sudo apt-get install seamonkey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  seamonkey-browser seamonkey-chatzilla seamonkey-gnome-support
  seamonkey-mailnews
Suggested packages:
  libkrb53 seamonkey-dom-inspector
The following NEW packages will be installed:
  seamonkey seamonkey-browser seamonkey-chatzilla seamonkey-gnome-support
  seamonkey-mailnews
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.2MB of archives.
After this operation, 40.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
lance@lance-desktop:~$ 

```

OK, I see it actually shows up in Synaptic as seamonkey.mozilla.build so:

```
lance@lance-desktop:~$ sudo apt-get install seamonkey.mozilla.build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  seamonkey.mozilla.build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main seamonkey.mozilla.build 2.0.1-0ubuntu1 [14.5MB]
Fetched 14.5MB in 24s (587kB/s)                                                
Selecting previously deselected package seamonkey.mozilla.build.
(Reading database ... 159752 files and directories currently installed.)
Unpacking seamonkey.mozilla.build (from .../seamonkey.mozilla.build_2.0.1-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu by seamonkey.mozilla.build'
Processing triggers for desktop-file-utils ...
Setting up seamonkey.mozilla.build (2.0.1-0ubuntu1) ...
lance@lance-desktop:~$ 

```

That worked fine although I must say I've never seen a package name separated with dots in Synaptic. That and the menu name:

[ATTACH]141695[/ATTACH]

Seamonkey works perfectly though! Plugins linked etc.

---

### Post by nanotube on 2009-12-29
> **kansasnoob said:**
> I'm just going to give this a try but noticed this:



I just wanted to say that during my last testing instead of:

```
ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py -a remove -p thunderbird
ubuntuzilla.py -a remove -p seamonkey

```

I just ran:

```
sudo apt-get --purge remove <each package>
```

Then after removing the existing Ubuntuzilla repo I started fresh. I hope I didn't somehow hose the testing process.

As I'm still learning I'd appreciate a brief explanation regarding the difference between the two when you have time.

Note: I am tired so if I run into trouble you might not hear from me again for about 24 hours.

ok, so... it seems that i need to clarify what ubuntuzilla actually does. :)

in broad strokes, what it does is the following:
1. grab the tar.gz archive from mozilla, extract it into /opt, 
2. divert the existing /usr/bin/<package> link to /usr/bin/<package>.ubuntu
3. make its own symlink in /usr/bin/<package> that now points to the binary in /opt

so, when you to "ubuntuzilla.py -a remove -p <package>", it undoes all that. namely:
1. delete the symlink in /usr/bin/<package> that points to /opt
2. undivert the repositories /usr/bin/<package>.ubuntu back to /usr/bin/<package>
3. delete the extracted files from /opt.

if you don't do that, and instead just do a "sudo apt-get remove <package>", what that does is remove the repositories version of the package, but all the stuff that ubuntuzilla has installed remains intact - including the diversion of the repositories symlink that is still stored in the database.

it is that local diversion that will conflict with the 'new' diversion that the new repository repacks of mozilla packages will be attempting. (you can, of course, simply manually remove the diversion)

if you want to see the existing diversions on your system, you can run "dpkg-divert --list", any diversions that are done by ubuntuzilla will be listed as 'local diversion'.

hope that clarifies things. 

so in all - well, you didn't 'hose' the testing process, but if you run into any diversion errors during install... you'll know why they're there. :)

---

### Post by nanotube on 2009-12-29
> **kansasnoob said:**
> I may be partially answering my own question:

```
lance@lance-desktop:~$ ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py: command not found
lance@lance-desktop:~$ ubuntuzilla.py -a remove -p thunderbird
ubuntuzilla.py: command not found
lance@lance-desktop:~$ ubuntuzilla.py -a remove -p seamonkey
ubuntuzilla.py: command not found
lance@lance-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
**deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main**
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe
lance@lance-desktop:~$ 

```

You can see that with the last Ubuntuzilla .deb repo still installed running the "py -a remove -p" commands fails.

Stay tuned.

yes, the ubuntuzilla.py command fails, because apparently you have uninstalled the ubuntuzilla package itself. 

the repo that is listed in your sources.list is the "mozilla repacks" repo, not the "ubuntuzilla script installation repo", by the way, which is as it should be, for testing the mozilla repacks. :)

---

### Post by nanotube on 2009-12-29
> **kansasnoob said:**
> 

Oddly Firefox still seems to work with the firefox package removed so I may need to revisit this with the Live CD just as a double check.

well, from what you told me, since you didn't run "ubuntuzilla.py -a remove", the ubuntuzilla-installed package of firefox is still there in /opt, and is being linked to from /usr/bin/firefox (as you should be able to verify by running "ls -al /usr/bin/firefox")

so no surprise that firefox is still there.

to find out whether you are running the ubuntu or the mozilla-build version of firefox, just go to help-> about in firefox. if it's the ubuntu version, it will say "firefox bla bla bla ubuntu", while if it's the mozilla-build, it won't mention ubuntu. (or, just look at where your /usr/bin/firefox is pointing)

---

### Post by nanotube on 2009-12-30
> **kansasnoob said:**
> So I reinstalled the repo, etc. odd results with Seamonkey I think:

```
lance@lance-desktop:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
lance@lance-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
lance@lance-desktop:~$ sudo apt-get update
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:1 http://switch.dl.sourceforge.net all Release.gpg [197B]                  
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Hit http://archive.canonical.com karmic Release                                
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://deb.opera.com stable Release                                        
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Hit http://us.archive.ubuntu.com karmic-security Release.gpg                   
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic Release                               
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US    
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg                   
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US    
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US   
Ign http://switch.dl.sourceforge.net all/main Translation-en_US                
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://us.archive.ubuntu.com karmic-security Release                       
Hit http://us.archive.ubuntu.com karmic-proposed Release                       
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com karmic-backports Release                      
Get:2 http://switch.dl.sourceforge.net all Release [961B]           
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources 
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages  
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources   
Hit http://us.archive.ubuntu.com karmic-security/main Packages     
Hit http://us.archive.ubuntu.com karmic-security/restricted Packages
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-security/main Sources      
Hit http://us.archive.ubuntu.com karmic-security/restricted Sources
Hit http://us.archive.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic-security/universe Sources
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Ign http://switch.dl.sourceforge.net all/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages          
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages            
Ign http://switch.dl.sourceforge.net all/main Packages                         
Get:3 http://switch.dl.sourceforge.net all/main Packages [850B]
Fetched 2,008B in 3s (596B/s)
Reading package lists... Done
lance@lance-desktop:~$ sudo apt-get install seamonkey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  seamonkey-browser seamonkey-chatzilla seamonkey-gnome-support
  seamonkey-mailnews
Suggested packages:
  libkrb53 seamonkey-dom-inspector
The following NEW packages will be installed:
  seamonkey seamonkey-browser seamonkey-chatzilla seamonkey-gnome-support
  seamonkey-mailnews
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.2MB of archives.
After this operation, 40.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
lance@lance-desktop:~$ 

```

OK, I see it actually shows up in Synaptic as seamonkey.mozilla.build so:

```
lance@lance-desktop:~$ sudo apt-get install seamonkey.mozilla.build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  seamonkey.mozilla.build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main seamonkey.mozilla.build 2.0.1-0ubuntu1 [14.5MB]
Fetched 14.5MB in 24s (587kB/s)                                                
Selecting previously deselected package seamonkey.mozilla.build.
(Reading database ... 159752 files and directories currently installed.)
Unpacking seamonkey.mozilla.build (from .../seamonkey.mozilla.build_2.0.1-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu by seamonkey.mozilla.build'
Processing triggers for desktop-file-utils ...
Setting up seamonkey.mozilla.build (2.0.1-0ubuntu1) ...
lance@lance-desktop:~$ 

```

That worked fine although I must say I've never seen a package name separated with dots in Synaptic. That and the menu name:

[ATTACH]141695[/ATTACH]

Seamonkey works perfectly though! Plugins linked etc.

the results don't look odd at all. 
first, you installed the ubuntu-repos-version of seamonkey, with package 'seamonkey', which installed successfully. 

then you installed the mozilla-repack of the latest seamonkey, with package seamonkey.mozilla.build, which also installed successfully, symlinked itself as /usr/bin/seamonkey, and diverted the ubuntu-repos version to /usr/bin/seamonkey.ubuntu.

so now, you have /usr/bin/seamonkey pointing to the mozilla-build of seamonkey, and all's nice.

you didn't actually have to install the ubuntu-repos version of seamonkey, it should work with just the seamonkey.mozilla.build package. your ubuntu-repos version is just sitting there taking up disk space now. but either way, they don't interfere with each other. 

so... encouraging results from the seamonkey test.

as far as the package name: yes, they tend to use dashes in package names in the repos, but i looked up the debian packaging official documentation, and dots are acceptable in package names, to i went with dots, because i like dots. :) (also note, e.g., the openoffice.org-<bla> packages).

as far as the menu name - i deliberatedy stuck "mozilla build of <bla>" as the title, to make it clear.

---

### Post by kansasnoob on 2009-12-30
This looks very promising! Wow:

```
lance@lance-desktop:~$ sudo apt-get install thunderbird.mozilla.build
[sudo] password for lance: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
lance@lance-desktop:~$ sudo apt-get install thunderbird.mozilla.build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thunderbird.mozilla.build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main thunderbird.mozilla.build 3.0-0ubuntu1 [12.0MB]
Fetched 12.0MB in 20s (584kB/s)                                                
Selecting previously deselected package thunderbird.mozilla.build.
(Reading database ... 160136 files and directories currently installed.)
Unpacking thunderbird.mozilla.build (from .../thunderbird.mozilla.build_3.0-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird.mozilla.build'
Processing triggers for desktop-file-utils ...
Setting up thunderbird.mozilla.build (3.0-0ubuntu1) ...
lance@lance-desktop:~$ sudo apt-get install firefox.mozilla.build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox.mozilla.build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main firefox.mozilla.build 3.5.6-0ubuntu1 [10.5MB]
Fetched 10.5MB in 17s (592kB/s)                                                
Selecting previously deselected package firefox.mozilla.build.
(Reading database ... 160567 files and directories currently installed.)
Unpacking firefox.mozilla.build (from .../firefox.mozilla.build_3.5.6-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox.mozilla.build'
Processing triggers for desktop-file-utils ...
Setting up firefox.mozilla.build (3.5.6-0ubuntu1) ...
lance@lance-desktop:~$ 

```

Look:

[ATTACH]141700[/ATTACH]

Both Karmic's Firefox and your Firefox show up and both work! That's awesome!

As I said I don't really use Thunderbird so I can't comment much on that but this looks very good.

However lets take the time to get this right! I'm tired so we need to do more testing, I'm dieing to see how this will work in Hardy (it's probably the most likely candidate for needing a newer browser version).

I also wonder about the usage of dot (.) in naming. I've never seen that, it's usually more like "firefox-mozilla-build".

I have tried the icons in the tray and they look great so I think you're heading in the right direction. It's cool to have things coexist!

Don't hesitate to correct me if I'm doing something wrong and please feel free to critique me on anything, you have an excellent project and the success of the project is the goal.

---

### Post by nanotube on 2009-12-30
so now we know seamonkey works fine... curious to see what happens with thunderbird and firefox. :)
thanks a lot for your help!

EDIT: oh heh, you posted ff and tb test results already. :) well, very encouraging!

One thing to note though: i suspect that both the "plain firefox" menu item and the 'mozilla build of firefox' items point at the same place, namely, /usr/bin/firefox, which is, due to the divert, pointing to the mozilla build. that is possibly a source of confusion... but shouldn't be a big deal, methinks...

looking forward to hardy results :)

EDIT2: if you really think it would make people scratch heads, it would be trivial to change package names to '<package>-mozilla-build'. i suppose that would be more in line with conventional usage...

---

### Post by kansasnoob on 2009-12-30
> but i looked up the debian packaging official documentation, and dots are acceptable in package names, to i went with dots, because i like dots

I can understand that. I still use <directory name>_backup which drives some people crazy.

This does look very good.

It may take a couple more days to get through all of the testing because of weather and vehicle problems but I think you're onto the best Ubuntuzilla yet.

Many thanks for a great addition to Ubuntu.

---

### Post by kansasnoob on 2009-12-30
> **nanotube said:**
> so now we know seamonkey works fine... curious to see what happens with thunderbird and firefox. :)
thanks a lot for your help!

EDIT: oh heh, you posted ff and tb test results already. :) well, very encouraging!

One thing to note though: i suspect that both the "plain firefox" menu item and the 'mozilla build of firefox' items point at the same place, namely, /usr/bin/firefox, which is, due to the divert, pointing to the mozilla build. that is possibly a source of confusion... but shouldn't be a big deal, methinks...

looking forward to hardy results :)

EDIT2: if you really think it would make people scratch heads, it would be trivial to change package names to '<package>-mozilla-build'. i suppose that would be more in line with conventional usage...

After a restart both launchers launch the Mozilla build. You know though, dumb me, I had Firefox open when I made the change.

I'm thinking we're down to easy tweaks (easy for me to say), sorry you have to deal with my stupidity :P

---

### Post by nanotube on 2009-12-30
> **kansasnoob said:**
> I can understand that. I still use <directory name>_backup which drives some people crazy.


heh well, that said - i've just changed the package names to <package>-mozilla-build and uploaded to the repo. so for future testing, use the dashed package names, since the dotted ones no longer exist. :)

> 
This does look very good.

cool!

> 
It may take a couple more days to get through all of the testing because of weather and vehicle problems but I think you're onto the best Ubuntuzilla yet.

well, no particular hurry - besides my own impatience to see this implemented, there's no deadline :)

> 
Many thanks for a great addition to Ubuntu.
and many thanks to you for helping me along! :)

---

### Post by kansasnoob on 2009-12-30
I spun up my Karmic Live CD this AM just to double check what Firefox packages are installed by default. Then I reverted my installed Karmic to it's native state.

I also installed the Ubuntu repo versions of Seamonkey and Thunderbird just to see how things would work. And it works great!!!!!!!!!!!!!!!

With the official Ubuntu packages of Seamonkey, Thunderbird, and Firefox installed I just went to synaptic and typed ubuntuzilla into it's search and up pop all three -mozilla-build packages so I mark them all for installation and it just works flawlessly!

One minor caveat, to me personally it's no big deal as it can be cleaned up by going to System > Preferences > Main Menu, but we end up with new launchers for the mozilla builds and still have the original launchers (oh and I guess the mozilla-build Thunderbird icon looks funny):

[ATTACH]141733[/ATTACH]

Either set of launchers launches the mozilla-build of all three apps. As I said, it's no big deal to me, and I don't know if it's possible or feasible to have an "if" in the process so a new launcher will only be created if no existing version is present.

Anyway this is looking awesome because it appears this will work regardless of what other version of the app is installed, or even if no previous version is installed at all.

Of course I'll want to check this out in Hardy and also Jaunty, but this is looking fabulous. BTW you didn't need to change those package names just on my account.

Just an aside here; is it possible to import Firefox bookmarks into Seamonkey? I'm just curious because, since I don't actually use Seamonkey, I've never checked to see if the Ubuntuzilla build properly imports bookmarks from the official Ubuntu version.

---

### Post by nanotube on 2009-12-30
> **kansasnoob said:**
> I spun up my Karmic Live CD this AM just to double check what Firefox packages are installed by default. Then I reverted my installed Karmic to it's native state.

I also installed the Ubuntu repo versions of Seamonkey and Thunderbird just to see how things would work. And it works great!!!!!!!!!!!!!!!

With the official Ubuntu packages of Seamonkey, Thunderbird, and Firefox installed I just went to synaptic and typed ubuntuzilla into it's search and up pop all three -mozilla-build packages so I mark them all for installation and it just works flawlessly!

awesome :)

> 
One minor caveat, to me personally it's no big deal as it can be cleaned up by going to System > Preferences > Main Menu, but we end up with new launchers for the mozilla builds and still have the original launchers (oh and I guess the mozilla-build Thunderbird icon looks funny):

[ATTACH]141733[/ATTACH]

Either set of launchers launches the mozilla-build of all three apps. As I said, it's no big deal to me, and I don't know if it's possible or feasible to have an "if" in the process so a new launcher will only be created if no existing version is present.


hrm well... i'll think about this. i'd like to keep the packages as simple as possible... so i don't want to fiddle around with ubuntu-repos icons, if they're there, they're there, if not, they're not, and my packages don't have to worry about it.

i'm leaning toward just making a note of that in the docs, and let users deal with it as they see fit.

as far as the thunderbird icon... oh yea, they placed their icons in a different place in the tar.bz2. so i'll mod the package and reupload. thanks for pointing it out :)

> 
Anyway this is looking awesome because it appears this will work regardless of what other version of the app is installed, or even if no previous version is installed at all.

that's the idea!

> 
Of course I'll want to check this out in Hardy and also Jaunty, but this is looking fabulous. BTW you didn't need to change those package names just on my account.

heh well, i didn't change it /just/ on your account - i checked all the existing package names that contain a dot, and found that dots only get used for version number separators (e.g. firefox-3.5), and for openoffice.org, because that actually has a dot in the name, but everywhere else dash is used. so to keep in line with accepted practice, i figured i might as well. 

> 
Just an aside here; is it possible to import Firefox bookmarks into Seamonkey? I'm just curious because, since I don't actually use Seamonkey, I've never checked to see if the Ubuntuzilla build properly imports bookmarks from the official Ubuntu version.

should be possible, since they have the same bookmark import/export mechanisms... haven't tried myself, but i don't see why not.

as far as importing bookmarks from the ubuntu version of /seamonkey/ - that should happen automagically, since those are stored in the user's profile, and both versions will be looking for the profile in the same place.

EDIT: fixed thunderbird icon path and uploaded the new package. please take a look for that next time you try it.

---

### Post by aysiu on 2009-12-30
nanotube, I'm a bit busy this week, but I will get to testing as soon as possible. This repository idea looks *very* promising!

---

### Post by nanotube on 2009-12-30
> **aysiu said:**
> nanotube, I'm a bit busy this week, but I will get to testing as soon as possible. This repository idea looks *very* promising!

Glad you like! No problem on the testing - i've got kansasnoob helping me out. :)

---

### Post by phillw on 2009-12-30
Hi,

When you're ready for a willing volunteer to play with it in 10.04, I'd be more than happy to give it a try for you. I'll have to read some more up on it first (quite a few pages to read !!) - I keep 10.04 well backed up - so if something breaks, it's no big deal.

Thunderbird, I used to use (with XP) - so shouldn't take toooo long to re-acquaint myself with it. I've never used SeaMonkey - but am happy to try. And I've had various beta's of FF on my system over the years.

PM me if you'd like me to test anything for you.

Regards,

Phill.

---

### Post by nanotube on 2009-12-30
> **phillw said:**
> Hi,

When you're ready for a willing volunteer to play with it in 10.04, I'd be more than happy to give it a try for you. I'll have to read some more up on it first (quite a few pages to read !!) - I keep 10.04 well backed up - so if something breaks, it's no big deal.

Thunderbird, I used to use (with XP) - so shouldn't take toooo long to re-acquaint myself with it. I've never used SeaMonkey - but am happy to try. And I've had various beta's of FF on my system over the years.

PM me if you'd like me to test anything for you.

Regards,

Phill.

hi
sure, a testing on 10.04 would be a good thing. just add the repository, and try installing ff, tb, and sm, and see if they work as advertised... 

as far as reading back in the thread - the only relevant bits are within the last 40 messages in this thread, as of this post - so you don't have to bother reading anything earlier. :)

appreciate your offer - let me know if you have any questions!

---

### Post by kansasnoob on 2009-12-30
Well in Hardy I already had your repo installed, still running Firefox 3.0, but new version of Seamonkey. So I removed that version of Seamonkey, then after a reload typing "ubuntuzilla" into Synaptics search showed the three mozilla-build packages so I decided to give cli a try:

```
lance@lance-desktop:~$ sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main firefox-mozilla-build 3.5.6-0ubuntu1 [10.5MB]
Fetched 10.5MB in 18s (577kB/s)                                                
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 112537 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Setting up firefox-mozilla-build (3.5.6-0ubuntu1) ...

```

Totally flawless! All seems well.

I'm super tired and still trying to finish up my auto brake line problem so I might be a bit slow, please be just a bit patient so I can double check things.

This is looking very, very good!

Oh and I agree on just adding a note about cleaning up the menu!

---

### Post by kansasnoob on 2009-12-30
I decided to try something a bit different. I installed Thunderbird in Hardy using Add-Remove and then tried installing your package:

```
lance@lance-desktop:~$ sudo apt-get install thunderbird-mozilla-build
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thunderbird-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main thunderbird-mozilla-build 3.0-0ubuntu1 [12.0MB]
Fetched 12.0MB in 28s (416kB/s)                                                
Selecting previously deselected package thunderbird-mozilla-build.
(Reading database ... 113302 files and directories currently installed.)
Unpacking thunderbird-mozilla-build (from .../thunderbird-mozilla-build_3.0-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build'
Setting up thunderbird-mozilla-build (3.0-0ubuntu1) ...

```

Flawless! Oh and I actually gave the plugins a test drive in Firefox and there was no problem.

I'll try Seamonkey in Hardy next.

---

### Post by kansasnoob on 2009-12-30
Since Seamonkey is not available in Add-Remove I thought what would be the most common way for someone to instruct a nOOb to install it ... I think:

```
lance@lance-desktop:~$ sudo apt-get install seamonkey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  seamonkey-browser seamonkey-mailnews
Suggested packages:
  latex-xft-fonts seamonkey-dom-inspector
Recommended packages:
  seamonkey-chatzilla seamonkey-gnome-support
The following NEW packages will be installed:
  seamonkey seamonkey-browser seamonkey-mailnews
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.0MB of archives.
After this operation, 35.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy-updates/universe seamonkey-browser 1.1.17+nobinonly-0ubuntu0.8.04.1 [9175kB]
Get:2 http://us.archive.ubuntu.com hardy-updates/universe seamonkey-mailnews 1.1.17+nobinonly-0ubuntu0.8.04.1 [1808kB]
Get:3 http://us.archive.ubuntu.com hardy-updates/universe seamonkey 1.1.17+nobinonly-0ubuntu0.8.04.1 [25.0kB]
Fetched 11.0MB in 27s (407kB/s)                                                
Selecting previously deselected package seamonkey-browser.
(Reading database ... 113732 files and directories currently installed.)
Unpacking seamonkey-browser (from .../seamonkey-browser_1.1.17+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Selecting previously deselected package seamonkey-mailnews.
Unpacking seamonkey-mailnews (from .../seamonkey-mailnews_1.1.17+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Selecting previously deselected package seamonkey.
Unpacking seamonkey (from .../seamonkey_1.1.17+nobinonly-0ubuntu0.8.04.1_all.deb) ...
Setting up seamonkey-browser (1.1.17+nobinonly-0ubuntu0.8.04.1) ...
Updating seamonkey chrome registry...done.

Setting up seamonkey-mailnews (1.1.17+nobinonly-0ubuntu0.8.04.1) ...
Updating seamonkey chrome registry...done.

Setting up seamonkey (1.1.17+nobinonly-0ubuntu0.8.04.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
**lance@lance-desktop:~$ sudo apt-get install seamonkey-mozilla-build**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  seamonkey-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main seamonkey-mozilla-build 2.0.1-0ubuntu1 [14.5MB]
Fetched 14.5MB in 36s (396kB/s)                                                
Selecting previously deselected package seamonkey-mozilla-build.
(Reading database ... 114523 files and directories currently installed.)
Unpacking seamonkey-mozilla-build (from .../seamonkey-mozilla-build_2.0.1-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu by seamonkey-mozilla-build'
Setting up seamonkey-mozilla-build (2.0.1-0ubuntu1) ...
lance@lance-desktop:~$ 


```

So I tried it and you can see that I then installed your build. No problems! I'd swear that we had some plugin problems with Hardy in the past, but not now! This is impressive.

Just be patient and let me try Jaunty. It has the old style Ubuntu packages installed so I think I'll try doing everything wrong :P

---

### Post by nanotube on 2009-12-30
looks totally awesome. :) thanks for all your work!

i'll wait until your results from jaunty, and if that looks good, i'll make an official announcement of the repo, with a view toward retiring the ubuntuzilla installer script and just hosting the repo. 

(though 64bit users would still be stuck with the script... at least until mozilla starts releasing 64bit builds...)

---

### Post by kansasnoob on 2009-12-31
All's well in Jaunty. As expected, since I'd used the old version of Ubuntuzilla, I had to:

```
ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py -a remove -p thunderbird
ubuntuzilla.py -a remove -p seamonkey
sudo apt-get remove --purge ubuntuzilla

```

Otherwise installation was flawless.

I'm curious if the old version will still be archived just in case?

---

### Post by nanotube on 2009-12-31
> **kansasnoob said:**
> All's well in Jaunty. As expected, since I'd used the old version of Ubuntuzilla, I had to:

```
ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py -a remove -p thunderbird
ubuntuzilla.py -a remove -p seamonkey
sudo apt-get remove --purge ubuntuzilla

```


by the way, the removal of the actual ubuntuzilla package (your last command there) is optional, as it doesn't affect anything.

> 
Otherwise installation was flawless.

cool. i suppose i'll make it official, then.

> 
I'm curious if the old version will still be archived just in case?

of course, i'll not be actually deleting anything. that's not the open source way. :)

---

### Post by nanotube on 2009-12-31
Well, I have made the changes to the ubuntuzilla website, now reflecting the use of the new repository. 

Please give it a look and let me know what you think.

---

### Post by kansasnoob on 2009-12-31
Looks great to me. Thanks for the great work.

---

### Post by nanotube on 2009-12-31
> **kansasnoob said:**
> Looks great to me. Thanks for the great work.

Excellent - thanks for all the help! :)

---

### Post by kansasnoob on 2009-12-31
Anytime! If I had spare $ I'd send them your way.

I actually enjoy this testing and I learn more each time. Like this time installing Hardy I learned more about a legacy grub system not wanting to install where grub2 exists.

The transition to grub2 sucks!

And oddly running Hardy I experienced better performance with both VLC and Totem.

---

### Post by nanotube on 2010-01-01
> **kansasnoob said:**
> Anytime! If I had spare $ I'd send them your way.


your help is worth way more than that! 

> 
I actually enjoy this testing and I learn more each time. Like this time installing Hardy I learned more about a legacy grub system not wanting to install where grub2 exists.

The transition to grub2 sucks!


heh... haven't been bitten by that one (yet).

> 
And oddly running Hardy I experienced better performance with both VLC and Totem.

hrm, probably something with video drivers or xorg setup... or maybe compiz is at fault?... (since iirc, hardy didn't come with compiz by default)

---

### Post by aysiu on 2010-01-01
It looks as if you've already got some good testing in. For what it's worth, I just tried your repository to install Firefox, and it worked flawlessly. Here's the output...

**Installation** ```
username@ubuntu:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
[sudo] password for username: 
username@ubuntu:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for username: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
username@ubuntu:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://download.virtualbox.org karmic Release                              
Get:2 http://dl.google.com stable Release [2,540B]                             
Hit http://download.virtualbox.org karmic/non-free Packages                    
Get:3 http://dl.google.com stable/main Packages [867B]                         
Hit http://mirrors.xmission.com karmic Release.gpg                             
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://mirrors.xmission.com karmic/main Translation-en_US                  
Get:4 http://switch.dl.sourceforge.net all Release.gpg [197B]                  
Ign http://mirrors.xmission.com karmic/restricted Translation-en_US            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://mirrors.xmission.com karmic/universe Translation-en_US              
Ign http://mirrors.xmission.com karmic/multiverse Translation-en_US            
Hit http://mirrors.xmission.com karmic-updates Release.gpg                     
Ign http://mirrors.xmission.com karmic-updates/restricted Translation-en_US    
Ign http://mirrors.xmission.com karmic-updates/main Translation-en_US          
Ign http://mirrors.xmission.com karmic-updates/multiverse Translation-en_US    
Ign http://mirrors.xmission.com karmic-updates/universe Translation-en_US      
Hit http://archive.canonical.com karmic Release                                
Hit http://deb.opera.com stable Release                                        
Hit http://mirrors.xmission.com karmic Release                                 
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://mirrors.xmission.com karmic-updates Release                         
Ign http://switch.dl.sourceforge.net all/main Translation-en_US                
Hit http://mirrors.xmission.com karmic/main Packages                           
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://mirrors.xmission.com karmic/restricted Packages                     
Hit http://mirrors.xmission.com karmic/universe Packages                       
Hit http://mirrors.xmission.com karmic/multiverse Packages                     
Hit http://mirrors.xmission.com karmic-updates/restricted Packages             
Hit http://mirrors.xmission.com karmic-updates/main Packages                   
Hit http://mirrors.xmission.com karmic-updates/multiverse Packages             
Hit http://mirrors.xmission.com karmic-updates/universe Packages               
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org karmic Release                               
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/universe Packages     
Ign http://deb.opera.com stable/non-free Packages                    
Get:5 http://switch.dl.sourceforge.net all Release [961B]            
Hit http://packages.medibuntu.org karmic/free Packages              
Hit http://deb.opera.com stable/non-free Packages
Hit http://packages.medibuntu.org karmic/non-free Packages
Ign http://switch.dl.sourceforge.net all/main Packages
Ign http://switch.dl.sourceforge.net all/main Packages       
Get:6 http://switch.dl.sourceforge.net all/main Packages [854B]
Fetched 5,608B in 2s (1,979B/s)
Reading package lists... Done
username@ubuntu:~$ sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main firefox-mozilla-build 3.5.6-0ubuntu1 [10.5MB]
Fetched 10.5MB in 18s (562kB/s)                                                
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 113634 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Processing triggers for desktop-file-utils ...
Setting up firefox-mozilla-build (3.5.6-0ubuntu1) ...
username@ubuntu:~$ firefox
firefox         firefox-3.5     firefox.ubuntu  
username@ubuntu:~$ firefox &
[1] 3681
username@ubuntu:~$ 
(firefox-bin:3697): GLib-WARNING **: g_set_prgname() called multiple times

(firefox-bin:3697): GLib-WARNING **: g_set_prgname() called multiple times
username@ubuntu:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2010-01-01 01:17 /usr/bin/firefox -> /opt/firefox/firefox
[1]+  Done                    firefox
username@ubuntu:~$ ls -l /usr/bin/firefox.ubuntu
lrwxrwxrwx 1 root root 11 2009-12-19 00:37 /usr/bin/firefox.ubuntu -> firefox-3.5
``` **Removal** ```
username@ubuntu:~$ sudo apt-get remove firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-mozilla-build
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 113869 files and directories currently installed.)
Removing firefox-mozilla-build ...
Removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Processing triggers for desktop-file-utils ...
username@ubuntu:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 11 2009-12-19 00:37 /usr/bin/firefox -> firefox-3.5
username@ubuntu:~$
```

---

### Post by nanotube on 2010-01-01
> **aysiu said:**
> It looks as if you've already got some good testing in. For what it's worth, I just tried your repository to install Firefox, and it worked flawlessly. Here's the output...

**Installation** ```
username@ubuntu:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
[sudo] password for username: 
username@ubuntu:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for username: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
username@ubuntu:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://download.virtualbox.org karmic Release                              
Get:2 http://dl.google.com stable Release [2,540B]                             
Hit http://download.virtualbox.org karmic/non-free Packages                    
Get:3 http://dl.google.com stable/main Packages [867B]                         
Hit http://mirrors.xmission.com karmic Release.gpg                             
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://mirrors.xmission.com karmic/main Translation-en_US                  
Get:4 http://switch.dl.sourceforge.net all Release.gpg [197B]                  
Ign http://mirrors.xmission.com karmic/restricted Translation-en_US            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://mirrors.xmission.com karmic/universe Translation-en_US              
Ign http://mirrors.xmission.com karmic/multiverse Translation-en_US            
Hit http://mirrors.xmission.com karmic-updates Release.gpg                     
Ign http://mirrors.xmission.com karmic-updates/restricted Translation-en_US    
Ign http://mirrors.xmission.com karmic-updates/main Translation-en_US          
Ign http://mirrors.xmission.com karmic-updates/multiverse Translation-en_US    
Ign http://mirrors.xmission.com karmic-updates/universe Translation-en_US      
Hit http://archive.canonical.com karmic Release                                
Hit http://deb.opera.com stable Release                                        
Hit http://mirrors.xmission.com karmic Release                                 
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://mirrors.xmission.com karmic-updates Release                         
Ign http://switch.dl.sourceforge.net all/main Translation-en_US                
Hit http://mirrors.xmission.com karmic/main Packages                           
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://mirrors.xmission.com karmic/restricted Packages                     
Hit http://mirrors.xmission.com karmic/universe Packages                       
Hit http://mirrors.xmission.com karmic/multiverse Packages                     
Hit http://mirrors.xmission.com karmic-updates/restricted Packages             
Hit http://mirrors.xmission.com karmic-updates/main Packages                   
Hit http://mirrors.xmission.com karmic-updates/multiverse Packages             
Hit http://mirrors.xmission.com karmic-updates/universe Packages               
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org karmic Release                               
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/universe Packages     
Ign http://deb.opera.com stable/non-free Packages                    
Get:5 http://switch.dl.sourceforge.net all Release [961B]            
Hit http://packages.medibuntu.org karmic/free Packages              
Hit http://deb.opera.com stable/non-free Packages
Hit http://packages.medibuntu.org karmic/non-free Packages
Ign http://switch.dl.sourceforge.net all/main Packages
Ign http://switch.dl.sourceforge.net all/main Packages       
Get:6 http://switch.dl.sourceforge.net all/main Packages [854B]
Fetched 5,608B in 2s (1,979B/s)
Reading package lists... Done
username@ubuntu:~$ sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://switch.dl.sourceforge.net all/main firefox-mozilla-build 3.5.6-0ubuntu1 [10.5MB]
Fetched 10.5MB in 18s (562kB/s)                                                
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 113634 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Processing triggers for desktop-file-utils ...
Setting up firefox-mozilla-build (3.5.6-0ubuntu1) ...
username@ubuntu:~$ firefox
firefox         firefox-3.5     firefox.ubuntu  
username@ubuntu:~$ firefox &
[1] 3681
username@ubuntu:~$ 
(firefox-bin:3697): GLib-WARNING **: g_set_prgname() called multiple times

(firefox-bin:3697): GLib-WARNING **: g_set_prgname() called multiple times
username@ubuntu:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2010-01-01 01:17 /usr/bin/firefox -> /opt/firefox/firefox
[1]+  Done                    firefox
username@ubuntu:~$ ls -l /usr/bin/firefox.ubuntu
lrwxrwxrwx 1 root root 11 2009-12-19 00:37 /usr/bin/firefox.ubuntu -> firefox-3.5
``` **Removal** ```
username@ubuntu:~$ sudo apt-get remove firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-mozilla-build
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 113869 files and directories currently installed.)
Removing firefox-mozilla-build ...
Removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Processing triggers for desktop-file-utils ...
username@ubuntu:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 11 2009-12-19 00:37 /usr/bin/firefox -> firefox-3.5
username@ubuntu:~$
```

nice - thanks for the testing! 

the repository is now 'live'... waiting for all the bug reports to roll in... ;)

---

### Post by aysiu on 2010-01-01
I don't have the output, but I did it for Thunderbird as well, and it also worked perfectly.

Excellent work, nanotube!

---

### Post by nanotube on 2010-01-01
> **aysiu said:**
> I don't have the output, but I did it for Thunderbird as well, and it also worked perfectly.


Well, as long as it works, there's no need for output. only when it doesn't, so i can figure out what went wrong.  

> 
Excellent work, nanotube!

glad you approve! :)

---

### Post by kansasnoob on 2010-01-01
Just got around to trying this in Lucid and all's well :)

Happy new year!

---

### Post by el cameleon on 2010-01-02
> **nanotube said:**
> Well, I have made the changes to the ubuntuzilla website, now reflecting the use of the new repository. 

Please give it a look and let me know what you think.
I have just try to install Thunderbird 3 and I succeeded. Unfortunately, I am not able to localise it into french, wheras the fr.xpi (*)is correctly installed, thunderbird stay in english...

I do not understand the problem:confused:

(*) find here: [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/linux-i686/xpi/)

---

### Post by nanotube on 2010-01-02
> **el cameleon said:**
> I have just try to install Thunderbird 3 and I succeeded. Unfortunately, I am not able to localise it into french, wheras the fr.xpi (*)is correctly installed, thunderbird stay in english...

I do not understand the problem:confused:

(*) find here: [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/3.0/linux-i686/xpi/)

after the language pack is installed, you have to enable it to be the in-use locale for your profile, which setting you can find in the advanced config editor. see the instructions on the mozilla website about this here:
[http://kb.mozillazine.org/Language_packs](http://kb.mozillazine.org/Language_packs)

(thanks for pointing this out - i'll add a link to this page on the ubuntuzilla site)

EDIT: added explicit instructions for enabling lanugage packs to the ubuntuzilla site, along with a link to the mozilla article.

---

### Post by nanotube on 2010-01-02
> **kansasnoob said:**
> Just got around to trying this in Lucid and all's well :)
[quote]
cool :)

[quote]
Happy new year!

you too!

---

### Post by nanotube on 2010-01-06
So, for the repository url i use one of the sourceforge file hosting mirrors directly (the switch.dl server, namely). however, using one of those directly means that the download counts on sourceforge don't get updated, and that if that particular mirror is down, that's that.

the 'standard' download server, downloads.sourceforge.net, is a gateway that automatically redirects to the best mirror, and would thus be a better url to use - not even to mention that it counts the downloads. 

however, on hardy and intrepid, apt-get does not support http 302 redirect responses, which caused the gateway to fail as an apt repository. according to the bug reports i have seen, however, this issue should be fixed as of jaunty. 

so could you try using the following as the ubuntuzilla repository, instead of switch.dl.sourceforge.net:
```

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

```

try it on jaunty and up, to see if it works (already tried it on intrepid, which is what i'm on now, and it doesn't work, as expected...). if it does, i'll use that as the main repository, and make a special note for hardy and intrepid users to use switch.dl.

---

### Post by kansasnoob on 2010-01-06
That works fine in Karmic (I'll try Jaunty later), I began by going to Synaptic and searching "ubuntuzilla" which brings up all 3 pkgs and removed them, then I went to Settings > Repos and removed the old Ubuntuzilla repo, then reloaded, and when all was done I checked to be sure all pkgs had reverted to the Ubuntu pkgs and they had.

I then went to Software Sources and installed the new repo, closed it and let the terminal do the rest:

```
lance@lance-desktop:~$ sudo apt-get update && sudo apt-get install firefox-mozilla-build seamonkey-mozilla-build thunderbird-mozilla-build
[sudo] password for lance: 
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://downloads.sourceforge.net all/main Translation-en_US                
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://archive.canonical.com karmic Release                                
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Hit http://us.archive.ubuntu.com karmic-security Release.gpg                   
Hit http://packages.medibuntu.org karmic Release                               
Hit http://deb.opera.com stable Release                                        
Hit http://downloads.sourceforge.net all Release.gpg                           
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic/partner Packages                       
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US        
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US    
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg                   
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US        
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US    
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg                  
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US   
Hit http://us.archive.ubuntu.com karmic Release                      
Ign http://deb.opera.com stable/non-free Packages                    
Hit http://us.archive.ubuntu.com karmic-updates Release              
Hit http://us.archive.ubuntu.com karmic-security Release            
Hit http://downloads.sourceforge.net all Release                               
Hit http://us.archive.ubuntu.com karmic-proposed Release                       
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com karmic-backports Release                      
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages         
Hit http://us.archive.ubuntu.com karmic/multiverse Packages         
Hit http://us.archive.ubuntu.com karmic/main Sources                
Hit http://us.archive.ubuntu.com karmic/restricted Sources          
Hit http://us.archive.ubuntu.com karmic/universe Packages           
Ign http://downloads.sourceforge.net all/main Packages              
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-security/main Packages
Hit http://us.archive.ubuntu.com karmic-security/restricted Packages
Ign http://downloads.sourceforge.net all/main Packages
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-security/main Sources
Hit http://us.archive.ubuntu.com karmic-security/restricted Sources
Hit http://us.archive.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic-security/universe Sources
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Hit http://downloads.sourceforge.net all/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build seamonkey-mozilla-build thunderbird-mozilla-build
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB/37.0MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://downloads.sourceforge.net all/main thunderbird-mozilla-build 3.0-0ubuntu1 [12.0MB]
Fetched 12.0MB in 19s (620kB/s)                                                
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 161106 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.5.7-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Selecting previously deselected package seamonkey-mozilla-build.
Unpacking seamonkey-mozilla-build (from .../seamonkey-mozilla-build_2.0.1-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu by seamonkey-mozilla-build'
Selecting previously deselected package thunderbird-mozilla-build.
Unpacking thunderbird-mozilla-build (from .../thunderbird-mozilla-build_3.0-0ubuntu1_i386.deb) ...
Adding `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build'
Processing triggers for desktop-file-utils ...
Setting up firefox-mozilla-build (3.5.7-0ubuntu1) ...
Setting up seamonkey-mozilla-build (2.0.1-0ubuntu1) ...
Setting up thunderbird-mozilla-build (3.0-0ubuntu1) ...
lance@lance-desktop:~$ 

```

---

### Post by nanotube on 2010-01-06
thanks for the test - looks encouraging!
if it also works on jaunty, i'll go and modify the website installation instructions...

---

### Post by kansasnoob on 2010-01-06
That works fine in both Jaunty and Lucid.

As you said though it fails in Hardy:

```
Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by kansasnoob on 2010-01-06
Just tried this on Mint Gloria also and it works fine still.

I used the:

```
echo "deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```

Much, much easier because they have no Software Sources gui and Synaptic is poorly modified.

thanks for teaching me that trick :)

---

### Post by aysiu on 2010-01-06
It'd be nice to have a little *if* statement to see if the source is already in there before adding it as a potential duplicate source. What would that command look like?

---

### Post by nanotube on 2010-01-06
> **kansasnoob said:**
> Just tried this on Mint Gloria also and it works fine still.

I used the:

```
echo "deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```

Much, much easier because they have no Software Sources gui and Synaptic is poorly modified.

thanks for teaching me that trick :)

sounds good! i'll edit it up, then. :)

---

### Post by nanotube on 2010-01-06
> **aysiu said:**
> It'd be nice to have a little *if* statement to see if the source is already in there before adding it as a potential duplicate source. What would that command look like?

well, it would be something like:
```

if ! grep -q '^deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main'; then echo "deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null; fi

```

but that would make the command much longer... and i do say "check your sources.list after it to make sure it looks good"...

so, do you really think complicating and lengthening the command is worth it? especially considering that duplicate repositories don't really do any harm (only generate some warning messages)?

---

### Post by aysiu on 2010-01-07
> **nanotube said:**
> well, it would be something like:
```

if ! grep -q '^deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main'; then echo "deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null; fi

```

but that would make the command much longer... and i do say "check your sources.list after it to make sure it looks good"...

so, do you really think complicating and lengthening the command is worth it? especially considering that duplicate repositories don't really do any harm (only generate some warning messages)?
My understanding (perhaps incorrect or outdated) is that having duplicate sources somehow prevents proper repository reloading. Or are you saying the error messages are there but just harmless?

I can definitely see where you're coming from on not trying to make the command too convoluted, though.

---

### Post by nanotube on 2010-01-07
> **aysiu said:**
> My understanding (perhaps incorrect or outdated) is that having duplicate sources somehow prevents proper repository reloading. Or are you saying the error messages are there but just harmless?

I can definitely see where you're coming from on not trying to make the command too convoluted, though.

it's not an error, it's just a warning on duplicate repositories, and is essentially harmless (you can try it yourself by putting in a duplicate of some repository and see what happens).

not only that, the warning is also very clear on what's going on, so if someone gets it, he should be able to figure out that there is a duplicate and he should go and delete it:
```

W: Duplicate sources.list entry http://switch.dl.sourceforge.net all/main Packages (/var/lib/apt/lists/switch.dl.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages)

```

---

### Post by aysiu on 2010-01-07
Cool beans.

---

### Post by aysiu on 2010-01-12
Just installed *firefox-mozilla-build* and it didn't appear to symlink the plugins, so no site was acknowledging I had Flash installed.

I had to do a manual symlink: ```
username@ubuntu:~$ cd /opt/firefox/
username@ubuntu:/opt/firefox$ ls
application.ini             libfreebl3.so    libxul.so
blocklist.xml               libmozjs.so      modules
browserconfig.properties    libnspr4.so      mozilla-xremote-client
chrome                      libnss3.so       old-homepage-default.properties
components                  libnssckbi.so    platform.ini
crashreporter               libnssdbm3.chk   plugins
crashreporter.ini           libnssdbm3.so    README.txt
crashreporter-override.ini  libnssutil3.so   removed-files
defaults                    libplc4.so       res
dictionaries                libplds4.so      run-mozilla.sh
extensions                  libsmime3.so     searchplugins
firefox                     libsoftokn3.chk  Throbber-small.gif
firefox-bin                 libsoftokn3.so   update.locale
greprefs                    libsqlite3.so    updater
icons                       libssl3.so       updater.ini
libfreebl3.chk              libxpcom.so
username@ubuntu:/opt/firefox$ ls -l plugins/
total 16
-rwxr-xr-x 1 root root 15824 2009-12-21 16:23 libnullplugin.so
username@ubuntu:/opt/firefox$ ls -l
total 17876
-rw-r--r-- 1 root root     2126 2009-12-21 16:23 application.ini
-rw-r--r-- 1 root root     2552 2009-12-21 16:23 blocklist.xml
-rw-r--r-- 1 root root      232 2009-12-21 16:23 browserconfig.properties
drwxr-xr-x 3 root root     4096 2010-01-11 19:41 chrome
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 components
-rwxr-xr-x 1 root root    45912 2009-12-21 16:23 crashreporter
-rw-r--r-- 1 root root     3801 2009-12-21 16:23 crashreporter.ini
-rw-r--r-- 1 root root      583 2009-12-21 16:23 crashreporter-override.ini
drwxr-xr-x 5 root root     4096 2010-01-11 19:41 defaults
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 dictionaries
drwxr-xr-x 3 root root     4096 2010-01-11 19:41 extensions
-rwxr-xr-x 1 root root     3883 2009-12-21 16:23 firefox
-rwxr-xr-x 1 root root    58228 2009-12-21 16:23 firefox-bin
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 greprefs
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 icons
-rw-r--r-- 1 root root      478 2009-12-21 16:23 libfreebl3.chk
-rwxr-xr-x 1 root root   321140 2009-12-21 16:23 libfreebl3.so
-rwxr-xr-x 1 root root   839912 2009-12-21 16:23 libmozjs.so
-rwxr-xr-x 1 root root   200736 2009-12-21 16:23 libnspr4.so
-rwxr-xr-x 1 root root   863000 2009-12-21 16:23 libnss3.so
-rwxr-xr-x 1 root root   338076 2009-12-21 16:23 libnssckbi.so
-rw-r--r-- 1 root root      478 2009-12-21 16:23 libnssdbm3.chk
-rwxr-xr-x 1 root root   122908 2009-12-21 16:23 libnssdbm3.so
-rwxr-xr-x 1 root root    78800 2009-12-21 16:23 libnssutil3.so
-rwxr-xr-x 1 root root    13180 2009-12-21 16:23 libplc4.so
-rwxr-xr-x 1 root root     8748 2009-12-21 16:23 libplds4.so
-rwxr-xr-x 1 root root   125644 2009-12-21 16:23 libsmime3.so
-rw-r--r-- 1 root root      478 2009-12-21 16:23 libsoftokn3.chk
-rwxr-xr-x 1 root root   194128 2009-12-21 16:23 libsoftokn3.so
-rwxr-xr-x 1 root root   447000 2009-12-21 16:23 libsqlite3.so
-rwxr-xr-x 1 root root   160140 2009-12-21 16:23 libssl3.so
-rwxr-xr-x 1 root root    12160 2009-12-21 16:23 libxpcom.so
-rwxr-xr-x 1 root root 14204400 2009-12-21 16:23 libxul.so
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 modules
-rwxr-xr-x 1 root root    10996 2009-12-21 16:23 mozilla-xremote-client
-rw-r--r-- 1 root root      112 2009-12-21 16:23 old-homepage-default.properties
-rw-r--r-- 1 root root      136 2009-12-21 16:23 platform.ini
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 plugins
-rw-r--r-- 1 root root      177 2009-12-21 16:23 README.txt
-rw-r--r-- 1 root root    15861 2009-12-21 16:23 removed-files
drwxr-xr-x 6 root root     4096 2010-01-11 19:41 res
-rwxr-xr-x 1 root root    10450 2009-12-21 16:23 run-mozilla.sh
drwxr-xr-x 2 root root     4096 2010-01-11 19:41 searchplugins
-rw-r--r-- 1 root root      825 2009-12-21 16:23 Throbber-small.gif
-rw-r--r-- 1 root root        6 2009-12-21 16:23 update.locale
-rwxr-xr-x 1 root root    70472 2009-12-21 16:23 updater
-rw-r--r-- 1 root root      143 2009-12-21 16:23 updater.ini
username@ubuntu:/opt/firefox$ sudo mv plugins plugins.old
[sudo] password for username: 
username@ubuntu:/opt/firefox$ sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
username@ubuntu:/opt/firefox$ 
```

---

### Post by nanotube on 2010-01-12
hm, which version of ubuntu?
firefox should automatically look for plugins in /usr/lib/mozilla/plugins ,
and at least since hardy, that's one of the directories where all the plugins get included...

---

### Post by aysiu on 2010-01-12
I'm using Karmic.

I don't know that it was symlinked to /usr/lib/mozilla, but on my installation, that doesn't appear to have the Flash plugin: ```
ls /usr/lib/mozilla/plugins/
librhythmbox-itms-detection-plugin.so  libvlcplugin.so  nppdf.so

```

---

### Post by nanotube on 2010-01-12
> **aysiu said:**
> I'm using Karmic.

I don't know that it was symlinked to /usr/lib/mozilla, but on my installation, that doesn't appear to have the Flash plugin: ```
ls /usr/lib/mozilla/plugins/
librhythmbox-itms-detection-plugin.so  libvlcplugin.so  nppdf.so

```

hrm, strange - kansasnoob said plugins worked for him... (and they do for me on my intrepid install, and all the plugins show up in /usr/lib/mozilla/plugins.)  

which flash package do you have installed? 

what do you get for:
```
locate *flash*.so
```

---

### Post by nanotube on 2010-01-12
i looked at the source of the flashplugin-installed karmic package, and it /does/ install a link in /usr/lib/mozilla/plugins.

specifically, the postinst script among the lines 103-120 which is where the update-alternatives script gets run, contain the following:
```

for p in $VARIANTS; do 
   update-alternatives --quiet --install "/usr/lib/$p/plugins/flashplugin-alternative.so" "$p-flashplugin" /usr/lib/flashplugin-installer/libflashplayer.so 50

```

and $VARIANTS is set on line 25 to:
```
VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"
```

among which you'll notice 'mozilla'. so if you have flashplugin-installed package installed, it should have installed a symlink to the flashplugin in /usr/lib/mozilla/plugins

---

### Post by aysiu on 2010-01-12
This is what I get: ```
sudo updatedb
locate *flash*.so
/opt/Adobe/Reader9/Reader/intellinux/lib/libflashsupport.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

---

### Post by nanotube on 2010-01-12
> **aysiu said:**
> This is what I get: ```
sudo updatedb
locate *flash*.so
/opt/Adobe/Reader9/Reader/intellinux/lib/libflashsupport.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

hrm well which flash package do you have installed? can you look up in synaptic?

or try
```
dpkg -S /usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

---

### Post by aysiu on 2010-01-12
```
dpkg -S /usr/lib/xulrunner-addons/plugins/libflashplayer.so
dpkg: /usr/lib/xulrunner-addons/plugins/libflashplayer.so not found.
``` Maybe I don't have a Flash package installed. Maybe that's the problem. Weird. Okay, I guess it's a non-issue. Not sure what happened there. I don't remember manually installing Flash...

---

### Post by nanotube on 2010-01-12
> **aysiu said:**
> ```
dpkg -S /usr/lib/xulrunner-addons/plugins/libflashplayer.so
dpkg: /usr/lib/xulrunner-addons/plugins/libflashplayer.so not found.
``` Maybe I don't have a Flash package installed. Maybe that's the problem. Weird. Okay, I guess it's a non-issue. Not sure what happened there. I don't remember manually installing Flash...

well, if it was stuffed in there by a post-install script, it wouldn't show up in dpkg -S... check out what shows up in synaptic - just because now i'm rather curious! :)

EDIT: to clarify, what shows up as /installed/ in synaptic, if you search by name for 'flash'.

all that said - i'm sure if you install the flashplugin-installer package, everything will work without symlinking the /opt/firefox/plugins dir.

---

### Post by aysiu on 2010-01-12
Yeah, I removed the symlink, installed *flashplugin-nonfree*, and it's working just fine. Sorry for the false alarm.

---

### Post by nanotube on 2010-01-12
> **aysiu said:**
> Yeah, I removed the symlink, installed *flashplugin-nonfree*, and it's working just fine. Sorry for the false alarm.

hey no prob. :)

hrm, i guess now we'll never know where that libflashplayer.so that you had in xulrunner-addons came from...

---

### Post by aysiu on 2010-01-15
On the installation part of the page, it says > All of this can also be done through the GUI with the Synaptic Package Manager, if you so desire. I'd like to create a tutorial showing people how to do this, just because some folks *are* intimidated by the terminal.

What's the GUI way to do this command, though? ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
``` Is there an address I can just download the key from? When I go to keyserver.ubuntu.com, I get nothing.

---

### Post by nanotube on 2010-01-16
> **aysiu said:**
> On the installation part of the page, it says  I'd like to create a tutorial showing people how to do this, just because some folks *are* intimidated by the terminal.


a superb idea! 

> 
What's the GUI way to do this command, though? ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
``` Is there an address I can just download the key from? When I go to keyserver.ubuntu.com, I get nothing.

well, you can browse the keyserver with the browser if you use the right port:
[http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/)

there, search for 'ubuntuzilla' and the ubuntuzilla signing key will come up.

here's a direct link:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCCC158AFC1289A29](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCCC158AFC1289A29)
(which is probably better to use because anyone can add a key with 'ubuntuzilla' in the description, and then the 'ubuntuzilla' search will come up with multiple keys...)

alternatively: i can just host a copy of the key on something like ubuntuzilla.sourceforge.net/signingkey.txt
which a user can just 'save as' from a browser, if you think it would be easier...

---

### Post by aysiu on 2010-01-18
Thanks. I've set up a page. Doing it point-and-click is rather tedious, but I think it's important to show it can be done for those who are really intimidated by the terminal (as I was when I first started using Linux):
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

---

### Post by nanotube on 2010-01-18
> **aysiu said:**
> Thanks. I've set up a page. Doing it point-and-click is rather tedious, but I think it's important to show it can be done for those who are really intimidated by the terminal (as I was when I first started using Linux):
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

looks great! thanks for all the effort you put into this! 
i have linked to it from the installation instructions. :)

---

### Post by aysiu on 2010-01-18
That's great.

---

### Post by nanotube on 2010-01-20
hey friends
so i just pushed out the thunderbird 3.0.1 release.

if you happen to not have installed it yet, could you check to see if it shows up in synaptic, in section 'status -> installed (upgradeable)' ?

a person in this thread (see the latest few posts):
[http://ubuntuforums.org/showthread.php?t=1323239](http://ubuntuforums.org/showthread.php?t=1323239)

says it doesn't show up there for him, though it does for me, so i'd like to see if anyone else is seeing the same problem. 

would appreciate some responses on this.

---

### Post by kansasnoob on 2010-01-20
I just booted into Hardy. I was trying this previously in Jaunty, more about that later. So I checked to be absolutely sure, thunderbird-mozilla-build is installed and it's version 3.0. Off to Synaptic I go.

Synaptic verifies I have 3.0-0ubuntu1 thunderbird-mozilla-build. So I'm going to click on Reload.

Well that worked fine. It showed an update to all three mozilla-build packages (I hadn't been here since our last testing) and they went off without a hitch.

I need to go back to .......... hmmmmm, maybe Karmic and try this.

I'd swear when I tried this in Jaunty earlier that I started with 3.0 and ended up with 3.0.1, but **silently**. That is it didn't show up in notifications.

I don't think it would do any good to try again in Jaunty because even if I removed the Ubuntuzilla repo, and then reinstalled, I'd get the new 3.0.1 package initially.

Stay tuned.

---

### Post by kansasnoob on 2010-01-20
Actual update log from Hardy:

> Commit Log for Wed Jan 20 14:32:42 2010


Upgraded the following packages:
bind9-host (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
dnsutils (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
firefox-3.0 (3.0.16+nobinonly-0ubuntu0.8.04.1) to 3.0.17+nobinonly-0ubuntu0.8.04.1
firefox-3.0-gnome-support (3.0.16+nobinonly-0ubuntu0.8.04.1) to 3.0.17+nobinonly-0ubuntu0.8.04.1
firefox-mozilla-build (3.5.7-0ubuntu1) to 3.5.7-0ubuntu2
gzip (1.3.12-3.2) to 1.3.12-3.2ubuntu0.1
libbind9-30 (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
libdns36 (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
libexpat1 (2.0.1-0ubuntu1) to 2.0.1-0ubuntu1.1
libisc35 (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
libisccc30 (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
libisccfg30 (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
libkrb53 (1.6.dfsg.3~beta1-2ubuntu1.1) to 1.6.dfsg.3~beta1-2ubuntu1.3
liblwres30 (1:9.4.2.dfsg.P2-2ubuntu0.4) to 1:9.4.2.dfsg.P2-2ubuntu0.5
libssl0.9.8 (0.9.8g-4ubuntu3.8) to 0.9.8g-4ubuntu3.9
libthai-data (0.1.9-1) to 0.1.9-1ubuntu0.2
libthai0 (0.1.9-1) to 0.1.9-1ubuntu0.2
linux-ubuntu-modules-2.6.24-26-generic (2.6.24-26.43) to 2.6.24-26.44
openssl (0.9.8g-4ubuntu3.8) to 0.9.8g-4ubuntu3.9
seamonkey-mozilla-build (2.0.1-0ubuntu1) to 2.0.2-0ubuntu1
thunderbird-mozilla-build (3.0-0ubuntu1) to 3.0.1-0ubuntu1
xulrunner-1.9 (1.9.0.16+nobinonly-0ubuntu0.8.04.1) to 1.9.0.17+nobinonly-0ubuntu0.8.04.1
xulrunner-1.9-gnome-support (1.9.0.16+nobinonly-0ubuntu0.8.04.1) to 1.9.0.17+nobinonly-0ubuntu0.8.04.1


Oops, should have used code tags.

---

### Post by kansasnoob on 2010-01-20
OK I'm in Karmic (after two hard lock-ups, arrgh):

```
lance@lance-desktop:~$ apt-cache showpkg thunderbird-mozilla-build
Package: thunderbird-mozilla-build
Versions: 
**3.0-0ubuntu2** (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages
                  MD5: c434c891d1eeee96dcc3636efa639cab


Reverse Depends: 
Dependencies: 
3.0-0ubuntu2 - 
Provides: 
3.0-0ubuntu2 - thunderbird 
Reverse Provides: 

```

Because of the frequency of hard lockups in Karmic I'm going to send these a chunk at a time :(

---

### Post by kansasnoob on 2010-01-20
After running apt-get update I get this:

```
lance@lance-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bind9-host dnsutils gnome-power-manager gzip libbind9-50 libdns50 libdns53
  libexpat1 libgssapi-krb5-2 libisc50 libisccc50 libisccfg50 libk5crypto3
  libkrb5-3 libkrb5support0 liblwres50 **thunderbird-mozilla-build**
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1MB of archives.
After this operation, 4,096B disk space will be freed.

```

Looks OK, I'll check Synaptic now.

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> After running apt-get update I get this:

```
lance@lance-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bind9-host dnsutils gnome-power-manager gzip libbind9-50 libdns50 libdns53
  libexpat1 libgssapi-krb5-2 libisc50 libisccc50 libisccfg50 libk5crypto3
  libkrb5-3 libkrb5support0 liblwres50 **thunderbird-mozilla-build**
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1MB of archives.
After this operation, 4,096B disk space will be freed.

```

Looks OK, I'll check Synaptic now.

yea, checking to see whether it shows up in synaptic, under status -> installed (upgradeable) was the very thing i was asking to test - i already know everything else works ;)

---

### Post by kansasnoob on 2010-01-20
No problem in Karmic but I'd swear that in Jaunty it updated silently. That is, the update completed, but with no notification.

Is there any way of trying to duplicate that?

---

### Post by kansasnoob on 2010-01-20
> **nanotube said:**
> yea, checking to see whether it shows up in synaptic, under status -> installed (upgradeable) was the very thing i was asking to test - i already know everything else works ;)

Sorry, it was a long morning of Gparted bug testing:

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179)

I still have Lucid to look at, but in Jaunty I used Synaptic and I swear the update completed but it was **silent**. That is it showed no notification anywhere! Not in Update Manager, nor the panel, nor Synaptic.

But it did update. then I thought I must be just goofy and decided to look at the behavior in Hardy. Now in Karmic.

Is there a way to duplicate the behavior in Jaunty?

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> No problem in Karmic but I'd swear that in Jaunty it updated silently. That is, the update completed, but with no notification.

Is there any way of trying to duplicate that?

so, you're saying that you got upgraded to thunderbird 3.0.1, without doing anything at all? not even a "sudo apt-get upgrade" ?  are you sure?

i don't think that's really possible... there is the checkbox somewhere in synaptic config to "install security updates automatically" but i think that only applies to stuff in the $distro-security section of the ubuntu repositories.

of course, if you happen to have stuck a "apt-get upgrade -y" into the system crontab, anything may happen... but you'd know if you did that. :)

---

### Post by kansasnoob on 2010-01-20
This may be helpful:

[ATTACH]144294[/ATTACH]

And yet look at the list of upgradable packages:

```
apport-symptoms (version 0.4) will be upgraded to version 0.5
fontconfig (version 2.6.0-1ubuntu13) will be upgraded to version 2.8.0-2ubuntu1
fontconfig-config (version 2.6.0-1ubuntu13) will be upgraded to version 2.8.0-2ubuntu1
gdm (version 2.29.5-0ubuntu4) will be upgraded to version 2.29.5-0ubuntu5
gnome-panel (version 1:2.29.5.1-0ubuntu1) will be upgraded to version 1:2.29.5.1-0ubuntu2
gnome-panel-data (version 1:2.29.5.1-0ubuntu1) will be upgraded to version 1:2.29.5.1-0ubuntu2
libfontconfig1 (version 2.6.0-1ubuntu13) will be upgraded to version 2.8.0-2ubuntu1
libpanel-applet2-0 (version 1:2.29.5.1-0ubuntu1) will be upgraded to version 1:2.29.5.1-0ubuntu2
software-center (version 1.1.8) will be upgraded to version 1.1.9
xdg-utils (version 1.0.2-6.1) will be upgraded to version 1.0.2-6.1ubuntu1

```

That is all done from Synaptic!

I'll be back after running the updates.

---

### Post by kansasnoob on 2010-01-20
> **nanotube said:**
> so, you're saying that you got upgraded to thunderbird 3.0.1, without doing anything at all? not even a "sudo apt-get upgrade" ?  are you sure?

i don't think that's really possible... there is the checkbox somewhere in synaptic config to "install security updates automatically" but i think that only applies to stuff in the $distro-security section of the ubuntu repositories.

of course, if you happen to have stuck a "apt-get upgrade -y" into the system crontab, anything may happen... but you'd know if you did that. :)

No! I was using only Synaptic in Jaunty. 

Before clicking on Reload I'd have sworn that the version was 3.0. I saw no notification of an update to thunderbird-mozilla-build, but afterward the version showed 3.0.1 and I assumed that I was just wrong!

Wait!

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> This may be helpful:

[ATTACH]144294[/ATTACH]

And yet look at the list of upgradable packages:

```
apport-symptoms (version 0.4) will be upgraded to version 0.5
fontconfig (version 2.6.0-1ubuntu13) will be upgraded to version 2.8.0-2ubuntu1
fontconfig-config (version 2.6.0-1ubuntu13) will be upgraded to version 2.8.0-2ubuntu1
gdm (version 2.29.5-0ubuntu4) will be upgraded to version 2.29.5-0ubuntu5
gnome-panel (version 1:2.29.5.1-0ubuntu1) will be upgraded to version 1:2.29.5.1-0ubuntu2
gnome-panel-data (version 1:2.29.5.1-0ubuntu1) will be upgraded to version 1:2.29.5.1-0ubuntu2
libfontconfig1 (version 2.6.0-1ubuntu13) will be upgraded to version 2.8.0-2ubuntu1
libpanel-applet2-0 (version 1:2.29.5.1-0ubuntu1) will be upgraded to version 1:2.29.5.1-0ubuntu2
software-center (version 1.1.8) will be upgraded to version 1.1.9
xdg-utils (version 1.0.2-6.1) will be upgraded to version 1.0.2-6.1ubuntu1

```

That is all done from Synaptic!

I'll be back after running the updates.

the screenshot you attached shows that package thunderbird-mozilla-build is not installed (the box on the left is not green).

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> No! I was using only Synaptic in Jaunty. 

Before clicking on Reload I'd have sworn that the version was 3.0. I saw no notification of an update to thunderbird-mozilla-build, but afterward the version showed 3.0.1 and I assumed that I was just wrong!

Wait!

if the screenshot you posted is right - then the version 3.0.1 is simply shown as 'available'. since the package is not installed, it is not offered for upgrade, or notifying you of the presence of upgrade. that explains everything.

---

### Post by kansasnoob on 2010-01-20
OK! I think I know what the deal is!

If the package is installed Synaptic shows the update correctly.

If the package is not installed it does NOT update but rather stays at the version last installed (or the original version when the PPA was installed).

I saw no change from that screenshot until I installed Thunderbird and now:

[ATTACH]144299[/ATTACH]

Does that make any sense at all?

But no notification of that package update showed up previously or just now in Lucid.

How to sort that out I have no idea.

---

### Post by kansasnoob on 2010-01-20
> **nanotube said:**
> if the screenshot you posted is right - then the version 3.0.1 is simply shown as 'available'. since the package is not installed, it is not offered for upgrade, or notifying you of the presence of upgrade. that explains everything.

We're posting over each other :D

Sorry I didn't post my original results from Jaunty but I thought I must have just screwed up. I hope this helps.

Feel free to shout anytime.

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> We're posting over each other :D


hehe yea looks like it

> 
Sorry I didn't post my original results from Jaunty but I thought I must have just screwed up. I hope this helps.

Feel free to shout anytime.

well, for all that, you still haven't shown me whether it shows up in the 'upgradeable' section in synaptic.
please see the last few posts in this thread (and the latest screenshot i posted), to see exactly what i'm looking for:
[http://ubuntuforums.org/showthread.php?t=1323239](http://ubuntuforums.org/showthread.php?t=1323239)

sorry if i haven't made clear what i was trying to do!

---

### Post by kansasnoob on 2010-01-20
Hey I hit post #200. Does that mean I get to use Ubuntuzilla for free forever?

I wish I knew 10% of what you know.

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> Hey I hit post #200. Does that mean I get to use Ubuntuzilla for free forever?


as it happens - yes you do! :D

> 
I wish I knew 10% of what you know.

you're being way too generous in your assessment of what i know. ;)

---

### Post by kansasnoob on 2010-01-20
> **nanotube said:**
> hehe yea looks like it



well, for all that, you still haven't shown me whether it shows up in the 'upgradeable' section in synaptic.
please see the last few posts in this thread (and the latest screenshot i posted), to see exactly what i'm looking for:
[http://ubuntuforums.org/showthread.php?t=1323239](http://ubuntuforums.org/showthread.php?t=1323239)

sorry if i haven't made clear what i was trying to do!

No, it doesn't. I did especially look in this last test and the update shows up nowhere. Not even using filters.

Although it worked perfectly in Hardy!

I suspect a change between Intrepid and Jaunty.

---

### Post by nanotube on 2010-01-20
> **kansasnoob said:**
> No, it doesn't. I did especially look in this last test and the update shows up nowhere. Not even using filters.

Although it worked perfectly in Hardy!

I suspect a change between Intrepid and Jaunty.

well, i know it won't show up for you in jaunty, because thunderbird-mozilla-build was not installed. so of course, it won't be in section "**installed** (upgradeable)". :) 

i was hoping you could look at it on a system where you did have 3.0 installed.

---

### Post by kansasnoob on 2010-01-20
OK, last OS. Mint Gloria (which is Jaunty with some tweaks), yes!

Once it's installed it does show up in the Installed (upgradeable) category.

So it does matter whether it's installed or not.

BTW Karmic was rough but the newest Mint was 10 times worse!

Hey, I'm really tired, time to rest a bit :)

---

### Post by nanotube on 2010-01-20
thanks!

looks like you've had a rough day - enjoy your rest :)

---

### Post by aysiu on 2010-01-20
For the record, worked for me in Karmic i386.

---

### Post by nanotube on 2010-01-20
> **aysiu said:**
> For the record, worked for me in Karmic i386.

cool, thanks :)

---

### Post by aysiu on 2010-01-22
Feature request:

(Not sure what you think about this, how much time you have for this, or how much work it would require)\

Even though I spent quite a bit of time putting together GUI instructions for adding the repository and signing key, what if UbuntuZilla had a .deb you could double-click, and the .deb would see if you already had the repository in /etc/apt/sources.list, add it if necessary, and add the signing key for the repository?

---

### Post by nanotube on 2010-01-22
> **aysiu said:**
> Feature request:

(Not sure what you think about this, how much time you have for this, or how much work it would require)\

Even though I spent quite a bit of time putting together GUI instructions for adding the repository and signing key, what if UbuntuZilla had a .deb you could double-click, and the .deb would see if you already had the repository in /etc/apt/sources.list, add it if necessary, and add the signing key for the repository?

hrm, well, that would certainly be a possibility... if i get around to it, i'll see about whipping it up in the next couple of weeks.

that said, copy-pasting 4 commands to enable the repository is just not that hard, so i'm not sure if a 'custom solution' is worth it...

if anything, probably implementing this spec:
[https://wiki.ubuntu.com/repoadder](https://wiki.ubuntu.com/repoadder)
would be a much more productive use of time, since it would be useable by everyone. 

hmm, in fact, i just think i'll try working on that in my spare time. :)

EDIT: it seems that another spec, [https://wiki.ubuntu.com/ThirdPartyApt](https://wiki.ubuntu.com/ThirdPartyApt) is further along the lines of implementation already.

---

### Post by aysiu on 2010-01-22
I've never heard of repoadder or ThirdPartyApt. They both look promising.

Yeah, I realize four commands is pretty easy, but to a new user scared of the terminal (as I was five years ago), even that can be (albeit irrationally) intimidating.

The simpler the better, if it's not too much trouble to implement, of course.

---

### Post by nanotube on 2010-01-22
> **aysiu said:**
> I've never heard of repoadder or ThirdPartyApt. They both look promising.

Yeah, I realize four commands is pretty easy, but to a new user scared of the terminal (as I was five years ago), even that can be (albeit irrationally) intimidating.

The simpler the better, if it's not too much trouble to implement, of course.

well, i'll give you a ping when i have something for you to try in this department. :)

---

### Post by aysiu on 2010-01-22
I'd be glad to test it.

---

### Post by nanotube on 2010-01-22
> **aysiu said:**
> I'd be glad to test it.

cool!

---

### Post by kansasnoob on 2010-02-07
Just a suggestion, where your instructions say:

> If you wish, verify that the repository has been added, by looking at /etc/apt/sources.list in your favorite text editor. 

I think this would be safer:

> If you wish, verify that the repository has been added, by running the command "cat /etc/apt/sources.list". 

What do you think?

---

### Post by nanotube on 2010-02-10
hm, not a bad idea, though i think i'll go with 'tail' instead of 'cat'. :)

---

### Post by Levis 1 on 2010-06-17
What will show up is every name you've given law enforcement, courts, or  corrections - as long as they made the connection between your old name  and your new name.  If nobody realized that John.

---

### Post by nanotube on 2012-01-06
Would anyone care to test that adding the ubuntuzilla repository using add-apt-repository works well for you on Lucid and later? And confirm that it includes the automatic import of the gpg key?

Specifically, this command:
```
sudo add-apt-repository 'deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main'
```

Thank you! :)

---

### Post by michael37 on 2012-01-06
> **nanotube said:**
> Would anyone care to test that adding the ubuntuzilla repository using add-apt-repository works well for you on Lucid and later? And confirm that it includes the automatic import of the gpg key?

Specifically, this command:
```
sudo add-apt-repository 'deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main'
```

Thank you! :)

nanotube, dumb question admittedly, but what's the point? New releases of Ubuntu switched to the new Firefox timeline and are shipping "latest and greatest".

---

### Post by nanotube on 2012-01-06
> **michael37 said:**
> nanotube, dumb question admittedly, but what's the point? New releases of Ubuntu switched to the new Firefox timeline and are shipping "latest and greatest".

good question. the answer is:
on oneiric, which is the latest release of ubuntu, 
seamonkey is still 2.4.1 (latest is 2.6.1)
firefox was just updated to 9.0.1 today (about a week after it was released) (admittedly, ubuntuzilla only updated a day earlier, because i was busy with other stuff and wanted to add 64bit support before i pushed out this release, but normally i try to do next-day release).
thunderbird is still 8.0 (latest is 9.0.1)

on ubuntu lucid lts, all of these are even older.

hope that clarifies things. :)

---

### Post by michael37 on 2012-01-06
> **nanotube said:**
> ...
on ubuntu lucid lts, all of these are even older.

hope that clarifies things. :)

On Lucid and Maverick, users can use Firefox Stable [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable) and Thunderbird Stable [https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable) 

Both had 9.0 since December...

---

### Post by mikewhatever on 2012-01-06
> **nanotube said:**
> Would anyone care to test that adding the ubuntuzilla repository using add-apt-repository works well for you on Lucid and later? And confirm that it includes the automatic import of the gpg key?

Specifically, this command:
```
sudo add-apt-repository 'deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main'
```

Thank you! :)

Unfortunately, no, the repository is added, but no key is imported. Here's what I get when running 'apt-get update' on 11.04 64bit:
```

~$ sudo apt-get update
...
Get:57 http://downloads.sourceforge.net all/main amd64 Packages [849 B]
Get:58 http://downloads.sourceforge.net all/main i386 Packages [847 B]                                  
Err http://downloads.sourceforge.net all/main Sources                                                   
  404  Not Found
Ign http://downloads.sourceforge.net all/main Translation-en_US                                         
Ign http://downloads.sourceforge.net all/main Translation-en                                            
Fetched 1,194 kB in 9s (132 kB/s)                                                                       
W: GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/source/Sources  404  Not Found

```


...and thank you for reviving the project!

---

### Post by Karlchen on 2012-01-06
Hello, nanotube.

```
sudo add-apt-repository 'deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main'
```Good news and bad news (basically same result as reported by Mikewhatever):

[U]Good news first:
[/U] > ubuntu@ubuntu:~$ sudo add-apt-repository 'deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main'
ubuntu@ubuntu:~$ echo $?
0
ubuntu@ubuntu:~$ The repository was successfully added to the file /etc/apt/sources.list
Using Synaptic the Ubuntuzilla repository was queried successfully and Firefox 9.0.1, Thunderbird 9.0.1 and Seamonkey 2.6.1 were added to the list.
Yet, a warning was displayed by Synaptic, too.

[U]Bad news second:
[/U]The signature could not be verified because the public Ubuntuzilla key was missing. > W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: Die folgenden Signaturen konnten nicht überprüft werden, weil ihr öffentlicher Schlüssel nicht verfügbar ist: NO_PUBKEY CCC158AFC1289A29(The following signatures could not be verified because their public keys were unavailable: NO_PUBKEY CCC158AFC1289A29)

Running the command ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
``` fixed the problem.

Is there any particular reason for trying to replace the two commands which you give on the [Sourceforge page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation") and which still work fine: ```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```Oh, before I forget: the tests were done on: Ubuntu 10.04.3 Desktop 64-bit.

Kind regards,
Karl
--
Corrected: Ubuntu 10.04.3 Desktop 64-bit, not 32-bit

---

### Post by Karlchen on 2012-01-06
Hello, nanotube.

Almost the same results for Ubuntu 11.04 Desktop 64-bit.
I.e. your commandline fails to get the appropriate public key.
Difference to Ubuntu 10.04:
The commandline ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CCC158AFC1289A29
```does not fix the public key problem. It will be downloaded and installed, but Synaptic keeps on complaining about it.

Only be removing the downloaded public key and the repository entry and by running the old commands 
```
echo -e "\ndeb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
``` next, the problems could be fixed.

Kind regards,
Karl
--
Corrected: Ubuntu 11.04 Desktop 64-bit, not 32-bit.

---

### Post by Karlchen on 2012-01-06
Hello, nanotube.

Final report for Ubuntu 11.10 Desktop 32-bit:
Basically, same problems as experienced before on Lucid and Natty.
In the end only resorting to the old commands would achieve the goal without problems.

Absolutely and ultimately final report for Ubuntu 11.10 Desktop 64-bit:
Same problems as reported before.
Using the 2 command lines found on your Sourceforge webpage: apt list updated, public key imported, Software Centre offers Ubuntuzilla software.
Downloaded and installed Firefox 9.0.1 64-bit and using it right now. 

Kind regards,
Karl

---

### Post by nanotube on 2012-01-08
Hi guys
thanks for testing
some doc i saw suggested that add-apt-repository may also automatically fetch the key, which would have been nice, to go from two commands to one.
since it doesn't do that, then i suppose it doesn't really matter, other than the fact that add-apt-repository would be shorter and look nicer than the current echo line :) 
so i guess we'll just leave it well enough alone.

---

### Post by nanotube on 2012-01-08
> **michael37 said:**
> On Lucid and Maverick, users can use Firefox Stable [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable) and Thunderbird Stable [https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable) 

Both had 9.0 since December...

yes the -stable repos are also good alternatives. they don't offer seamonkey though, but they do the job just fine if all you want is ff/tb, and you happen to be on lucid or maverick, and not on any of the other currently-supported releases. (and they don't use official mozilla builds, though that is probably irrelevant for most). i used to recommend those to people on 64bit systems.

---

