---
title: "synaptic package manager problems"
date: 2010-04-18
forum: System76 Support
---

### Post by porlaizquierda on 2010-04-18
when i open syanpticpackage manager i get this:

An error occurred

The following details are provided: 

E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i removed the mozilla lines from my software sources

and still got pretty much the same thing, just slightly different:

E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

what can i do?

---

### Post by riseringseeker on 2010-04-18
Can you post the contents of your sources.list file?

---

### Post by porlaizquierda on 2010-04-19
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
[http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu)
[http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu)
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
[http://planet76.com/repositories/](http://planet76.com/repositories/)
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by porlaizquierda on 2010-04-19
also now because of this i got system manager saying:

Could not initialize the package information:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/mozillateam-firefox-stable-karmic.list, E:The list of sources could not be read.'

---

### Post by thomasaaron on 2010-04-19
Try running these commands one at a time...

sudo mv /etc/apt/sources.list.d/mozillateam-firefox-stable-karmic.list /etc/apt/sources.list.d/mozillateam-firefox-stable-karmic.list.bk

sudo apt-get update

---

### Post by porlaizquierda on 2010-04-19
when i ran the first command it stalled and then i got this:

mv: cannot stat `/etc/apt/sources.list.d/mozillateam-firefox-stable-karmic.list': No such file or directory

when i ran sudo apt-get update i got this:

Hit [http://planet76.com](http://planet76.com) ./ Release.gpg
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                                                                                
Hit [http://planet76.com](http://planet76.com) ./ Release                                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                                                                
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                                                             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                                                                     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_US                                                          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release.gpg                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                           
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                                                                          
Ign [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Translation-en_US                                                          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                                                            
Hit [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                                                                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release                                                                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                                                                   
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Packages                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Reading package lists... Done                            
W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_main_binary-i386_Packages)

---

### Post by porlaizquierda on 2010-04-19
i am able to open synaptic package manager and update manager, but i would still like to get all this stuff cleaned up. what do i need to do?

---

### Post by thomasaaron on 2010-04-19
Go to System > Admin > Software Sources.

Delete the two entries that have "medibuntu" in them.

Then run...

sudo apt-get update

...and post the output.

---

### Post by porlaizquierda on 2010-04-19
seems to have done the trick. here's what i got.

Hit [http://planet76.com](http://planet76.com) ./ Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                                                                 
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                                  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                                                                     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_US                                                          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release.gpg                                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                                                                
Hit [http://planet76.com](http://planet76.com) ./ Release                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US                  
Ign [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Translation-en_US                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US                                              
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                                                                          
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                           
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                                                            
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                                                
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                                                         
Hit [http://planet76.com](http://planet76.com) ./ Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
Reading package lists... Done

---

### Post by riseringseeker on 2010-04-21
> **porlaizquierda said:**
> seems to have done the trick. here's what i got.

You should be able to re-enable the medibuntu repos today or tomorrow by all accounts.  It's been down hard since at least Sunday night.

---

