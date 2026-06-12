---
title: "Getting Gnome-fallback"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by haresear on 2012-04-24
I wanted to experiment with gnome-fallback on Precise (my older nVidia card won't run Unity 3D,and 2D is too slow). The current Precise ISO crashes during the install, but I've managed to get the current Lubuntu 12.04 installed. So I thought I would try to install gnome-fallback over Lubuntu, but I see that it pulls in just about everything in Ubuntu, including all the Unity stuff. Is there any other better option for trying gnome-fallback that I could consider?

---

### Post by newbie-user on 2012-04-24
It pulls a lot of stuff because you have to pull all of the Gnome stuff too. Since you installed Lubuntu, you have the LXDE environment instead of Gnome. If you want to use gnome-fallback, you have to have Gnome to begin with, otherwise there is no Gnome to fall back to.

---

### Post by haresear on 2012-04-24
The Gnome3 stuff I understand, but why things like Unity, Brasero, Evolution, Rhythmbox, UbuntuOne, etc?

---

### Post by newbie-user on 2012-04-24
It's probably trying to pull the ubuntu-desktop metapackage as well and that points to all that extra stuff.

---

### Post by 3rdalbum on 2012-04-24
> **haresear said:**
> The Gnome3 stuff I understand, but why things like Unity, Brasero, Evolution, Rhythmbox, UbuntuOne, etc?

Gnome includes Nautilus, and Nautilus has links to Brasero, Evolution, Rhythmbox and Ubuntu One to provide integration. Most of those programs also require at least a few Unity packages to provide integration with Unity's launcher emblems.

So yeah, that's why it's trying to install those extra components.

You may be able to get by with running:

```
sudo apt-get install gnome-session-fallback --no-recommends
```

which will install hard dependencies but NOT "recommended" packages. I'm not sure if Unity, Brasero et al are dependencies or merely recommended packages.

---

### Post by keithpeter on 2012-04-25
> **3rdalbum said:**
> 
You may be able to get by with running:

```
sudo apt-get install gnome-session-fallback --no-recommends
```


Hello 3rdalbum and all

I might try that as well on top of an XFCE install.

I might try adding nautilus in as well as it is the file manager that integrates best with gnome-panel.

---

### Post by megabuffen on 2012-04-25
Is there an alternate installer for Precise? If so, I would try it. After installing it, you can get a text terminal and login there to install gnome-session-fallback, without ever having to run Unity.

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-25
I have had trouble in the past with installing a different DE on top of an existing one.  I would suggest simply installing the regular Ubuntu when it comes out tomorrow and then installing the fallback.
That is the least complicated.  Then just remove the stuff you don't like later (unity, overlay scrollbars or whatever)

---

### Post by kansasnoob on 2012-04-25
> **megabuffen said:**
> Is there an alternate installer for Precise? If so, I would try it. After installing it, you can get a text terminal and login there to install gnome-session-fallback, without ever having to run Unity.

Ermmm, yes ........ you can use an Alt CD, then press F4 and select CLI install, or you can use the netboot mini.iso and install only what you wish.

But I've had nothing but trouble trying to get a classic session working acceptably in Precise other than this:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

---

### Post by haresear on 2012-04-26
> **TREESofRIGHTEOUSNESS said:**
> I have had trouble in the past with installing a different DE on top of an existing one.  I would suggest simply installing the regular Ubuntu when it comes out tomorrow and then installing the fallback.
That is the least complicated.  Then just remove the stuff you don't like later (unity, overlay scrollbars or whatever)
For some reason, the Ubuntu and Lubuntu 12.04 live ISOs (release versions) both crash at the end of the install when trying to display the slide show. I also tried the alternate ISO, but it failed too during the "load components" step. The Lubuntu install gets far enough that I can complete it manually -- that is the only success I've had.

3rdalbum's suggestion looks interesting -- I might give that a try.
I may also try to upgrade my U11.10 install later after the post-release excitement dies down.

---

### Post by haresear on 2012-04-26
Just to follow up on 3rdalbum's suggestion, (the apt-get option is actually "--no-install-recommends") I tried installing gnome-session-fallback, nautilus, and a few other gnome-related things with the --no-install-recommends option. Unfortunately the Gnome Classic (no effects) desktop that results is not functional -- just a couple of empty panels that are unresponsive.

---

