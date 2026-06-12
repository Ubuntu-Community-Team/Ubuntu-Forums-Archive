---
title: "Security update: Sun Java JRE update 19"
date: 2010-04-02
forum: Security
---

### Post by Pjotr123 on 2010-04-02
Oracle (Sun) has issued a new update for it's JRE, which fixes many security bugs: update 19.

I've therefore updated my how-to for manual installation of JRE:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by haddog on 2010-04-02
> **Pjotr123 said:**
> Oracle (Sun) has issued a new update for it's JRE, which fixes many security bugs: update 19.

I've therefore updated my how-to for manual installation of JRE:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Got it. Thnx!

---

### Post by quixote on 2010-04-03
I've followed your excellent instructions several times before and they work like a charm.  That was on my own computers.  Now I was helping a friend who wanted an up to date FF get 3.6.3 ... and managed to blow up their existing browser and canNOT get the java install to work.  :oops:

I followed the instructions at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) exactly -- the same instructions that worked on other machines -- and FF 3.6.3 acts like it doesn't exist.  This is a 64-bit Karmic system.  (I've installed it on 64-bit karmic before, just not on that specific machine.)  The java test site at Sun also doesn't see any java on that machine.

Wildly frustrating.  I realize I haven't given anyone much to go on there, but if you have any ideas for me, I'd be very grateful!

---

### Post by Nisal on 2010-04-04
when i enter this command 

> sudo mv ~/jre-6u19-linux-i586.bin /opt/java/32
im getting a error saying there is no such directory

---

### Post by Pjotr123 on 2010-04-04
> **quixote said:**
> I've followed your excellent instructions several times before and they work like a charm.  That was on my own computers.  Now I was helping a friend who wanted an up to date FF get 3.6.3 ... and managed to blow up their existing browser and canNOT get the java install to work.  :oops:

I followed the instructions at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) exactly -- the same instructions that worked on other machines -- and FF 3.6.3 acts like it doesn't exist.  This is a 64-bit Karmic system.  (I've installed it on 64-bit karmic before, just not on that specific machine.)  The java test site at Sun also doesn't see any java on that machine.

Wildly frustrating.  I realize I haven't given anyone much to go on there, but if you have any ideas for me, I'd be very grateful!

Can you pinpoint the exact step which doesn't yield the expected result? Was the installation at step 8 succesful (did you see activity in the terminal after that command)?

--edit--
It may have to do with the fact that you've installed a non-default Firefox version (3.6.3). The file paths are probably different from the defaults. 

Try adapting the commands for the Firefox plugins (step 11 and further), to the file paths of FF 3.6.3.

---

### Post by Soul-Sing on 2010-04-04
non default firefox versions, via PPA sources are (often) found in /opt, so the symlink goes====>/opt.

---

### Post by quixote on 2010-04-04
(Nisal: you have to make the directory first (sudo mkdir /opt/java/32).  If it's not already there, the mv command will return that error.)

I get no errors during install at all.  Every step terminates normally.  I think, as you say, that the problem is the path to the expected plugin dir.  Which I can't figure out!  

My 3.6.3 is in /usr/lib/firefox.  It wasn't installed via a ppa, but an unpacked tar.bz downloaded from mozilla.  (I had expected it to install to /usr/lib/firefox.3.6.3, not /usr/lib/firefox which is why I managed to step all over the existing install....)

There's a plugins dir at /usr/lib/firefox/plugins.  On my system (3.6.3 installed via ppa) that's a link to /usr/lib/firefox-addons/plugins ... which contains nothing!  but all my plugins work... ???  My ~/.mozilla/plugins dir has some actual plugins (not links), and a libvlc link to /usr/lib/mozilla/plugins.  

Hmm.  I think I may have just found the problem.  That's where all the plugins / plugin links seem to be.  I should try making the links there on my friend's computer and see if that helps.

Does that make sense?

Why do the devs keep moving the plugin directories around??  :shock:

---

### Post by quixote on 2010-04-04
Nope.  Just tried it, and FF is still not using them.  The really weird thing is the "default plugin" (libnullplugin.so) is listed in about: plugins, but is "not enabled".  ??  How can that be?  

Flash, which I managed to get working yesterday, is the only plugin that's working.  It installed strangely, and the actual library is in ~/.mozilla/plugins, but, hey, I'll take what I can get.  Putting links to the other plugins in that directory isn't doing anything, though.  Aargh.

---

### Post by moon_raker on 2010-04-05
I have updated Karmic but what about Hardy ? I remember once updating sun jre by adding the hardybleed repo [https://launchpad.net/~hardybleed/+archive/ppa](https://launchpad.net/~hardybleed/+archive/ppa) 
Unfortunately they still have the u18 version but I suppose there will soon be an update to u19.
Of course I could just download from Sun, but adding the hardybleed repo (then unticking it in sources after install of jre as it is afterall 'bleeding edge' and thus unsupported) seems the neater way.

---

### Post by BigCityCat on 2010-04-05
I just wanted to thank you for doing this.

---

### Post by bluelamp999 on 2010-04-06
> **BigCityCat said:**
> I just wanted to thank you for doing this.

I heartily second this. Excellent tutorial!

---

