---
title: "Directx = linux's biggest enemy?"
date: 2005-07-13
forum: The Cafe
---

### Post by NoTiG on 2005-07-13
I know alot of you like linux the way it is, and thats fine... but there are those who want linux to become mainstream, because if it does become more mainstream on the desktop it will benefit everyone that uses it (for example more manufacturers will make sure their drivers work on it , etc....)

So here is the basis of my reasoning:

The popularity of an OS is determined by computer sales. Put simply, whatever OS is shipped on a computer that is sold will remain on that computer(99% of the time).

Next: computer sales are driven by the game industry. I forgot where i read this quote, but im pretty sure this is true. you dont need 500000000 mhz to run an office program.

Next: games are driven by directx and Opengl. windows Uses both. Linux just uses opengl because directx is proprietary. What this means is that windows will always remain dominant as long as this is true, because to get directx games to work under linux takes from performance(because you have to emulate), and it also takes time. A game that is released in windows... will have to go through a tedious process (probably by transgaming) to become workable, with probable errors. People who play games want the best performance, and they also want to be able to play games when they are released.



So what this means is that even if linux did manage to get sold by computer hardware manufacturers ... it still needs to beat directx somehow. The conclusion is:

Since you can't make directx worse, you have to make opengl better. I'm not really sure how this could be done... how would you make opengl better? how would you get game developers to use it ? 

ANyways, this is just my opinion. I'm sure there are a couple of things that could thwart this reasoning. For instance...  if linux became widespread in education then the next generation would already know how to use it and companies wouldnt need to retrain to switch.. etc.... Also if third world countries started using it mainly, and soon the rest of the world is using it (except US) then US might be forced to switch .

NoTiG

---

### Post by sapo on 2005-07-13
[QUOTE=NoTiG]

Since you can't make directx worse, you have to make opengl better. I'm not really sure how this could be done... how would you make opengl better? how would you get game developers to use it ? 


NoTiG[/QUOTE]


All the unreal, quake and Doom series uses DirectX and have native linux ports, the problem isnt directx.. but the game companies... 

everybody knows that the Unreal Engine Supports OpenGL and directx.. but wait... lineage is based on the Unreal Engine.. but... where is the linux version?  ](*,)

---

### Post by NoTiG on 2005-07-13
> the problem isnt directx.. but the game companies. 

the problem isn't the game companies... if they use Directx because they deem its the best tool for the job its not THEIR fault. the fault lies in the fact that opengl is not as good a solution as direct... which I think could be remedied...They are simply using the best tool for job... and theres nothing wrong with that. you cant expect them to make a "moral " decision and only use opengl. Opengl HAS to be better than directx.

I am pretty sure the graphics of Doom 3 are handled by Opengl alone. IF it does use directX , its probably because DirectX also provides many other interfaces for working with sound, input, etc. OpenGL doesn't include any of this functionality, because it is a pure graphics library..

So maybe that could be a solution for improving opengl... to somehow allow it to work with other interfaces (besides graphics) to make it an all in one package or something that would make life easier on game progammers. 

Any input on someone with experience would be cool... opengl vs directx....

---

### Post by sapo on 2005-07-13
[QUOTE=NoTiG]the problem isn't the game companies... if they use Directx because they deem its the best tool for the job its not THEIR fault. the fault lies in the fact that opengl is not as good a solution as direct... which I think could be remedied...They are simply using the best tool for job... and theres nothing wrong with that. you cant expect them to make a "moral " decision and only use opengl. Opengl HAS to be better than directx.

I am pretty sure the graphics of Doom 3 are handled by Opengl alone. IF it does use directX , its probably because DirectX also provides many other interfaces for working with sound, input, etc. OpenGL doesn't include any of this functionality, because it is a pure graphics library..

So maybe that could be a solution for improving opengl... to somehow allow it to work with other interfaces (besides graphics) to make it an all in one package or something that would make life easier on game progammers. 

Any input on someone with experience would be cool... opengl vs directx....[/QUOTE]


You are not changing the games companies mind just with a better opengl.. they dont give a s**t about linux users... they think linux users dont like to pay for things.. thats why they use linux.. as long windows and directx exists and the companies continue to think in that way.. you are not going to have linux games even if openGL was better..

how much do you think ATI and NVIDIA pay for their "recommended logo" in a game?

Now answer me... for wich is ATI and NVIDIA card optimized? DirectX or OpenGL? 

if you dont believe me.. read this:

[http://www.theinquirer.net/?article=24422](http://www.theinquirer.net/?article=24422)

[quote=theinquirer.net]ATI gave Valve $2.4 million in cash for the deal. ATI also invested $1.2 million in marketing this great game. And last, but not least, was a cool $4.4 million that ATI and its partners spent for bundles. 

That amounts to some $8 million dollars. This is a lot of money, I can agree, but ATI never sold so many mainstream and high end cards in its long history as when it bundled them with the justly famous voucher. It sold an incredible lot of 9800XT and 9600XT cards just because of the nice voucher. That small piece of paper convinced many people to go out and buy ATI card.[/quote]
Now.. the ATI driver is the worst among the worsts.... so... is it interesting to them to have DirectX or Linux OpenGL version of Half Life 2?

I can garantee you.. that if a gamer really wants to play HL2 he is gonna install windows.. so in this case having a linux version isnt a priority...

the problem is more complicated than whe think.. it alway is...

---

### Post by NoTiG on 2005-07-13
> 
You are not changing the games companies mind just with a better opengl.. they dont give a s**t about linux users... they think linux users dont like to pay for things.. thats why they use linux.. as long windows and directx exists and the companies continue to think in that way.. you are not going to have linux games even if openGL was better.. 

I just said that you cant expect to have gaming companies make a "moral" decision

. If opengl was a better API than directx then gaing companies would use it. There is not some broad conspiracy where gaming companies use only directx... they simply use the best tool for the job. And the fact that they use directx is proof.. that it is better for them. 

And if the games were coded in opengl then porting games would be trivial.. and no longer would emulation , performance or timeliness issues be a factor. IMHO

---

### Post by AntiDragon on 2005-07-13
Edit: Ack! By the time I finished this post everyone has beaten me to it!


It's not that simple though (IMO).

Both DIrectX and OpenGL are direct rendering APIs - they are used to directly access a graphics cards capabilities. What a games designer can do visually is limited by the functions provided by the API. Obviously the gamer needs hardware that can support it too! However, it is quite a task to re-write software to use a different API as the way DirectX and OpenGL function are very different.

Unfortunately for us, because DirectX is closed and proprietary, Microsoft have full control over what capabilities they add to DirectX (vertex and pixel shaders for example). Most recently is the shader model 3.0 which massively extends pixel shader abilities - think of the reflective surfaces and water in Half-Life 2 for example. Those use shader model 2 (if you're lucky enough to have a card that uses them.

OpenGL tends to be in a constant state of catch up. It's an open standard (which is a **good** thing) but this limits the speed at which new features can be included.

As MS add more and more to their API, the card manufacturers play catch-up. In essence, MS drives ATI and NVidia towards adding features that match DirectX.

Couple this with the massive market share MS has, consoles like the XBox and XBox 360 and the massive levels of development support MS supplies and it's no wonder games designers will opt for DirectX platforms.  After PC and XBox software will need a rewrite to fit the other consoles. After that it often doesn't seem worthwhile to re-write yet again for a (from their point of view) small minority of Linux users.

Maybe what we need is someone who can supply OpenGL dev kits, like the MS, Sony and Nintendo dev kits that games companies purchase. They make it a lot easier to? develop software by providing not just tools but experts who can be queried for information.

Ah well. Gaming will probably be the final barrier for Linux to break through. But first we just need more users - hence a focus on business etc. Once that's accomplished, Linux is no longer a minority platform and maybe the games companies will take note.

---

### Post by sapo on 2005-07-13
[QUOTE=AntiDragon]Edit: Ack! By the time I finished this post everyone has beaten me to it!


It's not that simple though (IMO).

Both DIrectX and OpenGL are direct rendering APIs - they are used to directly access a graphics cards capabilities. What a games designer can do visually is limited by the functions provided by the API. Obviously the gamer needs hardware that can support it too! However, it is quite a task to re-write software to use a different API as the way DirectX and OpenGL function are very different.

Unfortunately for us, because DirectX is closed and proprietary, Microsoft have full control over what capabilities they add to DirectX (vertex and pixel shaders for example). Most recently is the shader model 3.0 which massively extends pixel shader abilities - think of the reflective surfaces and water in Half-Life 2 for example. Those use shader model 2 (if you're lucky enough to have a card that uses them.

OpenGL tends to be in a constant state of catch up. It's an open standard (which is a **good** thing) but this limits the speed at which new features can be included.

As MS add more and more to their API, the card manufacturers play catch-up. In essence, MS drives ATI and NVidia towards adding features that match DirectX.

Couple this with the massive market share MS has, consoles like the XBox and XBox 360 and the massive levels of development support MS supplies and it's no wonder games designers will opt for DirectX platforms.  After PC and XBox software will need a rewrite to fit the other consoles. After that it often doesn't seem worthwhile to re-write yet again for a (from their point of view) small minority of Linux users.

Maybe what we need is someone who can supply OpenGL dev kits, like the MS, Sony and Nintendo dev kits that games companies purchase. They make it a lot easier to? develop software by providing not just tools but experts who can be queried for information.

Ah well. Gaming will probably be the final barrier for Linux to break through. But first we just need more users - hence a focus on business etc. Once that's accomplished, Linux is no longer a minority platform and maybe the games companies will take note.[/QUOTE]

yep.. thats it.. you just killed the snake and showed the stick  :grin:

---

### Post by NoTiG on 2005-07-13
> 
OpenGL tends to be in a constant state of catch up. It's an open standard (which is a **good** thing) but this limits the speed at which new features can be included. 

So basically the conclusion to your post is that Opengl is not as good as directx because its not updated quickly enough. Is this fixable? Is it possible to update it as quickly? Or are you saying its not possible?

[QUOTE=AntiDragon]

Maybe what we need is someone who can supply OpenGL dev kits, like the MS, Sony and Nintendo dev kits that games companies purchase. They make it a lot easier to? develop software by providing not just tools but experts who can be queried for information.

Ah well. Gaming will probably be the final barrier for Linux to break through. But first we just need more users - hence a focus on business etc. Once that's accomplished, Linux is no longer a minority platform and maybe the games companies will take note.[/QUOTE]


Dev kits sounds interesting. BUt it seems to me that gaming is the ONLY barrier that prevents linux from becoming more mainstream. If computer sales are driven by gaming, and if directx only works with windows, then manufacturers will mainly sell computers with windows OS.

If computer manufacturers sold Linux OS and preconfigured them 99% of linux issues would disappear since they are preconfigured and gaming would be the main one. IMO

---

### Post by sapo on 2005-07-13
[QUOTE=NoTiG]So basically the conclusion to your post is that Opengl is not as good as directx because its not updated quickly enough. Is this fixable? Is it possible to update it as quickly? Or are you saying its not possible?
[/QUOTE]

hum.. i understood what he said in a different way... microsoft holds the standards.. and opengl needs to follow it.. is not OpenGL fault to stay back.. but as long as microsoft is in the top.. OpenGL needs to "copy" the directX features in order to have games running...

---

### Post by AntiDragon on 2005-07-13
[QUOTE=NoTiG]Dev kits sounds interesting. BUt it seems to me that gaming is the ONLY barrier that prevents linux from becoming more mainstream. If computer sales are driven by gaming, and if directx only works with windows, then manufacturers will mainly sell computers with windows OS.[/QUOTE]

I respectfully disagree.  :razz: 

It's not gaming that's the biggest barrier (although it obviously *is* a barrier). It's ignorance, MS FUD and technical polish.

The great mass of PC users are not gamers. They are Mr & Mrs home user. They just want to browse the web, do their tax returns and write snooty letters about the kids down the road! Since every PC they purchase comes with Windows, they don't realise there are alternatives.

Microsoft keeps putting out flyers and posters and ads stating how insecure, slow and unstable Linux is. This is aimed at the companies - Fear, Uncertainty and Doubt.

Finally, Joe Poweruser decides to give Linux a shot. It installs but his hardware setup is so exotic that it never quite works properly. He switches back to Windows.

These are the big barriers. Get Linux into the offices and the workers will use it at home. from there it will spread and become well known. Make it support an ever increasing range of hardware and no-one will need switch back.

And then we take over the world BWAHAHAHAH..erm, I mean "yay"!  :grin:

EDIT:

> If computer manufacturers sold Linux OS and preconfigured them 99% of linux issues would disappear since they are preconfigured and gaming would be the main one. IMO 

Unfortunately this isn't rally an option as MS marketing practices prevent this from being a reality. Antitrust is an ugly word....

---

### Post by NoTiG on 2005-07-13
I agree that getting linux into the workplace can only help in spreading its use. But.... the programs you use are what is most important in determining the operating system. FOr instance i used to have a macintosh performa... the thing was, barely any programs were written for macs compared to regular windows PC's. Now like you said, the average user is just a home user with mundane tasks. As time progresses... free software easily meets these needs. Look at firefox, openoffice... etc. EXCEPT games... and they won't in the foreseeable future **because of DirectX**

---

### Post by jsimmons on 2005-07-13
OpenGL is not supported by MS. If ATI and nVidia provide OpenGL drivers, they do it on their own.

The simple truth is driven by numbers. There's more Windows boxes than anything else combined.  DirextX is (or was) actively being improved by MS.  How aggressively is OpenGL being improved? Not very. When was the last time you heard anything about real changes to OpenGL?  Two years? And before that?

The real issue will be introduced when Longhorn comes out. MS will be dumping DirectX in favor of some new thing (I forgot what they're calling it). This will be so far removed from DirectX that Linux will be that much further behind - again.  And guess what the Game writers are going to write to?  Certainly not OpenGL.

Finally, the open source nature of Linux and everybody's insistance that drivers be OSS impedes driver performance, even from nVidia.  Face it - Linux is NOT hardware friendly in this respect. Efficient and high-performing drivers can indicate architectural details of the hardware, and the hardware manufacturers are not real eager to give away too many hints.

IMHO, OSS drivers are not neccessary. Afterall, they're hardware-specific. As long as they work, I really couldn't care less if I could get the source code.  Also, Linux kernel changes frequently break otherwise working video card drivers.  Why? It seems to me that the video card makers simply can't make it work on Linux, and until they can, the newest games will always be an issue.

---

### Post by AntiDragon on 2005-07-13
But you're thinking DirectX has a lock-in effect. I don't think it does (Warning: Personal Opinion!).

With something like Office, you are locked in because all the documents you write are in .doc format. You need Word to read them and so you use Word to make more (Yeah, I know about OpenOffice.org - I'm trying to make a point though  :-P ).

With Windows, all your programs run (or not!) on Windows, so you keep using it.

With DirectX, it's a set of functions that you use when writing a program. You use it, then move on. Next time, you might use DirectX again. But there is nothing stopping you from using OpenGL. Or assembly code. Or just quitting games design and opening a small Bistro in Paris.

Though only barrier to change is getting adjusted to a new API. And there's plenty of documentation on **that** !  As long as Linux keeps growing, let DirectX have it's way. Because once Linux becomes more mainstream, OpenGL will suddenly become a lot more attractive to the designers! :)

Oh, and if you're worried that ATi and NVidia will stop releasing OpenGL support in their drivers, I don't think that's likely as there's a lot of professional software (3D packages) that either require or prefer OpenGL. So OpenGL will always be part of Windows as well.

Right. I've gotta beat a couple of servers back into line.... ](*,)

---

### Post by sapo on 2005-07-13
[QUOTE=jsimmons]OpenGL is not supported by MS. If ATI and nVidia provide OpenGL drivers, they do it on their own.

The simple truth is driven by numbers. There's more Windows boxes than anything else combined.  DirextX is (or was) actively being improved by MS.  How aggressively is OpenGL being improved? Not very. When was the last time you heard anything about real changes to OpenGL?  Two years? And before that?

The real issue will be introduced when Longhorn comes out. MS will be dumping DirectX in favor of some new thing (I forgot what they're calling it). This will be so far removed from DirectX that Linux will be that much further behind - again.  And guess what the Game writers are going to write to?  Certainly not OpenGL.

Finally, the open source nature of Linux and everybody's insistance that drivers be OSS impedes driver performance, even from nVidia.  Face it - Linux is NOT hardware friendly in this respect. Efficient and high-performing drivers can indicate architectural details of the hardware, and the hardware manufacturers are not real eager to give away too many hints.

IMHO, OSS drivers are not neccessary. Afterall, they're hardware-specific. As long as they work, I really couldn't care less if I could get the source code.  Also, Linux kernel changes frequently break otherwise working video card drivers.  Why? It seems to me that the video card makers simply can't make it work on Linux, and until they can, the newest games will always be an issue.[/QUOTE]


hum.. OpenGL 2.0 is out from some time.. it has improvements.. but the NVIDIA driver i think use some of its functions.. the ATI.. how can i say it... still didnt realize that OpenGL 2.0 is out  :roll: 

here a pdf about OpenGL 2.0
[http://opengl.org/documentation/specs/version2.0/glspec20.pdf](http://opengl.org/documentation/specs/version2.0/glspec20.pdf)

---

### Post by NoTiG on 2005-07-13
[QUOTE=jsimmons]  How aggressively is OpenGL being improved? Not very. When was the last time you heard anything about real changes to OpenGL?  Two years? And before that?

The real issue will be introduced when Longhorn comes out. MS will be dumping DirectX in favor of some new thing (I forgot what they're calling it). This will be so far removed from DirectX that Linux will be that much further behind - again.  And guess what the Game writers are going to write to?  Certainly not OpenGL.

[/QUOTE]

A confirmation of what ive been saying.... Opengl is lackluster. but can it be made better? There is a board or committee that has to approve of changes... but that is also the case with directx. 

I dont think its ignorance that keeps linux from being widespread. You cant simply rely on people to know about it. you HAVE to have hardware manufacturers install it on their computers for sale. Otherwise it will never be mainstream. And here is the thing.. when a computer manufacturer determines the OS they put on their computer here is what they will have to take into account:

Hardware. Will the OS work with the hardware? now obviously , if the manufacturer gets to choose the hardware, they can make it work with linux and this is a non-issue

Usability - Can people use this? Now linux may, or may not be suitable as of now by the average user (installing an application can actually be easier in linux than windows, iwth synaptic for instance) but the point is that it is improving and it Will be. No question.

ANd finally the other thing taken into consideration is:

Programs/software - will people be able to use programs on this computer? As time progresses more and more viable choices are available, so it may or may not be the case as of now but it is improving, so it will be as well. Except... games. ANd this is the area where linux is NOT improving... because of directx.

---

### Post by NoTiG on 2005-07-13
[QUOTE=AntiDragon]But you're thinking DirectX has a lock-in effect. I don't think it does (Warning: Personal Opinion!).
[/QUOTE]

I think you are confusing a legitimate, and illegitimate lockin effect :P . YOu see...  theres nothing forcing gaming companies to use directX . BUt the fact that its BETTER , for them... is in essence a legitimate lockin.. as opposed to an illegitimate one like you just mentioned.

---

### Post by NoTiG on 2005-07-13
So let me summarize what im trying to say again and why directX is an important enemy IMO....

Linux is improving greatly , but the only area it is not is games. Games are a huge driving force in the hardware industry. ANd the hardware industry is what drives The os market. Whatever OS is shipped on a computer will likely remain.  THerefor as long as games are lackluster on linux compared to windows,  windows will remain mainstream.

Now what most of you are saying is that the games barrier... while it is not improving now, will come around once more users gradually shift. The reason why I disagree is because of directX... windows is widely available and those that do shift to linux will most likely still have access to windows which means games manufacturers will use the **best tool for the job**  rather than say to themselves "oh , more people are switching to linux, maybe we should have opengl ports" . In which they most likely  wont because those people will have access to windows as well.

---

### Post by AntiDragon on 2005-07-13
I know what you mean, but the point of a lock-in (legitimate or otherwise) is that it's difficult to break free from. A graphics API is not a lock-in.

Graphics cards have a set of capabilities. These capabliities can be accessed through any API you like. If you don't like DirectX or OpenGL then you could write an entirely new one. Call it "SuperGraphicsLanguage" or "BobGL"  :razz:  - as long as you know what the card can do you can write an API for it. At the end of the day it all get's turned into machine code. It's even possible to convert one API into another (Cedega does this on the fly).

Games companies do not just use DirectX because the non MS consoles do not use DirectX. They have there own custom APIs for controlling their hardware. When new consoles are released, there are new APIs. In fact the same is true of DirectX as well because of how dramatically it can change between versions - sometimes things are removed or cahnged, not just added. Alos, the GameCube uses it's own API (not DX or GL) yet uses ATi garphics. They wrote there own to match the exact capabilities of their hardware.

Learning to use a new API is not a small deal, but games companies do it all the time.
If you imagine Linux as a new console and OpenGL as it's preferred API then one day, when Linux achieves critical mass, the games companies will start using OpenGL more as well.

True, it's a bit of a catch 22 - to encourage Linux games, we need more Linux users but to get more Linux users we could do with Linux games. However, unlike a console, games isn't the only thing Linux has going for it. It can grow and expand without games for now - they can come later, and **they will** come, believe me.

DirectX is never going to prevent a switch to other APIs. But it is dangerous as a marketing ploy because it makes it more difficult to see the alternatives. Of course, this is true of just about any proprietary technology MS markets.

For now, I can live with Unreal Tournament and Neverwinter Nights!  :grin:

---

### Post by AntiDragon on 2005-07-13
[QUOTE=NoTiG]So let me summarize what im trying to say again and why directX is an important enemy IMO....

Linux is improving greatly , but the only area it is not is games. Games are a huge driving force in the hardware industry. ANd the hardware industry is what drives The os market. Whatever OS is shipped on a computer will likely remain.  THerefor as long as games are lackluster on linux compared to windows,  windows will remain mainstream.

Now what most of you are saying is that the games barrier... while it is not improving now, will come around once more users gradually shift. The reason why I disagree is because of directX... windows is widely available and those that do shift to linux will most likely still have access to windows which means games manufacturers will use the **best tool for the job**  rather than say to themselves "oh , more people are switching to linux, maybe we should have opengl ports" . In which they most likely  wont because those people will have access to windows as well.[/QUOTE]

Only if people continue to buy PCs with Windows pre-installed!

The only reason most people dual-boot is because they started with Windows first.  As more people use Linux, you'll find that less will dual-boot. When bigger OEMs start offering Linux PCs, they won't be dual-boot as that would kill the price advantage.  This could be years away and no doubt DirectX will slow the process, but one day Linux will be a viable gaming platform that's attractive to developers. Hell, it already is to a tiny few! Especially with the upcoming improvements to direct rendering in X.

I'm really enjoying this debate! Come on, shoot me down! :-P

---

### Post by Knome_fan on 2005-07-13
This whole discussion is seriously flawed.

1. The premise that computer sales are driven by the games industry is simply false. Just look at all the companies complaining about computer games becoming more and more irrelevant as consoles get more and more important.

2. Contrary to what some people seem to believe here OpenGL isn't lackluster but is very well able to compete with directx on a technical level. Just look at the latest doom to see what it is capable of, for example.

3. The reason that hardware companies don't sell computer with Linux (well, to be precise, almost every computer company sells linux computers, you are talking about deskotp computer) sure isn't that there aren't as many games on linux as there are on windows.  There simply isn't enough demand yet from private purchasers and there are still the problems with MS if you ship with anything other than Windows.

---

### Post by NoTiG on 2005-07-13
[QUOTE=AntiDragon]Only if people continue to buy PCs with Windows pre-installed!

The only reason most people dual-boot is because they started with Windows first.  As more people use Linux, you'll find that less will dual-boot. When bigger OEMs start offering Linux PCs, they won't be dual-boot as that would kill the price advantage.  This could be years away and no doubt DirectX will slow the process, but one day Linux will be a viable gaming platform that's attractive to developers. Hell, it already is to a tiny few! Especially with the upcoming improvements to direct rendering in X.

I'm really enjoying this debate! Come on, shoot me down! :-P[/QUOTE]

 I only mentioned that windows would still be widely available because OEMS wont start including linux until its more widespread, and it wont become more widespread until people start installing it on their pre-windows installed computers anyway. But even if it does become more widespread, a large majority will most likely still have windows... Strictly because of games. ANd oems will see that.  WHy else would they still keep windows? THe reasons dwindle... Except for games.  If you look at alot of the threads on "why i havent switched completely yet" or the like, i think you will be surprised of how many don't because of games.  If directX becomes an even better option in the future than opengl then i think its very bad for linux.....

---

### Post by NoTiG on 2005-07-13
[QUOTE=Knome_fan]This whole discussion is seriously flawed.

1. The premise that computer sales are driven by the games industry is simply false. Just look at all the companies complaining about computer games becoming more and more irrelevant as consoles get more and more important.[/QUOTE]

I disagree with this... IF all people needed to accomplish were mundane tasks like typing up documents, and writing emails... then what need to invest such a large sum of money in newer computers? If companies are complaining about computer games and making them is a waste, then why are they still being made? making games is a business like any other... if there was no money in it they wouldn't be made. THere is nothing that is forcing them to
.
> 
2. Contrary to what some people seem to believe here OpenGL isn't lackluster but is very well able to compete with directx on a technical level. Just look at the latest doom to see what it is capable of, for example.

I agree that it is Capable... but there is obviously a reason why more gaming companies choose it. Perhaps because directx comes as an all in one package that makes things easier ? Like audio, input etc...

> 
3. The reason that hardware companies don't sell computer with Linux (well, to be precise, almost every computer company sells linux computers, you are talking about deskotp computer) sure isn't that there aren't as many games on linux as there are on windows.  There simply isn't enough demand yet from private purchasers and there are still the problems with MS if you ship with anything other than Windows.

Yes of course, MS monopoly tactics have an impact on linux usage. Linux is free, while microsoft costs something, therefore if a company were to offer both you should see a realistic difference in their prices. the linux one should be cheaper than the microsoft one... but even if it was, would people sitll want it, if it couldn't use their programs(games) ?

---

### Post by AntiDragon on 2005-07-13
OK. You have a point. But it comes down to

"Is being able to play games the biggest factor in choosing a PC/OS?"

I don't have statistics or numbers - a lot of my info is second hand or from the press. I dop have experience from a corporate perspective but that's only one side of the coin.

I believe that yes, the size of the Linux games library will have a big impact on Linux adoption by the general public. Subsequently you enter the chicken and egg situation - games for Linux or Linux to play games?

I don't believe it will remain that way though. I don't believe (avid games player though I am) that the games playing public is the biggest part of the market. I believe the biggest market is corporate. After that you have the prodcutivity users. *Then* you have the gamers. And then the actual IT "geeks" - I hate that word... -  who currently hold the biggest portion of Linux use.

Corporate adoption is rocketing away. Linux is already Corporate ready and as more goverments and companies publicise their success, more move to Linux. In turn, the employees are mostly Productivity Users. They will have few (if any) problems switching to Linux at home.  

Now imagine this. A lot of companies use Linux. And so do a lot of home users. By now Linux DRI is improved and some hardware manufacturers are making Linux drivers. Linus is no longer marginalised. OpenGL already exists and is in use soooo... a few games developers make ports of their popular. This starts to draw the eyes of the gaming crowd. A few try moving to Linux and but the games. And so a few more developers do ports as well. And so on...

It's only a stab at the future. It's also an optimistic guess. But I think it's quite plausible.

(Throws ball back to NoTiG.) :-P

---

### Post by AntiDragon on 2005-07-13
[QUOTE=NoTiG]... IF all people needed to accomplish were mundane tasks like typing up documents, and writing emails... then what need to invest such a large sum of money in newer computers? If companies are complaining about computer games and making them is a waste, then why are they still being made? making games is a business like any other... if there was no money in it they wouldn't be made. THere is nothing that is forcing them to[/QUOTE]

Ah, but (again, thanks to MS inspired tradition and corporate greed...mmmm..greed...) those kind of productivity users don't really know what they need in terms of hardware, nor do they want to. And don't forget the ever present pressure to upgrade to latest greatest versions of Windows and Office - each more resource hungry than the last.

As for the games companies - the biggest proportion of their income is actually from console sales.  Some companies are of course dedicated to making PC games first but it's console versions that bring in the big bucks. Because consoles are dedicated gaming machines whereas PCs (Linux or WIndows) are multi-purpose. Everyone who owns a console plays games on it. Not so with PCs. This is of course balanced by the ease of development (score one for DirectX) and a PCs bleeding edge reputation. But you can't say 100% of PCs are used to play games like you can with consoles.

---

### Post by NoTiG on 2005-07-13
I agree that linux is improving in alot of those areas you mention and more. However, lets assume that games were NOT the major driving force of hardware sales. Lets say they are only 10% . Now you are a hardware manufacturer... will you virtually eliminate 10% of your sales from gamers by switching to linux? I don't think so. And I don't think linux will satisfy gamers as long as directX remains chosen more often by the game developers than openGL.  Now lets say down the road... that linux use surges in the coprorate area. Does that mean that desktop linux usage will increase? Most likely. But will opengl somehow magically all of the sudden become better than directx? More game companies might be interested in it, but what linux is about is being BETTER than the competition, and if opengl is not better than directX... then it simply wont be as good as windows (from a gamers perspective, and most gaming companies probably wouldnt want to be forced to use a tool that isnt the best that they could have. 

I think linux is improving in all areas, except games. that is why i see games as linux's biggest enemy, or more precisely directx!

---

### Post by AntiDragon on 2005-07-13
[QUOTE=NoTiG]I agree that linux is improving in alot of those areas you mention and more. However, lets assume that games were NOT the major driving force of hardware sales. Lets say they are only 10% . Now you are a hardware manufacturer... will you virtually eliminate 10% of your sales from gamers by switching to linux? I don't think so. And I don't think linux will satisfy gamers as long as directX remains chosen more often by the game developers than openGL.  Now lets say down the road... that linux use surges in the coprorate area. Does that mean that desktop linux usage will increase? Most likely. But will opengl somehow magically all of the sudden become better than directx? More game companies might be interested in it, but what linux is about is being BETTER than the competition, and if opengl is not better than directX... then it simply wont be as good as windows (from a gamers perspective, and most gaming companies probably wouldnt want to be forced to use a tool that isnt the best that they could have. 

I think linux is improving in all areas, except games. that is why i see games as linux's biggest enemy, or more precisely directx![/QUOTE]

OK. Score another one for NoTiG  ;-) 

I think it comes down to choice and opportunity. Hardware manufacturers won't be affected either way. The OS that gets' run on their systems makes little difference for them. As long as it's popular enough, they'll write their drivers.

OEMs like Dell and HP may have a dilemma. Ideally, you'd offer a choice of Linux, Windows and dual-boot. That way no-one gets alienated and you attract a share of the Linux lovers. Unfortunately MS' little "encouragements" prevents this kind of scenario. Maybe this will change with further Anti-Trust cases? If so, Linux would be available to gamers without harming the OEMs.

With regards to OpenGL improvements, I'd suspect that progress would increase. Bear in mind, DirectX is developed in concert with ATi and NVidia. If OpenGL was a more common API then I wouldn't be surprised to have them getting involved in it as any popular API is good for the graphic card companies. Such involvement can really speed up development of a standard.

---

### Post by MetalMusicAddict on 2005-07-13
I love reading this topic. :)

I do think however that polish and knowlege are linux biggest enemys. You give Mom & Pop user lookin at Best Buy a slick UI that takes advantage of the hardware and maybe a couple of classes I think people will start to take a chance.
Tech support is also an important part.

Ease of use and knowlege is what people need. Unless you one of those Linux people who doesnt want to "spread the word" and remain l33t. ;)

---

### Post by Knome_fan on 2005-07-13
[QUOTE=NoTiG]I disagree with this... IF all people needed to accomplish were mundane tasks like typing up documents, and writing emails... then what need to invest such a large sum of money in newer computers? 
[/quote]
Well, a lot of people and a lot of compnies don't upgrade. Others may need new hardware anyway as there old hardware is simply broken or their old hardware may not even be able to handle the "mundane tasks" anymore or the want to do some multimedia stuff.

You seem to make the mistake of taking one use of PCs that might be important to you and declare it important to anyone or the vast majority of PC users. However, for about 99.999999999% of all corparate desktops games are a total non-issue as they are for a vast part of private PC users.

[QUOTE=NoTiG]
If companies are complaining about computer games and making them is a waste, then why are they still being made? making games is a business like any other... if there was no money in it they wouldn't be made. THere is nothing that is forcing them to.
[/quote]
Huh? Where did I suggest that something is forcing them to? Please don't misrepresent what I wrote. To say it again, the PC as a gaming platform is rapidly becoming less relevant when compared to consoles. There are countless articles discussing this very issue on the net.

[QUOTE=NoTiG]
I agree that it is Capable... but there is obviously a reason why more gaming companies choose it. Perhaps because directx comes as an all in one package that makes things easier ? Like audio, input etc...
[/quote]
Simple again. No, it's not directaudio, it's the simple fact that directx is part of the OS that comes preinstalled with about every computer sold out there? So why exactly should they choose something else?

---

### Post by AntiDragon on 2005-07-13
[QUOTE=MetalMusicAddict]I love reading this topic. :)

I do think however that polish and knowlege are linux biggest enemys. You give Mom & Pop user lookin at Best Buy a slick UI that takes advantage of the hardware and maybe a couple of classes I think people will start to take a chance.
Tech support is also an important part.

Ease of use and knowlege is what people need. Unless you one of those Linux people who doesnt want to "spread the word" and remain l33t. ;)[/QUOTE]

Hehehe..Yes...Come join us.... You know the Truth...Bwahaha..

(Must go take my medication now!).


Linux as a desktop OS is constantly growing. Everytime we perceive a weakness in it, you can bet some uber-hacker will fix it up nicely.  It started off so far behind Windows in the useability stakes and now it's rocketing ahead. In some areas it matches or exceeds Mac OSX for user-friendliness. Of course, as whole there's still a whole lot to do, and gaming is one of the the weak spots.

Roll on Linux. Or GNU/Linux. Or FOSS. Or OpenSource or..or...(um..need more acronyms please?)

---

### Post by dcraven on 2005-07-13
I think I'm with Dragon on this one. I'm not sure it's in our best interest to now begin pouring resources into facsilitating a dieing market (PC games in the face of consoles). There are more important fronts on which to 'battle', and that is the direction we are moving in.

In time, it is possible that Linux's popularity might grow to the point where it is a viable market for more gaming companies to play in, but that should be secondary. Our focus should be more on convincing companies and other level-headed decision makers that Linux is a good solution and leave the gamers <generalization> and script kiddies</generalization> as a secondary goal. That's a tall and steep mountain to climb, and we're still in the foothills. To compete in this arena involves cooperation with gaming companies and hardware manufactures, both of which have their testicles firmly gripped by the makers of DirectX. The route we are moving in involves less cooperation from controlled entities like this, and also targets a larger population. 

This is my half informed opinion.

~djc

PS: If you truly want to help our cause, then get involved. There are many attractive technologies in the works for Linux that will improve the overall experience of an OSS desktop (Cairo comes to mind) and that may or may not be ready for general use by the time Longhorn arrives. When Longhorn arrives, it will take a large chunk of the user base that we've aquired since the XP release away from us unless our desktop offering is improved by then. Microsoft has the advantage of money and marketing, the only advantage we can afford is being first to market with some of the features that Longhorn touts. Coding, docs, translations, or even just spreading an **informed** word about these advancements are desperately needed now. Even the tinyest, seemingly insignificant effort contributes to the overall cause.

---

### Post by AntiDragon on 2005-07-13
> o compete in this arena involves cooperation with gaming companies and hardware manufactures, both of which have their testicles firmly gripped by the makers of DirectX 

Ouch!  :? 

Actually, the majority of hardware vendors couldn't care less about DirectX (Modems, network cards, HDDs etc). Get them making Linux drivers and you've won half the battle as Linux will be even easier to get running on starnge hardware combos. Once they're supporting Linux I wouldn't be surprised to see the GPU makers getting more involved with driver support and OpenGL.

I don't think gaming will make or break Linux as a platform. But I do think it musn't be ignored. I don't think playing catchup to DirectX will be a big problem. But I do believe that OpenGL needs to catch up eventually and then exceed it.

Unfortunately I'm not much of a coder so I can't play a direct roll. But we can all help by (gently) teachin people about the alternatives to MS. Then one day everyone really have a real choice. (Hopefully it'll galvanise MS into more honorable practices and better software too!)

```
umount /dev/soapbox
```

---

### Post by NoTiG on 2005-07-13
I agree that linux is constantly improving and getting better, but wouldnt you agree that the gaming side of linux isn't? now Gaming might be a small factor for normal home users , but the question is this: If linux can do what the average user can, and if windows can do what the average user wants + 10% more than linux (10% being games), then will the 30-40$ price difference (is that how much an OEM windows license costs?) make enough difference to someone if they could actually have a choice and pick which one they wanted? .  Would non - gamers still pick windows just to have the option in case they wanted it ? 

IF ati and nivida manufacturers are working with directx... what if in the near future it gets so far ahead of opengl that if linux was more widespread, it would still be handicapped by an inferior  gaming API ? Or are you saying that computer gaming will die in the future... which i seriously doubt. THe mouse and the keyboard are simply better controls for games, making it more fun. Try playing an FPS with one of those stick controllers! . 

So... a good statistic that could actually be of use to this discussion is, How much are hardware computer sales driven by games ?

---

### Post by GazaM on 2005-07-13
I've been reading this whole topic, and it seems that the majority of you are misinformed. 

Firstly, you should be comparing Direct3D to OpenGL, not DirectX. DirectX refers to a whole bunch of api's, such as DirectSound and Direct3D. In terms of the current state of the technologies, OpenGL is just as capable as Direct3D.

Secondly, once hardware manufacturers start giving proper OpenGL 2 drivers and games start using it you will see that OpenGL 2 is in fact very superior to Direct3D at the moment and in the near future. To give you something to think about, Doom3 uses only OpenGL 1.5 and looks vastly superior to any game I've played this year, including Half Life 2, so just imagine what OpenGL 2 games will look like.

Next Point, everybody seems overly worried about Microsoft, but in terms of gaming the real leader of the pack is Sony's Playstation. If any of you gamers out there have been reading up  on the next gen consoles you would know that the PS3 will be using none other than OpenGL for it's API, and that there is speculation of them selling an official hard-drive with a form of linux pre-installed. For the short-term future game developers will be concentrating on the next-gen consoles and working down to pc, because they will be more powerful than PC's for a short time anyway, as is always the case with new generation consoles. This is good news as many many developers doing PS3 games will learn OpenGL 2 and see it's advantages and ease of use, meaning that they will consider it a LOT more viable an alternative than Direct3D than before.

All in all, I am very optimistic about the future of gaming in linux, and for me one of the main issues for game dev's is not the graphics api, but sound. Linux is all over the place when it comes to sound, and IMO we need to settle on one api that works and has support for surround sound as is  very popular for new games.

---

### Post by AntiDragon on 2005-07-13
I'll see if I can't find some actual facts and figures.

With regards to price point, it's not just the license of the OS. There's AV, AntiSpyware, Office, image apps and a hundred other apps that cost a bomb. Considering these are also included in most OEM bundles you can often save up to £200 (from experience) if an OEM agrees to sell a blank PC. Of course, MS also discourages this too!

Linux gaming *is* improving. On both the actual OS support side and the number of companies that create Linux ports. It's just that this progress is glacial compared to the leaps and bounds in other areas. Maybe this would fit with the proportion of Linux users who think games is the top priority? I'm not sure.

---

### Post by AntiDragon on 2005-07-13
[QUOTE=GazaM]I've been reading this whole topic, and it seems that the majority of you are misinformed. 

Firstly, you should be comparing Direct3D to OpenGL, not DirectX. DirectX refers to a whole bunch of api's, such as DirectSound and Direct3D. In terms of the current state of the technologies, OpenGL is just as capable as Direct3D.

Secondly, once hardware manufacturers start giving proper OpenGL 2 drivers and games start using it you will see that OpenGL 2 is in fact very superior to Direct3D at the moment and in the near future. To give you something to think about, Doom3 uses only OpenGL 1.5 and looks vastly superior to any game I've played this year, including Half Life 2, so just imagine what OpenGL 2 games will look like.

Next Point, everybody seems overly worried about Microsoft, but in terms of gaming the real leader of the pack is Sony's Playstation. If any of you gamers out there have been reading up  on the next gen consoles you would know that the PS3 will be using none other than OpenGL for it's API, and that there is speculation of them selling an official hard-drive with a form of linux pre-installed. For the short-term future game developers will be concentrating on the next-gen consoles and working down to pc, because they will be more powerful than PC's for a short time anyway, as is always the case with new generation consoles. This is good news as many many developers doing PS3 games will learn OpenGL 2 and see it's advantages and ease of use, meaning that they will consider it a LOT more viable an alternative than Direct3D than before.

All in all, I am very optimistic about the future of gaming in linux, and for me one of the main issues for game dev's is not the graphics api, but sound. Linux is all over the place when it comes to sound, and IMO we need to settle on one api that works and has support for surround sound as is  very popular for new games.[/QUOTE]

Yes. I agree. I think we all tend to ignore the other (non graphical) aspects of DirectX.  Of course an argument could be had that having a complete unified API for all game related I/O is easier to work with than having to choose seperate APIs from a list of many.

---

### Post by NoTiG on 2005-07-13
[QUOTE=GazaM]I've been reading this whole topic, and it seems that the majority of you are misinformed. 

Firstly, you should be comparing Direct3D to OpenGL, not DirectX. DirectX refers to a whole bunch of api's, such as DirectSound and Direct3D. In terms of the current state of the technologies, OpenGL is just as capable as Direct3D.

[/QUOTE]

I said early in this post " DirectX also provides many other interfaces for working with sound, input, etc. OpenGL doesn't include any of this functionality, because it is a pure graphics library..

So maybe that could be a solution for improving opengl... to somehow allow it to work with other interfaces (besides graphics) to make it an all in one package or something that would make life easier on game progammers."

THis post isnt meant to compare just DIrect3d to opengl, although that is also necessary, but to determine why the gaming producers use the DirectX api over open, non-proprietary alternatives.
> 
Secondly, once hardware manufacturers start giving proper OpenGL 2 drivers and games start using it you will see that OpenGL 2 is in fact very superior to Direct3D at the moment and in the near future. To give you something to think about, Doom3 uses only OpenGL 1.5 and looks vastly superior to any game I've played this year, including Half Life 2, so just imagine what OpenGL 2 games will look like.

I have been reading some other opengl vs directx threads that i searched for. Most are out of date. but one common thing mentioned about HL2 vs doom3 is the water effects.....

> 

Next Point, everybody seems overly worried about Microsoft, but in terms of gaming the real leader of the pack is Sony's Playstation. If any of you gamers out there have been reading up  on the next gen consoles you would know that the PS3 will be using none other than OpenGL for it's API, and that there is speculation of them selling an official hard-drive with a form of linux pre-installed. For the short-term future game developers will be concentrating on the next-gen consoles and working down to pc, because they will be more powerful than PC's for a short time anyway, as is always the case with new generation consoles. This is good news as many many developers doing PS3 games will learn OpenGL 2 and see it's advantages and ease of use, meaning that they will consider it a LOT more viable an alternative than Direct3D than before.  

I have heard vaguely of this... I wonder if what they are using to develop these games is a whole kit, more than just opengl ? Its hard to believe that developers, whos job is creating games, haven't done all of the research ... and use directX not because its better but because they are ill informed and ignorant. But i guess its possible...

> 
All in all, I am very optimistic about the future of gaming in linux, and for me one of the main issues for game dev's is not the graphics api, but sound. Linux is all over the place when it comes to sound, and IMO we need to settle on one api that works and has support for surround sound as is  very popular for new games.

THis perhaps is the whole point of my post... if Opengl is good and keeping up with direct3d then maybe what needs improving  are the other API's that are typically involved, which come bundled with DIrectX !

---

### Post by Kvark on 2005-07-13
There are more important areas then trying to catch up on gaming. Most importantly linux distros that are a lot easier to use then the next windows release and productive linux programs that beat the windows equiliants by a noticeable margin.

The biggest enemies are word, excell, dreamweaver, flash (the editor), photoshop and other productive programs. Getting years ahead of all those would be the biggest advantage linux can hope for.

Yes, linux needs a bigger market share, but that maket share is IMO the corporate world, not the gamers.


Linux = What you use to do productive things, office tasks, graphical design, whatever work you happen to be doing on a computer.

Windows = Toy that you use to play games.

That market split seems much more realistic then trying to beat windows on all areas.


...but who knows, maybe the next release of windows will clog up so much resources that it actually goes faster to emulate games on linux then to run them on whats left of the system resources after booting windows.

---

### Post by AntiDragon on 2005-07-13
See [this page](http://www.the-infoshop.com/press/fi22603_en.shtml) - the data's a bit old but quite interesting. It bears out that as far as gaming is concerned, it's all about the consoles. And so far Sony is king of **that** particular hill.

I don't think you can acurately gauge how much PC hardware sales are gamer dependent as powerful systems are needed for servers and database apps. The only part of a PC that is really keyed to games is the graphics cards. Only NVidia and ATi do a good job of convincing business users to purchase high end card with their systems (Ignorance is a useful money making tool). 

Although I suppose you could argue that most Athlon FX and P4 EE systems are also for gamer use...

It really shows though when you consider that PC hardware numbers outnumber all the consoles combined (no proof, but almost certainly true) yet PC games software revenue only makes up a fraction compared to console games software.

---

### Post by NoTiG on 2005-07-13
It is probably hard to guage what % of users are gamers... but there are a couple of things that could skew the results. 

Free games - these wouldnt be listed on profits for software pc games, so they may not be noticed, but may drive hardware sales some , albeit not as much as what a cutting edge game would get (anyone know of any good free directx games for instance?) 

Pirated games - these wouldnt be listed either

THe difference between console and PC... now maybe there are alot more games being sold for consoles... but maybe thats because those who play computer games use far fewer games, but the ones they do use are like an obsession. For instance.... People are Obsessed with MMorpg's like World of warcraft. Their computers are basically like single purpose machines, whereas in general console users will play a more diverse set of games. 

ANyway... 4.6 billion isnt chump change :P

So far , the other enemies to linux that have been stated are: Ignorance, MS Corruption of OEM and how they strongarm them so they don't include linux or OS-less computers, and some programs (dreamweaver, photoshop) .

Now I agree that alternatives to those programs are necessary, but are they really what the average home desktop user needs? a 600 dollar photoshop program? i doubt it. 

As far as ignorance goes, it is an enemy of course... but IF linux was offered alongside windows... and the computer was cheaper, and it came with a bunch of cool free software that you had to pay alot for in windows, then that itself would make them question what it was about which would mitigate the effects of ignorance.

Now the strong arming tactics of MS on OEMs... That is a big enemy... but i see it as fixable.. at least easier to fix than convincing companies to switch from directX. How come the court didnt stop MS from doing this when they went to court several years ago?

---

### Post by AntiDragon on 2005-07-13
Bear in mind my £200 quid was an avaerage. It can vary wildly depending on the OEM bundle.

You're right, just because PC gamers are a small market doesn't make it insignificant. But when you think that more effort is spent on consoles (don't forget mobile phones and handhelds), it does make DirectX less of a factor as it's probably the least important API. In fact, you could argue we should have a library on Linux that implements Sony's Playstation API! Now **that** really would make Linux a game developers goldmine!

DirectX API is big and pervasive, but mostly from a marketing perspective. In terms of value and incentive to use it, Sony's API is more important. It's just no-one outside of a games company has heard of it. So It's not DirectX per-say that is preventing the growth of PC gaming but plain and simple market share.

---

### Post by AntiDragon on 2005-07-13
BTW (and this is just my opinion), I don't think you can include something like DirectX as antitrust material in the same way as Internet Explorer. It's not an OS component, it's a set of programming libraries (think libc etc.). Ruling against it would be like ruling against POSIX or the core WIN32 API.  The fact that it's a portable API is irrelevant - so is OpenGL and SDL and others.  The annoying thing is that unlike other open APIs, DirectX is closed so it's up to MS to decide how portable it is. There is certainly no major technical hurdles to porting DirectX (or a subset) to Linux. But why would they want to, eh? :smile:

---

### Post by NoTiG on 2005-07-13
Hmmmm. I guess if sony can create their own API around opengl, then it should be possible in the future, If linux was more mainstream, to have a better API around opengl for game developers. 

 I wonder specifically what their api is besides plain old opengl? I wonder how hard it was to create? Maybe something like theirs is what linux needs to become better?

Wouldnt it be nice if sony gave it for free and open sourced it ? I mean.... its not like microsoft will use it. THey will use their own proprietary directx anyway. Would that make sony playstation games compatible with regular computers ? would that make it easier to pirate them ?

---

### Post by sonny on 2005-07-13
I think you're forgetting something important here... companies WOULD make their games for Linux if the cost ISN'T high, that is why I think "Loki" SHOULD play a mayor role in gaming for Linux, Loki needs ALL our support, so he can sell the game company the idea of Loki making a "Linux Installer" free of charge, so people could BUY the original game, and then download the "Loki Installer" as it's been done right now, BUT on a BIGGER scale. I'm a gamer; back when I was 15-17 (about 7 years ago) I had about 25 different games installed in my PC, two years ago (I still had windows) I had about 10 games installed, and I WANT to see really cool Linux games, but I don't think Loki is doing the job as well as it could be done. They have just a few games, but they have to SELL the idea to the big companies, and make more Linux installer, then the game companies will realize that there's a growing market for games in Linux, and the one that conquers now will be king forever.

---

### Post by AntiDragon on 2005-07-13
[QUOTE=NoTiG]Hmmmm. I guess if sony can create their own API around opengl, then it should be possible in the future, If linux was more mainstream, to have a better API around opengl for game developers. 

 I wonder specifically what their api is besides plain old opengl? I wonder how hard it was to create? Maybe something like theirs is what linux needs to become better?

Wouldnt it be nice if sony gave it for free and open sourced it ? I mean.... its not like microsoft will use it. THey will use their own proprietary directx anyway. Would that make sony playstation games compatible with regular computers ? would that make it easier to pirate them ?[/QUOTE]

Sigh. So many dreams...I wish it were likely.  An API can be in any form - they're just a layer to simplify control of the hardware. Graphics cards aren't DirectX or OpenGL or anything. They just have capabilities. The drivers supplied give interfaces that can be used by an API to make it easier to write games that use the cards to their full potential. In our case, drivers supply an interface to be used by OpenGL or DirectX. In the case of Sony, the API translates directly to instructions to the hardware.  

As long as you know what code an API produces (machine code) and what it then expects the card to do, it's possible to write drivers that support it. So this way you can reverse engineer an existing API or (as Cedega does) translate one set of API calls into another - So DirectX calls become OpenGL calls which then get passed to the driver and then translated into calls that the graphics card understands.

After all, ATi cards and NVidia cards probably use completely different calls internally. The drivers they write act as translators and DirectX and OpenGL are the common languages.  Remember 3Dfx and glide? They created an API specifically for there cards. This let programmers take full advantage of them. But it didn't work for any other 3D cards. They ended playing catchup to make their cards work well with DirectX and OpenGL.

At the end of the day, APIs can come and go. As long as they're documented and supported by the hardware drivers, we can always have a new API.

---

### Post by Brunellus on 2005-07-13
[QUOTE=NoTiG]I disagree with this... IF all people needed to accomplish were mundane tasks like typing up documents, and writing emails... then what need to invest such a large sum of money in newer computers? [/QUOTE]

Escalating hardware requirements for basic software.  WinXP, IE, and MS Office run quite happily on a recent-vintage Pentium 4 and plenty of RAM (256-512 MB)....but not so happily on older machines.  A friend of mine has recently upgraded from Win98 to XP on his old 300 Mhz box, and the horrible performance has got him seriously thinking about ditching Windows, at least on that box.

The consumption pattern for software/hardware seems to be driven by a cycle:  increased hardware capabilities beget bloated programs, which in turn require further increases in hardware capabilities to run. 

In fairnes, not all "bloat" is bad--some is progress.  But the core systems are only getting bigger because new, more powerful machines are always available which will mask their bloat through better performance.

---

### Post by NoTiG on 2005-07-13
So i guess if there was a way to improve opengl, it would either be by making the updates to it more frequent (not likely) , or like DirectX , make  tools to deal with such components of a game as sound, music, input, networking, and multimedia all integrated into a coherent standard development kit ? Is that possible ? 

I've been reading some opengl vs directx articles... here are some quotes:

> they both run the same, opengl is just easier to program, and has 2 mb of librarys, headers, and dlls, as opposed the 100mb or whatever of DirectX, go with openGl 

> OpenGL gets updated faster than Direct3D, because you must rely on Microsoft to update the API, whereas any OpenGL provider can update the API to expose their cards' features. In short, OpenGL is MORE capable than Direct3D. Direct3D drivers are usually more reliable than OpenGL drivers, so most developers choose the route of least cost to maintain.  

> With the inclusion of vertex and fragment shaders into the core OpenGL API, we can now safely assume that OpenGL is as capable as Direct3D.

With OpenGL 2.0 supporting hardware for PC hitting the market, I believe the recent dominance of Direct3D in the gaming market will be reduced.

Also, DirectX is very shabby at producing accurate graphics - see the anti-aliasing results and the (now available) pixel shading results and you will see the that OpenGL can beat DirectX in terms of quality anytime.

I suppose that's why it is used as the primary API for professional graphics. And if you wnat to make a living earning more than a game programmer, then start learning OpenGL. The professional 3D industry rewards its OpenGL sons very well. 

> I've written a few minor games in DirectX, and I've been reading up on the differences. From what i've understood, OpenGL is a little more powerful, slightly more hardware-orented, and very similar in theory to Direct3D. DirectX has a wider range of abilities, is a little less powerful, but nearly eliminates the need for hardware-specific code. I'm in the middle of a game now that I was concidering rewriting for OpenGL, but I think I'll continue it in DX, only because it wouldnt be all that different, and I'm already using the other aspects of DirectX (Input, sound, networking, etc) that would take too much effort to smoothly replace... but future games will be written in OGL. 

> Only thing that bothered me (in the past) was support for latest effects... in directX you don't need to write several "graphic paths" to draw some cool pixel shading effects on different hardware. BUT and big BUT... OpenGL has finally evolved to version 2.0 and has its own shading language so -> this is not the problem anymore. So my vote goes to OpenGL. 

> You can use parts of DirectX -> DirectInput, DirectSound, DirectShow (for example to play mp3 or wma as bacgroun music, get input etc.)... and OpenGL togather in the same game. I use it... however if you decide to port the game to something else than windows you will have to replace DirectX components of the game with something else. 

> I have to say that OpenGL is vastly better than DirectX (see the above posts for reasons). If you want cross-platform input, sound, etc. You can use SDL (Simple DirectMedia Layer) with OpenGL! So with OGL + SDL, you get the whole set of features in DirectX, minus the complexity and big download, but plus the simplicity, speed, portability and more! 

> Whether you choose to use OpenGL or Direct3D is mainly a matter of preference, coding style, and portability. I personally think that Direct3D is easier to use if you have a good understanding of the language you are writing in. There are also many built-in utility libraries and applications that come with the SDK that make things easier for the programmer. The disk space required for the SDK is trivial by today's standards. With that in mind, DirectX does lack the portability that is offered by OpenGL, and will only be changed and updated at Microsoft's discretion. OpenGL and DirectX can be used together, however, so you can still take advantage of DirectInput, DirectSound, etc. while using OpenGL as your rendering API. I want to stress again that it is merely a matter of preference as to which API you use, being that they are very similar in function, ease-of-use, and versatility. 

> Opengl is easier to program than directx but directx has better hardware support according to some froums i read 

> DX is nice for larger projects, since it encapsulates alomost everything related to game programming (3D, sound, music, input, networking, etc.) while OGL is only graphics. Its code is also much more organized (OOP), while OGL is more "classic". It really depends on your programming style. 

> Well, IIRC DX is at a higher level than OpenGL. But OpenGL is moving towards those type of graphics capabilities such as shaders and stuff. They already have the plan laid out, they are just releasing it in a timely fashion. Most likely because the graphics capabilites are too taxing on performance. And OpenGL can use any new feature of a graphics card anyway because OpenGL allows extensions while DX needs another release.  

> DirectX gets updated relatively frequently (compared to OpenGL). Since MS can just unilaterally decide what to add to it, they can just toss new stuff in as it becomes available (hence DirectX 9.0a/b/c over the last couple years).

OpenGL's core specs get updated infrequently, but manufacturers can add extensions to it (for instance, until OGL2.0, fragment shaders were an extension).

So in theory, features probably get exposed faster in OpenGL, but in a manufacturer-specific way that requires more work from developers to support. In practice, the feature set of the two APIs is usually almost identical.


> If you want a good cross-platform hardware abstraction, use SDL. It does anything DirectX can do, portably. (On Windows it simply maps its functions to the DX ones.)  

> Open GL games tend be more stressful on the video card. Direct X games always see mto be CPU bound by the nature of the programming. Longhorn plans to change that with DX10 

> Certainly not true in all cases. Using DX you can utilize numerous features some time before anyone has them implemented in hardware and use refrast to test them. Due to the problems the ARB has had getting 2.0 out the door there is nothing that has been comparable on the OGL side. 

> Direct3d also has an overseeing board of members like openGL. So microsoft doesnt (but could if they were stupid enough) just throw in new features whenever they want. They consult with the vid card manufactures and game makers (that sit on teh board) about what can be done. Carmack joined the direct3d board a few years ago cause he "didn't want to see stupid decisions made again that would make it slower for the future". 

[http://forums.anandtech.com/messageview.aspx?catid=31&threadid=1557123&frmKeyword=&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear](http://forums.anandtech.com/messageview.aspx?catid=31&threadid=1557123&frmKeyword=&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear)
[http://www.free2code.net/plugins/forums/view.php?f=38&p=28618&os=0](http://www.free2code.net/plugins/forums/view.php?f=38&p=28618&os=0)

After reading a bunch of these posts, it seems like maybe opengl is as good or superior to directx, so maybe it is just ignorance on developers parts? Is the SDL, simple direct media layer combined with opengl as good as the directx package?

---

### Post by AntiDragon on 2005-07-13
When I talk to people who've used both, OpenGL comes out on top. The argument that DirectX has better hardware support is mostly down to ATi and NVidia spending more effort on the DirectX portion of their drivers than the OpenGL.

OpenGL with SDL is a pretty common combo so together, they are a more attractive API. It's just at the moment they're not the most *widespread* - DirectX is.  For fear of sounding repetitive, I don't think that's much of a danger as I believe developers will have no qualms in switching once Linux marketshare increases to the point that it's profitable. Infact, they'll probably relish the chance to get they're hands dirty! Then you'd see a reverse trend where Windows games use OpenGL. And so the drivers would improve in that area too.

One barrier that currently exists is performance though. DirectX came about as a way to bypass the existing OS methods of accessing hardware to improve performance and allow extra features without interfering with the OS core.

Linux has DRI in X but (as some will say) it's a bit lacking - it's a patch to a hack to a hack to a patch (no disrespect - a lot of people have poured their hearts and souls into X. And there lunches after looking at the CVS tree.... O:) ) However this is being worked on by X.Org and it's looking very promising.  The other barrier is the drivers to support direct hardware access - NVidia do a good job but ATi is still playing catch up. Yet even these have moved on a lot from how they used to be.

So, I would agree DirectX is a barrier of sorts, but I wouldn't call it an **enemy** - OpenGL has been round far longer and looks set to stay. To be honest, the card makers hold most of the chips when it comes to 3D support as they have to make the drivers for both OSes and they decide which APIs the drivers expose.

---

### Post by poofyhairguy on 2005-07-13
If OpenGL ever slays Directx it will be because of a huge surge in the popularity of the Apple platform after the Intel shift. The crossplatform tool will look better then.

Despite the truth, Linux users have a reputation of "people who won't pay for software" while Apple fans are "people whose wallet can't stop bleeding."

If developers come to Opengl, it will be to make it easier to get the tasty Mac users. We will probably benefit from such a shift.

---

### Post by AntiDragon on 2005-07-13
[QUOTE=poofyhairguy]If OpenGL ever slays Directx it will be because of a huge surge in the popularity of the Apple platform after the Intel shift. The crossplatform tool will look better then.

Despite the truth, Linux users have a reputation of "people who won't pay for software" while Apple fans are "people whose wallet can't stop bleeding."

If developers come to Opengl, it will be to make it easier to get the tasty Mac users. We will probably benefit from such a shift.[/QUOTE]

Well the Battle For The Desktop (insert StarWars theme song here) has always been more about ideals, perceptions and knowledge that the actual technologies. Although of course, the ideals are in part driven by the technologies they promote.

Ho hum, getting all socio-political now. DirectX sparking a moral debate...Who'd a thunk it? ;-)  You know I've wasted almost half my working day on this thread - not to good since I'm supposed to be getting my MDs mail server back up and running  :grin:... Guess what it was running.....! 

Ah..[Slap]..stay on topic....

---

### Post by NoTiG on 2005-07-13
Thats a good point poofy. I guess we will find out... when longhorn comes out if the new directx will destroy any competition.  but i still think directx is a big barrier to linux.. and in the foreseable future (unless more people shift to mac, which would actually help linux) . Maybe the problem isnt that opengl + SDL isnt good enough... its that its not as widely known ? 

[http://www.libsdl.org/articles.php](http://www.libsdl.org/articles.php)

Absolutely. One of the reasons for learning C was that an API like SDL was available and so very easy to use. Before I had written games on the Amiga in languages such as AMOS and Blitz Basic. After that I had been spoilt by Java, so programming a game in C seemed very daunting. SDL convinced me otherwise. When I started making Starfighter I had begun programming the game on Windows. The ease of SDL meant that getting it up and running on Linux was simply a case of installing the libraries and running make to build the game. For Linux games development SDL and OpenGL are certainly the way to go.

---

### Post by az on 2005-07-13
[QUOTE=poofyhairguy]If OpenGL ever slays Directx it will be because of a huge surge in the popularity of the Apple platform after the Intel shift. The crossplatform tool will look better then.

Despite the truth, Linux users have a reputation of "people who won't pay for software" while Apple fans are "people whose wallet can't stop bleeding."

If developers come to Opengl, it will be to make it easier to get the tasty Mac users. We will probably benefit from such a shift.[/QUOTE]

What about games consoles?

I would not purchase a game for my PC because I do not beleive in proprietary software.  By that, I mean security and the freedom to be able to know what my computer is doing, making changes to the source...etc...  It is not because I am cheap, but the games companies do not care about my reasons.  It's just a fact that it is a lesser market.

Or is it?  Aren't many linux users the younger crowd who are into games?

I would not have that same expectation of freedom from a game I play on a games console, though.

Ironically, I think developers are already turning to free and open technologies to make games since they do not have to pay royalties for proprietary technologies.

I guess my point is:  How much better is palying a game on your PC in comparison to using a games console?  Isn't it cheaper?  I don't know.  That is why I am asking.

---

### Post by Quest-Master on 2005-07-13
This is why I've completely forgotten about computer gaming. Worries about my video card, RAM, processor speed, blah. Why fuss out over it when there's a console? :)

---

### Post by NoTiG on 2005-07-13
I think the only reason why console wins is because they sell their hardware for a loss. I mean.... if computer hardware was sold as cheap as console, then it would make more sense to use a regular computer since its upgradable and you can upgrade individual components.  

Some reasons i like using a computer more: 

For one, look at the screen. Tv's typically have very low resolutions and look real pixelated. Its not the size of the screen that counts... its the DPI. My 15.4 inch LCD monitor looks way better than my 40+ inch TV.

Next controllers... my mouse and keyboard are alot better than any console controller.

Multitasking.. some games i can do other things while playing the game at the same time, such as instant messaging...  listening to music or whatever.

and finally.. special programs for some games... FOr instance in warcraft I had a program so i could recustomize the keys on the keyboard to suit my liking. Something like that wouldnt even be possible on the console. 

What you are seeing though.. is more and more the consoles are basically computers... and if they include ports for keyboard and mouse, allow you to hook up to the internet.. they will basically replace computers (of course) since they sell their hardware so cheap. But will they let you use them as a computer since they are taking a loss on the hardware and you might not actually  buy any games?

---

### Post by poofyhairguy on 2005-07-13
[QUOTE=azz]What about games consoles?[/QUOTE]

They are very nice. When I got into Linux, one of the first things I did was buy a Gamecube so I wouldn't have to rely on my PC for games anymore.


> I guess my point is:  How much better is palying a game on your PC in comparison to using a games console?  Isn't it cheaper?  I don't know.  That is why I am asking.

It is cheaper by far in many cases, but PCs can offer a better gaming experiance (IMHO). Many games for PC (such as Half Life 2) don't really have equals on a console. Of course that goes both ways (metroid prime) but its enough on both sides to want both.

It costs more....but that means for some that you can spend more and it will be better...

---

### Post by sonny on 2005-07-13
I love playing in my PC, cuz it's faster, sounds better, and it's just better than a console, if you want a bigger screen you can do some tv-out with your video card. The only thing you need is some Linux native games, and there's a lot of them ([www.happypenguin.org](www.happypenguin.org) and [www.tuxgames.com](www.tuxgames.com)) . I think buying a console is a waste of money, cuz you get a mediocre pc, that you can only play with it, a few houndred bucks more and you get a nice pc and you can do ANYTHING you want with it (that's my personal opinion). If you can't live without gaming, idual-boot with windows (for the time), cross you're fingers (cuz I'll be crossing mine) and hope that game copanies start seeing Linux users as part of the market, and of course... if you like a game wich has Linux support BUY it, and REGISTER saying you USE Linux, that way companies will take note on that.

---

### Post by NoTiG on 2005-07-13
I Found these tidbits btw:

SDL 2.0 will be a full redesign of the SDL functionality, based on what we've learned over the past four years. The architecture design is partially done, and we'll start prototyping the design soon. As soon as there's a working framework, we'll make it publicly available for comment and contributions. This new framework has about a year or so before we anticipate it being ready for stable release

    I'm not sure how big the SDL community is, but it seems to be huge. There are 459 games listed on the SDL web page. Over 100 add on libraries. If you look at a standard install of Linux you'll find SDL because so many of the desktop tools, applications, and games require it. SDL is being used in major commercial games such as Unreal Tournament 2004.

    SDL runs on just about everything that can run a program. Versions for cell phones are being developed. There is a version for the PS2.

    SDL is big and getting bigger. SDL is over 10 years old. There are several things in SDL that reflect the realities of game development 10 years ago. The next generation of SDL is going to clean out, or at least deprecate, those features and add features that reflect the current state of hardware. We are also taking a strong look at the future and trying harder to "future proof" SDL.

    Another trend that is affecting SDL is that while it was developed for game programming it is being used as a general applications development platform and as an image processing platform. The demands of those parts of the community are pushing SDL to be a more general while still trying to maintain its game programming roots.

---

### Post by Gnobody on 2005-07-13
OpenGL is like Direct3D and SDL is like having the rest of DirectX.  Also The Windows Graphics Foundation (which will be in Longhorn) is just DirectX 10 renamed, it is not a new API.

---

### Post by MetalMusicAddict on 2005-07-13
[QUOTE=Gnobody]The Windows Graphics Foundation (which will be in Longhorn) is just DirectX 10 renamed, it is not a new API.[/QUOTE]
Do you have some info on this?

---

### Post by Curlydave on 2005-07-13
I do agree that DirectX= a problem for linux games, but not for the majority of users, who use mostly office aps. OpenGL is great, and very capable. Doom3 and all id software games are OpenGL. UT2k4 is natively coded in D3D, but it has a very functional OpenGL emulator for use in Linux and on macs. There are some minor drawbacks with this, eg no full shadows, no modeled scope in RO and red rain, but other than that it's just like running in native D3D. I just wish that more game companies would be coded for OpenGL. Half-life1 was OpenGL (with an included D3D emulator), but HL2 is D3D. Oh well.

PS: Gaming on Linux has more issues than this, such as extremely poor ATI performance (I don't care who you blame for this one, it's a major problem nonetheless. People buy a card intending to use it for Windows, they get an ATI and love it. They then discover Linux and get really frustrated. Noone told them they needed nvidia for Linux.), lack of 3D settings such as AA, AF, Vsync, and the lack of ability to minimize games.

---

### Post by gruffy-06 on 2007-09-29
DirectX is not just in games, but on the desktop!

Take Windows Vista's Aero interface for example. It renders the entire desktop using DirectX, meaning increased widespread system performance, no graphical tearing/artifacts on screen and stunning effects.

In other words, Microsoft has already won.

---

### Post by gotonpo on 2007-09-29
Games take a very long time to develop.  Even if OpenGL proved superior and everyone started their new games using it, we wouldn't see the results for years.

I believe OpenGL is catching up feature-wise, as has been quoted.. but take WoW for example.  Blizzard developed the game in OpenGL for the Mac OS.. and you can run the game in Windows using OpenGL..  but they still took the time to develop it for DirectX.  There aren't any extra features that are enabled, so why did they go this path instead of just using one API?  Is it because the performance is better under DX?

I hope the people behind OpenGL & SDL continue their aggression and I hope more game companies look up to Blizzard & id.

---

### Post by Perfect Storm on 2007-09-29
> **gruffy-06 said:**
> DirectX is not just in games, but on the desktop!

Take Windows Vista's Aero interface for example. It renders the entire desktop using DirectX, meaning increased widespread system performance, no graphical tearing/artifacts on screen and stunning effects.

In other words, Microsoft has already won.

Nonesens.

Most games are made for OpenGL. Most games are sold to consoles like Gamecube, Playstation 3.
The only console that's using  DirectX is Xbox which also can run OpenGL.

---

### Post by a12ctic on 2007-09-29
dx is crapware, it only gets pushed because the gorilla known as microsoft pushes it towards developers. Performance wise Opengl destroys DX, and pretty much every professional non-gaming 3d application uses it. DX10 will probably be the end of DX, sense most gamers are still using xp and DX10 is vista only. Sure, devs wont get their ms bribes, but to sell cutting edge games to the largest market possible, they will have to use opengl.

---

### Post by Polygon on 2007-09-29
> **gruffy-06 said:**
> DirectX is not just in games, but on the desktop!

Take Windows Vista's Aero interface for example. It renders the entire desktop using DirectX, meaning increased widespread system performance, no graphical tearing/artifacts on screen and stunning effects.

In other words, Microsoft has already won.

windows used directx on the actual desktop long before vista. Every time you type on the keyboard.... directinput. Every time you listen and watch a youtube video, directsound /directdraw. It only recently added direct3d to the mix.

---

