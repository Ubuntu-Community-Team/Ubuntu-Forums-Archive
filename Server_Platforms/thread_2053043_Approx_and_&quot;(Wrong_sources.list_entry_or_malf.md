---
title: "Approx and &quot;(Wrong sources.list entry or malformed file)&quot;"
date: 2012-09-04
forum: Server Platforms
---

### Post by gnagnibu on 2012-09-04
Hi everybody.

I installed approx on Ubuntu Server 10.04.4; here /etc/approx/approx.conf

```

# Here are some examples of remote repository mappings.
# See http://www.debian.org/mirror/list for mirror sites.

#debian		http://ftp.debian.org/debian
#security	http://security.debian.org/debian-security
#volatile	http://volatile.debian.org/debian-volatile

ubuntu          http://it.archive.ubuntu.com/ubuntu
ubuntu-security http://security.ubuntu.com/ubuntu
ubuntu-partner  http://archive.canonical.com/ubuntu
ubuntu-extras	http://extras.ubuntu.com/ubuntu

# The following are the default parameter values, so there is
# no need to uncomment them unless you want a different value.
# See approx.conf(5) for details.

$port		9999
#$max_wait	10
#$max_rate	unlimited
#$user		approx
#$group		approx
#$syslog	daemon
#$pdiffs	true
#$verbose	false
#$debug		false

```

From other Ubuntu Server 12.04.1 :

1- /etc/apt/sources.list

```

deb http://192.168.200.106:9999/ubuntu precise main restricted universe multiverse
deb-src http://192.168.200.106:9999/ubuntu precise main restricted universe multiverse

deb http://192.168.200.106:9999/ubuntu precise-updates main restricted universe multiverse
deb-src http://192.168.200.106:9999/ubuntu precise-updates main restricted universe multiverse

deb http://192.168.200.106:9999/ubuntu-partner precise partner
deb-src http://192.168.200.106:9999/ubuntu-partner precise partner

deb http://192.168.200.106:9999/ubuntu-security precise-security main restricted universe multiverse
deb-src http://192.168.200.106:9999/ubuntu-security precise-security main restricted universe multiverse

```

and aptitude update:

```

# aptitude update
Ign http://192.168.200.106 precise InRelease
Ign http://192.168.200.106 precise-updates InRelease
Ign http://192.168.200.106 precise InRelease
Ign http://192.168.200.106 precise-security InRelease
Get: 1 http://192.168.200.106 precise Release.gpg [198 B]
Get: 2 http://192.168.200.106 precise-updates Release.gpg [198 B]
Get: 3 http://192.168.200.106 precise Release.gpg [198 B]
Get: 4 http://192.168.200.106 precise-security Release.gpg [198 B]
Get: 5 http://192.168.200.106 precise Release [49.6 kB]
Get: 6 http://192.168.200.106 precise-updates Release [49.6 kB]
Get: 7 http://192.168.200.106 precise Release [7,078 B]
Get: 8 http://192.168.200.106 precise-security Release [49.6 kB]
Get: 9 http://192.168.200.106 precise/main TranslationIndex [3,706 B]                                                                                                                                                                                                          
Get: 10 http://192.168.200.106 precise/multiverse TranslationIndex [2,676 B]                                                                                                                                                                                                   
Get: 11 http://192.168.200.106 precise/restricted TranslationIndex [2,596 B]                                                                                                                                                                                                   
Get: 12 http://192.168.200.106 precise/universe TranslationIndex [2,922 B]                                                                                                                                                                                                     
Get: 13 http://192.168.200.106 precise-updates/main TranslationIndex [3,564 B]                                                                                                                                                                                                 
Get: 14 http://192.168.200.106 precise-updates/multiverse TranslationIndex [2,605 B]                                                                                                                                                                                           
Get: 15 http://192.168.200.106 precise-updates/restricted TranslationIndex [2,461 B]                                                                                                                                                                                           
Get: 16 http://192.168.200.106 precise-updates/universe TranslationIndex [2,850 B]                                                                                                                                                                                             
Ign http://192.168.200.106 precise/partner TranslationIndex                                                                                                                                                                                                                    
Get: 17 http://192.168.200.106 precise/main Sources [1,175 kB]
Get: 18 http://192.168.200.106 precise/restricted Sources [5,306 B]                                                                                                                                                                                                            
Get: 19 http://192.168.200.106 precise/universe Sources [6,239 kB]                                                                                                                                                                                                             
Get: 20 http://192.168.200.106 precise/multiverse Sources [188 kB]                                                                                                                                                                                                             
Get: 21 http://192.168.200.106 precise/main amd64 Packages [1,640 kB]                                                                                                                                                                                                          
Get: 22 http://192.168.200.106 precise/restricted amd64 Packages [9,098 B]                                                                                                                                                                                                     
Get: 23 http://192.168.200.106 precise/universe amd64 Packages [6,167 kB]                                                                                                                                                                                                      
Get: 24 http://192.168.200.106 precise/multiverse amd64 Packages [152 kB]                                                                                                                                                                                                      
Get: 25 http://192.168.200.106 precise/main i386 Packages [1,641 kB]                                                                                                                                                                                                           
Get: 26 http://192.168.200.106 precise-security/main TranslationIndex [73 B]                                                                                                                                                                                                   
Get: 27 http://192.168.200.106 precise-security/multiverse TranslationIndex [71 B]
Get: 28 http://192.168.200.106 precise-security/restricted TranslationIndex [71 B]                                                                                                                                                                                             
Get: 29 http://192.168.200.106 precise-security/universe TranslationIndex [73 B]                                                                                                                                                                                               
Get: 30 http://192.168.200.106 precise/restricted i386 Packages [9,108 B]                                                                                                                                                                                                      
Get: 31 http://192.168.200.106 precise/universe i386 Packages [6,180 kB]                                                                                                                                                                                                       
Get: 32 http://192.168.200.106 precise/multiverse i386 Packages [155 kB]                                                                                                                                                                                                       
Get: 33 http://192.168.200.106 precise/main Translation-en_GB [96.4 kB]                                                                                                                                                                                                        
Get: 34 http://192.168.200.106 precise/main Translation-en [726 kB]                                                                                                                                                                                                            
Get: 35 http://192.168.200.106 precise/multiverse Translation-en_GB [79.8 kB]
Get: 36 http://192.168.200.106 precise/multiverse Translation-en [93.4 kB]
Get: 37 http://192.168.200.106 precise/restricted Translation-en_GB [2,406 B]
Get: 38 http://192.168.200.106 precise/restricted Translation-en [2,395 B]
Get: 39 http://192.168.200.106 precise/universe Translation-en_GB [5,492 B]
Get: 40 http://192.168.200.106 precise/universe Translation-en [3,341 kB]
Get: 41 http://192.168.200.106 precise-updates/main Sources [203 kB]
Get: 42 http://192.168.200.106 precise-updates/restricted Sources [2,997 B]
Get: 43 http://192.168.200.106 precise-updates/universe Sources [59.4 kB]
Get: 44 http://192.168.200.106 precise-updates/multiverse Sources [4,177 B]                                                                                                                                                                                                    
Get: 45 http://192.168.200.106 precise-updates/main amd64 Packages [486 kB]
Get: 46 http://192.168.200.106 precise-updates/restricted amd64 Packages [6,906 B]                                                                                                                                                                                             
Get: 47 http://192.168.200.106 precise-updates/universe amd64 Packages [165 kB]                                                                                                                                                                                                
Get: 48 http://192.168.200.106 precise-updates/multiverse amd64 Packages [9,084 B]                                                                                                                                                                                             
Get: 49 http://192.168.200.106 precise-updates/main i386 Packages [491 kB]                                                                                                                                                                                                     
Get: 50 http://192.168.200.106 precise-updates/restricted i386 Packages [6,885 B]                                                                                                                                                                                              
Get: 51 http://192.168.200.106 precise-updates/universe i386 Packages [166 kB]                                                                                                                                                                                                 
Get: 52 http://192.168.200.106 precise-updates/multiverse i386 Packages [10.2 kB]                                                                                                                                                                                              
Get: 53 http://192.168.200.106 precise-updates/main Translation-en_GB [96.4 kB]                                                                                                                                                                                                
Get: 54 http://192.168.200.106 precise-updates/main Translation-en [183 kB]                                                                                                                                                                                                    
Get: 55 http://192.168.200.106 precise-updates/multiverse Translation-en_GB [79.8 kB]                                                                                                                                                                                          
Get: 56 http://192.168.200.106 precise-updates/multiverse Translation-en [5,414 B]                                                                                                                                                                                             
Get: 57 http://192.168.200.106 precise-updates/restricted Translation-en_GB [2,406 B]                                                                                                                                                                                          
Get: 58 http://192.168.200.106 precise-updates/restricted Translation-en [1,484 B]                                                                                                                                                                                             
Get: 59 http://192.168.200.106 precise-updates/universe Translation-en_GB [5,492 B]                                                                                                                                                                                            
Get: 60 http://192.168.200.106 precise-updates/universe Translation-en [75.6 kB]                                                                                                                                                                                               
Get: 61 http://192.168.200.106 precise/partner Sources [3,895 B]                                                                                                                                                                                                               
Get: 62 http://192.168.200.106 precise/partner amd64 Packages [6,267 B]
Get: 63 http://192.168.200.106 precise/partner i386 Packages [4,691 B]
Get: 64 http://192.168.200.106 precise-security/main Sources [49.3 kB]                                                                                                                                                                                                         
Get: 65 http://192.168.200.106 precise-security/restricted Sources [1,742 B]                                                                                                                                                                                                   
Get: 66 http://192.168.200.106 precise-security/universe Sources [12.9 kB]                                                                                                                                                                                                     
Get: 67 http://192.168.200.106 precise-security/multiverse Sources [1,239 B]                                                                                                                                                                                                   
Get: 68 http://192.168.200.106 precise-security/main amd64 Packages [201 kB]
Get: 69 http://192.168.200.106 precise-security/restricted amd64 Packages [4,201 B]                                                                                                                                                                                            
Get: 70 http://192.168.200.106 precise-security/universe amd64 Packages [50.2 kB]                                                                                                                                                                                              
Get: 71 http://192.168.200.106 precise-security/multiverse amd64 Packages [1,965 B]                                                                                                                                                                                            
Get: 72 http://192.168.200.106 precise-security/main i386 Packages [206 kB]                                                                                                                                                                                                    
Get: 73 http://192.168.200.106 precise-security/restricted i386 Packages [4,197 B]                                                                                                                                                                                             
Get: 74 http://192.168.200.106 precise-security/universe i386 Packages [50.4 kB]                                                                                                                                                                                               
Get: 75 http://192.168.200.106 precise-security/multiverse i386 Packages [2,140 B]                                                                                                                                                                                             
Get: 76 http://192.168.200.106 precise-security/main Translation-en [75.2 kB]                                                                                                                                                                                                  
Get: 77 http://192.168.200.106 precise-security/multiverse Translation-en [995 B]                                                                                                                                                                                              
Get: 78 http://192.168.200.106 precise-security/restricted Translation-en [978 B]                                                                                                                                                                                              
Get: 79 http://192.168.200.106 precise-security/universe Translation-en [25.7 kB]                                                                                                                                                                                              
Ign http://192.168.200.106 precise/partner Translation-en_GB                                                                                                                                                                                                                   
Ign http://192.168.200.106 precise/partner Translation-en                                                                                                                                                                                                                      
Fetched 30.9 MB in 24s (1,273 kB/s)                                                                                                                                                                                                                                            
                            
Current status: 59051 new [+59040].

```

2- /etc/apt/sources.list

```

deb http://it.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse

deb http://it.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://security.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted universe multiverse

```

/etc/apt/apt.conf.d/01proxy

```

Acquire::http::Proxy "http://192.168.200.106:9999";

```

and aptitude update

```

# aptitude update
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.canonical.com precise InRelease
Get: 1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get: 2 http://security.ubuntu.com precise-security Release [49.6 kB]
Get: 3 http://archive.canonical.com precise Release.gpg [198 B]              
Get: 4 http://archive.canonical.com precise Release [49.6 kB]
Get: 5 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get: 6 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get: 7 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get: 8 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get: 9 http://security.ubuntu.com precise-security/main Sources [49.3 kB]
Get: 10 http://security.ubuntu.com precise-security/restricted Sources [1,742 B]
Get: 11 http://security.ubuntu.com precise-security/universe Sources [12.9 kB]
Get: 12 http://security.ubuntu.com precise-security/multiverse Sources [1,239 B]
Get: 13 http://security.ubuntu.com precise-security/main amd64 Packages [201 kB]
Get: 14 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,201 B]
Get: 15 http://security.ubuntu.com precise-security/universe amd64 Packages [50.2 kB]
Get: 16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,965 B]
Get: 17 http://security.ubuntu.com precise-security/main i386 Packages [206 kB]
Get: 18 http://security.ubuntu.com precise-security/restricted i386 Packages [4,197 B]
Get: 19 http://security.ubuntu.com precise-security/universe i386 Packages [50.4 kB]
Get: 20 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,140 B]
Get: 21 http://security.ubuntu.com precise-security/main Translation-en [75.2 kB]
Get: 22 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]
Get: 23 http://security.ubuntu.com precise-security/restricted Translation-en [978 B]
Get: 24 http://security.ubuntu.com precise-security/universe Translation-en [25.7 kB]
Ign http://it.archive.ubuntu.com precise InRelease
Ign http://it.archive.ubuntu.com precise-updates InRelease
Get: 25 http://it.archive.ubuntu.com precise Release.gpg [198 B]
Get: 26 http://it.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get: 27 http://it.archive.ubuntu.com precise Release [49.6 kB]
Get: 28 http://it.archive.ubuntu.com precise-updates Release [49.6 kB]
Get: 29 http://it.archive.ubuntu.com precise/main TranslationIndex [3,706 B]
Get: 30 http://it.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get: 31 http://it.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get: 32 http://it.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get: 33 http://it.archive.ubuntu.com precise/main Sources [1,175 kB]
Get: 34 http://it.archive.ubuntu.com precise/restricted Sources [5,306 B]
Get: 35 http://it.archive.ubuntu.com precise/universe Sources [6,239 kB]
Get: 36 http://it.archive.ubuntu.com precise/multiverse Sources [188 kB]
Get: 37 http://it.archive.ubuntu.com precise/main amd64 Packages [1,640 kB]
Get: 38 http://it.archive.ubuntu.com precise/restricted amd64 Packages [9,098 B]
Get: 39 http://it.archive.ubuntu.com precise/universe amd64 Packages [6,167 kB]
Get: 40 http://it.archive.ubuntu.com precise/multiverse amd64 Packages [152 kB]
Get: 41 http://it.archive.ubuntu.com precise/main i386 Packages [1,641 kB]
Get: 42 http://it.archive.ubuntu.com precise/restricted i386 Packages [9,108 B]
Get: 43 http://it.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get: 44 http://it.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get: 45 http://it.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get: 46 http://it.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get: 47 http://it.archive.ubuntu.com precise/universe i386 Packages [6,180 kB]
Get: 48 http://it.archive.ubuntu.com precise/multiverse i386 Packages [155 kB]                                                                                                                                                                                                 
Get: 49 http://it.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]                                                                                                                                                                                                  
Get: 50 http://it.archive.ubuntu.com precise/main Translation-en [726 kB]                                                                                                                                                                                                      
Get: 51 http://it.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]                                                                                                                                                                                            
Get: 52 http://it.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                                                                                                                                                                               
Get: 53 http://it.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]                                                                                                                                                                                            
Get: 54 http://it.archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                                                                                                                                                               
Get: 55 http://it.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]                                                                                                                                                                                              
Get: 56 http://it.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                                                                                                                                                                                
Get: 57 http://it.archive.ubuntu.com precise-updates/main Sources [203 kB]                                                                                                                                                                                                     
Get: 58 http://it.archive.ubuntu.com precise-updates/restricted Sources [2,997 B]                                                                                                                                                                                              
Get: 59 http://it.archive.ubuntu.com precise-updates/universe Sources [59.4 kB]                                                                                                                                                                                                
Get: 60 http://it.archive.ubuntu.com precise-updates/multiverse Sources [4,177 B]                                                                                                                                                                                              
Get: 61 http://it.archive.ubuntu.com precise-updates/main amd64 Packages [486 kB]                                                                                                                                                                                              
Get: 62 http://it.archive.ubuntu.com precise-updates/restricted amd64 Packages [6,906 B]                                                                                                                                                                                       
Get: 63 http://it.archive.ubuntu.com precise-updates/universe amd64 Packages [165 kB]                                                                                                                                                                                          
Get: 64 http://it.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,084 B]                                                                                                                                                                                       
Get: 65 http://it.archive.ubuntu.com precise-updates/main i386 Packages [491 kB]                                                                                                                                                                                               
Get: 66 http://it.archive.ubuntu.com precise-updates/restricted i386 Packages [6,885 B]                                                                                                                                                                                        
Get: 67 http://it.archive.ubuntu.com precise-updates/universe i386 Packages [166 kB]                                                                                                                                                                                           
Get: 68 http://it.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.2 kB]                                                                                                                                                                                        
Get: 69 http://it.archive.ubuntu.com precise-updates/main Translation-en_GB [96.4 kB]                                                                                                                                                                                          
Get: 70 http://it.archive.ubuntu.com precise-updates/main Translation-en [183 kB]                                                                                                                                                                                              
Get: 71 http://it.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [79.8 kB]                                                                                                                                                                                    
Get: 72 http://it.archive.ubuntu.com precise-updates/multiverse Translation-en [5,414 B]                                                                                                                                                                                       
Get: 73 http://it.archive.ubuntu.com precise-updates/restricted Translation-en_GB [2,406 B]                                                                                                                                                                                    
Get: 74 http://it.archive.ubuntu.com precise-updates/restricted Translation-en [1,484 B]                                                                                                                                                                                       
Get: 75 http://it.archive.ubuntu.com precise-updates/universe Translation-en_GB [5,492 B]                                                                                                                                                                                      
Get: 76 http://it.archive.ubuntu.com precise-updates/universe Translation-en [75.6 kB]                                                                                                                                                                                         
Fetched 30.9 MB in 17s (1,786 kB/s)                                                                                                                                                                                                                                            
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release  Unable to find expected entry 'partner/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

Current status: 59018 new [+59007].

```

any ideas?

Thanks!

---

