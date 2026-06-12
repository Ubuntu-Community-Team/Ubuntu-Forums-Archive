---
title: "What is the most annoying thing about PCs?"
date: 2010-07-07
forum: The Cafe
---

### Post by DreamShardDev on 2010-07-07
Hello Everyone lately me and a small group of friends have been working on a Desktop Environment (thats what I like to call it ) its taken on a very different look to the typical bar windows kind of scheme (probably going open source) that basically allows any user with a web-cam to control the PC without actually touching the mouse or keyboard ( you can also use the mouse if you wish and keyboard if you wish ). From the beta test runs that I have done there is a surprisingly high level of control. I also have good speech control and after writing my essay entirely with my voice and only a few mouse modifications I am pretty pleased with the result. Now I have gotten to the point where I am going to release an OS distro ( based of Ubuntu) and I was wondering what you guys would like to see improved in the OS of today. What would the perfect OS system be like for YOU? What annoys you about Linux , Mac or Windows ? What little things do you find annoying that you would like to see fixed ? Programmers out there, what kind of things hamper your productivity ?  You guys can post anything in regards to just what you want to see in your sorta dream OS

Thanks

Dream Shard Dev

---

### Post by Legendary_Bibo on 2010-07-07
I would like a fix after a kernel update in which I have to type sudo modprobe wacom every time I boot my computer when before the update I never had to do that. I could put it as a startup application but it needs super user privileges. So I guess the only thing that annoys me about Linux is that they should have chosen what needs root privileges a little better.

---

### Post by ubunterooster on 2010-07-07
> **DreamShardDev said:**
>  What annoys you about Linux , Mac or Windows ? What little things do you find annoying that you would like to see fixed ? What kind of things hamper your productivity ?
Sorry, but as soon as I saw the title I thought "the users" ;)

---

### Post by Cuddles McKitten on 2010-07-07
This probably isn't terribly helpful, but I sometimes get confused as to exactly where some bit of information is.  I use four workspaces and often have them filled with different programs, many of which have multiple tabs in them.  Maybe there's some why you could make it easy to just punch in "Firefox: *insert website title/tab name here*" for example and it would jump directly to the correct workspace with Firefox in focus and the correct tab selected or some such.  Then, a "return" command to go back to where it just was.

Though this problem is really of my own making by trying to do twenty things at once.

---

### Post by Dustin2128 on 2010-07-07
> **ubunterooster said:**
> Sorry, but as soon as I saw the title I thought "the users" ;)
Indeed :lol:

---

### Post by Lucradia on 2010-07-07
That ATI sucks?

---

### Post by yester64 on 2010-07-07
That programs get bloaded over time. Really annoying.

---

### Post by DreamShardDev on 2010-07-07
LOL @ Dustin.
 
Umm @ cuddles mckitten the layout of the DE makes that issue non-applicable , plus you could always jump to a particular program using voice control by saying " PC jump to ________" I actually do have the problem to which is why the interface is setup in a different manner. I might post some screenshots and show you what i mean.
 
What do you guys think of 3D ?? It is rather pointless in terms of efficency but with 3d tv coming out i think its not a bad option to have

---

### Post by marshmallow1304 on 2010-07-08
> **Legendary_Bibo said:**
> I would like a fix after a kernel update in which I have to type sudo modprobe wacom every time I boot my computer when before the update I never had to do that. I could put it as a startup application but it needs super user privileges. So I guess the only thing that annoys me about Linux is that they should have chosen what needs root privileges a little better.

Couldn't you just add
wacom
to /etc/modules ?

---

### Post by Legendary_Bibo on 2010-07-08
> **marshmallow1304 said:**
> Couldn't you just add
wacom
to /etc/modules ?
this thing?
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```

Do I just write wacom on a line?

---

### Post by murderslastcrow on 2010-07-08
Yeah, just type wacom directly under rtc on its own line. That's it.

Um... most annoying thing about computers is... they're not fully integrated with all of my senses just yet. And if it's not Linux, it feels a bit inhibitive due to the technologies only available with Linux, and the striking contrast.

So I guess I'd say the fact that a lot of them have to be running something other than Linux.

---

### Post by Legendary_Bibo on 2010-07-08
> **murderslastcrow said:**
> Yeah, just type wacom directly under rtc on its own line. That's it.

Um... most annoying thing about computers is... they're not fully integrated with all of my senses just yet. And if it's not Linux, it feels a bit inhibitive due to the technologies only available with Linux, and the striking contrast.

So I guess I'd say the fact that a lot of them have to be running something other than Linux.

Hey that worked! Now I only have one issue left but that's with compiz and I don't need it on (alpha blur plugin makes the the text in my window bar get fuzzy after a while). Now it's perfect!

My main issue with PCs is hardware <--> software incompatibilities.

---

### Post by Xianath on 2010-07-08
Software :) No, seriously. I find it hard to believe that this is the only Engineering product people are willing to accept with literally hundreds of known issues. I've been working with computers for 25 years and the number of software products I find acceptable in terms of features, stability, usability and quality can be counted by hand.A stuck gas pedal results in several million cars being pulled for refitting, but 50 bugs per 1000 lines of code and only 80% of them fixed (McConnell, Steve. Software Estimation: Demistifying the Black Art. 2001. Microsoft Press) is acceptable?

I write small software from time to time. I shouldn't because I can't, and I can't because I have neither studied to do it nor practiced it seriously nor am I under any kind of control It's like saying, "I build small bridges from time to time" or "I operate on small tumors for fun." If it takes years to practice, it shouldn't take a week to get started. I blame high-level languages, the ubiquity of personal computers, and the consumer psychology of the market (I want shiny new things NOW!), especially in the US, that encourages pointless feature bloat and insane deadlines (thus low quality), as well pure human greed (universities spewing out software engineers by the truckload, companies rushing to get *something* out before the competition...)

The above has nothing to do with your software. You asked what annoyed us in computers. I'm sure it will have bugs too but don't worry, if it's good, users will like it anyway :) Come on, screenies already!

---

### Post by chessnerd on 2010-07-08
Make your OS stand out.

How about you make it not so serious with itself? Windows and Mac are so serious all the time. Go more of the Chrome route. When something goes wrong, don't say "The system has encountered an error." say something like "Aw, snap!"

A few ideas:

Refer to the user by a gender-neutral nickname, like Chief. When a program is unresponsive, you could have it say "Yo, Chief, I think your program ain't looking so hot..." Options - "Let it die, then" or "Wait for it to cool off"

Instead of "start-up music" you could make something like one of those talking ring-tones. Something like "Your OS is starting"

Remember, though, it can't be juvenile or the novelty will wear off quickly. It needs to be more like classy sarcasm. Also, the OS behind it needs to be solid, too.

---

### Post by Legendary_Bibo on 2010-07-08
> **Xianath said:**
> Software :) No, seriously. I find it hard to believe that this is the only Engineering product people are willing to accept with literally hundreds of known issues. I've been working with computers for 25 years and the number of software products I find acceptable in terms of features, stability, usability and quality can be counted by hand.A stuck gas pedal results in several million cars being pulled for refitting, but 50 bugs per 1000 lines of code and only 80% of them fixed (McConnell, Steve. Software Estimation: Demistifying the Black Art. 2001. Microsoft Press) is acceptable?

I write small software from time to time. I shouldn't because I can't, and I can't because I have neither studied to do it nor practiced it seriously nor am I under any kind of control It's like saying, "I build small bridges from time to time" or "I operate on small tumors for fun." If it takes years to practice, it shouldn't take a week to get started. I blame high-level languages, the ubiquity of personal computers, and the consumer psychology of the market (I want shiny new things NOW!), especially in the US, that encourages pointless feature bloat and insane deadlines (thus low quality), as well pure human greed (universities spewing out software engineers by the truckload, companies rushing to get *something* out before the competition...)

The above has nothing to do with your software. You asked what annoyed us in computers. I'm sure it will have bugs too but don't worry, if it's good, users will like it anyway :) Come on, screenies already!

I had a teacher tell me that if they were to take some major program or more specifically an OS, it would take 20+ years to perfect it, and get rid of every bug. So imagine using Ubuntu 10.04 20 years from now or Win7 in 2030 just so it works perfectly. The bug fixing kind of follows a logistic curve in my mind.

---

### Post by Khakilang on 2010-07-08
Your title doesn't fit the thread. I though about hardware and find out after reading you talk about new Linux OS. To me if it ain't broke don't fix it. Ubuntu is as good as I want it to be. I don't know of any Distro can be better. I am not a fanboy but its the way I see and use it.

---

### Post by Xianath on 2010-07-08
> **Legendary_Bibo said:**
> I had a teacher tell me that if they were to take some major program or more specifically an OS, it would take 20+ years to perfect it, and get rid of every bug. So imagine using Ubuntu 10.04 20 years from now or Win7 in 2030 just so it works perfectly. The bug fixing kind of follows a logistic curve in my mind.

That's only because they are buggy to begin with (and they began ~20  or 30 years ago, respectively). Had they been developed with quality in mind right from the start, adding new features would not have led to regressions, and resources would not have to be spent chasing old bugs. Linux is community-driven, Windows is market-driven, and neither is primarily quality-driven.

There's a great quote by Tom DeMarco: "Quality is free, but only to those who are willing to pay heavily for it." And another one: "People under pressure don’t work better; they just work faster." There. In two sentences, he defines our industry's biggest underlying problem. People rush to get a product out (more pressure, less quality) and invest much more in development than in QA (for even less quality). It sometimes takes decades to reap the real benefit of quality, as is the case with Toyota or, if you want a more Western example, 60 year old Macallan whiskey. We're just too wound up in today to be thinking that far ahead. it's all about quotas and quarter reports and stock prices. It's never about actually delivering a high-quality product (though of course there is a correlation).

---

### Post by Legendary_Bibo on 2010-07-08
> **Xianath said:**
> That's only because they are buggy to begin with (and they began ~20  or 30 years ago, respectively). Had they been developed with quality in mind right from the start, adding new features would not have led to regressions, and resources would not have to be spent chasing old bugs. Linux is community-driven, Windows is market-driven, and neither is primarily quality-driven.

There's a great quote by Tom DeMarco: "Quality is free, but only to those who are willing to pay heavily for it." And another one: "People under pressure don’t work better; they just work faster." There. In two sentences, he defines our industry's biggest underlying problem. People rush to get a product out (more pressure, less quality) and invest much more in development than in QA (for even less quality). It sometimes takes decades to reap the real benefit of quality, as is the case with Toyota or, if you want a more Western example, 60 year old Macallan whiskey. We're just too wound up in today to be thinking that far ahead. it's all about quotas and quarter reports and stock prices. It's never about actually delivering a high-quality product (though of course there is a correlation).

Well wouldn't it be awesome if every OS developer (Windows, Linux, BSD, Solaris, Windows) just went into complete lockdown to perfect their OS? I mean I don't see why any OS needs to be updated besides for hardware, but we could all use the same computer for years while we wait for every company to perfect their OS. Then everyone will get a brand new computer and will never have a single issue ever again, tech support will be of little use, and all shall be pleased. It shall be glorious!

---

### Post by Xianath on 2010-07-08
> **Legendary_Bibo said:**
> Well wouldn't it be awesome if every OS developer (Windows, Linux, BSD, Solaris, Windows) just went into complete lockdown to perfect their OS? I mean I don't see why any OS needs to be updated besides for hardware, but we could all use the same computer for years while we wait for every company to perfect their OS. Then everyone will get a brand new computer and will never have a single issue ever again, tech support will be of little use, and all shall be pleased. It shall be glorious!

My point is, it would have been great if they had done it at the beginning. Unfortunately, Windows had to rush in and get their foot in the door, and FOSS has always been plagued by half-done hobbyist projects released onto the public in pre-alpha. Heck, it even prides itself in this approach! (Raymond, Eric. "The Cathedral and the Bazaar." [http://catb.org/esr/writings/homesteading/cathedral-bazaar/ar01s04.html](http://catb.org/esr/writings/homesteading/cathedral-bazaar/ar01s04.html)). Now we're in a position where there is so much old junk to fix in all software that your teacher was probably right. Any other engineering product of that quality (exploding fridge, electrocuting toaster, collapsing bridge...) would cause a lawsuit, but not software. That we as consumers allowed ourselves to be dragged here never ceases to amaze me.

---

### Post by Legendary_Bibo on 2010-07-08
> **Xianath said:**
> My point is, it would have been great if they had done it at the beginning. Unfortunately, Windows had to rush in and get their foot in the door, and FOSS has always been plagued by half-done hobbyist projects released onto the public in pre-alpha. Heck, it even prides itself in this approach! (Raymond, Eric. "The Cathedral and the Bazaar." [http://catb.org/esr/writings/homesteading/cathedral-bazaar/ar01s04.html](http://catb.org/esr/writings/homesteading/cathedral-bazaar/ar01s04.html)). Now we're in a position where there is so much old junk to fix in all software that your teacher was probably right. Any other engineering product of that quality (exploding fridge, electrocuting toaster, collapsing bridge...) would cause a lawsuit, but not software. That we as consumers allowed ourselves to be dragged here never ceases to amaze me.

Yeah, there was a lack of quality control from the beginning. If it was required that software was perfected as well as practices, and standards were put in place from the very start then today people wouldn't be having constant issues with their computers. It's a multiplicative effect really. You leave some bugs in place, update the system, more things break, more issues and bugs occur, and they don't get fixed. Update the system, etc. etc. 

Also the fact that universities are pumping out half baked software engineers isn't helping the situation. I'm not saying it's the SE's fault, I blame the universities, who don't thoroughly teach these people every technique imaginable to ensure that their software is perfected (i.e. memory optimization, bug squashing, hardware compatibilities etc.). 

Although some SEs can be blamed, they lack the discipline. I've met some, well actually tutored SE majors and they were lazy, and looking for the easy way to do everything without looking deeper into what or why they were doing it. What example I can think of is when I tutored this one guy because I was the T.A. for my Calculus professor and he was also in my C++ class, he was lazy, and arrogant. 

When he was supposed to think, he instead calculated. When he was to work, he found an easy way to just get it done. When he was supposed to learn, he declared it was a waste of time and that he was a genius. I noticed this same pattern of thought in other SEs I ran in to. I'm not saying they're all like this, but I'm just wondering why these modern SEs are developing this mindset, a lot of them just care about the money, and the L33T status, but they also don't seem to care about their work.

---

### Post by ubunterooster on 2010-07-08
> **chessnerd said:**
> Instead of "start-up music" you could make something like one of those talking ring-tones. Something like "Your OS is starting"
Knoppix does that, but other family members declare it creepy

---

### Post by Legendary_Bibo on 2010-07-08
> **ubunterooster said:**
> Knoppix does that, but other family members declare it creepy

What does it sound like?

---

### Post by kamaboko on 2010-07-08
> **chessnerd said:**
> Make your OS stand out.

How about you make it not so serious with itself? Windows and Mac are so serious all the time. Go more of the Chrome route. When something goes wrong, don't say "The system has encountered an error." say something like "Aw, snap!"

I'd rather have the error message match my thoughts.  For instance..."This f'ing piece of s**t crashed again. Curse it to hell".  lol.

---

### Post by Legendary_Bibo on 2010-07-08
> **kamaboko said:**
> I'd rather have the error message match my thoughts.  For instance..."This f'ing piece of s**t crashed again. Curse it to hell".  lol.

I hated Puppy Linux for baby talking to you pretty much at every help screen (Really hindered your ability to do certain things). Having error messages like that wouldn't bother me or even having error messages that actually told you what happened rather than in some obscure language. A little humor never hurt anyone either.

---

### Post by DreamShardDev on 2010-07-08
Thanks for the feedback guys, I have my work cut out for me. From what I have gathered people don't like a 2 inch piece of silicon telling them there stupid 8 hrs a day 5 days a week.  Im considering letting the user be able to configure the pc to just just how noob he is and just what kind of crap he wants it to show him. I gather you guys also want messages and notifications to be a little more interesting, i mean when the computer interrupts you in the middle of an IM with that hot girl, fail blogs or porno it better be worth the read!

As for buggy software well there will always be too many special cases different brands, models specific situations , hardware drivers and lets not forget all the viruses and ridiculous modifications users have made to their PC for a small team of developers to hit the nail on the head in one release. But being open source im sure you guys will be able to fix code that i did while under the influence of caffeine, alcohol and god know what else.

NOTE: I'm not really a drunk retard- I am wagering someone will debate that.....

As for when I am planning to release an alpha version of the OS well you can find that information on my website...... Coincidentally I haven't made a website for this yet but I will within the next 2 weeks. As for a rough Guesstimate ( I cant believe this word is on the forum dictionary thing) I would say in around 10 weeks time. Keep checking this thread for a link to the site and some screenies and vids.

Dream Shard Dev

---

### Post by ubunterooster on 2010-07-08
> **Legendary_Bibo said:**
> What does it sound like?
A female voice "Initiating startup sequence" 

When shutting down: "Initiating shutdown sequence"

---

### Post by chriswyatt on 2010-07-08
A little humour's nice but too much could become annoying very fast.  Also there's a narrow line between humorous and just being completely lame and annoying I think.

I think Google are good at keeping the balance, it's nice when a big company like that doesn't try to take things too seriously.

---

### Post by chriswyatt on 2010-07-08
> **ubunterooster said:**
> A female voice "Initiating startup sequence" 

When shutting down: "Initiating shutdown sequence"

Sounds like the computers in the movies which beep more than once a second and where everything seems to be controlled through the keyboard (e.g. if someone in a film navigates to a different page on the internet they seem to have to type an essay into their keyboard for some reason).

---

### Post by beercz on 2010-07-08
> **ubunterooster said:**
> Sorry, but as soon as I saw the title I thought "the users" ;)
The bits between keyboard and chair!

---

### Post by SunnyRabbiera on 2010-07-08
> What is the most annoying thing about PCs?

A good 99.9% of them come with windows

---

