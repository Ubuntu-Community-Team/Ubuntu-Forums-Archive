---
title: "Real player"
date: 2005-07-14
forum: Repositories &amp; Backports
---

### Post by Biffy on 2005-07-14
Hi, im trying to install Real player from Synaptic. A screen appears, asking me where the install file is. I dont have a clue where it is. Please help.

I am using hoary and im trying to install Real player 8.

---

### Post by netrattler on 2005-07-14
Instructions for Hoary.

Hoary :
[http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)


Joe

---

### Post by Biffy on 2005-07-15
Yes, i have already tried installing it from APT. That is when that screen apears asking me where the downloaded Realplayer install file is. And i dont know that.

---

### Post by netrattler on 2005-07-15
When apt downloads the file will download to  /var/cache/apt/archives

Joe

---

### Post by Biffy on 2005-07-17
[QUOTE=netrattler]When apt downloads the file will download to  /var/cache/apt/archives

Joe[/QUOTE]

It aint there either. Maybe i must download the rpm file manually, but this seems weird since i need a deb file.

Any info on this?

---

### Post by Majlo on 2005-07-17
Hi . .

First add Backport repository to your sources list 
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then 

sudo apt-get update
sudo apt-get install realplayer
killall gnome-panel

Go to Applications --> Sound & Video --> Realplayer

In Backport is new version 10.0.4

---

