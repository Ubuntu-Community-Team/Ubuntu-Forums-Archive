---
title: "Annoyance"
date: 2010-05-05
forum: The Cafe
---

### Post by scottuss on 2010-05-05
Just ran apt-get update, Transmission had a dependency problem and the update crashed the whole machine. gnome-settings daemon was something that didn't get updated properly so on restart I had a horrid looking desktop.

When I did get everything working, the update has put the Window buttons back on the left. Not a massive deal to move them back, but it is really quite annoying.

I don't mind the decisions that Canonical make, but for the love of everything PLEASE respect MY decisions. I WANT THE BUTTONS ON THE DARN RIGHT!!!!!!!!


/rant

Ubuntu still rocks, however :)

---

### Post by NightwishFan on 2010-05-05
Do not update when it may break packages. Generally that only happens on development editions though.

---

### Post by juancarlospaco on 2010-05-05
*Beta means beta... fresh install Final*

---

### Post by scottuss on 2010-05-05
> **NightwishFan said:**
> Do not update when it may break packages. Generally that only happens on development editions though.

I didn't have much choice, I clicked update in the update manager and it went on it's way without complaining until it was too late.

I'm running Lucid Final, no development version here!

---

### Post by NightwishFan on 2010-05-05
It would warn you with a partial upgrade, which you can choose not to do by canceling. Then it will just update everything possible without breaking packages.

---

### Post by Mr. Picklesworth on 2010-05-05
> **scottuss said:**
> I don't mind the decisions that Canonical make, but for the love of everything PLEASE respect MY decisions. I WANT THE BUTTONS ON THE DARN RIGHT!!!!!!!!

You didn't happen to move your window buttons over by adjusting the gconf key manually, did you? The button layout is tied to your seleced theme, now, so if you select a different theme your gconf setting is overridden with that theme's preferred layout.

So the Ambiance, Radiance and Dust themes explicitly say they want buttons in a particular order on the left. Meanwhile Homosapien, Human, Sorbet and New Wave say they want buttons on the right. As you change themes it'll make sense ;)

So, if you want Ambiance or Radiance with buttons on the right, I made a little theme package just for your case :P :
[http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)

---

### Post by scottuss on 2010-05-06
> **NightwishFan said:**
> It would warn you with a partial upgrade, which you can choose not to do by canceling. Then it will just update everything possible without breaking packages.

Um... I didn't do a partial upgrade. Package updates my dear man, package updates.

> **Mr. Picklesworth said:**
> You didn't happen to move your window buttons over by adjusting the gconf key manually, did you? The button layout is tied to your seleced theme, now, so if you select a different theme your gconf setting is overridden with that theme's preferred layout.

So the Ambiance, Radiance and Dust themes explicitly say they want buttons in a particular order on the left. Meanwhile Homosapien, Human, Sorbet and New Wave say they want buttons on the right. As you change themes it'll make sense ;)

So, if you want Ambiance or Radiance with buttons on the right, I made a little theme package just for you:
[http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)

That's awesome, thanks so much! :D:D:D:D

---

### Post by NightwishFan on 2010-05-06
I think your mistaken somehow, but I things happen I suppose. In any case to fix packages try:
```
sudo apt-get -f install
```

---

### Post by scottuss on 2010-05-07
> **NightwishFan said:**
> I think your mistaken somehow, but I things happen I suppose. In any case to fix packages try:
```
sudo apt-get -f install
```

What? I assure you that I am not mistaken. The Update Manager GUI listed some updates, which I said yes to. I entered my password as requested and the updates started. Something went wrong so I opened the Terminal and did sudo apt-get update and sudo apt-get upgrade. At this point, I was warned of the dependency problems.

At no point was I warned before I did the update through the update manager.

P.S - I know about the -f switch :)

---

### Post by NightwishFan on 2010-05-07
Well alright then. :) Are the dependency issues still present?

---

