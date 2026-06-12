---
title: "SD card reader 20.04 LTS"
date: 2020-06-23
forum: Ubuntu, Linux and OS Chat
---

### Post by aitkenrob on 2020-06-23
USB card reader for sd card. 
Cant see sd card. Replaced usb reader. Same. I see it in Gparted but cant do anything. Format....I stick it in my phone and I see the movies and works fine on other machines.
Ran the following: sudo add-apt-repository universe
sudo apt install exfat-fuse exfat-utils
sudo apt install exfat-utils exfat-tools
sudo apt-get install --reinstall udisks2

Ran: sudo lsblk 
and it picked it up, 
sdc      8:32   1  14.9G  0 disk 
When I try format: Input/ouput error during read on/dev/sdc

I have used Ubuntu since 10 and am stumped. Contemplating a fresh install. 
Any advise will be appreciated.

---

