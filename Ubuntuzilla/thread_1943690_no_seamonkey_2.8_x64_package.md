---
title: "no seamonkey 2.8 x64 package"
date: 2012-03-19
forum: Ubuntuzilla
---

### Post by Maloy14 on 2012-03-19
I found out that seamonkey has updated to a new version ( 2.8 ), but when I use update manager, the package doesn't show up.  I have ubuntuzilla ppa in my software sources, but it seems it does not have the package.  Here is what i wrote at the terminal:

maloy@maloy-laptop:~$ sudo apt-get update
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg                           
Ign [http://downloads.sourceforge.net/project/ubuntuzila/mozilaa/apt/](http://downloads.sourceforge.net/project/ubuntuzila/mozilaa/apt/) all/main Translation-en_PH
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu/](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu/) lucid/main Translation-en_PH
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_PH   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_PH
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_PH       
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_PH          
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_PH    
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release                               
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                               
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_PH                   
Ign [http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu/](http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu/) lucid/main Translation-en_PH
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) lucid/main Translation-en_PH
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/showard314/librecad/ubuntu/](http://ppa.launchpad.net/showard314/librecad/ubuntu/) lucid/main Translation-en_PH
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) lucid/main Translation-en_PH
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_PH
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_PH
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_PH      
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_PH    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_PH  
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_PH
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid Release                                 
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates Release                         
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/main Packages                           
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/main Sources                            
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/universe Packages                       
Err [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
  404  Not Found
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/universe Sources              
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/main Sources          
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/universe Packages     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/universe Sources      
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/multiverse Sources
W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzila/mozilaa/apt/dists/all/main/binary-amd64/Packages.gz](http://downloads.sourceforge.net/project/ubuntuzila/mozilaa/apt/dists/all/main/binary-amd64/Packages.gz)  404  Not Found

I tried to follow the link at sourceforge, but it does not have the package.  I also tried apt-get install seamonkey=2.8:

maloy@maloy-laptop:~$ sudo apt-get install seamonkey=2.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '2.8' for 'seamonkey' was not found

Little help. Thanks!

---

### Post by Karlchen on 2012-03-20
Hello, Maloy14.

Based on these lines which "apt-get update" generates > Err [http://downloads.sourceforge.net]("http://downloads.sourceforge.net/") all/main Packages                         
  404  Not Found I wonder whether the corresponding line in your file /etc/apt/sources.list really reads ```
http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
``` At least it is worth verifying.

Kind regards,
Karl

---

### Post by Maloy14 on 2012-03-27
Hi Karl,

Thanks for the reply, and I apologize for not replying before now.  I checked my software sources and found out that my ubuntuzilla apt had typo errors.  I already fixed them, but still no seamonkey 2.8 package detected when I run update manager.

---

### Post by nanotube on 2012-03-27
Hi,
the ubuntuzilla package is called "seamonkey-mozilla-build" not plain "seamonkey". Give that a try :)

---

### Post by Maloy14 on 2012-03-28
Hi,
I figured it out, and it was a silly mistake. :p
I could not update my seamonkey because i installed it by downloading from the seamonkey site, and not by apt-get.  Hence, it wasn't listed in the synaptic package manager.  I tried seamonkey-mozilla-project and it worked. Am now writing this reply and viewing this page with seamonkey 2.8 :)

Thanks

---

### Post by nanotube on 2012-03-29
great :)

---

