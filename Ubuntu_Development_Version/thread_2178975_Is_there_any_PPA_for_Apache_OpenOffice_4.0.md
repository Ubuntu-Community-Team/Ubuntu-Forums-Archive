---
title: "Is there any PPA for Apache OpenOffice 4.0?"
date: 2013-10-06
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-10-06
Is there any PPA for Apache OpenOffice 4.0?

---

### Post by VinDSL on 2013-10-06
AFAIK, you'll need to download the deb from [the official Apache OpenOffice web page]("http://www.openoffice.org/download/other.html#aoo"), and manually install it.

Dittos for [Kingsoft Office]("http://wps-community.org/download.html") (although you didn't ask :) ).

---

### Post by NikTh on 2013-10-06
> **VinDSL said:**
> AFAIK, you'll need to download the deb from [the official Apache OpenOffice web page]("http://www.openoffice.org/download/other.html#aoo"), and manually install it.

Also it would be a good idea to **remove completely** LibreOffice before the installation of openoffice.org.

---

### Post by VinDSL on 2013-10-06
> **NikTh said:**
> Also it would be a good idea to **remove completely** LibreOffice before the installation of openoffice.org.
True that...  ;)

---

### Post by ping-wu on 2013-10-06
Our experience is , with some tweaks, yes, we can make Apache OpenOffice co-exist with LibreOffice &#65288;of course one will be made ostensibly dormant).

I had all but abandoned OpenOffice (in favor of LibreOffice) until I started playing with UbuntuKylin.  The Chinese translation of LibreOffice is largely incomplete--to the extent that it is almost laughable.  Also when running in the Chinese locale (even with the base Ubuntu), LibreOffice's performance often sucks.

In comparison, the Chinese translation of Apache OpenOffice is professional done, and without any performance glitch.  (Apache OpenOffice has more than a dozen Beijing-based developers from IBM and CS2C, that's maybe the reason.)  We have switched all our machines to Apache OpenOffice even in our daily en_US locale.

---

### Post by richardsdma on 2013-10-07
there is no PPA for apache open office. but the install prosecc is quite simple: 
remove  completly libreoffice (i dont know how)
download tha proper debs archive from their website.
right click on the archive and choose "extract here" ....you will see a folder named en_us (if i recall right) 
in that folder you have a lot of debs and a folder with only one deb for desktop integration.
now, you first need to install that "many debs".....you can do this one by one but it is a lot of work. 
instead, open the terminal and go to en_us folder by typing "cd" and drag the "en-us" folder into terminal.....then hit enter.
then type: 
sudo dpkg -i *.deb

this command will install all debs from that folder. 

and the last operation is to install the "desktop integration" folder and to install that only one deb by right click, open with USC and install. 

the same precedure you can do also for upgrade apache openoffice.

---

