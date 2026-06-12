---
title: "Which restricted extras package should I install?"
date: 2013-06-21
forum: Ubuntu Studio
---

### Post by raydar on 2013-06-21
I've just done a fresh install of Ubuntu Studio 13.04 on an HP Pavillion dv7. In the subsequent process of installing all the little things for multimedia, I found three flavors of "restricted extras" package: Xubuntu Kubuntu, and Ubuntu. 

I usually use Synaptic, but this time I tried the Software Center and quickly saw more and more checkboxed package options as I went down that list (checking in Synaptic, I didn't see those; for the first time I found something about the Software Center rather useful). 

I'm tempted to want all the plugins and codecs I can get, which would argue in favor of ubuntu-restricted-extras. But Ubuntu Studio uses xfce like Xubuntu, right, so perhaps there's something particularly xfcey about xubuntu-restricted-extras. Then again maybe the Xubuntu flavor installs less in order for it to remain a more streamlined distribution. What is actually the case?

---

### Post by 2F4U on 2013-06-22
This UbuntuStudion documentation suggests to install the ubuntu-restricted-extra package:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by cub on 2013-06-24
I checked the box about addons in the installation phase already and that made the ubuntu-restricted-addons to be installed. From what I have read it's some difference between in case they have any dependencies: [http://askubuntu.com/questions/248769/what-is-the-difference-between-ubuntu-kubuntu-xubuntu-and-lubuntu-restricted-e](http://askubuntu.com/questions/248769/what-is-the-difference-between-ubuntu-kubuntu-xubuntu-and-lubuntu-restricted-e)

In this case I suppose you could run with either xubuntu- or ubuntu-restricted.

---

### Post by raydar on 2013-06-25
2F4U, thank you for the link to [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation). It was an informative read; I'm glad I did. But it looks like that "Ubuntu Studio Preparation" page is sort of tangent to the Ubuntu Studio installation you get by throwing the DVD in and booting to install; it's more like how to configure straight Ubuntu to approximate Ubuntu Studio, or how to know what all distinguishes Ubuntu Studio from straight Ubuntu--here's what the intro says:
> You will find on this page what to do if you want to setup a multimedia production workstation with a standard Ubuntu installation (means without installing Ubuntu Studio).
If you prefer to install the packages with Synaptic, you can.
. . . .
First of all, you have of course to install Ubuntu. I386 or amd64 should be both fine.
. . . .
Unity desktop environment is now stable and it is possible to work with it for multimedia, even at very low latency. . . . This is why this howto will use vanilla Ubuntu as a base.
Of course, you are free to install the flavour of Ubuntu and the desktop environment of your choice. However, please think that all flavour and desktops are different and some tweaks may not work like in vanilla Ubuntu. 


Cub, you succeeded in finding what I did not: a thread mentioning pretty much the same question I had, albeit not in the Ubuntu Studio context. It talks mainly about media player dependencies that differ between straight Ubuntu and the other flavors, but I don't know that Ubuntu Studio's xfce-related dependencies differ from Ubuntu's in exactly the same way as Xubuntu's do, such that I should choose Xubuntu-related metapackages over Ubuntu-related ones. I wouldn't be surprised if Ubuntu Studio includes by default (in order to be fully outfitted for its purpose) many of the things Xubuntu leaves out by default (in order to be smaller or less resource hungry). 

Since a fresh Ubuntu Studio installation yields an xfce environment, but since I want every media capability straight Ubuntu would have, I'm tempted to install both the ubuntu-restricted-extras metapackage *and* the xubuntu-restricted-extras one, if it will let me--or, if it won't, to install one and then the other, if the actual packages installed by the first metapackage will remain even after installing the second metapackage causes the first metapackage to be removed.  Does that sound rational?

---

### Post by cub on 2013-06-25
When comparing the two [http://packages.ubuntu.com/raring/ubuntu-restricted-extras](http://packages.ubuntu.com/raring/ubuntu-restricted-extras) and [http://packages.ubuntu.com/raring/xubuntu-restricted-extras](http://packages.ubuntu.com/raring/xubuntu-restricted-extras) I can't see much difference or that one includes more formats than the other. Then again, I could miss some detail.

I would be surprised if the ubuntu and xubuntu packages would remove each other, but it's easy to find out by just installing them as you suggested. (I would try it myself but I'm cheating on an Debian Xfce laptop at the moment..;) )

---

### Post by raydar on 2013-06-25
Yes, in fact when I looked at those pages you linked to, I had to drill down into the ___-restricted-addons package, itself a metapackage that gets installed by the ___-restricted-extras metapackage, before I found anything different between the Xubuntu and straight Ubuntu restricted extras. What I found is that all the packages "contained by" the metapackages are identical except the Xubuntu flavored one lacks two packages the straight Ubuntu flavored one has, namely:

> gstreamer1.0-plugins-bad
    GStreamer plugins from the "bad" set 

gstreamer1.0-plugins-ugly
    GStreamer plugins from the "ugly" set 


Now maybe there's a finer level of detail I'm missing, but after seeing this, I don't see any reason to bother with xubuntu-restricted-extras; I could install it and then install those other two GStreamer plugin packages, but it'd be easier to just install ubuntu-restricted-extras and call it good. It wasn't terribly easy getting to this conclusion, but I think that's what I'll do. Thank you for your help, Cub!

---

### Post by cub on 2013-06-26
Yeah, I also wondered about those two packages and how they differ from:
> gstreamer0.10-plugins-bad
GStreamer plugins from the "bad" set

gstreamer0.10-plugins-ugly
GStreamer plugins from the "ugly" set
except for the obvious 0.10 vs 1.0.

---

### Post by raydar on 2013-06-26
No, actually, both xubuntu-restricted-extras and ubuntu-restricted-extras (by way of the ___-restricted-addons metapackages they "contain") have the 0.10 packages (see attached screenshot). The Xubuntu flavored one doesn't have the 1.10 packages, but the straight Ubuntu flavored one does.

But I did goof by stating that the Ubuntu one has only two GStreamer 1.10 packages that the Xubuntu one lacks; there are three:
> gstreamer1.0-libav
    FFmpeg plugin for GStreamer 

gstreamer1.0-plugins-bad
    GStreamer plugins from the "bad" set 

gstreamer1.0-plugins-ugly
    GStreamer plugins from the "ugly" set 


---

