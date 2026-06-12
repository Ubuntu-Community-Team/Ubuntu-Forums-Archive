---
title: "LibreOffice 3.5.0 b2 fails to install"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-12
Right now in Launchpad there is a new beta2 version of LibreOffice 3.5.0.
Here:
[https://launchpad.net/ubuntu/precise/+source/libreoffice/1:3.5.0~beta2-2ubuntu2]("https://launchpad.net/ubuntu/precise/+source/libreoffice/1:3.5.0%7Ebeta2-2ubuntu2")

I tried to install it with dpkg, but that failed.
Package libreoffice-core will not install.
It warns about not being able to delete '/usr/lib/libreoffice/basis3.4/program/'
It claims there is no such file or directory, even though there definitely is.
Then preinstallation script fails and libreoffice-core is thus not installed.

This happens with a 64-bit setup.

Does anyone else see this?

---

### Post by mswift on 2012-01-12
Yes, had the same problem with a 64-bit setup.
However, manually creating the folder solved the problem for me.

```
sudo mkdir /usr/lib/libreoffice/basis3.4/program/
```

after that, upgrade with ```
sudo apt-get -f install
```

---

### Post by zika on 2012-01-12
Are we being (softly) persuaded to use icedtea:
```
:~$ sudo aptitude dist-upgrade 
[sudo] password for zika: 
The following NEW packages will be installed:
  ca-certificates-java{a} default-jre{a} default-jre-headless{a} fonts-opensymbol{a} icedtea-6-jre-cacao{a} icedtea-6-jre-jamvm{a} icedtea-netx{a} icedtea-netx-common{a} java-common{a} 
  libaccess-bridge-java{a} libaccess-bridge-java-jni{a} libebook-1.2-12{ab} libecal-1.2-10{ab} libedataserver-1.2-15{ab} libreoffice-filter-binfilter{a} libreoffice-java-common{a} 
  libreoffice-style-tango{a} libxerces2-java{a} libxml-commons-external-java{a} libxml-commons-resolver1.1-java{a} openjdk-6-jre{a} openjdk-6-jre-headless{a} openjdk-6-jre-lib{a} 
  ttf-dejavu-extra{a} 
The following packages will be upgraded:
  evolution-data-server evolution-data-server-common libcamel-1.2-29 libebackend-1.2-1 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserverui-3.0-1 libreoffice-base-core 
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-writer 
  python-uno ttf-opensymbol 
20 packages upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
Need to get 141 MB of archives. After unpacking 141 MB will be used.
The following packages have unmet dependencies:
  libedataserver-1.2-15: Breaks: libedataserver1.2-15 but 3.2.2-0ubuntu2 is installed.
  libebook-1.2-12: Breaks: libebook1.2-12 but 3.2.2-0ubuntu2 is installed.
  libecal-1.2-10: Breaks: libecal1.2-10 but 3.2.2-0ubuntu2 is installed.
  libreoffice-l10n-en-gb: Depends: libreoffice-common (< 1:3.5~) but 1:3.5.0~beta2-2ubuntu2 is to be installed. or
                                   language-support-translations-en which is a virtual package.
  libreoffice-l10n-en-za: Depends: libreoffice-common (< 1:3.5~) but 1:3.5.0~beta2-2ubuntu2 is to be installed. or
                                   language-support-translations-en which is a virtual package.
The following actions will resolve these dependencies:

      Remove the following packages:                       
1)      empathy                                            
2)      evolution                                          
3)      evolution-data-server                              
4)      evolution-exchange                                 
5)      evolution-indicator                                
6)      evolution-plugins                                  
7)      gnome-applets                                      
8)      gnome-contacts                                     
9)      gnome-panel                                        
10)     gnome-session-fallback                             
11)     gnome-shell                                        
12)     indicator-datetime                                 
13)     libcamel-1.2-29                                    
14)     libebackend-1.2-1                                  
15)     libebook1.2-12                                     
16)     libecal1.2-10                                      
17)     libedata-book-1.2-11                               
18)     libedata-cal-1.2-13                                
19)     libedataserverui-3.0-1                             
20)     libevolution                                       
21)     libfolks-eds25                                     
22)     libreoffice-help-en-gb                             
23)     libreoffice-l10n-en-gb                             
24)     libreoffice-l10n-en-za                             
25)     thunderbird-gnome-support                          
26)     ubuntuone-client-gnome                             

      Keep the following packages at their current version:
27)     libebook-1.2-12 [Not Installed]                    
28)     libecal-1.2-10 [Not Installed]                     
29)     libedataserver-1.2-15 [Not Installed]              

      Leave the following dependencies unresolved:         
30)     evolution-common recommends evolution              
31)     libfolks25 recommends libfolks-eds25               
32)     ubuntu-desktop recommends empathy                  
33)     ubuntu-desktop recommends thunderbird-gnome-support
34)     ubuntu-desktop recommends ubuntuone-client-gnome   
35)     alacarte recommends gnome-panel                    
36)     gnome-contacts recommends libfolks-eds25           
37)     gnome-panel-data recommends gnome-panel            
38)     gnome-shell recommends gnome-session-fallback      
39)     gnome-shell recommends gnome-contacts              
40)     unity-2d-panel recommends indicator-datetime       
41)     unity recommends indicator-datetime                


Accept this solution? [Y/n/q/?]q 
```

---

### Post by Harry33 on 2012-01-12
> **zika said:**
> Are we being (softly) persuaded to use icedtea:
```
:~$ sudo aptitude dist-upgrade 
[sudo] password for zika: 
The following NEW packages will be installed:
  ca-certificates-java{a} default-jre{a} default-jre-headless{a} fonts-opensymbol{a} icedtea-6-jre-cacao{a} icedtea-6-jre-jamvm{a} icedtea-netx{a} icedtea-netx-common{a} java-common{a} 
  libaccess-bridge-java{a} libaccess-bridge-java-jni{a} libebook-1.2-12{ab} libecal-1.2-10{ab} libedataserver-1.2-15{ab} libreoffice-filter-binfilter{a} libreoffice-java-common{a} 
  libreoffice-style-tango{a} libxerces2-java{a} libxml-commons-external-java{a} libxml-commons-resolver1.1-java{a} openjdk-6-jre{a} openjdk-6-jre-headless{a} openjdk-6-jre-lib{a} 
  ttf-dejavu-extra{a} 
The following packages will be upgraded:
  evolution-data-server evolution-data-server-common libcamel-1.2-29 libebackend-1.2-1 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserverui-3.0-1 libreoffice-base-core 
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-writer 
  python-uno ttf-opensymbol 
20 packages upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
Need to get 141 MB of archives. After unpacking 141 MB will be used.
The following packages have unmet dependencies:
  libedataserver-1.2-15: Breaks: libedataserver1.2-15 but 3.2.2-0ubuntu2 is installed.
  libebook-1.2-12: Breaks: libebook1.2-12 but 3.2.2-0ubuntu2 is installed.
  libecal-1.2-10: Breaks: libecal1.2-10 but 3.2.2-0ubuntu2 is installed.
  libreoffice-l10n-en-gb: Depends: libreoffice-common (< 1:3.5~) but 1:3.5.0~beta2-2ubuntu2 is to be installed. or
                                   language-support-translations-en which is a virtual package.
  libreoffice-l10n-en-za: Depends: libreoffice-common (< 1:3.5~) but 1:3.5.0~beta2-2ubuntu2 is to be installed. or
                                   language-support-translations-en which is a virtual package.
The following actions will resolve these dependencies:

      Remove the following packages:                       
1)      empathy                                            
2)      evolution                                          
3)      evolution-data-server                              
4)      evolution-exchange                                 
5)      evolution-indicator                                
6)      evolution-plugins                                  
7)      gnome-applets                                      
8)      gnome-contacts                                     
9)      gnome-panel                                        
10)     gnome-session-fallback                             
11)     gnome-shell                                        
12)     indicator-datetime                                 
13)     libcamel-1.2-29                                    
14)     libebackend-1.2-1                                  
15)     libebook1.2-12                                     
16)     libecal1.2-10                                      
17)     libedata-book-1.2-11                               
18)     libedata-cal-1.2-13                                
19)     libedataserverui-3.0-1                             
20)     libevolution                                       
21)     libfolks-eds25                                     
22)     libreoffice-help-en-gb                             
23)     libreoffice-l10n-en-gb                             
24)     libreoffice-l10n-en-za                             
25)     thunderbird-gnome-support                          
26)     ubuntuone-client-gnome                             

      Keep the following packages at their current version:
27)     libebook-1.2-12 [Not Installed]                    
28)     libecal-1.2-10 [Not Installed]                     
29)     libedataserver-1.2-15 [Not Installed]              

      Leave the following dependencies unresolved:         
30)     evolution-common recommends evolution              
31)     libfolks25 recommends libfolks-eds25               
32)     ubuntu-desktop recommends empathy                  
33)     ubuntu-desktop recommends thunderbird-gnome-support
34)     ubuntu-desktop recommends ubuntuone-client-gnome   
35)     alacarte recommends gnome-panel                    
36)     gnome-contacts recommends libfolks-eds25           
37)     gnome-panel-data recommends gnome-panel            
38)     gnome-shell recommends gnome-session-fallback      
39)     gnome-shell recommends gnome-contacts              
40)     unity-2d-panel recommends indicator-datetime       
41)     unity recommends indicator-datetime                


Accept this solution? [Y/n/q/?]q 
```


Seems to be the case.
BTW. I made another thread about the evolution-data-server issue. It will remove gnome-panel and gnome-shell, because these depend on the old libebook, libecal and libedataserver packages.

See more of it here:
[http://ubuntuforums.org/showthread.php?t=1907813](http://ubuntuforums.org/showthread.php?t=1907813)

---

### Post by Harry33 on 2012-01-12
> **mswift said:**
> Yes, had the same problem with a 64-bit setup.
However, manually creating the folder solved the problem for me.

```
sudo mkdir /usr/lib/libreoffice/basis3.4/program/
```after that, upgrade with ```
sudo apt-get -f install
```

Well, like I wrote, I do have that directory (I cannot double create it), because I have libreoffice 3.4.4 installed.

I haven't tried installation (3.5.0 b2) by purging old libreoffice (3.4.4) first, though.

---

### Post by zika on 2012-01-12
> **Harry33 said:**
> Seems to be the case.
BTW. I made another thread about the evolution-data-server issue. It will remove gnome-panel and gnome-shell, because these depend on the old libebook, libecal and libedataserver packages.

See more of it here:
[http://ubuntuforums.org/showthread.php?t=1907813](http://ubuntuforums.org/showthread.php?t=1907813)
I'll fight 'till I can. I'm used to my (simple) method of obtaining Java preview and...
No, I'm not writing about „evolution-issue“, I was lazy enough not to clean-out evolution from my quote...

---

### Post by Harry33 on 2012-01-12
There are a number of bug reports in Launchpad now.
Like this one (#915271):
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915271](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915271)

---

### Post by dino99 on 2012-01-12
have made mine too (before seeing that one :()

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915332](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915332)

---

### Post by Harry33 on 2012-01-12
OK, purging previous LibreOffice made it possible to install this 3.5.0 b2 version.
Still, this is an issue worth reporting a bug.

---

### Post by ventrical on 2012-01-12
> **Harry33 said:**
> OK, purging previous LibreOffice made it possible to install this 3.5.0 b2 version.
Still, this is an issue worth reporting a bug.


Whats the sudo code for that harry33??

thanks

 I think i got the same problem..

---

### Post by ventrical on 2012-01-12
got it..

peace..

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915466](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915466)

---

### Post by antoniomiguel on 2012-01-12
> **mswift said:**
> Yes, had the same problem with a 64-bit setup.
However, manually creating the folder solved the problem for me.

```
sudo mkdir /usr/lib/libreoffice/basis3.4/program/
```after that, upgrade with ```
sudo apt-get -f install
```

This worked on me too! Thanks

---

### Post by teh603 on 2012-01-12
> **Harry33 said:**
> OK, purging previous LibreOffice made it possible to install this 3.5.0 b2 version.
Still, this is an issue worth reporting a bug.Y'know, my install of LibreOffice was so borked that when I rebooted to solve a few issues, it killed networking and several other important services. Couldn't purge LibreOffice either, and the recomended code to fix the broken packages wouldn't work either. I finally had to just reinstall the Ocelot.

---

### Post by Jim_in_Omaha on 2012-01-12
> **mswift said:**
> Yes, had the same problem with a 64-bit setup.
However, manually creating the folder solved the problem for me.

```
sudo mkdir /usr/lib/libreoffice/basis3.4/program/
```

after that, upgrade with ```
sudo apt-get -f install
```

Seems to have done the trick.. 

Thanks

---

### Post by ventrical on 2012-01-13
> **teh603 said:**
> Y'know, my install of LibreOffice was so borked that when I rebooted to solve a few issues, it killed networking and several other important services. Couldn't purge LibreOffice either, and the recomended code to fix the broken packages wouldn't work either. I finally had to just reinstall the Ocelot.

  Mine too was borked but it was a slightly different issue. I basically went to the LibreOffice website and downloaded the stables from there and re-installed them. It was a tedious job removing and then manually re-installing - but fresh installs are  a unique thing with Ubuntu and if you have a fast system and do not pay usage then a fresh install would be much more efficient.

  With todays high speed pCs it could take less than a half an hour to install and update a fresh install as compared to  analyzing and tracking down a bug and then performing a workaround which might take the average noob a couple of hours.

---

### Post by zika on 2012-01-13
> **Jim_in_Omaha said:**
> Seems to have done the trick.. 

ThanksI do have that folder. Removing it (manually) did not help...
```
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-core
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
11 not fully installed or removed.
Need to get 38.6 MB of archives.
After this operation, 5,895 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main libreoffice-core amd64 1:3.5.0~beta2-2ubuntu2 [38.6 MB]
Fetched 38.6 MB in 58s (658 kB/s)                                               
(Reading database ... 290076 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_amd64.deb) ...
rmdir: failed to remove [COLOR="Red"]`usr/lib/libreoffice/basis3.4/program/'[/COLOR]: Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Am I wrong or leading &#8222;/&#8220; is missing...```
usr/lib/libreoffice/basis3.4/program/
```


Update: I've made it. I've moved program>program-old. Made new program. Then it worked...

---

### Post by jbicha on 2012-01-13
[Fixed]("https://launchpad.net/ubuntu/+source/libreoffice/1:3.5.0%7Ebeta2-2ubuntu3") libreoffice is building now. Expect it to show up in your updates when it finishes later today!

---

### Post by zika on 2012-01-13
> **jbicha said:**
> [Fixed]("https://launchpad.net/ubuntu/+source/libreoffice/1:3.5.0%7Ebeta2-2ubuntu3") libreoffice is building now. Expect it to show up in your updates when it finishes later today!Every situation like this makes us stronger and more prepared for testing next versions... ;)
Waiting for upgradeis not an viable option... ;)

---

### Post by ventrical on 2012-01-13
> **zika said:**
> I do have that folder. Removing it (manually) did not help...
```
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-core
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
11 not fully installed or removed.
Need to get 38.6 MB of archives.
After this operation, 5,895 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main libreoffice-core amd64 1:3.5.0~beta2-2ubuntu2 [38.6 MB]
Fetched 38.6 MB in 58s (658 kB/s)                                               
(Reading database ... 290076 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_amd64.deb) ...
rmdir: failed to remove [COLOR=Red]`usr/lib/libreoffice/basis3.4/program/'[/COLOR]: Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Am I wrong or leading „/“ is missing...```
usr/lib/libreoffice/basis3.4/program/
```
Update: I've made it. I've moved program>program-old. Made new program. Then it worked...

this is where I get stuck. how do I   move program to program old and make new program directory?

I got 11 installs and this is # 2  that is just about fubared.

---

### Post by ventrical on 2012-01-13
> **jbicha said:**
> [Fixed]("https://launchpad.net/ubuntu/+source/libreoffice/1:3.5.0%7Ebeta2-2ubuntu3") libreoffice is building now. Expect it to show up in your updates when it finishes later today!


this one has been a real migrane ya know .. but thanks anyways..  :)

---

### Post by shuttleworthwannabe on 2012-01-13
Can someone be so kind and give (the really slow learner) a step by step command line to get this right; without this problems fixed i can't install any other app; keep giving me this error in terminal.

Much appreciated,
SwB

---

### Post by terry_gardener on 2012-01-13
the original command didn't work for me either. neither did purging the libreoffice install and then installing it again. 

the way i got it to work which was based on the command was navigate to 

/usr/lib/ with cd command 

and then navigate to the libreoffice folder (if missing create using sudo mkdir libreoffice) 

then navigate to the basis3.4 folder (create if needed) 

and then navigate to program folder (create if needed) 

then you should be able to install the libreoffice-core package. 

sudo apt-get install -f

and it worked. it didn't work the first time as i was missing the basis3.4 folder and had to create it then program folder.

---

### Post by ventrical on 2012-01-13
> **terry_gardener said:**
> the original command didn't work for me either. neither did purging the libreoffice install and then installing it again. 

the way i got it to work which was based on the command was navigate to 

/usr/lib/ with cd command 

and then navigate to the libreoffice folder (if missing create using sudo mkdir libreoffice) 

then navigate to the basis3.4 folder (create if needed) 

and then navigate to program folder (create if needed) 

then you should be able to install the libreoffice-core package. 

sudo apt-get install -f

and it worked. it didn't work the first time as i was missing the basis3.4 folder and had to create it then program folder.

did not work ...

---

### Post by terry_gardener on 2012-01-13
the new version of libreoffice are in the repos so should now let you install update

i'm using the main server for repos

---

### Post by ventrical on 2012-01-13
> **terry_gardener said:**
> the new version of libreoffice are in the repos so should now let you install update

i'm using the main server for repos

even switch to main server...

not a chance...

---

### Post by zika on 2012-01-13
> **ventrical said:**
> this is where I get stuck. how do I   move program to program old and make new program directory?

I got 11 installs and this is # 2  that is just about fubared.Either in CLI (Terminal) or in GUI (Nautilus, or whatever).
But, it is not important anymore, new version is doing that for You...

---

### Post by Harry33 on 2012-01-13
> **terry_gardener said:**
> the new version of libreoffice are in the repos so should now let you install update

i'm using the main server for repos

The common packages (*_all.deb) and 32-bit packages are not yet uploaded into repos.
Just wait for an hour or so.

I installed them manually with dpkg. Worked fine here.

---

### Post by ventrical on 2012-01-13
> **zika said:**
> Either in CLI (Terminal) or in GUI (Nautilus, or whatever).
But, it is not important anymore, new version is doing that for You...

Thanks zika for your help. I guess what I meant to say is that I  just do not know some of the sudo commands (or terminal commands) to do some of the things you suggested. And even following some of the suggestions in launchpad and from dino99 and others .. just no way.. So what I did on one install was purge out libreoffice completely and then went to the libreoffice website and downloaded the debian version and it worked just great .. that is until I updated and it is that same old &$^%#! file that wants to play the fly in the ointment for the day!

 Of course, as you say ( and harry33) the fix is on the way :)

---

### Post by ventrical on 2012-01-13
Now what .. ??  Does it got to get worse before it gets better ? :)

---

### Post by kuvanito on 2012-01-13
it's already worse...i sudo my updates and -f so i am skrewed as of now,system borked.... :(
i am gonna stop playing with pangolin until it is released
in the mean time i will stick with oneiric

---

### Post by Basher101 on 2012-01-13
haha at least it said your Signature is good :D :D

---

### Post by MG&amp;TL on 2012-01-13
Have had an error like this in 11.10 testing, couldn't remember what caused it. I think it was me chopping the internet while adding a PPA, but that's just a hunch.

It's never good when the error message ends with "?!"...

---

### Post by ventrical on 2012-01-13
> **kuvanito said:**
> it's already worse...i sudo my updates and -f so i am skrewed as of now,system borked.... :(
i am gonna stop playing with pangolin until it is released
in the mean time i will stick with oneiric


   I think I have a remote attacker ATM ...  oh joy :) 

hehehe

 firefox just crashed like a looney .. I think it is breakage time !! :)

---

### Post by cctsim on 2012-01-13
I had to do the following:

cd /var/cache/apt/archives/

sudo mkdir -p usr/lib/libreoffice/basis3.4/program

sudo apt-get install -f

Now it works fine but some packages are still from 3.4.4 version, e.g.

libreoffice-l10n-common
libreoffice-report-builder-bin
libreoffice-style-human

Are they going to be updated soon ?

---

### Post by PaulW2U on 2012-01-13
Just downloaded and upgraded 25 packages that have all installed correctly.

Problem fixed. :D

---

### Post by ronacc on 2012-01-13
I just got the same thing but with different apps for me it was mplayer and screenlets that couldn't be authenticated .

---

### Post by ventrical on 2012-01-13
Thanks ronacc for chiming in...

---

### Post by kuvanito on 2012-01-13
i spoke too soon
in the last minute after doing my sudos all works perfectoooooo
sudo apt-get update
sudo apt-get upgrade 
sudo apt-get dist-upgrade

now since i am little stubborn i always do my -f
sudo apt-get update
sudo apt-get upgrade -f
sudo apt-get dist-upgrade -f

i feel like little chicken,sorry guys,ALL IS FINE!!!
Keep Rocking Pangolin!!! :)

---

### Post by ventrical on 2012-01-13
> **MG&TL said:**
> Have had an error like this in 11.10 testing, couldn't remember what caused it. I think it was me chopping the internet while adding a PPA, but that's just a hunch.

It's never good when the error message ends with "?!"...

 No ppas here ATM... just raw Precise.. I did  try to remove some files from the /program/ directory .. but I do not think it would have anything to do with this activity.

---

### Post by ventrical on 2012-01-13
I'm shocked .. just unbelievable. I went here and did these commands:

[http://ubuntuforums.org/archive/index.php/t-1511379.html](http://ubuntuforums.org/archive/index.php/t-1511379.html)

to try and get my keys back. It told me that it was already installed.

Then I went:

sudo apt-get -f install

 and a bunch of updates with libreoffice FINALLY installed  but the real shocker was that when the Unity Screen booted up the launcher sidebar rendered itself like a stroke of blue lightning (sort of like a visual effects rendering) and then BOOM .. I am in Unity 3D on a blacklisted  Intel  video adapter card- just baffling ...  this is better than any video game I ever played ! :)
** Just noting that I could not get Unity 3D to work because this adpater card does not support compiz - but it looks like somthing happened and it may do so now... either that or compiz is now working in Unity 2D. I kid you not !

EDIT:

 Ok.. it appears that it was only a one time phenomenon .. and Precise is acting pretty unstable right now .. but I think it will settle down..

---

### Post by Basher101 on 2012-01-13
wow o.O you broke your system so much that...it now works.

i guess fighting fire with fire is not such a bad idea after all :popcorn:

---

### Post by TheNessus on 2012-01-13
ok, so after some update a few days ago, apt-get is dead.

I get this:


```
the-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-calc : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-common : Breaks: libreoffice-core (< 1:3.5~) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-filter-binfilter : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 python-uno : Depends: libreoffice-core (= 1:3.5.0~beta2-2ubuntu2) but 1:3.4.4-0ubuntu2 is installed
 usb-creator-gtk : Depends: gir1.2-unity-5.0 but it is not installed
E: Unmet dependencies. Try using -f.
```


I tried it with --fix-broken, tried all the other options in apt-get, nothing works. example, with fix-broken i get this:


```
the-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  gir1.2-unity-4.0
The following NEW packages will be installed:
  gir1.2-unity-5.0
The following packages have been kept back:
  unity unity-common unity-services
The following packages will be upgraded:
  alsa-utils apparmor apport bamfdaemon brasero brasero-cdrkit brasero-common
  command-not-found command-not-found-data deja-dup empathy empathy-common
  evince evince-common evolution-data-server evolution-data-server-common
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  gir1.2-totem-1.0 gnome-control-center gnome-control-center-data gnome-media
  gnome-settings-daemon libbamf0 libbamf3-0 libbrasero-media3-1
  libcamel-1.2-29 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10
  libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15
  libedataserverui-3.0-1 libevince3-3 libgnome-control-center1 libjpeg-turbo8
  libnautilus-extension1a libqtbamf1 libqtdee2 libreoffice-core libtotem0
  libutouch-geis1 nautilus nautilus-data nautilus-sendto-empathy nux-tools
  python-apport python-problem-report telepathy-indicator totem totem-common
  totem-mozilla totem-plugins unity-lens-applications unity-lens-files
  unity-lens-music unity-scope-musicstores update-manager update-manager-core
62 upgraded, 1 newly installed, 1 to remove and 3 not upgraded.
13 not fully installed or removed.
Need to get 0 B/72.5 MB of archives.
After this operation, 2,699 kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 241403 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb) ...
rmdir: failed to remove `usr/lib/libreoffice/basis3.4/program/': Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb

```

Messing with Synaptics obviously didn't work as well. I changed servers from which synaptics downloads, no help there too.

Also possibly related is this bug:

[B]Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit timed out
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

```

the-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gir1.2-unity-4.0 unity
The following NEW packages will be installed:
  gir1.2-unity-5.0 libnux-2.0-0 libnux-2.0-common
The following packages have been kept back:
  unity-services
The following packages will be upgraded:
  alsa-utils apparmor apport bamfdaemon brasero brasero-cdrkit brasero-common
  command-not-found command-not-found-data deja-dup empathy empathy-common
  evince evince-common evolution-data-server evolution-data-server-common
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  gir1.2-totem-1.0 gnome-control-center gnome-control-center-data gnome-media
  gnome-settings-daemon libbamf0 libbamf3-0 libbrasero-media3-1
  libcamel-1.2-29 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10
  libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15
  libedataserverui-3.0-1 libevince3-3 libgnome-control-center1 libjpeg-turbo8
  libnautilus-extension1a libqtbamf1 libqtdee2 libreoffice-core libtotem0
  libutouch-geis1 nautilus nautilus-data nautilus-sendto-empathy nux-tools
  python-apport python-problem-report telepathy-indicator totem totem-common
  totem-mozilla totem-plugins unity-common unity-lens-applications
  unity-lens-files unity-lens-music unity-scope-musicstores update-manager
  update-manager-core
63 upgraded, 3 newly installed, 2 to remove and 1 not upgraded.
13 not fully installed or removed.
Need to get 0 B/73.5 MB of archives.
After this operation, 2,116 kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 241403 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb) ...
rmdir: failed to remove `usr/lib/libreoffice/basis3.4/program/': Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb
^[[A^[[A^[[B^[[B^[[B^[[B^[[B

Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit timed out
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by grahammechanical on 2012-01-13
I had problems with the repositories since just after midnight (UK time) 13th . I tried to install Unity 5 through synaptic and it wanted to remove ubuntu-desktop. I tried again pm (UK time) and synaptic was willing to install the updates without removing ubuntu-decktop and in the process udated Libreoffice but failed to update lireoffice-core.

So, a broken Libreoffice that software Centre had difficulty removing and re-installing because of broken dependences. It did not even have the Libreoffice suite to offer. Just the individual modules of Libreoffice. The cache and repository list would not update.

I waited a few more hours and I was able to use synaptic to fix the broken packages and install Libreoffice but it is version 3.5.0beta2. Who asked for that! Worse of all it looks like something borrowed from Windows 98!

Apparently Libreoffice cannot find the git binary and wants to know if git is installed and in the PATH. It (git) is now installed and I am trying not to put the cockney meaning to the word git.

So, something funny has been going on. I am about to uninstall Libreoffice and try to install it again but at least Unity 5 is there and if I have a bit of time I will run the Unity Test application.

I am surprised that some of you are just experiencing this problem. Still if we cannot take a joke we shouldn't have joined.

Regards.

Update: software Centre is offering Libreoffice 3.5.0beta2. It seems that testing Precise also means that we now also get to test Libreoffice whether we want to or not. I am about to install and I hope there is a better looking design.

---

### Post by t1497f35 on 2012-01-13
"sudo apt-get -f install" worked for me, note, "install" not "upgrade".

---

### Post by TheNessus on 2012-01-13
> **t1497f35 said:**
> "sudo apt-get -f install" worked for me, note, "install" not "upgrade".

no luck here either:

```
the-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gir1.2-unity-5.0 libreoffice-core
The following packages will be REMOVED:
  gir1.2-unity-4.0
The following NEW packages will be installed:
  gir1.2-unity-5.0
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 1 newly installed, 1 to remove and 64 not upgraded.
13 not fully installed or removed.
Need to get 0 B/37.3 MB of archives.
After this operation, 2,541 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 241403 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb) ...
rmdir: failed to remove `usr/lib/libreoffice/basis3.4/program/': Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb
Error org.freedesktop.DBus.Error.TimedOut: Activatthe-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gir1.2-unity-5.0 libreoffice-core
The following packages will be REMOVED:
  gir1.2-unity-4.0
The following NEW packages will be installed:
  gir1.2-unity-5.0
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 1 newly installed, 1 to remove and 64 not upgraded.
13 not fully installed or removed.
Need to get 0 B/37.3 MB of archives.
After this operation, 2,541 kB disk space will be freed.
Do you want to continue [Y/n]? &#1496;
Abort.
the-nessus@thenessus-Inspiron-N3010:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gir1.2-unity-5.0 libreoffice-core
The following packages will be REMOVED:
  gir1.2-unity-4.0
The following NEW packages will be installed:
  gir1.2-unity-5.0
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 1 newly installed, 1 to remove and 64 not upgraded.
13 not fully installed or removed.
Need to get 0 B/37.3 MB of archives.
After this operation, 2,541 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 241403 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb) ...
rmdir: failed to remove `usr/lib/libreoffice/basis3.4/program/': Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb
Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit timed out
E: Sub-process /usr/bin/dpkg returned an error code (1)
ion of org.freedesktop.PackageKit timed out
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ventrical on 2012-01-13
@thenessus


 I too think there is somthing wrong with apt-get - not just sure what it is though.

---

### Post by TheNessus on 2012-01-13
> **ventrical said:**
> @thenessus


 I too think there is somthing wrong with apt-get - not just sure what it is though.

I think it has to do with LibreOffice or with Unity 5 (I can't use Unity now either, I use shell instead. As you can see, it somehow removed unity-service from my system!

solved it by purging libreoffice with aptitude.

---

### Post by TheNessus on 2012-01-13
you need to remove libreoffice completely to resolve the apt-get failure issue which renders apt-get broken, and your whole system is therefore borked. But how can you remove libreoffice if apt-get doesn't work?  simple, use "sudo aptitude purge libreoffice". For now, at least, you can live without libre.

---

### Post by ventrical on 2012-01-13
> **TheNessus said:**
> I think it has to do with LibreOffice or with Unity 5 (I can't use Unity now either, I use shell instead. As you can see, it somehow removed unity-service from my system!


 My next question would be is 'how do we install a new apt-get if it is corrupt? Is there a workaround network fix for this?

---

### Post by ventrical on 2012-01-13
Wow .. just out of the blue it has healed itself.

ventrical@ventrical-OptiPlex-GX270:~$ sudo apt-get -f install
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnettle4 libx264-116 linux-headers-3.0.0-14 libgnutls28
  linux-headers-3.0.0-14-generic openoffice.org-common libhogweed2
  libreoffice-l10n-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
ventrical@ventrical-OptiPlex-GX270:~$

---

### Post by kansasnoob on 2012-01-13
Excuse me for being rude ............ I guess I am being rude :rolleyes:

But there is a lot of talk about libreoffice breaking things:

[http://ubuntuforums.org/showthread.php?t=1908587](http://ubuntuforums.org/showthread.php?t=1908587)

[http://ubuntuforums.org/showthread.php?t=1907806](http://ubuntuforums.org/showthread.php?t=1907806)

On top of that we have complaints about no new live daily image:

[http://ubuntuforums.org/showthread.php?t=1908421](http://ubuntuforums.org/showthread.php?t=1908421)

Do we need a new sticky regarding just what a development release is :confused:

Participation at this point is low enough that I'd think anyone would at least scan the first two pages of recent threads to see if the issue is already being discussed :)

---

### Post by ventrical on 2012-01-13
> **TheNessus said:**
> you need to remove libreoffice completely to resolve the apt-get failure issue which renders apt-get broken, and your whole system is therefore borked. But how can you remove libreoffice if apt-get doesn't work?  simple, use "ssudo aptitude purge libreoffice". For now, at least, you can live without libre.

  Thanks .. Of course that would be conditional if we had aptitude installed because it is not by default.

---

### Post by TheNessus on 2012-01-13
see here for a solution (not a fix):

[http://ubuntuforums.org/showthread.php?t=1908619](http://ubuntuforums.org/showthread.php?t=1908619)

---

### Post by TheNessus on 2012-01-13
> **ventrical said:**
> Thanks .. Of course that would be conditional if we had aptitude installed because it is not by default.

oh. well, mine is upgraded from 11.10 so I guess it's why I have aptitude.

---

### Post by jfernyhough on 2012-01-13
A merge might be handy here: [http://ubuntuforums.org/showthread.php?t=1907806&page=3](http://ubuntuforums.org/showthread.php?t=1907806&page=3)

---

### Post by cariboo on 2012-01-13
I merged 3 Libreoffice threads.

**Edit**: I merged another one, as the title was rather deceptive, saying the problem was apt-get, instead of libroffice, which is the real problem.

---

### Post by shuttleworthwannabe on 2012-01-14
Todays build fixed the problem for me. All's good here now.

---

### Post by ventrical on 2012-01-14
> **shuttleworthwannabe said:**
> Todays build fixed the problem for me. All's good here now.

 It was a nice work around. A class act indeed.

 Nice work devs !

 I only did one fresh install out of 11 installs on 8 different PCs.. so that saves me a lot of work.

---

