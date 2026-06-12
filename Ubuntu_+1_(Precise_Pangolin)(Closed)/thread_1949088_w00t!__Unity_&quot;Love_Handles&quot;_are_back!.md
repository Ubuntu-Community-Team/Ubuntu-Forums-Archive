---
title: "w00t!  Unity &quot;Love Handles&quot; are back!"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2012-03-29
Last night's upgrades blitzed all of my custom Unity Plugin settings. 

Okay, fine!  That's the bad part...

The good part is, when I went to CCSM, to reconstruct my desktop, I noticed that the "Love Handles" are back. 


[INDENT][IMG]http://vindsl.com/images/unity-love-handles-29-mar-2012.png[/IMG][/INDENT]


Yeah, devs!  

Thank you!!!  ):P

---

### Post by Torgas Prim on 2012-03-29
What is "love handles"?

---

### Post by neu5eeCh on 2012-03-29
No love handles for me... :( I still can't load Unity 3D. That last compiz update _seriously_ sank my battleship. 

I keep switching over to Gnome Shell but, gawd, I can't stand Gnome Shell without a slew of extensions (still unavailable for the latest version). It's really unusable. I _just don't get_ how anyone can use Gnome Shell in its generic form. Not to get too far off-topic, but if all their extensions are going to be unusable after every little update, this is going to be a problem.

---

### Post by cottfcfan on 2012-03-29
Compiz screwed a few people generally all you have to do is drop to a console CTRL+ALT+F2 - login in - then:
```
gconftool-2 --recursive-unset /apps/compiz-1
```
```
gconftool-2 --recursive-unset /apps/compizconfig-1
```
You should be able to login again now.

---

### Post by effenberg0x0 on 2012-03-29
> **VinDSL said:**
> 
...
I noticed that the "Love Handles" are back. 
...

> **Torgas Prim said:**
> What is "love handles"?
Hey Vin,
Please don't post adult-oriented content in the Forums. 

LOL :) :) :)

Regards,
Effenberg

---

### Post by QIII on 2012-03-29
Oh, who cares about love handles?

What's that cool font you are using for temperature and time at the bottom of your conky? ;)

---

### Post by MG&amp;TL on 2012-03-29
Oh, the love handles are "unity mt grab handles" under CCSM. You can unset whatever it is that's starting them, or keep them if you prefer. Always been there AFAIK. Or am I missing the point?

Although I prefer the name "love handles" too. :P

---

### Post by VinDSL on 2012-03-29
> **QIII said:**
> Oh, who cares about love handles?
I used it all the time, but they did away with it, for a long while.  I missed 'em like sin!

I run a lot of borderless windows, so there is no way to grab them with a mouse.  Alt-F8 sorta worked, but mostly didn't.

Anyway, I'm overjoyed they're back!  ;)

> **QIII said:**
> What's that cool font you are using for temperature and time at the bottom of your conky? ;)
That's called, "Radio Space" (by Iconian Fonts).

I get most of my fonts from Dafont.

LINKAGE:  [http://www.dafont.com/radio-space.font?text=VinDSL&psize=l](http://www.dafont.com/radio-space.font?text=VinDSL&psize=l)

---

### Post by QIII on 2012-03-29
I was cracking wise about the handles, I hope you inderstand!  :D

---

### Post by VinDSL on 2012-03-29
> **effenberg0x0 said:**
> Hey Vin,
Please don't post adult-oriented content in the Forums. 

LOL :) :) :)
Ironically, they are kinda sexy!  :)

---

### Post by VinDSL on 2012-03-31
Heh!

Took me 2 days to figure out how to go borderless on chromium, opera-next, and firefox.

I'm posting it, for the Google bots, before I forget it again...  :D

CCSM -> Window Decoration -> Decoration Windows

```
(any) & !(class=Chromium-browser) & !(class=OperaNext) & !(class=Firefox)
```

Adding it to Tomboy, too!  ;)

---

### Post by jeremy on 2012-04-02
Just to clarify, CCSM is Compiz Config Settings Manager, which can be installed from the repos:

~$ sudo apt-get install compizconfig-settings-manager

---

