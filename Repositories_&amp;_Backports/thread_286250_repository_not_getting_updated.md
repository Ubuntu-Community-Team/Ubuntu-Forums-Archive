---
title: "repository not getting updated"
date: 2006-10-27
forum: Repositories &amp; Backports
---

### Post by rkakkar on 2006-10-27
my repository looks like this:

```

##################################
##### SUPPORTED/OFFICIAL UBUNTU-EDGY #####
##################################

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES
##(produced after the final release)
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

##### BACKPORTS REPOSITORY
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
                                                                                                                                                                          
##### CANONICAL COMMERCIAL REPOSITORY
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

####################
##### UNSUPPORTED #####
####################

##### PLF
##(Please report any bug on https://launchpad.net/products/plf/+bugs)
deb http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free


```

however update does not run successfully and basically freezes at the last step mentioned below. its not an issue with my Internet connection:

```

$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [189B]                                                           
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                                         
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]                                       
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US                                     
Get:3 http://archive.ubuntu.com edgy Release.gpg [191B]                                                       
Ign http://archive.ubuntu.com edgy/main Translation-en_US                                                     
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                     
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                       
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US                                     
Hit http://security.ubuntu.com edgy-security Release                                                          
Get:4 http://archive.canonical.com dapper-commercial Release [4886B]                                          
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                                                    
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                                                      
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                                                    
Get:5 http://archive.ubuntu.com edgy-proposed Release.gpg [189B]                                                   
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US                                                 
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US                                           
Hit http://security.ubuntu.com edgy-security/main Packages                                                         
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US                                             
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US                     
Get:6 http://archive.ubuntu.com edgy-updates Release.gpg [189B]                              
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US                            
Hit http://security.ubuntu.com edgy-security/restricted Packages                             
Hit http://security.ubuntu.com edgy-security/universe Packages                                                     
Hit http://security.ubuntu.com edgy-security/multiverse Packages                                                   
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US                                            
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US                        
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US                      
Get:7 http://archive.ubuntu.com edgy-backports Release.gpg [189B]                            
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US                          
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US                    
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US                      
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US                    
Hit http://archive.ubuntu.com edgy Release                                                   
Hit http://archive.ubuntu.com edgy-proposed Release                                          
Hit http://archive.ubuntu.com edgy-updates Release                                                                
Hit http://archive.ubuntu.com edgy-backports Release                                                              
Get:8 http://archive.canonical.com dapper-commercial/main Packages [1889B]                                                  
Hit http://archive.ubuntu.com edgy/main Packages                                                                            
Hit http://archive.ubuntu.com edgy/restricted Packages                                                                      
Hit http://archive.ubuntu.com edgy/universe Packages                                                                        
Ign http://archive.ubuntu.com edgy/multiverse Packages                                                                      
Hit http://archive.ubuntu.com edgy-proposed/main Packages                                                                   
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages                                                             
Hit http://archive.ubuntu.com edgy-proposed/universe Packages                                                               
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages                                                             
Hit http://archive.ubuntu.com edgy-updates/main Packages                                                                    
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                                                              
Hit http://archive.ubuntu.com edgy-updates/universe Packages                                                                
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages                                                              
Hit http://archive.ubuntu.com edgy-backports/main Packages                                                                  
Hit http://archive.ubuntu.com edgy-backports/restricted Packages                                                            
Hit http://archive.ubuntu.com edgy-backports/universe Packages                                                              
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages                                                            
Get:9 http://archive.ubuntu.com edgy/multiverse Packages [162kB]                                                            
99% [9 Packages gzip 0] [Connecting to packages.freecontrib.org]                                                 19.1kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/multiverse Packages                                                                      
  Sub-process gzip returned an error code (1)
99% [Connecting to packages.freecontrib.org]                                                                                

```

---

### Post by fireduck on 2006-10-27
I'm pretty sure the issue is with the last repository in your sources.list file. When I upgraded to Edgy earlier today I had to comment out (add # to the front of the line) all of my unsupported repositories because I was having connection issues with them. I imagine the connection issue is on the end of the unsupported repository and that's why you can't connect.

---

### Post by tronica on 2006-10-27
i'm having problems with the packages.freecontrib.org repo, i'm not able to connect. I was able too before edgy was released. Will it be back up.

---

### Post by rkakkar on 2006-10-28
okay. that solved the problem, but the repository still isn't getting updated :(

```

$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [189B]                                              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                               
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                         
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                           
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US                                         
Hit http://security.ubuntu.com edgy-security Release                                                              
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]           
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US         
Hit http://security.ubuntu.com edgy-security/main Packages                        
Hit http://archive.canonical.com dapper-commercial Release  
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages                    
Hit http://security.ubuntu.com edgy-security/multiverse Packages                  
Hit http://archive.canonical.com dapper-commercial/main Packages                  
Get:3 http://archive.ubuntu.com edgy Release.gpg [191B]                                                                     
Ign http://archive.ubuntu.com edgy/main Translation-en_US                                                                   
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                                                             
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                                                               
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                                                             
Get:4 http://archive.ubuntu.com edgy-proposed Release.gpg [189B]                                                            
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US                                                          
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US                                                    
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US                                                      
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US                                                    
Get:5 http://archive.ubuntu.com edgy-updates Release.gpg [189B]                                                             
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US                                                           
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US                                                     
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US                                                       
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US                                                     
Get:6 http://archive.ubuntu.com edgy-backports Release.gpg [189B]                                                           
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US                                                         
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US                                                   
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US                                                     
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US                                                   
Hit http://archive.ubuntu.com edgy Release                                                                                  
Hit http://archive.ubuntu.com edgy-proposed Release                                                                         
Hit http://archive.ubuntu.com edgy-updates Release                                                                          
Hit http://archive.ubuntu.com edgy-backports Release                                                                        
Hit http://archive.ubuntu.com edgy/main Packages                                                                            
Hit http://archive.ubuntu.com edgy/restricted Packages                                                                      
Hit http://archive.ubuntu.com edgy/universe Packages                                                                        
Ign http://archive.ubuntu.com edgy/multiverse Packages                                                                      
Hit http://archive.ubuntu.com edgy-proposed/main Packages                                                                   
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages                                                             
Hit http://archive.ubuntu.com edgy-proposed/universe Packages                                                               
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages                                                             
Hit http://archive.ubuntu.com edgy-updates/main Packages                                                                    
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                                                              
Hit http://archive.ubuntu.com edgy-updates/universe Packages                                                                
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages                                                              
Hit http://archive.ubuntu.com edgy-backports/main Packages                                                                  
Hit http://archive.ubuntu.com edgy-backports/restricted Packages                                                            
Hit http://archive.ubuntu.com edgy-backports/universe Packages                                                              
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages                                                            
Get:7 http://archive.ubuntu.com edgy/multiverse Packages [162kB]                                                            
99% [7 Packages gzip 0]                                                                                           3962B/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/multiverse Packages                                                                      
  Sub-process gzip returned an error code (1)
Fetched 7B in 11s (1B/s)                                                                                                    
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
$

```

---

### Post by depi on 2006-10-28
I have the same problem too, any solution?

---

### Post by ujecrh on 2006-10-30
Same problem here, no solution yet?

---

