---
title: "NEWBIE: What's the easiest /best way to make Ubuntu into Ubuntu Studio?"
date: 2010-04-11
forum: Ubuntu Studio
---

### Post by brucewagner on 2010-04-11
In other words....

Can I simply add a few repositories, and then install a list of applications....

...to sorta make a normal Ubuntu 9.10 into a sorta Ubuntu Studio (in capabilities)...?

If so,  what repositories? 

What list of applications?

---

### Post by philip5 on 2010-04-11
If you install the metapackage ubuntustudio-desktop then your Ubuntu install will install what ever applications that Ubuntu studio comes with (it will not remove anything besides if there would be any conflicts). That should be the easiest way if you don't want to download and install an Ubuntu studio cd and install ubuntu with all the ubuntu studio pre-selected applications.

---

### Post by Pablo_F on 2010-04-11
There is no need to add an extra repo to install that metapackage. For audio apps you have other two metapackages: ubuntustudio-audio and ubuntustudio-audio-plugins. For video, ubuntustudio-video installs some video apps.

Suggestion: add Philip's PPA to your repo list and you will have available very recent versions of some of the best apps in linux audio.

Philip, thank you very much. I am another user and advocate of your excellent PPA.

Cheers! Pablo

---

### Post by brucewagner on 2010-04-11
So... in review...  ( for the newbie me )...

(1)   I should add Philip Johnsson's “Ubuntu Studio” Repository  ( see [https://launchpad.net/~philip5/+archive/extra/+index?start=0&batch=75](https://launchpad.net/~philip5/+archive/extra/+index?start=0&batch=75) )

...by typing into Terminal: 

     sudo add-apt-repository ppa:philip5/extra

(2)   Then I should install the following packages:

    sudo apt-get install ubuntustudio-desktop
    sudo apt-get install ubuntustudio-audio
    sudo apt-get install ubuntustudio-audio-plugins
    sudo apt-get install ubuntustudio-video

Right?

And this will turn my Ubuntu 9.10 (SuperOS 9.10) into basically the same thing as Ubuntu Studio 9.10....?

Am I losing anything by doing it this way?

What's the difference (or advantage) to installing Ubuntu Studio directly?

---

### Post by cchhrriiss121212 on 2010-04-12
> 
What's the difference (or advantage) to installing Ubuntu Studio directly?
Not much really, you will just have two kernels to select from in grub. You will want to choose the real time kernel as default as this is what you need for audio processing. You can do this easily with startup manager which is in the repos.

The studio package can't be broken up, so that you can't uninstall programs you do not use and you might think this is a disadvantage. For this reason it might be an option to install an rt kernel separately from synaptic and then try out a few programs at a time from the philip5 ppa.

---

### Post by brucewagner on 2010-04-12
I installed startup-manager ..... cool.  (Now, I can select an new usplash theme, I see)

Stupid question: Which is the real time kernal?

I am offered:

1.Ubuntu, Linux 2.6.31-20-generic-pae
2.Ubuntu, Linux 2.6.31-19-generic-pae
3.Ubuntu, Linux 2.6.31-17-generic-pae

....plus a "(recovery mode)" for each one, and a couple "memory test" items.

Will using the "wrong" one negatively impact my Ubuntu Studio audio apps?

Will using the "right" one negatively impact any of my NON-UbuntuStudio apps?

---

### Post by brucewagner on 2010-04-12
> **cchhrriiss121212 said:**
> The studio package can't be broken up, so that you can't uninstall programs you do not use and you might think this is a disadvantage. For this reason it might be an option to install an rt kernel separately from synaptic and then try out a few programs at a time from the philip5 ppa.

This sounds like a very practical idea... 

(1)   How can I install a rt kernel separately?  I mean... How would I know WHICH kernal to install?  (Remember, you're talking to a novice here.)

(2)   Can I get a separate list of all the programs included in the ubuntustudio-desktop (along with their actual synaptic names), which I can choose from?   Where can I find that list?

---

### Post by spicey_mike on 2010-04-13
I am brand new here myself and brand new to Linux but i am thoroughly enjoying it so far. I think the easiest way of getting studio is a fresh install.

I just downloaded and installed the public  beta2 of 10.04 and it solved all of my video issues with 865g chipset I was having in karmic.  All resolutions worked out of the box and it even identified my monitor  manufacturer.

I am having two minor issues with this release:

1st with audio (ICH5 Integrated). Although my audio is much better than it was in karmic (no snaps, crackles, or pops) I still have a higher level on my right side speaker. I cannot figure out why. It is not a speaker issue as they worked perfectly in Win7.  

2nd with Synaptic Package Manager. For some reason it is not giving admin rights in synaptic. I tried adding my main account to the root and admin groups and logged out and logged back in still with no admin rights.

Anyone have any ideas?

---

### Post by cchhrriiss121212 on 2010-04-13
> (1) How can I install a rt kernel separately? I mean... How would I know WHICH kernal to install? (Remember, you're talking to a novice here.)
Just go to system>synaptic package manager and enter linux-rt into the search box, you should install the package that has "complete rt linux kernel", there is only one rt kernel in there. Once that has installed you can use startup manager to select it as default.
Sometimes a system will not co-operate with a new kernel, so if you get weird problems let me know and I can post a link to some other rt kernels not in the repos.  

> Will using the "wrong" one negatively impact my Ubuntu Studio audio apps?
Will using the "right" one negatively impact any of my NON-UbuntuStudio apps? 	
An rt kernel makes a difference for low latency audio, as it allows you to use the realtime mode in jack. It won't affect any of your other programs.

> (2) Can I get a separate list of all the programs included in the ubuntustudio-desktop (along with their actual synaptic names), which I can choose from? Where can I find that list?
[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)
Jack should be the first thing you install as it's the sound server for all the audio programs. Which reminds me that you should make these modifications:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
sudo adduser <username> audio
```

This is from this guide:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by cub on 2010-04-13
I just followed the instructions on [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

I thought that was very straight forward and easy.

---

### Post by untmdsprt on 2010-04-17
> **philip5 said:**
> If you install the metapackage ubuntustudio-desktop then your Ubuntu install will install what ever applications that Ubuntu studio comes with (it will not remove anything besides if there would be any conflicts). That should be the easiest way if you don't want to download and install an Ubuntu studio cd and install ubuntu with all the ubuntu studio pre-selected applications.

This is actually the better way if you still want to dual boot your computer. I've found the UbuntuStudio installer to be generic in nature, and doesn't account for the other OS you may have. I've found the desktop "look" isn't exactly the same though. :(

---

### Post by ProDigit on 2010-04-21
I'm stuck with another problem;
You can install Studiobuntu straight on top of Ubuntu 10.4, but when uninstalling it, you're still stuck with the exiting (or shutdown) splash screen.

Any solutions to remove the splash screen?
Ub10.4 isn't stable yet and at times I get some errors, which I would like to see without pressing the <esc> key all the time.

---

### Post by JC Cheloven on 2010-04-23
@ the OP:  

- Either way, be sure to end up with UbuntuStudio Controls installed. Its menu entry will be at system/administration. Use that to set your "nice" and memlock percentages to something suitable for your system (maybe -10 & 25 respectively, for example)

- In addition to the link Cub gave you (excellent, although "under construction"), please read this guide. It's a classic: 
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Cheers

---

