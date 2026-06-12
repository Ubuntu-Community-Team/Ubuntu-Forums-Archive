---
title: "linux to run on old computer"
date: 2006-01-02
forum: The Cafe
---

### Post by nemik on 2006-01-02
hello,

my girlfriend's mother found an older laptop, around 233 MHz with 64MB or so of RAM and a 4GB hard-drive.

i know how much ubuntu/gnome lagged on a 400MHZ, i can't eve imagine it on this old pentium II.

what distro would you guys recommend that can simply run firefox so she can go on the internet and detect a PCMCIA wireless card?

thanks guys!

---

### Post by Iandefor on 2006-01-02
Damn Small Linux. Also, you might try Puppy. Also: Beatrix and Vector Linux might be good bets.
Failing all else, you could even try the Elive install.

For a distro that really runs without encumberment, though, you just can't beat tomsrtbt :-D.

---

### Post by Aviatrixie on 2006-01-02
I agree with the 4 distros that Iandefor mentioned, as I have used the live CDs of DSL, Puppy, BeatrIX, and Vector and they all ran well on older slower machines. I really like BeatrIX as it's actually built on Ubuntu and once installed can use the Ubuntu repositories. BeatrIX has no multimedia but those can be added once installed. it does come with the full Open Office suite, Gaim,and several other top tier apps. As one glowing review put it, BeatrIX "is Ubuntu, minus 25 pounds, and in training. Gnome, Firefox, OpenOffice.org, Evolution, GAIM. The breakfast of champions".

In fact, I picked up a 266mhz PII PC (with 128 mb ram) with monitor, KB, and mouse that I intend to install Beatrix on and give to my father. He's 75 and I've already had to rescue his XP from virus's before. He's really getting to old to have to know how to maintain a healthy windows so I'm going to ease him into Linux.  ;)

---

### Post by super on 2006-01-02
i haven't tried BeatrIX but i can vouch for Elive.
it's debian based (you can use apt-get), it's fast,
and i looks super-cool too! (but not quite like me! :razz: )

---

### Post by Iandefor on 2006-01-02
[quote=Aviatrixie]I agree with the 4 distros that Iandefor mentioned, as I have used the live CDs of DSL, Puppy, BeatrIX, and Vector and they all ran well on older slower machines. I really like BeatrIX as it's actually built on Ubuntu and once installed can use the Ubuntu repositories. BeatrIX has no multimedia but those can be added once installed. it does come with the full Open Office suite, Gaim,and several other top tier apps. As one glowing review put it, BeatrIX "is Ubuntu, minus 25 pounds, and in training. Gnome, Firefox, OpenOffice.org, Evolution, GAIM. The breakfast of champions".[/quote]

I didn't know Beatrix included those; why would they do that? GNOME, Firefox, OpenOffice.org and Evolution are all memory hogs of the worst sort. That's why I use XFCE, Epiphany-Browser, and Abiword, and check my email via my web browser. I have a computer with similar specifications to the original poster's computer (It has a more powerful processor, though: An AMD  Duron rated at 700 mhz), and those are all terribly slow with it. I retract my support for Beatrix as a distribution that would work well with the original poster's computer, then.

---

### Post by nemik on 2006-01-03
thanks for the suggests guys. out of curiousity, i decided to try a full-blow ubuntu desktop install. the install procedure took forever, but once set up, isn't terrible.

screen resultion sucked at first at 800X600 but i increased it to a great-looking 1024x768 by reducing default color depth to 16 in xorg.xonf. cheap generic PCMCIA wifi card was instantly recognized and worked without any problems.

sound isn't working but not a big issue for her so i'll leave it alone for now.

she needs some open-office apps and firefox. all work great, though kinda slow. she doesn't seem to mind and loves the computer. i'm actuall surprised at how well it runs as well.
i would try some of the other distros you guys mentioned, but i'm not sure any of them could so flawlessly detect and allow use of that wifi card.

thank you all again very much!

---

### Post by poofyhairguy on 2006-01-03
At least put XFCE on there.

---

### Post by xequence on 2006-01-03
Go with Damn small linux. XFCE wont run in 64MB ram, its not even blazing fast in 192 MB RAM.

---

### Post by nemik on 2006-01-03
[QUOTE=xequence]Go with Damn small linux. XFCE wont run in 64MB ram, its not even blazing fast in 192 MB RAM.[/QUOTE]

its got 128MB RAM. gnome isn't lightning on it, but usable.

---

### Post by Iandefor on 2006-01-03
[quote=xequence]Go with Damn small linux. XFCE wont run in 64MB ram, its not even blazing fast in 192 MB RAM.[/quote] *Looks around bewilderdly*
It runs fine on my 64 MB computer. I'd hardly call it blazing fast, but it runs.

---

### Post by mstlyevil on 2006-01-03
[QUOTE=Iandefor]*Looks around bewilderdly*
It runs fine on my 64 MB computer. I'd hardly call it blazing fast, but it runs.[/QUOTE]

I personally am clueless when it comes to DE's outside of Gnome and KDE. But I can tell you both of them run blazing fast on a A64 3200 with 1 Gig of RAM. ;)

---

### Post by Galoot on 2006-01-03
I've had no issues at all running Xfce on 128MB of RAM.

---

### Post by majikstreet on 2006-01-03
maybe ubuntu "server install" with icewm? [https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28memory%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28memory%29)

---

