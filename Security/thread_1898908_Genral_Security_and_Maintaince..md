---
title: "Genral Security and Maintaince."
date: 2011-12-22
forum: Security
---

### Post by The Little Book of Calm on 2011-12-22
I've been using Ubuntu 10.10 for a while and since I've manage to Iron out the kinks (such as wireless not working and speakers not muting with headphones) I've got to say I love it. However my main concern is the lack of security Applications such as AVG, Avast, anti spy ware and Comodos Firewall  that I used to use on a regular basis. And even though my laptop is running faster than ever I cant see any maintenance applications like disk defragmentor, disk cleaner or registry cleaner applications . Should this be something I should sort out or are all these applications not necessary with Linux.

It might be worth mentioning that I send emails and use pen drives with with windows operating systems on a regular basis and that I'd like to use online banking on my laptop to. 

Finally just a question of curiosity, if Linux is free then how does it manage to make profit. I've only been using Ubuntu for a short while but I can easily say it wipes the floor with Microsoft XP and by not buying a windows XP disk for my once dead laptop I've saved £60.

Whilst I remember I have a folder on my laptop called Lost + Found but I can not access it. Is is 35GB in size which is the same amount of memory used by my XP operating system and its files. Is there any way to gain access to it or shall I just delete it? (It's mainly games and music so its not the end of the world if it can't be opened)? Sorry for the bombardment of questions but any information will be greatly appreciated, thanks.

---

### Post by MG&amp;TL on 2011-12-22
Some links:

[http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

[wiki.ubuntu.com/BasicSecurity]("wiki.ubuntu.com/BasicSecurity")

Disk defragmenting is (generally) not necessary on Linux, the filesystem doesn't fragment in the same way.

AV is also not really necessary, but check the security link first. :)


Lost-found you cannot access as anything but root, as far as I can tell it's random deleted stuff waiting to be reallocated somewhere else. Don't try.

if you *need* to have a clean, look at ubuntu tweak and bleachbit. Both cleaner programs.

And a hint, please don't use centered typeface, it's really hard to read. :) Thanks!

---

### Post by Megaptera on 2011-12-22
Hi,
Useful info on Ubuntu security here: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

This about Ubuntu and how it makes money "Ubuntu is backed by Canonical - the number-one Ubuntu services provider.
Companies can choose to receive expert training, support or consultancy for a fee that goes towards the continued development of Ubuntu." [http://www.ubuntu.com/project](http://www.ubuntu.com/project)

---

### Post by The Little Book of Calm on 2011-12-22
Thanks for the links, Ive red them and noticed that I do need to run some updates but I'm having problems. When I attempt to run update manage i get this error message.

Could not determine the upgrade 
  
 An unresolvable problem occurred while calculating the upgrade. 
  
 Please report this bug in the 'update-manager' package and try to include the following error message: 
 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

when I then click install updates I get this message. 


Requires installation of untrusted packages 
  
 The action would require the installation of packages from unauthenticated sources.
 
 app-install-data libavc1394-0 libraw1394-8 mailx

What would anyone recommend?

---

### Post by oldos2er on 2011-12-22
Please use the default font size.

Re: your update problem, can you run ```
sudo apt-get update
``` in a terminal (Ctrl-Alt-t) and post the output here?

---

### Post by The Little Book of Calm on 2011-12-22
results from terminal:
```

dominic@dominic-HP-Compaq-nx6325-EY345EA-ABU:~$ sudo apt-get update
[sudo] password for dominic: 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main Translation-en_GB
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB       
Get:1 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release.gpg [1,034B]                      
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB   
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg [198B]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en_GB              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/) maverick/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg      
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release.gpg [198B]
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Get:4 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release [85.6kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release                    
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release [31.4kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  404  Not Found
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release [32.4kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  404  Not Found
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages    
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Sources/DiffIndex              
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main i386 Packages/DiffIndex        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse i386 Packages
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources [146kB]
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main i386 Packages
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources [778B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources [55.0kB]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources [2,513B]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main i386 Packages [397kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe i386 Packages [185kB]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,213B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/main i386 Packages [128kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/universe i386 Packages [29.4kB]
Fetched 1,016kB in 2s (419kB/s)                           
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: Failed to fetch [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dominic@dominic-HP-Compaq-nx6325-EY345EA-ABU:~$ ^C
```

---

### Post by MG&amp;TL on 2011-12-22
Close anything else that's running a package manager. Ubuntu software centre, synaptic...

---

### Post by cariboo on 2011-12-22
> **The Little Book of Calm said:**
> results from terminal:
```

dominic@dominic-HP-Compaq-nx6325-EY345EA-ABU:~$ sudo apt-get update
[sudo] password for dominic: 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main Translation-en_GB
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB       
Get:1 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release.gpg [1,034B]                      
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB   
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg [198B]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en_GB              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/) maverick/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg      
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release.gpg [198B]
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Get:4 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release [85.6kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release                    
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release [31.4kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  404  Not Found
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed Release [32.4kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  404  Not Found
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages    
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Sources/DiffIndex              
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main i386 Packages/DiffIndex        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse i386 Packages
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources [146kB]
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main i386 Packages
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources [778B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources [55.0kB]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources [2,513B]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main i386 Packages [397kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe i386 Packages [185kB]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,213B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/main i386 Packages [128kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-proposed/universe i386 Packages [29.4kB]
Fetched 1,016kB in 2s (419kB/s)                           
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: Failed to fetch [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/zsitvaij/ppa-zsitvaij/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dominic@dominic-HP-Compaq-nx6325-EY345EA-ABU:~$ ^C
```

You may run into problems using debian repositories as well as Ubuntu repositories, because of dependancy problems. Ubuntu uses Debian for it's base, and takes a snapshot of the Debian repositories at the start of each development cycle.

I also see from you output that you are getting 404's from a couple of ppa.

I'd suggest you bring your /etc/apt/sources back to the default. remove the ppas and debian repositories, and try again.

---

### Post by The Little Book of Calm on 2011-12-23
I've solved the security problem by updating to ubuntu 11.10 however it seems to be running a lot slower and is not capable of running 3d games (emulators) quiet as smoothly. The boot up speed has tripled, opening applications takes longer and whenever i attempt to due tasks such as move windows or browse folders there is quiet a bit of lag.  I've looked around and although it seems like a common issues there doesn't appear to be a common solution. It's not so slow that I can't use my laptop but it's defiantly less enjoyable to use.

Also how would I bring back the  /etc/apt/sources and remove the ppas and debian repositories. I'm still kinda new to all this.

My laptop specs are

HP - Compaq nx6325
1.8ghz amd processor
ATI graphics card
128mb of vram
1gb of ram
60gb hdd


Thanks for putting up with all my questions.

---

### Post by MG&amp;TL on 2011-12-23
I would reccommend usinbg something like ppa-purge to remove the PPAs, but you can do it with:

```
gksu gedit /etc/apt/sources.list
```

and removing any ppa and debian references. Also remove anything from /etc/apt/sources.list.d/ that mentions a PPA.

Be CAREFUL.

If you don't like Unity, google Ubuntu alternatives. It's here to stay and it's not changing. Sorry. Xubuntu, Lubunt, and Kubuntu are all good alternatives. Also Linux Mint.

---

### Post by The Little Book of Calm on 2011-12-28
Its sorted thank you.

---

