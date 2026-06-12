---
title: "How do I install SNORTS?"
date: 2017-10-18
forum: Security
---

### Post by 1jarwolf on 2017-10-18
I have tried to install SNORTS from another post from Ubuntuforums however I could never seem to get it worked. I am wanting to try it again as it has been a while sense I have tried. ( a couple months. ) What is the [COLOR=#ff0000]_***EASIEST***_[/COLOR] way to install SNORTS onto my Ubuntu 17.04 Zesty?

---

### Post by Kirboosy on 2017-10-19
The only way I know how to install SNORT is to use the source and compile the software. However, its not as daunting as it might sound.

```
sudo apt update && sudo apt install openssh-server ethtool build-essential libpcap-dev libpcre3-dev libdumbnet-dev bison flex zlib1g-dev liblzma-dev openssl libssl-dev
```

[U][B]Install DAQ
[/B][/U]Download DAQ Source
```
wget https://www.snort.org/downloads/snort/daq-2.0.6.tar.gz
```
Extract Source
```
tar -xvf daq-2.0.6.tar.gz
```
Change into extracted folder
```
cd daq-2.0.6
```
Configure and compile the package
```
./configure && make
```
Install Package
```
sudo make install
```

[U][B]Install SNORT
[/B][/U]Download SNORT Source
```
wget https://www.snort.org/downloads/snort/snort-2.9.11.tar.gz
```
Extract Source
```
tar -xvf 
``````
snort-2.9.11.tar.gz
```
Change into extracted folder
```
cd 
``````
snort-2.9.1
```
Configure and compile the package
```
./configure --enable-sourcefire && make
```
Install Package
```
sudo make install
```
Update System shared librarys
```
sudo ldconfig
```
Test SNORT Install
```
sudo snort -v
```

SNORT is now installed on your system but now its up to you to configure it to do something productive. 

Hope that helps!
~Caboose

PS That is a quick and dirty guide. Should work for you as I just used it a few weeks ago on my system to setup SNORT.

---

### Post by 1jarwolf on 2017-10-20
Cool! Thanks, it was successfully installed! and works! When you type ***[COLOR=#000000][FONT=&amp]sudo snort -v[/FONT][/COLOR]*** in the terminal, it will just keep scanning constantly? How do I configure this for how I want it?

---

### Post by Kirboosy on 2017-10-20
[SNORT Configuration]("https://www.snort.org/configurations")

You can also take a peak at the [SNORT Documentation]("https://www.snort.org/documents"). They will cover everything you need to know about SNORT.

---

