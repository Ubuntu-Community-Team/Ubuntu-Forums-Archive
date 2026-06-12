---
title: "Which Thinkpad Model/Processor"
date: 2020-01-06
forum: The Cafe
---

### Post by random turnip on 2020-01-06
I'm in the market for a "new" laptop and after looking around it seems there's quite a community around Thinkpads and after a brief look it seems like you get way more bang for your buck from a 2nd hand one over a cheaper new laptop.  I'm looking mainly at the T series (specifically thinking of T450 or T460 depending on what deals I can find, there seems to be a sharp increase in price for a T470) and looking to get the fastest machine I can for ~£200 or less.  I'm only going to be word processing (wannabe author) and web browsing while listening to music the majority of the time, maybe will be used for some light (indie, retro...) gaming from time-to-time, but that's not important.  Ideally I just want something that starts up quickly when using Ubuntu.

My main concern with these laptops are the processors.  I'm pretty out of date on hardware, I built a desktop probably 8 years ago now with an i5 2500K processor, which is quad core at 3.2GHz if I remember correctly, but looking at the most common T450 or T460 models, they only have 2.3/2.4GHz dual cores, which are surely going to be much slower than an already 8 year old machine unless I'm missing some basic understanding?  Now I don't need an amazing CPU, but this seems really low powered to me, or is this perfectly usable with an SSD?

I've seen processors in some models (not sure if these ones specifically) are upgradable, but this isn't something I want to spend money on right now, so will be run stock with only mod being an SSD if it doesn't come with one, maybe 8GB of RAM if it has much less too.  So how do these machines run with up-to-date Ubuntu stock considering they're 4 or 5 years old at this point?

Any other general tips on this would be handy, I've not kept an eye on general PC hardware in some time.

---

### Post by CatKiller on 2020-01-06
> **random turnip said:**
> My main concern with these laptops are the processors.  I'm pretty out of date on hardware, I built a desktop probably 8 years ago now with an i5 2500K processor, which is quad core at 3.2GHz if I remember correctly, but looking at the most common T450 or T460 models, they only have 2.3/2.4GHz dual cores, which are surely going to be much slower than an already 8 year old machine unless I'm missing some basic understanding?  Now I don't need an amazing CPU, but this seems really low powered to me, or is this perfectly usable with an SSD?

There have been instructions-per-clock improvements since Sandy Bridge - each cycle just gets more done. More importantly, the nominal clock speed just doesn't matter that much; my Sandy Bridge desktop machine *can* go to 4.2 GHz, but spends most of its time at 1.6 GHz. My Ryzen desktop machine *can* go to 4.3 GHz, but spends most of its time at 800 MHz, and is *way* faster than the old machine.

All computers, especially a machine that's used for stuff like word processing and web browsing, spends almost all of its time doing no-ops while it's waiting for input from the user. You want it to be in the lowest possible power state while it's doing that; to save battery for a laptop and to prevent noise on a desktop.

What users notice is *latency*: the time between doing a thing and getting a result. Things like using an SSD (big boost), RAM speed, architectural efficiency, smooth user interface from running it on a gpu, and so on, are *much* more important for the user than raw clock speed.

---

### Post by wolftrax on 2020-01-06
I bought a lenovo thinkpad T530 with a  Intel(R) Core(TM) i5-3320M CPU @ 2.60GHz   and this machine really runs great.  I am very happy with it. it has 4 gigabyte of ram but can be upgraded and I been running ubuntu and fedora and ubuntu studio on it and its simply the best computer I ever owned.  

 I ran freeBSD based liveCDs on it but it does however not boot up on open indiana live CDs and I don't know why but it runs my Ubuntu system very well and as said I never had a better laptop than this.  I got it three months ago.

---

### Post by random turnip on 2020-01-09
> **wolftrax said:**
> I bought a lenovo thinkpad T530 with a  Intel(R) Core(TM) i5-3320M CPU @ 2.60GHz   and this machine really runs great.  I am very happy with it. it has 4 gigabyte of ram but can be upgraded and I been running ubuntu and fedora and ubuntu studio on it and its simply the best computer I ever owned.  

 I ran freeBSD based liveCDs on it but it does however not boot up on open indiana live CDs and I don't know why but it runs my Ubuntu system very well and as said I never had a better laptop than this.  I got it three months ago.

Well that's pretty high endorsement.  I may well be worrying about nothing, after all it will only ever be subject to pretty basic tasks.

> **CatKiller said:**
> There have been instructions-per-clock improvements since Sandy Bridge - each cycle just gets more done. More importantly, the nominal clock speed just doesn't matter that much; my Sandy Bridge desktop machine *can* go to 4.2 GHz, but spends most of its time at 1.6 GHz. My Ryzen desktop machine *can* go to 4.3 GHz, but spends most of its time at 800 MHz, and is *way* faster than the old machine.

All computers, especially a machine that's used for stuff like word processing and web browsing, spends almost all of its time doing no-ops while it's waiting for input from the user. You want it to be in the lowest possible power state while it's doing that; to save battery for a laptop and to prevent noise on a desktop.

What users notice is *latency*: the time between doing a thing and getting a result. Things like using an SSD (big boost), RAM speed, architectural efficiency, smooth user interface from running it on a gpu, and so on, are *much* more important for the user than raw clock speed.

Thank you for all of this info, seems like I'm likely worrying about nothing (or the wrong thing at least).  Intend on buying a new SSD to put in the machine regardless of what it comes with and if it came with less than 8GB of RAM then probably upgrading that as well, I never considered the RAM speed as important, but it makes sense when you think of it.  So basically, these standard of laptop should deal with the sort of tasks I'd be asking of it quickly enough that I'm not going to be frustrated waiting for it, which is all I'm really after.

---

### Post by CatKiller on 2020-01-09
> **random turnip said:**
> Thank you for all of this info, seems like I'm likely worrying about nothing (or the wrong thing at least).  Intend on buying a new SSD to put in the machine regardless of what it comes with and if it came with less than 8GB of RAM then probably upgrading that as well, I never considered the RAM speed as important, but it makes sense when you think of it.  So basically, these standard of laptop should deal with the sort of tasks I'd be asking of it quickly enough that I'm not going to be frustrated waiting for it, which is all I'm really after.

Exactly. With the MHz Wars of the late 90s speed was somewhat important, but those processors were all single-core at a fixed frequency. "Race to sleep" is how it generally works with modern machines - get small tasks done really quickly, then drop back into the lowest power states - with huge improvements in interconnects so that you aren't waiting for data to be shuffled about.

---

### Post by mastablasta on 2020-01-10
i would invest in 5th or even 6th gen intel for laptop. mostly because they had a bit more significant power improvements. however if battery is not a big concern then 3rd and 4th gen will do fine.

---

### Post by bunny9000 on 2020-01-11
On the issue of RAM - I'd say 8GB is a good, fairly future proof amount. Even if you're just browsing the internet modern browsers can get pretty hungry for ram and if you end up having several tabs, a youtube audio video playing and few docs open you can pass 4GB without really noticing. You can get away with 4GB if you're a 1 tab kinda person. But tabs were invented to be used :)

Regarding retro gaming I brought a $30 desktop with an intel core 2 duo. That's a 2 core processor without hyperthreading and it had 4GB RAM and windows xp. I then ran emulators that allowed me to run the classics such as the original Doom although those emulators can run on windows 10 especially if you get games from GOG. But for the authentic experience you can't beat the physical disks and the OS they were designed on (just don't connect XP outside your lan). Most modern integrated graphics chips can get stuff like Quake 2 / 1 & even quake 3 running pretty smoothly. A HD545 which runs at around $50 can handle all the early / mid 90s stuff fine and that was still running on the core 2 duo. Had a lot of fun with that till I had to put the games to one side and use my computers for real work :)

I upgraded one of my old DDR2 machines recently from 2GB to 4GB RAM and it cost me about $5. I'm using it right now to write this ever growing post. six tabs, some youtube, a doc and some file tranfers and it's only using about 3GB of it's 4GB total RAM.

For writing I actually preffer a screen in 4:3 rather than 16:9 aspect ratio.

Although the advantages of the more modern stuff is that they use less electricity for the same amount of computing power.

I'd avoid anything with an atom in it or the AMD equivilant. 2 or 3 cores, 4 to 8GB RAM. You can get kingston branded 160GB SSDs for around $30 or less. They're not good for big file transfers, but they have enough cache to quickly boot the OS and load applications. I've got a couple in my older machines and they really do perk them up.

Not really an answer to your question, but the rambling may be of some use. :cool:

---

### Post by mastablasta on 2020-01-13
actually old games run well in wine. though some do not run so perfect. or you can install them.

i also found a few engines ported and they work relatively well. there is jdoom or whatever it's called these days. it gives doom a whole new life. besides that there is zandornum for that old feel. there are quake implementations. lately we've had fun with Open Jedi knight and Open Jedi Academy. academy runs better. OpenMW for morrowind is another good one. it's like having native port. i installed many xp games on wine. Far Cry 2 that had issues under XP on same PC works smoothly and higher setting in wine. :o i am dual booting windows XP and Kubuntu on a Single core Amd CPU, 4 GB DDR2 and nvidia GT730 card. some games i had problem installing in wine, but i could move windows install to Linux and then they worked. some games i still haven't tried to install but i read they have issues. so i need more time to see if they would work. i had this one for 16 years now. thought it would die out by now, but it is still working well. changed the HDD, changed the GPU and PSU and it is still working well.

but still like i said in laptop batter is usually more important which is why i would get a more power efficient CPU. game might not work as well there as they do on desktop but the battery would last and it's portable machine.

---

### Post by tasket on 2020-02-03
I'm also looking for a newer system.

If you're into open source firmware at all, the Lenovo G505s is an interesting choice. It has an AMD A10 quad core processor, advanced virtualization features, up to 16GB RAM and Coreboot BIOS can be installed on it. I found out about it because some Qubes OS users like it, and I also run Qubes in addition to Ubuntu.

Another advantage for an AMD-based system is they're significantly less prone to the kind of side-channel vulnerabilities that Intel has become infamous for. This is one reason why Intel CPUs have fared so poorly compared to AMD in benchmarks lately... the firmware 'fixes' for these vulnerabilities take a severe toll. Most of Intel's advantage over the last 20 years was built on lies, threats and cheating. For example, they threatened PC makers with price retaliation if their PC product lines weren't at least 85% Intel. And they have spent years denying they will ever pay the fines they owe from the resulting court battle which they lost. And there is this little [chestnut]("https://www.reddit.com/r/Amd/comments/e4klj0/intel_is_still_sneakily_sabotaging_amd/"). So Intel are outlaws and also show they don't care about their customers &#8211;&#8211; Avoid!

If you want something newer than a 2013 system, there are a number of Thinkpads that feature AMD CPUs on up through the current T495. But I think if I were to buy something so new, I would hold out for a laptop based on the [impressive]("https://www.anandtech.com/show/15324/amd-ryzen-4000-mobile-apus-7nm-8core-on-both-15w-and-45w-coming-q1") new Ryzen 4000 family. So probably what I'd like to have is a "T4005" or whatever Lenovo would call the next iteration.

---

### Post by mastablasta on 2020-02-05
the new ryzen 400 will have to get drivers in linux first. so new is again not best option in linux.

---

