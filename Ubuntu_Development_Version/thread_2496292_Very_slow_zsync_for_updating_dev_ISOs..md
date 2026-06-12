---
title: "Very slow zsync for updating dev ISOs."
date: 2024-03-22
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-03-22
Since very early in the dev availability I have been updating to new versions of my current Xubuntu iiso file from the pending daily repos using zsync to save time and bandwidth.
Suddenly over the past few days it has become incredibly slow once the download actually starts, very often stopping completely.  Reading the input file is normal speed then it goes to about 2KiB/s and hovers around that speed but often going down to 0KiB/s.

Anyone else seen that? I realise it's not specifically about the dev version (at least I assume not) but I presume other users will be doing the same using zsync so I'm interested to see if I am the only person seeing this zsync problem.
I haven't tried a straight download of the ISO without using zsync yet but will try later to see if it's just that pending repo and maybe nothing to do with zsync which has always in the past worked as expected giving a download speed of about 5200KiB/s, close to my network speed.

---

### Post by oldfred on 2024-03-22
I have been using zsync to update Kubuntu 24.04 and have the same issue.
Often very slow, sometimes resets after a bit & is a bit faster.

While I can do the workaround to get Kubuntu Calamares installer to work, I want to have an ISO that works without workaround. 
Have not tested today's installer, but only a tiny amount of update to ISO.

While forum has been ok, I get major dropouts.
mtr [www.ubuntuforums.org](www.ubuntuforums.org)

First one for me is Miami, but years ago they said it was not them, so then last entry.
Is this then London & those on otherside of pond have same issue?
[FONT=monospace][COLOR=#000000] [/COLOR][COLOR=#000000]**port-channel11.core3.lon2.he.net**[/COLOR][COLOR=#000000] [/COLOR]
[/FONT]

---

### Post by ajgreeny on 2024-03-22
Like you, by the sounds of it, I update my iso files just about every other day and install the using KVM/QEMU, but then delete them and start again two days later just to see the progress of things and whether bugs have been squashed or are still present as seems to be the case with Xubuntu Noble more than in the previous LTS versions.

I seldom bother with the intermediate versions,  but stick with LTS only, but I i do feel this 24.04 version has been more trouble than usual.
Perhaps my memory of times past are mistaken?

---

### Post by guiverc on 2024-03-27
I can't really add anything here.. as I don't watch the terminal where my `zsync` runs usually 

I haven't run `zsync_noble` today for Xubuntu, but a day or two ago when last run and looking at the terminal output now I see tons of

```

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso:
###################- 99.6% 265.9 kBps         A  

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso:
###################- 99.7% 268.6 kBps         A  

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso:
###################- 99.8% 140.5 kBps         A  

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso:
###################- 99.9% 70.9 kBps         A  

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso:
###################- 99.9% 51.8 kBps         A  

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso:
#################### 100.0% 143.0 kBps DONE    A  

verifying download...checksum matches OK


```

which probably means it's SLOW for me too..

I've taken it for granted that Canonical infrastructure is slow at times, better at other times.

I just start my zsync script (*run on terminal on a monitor that isn't really in my normal eyesight anyway*) and ignore, if I want to see if its completed look up & I'll see the verified detail and some highlights of changes (some package details, diff [contrasted with last ISO I downloaded] etc) which is what I look for to know its completed.

Maybe we're all running zsync at the same time???

---

### Post by ajgreeny on 2024-03-27
I run zsync in terminal just like you, though I didn't realise there is any other way to use it, and I get exactly the same type of output as you with lots of auto-reconnections which didn't happen in previous versions as far as I can remember.

At least it doesn't crash and totally lose the partialy downloaded iso, and we can also, of course, be certain that the end result is not corrupt in any way.

---

### Post by Irihapeti on 2024-03-28
I'm seeing the same thing, and for some reason especially with Xubuntu. Almost down to dialup speeds at times. I've not been able to figure out any rhyme or reason for it. If we're all running zsync at the same time, how come it's started only lately? :)

---

