---
title: "Lubuntu 15.04 has inside Zeitgeist Datahub.  For what?"
date: 2015-07-13
forum: Security
---

### Post by soto-valera on 2015-07-13
What`s the function of "*Zeitgeis*t Datahub " in Lubuntu 15.04?
What`s it for Zeitgeist Datahub?
What`s the benefit for the Lubuntu user if we don`t use Unity?
Why should I keep "Zeitgeist DataHub" on my Lubuntu system?

---

### Post by v3.xx on 2015-07-13
This question has been around for a while.

[https://www.google.com/search?client=ubuntu&channel=fs&q=remove+Zeitgeist&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=remove+Zeitgeist&ie=utf-8&oe=utf-8)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+Zeitgeist&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+Zeitgeist&sa=Search&cof=FORID:9)

---

### Post by vasa1 on 2015-07-13
> **soto-valera said:**
> What`s the function of "*Zeitgeis*t Datahub " in Lubuntu 15.04?
What`s it for Zeitgeist Datahub?
What`s the benefit for the Lubuntu user if we don`t use Unity?
Why should I keep "Zeitgeist DataHub" on my Lubuntu system?

Lubuntu 14.04 doesn't have it. I didn't know it's now in 15.04. Still, I doubt that it's part of Lubuntu 15.04. Are you sure you haven't installed some package that pulled it in?

---

### Post by howefield on 2015-07-13
> **vasa1 said:**
> Lubuntu 14.04 doesn't have it. I didn't know it's now in 15.04.

Neither does 15.04.

---

### Post by v3.xx on 2015-07-13
Not in Mate either.  Must be a ubuntu-desktop depends.

---

### Post by deadflowr on 2015-07-13
> **vasa1 said:**
> Lubuntu 14.04 doesn't have it. I didn't know it's now in 15.04. Still, I doubt that it's part of Lubuntu 15.04. **Are you sure you haven't installed some package that pulled it in?**
Perhaps gedit-plugins.(?)...

---

### Post by vasa1 on 2015-07-13
Check out [http://cdimage.ubuntu.com/lubuntu/releases/15.04/release/lubuntu-15.04-desktop-amd64.manifest](http://cdimage.ubuntu.com/lubuntu/releases/15.04/release/lubuntu-15.04-desktop-amd64.manifest)

Seems more likely you've installed something which pulled in zeitgeist-related stuff. Gedit?

Getting ninja'ed too often :(

---

### Post by v3.xx on 2015-07-13
Lets see what you have installed.  I think this will work in Lu..
```
ls /usr/share/applications
```

---

### Post by vasa1 on 2015-07-13
> **deadflowr said:**
> Perhaps gedit-plugins.(?)...
That's most probably via gedit:```
10:42 PM ~ $ apt-cache rdepends zeitgeist-datahub
zeitgeist-datahub
Reverse Depends:
  zeitgeist-datahub:i386
  zeitgeist-core
  zeitgeist
  zeitgeist-datahub:i386
  **gedit-plugins**
  zeitgeist-core
  zeitgeist
10:42 PM ~ $ 

```and part of *apt-get install -s gedit* shows```
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 gnome-user-guide
  libgtksourceview-3.0-1 libgtksourceview-3.0-common libpeas-1.0-0
  libpeas-common libpython3.4 libyelp0 lib**zeitgeist**-2.0-0 python-gi-cairo
  python-**zeitgeist** yelp yelp-xsl **zeitgeist** **zeitgeist**-core **zeitgeist**-datahub

```

---

