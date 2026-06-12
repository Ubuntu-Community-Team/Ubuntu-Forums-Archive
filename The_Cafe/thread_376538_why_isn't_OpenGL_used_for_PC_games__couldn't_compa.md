---
title: "why isn't OpenGL used for PC games?  couldn't companies gain more $ by using OpenGL"
date: 2007-03-05
forum: The Cafe
---

### Post by billdotson on 2007-03-05
So there are many people who use just keep Windows for playing commercial PC games and use Linux or OS X for everything else.  Since the OpenGL API is cross-platform why don't game developers develop OpenGL games?  If developers developed games for OpenGL wouldn't they get more money because then those games would work in OS X and Linux OSes.  Then you would have not only Windows users buying the games you would also have Linux users and Mac OS users buying those games.

So I ask why aren't games developed for OpenGL so they are cross-platform and can be run in almost all OSes not just Windows?

---

### Post by tubasoldier on 2007-03-05
good question. why dont you see if you can get a response from EA Games?

---

### Post by cowlip on 2007-03-05
They end up using OpenGL and OpenAL when programming for consoles other the the (Direct)Xbox [that's what its original name was actually going to be:)], such as the Wii, Gamecube, PS3/2/1, etc.  Apparently there are issues with the vendor's different implementations of OpenGL on Windows.  Of course on linux there's a different story as the open source drivers should support the standards even if performance is not as amazing as the vendor's binaries.

---

### Post by hardyn on 2007-03-05
somebody who hacks game code may want to correct me, but a friend of mine preferred hacking with directX over openGL; that might have something to do it with it too...

but they're are lots of games writting in openGL, most anything that comes out of id software is open gl, and im sure they are many more examples.  there are other things associated with games and directX than graphics, sound are input controllers are also a big part, it might simply be easier... and 80% of people use windows... and that says enought right there.

---

### Post by cowlip on 2007-03-05
The things about DirectX is that it's a lot of separate things in one API.  But there are open equivalents, like OpenGL, OpenAL for sound, input, etc.  Like hardyn, I'm to not qualified to judge if one is better than the other.  I'm sure in terms of integration, MS has made it very attractive to use DirectX on Windows (biggest PC gaming platform, although not biggest gaming platform in total due to game consoles).  After all..."Developers, developers, developers..."  MS is also converging the PC and Xbox 360 with their new XNA which allows you to write games in .NET on the PC and put them on the Xbox, with a subscription fee of course ( [http://en.wikipedia.org/wiki/Microsoft_XNA#XNA_Game_Studio](http://en.wikipedia.org/wiki/Microsoft_XNA#XNA_Game_Studio) ), although they also hobbled it by denying access to the ethernet port.

I think Sony made a mistake in tying up Linux so much on the PS3 and not giving graphics card access.  What do they have to compete with XNA?

But the existence of these games on other consoles must mean that OpenGL/AL is used in some shape or form, or am I wrong?

---

### Post by billdotson on 2007-03-05
hmm well if OpenGL and OpenAL were combined into a all-in-one API like DirectX wouldn't OpenGL be more useful?  I mean you would surely make more money developing a game in OpenGL+OpenAL that would run in Linux or Mac OSes as well as Windows.  That means more people will buy it.  Id software makes money because some Linux users purchase their games.  Wouldn't it be more profitable to use OpenGL+OpenAL or are there simply issues with OpenGL+OpenAL that make the DirectX API more appealing?

and btw the XNA game studio doesn't seem very appealing to me.  Seeing as it is so hard to make a modern 3D game (I have a friend that has been trying for 3 years and all he has is like 2 skins and a couple weapon models) why does this appeal to people?  If people were going to create their own games couldn't they just do it in a programming language?  I mean even though the XNA game studio is supposed to make it easier to do wouldn't most of the people who were interested in doing something like that have already learned how to do so in a programming language?  Also, many people that are going to be using XNA are probably more avid PC gamers/ PC people as there probably are not as many console gamers who want to actually sit down and write their own game, much less get the source code through someone else on Xbox Live by paying a $100 fee.  That just seems kind of silly.  It seems that an IDE such as XNA would make it easier to "make" a game but since it is there to make it easier wouldn't there be many XNA games that are extremely similar to other ones?

Honestly though unless there isn't a great reason and if the only reason to not use OpenGL+OpenAL for game development is just because it is a little bit harder is quite stupid.  Developers would make more money if the game could be played on more operating systems and more consoles.  It is that simple.. and also the people that play the games would benefit.. you wouldn't have to use Windows just to play games (which is why many Linux users keep their Windows install at all)

---

### Post by Tomosaur on 2007-03-05
Don't quote me on this - but I think Microsoft actually ended support for OpenGL on Windows. It is a lot harder to write OpenGL stuff on Windows because, although Microsoft don't intentionally stop OpenGL working, there is no included method of getting OpenGL to work. Developers who want to use OpenGL need to provide everything to make OpenGL work themselves - similar to how many things in the closed-source world work. If each developer has to start from scratch to get OpenGL working properly, they're much less likely to spend the time on it.

DirectX IS a powerful API - there's no denying it, but relying on MS just seems like a risky venture to me. Even if OpenGL is less powerful (and this is debatable - I've heard many people saying that OpenGL is faster to develop in than DirectX - and although it is not inherently more powerful - it can be MADE a lot more powerful with a little more work. Just look at Doom3 - it looks absolutely amazing, and it's OpenGL.

---

### Post by Oki on 2007-03-05
Here are some upcoming games that use OpenGL:

[http://www.enemyterritory.com/](http://www.enemyterritory.com/)
[http://www.unrealtournament2007.com/](http://www.unrealtournament2007.com/)
[http://savage2.s2games.com/](http://savage2.s2games.com/)

Lets hope they sell a lot so others would like to also use OpenGL.

---

### Post by jamyskis on 2007-03-05
> **Tomosaur said:**
> Don't quote me on this - but I think Microsoft actually ended support for OpenGL on Windows. It is a lot harder to write OpenGL stuff on Windows because, although Microsoft don't intentionally stop OpenGL working, there is no included method of getting OpenGL to work. Developers who want to use OpenGL need to provide everything to make OpenGL work themselves - similar to how many things in the closed-source world work. If each developer has to start from scratch to get OpenGL working properly, they're much less likely to spend the time on it.

I'm no friend of Microsoft, but it was never Microsoft's responsibility in the first place to supply GL support in the OS. After all, with no 3D driver preinstalled, OpenGL is next to useless anyway. I know the bog standard VESA drivers did supply a basic GL interface, but it was next to useless, unless you wanted to play Neverball at 320x240, low textures at 5 fps. NVIDIA, ATI et al. shoulder the responsibility for interfacing between OpenGL apps and the video drivers.

> DirectX IS a powerful API - there's no denying it, but relying on MS just seems like a risky venture to me. Even if OpenGL is less powerful (and this is debatable - I've heard many people saying that OpenGL is faster to develop in than DirectX - and although it is not inherently more powerful - it can be MADE a lot more powerful with a little more work. Just look at Doom3 - it looks absolutely amazing, and it's OpenGL.

I saw an article recently that developers and publishers are facing the conundrum that as development costs go up, so do the prices they need to charge for games, and as such games sales are coming down. As such, the solution presented was to release a single game for as many platforms as possible to maximise sales. Hopefully, this means we'll get more console-style games for PC (I love stuff like Onimusha, Outrun 2006 and Devil May Cry) but it also means there's little practical logic in developing using DirectX when every other console except the XBox and XBox 360 uses OpenGL.

---

### Post by Slychilde on 2007-03-05
The only reason I have come up with is Microsoft strong arming them into using their API.  There really is no logical reason to not use OpenGL.  More platform + same amount of work = more revenue / better profit percentages.

---

### Post by rejser on 2007-03-05
My friend at an un-named big swedish gaming company that may have produced a quite famous fps game said to me that developing towards dx is both easier and more cost effience then opengl.
Don't know where the difference is, just his words.

---

### Post by Tomosaur on 2007-03-05
> **jamyskis said:**
> I'm no friend of Microsoft, but it was never Microsoft's responsibility in the first place to supply GL support in the OS. After all, with no 3D driver preinstalled, OpenGL is next to useless anyway. I know the bog standard VESA drivers did supply a basic GL interface, but it was next to useless, unless you wanted to play Neverball at 320x240, low textures at 5 fps. NVIDIA, ATI et al. shoulder the responsibility for interfacing between OpenGL apps and the video drivers.


Yeah - it's not Microsoft's responsibility - but they produce an operating system, and it IS their responsibility - and to their benefit, to ensure that things people want to work, work. That's pretty much the definition of an operating system. Most people don't know the difference between OpenGL and DirectX - they just like, and want to play games. Microsoft gain very little from NOT supporting OpenGL - aside from a greater adoption of DirectX - and as you pointed out, this eventually leads to problems further down the line. Short term substantial gains (more use of DirectX an thus more money for MS) is cancelled out by a long term problem with no easy solution (if developers become reluctant to develop games, then everyone loses out. If developers focus only on DirectX - then when the DirectX bubble 'bursts', so to speak, there will be very few major developers with the skills necessary to develop using OpenGL).

If Microsoft continued to support OpenGL - there would be a greater amount of competition - which means it would be in developer's interests to keep costs down. The games themselves would advance (in terms of graphics etc) a bit more slowly - but the cost of developing them would be much more sustainable, and revenue would be sustained for a longer period. Sony has not helped the matter with their catastrophic failure that is the PS3 - and XBox is only compounding the problem. The Nintendo Wii is pretty much the only thing keeping Microsoft from total market domination at the moment - unless the PS3 suddenly undergoes a massive popularity boost. I see a pretty bleak future for games developers in the near future. I know I'm not willing to fork over £50-£60 for a three hour game, and am even less inclined to spend upwards of £300 for a games console to play them on. I just don't have that kind of money - and neither do any of my friends or anybody I've spoken to.

---

### Post by weatherman on 2007-03-05
would an open source implementation of the directx api be theoretically possible?

---

### Post by hardyn on 2007-03-05
you bet, but i would have the same legal implications as mono, and WMx

---

### Post by v8YKxgHe on 2007-03-05
> **weatherman said:**
> would an open source implementation of the directx api be theoretically possible?

Isn't that what parts of Wine are?

---

### Post by Foudre on 2007-03-05
> **weatherman said:**
> would an open source implementation of the directx api be theoretically possible?


hmm could get around the copywrite  if you didn't copy it, if you made an inturpurter to accept dx commands and convert to opengl or mimic the dx command in a new api. Hmm too bad ms owns dx, but many protected things have been remade in linux really without copiing them. Example my printer driver.


but i have noticed dx games seam to run smoother, of course they seam to take up more resources then opengl, probally why they run better. But dx10 is a major improvement over dx9, on the same system games run faster and i can set them at higher detail levels with out loosing performance

---

### Post by SunnyRabbiera on 2007-03-05
I dunno I have seen a few commercial games use open GL here and there, though it is rare.

---

### Post by billdotson on 2007-03-05
DirectX might be good but even if OpenGL and OpenAL is messier it would still bring in more revenue and would allow them to be on all platforms (Wii, PS3, Xbox360, Windows, Linux, OS X) I wonder.. why hasn't the gov't talked to Microsoft about being a trust again?  They are clearly trying to strangle the market into doing what MS wants.

---

### Post by payton on 2007-04-12
The sole reason is that MS gives support to the developers. This means that the companies developing games get to use MS facilities like sound studios and a whole lot of other things. At my University we had a lecture by a game development studio and they said they would never step away from MS and DirectX due to this support MS gives them
Now why do MS give this support? Games sell computers nowadays, and if you sell computers you sell os'es....
There is also the problem of games being hacked which open source os like Linux offers less protection against.

---

