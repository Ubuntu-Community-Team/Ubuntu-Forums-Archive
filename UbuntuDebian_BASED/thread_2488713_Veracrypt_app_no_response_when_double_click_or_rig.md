---
title: "Veracrypt app no response when double click or right click and open"
date: 2023-07-13
forum: Ubuntu/Debian BASED
---

### Post by johnnyblack2 on 2023-07-13
I'm using the Zorin OS 16.2 which is Ubuntu 22.04 version.

veracrypt-1.25.9-Ubuntu-22.04-amd64.deb 

I downloaded the .deb format file from their official website.

I used Gdebi installer and found that I need 2 more dependencies.

libayatanaappindicator3-1
libayatanaindicator3-7
(name could be a little wrong or something.)

I installed 2 dependencies and installed the .deb Veracrypt.

I searched Veracrypt and put it on desktop. 
Double click or right click open, non works. (Because unlike windows, linux has 2 methods and some won't respond unless right click open or click "enter".)

I did a update upgrade through terminal right before doing this and there was a error message saying "broken" whatever.
I can't find that notification anymore. I was tired of getting multiple problems when I was trying to solve 1. (Happens everyday in linux.)
All other softwares work so I don't think that was the reason.

I'm not used to tarbz or mkdir, wget methods.

I only use Terminal, Synaptic or .Deb since these are safe from problems where I don't have to reinstall the entire os.




I tried something similar in "itsfoss.com" tutorial where they teach you how to install the latest WINE version. 
It's "mkdir" "wget" "keyrings" "Jammy (know your ubuntu version and type it. I use zorin but still it's Ubuntu 22.04 based.) 
These things are something that I have no idea what it is. I couldn't update or upgrade anymore so I installed the entire os.
I'm guessing the keyrings and stuff that I wrote is where the udpate and ugprade location changed to, or something ? Instead of the main repository update & upgrade ?
I could not change it back or solve.

sudo dpkg --add-architecture i386

sudo apt update
sudo apt install wine

sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -0 /etc/apt/keyrings/winehq-archive.key [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key)

sudo apt install wget

lsb_release -cs

sudo wget -NP /etc/apt/sources.list.d/ [https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/](https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/)
winehq-jammy.sources

sudo apt update

sudo apt install --install-recommends winehq-stable

---

### Post by howefield on 2023-07-13
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

