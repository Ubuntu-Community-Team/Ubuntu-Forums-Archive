---
title: "Skype 1.1.0.13_API released"
date: 2005-05-25
forum: The Cafe
---

### Post by mtron on 2005-05-25
Skype released a new version of their popular VoIP software today. still qt  :-x  only.

grab the deb at [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)

$ sudo apt-get remove skype

cd to your download dir

$ sudo apt-get install  skype_1.1.0.13-1_i386.deb

[Change Log](http://www.skype.com/products/skype/linux/changelog.html)  (25.05.2005 Skype for Linux version 1.1.0.13)

---

### Post by pdk001 on 2005-05-25
thanks for latest skype information

---

### Post by FreeEagle on 2005-05-25
sudo apt-get install skype_1.1.0.13-1_i386.deb
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
E: Konnte Paket skype_1.1.0.13-1_i386.deb nicht finden


it does not work ..... i tried to install it , but now was, it shows this, 

E: could not find Paket skype_1.1.0.13-1_i386.deb

I loged as a Super User even and no way, and i am in the same Directory .... 


Help Please!!!!


FreeEagle

---

### Post by pdk001 on 2005-05-25
if that doesnt work, download the file here [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
and enter the following command " sudo dpkg -i skype_1.1.0.13-1_i386.deb " where is skype_1.1.0.13-1_i386.deb the file of the name you downloaded

---

### Post by clb137 on 2005-05-25
[QUOTE=FreeEagle]sudo apt-get install skype_1.1.0.13-1_i386.deb
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
E: Konnte Paket skype_1.1.0.13-1_i386.deb nicht finden


it does not work ..... i tried to install it , but now was, it shows this, 

E: could not find Paket skype_1.1.0.13-1_i386.deb

I loged as a Super User even and no way, and i am in the same Directory .... 


Help Please!!!!


FreeEagle[/QUOTE]


hi have you amended your /apt/sources.list with the required repos?????

---

### Post by ciprol on 2005-05-26
[QUOTE=pdk001]if that doesnt work, download the file here [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
and enter the following command " sudo dpkg -i skype_1.1.0.13-1_i386.deb " where is skype_1.1.0.13-1_i386.deb the file of the name you downloaded[/QUOTE]
Tried this and it responded with...
"Setting up skype (1.1.0.13) ..."
And then nothing more happens. I can now see Skype in the Applications menu with a generic rectangular icon. Clicking it makes no difference...

---

### Post by pdk001 on 2005-05-27
generic rectangular icon -> you need re-boot to show icon
and register an account at [www.skype.com](www.skype.com) if you aint yet

---

### Post by TheSavage on 2005-05-29
No need to reboot, just do a "killall gnome-panel" and that'll do the trick.

---

### Post by thechitowncubs on 2005-05-29
[QUOTE=mtron]Skype released a new version of their popular VoIP software today. still qt  :-x  only.

grab the deb at [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)

$ sudo apt-get remove skype

cd to your download dir

$ sudo apt-get install  skype_1.1.0.13-1_i386.deb

[Change Log](http://www.skype.com/products/skype/linux/changelog.html)  (25.05.2005 Skype for Linux version 1.1.0.13)[/QUOTE]
 no
you don't need to remove it
and you don't install local debs w/ apt
to install it type: sudo dpkg - <skype>.deb

---

