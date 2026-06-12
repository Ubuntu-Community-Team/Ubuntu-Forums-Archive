---
title: "Reinstall Wine and Unmet Dependencies"
date: 2010-02-17
forum: Wine
---

### Post by amaz1ng on 2010-02-17
So, in getting back to Ubuntu 9.10 after a several-month long break, I decided to get back into the swing of things and try out Battlezone II, as a member of the community just posted his how-to get it working.

Then, This happened

```

**bill@AWESOMELAPPY:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa **
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
** bill@AWESOMELAPPY:~$ sudo apt-get update **
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/main Translation-en_US                         
Get:2 http://dl.google.com stable Release [2,540B]                             
Get:3 http://dl.google.com stable/main Packages [868B]                         
Get:4 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://archive.canonical.com karmic Release                                
Get:5 http://ppa.launchpad.net karmic Release [66.0kB]                         
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://packages.medibuntu.org karmic Release                          
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://archive.canonical.com karmic/partner Sources                        
Hit http://packages.medibuntu.org hardy Release                                
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                 
Hit http://security.ubuntu.com karmic-security/restricted Sources           
Hit http://security.ubuntu.com karmic-security/universe Packages            
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://us.archive.ubuntu.com karmic/universe Sources                    
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                 
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                  
Hit http://us.archive.ubuntu.com karmic-updates/main Packages               
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages         
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                
Hit http://packages.medibuntu.org karmic/free Packages                      
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Get:6 http://ppa.launchpad.net karmic/main Packages [2,296B]         
Hit http://packages.medibuntu.org hardy/free Packages                      
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 72.2kB in 0s (106kB/s)
Reading package lists... Done
** bill@AWESOMELAPPY:~$ sudo apt-get install wine **
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[b]The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
[/b]

```

Any suggestions?

---

### Post by dino99 on 2010-02-17
seems that yours repo or cache are not clean.
so, sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove

then, check your sources.lst to be sure that there is only karmic repos.

sudo apt-get update && sudo apt-get upgrade

in synaptic, desinstall (completly) all wine packages.
in your home dir, search the hidden file .wine and delete it.

in synaptic, you should have 1.1.38 release of wine (latest from wine-ppa), install wine1.2 again.

i'm using it without problem.

---

### Post by webmadman on 2010-02-23
Just had the same issue- found the "wine" dummy package gives broken dependencies, but wine1.2 works, as in:

sudo apt-get install wine1.2

Rather than just wine.

Hope that helps- I was installing Myst Online and ran into the same issue, came across this thread in looking for help, when using the above worked, I figured I would let you know :-)

---

