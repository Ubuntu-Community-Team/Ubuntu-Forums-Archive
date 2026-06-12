---
title: "&quot;Software updates can't be authenticated..."
date: 2011-04-24
forum: Security
---

### Post by welshmike on 2011-04-24
...a malicious individual could damage or take control of your system"
See: [https://dl-web.dropbox.com/get/Public/Screenshot1.png?w=ae903921](https://dl-web.dropbox.com/get/Public/Screenshot1.png?w=ae903921)
and: [https://dl-web.dropbox.com/get/Public/Screenshot2.png?w=2c144a02](https://dl-web.dropbox.com/get/Public/Screenshot2.png?w=2c144a02)

So should I really go ahead and install the updates or what may have gone wrong at the Ubuntu repository?

---

### Post by CharlesA on 2011-04-24
403 error - permission denied.

Post the terminal output after you run this:

```
sudo apt-get update
```

---

### Post by welshmike on 2011-04-24
Thanks for fast reply.

```
mike@mike-i3-laptop:~$ sudo apt-get update
[sudo] password for mike: 
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB       
Hit http://gb.archive.ubuntu.com lucid Release.gpg                             
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [62.9kB]
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://packages.medibuntu.org lucid Release.gpg                            
Get: 2 http://dl.google.com stable Release.gpg [197B]                          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://archive.canonical.com lucid Release                                 
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_GB
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://packages.medibuntu.org/ lucid/free Translation-en_GB                
Get: 3 http://dl.google.com stable Release [1,347B]                            
Get: 4 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,332B]
Get: 5 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [33.9kB]
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_GB              
Hit http://archive.canonical.com lucid/partner Packages                        
Get: 6 http://download.virtualbox.org lucid Release.gpg [197B]                 
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_GB            
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/contrib Translation-en_GB
Hit http://linux.dropbox.com lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Get: 7 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB  
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release                                 
Hit http://packages.medibuntu.org lucid Release                                
Hit http://gb.archive.ubuntu.com lucid-updates Release                         
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                     
Hit http://gb.archive.ubuntu.com lucid/main Sources                            
Hit http://gb.archive.ubuntu.com lucid/restricted Sources                      
Hit http://gb.archive.ubuntu.com lucid/universe Packages                       
Hit http://gb.archive.ubuntu.com lucid/universe Sources                        
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://packages.medibuntu.org lucid/free Packages                          
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Get: 8 http://dl.google.com stable/main Packages [1,097B]                      
Hit http://linux.dropbox.com lucid/main Packages                         
Get: 9 http://download.virtualbox.org lucid Release [5,429B]             
Ign http://download.virtualbox.org lucid Release
Hit http://download.virtualbox.org lucid/contrib Packages
Fetched 140kB in 2s (57.1kB/s)
Reading package lists... Done
W: GPG error: http://download.virtualbox.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
mike@mike-i3-laptop:~$ 
```

---

### Post by CharlesA on 2011-04-24
Ok. It looks like you forgot to add the key for the virtualbox repos.

Run this:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

From [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

Also, you have a duplicate line in /etc/apt/sources.list, fine it and remove it. :)

---

### Post by welshmike on 2011-04-24
Sorry. I can't see the duplicates. Can a younger man with good eyesight?

mike@mike-i3-laptop:~$ sudo gedit  /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

deb http://download.virtualbox.org/virtualbox/debian lucid contrib

```

---

### Post by CharlesA on 2011-04-24
Hrm. I don't see a duplicate either.

---

### Post by welshmike on 2011-04-25
I did
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add 
```
but got same message.
I then unticked VirtualBox and the other three updates were applied with no error.
So it is VirtualBox update that can't be authenticated.

---

### Post by tgm4883 on 2011-04-25
> **welshmike said:**
> Sorry. I can't see the duplicates. Can a younger man with good eyesight?

mike@mike-i3-laptop:~$ sudo gedit  /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

deb http://download.virtualbox.org/virtualbox/debian lucid contrib

```

There isn't a duplicate there, do you have any files listed in /etc/apt/sources.list.d/ ?

---

### Post by welshmike on 2011-04-25
Yes there are:
```
mike@mike-i3-laptop:~$ dir /etc/apt/sources.list.d 
dropbox.list		 lucid-partner.list   tualatrix-ppa-lucid.list
google-chrome.list	 medibuntu.list       tualatrix-ppa-lucid.list.save
google-chrome.list.save  medibuntu.list.save
mike@mike-i3-laptop:~$ 
```

---

### Post by CharlesA on 2011-04-25
rename/remove the lucid-partner.list file.

---

### Post by welshmike on 2011-04-25
Sorry, after removal problem still occurs.

---

### Post by tgm4883 on 2011-04-25
> **welshmike said:**
> Sorry, after removal problem still occurs.

You removed that file then ran 'apt-get update' and the problem still occurs? 

You will need to cat the rest of the files in that directory then and look for the dupe of the partner repo

---

### Post by welshmike on 2011-04-25
> **tgm4883 said:**
> You removed that file then ran 'apt-get update' and the problem still occurs? 

You will need to cat the rest of the files in that directory then and look for the dupe of the partner repo

```
mike@mike-i3-laptop:~$ sudo apt-get update
[sudo] password for mike: 
...
W: GPG error: http://download.virtualbox.org lucid Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org
```

---

### Post by tgm4883 on 2011-04-25
> **welshmike said:**
> ```
mike@mike-i3-laptop:~$ sudo apt-get update
[sudo] password for mike: 
...
W: GPG error: http://download.virtualbox.org lucid Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org
```

Well thats different from the other error we were dealing with.  What is the output of

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

---

### Post by welshmike on 2011-04-25
> **tgm4883 said:**
> Well thats different from the other error we were dealing with.  What is the output of

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

```
mike@mike-i3-laptop:~$ wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
[sudo] password for mike: 
OK
mike@mike-i3-laptop:~$ 
```

EDIT:
Maybe I should uninstall VirtualBox as it looks dodgy?

---

### Post by CharlesA on 2011-04-25
Virtualbox is fine. I use it and I'm sure many others do too.

Is it still giving you the same error when you run this:

```
sudo apt-get update
```

---

### Post by welshmike on 2011-04-25
```
mike@mike-i3-laptop:~$ sudo apt-get update
[sudo] password for mike: 
Hit http://security.ubuntu.com lucid-security Release.gpg
.
.
.

```
Last two lines are:
```
Hit http://packages.medibuntu.org lucid/non-free Packages
99% [Waiting for headers]                                                      

```
with cursor blinking after last line.
Then eventually:```
Err http://download.virtualbox.org lucid Release.gpg                           
  Connection failed
Err http://download.virtualbox.org/virtualbox/debian/ lucid/contrib Translation-en_GB
  Connection failed
Ign http://download.virtualbox.org lucid Release           
Ign http://download.virtualbox.org lucid/contrib Packages  
Ign http://download.virtualbox.org lucid/contrib Packages  
Err http://download.virtualbox.org lucid/contrib Packages  
  Connection failed
Fetched 2,641B in 4min 4s (11B/s)
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release.gpg  Connection failed

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/lucid/contrib/i18n/Translation-en_GB.bz2  Connection failed

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/lucid/contrib/binary-i386/Packages.gz  Connection failed

E: Some index files failed to download, they have been ignored, or old ones used instead.
mike@mike-i3-laptop:~$ 

```

EDIT
Thanks for replies both. Off to bed now. Will view tomorrow.

---

### Post by CharlesA on 2011-04-25
Try it again tomorrow, it seems like it can't connect to the download server for some reason.

---

