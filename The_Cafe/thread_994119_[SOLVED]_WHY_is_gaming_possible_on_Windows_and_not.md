---
title: "[SOLVED] WHY is gaming possible on Windows and not on Linux?"
date: 2008-11-26
forum: The Cafe
---

### Post by gshockxc on 2008-11-26
We see it often enough, right?  "I'm keeping my Windows box just so that I can play games, but I really like Linux better... ", etc.

One thing I've learned is that we haven't really answered the question until we can ask, "Why?" 5 times.  

Example:
[LIST=1]
[*]Why don't you get rid of your Windows system completely?
**A:** Because I can't play my games on my Ubuntu system.


[*]Why can't you play your games on your Ubuntu sytem?
**A:** Because Ubuntu doesn't support gaming?
[/LIST]

... and that's usually (to my uneducated mind) where the discussion ends.  

WHY can't we play games in Ubuntu?  
**A:** (Just a ridiculous example) Because the video controller doesn't allow .... (whatever, make up your own response).

WHY Doesn't the video controller allow .... (insert whatever from above)?
**A:** Because 'xyz' can't happen in Linux, but it does in Windows.

The point being, I'm sure if we ask 'why' long enough, we can drive it back to the point where it's a simple problem that we can solve.  That solution leads to solving another problem, and so on.  

How many times have you started a simple task, only to find that when you trace the problem back to its roots, there's hardly any relation to the original issue?

There are many great minds out there using Linux, and probably many more who have tried to solve much more complicated problems than this.  And I'm sure there are many on this site who are probably much smarter than I am, trying to solve this problem.  

In my real job, I get paid to solve problems, so I hope you'll forgive me if I want to ask "WHY?" just a few more times.

As always, thanks for your patience...

---

### Post by gn2 on 2008-11-26
Time to [get some education]("http://www.google.co.uk/search?q=linux+gaming&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enGB279GB280").

---

### Post by Tom--d on 2008-11-26
People use Windows for gaming because the manufacture(s) of the game(s) does not support Linux.

---

### Post by damis648 on 2008-11-26
It is certainly possible, it is just that people want to play their Windows games which are not available for Linux. There is no difference in capabilities, just that the popular games are only available for Windows.

---

### Post by Tom--d on 2008-11-26
This game is brilliant!

[http://en.wikipedia.org/wiki/Nexuiz](http://en.wikipedia.org/wiki/Nexuiz)

---

### Post by Ozor Mox on 2008-11-26
> **Tom--d said:**
> People use Windows for gaming because the manufacture(s) of the game(s) does not support Linux. That's it. Nothing else to it.

Exactly. And the reason games producers do not release their games for Linux is because it is not widely used enough to make a port worth their while. If usage of Linux on the desktop continues to increase, I have no doubt that sooner or later we will start to see more games on the platform.

---

### Post by Xanavi on 2008-11-26
Urban Terror is one of the best FPS games around. It was a quake 3 mod for a while then went standalone with the q3 source release.

[URL="http://www.urbanterror.net"]
http://www.urbanterror.net/[/URL]

---

### Post by gshockxc on 2008-11-26
> **Tom--d said:**
> People use Windows for gaming because the manufacture(s) of the game(s) does not support Linux. That's it. Nothing else to it.

Isn't there a program in Ubuntu that will allow you to run your windows programs?  Why does that not work for games?  

Maybe it does, and I'm still not educated enough to know the answer yet.

---

### Post by damis648 on 2008-11-26
> **gshockxc said:**
> Isn't there a program in Ubuntu that will allow you to run your windows programs?  Why does that not work for games?  

Maybe it does, and I'm still not educated enough to know the answer yet.

There is (are). They are Wine (free and OSS) and Crossover (non-free). They are Windows API implementation layers, so they do try to run Windows programs, but they cannot run everything, and probably will never be able to. Not all games run, so that is why people keep Windows.

---

### Post by Tom--d on 2008-11-26
> **gshockxc said:**
> Isn't there a program in Ubuntu that will allow you to run your windows programs?  Why does that not work for games?  

Maybe it does, and I'm still not educated enough to know the answer yet.

Yes there is called Wine but don't expect it to work. Read the wine database first to see what you want to work works.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by aysiu on 2008-11-26
I know a lot of people on the Ubuntu Forums are Windows ex-power users who are really into PC gaming, but outside of the Linux communities and Windows power user communities, high-end commercial PC gaming (big industry though it is) pales in comparison to console gaming in terms users and money spent.

I frankly don't care about gaming on Ubuntu. It will come with time when there are more Linux users. Or the vast majority of people into commercial games will keep buying consoles and a handful of Windows power users and their friends will keep using Windows for their expensive gaming rigs.

---

### Post by chucky chuckaluck on 2008-11-26
obviously the op is unaware of the bsdgames package, or he'd be blissfully playing them now.

---

### Post by jomiolto on 2008-11-26
> **chucky chuckaluck said:**
> obviously the op is unaware of the bsdgames package, or he'd be blissfully playing them now.

For once I can honestly say: LOL. Seriously that was brilliant :D

---

### Post by gshockxc on 2008-11-26
> **chucky chuckaluck said:**
> obviously the op is unaware of the bsdgames package......

Of course I am...

I'm a Noob.  Most days, I'm lucky that I can find the power button.  :)

Half of the problem with starting something new like this is that you don't know what you don't know.  (Of course, the other half is knowing what to do with it when you find it - but that's another forum).

---

### Post by snova on 2008-11-26
If the OP is looking for technical reasons, I can provide a few, although I may not be totally correct.

We all know that Windows binaries will not run on Linux. There are fundamental differences in the file format. And then there is the Windows API- the set of services that Windows provides to applications.

Wine is capable of loading Windows binaries, and also provides a layer mapping most Windows API calls to their Linux equivalents. If Wine were perfect, all Windows programs would run- but it isn't, and they don't.

From what I understand, many games make extensive use of API's that Wine does not totally implement, or only partially. One of these is DirectX.

There's a commercial fork (or something like that) of Wine called Crossover that might work better for some things.

---

### Post by SunnyRabbiera on 2008-11-26
Gaming on linux is possible if the game developers actually get there is more then one OS out there.
Linux has great gaming potential if given the chance.

---

### Post by CholericKoala on 2008-11-26
Games use DirectX.

DirectX != OpenGL

The end.

---

### Post by gshockxc on 2008-11-26
I guess a better way to ask the question would have been, "For those games that can't be played on Linux, and only on Windows, what is the reason behind this?"

It appears that this would be a better question, since there are so many "gaming" options in Linux, just not the same games as in Windows.

---

### Post by SunnyRabbiera on 2008-11-26
> **CholericKoala said:**
> Games use DirectX.

DirectX != OpenGL

The end.

Yeh but openGL is much better then direct X, too bad its not looked at as an option.

---

### Post by RiceMonster on 2008-11-26
OP seems to think Linux doesn't support gaming.

No, gaming doesn't support Linux.

---

### Post by gshockxc on 2008-11-26
> **CholericKoala said:**
> Games use DirectX.

DirectX != OpenGL

The end.

NOW, we are getting somewhere!  In a nutshell, that pretty much sums it up.

What is DirectX?  Can I make an open source program that could do the same thing?

---

### Post by SunnyRabbiera on 2008-11-26
> **gshockxc said:**
> NOW, we are getting somewhere!  In a nutshell, that pretty much sums it up.

What is DirectX?  Can I make an open source program that could do the same thing?

[http://en.wikipedia.org/wiki/DirectX](http://en.wikipedia.org/wiki/DirectX)

and there is already an answer to direct X in the form of openGL

---

### Post by shadylookin on 2008-11-26
> **gshockxc said:**
> NOW, we are getting somewhere!  In a nutshell, that pretty much sums it up.

What is DirectX?  Can I make an open source program that could do the same thing?

games can and have been written in opengl WoW for instance has been written in both. 

Quite simply the only reason there are fewer commercial games for linux is because game manufactures don't think linux has enough market share to bother with. There's absolutely nothing wrong with linux that seriously impedes game development

---

### Post by gshockxc on 2008-11-26
> **SunnyRabbiera said:**
> [http://en.wikipedia.org/wiki/DirectX](http://en.wikipedia.org/wiki/DirectX)

and there is already an answer to direct X in the form of openGL

OK.  That answers my questions.  Thanks for taking the time.  Now it all makes sense.

---

### Post by SunnyRabbiera on 2008-11-26
> **shadylookin said:**
> games can and have been written in opengl WoW for instance has been written in both. 

Quite simply the only reason there are fewer commercial games for linux is because game manufactures don't think linux has enough market share to bother with. There's absolutely nothing wrong with linux that seriously impedes game development

Indeed, actually it should be easier to make games for linux because of its open nature, if you need to make sure the game works you can take a peek at the code of the OS no questions asked :D
But no attention = no profit for the game makers out there

---

### Post by OMJD on 2008-11-26
> **gshockxc said:**
> I guess a better way to ask the question would have been, "For those games that can't be played on Linux, and only on Windows, what is the reason behind this?"

It appears that this would be a better question, since there are so many "gaming" options in Linux, just not the same games as in Windows.

Simply because the games in question are not compatible with Linux. To elaborate further; Linux is an entirely different operating system which runs completely differently to Windows, and the programs (software/games) for it are written in a programming language which Linux can understand. Many of the games available for Windows are not written in a programming language which Linux can understand, they are programmed in a language which Windows can understand. (It is slightly more complicated than that, but I tried to explain it as simple as I could) 

It's like asking "Why can't I understand this person when he speaks Chinese?" The reason is simply because you don't understand that language, and therefore, you're incompatible with the Chinese person in that respect.

The only real way for this issue to be resolved, is for software developers to make their products natively compatible with Linux. However, unless the market is big enough, it won't happen. That said, it has improved in recent years as more and more people are starting to use Linux as their desktop operating system.

---

### Post by gshockxc on 2008-11-26
> **OMJD said:**
> ... it has improved in recent years as more and more people are starting to use Linux as their desktop operating system.

If the number of users running Ubuntu is any indication, it won't be long before they sit up and take notice.

To all: thanks very much for taking the time to help me understand this.  I probably won't be gaming much right away, but I'm certainly a lot more interested in experimenting than I was before.

Like I said [before]("http://ubuntuforums.org/showthread.php?t=993404&page=3"), every day brings new information, and that changes the path I take each day.  I never know where I might end up!

---

### Post by days_of_ruin on 2008-11-26
If developers used OpenGL more there would be more commercial games for linux.ETQW is one example.I think only one guy "ported"? it to linux.

---

### Post by shadylookin on 2008-11-26
> **OMJD said:**
> Simply because the games in question are not compatible with Linux. To elaborate further; Linux is an entirely different operating system which runs completely differently to Windows, and the programs (software/games) for it are written in a programming language which Linux can understand. Many of the games available for Windows are not written in a programming language which Linux can understand, they are programmed in a language which Windows can understand. (It is slightly more complicated than that, but I tried to explain it as simple as I could) 

It's like asking "Why can't I understand this person when he speaks Chinese?" The reason is simply because you don't understand that language, and therefore, you're incompatible with the Chinese person in that respect.

The only real way for this issue to be resolved, is for software developers to make their products natively compatible with Linux. However, unless the market is big enough, it won't happen. That said, it has improved in recent years as more and more people are starting to use Linux as their desktop operating system.

most commercial games are written in c and c++ and linux has compilers for them. In fact I can't think of a programing language that only works on windows.

---

### Post by mips on 2008-11-26
> **Xanavi said:**
> Urban Terror is one of the best FPS games around. It was a quake 3 mod for a while then went standalone with the q3 source release.

[URL="http://www.urbanterror.net"]
http://www.urbanterror.net/[/URL]

Unfortunately it does not compare to CS:S

---

### Post by earthpigg on 2008-11-26
> **gn2 said:**
> Time to [get some education]("http://www.google.co.uk/search?q=linux+gaming&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enGB279GB280").

never seen that article before.

good thing you pointed it out: the link to "Ultimate Edition" was pointing to the article on "Ubuntu", which i fixed.

---

### Post by chris4585 on 2008-11-26
Urban Terror is one of the most stablest games I've ever played on Linux.  

I also am just waiting for the game developers to realize how much potential linux has.  And how much money is in it, I'd pay for games for linux, wouldn't you?

---

### Post by Ozor Mox on 2008-11-26
> I'd pay for games for linux, wouldn't you?

Yes.

There are loads of really good free and open source games on Linux, many of which I play regularly on my PC. I have a PS3 for commercial games, but if they were to come to Linux I'd no doubt buy the ones I really like the look of. Some games (RTS and TBS spring to mind) just aren't really suited for the console.

---

### Post by earthpigg on 2008-11-26
> **chris4585 said:**
> I'd pay for games for linux, wouldn't you?


i already have ;)

[http://en.wikipedia.org/wiki/DEFCON_(game)]("http://en.wikipedia.org/wiki/DEFCON_(game)")

i highly recommend the trial version, as well.

---

### Post by chucky chuckaluck on 2008-11-26
> **gshockxc said:**
> I'm a Noob.  Most days, I'm lucky that I can find the power button.  :)

whoa! there's a power button?

---

### Post by Bölvaður on 2008-11-26
Actually after reading this thread I came to remember that although it is true that the only reason there aren't games on linux, is because game manufacturers arent making them or porting them to linux, there is another problem.

That is API for the gaming companies. I have heard that complaint before and most people reading this thread probably remember reading that also.

One other is the audio... it really needs to be fixed.

But all in all those are just excuses as it isn't really a big hurdle.

---

### Post by Persistence on 2008-11-26
My solution, since my ONLY reason for having a windows box is Warcraft, is that I'm going to set up a dual boot dedicating a measly 40gb for it and the other 710gb will be for Ubuntu.  Since I paid for XP I might as well use it, install WoW and use that boot solely for Warcraft.  Ubuntu is my friend so I will spend all my non-addiction time playing with her.

---

### Post by earthpigg on 2008-11-26
Persistence: WoW runs very well under WINE.

edit - although i can not speak for WINE from the repos.

---

### Post by zmjjmz on 2008-11-26
> **SunnyRabbiera said:**
> [http://en.wikipedia.org/wiki/DirectX](http://en.wikipedia.org/wiki/DirectX)

and there is already an answer to direct X in the form of openGL

OpenGL is not necessarily the answer, but it is the equivalent to Direct3D, which is only a part of DirectX. There is much more to DirectX and Linux doesn't have an answer to all of them integrated into one, easy to port to package.

---

### Post by Chame_Wizard on 2008-11-26
Ironic that almost all games(online) can be played/downloaded from a server working on Linux.:lolflag:

---

### Post by Bölvaður on 2008-11-26
> **Chame_Wizard said:**
> Ironic that almost all games(online) can be played/downloaded from a server working on Linux.:lolflag:

Dont forget that those same games when played in multiplayer are played on linux server editions of those same games.... they just dont port the client only the server.

---

### Post by Persistence on 2008-11-26
> **earthpigg said:**
> Persistence: WoW runs very well under WINE.

edit - although i can not speak for WINE from the repos.

Unfortunately even with all the tricks and tweaks the game gets 10fps.  I use over a hundred addons and I don't think Wine can handle it (as demonstrated by playing without addons and getting 40fps).  However I just built a slightly faster computer with 4gb of memory so we'll see how it goes.

---

