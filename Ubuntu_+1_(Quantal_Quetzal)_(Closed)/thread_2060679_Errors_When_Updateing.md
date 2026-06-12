---
title: "Errors When Updateing"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by robtygart on 2012-09-20
Kubuntu 12.10

When I sudo apt-get update, I end with errors.

```
rob@mobile:~$ sudo apt-get update
[sudo] password for rob: 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                                                         
Ign http://us.archive.ubuntu.com quantal InRelease                                                                                                                            
Get:2 http://dl.google.com stable Release                                                                             
Ign http://us.archive.ubuntu.com quantal-updates InRelease                                                           
Ign http://security.ubuntu.com quantal-security InRelease                                  
Ign http://extras.ubuntu.com quantal InRelease                                             
Ign http://ppa.launchpad.net quantal InRelease                                             
Ign http://us.archive.ubuntu.com quantal-backports InRelease                               
Hit http://security.ubuntu.com quantal-security Release.gpg                                
Hit http://extras.ubuntu.com quantal Release.gpg                                           
Get:3 http://us.archive.ubuntu.com quantal Release.gpg [933 B]                             
Ign http://ppa.launchpad.net quantal Release.gpg                                                                             
Hit http://us.archive.ubuntu.com quantal-updates Release.gpg                                                      
Get:4 http://dl.google.com stable/main amd64 Packages [469 B]                               
Hit http://security.ubuntu.com quantal-security Release                                                                                  
Hit http://extras.ubuntu.com quantal Release                                                                       
Ign http://ppa.launchpad.net quantal Release                                                                       
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg                               
Get:5 http://dl.google.com stable/main i386 Packages [464 B]                                 
Get:6 http://us.archive.ubuntu.com quantal Release [49.6 kB]                                                      
Hit http://security.ubuntu.com quantal-security/main Sources                                                             
Hit http://extras.ubuntu.com quantal/main Sources                                                                        
Hit http://security.ubuntu.com quantal-security/restricted Sources                                   
Hit http://extras.ubuntu.com quantal/main amd64 Packages                                             
Hit http://us.archive.ubuntu.com quantal-updates Release                                                                                   
Hit http://security.ubuntu.com quantal-security/universe Sources                                                                         
Hit http://extras.ubuntu.com quantal/main i386 Packages                                                                                  
Hit http://us.archive.ubuntu.com quantal-backports Release                                                                               
Hit http://security.ubuntu.com quantal-security/multiverse Sources                                                                       
Ign http://dl.google.com stable/main Translation-en_US                                                            
Get:7 http://us.archive.ubuntu.com quantal/main Sources [868 kB]                            
Ign http://dl.google.com stable/main Translation-en                                                                     
Hit http://security.ubuntu.com quantal-security/main amd64 Packages                                                     
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages                         
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages                            
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages                          
Hit http://security.ubuntu.com quantal-security/main i386 Packages           
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages     
Hit http://security.ubuntu.com quantal-security/universe i386 Packages                             
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages                           
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                        
Ign http://extras.ubuntu.com quantal/main Translation-en                                           
Hit http://security.ubuntu.com quantal-security/main Translation-en          
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en                                                                                                         
Hit http://security.ubuntu.com quantal-security/restricted Translation-en                                                                                                         
Get:8 http://us.archive.ubuntu.com quantal/restricted Sources [5,611 B]                                                                                                           
Hit http://security.ubuntu.com quantal-security/universe Translation-en                                                                                                           
Get:9 http://us.archive.ubuntu.com quantal/universe Sources [5,539 kB]                                                                                                            
Err http://ppa.launchpad.net quantal/main Sources                                                                                                                                 
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages                                                                                                                          
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages                                                                                                                           
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US                                                                                                                       
Ign http://ppa.launchpad.net quantal/main Translation-en                                                                                                                          
Ign http://security.ubuntu.com quantal-security/main Translation-en_US                                                                                                            
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US                                                                                                      
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US                                                                                                      
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US                                                                                                        
Get:10 http://us.archive.ubuntu.com quantal/multiverse Sources [166 kB]                                                                                                            
Get:11 http://us.archive.ubuntu.com quantal/main amd64 Packages [1,138 kB]                                                                                                          
Get:12 http://us.archive.ubuntu.com quantal/restricted amd64 Packages [8,295 B]                                                                                                     
Get:13 http://us.archive.ubuntu.com quantal/universe amd64 Packages [5,325 kB]                                                                                                      
Get:14 http://us.archive.ubuntu.com quantal/multiverse amd64 Packages [128 kB]                                                                                                      
Get:15 http://us.archive.ubuntu.com quantal/main i386 Packages [1,138 kB]                                                                                                           
Get:16 http://us.archive.ubuntu.com quantal/restricted i386 Packages [8,240 B]                                                                                                      
Get:17 http://us.archive.ubuntu.com quantal/universe i386 Packages [5,334 kB]                                                                                                       
Get:18 http://us.archive.ubuntu.com quantal/multiverse i386 Packages [130 kB]                                                                                                       
Get:19 http://us.archive.ubuntu.com quantal/main Translation-en [659 kB]                                                                                                            
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en                                                                                                                  
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en                                                                                                                  
Get:20 http://us.archive.ubuntu.com quantal/universe Translation-en [3,669 kB]                                                                                                      
Hit http://us.archive.ubuntu.com quantal-updates/main Sources                                                                                                                       
Hit http://us.archive.ubuntu.com quantal-updates/restricted Sources                                                                                                                 
Hit http://us.archive.ubuntu.com quantal-updates/universe Sources                                                                                                                   
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Sources                                                                                                                 
Hit http://us.archive.ubuntu.com quantal-updates/main amd64 Packages                                                                                                                
Hit http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages                                                                                                          
Hit http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages                                                                                                            
Hit http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages                                                                                                          
Hit http://us.archive.ubuntu.com quantal-updates/main i386 Packages                                                                                                                 
Hit http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages                                                                                                           
Hit http://us.archive.ubuntu.com quantal-updates/universe i386 Packages                                                                                                             
Hit http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages                                                                                                           
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en                                                                                                                
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en                                                                                                          
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en                                                                                                          
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en                                                                                                           
Hit http://us.archive.ubuntu.com quantal-backports/main Sources                                                                                                                    
Hit http://us.archive.ubuntu.com quantal-backports/restricted Sources                                                                                                              
Hit http://us.archive.ubuntu.com quantal-backports/universe Sources                                                                                                                
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Sources                                                                                                              
Hit http://us.archive.ubuntu.com quantal-backports/main amd64 Packages                                                                                                             
Hit http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages                                                                                                       
Hit http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages                                                                                                         
Hit http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages                                                                                                       
Hit http://us.archive.ubuntu.com quantal-backports/main i386 Packages                                                                                                              
Hit http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages                                                                                                        
Hit http://us.archive.ubuntu.com quantal-backports/universe i386 Packages                                                                                                          
Hit http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages                                                                                                        
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en                                                                                                             
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en                                                                                                       
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en                                                                                                       
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en                                                                                                         
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                                                                                                                    
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Fetched 24.2 MB in 3min 35s (112 kB/s)
W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
rob@mobile:~$ 

```

---

### Post by arpanaut on 2012-09-20
There are no packages for quantal in that ppa.
See:
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/)

---

### Post by robtygart on 2012-09-20
How do I keep from getting the message?

---

### Post by whatthefunk on 2012-09-20
Comment out those ppas in /etc/apt/sources.list and from the relavant files in /etc/apt/sources.list.d/  Then run sudo apt-get update again.

You can also use the GUI.  Open up Muon and edit the software sources.

---

### Post by robtygart on 2012-09-20
That fixed it! 

Thank you...

---

