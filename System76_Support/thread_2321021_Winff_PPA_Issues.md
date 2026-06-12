---
title: "Winff PPA Issues"
date: 2016-04-19
forum: System76 Support
---

### Post by William_Griff_Hage on 2016-04-19
Dear System76,

I have installed a PPA for a video converting software called WindFF. Once updating it told me that it has a 404 error. Here is the code from the terminal.

```
griffprogrammed@griffprogrammed-oryx-pro:~$ sudo add-apt-repository ppa:paul-climbing/ppa[sudo] password for griffprogrammed: 
 This PPA was meant to support WinFF on old versions of Ubuntu. However, as they landed in Debian and Ubuntu proper, I don't see great benefit for now.
Apart from here they are also published at the WinFF.org website. Please file bugs at http://code.google.com/p/winff/issues/list


 More info: https://launchpad.net/~paul-climbing/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpltdftooi/secring.gpg' created
gpg: keyring `/tmp/tmpltdftooi/pubring.gpg' created
gpg: requesting key F96FD737 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpltdftooi/trustdb.gpg: trustdb created
gpg: key F96FD737: public key "Launchpad PPA for Paul Gevers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
griffprogrammed@griffprogrammed-oryx-pro:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com wily InRelease
Hit http://us.archive.ubuntu.com wily-updates InRelease                        
Hit http://us.archive.ubuntu.com wily-backports InRelease                      
Hit http://archive.canonical.com wily InRelease                                
Hit http://security.ubuntu.com wily-security InRelease                         
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://us.archive.ubuntu.com wily/main Sources                             
Hit http://us.archive.ubuntu.com wily/restricted Sources                       
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Hit http://security.ubuntu.com wily-security/main Sources                      
Hit http://us.archive.ubuntu.com wily/universe Sources                         
Ign http://ppa.launchpad.net wily InRelease                                    
Hit http://us.archive.ubuntu.com wily/multiverse Sources                       
Hit http://archive.canonical.com wily/partner i386 Packages                    
Hit http://us.archive.ubuntu.com wily/main amd64 Packages                      
Hit http://security.ubuntu.com wily-security/restricted Sources                
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://us.archive.ubuntu.com wily/restricted amd64 Packages                
Hit http://us.archive.ubuntu.com wily/universe amd64 Packages                  
Hit http://archive.canonical.com wily/partner Translation-en                   
Hit http://security.ubuntu.com wily-security/universe Sources                  
Hit http://us.archive.ubuntu.com wily/multiverse amd64 Packages                
Hit http://ppa.launchpad.net wily InRelease                                    
Ign http://dl.google.com stable InRelease                                      
Hit http://us.archive.ubuntu.com wily/main i386 Packages                       
Hit http://dl.google.com stable Release.gpg                                    
Hit http://security.ubuntu.com wily-security/multiverse Sources                
Hit http://us.archive.ubuntu.com wily/restricted i386 Packages                 
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com wily/universe i386 Packages                   
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com wily/multiverse i386 Packages                 
Hit http://security.ubuntu.com wily-security/main amd64 Packages               
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Hit http://us.archive.ubuntu.com wily/main Translation-en                      
Hit http://us.archive.ubuntu.com wily/multiverse Translation-en                
Hit http://security.ubuntu.com wily-security/restricted amd64 Packages         
Hit http://us.archive.ubuntu.com wily/restricted Translation-en                
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Hit http://security.ubuntu.com wily-security/universe amd64 Packages           
Hit http://us.archive.ubuntu.com wily/universe Translation-en                  
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://us.archive.ubuntu.com wily-updates/main Sources                     
Hit http://security.ubuntu.com wily-security/multiverse amd64 Packages         
Hit http://us.archive.ubuntu.com wily-updates/restricted Sources               
Hit http://us.archive.ubuntu.com wily-updates/universe Sources                 
Hit http://security.ubuntu.com wily-security/main i386 Packages                
Hit http://us.archive.ubuntu.com wily-updates/multiverse Sources               
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://ppa.launchpad.net wily Release.gpg                                  
Hit http://us.archive.ubuntu.com wily-updates/main amd64 Packages              
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages        
Hit http://security.ubuntu.com wily-security/restricted i386 Packages          
Hit http://us.archive.ubuntu.com wily-updates/universe amd64 Packages
Hit http://ppa.launchpad.net wily/main amd64 Packages              
Hit http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com wily-security/universe i386 Packages            
Hit http://us.archive.ubuntu.com wily-updates/main i386 Packages               
Hit http://ppa.launchpad.net wily/main i386 Packages                
Hit http://us.archive.ubuntu.com wily-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily-updates/universe i386 Packages           
Hit http://security.ubuntu.com wily-security/multiverse i386 Packages          
Hit http://ppa.launchpad.net wily/main Translation-en          
Hit http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily-updates/main Translation-en  
Hit http://security.ubuntu.com wily-security/main Translation-en   
Hit http://us.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://ppa.launchpad.net wily/main amd64 Packages              
Hit http://us.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://ppa.launchpad.net wily/main i386 Packages               
Hit http://us.archive.ubuntu.com wily-backports/main Sources       
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://ppa.launchpad.net wily/main Translation-en              
Hit http://us.archive.ubuntu.com wily-backports/restricted Sources 
Hit http://security.ubuntu.com wily-security/universe Translation-en
Hit http://us.archive.ubuntu.com wily-backports/universe Sources   
Hit http://ppa.launchpad.net wily/main amd64 Packages              
Hit http://us.archive.ubuntu.com wily-backports/multiverse Sources
Hit http://us.archive.ubuntu.com wily-backports/main amd64 Packages  
Hit http://ppa.launchpad.net wily/main i386 Packages                 
Hit http://us.archive.ubuntu.com wily-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/main i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/universe i386 Packages
Hit http://ppa.launchpad.net wily/main Translation-en
Hit http://us.archive.ubuntu.com wily-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/main Translation-en
Hit http://us.archive.ubuntu.com wily-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-backports/restricted Translation-en
Ign http://ppa.launchpad.net wily Release       
Hit http://us.archive.ubuntu.com wily-backports/universe Translation-en
Err http://ppa.launchpad.net wily/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net wily/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_US                       
Ign http://ppa.launchpad.net wily/main Translation-en                          
W: Failed to fetch http://ppa.launchpad.net/paul-climbing/ppa/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/paul-climbing/ppa/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

How do I delete this PPA?

---

### Post by howefield on 2016-04-19
This is really a General Help question rather than one for System76.

Try opening a terminal and using the following command..

```
sudo rm /etc/apt/sources.list.d/paul-climbing-ubuntu-ppa-wily.list
```

and then 

```
sudo apt update
```

If you want to do it graphically, again use the terminal first to open the file manager with elevated privileges..

```
sudo -H nautilus
```

and navigate to /etc/apt/sources.list.d/ and delete the paul-climbing-ubuntu-ppa-wily.list file or move it out of the way, perhaps to your Documents folder if you want to hold on to it. Then close the Nautilus window so you don't do any damage.

---

### Post by ajgreeny on 2016-04-19
Just for the record, it looks as if that ppa has not been updated for almost 4 years, so is very unlikely to work now except in Precise 12.04.

---

