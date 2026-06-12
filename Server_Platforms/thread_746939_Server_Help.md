---
title: "Server Help"
date: 2008-04-06
forum: Server Platforms
---

### Post by BrentMlady on 2008-04-06
Hi Everyone,

I am new to ubuntu sever and I am trying to learn more about it.  I thought it would be a good idea to try and install a GUI so it will make learning a bit easier.  Yes I know why would you install a GUI but i find it easier to learn when I can see a GUI.

I have tried to use the following but I have had no luck.

# apt-get update
# apt-get install xserver-xorg xfonts* gnome

But it said 
"Package xserver-xorg has no installation candidate"

so i tried 
# apt-get install xserver-xorg-core

But it said 
"The following packages have unmet dependencies:
  xserver-xorg-core: Depends: xserver-xorg but it is not installable"

I then tried 

# apt-get install ubuntu-desktop

But it said 
"E: Couldn't find package ubuntu-desktop"

Can anyone give me a clue as to what I am doing wrong.  I have also tried all of the above with aptitude.
I am currently running Ubuntu Server 7.10 with all the latest updates.

Thanks

---

### Post by WhiteCross on 2008-04-06
In my experience, here's what ive done so far.

my Ubuntu is installed in VMWare,
the ethernet is set to NAT because
i have a wireless connection that auto detects internet
so i cant use static config on the interfaces

i let the cd installer in cd-rom drive (i dont know if it affects anything)

i jz used the dhcp

enabled the universe and multiverse at /etc/apt/sources.list

then

sudo apt-get update

then

sudo apt-get install ubuntu-desktop

i successfully installed the GUI..

now here's the thing, i still dont know how to run it,
I hope someone would be kind enough to tell us how to run it
after installing it..

---

### Post by tamoneya on 2008-04-06
```
startx
```

---

