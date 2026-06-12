---
title: "Cannot update or install any software on my ubuntu 14.04LTS running on virtual machin"
date: 2015-06-17
forum: Virtualisation
---

### Post by Satyam_Dwivedi on 2015-06-17
i am getting following errors while using apt-get update

```
root@ubuntu:/home/ubuntu# apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                       
Ign [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty InRelease                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                    
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B] 
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Ign [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty Release.gpg               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [63.5 kB]   
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty Release                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed InRelease                     
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]                      
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]                
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [285 kB]   
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release.gpg [933 B]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [108 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]         
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,841 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release [58.5 kB]                   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [156 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [1,679 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [2,266 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [61.1 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [63.5 kB]         
Err [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty/partner Sources
  404  Not Found
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release [211 kB]
Err [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty/partner i386 Packages
  404  Not Found
Ign [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty/partner Translation-en_US
Ign [http://in.archive.canonical.com](http://in.archive.canonical.com) trusty/partner Translation-en
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [63.5 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources [1,064 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources [5,433 B]        
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources [6,399 kB]         
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources [174 kB]         
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages [1,348 kB]       
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages [13.4 kB]  
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages [5,866 kB]   
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages [134 kB]   
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en [762 kB]        
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en [102 kB]  
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en [3,457 B] 
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en [4,089 kB]  
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [6,285 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [30.3 kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,249 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [3,645 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en [776 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [26.7 kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted i386 Packages [28 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main i386 Packages [156 kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe i386 Packages [22.0 kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [28 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en [66.2 kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en [28 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en [28 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en [15.9 kB]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [11.8 kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [528 kB] 
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [287 kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [261 kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,148 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [2,774 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [150 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 22.7 MB in 48s (465 kB/s)                                              
W: Failed to fetch [http://in.archive.canonical.com/ubuntu/dists/trusty/partner/source/Sources](http://in.archive.canonical.com/ubuntu/dists/trusty/partner/source/Sources)  404  Not Found

W: Failed to fetch [http://in.archive.canonical.com/ubuntu/dists/trusty/partner/binary-i386/Packages](http://in.archive.canonical.com/ubuntu/dists/trusty/partner/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


I have tried manny things but am unable to solve the problem... It was working fine a while ago

---

### Post by QIII on 2015-06-17
What did you try already?  It would be helpful to know so people don't repeat the suggestions and waste time.

Based on what I see here, you should still be able to update much of your system.  To get all of it, I would try a different mirror before anything else.

---

### Post by Satyam_Dwivedi on 2015-06-17
I followed everything given here [http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error/160179#160179](http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error/160179#160179) but nothing worked

---

### Post by QIII on 2015-06-17
The 404 indicates that the resources at the trusty/Partner at in.archive are not available.  The page is not found.  That may mean the page no longer exists, or it is down either for maintenance or update.

Almost certainly, that means you will have to change at least those two repos, even if just temporarily.

Since you don't seem to be having trouble with any of the US archives, I would suggest changing those two specifically to the US mirror.  If you are using Unity, that can be accomplished through the Software Centre.

---

