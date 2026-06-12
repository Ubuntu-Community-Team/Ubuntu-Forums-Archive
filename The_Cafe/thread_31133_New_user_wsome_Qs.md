---
title: "New user w/some Qs"
date: 2005-05-02
forum: The Cafe
---

### Post by sprucio on 2005-05-02
Hi guys,

I have heard such great things about Ubuntu, I decided to try it out. Before I decide to rid of Debian, I had some questions that I need some answers to.

1. Since Ubuntu focuses in on GNOME and Kubuntu on KDE, does this mean that I won't be able to install KDE apps on Ubuntu and GNOME apps on Kubuntu? A classic example would be adding kmail on a GNOME desktop. I wish to be able to do this without adding an external source to /etc/apt/sources.list. When I've done this in the past, I've had a number of broken dependency issues in Debian.

2. How is upgrading in Ubuntu? One of the reasons why I like Debian is that I can just run a apt-get dist-upgrade and it'll upgrade. I do not wish to do a major upgrade like FC.

3. Does anyone know where the "Luxi Sans" fonts are packaged?

4. How large is Ubuntu's software selection? As you all know, I believe Debian really  is the king when it comes to this topic.

---

### Post by 23meg on 2005-05-02
> 1. Since Ubuntu focuses in on GNOME and Kubuntu on KDE, does this mean that I won't be able to install KDE apps on Ubuntu and GNOME apps on Kubuntu? A classic example would be adding kmail on a GNOME desktop. I wish to be able to do this without adding an external source to /etc/apt/sources.list. When I've done this in the past, I've had a number of broken dependency issues in Debian. 

no, you can install kde apps in gnome, and vica versa. whenever you try to install one via synaptic it will automatically add the kde base libraries and other needed ones for the app you're installing. chances are things will be smoother than in debian. i've done it for a few kde apps without problems, but later i found equivalent or better gtk2 apps, so i got rid of them. i suggest you look around at gnomefiles.org and gnome-apps.org for native gnome apps before "surrendering" to kde counterparts :)

> 2. How is upgrading in Ubuntu? One of the reasons why I like Debian is that I can just run a apt-get dist-upgrade and it'll upgrade. I do not wish to do a major upgrade like FC.

it's the same as in debian. you won't have any problems there.

> 3. Does anyone know where the "Luxi Sans" fonts are packaged?

sorry, can't help you there.

> 4. How large is Ubuntu's software selection? As you all know, I believe Debian really  is the king when it comes to this topic.

16000+ packages. and you can install packages from the debian repositories as well.

---

### Post by SamH on 2005-05-02
I can answer your first point.  You can add KDE apps, or pretty much all of KDE, without adding a bunch of other sources.  Look in synaptic and you can see that KDE is there.  You can also add XFCE if you like.

I haven't added all of KDE, but have added K3B for CD/DVD burining.  It works great.  I also tried adding JuK, but it doesn't function quite right.  I am satisfied enough with XMMS that I haven't worked on fixing it.

Hope this helps.

---

### Post by TravisNewman on 2005-05-02
Moving from Tips&Tricks, as this is neither Tip nor Trick ;)

---

### Post by poofyhairguy on 2005-05-02
[QUOTE=sprucio]
3. Does anyone know where the "Luxi Sans" fonts are packaged?
[/QUOTE]

[http://www.ubuntulinux.org/wiki/BeautifyKoreanFonts](http://www.ubuntulinux.org/wiki/BeautifyKoreanFonts)

---

### Post by hashimoto on 2005-05-02
2: Ubuntu is based on Debian and uses apt-get, so dist-upgrade is available, too. I've updated my system from Warty to Hoary with it. AFAIK, you can even update Debian to Ubuntu with apt-get.

---

### Post by sprucio on 2005-05-02
Sorry about putting this post in the wrong section. It won't happen again.

Thanks for all the input.

poofyhairguy,

That links to how you get Korean ttf fonts. Am I missing something here?

---

### Post by poofyhairguy on 2005-05-02
[QUOTE=sprucio]
poofyhairguy,

That links to how you get Korean ttf fonts. Am I missing something here?[/QUOTE]

LOL. Sorry, it was the only page in the wiki that mentioned that font. Since I have never seen it, I assumed it was a korean font. my bad...

---

