---
title: "Aptitude GUI???"
date: 2006-06-18
forum: The Cafe
---

### Post by user1397 on 2006-06-18
I was wondering something about the aptitude GUI.  first of all, aptitude is supposed to be better than apt-get for everything pretty much, so shouldn't there be a synaptic-like package management GUI for aptitude?  if there's only the text-mode aptitude gui (the one you find when typing in the terminal```
sudo aptitude
```) , I fear that it'll never be adopted by users, and everyone will just keep on going, using apt-get mindlessly.

---

### Post by weasel fierce on 2006-06-18
what does aptitude do better than apt-get ?

---

### Post by xXx 0wn3d xXx on 2006-06-18
[QUOTE=weasel fierce]what does aptitude do better than apt-get ?[/QUOTE]
It keeps track of dependencies so if you would install kde and didn't like it, aptitude would remove the entire thing including all the packages you installed along with installing kde. Apt-get would just remove the meta-package.

---

### Post by weasel fierce on 2006-06-18
ah, very handy

---

### Post by user1397 on 2006-06-18
[quote=weasel fierce]what does aptitude do better than apt-get ?[/quote]it remembers all dependencies for a program.  The best example of using aptitude, would be this situation:  You installed ubuntu (gnome) but you would like to give the KDE desktop environment a try.  So you install kde with this command ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
``` and as you can see, a lot of packages are included with the kubuntu-desktop package (which is a metapackage, a pointer of dependencies) Later, you figure out you hate kde, so you decide to uninstall it.  So you do ```
sudo apt-get update && sudo apt-get remove kubuntu-desktop
``` Then you realize, only the kubuntu-desktop metapackage is uninstalled, and all of the other stuff that got installed with it is still there!!!  Now, if you simply did ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` followed by ```
sudo aptitude update && sudo aptitude remove kubuntu-desktop
``` all the installed packages would be removed, not only the metapackage.

---

### Post by Jucato on 2006-06-18
Unfortunately, there's no full GUI for Aptitude available. it seems that all GUIs prefer to use apt-get. I'm waiting for the SMART Package Manager to see if it really delivers on its promises. If it does, it might be a good alternative to aptitude.

BTW, just in case some people don't know it yet, but you can use the mouse to point and click in Aptitude, when you launch it inside a terminal (GNOME-terminal or Konsole or Xterm).

---

### Post by user1397 on 2006-06-18
[quote=Fenyx]Unfortunately, there's no full GUI for Aptitude available. it seems that all GUIs prefer to use apt-get. I'm waiting for the SMART Package Manager to see if it really delivers on its promises. If it does, it might be a good alternative to aptitude.[/quote]whats so different about the smart PM? what does it use, apt-get or aptitude or something else?

---

### Post by xXx 0wn3d xXx on 2006-06-18
[QUOTE=erik1397]whats so different about the smart PM? what does it use, apt-get or aptitude or something else?[/QUOTE]
It's very easy to use and it handles dependencies very well.

---

### Post by user1397 on 2006-06-18
[quote=xXx 0wn3d xXx]It's very easy to use and it handles dependencies very well.[/quote]cool! so what exactly does it use for package management? or is it its own PM?

---

### Post by Jucato on 2006-06-18
For reference: [http://labix.org/smart](http://labix.org/smart) and [http://labix.org/smart/faq](http://labix.org/smart/faq)

AFAIK, it's a package manager that can handle deb and rpm (and also tgz?), some sort of like a super apt+urpmi+yum, etc

---

### Post by rattaro on 2006-06-19
Does SMART also track dependencies like Aptitude, and remove them when no longer needed?  It's not clear from the web site.

---

### Post by Narpa on 2008-06-09
> **ubuntuman001 said:**
> I was wondering something about the aptitude GUI.  first of all, aptitude is supposed to be better than apt-get for everything pretty much, so shouldn't there be a synaptic-like package management GUI for aptitude?  if there's only the text-mode aptitude gui (the one you find when typing in the terminal

I know this thread is over two years old, but its the only relevant one I can find.

There appears to be a Google Summer of Code 2008 project called Aptitude-gtk addressing just this issue, it does not look ready for prime time yet and I haven't even bothered to try it out, but it'll be interesting to see how it develops.

See here for more details:
[http://wiki.debian.org/SummerOfCode2008/Aptitude-gtk]("http://wiki.debian.org/SummerOfCode2008/Aptitude-gtk")

---

### Post by L_V on 2008-07-29
[_shaman_](http://boom1992.wordpress.com/2008/04/16/shaman-in-beta-quality/) is a candidate.

---

### Post by user1397 on 2008-07-30
haha love how this thread keeps going!

keep up the news guys :)

---

### Post by cariboo on 2008-07-30
Hasn't anybody here tried:

```
aptitude -v
```

The will give you an ncurses interface.

Jim

---

### Post by myusername on 2008-07-30
anyone notice how the smart pm is also developing for os x? how does that work??

---

### Post by Mateo on 2008-07-30
> **ubuntuman001 said:**
> it remembers all dependencies for a program.  The best example of using aptitude, would be this situation:  You installed ubuntu (gnome) but you would like to give the KDE desktop environment a try.  So you install kde with this command ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
``` and as you can see, a lot of packages are included with the kubuntu-desktop package (which is a metapackage, a pointer of dependencies) Later, you figure out you hate kde, so you decide to uninstall it.  So you do ```
sudo apt-get update && sudo apt-get remove kubuntu-desktop
``` Then you realize, only the kubuntu-desktop metapackage is uninstalled, and all of the other stuff that got installed with it is still there!!!  Now, if you simply did ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` followed by ```
sudo aptitude update && sudo aptitude remove kubuntu-desktop
``` all the installed packages would be removed, not only the metapackage.

Doesn't 'apt-get autoremove' do the same thing?

---

### Post by voteforpedro36 on 2008-07-30
> **Mateo said:**
> Doesn't 'apt-get autoremove' do the same thing?

Yes, exactly what I was thinking.

---

### Post by visionaire on 2008-07-31
the PM in kubuntu i guess is an Aptitude GUI?

I'm not sure 'cause i change to gnome a few moth ago, anyway I'm downloading the kubuntu-kde4-desktop (KDE 4.1) just now :lolflag:

EDIT: well i just google and adept is only an apt-get gui after all =)

---

### Post by user1397 on 2008-08-02
> **Mateo said:**
> Doesn't 'apt-get autoremove' do the same thing?

> **voteforpedro36 said:**
> Yes, exactly what I was thinking.actually, I'm not quite sure.  they may do similar things, but I don't think apt-get autoremove does entirely the same thing as aptitude remove does.

Anyone with more experience on the subject have more input on this?

---

### Post by doorknob60 on 2008-08-02
> **Mateo said:**
> Doesn't 'apt-get autoremove' do the same thing?

Sometimes it would do the trick, but in the case of Kubuntu, it wouldn't work.

---

### Post by Mateo on 2008-08-02
how so?

---

### Post by Polygon on 2008-08-02
this thread is two years old. programs change

it used to be before that apt-get didnt remove programs that wernt in use, now it will bug you saying that some programs were automatically installed but are not needed anymore, and will ask you to run apt-get autoremove to remove them.

and as kubuntu still has the terminal, it would do the same thing

---

### Post by LaRoza on 2008-08-02
[img]http://www.imageviper.com/displayimage/116046/0/necromancing.jpg[/img]

---

