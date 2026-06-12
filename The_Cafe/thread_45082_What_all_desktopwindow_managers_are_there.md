---
title: "What all desktop/window managers are there?"
date: 2005-06-28
forum: The Cafe
---

### Post by CoriolisSTORM on 2005-06-28
Guys, I'm considering messing around with my Ubuntu here (since the winmodem still isnt working and everything.  I also have nothing important in my Ubuntu partition yet.)   Anyway, I'm looking at other desktop or window managers besides Gnome (what is it technically?) Right now the ones I know about are Gnome, KDE, Blackbox, and Fluxbox.  What others are there?  I also need another one separate from these because I'm going to do a minimal install on an old PC of mine, and try to use blackbox or something as the interface.  Which ones would you recommend?

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=CoriolisSTORM]Guys, I'm considering messing around with my Ubuntu here (since the winmodem still isnt working and everything.  I also have nothing important in my Ubuntu partition yet.)   Anyway, I'm looking at other desktop or window managers besides Gnome (what is it technically?) Right now the ones I know about are Gnome, KDE, Blackbox, and Fluxbox.  What others are there?  I also need another one separate from these because I'm going to do a minimal install on an old PC of mine, and try to use blackbox or something as the interface.  Which ones would you recommend?[/QUOTE]


I recommend XFCE. Its light but still looks good.

Look here:

[http://xwinman.org/](http://xwinman.org/)

---

### Post by papangul on 2005-06-29
My favourite is IceWM. It is more lightweight, fast and intuitive than xfce. It has a nice control panel also , but you may need to install that separately.

---

### Post by munkay on 2005-07-05
[QUOTE=CoriolisSTORM]Guys, I'm considering messing around with my Ubuntu here (since the winmodem still isnt working and everything.  I also have nothing important in my Ubuntu partition yet.)   Anyway, I'm looking at other desktop or window managers besides Gnome (what is it technically?) Right now the ones I know about are Gnome, KDE, Blackbox, and Fluxbox.  What others are there?  I also need another one separate from these because I'm going to do a minimal install on an old PC of mine, and try to use blackbox or something as the interface.  Which ones would you recommend?[/QUOTE]

There's a fork of Blackbox called Openbox [[http://www.openbox.org](http://www.openbox.org)] as well. It's very slow in development, but its really fast, and easy to configure using xml config files. Also supports keybindings and anti-aliased fonts standard. Check it out if you're in the market for something simple and fast.

---

### Post by knewbix on 2005-07-05
[Enlightenment](http://www.enlightenment.org/)  looked quite good when I tried it on another distro, but it still was a bit too buggy to use in my particular case.

---

### Post by papabean on 2005-07-05
[QUOTE=knewbix][Enlightenment]("http://www.enlightenment.org/")  looked quite good when I tried it on another distro, but it still was a bit too buggy to use in my particular case.[/QUOTE]

Depends on which version Enlightenment 16 is quite stable and fairly easy to configure.  Plus, it's gorgeous.

If you're looking for lightweight, but still pleasing to the eye, XFCE4 (as someone else also suggested) is a solid choice.

If you're not too concerned about graphical appearance, there's always the minimalist WMs: WMI & ratpoison.

Of course, there's always TWM, the default window manager.  It's ugly, but it's quick.

---

### Post by knewbix on 2005-07-05
[QUOTE=papabean]Depends on which version Enlightenment 16 is quite stable and fairly easy to configure.  Plus, it's gorgeous.[/QUOTE]

Thanks for the *enlightenment*, papabean. (bad pun intended!)

I am curious though, I am still quite new to this stuff so I got Enlightenment via *apt-get install enlightenment*. Is there a way to specify that I want Enlightenment 16 when I apt-get it? (I tried *apt-get install enlightenment16* but no joy) Thanks.

---

### Post by Stormy Eyes on 2005-07-05
[QUOTE=CoriolisSTORM]Anyway, I'm looking at other desktop or window managers besides Gnome (what is it technically?) Right now the ones I know about are Gnome, KDE, Blackbox, and Fluxbox.  What others are there?[/QUOTE]

Try Openbox. You can use it for a minimal install. Just refer to the HOWTO link in my signature.

---

### Post by papabean on 2005-07-05
[QUOTE=knewbix]Thanks for the *enlightenment*, papabean. (bad pun intended!)

I am curious though, I am still quite new to this stuff so I got Enlightenment via *apt-get install enlightenment*. Is there a way to specify that I want Enlightenment 16 when I apt-get it? (I tried *apt-get install enlightenment16* but no joy) Thanks.[/QUOTE]

Right now, Enlightenment 17 is still alpha-quality and isn't in the main distribution.  In order to get that, you'd have to follow one of the howto's in the forum.  If you got enlightenment from the main repositories, you've got E 16.

---

### Post by Big Venus on 2005-07-05
[QUOTE=knewbix][Enlightenment](http://www.enlightenment.org/)  looked quite good when I tried it on another distro, but it still was a bit too buggy to use in my particular case.[/QUOTE]
Agreed and if I hadn't been such a GNOME advocate, I use it as my primary desktop manager...

---

### Post by Sye d'Burns on 2005-07-05
[QUOTE=poofyhairguy]I recommend XFCE. Its light but still looks good.[/QUOTE]

I second XFCE. I originally installed it on this box to free up ram while running vmware. It's just so perky I can't stop using it.

---

### Post by crashtest on 2005-07-05
What?  No votes for FVWM2?

---

### Post by Big Venus on 2005-07-05
Sorry but FVWM2 I never tried and until now I never even heard of...

---

### Post by crashtest on 2005-07-05
[QUOTE=Big Venus]Sorry but FVWM2 I never tried and until now I never even heard of...[/QUOTE]

It's an older window manager.  Lightweight, fast, and invinitely configurable

---

### Post by ]Nbx*cmD[ on 2006-02-09
I vote for ratpoison.

---

### Post by bonzodog on 2006-02-09
Don't forget about WindowMaker *(sudo apt-get install wmaker)*. WindowMaker is a NextStep derivative desktop with right click dynamic menu's. In my opinion it is one of the better ones out there. If you want Xfce4, which is also highly recommended, do:
```
sudo apt-get install xubuntu-desktop
```

Xfce is becoming so popular as a lighter desktop that it now has it's own ubuntu flavour called xubuntu, which hopefully will be available as a CD ISO image on the release of dapper.

---

### Post by fuscia on 2006-02-09
knock yourself out - [http://www.plig.org/xwinman/](http://www.plig.org/xwinman/)  lots of descriptions and links, etc.

---

### Post by xequence on 2006-02-09
I probably wont understand why you people seem to think XFCE is light! It is a bit lighter then gnome, and alot faster switching themes, but when you get some programs opened up it goes slower.

---

### Post by Stormy Eyes on 2006-02-09
[QUOTE=munkay]There's a fork of Blackbox called Openbox [[http://www.openbox.org](http://www.openbox.org)] as well. It's very slow in development, but its really fast, and easy to configure using xml config files. Also supports keybindings and anti-aliased fonts standard. Check it out if you're in the market for something simple and fast.[/QUOTE]

Development on Openbox is slow because it's pretty much done. Most of the mailing list traffic I see is either questions from newbies, theme announcements, or feature requests. It's a bitchin' good window manager; I use it myself and helped test it when version 3.0 was still in early development. I might try other WMs, but I always come back to Openbox.

---

