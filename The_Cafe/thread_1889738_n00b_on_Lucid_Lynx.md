---
title: "n00b on Lucid Lynx"
date: 2011-12-01
forum: The Cafe
---

### Post by citizenmilton on 2011-12-01
I'm trying to learn Ubuntu starting w/ the book "Ubuntu for Non-Geeks." It's well-written, takes things very slowly. Perhaps a bit too slow.

I'm not quite halfway though, but, I have some questions for the experienced Ubuntu users out there.

I'm experiencing a noticeable amount of flaky behavior. Some things aren't working as expected (deja dup won't install, gnome-art fonts keep reverting to this one font instead of the new one i install, etc.). It's not overwhelming, but, it's getting in the way of following the examples to the fullest. 

Are these types of things more likely to be:

1. personal hardware issues
2. stuff just not being fully supported in 10.04 anymore
3. ???

I'm wondering if I should ditch Lucid Lynx, get current, and see if that makes things smoother?

Or, is this just how it is out here in the wild world of ubuntu - don't expect everything to go smoothly and just adapt.

thanks!

---

### Post by beew on 2011-12-01
> **citizenmilton said:**
> 

I'm wondering if I should ditch Lucid Lynx, get current, and see if that makes things smoother?

Or, is this just how it is out here in the wild world of ubuntu - don't expect everything to go smoothly and just adapt.

thanks!
It depends of what you mean by "get current".  If your hardware is not too old, I would recommend 11.04, or even 10.10. But 11.10 is very unstable at the moment, I would give it at least another month before I will look at it again. New releases are always buggy because Canonical has the tendency to rush before it is ready just to  meet the release schedule, and 11.10 and 11.04 has been particularly so and it takes longer to stabilize because of the drastic changes under the hood. 11.04 is quite stable now after more than 6 months but in my experience 11.10 is still horrible, some of that may have to do with my set up, but others are well known bugs and some software has not been ported to 11.10 yet. 

I understand others may say 11.10 is great, I am just giving my opinion based on my own experience.

---

### Post by staf0048 on 2011-12-01
Funny, I ready that book too!  Though it was a much different version...


Anyway,

None of the things you mentioned should really be an issue.  

How is the book asking you to install deja dup and how do you know it didn't install?
After you've installed a new font, how are you telling the computer to use the new font?

Your answers to these questions might give us a better understanding of your troubles.

Good luck and stick with it!

---

### Post by BBQdave on 2011-12-02
> **citizenmilton said:**
> I'm wondering if I should ditch Lucid Lynx, get current, and see if that makes things smoother?

*Short answer*: Get current.

*Expanded answer*: newer hardware - try Ubuntu, older hardware - try Xubuntu.

*Super answer*: If you like Gnome 2 (desktop environment of Lucid Lynx) then get and install **Debian 6** :)

**Debian**, a little more to learn, but well worth it down the road with whatever distro you chose to use :tongue:

[http://www.debian.org/](http://www.debian.org/)

---

### Post by mastablasta on 2011-12-02
yah only plenty things there don't work out of the box (tried live and half of the stuff on notebook didn't work). however Chrunchbang made some improvements on it (debian 6 stable). it's easy to install. though now they switched purely to Openbox which is a shame as their XFCE was nice. consumes 80 MB ram if Conky is to be trusted.

---

### Post by lolpenguin on 2011-12-02
Lucid Lynx is the current LTS version, which means it is very stable. Oneiric Ocelot is the current stable release. Having a newer release does not mean that your computer will run more smoothly.

---

### Post by beew on 2011-12-02
> **lolpenguin said:**
> Lucid Lynx is the current LTS version, which means it is very stable.
Also very old.
> 
 Oneiric Ocelot is the current stable release. .That is false advertisment (on Canonical's part) It is certainly the newest supported version but it is anything but stable.

> Having a newer release does not mean that your computer will run more smoothly
Usually it does, if the newer release is not too new (with the exceptions with some major hardware incompatibility, but assuming most things work and only concerning performance). I get the best result by installing  3 -6 months after release date. Since I use ppa to keep my sofware up to date I usually keep my OS for 1 year, thereby skipping a release. Currently I think 11.04 gets the best of all worlds. 10.10 would be next but it expires in April.

---

### Post by citizenmilton on 2011-12-02
Thanks to everyone for helping out. I'll see if sticking w/ Lucid & debugging individually works.

> **staf0048 said:**
> 
How is the book asking you to install deja dup and how do you know it didn't install?

I've tried through adding the PPA for deja dup into the 'other sources' section of the Ubuntu Software Center. this is the URL I've added:

[http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu)

& it shows up in the left-hand column of the Ubuntu Software Center menu.

When I first started trying to install, it would get to about 3% progress and just crap out without any sort of error message.

I tried other methods.

I also added the PPA URLs for karmic & maverick, not realizing what I was doing yet. that might've caused some conflicts.

Now, when I try to install through the GUI in the Ubuntu Software Center, I get this error:

                     > This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.Thanks again.

---

### Post by Old_Grey_Wolf on 2011-12-02
> **citizenmilton said:**
> I'm experiencing a noticeable amount of flaky behavior. Some things aren't working as expected (deja dup won't install, gnome-art fonts keep reverting to this one font instead of the new one i install, etc.). It's not overwhelming, but, it's getting in the way of following the examples to the fullest.

People on this forum are willing to help. For example, if you get an error when trying to install software, like Deja-Dup, post the error and ask for help. Upgrading to a newer version of Ubuntu; such as, 11.10 may be more confusing because the GUI is different from what is in the book you are using.

---

### Post by Old_Grey_Wolf on 2011-12-02
> **citizenmilton said:**
> 
I've tried through adding the PPA for deja dup into the 'other sources' section of the Ubuntu Software Center.
You didn't need to add the PPA. Deja-Dup should have already been in the Lucid repository.

> I also added the PPA URLs for karmic & maverick, not realizing what I was doing yet. that might've caused some conflicts.
Don't use repositories from other releases. Only use the Lucid repository.

> Now, when I try to install through the GUI in the Ubuntu Software Center, I get this error:

Post the output from entering this command in the terminal ```
sudo apt-get update
``` it may also help if you post the output of ```
cat /etc/apt/sources.list
```

---

### Post by citizenmilton on 2011-12-02
Thanks wolf!

Note: before I followed your instructions here, I went into software sources and unchecked, but did not remove, those maverick and karmic sources. Maybe that's my current problem? Starting by removing them? But, remember I was also having problems installing it before I added those goof ups.
  > 
**milton@Ubuntu-Dell:~$ sudo apt-get update**

Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release.gpg
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb/apps Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                               
Ign [http://ppa.launchpad.net/4dtris-dev/all-releases/ubuntu/](http://ppa.launchpad.net/4dtris-dev/all-releases/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu/](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources           
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Packages
Reading package lists... Done
> 
**milton@Ubuntu-Dell:~$ cat /etc/apt/sources.list **
 # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 
  
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security multiverse 
 deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps 
 # deb [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu) karmic main 
 # deb-src [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu) karmic main 
 # deb [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu) maverick main 
 # deb-src [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu) maverick main 
 milton@Ubuntu-Dell:~$  


---

### Post by staf0048 on 2011-12-02
> **citizenmilton said:**
> I also added the PPA URLs for karmic & maverick, not realizing what I was doing yet. that might've caused some conflicts.


Well, this could be the cuase of all your trouble.  The different versions almost never play nicely together.  Go back into the sources section and remove all the stuff the book asked you to add.

Deja dup is already in the repositories (sorry of the jargon), so you should not need to add a different software source - as far as I know anyway.  Once you remove the software sources the book told you to add you'll need to do some clean up work to get back to normal.  The only way I know how to do this is with the command line - if anyone else knows of a better (or gui) way, please chime in.  Don't be scared though, it's not as bad as you might think and you can just copy and paste my commands into the terminal.

1st you'll need to fire up a terminal.  On lucid you can simply go to: Applications/Accessories/Terminal.


Once there, do this: (note: copy/paste each box individually into the terminal)

```
sudo apt-get purge deja-dup
```  Note: this first command may or may not do anything since it was probably never installed in the first place

```
sudo apt-get update
```  This makes sure your software repository list is up to date

```
sudo apt-get upgrade
```  This will update any old packages you might have left on your computer

```
sudo apt-get autoremove
```  This will clean up any orphaned packages left on your computer after the upgrade.

Ok, so now you *should* have a clean computer that's back to the Lucid state

From here you can go back to the software center and see if Deja Dup is there, or if you're getting the hange of the terminal now you can simply do this:

```
sudo apt-get install deja-dup
```

With any luck this will work for you.  If not, don't be afraid to come back for more!  :-)

---

### Post by Old_Grey_Wolf on 2011-12-02
I din't see the post by staf0048. Try that first. If you still have a problem try this:

Use the command ```
gksudo gedit /etc/apt/sources.list
``` then remove the line (fifth from the bottom) that has ```
deb http://archive.getdeb.net/ubuntu oneiric-getdeb apps
``` then run the commands ```
sudo apt-get update
``````
sudo apt-get upgrade
```. Post any errors you get.

---

### Post by citizenmilton on 2011-12-02
Thanks staf0048 + old gray wolf -- that's solved the problem. 

The application is now installed and runs. 

thanks again!

(of course, now I'll need to go back + re-read that section of the tutorial and try to install something else using the method it was trying to teach. all in good fun.:))

---

### Post by Old_Grey_Wolf on 2011-12-02
citizenmilton,

When/If you have more problems, the Ubuntu forum has been a friendly place to ask for help.

---

