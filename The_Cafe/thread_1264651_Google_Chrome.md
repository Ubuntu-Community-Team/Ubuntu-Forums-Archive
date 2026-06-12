---
title: "Google Chrome"
date: 2009-09-12
forum: The Cafe
---

### Post by T2manner on 2009-09-12
I'm not sure if anybody has posted this yet, but i just stumbled upon the developers release of Google Chrome for linux.  This isn't chromium, this is Google Chrome.
[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

---

### Post by chriskin on 2009-09-12
yes it has been posted many times

Chromium is way better if i can say my opinion here

it seems the same but it's the next version than chrome, meaning bugs have been fixed.

---

### Post by joey-elijah on 2009-09-12
> **chriskin said:**
> yes it has been posted many times

Chromium is way better if i can say my opinion here

it seems the same but it's the next version than chrome, meaning bugs have been fixed.

...but comes with new bugs that have yet to be discovered ;)

---

### Post by Sporkman on 2009-09-12
I don't like how there's no way to get to bookmarks without enabling the bookmarks toolbar (i.e. no straightforward menu selection).

---

### Post by NormanFLinux on 2009-09-12
You can run Chrome in Wine but porting it completely to Linux would make it a native application. Google is also working on its own OS. A version may be ready by next year.

---

### Post by hanzomon4 on 2009-09-12
> **NormanFLinux said:**
> You can run Chrome in Wine but porting it completely to Linux would make it a native application. Google is also working on its own OS. A version may be ready by next year.

Chrome and Chromium are native applications.. perhaps I don't follow

---

### Post by chriskin on 2009-09-12
> **hanzomon4 said:**
> Chrome and Chromium are native applications.. perhaps I don't follow

he is probably not aware that they are
or he thinks that they are not ready, as they are not final versions

---

### Post by chriskin on 2009-09-12
> **joey-elijah said:**
> ...but comes with new bugs that have yet to be discovered ;)

i haven't seen any myself, the last one (no sound on flash) was fixed and isn't fixed on chrome yet

---

### Post by Pogeymanz on 2009-09-12
I'm using Iron right now, which is the latest Chromium with all the tracking stuff ripped out. Very nice browser. Still a little rough around the edges, but it'll honestly be better than FF or Opera once it gets its features going.

---

### Post by chriskin on 2009-09-12
> **Pogeymanz said:**
> I'm using Iron right now, which is the latest Chromium with all the tracking stuff ripped out. Very nice browser. Still a little rough around the edges, but it'll honestly be better than FF or Opera once it gets its features going.

but isn't Iron Chrome without the tracking stuff? i think that chromium doesn't have any either way

---

### Post by NormanFLinux on 2009-09-12
They're not final versions. There's every reason to be believe they will be ready once they're generally available.

---

### Post by chriskin on 2009-09-12
> **NormanFLinux said:**
> They're not final versions. There's every reason to be believe they will be ready once they're generally available.

excuse me but what are you responding to? :popcorn:

---

### Post by bodyharvester on 2009-09-12
are chrome, chromium and iron chrome seperate things or variations of one?

---

### Post by chriskin on 2009-09-12
> **bodyharvester said:**
> are chrome, chromium and iron chrome seperate things or variations of one?

chromium is the base 
chrome is chromium with google's branding
iron is chrome that is not allowed to call home

---

### Post by bodyharvester on 2009-09-12
> **chriskin said:**
> chromium is the base 
chrome is chromium with google's branding
iron is chrome that is not allowed to call home

thanks :)

---

### Post by hoppipolla on 2009-09-12
So, if Chromium is better, where is the best place for me to download it for Ubuntu? :)

---

### Post by aysiu on 2009-09-12
> **hoppipolla said:**
> So, if Chromium is better, where is the best place for me to download it for Ubuntu? :)
From the daily build repositories.

Instructions here:
[http://www.psychocats.net/ubuntucat/chromium/](http://www.psychocats.net/ubuntucat/chromium/)

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> So, if Chromium is better, where is the best place for me to download it for Ubuntu? :)

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

add the sources (and the key?) and install :)

---

### Post by chriskin on 2009-09-12
> **aysiu said:**
> From the daily build repositories.

Instructions here:
[http://www.psychocats.net/ubuntucat/chromium/](http://www.psychocats.net/ubuntucat/chromium/)

it seems i came second

use this one, it is better as it is a tutorial (if you are not experienced with adding sources)

---

### Post by hoppipolla on 2009-09-12
> **chriskin said:**
> it seems i came second

use this one, it is better as it is a tutorial (if you are not experienced with adding sources)

Waaaait wait wait wait....

When I add repositories to Ubuntu... I have to add them in the command line AND in Synaptic? I thought it was one or the other? Is that why the new Amarok beta didn't pop up after I added the repository in Synaptic? ._.


EDIT -- Oo wait, sorry again, the first one was for the GPG Key, my bad :)

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> Waaaait wait wait wait....

When I add repositories to Ubuntu... I have to add them in the command line AND in Synaptic? I thought it was one or the other? Is that why the new Amarok beta didn't pop up after I added the repository in Synaptic? ._.

you only have to add it via the software sources at system/admin OR via editing the text file of /etc/apt/sources.list

that's the same thing done in two ways, you don't have to do both 

a link for the software sources can be found at synaptic package manager as well, i think

---

### Post by hoppipolla on 2009-09-12
Yeah I did the whole thing as stated (as I always do) and as usual Synaptic didn't find the package when I searched for it :(

Man I really hope they improve this in Karmic, I mean surely it can't be too hard to list packages in new repositories? :(

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> Yeah I did the whole thing as stated (as I always do) and as usual Synaptic didn't find the package when I searched for it :(

Man I really hope they improve this in Karmic, I mean surely it can't be too hard to list packages in new repositories? :(

did you check for updates first? checking for updates fetches the latest info about the packages and will show it
if now , just try sudo apt-get update && sudo apt-get install chromium-browser on a terminal

---

### Post by hoppipolla on 2009-09-12
> **chriskin said:**
> did you check for updates first? checking for updates fetches the latest info about the packages and will show it
if now , just try sudo apt-get update && sudo apt-get install chromium-browser on a terminal

Yeah I did, and it still didn't come up in Synaptic.

However, when I put "sudo apt-get chromium-browser" into a prompt it worked fine. Sometimes I find synaptic can be a bit slow, or maybe not even list things at all I don't know :S

Anyway, let's try Chromium! :)

---

### Post by hoppipolla on 2009-09-12
Yes! Chrome works! I'm on it now :)

Man I love this browser lol :)

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> Yeah I did, and it still didn't come up in Synaptic.

However, when I put "sudo apt-get chromium-browser" into a prompt it worked fine. Sometimes I find synaptic can be a bit slow, or maybe not even list things at all I don't know :S

Anyway, let's try Chromium! :)

it has never happened to my synaptic, i don't know why it does it on yours

now, back on topic
you might want to start chromium with the command "chromium-browser --enable-user-scripts --enable-extensions --enable-plugins" for it to be more complete

you can do it by right clicking on menu and editing chromium's launcher

---

### Post by hoppipolla on 2009-09-12
Wow it looks better than on XP!

And OK I'll change it's launcher :)

---

### Post by chriskin on 2009-09-12
you might as well be interested in this site, it has all the available extensions , plugins and bookmarklets that work on chrome/chromium

[http://www.chromeplugins.org/google/chrome-plugins/chrome-extensions-bookmarklets-userscripts-compilation-7510.html](http://www.chromeplugins.org/google/chrome-plugins/chrome-extensions-bookmarklets-userscripts-compilation-7510.html)

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> Wow it looks better than on XP!

And OK I'll change it's launcher :)

as for the looks. check on the options, you can set it to look gtk native, in order to NOT be that horrible blue :)

---

### Post by hoppipolla on 2009-09-12
> **chriskin said:**
> as for the looks. check on the options, you can set it to look gtk native, in order to NOT be that horrible blue :)

But my whole Ubuntu desktop is also blue ._.  lol

And it's just so speedy! I really do much prefer Chrome to Firefox... sorry Mozilla as I do think you are cool ._.

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> But my whole Ubuntu desktop is also blue ._.  lol

And it's just so speedy! I really do much prefer Chrome to Firefox... sorry Mozilla as I do think you are cool ._.

your whole desktop is blue?
take this popcorn then :popcorn: 

i prefer silver/grey or black , depending on the mood

anyway, that's too offtopic

yes, chromium is way faster than firefox, both on cold starts and on browsing

---

### Post by hoppipolla on 2009-09-12
> **chriskin said:**
> your whole desktop is blue?
take this popcorn then :popcorn: 

i prefer silver/grey or black , depending on the mood

anyway, that's too offtopic

yes, chromium is way faster than firefox, both on cold starts and on browsing

Such a shame, I mean Firefox looked so good for so long but... sitting here now, there is just no comparison ._.

---

### Post by chriskin on 2009-09-12
> **hoppipolla said:**
> Such a shame, I mean Firefox looked so good for so long but... sitting here now, there is just no comparison ._.

if you don't use the extra features firefox has, there are not many reasons to use it. i don't, at least :)

---

### Post by hoppipolla on 2009-09-12
> **chriskin said:**
> if you don't use the extra features firefox has, there are not many reasons to use it. i don't, at least :)

But I LIKE Mozilla ._.

I mean, Google are OK and all but... hmm ._.

Damn them and their browser's evident superiority! lol

---

### Post by chriskin on 2009-09-12
teh internets belongs to Googel :)

were you the one who clicked on my dropbox link just now?

---

### Post by hoppipolla on 2009-09-12
> **chriskin said:**
> teh internets belongs to Googel :)

were you the one who clicked on my dropbox link just now?

No that wasn't me... I will now though :)

Plus, I'm sure Chrome is rendering pages better... lol

---

