---
title: "According to this WINE picture...."
date: 2011-05-30
forum: Wine
---

### Post by TAspr on 2011-05-30
Where should I install the libraries?

---

### Post by webofunni on 2011-05-30
What exactly is this ? I saw this in another thread opened by you. Which program/command resulted in this window ?

---

### Post by TAspr on 2011-06-02
This is the screen that comes up in Wine when trying to configure the "libs."
Any idea?

---

### Post by iansane on 2011-06-02
actually that's q4wine which apparently adds a bunch of funcionality to it or makes available functionality I didn't know existed. I just installed wine1.3 then q4wine which removed wine1.3 and installed wine1.0 and when lookin in system tools I now have q4wine which brought up that first time use wizard in your picture. 

edit:

The libs are in /usr/lib/wine. On my system it's /usr/lib32/wine because it's a 64bit OS so which ever one of those two you have.

Here's a link on the setup that explains the libs
[http://q4wine.brezblock.org.ua/documentation/en_us/03-first-startup-wizard.html](http://q4wine.brezblock.org.ua/documentation/en_us/03-first-startup-wizard.html)

---

### Post by uRock on 2011-06-02
Moved to *Wine*.

---

### Post by cwwilson721 on 2011-06-02
> **iansane said:**
> [COLOR="Magenta"]actually that's q4wine which apparently adds a bunch of funcionality[/COLOR] to it or makes available functionality I didn't know existed. I just installed wine1.3 then [COLOR="Red"]q4wine which removed wine1.3 and installed wine1.0[/COLOR] and when lookin in system tools I now have q4wine which brought up that first time use wizard in your picture. 

edit:

The libs are in /usr/lib/wine. On my system it's /usr/lib32/wine because it's a 64bit OS so which ever one of those two you have.

Here's a link on the setup that explains the libs
[http://q4wine.brezblock.org.ua/documentation/en_us/03-first-startup-wizard.html](http://q4wine.brezblock.org.ua/documentation/en_us/03-first-startup-wizard.html)

Wow... That's "added" functionality? I would really hate to see "reduced"..Or maybe it would replace 1.3 with wine 2K (Not a real app).

THIS is one MAJOR reason I only use wine, no POL, q4wine, Crossover, etc.

***It ain't wine.***

If you want answers, find a q4wine forum, and ask the devs of this P.O.S. "addon" to wine that trashes it.

To me, it's like buying a Ferrarri, then putting a Briggs and Stratton lawnmower engine in it, then going to Ferrari and asking why it goes so slow.

---

### Post by TAspr on 2011-06-02
> **cwwilson721 said:**
> Wow... That's "added" functionality? I would really hate to see "reduced"..Or maybe it would replace 1.3 with wine 2K (Not a real app).

THIS is one MAJOR reason I only use wine, no POL, q4wine, Crossover, etc.

***It ain't wine.***

If you want answers, find a q4wine forum, and ask the devs of this P.O.S. "addon" to wine that trashes it.

To me, it's like buying a Ferrarri, then putting a Briggs and Stratton lawnmower engine in it, then going to Ferrari and asking why it goes so slow.

Where in the world do do you get WINE?  Everytime I try to install it, it wants me to install it again, and again, and again.

---

### Post by cwwilson721 on 2011-06-02
Easy.

```
sudo apt-get wine
```
Or, for 1.3
```
sudo apt-get wine1.3
```

Then just run ```
winecfg
```and it creates your .wine directory, with Gecko.

---

### Post by TAspr on 2011-06-03
> **cwwilson721 said:**
> Easy.

```
sudo apt-get wine
```Or, for 1.3
```
sudo apt-get wine1.3
```Then just run ```
winecfg
```and it creates your .wine directory, with Gecko.

Is there a difference on using ***sudo apt-get install wine*** as compared to ***sudo apt-get wine*** as mentioned above?  Do you have to run the ***winecfg*** for either commands?  I would like to make sure of this before running the command.

Thanks

---

### Post by cwwilson721 on 2011-06-03
You are correct.
It IS ```
sudo apt-get install wine
``` or ```
sudo apt-get install wine1.3
```
And, yes, I would run ```
winecfg
```using either 1.2 or 1.3

That is the best way to insure the .wine folder has all the stuff needed, dll's, fake IE, a registry, the correct folders, etc.

---

### Post by TAspr on 2011-06-03
> **cwwilson721 said:**
> You are correct.
It IS ```
sudo apt-get install wine
``` or ```
sudo apt-get install wine1.3
```And, yes, I would run ```
winecfg
```using either 1.2 or 1.3

That is the best way to insure the .wine folder has all the stuff needed, dll's, fake IE, a registry, the correct folders, etc.

Why does it not show in the applications directory as an available application as in the picture?

---

### Post by cwwilson721 on 2011-06-03
Because it ISN'T one. It is designed to run from the cli (Command Line Interface).

Go to winehq.com, and read up on it.

Another good read is [this post here in the forum]("http://ubuntuforums.org/showthread.php?t=497332") (old, but valid enough)

---

### Post by TAspr on 2011-06-03
> **cwwilson721 said:**
> Because it ISN'T one. It is designed to run from the cli (Command Line Interface).

Go to winehq.com, and read up on it.

Another good read is [this post here in the forum]("http://ubuntuforums.org/showthread.php?t=497332") (old, but valid enough)

I Will, thanks.

---

