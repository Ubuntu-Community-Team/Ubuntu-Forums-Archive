---
title: "How to fix hosed package management system"
date: 2014-08-31
forum: Ubuntu Studio
---

### Post by mashaffer on 2014-08-31
For some time I have been dealing with a problem with my package management system. I have tried removing repositories that I had added to no avail. I am unable to do any upgrades or installations in a normal fashion through apt-get, synaptic or Ubuntu software center. If I can find a .deb for something and download it I can install it but none of the interfaces work.

sudo apt-get update gives tons of errors...

> 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe amd64 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted amd64 Packages/DiffIndex                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages/DiffIndex 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages/DiffIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages/DiffIndex                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages/DiffIndex                           
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages/DiffIndex                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages/DiffIndex            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted amd64 Packages/DiffIndex        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US                          
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en              
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
mike@mike-MacBookPro:~$ 

.
Does anyone know how to fix this? Is it possible to restore the package management system to its original state without reinstalling the entire OS?

I have tried the restore defaults in the authentication tab of the repositories in synaptic with no success. When I use the "select best server" button it says there are no suitable servers yet in firefox I can go to the servers.

Any ideas? Keep in mind I am pretty green when it comes to Linux administration.

mike

---

### Post by Bashing-om on 2014-08-31
mashaffer; Hi !

It falls on me I guess to be that bearer of bad news.
'raring' aka 13.04 is End_Of_Life and no longer has support, the software repository has been turned away and no longer exist as you have known it.
It is highly suggested and greatly recommended to upgrade to a current release.
The online method:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
old info, but still apt.

Easier, faster and the more secure means is to do a clean fresh install of a current release. Make sure your hardware supports the distribution you intend on installing. ( if it ran 13.04 well, then 14.04 should also do well )

[INDENT][INDENT]all good things come to an end
[/INDENT][/INDENT]

---

### Post by mashaffer on 2014-08-31
Oh, OK. I guess I should try. In a brief survey it appears rather complex but I would rather not have to reinstall jOrgan and all of the midi device extensions  etc, etc, etc. Worst case is an epic fail leading to having to do a fresh install anyway. Since this computer is OSX dual boot are there any special pitfalls (macbook pro)? Of course another option is to relent and buy that dedicated jOrgan computer that I really have been wanting in the first place.

mike

---

### Post by Bashing-om on 2014-08-31
mashaffer; UMMphhh..

Totally unqualified to offer an opinion in this context, I have not laid my hands on a Mac in years.
Others will have to advise here.

[INDENT][INDENT]what can I say ?
[INDENT][INDENT][INDENT][INDENT]I am not a know-it-all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mashaffer on 2014-08-31
Thank you very much for your help. I will ponder my options a bit and see where the spirit leads as it were. ;) The computer I have is a hand me down. There is no way I could afford Apple on my meager income. :D

mike

---

### Post by jejeman on 2014-09-01
If you really need to stick to 13.04 you can change your repositories to the archived ones.
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse
```

---

### Post by ian-weisser on 2014-09-01
...however, you will not receive any security updates.
Your system will be vulnerable to known, published exploits.
Not recommended for network-connected systems.

---

### Post by mashaffer on 2014-09-23
Your help is much appreciated. Since I have two systems set up with this I decided to start by doing a full install on the one that is dedicated to the organ project rather than my main home computer. The organ computer was dual boot with windows which I have no use for so I installed on the full hard disk. Seems to be working fine so I will probably install on my main computer next. One complication there is that it is dual boot OSX which I do need to keep so I will have to learn how to install it only to the existing linux partitions leaving OSX alone.

mike

---

### Post by mashaffer on 2014-10-03
> **mashaffer said:**
> Your help is much appreciated. Since I have two systems set up with this I decided to start by doing a full install on the one that is dedicated to the organ project rather than my main home computer. The organ computer was dual boot with windows which I have no use for so I installed on the full hard disk. Seems to be working fine so I will probably install on my main computer next. One complication there is that it is dual boot OSX which I do need to keep so I will have to learn how to install it only to the existing linux partitions leaving OSX alone.

mike

Just wanted to give you all an update. I did upgrade on the macbook and it went well. The installer complained about lack of a boot partition or something like that but it worked fine anyway. I had to reinstall a couple of applications but nothing very traumatic at all and as far as I can tell all of my functionality is back and dual booting is working fine.

I appreciate the help and encouragement.

mike

---

### Post by Bashing-om on 2014-10-03
mashaffer; Great !

Glad ya up and running - 14.04 ?? - 
Please that you took the time to let us know "how it goes", It is important to us.

As this matter is now completed, please mark this thread solved:
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
from the top of the post -> thread tools.

[INDENT][INDENT]I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

