---
title: "AIGLX vs. XGL. Eye candy wars in the making?"
date: 2006-02-20
forum: The Cafe
---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
Now with XGL recently released and even available on dapper now (and it rocks btw.) you thought the future of X was settled?

Think again.
Redhat has apparently been working on something similar within the existing xorg structure, contrary to Novell which developed XGL inhouse, and seems to be not all that pleased about XGL.
[http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx) 

So, does that mean we'll have competiotion (good), or does that mean we'll get unnecessary fragmentation (bad)?
Interesting times for desktop linux indeed.

---

### Post by pccampos on 2006-02-20
I will go with the one wich will work first on my i915 card. It's good to be using a distro that leaves the choice to me!

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=pccampos]I will go with the one wich will work first on my i915 card. It's good to be using a distro that leaves the choice to me![/QUOTE]
Then you have a problem.
AFAIK xgl should work on your card and according to redhat, their new bling should also work on it. :D 

I'll admit it though, one can have worse problems. ;)

---

### Post by GeneralZod on 2006-02-20
Just when I thought I was confused enough about Linux graphics, this comes along to prove me wrong :)

---

### Post by Stormy Eyes on 2006-02-20
[quote="Red Hat"]Known to not work

nvidia, ati radeon >= 9500, ati mach64, 3dfx voodoo 1 and 2, anything without a free 3d driver. Some of these should work in the future (such as the r300 cards), but the nv driver will never work. [/quote]

Well, since Xgl supports my nVidia gear, I'll be using that when it's finally stable.

---

### Post by Iandefor on 2006-02-20
Hmm. AIGLX seems to have some interesting things going for it.

---

### Post by mstlyevil on 2006-02-20
The more the merrier. May the best one win.

---

### Post by Sirin on 2006-02-20
Which one will Ubuntu use? Since AIGLX works on Metacity, which Ubuntu uses currently, it might not take that much tweaking. :)

---

### Post by bonzodog on 2006-02-20
heh..metacity has it's own compositing engine as well, which is being introduced in gnome 2.14. so, it's your choice...metacity with it's own engine, xcompmgr, xgl, or aiglx! It's your choice. Also, xubuntu now comes with it's own compositing engine.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=bonzodog]heh..metacity has it's own compositing engine as well, which is being introduced in gnome 2.14. so, it's your choice...metacity with it's own engine, xcompmgr, xgl, or aiglx! It's your choice. Also, xubuntu now comes with it's own compositing engine.[/QUOTE]
I might be wrong (I often am), but I don't think it's really about the compositing engine, but about the underlying architecture.
Case in point, the redhad solution also uses metacity with a compositor and they state that at least in theory compiz should also work on their server.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]Now with XGL recently released and even available on dapper now (and it rocks btw.) you thought the future of X was settled?

Think again.
Redhat has apparently been working on something similar within the existing xorg structure, contrary to Novell which developed XGL inhouse, and seems to be not all that pleased about XGL.
[http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx) 

So, does that mean we'll have competiotion (good), or does that mean we'll get unnecessary fragmentation (bad)?
Interesting times for desktop linux indeed.[/QUOTE]


Redhat has been working on OpenGL compositors on regular X since the Luminocity days. Its no surprise that they see that as the future. Its more of a transitional way to approach compositing where huge upgrades to the Xserver like XGL are not needed.

But honestly what Redhat is developing can't really hold a candle to the XGL work so far. Maybe if they would have released this stuff a year ago or something like that then it would have a head start that would have made it so both would have competed fairly. Its not a fair fight anymore.

Look for yourself. There are videos on that page of their new Metacity effects. In 2005 that stuff would have been amazing. In the post Compiz world its quant.

I installed their distro just to try out the Metacity compositor (I had a r200 for a week) and I have to say its neat but not AMAZING like Compiz and XGL are.

I mean....Red Hat makes most of their money in the server market...who really expects the next great Xserver eye candy to come from that direction? From the start they are moving with careful steps, while Novell with XGL just said "here is everything, prune off what you want." I see no plans in any of Redhat's mailing lists for things like Compiz's Expose pluggin, or alt-tab pluggin, or the cube flip. Plus I see many issues with video players that XGL doesn't have.

One thing Redhat IS better at than Novell is open source politics. They have done everything they can to convince those traditionalists in the community that their way is better:

1. They pick on Novell for keeping the code closed for so long (even though in that period one guy did about twice as much in the field as Redhat can even dream to do this year).

2. They made it work with Open Source drivers first so that big wigs that refuse to use closed drivers get what they want.

3. They are taking baby steps to ensure that they don't shock anyone. I'm sure more than one developer tried Compiz and said "this goes to far." They are playing into that.

4. They are bringing Metacity with them so that they can have some sort of Gnome legitimacy.

But make no bones about it, at this point XGL + Compiz is FAR ahead. Far far ahead. I mean, it true that Redhat's path CAN catch up. It would be ignorant to say that it couldn't. The problem is that I personally (along with many others) are sick of promises that Metacity and Gnome will catch up someday in the future. They hane to compete with David's work as it is today- which is far beyond what they have done. If Redhat DOES use their influence to force Gnome down this path rather than the path of XGL it won't be that bad though. 

Why?

KDE. The people who wanted the XGL code opened were KDE developers. They want to use this framework for KDE. So if Gnome is forced by Redhat down the more primative path, then KDE will blow it away to the point that other Gnome based distros might mutiny against Redhat's leadership. Actually thats just me being hopeful. What will probablu happen is the trend for the last few years-  Metacity will remain the most boring window manager.

Which is fine....I will personally replace it with Compiz from now until KDE 4.  Soeren Sandmann from Redhat says it himself:

> 
The big benefit I see to extending metacity is that it is an incremental improvement. There has been tons of work put into metacity to make it usable, handle broken legacy application and integrate well with GNOME. Extending metacity makes use of that work.

Any success it has is because of the conservatism of major Linux Desktop developers (it changes less to get you less).

One funny thing is that it seems that Nvidia prefers the Redhat way. Its not too much of a surprise- they have already spent a lot of time working on this direction. If Novell's way is made to rule the years of advantages that they have built up over ATI on the Linux Desktop could be gone. Of course what they don't know is that David's work has fixed many problems that they never could fix with their own drivers such as making videos a part of the composite act. Plus XGL's lack of the composite extension gets rid of all the problems with OpenGL and composite. They would prefer that what they have worked on before is not wasted, but they will go the direction the market goes.

In the end it is good that they are competing since Redhat and Novell are some of the biggest players in the market. I think that this summer will show what technology will win- if plenty of people switch to Novell's Linux just to get the eye candy then the meritocracy called Linuxland will decide the direction to be taken. If interest in Compiz dies off by then Redhat has a shot to pull ahead. 

Either way, this is an interesting year.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=poofyhairguy]Redhat has been working on OpenGL compositors on regular X since the Luminocity days. Its no surprise that they see that as the future. Its more of a transitional way to approach compositing where huge upgrades to the Xserver like XGL are not needed.
[/quote]
Redhat and some X hackers seem to disagree on this. At least they claim that it's far from certain that XGL is the better, more sustainable apporach.

[QUOTE=poofyhairguy]
But honestly what Redhat is developing can't really hold a candle to the XGL work so far. Maybe if they would have released this stuff a year ago or something like that then it would have a head start that would have made it so both would have competed fairly. Its not a fair fight anymore.

Look for yourself. There are videos on that page of their new Metacity effects. In 2005 that stuff would have been amazing. In the post Compiz world its quant.
[/quote]
Ah, I think you are making the mistake of equating the compositor effects with the underlying technology. As the redhat site states, they focused on the underlying technology and not on the effects. And they also state that the same stuff that is possible with XGL should be possible with their server. They even claim that compiz should run on it and after all compiz is what gives XGL these great effects.

[QUOTE=poofyhairguy]
I installed their distro just to try out the Metacity compositor (I had a r200 for a week) and I have to say its neat but not AMAZING like Compiz and XGL are.

I mean....Red Hat makes most of their money in the server market...who really expects the next great Xserver eye candy to come from that direction? From the start they are moving with careful steps, while Novell with XGL just said "here is everything, prune off what you want." I see no plans in any of Redhat's mailing lists for things like Compiz's Expose pluggin, or alt-tab pluggin, or the cube flip. Plus I see many issues with video players that XGL doesn't have.
[/quote]
Again, that's compiz, not the underlying technology.

[QUOTE=poofyhairguy]
One thing Redhat IS better at than Novell is open source politics. They have done everything they can to convince those traditionalists in the community that their way is better:
[/quote]
Seeing how many people in the open source community hate redhat, I really doubt they are great at this.

[QUOTE=poofyhairguy]
1. They pick on Novell for keeping the code closed for so long (even though in that period one guy did about twice as much in the field as Redhat can even dream to do this year).
[/quote]
How do you know? Did you compare the two code bases?

[QUOTE=poofyhairguy]
2. They made it work with Open Source drivers first so that big wigs that refuse to use closed drivers get what they want.
[/quote]
Hm, there might also have been a very simple pragmatic reason. They can change and improve the open source drivers to provide what they need, they can't do this with the closed source ones. No need for conspiracy theories here I think.

[QUOTE=poofyhairguy]
3. They are taking baby steps to ensure that they don't shock anyone. I'm sure more than one developer tried Compiz and said "this goes to far." They are playing into that.
[/quote]
Did you even read the link? This isn't about the effects in compiz. I can only repeat it, they even explicitly state they love compiz and that it should work on their X server.

[QUOTE=poofyhairguy]
4. They are bringing Metacity with them so that they can have some sort of Gnome legitimacy.
[/quote]
Again, no need for conspiracy theories. Maybe not throwing all the old code away could make sense from a simply pragmatic point of view?

[QUOTE=poofyhairguy]
But make no bones about it, at this point XGL + Compiz is FAR ahead. Far far ahead. I mean, it true that Redhat's path CAN catch up. It would be ignorant to say that it couldn't. The problem is that I personally (along with many others) are sick of promises that Metacity and Gnome will catch up someday in the future. They hane to compete with David's work as it is today- which is far beyond what they have done. If Redhat DOES use their influence to force Gnome down this path rather than the path of XGL it won't be that bad though.[/quote]
See above. You are making your judgments not on the technology, but on the nice compiz effects, which is something really different. And again, according to redhat compiz and all the effect should work on their server two, so your point is mute, imho.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]Redhat and some X hackers seem to disagree on this. At least they claim that it's far from certain that XGL is the better, more sustainable apporach.[/QUOTE]

Of course they would say that. They have their own horse to bet on.

> 
Ah, I think you are making the mistake of equating the compositor effects with the underlying technology. As the redhat site states, they focused on the underlying technology and not on the effects. And they also state that the same stuff that is possible with XGL should be possible with their server. They even claim that compiz should run on it and after all compiz is what gives XGL these great effects.

Again, that's compiz, not the underlying technology.


My point was that Redhat is making promises- "our framework will do everything Novell's will" - while Novell is showing a near final project. David worked a lot on the underlying technology of XGL to get it to the point its at. Mid last year XGL was about as half as done as it is today.

I'm not confusing the two. What I am saying is that Redhat is at step 3 (we have built the framework and Metacity has basic effects) while Novell is at step 12 (we have built the framework, built a compositor to do it, AND built in effects to show what this framework can do).

I will take the working XGL + Compiz on my desktop anyday over the promises of Redhat.

> 
Hm, there might also have been a very simple pragmatic reason. They can change and improve the open source drivers to provide what they need, they can't do this with the closed source ones. No need for conspiracy theories here I think.

Again not my point. My point is that neither technology can move forward without support from ATI and Nvidia. Redhat is at the step of getting to work with open drivers (which means no modern hardware) while Novell has already gotten promises from Nvidia (not surprising) and ATI (very surprising) to support their framework.

It was yet another example to prove that Redhat is behind.

> 
Did you even read the link? This isn't about the effects in compiz. I can only repeat it, they even explicitly state they love compiz and that it should work on their X server.

My point was that Novell is to the point that they are actually creating new and innovative ways to use what they have built, while Redhat is mostly talking about the future.

Sure Compiz ONE DAY can maybe run on Redhat's project. And if its better than one day Redhat's framework should be used to some extent. 

But today is a day when Redhat WANTS to compare what its done to the Novell work, and any observer would say that the Redhat people are FAR behind. Untill Redhat's framework solves its many problems that Novell's route does not have (problems with drivers, video, or the fact that only Fedora has this stuff) then they are behind. Its that simple.

> 
Again, no need for conspiracy theories. Maybe not throwing all the old code away could make sense from a simply pragmatic point of view?

No code is thrown away with XGL. Its extends the xserver in ways it lacks. The Xegl project plans to throw away the Xserver code, but that is a dead end so far.

> 
See above. You are making your judgments not on the technology, but on the nice compiz effects, which is something really different. And again, according to redhat compiz and all the effect should work on their server two, so your point is mute, imho.

My point is not mute. Here it is in a nutshell:

Redhat- SAYS that what amazing effects Compiz provides COULD be done with their framework. Says that the big problems with its framework today (video playing, drivers) COULD be fixed.

Novell- SHOWS what amazing effects Compiz+ XGL DOES provide today with their framework. Has SHOWN that some of the biggest problems with composite in teh past (video playing, lack of being able to use the closed source ATI driver, etc) their framework can fix. 

Its the difference between a possibility and a certainty. When Redhat actually SHOWS what their framework can do AT THE LEVEL of what Novell has SHOWN then I will sing a different tune. Till then Novell is pioneering the future of X while Redhat is making promises.

---

### Post by r_a_trip on 2006-02-20
*They made it work with Open Source drivers first so that big wigs that refuse to use closed drivers get what they want.*

Which is what anybody should want. Closed source is all good and well, but it is mutually exclusive of Free Software. There is no "hybrid" system. As soon as a piece of proprieatary software enters your system it is closed. You can't ship your setup as is with it included without violating copyright.

When it is just a user space app, the damage that can be done, is relatively small. If a vendor cuts you off from using the current or a newer version, you can ultimately seek a replacement (preferably a Free one).

If proprietary software is becoming part of the core infrastructure of Free Software, it means the integrity of Free Software in general is compromised. If GNU/Linux is only able to run on proprietary hardware through proprietary drivers (read absolutely no usable Free drivers exist), the single reason for having a Free system in the first place is destroyed. You again are beholden to interests that may, but most possibly don't coincide what YOU need from computing.

The reason we have GNU/Linux now is because we "big wigs" (and not so big wigs) "refuse to use closed drivers" and only reluctantly accept the existance of proprietary software. If we hadn't adopted a strong Free Software ethos, we would have sold out Free Software long ago and you would be stuck with the choice between proprietary software and proprietary software.

I for one support the reasoning behind aiglx. It enables to have reasonable graphical improvements without having to sacrifice indepence from proprietary software. It keeps your options open and doesn't force you to rely on proprietary NVidia or ATI support to even have a shot at improvements.

I know that Ubuntu is becoming the safe haven for Windows expatriots. Which is great. Being Free from coercion and crappy software is bliss (I can rembember the feeling from switching fulltime five and a half years ago.) I just want to make sure that you don't unwittingly sacrifice your new won Freedom in exchange for some short term gains, which will lock you up into the proprietary treadmill once again. (OTOH, if you willingly sell your Freedom to get some nice to have eyecandy, you deserve your own enslavement).

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=poofyhairguy]Of course they would say that. They have their own horse to bet on.
[/quote]
And this assumption is all you base your very clear opinion on? Come on, tell me that's not true.

[QUOTE=poofyhairguy]
My point was that Redhat is making promises- "our framework will do everything Novell's will" - while Novell is showing a near final project. David worked a lot on the underlying technology of XGL to get it to the point its at. Mid last year XGL was about as half as done as it is today.
[/quote]
But that's not true. The only differnce you can see and the only thing you seem to base your judgment on is that compiz has better eye candy than the metacity redhat provides. While this is true this doesn't mean that Redhat is just making promises, after all, they released the X server and it does in no way answer which technology is better or what the advantages/disatvantages of one technology compred to the other are.

[QUOTE=poofyhairguy]
I'm not confusing the two. What I am saying is that Redhat is at step one (we have built the framework) while Novell is at step 12 (we have built the framework, built a compositor to do it, AND built in effects to show what this framework can do).
[/quote]
Nope, you were clearly confusing the two and you clearly didn't read the article. However, you still aren't able to admit a mistake.
And though I'm far from being an expert, it should be pretty obvious to anyone that the underlying technology is the hard part, what you label step 12 is just the icing on the cake.

[QUOTE=poofyhairguy]
I will take the working XGL + Compiz on my desktop anyday over the promises of Redhat.
[/quote]
Me too. I'm really impressed with XGL + Compiz, but then again, that besides the point.

[QUOTE=poofyhairguy]
Again not my point. My point is that neither technology can move forward without support from ATI and Nvidia. Redhat is at the step of getting to work with open drivers (which means no modern hardware) while Novell has already gotten promises from Nvidia (not surprising) and ATI (very surprising) to support their framework.

It was yet another example to prove that Redhat is behind.
[/quote]
Again, you shouldn't go around changing your points.
Clearly
> They made it work with Open Source drivers first so that big wigs that refuse to use closed drivers get what they want.is a far cry from what you claim to be your point now.
Be that as it may, Nvidia and Ati are working on supporting GLX_EXT_texture_from_pixmap which is needed for both XGL and AIGLX, so your other point about Redhat behing behind is also mute.

[QUOTE=poofyhairguy]
My point was that Novell is to the point that they are actually creating new and innovative ways to use what they have built, while Redhat is mostly talking about the future.
[/quote]
Again, this wasn't your point, but I'll refrain from quoting your original post as this is just getting silly. And again, AIGLX is there, it's not a promise, you can use it now, you can inspect the code now. The only difference is that there isn't a composite manager for it yet that is as impressive as compiz, which again, says nothing at all about the actual technology.

[QUOTE=poofyhairguy]
But today is a day when Redhat WANTS to compare what its done to the Novell work, and any observer would say that the Redhat people are FAR behind. Untill Redhat's framework solves its many problems that Novell's route does not have (problems with drivers, video, or the fact that only Fedora has this stuff) then they are behind. Its that simple.
[/quote]
Nope, only an observer who is unable to differentiate between the underlying technology and the icing on the cake would say that.

[QUOTE=poofyhairguy]
No code is thrown away with XGL. Its extends the xserver in ways it lacks. The Xegl project plans to throw away the Xserver code, but that is a dead end so far.[/quote]
Arghhhhhh.
I was answering to you talking about metacity. Clearly, metacity is not, I repeat not an X server, but a window manager and I was pointing out that not throwing away all the window manager code to create a new window manager with an integrated compositor but instead use and extend the current one might be a pragmatic decision. Jesus....

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=r_a_trip]*They made it work with Open Source drivers first so that big wigs that refuse to use closed drivers get what they want.*

Which is what anybody should want. Closed source is all good and well, but it is mutually exclusive of Free Software. There is no "hybrid" system. As soon as a piece of proprieatary software enters your system it is closed. You can't ship your setup as is with it included without violating copyright.

When it is just a user space app, the damage that can be done, is relatively small. If a vendor cuts you off from using the current or a newer version, you can ultimately seek a replacement (preferably a Free one).

If proprietary software is becoming part of the core infrastructure of Free Software, it means the integrity of Free Software in general is compromised. If GNU/Linux is only able to run on proprietary hardware through proprietary drivers (read absolutely no usable Free drivers exist), the single reason for having a Free system in the first place is destroyed. You again are beholden to interests that may, but most possibly don't coincide what YOU need from computing.

The reason we have GNU/Linux now is because we "big wigs" (and not so big wigs) "refuse to use closed drivers" and only reluctantly accept the existance of proprietary software. If we hadn't adopted a strong Free Software ethos, we would have sold out Free Software long ago and you would be stuck with the choice between proprietary software and proprietary software.

I for one support the reasoning behind aiglx. It enables to have reasonable graphical improvements without having to sacrifice indepence from proprietary software. It keeps your options open and doesn't force you to rely on proprietary NVidia or ATI support to even have a shot at improvements.

I know that Ubuntu is becoming the safe haven for Windows expatriots. Which is great. Being Free from coercion and crappy software is bliss (I can rembember the feeling from switching fulltime five and a half years ago.) I just want to make sure that you don't unwittingly sacrifice your new won Freedom in exchange for some short term gains, which will lock you up into the proprietary treadmill once again. (OTOH, if you willingly sell your Freedom to get some nice to have eyecandy, you deserve your own enslavement).[/QUOTE]

Three things:

1. Work being done on open source drivers right now will make it so that all the traditional open drivers (Intell, R200, Etc.) will work with XGL + Compiz. Some on the forum have already gotten this to work more. Compiz CAN use the open source drivers.

2. NO MODERN HARDWARE RELEASED HAS OPEN SOURCE DRIVERS. The most powerful hardware with open source drivers is the newer Intel chipsets. Yes, those integrated chipsets which represent the very bottom of the performance charts in Windowsland. You might be fine never advancing beyond what this card can do and make it so that the only way to get such effects in this card, but you don't speak for everyone.

3. Its not just Ubuntuland that is being overrun with Windows refugees that don't care about staying primative for ideals. Most of the marketshare gain by the Linux desktop in the last year almost ALL come from this demographic. So in the future those who care about the Libre philosophy will be in the minority in the Linux community (if that is not already the case). If you (and those like you) want to wreck the car before this new generation gets a chance at the wheel then be my guest. Just don't expect us to thank you for it.

4. All of the work done does not threaten a libre desktop. If you want only open drivers, the YOU don't get to use the effects (unless you have one of the few cards that are powerful enough with open source drivers). But all this stuff does not take away anything from you. It gives something of value to a person like myself that does not see the world in such a black and white way.
> 
There is no "hybrid" system. As soon as a piece of proprieatary software enters your system it is closed. 

I believe this is false. I believe a Linux install with a few closed drivers IS better than a full closed system. But it does not matter, the masses migrating to Linux will decide the future. And my guess is that you absolutist stance will find you to be a minority soon.

> 
(OTOH, if you willingly sell your Freedom to get some nice to have eyecandy, you deserve your own enslavement).

I did. I bought a Nvidia card last year JUST for its closed source drivers. Why? Because they are far ahead of everything other driver in Linuxland.

If this is prison, it sure it pretty.

---

### Post by poofyhairguy on 2006-02-20
***Disclaimer- I could be wrong****

[QUOTE=SuperDiscoMachine V.5.7-3]And this assumption is all you base your very clear opinion on? Come on, tell me that's not true.[/QUOTE]

No. That was a cheap shot by me, I admit it. Redhat has many smart people working for it.

> 
But that's not true. The only differnce you can see and the only thing you seem to base your judgment on is that compiz has better eye candy than the metacity redhat provides. While this is true this doesn't mean that Redhat is just making promises, after all, they released the X server and it does in no way answer which technology is better or what the advantages/disatvantages of one technology compred to the other are..

I am more concerned with the fact that Redhat's solution brings back old composite problems (such as video playing and ATI drivers) that the XGL +Compiz solution got rid of. The compiz effects are more an example that Novell considers their work to almost be done.

> 
Nope, you were clearly confusing the two and you clearly didn't read the article. However, you still aren't able to admit a mistake.
And though I'm far from being an expert, it should be pretty obvious to anyone that the underlying technology is the hard part, what you label step 12 is just the icing on the cake..

Exactly. Step 12 is near the end. David only got to work on the Compiz effects because his work on the XGL is almost done. I can tell you from experiance- in the past week it is more stable than any other composite solution I have used.

>  The only difference is that there isn't a composite manager for it yet that is as impressive as compiz, which again, says nothing at all about the actual technology..

No. The difference is that ATI driver (which never did anything composite wise) work great with XGL while the wiki page says it doesn't for Redhat's solution. Also Redhat's solution has problems with video playing like every other compositor in existence not called Compiz.

I am arguing that the Novell framework is ahead. Sure I haven't looked at the code to see, but I do recognize old problems with composite when I see them and Redhat's framework suffers from every major one from the past.

The video problem alone is so bad I never though the composite extension would be turned on in a major distro. Novell's solution fixed that. Until Redhat's way can at least fix the same problems that XGL+ Compiz does that there is no way its comparible at this point.

The Compiz effects are Novell's proof that it works. "We have gotten so far that we are now working on icing." Redhat is still baking cake.

> 
Arghhhhhh.
I was answering to you talking about metacity. Clearly, metacity is not, I repeat not an X server, but a window manager and I was pointing out that not throwing away all the window manager code to create a new window manager with an integrated compositor but instead use and extend the current one might be a pragmatic decision. Jesus....

Fine. Good point. I will admit that I was wrong there. Metacity should not be thrown away.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=poofyhairguy]
I am more concerned with the fact that Redhat's solution brings back old composite problems (such as video playing and ATI drivers) that the XGL +Compiz solution got rid of. The compiz effects are more an example that Novell considers their work to almost be done.
[/quote]
Ehm, many people are still having problem with video playback and XGL, especiall when using xv.

[QUOTE=poofyhairguy]
Exactly. Step 12 is near the end. David only got to work on the Compiz effects because his work on the XGL is almost done. I can tell you from experiance- in the past week it is more stable than any other composite solution I have used.
[/quote]
Don't twist my words, young man.
If anything redhat is at step 11, not at step 1. That is, they've got the hard part, the underlying technology, and what's missing is the icing on the cake.
And don't worry, I know how great and stable XGL and compiz are, I'm using them myself and I'm really impressed.

[QUOTE=poofyhairguy]
No. The difference is that ATI driver (which never did anything composite wise) work great with XGL while the wiki page says it doesn't for Redhat's solution. Also Redhat's solution has problems with video playing like every other compositor in existence not called Compiz.
[/quote]
About video, see above.
About ATI. AFAIK XGL works, because the missing things are implemented in software, that is mesa, something that would probably also work for AIGLX I think. And of course this still doesn't answer the question which technology is "better", which design is more promising, etc.
[QUOTE=poofyhairguy]
I am arguing that the Novell framework is ahead. Sure I haven't looked at the code to see, but I do recognize old problems with composite when I see them and Redhat's framework suffers from every major one from the past.
[/quote]
But you seem to be quite selective when it comes to recognizing problems.

[QUOTE=poofyhairguy]
The Compiz effects are Novell's proof that it works. "We have gotten so far that we are now working on icing." Redhat is still baking cake.
[/quote]
Nah, that's what you like to think, but maybe NOVELL just wanted something impressive to show of at the recent X confernce and so put a lot of effort into compiz. And again, all you do is judging the underlying framework from looking at the icing on the cake and I don't think that's really convincing.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]Ehm, many people are still having problem with video playback and XGL, especiall when using xv.[/QUOTE]

Most of the time this is because the people have not chosen the correct backend in the media player for the card they are using.

But sure, you are right. Compiz is not perfect yet. I just know composite problems all too well and significant ones are gone with Novell's solution as soon as the drivers catch up.

The Redhat solution gave me video playing problems on a r200- the card it was designed to work on! I had a few artifacts and using the Opengl backend on Gxine gave me an outright crash!

> 
Don't twist my words, young man.

Sorry.

> 
If anything redhat is at step 11, not at step 1. That is, they've got the hard part, the underlying technology, and what's missing is the icing on the cake.

I guess neither of us really know what step Novell or Redhat are at, so I will admit defeat here just to now have to argue the point further.

I will say that personally until I see Redhat's framework work as well with ATI cards (with the official ATI drivers) as XGL + Compiz current do then I refuse to believe Redhat is ahead.....

> 
About video, see above.
About ATI. AFAIK XGL works, because the missing things are implemented in software, that is mesa, something that would probably also work for AIGLX I think. And of course this still doesn't answer the question which technology is "better", which design is more promising, etc.

Personally I think "better" is what gets this stuff into major distros as the default the fastest. Novell's work seems farther ahead on that point because it has less HUGE problems.

Other people might have far different definitions.

> 
But you seem to be quite selective when it comes to recognizing problems.

I will admit to that. I dislike the problems that make it so that two years after the composite extension was made no major distro uses it by default. That includes video playing and ATI drivers.

> 
Nah, that's what you like to think, but maybe NOVELL just wanted something impressive to show of at the recent X confernce and so put a lot of effort into compiz. And again, all you do is judging the underlying framework from looking at the icing on the cake and I don't think that's really convincing.

I judge this on the fact that XGL is about twice as stable as I thought it to be at this point. It has NO composite artifacts that I have found (even OSX still has those) and no major Xserver crashes if its set up in the correct way. 

I'll be honest. I am biased. As soon as I saw XGL + Compiz working well enough (better than anything before it) on a modern ATI card I was sold. I would like to stop making guides to tell people how to use this stuff- I'd prefer it to be hte default.

Any solution that has us going backwards on key areas should not be considered at this point. If I read the Redhat wiki that these problems have been fixed I will try it again and push for it. Til then.....

---

### Post by r_a_trip on 2006-02-20
*2. NO MODERN HARDWARE RELEASED HAS OPEN SOURCE DRIVERS. The most powerful hardware with open source drivers is the newer Intel chipsets. Yes, those integrated chipsets which represent the very bottom of the performance charts in Windowsland. You might be fine never advancing beyond what this card can do and make it so that the only way to get such effects in this card, but you don't speak for everyone.*

True, I don't speak for everybody when I defend the Freedom in Free Software. Then again, those who are along for the _free ride_ in Free Software, will leave it behind as soon as they perceive the golden cage of proprietary software to offer more instant gratification. That is fine. Everybody is Free to choose Freedom over enslavement, but real Freedom also means that people should be allowed to choose enslavement over Freedom.

I'm just on the guard to counter every attempt from the "freeloaders" to decide fundamental policy. Freeloaders (those that don't care for the Free Software philosophy) are the enemy within. They have the potential to destroy in a few years, what decades of sacrifices in convenience has made possible within the Free Software movement. My stance is "No voting without a pledge of allegiance to the cause".

Besides, everybody will reach a point in their personal development where they will realise that **My graphics card is bigger than yours!** does not encompass all the rich experiences life has to offer.

*If you (and those like you) want to wreck the car before this new generation gets a chance at the wheel then be my guest. Just don't expect us to thank you for it.*

I'd rather wreck the car myself, than let a recalcitrant snotnose without respect for a Free Software license wreck it for me. Your goals are better served with Windows. Just get a job and pay for convenience. We pay with a little inconvenience for Freedom. If Windows refugees become a pest, we, the believers in Freedom, will leave you behind with a proprietary infested system and move on to the next Free System. (We might get the bug spray out and exterminate the infestation though.) You need the commie, pinko, Free Software wacko's more, than we need you. Mark's billions can't buy idealism, which Mark seems to understand, but you don't.

*It gives something of value to a person like myself that does not see the world in such a black and white way.*

A little pregnant. A little dead. A little enslaved. If all of us seem to accept closed drivers there is absoluty no hope of having an Open Hardware industry. That means that obsolescense is built in. Vendor X stops driver development and forces you to buy new gadget Z while your year old gadget Y is still perfectly functioning, but doesn't run on the latest Free kernel, because the driver module doesn't load anymore. 

*Keep using the old kernel. Stable driver APi's yadda, yadda, yadda.* Horse Shit! Just stopping kernel advancement to accomodate proprietary, maximum profit interests is braindead. Most of you are not even considering trailing edge hardware, why should we (or you) consider staying frozen at a particular kernel version? Fully Free Software drivers solve this "proprietary software consumer strong-arming" problem. Voting with your wallet and making this known by being vocal makes changes happen. Kissing Novells butt, because they threw a shiney bone, won't.

*If this is prison, it sure it pretty.*

"The greatest enemy of Freedom is a happy slave."

---

### Post by Virogenesis on 2006-02-20
r_a_trip hate to say it but you're the biggest elitest I've ever come across.
Free software and closed software can live together. 
We **_NEED_** good graphics cards and those cheap cards can not provide that.
Whats the point in having a computer without a cpu?
Without the nvidia drivers I'm sure blender wouldn't be such a success.
Novell have done some great work and if it wasn't for novell's actions in the past we might of seen SCO actually do some damage to Linux.

I'm actually surpised redhat did this as they could be spending their time working on xegl as that is what we need.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=r_a_trip]
True, I don't speak for everybody when I defend the Freedom in Free Software. Then again, those who are along for the _free ride_ in Free Software, will leave it behind as soon as they perceive the golden cage of proprietary software to offer more instant gratification. That is fine. Everybody is Free to choose Freedom over enslavement, but real Freedom also means that people should be allowed to choose enslavement over Freedom.[/QUOTE]

Hint: calling people slaves for having a few closed source drivers is a funny statement in a world where REAL slavery exists.

> 
I'm just on the guard to counter every attempt from the "freeloaders" to decide fundamental policy. Freeloaders (those that don't care for the Free Software philosophy) are the enemy within. They have the potential to destroy in a few years, what decades of sacrifices in convenience has made possible within the Free Software movement. My stance is "No voting without a pledge of allegiance to the cause".

And once the Intel cards work well then you have your open source option. Would you stand in MY way of having a choice to go along a path that is more grey?

Then watch as your kind DOES LOSE Linux to those with more moderate positions.

> 
Besides, everybody will reach a point in their personal development where they will realise that **My graphics card is bigger than yours!** does not encompass all the rich experiences life has to offer.

Thats a great way to look at it- it just doesn't matter. Maybe not to you, this is my itch.

> 
I'd rather wreck the car myself, than let a recalcitrant snotnose without respect for a Free Software license wreck it for me. Your goals are better served with Windows. Just get a job and pay for convenience. We pay with a little inconvenience for Freedom. If Windows refugees become a pest, we, the believers in Freedom, will leave you behind with a proprietary infested system and move on to the next Free System. (We might get the bug spray out and exterminate the infestation though.) You need the commie, pinko, Free Software wacko's more, than we need you. 

Wow. First time on this forum after over a year here I was told to use Windows.

I prefer the Linux operating system over all others for many reasons. Should I not be allowed to speak because "protecting the ideals of free software" is not my top priority?

Sorry mate. Ubuntu is Linux for Humand Beings. That means it includes all of us who don't have such a black and white view of software. I belong here just as much as you do.....

> 
Mark's billions can't buy idealism, which Mark seems to understand, but you don't.


Mark's Linux loads the Madwifi drivers when it installed to get my wireless to work. Ubuntu was created because Mark understood that a black and white view of libre OSes (like Debian has) is not the best way to get on the desktop. So his distro loads closed source things off the bat. Should he be run out on a rail as well?

> 
A little pregnant. A little dead. A little enslaved. If all of us seem to accept closed drivers there is absoluty no hope of having an Open Hardware industry.   

Trust me, the fact that the movement could not find funding is the reason that the Open Graphics Project is pretty much dead. Because guess who has the money to make things like that? Companies that dislike your black and white viewpoint.

> 
That means that obsolescense is built in. Vendor X stops driver development and forces you to buy new gadget Z while your year old gadget Y is still perfectly functioning, but doesn't run on the latest Free kernel, because the driver module doesn't load anymore. 

Then I will buy a new one. Who cares, its just a graphics card! 

If the person who created the drivers for my ATI 9250 doesn't update the driver to work with XGL then I'm in the same boat as if Nvidia did not do it. I can not hack on drivers. The thousands of new migrants to Linux also can't hack new drivers.

Trust me, I went down your path. I tried to support only graphics hardware that had open source drivers. Thats why I got a 9250. But then I found something out- my open source masters are no better than my former closed source ones. RMS and yourself might be able to hack drivers but I can't and neither can millions of other Linux users. We are just as dependent on the makers of the open source graphics cards as closed source ones.

If a graphics driver lacks a feature then it does not matter how Free it is- I am screwed either way out of that feature. Sure you say "but you can hire someone to do it for you." I looked into that. For the feature I wanted I could find no one willing to allow me to pay them to add it to the R200 driver. To most of the world, the Libre approach is fine when it works, and just as bad as the closed source route when it doesn't.

> Horse Shit! Just stopping kernel advancement to accomodate proprietary, maximum profit interests is braindead. Most of you are not even considering trailing edge hardware, why should we (or you) consider staying frozen at a particular kernel version? Fully Free Software drivers solve this "proprietary software consumer strong-arming" problem. Voting with your wallet and making this known by being vocal makes changes happen. Kissing Novells butt, because they threw a shiney bone, won't.

Yes, because your sort of zealot has done very well with convincing ATI and Nvidia to open source their drivers. Oh wait. That didn't happen.

Each of us should be allowed to chose how much freedom we have. If we chose a little bit or none then that is for good reason.

> 
"The greatest enemy of Freedom is a happy slave."

The greatest enemy to any cause is extremists that give the cause a bad name. Mark understands the point of compromise. Many of us do. If you don't then fine: use the old ATI cards and all the old hardware that has open source drivers. I will not stop you. Neither will XGL.

But if you try to stop me, expect me to spend more money on my gilded cage. It has served me better than the one with the door open!

---

### Post by poofyhairguy on 2006-02-20
The final say:

> Some people have characterized this as “Red Hat vs. Novell.”  This is the wrong way to frame this.   True, Dave at Novell is the one who is largely responsible for the XGL work and the X hackers at Red Hat are some of the primary authors of the aiglx work.  However, there’s been a huge number of external contributions to the aiglx work from outside of Red Hat and one of the primary components of aiglx (the pixmap to texture extension) actually comes from the XGL!  It’s just where it’s integrated that’s important.  At worst, it’s a competition, at best, it’s inadvertent teamwork.

The irony here is that what we’ve done with the aiglx work means that we run on a lot of the open source 3d drivers, but we don’t run on the NVidia binary driver.  But NVidia says that they will be adding support for the extension in their next major driver release, which means that the aiglx code will run on a pretty wide variety of cards under Linux.  (I don’t know about the ATI folks - they have been mum on the subject.)

The important thing to realize about aiglx is that it’s a method to incrementally improve the desktop.  If your driver supports it, you turn it on.  If you don’t it still works.  And it turns out that building a window manager takes years of work.  Sure, you can get one that’s working properly in a couple of months but you spend years adding support for all the old strange legacy clients that are out there and adding enough features to make it usable for a wide variety of users.  Simply put, it’s easier to add compositing manager capabilities to a working window manager than it is to turn a compositing manager into a working window manager.  What I’m really hoping will happen is that we can take all of the really well-polished features that are found in compiz and get them into metacity.   Because that’s where the real value is in compiz - not the window management capabilities, but the great 3D effects it has.  It would be great if we could get the best of both worlds and deliver a unified solution. 

[http://www.0xdeadbeef.com/?p=178](http://www.0xdeadbeef.com/?p=178)

So its a non-issue.

---

### Post by heretic9 on 2006-02-22
There are a couple of small vids of aixgl here:

[http://fedoraproject.org/wiki/RenderingProject/aiglx]("http://fedoraproject.org/wiki/RenderingProject/aiglx")

From what i've seen what aixgl wants to do soon, xgl can do now. I like the fact that their changes are incremental in nature but they're still some way off where as XGL development seems to be steam rolling ahead.

BTW, they mention a demo here:
[http://fedoraproject.org/wiki/RenderingProject/DemoPlans]("http://fedoraproject.org/wiki/RenderingProject/DemoPlans")

Anyone know if they actually showed the demo at the xdev meeting?

---

### Post by gururise on 2006-02-22
Ok, so after much reading, I have come to the following conclusions:

_Advantages of XGL + Compiz:_

1) XGL + Compiz can "today" produce flashier effects than AIGLX.  However, this does not necessarily translate directly to having a better architecture or better technology.

2) XGL + Compiz gets rid of most of the Composite problems (crashing/jittery video playback, etc) by bypassing Composite altogether and going straight to OpenGL for everything.  As a side effect, you do not need video card drivers that support the Composite extension, but rather only OpenGL.

3) **XGL + Compiz accelerates EVERYTHING on the desktop, including 2D by going through the 3D engine of the gfx card.**

_Advantages of AIGLX:_

1) An incremental approach, therefore supposedly not requiring as many code changes (however, I dont think anyone has compared code between the two approaches yet).

2) More support for open drivers (currently), however, there is little or no support for closed drivers.

3) Utilizes existing Metacity window manager.  Metacity is known to work well with GNOME and apparently can handle certain legacy situations well.  It is unknown if Compiz has issues with legacy cards.


Unless I am mistaken, **XGL will accelerate your whole desktop, and I see that as a major advantage**.  Sure, some of the older cards that do not support OpenGL may not work, but do we want to stymie progress just to maintain backward compatability with older cards?  Look at the requirements for Vista, you will require DX9+ in order to use most of the graphical enhancements.  Sorry, if you have an old SIS graphics card, you might as well stick with Windows 2000.  

So while I understand that an 'incremental' update to the XServer may be seen as an advantage for some.  The majority of users who have who have hardware built after 2001+  will be able to take better advantage of XGL.  If the metacity issue is a showstopper, maybe they should concentrate on porting metacity to XGL.  

I feel that the touted advantage of 'incremental upgrade' to the XServer is really a disadvantage.  A re-write of the XServer in the spirit of XGL would provide a greater advantage to most users.  What do you guys think?

---

### Post by DrFunkenstein on 2006-02-22
[QUOTE=gururise]
Unless I am mistaken, **XGL will accelerate your whole desktop, and I see that as a major advantage**. 
[/QUOTE]
I think you are mistaken in thinking that only using OpenGL does provide hardware acceleration. IIUC some of the xorg devs are arguing that it is even more efficient to do certain opperations with the 2D hardware, not the 3D hardware and use OpenGL only where it makes sense.

And you shouldn't take backward compatability to lightly. That people can run Linux on older hardware is a great feature of the OS imho, but then again, nobody is forced to use XGL so it doesn't really take away backward compatability either.

---

### Post by r_a_trip on 2006-02-22
*r_a_trip hate to say it but you're the biggest elitest I've ever come across.*

*"Linux is not windows, windows is simple, easier and work for me." - Simple tasks for simple people if they can't think outside the box then it is their problem.*

Look who's talking...


see: [http://www.ubuntuforums.org/showthread.php?t=133555&page=3&highlight=aiglx](http://www.ubuntuforums.org/showthread.php?t=133555&page=3&highlight=aiglx)

---

### Post by elanthis on 2006-02-22
> Advantages of XGL + Compiz:

1) XGL + Compiz can "today" produce flashier effects than AIGLX. However, this does not necessarily translate directly to having a better architecture or better technology.

AIGLX produces the exact same flashy effects.  You seriously need to NOT lump compiz and Xglx together.  Anything and everything that Xglx can do, the AIGLX X.org branch can do, and vice versa.

> 2) XGL + Compiz gets rid of most of the Composite problems (crashing/jittery video playback, etc) by bypassing Composite altogether and going straight to OpenGL for everything. As a side effect, you do not need video card drivers that support the Composite extension, but rather only OpenGL.

This is all wrong.  Xglx does NOT get rid of Composite.  Let me repeat, Xglx does NOT get rid of Composite.  If you didn't have Composite, how would Compiz even work?  Compiz is a composite manager.  It is based entirely off of the Composite extension!

What Xglx *does* do is add an alternate implementation of all X 2D drawing commands, including the Composite extension, and accelerate it all through a host X server's GL support (i.e., DRI or NVIDIA's GL acceleration architecture).

> 3) XGL + Compiz accelerates EVERYTHING on the desktop, including 2D by going through the 3D engine of the gfx card.

That would be true if the 3D engine and the OpenGL drivers were capable of accelerating everything.  They can't all do that.  Not even NVIDIA's drivers do right now.  Xglx is actually noticably slower than X.org on NVIDIA hardware (though it is hard to notice at first, as the perceived speed is boosted thanks to Composite).  That won't be fixed until the NVIDIA driver supports GLX_EXT_texture_from_pixmap.  And, the second the NVIDIA driver supports that, Compiz will be able to run at full speed on the X.org AIGLX branch.

> Advantages of AIGLX:

1) An incremental approach, therefore supposedly not requiring as many code changes (however, I dont think anyone has compared code between the two approaches yet).

It's really a no-brainer.  All AIGLX does is add indirect accelerated rendering to X.org.  This has been in the works for a long while.  Most of that work was NOT done by Red Hat, in fact; much of it was done by IBM and other X.org contributors.  Some of it even done by Novell!

> 2) More support for open drivers (currently), however, there is little or no support for closed drivers.

It has all the support for closed drivers that Xglx has.

The big difference is that the AIGLX branch doesn't have any software version of GLX_EXT_texture_from_pixmap... yet.  A software version of that can give tolerable speeds.  To get truly blazing speeds, though, both Xglx and AIGLX are going to need driver support.

> 3) Utilizes existing Metacity window manager. Metacity is known to work well with GNOME and apparently can handle certain legacy situations well. It is unknown if Compiz has issues with legacy cards.

This is wrong, because Metacity is not tied to the AIGLX branch and Compiz is not tied to Xglx.  You can run either Metacity (with compositor) or Compiz on either the AIGLX branch or Xglx.

---

### Post by r_a_trip on 2006-02-22
*Should I not be allowed to speak because "protecting the ideals of free software" is not my top priority?*

Speak. I am not silencing you. Don't expect me to shut up either. I will stay vocal too. Free Software exists because it is about Freedom, not some latest whizbang gizmo. Every descision that could potentially lead to inclusion of technology solely dependant on closed source infrastructure is a nail in the coffin of Free Software.

Everybody who thinks that a little closed source isn't damaging is an enemy within. It is your stance on things that convinces me that you are a danger to the survival chances of Free Software, in this case particularly the GNU/Linux variant of Free Operating systems.

Your stance is utterly selfish and shallow. You only want some short term gains. You don't think about the rammifications your cries for some ultimately redundant eyecandy has. If XGL will become the default on all distro's and the true X server framework becomes a ghostly background shadow, you've just shut out all those not so fortunate to be able to say: *Then I will buy a new one. Who cares, its just a graphics card!* Not everybody is as lucky as you and me to just run brainlessly around buying new gadgets. Your "itch" has the potential to become other peoples pain.

*RMS and yourself might be able to hack drivers but I can't and neither can millions of other Linux users.*

I can't either, but I can restrain myself to strive for the best technology accessible to almost all. This sometimes means saying no to stuff that could give me some pleasure, but others much grief.

*If a graphics driver lacks a feature then it does not matter how Free it is- I am screwed either way out of that feature. Sure you say "but you can hire someone to do it for you." I looked into that. For the feature I wanted I could find no one willing to allow me to pay them to add it to the R200 driver. To most of the world, the Libre approach is fine when it works, and just as bad as the closed source route when it doesn't.*

Sorry, all I hear is "Me, me, me." You don't need everything that is available under the sunshine my dear.

*But if you try to stop me, expect me to spend more money on my gilded cage. It has served me better than the one with the door open!*

Which is why you are the enemy within. You say you are into GNU/Linux and you love it, but the instant a less than Free graphics solutions hops along, you wipe away any common sense and scream: Me wanna, me wanna. If your kind gets its way, GNU/Linux will end up being another semi-closed source OS and you will eventually migrate to something else, leaving the perverted, dying carcas of GNU/Linux behind.

I can now see why we can't beat Microsoft. The moment someone with some mirrors and beads comes along, you trade in all your valuables to just get the trinkets.

---

### Post by aent on 2006-02-22
[QUOTE=r_a_trip]Voting with your wallet and making this known by being vocal makes changes happen. Kissing Novells butt, because they threw a shiney bone, won't.[/QUOTE]
Can you please explain to me how to vote with my wallet? Currently, there are ZERO decent video cards with open source drivers. My only option would be to not buy a video card. If I do that, however, NVIDIA and ATI would not see any lost sales as I would not be a potential customer, and my vote with my wallet would not be heard. The day that there are open source drivers for a competitve video card at a competitive price, I am sure I, along with many others, will vote with our wallet. Until then, its really impossible to effectively vote with our wallet.

---

### Post by poofyhairguy on 2006-02-23
[QUOTE=r_a_trip]*Should I not be allowed to speak because "protecting the ideals of free software" is not my top priority?*

Speak. I am not silencing you. Don't expect me to shut up either. I will stay vocal too. Free Software exists because it is about Freedom, not some latest whizbang gizmo. Every descision that could potentially lead to inclusion of technology solely dependant on closed source infrastructure is a nail in the coffin of Free Software.

Everybody who thinks that a little closed source isn't damaging is an enemy within. It is your stance on things that convinces me that you are a danger to the survival chances of Free Software, in this case particularly the GNU/Linux variant of Free Operating systems.[/QUOTE]

Nothing I can do nor anyone can stop the path of free software. Debian will exist with its puritan nature not matter if people like me are in the overall Linux community or not.

> 
Your stance is utterly selfish and shallow. You only want some short term gains. You don't think about the rammifications your cries for some ultimately redundant eyecandy has. 

Its about more than eye candy- its about having a modern framework for graphics on Linux.

> 
If XGL will become the default on all distro's and the true X server framework becomes a ghostly background shadow, you've just shut out all those not so fortunate to be able to say: *Then I will buy a new one. Who cares, its just a graphics card!* Not everybody is as lucky as you and me to just run brainlessly around buying new gadgets. Your "itch" has the potential to become other peoples pain.

Stop right there. Never will "all distro's" have XGL as the default. There will always be things like Damn Small Linux for older computers. If the major distros don't shoot for having the lowest system requirements then that is progress is many ways.

> 
Sorry, all I hear is "Me, me, me." You don't need everything that is available under the sunshine my dear.

No. But I am going to scratch my itch. And guess what? My plan works for me.

Show me modern hardware with open drivers. There is none. Oh yeah - "I don't need everything under the sun." Great answer- way to win people to your side!

While I'll go "if you buy this Nvidia card and follow this guide your Linux desktop will beat all other desktops out there." Guess who will win more converts.

The writings on the wall. The Novells and Linspires and Ubuntus of the world control the fate of Desktop Linux, not people like yourself. Each of them offers a "tainted" product. Heck Mark will admit to anyone that Lauchpad is closed source software now because he plans to make money on it. 

Nothing can kill the Libre operation system called Linux. You will always have a 100% open source option. It just might be more limited or primative compared to tainted Distros, just like today.

> 
Which is why you are the enemy within. You say you are into GNU/Linux and you love it, but the instant a less than Free graphics solutions hops along, you wipe away any common sense and scream: Me wanna, me wanna.

First of all there is no "less than Free graphics solution." Xgl (and ALL of this stuff) is licenced under a Debian approved license. I know for a fact XGL works with the r200 drivers- a friend of mine did it.

> 
If your kind gets its way, GNU/Linux will end up being another semi-closed source OS and you will eventually migrate to something else, leaving the perverted, dying carcas of GNU/Linux behind.

Again, there will always be at least a few distros that don't package binary drivers or other things like that. Your sort demands the option. I just refuse to accept "you don't need that" as the answer to why there can't be acceptable "tainted" options as well.

But keep up your venom, you sure are keeping this thread on topic.

> 
I can now see why we can't beat Microsoft. The moment someone with some mirrors and beads comes along, you trade in all your valuables to just get the trinkets.

We can't beat Microsoft because of people like me?! Thats the funniest thing I have ever heard in my life.

---

### Post by mstlyevil on 2006-02-23
[QUOTE=r_a_trip]*Should I not be allowed to speak because "protecting the ideals of free software" is not my top priority?*

Speak. I am not silencing you. Don't expect me to shut up either. I will stay vocal too. Free Software exists because it is about Freedom, not some latest whizbang gizmo. Every descision that could potentially lead to inclusion of technology solely dependant on closed source infrastructure is a nail in the coffin of Free Software.

Everybody who thinks that a little closed source isn't damaging is an enemy within. It is your stance on things that convinces me that you are a danger to the survival chances of Free Software, in this case particularly the GNU/Linux variant of Free Operating systems.

Your stance is utterly selfish and shallow. You only want some short term gains. You don't think about the rammifications your cries for some ultimately redundant eyecandy has. If XGL will become the default on all distro's and the true X server framework becomes a ghostly background shadow, you've just shut out all those not so fortunate to be able to say: *Then I will buy a new one. Who cares, its just a graphics card!* Not everybody is as lucky as you and me to just run brainlessly around buying new gadgets. Your "itch" has the potential to become other peoples pain.

*RMS and yourself might be able to hack drivers but I can't and neither can millions of other Linux users.*

I can't either, but I can restrain myself to strive for the best technology accessible to almost all. This sometimes means saying no to stuff that could give me some pleasure, but others much grief.

*If a graphics driver lacks a feature then it does not matter how Free it is- I am screwed either way out of that feature. Sure you say "but you can hire someone to do it for you." I looked into that. For the feature I wanted I could find no one willing to allow me to pay them to add it to the R200 driver. To most of the world, the Libre approach is fine when it works, and just as bad as the closed source route when it doesn't.*

Sorry, all I hear is "Me, me, me." You don't need everything that is available under the sunshine my dear.

*But if you try to stop me, expect me to spend more money on my gilded cage. It has served me better than the one with the door open!*

Which is why you are the enemy within. You say you are into GNU/Linux and you love it, but the instant a less than Free graphics solutions hops along, you wipe away any common sense and scream: Me wanna, me wanna. If your kind gets its way, GNU/Linux will end up being another semi-closed source OS and you will eventually migrate to something else, leaving the perverted, dying carcas of GNU/Linux behind.

I can now see why we can't beat Microsoft. The moment someone with some mirrors and beads comes along, you trade in all your valuables to just get the trinkets.[/QUOTE]

I hate to break it to you but the kernel creator himself (Linus Torvaldis) has expressed recently that Linux should support closed source software and DRM. That means the kernel is tainted at the core and that Linux is compromised from the ground up. If you are so concerned about having a Operating System that is not tainted by propietary software then you will have to ditch Linux and move on to Free BSD or something else. Linux has already left you behind yet you keep holding on to some utopian idea that just does not exist in Linux.

Also, **most** people using Linux do not believe the way you believe so if you think by somehow taking a thread off topic in a forum is going to change the world, you are sadly mistaken.

---

### Post by DrFunkenstein on 2006-02-23
[QUOTE=mstlyevil]I hate to break it to you but the kernel creator himself (Linus Torvaldis) has expressed recently that Linux should support closed source software and DRM.
[/quote]
I hate to break it to you, but these very same kernel developers have again and again expressed their dislike of propietary, non-free kernel modules. In fact, people KGH even discuss now to change the kernel in a way that would make non-free kernel modules impossible. And after all, we are talking about graphic drivers which, surprise, surprise, are implemented as kernel modules.

[QUOTE=mstlyevil]
 That means the kernel is tainted at the core and that Linux is compromised from the ground up.
[/quote]
See above. Not true.

[QUOTE=mstlyevil]
If you are so concerned about having a Operating System that is not tainted by propietary software then you will have to ditch Linux and move on to Free BSD or something else. Linux has already left you behind yet you keep holding on to some utopian idea that just does not exist in Linux.
[/quote]
It's not an utopian idea, it's the ideas of the free software movement, without which you wouldn't have something like Ubuntu in the first place.

[QUOTE=mstlyevil]
Also, **most** people using Linux do not believe the way you believe so if you think by somehow taking a thread off topic in a forum is going to change the world, you are sadly mistaken.[/QUOTE]
He was answering to some rather stupid comments someone else made. Even if you don't agree with him this does not mean a personal attack on him is justified. On the contrary, it's just pathetic.

---

### Post by mstlyevil on 2006-02-23
[QUOTE=DrFunkenstein]I hate to break it to you, but these very same kernel developers have again and again expressed their dislike of propietary, non-free kernel modules. In fact, people KGH even discuss now to change the kernel in a way that would make non-free kernel modules impossible. And after all, we are talking about graphic drivers which, surprise, surprise, are implemented as kernel modules.
[/QUOTE]

So you are saying the lead developer of the kernel who has time and time again stated that he has no problem with proprietary software and DRM support being included in the kernel has no influence whatsoever on the rest of the development team? Linus even refuses to support GPL3 or allow Linux to be licensed under it for that very reason. In fact most of the developers are against moving it to the GPL 3 license so they can not be against proprietary software and DRM support in Linux.

[QUOTE=DrFunkenstein]It's not an utopian idea, it's the ideas of the free software movement, without which you wouldn't have something like Ubuntu in the first place.[/QUOTE]

A lot of people that support the free software movement do not take the extreme positions that RMS and r_a_trip do, including myself. In fact many of those people believe the ideas of the free software movement and proprietary software can live side by side. It is extremist views on both sides of the fence that lead to tyranny. 

[QUOTE=DrFunkenstein]He was answering to some rather stupid comments someone else made. Even if you don't agree with him this does not mean a personal attack on him is justified. On the contrary, it's just pathetic.[/QUOTE]

Where do you get this is a personal attack? Did I call him names? Or did I call him stupid or pathetic like you called me? I stated a fact. He took the thread off topic and he is trying to change the world by shoving his ideas down everyones throat. It is ok to give an opinion but to tell a **moderator** that he should just go back to using Windows just because he disagrees with him is pretty damn pushy and rude. His reply to poofyhairyguy was a personal attack.

---

### Post by DrFunkenstein on 2006-02-23
[QUOTE=mstlyevil]So you are saying the lead developer of the kernel who has time and time again stated that he has no problem with proprietary software and DRM support being included in the kernel has no influence whatsoever on the rest of the development team? 
[/quote]
No, I'm saying you are wrong about what Linus and other core kernel devs said about this matter. Just you want it to be the way you like it doesn't mean it is the way you like it.
So let me repeat it, they have made it very clear time and time again that they don't want non-free modules in kernelspace.

[QUOTE=mstlyevil]
Linus even refuses to support GPL3 or allow Linux to be licensed under it for that very reason. In fact most of the developers are against moving it to the GPL 3 license so they can not be against proprietary software and DRM support in Linux.
[/quote]
Sigh, how about actually reading what Linus said? He isn't againt GPL3 because he wants DRM, but as he made very clear, because he thinks that the GPL3 takes the wrong approach at fighting DRM. Now as many have stated, even this view isn't very convincing, as Linus might be wrong about what the GPL3 tries to achieve.
And where did you get the idea that most kernel devs were against moving to the GPL3 (that btw. doesn't even exist yet) and that they were against it becuase they want to support DRM and propietary software on Linux?

Anyway, we are talking about non-free modules in kernelspace here, not about some software running on top of the kernel that and the devs have been very, very clear about this issue.

[QUOTE=mstlyevil]
A lot of people that support the free software movement do not take the extreme positions that RMS and r_a_trip do, including myself. In fact many of those people believe the ideas of the free software movement and proprietary software can live side by side. It is extremist views on both sides of the fence that lead to tyranny. [/quote]
Then they don't know what the free software movement is and mix it up with the open source movement. And no, having a clear moral position does not lead to tyranny and broad sweeping assertions like "what my oponent thinks will lead to tyranny" are only a very sorry excuse for a coherent argument.


[QUOTE=mstlyevil]
Where do you get this is a personal attack? Did I call him names? Or did I call him stupid or pathetic like you called me? I stated a fact. He took the thread off topic and he is trying to change the world by shoving his ideas down everyones throat. It is ok to give an opinion but to tell a **moderator** that he should just go back to using Windows just because he disagrees with him is pretty damn pushy and rude. His reply to poofyhairyguy was a personal attack.[/QUOTE]
Maybe his reply was a personal attack, but then again, poofyhairyguy wasn't very civil either, to put it mildly.
About your post being a personal attack. Calling people extremists, saying their ideas will lead to tyranny in my, accusing them of taking the thread off topic, though they only replied to something, very much constiutes personal attacks.

---

