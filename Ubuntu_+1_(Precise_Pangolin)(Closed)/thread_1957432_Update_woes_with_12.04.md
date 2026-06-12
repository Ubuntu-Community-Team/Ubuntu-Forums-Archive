---
title: "Update woes with 12.04"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sfrank on 2012-04-12
Hi,

I'm having trouble updating from Oneiric to Precise. The Update Manager states that the package unity is about to be removed but it is in a non-removal blacklist.

I'm pretty sure this has to do with some PPA package that I have installed. How is one supposed to find out which dependency causes the conflict and the resulting removal? The Update Manager is not very helpful with any other messages and just resets the system/package state to its original setting.

Many thanks for any suggestions.

Stephan

---

### Post by fantab on 2012-04-12
Personally, I will always recommend a Clean Install/ Fresh Install as opposed to Upgrade. 
Back up your important data and do a clean install. It is always safe, clean and simple.

---

### Post by kansasnoob on 2012-04-12
> **sfrank said:**
> Hi,

I'm having trouble updating from Oneiric to Precise. The Update Manager states that the package unity is about to be removed but it is in a non-removal blacklist.

I'm pretty sure this has to do with some PPA package that I have installed. How is one supposed to find out which dependency causes the conflict and the resulting removal? The Update Manager is not very helpful with any other messages and just resets the system/package state to its original setting.

Many thanks for any suggestions.

Stephan

What exact procedure are you following?

I mean, what command(s) are you running to initiate the upgrade process to Precise Beta 2?

---

### Post by Mathor on 2012-04-12
> **sfrank said:**
> Hi,

I'm having trouble updating from Oneiric to Precise. The Update Manager states that the package unity is about to be removed but it is in a non-removal blacklist.

I'm pretty sure this has to do with some PPA package that I have installed. How is one supposed to find out which dependency causes the conflict and the resulting removal? The Update Manager is not very helpful with any other messages and just resets the system/package state to its original setting.

Many thanks for any suggestions.

Stephan

Get Synaptic Package manager and find out which package is trying to remove it, and hold that package back or remove it (in my case it was cinnamon, as it doesn't play nice with 12.04 right now)

And I will reiterate what fantab said, as a clean-install ultimately results in more stability, and doesnt take that much time if you have everything backed up.

---

### Post by sfrank on 2012-04-12
simply a

sudo update-manager -d

then click on the update button to 12.04. After that it tells me that it disabled any third party repos, calculates the dependencies, errors out with the above error concerning unity removals and finally restores the intial setting.

---

### Post by kansasnoob on 2012-04-12
You shouldn't use sudo for that, and just for poops and giggles try:

```
update-manager -d -c
```

If if displays any errors please grab a screenshot.

You may also want to try something like:

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get update
```

Before trying again ........... and obviously post any errors here.

---

### Post by Holdolin on 2012-04-12
I'd always reccomend a clean install.  I've seen waay to many problems using the updater to upgrade releases.

---

### Post by Gregory Lee on 2012-04-12
I've not very enthusiastic about a fresh install.  I've been using "aptitude safe-upgrade", but that is currently holding back 9 packages.  Here is what aptitude says it would do if I were to ask for a full-upgrade:
```
:~# aptitude full-upgrade
The following NEW packages will be installed:
  libfarstream-0.1-0{ab} libgdict-common{ab} libtelepathy-farstream2{a} 
The following packages will be upgraded:
  empathy empathy-common gnome-dictionary kde-l10n-engb language-pack-kde-en language-pack-kde-en-base 
  libgdict-1.0-6 libpurple0 nautilus-sendto-empathy 
9 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,777 kB of archives. After unpacking 2,485 kB will be used.
The following packages have unmet dependencies:
 libgdict-common : Breaks: gnome-utils-common (< 3.3) but 3.2.1-0ubuntu5 is installed.
 libfarstream-0.1-0 : Conflicts: libgstfarsight0.10-0 but 0.0.31-1ubuntu3 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                                           
1)      banshee-extension-telepathy                                                            
2)      empathy                                                                                
3)      gnome                                                                                  
4)      gnome-core                                                                             
5)      gnome-dictionary                                                                       
6)      libgdict-1.0-6                                                                         
7)      libpurple0                                                                             
8)      telepathy-haze                                                                         

      Keep the following packages at their current version:                                    
9)      libfarstream-0.1-0 [Not Installed]                                                     
10)     libgdict-common [Not Installed]                                                        
11)     libtelepathy-farstream2 [Not Installed]                                                

      Leave the following dependencies unresolved:                                             
12)     ubuntu-desktop recommends empathy                                                      
13)     banshee-community-extensions recommends banshee-extension-telepathy (>= 2.4.0-1ubuntu1)


Accept this solution? [Y/n/q/?] 

```
(I answered "q".)

---

### Post by sfrank on 2012-04-12
Thanks Gregory, I didn't know about this aptitude function.

In the meantime I've found the culprit to be some left-over development version of compiz. By downgrading these packages I was able to upgrade to 12.04.

Many thanks to everbody for their input.

---

### Post by JRV on 2012-04-12
> **Holdolin said:**
> I'd always reccomend a clean install.  I've seen waay to many problems using the updater to upgrade releases.

+1, I would definitely recommend a fresh install.
The change from gnome2 to gnome3/Unity is huge, as is the change from gtk2 to gtk3.

---

