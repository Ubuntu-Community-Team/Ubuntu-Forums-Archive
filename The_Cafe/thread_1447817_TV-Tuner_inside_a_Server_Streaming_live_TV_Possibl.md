---
title: "TV-Tuner inside a Server? Streaming live TV? Possibly HD?"
date: 2010-04-05
forum: The Cafe
---

### Post by Kdar on 2010-04-05
I was reading somewhere before that it is possible to put TV-Tuner into Server and stream that to other computers and HTPCs.

Can I have a streaming live TV this way? or do recording?... etc

if it possibly, can I stream live HD TV to my HTPC?

Would TV-Tuner require something extra from a Server? in terms of specs/hardware.

---

### Post by Kdar on 2010-04-06
anyone?

---

### Post by aeiah on 2010-04-06
the easiest way is to implement a mythtv server / frontend setup. the only restriction you'll probably have as far as HD goes is network speed. wired network or at least wireless N will be necessary. you may even need gigabit ethernet for it to be reliable, especially if you're streaming to multiple clients at once.

---

### Post by eriktheblu on 2010-04-06
Hardware requirements are fairly modest, [http://www.mythbuntu.org/requirements](http://www.mythbuntu.org/requirements)

Many HD providers will encrypt their signals, this may require you to decrypt eternally (e.g. cable box).

I have a setup that does streaming over wireless G.. It works well enough for SD.

---

### Post by Kdar on 2010-04-06
> **aeiah said:**
> the easiest way is to implement a mythtv server / frontend setup. the only restriction you'll probably have as far as HD goes is network speed. wired network or at least wireless N will be necessary. you may even need gigabit ethernet for it to be reliable, especially if you're streaming to multiple clients at once.

Well, in my house there mostly just two people.. so there probably will not be streaming to multiple clients... at most 2 clients at one time.

I will have house wired before I will build this server/HTPC set up.

---

### Post by LowSky on 2010-04-06
> **aeiah said:**
> the easiest way is to implement a mythtv server / frontend setup. the only restriction you'll probably have as far as HD goes is network speed. wired network or at least wireless N will be necessary. you may even need gigabit ethernet for it to be reliable, especially if you're streaming to multiple clients at once.

Sorry to correct you but a few things in this statement are wrong or misleading

1. you will need a mythtv backend for the server, and a front end on any of the computer that will enjoy the content, or at least share the file locations that the content is recorded to.

2. To stream HD on requires only a normal 10/100Mb router connection. A gigabite router is better but not really required unless you are going to stream to  a bunch of people, 1 or 2 at the same time on a closed network is fine. You will need Wireless N for wifi though. Or a Wireless G that is rated at 108Mbps (Pre-draft N basically).

3. MythTv states you dont need much hardware, but in all honesty if you want the machine to work and not struggle, get some decent components. Especially if you want to transcode, remove or flag commercials, or recode more than one show at a time.

I'm not saying you need top of the line, but last Generations's tech is much better than trying to use geriatric old P4 or Athlon 64. Get a low end $60 dual core chip and you'll be happy. 

4.Get a TV tuner card that can decode analog signals. it will be better on the systems health and speed things along.

5 Also get a card that has two tuners on the card. This way you can watch and record at the same time if needed. And it save space for additional cards if you so need them.

6. TV Tuner card support can be hit or miss. My HVR-2250 is one of the best cards out there but it is sort of crippled in Linux. I have no analog support which I really dont care about, but it means I cant receive through my cable box but only by QAM or OTA. Check the models compatibility before buying.

7. Its annoying to set up MythTV. You might break things once in a while. Be prepared to scratch your head in deep thought on figuring out hat you broke. I honestly will admit Windows 7 Media Center works great for people who want to set up and forget. But MythTV wins in my book for not having DRM or requiring every PC to have Windows 7

---

