---
title: "Odd internet problem - only google available???"
date: 2010-07-09
forum: Ubuntu Studio
---

### Post by Smithernz on 2010-07-09
I have ubuntu studio 10.04 installed on my PC, dual-booting it with Vista. I also have Ubuntu Studio 10.04 on my laptop. When I plug the internet cable onto my PC it works in Vista. Then, when I restart, and load Ubuntu Studio, I am only able to access google as far as I can see. By this, I mean that I can successfully search anything, but I can't load up any of the other websites. Interestingly though, when I load up the Network Tools, I can ping Google and ubuntuforums.org (which I can't access).

Finally, when I switch the cable to my laptop with Ubuntu loaded, it is all fully working.

Please help!!!

---

### Post by mango42 on 2010-07-10
What happens if you ping startpage.com instead of go00ogle ?

Sounds like Vista is ghosting net kontrol, to me - tunneling AV software, perhaps ;-)

Solution? Ditch Vista for starters, preferably with DBan in autonuke mode...

---

### Post by Smithernz on 2010-07-10
startpage.com will ping as well.

Is there a solution without deleting vista, as this is not an option.

---

### Post by cchhrriiss121212 on 2010-07-10
I doubt vista is the issue here. Can you access updates and use synaptic? Perhaps try out another web browser, chrome or opera.

---

### Post by Smithernz on 2010-07-11
Updates gets stuck when "downloading file 2 or 16", giving this when I press cancel:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release)  
Some index files failed to download, they have been ignored, or old ones used instead.

Then, in Synaptic, I can only see packages that I have on the computer already. When I click reload, it once again says that it is stuck downloading file 2 of 16, and clicking cancel gives me the same message as above.

I would try another browser, but I am completely new to linux, so I don't know how to without synaptic...

---

### Post by _Mark_ on 2010-07-11
Seems like it could be a DNS problem, not knowing how you get you're nameservers assigned (probably using you're ISP's)bit of a guess here.

You say on you're laptop it works fine? take a look at /etc/resolv.conf on the laptop this should show the the nameservers IP address/s, compare this to the resolv.conf on the desktop if different amend the desktop to match the laptop

---

### Post by Smithernz on 2010-07-11
Oddly, they are both the same.

---

### Post by cchhrriiss121212 on 2010-07-11
Did you try installing network manager and it's dependencies?
It's on the studio image:
[http://ubuntuforums.org/showthread.php?t=1525705](http://ubuntuforums.org/showthread.php?t=1525705)

Also to install chrome, just download the .deb file from google, and it will install like an .exe does on windows.

---

### Post by _Mark_ on 2010-07-11
> **Smithernz said:**
> Oddly, they are both the same.

Hmm, is very odd has it always been a problem since install or has it worked ok in the past? If it has worked in the past have you done anything between working and not working?

All I can really think of is try clearing you browsers cache, what browser are you using by the way? and have you tried another?

---

### Post by Smithernz on 2010-07-12
cchhrriiss121212, I tried to install those packages, but I got a Dependency error on libnm-glib2 - Error: Dependency is not satisfiable: libnm-util1 (>= 0.8~a~git.20090804t185522.4bab334) -, while all the others said that it couldn't open them.
 
_Mark_, I have just installed google chrome, so I now have that, as well as the included firefox. Neither of these work, other than for viewing any of google's pages (e.g. I was able to download chrome straight from google's page for it with firefox). My internet never worked properly with this installation of Ubuntu Studio.
 
EDIT: My computer just crashed, and when I loaded Ubuntu Studio again, Chrome had vanished from the internet program list. Synaptic still tells me its installed. *looks to his left - the cocmputer has just crashed again* :S Any suggestions for this?

EDIT2: Turns out I have a failing backlight. This is no longer a problem.

---

