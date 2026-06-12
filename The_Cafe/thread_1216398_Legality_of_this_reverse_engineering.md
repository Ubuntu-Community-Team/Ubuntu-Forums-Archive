---
title: "Legality of this reverse engineering"
date: 2009-07-18
forum: The Cafe
---

### Post by linuxguymarshall on 2009-07-18
I have been reading articles on reverse engineering and the legal effects of it. I keep finding that the only way you are able to be charged with a crime is if you accept the EULA and it states that you can not reverse engineer. 

So I give you this scenario :

I am wanting to create a native Linux client of the Half-Life 1 game. This will not connect to the official Half-Life servers for anything, all it will do is use the existing Half-Life textures, models, sounds etc to make it all work. So where under U.S. law would this come at. 

Sorry for the rather nontechnical explanation. I am rather tired at the moment and don't have the patience to type out a full technical summary. Feel free to ask questions if you have them though.

---

### Post by eragon100 on 2009-07-18
> **linuxguymarshall said:**
> I have been reading articles on reverse engineering and the legal effects of it. I keep finding that the only way you are able to be charged with a crime is if you accept the EULA and it states that you can not reverse engineer. 

So I give you this scenario :

I am wanting to create a native Linux client of the Half-Life 1 game. This will not connect to the official Half-Life servers for anything, all it will do is use the existing Half-Life textures, models, sounds etc to make it all work. So where under U.S. law would this come at. 

Sorry for the rather nontechnical explanation. I am rather tired at the moment and don't have the patience to type out a full technical summary. Feel free to ask questions if you have them though.

If it's commercial: definitely illegal. You didn't make that content, so you can't make money from it without permission from the creators.

If it's not commercial: it *might* fall under the American fair use clause. Ask a lawyer :wink:

---

### Post by linuxguymarshall on 2009-07-18
Well my idea would only to be to distribute the binaries that way a person would still have to have a copy of the actual game's files and they would just have to copy them into the appropriate directories.

And it would not be commercial, it would be 100% free and open source under the zlib/libPNG license

---

### Post by hetx on 2009-07-18
Pretty sure Half-Life comes with a "don't mess with the code" clause, for the core of it.

---

### Post by aesis05401 on 2009-07-18
> **linuxguymarshall said:**
> Well my idea would only to be to distribute the binaries that way a person would still have to have a copy of the actual game's files and they would just have to copy them into the appropriate directories.

And it would not be commercial, it would be 100% free and open source under the zlib/libPNG license

This falls under copyright law.  Unless the company in question wants to grant you some sort of waiver this behavior would clearly violate fair use.

Under most circumstances the only copying of copyrighted material that is allowed without explicit license is for 'fair use,' which includes making a single copy on archive media for yourself.  And even that only holds water if you can prove that you were granted a license to possess the material in the first place (ie: you paid for a game license).

---

### Post by linuxguymarshall on 2009-07-18
> **aesis05401 said:**
> This falls under copyright law.  Unless the company in question wants to grant you some sort of waiver this behavior would clearly violate fair use.

Under most circumstances the only copying of copyrighted material that is allowed without explicit license is for 'fair use,' which includes making a single copy on archive media for yourself.  And even that only holds water if you can prove that you were granted a license to possess the material in the first place (ie: you paid for a game license).



I was afraid of this. 
Well thanks anyways guys. Stupid DMCA and the idea of copyright

---

### Post by linuxguymarshall on 2009-07-18
> **hetx said:**
> Pretty sure Half-Life comes with a "don't mess with the code" clause, for the core of it.

Once again, I would be using an entirely different game engine just reprogramming that engine to act like the GoldSrc (Half-Life) engine.

---

### Post by mmix on 2009-07-18
openarena, i recommend.

[http://www.openarena.ws/](http://www.openarena.ws/)

---

### Post by Mehall on 2009-07-18
Erm... wait a minute...

You can freely get the Doom engine, and derivatives, it's just the .WAD files that are illegal to redistribute.

if he makes his OWN version of the game engine, utilising nothing of the original, and then has users copy over the textures and stuff, the content (as with the .WAD ) then surely it's fair?

---

### Post by aesis05401 on 2009-07-18
> **linuxguymarshall said:**
> I was afraid of this. 
Well thanks anyways guys. Stupid DMCA and the idea of copyright

I feel your pain.  

I hope you find a good way to accomplish your goal without ending up incarcerated ;)

---

### Post by aesis05401 on 2009-07-18
> **Mehall said:**
> Erm... wait a minute...

You can freely get the Doom engine, and derivatives, it's just the .WAD files that are illegal to redistribute.

if he makes his OWN version of the game engine, utilising nothing of the original, and then has users copy over the textures and stuff, the content (as with the .WAD ) then surely it's fair?

If the people doing the copying are in America, and the material has not been released under some sort of license or copyright waiver, copyright protection is automatic.  

Your scenario would be harder to prosecute than if he were redistributing the textures etc... but equally against the law. 

I don't know where these forums are hosted, but when I post on American sites I am actually acquiring copyright simply by posting in a public place.  As the OP mentions, the DMCA stuff is pretty messed up over here.

To be clear, though, we are talking about files specific to a game that are distributed by a publisher for use with their paid services, right?  If the files in question were generic enough you might have some wiggle room... (ie: similar to a 'obvious to a contemporary professional in the field' patent defense).

---

### Post by forrestcupp on 2009-07-18
Reverse engineering is perfectly legal as long as you use a [clean room design.](http://en.wikipedia.org/wiki/Clean_room_design)  That basically means that your entire design team and process has absolutely no knowledge of how the original product was created or coded, and you can prove that no one had any knowledge.  Reverse engineering is perceived to be illegal, but it actually is not if you do it in this format.

Incorporating game content may be a different story.  I think it could be done, though.  You should try to track down some of the guys that used to work on the [Loki installers](http://www.liflg.org/) and ask them about it.  They used to do exactly what you're talking about with all kinds of commercial games.  I don't know if they worked in league with the original software companies or not.

---

### Post by armandh on 2009-07-18
I am not a lawyer and you would probably need one B4 selling anything! but: there is [as I recall] some exception to enable play of copyrighted material when the original "players" become obsolete. and: selling a hack with no copy righted material that does not promote illegal use or distribution may be a free speech issue. again I am not a lawyer and you may need one

---

### Post by 3rdalbum on 2009-07-18
You could try a "clean room/dirty room" reverse-engineering scheme.

The idea is that there are two teams: Clean room team, and dirty room team, with one supervisor who is the only conduit of information between the two teams.

The dirty room team can legally disassemble the software, and write the information obtained as a set of specifications for the software like a clean-room team would write. The supervisor checks the specifications document to ensure that there's no "dirty" material like code fragments, and then gives it to the clean room team. The clean room team takes the specification and writes some software to implement the specification.

It's a very clever way of reverse-engineering without risk, as both things seperately are legal, but doing both by one team is risky or illegal.

---

### Post by SunnyRabbiera on 2009-07-18
In this case I say screw legal, the current law system is corrupt and only benefits some guy who smokes cigars in his real leather chair while drinking wine inside of his golden mansion just outside of the slums where people are so poor they cannot even afford a cardboard box.

---

### Post by Yownanymous on 2009-07-18
It's a mortal sin to share things you know. It hurts people and funds terrorism. At least that's what RIAA says. Speaking of which, their entire database, which was ridiculously vulnerable, got hacked and wiped a little while ago!

Spending too much time thinking of groan-inducing propaganda?

----------------
Now playing: [The Beatles - Old Brown Shoe](http://www.foxytunes.com/artist/the+beatles/track/old+brown+shoe)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by mips on 2009-07-18
> **forrestcupp said:**
> Reverse engineering is perfectly legal as long as you use a [clean room design.](http://en.wikipedia.org/wiki/Clean_room_design)  That basically means that your entire design team and process has absolutely no knowledge of how the original product was created or coded, and you can prove that no one had any knowledge.  Reverse engineering is perceived to be illegal, but it actually is not if you do it in this format.

Incorporating game content may be a different story.  I think it could be done, though.  You should try to track down some of the guys that used to work on the [Loki installers](http://www.liflg.org/) and ask them about it.  They used to do exactly what you're talking about with all kinds of commercial games.  I don't know if they worked in league with the original software companies or not.

+1 What he said. Reverse engineering can be legal. 

There are many projects out there that do reverse engineering. 
You need two separate teams though so you don't stuff up. One to do the reverse engineering and write the specification, another to write code from the specification.

---

### Post by zolookas on 2009-07-18
Check you country's law. I think in most countries reverse engineering is legal if you are trying to ensure compatibility.

---

### Post by linuxguymarshall on 2009-07-19
> **forrestcupp said:**
> Reverse engineering is perfectly legal as long as you use a [clean room design.](http://en.wikipedia.org/wiki/Clean_room_design)  That basically means that your entire design team and process has absolutely no knowledge of how the original product was created or coded, and you can prove that no one had any knowledge.  Reverse engineering is perceived to be illegal, but it actually is not if you do it in this format.

Incorporating game content may be a different story.  I think it could be done, though.  You should try to track down some of the guys that used to work on the [Loki installers](http://www.liflg.org/) and ask them about it.  They used to do exactly what you're talking about with all kinds of commercial games.  I don't know if they worked in league with the original software companies or not.

I was not around back when Loki was still around but if I am correct they made software to do EXACTLY what the original binaries did. Mine are just going to replicate the look and feel, they would not allow you to connect to the Valve servers and play on the official servers. They will just load the game's files.

> **armandh said:**
> I am not a lawyer and you would probably need one B4 selling anything! but: there is [as I recall] some exception to enable play of copyrighted material when the original "players" become obsolete. and: selling a hack with no copy righted material that does not promote illegal use or distribution may be a free speech issue. again I am not a lawyer and you may need one
I am not selling anything. This is going to be an open-source project and I will be giving everything away. I don't even plan on taking donations to work on it.

> **SunnyRabbiera said:**
> In this case I say screw legal, the current law system is corrupt and only benefits some guy who smokes cigars in his real leather chair while drinking wine inside of his golden mansion just outside of the slums where people are so poor they cannot even afford a cardboard box.

Amen.

> **zolookas said:**
> Check you country's law. I think in most countries reverse engineering is legal if you are trying to ensure compatibility.

It is the United States. Anything regarding anything digital is pretty much illegal unless you do exactly what they intend for you to do. It is all about the fine print here. And its not obvious fine print either. Its the fine print that comes on the box of your computer that says you are subject to the EULA of software on the machine if you turn the machine on. and thats after you pay Dell $1350 for the laptop.

---

### Post by bodhi.zazen on 2009-07-19
thread closed. This is not a legal forums.

If you seek a legal opinion use a legal forums, contact the FSF, or better hire a lawyer.

---

