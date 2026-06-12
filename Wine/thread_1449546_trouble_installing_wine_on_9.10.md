---
title: "trouble installing wine on 9.10"
date: 2010-04-08
forum: Wine
---

### Post by jp351 on 2010-04-08
as the title says, i'm having a little issue installing wine 1.0.1. i've just recently got my hands on ubuntu karmic 9.10, pretty much what you might consider an "original" distribution. when i try the install in terminal, i get an error msg saying i'm missing flex, when i try installing flex, i get another saying i'm missing something else, again, when i try installing that, it says i'm missing x11... it's my understanding that 9.10 comes with some version of x11 already pre-loaded...mostly because it's listed in the software manager..thing... sorry if that's incorrect, but i'm new to linux systems. regardless, i was wondering if anyone could help me with this so that i can get on to "bigger and better things"... or if anyone had any advice or possibly a link to a package or what have you that i could download and install which included all or at least most of the items i need to install and run wine. oh, by the way, the computer i am using with ubuntu on it is not currently connected to the internet, so i do have to download and install the packages and such by hand.

feel free to email me if necessary. thanks.
[EMAIL="legionknght@yahoo.com"]legionknght@yahoo.com[/EMAIL]

---

### Post by dino99 on 2010-04-08
wine 1.0.1 is very outdated, so remove/purge wine package with synaptic, and the hidden file .wine into your /home

add wine repo to your sources.list:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

with synaptic, update and install 1.1.42 (latest release)

then go to menu bar on top left corner: apps -- wine -- wine config : only validate the default choice.

Now you can load any apps by clicking on the exe file as you do with windoz, or into console you do : wine your-app.exe

it's as simple than that.

---

### Post by jp351 on 2010-04-08
well, i can't repo it.. assuming that the repo action involves using the software source apt line thing.. regardless, if i download it and run it in terminal i should have no problems? would i still need to download and run flex and such? by the way, i was under the understanding that 1.1.42 was still somewhat unstable.. hence why i chose to go with 1.0.1 (labeled most recent ***stable*** release)

however, like i said, i am still new to linux systems. i know i don't have all the terms right, not exactly, but hey, i've only had it for about 4 or 5 days..

anyway, i'll give it a whirl and see what i get.

thanks dino :)

*edited* 
ummm, question..well, 2 really..  1.1.42 isn't listed for 9.10, should i be concerned with that? and i can't just download it and install it or anything, can i? as i said in the first post, the computer i've got ubuntu on isn't connected to the net.. :/

---

### Post by ubun2warrior on 2010-04-08
The simplest way to install wine is through synaptics. Just search for wine, if it does not show up in the result then you need to reload the packages(which can be done with a click on reload button in synaptics). After that you can simply install synaptics. 

I did the same thing.

---

