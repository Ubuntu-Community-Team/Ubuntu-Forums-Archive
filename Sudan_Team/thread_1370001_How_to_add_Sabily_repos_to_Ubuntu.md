---
title: "How to add Sabily repos to Ubuntu"
date: 2010-01-01
forum: Sudan Team
---

### Post by zero-n on 2010-01-01
[SIZE=3][U][B]1- Add their PPA:
[/B][/U][/SIZE]
```
sudo gedit /etc/apt/sources.list
```_add one of  the following to the end of file:_

**Ubuntu 10.04 Lucid Lynx:**
```
#Launchpad PPA for Ubuntu Muslim Edition Team
deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu lucid main
```**Ubuntu 9.10 Karmic Koala:**
```
#Launchpad PPA for Ubuntu Muslim Edition Team
deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu karmic main
```[B]
Ubuntu 9.04 Jaunty Jackalope:[/B]
```

#Launchpad PPA for Ubuntu Muslim Edition Team
deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu jaunty main 

```[SIZE=3][B][U]

2- Add GPG key:

[/U][/B][/SIZE][LEFT]```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D1A0D2FB
```if it goes will it will show you 

```
[LEFT]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys D1A0D2FB
gpg: requesting key D1A0D2FB from hkp server keyserver.ubuntu.com
gpg: key D1A0D2FB: public key "Launchpad PPA for Ubuntu Muslim Edition Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
[/LEFT]

```[SIZE=3][U][B]

3- Update sources list:[/B][/U][/SIZE]

```
sudo apt-get update
```[/LEFT]

---

### Post by mhmdfoss on 2010-01-02
[center][size=3]&#1601;&#1578;&#1588;&#1578;&#1575; &#1593;&#1606; &#1591;&#1585;&#1610;&#1602;&#1577; &#1575;&#1590;&#1575;&#1601;&#1577; &#1605;&#1589;&#1575;&#1583;&#1585; &#1578;&#1608;&#1586;&#1610;&#1593;&#1577; &#1587;&#1576;&#1610;&#1604;&#1609; &#1576;&#1609; &#1587;&#1591;&#1585; &#1575;&#1604;&#1575;&#1608;&#1575;&#1605;&#1585; &#1576;&#1587;](*,)[/size]
[size=3]&#1578;&#1588;&#1603;&#1585; &#1610;&#1575; &#1576;&#1575;&#1588;&#1575;[/size]

[/center]

---

### Post by ejlal on 2010-01-02
hey 
salam 3alikom

is there any difference from adding it through software source:
**Adding this PPA to your system**

                  You can update your system with unsupported packages from           this untrusted PPA by adding           **ppa:sabily.team/ppa**           to your system's Software Sources.


[[COLOR=Red]**Source**[/COLOR]]("https://launchpad.net/%7Esabily.team/+archive/ppa/+index?field.series_filter=jaunty")


i added it this way so if there is any difference i want to know, to re-add it again.
thanks 
and Happy New Year.

---

### Post by zero-n on 2010-01-02
Not it's the same cause **[COLOR="Red"]Software Sources[/COLOR]** is using:

```
/etc/apt/sources.list
```

as the configuration file and you can import keys from the **[COLOR="Red"]Software Sources[/COLOR]** too.

---

### Post by abu_umair on 2010-01-09
HI....
 
Can  we add sabily repos to ubuntu offline (no internet connection)?
 
 
 
Thank's

---

### Post by zero-n on 2010-01-10
You can add it to the repositories list but you can't add it's key.

you will need internet connection to download the key and off-course to download 

packages.



**But you can make an offline repository:**
download the latest issue of Full Circle Magazine and you will find a topic about offline repository.

Download link: **[COLOR="Red"][Issue 32]("http://dl.fullcirclemagazine.org/issue32_en.pdf")[/COLOR]**

---

