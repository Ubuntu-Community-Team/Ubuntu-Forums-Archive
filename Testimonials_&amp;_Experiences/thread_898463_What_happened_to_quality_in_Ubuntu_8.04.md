---
title: "What happened to quality in Ubuntu 8.04?"
date: 2008-08-23
forum: Testimonials &amp; Experiences
---

### Post by Matt05 on 2008-08-23
I recently "upgraded" from 7.10 to 8.04.  This is my experience:

- I created a new and encrypted partition for ubuntu.  Worked great until the first hybernation (on a Dell D610).  After that one I could no longer access the partition.  Data was lost.

- Hybernation and sleep used to work in 7.10 but now are very unreliable.

- Keyboard layout is broken.  I can no longer switch between German and US layout which is a showstopper for me.

- Firefox plays no or unreliable sound with Flash.  It crashes with Flash.

- The age-old bug that nm-applet would not remember the correct WAP2 keys when using "manual" mode (the _only_ mode that actually works on my machine) is still not fixed.

- All these bugs are filed in launchpad and they are not bugs that affect very few users only.

I've been really impressed with ubuntu until 7.10.  I was even thinking about putting it on my parent's new notebook.  Now I'm really glad I didn't.

---

### Post by gjoellee on 2008-08-23
> **Matt05 said:**
> I recently "upgraded" from 7.10 to 8.04.  This is my experience:

- I created a new and encrypted partition for ubuntu.  Worked great until the first hybernation (on a Dell D610).  After that one I could no longer access the partition.  Data was lost.

- Hybernation and sleep used to work in 7.10 but now are very unreliable.

- Keyboard layout is broken.  I can no longer switch between German and US layout which is a showstopper for me.

- Firefox plays no or unreliable sound with Flash.  It crashes with Flash.

- The age-old bug that nm-applet would not remember the correct WAP2 keys when using "manual" mode (the _only_ mode that actually works on my machine) is still not fixed.

- All these bugs are filed in launchpad and they are not bugs that affect very few users only.

I've been really impressed with ubuntu until 7.10.  I was even thinking about putting it on my parent's new notebook.  Now I'm really glad I didn't.

You should check out Linux Mint 5, it is based on Ubuntu but it is "out of the box". Flash in Firefox runs like a dream and all other media (may not work good in the live CD). There are also many other options etc in Linux Mint.

---

### Post by mike1234 on 2008-08-23
> **gjoellee said:**
> You should check out Linux Mint 5, it is based on Ubuntu but it is "out of the box". Flash in Firefox runs like a dream and all other media (may not work good in the live CD). There are also many other options etc in Linux 
Mint.

"There are also many other options etc in Linux 
Mint".

 Yeah, Like viruses. :)

[http://www.linuxmint.com/blog/?p=235](http://www.linuxmint.com/blog/?p=235)

---

### Post by wolfen69 on 2008-08-23
quality with hardy has never been an issue with me. then again, i always do a fresh install. upgrading is the  worst way to go. or didnt you know that? try a fresh install then tell us how it is.

---

### Post by y6FgBn)~v on 2008-08-23
> **mike1234 said:**
> "There are also many other options etc in Linux 
Mint".

 Yeah, Like viruses. :)

[http://www.linuxmint.com/blog/?p=235](http://www.linuxmint.com/blog/?p=235)

How embarrassing.:eek:

---

### Post by karellen on 2008-08-23
> **mike1234 said:**
> "There are also many other options etc in Linux 
Mint".

 Yeah, Like viruses. :)

[http://www.linuxmint.com/blog/?p=235](http://www.linuxmint.com/blog/?p=235)

any distro could be plagued by this, don't bash Mint for no reason

---

### Post by exploder on 2008-08-23
Hardy is very high quality at this point in time. There are daily builds of Hardy available that resolve many issues. You can get a current build here.

[http://cdimage.ubuntu.com/hardy/daily-live/current/](http://cdimage.ubuntu.com/hardy/daily-live/current/)

Both Hardy and Mint are only as good as the packages available to build with. It takes time to fix things. 

Also, the LinuxMint site was not the only site attacked, RedHat and Zenwalk apparently were also victims too. LinuxMint was quick to respond to the issue and published a statement explaining what had happened. I have a great deal of respect for LinuxMint for making a public announcement and not hiding anything about the incident.

There are packages in the "proposed repositories" that address problems too. Have a look, you might be pleasantly surprised.

---

### Post by vikramaditya on 2008-08-23
> **Matt05 said:**
> - Hybernation and sleep used to work in 7.10 but now are very unreliable.
I never use those features, so can't help.
> **Matt05 said:**
> - Keyboard layout is broken.  I can no longer switch between German and US layout which is a showstopper for me.
Nah...that's just a "dealbreaker".  A "showstopper" is when everything you type shows up in aramaic, then God starts reading it to you.
> **Matt05 said:**
> - Firefox plays no or unreliable sound with Flash.  It crashes with Flash.
I keep asking nobody in particular, "why FF?".  Opera (now in 9.52 flavor!) does java & flash with none of the issues I had in FF.
> **Matt05 said:**
> - The age-old bug that nm-applet would not remember the correct WAP2 keys when using "manual" mode
No need for nm here, so can't help.

As **wolfen69** points out, maybe you should try a clean install.  Even MS & Mac have issues with "upgrading".  Besides, who needs quality when there's so much freakin' quantity? :)

---

### Post by Matt05 on 2008-08-24
I _did_ a clean install.  (Although this should _not_ be necessary on a Debian-based distribution.)

Thanks for the hints.

P.S.: I traced some problems back to Pulse which is yet! another! sound system for Linux. :(

---

### Post by Matt05 on 2008-08-24
> **exploder said:**
> Hardy is very high quality at this point in time. There are daily builds of Hardy available that resolve many issues.

I've just seen the poll in this forum "Share with the community your Hardy install/upgrade experience" and I disagree: About 11% of Hardy installs or upgrades "worked flawlessly".  In other words: 89% did not.

If Ubuntu wants to be the distro which you can safely install on your parents' computer and you can expect that "it just works" it should not be the first to switch to new and untested infrastructure.  Right now the audio system pulseaudio seems to be the root cause of many reported bugs, previously it was gstreamer which Ubuntu adopted very (IMHO: too) quickly.

The open source community once had the tradition not to release prematurely.  Debian put that to an extreme with super-long release cycles and as a reaction to that Ubunutu was created.  With 8.04 it is the first time that I have the impression that the distro might have been released prematurely and that the strict X.04 X.10 releases should have been relaxed to allow more testing.

---

### Post by wolfen69 on 2008-08-24
@ Matt05

you have to realise that alot of people that come here are looking for help. so of course that "poll" is going to be slanted in favor of installs not going so well. what about all the people that had perfect installs? they would probably not have as much reason to come here. but you believe what you want. we all know you are an expert in such matters.

at least my findings are based on fact. (that hardy is good) i have now  installed hardy  on over 25 different computers without much of an issue. lucky? i dont think so. therefore, until you start testing it on a wide variety of computers, your opinion holds little weight. as uninformed as your opinion is, you are entitled to it though. :rolleyes:

---

### Post by swisscow on 2008-08-24
Agreed with Wolfen here. And also remember you are installing from a generic one size fits all cd - it's amazing that most things work. Try doing that with xp, it'll fire up but will you have the correct drivers?

---

