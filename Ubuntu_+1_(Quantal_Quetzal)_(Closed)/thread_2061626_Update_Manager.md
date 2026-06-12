---
title: "Update Manager"
date: 2012-09-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MikeCyber on 2012-09-23
Hi
could we finally get an Update Manager that only updates installed stuff! The 12.04 downloads/installs all available updates...sigh. :confused:

---

### Post by Bucky Ball on 2012-09-23
*Thread moved to **General Help***

*Reason*: Originally posted in ***Ubuntu +1*** sub-forum which is intended for 12.10 discussion. ;)

---

### Post by Sonsum on 2012-09-23
> **MikeCyber said:**
> Hi
could we finally get an Update Manager that only updates installed stuff! The 12.04 downloads/installs all available updates...sigh. :confused:

Could you maybe elaborate on your question? The Update Manager does only apply updates to your system, with the exception of kernel upgrades and other software recommended by ubuntu-desktop and other metapackages.

These new packages are installed because they are connected and necessary for the other packages you already have installed that are updating.

---

### Post by akoskm on 2012-09-23
> **MikeCyber said:**
> Hi
could we finally get an Update Manager that only updates installed stuff! The 12.04 downloads/installs all available updates...sigh. :confused:

The Update Manager downloads/installs available updates only for the installed stuff. I think it's always worked like that.

---

### Post by MikeCyber on 2012-09-23
No, in the last update it did install tons of for ex. DNS stuff. Boot takes longer as it now starts  additional stuff.-
There's no runlevel editor anymore? How/where to disable those?

---

### Post by TenPlus1 on 2012-09-23
Update Manager will only install updates for the packages you already have installed on your system, although sometimes it will update a meta-package and pull in something new that is required...  This is how it works and cannot be changed unless you update manually...

---

### Post by grahammechanical on 2012-09-23
Is this a typing error:

> The 12.04 downloads/installs all available updates.

I sometimes get my 12.10s mixed up with 12.04s. I ask because this post is in the Ubuntu+1 (that is 12.10) section. And I think that the updates work slightly differently in the development release than in the distribution release (12.04 and older).

I think that stuff is installed in advance of other stuff because of intended changes to the design and way of working.

For example, for some weeks now network manager has been able to make a network connection by the time we reached the log-in  screen. For what purpose? so that we can make a remote connection to another computer at login time (something that has only just been possible).

So, I am not surprised to see stuff being downloaded and installed in 12.10 that is not strictly an update to existing packages. Watching the release develop over the weeks is what makes using Ubuntu+1 interesting for me.

Regards.

---

### Post by jerrylamos on 2012-09-23
> **MikeCyber said:**
> Hi
could we finally get an Update Manager that only updates installed stuff! The 12.04 downloads/installs all available updates...sigh. :confused:"Update Manager" has screwed so many installs for me the first thing I do is turn daily updates off in software sources.  
sudo software-properties-gtk
On second window turn partners on, on third window turn off unsupported and turn off daily
sudo synaptic, settings, repositories will get you to the same screens
Sometimes Systems Settings way down at the bottom there is software sources, sometimes not.
Then especially during development I make an exec 

gedit ad
#!/bin/bash
sudo apt-get update  
sudo apt-get -y dist-upgrade
save
sudo chmod +x ad

Then just do a 
./ad
when I want to, daily when changes are being made, not "update manager" come crashing in to what I'm doing.  Of course "update manager partial" has been a real disaster.  Don't do that!

Do note the "-y" is dangerous because on occasion upgrade wants to remove essentioal stuff....to be safe, remove that, let upgrade ask "Y/n".  Has been O.K. lately.

---

### Post by cariboo on 2012-09-23
You didn't specify what version you are running, but I would bet you have removed several applications installed by default, without removing the *-desktop meta package. For example if you removed some of the recommended programs, that the ubuntu-desktop installs, without removing the ubuntu-desktop, they will get re-installed/updated when you do an update.

Ubuntu uses upstart, and has for years, there isn't a run-level editor. See [here]("http://askubuntu.com/questions/133807/how-to-config-start-services-with-upstart"), on how to set what services start and when.

---

### Post by Cavsfan on 2012-09-24
**Ranch Hand** always called update manager update mangler. LOL!
He told me to always use:
[B]sudo apt-get update
sudo apt-get upgrade[/B]
I believe those are much better than using update manager as you can see what will be installed as well as what is held back.

Sometimes before installing the updates I will open update manager or synaptic package manager to see what the updates are.
But, I never update anything from there.

If you have a new kernel or other programs being held back, after the updates enter:
**sudo apt-get dist-upgrade**
That will install the held packages again with a (Y/n) option to install them.

Another user on this forum told me how to make these into a script:
Edit .bashrc in your home directory
**gksu gedit ~/.bashrc**
I copied and pasted these after line 88.
```
# update aliases
alias **ud**='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias **ud2**='sudo apt-get dist-upgrade'
```Once you logoff and back on you just have to enter **ud** in terminal and enter your password. You will be shown the updates with a (Y/n) option to install them.
After installing the updates if you see something held back, enter **ud2** to get the ones being held back.
This method will never fail you.

---

