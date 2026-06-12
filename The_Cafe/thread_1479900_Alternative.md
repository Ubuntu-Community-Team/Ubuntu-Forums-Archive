---
title: "Alternative"
date: 2010-05-11
forum: The Cafe
---

### Post by dzon65 on 2010-05-11
Hi,

    I can't escape the feeling, that since 9.10, things are going the wrong way. Things are getting heavier and the ease of customizing is dropping through the floor. Someone who's been on the forum for years pointed out to me that most issues with the first release up to 9.10 could be solved in pretty much the same way but with Lucid, allot of the time, he doesn't even know where to begin. Change is here and it wasn't all for the best. So, for me, I've given up on the Compiz and Emerald eye candy in favor of solidness. Were it not for headphone trouble in 8.04, 8.10, and 9.04, I'd probably still be using one of them. For now, I'm stuck with 9.10. And I do mean stuck. 

    Many of my friends want to give Ubuntu a try but once they take a look at the Threads or their sound is suddenly missing or wireless is a nightmare.....well,you know. I'm pretty sure I'm not the only one to say that 9.10 was a buggy release and still is. Lucid is only just starting and its already got some major issues too, so only time will tell.But for now,many people are scared in advance and could really do without some major issues in order to get familiar with how it feels/works.

    Now, I hardly use any of the default installed programs, the bugs that come along with it, and, probably most importantly, the overall need for stability. Each time I booted Karmic, I wasn't even sure I'd be able to log in. Due to this and other things, I decided to install minimal and nothing but minimal. Now don't get me wrong, it's as if my PC was made for Linux and I didn't really experience any serious problems, but still, even the 9.10 minimal version wasn't what you could call flawless. I spent hours trying to solve LXDE issues until I finally gave up on it. No problems with a 8.10 or 9.04 minimal (aside from my headphones). Nevertheless, this is how I set up 9.10 minimal:

Minimal (xorg etc..)

As listed in Synaptic:

openbox (obconf,obmenu...)
thunar (+ needed plugins)
mplayer
exaile
gimp
abiword
gnumeric
gcolor2
lxappearance
gpicview
openoffice.impress
gnome-utils (I'll get back on this)
roxterm
clearlooks-engine
nitrogen
shutdownbox
firefox
language pack (being Belgian)
conky (with switch)
leafpad
....................................

And yes, gnome-panel

Why gnome-panel/gnome-utils? For the simple reason that I put website shortcuts on it. I could use Cairo or something similar but my nvidia 6150 card really sucks so that's a no go. Gnome-panel /utils isn't really that much heavier than other panels or apps (some are really fast) but unfortunately it draws in half of its family. It's like calling your Mom and you end up talking to her, your Dad, his bowling partner, all your cousins, your Aunt Hilda, and her Yoga Therapist.Of course,there are many panels/docks out there so choice is big.

The whole point, however, is if I were to set this up on, say, 8.04, no one could visually notice the difference from 9.10 Karmic or whatever. The main difference is that it would, almost certainly, be more stable. The combination of this setup makes it feel rock solid, kinda back to basics. Like I said, kinda lucky myself in that my PC works very well with Linux and I'm not saying issues don't appear in customized setups, merely saying that you can have a solid, reliable and (very) fast alternative. Preferably set up on a previous release.
By the way,this setup "weighs" 1.8 Gb and is pretty much packed with all basics.

Like I said,hundreds of things available,adding/removing stuff's a matter of taste and needs but it's a good setup to begin with and will work well on older pc's.It's not slitaz or puppy but it's just an idea for those wanting to stay in the ubuntu family.


One more thing. Since it's openbox,compiz fancies are out of the question.Which is okay but...This is more a request to the Openbox "engineers". A more advanced transparency possibility. I'm not talking xcompmgr, transset or xcompmgr-dana, but more possibilities for window decoration.

Another, someone please pick up the 3Ddesktop program. Nothing too fancy, a simple window browser, shiftswitcher or 3D flip style (it was this already, I know) only nicer than what it offers right now.It would certainly increase openbox users.

I added two screenshots to show this doesn't have to be spartan.Once's my daytheme,the other for nightowls.Both are clearlooks.

(Formal editing into a reasonable facsimile of a human language done by warfacegod)

---

### Post by NightwishFan on 2010-05-11
Nice wallpaper of Pandora and Polyphemus, and thanks for the advice.

---

### Post by dzon65 on 2010-05-11
Yeah,the wallpaper.....could use a sharper one.It's a bit blurry.

---

### Post by m4tic on 2010-05-11
KDE's overtaking

---

### Post by NightwishFan on 2010-05-11
Enjoy!

[http://sites.google.com/site/wayfarergroup22/pandora.zip?attredirects=0&d=1](http://sites.google.com/site/wayfarergroup22/pandora.zip?attredirects=0&d=1)

---

### Post by pwnst*r on 2010-05-11
lol @ the post edit.

---

### Post by itreius on 2010-05-11
Doing a minimal install without at least having
```
APT::Install-Recommends "0"
APT::Install-Suggests "0"
```
in /etc/apt/apt.conf isn't exactly worth it, in my opinion.

---

### Post by warfacegod on 2010-05-11
> **itreius said:**
> Doing a minimal install without at least having
```
APT::Install-Recommends "0"
APT::Install-Suggests "0"
```
in /etc/apt/apt.conf isn't exactly worth it, in my opinion.

What does this do?

---

### Post by urukrama on 2010-05-11
You might be more comfortable with Debian.

---

### Post by itreius on 2010-05-11
> **warfacegod said:**
> What does this do?

Disables automatic installing of recommended and suggested packages in apt-get.

---

### Post by dzon65 on 2010-05-12
> **NightwishFan said:**
> Enjoy!

[http://sites.google.com/site/wayfarergroup22/pandora.zip?attredirects=0&d=1](http://sites.google.com/site/wayfarergroup22/pandora.zip?attredirects=0&d=1)

Thanks man.
Kind regards,J.

---

### Post by dzon65 on 2010-05-12
> **itreius said:**
> Disables automatic installing of recommended and suggested packages in apt-get.

Not quite awake yet but I'm not sure what you mean.

---

### Post by t0p on 2010-05-12
> **dzon65 said:**
> Not quite awake yet but I'm not sure what you mean.

By default in Ubuntu, when you install a package, apt-get will also install "recommended" packages and will also list options of "suggested" packages to go with what you're installing.  The config lines described above disable that feature.

---

### Post by dzon65 on 2010-05-12
Oh,I see.Thought this applied to a minimal install.My bad.

---

### Post by Excedio on 2010-05-12
> **pwnst*r said:**
> lol @ the post edit.
 
Holy smokes! You're still around?! Havn't seen you in a while. </hijack>

---

