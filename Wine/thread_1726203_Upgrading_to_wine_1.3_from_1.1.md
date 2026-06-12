---
title: "Upgrading to wine 1.3 from 1.1"
date: 2011-04-10
forum: Wine
---

### Post by BlackRat90 on 2011-04-10
Im trying to get Age of Empires 3 running, but according to the wine [website]("http://appdb.winehq.org/appview.php?iVersionId=3795&iTestingId=10297") it only really works on 1.3

So I tried downloading the wine 1.3 packages from the synaptic package manager, but it still says my version of Wine is 1.1.44

Do I need to reinstall wine? I don't understand why its not updating.

---

### Post by Enigmapond on 2011-04-10
Try doing from the PPA. Open a terminal and do:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BlackRat90 on 2011-04-10
I had already tried adding that ppa when before I tried to get the packages from synaptic. (sorry forgot to mention that)

I tried anyways, and it didnt update anything.

```


nate@Rats:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
nate@Rats:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Get:2 http://dl.google.com stable Release [1,347B]                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                             
Get:3 http://dl.google.com stable/main Packages [1,086B]                       
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Fetched 2,630B in 1s (2,451B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Enigmapond on 2011-04-10
Are you certain you ran an update prior? The newer version 1.3 was just re-built and that will override anything coming from the main repos...run update, uninstall wine and then re-install it. It HAS to update to 1.3.

```
sudo apt-get update
sudo apt-get remove wine && sudo apt-get install wine
```

---

### Post by BlackRat90 on 2011-04-10
Its not working!! This is really starting to get at me....

I did all of that and still "wine --version" returned 1.1.44!

I made sure all the packages where dated, and then reinstalled and it stills give 1.1.44 :confused:

---

### Post by Enigmapond on 2011-04-10
Ok,,,plan C...go right to the source and get the deb...LOL Can;t understand why the normal way didn't click...:confused:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by BlackRat90 on 2011-04-10
Well this is quite odd, I removed wine and it still is active? And can run my windows programs???

Is it possible that I have two versions of Wine running???

---

### Post by Enigmapond on 2011-04-10
Maybe you needed to specify wine 1.3 but still.....

---

### Post by cogadh on 2011-04-10
Did you ever install Wine from the sources, i.e. did you compile it yourself rather than installing a packaged version? If so, you can't uninstall it via the package manager, you'll need to go to your sources directory and run a "make uninstall". 

If you didn't install from sources, then all you should need to do is uninstall whatever Wine you do have, either via Synaptic or the terminal, then either from the terminal run "sudo apt-get install wine1.3" or look for the Wine 1.3 package in Synaptic and install that.

---

### Post by Enigmapond on 2011-04-10
> **BlackRat90 said:**
> Well this is quite odd, I removed wine and it still is active? And can run my windows programs???

Is it possible that I have two versions of Wine running???

I don't think so but you can go to synaptic and kill everything wine and see what happens...LOL

---

### Post by BlackRat90 on 2011-04-10
> **cogadh said:**
> Did you ever install Wine from the sources, i.e. did you compile it yourself rather than installing a packaged version? If so, you can't uninstall it via the package manager, you'll need to go to your sources directory and run a "make uninstall". 

Now that you say that i remember way back when I started with ubuntu i think i installed this way ubuntu with out knowing any better

---

### Post by BlackRat90 on 2011-04-10
Where could I find the Sources Directory?

---

### Post by BlackRat90 on 2011-04-10
Ok, i went into the wine source directory and did "make uninstall"
but then I get this error:
 
> make: *** No rule to make target `uninstall'.  Stop.

---

### Post by Enigmapond on 2011-04-10
Sorry...didn't mean to bow out but I'm not good at compiling and the source directory would not necessarily be the WINE source directory if you compiled to a different one. Normally I compile to a folder in my Home directory. I hope you solve you issue.

Cheers!

---

### Post by BlackRat90 on 2011-04-10
Well I did whereis wine and got this:
```
wine: /usr/local/bin/wine /usr/local/lib/wine

```

im playing around with the /.wine/ folder for the source...
gah! the stupid things i did in ubuntu before i knew what i was doing...
Considering I am running the same install from back when i was working in 9.04 and have collected a lot of junk over the years, I am temped to just reinstall ubuntu all together >.<

---

### Post by cogadh on 2011-04-11
Those are not the source directories, those are the directories that Wine is installed in (bin is the Wine binaries, lib is the Wine libraries, .wine is the "fake Windows" directory). The source directory would be wherever you downloaded the Wine source code files to and ran the compile from, usually a directory within your home directory. If you no longer have that, you could manually delete the /usr/local/bin/wine and /usr/local/lib/wine directories to get rid of whatever Wine you still have installed.

---

