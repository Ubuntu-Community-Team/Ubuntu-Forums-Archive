---
title: "Removing Unity and keeping Gnome Shell 3.8"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by DisappearingOak on 2013-04-19
Hi, I have 13.04 updated. it is the unity version with Gnome 3.8 added via ppa. I want to remove Unity and it's dependencies (compiz, nux, etc.) while retaining Gnome 3.8 and apps without breaking anything. Please help.
If that's not possible, how do I get a Ubuntu-Gnome while retaining Gnome 3.8 and without Unity? Is there a psychocats like command?
Thanks.

---

### Post by cariboo on 2013-04-19
Why not just install Raring using the Ubuntu Gnome iso, available [here]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/").

---

### Post by DisappearingOak on 2013-04-19
I've been using this as my primary install and have a lot of stuff going on, data saved here and there, and my browsers properly set up. So I would rather not do a clean install, if possible.

---

### Post by serdotlinecho on 2013-04-19
```
sudo apt-get purge compiz compiz-core compiz-gnome compiz-plugins-default compizconfig-settings-manager libcompizconfig0 libunity-webapps0 python-compizconfig unity unity-asset-pool unity-lens-* unity-scope-* unity-services unity-webapps-* xul-ext-unity libnux-4.0-0 libnux-4.0-common nux-tools
```

If you're not sure, use sudo apt-get -s purge to do simulation.

---

### Post by EgoGratis on 2013-04-19
If you have big enough HDD/SDD don't bother it doesn't take much disk space and your PC wont work any faster if you remove Unity.

---

### Post by montag dp on 2013-04-19
You could reinstall but not format the /home partition (assuming you do have a separate /home). Just get rid of the hidden folders you don't need to retain.

---

### Post by Rukiri on 2013-04-20
Better yet and recommended for any ubuntu installation is to start with nothing, use the server ISO and build what you want and add what you need, this way you get what you want in your system and nothing you don't.
Plus I find Ubuntu's installer seriously buggy...(I literally have to UPDATE the installer before I can install ubuntu, that's just ridiculous!!)

---

### Post by MikeCyber on 2013-04-20
> **montag dp said:**
> You could reinstall but not format the /home partition (assuming you do have a separate /home). Just get rid of the hidden folders you don't need to retain.

Yes but keep the hidden .* files as they contain the config for ex. thunderbird's received mails and config/settings.-

---

### Post by DisappearingOak on 2013-04-20
Thanks. I was able to uninstall unity and keep Gnome. Actually I wanted to remove unity and extra fluff because I'm on a slow internet connection (700kbps-1Mbps)  and the updates and upgrades can take some time to do. It didn't make too much difference but the command posted in the thread did work. Thanks.

---

### Post by kuvanito on 2013-04-20
so you want 13.04 gnome,here it goes:

sudo apt-get install gnome-shell (choose gdm)
sudo reboot (at login choose gnome)
sudo apt-get purge unity*
sudo apt-get install nautilus
sudo apt-get autoremove
sudo apt-get autoclean
sudo reboot

be aware,unity will be gone for good and gnome shell will be 3.6,believe me there is no difference between 3.6 and 3.8 
no it's not the same using 13.04 gnome shell remix,they still use old apps like evolution mail and the look is ugly
doing this way you still keep the look and feel of the latest 13.04 and the beautiful themes,remember dconf-editor it's your best friend
now if you want to clean some of the clutter,eliminate a bunch of apps that are at least useless for me,here you go:

sudo apt-get purge aisleriot* baobab* empathy* gnome-games-data* gnome-mines* gnome-disk-utility* gnome-mahjongg* gnome-sudoku* gwibber* deja-dup* onboard* overlay-scrollbar* gnome-orca* remmina* rhythmbox* shotwell* usb-creator* ubuntuone* software-center* xdiagnose* xterm* && sudo apt-get autoremove && sudo apt-get autoclean

here are some pics of my Ubuntu 13.04 Gnome Shell Edition my way,hehehehe

---

### Post by montag dp on 2013-04-20
> **MikeCyber said:**
> Yes but keep the hidden .* files as they contain the config for ex. thunderbird's received mails and config/settings.-Right, that's why I said to get rid of the ones he didn't need.

---

### Post by MikeCyber on 2013-04-21
Tried the iso mentioned above in virtualbox and gnome-shell --version returns 3.6.31 or so. How/should I to update to 3.8 and what are the differences? I'll install the final in a week...is there a website for hmm how is the gnome version called? Thanks

---

### Post by sgage on 2013-04-21
> **MikeCyber said:**
> Tried the iso mentioned above in virtualbox and gnome-shell --version returns 3.6.31 or so. How/should I to update to 3.8 and what are the differences? I'll install the final in a week...is there a website for hmm how is the gnome version called? Thanks

To get GS 3.8 you do:

```
sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
```

3.8 isn't that different from 3.6, at least for me and the way I work. If you have extensions that you absulutely must have, be advised they might not be updated yet. There have been several reviews here and there re: 3.8, you should be able to google something up pretty easily.

---

### Post by sgage on 2013-04-21
> **Rukiri said:**
> Better yet and recommended for any ubuntu installation is to start with nothing, use the server ISO and build what you want and add what you need, this way you get what you want in your system and nothing you don't.
Plus I find Ubuntu's installer seriously buggy...(I literally have to UPDATE the installer before I can install ubuntu, that's just ridiculous!!)

I've personally never found the Ubuntu installer 'seriously buggy', but just for grins, I decided to do a fresh install from the mini.iso, and bring up a system from there. It was remarkably easy. 

I did the absolute minimum install (did not select any additional software beyond the core system). When I booted into my new command-line-only system, I simply did 'sudo apt-get install gnome-shell', and that brought in pretty much everything I wanted. After it was done, I booted into GS and didn't have to install more than half a dozen or so packages (in addition to my usual post-install script) to be right where I wanted. And that's what I'm running right now...

There are many packages that typically get installed that I have absolutely no use for, and I'd just as soon not install them and all their dependencies. I'm not particularly hurting for disk space, but it's an aesthetic thing, I guess :KS

That said, the Ubuntu Gnome iso does a great job, if you want a Gnome Shell system. It doesn't install much of what I consider extraneous packages. But we all use our computers differently. Hurrah!

---

