---
title: "Question about Yakuake"
date: 2008-09-30
forum: The Cafe
---

### Post by bash on 2008-09-30
I read in another thread here on the forum (Link) about lots of different Terminals. Got especially in the pulldown game-style Terminals. Found so far Tilda and Yakuake.

Tried Tilda but I am not completely happy with it. Now I wanted to give Yakuake a try but I noticed it depends on about 100 MB of KDE libraries (using GNOME as my DE). Now I am wondering if anybody knows if there exists a "reduced" version that only builds against a few KDE/Qt core libraries like for example Skype or Virtualbox do. 

Or if that doesn't exist are there any other fancy pulldown style terminals?

---

### Post by barbedsaber on 2008-09-30
I often use a pull up terminal, in whichever dock I am using. There should be an applet for AWN and cairo (havn't tried any others, shame on me) I think you can set a command to bring it up. What was wrong with tilda again?

---

### Post by meho_r on 2008-09-30
> **bash said:**
> I read in another thread here on the forum (Link) about lots of different Terminals. Got especially in the pulldown game-style Terminals. Found so far Tilda and Yakuake.

Tried Tilda but I am not completely happy with it. Now I wanted to give Yakuake a try but I noticed it depends on about 100 MB of KDE libraries (using GNOME as my DE). Now I am wondering if anybody knows if there exists a "reduced" version that only builds against a few KDE/Qt core libraries like for example Skype or Virtualbox do. 

Or if that doesn't exist are there any other fancy pulldown style terminals?

I don't know if there is "reduced" version, but alterantively you may try [this]("http://guake-terminal.org/") one. Although, I personally prefer yakuake even with Gnome.

---

### Post by binbash on 2008-09-30
guake is the best for gnome ;)

---

### Post by bash on 2008-09-30
> **meho_r said:**
> I don't know if there is "reduced" version, but alterantively you may try [this]("http://guake-terminal.org/") one. Although, I personally prefer yakuake even with Gnome.

> **binbash said:**
> guake is the best for gnome ;)

Thanks for the replies. Just found Guake myself as well as I googled for "Tilda GTK". Quite happy with it and would recommend it any day over Tilda.

---

### Post by Flynn555 on 2008-09-30
yeah i used yakuake quite often with pclinuxOS but not much with ubuntu.

edit: oh cool im gonna have to try Guake.  its like the same thing for gnome :)

---

### Post by meho_r on 2008-09-30
Well, I prefer Yakuake because of
1. using less resources (Yakuake 5MB, Guake ~35MB)
2. much space for customizing
3. support for multiple screens (horizontal and vertical split screen -- something like Terminator Gnome Terminal)

However, if you've decided to use Guake, keep in mind one thing: if you try to change hotkeys you'll have to turn off NumLock to get proper key (i.e. if you try to set F9 key for Toggle terminal visibility and you haven't turn NumLock off you'll get Mod2+F9 and key wouldn't work). So, don't forget turning NumLock off ;)

---

### Post by barbedsaber on 2008-09-30
everyone else here has a tux avatar, I feel so, different.

---

### Post by bash on 2008-09-30
> **meho_r said:**
> Well, I prefer Yakuake because of
1. using less resources (Yakuake 5MB, Guake ~35MB)
2. much space for customizing
3. support for multiple screens (horizontal and vertical split screen -- something like Terminator Gnome Terminal)

However, if you've decided to use Guake, keep in mind one thing: if you try to change hotkeys you'll have to turn off NumLock to get proper key (i.e. if you try to set F9 key for Toggle terminal visibility and you haven't turn NumLock off you'll get Mod2+F9 and key wouldn't work). So, don't forget turning NumLock off ;)

From what I have seen from the screenshots it does seem to be more fancy. But the fact that I have to install what seems like half the KDE desktop just to get one program working makes it a no-go for me. If at some point I decide to switch to KDE I'll definitly give it a try. 

But for now Guake does everything I need. And compared to Tilda, it lets you configure more keys and just seems "rounder".

---

### Post by meho_r on 2008-09-30
Of course, it's your call ;) I installed some other KDE apps so I already had those 100 MB and more additional libraries/apps installed. If not, I'd use Guake too.

---

### Post by pelle.k on 2008-09-30
Stjerm FTW!
> *Stjerm is a quake-like terminal emulator. It's window is shown with a key shortcut. Stjerm is very minimalistic and works well with Compiz window manager.*
[http://www.getdeb.net/app/stjerm](http://www.getdeb.net/app/stjerm)

---

### Post by Flynn555 on 2008-09-30
i just remembered that i had the kde desktop already installed. so there would be no need not to use yakuake.

---

### Post by blink0 on 2009-02-18
Hey there!
Maybe this is not the place to post this, but here it goes:

anyone having troubles running yakuake? I just dust-upgraded to Ubuntu 8.10 (with gnome 2.24, apparently) and I can't run yakuake... I get the following error:

dgomes@heisenberg:~/guake-0.3.1$ yakuake
DCOP aborting (delayed) call from 'anonymous-10762' to 'yakuake'
dgomes@heisenberg:~/guake-0.3.1$ KCrash: Application 'yakuake' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

I saw somewhere here on the forums you should run kdeinit before, so I did it, but it's the same. I think I even have the kdebase package, so what could be the problem here? :S
Trying to install that drkonqi package yields:

Package drkonqi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdebase-runtime-data

And kdebase-runtime-data "is already the newest versio"...

Any ideas? Thanks in advance!

---

