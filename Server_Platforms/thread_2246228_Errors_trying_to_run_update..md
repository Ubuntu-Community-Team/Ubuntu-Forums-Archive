---
title: "Errors trying to run update."
date: 2014-09-29
forum: Server Platforms
---

### Post by irv on 2014-09-29
This morning when I login to my server it said I had two security updates so I ran
```
sudo apt-get update
```

and here is what I got.

> no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
  
Err [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
  
Err [http://download.webmin.com](http://download.webmin.com) sarge InRelease
  
Err [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg
  Could not resolve 'download.webmin.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/InRelease](http://archive.canonical.com/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease](http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://download.webmin.com/download/repository/dists/sarge/InRelease](http://download.webmin.com/download/repository/dists/sarge/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg](http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://download.webmin.com/download/repository/dists/sarge/Release.gpg](http://download.webmin.com/download/repository/dists/sarge/Release.gpg)  Could not resolve 'download.webmin.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

My network and Internet are up and running but not sure what is going on why it can't fetch packages. It can't even reach the Ubuntu repository. Also I see that memory leak again. Does anyone have any idea what's going on.

Thanks.

---

### Post by weedwacker2 on 2014-09-29
I have the exact same problem as you. I have already posted my plea for help, but at this time not resolved yet. I do have some things I want to try to see if I am successful. One of which is to turn off my automatic updates.

Are you running a server edition? 12.04 or 14.04?

---

### Post by weedwacker2 on 2014-09-29
Try the solution that I got here: [http://ubuntuforums.org/showthread.php?t=2246138&p=13131725#post13131725](http://ubuntuforums.org/showthread.php?t=2246138&p=13131725#post13131725)

Weedwacker

---

### Post by irv on 2014-09-29
Added nameserver 8.8.8.8 8.8.4.4 and adding "dns-nameservers 8.8.8.8 8.8.4.4" to /etc/network/interfaces rebooted the server and this fixed the problem. Here is what a got with

```
sudo apt-get update
```

> Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://download.webmin.com](http://download.webmin.com) sarge InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release                                   
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [59.7 kB]            
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://download.webmin.com](http://download.webmin.com) sarge/contrib i386 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [59.7 kB]          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources/DiffIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages/DiffIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [45.3 kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [10.8 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [121 kB]       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [700 B]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [136 kB]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [85.1 kB]  
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [3,527 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [318 kB] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [206 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,545 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [146 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [48.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,398 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [104 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [4,760 B]    
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [70.2 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [13.7 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1,315 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [6,379 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [16.8 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [945 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [28.6 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [14.3 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 1,582 kB in 7s (219 kB/s)                                              
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

---

### Post by irv on 2014-09-29
> **weedwacker2 said:**
> I have the exact same problem as you. I have already posted my plea for help, but at this time not resolved yet. I do have some things I want to try to see if I am successful. One of which is to turn off my automatic updates.

Are you running a server edition? 12.04 or 14.04?

I am running 14.04.

---

### Post by weedwacker2 on 2014-09-29
It looks like you got your updates except for the last item which I don't know about.

Did you also run: sudo apt-get upgrade to load your new updated files?

weedwacker

---

### Post by irv on 2014-09-29
I am running

> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

when I type

```
 lsb_release -a
```

Will mark thread solved.

---

