---
title: "totem (GNOME video player) package needs to be upgraded in Ubuntu"
date: 2014-01-25
forum: Ubuntu, Linux and OS Chat
---

### Post by syntaxerror74 on 2014-01-25
Hi there,

I have no idea where to post this, so here...this is to alert some Ubuntu packaging guy that there really needs to be done something about the **ancient**  (3 years old) version of totem which is currently in latest Ubuntu (3.8.2)

I was able to upgrade to 3.10 by adding [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) to /etc/apt/sources.list, creating the GPG key (this is required as well for a reason I don't know) and then apt-get install'ing things as normal.

So **why is 3.8.2 unusable**? 

You will realise it once you've played an audio (not necessarily a video) file by drag-and-drop:
[http://www.tuneid.com/chilled-beats/56400-my-last-unknown-chillout-tune.html](http://www.tuneid.com/chilled-beats/56400-my-last-unknown-chillout-tune.html)

- Open totem
- Do NOT click on the file so you can bypass the download request box and all that...but instead DRAG the file into totem.
- Play the file

Now let it play for some seconds, then SEEK forward (or backwards) by using the slider labeled 'Time:'.
Totem should now FREEZE up totally and will have to be killed on console. The issue was reproducible in 5 out of 5 tries.

**3.10 works perfectly** in that respect.
So this is the reason why 3.8.2 is no longer recommended for daily use.
And no, I didn't think of ridiculing myself by filing a bug report for that old version - they would've closed it down, saying 'dude - upgrade first'.

---

### Post by QIII on 2014-01-25
Not a support request. Moved.

As a rule the Ubuntu developers do not frequent the Forums, so the forums are not really a good place to make suggestions to them.

---

### Post by monkeybrain20122 on 2014-01-26
Is it the chillout.mp3? Works for me. Drag and drop or just open with Totem. drag along the slider back and forth, no freezing. I suppose totem is part of the gnome desktop so it goes by the gnome version. Ubuntu's gnome version is not the most up to date because rapid upstream changes may break compatibility with Unity, so the totem package is also not up to date. Ubuntu 13.10 64 bits, Totem 3.8.2.

---

### Post by ibjsb4 on 2014-01-26
Thats one reason why I like LTS, less breakage :)

---

### Post by grahammechanical on 2014-01-26
Patience. Trusty Tahr installs Totem 3.10.1-1ubuntu by default. So, Totem 3.10 will be in Ubuntu 14.04 LTS. Only three months wait.

---

### Post by monkeybrain20122 on 2014-01-26
> **ibjsb4 said:**
> Thats one reason why I like LTS, less breakage :)

Well OP is complaining about outdate packages, how is LTS supposed to help? Packages are even more outdated in LTS. Also it is not true that LTS has less breakage, if there is breakage you get stuck with it for 5 years (unless you use a ppa or compile yourself, but that defeats the purpose of LTS and Totem, unfortunately is not easy to compile because of all the gnome dependencies)

---

### Post by monkeybrain20122 on 2014-01-26
> **grahammechanical said:**
> Patience. Trusty Tahr installs Totem 3.10.1-1ubuntu by default. So, Totem 3.10 will be in Ubuntu 14.04 LTS. Only three months wait.

Sorry dude, that is not an answer. One issue I have with Ubuntu is that packages are not backported  to current release when fixes/updates are available. If someone needs something for mission critical purpose waiting 3 months or 6 months for the next Ubuntu release is not an option. In this case it seems that it may be a false alarm (as it works for me with OP's sample) but scenarios like that happpens. In that case I would find a ppa or compile foo myself instead of waiting for the next release (and expecting new bugs) I am not 'patient' and don't expect others to be. :)

---

### Post by ibjsb4 on 2014-01-26
> **monkeybrain20122 said:**
> Well OP is complaining about outdate packages, how is LTS supposed to help? Packages are even more outdated in LTS. Also it is not true that LTS has less breakage, if there is breakage you get stuck with it for 5 years (unless you use a ppa or compile yourself, but that defeats the purpose of LTS)

You wish to change this into a rant?  No thank you :)

---

### Post by syntaxerror74 on 2014-01-30
> **grahammechanical said:**
> Patience. Trusty Tahr installs Totem 3.10.1-1ubuntu by default. So, Totem 3.10 will be in Ubuntu 14.04 LTS. Only three months wait.

Well!
This is an answer I can live with (for the time being), thank you. I was just trying to keep myself from delving into Tahr currently since I feared to break too much with this "half-bred "status Tahr is in atm...so I prefer to stick with Saucy Plus X 
(where 'Plus X ' = some hand-picked updating here and then, but refraining from changing major things)
My gawd, 'bout time to get essential applications like **gedit** updated to 3.10, dammit! :P

The 'Buntus are really a bit behind at the moment with all that GNOME-ish stuff as it looks...given that even libgtk-3-* (which nearly all GNOME applications are based on) is working perfectly in version 3.10 *already*, to begin with. Just upgraded my entire dev environment for that reason some days ago. So that's another 'Plus X' I could have waited eternally for until Tahr finalization ;)

BTW, I'm on **L**ubuntu, so LXDE, not Unity. (And I like it that way. :P) But I deliberately didn't tag this thread since it's really no Lubuntu-specific issue.

---

