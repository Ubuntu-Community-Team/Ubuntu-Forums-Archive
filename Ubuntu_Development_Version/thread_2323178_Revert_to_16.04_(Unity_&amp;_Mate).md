---
title: "Revert to 16.04 (Unity &amp; Mate)"
date: 2016-05-03
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-05-03
Is there any way to revert from Yakkety to Xenial?

---

### Post by howefield on 2016-05-03
Realistically.. only with a clean install.

---

### Post by izznogooood on 2016-05-03
Well, i guess I'll keep it until something happens. I tried to install Mate today :/

```
anders@lenox:~$ sudo apt install ubuntu-mate-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ubuntu-mate-desktop : Depends: libqt5libqgtk2 but it is not going to be installed
                       Depends: ubuntu-mate-core but it is not going to be installed
                       Depends: vlc but it is not going to be installed
                       Depends: xul-ext-gdata-provider but it is not going to be installed
                       Depends: xul-ext-lightning but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by rrnbtter on 2016-05-03
Greetings,
I've had no problem switching systems. But, I use a separate Home, Root and Boot partitions. With this setup I I load the desired install disk, Choose "Other" ,  reuse Home, reformat Root and also reuse Boot. But prior to the install I use a Puppy Linux disk to erase the contents of Boot. The installer seems to clean things up nicely.  I have used the same Home partition for years.

If you are installing on a single partition, then NO.

---

### Post by QDR06VV9 on 2016-05-03
> **izznogooood said:**
> Well, i guess I'll keep it until something happens. I tried to install Mate today :/

```
anders@lenox:~$ sudo apt install ubuntu-mate-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ubuntu-mate-desktop : Depends: libqt5libqgtk2 but it is not going to be installed
                       Depends: ubuntu-mate-core but it is not going to be installed
                       Depends: vlc but it is not going to be installed
                       Depends: xul-ext-gdata-provider but it is not going to be installed
                       Depends: xul-ext-lightning but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
See this recommended install mate: [http://wiki.mate-desktop.org/replace_unity_by_mate](http://wiki.mate-desktop.org/replace_unity_by_mate)

---

### Post by izznogooood on 2016-05-03
Thank you but I dont want to change to mate, i just want it as an option to experiment. I ca see the new mate has a "unity" layout option i wanted too try ;)

---

### Post by QDR06VV9 on 2016-05-03
That's why I posted the link...For myself Unity && Mate do not play nice with each other.

---

### Post by izznogooood on 2016-05-03
Oh, I had no idea. Are you saying I cant have my cake and eat it too? (Unity & Mate)

(Maybe forum admin can move this to somewhere we can continue this mate and unity discussion?)

---

### Post by howefield on 2016-05-03
You might need ubuntu-mate-core as well as ubuntu-mate-desktop for the full Mate experience.

Just tried it with this about to be burned partition of yakkety. Seems to work well enough although there is some "bleeding" from the Mate environment into the Unity environment, mainly theming stuff like scrollbars and colours.

---

