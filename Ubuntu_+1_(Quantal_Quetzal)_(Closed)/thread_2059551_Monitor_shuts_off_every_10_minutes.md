---
title: "Monitor shuts off every 10 minutes"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by floydsp on 2012-09-18
In both ubuntu 12.10 & also Gnoubuntu remix the monitor will shut off when playing a movie both in totem & VLC. I have it set to never shut down, any help please

floydsp

---

### Post by jfernyhough on 2012-09-18
This is a GNOME3 "feature".

There are two potential ways of solving this. The first is to edit the idle timeout in dconf (though this sometimes doesn't always work, and it also means your IM status will never set to "away").

The easiest is to install Caffeine then use "Caffeine Preferences" to add Totem, VLC, XBMC, etc... to the list of applications Caffeine will keep the screen active for.

---

### Post by reptilez on 2012-09-18
> **jfernyhough said:**
> This is a GNOME3 "feature".

There are two potential ways of solving this. The first is to edit the idle timeout in dconf (though this sometimes doesn't always work, and it also means your IM status will never set to "away").

The easiest is to install Caffeine then use "Caffeine Preferences" to add Totem, VLC, XBMC, etc... to the list of applications Caffeine will keep the screen active for.

I might just be dumb, but how would one go about installing caffeine on 12.10 ? 
First, I'm pretty new to Ubuntu. Looking at caffeine on launchpad, 12.04 is the latest, available Ubuntu-version ?

ANY light would be appreciated. :guitar:

---

### Post by cariboo on 2012-09-18
First off, if you are new to Ubuntu, you may be better off using 12.04.1, as Quantal is still in development, and although we are in a Feature freeze, there could still be problems that make it unusable.

To install caffeine, you need to add the ppa to your sources.list, to add the ppa, open a terminal and type:

```
sudo apt-add-repository ppa:caffeine-developers/ppa
```

Then you have go to System Settings -> Software Sources, and change the version of the ppa from quantal to precise.

Once you have done the above, in a terminal type:

```
sudo apt-get update
```

then

```
sudo apt-get install caffeine
```

---

### Post by reptilez on 2012-09-18
> **cariboo907 said:**
> First off, if you are new to Ubuntu, you may be better off using 12.04.1, as Quantal is still in development, and although we are in a Feature freeze, there could still be problems that make it unusable.

To install caffeine, you need to add the ppa to your sources.list, to add the ppa, open a terminal and type:

```
sudo apt-add-repository ppa:caffeine-developers/ppa
```

Then you have go to System Settings -> Software Sources, and change the version of the ppa from quantal to precise.

Once you have done the above, in a terminal type:

```
sudo apt-get update
```

then

```
sudo apt-get install caffeine
```

Yeah, I've been fooling around LTS. Both 10.04 (I love Gnome2), and 12.04. But I wan't to learn more! \\:D/
I even removed Windows from my main PC, because I fell in love with Ubuntu.

But anyways. Since I'm still learning all this new stuff, I touhgt that adding a ppa, it had to have a package for my 12.10. But guess not. :-D YAY :guitar:

Thank you for the light. ;-)

---

### Post by floydsp on 2012-09-18
> **cariboo907 said:**
> First off, if you are new to Ubuntu, you may be better off using 12.04.1, as Quantal is still in development, and although we are in a Feature freeze, there could still be problems that make it unusable.

To install caffeine, you need to add the ppa to your sources.list, to add the ppa, open a terminal and type:

```
sudo apt-add-repository ppa:caffeine-developers/ppa
```

Then you have go to System Settings -> Software Sources, and change the version of the ppa from quantal to precise.

Once you have done the above, in a terminal type:

```
sudo apt-get update
```

then

```
sudo apt-get install caffeine
```

Thanks that did the trick
floydsp

---

### Post by robtygart on 2012-09-18
Question? Will this help me too?

Mine does the same thing in 12.04 and the only way to stop it is to do ```
xset -dpms
```

---

### Post by VinDSL on 2012-09-18
> **robtygart said:**
> Question? Will this help me too?

Mine does the same thing in 12.04 and the only way to stop it is to do ```
xset -dpms
```
I use:

```
xset s off && xset dpms force on && xset -dpms
```

To check the status:

```
xset q | grep -A1 -i dpms
```

---

### Post by floydsp on 2012-09-19
Thanks for that VinDSL

---

