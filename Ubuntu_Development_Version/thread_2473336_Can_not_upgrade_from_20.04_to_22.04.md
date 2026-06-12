---
title: "Can not upgrade from 20.04 to 22.04"
date: 2022-04-01
forum: Ubuntu Development Version
---

### Post by oden99 on 2022-04-01
Now a short while before the official update to 22.04 I stried to update to the latest beta of 22.04 (now have 22.04)

Trying to following any directions will fail.

Ubuntu update complaining about that I have some PPA that is not supported.

So I turned off all PPA's in the GUI part of PPA's in the settings menu even turned of the Nvidia drivers in there..

trying to update STILL say it can not continue the update due to some unsupported PPA's that are installed.

Switching the PPA's of in the settings menu GUI don't seems to work.

If i list the PPA's manually i get:

deadsnakes-ubuntu-ppa-focal.list              
home:stevenpusser.list.distUpgrade                      
nordvpn.list.save
deadsnakes-ubuntu-ppa-focal.list.distUpgrade  
home:stevenpusser.list.save                             
stebbins-ubuntu-handbrake-releases-focal.list
deadsnakes-ubuntu-ppa-focal.list.save         
kicad-ubuntu-kicad-5_1-releases-focal.list              
stebbins-ubuntu-handbrake-releases-focal.list.distUpgrade
gezakovacs-ubuntu-ppa-focal.list              
kicad-ubuntu-kicad-5_1-releases-focal.list.distUpgrade  
stebbins-ubuntu-handbrake-releases-focal.list.save
gezakovacs-ubuntu-ppa-focal.list.distUpgrade  
kicad-ubuntu-kicad-5_1-releases-focal.list.save         
tor-project.list
gezakovacs-ubuntu-ppa-focal.list.save         
mozillateam-ubuntu-ppa-focal.list                       
tor-project.list.distUpgrade
home:FrodeSolheim:stable.list                 
mozillateam-ubuntu-ppa-focal.list.distUpgrade           
tor-project.list.save
home:FrodeSolheim:stable.list.distUpgrade     
mozillateam-ubuntu-ppa-focal.list.save                  
vscodium.list
home:FrodeSolheim:stable.list.save            
nordvpn.list                                            
vscodium.list.distUpgrade
home:stevenpusser.list                       
 nordvpn.list.distUpgrade                                
vscodium.list.save


Looks like some of the abowe stopping the update to 22.04 even that I "untick" them in the GUI.

Any suggestions on how to get through with the update ?

---

### Post by Frogs Hair on 2022-04-01
**Moved to Ubuntu Development Version**.

 22.04 is still beta and the LTS direct upgrade won't likely be available until the summer. If you need the beta version a clean installation would be the best option now.

---

### Post by oden99 on 2022-04-01
Well it should be 2weeks untiull the release and the last beta are out..so updating don't seem to far off
And it also seems like people can not do the update easely due to the failiure I am getting trying to update.

---

### Post by Frogs Hair on 2022-04-01
Upgrade from 21.10 will come first, but the   LTS direct upgrade won't be available until the first point release based on passed history.

---

### Post by DuckHook on 2022-04-01
> **oden99 said:**
> Well it should be 2weeks untiull the release and the last beta are out..so updating don't seem to far off
And it also seems like people can not do the update easely due to the failiure I am getting trying to update.
There are two separate issues lumped together in your request:

It is possible to upgrade to Jammy by invoking the -d flag. However, like Frogs Hair says, you would first have to go through Impish. This would involve two separate do-release-upgrade cycles with each cycle increasing your likelihood of upgrade failure.

The biggest problem in your case is not the upgrade process, but the fact that you have so many PPAs. You are carrying a massive PPA burden that has modified your dpkg database so much that chances of a successful online upgrade are essentially nil. Even backing all of them out at this point is unlikely to help. The problem with PPAs is the way they corrupt the package database with their own often outdated dependencies. These have already been dragged in. Purging the PPA at this point is likely too late.

I have no idea whether you are new to Linux or an old hand, but, if new, then your number of PPAs is not a good habit.

For this reason especially, it would be better for you to reinstall from scratch, this time refraining from the zoo of PPAs that you've installed into your existing version.

For what it's worth, I have done dozens of online updates and mine are a piece of cake, taking all of 20 minutes. The failure of yours has nothing to do with the process itself and has everything to do with the way you have compromised the pristine environment of a default install.

---

### Post by deadflowr on 2022-04-01
> Now a short while before the official update to 22.04
Over 3 months.
The LTS upgrade channel is not officially open until late July/early August.

---

### Post by grahammechanical on 2022-04-01
I have a lot of experience upgrading from the last release to the next release under development. I have done this many times. Last November I upgraded from 21.10 to 22.04 (development) within two weeks of the 26 week development period starting. At that time the difference in code between the two versions was not great. 

I know a sure way to upgrade from 20.04 to 22.04 development version. But I would not do it as the code difference is so very great. The result would sure to be a broken mess. In your case, you have added lots of extra applications that may not have been upgraded to 22.04 libraries. In my opinion, the official upgrade path would be very risky for you.

A few months ago I purchased a laptop with 20.04 pre-installed. A couple of days ago I installed 22.04 development version. I will test out 22.04 and see how well any special applications install. I will do this before I upgrade 20.04 to 22.04 using the official method.

So, I suggest that you dual boot with 22.04 development version. Then if the official upgrade of 20.4 to 22.04 fails you will still have a working LTS version that you can use.

Regards

---

### Post by xxasdqwe on 2022-04-01
I upgraded from 20.04 to 22.04 without any problems except the VM sound module didnt get install and the iptables had to be set to the legacy package for ufw `update-alternatives --set iptables /usr/sbin/iptables-legacy`.

---

### Post by guiverc on 2022-04-01
I agree with almost all of DuckHook's suggestion, regarding issues with PPAs & the complications (*negative effects*) they do on the system which hamper upgrades.

I didn't see if you're using a desktop or server install; however if it was a desktop install - I'd recommend *upgrade via reinstall*.

What I'd use is a install; **without format** of your partition(s).  This will cause

- your *manually installed* packages are noted
- system directories are wiped (*thus package messages are gone!*)
- new system from media is installed
- if internet is available; the *manually installed* packages noted earlier are re-installed **IF** available in Ubuntu repositories for the new release
- no user file is touched, though any global configs saved in system directories will be gone
- user is asked to reboot  (*error on unavailable packages can be expected if packages are removed, or 3rd party - ignore these*)

If you decide to do this, I'd suggest copying your existing sources somewhere first, then removing all 3rd party sources from them - it allows for a cleaner install. You'll need of course to re-add them back (*if required*) post-install. Of course backup first, as this is a **major** change and mistakes are easy to make, so create for yourself a *backout* plan.

I have boxes where I *upgrade via re-install* regularly instead of performing normal upgrades, as it (1) upgrades my packages & (2) performs a QA-test install for the project involved at the same time.  I also use this method when a release goes EOL so I can *bump* that box to a release that's useful; ie. when 21.04 reached EOL; I *bumped* that install to 22.04 as I already had a 21.10 install (*my 20.10 install became 21.10 when groovy reached EOL*).

FYI:  This method also works going backwards too, ie. I regularly bump installs back to the prior LTS for QA-testing purposes.. however there are complications with going backwards, so do your homework before you do it (*what application/packages do you rely on, can the older software deal with databases/files from later versions etc*).

---

