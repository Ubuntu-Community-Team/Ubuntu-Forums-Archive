---
title: "how to install ms tt core fonts for ies4linux"
date: 2010-03-24
forum: Wine
---

### Post by wstay on 2010-03-24
Can someone please show how to install ms tt core fonts for ies4linux?

---

### Post by _h_ on 2010-03-24
The Microsoft TrueType core fonts package? It's in the repos if Wine didn't install it with it's install:

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by wstay on 2010-03-24
> **_h_ said:**
> The Microsoft TrueType core fonts package? It's in the repos if Wine didn't install it with it's install:

```
sudo apt-get install ttf-mscorefonts-installer
```

I post:
wstay1@wstay-ubuntu9:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for wstay1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
wstay1@wstay-ubuntu9:~$ 

How do I get wine or ies4linx (ie6) to read the ms core fonts.
The ie6, one of my Bank site, the Share Trading cannot read the Shares in English. Don't know why it read the Shares in Chinese although I installed ies4linux by choosing Locale: EN-US.
May be I should upgrade the 11 not upgraded when I posted 'sudo apt-get install ttf-mscorefonts-installer' And how to do the the upgrade? Any advise please.

---

### Post by dino99 on 2010-03-25
> **wstay said:**
> I post:
wstay1@wstay-ubuntu9:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for wstay1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
wstay1@wstay-ubuntu9:~$ 

How do I get wine or ies4linx (ie6) to read the ms core fonts.
The ie6, one of my Bank site, the Share Trading cannot read the Shares in English. Don't know why it read the Shares in Chinese although I installed ies4linux by choosing Locale: EN-US.
May be I should upgrade the 11 not upgraded when I posted 'sudo apt-get install ttf-mscorefonts-installer' And how to do the the upgrade? Any advise please.

Go there: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
install winetricks
then install allfonts from it ( load it with sh winetricks and scroll list down till allfonts)

---

### Post by wstay on 2010-03-29
> **dino99 said:**
> Go there: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
install winetricks
then install allfonts from it ( load it with sh winetricks and scroll list down till allfonts)

I installed allfonts from winetricks, it didn't work.
Is there a way to link the ms core fonts from the /home/wstay1/.wine/drive_c/windows/Fonts folder to the /home/wstay1/.ies4linux/ie6/drive_c/windows/Fonts.
I read somewhere  before on how to link these fonts but could not find these posts now when I use google to search.

---

