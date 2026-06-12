---
title: "How Ubuntu failed me"
date: 2008-07-06
forum: Testimonials &amp; Experiences
---

### Post by lotuseater_ on 2008-07-06
I don't mean this as a flame towards ubuntu, I mean it as constructive criticism. If you reply to say "you really know nothing about linux," then you've entirely missed the point. Here's my experience:

I have an IBM Thinkpad T23 with only 128mb of memory. For two years I have successfully run XP Pro on it without a single hitch, except that it was a bit slow. It never crashed, it never got a virus, I was able to quickly and easily install new software in 30 seconds, and it was compatible with everything. All I need is internet browsing, word processing, and music playing. That's it. I don't give a flying **** about learning linux terminal commands or how the filesystem or any of it works. That was likely my problem.

I had the wise idea to move to linux thinking that it would speed everything up and give me a "cool geeky" feeling while I use it on campus. Yes, I know that is stupid. I first try vanilla Ubuntu, having listened to all the hype about its user friendliness, and it stalls and goes nowhere during the installation. So, the Ubuntu installation requires more system resources than XP Pro did. Great. I move to the "lighter" version, xubuntu, and the same thing happened. I update the BIOS, embedded controller, and dvd drive firmware. Still fails. I disconnect my hub, flash drives, wireless card, and usb mouse, and it still fails. Then I try xubuntu's "alternate" installation for sub-128mb computers. Still fails.

By now, I have lost my entire saturday and a couple hours of sunday because of this. I end up installing fluxbuntu, which takes forever but finally succeeds. The user environment seems nice. Very minimal, which I like a lot. I try to access my FAT32 flash drive. I end up having to follow some tutorial, copying terminal commands, until I finally get it to work an hour later. What a pain in the ***. Then I spend the next two hours trying to figure out how to get my wireless network working. I glance at tutorials about compiling and installing software, and suddenly I have a migraine. Most of my weekend is gone because of this.

Finally, I get rid of it all and reinstall XP pro. Everything works and I am happy again, at last. What a tremendous waste of time.

---

### Post by kaldor on 2008-07-06
Ubuntu and Linux as a whole can be a hassle to a new user. Sure the terminal seems scary at first, but once you learn about it, you'll never want to let it go. 

As for the installation, Live CDs require at least 216 RAM I think. Though I don't know why the sub 128 xubuntu wouldn't work.

Linux is great in some ways. It's not perfect, but it works better than Windows in some ways, and in some ways it doesn't. Linux can't get viruses like Windows. Linux can't play games like Windows, and so on.

Depending on your system and your needs it can be great, and much better than Windows. To some people, they'd need Windows. It depends on your needs really.

At least you gave Linux a try and didn't automatically piss on it because it isn't made by Microsoft :)


Edit: On a side note, I installed Ubuntu on my new HP laptop in less than 10 minutes. :)

---

### Post by pikabuntu on 2008-07-06
Yeah, I can see your point, but not wanting to learn the terminal, etc. would make it a bit frustrating.  If you are just using the computer for the things like you said, it would probably not be worth it to try to totally switch over in one weekend.  Just give it some time and it might grow on you.

(i had a ton of trouble in the beginning to but it was worth it)

---

### Post by vikramaditya on 2008-07-06
methinks this should be in testimonials . . .

---

### Post by sports fan Matt on 2008-07-06
See, I havent missed the point.  I read the entire post, and honestly it was a rant.  

1.  You only having one post seems imteresting.  Why didnt you ask for help, we would have at least tried to give it.  If you dont care about learning new things why did you even try in the first place?

2.  128 MB ram probably would have been better with Damn small linux or Puppy linux.  Xubuntu would be a stetch as far as i know.  It was probably compatible yes, but slow cause of the ram you had.  

3.  Linux isnt Windows.  If you probably asked questions like I said in point #1 you would have gotten some additional help.  It generally depends on your hardware if Ubuntu will work well or not.  

Sorry but this post is a waste of time to me, its considered a rant in my opinion and is a tremoundous waste of time to read.  Have fun getting viruses (cause you will get them) and when you cool off, and ever decide to try Ubuntu and linux again, we will help.

---

### Post by EXCiD3 on 2008-07-06
Should be moved to community forum.

How can this be considered "constructive"? You give no support whatsoever on idea how to fix things and how to make it better?

Have you asked about your issues here before? probably not seeing that you only have 1 post. Many users would be glad to help you out, like myself. Just give us something to work with. If you really do wish to use linux, you have to want to use it, and not try halfway. Yes it may take a little more work that XP because some hardware just isnt supported entirely. If you post your specs and issues we can try to help! Another Linux user makes the world a better place! :)

---

### Post by sports fan Matt on 2008-07-06
I'll give him that..he tried..just seems abrasive and critical , cause the person thinks it needs to go exactly like Windows which isnt the case

---

### Post by tubasoldier on 2008-07-06
> **lotuseater_ said:**
> I don't mean this as a flame towards ubuntu, I mean it as constructive criticism. If you reply to say "you really know nothing about linux," then you've entirely missed the point.

So in other words: don't criticize his criticism.

---

### Post by Fingers &amp; Thumbs on 2008-07-06
Possible alternative titles for this thread:

How hardware manufacturers fail the common linux user.

or

How potential new linux user fails to do adequate research.

---

### Post by geovino on 2008-07-06
On a laptop with only 128 RAM I would have tried some lighter weight Linux distros like Tiny Me (PCLOS) or even Puppy Linux which runs well with 128 RAM. I would have also run it live for a few days and see how much can be tried out before a install. I wouldn't even bother with any computer with under 512 RAM for any good experience. Plus, laptops have more hardware problems than desktops overall. That's the beauty of live CDs... you can test drive before installing. 

I use five different distros (Ubuntu, Mint, PCLOS, sidux, opensuse) and they all work well, but I have a 2gb PC and another 1.25gb PC to try distros out on. 

I have five friends who knew nothing about windows and are happily using Linux of one form or another. You just picked the wrong computer to try it on.

I hope in the future you give Linux a try on another PC! :)

---

### Post by kamitsukai on 2008-07-06
you dont have to learn anything about the terminal it's called copy and paste...i cant see how you expected to get linux installed without even asking for help :( but alas you tried

---

### Post by snowpine on 2008-07-06
Hi Lotuseater, it is a shame this was your first post--if you'd come here sooner, we could have saved you a lot of time! The system requirements for Ubuntu are well-publicized: 256mb RAM (384 for the live CD), but we could have suggested a different "flavor" of Linux that would be a better match for your system.  

As for your problem auto-mounting USB devices in Fluxbuntu, it's a known bug that is mentioned right on the download page. All you need to do is enter the following code in the terminal:

```
mkdir ~/.ivman
```

I mention this in case you decide to give it another try, or for anyone else reading the thread with the same problem.

Good luck and thanks for sharing your experiences!

---

### Post by Sef on 2008-07-06
> methinks this should be in testimonials . . .

Agreed.

---

### Post by james_vanb on 2008-07-06
Just installed Xubuntu using Alternate CD on an IBM Thinkpad 570 with 128 M RAM,  Had to restart the install a few times, but it ultimately loaded.  Sound worked out of the box.  Wireless took about 15 min. using ndiswrapper.  Sorry it didn't work for you.

---

### Post by steveneddy on 2008-07-06
I think if you just bumped up the memory you would have had a better experience.

Who expects a modern OS to run on 128 mb of memory anyway?

Did you check for hardware compatibility?

Here's a T22, almost your specs, that runs Hardy, but they have more RAM.

[http://www.jarviser.co.uk/jarviser/ubuntu8ont22.html](http://www.jarviser.co.uk/jarviser/ubuntu8ont22.html)

Install more RAM to get a better experience.

Otherwise, run an older version of Ubuntu.

I might as well have gotten out my old 486 w/ 64 k of memory and complain that XP won't install, so it must be  POS and not ready for public consumption.

More RAM is the answer to your question.

Link to Linux on Laptops.

[http://www.linux-laptop.net/ibm.html](http://www.linux-laptop.net/ibm.html)

---

### Post by lazyart on 2008-07-06
XP was released in 2001, so a version of Linux released at about that time (or a year or two later) might've done you better and surely would've been a better comparison.  In defense however, if you would have looked at the system requirements you would have plainly seen that the current Ubuntu is too advanced for your hardware.

Would you install XP on a 286?  Probably not.  Same basic premise.  Ubuntu hasn't failed you.  You have failed Ubuntu.

---

### Post by wolfen69 on 2008-07-06
> **lotuseater_ said:**
> 

I have an IBM Thinkpad T23 with only 128mb of memory.

UBUNTU WILL NOT RUN ON 128 RAM! use the right tool for the right job. try something like puppy linux or damn small linux. geez. you try to put a square peg in a round hole and then complain it wont fit! wake up already. that thinkpad of yours is ancient. use a distro made for prehistoric equipment and stop complaining.

> lazyart:
Would you install XP on a 286? Probably not. Same basic premise. Ubuntu hasn't failed you. **You have failed Ubuntu**. well said.

---

### Post by lotuseater_ on 2008-07-06
Actually, I did find a small version that installed and ran fast. It was fluxbuntu, as I explained.

I thought this might offend more than a few people. I didn't need to post any new help topics because I know how to use search engines and all my issues were already out there, many times over. It was just a matter of jumping through hours worth of hoops to follow them and get things working. I just got tired of it. 

I listened to the hype that ubuntu was an accessible alternative to windows, that a windows user could switch to it with ease. I don't see how you can say I "failed ubuntu" if I used it with this expectation. I know this may be a hard concept to grasp for many of you, but I have absolutely zero interest in learning terminal commands and various technical aspects of an OS, and this seems to be totally required to be a user of any linux distro. The process I had to go through to get my flash drive working and mounted was ridiculous. And it seemed to be the norm. Ubuntu could never replace the accessibility of OS X or windows at this point, from my experience.

---

### Post by wolfen69 on 2008-07-06
OK, wise one, give somebody a copy of windows to install *that has never used windows* and then talk to me. they would do nothing but complain how hard it is. please, dont go there.

---

### Post by Red-Shield on 2008-07-06
wow that was a lot to read i have to say i have only been a linux user for about 2 1/2 years now having all the usual problems with microsoft i still use it i have seperate hard drives microsoft for games and linux ubuntu ultimate for every thing else  i was warned it would be hard to start and wow was it but linux has opened a whole new world of computing and controle it can do things i never thought possible after using both for this period of time i still choose linux i have also started using unix i have learned far to much to mention in a thread using windows created a lazy person and i had no idea how to fix my comp when it broke because i did not understand what was what i thought the GUI was the OS wow is right linux rules i think you should try again it is worth it using linux helped me to understand windows better also although i never use it linux gives you complete controle over your computer my laptop runs cooler and is never bogged down please sir i ask you that you try again and this time use your resourses like this fourm and dont just click and past do your best to understand it and it will do things for you that you never thought possable................................................... here are all the periods you can put them where you see fit...........

---

### Post by bravo331 on 2008-07-06
> **Red-Shield said:**
> wow that was a lot to read i have to say i have only been a linux user for about 2 1/2 years now having all the usual problems with microsoft i still use it i have seperate hard drives microsoft for games and linux ubuntu ultimate for every thing else  i was warned it would be hard to start and wow was it but linux has opened a whole new world of computing and controle it can do things i never thought possible after using both for this period of time i still choose linux i have also started using unix i have learned far to much to mention in a thread using windows created a lazy person and i had no idea how to fix my comp when it broke because i did not understand what was what i thought the GUI was the OS wow is right linux rules i think you should try again it is worth it using linux helped me to understand windows better also although i never use it linux gives you complete controle over your computer my laptop runs cooler and is never bogged down please sir i ask you that you try again and this time use your resourses like this fourm and dont just click and past do your best to understand it and it will do things for you that you never thought possable................................................... here are all the periods you can put them where you see fit...........

Thats funny. I was reading above post and thinking "Has this person ever heard of a period?" Then I get to the end...

Anyway try Puppy Linux it is easy as hell to download and burn and it runs right from the CD!

---

### Post by lotuseater_ on 2008-07-06
All right, I'm going to install puppy linux. I'm determined to try to use linux for one month before I judge it so harshly. 

And I promise I won't make any vent threads ever again.... At least I didn't take my anger out on my cat or something.

---

### Post by steveneddy on 2008-07-06
> **lotuseater_ said:**
> All right, I'm going to install puppy linux. I'm determined to try to use linux for one month before I judge it so harshly. 

And I promise I won't make any vent threads ever again.... At least I didn't take my anger out on my cat or something.

If you can afford it and find memory for it, install at least 512 mb of memory in that laptop.

My old PIII has 512 mb of memory and runs Ubuntu fine.

Your main problem to this that I can see is the simple fact that you need more memory. The processor is a little slow, but should run Ubuntu well enough with Hardy.

Good luck, you'll like Puppy. It's a very fun distro.

---

### Post by Bubba64 on 2008-07-06
It is posts like this which make me realize how nice it has been to start with a Linux distro. I have never had to compare it with another, except when I have to use MS at school. Started with Dapper-Feisty-Gutsy-Hardy each one got easier to setup after installation, due to developers putting 3rd party packages access together in add remove.

---

### Post by wolfen69 on 2008-07-06
if the OP could manage to get even 256 ram in there, it would make a huge difference. with 256, and a half way decent cpu, i usually try to run xubuntu 7.04 and use the alternate cd. feisty seems to run decent on older hardware. but anyway, there's a ton of distros/scratch installs to try. it's not like your life depends on finding the perfect distro overnight. try different things and have fun with it. plus, you'll learn alot along the way. learning how to install linux properly would be a great thing to learn first. 

To th OP: btw, dont take my previous comments personally. im just very passionate about linux. peace.

---

### Post by L815 on 2008-07-06
I don't mean to sound harsh, but you're expecting too much from 128mb of ram. 

As far as terminal commands, it can be a bit scary for a new user, but you don't have to use it majority of the time. The reason it's popular is because it does things 'quicker' than via GUIs, and because of the power it has.

Anyway, maybe you'll give Linux a try again in the future.

---

### Post by buntunub on 2008-07-06
128M Ram

:lolflag:

Well anyway, there are some really great Distro's out there that can handle that minuscule amount of RAM with great ease -

DSL
PuppyLinux
Arch
Slackware
Gentoo
Few others I cant remember right now that were specifically built for ultra low end systems like yours.

Point is, you gave Linux a try for all the wrong reasons and you got burnt. Ubuntu minimum requirements are more than yours and 384M is recommended just to run even somewhat well. Heck, I have 512M on the server and it sometimes runs a bit sluggish. WinXP Pro on 128M Ram?.. Sorry, thats just not happening. Its doable, but performance on that pathetic system you have would be plain unbearable.

---

### Post by stchman on 2008-07-07
> **lotuseater_ said:**
> I don't mean this as a flame towards ubuntu, I mean it as constructive criticism. If you reply to say "you really know nothing about linux," then you've entirely missed the point. Here's my experience:

I have an IBM Thinkpad T23 with only 128mb of memory. For two years I have successfully run XP Pro on it without a single hitch, except that it was a bit slow. It never crashed, it never got a virus, I was able to quickly and easily install new software in 30 seconds, and it was compatible with everything. All I need is internet browsing, word processing, and music playing. That's it. I don't give a flying **** about learning linux terminal commands or how the filesystem or any of it works. That was likely my problem.

I had the wise idea to move to linux thinking that it would speed everything up and give me a "cool geeky" feeling while I use it on campus. Yes, I know that is stupid. I first try vanilla Ubuntu, having listened to all the hype about its user friendliness, and it stalls and goes nowhere during the installation. So, the Ubuntu installation requires more system resources than XP Pro did. Great. I move to the "lighter" version, xubuntu, and the same thing happened. I update the BIOS, embedded controller, and dvd drive firmware. Still fails. I disconnect my hub, flash drives, wireless card, and usb mouse, and it still fails. Then I try xubuntu's "alternate" installation for sub-128mb computers. Still fails.

By now, I have lost my entire saturday and a couple hours of sunday because of this. I end up installing fluxbuntu, which takes forever but finally succeeds. The user environment seems nice. Very minimal, which I like a lot. I try to access my FAT32 flash drive. I end up having to follow some tutorial, copying terminal commands, until I finally get it to work an hour later. What a pain in the ***. Then I spend the next two hours trying to figure out how to get my wireless network working. I glance at tutorials about compiling and installing software, and suddenly I have a migraine. Most of my weekend is gone because of this.

Finally, I get rid of it all and reinstall XP pro. Everything works and I am happy again, at last. What a tremendous waste of time.

If all you need is internet browsing, word processing, and music playing then Ubuntu fits the bill.

Before installing Linux you need to make sure that all the hardware is compatible.

---

### Post by lazyart on 2008-07-07
> **lotuseater_ said:**
> Ubuntu could never replace the accessibility of OS X or windows at this point, **from my experience.**

Everyone is welcome.  And of course, everyone is entitled to a refund.  But seriously, your hardware isn't ready for Ubuntu.  With 128 megs of memory I don't know how it's ready for XP Pro.  I support XP machines as my primary source of income and you can see instantly the machines with 256 megs vs those with 512 and above.

As for the flash drive, you've got me stumped.  I use them all the time and they auto mount and nautilus opens them.

There is one more bit about Linux that many folks don't realize.  Ubuntu is not the only linux distro.  To extend that further, the issues you have with Ubuntu linux might go away with DSL, Puppy, Mandriva, PCLinux OS, etc.  It's a huge umbrella.  I tried Red Hat and Mandrake (now known as Fedora and Mandriva) many many moons ago and had the same reaction-- this stuff is for the birds!

The biggest difference is that I didn't blame the OS, I blamed myself for not going deep enough into it to learn and understand.  I tried them for about a week, and that is not enough.  When I went to Ubuntu a year and a half ago I installed it on a seperate machine and tried it for an hour or so, then went back to Windows.  After about a month I was doing equal time on the machines, and in three months I had stopped booting Windows altogether.  Ease yourself in so you can stay productive while learning.

And yes, the command line is forever married to Linux.  And it's efficient.  Imagine if you had to point and click your way through creating a Word document.  Locate an icon for each word and punctuation mark.  Not the best way to get things done, is it?

So the stove is in a different place.  Maybe the door on the fridge opens backwards.  The spices are not where you thought they would be.  The dial on the oven works differently.  That's okay.  Spend enough time in the linux kitchen and you'll be cooking like the rest of us.  Even if you just want to use the microwave, just learn to use the control panel.  It all works.

---

### Post by wolfen69 on 2008-07-08
> **lazyart said:**
> 

There is one more bit about Linux that many folks don't realize.  Ubuntu is not the only linux distro.  To extend that further, the issues you have with Ubuntu linux might go away with DSL, Puppy, Mandriva, PCLinux OS, etc.  It's a huge umbrella.  I tried Red Hat and Mandrake (now known as Fedora and Mandriva) many many moons ago and had the same reaction-- this stuff is for the birds!

The biggest difference is that I didn't blame the OS, I blamed myself for not going deep enough into it to learn and understand.  I tried them for about a week, and that is not enough.  When I went to Ubuntu a year and a half ago I installed it on a seperate machine and tried it for an hour or so, then went back to Windows.  After about a month I was doing equal time on the machines, and in three months I had stopped booting Windows altogether.  Ease yourself in so you can stay productive while learning.



nice reply. i agree. wow, people actually use their brain.

---

### Post by Fingers &amp; Thumbs on 2008-07-08
> At least I didn't take my anger out on my cat or something.

That is a good thing. I'm glad that you have decided to give linux another try, not because I have anything against windows, windows is the right choice for many people, but rather because you had a bad experience at first and now, having gained some good advice, you can now make a much more informed decision. So already your bad experience has become a positive experience.

You mentioned in your initial post about the hype surrounding ubuntu, and of course hype makes things sound compelling, but hype is never a guarantee that something is right for you.

On a final note, don't be put off by the command line, although it isn't necessary to use it, it's not as daunting as you may think and can speed many tasks up conciderably. And above all it opens up a whole new world in terms of making your computer do what you want to do, the way you wamt to do it, and you don,t have to be an expert to make yourself feel like a genius.

Best wishes and good luck with your choice of distro.

---

### Post by gunashekar on 2008-07-08
> **Fingers & Thumbs said:**
> Possible alternative titles for this thread:

How hardware manufacturers fail the common linux user.

or

How potential new linux user fails to do adequate research.

Could there be a more friendly approach to criticism?

---

### Post by caravel on 2008-07-08
This thread has reminded me that I need to get some memory for that crap laptop of mine... :lolflag:

---

### Post by Fingers &amp; Thumbs on 2008-07-08
> Could there be a more friendly approach to criticism?

You're absolutely right, gunashekar and I appologise. That post was intended to be much longer with more constructive advice, but much demands on my time meant I was forced to end abruptly. In hindsight, I perhaps should have refrained from posting an incomplete message. I hope my post immediately previous to yours demonstrated that I meant no offense or unfriendliness, since it is friendliness that is ubuntus greatest asset.

My greatest respect goes to all in this thread who have helped turn the OP's experience into a posive one.

---

### Post by grimdeath on 2008-07-08
i started reading this thread being upset with with the original posters attitude, or well...frustrated FOR him because I did have some similar issues when I first used linux (red hat fedora 3 years ago)

there are things that are absolutely different then windows and this can cause problems for new users that are use to windows. after discovering the forums and leaning to do the "ubuntu (insert problem here)" search on google I have found myself much happier.

there's a couple things that people have touched on but I want to help make clear:

-Ubuntu has a Live disc as well as a install disc. the install disc works like windows with very basic graphical menus rather then a full desktop environment. If you are dual booting Hard Haron has Wubi which allows you to install ubuntu from inside windows.

-I have tried Ubuntu numerous times and my least favorite part is still the command line, I know enough to get by but that is OK...a wide majority of tasks that rely on it can be completed using copy/paste...when I first started I was trying to type everything in manually which was a pain!

I kinda found it funny that you said Mac OS is however you put it, better and more able. Mac OS is derived from the same place linux is. In fact my experience using a Mac lately made me realize how closely the interface at least with ubuntu/gnome is to a mac...very clean, graphical and things like the file structure work almost exactly the same. Even the fact that the applications drop down is in the upper left corner by default was kinda funny to me.

At any rate, I am super glad you have decided to give it a chance now that you know what your issue was. I think we all hate that you had a bad experience your first time but if you are anything like me...you will be back over and over :P

Enjoy!

---

### Post by 3rdalbum on 2008-07-09
Fluxbuntu is not for newbies - I know, they should make it more obvious on their website.

Did you try using the Alternative CD to install Xubuntu? 128 megs of RAM is really too little for an operating system from 2008. **Xubuntu can run, but not install, in 128 megs.**

I'd also like to point out that most people never actually install Windows; it comes preinstalled on computers. The future of Linux is in preinstalled configurations where everything either works out-of-the-box already, or is already set up for you.

---

### Post by decoherence on 2008-07-09
Today I installed a printer driver for an XP user. The installer died part way through. When I finally did get it installed, I discovered the desktop location policy had changed (these are network account... users have the option of a personal desktop or a common desktop) causing the user's icons to mysteriously vanish.

So what happened? Was the printer installer writing over parts of the registry that it didn't have to? Who knows? The driver and installer (and operating system) are closed source and getting a straight answer from HP isn't possible. Just one of those wacky Windows things where you whip it back in to shape, shrug your shoulders and move on. I really hate not knowing WHY something went wrong because it means it could go wrong again.

Just thought I'd share that anecdote, since it just happened. No such thing as a perfect (or even consistently good) operating system. They all suck in one way or another. The question is which one sucks least for what you're doing, which one lets you most easily work around the suckage and which one will stop sucking as quickly as possible?

You know the answer! ;)

---

### Post by snowpine on 2008-07-09
> **3rdalbum said:**
> Fluxbuntu is not for newbies - I know, they should make it more obvious on their website.

Hey, I am a total "n00b" and I love Fluxbuntu! I think there is an important distinction between "being a beginner" and having "beginner mind." Beginner mind means, among other things, being patient, going step by step, asking for help, making notes of what works and doesn't work, not making assumptions or jumping to conclusions, etc. If you have this frame of mind, there's no such thing as "not for newbies."

On the other hand is the occasional post from a beginner who does not have beginner mind. "I know how to defragment my hard drive, use itunes, and browse with internet explorer; but when I tried ubuntu, it didn't work."

I used to work in tech support, and it never ceased to amaze me how hard it is for some people to follow step-by-step directions. I guess it is a Meyers-Briggs type of thing. 

me: ...and type the URL mail.snowpine.com
them: Page not found
me: Really? what URL did you type?
them: [www.mail.snowpine.com](www.mail.snowpine.com)

And so forth. :)

Oh I'm rambling, what's my point? Oh right, beginner mind is good for you!

---

### Post by Jammy4041 on 2008-07-09
Nice to see that you've given ubuntu a second chance. Don't be afraid to ask for help.I think their might be a Puppy Linux subforum on this website.

As for the terminal- don't worry about it. It's scary at first, but you'll come to know the terminal like your back of your hand- I for one was definitly in the same boat, and I think so were many linux users.

BTW: I would upgrade your RAM. 128 even for windows is rough. I wouldn't even use Windows XP on that, so it would be much of a help if you would get some more.

---

### Post by lotuseater_ on 2008-07-13
Just wanted to update and say that I used puppy linux for a few days. I got everything to work but the network card. The GUI ran really fast and I started to learn a bunch of terminal commands. It was glaringly apparent that the OS itself is far better constructed and organized than windows.

I did get the wireless card to work, but it had unusually poor and finicky performance using both a linux driver and ndiswrapping a windows driver. A lot of different things ended up going wrong, and I spent quite a while scouring forums and following instruction. Later, when I plugged in my speakers, I found that my audio jack didn't work at all. My frustration got the better of me and I reinstalled windows... sorry guys. I guess my biggest obstacle ended up being hardware compatibility, rather than the OS itself. I'm sure I'll give it a shot again in the future, but for now I just need my crappy laptop to be functional.

---

### Post by Canis familiaris on 2008-07-14
> **lotuseater_ said:**
> Just wanted to update and say that I used puppy linux for a few days. I got everything to work but the network card. The GUI ran really fast and I started to learn a bunch of terminal commands. It was glaringly apparent that the OS itself is far better constructed and organized than windows.

I did get the wireless card to work, but it had unusually poor and finicky performance using both a linux driver and ndiswrapping a windows driver. A lot of different things ended up going wrong, and I spent quite a while scouring forums and following instruction. Later, when I plugged in my speakers, I found that my audio jack didn't work at all. My frustration got the better of me and I reinstalled windows... sorry guys. I guess my biggest obstacle ended up being hardware compatibility, rather than the OS itself. I'm sure I'll give it a shot again in the future, but for now I just need my crappy laptop to be functional.
Next time you buy a PC buy hardware which is more Linux compatible.

---

### Post by binukavumkal on 2008-07-18
I had the problem similar to you. The whole day I was trying to install Ubuntu on my desk top.

The first problem was DVD itself was not detecting. I tried an hour and then posted in this forum. Believe me, with in minutes two to three reply came and I could resolve the issue.

Next the sytem hangs when I tried to replace the my older Ubuntu version with the new one. Again I got the help and tried with text mode installation.

Successfully installed. And so on. 

The point here is if you are connected, you can solve the problem. There are thousands of people around you who are ready to help you.

Of course Ubuntu (or any variant Linux) is NOT Windows. It's open source software. So it has its own issues. And you know people around the globe try to solve them. 

So we need to reach them to get the issues resolved

---

### Post by tiachopvutru on 2008-07-18
> **lotuseater_ said:**
> Just wanted to update and say that I used puppy linux for a few days. I got everything to work but the network card. The GUI ran really fast and I started to learn a bunch of terminal commands. It was glaringly apparent that the OS itself is far better constructed and organized than windows.

I did get the wireless card to work, but it had unusually poor and finicky performance using both a linux driver and ndiswrapping a windows driver. A lot of different things ended up going wrong, and I spent quite a while scouring forums and following instruction. Later, when I plugged in my speakers, I found that my audio jack didn't work at all. My frustration got the better of me and I reinstalled windows... sorry guys. I guess my biggest obstacle ended up being hardware compatibility, rather than the OS itself. I'm sure I'll give it a shot again in the future, but for now I just need my crappy laptop to be functional.

Well, you made the right choice. There's no reason sticking with an OS that would frustrate you, and don't worry about it, Linux users acknowledge that hardware compatibility is one of the main problems, if not the #1 problem, for ease of usage on a Linux OS/distro.

You jumped to conclusion a bit too early on the user friendliness of Ubuntu, but it's a good thing that you decided to be patience. I had a similar experience that you have had in the beginning, and I understand how frustrating it is when the hardware doesn't work, or take a long time looking things up in order for it to work.

Next time you install Ubuntu, or Linux for that matter, make sure you get more compatible-hardwares. It will make your experience a lot better.

Also, note that if you didn't have the hardware compatibility issues, there would be no need at all for using the terminal on Ubuntu if you don't want to. :)

---

