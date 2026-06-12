---
title: "PPA packages only showing up on command line"
date: 2007-09-18
forum: Repositories &amp; Backports
---

### Post by StevenHarper on 2007-09-18
Hi,

I am on the launchpad BETA, I have made my first PPA

(Personal Package Archive)

I have added the following to my /etc/apt/sources.list

```

deb     http://ppa.launchpad.net/stevenharperuk/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.launchpad.net/stevenharperuk/ubuntu feisty main restricted universe multiverse

```

When I look in the graphical app-manager, my packages don't appear, however on command line they do

```

apt-cache search easycrypt
apt-get install easycrypt

```

both work.

However I can't see them in the graphical manager...

can anyone help?

Steve

---

### Post by StevenHarper on 2007-09-18
the answer is that the list in the App Manager is controlled by the 

**gnome-app-install** package

what happens is that gnome-app-install, has a set of files (/usr/share/app-install) these are for the entries in the App Manager.

So really you can get anything added to App Manager without

[LIST]
[*]Hacking the files in
[*]Replacing gnome-app-install with your own version (bad)
[/LIST]

So the verdict is : it can't be done : use the terminal

Steve

---

