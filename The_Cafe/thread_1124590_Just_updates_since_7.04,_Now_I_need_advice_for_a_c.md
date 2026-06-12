---
title: "Just updates since 7.04, Now I need advice for a clean install of 9.04"
date: 2009-04-13
forum: The Cafe
---

### Post by legolas_w on 2009-04-13
Hello everyone.
It is about 2 years that I completely switched to ubuntu (since 7.04). I just upgrade and update the system instead of reinstalling the OS. Now I want to perform a clean install of 9.04 and I look for advices about it.

- I have created a seperate partition for home, and opt. So I will assign their mount point during the installation.
- I want to move some of configurations like: FireFox and Thunderbird, Transmission, Pidgin, and IDEs.

Please advice me on what other information I may need to copy to the new installation, what other things I should consider to have a perfect installation, and so on.

Thanks.

---

### Post by ugm6hr on 2009-04-13
If you have a separate /home partition, Firefox and T-bird should not require any manual adjustment, as long as you used the default profile locations (in /home/.mozilla)

Pretty sure that Pidgin does the same, but less certain about Transmission, although I would be surprised if it didn't keep all setup files in /home.

---

### Post by Pogeymanz on 2009-04-13
Just don't format your /home.
Then when you install your IDE, etc it will see your old configs.
I would let everything else get formatted.

Otherwise, you shouldn't have any problems.

---

### Post by swoll1980 on 2009-04-13
If you don't have a seperate /home make a backup to dvd. If you want to switch to ext4, or If /home is to big to put on a dvd, make a partition, copy /home to it, install Ubuntu, transfer your /home copy back to Ubuntu then delete the extra partition, and grow your Ubuntu partition to fill the gap

---

### Post by legolas_w on 2009-04-13
Right now my /home is not in a seperate partition but I create a partition to use it as /home for new installation.

A question: 
What is exactly content of /home/username? For example does it contains sound system configuration or any type of configuration related to operating system or it is just for personal software that we install?

I do not want to have anything related to my sound system moved from my current installation to the new installation.

Thanks

---

### Post by hessiess on 2009-04-13
All user editable configurations(anything which dosn't require sudo) is stored in the home directory. try pressing ctrl+h to un-hide all the hidden files ;) outher configuration files are generally stored in /etc

---

### Post by ugm6hr on 2009-04-13
> **legolas_w said:**
> Right now my /home is not in a seperate partition but I create a partition to use it as /home for new installation.

I misunderstood.  But you can just copy **all** contents from old /home directory to new /home partition *before* installing Jaunty (using manual option and preserving /home).

/home contains all desktop settings and application configurations and settings.

e.g. your desktop wallpaper, nautilus preferences, FF and T-bird profiles (i.e. favourites, email folder etc).

EDIT: Don't forget hidden files / folders

---

### Post by andamaru on 2009-04-13
The configuration of fireFox and Thunderbird, Transmission, Pidgin, and IDE are all stored in your home directory.

Linux automatically hides files that contain a "." in front of their name, example .andamaru will not show up unless you tell your file manager to show hidden files. Programs take advantage of this and use it to store all their configurations in "hidden" folders. For example Firefox user configuration is stored in .firefox, and netbeans is stored in .netbeans.

Another thing to remember is user specific settings are stored in your home directory (eg. /home/andamaru) but system wide settings are stored in /etc/. User specific settings would be your set up of firefox, and netbeans, an easy way to tell is if the setting would be different for every user is most likely stored in your home directory. If we take something like samba these settings will be the same for everyone so it's stored in /etc

If you make a list of all the program settings you want saved myself and everyone else will help you backup all of them.

---

### Post by swoll1980 on 2009-04-13
> **ugm6hr said:**
> I misunderstood.  But you can just copy **all** contents from old /home directory to new /home partition *before* installing Jaunty (using manual option and preserving /home).

/home contains all desktop settings and application configurations and settings.

e.g. your desktop wallpaper, nautilus preferences, FF and T-bird profiles (i.e. favourites, email folder etc).

You can do it this way to. My technique listed above would be if you didn't want a separate partition for /home

---

