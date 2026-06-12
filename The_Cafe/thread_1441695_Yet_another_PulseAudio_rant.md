---
title: "Yet another PulseAudio rant"
date: 2010-03-29
forum: The Cafe
---

### Post by PC_load_letter on 2010-03-29
So, I added the Mozilla daily PPA to get a taste of Thunderbird 3. To my surprise, and in order for the new versions of Thunderbird to install, esound was to be removed and PulseAudio installed. WTF?

Why does Firefox or Thunderbird depend on PulseAudio? I do feel strongly about PulseAudio in the sense that I believe it neither lives up to my requirements, nor that it installs or behaves nicely on my computers. Does this mean I will not be able to install Thunderbird 3?!!!! :(:(

---

### Post by dragos240 on 2010-03-29
> **PC_load_letter said:**
> So, I added the Mozilla daily PPA to get a taste of Thunderbird 3. To my surprise, and in order for the new versions of Thunderbird to install, esound was to be removed and PulseAudio installed. WTF?

Why does Firefox or Thunderbird depend on PulseAudio? I do feel strongly about PulseAudio in the sense that I believe it neither lives up to my requirements, nor that it installs or behaves nicely on my computers. Does this mean I will not be able to install Thunderbird 3?!!!! :(:(

No idea why that would be a dependency. Also, there is nothing wrong with pulseaudio, it's just that ubuntu's implementation of pulseaudio is awful. You should download the deb of thunderbird, and edit the file containing the deps inside.

---

### Post by PC_load_letter on 2010-03-29
PulseAudio flat out didn't produce any sound on my sound card, M-Audio 2496 w/ Karmic. I understand PA is tolerable for some, but it wasn't in my case. 

I'm not trying to complain about PA here as much as the required dependency, which doesn't make any sense to me.

Anyway, thanks for the advice, I'll try the deb file.

---

### Post by SmittyJensen on 2010-03-29
> **dragos240 said:**
> No idea why that would be a dependency. Also, there is nothing wrong with pulseaudio, **it's just that ubuntu's implementation of pulseaudio is awful**. You should download the deb of thunderbird, and edit the file containing the deps inside.
got any proof to back that up?

---

### Post by pt123 on 2010-03-29
I found deleting the .pulse folder from previous installations helped when upgrading to a new one. In Karmic pulse has been great for me.

---

### Post by dragos240 on 2010-03-29
> **SmittyJensen said:**
> got any proof to back that up?

No, but ubuntu's PA didn't work at all for me. Arch and gentoo worked just fine. Personal experience, plus one of the devs for PA said it was the implementation that was the issue.

---

### Post by Regenweald on 2010-03-29
We are ranting on buttons nowadays, pulseaudio just doesn't have that arrgh! zing! anymore. Sorry.

---

### Post by Simian Man on 2010-03-29
> **SmittyJensen said:**
> got any proof to back that up?

Not exactly proof, but the lead Pulseaudio developer certainly believes that [Ubuntu does a poor job]("http://0pointer.de/blog/projects/pa-in-ubuntu.html") with it.  I personally have less sound troubles in Fedora than I did with Ubuntu, but there likely are others with the opposite experience.

---

### Post by Mr. Picklesworth on 2010-03-29
> **PC_load_letter said:**
> PulseAudio flat out didn't produce any sound on my sound card, M-Audio 2496 w/ Karmic. I understand PA is tolerable for some, but it wasn't in my case. 

I'm not trying to complain about PA here [...].

Your thread title speaks to the contrary ;)

On the topic of PA, it seems to be much better settled in with Lucid, now that rtkit and all that have landed in the appropriate upstream places. For me, it's all feeling very elegant, and judging by the complete lack of PA discussion amongst Lucid users, I would guess that to be the case for most others. So, I recommend you try it again when that rolls in.

Seems odd that anything Mozilla would depend on it, since they're more likely to use something very abstract, being that they target three platforms at once.

---

### Post by l-x-l on 2010-03-29
I personally cringe whenever I see package(s) update for pulseaudio for Ubuntu. Usually it breaks things on my laptop that I have to refix. I think going forward I'll be pinning that package(s) once I get it working properly so that I no longer have to fix.

---

### Post by l-x-l on 2010-03-29
> **Mr. Picklesworth said:**
> Your thread title speaks to the contrary ;)

On the topic of PA, it seems to be much better settled in with Lucid, now that rtkit and all that have landed in the appropriate upstream places. For me, it's all feeling very elegant, and judging by the complete lack of PA discussion amongst Lucid users, I would guess that to be the case for most others.

I sincerely hope you're right about lucid being a breakthrough for PA. On the positive note though, when things break I'm forced to fix it which in turns forces to learn about the guts of Ubuntu & Linux in general. I get a chance to explore my laptop/OS in a way I never did with Windows.

---

### Post by PC_load_letter on 2010-03-29
> **Mr. Picklesworth said:**
> Your thread title speaks to the contrary ;)

On the topic of PA, it seems to be much better settled in with Lucid, now that rtkit and all that have landed in the appropriate upstream places. For me, it's all feeling very elegant, and judging by the complete lack of PA discussion amongst Lucid users, I would guess that to be the case for most others. So, I recommend you try it again when that rolls in.

Seems odd that anything Mozilla would depend on it, since they're more likely to use something very abstract, being that they target three platforms at once.

This is how it happened:
- I added the Mozilla daily PPA w/ sudo add-apt repository ....
- sudo apt get update && sudo apt get upgrade
- Nothing happened, so I fired up update manager which told me that a previous upgrade attempt has failed and I should consider  a partial upgrade. The software available for update were all from the Mozilla daily PPA.
- I clicked on partial upgrade, it said something is gonna be removed, so I clicked "details", only to find out that esound will be removed and PA is among the packages to be installed!!!!!

- I cancelled and posted this :D

---

