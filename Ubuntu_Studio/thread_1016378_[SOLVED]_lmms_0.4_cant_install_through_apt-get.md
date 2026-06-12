---
title: "[SOLVED] lmms 0.4 cant install through apt-get???????"
date: 2008-12-19
forum: Ubuntu Studio
---

### Post by rixtr66 on 2008-12-19
I was happily using lmms 0.4.0 last week.but i had to reinstall
now when i add the address to the apt sources list it doesnt show up
when i do sudo apt-get update????ive done this before so i know it was working,im using ubuntu 8.04.1,have they made it only available to 8.10?
or is there something wrong with what im doing?
heres the sources```
deb http://ppa.launchpad.net/tobydox/ubuntu hardy main
deb-src http://ppa.launchpad.net/tobydox/ubuntu hardy main
```
and heres what i get when i update```
rick@ubuntu-laptop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security Release                
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://us.archive.ubuntu.com hardy-updates/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://ppa.launchpad.net hardy/main Sources                      
Hit http://security.ubuntu.com hardy-security/multiverse Sources     
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Fetched 1B in 0s (1B/s)  
Reading package lists... Done
rick@ubuntu-laptop:~$ 
```

it doesnt look like its there??or is it ,no matter it keeps giving me lmms 3.1,and i dont want that one!
any help would be appreciated!
Rick

---

### Post by barisurum on 2008-12-20
Here is a new version, maybe it will suit your needs. [http://lmms.sourceforge.net/download.php](http://lmms.sourceforge.net/download.php)

Edit: Ummm sorry I think its the same link that you have :S

---

### Post by thorgal on 2008-12-20
try in there : [http://ppa.launchpad.net/tobydox/ubuntu/pool/main/l/lmms/](http://ppa.launchpad.net/tobydox/ubuntu/pool/main/l/lmms/)

you may have dependency issues since these packages may have been compiled against Intrepid. Good luck.

---

### Post by rixtr66 on 2008-12-20
Yeah i think they moved ver.4 to intrepid!,soooo,i installed intrepid,
and got lmms,lmms-extras,and ALL the dependencies,i installed the suggested packages as well.so i think this problem is solved!
Thanks for the input!
Rick

---

### Post by megandy on 2009-01-24
Hi there,

I tried to install lmms via the repos above but I only get a version 3.1 on hardy. Can anyone confirm that 4.2 is also available for hardy?

Thanks

---

### Post by Stochastic on 2009-01-24
If you look at: [https://launchpad.net/~tobydox/+archive](https://launchpad.net/~tobydox/+archive)

You'll see that LMMS is only packaged for Intrepid (at least in this repository).

If you want 0.4 in Hardy, you'll need to build it from source.

---

