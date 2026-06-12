---
title: "Ubuntu, Remove None-Free-Packages"
date: 2009-11-22
forum: The Cafe
---

### Post by GreenDance on 2009-11-22
Hi, does anyone know to remove the none-free-packages in Ubuntu to make it completely a free software operating system.

---

### Post by -grubby on 2009-11-22
It would be easier to just install [GNewSense](http://www.gnewsense.org/).

However, I don't think you fully realize the implications of removing every piece of proprietary software on your system.

Do you use Flash? Want 3d acceleration for an Nvidia or ATI card?

---

### Post by Psumi on 2009-11-22
> **-grubby said:**
> Do you use Flash? Want 3d acceleration for an Nvidia or ATI card?

Or even,

Do you want to play DVDs, MP3s (patents end in 2018 for MP3s), WMVs, etc?

---

### Post by GreenDance on 2009-11-22
oh i see,

do Ubuntu pay for these restricted packages?

---

### Post by NoaHall on 2009-11-22
Non-free != cost money
Non-free = closed source, proprietary software.

Ubuntu doesn't pay anyone for them, no.

---

### Post by GreenDance on 2009-11-22
> **NoaHall said:**
> Non-free != cost money
Non-free = closed source, proprietary software.

Ubuntu doesn't pay anyone for them, no.

interesting, so why does gNS remove them for?

*(learning ;))*

---

### Post by RiceMonster on 2009-11-22
> **GreenDance said:**
> interesting, so why does gNS remove them for?

*(learning ;))*

Because they don't have access to the source code, and they are not considered Free Software by the FSF.

---

### Post by NoaHall on 2009-11-22
> **GreenDance said:**
> interesting, so why does gNS remove them for?

*(learning ;))*

Well, some people (ZankerH might want to share his views on it with you, try PM'ing him about it) consider closed-source software evil, and immoral.

---

### Post by GreenDance on 2009-11-22
With the Internet now a days these restricted packages are needed aren't they?

---

### Post by NoaHall on 2009-11-22
> **GreenDance said:**
> With the Internet now a days these restricted packages are needed aren't they?

Well, to be honest, yes. nvidia can't open-source their drivers, because there is code there from other people, and it'd be a huge legal mess, and their competition would be able to see , etc,etc. Flash won't be open-sourced, but with HTML 5 support coming soon for the major browser(I.E, whether you like it or not), we might see the death of Flash(I hope). There are other ways to get around things, but it's usually best to use the closed source software.

---

### Post by sisco311 on 2009-11-22
You can use [vrms]("apt://vrms") (virtual Richard M. Stallman) to get a list of non-free and contrib packages which are currently installed on your system.

```
vrms -e
```

---

### Post by GreenDance on 2009-11-22
> **NoaHall said:**
> Well, to be honest, yes. nvidia can't open-source their drivers, because there is code there from other people, and it'd be a huge legal mess, and their competition would be able to see , etc,etc. Flash won't be open-sourced, but with HTML 5 support coming soon for the major browser(I.E, whether you like it or not), we might see the death of Flash(I hope). There are other ways to get around things, but it's usually best to use the closed source software.

Thank You :popcorn::KS

Thanks for your signature "BBC" ;)

---

### Post by supermelon928 on 2009-11-22
ummmm

Applications > Add/Remove

amidoinitrite?

---

### Post by Praxicoide on 2009-11-22
> **sisco311 said:**
> You can use [vrms]("apt://vrms") (virtual Richard M. Stallman) to get a list of non-free and contrib packages which are currently installed on your system.

```
vrms -e
```

rofl! what an apt name.

---

### Post by AndyCooll on 2009-11-22
> **GreenDance said:**
> With the Internet now a days these restricted packages are needed aren't they?
It depends on what your personal view is of "need".

You don't "need" Adobe Flash to access and use the Internet. However having this installed certainly enriches your Internet experience. Furthermore using (free as in freedom) alternatives to Adobe Flash such as swfdec and gnash will work on the majority of webpages when Flash is required. However these alternatives are not at the moment as developed or feature rich, and unfortunately though most websites work ...some don't. 

For GnewSense users (for instance) "free as in freedom" is the most important aspect of their computing experience. And they are willing to forego the ability to access certain websites in order to stand by their principles. And fair play to them. To use an admittedly bad analogy, vegetarians are willing to forego eating meat in order to stand by the principles they strongly believe in. 

Some choose "free as in freedom" where practical. So, these people in principle follow the "free as in freedom" viewpoint ...but not at all costs. They prefer "free as in freedom" software and are prepared to tolerate some inconveniences, but in the end a working system matters.

And many simply want a fully-functioning system that works. Free for them means "no cost". How it works doesn't matter, and the fact that they don't have access to the code is of little importance. They simply want the best tool for the job.

How far you choose to follow the principles of freedom is up to you, and what is most important to you in your computing experience.

:cool:

---

### Post by supermelon928 on 2009-11-22
> **Praxicoide said:**
> rofl! what an apt name.

sudo! what an apt-get name.

---

### Post by phrostbyte on 2009-11-22
You can replace Flash with Gnash. I find that it can play a large variety of standard Flash animations, but it chokes a bit on YouTube (currently). For YouTube you can use a Greasemonkey script that replaces the Flash video with a embedded video player like vlc.

Intel video drivers are open source, and the open source ATI drivers have full 2D acceleration and partial 3D acceleration. MP3/DVD player uses FOSS software, which may be patent encumbered, but it's still FOSS and I'm pretty sure vrms approves.

It's really not that difficult to have a fully FOSS system.

---

### Post by NoaHall on 2009-11-22
> **supermelon928 said:**
> sudo! what an apt-get name.

Sudo isn't related to apt-get at all. That's like saying "root, what a apt-get name". I've never apt-got root.

---

### Post by Psumi on 2009-11-22
> **phrostbyte said:**
> You can replace Flash with Gnash. I find that it can play a large variety of standard Flash animations, but it chokes a bit on YouTube (currently). For YouTube you can use a Greasemonkey script that replaces the Flash video with a embedded video player like vlc.

what if you want to watch homestar runner and access all the easter eggs?

Gnash chokes on some of homestar runner as well, sometimes buttons will not press. Gnash also cannot render blur, and sometimes, gnash renders too fast for the sound to catch up on.

---

### Post by cariboo on 2009-11-22
This may not be what the op is looking for, but Karnmic now gives you the option to install free software only. I haven't tried it yet so I can't say how it works.

---

### Post by castrojo on 2009-11-22
Hitting F6 (or something) when you first boot will give you a free software only option on install. I think it's been there since Intrepid-ish?

---

### Post by cariboo on 2009-11-22
Thanks, that's where I saw the option.

---

### Post by Psumi on 2009-11-22
Not to mention the square enix site: [http://www.square-enix.com/na/](http://www.square-enix.com/na/)

Gnash chokes on it as well slightly.

---

