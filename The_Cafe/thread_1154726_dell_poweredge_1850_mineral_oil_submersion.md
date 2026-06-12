---
title: "dell poweredge 1850 mineral oil submersion"
date: 2009-05-10
forum: The Cafe
---

### Post by dpsleep on 2009-05-10
That's right, a dell poweredge 1850 server [s]blade[/s] submerged in mineral oil. Why? Because otherwise it sounds like a lawn mower on crack, which doesn't work too well in an apartment. I just got everything powered up and seeing how everything is doing.[s] I only have one problem so far, I cant seem to be able to get ipmi to work. Any suggestions?[/s]

Otherwise it works great, needs a little more oil (I bought out 4 wallmarts' supply), and silent. :)

[IMG]http://imgur.com/JVe.jpg[/IMG]

 Also, anyone know where I could get a male to female scsi sca 80 pin u320 cable?

[IMG]http://imgur.com/Jye.jpg[/IMG]
[IMG]http://imgur.com/Jy.jpg[/IMG]
[IMG]http://imgur.com/Jz1K.jpg[/IMG]
[IMG]http://imgur.com/Jz2p.jpg[/IMG]
[IMG]http://imgur.com/Jz4A.jpg[/IMG]
[IMG]http://imgur.com/Jz5e.jpg[/IMG]

---

### Post by stwschool on 2009-05-10
Err wouldn't submerging a computer in liquid make it go bang? *confused beyond belief*

---

### Post by 3rdalbum on 2009-05-10
> **stwschool said:**
> Err wouldn't submerging a computer in liquid make it go bang? *confused beyond belief*

Not all liquid is conductive to electricity :-)

I suspect the computer's heat transfers to the oil, and the oil's convection currents transfers the heat to the air above the surface of the oil.

Convection currents are basically where warm liquid rises the the top, gets cooled, drops, and gets replaced by newly-warmed liquid from the bottom.

---

### Post by .Maleficus. on 2009-05-10
> **3rdalbum said:**
> Not all liquid is conductive to electricity :-)

I suspect the computer's heat transfers to the oil, and the oil's convection currents transfers the heat to the air above the surface of the oil.

Convection currents are basically where warm liquid rises the the top, gets cooled, drops, and gets replaced by newly-warmed liquid from the bottom.
IIRC, you are correct.  The same can be done with vegetable oil, except after a while the vegetable oil will cook, which is why nobody does it :p.  I've considered submersion cooling, but I'm not sure about how effective it is.  I think I'll stick with liquid cooling.

---

### Post by stwschool on 2009-05-10
> **3rdalbum said:**
> Not all liquid is conductive to electricity :-)

I suspect the computer's heat transfers to the oil, and the oil's convection currents transfers the heat to the air above the surface of the oil.

Convection currents are basically where warm liquid rises the the top, gets cooled, drops, and gets replaced by newly-warmed liquid from the bottom.
But wouldn't that make it get all messy? I mean really who wants to clean oil off their processor?

---

### Post by mips on 2009-05-10
> **stwschool said:**
> But wouldn't that make it get all messy? I mean really who wants to clean oil off their processor?

Why?

There is no need to clean the computer. It's submerged so it will not collect any dust.

---

### Post by pwnst*r on 2009-05-10
i understand how it works, but doesn't that put extra strain on the fan components having to "trudge" through the density?

---

### Post by artir on 2009-05-10
The fans are disabled in this cases.

---

### Post by pwnst*r on 2009-05-10
> **artir said:**
> The fans are disabled in this cases.

ah, tells you how much reading up i've done on this kind of set up.

---

### Post by HappyFeet on 2009-05-10
Here is another one submersed in mineral oil and the cpu cooled with liquid nitrogen. This photo was taken a the Gigabyte overclocking national championships.

---

### Post by pwnst*r on 2009-05-10
lol probably 4k worth of equipment in a kitty litter box

---

### Post by drawkcab on 2009-05-10
> **HappyFeet said:**
> Here is another one submersed in mineral oil and the cpu cooled with liquid nitrogen. This photo was taken a the Gigabyte overclocking national championships.

I'm waiting for the portable version.

---

### Post by dpsleep on 2009-05-10
> **pwnst*r said:**
> lol probably 4k worth of equipment in a kitty litter box

lol, I didn't see it before... but now I think of a litter box every time I look at it. hope my cat doesn't think the same.

the server is working very well, heats up my apartment nicely. this is my second mineral oil submersion and I love it. sure I could have liquid cooled it, but it just isn't as cool.

I really wish I could find a way to extend the SCSI ports out of the box, but the only cables I could find are u160 and that just wont do.

---

### Post by pwnst*r on 2009-05-11
> **dpsleep said:**
> lol, I didn't see it before... but now I think of a litter box every time I look at it. hope my cat doesn't think the same.

the server is working very well, heats up my apartment nicely. this is my second mineral oil submersion and I love it. sure I could have liquid cooled it, but it just isn't as cool.

I really wish I could find a way to extend the SCSI ports out of the box, but the only cables I could find are u160 and that just wont do.

actually i was talking about happy feet's pic =)  that's cool that you've done that though.  i want to do that with my now replaced old gaming rig.

---

### Post by LightB on 2009-05-11
> **HappyFeet said:**
> Here is another one submersed in mineral oil and the cpu cooled with liquid nitrogen. This photo was taken a the Gigabyte overclocking national championships.

Wow, amazing, but kind of silly and definitely dangerous.

Anyways, I heard water can build up over time when you do this mineral oil thing.

---

### Post by toupeiro on 2009-05-11
> ipmitool delloem "TAKEMEOUTOFTHISSTUFF"

BTW, have fun with the warranty :P

EDIT: after taking a closer look at the picture, I am very tempted to call BS.. I haven't seen the Dell blades, but I have seen the HP and Sun blades and quite frankly you would NOT be able to power them up without a chassis let alone get anything to post...  Blade PSU's are almost always attached via a chassis blackplane and the PSU's have hot-plug outlets, (NOT corded...).  Otherwise, they would be servers, not blades...  Chassis are also several rack units high and WELL over 100 pounds bare metal, or in other words, MUCH bigger than a litter box...

---

### Post by dmizer on 2009-05-11
Mineral oil is a TERRIBLE heat conductor; keep a close eye on your temperatures.

---

### Post by dpsleep on 2009-05-11
> **toupeiro said:**
> BTW, have fun with the warranty :P

EDIT: after taking a closer look at the picture, I am very tempted to call BS.. I haven't seen the Dell blades, but I have seen the HP and Sun blades and quite frankly you would NOT be able to power them up without a chassis let alone get anything to post...  Blade PSU's are almost always attached via a chassis blackplane and the PSU's have hot-plug outlets, (NOT corded...).  Otherwise, they would be servers, not blades...  Chassis are also several rack units high and WELL over 100 pounds bare metal, or in other words, MUCH bigger than a litter box...

This isn't a litter box, its a 67 Qt. Tupperware container. And its has 8.25 Gal. of mineral oil in it.

The heat isn't too bad, I calculated 33 million digits of pi with the cpus clocked all the way. at the end I had a ambient temp of 48c and a core temp of 68c. ipmi says they can go up to 85-90c but 70c is a little high for me. I think I'm going to hook up a radiator to it.

as far as the warranty goes, I got the server for free so... never really had one.

There is no water build up with mineral oil. puget systems is down the street from me [(the guys that did the mineral oil submersion video)]("http://www.youtube.com/watch?v=PtufuXLvOok") and they have had it running for around 2 years now. the guy that uses it as his everyday hasn't had any problems besides stickers falling off and oil seeping up the cables.

like I said this is the second one I have done, the first has been running for a year as a mythtv server backend.

[IMG]http://imgur.com/Jye.jpg[/IMG]
[IMG]http://imgur.com/Jy.jpg[/IMG]
[IMG]http://imgur.com/Jz1K.jpg[/IMG]
[IMG]http://imgur.com/Jz2p.jpg[/IMG]
[IMG]http://imgur.com/Jz4A.jpg[/IMG]
[IMG]http://imgur.com/Jz5e.jpg[/IMG]

---

### Post by mxboy15u on 2009-05-11
That apartment looks like a nerd's fantasy. Cool setup!

---

### Post by toupeiro on 2009-05-11
Got it.  Its a server.  Not a server blade.  This is what was throwing me..

This is a dell server blade...

[IMG]http://www.shopricom.com/items/www.shopricom.com/photos/Image8q17I32W6W_full.jpg[/IMG]

quite a large difference between the two.  It would take about 3 of these side, by side, by side to be as wide as an 1850 :)  

I know you got it for free, but have you considered your power bill, and how much money per year you could save by building a *desktop*?  Probably enough money to .. *buy a desktop* ;)

---

### Post by 3rdalbum on 2009-05-11
If mineral oil works so well as a coolant, and doesn't cause problems, why doesn't anyone ship any computers pre-oiled? I'm not challenging you, I'm just wondering.

---

### Post by mips on 2009-05-11
> **3rdalbum said:**
> If mineral oil works so well as a coolant, and doesn't cause problems, why doesn't anyone ship any computers pre-oiled? I'm not challenging you, I'm just wondering.

It's really not practical for most people. It's something for nerds.

And then there is the weight...

---

### Post by dpsleep on 2009-05-11
> **toupeiro said:**
> Got it.  Its a server.  Not a server blade.  This is what was throwing me..

This is a dell server blade...

[IMG]http://www.shopricom.com/items/www.shopricom.com/photos/Image8q17I32W6W_full.jpg[/IMG]

quite a large difference between the two.  It would take about 3 of these side, by side, by side to be as wide as an 1850 :)  

I know you got it for free, but have you considered your power bill, and how much money per year you could save by building a *desktop*?  Probably enough money to .. *buy a desktop* ;)


oh, ok. sorry, I really don't know much about rack mount servers and what a blade is. I just thought, because of the word blade, it just meant a thin rack mount server. silly me...

as far as a desktop, I have desktops. I'm using this as a server, not as  a PC. not saying I have allot to serve, but I want something to be on all the time and be fast enough to host a site or two. and I use my desktop and laptop regularly, so I don't want to be in the middle of a game and have someone load a php page and you get the idea. sure it will increase my power bill, but my power is cheap so my pocket wont be hit too bad.

really if I could I would sell it and buy a desktop/server, but I can't and I've had it sitting around for so long that I just wanted to make use of it.

---

### Post by dpsleep on 2009-05-11
> **3rdalbum said:**
> If mineral oil works so well as a coolant, and doesn't cause problems, why doesn't anyone ship any computers pre-oiled? I'm not challenging you, I'm just wondering.

It's messy... and I don't know. it really doesn't cause any harm to the computer. if I wanted to put down the $$ I could have water cooled it. But I didn't. really mineral oil works allot better than people think, especially if you get light mineral oil. when its warm its almost the same as water as far as thickness. plus, its soooo quiet, so very very quiet. if it wasn't for the lights I wouldn't know if it was on.

And I just love the look on people's face when they see a computer submerged in oil.

There are allot of things people do that could be done better a different way, like smoking and breathing. sure it doesn't work as well, but they enjoy it.

p.s. mineral oil does not cause cancer :)

---

