---
title: "Is [quality] OSS gaming possible?"
date: 2010-06-28
forum: The Cafe
---

### Post by dr.frankinfurter on 2010-06-28
The question: Is it?

[LEFT]For the sake of argument, I will use the first person shooter 'Crysis' as the standard for quality. It cost 22 million USD to produce the game and even with the staggering production costs it still made a profit. Source: [http://www.totalvideogames.com/Bioshock/news/BioShock-Smashes-Through-15-Million-Sales-11586.html](http://www.totalvideogames.com/Bioshock/news/BioShock-Smashes-Through-15-Million-Sales-11586.html).

At it's time, ( 2008 ) it was the paragon of video games. Now, hypothetically, how can an OSS game of the same quality come into existence? If the source code was available then a user could, theoretically, compile everything for free without any repercussions from the law. So, first problem: price. Or rather, "how are we going to throw 22 mil. into producing a single application."

What about the technology? I know for sure that OpenGL is suitable for quality gaming but what about the engine? I've seen some quality engines around the net but they look more like vaporware then anything else. I'm no developer but I'm guessing the engine takes up a large chunk of development resources since there was a viral plague of open source games after the quake engine was open-sourced. So I'm guessing we would have more high-quality games if something similar to the engine that powered Crysis got birthed. But the technological barrier stretch beyond graphics engines; crappy GPU driver stacks are a problem as well. First of all, ATI cards are a cluster**** of problems so I'm not even going to touch that, but what about nVidia? When can we have a good open source driver for nVidia cards? I know we have nouveau but will the developers follow through on it and make it stable then continue to maintain it? Even the proprietary Linux driver is not as good as the one written for Windows (too lazy to provide the source but there is a recent article detailing the performance gabs between the two) Then there are other problems... what about the X server? It's ancient and old and there is no viable alternative. So, problem number two: How do we get a firm base to build upon?

There are few companies that are friendly enough to Linux to develop for it and even fewer that make enough money to throw around 22 mil. Red Hat and Canonical may be able to suffer the financial strain but they have their hands full with their respective products. What about Google? They have a TON of resources! Well, I can't say they are interested in developing a quality game but they seem to show an interest in putting 3D graphics capability on the web. Third problem: Who's gonna' do it?

Now, I know a lot of people believe that video games are a frivolous waste of time ('a lot' is relevant to the Ubuntu community) but not a single one of you can say that gaming is a dead market. In fact, it's a billion dollar industry that caters to almost every single demographic imaginable and it's an industry that spurns Linux. Ubuntu doesn't have Photoshop, iMovie, iWork, put your favorite OS X compatible program here ____, and therefore it can't sustain the large user base that Apple enjoys. I'm not here to bash Linux. I'm here to try to get some answers. How do we get this elephant out of the door?
[/LEFT]

---

### Post by Johnsie on 2010-06-28
I don't think it is possible. When you pay someone to work 9 to 5 and manage them properly they will generally get alot more done. You can also have much bigger development teams if there is some money to throw at it.

Having hobbyists working on a game during their free time will take alot longer and there may not be the same level of Quality Assurance applied to the final product. How do you manage hobbyists? They have no financial incentive, so if you offend them they might just leave the project.

Alot of the artwork and music in those applications is created by professional artists and sound engineers in studios. That kind of thing takes money.

An open source game project could only make money if users had to pay to play online, and if it's open source then someone could just make a version that bypasses the paid servers.


This doesn't just affect games, it affects the quality of open source applications in general. There are so few high quality applications being developed because there is no money to be made in open source.

---

### Post by V for Vincent on 2010-06-28
I don't believe you need anything near crysis's budget to produce a top quality game. However, you need to handle things differently. If you try to do the same thing as a major games company with no budget, you will fail. But there are some great indie games (world of goo, I'm looking at you) and mods out there. Those are budgets open source could compete with. Really, tons of money go into things a good game doesn't need. Marketing, state-of-the-art graphics, video sequences,... And gameplay and plot are still lacking in the vast majority of cases. Note that I said state-of-the-art graphics, not "graphics" in general. Too many projects disregard those entirely. I'd rather devs just grabbed something like the sauerbraten engine or ogre and started working on the game proper right away.

That said, I do think that great open source games will always be an exception. Any kind of game requires a lot of work and, in the end, serves no useful purpose. Other apps do.

---

### Post by Half-Left on 2010-06-28
Crysis a standard of quality? :lolflag:

Crysis was a techdemo with some horrendous flaws.

---

### Post by NightwishFan on 2010-06-28
What about Nexuiz?
[http://en.wikipedia.org/wiki/Nexiuz](http://en.wikipedia.org/wiki/Nexiuz)

---

### Post by Johnsie on 2010-06-28
Nexuiz is based on the Quake Engine which was built using a proprietary business model. Some games can run off the back off that in this way but usually they use outdated technologies.

---

### Post by NightwishFan on 2010-06-28
It is GPL software I do not see the issue. [COLOR="White"]Another one arguing for the sake of arguing.. Wonderful.[/COLOR]

---

### Post by Legendary_Bibo on 2010-06-28
I actually remember seeing a high quality game that's still in production. It's from a team who built an open source engine which they'll release once they release their game (I saw the quality of it, it's not going to be distributed for free moneywise). I know that it wouldn't run on my laptop's danky graphics card. Also what about YoFrankie! Although it never worked for me, I think it only works with a game pad controller.

---

### Post by cascade9 on 2010-06-28
Considering that linux distros can approach (and IMO at least equal) a windows OS shows that its more than possible for opensource to make some amazing things, mostly without the huge pricetag of normal commercial ventures. 
> **Half-Left said:**
> Crysis a standard of quality? :lolflag:

Crysis was a techdemo with some horrendous flaws.

Pretty much. 

Well, crysis wasnt really a demo, but where it originally came from (x-isle) was. IIRC, nVidia chucked some money in towards the development cost. Mainly because they knew that any game running the cryengine would need some serious GPU power to run well.  

> "We are very excited to be working closely with NVIDIA to exploit a new generation of hardware. With graphics fuelled by the GeForce3, Dinosaur Island showcases the OpenGL-based CryENGINE technology. We are now able to feature very detailed vast landscapes and even more detailed dinosaurs and have both realistically interacting together; graphics like these are only possible with the new cutting-edge features from the GeForce3 chip. Our progressive mesh technology enables us to have massive scenes with 50+ skeletal animated dinosaurs walking through at once." says Cevat Yerli&#8212;CEO/President of Crytek Studios.[http://www.nvidia.com/object/dinoisle.html](http://www.nvidia.com/object/dinoisle.html)

Gefroce 3......which shows how long cryengine has been in development. 

Yes, I know, crysis uses the cryengine 2, but its just an updated version of cryengine 1. 

22mil isnt that much considering how many games have been based on the various versions of cryengine.

---

### Post by JDShu on 2010-06-28
We have the open source tools (eg. Ogre3D) and the talent. However the difficulty is not the technical programming side, but the content creators and the directors. Artists, for example, do not buy into the open culture that programmers do, and the dynamics between the two groups of people are rarely friendly as far as I have seen.

---

### Post by dr.frankinfurter on 2010-06-28
> **Half-Left said:**
> Crysis a standard of quality? :lolflag:

Crysis was a techdemo with some horrendous flaws.


I played it, and I thought it was of excellent quality (I especially liked the game mechanics). And compared to most games it had a pretty okay story. Don't like Crysis? Fine. But you can't ignore the fact that it made enough to cover it's huge production cost. If you wish you could pick another tier 1 Windows game then do so. Bioshock, Dragon Age, Oblivion - all of them cost over a million dollars. Bioshock had an interesting story by the way if someone wants a good recommendation (Dead Space and Mass Effect also have good stories as well).

>  		I don't think it is possible. When you pay someone to work 9 to 5 and  manage them properly they will generally get alot more done. You can  also have much bigger development teams if there is some money to throw  at it.

Having hobbyists working on a game during their free time will take alot  longer and there may not be the same level of Quality Assurance applied  to the final product. How do you manage hobbyists? They have no  financial incentive, so if you offend them they might just leave the  project.

Alot of the artwork and music in those applications is created by  professional artists and sound engineers in studios. That kind of thing  takes money.

An open source game project could only make money if users had to pay to  play online, and if it's open source then someone could just make a  version that bypasses the paid servers.


This doesn't just affect games, it affects the quality of open source  applications in general. There are so few high quality applications  being developed because there is no money to be made in open source.

I think you hit the nail on the head.

I also think that high-profile applications (gaming being of particular importance) are crucial for Linux, or any open source operating system for that matter, to succeed.

> Considering that linux distros can approah (and IMO at least equal) a  windows OS shows that its more than possible for opensource to make some  amazing things, mostly without the huge pricetag of normal commercial  ventures. 

That's what gives me hope actually. Though, I do have something to say: Operating system != video game. Take a look at how Linux has been built; it's a conglomeration of different parts strung together to produce an operating system. There's a reason why the correct term is GNU/Linux after all. The cost of producing it - financially and time wise - has been spread over different projects, making Linux distributions easier to make. Canonical probably would have a lot harder of a time making Ubuntu the way it is if it was in charge of producing it's own libraries, drivers, kernel updates, desktop interface, etc...

Games are different in the way that you rarely have previous resources to draw upon. An engine maybe, but do you see a quality one around that's ready to use or is not in early development stages? It's a HUGE undertaking that needs to be managed by tons of developers, story writers, artists, musicians, and so on and so forth. It's a singularity that can only be accomplished by a huge financial backing - unlike Linux which was sort of just pieced together from different open source projects.

> 
22mil isnt that much considering how many games have been based on the  various versions of cryengine. 	

This is where I bring up the Source engine. I have high hopes for it since it will be able to spawn something worthy of awesome. But still, it's showing it's age and I'm hoping that someone worthy will be able to step up to the plate and create a great graphics engine.

> Really, tons of money go into things a good game doesn't need. Marketing,  state-of-the-art graphics, video sequences,... And gameplay and plot  are still lacking in the vast majority of cases. Note that I said  state-of-the-art graphics, not "graphics" in general. Too many projects  disregard those entirely. I'd rather devs just grabbed something like  the sauerbraten engine or ogre and started working on the game proper  right away.

I would consider a game that rivals tier one Windows game to have 'state-of-the-art graphics.' :) As far as story, um, Windows games still have better stories then the ones produced for Linux. And graphics tie in heavily with the environment the story is placing you in. For example, can you really be scared of the spooky aliens if they are 2D? I remember playing Doom 3 and I nearly wet myself because of how well done the environment was done (this included graphics, musical score, lighting choices, and creature sounds). And stories don't just 'make themselves' - skilled writers are needed to spruce them up. Unfortunately, most developers are not writers by trade and can't make a good story to pair with their game. So, let's say a group of people took the quake engine and started to make a game that focused on story telling. Let's see who you would need: developers to create the GUI and the A.I, artists (3D, painting, etc) to produce meshes and to create the animated scenes, writers for the actual story and dialogue, musicians for the musical score and for creating sound effects... I could go on but I think you catch my drift. Also, having a game that consists mostly of you reading is pretty pointless since you could go buy a book. Good video games, IMO, are meant to temporarily emulate an exciting existence that isn't possible in real life. Revealing a story is part of this, but so is immersing the player in a cacophony of lights and sounds. 

Also, good game play mechanics are needed. I really like the wheel in Crysis. Switching in between stealth, strength, speed, and armor mode to kill opponents was just... fun. Switch to strength to jump on a building, use the advantage to kill a few guards, switch to armor when the bullets start going your way- oh man the fun. (Sorry for going off topic a bit)

Also, Bioshock had great mechanics now that I think of it... The point is that money has to go into game play mechanics in order to differentiate it from other games of the same genre. Most FPS have you shoot stuff, but in Crysis you had multiple options on how you could approach a battle sequence. Running in guns blazing could be an option, but so could cloaking and going in stealth as well. (I've JUST decided to play it again - see what you did?!?!)

Sorry for the long-winded posts.

---

### Post by V for Vincent on 2010-06-28
> **dr.frankinfurter said:**
> 
I would consider a game that rivals tier one Windows game to have 'state-of-the-art graphics.' :) As far as story, um, Windows games still have better stories then the ones produced for Linux. And graphics tie in heavily with the environment the story is placing you in. For example, can you really be scared of the spooky aliens if they are 2D? I remember playing Doom 3 and I nearly wet myself because of how well done the environment was done (this included graphics, musical score, lighting choices, and creature sounds). And stories don't just 'make themselves' - skilled writers are needed to spruce them up. Unfortunately, most developers are not writers by trade and can't make a good story to pair with their game. So, let's say a group of people took the quake engine and started to make a game that focused on story telling. Let's see who you would need: developers to create the GUI and the A.I, artists (3D, painting, etc) to produce meshes and to create the animated scenes, writers for the actual story and dialogue, musicians for the musical score and for creating sound effects... I could go on but I think you catch my drift. Also, having a game that consists mostly of you reading is pretty pointless since you could go buy a book. Good video games, IMO, are meant to temporarily emulate an exciting existence that isn't possible in real life. Revealing a story is part of this, but so is immersing the player in a cacophony of lights and sounds. 


I never said Linux games had better stories than windows games. There are practically no games that have a proper story, period. Most are just "nondescript soldier type takes on lots of monsters". Those "skilled writers" you mention are few and far between in the games industry. Most would fail as airport novelists.

Also, games that are heavy on reading or have 2d graphics are not pointless. Take planescape: torment. Now that's making good use of atmosphere. I mainly expect original elements and a consistent vision, which has been done in low budget/free games in the past.

Quality games of the kind I like are more feasible on a low budget than the kind you prefer, because quality means something else to me than it does to you. But, as I said, that's only if you take budget into account. I think what's really lacking in open source gaming is motivation.

---

### Post by Kdar on 2010-06-28
Wesnoth is pretty good. Great quality game.

---

### Post by Proteus Vulgaris on 2010-06-28
> **Johnsie said:**
> I don't think it is possible. When you pay someone to work 9 to 5 and manage them properly they will generally get alot more done. You can also have much bigger development teams if there is some money to throw at it.

Having hobbyists working on a game during their free time will take alot longer and there may not be the same level of Quality Assurance applied to the final product. How do you manage hobbyists? They have no financial incentive, so if you offend them they might just leave the project.

Alot of the artwork and music in those applications is created by professional artists and sound engineers in studios. That kind of thing takes money.

An open source game project could only make money if users had to pay to play online, and if it's open source then someone could just make a version that bypasses the paid servers.


This doesn't just affect games, it affects the quality of open source applications in general. There are so few high quality applications being developed because there is no money to be made in open source.

Now that is just spooky, the hairs on the back of my neck all stood to attention.

I had this conversation with an acquaintance of mine, a man who has invested much time and money in Microsoft software and qualifications over many years. As far as he is concerned Linux and Open Source are not good enough now and never will be, ever. End of story. 

(This is probably why I keep my distance and he remains just an acquaintance and not a friend, I am sure the feeling is mutual. :-) )

I read comments such as Johnsie's and I always remember this guy. Simple fact is, to these people, Linux and Open Source are not good enough now and never will be, ever. End of story. The quality of the software has little to do with it.

But I like how they are always here remind us about such things, bless them. :rolleyes:

---

### Post by nrs on 2010-06-28
> **Kdar said:**
> Wesnoth is pretty good. Great quality game.
Mhmm. It also looks and feels like it was produced in the early-mid 90's. Doesn't make it bad of course.

---

### Post by nrs on 2010-06-28
I think it depends on the type of game.

I don't think open source games can compete in genres where art (defined loosely) assets are of primary / defining importance. I don't think we'll ever have an FPS that can compete with its peers. 


There is a game that really opened my eyes: 
[IMG]http://image.versiontracker.com/scrnsht/145561/402698/391DEFCON.jpg[/IMG]
I consider that downright beautiful, opinions may vary of course. But it made me realize you don't need insanely detailed textures or models to look nice. I think we can make a lot of our games look nice by adopting simple visual styles.

I think it is within our grasp to pull something like this off: 
[IMG]http://img214.imageshack.us/img214/4523/map1rh4.jpg[/IMG]
[IMG]http://www.alternatehistory.com/discussion/attachment.php?attachmentid=55002&d=1222226917[/IMG]

Maybe not mine, this what I've designed so far:
[IMG]http://img514.imageshack.us/img514/7969/screenfa.png[/IMG]
But w/e. The textures are swappable so I'll concentrate on designing the game first and let someone else worry about it. :P

---

### Post by dr.frankinfurter on 2010-06-28
> **V for Vincent said:**
> I never said Linux games had better stories than windows games. There are practically no games that have a proper story, period. Most are just "nondescript soldier type takes on lots of monsters". Those "skilled writers" you mention are few and far between in the games industry. Most would fail as airport novelists.

Also, games that are heavy on reading or have 2d graphics are not pointless. Take planescape: torment. Now that's making good use of atmosphere. I mainly expect original elements and a consistent vision, which has been done in low budget/free games in the past.

Quality games of the kind I like are more feasible on a low budget than the kind you prefer, because quality means something else to me than it does to you. But, as I said, that's only if you take budget into account. I think what's really lacking in open source gaming is motivation.

I'm sorry, maybe 2D graphics was a bit... misleading. I meant more in the way as 'inferior to the products around it.' The 8-bit Mario games were fun as all get out back in the day and those bits probably looked great up on your TV screen - but that was quite a bit back. When faced with the choice of playing Mario Bros. or say, Half-Life 2, *most* people will choose the better game. Sure something could be impressive at the time but take this into account: What if someone made something similar to Planescape but with updated graphics? A *really* impressive story with dialogue instead of text but with something similar to the engine that ran Crysis? Would your opinion differ? I think it's like saying that a motor on a lawn mower doesn't determine how high of quality that mower will be since push mowers were just as popular at a time. What if, one day, we have holodecks that have interactive video games? I'm not knocking story in any sort of way, but I'm all for a more realistic environment to stretch my legs in. Technological advancements need to be default in a video game if it's going to 'trounce the rest' so to speak. IMHO of course :).

Also, Planescape: Torment was proprietary, sold commercially, and had a very large budget. Being made in 1997 (wasn't that the same year Diablo was released?), three years before Diablo II, Planescape wasn't THAT far behind. And, it was very pretty good looking compared to what was around back then. Had a 3D RPG been produced by then? I know 3D shooters were sprouting up (Half-Life FTW) but I can't recall anything besides isometric viewpoints or rogue games.


> Those "skilled writers" you mention are few and far between in the games  industry.

True, but they don't need to be better then airport novelists. Besides, have you read the stories created by solo game developers? Or small teams of developers? Wait, ARE there stories written by solo/small group developer(s) First off, they don't have the time to write the huge script. Regardless if good stories are needed for OSS games to compete with closed-source games it's still something that costs a ton of money to implement something like that. Planescape had a team of four developers working on the spell artwork alone. Who do you think wrote the 800,000+ lines of text in the game? (Wikipedia FTW) This brings me back to the first problem of the original post: Where is the money going to come from?

Even though it's a tad off-topic, my idea of a ground-breaking game (using todays technologies) would be something akin to Oblivion but with a MUCH, MUCH more detailed story line and more in depth personalities coupled with a more well laid out and diverse world. A overhaul of the combat system would be nice also. (Also to note: Planescape was criticized for it's combat mechanisms) But, then again, that's my opinion and it's the opinion of the masses that count. 

Thanks for your replies :)

---

### Post by cb951303 on 2010-06-28
quality does not always come with budget and technology.
check out IGF winners to see some low budget quality indie games.
those are definitely possible with OSS business model: make the game GPL but not the assets. recently gish, aquaria, world of goo and some other indie games did this. i don't see why it wouldn't work from the start.

---

### Post by dr.frankinfurter on 2010-06-28
> **Kdar said:**
> Wesnoth is pretty good. Great quality game.

'tyler' is my screen-name and I challenge you!

The subject of the post was that if top-quality games produced by open source could *compete* with top-quality closed source games.

I believe Wesnoth is an excellent game, been playing it for two years in fact, but the fact is it wouldn't be able to compete with any current top-tier Windows game in the marketplace. Sure, every single one of us has subjective opinions on what consists of a good game (I've expressed mine all over this thread) but we have to keep in mind what the masses want. Tetris was a great game and I still play it occasionally. Would I spend more time playing that then Dragon Age? No. Would the 14-30 demographic play Tetris more then DA? Well, depends on personal preference but I'm guessing the majority would pick the newer game. Also, Wesnoth has a terrible story - it's the online game play mechanics that draws most of the players in. I think it needs more then clever mechanics to make it big. (Crysis would be a fleeting interest if I just liked the mechanics)

> Mhmm. It also looks and feels like it was produced in the early-mid  90's. Doesn't make it bad of course. 	

Never said that. I'm just saying it wouldn't be able to compete with larger titles for multiple reasons -- graphics being one of them.

> Now that is just spooky, the hairs on the back of my neck all stood to  attention.

I had this conversation with an acquaintance of mine, a man who has  invested much time and money in Microsoft software and qualifications  over many years. As far as he is concerned Linux and Open Source are not  good enough now and never will be, ever. End of story. 

(This is probably why I keep my distance and he remains just an  acquaintance and not a friend, I am sure the feeling is mutual. :smile: )

I read comments such as Johnsie's and I always remember this guy. Simple  fact is, to these people, Linux and Open Source are not good enough now  and never will be, ever. End of story. The quality of the software has  little to do with it.

But I like how they are always here remind us about such things, bless  them.

I meant this thread to be constructive; a thread meant to figure out how to solve a problem. Who knows? Maybe open source can't garner enough money to solve this particular problem and we must leave it up to a proprietary solution. It's sort of like a face-off between socialist and capitalistic market types - sometimes a combination of the two produce the best results (that's entirely subjective and I hope the thread doesn't make a b-line for the off-topic realm). A lot of good has come from OSS but, like everything, it [probably] has limits. I found Johnsie's response to be practical, reasonable, and logical.

> This is probably why I keep my distance and he remains just an  acquaintance and not a friend, I am sure the feeling is mutual

I really hate to be judgmental here but perhaps the feeling *isn't* mutual? Maybe he's just confused as to why someone is alienating him over his software choices? Or maybe even confused as to why he's being ostracized? My girlfriend and I have a disagreement over how awesome John McClain is but we're not going to end our relationship over the dispute. Perhaps a common bond could be forged through the love of technology and innovation?

Besides, isn't the point of OSS is to garner freedom? I don't see how it's any more free if people are forced into using it through prejudiced or spurned because they have a different preference.

Personally, I choose OSS software because some companies engage in unethical monopolistic practices and that bothers me. I also like that it doesn't cost anything and that the community is so constructive (most of the time). I don't mind paying for proprietary technology as long as their is a logical reason for it being proprietary and that the company has a good code of ethics.

But that's off-topic. Lol. :)

Thanks for all your replies.

---

### Post by dr.frankinfurter on 2010-06-28
> **cb951303 said:**
> quality does not always come with budget and technology.
check out IGF winners to see some low budget quality indie games.
those are definitely possible with OSS business model: make the game GPL but not the assets. recently gish, aquaria, world of goo and some other indie games did this. i don't see why it wouldn't work from the start.

I didn't see 'open-source' attached to many of those games. Many of them were built on proprietary technologies (few worked on Linux; most were for Windows). Personally I think the resources used should be open-sourced (like the game engine for example) but some things should be kept proprietary so that it could be sold. This seems to work fairly well and is a trend among companies. Id did it and so will Valve.

Although, I'm still wondering if an 'all-OSS' strategy can be used to produce something as high of quality as what's being used for Windows users.

[Edit: Sorry for the double post. Also: > quality does not always come with budget and technology I'm not sure about 'quality' per say but I would say success would come if you threw enough money at a project. Proof? 'Avatar' had a sub-par story and sub-par acting. It was filled with bash-you-over the head allegories about race and environmentalism (not that it went against or supported my political viewpoints it was just blatant and annoying) and it's 'acting' just ended up looking cheesy and melodramatic. But the thing cost more then I'm worth as a person (joke) and it made a profit. Sure, you could say the director was a visual genius but I've seen similar plant constructs on DeviantArt; he really wasn't original in the slightest. Just goes to show that if you throw enough money into visual effects your going to get something a lot of people will want to see.]

[Second edit: Unobtanium?! Seriously? Are you _____ing serious?! How did.... RAGE!! RAGE!!!

---

### Post by donkyhotay on 2010-06-28
> **dr.frankinfurter said:**
> I didn't see 'open-source' attached to many of those games. Many of them were built on proprietary technologies (few worked on Linux; most were for Windows). Personally I think the resources used should be open-sourced (like the game engine for example) but some things should be kept proprietary so that it could be sold. This seems to work fairly well and is a trend among companies. Id did it and so will Valve.

Although, I'm still wondering if an 'all-OSS' strategy can be used to produce something as high of quality as what's being used for Windows users.

[Edit: Sorry for the double post. Also:  I'm not sure about 'quality' per say but I would say success would come if you threw enough money at a project. Proof? 'Avatar' had a sub-par story and sub-par acting. It was filled with bash-you-over the head allegories about race and environmentalism (not that it went against or supported my political viewpoints it was just blatant and annoying) and it's 'acting' just ended up looking cheesy and melodramatic. But the thing cost more then I'm worth as a person (joke) and it made a profit. Sure, you could say the director was a visual genius but I've seen similar plant constructs on DeviantArt; he really wasn't original in the slightest. Just goes to show that if you throw enough money into visual effects your going to get something a lot of people will want to see.]

I agree, especially with games it all depends on what you consider quality. Most of the "top-tier" games out there have tons of eye candy, but aren't all that much fun to play, especially on replay. My favorite commercial game of all time is [Moonbase Commander](http://en.wikipedia.org/wiki/Moonbase_Commander) which had very boring graphics/story even by the standards when it came out (2002 release). However the gameplay had lots of depth and strategy within it that I still enjoy to this day. So much so that me and some other fans have been working on [our own FOSS remake](code.google.com/p/tether). Graphics are even worse in our version but that doesn't bother us very much so longa as we get the gameplay down.

---

### Post by dr.frankinfurter on 2010-06-28
> **donkyhotay said:**
> I agree, especially with games it all depends on what you consider quality. Most of the "top-tier" games out there have tons of eye candy, but aren't all that much fun to play, especially on replay. My favorite commercial game of all time is [Moonbase Commander]("http://en.wikipedia.org/wiki/Moonbase_Commander") which had very boring graphics/story even by the standards when it came out (2002 release). However the gameplay had lots of depth and strategy within it that I still enjoy to this day. So much so that me and some other fans have been working on [our own FOSS remake]("http://code.google.com/p/tether"). Graphics are even worse in our version but that doesn't bother us very much so longa as we get the gameplay down.

Congratulations on your game.

I define 'quality' in this context as something that appeals to the masses. I disagree with your opinion on top-tier games. Most of the quality commercial games I play I usually play them again. All the ones I've listed so far in previous posts were excellent games IMO that I've played multiple times. I went through Half-Life 2 three times, I've logged in hours of my time into Oblivion (and Morrowind for that matter), I went through Crysis five times I think, and I'm going through Dragon Age (think Neverwinter Nights on steriods) for the... 3rd time. Of course, you could say that's my preference - but it's also the preference of many, many, many Windows gamers as well.

Personally, I see proprietary games on Linux as a good thing. Savage 2 and Heroes of Newerth did an excellent job of providing a Linux compatible version and I'm highly grateful for this.

It's funny though, either people say "2D games are good enough and I love them" (I'm satisfied) or "Yeah, you're right, it's just not going to happen." Is there no initiative to provide broaden the portfolio of quality projects under the OOS movement's belt?

---

### Post by kaldor on 2010-06-28
Quality? What about Quake and Doom? What about the JK series in WINE? OpenArena even?

---

### Post by Lucradia on 2010-06-28
World Forge?

[http://www.worldforge.org/](http://www.worldforge.org/)

---

### Post by dr.frankinfurter on 2010-06-28
Outdated, outdated, and outdated. The point of the thread was to see if making an open source game that would equal top-tier games released for Windows under proprietary licenses in quality was possible. Currently, I think there is no open source game that comes close to the Windows gaming experience. The closes proprietary game for Linux I've seen is Heroes of Newerth.

There are some great games out there for Linux, sure - but nothing produced produced using a budge akin to a massive budget of a proprietary game.

I'm guessing the people who have been replying to this thread haven't played many recent Windows video game releases. Also, WINE is NOT a good solution. Sort of like how Flash is not a good solution to displaying web content. I know the state of Linux gaming and I've tried the numerous games released for Linux. The question isn't about whether we have something now it's about whether something better could be achieved in the future through OSS methods.

---

### Post by nrs on 2010-06-28
> **dr.frankinfurter said:**
> Outdated, outdated, and outdated. The point of the thread was to see if making an open source game that would equal top-tier games released for Windows under proprietary licenses in quality was possible. Currently, I think there is no open source game that comes close to the Windows gaming experience. The closes proprietary game for Linux I've seen is Heroes of Newerth.

There are some great games out there for Linux, sure - but nothing produced produced using a budge akin to a massive budget of a proprietary game.

I'm guessing the people who have been replying to this thread haven't played many recent Windows video game releases. Also, WINE is NOT a good solution. Sort of like how Flash is not a good solution to displaying web content. I know the state of Linux gaming and I've tried the numerous games released for Linux. The question isn't about whether we have something now it's about whether something better could be achieved in the future through OSS methods.
You're restricting 'good' to epic blockbusters. This is such a narrow view. As I said earlier I think it's doubtful. Technologically maybe, we have plenty of talented programmers. But there's so much more to these games than code. 
But I think we can  create modern and fun games in genres / games that don't require such an artistic investment.

I don't even think most proprietary games look good. The ones that do are exceptional.

---

### Post by Simian Man on 2010-06-28
Are you asking if it's possible to make a free game of high quality or an open source game of high quality?  Because those are very different questions.

I think it would be possible to make a high quality open source game and then charge for the content - which is by far the most expensive part of making a game.  This is the case with id's games, although they were only open-sourced after the fact.

There are some great free games out there, but expecting something comparable to games that cost millions to make is unrealistic.

---

### Post by nrs on 2010-06-28
Do you consider these as ugly / dated? 
[IMG]http://www.freeorion.org/images/1/1c/039galaxymap.jpg[/IMG]
It's certainly not stunning, but for what the game is (Orion-like 4x), I think it looks just as nice as any of it's proprietary counterparts.

---

### Post by dr.frankinfurter on 2010-06-28
I wouldn't call them blockbusters, and if I did then I guess you could say that the gaming industry is pretty good at pushing blockbusters out. I would compare it to the movie industry - it has a ton of money flowing into it and it has a ton of high quality productions being pushed out. The gaming industry made 11.7 billion in 2008 ([http://en.wikipedia.org/wiki/Video_game_industry](http://en.wikipedia.org/wiki/Video_game_industry)) That's a lot of cash, regardless of whether you think that most games produced for Windows are un-interesting, there are enough people shelling out cash for the games to generate double-digit billion revenue numbers. Video games are taking on a more cinematic quality and the OSS community is still producing games that look like they were made two decades ago. I'm sorry if I don't have the complacent attitude everyone else seems to have but it's a problem.

How about this: If you think 'blockbusters' are so rare then how about I start a list of games that have sold over a million copies this year? (Note that the minimum is 1 million)

Red Dead Redemption (5.2 million copies)
Mass Effect 2 (1.6 million copies)
Bioshock 2 (3 million copies)
Call of Duty: Modern Warfare (4.7 million units for the PC, 10 million when you add the console sales; worldwide sales)
Left 4 Dead 2 (2.9 million copies)
Borderlands (3 million copies)

That's a lot of purchases. That's a lot of money. That's not counting piracy.

The year isn't over yet (Starcraft 2 and Diablo 3 are up and coming) And those are the ones just off the top of my head. I simply can't believe people are pointing to Quake and saying: "Look at this, Linux can play games too! If it's good enough for me it's good enough for everyone!" Only replies I've gotten are either filled with a denial that it's a problem or they say it can't be done. Try to imagine someone other then a Linux geek who forgoes flash for efficiency, someone who hasn't been snorting kernels since 92.' Isometric 2D games from the nineties and a worn-out graphics engine doesn't cut it for most 'gamers' out there. That's why WINE exists (which doesn't really work all that well for most things and if it does it reduces stability and performance to the point where it's more worth it to re-boot into Windows) and why people dual-boot.

Hmm, maybe the problem with Linux gaming is not a financial barrier but complacency among the Linux community?

---

### Post by dr.frankinfurter on 2010-06-28
> **Simian Man said:**
> Are you asking if it's possible to make a free game of high quality or an open source game of high quality?  Because those are very different questions.

I think it would be possible to make a high quality open source game and then charge for the content - which is by far the most expensive part of making a game.  This is the case with id's games, although they were only open-sourced after the fact.

There are some great free games out there, but expecting something comparable to games that cost millions to make is unrealistic.

Yes, that is is exactly what I am saying. I fully recognize that free != open source. But, I'm just posing the question: Can it be done?

Sure, Quake was a good start and the Source Engine will be a noble effort... but I don't see how an Open Source project can get enough money to create a rival to the numerous aforementioned titles. And, I'm curious about a COMPLETELY open sourced game and not a proprietary/OSS mix. Besides, if the source is available then couldn't someone theoretically produce a imitation?

---

### Post by NightwishFan on 2010-06-28
Ok, how about **you** get up, and go ask them to make games for us. How about it?

I do not mind if there are not any mainstream games for Linux. I suppose you do not seem to get that we are an *open source* community. Thus we only directly support and approve of *open source* games.

Of course that does not mean that mainstream games should not be ported for our platform. As Linus once said, "99% of things I use are under the GPL.. but that is **my** choice."

---

### Post by betrunkenaffe on 2010-06-28
If you Open Source a game, you basically made it free so yes, you are asking if you can make a free game of X quality and then selecting multiple million dollar production games. Sort of feels like trying to compare Avatar to made for TV movies...

I know where you are coming from and given your stringent (and extremely unrealistic) standards, no.

It isn't the programmers, as has been stated, it is the artists, writers and musicians.

Can you get quality OSS gaming, yes.

---

### Post by dr.frankinfurter on 2010-06-28
> **NightwishFan said:**
> Ok, how about **you** get up, and go ask them to make games for us. How about it?

I do not mind if there are not any mainstream games for Linux. I suppose you do not seem to get that we are an *open source* community. Thus we only directly support and approve of *open source* games.

Of course that does not mean that mainstream games should not be ported for our platform. As Linus once said, "99% of things I use are under the GPL.. but that is **my** choice."

Woah, woah, woah, I didn't see what I said to prompt such aggravation.

Also, where did I say that I wanted proprietary games written for Linux? Have you read the original posts? Any posts at all in fact?

I was simply asking a question: Is it possible to produce a open source game of the same quality as a proprietary game? And, if so, how would it be paid for?

Apparently you misunderstand me. I don't want ports, I want native games that are entirely open source. I don't mind if they have a price tag, developers need to compensated for their hard work.

I was also not playing the blame game. I'm not saying any one person or group was incompetent for the state of gaming in Linux. I'm just trying to figure things out.

But, I see that you're probably going to ignore this and fly off the handle again in some brash and entirely rude manner.

---

### Post by cb951303 on 2010-06-28
> **dr.frankinfurter said:**
> I didn't see 'open-source' attached to many of those games. Many of them were built on proprietary technologies (few worked on Linux; most were for Windows). Personally I think the resources used should be open-sourced (like the game engine for example) but some things should be kept proprietary so that it could be sold. This seems to work fairly well and is a trend among companies. Id did it and so will Valve. 
 
sure they are proprietary (although I wouldn't say that they are based on proprietary technologies. world of goo uses sdl, libpng, freetype and opengl) but the key part is that they can be made in OSS business model because they don't require top of the line technology and high budgets. They are "indie" after all. as I said earlier "indie bundle" games open sourced their engine but not their assets. i think it's a good business model and would work from the start.

> 
[Edit: Sorry for the double post. Also:  I'm not sure about 'quality' per say but I would say success would come if you threw enough money at a project. Proof? 'Avatar' had a sub-par story and sub-par acting. It was filled with bash-you-over the head allegories about race and environmentalism (not that it went against or supported my political viewpoints it was just blatant and annoying) and it's 'acting' just ended up looking cheesy and melodramatic. But the thing cost more then I'm worth as a person (joke) and it made a profit. Sure, you could say the director was a visual genius but I've seen similar plant constructs on DeviantArt; he really wasn't original in the slightest. Just goes to show that if you throw enough money into visual effects your going to get something a lot of people will want to see.]

if you throw enough money to a bad project you will end up with a very expensive bad product :) that's a fact. the key to the success of such a product is nothing but marketing. and I think this is a bit off from the original question.

back to the original question: Is [quality] OSS gaming possible?
definitely. you don't need the best technology and a high budget to produce a quality game.

the problem with top-tier games is that they stopped being original a long time ago. every year we play the same games only with better graphics, physics etc... most of the budget for these games go to marketing and unnecessary things like DRM.

---

### Post by NightwishFan on 2010-06-28
>_>?

Anyway, yes it is possible. Stuff as complicated as the Darwin kernel is as well. Though I am sure it would take a lot of work, if it can be done closed it can be done open with enough volunteers or even paid employees.

---

### Post by dr.frankinfurter on 2010-06-28
Thank you all for your replies.

I'm not 100% on it but I'm exhausted and need sleep... and don't want to think about it anymore. I haven't really heard anything definite yet. "If it works closed it will work open" is kind of vague. And part-open/part-closed solutions isn't really that satisfying (I was going for *entirely* open), sorry. I guess I will believe it when I see it. Until then I can only hold respect and awe for all the employees that produced the games that I, and millions others, have enjoyed. I can also respect the proprietary software format since it delivered quality software - regardless of any philosophical/moral quandaries associated with it.

Personally, I still hold the opinion that the part-closed/part-open format would be the most efficient at garnering revenue while still contributing something back to society at the same time.

Just curious to see what people thought of pure OSS games and how to make them as good as what's out there for our competitor.

Oh well, again, thanks for your replies.

Now I'm going to go throw myself into a heap of blankets and sleep till the Earth melts.

---

