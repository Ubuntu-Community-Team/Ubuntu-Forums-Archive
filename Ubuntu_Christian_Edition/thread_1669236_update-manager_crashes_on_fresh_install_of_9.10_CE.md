---
title: "update-manager crashes on fresh install of 9.10 CE 6"
date: 2011-01-17
forum: Ubuntu Christian Edition
---

### Post by AlexNagy on 2011-01-17
I tried to file a bug report (but apparently that was in vain), so here it is:

1) Ubuntu 9.10 Karmic Koala (ChristianUbuntu)
2) janagyjr@NewJerusalem:~$ apt-cache policy update-manager
E: Problem parsing dependency Depends
E: Error occurred while processing libedataserverui1.2-8 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
3) The update manager to launch so that I might get the most up-to-date software available.
4) The following error message was displayed:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include
the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing
libedataserverui1.2-8 (NewVersion1), E:Problem with MergeList
/var/lib/apt/lists/us.archive.ubuntu
.com_ubuntu_dists_karmic_main_binary-i386_Packages, E:The package lists
or status file could not be parsed or opened.'

This is the third install of CE6 I've done and the first where I have this issue.

Also, if you guys are going to extend the ISO past the size of a CD, you might as well make it worth chucking on a DVD. I have nearly 4GB of wasted space on my install disc ):

---

### Post by AlexNagy on 2011-01-17
I tried changing the permissions on the files in question to no effect. I'm going to try and change the ownership, though it shouldn't matter, right?

---

### Post by david_kt on 2011-01-17
> **AlexNagy said:**
> I tried to file a bug report (but apparently that was in vain), so here it is:

1) Ubuntu 9.10 Karmic Koala (ChristianUbuntu)
2) janagyjr@NewJerusalem:~$ apt-cache policy update-manager
E: Problem parsing dependency Depends
E: Error occurred while processing libedataserverui1.2-8 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages


Could you try:

```
sudo apt-get update && sudo apt-get upgrade
```

Enter password when requested.

DK

---

### Post by AlexNagy on 2011-01-17
That gets me this:
```
janagyjr@NewJerusalem:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for janagyjr: 
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://ubuntuce.com karmic_i386/ Release.gpg                               
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://ubuntuce.com karmic_i386/ Translation-en_US                         
Ign http://ubuntuce.com karmic_i386/ Release                                   
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://ubuntuce.com karmic_i386/ Packages                                  
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US       
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://archive.canonical.com karmic Release                      
Hit http://us.archive.ubuntu.com karmic Release                      
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://archive.canonical.com karmic/partner Packages             
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic/partner Sources              
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://ppa.launchpad.net karmic/main Sources
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libedataserverui1.2-8 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
janagyjr@NewJerusalem:~$ 
```

---

### Post by david_kt on 2011-01-17
> **AlexNagy said:**
> 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libedataserverui1.2-8 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
janagyjr@NewJerusalem:~$

Try below:

```
sudo mv var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages.old && sudo apt-get update && sudo apt-get upgrade
```

DK

---

### Post by AlexNagy on 2011-01-17
I feel like a linux n00b all over again, except this isn't RH6.2

That seems to have done it. Thanks for being patient. I've done several installs of U9.10 CE6 and this is the first time I've run into issues like this.

---

### Post by david_kt on 2011-01-17
> **AlexNagy said:**
> I feel like a linux n00b all over again, except this isn't RH6.2

That seems to have done it. Thanks for being patient. I've done several installs of U9.10 CE6 and this is the first time I've run into issues like this.

If the problem already solved, follow up with below to clean up:

```
sudo rm var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages.old
```

DK

---

### Post by AlexNagy on 2011-01-18
One other thing, I upgraded to 4.10 (it's month year, right?) and lost my CE customizations, can I follow the directions on the website for the CE5 to CE6 upgrade to get those back? I really like the custom splash and all. (:

The command failed, seems the file isn't there? No biggie. It's not a big file so I'm not too concerned about having it laying around, for now.

---

### Post by david_kt on 2011-01-18
> **AlexNagy said:**
> One other thing, I upgraded to 4.10 (it's month year, right?) and lost my CE customizations, can I follow the directions on the website for the CE5 to CE6 upgrade to get those back? I really like the custom splash and all. (:

The command failed, seems the file isn't there? No biggie. It's not a big file so I'm not too concerned about having it laying around, for now.

It would be different splash actually.
The command fail because there is a mistake, I missed the / in front when copying it:

```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages.old
```

DK

---

### Post by AlexNagy on 2011-01-18
Oh I realized that and corrected it, the command failed because it said file not found (and I already copy pasted the original command, changing what was needed to rm the file).

---

