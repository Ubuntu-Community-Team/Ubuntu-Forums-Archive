---
title: "problems with update manager"
date: 2010-04-08
forum: System76 Support
---

### Post by porlaizquierda on 2010-04-08
i use 9.10 on a starling netbook and since yesterday i keep getting an exclamation mark next to the battery icon saying my repositories are outdated. then when i open update manager it checks repositores and i get this message:

Could not download all repository indexes:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and then it the windows it says:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

i know it has something to do with software sources but i don't know which ones i should add or delete. can someone help me?

---

### Post by thomasaaron on 2010-04-08
Establish a wired Internet connection, and then open a terminal and run...

sudo apt-get update

Did you get the same message?

---

### Post by porlaizquierda on 2010-04-08
i get all of this:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                                                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) karmic Release.gpg                                                                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) karmic/main Translation-en_US                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US                                                
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                                       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                                  
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                                                                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                                                                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) karmic Release                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                                                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US                                                
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                                                                     
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                                                                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                                                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) karmic/main Packages                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                                                            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Sources                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages                                                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) karmic/main Packages                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources                                                          
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [83.3kB]                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources                                                        
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) karmic/main Packages                                                                    
  404  Not Found
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]                                                  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [25.4kB]                                                      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]                                                  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [41.8kB]                                                
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [8,486B]                                                 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B]                                              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]                                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                                                                     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_US                                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                         
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Translation-en_US
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                        
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                                                                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                                                                   
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Packages                                                                   
Hit [http://planet76.com](http://planet76.com) ./ Release.gpg                                                                                      
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                                                                                
Hit [http://planet76.com](http://planet76.com) ./ Release                                                                                          
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Fetched 206kB in 11s (18.7kB/s)                                                                                             
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by porlaizquierda on 2010-04-08
the exclamation mark popped up again and this time it brought me to synaptic package manager but i get the message:

An error occured
The following details are  provided:

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_main_binary-i386_Packages)

---

### Post by thomasaaron on 2010-04-09
All in all, that looks pretty good. But you probably need to do a little tweaking in your software sources.

Go to System > Administration > Software Sources and click the "Other Software" tab.

1. Delete the repository that pertains to Wine.
2. You'll have two entries for "http://security.ubuntu.com  karmic-security/main." They'll either be under the "Ubuntu Software" tab or the "Other Software" tab. Delete one of them.
3. Delete this one... 
[http://ppa.launchpad.net](http://ppa.launchpad.net)  karmic Release
...and this one...
[http://ppa.launchpad.net](http://ppa.launchpad.net)  jaunty Release

Then close software sources and run...

sudo apt-get update

---

### Post by porlaizquierda on 2010-04-09
i deleted the wine software sources, but i could find the launchpad repositories that you told me to delete. now i'm getting this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21

i also  could not add the repository you suggested.

---

### Post by thomasaaron on 2010-04-12
Please post the output of...

```
cat /etc/apt/sources.list
```

---

