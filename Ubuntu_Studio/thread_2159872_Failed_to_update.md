---
title: "Failed to update"
date: 2013-07-04
forum: Ubuntu Studio
---

### Post by Acepony on 2013-07-04
I managed to get my system to update and it had a succesful reboot but with a message. I fallowed what it said and got this;

W:Failed to fetch [http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What does this mean?:confused:

---

### Post by Bashing-om on 2013-07-04
Acepony; Hi !

Looks like the PPA is no longer maintained,,,I see no other activity after 2011, last supported version was natty;

What application is the PPA attempting to update ? ... looks like Robert-ance had developed several.
In any event .. to resolve the error messages, remove that source from your software sources - Software Center, or edit the files directly from command line utilities; Whichever you are the more comfortable with.

[INDENT][INDENT][INDENT]just try'n to help
[/INDENT][/INDENT][/INDENT]

---

### Post by ennodj on 2013-07-08
Hello,

not sure in which thread to post this?

Kernel update fail

I&#7743; running ubuntu studio on a Aspire-5520G laptop

uname -a: Linux Aspire-5520 3.2.0-48-lowlatency-pae #50-Ubuntu SMP PREEMPT Sat Jun 8 16:20:41 UTC 2013 i686 athlon i386 GNU/Linux




After running:

apt-get dist-upgrade

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-49 linux-headers-3.2.0-49-generic-pae
  linux-headers-3.2.0-49-lowlatency-pae linux-image-3.2.0-49-generic-pae
  linux-image-3.2.0-49-lowlatency-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-headers-lowlatency-pae
  linux-image-generic-pae linux-image-lowlatency-pae linux-lowlatency-pae
6 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/90.1 MB of archives.
After this operation, 305 MB of additional disk space will be used.
Do you want to continue [Y/n]? 


When I choose "Y"

I get:

Get:1 Changelog for linux-image-generic-pae ([http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.49.59/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.49.59/changelog)) [32.3 kB]
linux-meta (3.2.0.49.59) precise; urgency=low

  [ Steve Conklin ]

  * Bump ABI

 -- Steve Conklin <sconklin@canonical.com>  Tue, 18 Jun 2013 12:37:21 -0500

Get:1 Changelog for linux-image-lowlatency-pae ([http://changelogs.ubuntu.com/changelogs/pool/universe/l/linux-meta-lowlatency/linux-meta-lowlatency_3.2.0.49.38/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/l/linux-meta-lowlatency/linux-meta-lowlatency_3.2.0.49.38/changelog)) [3,776 B]
linux-meta-lowlatency (3.2.0.49.38) precise; urgency=low

  * Bump ABI

 -- Kaj Ailomaa <zequence@mousike.me>  Mon, 24 Jun 2013 17:17:02 +0200

/tmp/tmpG94XpL (END)


and everything gets stuck...

Any Ideas?

Thank you in Advance;-)

---

### Post by Acepony on 2013-07-08
Here is more information on my part. I am still failing to update/Upgrade

This is the terminal output

> octavian@octavian-Inspiron-1545:~$ sudo apt-get update
[sudo] password for octavian: 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_US            
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg [933 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources                    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release [40.8 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources [46.7 kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources [14 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources [60.9 kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources [690 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages [120 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages [110 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages [1,403 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en_US   
Fetched 382 kB in 53s (7,149 B/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
octavian@octavian-Inspiron-1545:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-headers-lowlatency linux-image-generic
  linux-image-lowlatency linux-lowlatency
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
octavian@octavian-Inspiron-1545:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hyphen-en-us linux-headers-3.8.0-19-lowlatency
  linux-image-3.8.0-19-lowlatency linux-lowlatency-headers-3.8.0-19
  mythes-en-au openoffice.org-hyphenation sword-comm-mhcc sword-comm-pers
  sword-dict-naves sword-language-pack-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
octavian@octavian-Inspiron-1545:~$ 


---

### Post by Bashing-om on 2013-07-08
Acepony; Hi ! 

Let's get your source file database fixed up. Post the out put of terminal codes:
- between code tags (#) located at the top of the post -
```
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```
Next we will tackle the packages not upgraded situation.

[INDENT][INDENT]not a great big deal
[/INDENT][/INDENT]

---

### Post by jejeman on 2013-07-08
Remove the  [http://ppa.launchpad.net/robert-ance...-i386/Packages](http://ppa.launchpad.net/robert-ance...-i386/Packages) repository.

---

### Post by Acepony on 2013-07-10
here is the output.

> octavian@octavian-Inspiron-1545:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Studio 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
octavian@octavian-Inspiron-1545:~$ ls -la /etc/apt/sources.list.d
total 20
drwxr-xr-x 2 root root 4096 Jun 27 19:45 .
drwxr-xr-x 6 root root 4096 Jun 27 19:45 ..
-rw-r--r-- 1 root root  158 Jun 27 19:45 private-ppa.launchpad.net_commercial-ppa-uploaders_stroget_ubuntu.list
-rw-r--r-- 1 root root  158 Jun 27 19:45 private-ppa.launchpad.net_commercial-ppa-uploaders_stroget_ubuntu.list.save
-rw-r--r-- 1 root root  158 Jun 27 19:45 robert-ancell-sane-backends-raring.list
octavian@octavian-Inspiron-1545:~$ 


---

### Post by Bashing-om on 2013-07-10
Acepony; Hey ,

Same advise applies.
This one has seen no activity since Feb 2011, last supported version was natty, suggest remove that file in /etc/apt/sources.list.d.
> [http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/](http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/)

If you require guidance to remove that source, will be happy to oblige .

Once removed; run
```
sudo apt-get update
sudo apt-get upgrade

```

to get a fresh look.

[INDENT][INDENT]ain't nothing but a thing[/INDENT][/INDENT]

---

### Post by Acepony on 2013-07-12
How do you remove it? Do you just simply delete it in terminal or do you have to do the apt-get remove purge comand? Sorry still getting use to the normal terminal comands.

---

### Post by BreezyBrooke on 2013-07-12
To remove a ppa in Ubuntu Studio. Try this:

```
sudo add-apt-repository --remove ppa:robert-ancell/sane-backends
```

---

### Post by Acepony on 2013-07-13
It worked and no more errors to report. Thanks again.

---

