---
title: "[SOLVED] Ardour3"
date: 2013-05-25
forum: Ubuntu Studio
---

### Post by eamner on 2013-05-25
Hello

First of all I have to say that I'm not an expert on dealing with compiling source code, managing packages, etc. 
I've been struggling for some time trying to install ardour3. First I tried downloading the source and compiling but it was a mess.
Then I found out about the KXStudio repositories, which actually helped a lot in installing other things I needed.
However, when I try to install Ardour3 (using aptitude or any other package manager) I get:
```
eric@Eric-PC:~/Downloads$ sudo aptitude install ardour3
The following NEW packages will be installed:
  ardour3{b} 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.3 MB of archives. After unpacking 51.2 MB will be used.
The following packages have unmet dependencies:
 ardour3 : Depends: python-twisted but it is not installable.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     ardour3 [Not Installed]                            


```

```
eric@Eric-PC:~/Downloads$ sudo aptitude install python-twisted
No candidate version found for python-twisted
No candidate version found for python-twisted
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

And if I use apt-get:
```
eric@Eric-PC:~/Downloads$ sudo apt-get install python-twisted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-twisted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-twisted-core python-twisted-web

E: Package 'python-twisted' has no installation candidate

```

I even downloaded a .deb, but this is all I got:
```
eric@Eric-PC:~/Downloads$ sudo dpkg -i python-twisted_11.1.0-1ubuntu2_all.deb 
Selecting previously unselected package python-twisted.
(Reading database ... 433267 files and directories currently installed.)
Unpacking python-twisted (from python-twisted_11.1.0-1ubuntu2_all.deb) ...
dpkg: dependency problems prevent configuration of python-twisted:
 python-twisted depends on python-twisted-conch (>= 1:11.0); however:
  Package python-twisted-conch is not installed.
 python-twisted depends on python-twisted-mail (>= 11.0); however:
  Package python-twisted-mail is not installed.
 python-twisted depends on python-twisted-lore (>= 11.0); however:
  Package python-twisted-lore is not installed.
 python-twisted depends on python-twisted-news (>= 11.0); however:
  Package python-twisted-news is not installed.
 python-twisted depends on python-twisted-runner (>= 11.0); however:
  Package python-twisted-runner is not installed.
 python-twisted depends on python-twisted-words (>= 11.0); however:
  Package python-twisted-words is not installed.
dpkg: error processing python-twisted (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Errors were encountered while processing:
 python-twisted

```

As I said, I'm no expert..
Please somebody help me. I don't mind the method, I just would like to use Ardour3.

I have Kubuntu 12.04, M-audio 1010lt. I have installed python 2.7.3.
Thanks in advance.

---

### Post by ohnonot on 2013-05-25
```
However the following packages replace it:
  python-twisted-core python-twisted-web
```this would be my next step - to try to install those two packages.

---

### Post by eamner on 2013-05-25
> **ohnonot said:**
> this would be my next step - to try to install those two packages.

Thanks, but they are already installed. It just keeps saying that it needs "python-twisted".

---

### Post by ibjsb4 on 2013-05-25
Python-twisted is in the repositories.

[http://packages.ubuntu.com/precise/python-twisted](http://packages.ubuntu.com/precise/python-twisted)

Has KXStudio repositories replaced your standard ubuntu repositories?  Lets have a look.

```
cat /etc/apt/sources.list
```

---

### Post by eamner on 2013-05-25
> **ibjsb4 said:**
> Python-twisted is in the repositories.

[http://packages.ubuntu.com/precise/python-twisted](http://packages.ubuntu.com/precise/python-twisted)

Has KXStudio repositories replaced your standard ubuntu repositories?  Lets have a look.

```
cat /etc/apt/sources.list
```

Here it is:

```
eric@Eric-PC:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ve.archive.ubuntu.com/ubuntu/ precise restricted
deb-src http://ve.archive.ubuntu.com/ubuntu/ precise restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates restricted
deb-src http://ve.archive.ubuntu.com/ubuntu/ precise-updates restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ve.archive.ubuntu.com/ubuntu/ precise universe
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ve.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ve.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ve.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner

deb http://security.ubuntu.com/ubuntu precise-security restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://extras.ubuntu.com/ubuntu precise main #Third party developers repository

# Eternity Screensaver

deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
deb http://archive.getdeb.net/ubuntu precise-getdeb games
deb-src http://archive.getdeb.net/ubuntu precise-getdeb games
```

---

### Post by ibjsb4 on 2013-05-26
Your Venezuela sources list seem to be incomplete.  I do not see these in your list.

## Ubuntu Main Repos
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

## Ubuntu Update Repos
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

I think they need to be added, but first would you run an update and let me know if you get errors.

```
sudo apt-get update
```

---

### Post by eamner on 2013-05-26
> **ibjsb4 said:**
> 
I think they need to be added, but first would you run an update and let me know if you get errors.

```
sudo apt-get update
```

Ok I got some errors, but they're related to the getdeb repositories, which I can get rid of, as I used them just to install a couple games some time ago:

```
eric@Eric-PC:~$ sudo apt-get update
[sudo] password for eric: 
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release.gpg                                                       
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]                             
Hit http://dl.google.com stable Release                                                           
Hit http://ppa.launchpad.net precise Release.gpg                                                  
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                                        
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]                               
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                                         
Hit http://dl.google.com stable Release                                                           
Hit http://archive.canonical.com precise Release.gpg                                              
Hit http://archive.canonical.com precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release                                                      
Hit http://dl.google.com stable/main i386 Packages                                                
Ign http://dl.google.com stable/main TranslationIndex                                             
Hit http://extras.ubuntu.com precise Release                                                      
Hit http://archive.canonical.com precise Release                                                  
Hit http://dl.google.com stable/main i386 Packages                                                
Ign http://dl.google.com stable/main TranslationIndex                                             
Get:5 http://ppa.launchpad.net precise Release [11.9 kB]                                          
Hit http://extras.ubuntu.com precise/main i386 Packages                                           
Get:6 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                    
Hit http://ve.archive.ubuntu.com precise Release.gpg                                              
Get:7 http://ve.archive.ubuntu.com precise-updates Release.gpg [198 B]                            
Hit http://archive.canonical.com precise Release                                                  
Ign http://extras.ubuntu.com precise/main TranslationIndex                                        
Get:8 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]                    
Get:9 http://security.ubuntu.com precise-security/universe Sources [24.3 kB]                      
Get:10 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]             
Hit http://ve.archive.ubuntu.com precise Release                                                  
Hit http://archive.canonical.com precise/partner i386 Packages                                    
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Get:11 http://security.ubuntu.com precise-security/universe i386 Packages [75.5 kB]               
Hit http://ppa.launchpad.net precise/main Sources                                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Get:12 http://ve.archive.ubuntu.com precise-updates Release [49.6 kB]                             
Hit http://archive.canonical.com precise/partner Sources                                          
Hit http://archive.canonical.com precise/partner i386 Packages                                    
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Get:13 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,375 B]             
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                       
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                       
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                         
Get:14 http://ppa.launchpad.net precise/main Sources [51.3 kB]                                    
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                         
Hit http://security.ubuntu.com precise-security/restricted Translation-en                         
Hit http://archive.getdeb.net precise-getdeb Release.gpg                                          
Hit http://security.ubuntu.com precise-security/universe Translation-en                           
Get:15 http://ppa.launchpad.net precise/main i386 Packages [90.1 kB]                              
Hit http://ve.archive.ubuntu.com precise/restricted Sources                                       
Hit http://ve.archive.ubuntu.com precise/multiverse Sources                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Hit http://ve.archive.ubuntu.com precise/universe Sources                                         
Ign http://dl.google.com stable/main Translation-en_US                                            
Hit http://ve.archive.ubuntu.com precise/restricted i386 Packages                                 
Ign http://dl.google.com stable/main Translation-en                                               
Ign http://dl.google.com stable/main Translation-en_US                                            
Ign http://dl.google.com stable/main Translation-en                                               
Hit http://ve.archive.ubuntu.com precise/universe i386 Packages                                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                                       
Hit http://ve.archive.ubuntu.com precise/multiverse i386 Packages                                 
Ign http://extras.ubuntu.com precise/main Translation-en                                          
Hit http://ve.archive.ubuntu.com precise/multiverse TranslationIndex                              
Ign http://archive.canonical.com precise/partner Translation-en_US                                
Hit http://ve.archive.ubuntu.com precise/restricted TranslationIndex                              
Ign http://archive.canonical.com precise/partner Translation-en                                   
Hit http://ve.archive.ubuntu.com precise/universe TranslationIndex                                
Ign http://archive.canonical.com precise/partner Translation-en_US                                
Ign http://archive.canonical.com precise/partner Translation-en                                   
Get:16 http://ve.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]                  
Get:17 http://ve.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]                  
Get:18 http://ve.archive.ubuntu.com precise-updates/universe Sources [88.4 kB]                    
Ign http://ppa.launchpad.net precise/main Translation-en_US                                       
Ign http://ppa.launchpad.net precise/main Translation-en                                          
Ign http://ppa.launchpad.net precise/main Translation-en_US                                       
Ign http://ppa.launchpad.net precise/main Translation-en                                          
Get:19 http://ve.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]            
Get:20 http://ve.archive.ubuntu.com precise-updates/universe i386 Packages [205 kB]               
Get:21 http://ve.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]            
Hit http://ve.archive.ubuntu.com precise-updates/multiverse TranslationIndex                      
Hit http://ve.archive.ubuntu.com precise-updates/restricted TranslationIndex                      
Hit http://ve.archive.ubuntu.com precise-updates/universe TranslationIndex                        
Hit http://ve.archive.ubuntu.com precise/multiverse Translation-en                                
Hit http://ve.archive.ubuntu.com precise/restricted Translation-en                                
Hit http://ve.archive.ubuntu.com precise/universe Translation-en                                  
Hit http://ve.archive.ubuntu.com precise-updates/multiverse Translation-en                        
Hit http://ve.archive.ubuntu.com precise-updates/restricted Translation-en                        
Hit http://ve.archive.ubuntu.com precise-updates/universe Translation-en                          
Ign http://archive.getdeb.net precise-getdeb Release                                              
Ign http://archive.getdeb.net precise-getdeb/games Sources/DiffIndex
Ign http://archive.getdeb.net precise-getdeb/games i386 Packages/DiffIndex
Ign http://archive.getdeb.net precise-getdeb/games TranslationIndex
Err http://archive.getdeb.net precise-getdeb/games Sources
  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]
Err http://archive.getdeb.net precise-getdeb/games i386 Packages
  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]
Err http://archive.getdeb.net precise-getdeb/games Translation-en_US
  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]
Err http://archive.getdeb.net precise-getdeb/games Translation-en
  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]
Fetched 693 kB in 1min 7s (10.2 kB/s)
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/source/Sources  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en_US  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http: [IP: 141.101.117.236 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

And here's a screen of my software sources, according to Muon Software center:
[IMG]http://img.photobucket.com/albums/v624/eamner/sources_zps3d4dd7fd.jpeg[/IMG]

---

### Post by ibjsb4 on 2013-05-26
Uncheck "getdeb" from your software sources and run another update, that should clear up all the errors.  Then try installing python-twisted again.  If still not installing, go ahead and add the three above links to your software "sources.list".  But first lets make a copy for backup.  In terminal:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Then to edit your sources list:

```
kdesudo kate /etc/apt/sources.list
```

And add this to the list:

> ## Ubuntu Main Repos
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

## Ubuntu Update Repos
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

Then again update and try to install python-twisted.

---

### Post by eamner on 2013-05-26
> **ibjsb4 said:**
> 
Then again update and try to install python-twisted.

Ok no errors this time:
```
eric@Eric-PC:~$ sudo apt-get update
[sudo] password for eric: 
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release.gpg                                                       
Hit http://security.ubuntu.com precise-security Release.gpg                                       
Hit http://ppa.launchpad.net precise Release.gpg                                                  
Hit http://ppa.launchpad.net precise Release.gpg                                                  
Hit http://extras.ubuntu.com precise Release.gpg                                                  
Hit http://archive.canonical.com precise Release.gpg                                              
Hit http://archive.canonical.com precise Release.gpg                                              
Hit http://dl.google.com stable Release                                                           
Hit http://security.ubuntu.com precise-security Release                                           
Hit http://ve.archive.ubuntu.com precise Release.gpg                                              
Hit http://ve.archive.ubuntu.com precise-updates Release.gpg                                      
Hit http://ppa.launchpad.net precise Release                                                      
Hit http://dl.google.com stable Release                                                           
Hit http://extras.ubuntu.com precise Release                                                      
Hit http://archive.canonical.com precise Release                                                  
Hit http://security.ubuntu.com precise-security/restricted Sources                                
Hit http://dl.google.com stable/main i386 Packages                                                
Ign http://dl.google.com stable/main TranslationIndex                                             
Hit http://ve.archive.ubuntu.com precise Release                                                  
Hit http://ppa.launchpad.net precise Release                                                      
Hit http://extras.ubuntu.com precise/main i386 Packages                                           
Hit http://archive.canonical.com precise Release                                                  
Hit http://security.ubuntu.com precise-security/multiverse Sources                                
Hit http://security.ubuntu.com precise-security/universe Sources                                  
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                          
Hit http://security.ubuntu.com precise-security/universe i386 Packages                            
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                       
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                       
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                         
Hit http://dl.google.com stable/main i386 Packages                                                
Ign http://dl.google.com stable/main TranslationIndex                                             
Hit http://ve.archive.ubuntu.com precise-updates Release                                          
Hit http://ppa.launchpad.net precise/main Sources                                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                                        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                         
Hit http://archive.canonical.com precise/partner i386 Packages                                    
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Hit http://ve.archive.ubuntu.com precise/restricted Sources                                       
Hit http://ve.archive.ubuntu.com precise/multiverse Sources                                       
Hit http://ve.archive.ubuntu.com precise/universe Sources                                         
Hit http://ve.archive.ubuntu.com precise/restricted i386 Packages                                 
Hit http://ve.archive.ubuntu.com precise/universe i386 Packages                                   
Hit http://ve.archive.ubuntu.com precise/multiverse i386 Packages                                 
Hit http://ve.archive.ubuntu.com precise/multiverse TranslationIndex                              
Hit http://ve.archive.ubuntu.com precise/restricted TranslationIndex                              
Hit http://ve.archive.ubuntu.com precise/universe TranslationIndex                                
Hit http://security.ubuntu.com precise-security/restricted Translation-en                         
Hit http://ppa.launchpad.net precise/main Sources                                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Hit http://archive.canonical.com precise/partner Sources                                          
Hit http://archive.canonical.com precise/partner i386 Packages                                    
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Hit http://security.ubuntu.com precise-security/universe Translation-en                           
Hit http://ve.archive.ubuntu.com precise-updates/restricted Sources                               
Hit http://ve.archive.ubuntu.com precise-updates/multiverse Sources                               
Hit http://ve.archive.ubuntu.com precise-updates/universe Sources                                 
Hit http://ve.archive.ubuntu.com precise-updates/restricted i386 Packages                         
Hit http://ve.archive.ubuntu.com precise-updates/universe i386 Packages                           
Hit http://ve.archive.ubuntu.com precise-updates/multiverse i386 Packages                         
Hit http://ve.archive.ubuntu.com precise-updates/multiverse TranslationIndex                      
Hit http://ve.archive.ubuntu.com precise-updates/restricted TranslationIndex                      
Hit http://ve.archive.ubuntu.com precise-updates/universe TranslationIndex                        
Hit http://ve.archive.ubuntu.com precise/multiverse Translation-en                                
Hit http://ve.archive.ubuntu.com precise/restricted Translation-en                                
Hit http://ve.archive.ubuntu.com precise/universe Translation-en                                  
Hit http://ve.archive.ubuntu.com precise-updates/multiverse Translation-en                        
Hit http://ve.archive.ubuntu.com precise-updates/restricted Translation-en                        
Hit http://ve.archive.ubuntu.com precise-updates/universe Translation-en                          
Ign http://dl.google.com stable/main Translation-en_US                                            
Ign http://dl.google.com stable/main Translation-en                                        
Ign http://extras.ubuntu.com precise/main Translation-en_US                                
Ign http://dl.google.com stable/main Translation-en_US                                     
Ign http://dl.google.com stable/main Translation-en                                        
Ign http://extras.ubuntu.com precise/main Translation-en                                   
Ign http://ppa.launchpad.net precise/main Translation-en_US          
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en
Reading package lists... Done
```

Then when installing python-twisted, strangely it wanted to remove python-twisted... probably it was (wrongfully) installed in one of my previous attempts with the .deb:

```
eric@Eric-PC:~$ sudo aptitude install python-twisted
The following partially installed packages will be configured:
  python-twisted{b} 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
 python-twisted : Depends: python-twisted-conch (>= 1:11.0) but it is not installable.
                  Depends: python-twisted-mail (>= 11.0) which is a virtual package.
                  Depends: python-twisted-lore (>= 11.0) which is a virtual package.
                  Depends: python-twisted-news (>= 11.0) which is a virtual package.
                  Depends: python-twisted-runner (>= 11.0) which is a virtual package.
                  Depends: python-twisted-words (>= 11.0) which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     python-twisted              

Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  python-twisted{a} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 57.3 kB will be freed.
Do you want to continue? [Y/n/?] Y
(Reading database ... 433272 files and directories currently installed.)
Removing python-twisted ...
Processing triggers for menu ...
                                         
Current status: 0 broken [-1].

```

Then I tried again, and I got the same old message:
```
eric@Eric-PC:~$ sudo aptitude install python-twisted
No candidate version found for python-twisted
No candidate version found for python-twisted
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

So I added the sources you mentioned to the sources file, and when updating, it said I had some 'duplicate' sources:

```
eric@Eric-PC:~$ sudo apt-get update 
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release.gpg                                                       
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]                             
Hit http://dl.google.com stable Release                                                           
Hit http://ppa.launchpad.net precise Release.gpg                                                  
Hit http://ppa.launchpad.net precise Release.gpg                                                  
Hit http://extras.ubuntu.com precise Release.gpg                                                  
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]                               
Hit http://ve.archive.ubuntu.com precise Release.gpg                                              
Hit http://ve.archive.ubuntu.com precise-updates Release.gpg                                      
Get:3 http://ve.archive.ubuntu.com precise-security Release.gpg [198 B]                           
Hit http://dl.google.com stable Release                                                           
Hit http://archive.canonical.com precise Release.gpg                                              
Hit http://archive.canonical.com precise Release.gpg                                              
Hit http://ppa.launchpad.net precise Release                                                      
Hit http://dl.google.com stable/main i386 Packages                                                
Hit http://extras.ubuntu.com precise Release                                                      
Ign http://dl.google.com stable/main TranslationIndex                                             
Hit http://ve.archive.ubuntu.com precise Release                                                  
Hit http://archive.canonical.com precise Release                                                  
Hit http://dl.google.com stable/main i386 Packages                                                
Ign http://dl.google.com stable/main TranslationIndex                                             
Hit http://ppa.launchpad.net precise Release                                                      
Hit http://extras.ubuntu.com precise/main i386 Packages                                           
Hit http://ve.archive.ubuntu.com precise-updates Release                                          
Get:4 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                    
Hit http://archive.canonical.com precise Release                                                  
Hit http://ppa.launchpad.net precise/main Sources                                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                                        
Get:5 http://ve.archive.ubuntu.com precise-security Release [49.6 kB]                             
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]                    
Get:7 http://security.ubuntu.com precise-security/universe Sources [24.3 kB]                      
Get:8 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]              
Hit http://archive.canonical.com precise/partner i386 Packages                                    
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Hit http://ppa.launchpad.net precise/main Sources                                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Get:9 http://security.ubuntu.com precise-security/universe i386 Packages [75.5 kB]                
Hit http://archive.canonical.com precise/partner Sources                                          
Hit http://archive.canonical.com precise/partner i386 Packages                                    
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Hit http://ve.archive.ubuntu.com precise/restricted Sources                                       
Hit http://ve.archive.ubuntu.com precise/multiverse Sources                                       
Hit http://ve.archive.ubuntu.com precise/universe Sources                                         
Hit http://ve.archive.ubuntu.com precise/restricted i386 Packages                                 
Hit http://ve.archive.ubuntu.com precise/universe i386 Packages                                   
Hit http://ve.archive.ubuntu.com precise/multiverse i386 Packages                                 
Get:10 http://ve.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                         
Get:11 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,375 B]             
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                       
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                       
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                         
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                         
Hit http://security.ubuntu.com precise-security/restricted Translation-en                         
Hit http://security.ubuntu.com precise-security/universe Translation-en                           
Ign http://extras.ubuntu.com precise/main Translation-en_US                                       
Ign http://dl.google.com stable/main Translation-en_US                                            
Ign http://extras.ubuntu.com precise/main Translation-en                                          
Ign http://dl.google.com stable/main Translation-en                                               
Ign http://dl.google.com stable/main Translation-en_US                                            
Ign http://dl.google.com stable/main Translation-en                                               
Ign http://ppa.launchpad.net precise/main Translation-en_US                                       
Ign http://archive.canonical.com precise/partner Translation-en_US                                
Ign http://ppa.launchpad.net precise/main Translation-en                                          
Ign http://ppa.launchpad.net precise/main Translation-en_US                                       
Ign http://archive.canonical.com precise/partner Translation-en                                   
Ign http://archive.canonical.com precise/partner Translation-en_US                                
Ign http://ppa.launchpad.net precise/main Translation-en                                          
Ign http://archive.canonical.com precise/partner Translation-en                                   
Get:12 http://ve.archive.ubuntu.com precise/main TranslationIndex [3,706 B]                       
Hit http://ve.archive.ubuntu.com precise/multiverse TranslationIndex                              
Hit http://ve.archive.ubuntu.com precise/restricted TranslationIndex                              
Hit http://ve.archive.ubuntu.com precise/universe TranslationIndex                                
Hit http://ve.archive.ubuntu.com precise-updates/restricted Sources                               
Hit http://ve.archive.ubuntu.com precise-updates/multiverse Sources                               
Hit http://ve.archive.ubuntu.com precise-updates/universe Sources                                 
Hit http://ve.archive.ubuntu.com precise-updates/restricted i386 Packages                         
Hit http://ve.archive.ubuntu.com precise-updates/universe i386 Packages                           
Hit http://ve.archive.ubuntu.com precise-updates/multiverse i386 Packages                         
Get:13 http://ve.archive.ubuntu.com precise-updates/main i386 Packages [631 kB]                   
Get:14 http://ve.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]               
Hit http://ve.archive.ubuntu.com precise-updates/multiverse TranslationIndex                      
Hit http://ve.archive.ubuntu.com precise-updates/restricted TranslationIndex                      
Hit http://ve.archive.ubuntu.com precise-updates/universe TranslationIndex                        
Get:15 http://ve.archive.ubuntu.com precise-security/main i386 Packages [280 kB]                  
Get:16 http://ve.archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]           
Get:17 http://ve.archive.ubuntu.com precise-security/universe i386 Packages [75.5 kB]             
Get:18 http://ve.archive.ubuntu.com precise-security/multiverse i386 Packages [2,375 B]           
Get:19 http://ve.archive.ubuntu.com precise-security/main TranslationIndex [74 B]                 
Get:20 http://ve.archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]           
Get:21 http://ve.archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]           
Get:22 http://ve.archive.ubuntu.com precise-security/universe TranslationIndex [73 B]             
Get:23 http://ve.archive.ubuntu.com precise/main Translation-en [726 kB]                          
Hit http://ve.archive.ubuntu.com precise/multiverse Translation-en                                
Hit http://ve.archive.ubuntu.com precise/restricted Translation-en                                
Hit http://ve.archive.ubuntu.com precise/universe Translation-en                                  
Get:24 http://ve.archive.ubuntu.com precise-updates/main Translation-en [277 kB]                  
Hit http://ve.archive.ubuntu.com precise-updates/multiverse Translation-en                        
Hit http://ve.archive.ubuntu.com precise-updates/restricted Translation-en                        
Hit http://ve.archive.ubuntu.com precise-updates/universe Translation-en                          
Get:25 http://ve.archive.ubuntu.com precise-security/main Translation-en [125 kB]                 
Get:26 http://ve.archive.ubuntu.com precise-security/multiverse Translation-en [995 B]            
Get:27 http://ve.archive.ubuntu.com precise-security/restricted Translation-en [1,253 B]          
Get:28 http://ve.archive.ubuntu.com precise-security/universe Translation-en [45.7 kB]            
Fetched 3,660 kB in 1min 3s (57.9 kB/s)                                                           
Reading package lists... Done
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise-updates/multiverse i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

``` 

But after running again, I still get the "DUPLICATE SOURCES" messages....
Anyway, I tried to install python-twisted, and BINGO:

```
eric@Eric-PC:~$ sudo aptitude install python-twisted
The following NEW packages will be installed:
  python-pyasn1{a} python-twisted python-twisted-conch{a} python-twisted-lore{a} 
  python-twisted-mail{a} python-twisted-news{a} python-twisted-runner{a} 
  python-twisted-words{a} 
0 packages upgraded, 8 newly installed, 0 to remove and 67 not upgraded.
Need to get 839 kB of archives. After unpacking 4,411 kB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-pyasn1 all 0.0.11a-1ubuntu1 [30.4 kB]
Get: 2 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted-lore all 11.1.0-1 [85.3 kB]
Get: 3 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted-mail all 11.1.0-1 [193 kB]
Get: 4 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted-news all 11.1.0-1 [23.7 kB]
Get: 5 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted-runner i386 11.1.0-1 [18.9 kB]
Get: 6 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted-words all 11.1.0-1 [215 kB]
Get: 7 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted-conch all 1:11.1.0-1 [269 kB]
Get: 8 http://ve.archive.ubuntu.com/ubuntu/ precise/main python-twisted all 11.1.0-1ubuntu2 [4,064 B]
Fetched 839 kB in 14s (59.9 kB/s)                                                                  
Selecting previously unselected package python-pyasn1.
(Reading database ... 433267 files and directories currently installed.)
Unpacking python-pyasn1 (from .../python-pyasn1_0.0.11a-1ubuntu1_all.deb) ...
Selecting previously unselected package python-twisted-lore.
Unpacking python-twisted-lore (from .../python-twisted-lore_11.1.0-1_all.deb) ...
Selecting previously unselected package python-twisted-mail.
Unpacking python-twisted-mail (from .../python-twisted-mail_11.1.0-1_all.deb) ...
Selecting previously unselected package python-twisted-news.
Unpacking python-twisted-news (from .../python-twisted-news_11.1.0-1_all.deb) ...
Selecting previously unselected package python-twisted-runner.
Unpacking python-twisted-runner (from .../python-twisted-runner_11.1.0-1_i386.deb) ...
Selecting previously unselected package python-twisted-words.
Unpacking python-twisted-words (from .../python-twisted-words_11.1.0-1_all.deb) ...
Selecting previously unselected package python-twisted-conch.
Unpacking python-twisted-conch (from .../python-twisted-conch_1%3a11.1.0-1_all.deb) ...
Selecting previously unselected package python-twisted.
Unpacking python-twisted (from .../python-twisted_11.1.0-1ubuntu2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for python-twisted-core ...
Processing triggers for menu ...
Setting up python-pyasn1 (0.0.11a-1ubuntu1) ...
Setting up python-twisted-lore (11.1.0-1) ...
Setting up python-twisted-mail (11.1.0-1) ...
Setting up python-twisted-news (11.1.0-1) ...
Setting up python-twisted-runner (11.1.0-1) ...
Setting up python-twisted-words (11.1.0-1) ...
Setting up python-twisted-conch (1:11.1.0-1) ...
Processing triggers for python-twisted-core ...
Setting up python-twisted (11.1.0-1ubuntu2) ...
Processing triggers for menu ...
```

**Python-Twisted is finally installed!**

Next, I tried installing Ardour3 via package manager, and DONE!
Thanks a lot for your help!

But, can you tell me what could possibly be the cause of this? I don't remember removing those sources. Could they have been replaced or removed in other way?

---

### Post by ibjsb4 on 2013-05-26
It looks like /var/lib/apt/lists has duplicate sources.  I suppect that a ppa or two is still messing with you, but lets see if these duplicate sources can just be removed.

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by eamner on 2013-05-26
> **ibjsb4 said:**
> It looks like /var/lib/apt/lists has duplicate sources.  I suppect that a ppa or two is still messing with you, but lets see if these duplicate sources can just be removed.


Still, same error....

```
eric@Eric-PC:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [198 B]
Get:2 http://dl.google.com stable Release.gpg [198 B]                                             
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]                             
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                                         
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]                                        
Get:6 http://ppa.launchpad.net precise Release.gpg [316 B]                                        
Get:7 http://archive.canonical.com precise Release.gpg [198 B]                                    
Get:8 http://archive.canonical.com precise Release.gpg [198 B]                                    
Get:9 http://dl.google.com stable Release [1,351 B]                                               
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]                              
Get:11 http://ve.archive.ubuntu.com precise Release.gpg [198 B]                                   
Get:12 http://ve.archive.ubuntu.com precise-updates Release.gpg [198 B]                           
Get:13 http://ve.archive.ubuntu.com precise-security Release.gpg [198 B]                          
Get:14 http://extras.ubuntu.com precise Release [11.9 kB]                                         
Get:15 http://ppa.launchpad.net precise Release [11.9 kB]                                         
Get:16 http://dl.google.com stable Release [1,338 B]                                              
Get:17 http://archive.canonical.com precise Release [7,078 B]                                     
Get:18 http://ve.archive.ubuntu.com precise Release [49.6 kB]                                     
Get:19 http://dl.google.com stable/main i386 Packages [1,320 B]                                   
Ign http://dl.google.com stable/main TranslationIndex                                             
Get:20 http://dl.google.com stable/main i386 Packages [464 B]                                     
Ign http://dl.google.com stable/main TranslationIndex                                             
Get:21 http://ppa.launchpad.net precise Release [11.9 kB]                                         
Get:22 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                   
Get:23 http://archive.canonical.com precise Release [7,078 B]                                     
Get:24 http://ve.archive.ubuntu.com precise-updates Release [49.6 kB]                             
Get:25 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]                              
Get:26 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]                   
Get:27 http://security.ubuntu.com precise-security/universe Sources [24.3 kB]                     
Get:28 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]             
Get:29 http://ve.archive.ubuntu.com precise-security Release [49.6 kB]                            
Get:30 http://security.ubuntu.com precise-security/universe i386 Packages [75.5 kB]               
Get:31 http://ppa.launchpad.net precise/main Sources [948 B]                                      
Get:32 http://ppa.launchpad.net precise/main i386 Packages [801 B]                                
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Get:33 http://archive.canonical.com precise/partner i386 Packages [8,273 B]                       
Get:34 http://ve.archive.ubuntu.com precise/restricted Sources [5,470 B]                          
Ign http://extras.ubuntu.com precise/main TranslationIndex                                        
Get:35 http://ppa.launchpad.net precise/main Sources [51.8 kB]                                    
Get:36 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,375 B]             
Get:37 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]             
Get:38 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]             
Get:39 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]               
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Get:40 http://archive.canonical.com precise/partner Sources [4,507 B]                             
Get:41 http://archive.canonical.com precise/partner i386 Packages [8,273 B]                       
Get:42 http://ve.archive.ubuntu.com precise/multiverse Sources [155 kB]                           
Get:43 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]              
Get:44 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]            
Ign http://archive.canonical.com precise/partner TranslationIndex                                 
Get:45 http://ppa.launchpad.net precise/main i386 Packages [90.1 kB]                              
Get:46 http://security.ubuntu.com precise-security/universe Translation-en [45.7 kB]              
Get:47 http://ve.archive.ubuntu.com precise/universe Sources [5,019 kB]                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                        
Ign http://dl.google.com stable/main Translation-en_US                                            
Ign http://dl.google.com stable/main Translation-en                                               
Ign http://dl.google.com stable/main Translation-en_US                                            
Ign http://extras.ubuntu.com precise/main Translation-en_US                                       
Ign http://dl.google.com stable/main Translation-en                                               
Ign http://extras.ubuntu.com precise/main Translation-en                                          
Ign http://archive.canonical.com precise/partner Translation-en_US                                
Ign http://archive.canonical.com precise/partner Translation-en                 
Ign http://archive.canonical.com precise/partner Translation-en_US              
Ign http://archive.canonical.com precise/partner Translation-en                 
Ign http://ppa.launchpad.net precise/main Translation-en_US                                       
Ign http://ppa.launchpad.net precise/main Translation-en                                          
Ign http://ppa.launchpad.net precise/main Translation-en_US                                       
Ign http://ppa.launchpad.net precise/main Translation-en                                          
Get:48 http://ve.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                    
Get:49 http://ve.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                     
Get:50 http://ve.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                     
Get:51 http://ve.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                         
Get:52 http://ve.archive.ubuntu.com precise/main TranslationIndex [3,706 B]                       
Get:53 http://ve.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]                 
Get:54 http://ve.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]                 
Get:55 http://ve.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]                   
Get:56 http://ve.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]                  
Get:57 http://ve.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]                  
Get:58 http://ve.archive.ubuntu.com precise-updates/universe Sources [88.4 kB]                    
Get:59 http://ve.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]            
Get:60 http://ve.archive.ubuntu.com precise-updates/universe i386 Packages [205 kB]               
Get:61 http://ve.archive.ubuntu.com precise-updates/universe i386 Packages [205 kB]               
Get:62 http://ve.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]            
Get:63 http://ve.archive.ubuntu.com precise-updates/main i386 Packages [631 kB]                   
Get:64 http://ve.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]               
Get:65 http://ve.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]         
Get:66 http://ve.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]         
Get:67 http://ve.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]           
Get:68 http://ve.archive.ubuntu.com precise-security/main i386 Packages [280 kB]                  
Get:69 http://ve.archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]           
Get:70 http://ve.archive.ubuntu.com precise-security/universe i386 Packages [75.5 kB]             
Get:71 http://ve.archive.ubuntu.com precise-security/multiverse i386 Packages [2,375 B]           
Get:72 http://ve.archive.ubuntu.com precise-security/main TranslationIndex [74 B]                 
Get:73 http://ve.archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]           
Get:74 http://ve.archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]           
Get:75 http://ve.archive.ubuntu.com precise-security/universe TranslationIndex [73 B]             
Get:76 http://ve.archive.ubuntu.com precise/main Translation-en [726 kB]                          
Get:77 http://ve.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                   
Get:78 http://ve.archive.ubuntu.com precise/restricted Translation-en [2,395 B]                   
Get:79 http://ve.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                    
Get:80 http://ve.archive.ubuntu.com precise-updates/main Translation-en [277 kB]                  
Get:81 http://ve.archive.ubuntu.com precise-updates/multiverse Translation-en [7,834 B]           
Get:82 http://ve.archive.ubuntu.com precise-updates/restricted Translation-en [2,432 B]           
Get:83 http://ve.archive.ubuntu.com precise-updates/universe Translation-en [118 kB]              
Get:84 http://ve.archive.ubuntu.com precise-security/main Translation-en [125 kB]                 
Get:85 http://ve.archive.ubuntu.com precise-security/multiverse Translation-en [995 B]            
Get:86 http://ve.archive.ubuntu.com precise-security/restricted Translation-en [1,253 B]          
Get:87 http://ve.archive.ubuntu.com precise-security/universe Translation-en [45.7 kB]            
Fetched 17.9 MB in 5min 0s (59.6 kB/s)                                                            
Reading package lists... Done
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://ve.archive.ubuntu.com/ubuntu/ precise-updates/multiverse i386 Packages (/var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by ibjsb4 on 2013-05-26
[ATTACH=CONFIG]243110[/ATTACH]
Uncheck these in your software sources. Also go to "Kubuntu Software" tab and uncheck the box that says something like "source" or "source code".  Then update.

---

### Post by eamner on 2013-05-27
> **ibjsb4 said:**
> [ATTACH=CONFIG]243110[/ATTACH]
Uncheck these in your software sources. Also go to "Kubuntu Software" tab and uncheck the box that says something like "source" or "source code".  Then update.

Thanks, I'll do it tonight when I get home (I'm at work now ;)) and I'll let you know.

---

### Post by eamner on 2013-05-27
> **ibjsb4 said:**
> 
Uncheck these in your software sources. Also go to "Kubuntu Software" tab and uncheck the box that says something like "source" or "source code".  Then update.

Done. But the duplicates remain.
Isn't there an option for apt-get to automatically eliminate the duplicates?

---

### Post by CraigPid on 2013-05-27
You know if you download from ardour.org you can choose to pay $1 and if you really don't want to pay you can choose to pay 0 and they'll still give it to you.
  Craig

---

### Post by ibjsb4 on 2013-05-28
> **eamner said:**
> Done. But the duplicates remain.
Isn't there an option for apt-get to automatically eliminate the duplicates?

Not an apt-get command, but post #10.  Those commands remove all entries and leaves /var/lib/apt/lists completely empty.  The update command then rebuilds /var/lib/apt/lists.  However when yours gets rebuilt the double entries are re-entered.   This is what makes me think that its a ppa thats doing this.  So I want to give the ppa's one last shot.  You still have two on the list that could cause this and I would like to remove them (temporarily).

Uncheck [http://ppa.launch.net/kxstudio-team](http://ppa.launch.net/kxstudio-team) and /happy.neko

Then in terminal:

```
sudo apt-get clean
sudo apt-get autoremove
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

If this does not resolve the problem, go ahead and recheck them and again update.  This will restore both PPAs.

While your doing that, I will go back over this thread to see if I have missed anything.

---

### Post by eamner on 2013-05-28
> **ibjsb4 said:**
> 
While your doing that, I will go back over this thread to see if I have missed anything.

Thanks, I will try this tonight when I get home.

---

### Post by eamner on 2013-05-29
> **ibjsb4 said:**
> 
If this does not resolve the problem, go ahead and recheck them and again update.  This will restore both PPAs.

While your doing that, I will go back over this thread to see if I have missed anything.

Hello.
Again, the errors remain. I believe it has something to do with the lines we added to the sources file. Even though it solved my python problem, I don't remember seeing those errors before.
Thx.

---

### Post by ibjsb4 on 2013-05-29
!!#^*%!## :(

Too many post.  Please humor me and repost your "sources.list" and "sources.list.d"  I want to verify them one more time.  Also Im heading out the door and hope to get back to you this evening.  Thank you

---

### Post by Cheesemill on 2013-05-29
Can you run the following command, it will give us a nicely formatted list of all of the locations apt is looking at for software sources...

```
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

---

### Post by eamner on 2013-05-29
Thanks to you two. I'll do it tonight when I get home.

---

### Post by eamner on 2013-05-29
> **ibjsb4 said:**
> !!#^*%!## :(

Too many post.  Please humor me and repost your "sources.list" and "sources.list.d"  I want to verify them one more time.  Also Im heading out the door and hope to get back to you this evening.  Thank you

Ok, this is sources.list :

```
eric@Eric-PC:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ve.archive.ubuntu.com/ubuntu/ precise restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ve.archive.ubuntu.com/ubuntu/ precise universe
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ve.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ve.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ve.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner

deb http://security.ubuntu.com/ubuntu precise-security restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://extras.ubuntu.com/ubuntu precise main #Third party developers repository

# Eternity Screensaver

deb http://archive.canonical.com/ precise partner
# deb-src http://archive.canonical.com/ precise partner
# deb http://archive.getdeb.net/ubuntu precise-getdeb games
# deb-src http://archive.getdeb.net/ubuntu precise-getdeb games

## Ubuntu Main Repos
deb http://ve.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse

## Ubuntu Update Repos
deb http://ve.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse


```

With sources.d you mean the content of the directory? 
```
eric@Eric-PC:/etc/apt/sources.list.d$ ls
falk-t-j-festige-precise.list                hugin-hugin-builds-maverick.list
falk-t-j-festige-precise.list.save           hugin-hugin-builds-maverick.list.distUpgrade
gcstar-ppa-maverick.list                     hugin-hugin-builds-maverick.list.save
gcstar-ppa-maverick.list.distUpgrade         hugin-hugin-builds-oneiric.list
gcstar-ppa-maverick.list.save                hugin-hugin-builds-oneiric.list.distUpgrade
gcstar-ppa-natty.list                        hugin-hugin-builds-oneiric.list.save
gcstar-ppa-natty.list.distUpgrade            kubuntu-ppa-ppa-maverick.list
gcstar-ppa-natty.list.save                   kubuntu-ppa-ppa-maverick.list.distUpgrade
getdeb.list                                  kubuntu-ppa-ppa-maverick.list.save
getdeb.list.distUpgrade                      kxstudio-team-kxstudio-precise.list
getdeb.list.save                             kxstudio-team-kxstudio-precise.list.save
google-chrome.list                           kxstudio-team-ppa-precise.list
google-chrome.list.distUpgrade               kxstudio-team-ppa-precise.list.save
google-chrome.list.save                      medibuntu.list
google-earth.list                            medibuntu.list.distUpgrade
google-earth.list.distUpgrade                medibuntu.list.save
google-earth.list.save                       sunab-kdenlive-release-oneiric.list
happy-neko-ps3mediaserver-precise.list       sunab-kdenlive-release-oneiric.list.distUpgrade
happy-neko-ps3mediaserver-precise.list.save  sunab-kdenlive-release-oneiric.list.save
```

There's some rubbish there, from previous installations...

And this is the output for Cheesemill:

```
eric@Eric-PC:~$ find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/medibuntu.list

     1  ## Please report any bug on https://bugs.launchpad.net/medibuntu/

/etc/apt/sources.list.d/kxstudio-team-ppa-precise.list

     1  # deb http://ppa.launchpad.net/kxstudio-team/ppa/ubuntu precise main
     2  # deb-src http://ppa.launchpad.net/kxstudio-team/ppa/ubuntu precise main

/etc/apt/sources.list.d/falk-t-j-festige-precise.list


/etc/apt/sources.list.d/kxstudio-team-kxstudio-precise.list


/etc/apt/sources.list.d/hugin-hugin-builds-maverick.list


/etc/apt/sources.list.d/kubuntu-ppa-ppa-maverick.list


/etc/apt/sources.list.d/gcstar-ppa-natty.list


/etc/apt/sources.list.d/getdeb.list


/etc/apt/sources.list.d/google-chrome.list

     1  ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2  # You may comment out this entry, but any other modifications may be lost.
     3  deb http://dl.google.com/linux/chrome/deb/ stable main

/etc/apt/sources.list.d/happy-neko-ps3mediaserver-precise.list

     1  # deb http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu precise main
     2  # deb-src http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu precise main

/etc/apt/sources.list.d/hugin-hugin-builds-oneiric.list


/etc/apt/sources.list.d/google-earth.list

     1  ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2  # You may comment out this entry, but any other modifications may be lost.
     3  deb http://dl.google.com/linux/earth/deb/ stable main

/etc/apt/sources.list.d/sunab-kdenlive-release-oneiric.list


/etc/apt/sources.list.d/gcstar-ppa-maverick.list


/etc/apt/sources.list

     1  # deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
     2  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3  # newer versions of the distribution.
     4
     5  deb http://ve.archive.ubuntu.com/ubuntu/ precise restricted
     6
     7  ## Major bug fix updates produced after the final release of the
     8  ## distribution.
     9  deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates restricted
    10
    11  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12  ## team. Also, please note that software in universe WILL NOT receive any
    13  ## review or updates from the Ubuntu security team.
    14  deb http://ve.archive.ubuntu.com/ubuntu/ precise universe
    15  deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates universe
    16
    17  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18  ## team, and may not be under a free licence. Please satisfy yourself as to 
    19  ## your rights to use the software. Also, please note that software in 
    20  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21  ## security team.
    22  deb http://ve.archive.ubuntu.com/ubuntu/ precise multiverse
    23  deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    24
    25  ## Uncomment the following two lines to add software from the 'backports'
    26  ## repository.
    27  ## N.B. software from this repository may not have been tested as
    28  ## extensively as that contained in the main release, although it includes
    29  ## newer versions of some applications which may provide useful features.
    30  ## Also, please note that software in backports WILL NOT receive any review
    31  ## or updates from the Ubuntu security team.
    32  # deb http://ve.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    33  # deb-src http://ve.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    34
    35  ## Uncomment the following two lines to add software from Canonical's
    36  ## 'partner' repository.
    37  ## This software is not part of Ubuntu, but is offered by Canonical and the
    38  ## respective vendors as a service to Ubuntu users.
    39  # deb http://archive.canonical.com/ubuntu precise partner
    40
    41  deb http://security.ubuntu.com/ubuntu precise-security restricted
    42  deb http://security.ubuntu.com/ubuntu precise-security universe
    43  deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44  deb http://extras.ubuntu.com/ubuntu precise main #Third party developers repository
    45
    46  # Eternity Screensaver
    47
    48  deb http://archive.canonical.com/ precise partner
    49  # deb-src http://archive.canonical.com/ precise partner
    50  # deb http://archive.getdeb.net/ubuntu precise-getdeb games
    51  # deb-src http://archive.getdeb.net/ubuntu precise-getdeb games
    52
    53  ## Ubuntu Main Repos
    54  deb http://ve.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
    55
    56  ## Ubuntu Update Repos
    57  deb http://ve.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
    58  deb http://ve.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
    59

```

---

### Post by Cheesemill on 2013-05-29
Comment out lines 22 and 23 in /etc/apt/sources.list as you also have those sources defined in lines 57 and 58.

---

### Post by eamner on 2013-05-29
> **Cheesemill said:**
> Comment out lines 22 and 23 in /etc/apt/sources.list as you also have those sources defined in lines 57 and 58.

Still same errors... believe it or not. Should I leave them commented or should I put them back in?

---

### Post by Cheesemill on 2013-05-29
Sorry, they were just the first duplicates I found. You also need to comment out lines 5, 9, 14 and 15 as they are repeated in lines 54, 57 and 58.
In fact it looks as if all of your entries had a duplicate added at the bottom of the file, can you remember why you added those last 7 lines in the first place?

If you are still getting duplicates then it may be quicker just to start you sources.list from scratch, you can generate a new one using this website...
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by eamner on 2013-05-29
> **Cheesemill said:**
> Sorry, they were just the first duplicates I found. You also need to comment out lines 5, 9, 14 and 15 as they are repeated in lines 54, 57 and 58.
In fact it looks as if all of your entries had a duplicate added at the bottom of the file, can you remember why you added those last 7 lines in the first place?

If you are still getting duplicates then it may be quicker just to start you sources.list from scratch, you can generate a new one using this website...
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

**ibjsb4** made me do it!
Just kidding.. look at post #6... but adding those lines actually solved my python-twisted problem.

Anyway, guess what... the errors are gone.
I just hope I'm not missing any important update source after all these edits...

Thank you very much guys, ibjsb4, Cheesemill, for your patience.

---

### Post by ibjsb4 on 2013-05-30
I will add my thanks to that too Cheesemill :)  Im starting to think this may be solved.

---

