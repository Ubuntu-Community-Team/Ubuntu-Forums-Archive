---
title: "Apollo 11 Guidance Computer code released"
date: 2009-07-20
forum: The Cafe
---

### Post by Sealbhach on 2009-07-20
On this day 40 years ago, Neil Armstrong and Buzz Aldrin became the first humans to walk on the Moon. This was quite an achievement for mankind and a key milestone in world history.

To commemorate this event the Command Module code (Comanche054) and Lunar Module code (Luminary099) have been transcribed from scanned images to run on yaAGC (an open source [AGC emulator]("http://en.wikipedia.org/wiki/Apollo_Guidance_Computer")) by the [Virtual AGC and AGS]("http://www.ibiblio.org/apollo/") project. 

[http://googlecode.blogspot.com/2009/07/apollo-11-missions-40th-anniversary-one.html](http://googlecode.blogspot.com/2009/07/apollo-11-missions-40th-anniversary-one.html)


.

---

### Post by Delever on 2009-07-20
So cool :)

---

### Post by Sealbhach on 2009-07-21
You can download it from Softpedia now:

[http://linux.softpedia.com/get/System/Emulators/Virtual-AGC-8805.shtml](http://linux.softpedia.com/get/System/Emulators/Virtual-AGC-8805.shtml)

.

---

### Post by Mr. Picklesworth on 2009-07-21
It's pretty scary code, too :P

```
		TS	WCHPHASE
		TC	BANKCALL	# TEMPORARY, I HOPE HOPE HOPE
		CADR	STOPRATE	# TEMPORARY, I HOPE HOPE HOPE
		TC	DOWNFLAG	# PERMIT X-AXIS OVERRIDE
```

```
		DMP*	VXSC
			GAINBRAK,1	# NUMERO MYSTERIOSO
			ANGTERM
```

---

### Post by Firestem4 on 2009-07-21
> **Mr. Picklesworth said:**
> It's pretty scary code, too :P

```
		TS	WCHPHASE
		TC	BANKCALL	# TEMPORARY, I HOPE HOPE HOPE
		CADR	STOPRATE	# TEMPORARY, I HOPE HOPE HOPE
		TC	DOWNFLAG	# PERMIT X-AXIS OVERRIDE
```

```
		DMP*	VXSC
			GAINBRAK,1	# NUMERO MYSTERIOSO
			ANGTERM
```


lmao..  That is one of the last things i'd want to see in the code for which this was serving a purpose..ARG!

---

### Post by LowSky on 2009-07-21
anyone else very scary that it too such little code to fly to the moon, yet  a car built today  has much more written code in its breaking system.

So sad we haven't been to the moon or even beyond Earth's grasp since Apollo 17.

---

### Post by MaxIBoy on 2009-07-21
Yikes! This is why we don't use assembly in mission-critical code anymore!

---

### Post by elliotn on 2009-07-21
What does the code do

---

### Post by 23meg on 2009-07-21
> **elliotn said:**
> What does the code do

It lands an Apollo Lunar Module on the moon.

---

### Post by MikeTheC on 2009-07-21
The fact of the matter is that piloting a craft really doesn't take an insane amount of code to do. It's when you start asking more and more of the hardware that you start needing more powerful stuff.

Truth be told, any one of our home computers has enough processing power to fly the entire Saturn V stack, CSM and LM included, to the moon, land it there, lift off, and fly back. In fact, it could do that in the background while you're playing WoW or rendering a 3D scene.

Having been to a shuttle launch once (and going again in March!) I can only imagine what seeing a Saturn V launch was like. It's not really a "regret" in the proper sense as I wasn't born until after Apollo 17 flew and returned, but I do wish I could have been there to see it.

Actually, let me take a moment to say a couple things about this...

2010 is the last year for shuttle flights. Depending on what NASA, Congress and the President do, we may or may not have the Constellation program up and running in 2014 or 2015. Therefore, if you've ever wanted to go to a manned launch, 2010 is probably going to be your best shot at it. Moreover, if you've ever wanted to go to Kennedy Space Center, there's no time like the present. It's a really neat and historic place.

And if you go, you *absolutely* must go to the Apollo/Saturn building they've built for one of the last surviving Apollo / Saturn stacks. It is simply incredible standing in the same room as one of those things; there simply aren't words to describe what it's like. I'll be taking my girlfriend there and she is sooooo excited (being the techy-type like me) to get to KSC and see a launch.

In addition to the software mentioned up-thread, the following link will take you to a web-based simulator:

[http://apollo.spaceborn.dk/dsky-sim.html](http://apollo.spaceborn.dk/dsky-sim.html)

---

### Post by RiceMonster on 2009-07-21
> **MikeTheC said:**
> Truth be told, any one of our home computers has enough processing power to fly the entire Saturn V stack, CSM and LM included, to the moon, land it there, lift off, and fly back. In fact, it could do that in the background while you're playing WoW or rendering a 3D scene.

I know what I'm doing this weekend.

---

### Post by 23meg on 2009-07-21
> **RiceMonster said:**
> In know what I'm doing this weekend.

Don't forget [the Owner's Manual]("http://www.haynes.co.uk/webapp/wcs/stores/servlet/BookFeature_Apollo11View?langId=-1&storeId=10001&catalogId=10001")!

---

### Post by Sealbhach on 2009-07-21
> **MikeTheC said:**
> 

And if you go, you *absolutely* must go to the Apollo/Saturn building they've built for one of the last surviving Apollo / Saturn stacks. It is simply incredible standing in the same room as one of those things; there simply aren't words to describe what it's like. 



Cool. The only rockets I've seen are the German V2 rockets in a museum in Munich, built by Werner von Braun. They look strange, they seem too "modern" for WW2.


.

---

### Post by Ozor Mox on 2009-07-21
Wow, that is immensely cool!

---

### Post by Sealbhach on 2009-07-21
There's a pre-built Linux binary here:

[http://www.ibiblio.org/apollo/Downloads/VirtualAGC-installer](http://www.ibiblio.org/apollo/Downloads/VirtualAGC-installer)

which installs and runs just fine on my Jaunty 64-bit.

---

### Post by elliotn on 2009-07-21
> **23meg said:**
> It lands an Apollo Lunar Module on the moon.

Still why would we need the code, unless u want to land ur kite in d moon

---

### Post by MaxIBoy on 2009-07-22
Actually, with the Apollo 11 mission, the computer failed, and one of the astronauts had to grab a joystick  and land it manually.

Now we know why.

---

### Post by Ozor Mox on 2009-07-22
> **elliotn said:**
> Still why would we need the code, unless u want to land ur kite in d moon

We don't *need* the code, it's just been released for interest.

---

### Post by markbuntu on 2009-07-23
> **MaxIBoy said:**
> Yikes! This is why we don't use assembly in mission-critical code anymore!

That is not really true. Almost all tiny sensor modules are coded in assembler. For something small, running in a tiny loop, assembler is fast and absolutely reliable. It directly translates into machine language.

Besides, the machines the Apollo people were programing were very small, 8 bit processors with 16k ram running a Kbs speeds. You really needed to talk to the machine directly at that scale to assure that nothing is wasted, no time, no space.

Todays programs, and their programmers are extremely wasteful of resources. Much of the fault is the higher level languages and their generic compilers that are not optimized for hardware.

---

### Post by Whiffle on 2009-07-23
> **MaxIBoy said:**
> Yikes! This is why we don't use assembly in mission-critical code anymore!

Well written assembly code can be just as good, so long as it is thoroughly tested, just like any other piece of code.  Writing code for such an application, no matter the language, and not ensuring that it works 100% before putting it into use is pure negligence.  Additionally, I don't think its the language that makes good code, its the practices and standards used to ensure the best quality of that code.  Higher level languages are more for convenience anyway.


But while we're on the subject, some other coding types might be interested in this excellent reading from JPL:

The Power of Ten: 10 Rules for Writing Safety Critical Code
[http://www.spinroot.com/p10/](http://www.spinroot.com/p10/)

---

### Post by dullard on 2009-07-23
The wetware was far more important :-)

---

### Post by MythAaron on 2009-07-23
> **MaxIBoy said:**
> Actually, with the Apollo 11 mission, the computer failed, and one of the astronauts had to grab a joystick  and land it manually.

All of the LEMs (Except for Apollo 13) were landed manually.  Sure, Armstrong had to take over early but the computer was only supposed to get them so far.  It took a pilot to land.

---

### Post by linuxguymarshall on 2009-07-23
Will I ever use it? No.

Will I study and stare in amazement for a few hours this weekend? Without a doubt.

---

### Post by fillintheblanks on 2009-07-23
wow I am amazed people still believe in this.

the moon landings were so obviously fake. and with the technology available at the time?? give me a break. if NASA could do it with such regularity and ease you would think they would of built a moon base there by now. 

and did they ever make deep space travel test? to see what the effect would be on the body and propolsion system? no. they amazingly did in on first try. establishing lunar orbit, making picture perfect landing with unproven equipment. amazing!

only apollo "unlucky" 13 failed surprise surprise :roll:

---

### Post by BslBryan on 2009-07-23
> **fillintheblanks said:**
> wow I am amazed people still believe in this.

the moon landings were so obviously fake. and with the technology available at the time?? give me a break. if NASA could do it with such regularity and ease you would think they would of built a moon base there by now. 

and did they ever make deep space travel test? to see what the effect would be on the body and propolsion system? no. they amazingly did in on first try. establishing lunar orbit, making picture perfect landing with unproven equipment. amazing!

only apollo "unlucky" 13 failed surprise surprise :roll:

May I count the grammatical errors in your post to help prove how very little I believe you actually know about this?

[QUOTE=Stephen Colbert]It's all right if you have an opinion that's different than mine as long as you realize that your differing opinion is wrong.[/QUOTE]

---

### Post by phrostbyte on 2009-07-23
So if I compile this I can fly to the moon? Where do I get the required hardware? :D

---

### Post by phrostbyte on 2009-07-23
Anyone successful in compiling this from source? This might by a interesting thing to try to package as a DEB.

The source code is here:

```

svn checkout [http://virtualagc.googlecode.com/svn/trunk/](http://virtualagc.googlecode.com/svn/trunk/) virtualagc-read-only  

```

make seems to fail on the current head (for me)
Revision is 261, I am trying to compile on Ubuntu 9.04 64-bit

---

### Post by MythAaron on 2009-07-25
> **phrostbyte said:**
> So if I compile this I can fly to the moon? Where do I get the required hardware? :D
Check with the OpenApollo, OpenLEM, and OpenSaturn projects :D

---

### Post by phrostbyte on 2009-07-25
Sooooooooo anyone tried to compile this? :D

---

