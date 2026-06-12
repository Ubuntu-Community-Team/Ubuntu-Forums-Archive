---
title: "LAMP server: &quot;unmet dependencies&quot;"
date: 2011-10-23
forum: Server Platforms
---

### Post by dargaud on 2011-10-23
Hello all,
I never know what to do when there are unmet dependencies. Here I'm trying to reinstall my LAMP server on a fresh 11.10 install:
```
$ sudo aptitude install phpmyadmin
The following NEW packages will be installed:
  dbconfig-common{a} libgd2-xpm{ab} libmcrypt4{a} libt1-5{a} php5-gd{a} php5-mcrypt{a} php5-mysql{a} phpmyadmin 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,290 kB of archives. After unpacking 22.0 MB will be used.
The following packages have unmet dependencies:
  libgd2-xpm: Conflicts: libgd2 which is a virtual package.
              Conflicts: libgd2-noxpm but 2.0.36~rc1~dfsg-5.1ubuntu1 is installed.
  libgd2-noxpm: Conflicts: libgd2 which is a virtual package.
                Conflicts: libgd2-xpm but 2.0.36~rc1~dfsg-5.1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

      Remove the following packages:                              
1)      flashplugin-downloader                                    
2)      flashplugin-installer                                     
3)      libasound2                                                
4)      libasound2-plugins                                        
5)      libasyncns0                                               
6)      libatk1.0-0                                               
7)      libavahi-client3                                          
8)      libavahi-common3                                          
9)      libc6                                                     
10)     libcairo2                                                 
11)     libcomerr2                                                
12)     libcups2                                                  
13)     libcurl3                                                  
14)     libdatrie1                                                
15)     libdb5.1                                                  
16)     libdbus-1-3                                               
17)     libexpat1                                                 
18)     libffi6                                                   
19)     libflac8                                                  
20)     libfontconfig1                                            
21)     libfreetype6                                              
22)     libgcc1                                                   
23)     libgcrypt11                                               
24)     libgdk-pixbuf2.0-0                                        
25)     libglib2.0-0                                              
26)     libgnutls26                                               
27)     libgpg-error0                                             
28)     libgssapi-krb5-2                                          
29)     libgtk2.0-0                                               
30)     libice6                                                   
31)     libidn11                                                  
32)     libjack-jackd2-0                                          
33)     libjasper1                                                
34)     libjpeg62                                                 
35)     libjson0                                                  
36)     libk5crypto3                                              
37)     libkeyutils1                                              
38)     libkrb5-3                                                 
39)     libkrb5support0                                           
40)     libldap-2.4-2                                             
41)     libnspr4                                                  
42)     libnspr4-0d                                               
43)     libnss3                                                   
44)     libnss3-1d                                                
45)     libogg0                                                   
46)     libpango1.0-0                                             
47)     libpcre3                                                  
48)     libpixman-1-0                                             
49)     libpng12-0                                                
50)     libpulse0                                                 
51)     librtmp0                                                  
52)     libsamplerate0                                            
53)     libsasl2-2                                                
54)     libsasl2-modules                                          
55)     libselinux1                                               
56)     libsm6                                                    
57)     libsndfile1                                               
58)     libspeexdsp1                                              
59)     libsqlite3-0                                              
60)     libssl1.0.0                                               
61)     libstdc++6                                                
62)     libtasn1-3                                                
63)     libthai0                                                  
64)     libtiff4                                                  
65)     libuuid1                                                  
66)     libvorbis0a                                               
67)     libvorbisenc2                                             
68)     libwrap0                                                  
69)     libx11-6                                                  
70)     libxau6                                                   
71)     libxcb-render0                                            
72)     libxcb-shm0                                               
73)     libxcb1                                                   
74)     libxcomposite1                                            
75)     libxcursor1                                               
76)     libxdamage1                                               
77)     libxdmcp6                                                 
78)     libxext6                                                  
79)     libxfixes3                                                
80)     libxft2                                                   
81)     libxi6                                                    
82)     libxinerama1                                              
83)     libxrandr2                                                
84)     libxrender1                                               
85)     libxt6                                                    
86)     nspluginviewer                                            
87)     nspluginwrapper                                           
88)     zlib1g                                                    

      Keep the following packages at their current version:       
89)     libgd2-xpm [Not Installed]                                
90)     php5-gd [Not Installed]                                   

      Leave the following dependencies unresolved:                
91)     phpmyadmin recommends php5-gd                             
92)     kubuntu-restricted-addons recommends flashplugin-installer


Accept this solution? [Y/n/q/?]
```
Removing 88 packages because libgd is missing ?!? Seems a little harsh, no ? What am I supposed to do in this case ?

And why does it suggest to '*keep at their current version*' packages which are '*not installed*' ? What's that even supposed to mean ?

Apache & Co were installed as such:
```
sudo aptitude install php5 mysql-server
```
Trying to install php5-gd leads to a big list of problems like above.

---

### Post by dargaud on 2011-10-24
I do not understand what's going to happen if I clic 'Yes'. Anyone cares to elaborate ?
Thanks.

---

### Post by koenn on 2011-10-24
Don't click "yes"

it *will* delete all  those packages, and you probably don't want that


What you're seeing is probably a result of cascading dependencies.
The package manager has detected a dependency conflict, and calculates what will happen if the offending package is removed

If that results in the removal of 1 or 2 obviously related packages, you'd probably accept that as a solution.
In this case, it seems to trigger a removal that causes other packages to be removed as well because they depend on the removed package, an dpossibly that triggered the removal of some more packages that depend on the previous set of removed packages,  ...  etc, you get the picture. 


if this really is a fresh install with standard repositories, I'd say there's a problem in the packaging of phpmyadmin and/or php-gd or the the libgd packages.


In that case, it should get fixed in an update.
You might want to try to ignore the dependency issue, but that 'll most likely break a number of things. 



If it's not really a fresh install (you've been tweaking stuff, you've added ppas and 3th party repos, you got some leftover libs with wrong versions for the current release, you've been messing with apt preferences and sources lists, you've  installed software from tarbals or other non-apt methods, ...)n then that is possible the reson the dependencies don't work out correctly, and you have to get to the bottom of that. 




"Deer in the headlights" - yeah, I know that feeling. 's been a while, though ...

---

### Post by dargaud on 2011-10-25
That's a fresh install because of a completely collapsed kmail. I hated to do it as all those LAMP stuff are always hard to reinstall as they were before. Indeed. So I'm stuck having to wait for corrections ? Or installing phpmyadmin manually.

---

### Post by koenn on 2011-10-25
The conflict is in the libgd2 package, and it looks like you have something there that's 'release candidate' ('rc in the name ?)
```

  libgd2-xpm: Conflicts: libgd2 which is a virtual package.
              Conflicts: libgd2-noxpm but 2.0.36~rc1~dfsg-5.1ubuntu1 is installed.
  libgd2-noxpm: Conflicts: libgd2 which is a virtual package.
                Conflicts: libgd2-xpm but 2.0.36~rc1~dfsg-5.1ubuntu1 is to be installed.
```
It could be a packaging error, or just a naming convention (a Debian rc repackaged by ubuntu), or it's a sign your install isn't as clean as you think it is.



I think you need to review your sources.list, and possibly reduce it to the bare minimum - including the sources.list.d, then run apt-get update to get the newest package definitions, then see if the problem goes away when you install phpmyadmin


If that doesn't help, I'd apt-get remove libgd2, libgd2-noxpm, libgd2-xpm, 
and try installing phpmyadmin again.

If that also doesn't work, again apt-get remove libgd2, libgd2-noxpm, libgd2-xpm, 
and install every one of those packages one by one.
I'm guessing a good order would be
dbconfig-common  libgd2-xpm  libmcrypt4 libt1-5 php5-gd php5-mcrypt  php5-mysql  phpmyadmin

Reason behind this : 
- see which ones cause trouble, to narrow it down, and 
- it might avoid errors in the calculation of "required packages"

If any of that causes weird output ("along the lines of 500 packages will be removed", or "if you contibue your system may become unbootable"), don't continue; stop and think. 


But the most important thing is : check that this is *not* caused by a stray package from a forgotten testing/experimental/3rd party/ppa/... repo in an overlooked sources list in sources.list.d, or so

---

### Post by dargaud on 2011-10-27
I installed from CD last week and just performed the default updates after that. I haven't touched the repositories.
```
$ cat /etc/apt/sources.list
#deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

#deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

I solved the PhpMyAdmin problem by simply installing manually (easy in that case), but still I'm suspicious...

---

### Post by koenn on 2011-10-27
you may run into problems when future updates replace the libraries phpadmin now uses, that's something to keep in mind.

Your sources list looks OK, except that I'd have (at least temporarily) excluded the backports. 

You could still run some of the apt-get statements i suggested, but at -s in each of them (for simulation, just see what would happen) because actually removing packages might remove somthing your current phpmyadmin is using

---

### Post by dargaud on 2011-10-28
Thanks for the advice. After using the simulation I did remove libgd2-noxpm, which installed libgd2-xpm all by itself, and now I can install phpmyadmin (although I won't since I have it from source).

Thanks.

---

### Post by yanaek on 2011-12-13
same problem here

to solve it: apt-get has to be used instead of aptitude
aptitude gets lost in dependencies and wants to remove too much, apt-get just does the job

---

### Post by dargaud on 2011-12-20
> **yanaek said:**
> to solve it: apt-get has to be used instead of aptitude

Thanks for your simple solution that solved it. I use aptitude by habit but also for the 'search' capability which AFAIK is no present in apt-get.

---

