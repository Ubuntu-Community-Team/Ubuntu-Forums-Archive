---
title: "Abandoning Ubuntu on the family desktop"
date: 2010-01-22
forum: Testimonials &amp; Experiences
---

### Post by hoki_goujons on 2010-01-22
Hi folks,

I don't know if anyone reads these or cares, but here's my tuppence worth.

Broad picture:'ve had 9.10 on my home desktop for about a month now, used by me (a geek), my wife (no interest at all) and my two kids aged 6 and 3. I've run FreeBSD servers at work in the past, and use Ubuntu UNR on my netbook, and desktop in work in a VM for various things.

I've tried it as my main home desktop, and I'm going back to XP. There are a list of problems, which I'll go into, but the gist of it is that I just can't be bothered with the effort. I brutalise computers into doing what I want them to do all day in work, and don't want to have to do it at home. Maybe at one time I'd have enjoyed it, but not any more.

Problems:
[LIST]
[*]Fast user switching didn't work (essential in our house). Trying to use it would make the machine hang at a black screen. I disabled the non-free ATI drivers, and it worked. Yay. Disabling them meant that scrolling in all apps was jerky and unresponsive to the point of being barely usable. Boo.
[*]My son's Lego Star Wars games don't work. Some people have been able to get them going under Wine, other people can't. I can't in the time that I'm prepared to give it.
[*]Unclear crap with USB devices: I use a Mybook for all my media. Under Ubuntu, this keeps disappearing. Also, if someone plugs in a USB storage device and switches user, they get an error saying that they don't have permission to access that drive.
[*]Sound: can't get the front panel headphone jack to work in the time I'm prepared to give it. The sound card keeps disappearing and being replaced with a 'dummy' until reboot.
[/LIST]

There aren't many things in that list, but they're pretty much the essential things that we use our computer for - can't browse the web or write a document in comfort because of the scrolling issue, can't play games, can sometimes access media, can sometimes use audio.
Oh, and on a petty note - if I shut down, reboot or log out, I want it to happen when I tell it to. If I wanted it to happen in 60 seconds, I'd have clicked the button 60 seconds later. WTF is that all about?

Things I'll miss include MythTV, Dansguardian, all the great software in the repositories and the speed at which you've got a usable desktop after logging in.

This isn't a rant against Ubuntu - I use it for other things and it's great. But my home computer is a bland, 2 year old Dell with no exotic hardware and I just want an OS to work on it. I know some of my problems are caused by hardware vendors, some are are almost certainly fixable with enough time and effort, but I don't *want* to put effort into my home computer. My wife hates Ubuntu already after only a short time, and even my son - a geek in the making - wants XP back on. This adventure in OS choice hasn't been as bad as Vista, but it's been pretty disappointing.

---

### Post by OrangeCrate on 2010-01-22
There's nothing wrong with Vista, though I'd suggest an upgrade to Windows 7 from XP. It's pretty nice, and most likely would please all involved.

That being said, I haven't been happy with 9.10 either, and rolled back to 9.04, in anticipation of the release of 10.04 in April. You might try that, if you're up to it.

[http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html](http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html)

Good luck

---

### Post by kmsalex on 2010-01-22
> **hoki_goujons said:**
> Hi folks,
if I shut down, reboot or log out, I want it to happen when I tell it to. If I wanted it to happen in 60 seconds, I'd have clicked the button 60 seconds later. WTF is that all about?


its to give you time to do something you might have forgot, in xp you still have to click a confirmation after initially hitting shut-down from the start menu. the difference is that ubuntu keeps the desktop interactive where windows freezes the desktop
 

>  My wife hates Ubuntu already after only a short time, and even my son - a geek in the making - wants XP back on.

its the crack cocaine windows slips into the mouse clicks. ;)

---

### Post by Methuselah on 2010-01-22
Use what works for your harwdare, your family usage patterns, and the applications that you want to run!
Good luck with Xp.
):P

---

### Post by Corners on 2010-01-22
Did you at least try Kubuntu?  I tried both.  I did full installs on each on this "practice" (extra) computer I have.  Ubuntu didn't work as well ( for me).  Every time the computer went to sleep, the screen would go black, and it would never wake up.  You have to do the old push and hold the power button to kill it, and restart it.  In Kubuntu, everything worked better right off the bat.  The only "issue" I had was I had to change the master channel volume to "headphone" to get the volume buttons on the keyboard to actually change the volume of the speakers.  Other than that, so far, so good.  Currently, this "practice" computer is going to my father-in-law this Sunday as a test.  He is NOT computer literate.  He only surfs the net to check email.  His XP computer is SOOOOO slow.  I've tried to clean it up, but I can't get it running right.  Of course, there is no windows CD to reinstall it, so I'm going to give him this computer to see how it goes.

---

### Post by Swagman on 2010-01-23
User switching ?

Never needed it. I built my three daughters their own desktop computers (No bitching then is there)

Ati = Phail anyway.

Have fun in Malware land

---

### Post by ElSlunko on 2010-01-23
If you ever build a new PC and intend to use Ubuntu on it definitely get an NVIDIA based gpu. It'll work boatloads better and probably solve most of those issues you're having. But like most posters say, use what works best since it's the family PC. I don't bother trying to teach my girlfriend how to use Ubuntu because I know she simply doesn't care about my 'nerd' stuff ;P.

---

### Post by K7522 on 2010-01-23
First off I'd like to acknowledge that our hardware is different and what works for me may not for you. That said, we'll get into my two cents!

> **hoki_goujons said:**
> Oh, and on a petty note - if I shut down, reboot or log out, I want it to happen when I tell it to. If I wanted it to happen in 60 seconds, I'd have clicked the button 60 seconds later. WTF is that all about?
I don't know the hardware for your machine, but my machine takes 8 seconds from pressing the button to desktop and about 15 from shut down to power off. Perhaps processes installed by other users are complicating the shutdown, or more likely a slower hard drive (or one that's failing).

> **hoki_goujons said:**
> I know some of my problems are caused by hardware vendors, some are are almost certainly fixable with enough time and effort, but I don't *want* to put effort into my home computer.
If you do not install drivers, hardware will not work properly. I don't care if it's Windows XP, Windows 7, MAC or any Unix based OS. You have to put effort in. You have to get drivers. Ubuntu just makes it easier than any of the others. Instead of going and finding the drivers online, it's just a 'sudo apt-get install' away, or in the case of restricted video drivers, a popup on your desktop.

Actually... now that I look at it, most of your 'issues' are no  more than a 'sudo apt-get install' away. Not to come across like an ***, but you have no problem going to the nvidia website to get video drivers for Windows to work properly, what makes you think you can get away with not installing drivers in Ubuntu? Right... forgot... Ubuntu should already know and test all millions of hardware possibilities with each software choice in the repositories, and should include every driver ever created, even legacy to prevent the simplest 'sudo apt-get install'.

---

### Post by hoki_goujons on 2010-01-24
Wow, all these replies I didn't get notified about :D

I considered trying Kubuntu, but all the 'buntus have outworn their welcome here - my missus just wants her familiar stuff back, and even I'm sick of it.

I'm aware that Nvidia is more suited to Linux - it's always been the case since I started messing about with it 9 years or so back.

Just so you know where I'm coming from with this:

A couple of years ago I got bored of messing about with computers at home. I work with computers (digital forensics) for a living and used to find the constant tinkering fun, but now I just want stability and ease of use. I'd always built my own PCs and a had half a dozen cannibalised ones clutttering up the house, but it came time to build a new family one and speccing it up component by component just didn't appeal any more, so I went to Dell and spent 20 minutes choosing one, and felt very happy with it.
It's done very well, the only change I've made to it being replacing Vista with XP.  The video card was absolutely fine for my needs under XP. I suppose that the urge to tinker hadn't completely died in me though, because I started wondering about how well the family would do with Ubuntu - as I said, I use it on my netbook and a couple of machines in work, and I'm a big fan of it.


To K7522 - if you read my original post, I did install the restricted drivers for the ATI card but they meant that I couldn't do user switching - which is a bit of a showstopper in our house.

To Swagman - solving the user switching problem by buying 2 new computers is hilarious. Likewise, blaming the card for the lack of support doesn't really wash with me - I'm at the stage at home now where I don't want to be doing any 'helpdesk' duties at all, ever. These days, I want to be a user at home, not an admin - I don't care if the problem is with ATI not releasing decent drivers, or with Ubuntu not understanding the card, or the pixies sprinkling too much magic dust on the PCB. 

I want to install the OS on my generic, mass-market hardware, and I want it to work for me. XP, on this computer, does this a lot better than Ubuntu does. There have been times when Ubuntu has done it better - my work Acer Ferrari laptop takes about 2 days to get up and running with XP 64bit. Doing it on 64bit Ubuntu takes about 20 minutes from putting the CD in to logging on, and it works beautifully. My philosophy is that all software is fundamentally crap. The challenge is to find something that's un-crap enough to let you do what you want to do.

---

### Post by Irihapeti on 2010-01-24
I say use what works, for you, your hardware and your personal circumstances. Never mind what anyone else says. You've given it a good try.

I have to admit that I get irritated by the "it's not Ubuntu's fault, it's the manufacturers" line. If someone has a problem, they want an answer, not a statement assigning blame. That doesn't solve anything for them. Much more to the point, in my view, is "what are we going to do about it so as to solve your problem?" If there is no ready answer to that, better to say so outright.

---

### Post by M1ke on 2010-01-24
> **hoki_goujons said:**
> My philosophy is that all software is fundamentally crap. The challenge is to find something that's un-crap enough to let you do what you want to do.

I like it! :lol:

If you're looking for an upgrade from the aged XP in time and don't want to return to Ubuntu, you might want to consider Windows 7. It's actually a very solid OS in my experience, and I was delighted to find I didn't have to manually install a single driver. Out of the box it supported absolutely all of my hardware.

Granted it's not Ubuntu-fast on my setup, but it's far nippier than XP was and looks gorgeous.

---

### Post by ElSlunko on 2010-01-24
> **hoki_goujons said:**
> Likewise, blaming the card for the lack of support doesn't really wash with me - I'm at the stage at home now where I don't want to be doing any 'helpdesk' duties at all, ever. These days, I want to be a user at home, not an admin - I don't care if the problem is with ATI not releasing decent drivers, or with Ubuntu not understanding the card, or the pixies sprinkling too much magic dust on the PCB. .

It should wash though since your mass market hardware only works in windows because the 3rd party vendor created drivers for it on windows. I bought an nvidia card after struggling with ati for a while. It's just as simple as buying hardware that is best supported by the OS you want to use. In my case I liked ubuntu enough to buy my way out of problems. Nvidia is also mass market.

---

### Post by Swagman on 2010-01-24
Likewise I wonder why it's hilarious to want your children to have their own machine ?

They're going to need it for their school work soon enough and **BUILDING** a machine for them each is very cheap and cures any bitching between them issues.

---

### Post by Methuselah on 2010-01-24
You may want Ubuntu to work on your 'mass market' hardware but the fact is that it doesn't so unless you're going to do something about it, you just have to move on.
It appears you have done that which is the best course of action in such a situation.

But people like to cast these decisions in an overly emotional way.
I guarantee you that Ubuntu's feelings are not hurt by being removed and your feelings should not be hurt by the fact that it didn't work for you.
Computers from Dell are not unknown to contain cheap and somewhat obscure components while ATI's linux drivers are not of the best quality.

Once again,
Good luck to you!

---

### Post by malspa on 2010-01-24
Glad I'm not in the OP's shoes.

Multiple computers in this household: My Linux computers, and machines running Vista and XP.  The wife and kids normally use the Windows machines.  Everyone's happy.

---

### Post by steveneddy on 2010-01-24
So, you only tried one of the Ubuntu versions when there are four currently supported options for you right now?

8.04, 8.10, 9.04 and 9.10

Did you check your hardware for complete compatibility with Linux?

User switcher? Just log off and let the other person log on. Easy peasy. 

If you are running Ubuntu and the kids want to play video games (shudder) then install a VM and play Legos there.

Get rid of the ATI video card and go with Nvidia. 

Look, Ubuntu is a great OS, if, like Windows, all of the hardware is supported.

Great PC's with Ubuntu pre-installed are available through System76.com. That's where I purchase my laptops. I don't have time to play with the PC, so I buy known supported hardware and I don't have any issues. It's worth the expense every time.

I bought my daughter a System76 laptop for college and she loves it. She also had a Mac Book Pro dual booting with 7. She uses all three OS's depending on her task.

Enjoy Windows, but there are lots of other options out there. You just chose not to choose the correct options for you to have a good experience with Ubuntu.

---

### Post by llawwehttam on 2010-01-24
> **OrangeCrate said:**
> There's nothing wrong with Vista, though I'd suggest an upgrade to Windows 7 from XP. It's pretty nice, and most likely would please all involved.

That being said, I haven't been happy with 9.10 either, and rolled back to 9.04, in anticipation of the release of 10.04 in April. You might try that, if you're up to it.

[http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html](http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html)

Good luck

My experience with 9.10 almost made me roll back as 8.10 was great on my machine ( no even though others had problems with it) but I have just decided to live with 9.10 until Lucid. It had better impress me or I will be going over to the arch side.

---

### Post by JSeymour on 2010-01-24
> **hoki_goujons said:**
> I've tried [Ubuntu] as my main home desktop, and I'm going back to XP. There are a list of problems, which I'll go into, but the gist of it is that I just can't be bothered with the effort. I brutalise computers into doing what I want them to do all day in work, and don't want to have to do it at home. Maybe at one time I'd have enjoyed it, but not any more.
...
This isn't a rant against Ubuntu - I use it for other things and it's great. But my home computer is a bland, 2 year old Dell with no exotic hardware and I just want an OS to work on it. I know some of my problems are caused by hardware vendors, some are are almost certainly fixable with enough time and effort, but I don't *want* to put effort into my home computer. My wife hates Ubuntu already after only a short time, and even my son - a geek in the making - wants XP back on. This adventure in OS choice hasn't been as bad as Vista, but it's been pretty disappointing.I feel your pain--really I do.  I am also a Systems & Network Admin at work, and the _last_ thing **I** want to do is muck-about with computer problems at home, too.  At the end of the day, and on my days off, I want to be able to sit down and just *use* the thing.

I'm running Ubuntu 9.10 Desktop (with a boat-load of server stuff added).  99-44/100% of what's on it is direct from the normal repos.  *So far* it's gone mostly painlessly for me.  Oh, there've been hiccups.  Mostly thanks to me trying to run server hardware as a desktop, and some due to (what turns out to be) typical Dell stunts.  But, all-in-all, it hasn't been too bad.  I'm seeing the light at the end of the tunnel.

For me: It's gone well enough that, were it not for the TomTom One GPS app my wife needs, I'd seriously consider putting in the effort to switch her computer over to Ubuntu Linux.  You see: Careful tho she is, and even with the measures I've implemented, it Scares The Hell Out Of Me that she's running a veritable Internet Petri Dish and does our banking and other sensitive stuff with that computer.  But she needs that TomTom desktop app, so there's nothing to be done for it.

You gotta do what you gotta do, and I, for one, don't blame you for wanting to take the easy way out and wanting to maintain peace in the household.  I'd probably do the same.

Well... unless it was the only computer in the home, and I had to use it, too.  I don't use MS-Win at work, other than in support of my job, and I will **not** use an MS-Win box at home.  Period.

Jim

---

### Post by luffy_chan_19 on 2010-01-24
> **ElSlunko said:**
> If you ever build a new PC and intend to use Ubuntu on it definitely get an NVIDIA based gpu. It'll work boatloads better and probably solve most of those issues you're having. But like most posters say, use what works best since it's the family PC. I don't bother trying to teach my girlfriend how to use Ubuntu because I know she simply doesn't care about my 'nerd' stuff ;P.
   

see this is the problem with fermales these days they dont understand our nerd qualities. they just see it as pointless technical crap that is pointless to learn., but i kinda like it that way, because who dothey call when their buff meathead guy cant fix their electronics. 
us thats who they call us, because we are the only people with the brains enough to figure this stuff out. we value simple calculations and deduction over their brawn and muscle. 


oh and to all those people who actually have those networ admin jobs or decent tech jobs i envy you, because all of my knowledge is sel;f taught by studying the CompTIA A+ linux+ network+, etc certification books. i love configuring my computer at home and when i am configuring someone elses. well of coarse i only get to troubleshoot computers when one of my friends or family recomends me to someone to fix their computer or install hardwar, software, etc. i would love to actually get some of the certifications so that i could become a systems admin.

---

### Post by Swagman on 2010-01-24
You ***DO*** realise that there are some seriously intelligent, nerdy girls on here too don't you ?

---

### Post by marin123 on 2010-01-24
so, you installed xp and now had made a whole thread about it? hey, i installed chrome the other day, but sorry, i forgot to make a new thread...
and you said you have lots of computer parts at home and you're too lazy to take 30 minutes to get one working... and you are too lazy to set up ubuntu the way it will work for you...
if you are the expert and geek you say you are, this shouldnt take you a lot of time (you say you have it on netbook, so you should know how to get it working)..
i know ubuntu is free and therefore should work better than 150 euro worth OS.. and on xp you dont have to find drivers and install them, it just appears by itself...
enjoy antiviruses and spybots, i'm taking off, going to make a thread about installing chrome...
cheers

---

### Post by Tamlynmac on 2010-01-24
To the OP:

):P

Hope you enjoy which ever OS meets your expectations. Choice, is a wonderful thing.

Since this is not a debating section of the forum (see T&E Header), I will not argue the merits of any OS or comment on your opinions.

You had the opportunity to share your experience and all that's left, is to wish you Farewell & Good Luck.

---

### Post by jrusso2 on 2010-01-24
> **Swagman said:**
> You ***DO*** realise that there are some seriously intelligent, nerdy girls on here too don't you ?

And at least one has 11 years as a system admin.

---

### Post by k64 on 2010-01-24
> **OrangeCrate said:**
> There's nothing wrong with Vista, though I'd suggest an upgrade to Windows 7 from XP. It's pretty nice, and most likely would please all involved.

That being said, I haven't been happy with 9.10 either, and rolled back to 9.04, in anticipation of the release of 10.04 in April. You might try that, if you're up to it.

[http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html](http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html)

Good luck

Oh, yeah, if you want to wipe out your hard drive! To upgrade to Windows 7 from XP, you need to do a clean install. This, besides having to pay more.

---

### Post by JoeWheeler on 2010-01-25
Hey OP!

It's a shame you don't get on with Ubuntu but I understand, I can imagine if I installed it on my home PC I think my wife would implode with confusion, moving to a new OS is always confusing especially if it keeps screwing up.

Good luck with XP!

---

### Post by Macchi on 2010-01-26
Here is another sad (and long) tale:

Rephrasing: Abandoning Ubuntu as the family OS
 
We have been forced to abandon Ubuntu Linux when four machines in our home network started to show many different kinds of problems with Karmic 9.10. Only the 8.04 LTS RAID server (the 5th machine) remained in a relatively stable state. Even after rolling back most clients to 9.04 chaos still reigned for a few weeks. I could not endure the complaints within the family and acquired five (!) Macs. This happened after almost five years with Linux and Ubuntu as the officially supported operating system in the fo tamily. 

Going back to Windows was definitely not an option and it was not possible wait for uncertain software updates on Linux. 

For the record, we are two adults and two kids, 7 & 10 years old, all having a quite good IT-literacy level. Me and my wife rely daily on computers as good tools to study, work, learn, and create. Not forgetting to mention that our news, music, video, pictures, and even the kid's homeworks from school are also somewhat dependent on computers.

It feelt bad leaving Ubuntu. But on the other hand now we are in the particular segment of the market where installing a computer is equal to plugging in the power cable to the mains. Everything just works. 
Usability is excellent and I really hope that many Linux developers will take a close look at the Mac OS X as inspiration on how to simplify things for the end-user.

---

### Post by Methuselah on 2010-01-26
> **Macchi said:**
> Here is another sad (and long) tale:

Rephrasing: Abandoning Ubuntu as the family OS
 
We have been forced to abandon Ubuntu Linux when four machines in our home network started to show many different kinds of problems with Karmic 9.10. Only the 8.04 LTS RAID server (the 5th machine) remained in a relatively stable state. Even after rolling back most clients to 9.04 chaos still reigned for a few weeks. I could not endure the complaints within the family and acquired five (!) Macs. This happened after almost five years with Linux and Ubuntu as the officially supported operating system in the fo tamily. 

Going back to Windows was definitely not an option and it was not possible wait for uncertain software updates on Linux. 

For the record, we are two adults and two kids, 7 & 10 years old, all having a quite good IT-literacy level. Me and my wife rely daily on computers as good tools to study, work, learn, and create. Not forgetting to mention that our news, music, video, pictures, and even the kid's homeworks from school are also somewhat dependent on computers.


9.10 was a bit too 'cutting edge' for its own use in some instances.
When it works well it is a joy but if you have bad luck with it you'll wonder how it ever made it out of the gate.

> 
It feelt bad leaving Ubuntu. But on the other hand now we are in the particular segment of the market where installing a computer is equal to plugging in the power cable to the mains. Everything just works. 
Usability is excellent and I really hope that many Linux developers will take a close look at the Mac OS X as inspiration on how to simplify things for the end-user.

If Ubuntu only had to work on Canonical sanctioned hardware and if they stipulated that is was ILLEGAL for you to install it on anything else I guarantee you things would be just as 'plug and play'.
But that's not how it works, people install Ubuntu on any old junk they have lying around that was previously running Windows or MacOS etc.
I would not want it any different but the result is a tremendous amount of variability in hardware configurations which probably accounts for 90% of the problems people face.

Apple controls the hardware platform and this is a big factor in how use of Macs appear to be so seamless in comparison with everything else.
The disadvantage is that you are pretty much locked into a hardware supplier and their devices are a bit more expensive than necessary sometimes.

I think a key distinction is that people do not usually buy Ubuntu preinstalled and so inherit the burden of making sure their harwdrae is supported.
I like that freedom but I guess it comes with a potential cost.

---

### Post by luffy_chan_19 on 2010-01-26
> **marin123 said:**
> so, you installed xp and now had made a whole thread about it? hey, i installed chrome the other day, but sorry, i forgot to make a new thread...
and you said you have lots of computer parts at home and you're too lazy to take 30 minutes to get one working... and you are too lazy to set up ubuntu the way it will work for you...
if you are the expert and geek you say you are, this shouldnt take you a lot of time (you say you have it on netbook, so you should know how to get it working)..
i know ubuntu is free and therefore should work better than 150 euro worth OS.. and on xp you dont have to find drivers and install them, it just appears by itself...
enjoy antiviruses and spybots, i'm taking off, going to make a thread about installing chrome...
cheers
 

actually even for some people including me depending on the day and the mood you are in it could take from an hour and a half to 2 hours to fully customise an xp machine.  and as for drivers, certain video and sound drivers do not just automatically install with xp. when i did a fresh install on one of my systems of xp (e machines peice of crap) i had to go to the motherboards manufacturer;s site to download the chipset drivers. it took me about 3 and a half 4 minutes to do this, by looking at the motherboard to determine the model of motherboard etc. im just saying sometimes it takes longer than to just install windows xp to get a system running. and this is why i prefer ubuntu. when i installed ubuntu on the same system, i did not have to install the drivers for the onboard sound, it did it automatically.

---

### Post by texaswriter on 2010-01-26
I find it a bit hard to believe ethat people who have been using Linux for 5+ years [or 10 years] and not being able to configure there way out of seriously easy problems. Or 5 years and have to resort to metaphors to describe their problems... 
 
I've used Linux for less than a year and let me list some of my accomplishments so far: 

1) Every modern PC game I own I have gotten working on Debian Lenny and/or Ubuntu Jaunty WITH an ATI card on the Lenny box and an Intel GMA 4500HD on the Jaunty [now Karmic] box... Most with max settings and/or no or little problems affecting gameplay. 

2) On a separate machine, set up an FTP server... 

3) Installed dual operating systems on my laptop [Karmic and Windows 7].
 
4) Custom compiled dozens of programs [some very lengthy... with even lengthier instructions :( ]

5) Troubleshooted hardware driver issues... [this considerably more with Linux community support... thanks] 
 
So, I wouldn't let an ATi card problem be an excuse... FWIW, I have the same problem when trying to have multiple users logged in too [might be a problem with the ATi card.. though haven't tried it since compiling ATI drivers from their website].  If I want to switch to another user, I just log out and log in as the new user... quick and painless. 
 
Typically, hardware works very well out of the box. If you don't have bleeding edge hardware, you are pretty much in luck. I personally wouldn't boot up to a newer operating system on an older computer... I have an older version of Ubuntu Server on the Pentium 3 that I use for a file server. It works great... That computer will never get a newer operating system until I can be guaranteed that all the hardware will be supported. 

Obviously it is your choice of an OS, I think that's what Ubuntu and Linux is all about: providing an alternative. Microsoft works very hard to force people to use their [insert product here] in a way that precludes anybody else from competing or providing an alternative. 

Best of luck wherever you go and whatever you choose, and I hope you don't give up that easily elsewhere in your life

---

### Post by Macchi on 2010-01-27
> [texaswriter]("http://ubuntuforums.org/showpost.php?p=8729388&postcount=29"): I find it a bit hard to believe ethat people who have been using Linux for 5+ years [or 10 years] and not being able to configure there way out of seriously easy problems. Or 5 years and have to resort to metaphors to describe their problems...

Yes TexasWriter, believe it or not, despite having a quite good experience in the practical applications of Linux I did not have time to fix MANY >10 machines failing in different ways. I have approximately 12 experimental desktops and laptops with linux both at work and at home.
Upon multiple failures and complaints there was no time to fix the mess, I just had to act!

Within my role as IT-manager for a few small and medium organizations, I try to promote the integration of stable open source software solutions into some practical applications for business enterprises. 

At home, my shortcut for minimizing the complaints was to trow away  the Linux machines and bring in the Macs. 

The REAL challenge is that after these problems with the 2009 releases, I am about to miss the opportunity to influence some commercial organizations that would be willing to work with Linux. This means that approx 50 machines may be upgraded to new versions of Win instead of migrating to Linux. THIS is really sad!

A sample of the problems described by my experimental users are many difficulties and lock-ups related to Login, User Switching, Hibernate+Suspend, and file sharing problems with Mac and Windows (File sharing worked better before,  I did not have time to investigate why it fails). There were also problems with graphics and wireless cards/adapters on laptops, in many cases on hardware that worked before. It is bad that the quest for extra functionality and compatibility with some of the latest versions bewitched us to upgrade. 

On the positive side, 3 fileservers etc with LTS survived and other 3 experimental webservers could be simply reinstalled. All these experiences covered not only 9.10 but actually combine the experiences and expectations raising from 8.04 LTS that did not give us a return by the end of 2009.


It is my personal opinion that a more strict hardware certification program for Ubuntu, combined with a simplification of  the user interface solutions would provide a very competitive system to the market. Despite this, the biggest challenges for Linux are probably on achieving a better communications with the market and understanding the psychological mechanisms of resistance to change.

---

### Post by lordbushbaron on 2010-01-27
I have to agree with the original post, 9.04 was much better as an OS than 9.10.  9.10 seems to be Uuu-but-not-so-boot-to's OS.  I am not happy.  I loaned out my 9.04 disk and it never came back-and they don't offer that version to download.  I may go back to XP as well, at least until they find the bugs in Win's7.  I have tried other versions of Linux, I generally love Ubuntu's  OS, just not this one. This version is roadkill.  I have a generally fast system 2G RAM 1.5G processor, but this OS runs like somebodies granny, with *Emphysema*,  up an ant hill.  Wine is so slow... Where did you find the wino to model this after?  Mozilla 3.5 crashes so much I think they should enter it in a demolition derby.  None of the other browsers run worth a crap. Going in to make changes in a terminal is either TERMINAL or not working-at all.  Sad to say, Ubuntu, You let us down in a bad way.  Many of us cannot afford to be trendy and buy new computers-make the OS more backward convertible or make past working versions available.

---

### Post by Bartender on 2010-01-27
> **lordbushbaron said:**
> I loaned out my 9.04 disk and it never came back-and they don't offer that version to download.

?????  You didn't look very hard.  I just downloaded 9.04 a coupla days ago.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by malspa on 2010-01-27
> **lordbushbaron said:**
> Many of us cannot afford to be trendy and buy new computers-make the OS more backward convertible or make past working versions available.

I would be very happy if more distros took this approach.

---

### Post by Tamlynmac on 2010-01-27
I struggle understanding why some make the upgrade process so complex. I use a spare HDD for testing purposes (on numerous systems) of new releases and/or questionable updates. I purchased a used spare HDD for very little capital and have used it to test multiple releases prior to commitment.

Upgrading is a choice and It really doesn't need to be a complicated or costly one. A simple testing procedure and a used HDD has reduced the process down to a go - no go solution. We have 4 systems all running Ubuntu and all are tested prior to upgrade. This solves the issue of stability, should a new release fail to function or improve system performance - it's not installed on the primary HDD. Wow, a tough decision... ;)

Why, blindly install a new release when such a procedure would eliminate associated risks and/or frustrations. Guess I'll never understand the logic behind not testing and then ranting. I'm still using 9.04 on this system - wonder why? I'm not debating, just suggesting an alternative to blind assumption. Since the OS is free, it seems illogical to rant or complain when one doesn't need to stand in line waiting for a refund.

Perhaps, some prefer the challenge and excitement of installing a new release without testing. But then why rant and complain should the challenge exceed their or their systems capabilities. If one's not satisfied with the OS, then might I suggest they use an alternative. One of (IMHO) the true benefits of Ubuntu - free to download, install, update/upgrade and use. Isn't freedom of choice a wonderful thing? I'm certain that some will argue that the upgrade process should work on all systems and all hardware - good luck with that.

* I will not argue or respond to any posts that wish to debate my opinions/experiences. As this section of the forum is not for debating purposes - as stated in the T&E header. :-k

---

### Post by doublewitt on 2010-01-27
Take a look at this:
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by texaswriter on 2010-01-27
> **Macchi said:**
> Yes TexasWriter, believe it or not, despite having a quite good experience in the practical applications of Linux I did not have time to fix MANY >10 machines failing in different ways. I have approximately 12 experimental desktops and laptops with linux both at work and at home.
Upon multiple failures and complaints there was no time to fix the mess, I just had to act!

Within my role as IT-manager for a few small and medium organizations, I try to promote the integration of stable open source software solutions into some practical applications for business enterprises. 

At home, my shortcut for minimizing the complaints was to trow away  the Linux machines and bring in the Macs. 

The REAL challenge is that after these problems with the 2009 releases, I am about to miss the opportunity to influence some commercial organizations that would be willing to work with Linux. This means that approx 50 machines may be upgraded to new versions of Win instead of migrating to Linux. THIS is really sad!

A sample of the problems described by my experimental users are many difficulties and lock-ups related to Login, User Switching, Hibernate+Suspend, and file sharing problems with Mac and Windows (File sharing worked better before,  I did not have time to investigate why it fails). There were also problems with graphics and wireless cards/adapters on laptops, in many cases on hardware that worked before. It is bad that the quest for extra functionality and compatibility with some of the latest versions bewitched us to upgrade. 

On the positive side, 3 fileservers etc with LTS survived and other 3 experimental webservers could be simply reinstalled. All these experiences covered not only 9.10 but actually combine the experiences and expectations raising from 8.04 LTS that did not give us a return by the end of 2009.


It is my personal opinion that a more strict hardware certification program for Ubuntu, combined with a simplification of  the user interface solutions would provide a very competitive system to the market. Despite this, the biggest challenges for Linux are probably on achieving a better communications with the market and understanding the psychological mechanisms of resistance to change.

OK, you have 50+ machines that WORK, why would you change that. The ONLY reason I update operating systems is to get some piece of hardware that **doesn't work** to work. AKA, I have a laptop from Dell that came pre-installed with Ubuntu Jaunty 9.04. Over Xmas, I started planning for getting a Wacom tablet that I knew was **very new. **So I upgraded to Karmic then... Didn't like it, well actually it had really bad support [at the time] for my graphics card [made simple 2d things lag really bad... at least with what was installed {compiz I think}]... So, I ended up trying Sidux after that... Sidux was very hard to get my wifi working [kinda important at school]...once again, a relatively new device. But I did initially get it going... and it had great support for my card... unfortunately didn't help me anymore with my **new hardware. **

As of now, I have the wifi card working and the wacom tablet working in Ubuntu Karmic, and somehow, 2 weeks later Karmic has even better support for my intel gma card then even Jaunty did... 

Anyways, the point I want to make is this: I was satisfied with Ubuntu Jaunty before... it came on a livecd that was customized with drivers for that laptop... more or less, it fulfilled all of its expectations without driver problems... The only reason I had to change was to get that tablet working because it was going to fundamentally change how I used that laptop. That was what required a newer operating system... 

So, I ask you: why would put a new operating system on old computers that work... The released LTS' DO cover until a new LTS is released... probably even a little overlap to account for bad release.. As soon as the next LTS supports my WACOM tablet, I'm upgrading and that will get left alone for the rest of the life of the laptop. Same with my Desktop, has Lenny and will stay that way until I do a full upgrade of its hardware [new cpu, mobo, memory, etc]... 

And MACS? Really, do you really want to spend that much more for a computer that runs a fundamentally neglible amount of programs. I mean Linux distro's have **huge** repositories. Windows has even more programs available. Mac has like less than 1% of the programs available on Windows... All I can say is this: they are pretty and they cost alot... That's it... Not even nicer than Compiz-Fusion... And although they have a version of WINE [and even Crossover], there is still considerably less native software for that os... 

I can definitely understand frustration, having experienced that getting programs and hardware to work, but I had more frustration with Windows problems, and anger when there was **no** way to customize a feature. With Mac, if there's not a feature in the operating system or not a way to change something, that's Apple's way of telling you **you do not need it**. Even more closed than Windows.  
 
Just can't understand why somebody would change something that worked. Sounds so ridiculous to hear from an IT guy that managed these computers for years with Linux.

---

### Post by malspa on 2010-01-27
> **Tamlynmac said:**
> I struggle understanding why some make the upgrade process so complex. I use a spare HDD for testing purposes (on numerous systems) of new releases and/or questionable updates.

This is a good idea. I normally try out new installations on a different set of partitions while keeping the old system in place.  Sometimes it's on the same hard drive as the old system, sometimes it's on a 2nd drive.  (Either way, I back up the old system before I do anything.) I find it helpful to be able to go back and forth between the old one and the new one, for comparison purposes, while I'm testing out the new system.

No matter which way you go about it, I have to agree with this point:


> **Tamlynmac said:**
> Why, blindly install a new release when such a procedure would eliminate associated risks and/or frustrations. Guess I'll never understand the logic behind not testing and then ranting.

---

### Post by steveneddy on 2010-01-27
> **Macchi said:**
> Here is another sad (and long) tale:

Rephrasing: Abandoning Ubuntu as the family OS
 
We have been forced to abandon Ubuntu Linux when four machines in our home network started to show many different kinds of problems with Karmic 9.10. Only the 8.04 LTS RAID server (the 5th machine) remained in a relatively stable state. Even after rolling back most clients to 9.04 chaos still reigned for a few weeks. I could not endure the complaints within the family and acquired five (!) Macs. This happened after almost five years with Linux and Ubuntu as the officially supported operating system in the fo tamily. 

Going back to Windows was definitely not an option and it was not possible wait for uncertain software updates on Linux. 

For the record, we are two adults and two kids, 7 & 10 years old, all having a quite good IT-literacy level. Me and my wife rely daily on computers as good tools to study, work, learn, and create. Not forgetting to mention that our news, music, video, pictures, and even the kid's homeworks from school are also somewhat dependent on computers.

It feelt bad leaving Ubuntu. But on the other hand now we are in the particular segment of the market where installing a computer is equal to plugging in the power cable to the mains. Everything just works. 
Usability is excellent and I really hope that many Linux developers will take a close look at the Mac OS X as inspiration on how to simplify things for the end-user.

So, basically, what you are trying to tell us is that you used poor judgement in installing and using the **bleeding edge version** of Ubuntu instead of the **LTS version** for stability (because I believe that was the emphasis of your post) and spend a maddening amount of money due to the fact that you didn't use common judgement in what operating system you would use for your family.

Nice.

---

### Post by k64 on 2010-01-27
> **hoki_goujons said:**
> Wow, all these replies I didn't get notified about :D

I considered trying Kubuntu, but all the 'buntus have outworn their welcome here - my missus just wants her familiar stuff back, and even I'm sick of it.

I'm aware that Nvidia is more suited to Linux - it's always been the case since I started messing about with it 9 years or so back.

Just so you know where I'm coming from with this:

A couple of years ago I got bored of messing about with computers at home. I work with computers (digital forensics) for a living and used to find the constant tinkering fun, but now I just want stability and ease of use. I'd always built my own PCs and a had half a dozen cannibalised ones clutttering up the house, but it came time to build a new family one and speccing it up component by component just didn't appeal any more, so I went to Dell and spent 20 minutes choosing one, and felt very happy with it.
It's done very well, the only change I've made to it being replacing Vista with XP.  The video card was absolutely fine for my needs under XP. I suppose that the urge to tinker hadn't completely died in me though, because I started wondering about how well the family would do with Ubuntu - as I said, I use it on my netbook and a couple of machines in work, and I'm a big fan of it.


To K7522 - if you read my original post, I did install the restricted drivers for the ATI card but they meant that I couldn't do user switching - which is a bit of a showstopper in our house.

To Swagman - solving the user switching problem by buying 2 new computers is hilarious. Likewise, blaming the card for the lack of support doesn't really wash with me - I'm at the stage at home now where I don't want to be doing any 'helpdesk' duties at all, ever. These days, I want to be a user at home, not an admin - I don't care if the problem is with ATI not releasing decent drivers, or with Ubuntu not understanding the card, or the pixies sprinkling too much magic dust on the PCB. 

I want to install the OS on my generic, mass-market hardware, and I want it to work for me. XP, on this computer, does this a lot better than Ubuntu does. There have been times when Ubuntu has done it better - my work Acer Ferrari laptop takes about 2 days to get up and running with XP 64bit. Doing it on 64bit Ubuntu takes about 20 minutes from putting the CD in to logging on, and it works beautifully. My philosophy is that all software is fundamentally crap. The challenge is to find something that's un-crap enough to let you do what you want to do.

Have you tried Mint? See if your computer will support it as well as fast user switching. What model ATI card do you have? It works for me on the HD 2400 Pro and Ubuntu Lucid Lynx Alpha 2.

---

### Post by texaswriter on 2010-01-28
> **k64 said:**
> Have you tried Mint? See if your computer will support it as well as fast user switching. What model ATI card do you have? It works for me on the HD 2400 Pro and Ubuntu Lucid Lynx Alpha 2.

Ubuntu Lucid Lynx Alpha 2, heh, you **are brave!!!*****[B] :popcorn::KS**[/B]*

---

### Post by caravel on 2010-01-28
> **Macchi said:**
> Here is another sad (and long) tale... ...We have been forced to abandon Ubuntu Linux... ...I could not endure the complaints within the family and **acquired five (!) Macs**. 
My heart bleeds for you... no really.

:rolleyes:

---

### Post by kidux on 2010-01-28
I'm in the exact opposite boat. My wife became so fed up with the issues indicative of WinME, she got to the point of completely refusing to use our computer at home until I "fixed" the problems. At that point, my options were to either "up"grade to 98SE, buy a mac, or look into Linux. I didn't have a 98SE disc, nor was I willing to spend the money on it or a Mac, so I looked into Linux. We started with Red Hat, but didn't care much for it, but Slackware fit the bill nicely. 

For about 10 years now we have been an all Linux household, currently using Ubuntu 8.04 on the home server/general use machine, and Kubuntu 9.10 on our laptop, with Edubuntu 8.04 on our son's machine. She hates the fact that she is forced to use MS products at work, and wishes they would fo to *buntu. And for the record, she is not a techie by any sense of the word, but is able to do everything she needs to on our home machines.

---

### Post by Macchi on 2010-01-28
Stevenddy made some comments on my story:
> **steveneddy said:**
> So, basically, what you are trying to tell us is that you used poor judgement in installing and using the **bleeding edge version** of Ubuntu instead of the **LTS version** for stability (because I believe that was the emphasis of your post) and spend a maddening amount of money due to the fact that you didn't use common judgement in what operating system you would use for your family.

Nice.

Yes, I agree that I should have been more careful with the risks of upgrading several machines. We know about Murphy's Law and it would have been safer only to rely on the Long Term Support release (as I did for the servers!). 

Just blame me, or not. But you should agree that there is a classic dilemma on choosing between the latest release with bugs or the stable release with limited functionality. This can be a difficult choice even for experienced engineers.




PS: By the way, I was not primarily talking about the money involved. This is certainly controversial, but if accounting for time spent around installation, support, and maintenance, then Windows is the most expensive operating system, Linux would take second place, and Mac OS X would be the cheapest. Despite the clear premium markup on Apple HW. The so called real cost depends on what you want to account for.  At last I wish to mention that on commercial and professional applications I always try to add a bias towards the high value advantages of open source solutions.

---

### Post by texaswriter on 2010-01-28
Macchi> Your last post did hit on something *real* important. Mac's are "customized" in such a way so that there is considerably less you can do to them, even less so when you actually consider Apple's user base expects everything handed to them. Windows are somewhat beyond this, though you find just as helpless users, the average PC user prolly knows more about changing settings and fine tuning things than the Mac user. Obviously using Linux is a learning curve, but once you get used to it this proves that you had the desire and the willingness [and hence the need] to do so. This kind of precludes going to another operatoing system with less availability of customization. That said, there I've spent days in Windows OS trying to get this or that to work to my satsisfaction and often result in failure because of my inability to change a particular setting or system attribute. With so many settings hidden in the registry, the few programs or scripts that change this or that is nothing compared to the real power of registry tweaking in Windows... I don't think there is even anything such as that in Mac... At least hypothetically, if you knew enough, you could customize a GREAT DEAL of things in Windows with the registry, but MS has always associated this taboo with playing with the registry, leaving people left to follow unofficial []...  
 
Anyways, I could never recommend to people that they buy a Mac, twice as much, a relatively neglible amount of software... TCO is very relative to the user and their needs. If you must know, for a *basic user* which fits the bill for most people who just want to turn it on and for it to work, Ubuntu works very nicely just out of the LiveCD... Installing it you get even more performance. If you never do bleeding edge, or intense graphics, Ubuntu does a clean install on every machine I've ever put it on from a Pentium III to a Core 2 Duo... Old hardware always works plenty fine. Newest hardware is occasionally a trouble, but not necessarily so.. So, TCO for the average user could be neglible if they didn't just listen to the rhetoric in the marketplace. 

If you have the kind of money to throw on 5 macs, heh, good for you, that's quite an investment... 

FWIW for anybody looking at TCO, I spend about $1000 per 5 years on my main home computer. That keeps it new enough to play th emajority of new games **throughout **that five years. That includes a new mobo and 1 or 2 sticks of newer/replacement memory in that timeframe. 

For example, I have the option of upgrading just my CPU, mobo, and memory in the next "iteration"... If I chose that least cost method, I could get a quad core or better plus a ton of ram for around $300... That configuration, since quad-core mobo's are already revised [as in not brand new... psst me if you want a further explanation of that] will in all likelihood not need to be upgraded midway though the next 5 years... just possibly needing more RAM / newer RAM. That presents a very interesting picture of affordability. Throwing in an operating system or two purchase in that same time frame would affect the bottom line considerably. I mean, take Vista, if you don't get the middle of the tier OS from them, you **actually got an OS that was disabled**; Windows 7 uses the same format... That means, just to have an OS that doesn't make your system slower/worse, you have to spend $200-$300 [OUCH].  In my little comparison there, that's 50%-100% above what I would've paid. On a Mac if I had a 5 year old computer my upgrade options **would have** been neglible... I'm not sure how upgradeable current ones are... I don't think you can install Mac OS X on just any Intel [unless u have special haxing skills].  That would suggest that you have to get **special **hardware [i.e. same thing as rest but more expensive]...  
 
So, if you have no problem custom building your computer, you can get top of the line hardware for bottom of the barrel prices. 

TCO = Linux:popcorn::KS:p:D for those who have the computer building / maintenance skills necessary.

---

### Post by clbaines on 2010-01-28
I am not going to abandon Ubuntu. However, I say "amen brother" to not wanting to 
tinker anymore. I will do a little but not much.

---

### Post by danilius on 2010-02-01
I have three laptops with Karmic installed: a Toshiba Tecra, an ancient Compaq and a Alienware mx15. The ancient Compaq is used by the kids for educational play. Installation of Karmic was a breeze. It simply works, day in day out. Likewise for the Toshiba, a few clicks and everything was running fine. 

It's worth pointing out, though, that on the Toshiba and Alienare, 64-bit Karmic was a disaster and rapidly got dumped.

On the Alienware, the experience has slowly degraded. The processor does not appear to be fully supported. The virtual terminals have now became garbled. I could live with that. But now the hibernation no longer functions. Video tears. 

So I've installed installed VirtualBox on Windows 7 and am using Ubuntu that way. On my other laptops, I hardly boot into Windows, because I am far more productive on Ubuntu.

The point of this comment is that even techies with years of professional computing experience like myself are finding the fiddling that Ubuntu can require at times a little tedious. And when the system breaks from one update to another, one has to ask the obvious: why break it if it works?

---

### Post by texaswriter on 2010-02-01
As far as the 9.04 vs 9.10 discussion (etcetera) if you have an old computer and are satisfied, why change.  As far as I am concerned, so long as an LTS is supported, it is good to go. My file server, old computer, P3 old Ubuntu version... Hardy Heron. I might play with upgrading that to Lucid, but only cuz it's the next LTS. If Lucid doesn't do anything for my school laptop, Karmic will stay.. These are all intended to be examples of the practicality of upgrading or not. You don't just have to arbitrarily upgrade just because a new versiion comes out.

---

### Post by kidux on 2010-02-02
> **danilius said:**
> *snip*

The point of this comment is that even techies with years of professional computing experience like myself are finding the fiddling that Ubuntu can require at times a little tedious. And when the system breaks from one update to another, one has to ask the obvious: why break it if it works?

I've brought this up before, but it still amazes me that people seem to just blindly install updates. Whenever I update, I check each one out before installing, to see if there are noted bugs, and even then I usually only update if it's a critical update, or something that adds needed functionality. This should be done even on Windows. I don't update as soon as they're available either, but wait a week or so just to make sure it's not going to cause issues. Seems simple enough to me, and I've never had an issue. I've been a Linux user for almost 10 years now.

---

### Post by Macchi on 2010-02-02
> **kidux said:**
> I've brought this up before, but it still amazes me that people seem to just blindly install updates. Whenever I update, I check each one out before installing, to see if there are noted bugs, 
... (stuff deleted)


Well Kidux, my personal and professional experience is that there is a trade-off on every software update or upgrade.
The dilemma is between the NEED for new functionality and FEAR for a higher probability of problems. The application of security patches may also fall in a similar category, since according to the infamous Murphy´s law every change may imply in a risk of crashing the system.

If important basic functionality is not working then I tend to go for the upgrades on laptops and desktops - as a last resort. From 5.04 until 9.04 my subjective experience was that I got more advantages than disadvantages with upgrading (always clean installs). But 9.10 was unfortunately an exception to that rule and "suddenly" I had not one but a dozen of experimental Ubuntu laptops and desktops with diverse problems. Users got quite irritated and you can guess that I was the nearest target to blame.

PS: Yes I have a rollback scheme with separate homes and backups but I have no automatic tools like a time capsule an auto restore. Thus rollback requires a lot of work on Ubuntu. 
A very strick policy around LTS and standard hardware is the only way to for me if I am going to succeed on converting some organizations to GNU/Linux. Professionally I will have to wait for 10.04 and then test it, thus closing the possibilities to deliver anything before 2010-Q4.

---

### Post by mastablasta on 2010-02-02
Ok if you had problems and if there is solution but would take too long to find wouldn't it be cheaper/more cost effective to pay for Canonical support than buy all those Macs?

---

### Post by danilius on 2010-02-03
Kidux, I do not want to spend significant amounts of my time researching every possible update. Outside of computing and work I actually have a real life.

Now, granted that the complexity of any core update (i.e. anything the system can't really function properly without) is far more complex than updating Thunderbird, for argument's sake, due to the vast array of hardware a given update has to take into consideration.

Granted, too, that I have not paid a penny for the OS either.

I am not moaning about the efforts of all involved. Far from it. What I think this thread is really about is that some decisions being made are quite baffling, and end in even experienced users getting frustrated, but never ungrateful.

For Ubuntu to go mainstream, this sort of experience has to change. We moaners are simply providing the essential feedback to make this possible as opposed to looking for advice that we are fully aware of anyway.

---

### Post by malspa on 2010-02-03
> **danilius said:**
> Kidux, I do not want to spend significant amounts of my time researching every possible update. Outside of computing and work I actually have a real life. [...] For Ubuntu to go mainstream, this sort of experience has to change. We moaners are simply providing the essential feedback to make this possible as opposed to looking for advice that we are fully aware of anyway.

> **kidux said:**
> I've brought this up before, but it still amazes me that people seem to just blindly install updates. Whenever I update, I check each one out before installing, to see if there are noted bugs, and even then I usually only update if it's a critical update, or something that adds needed functionality. This should be done even on Windows. I don't update as soon as they're available either, but wait a week or so just to make sure it's not going to cause issues. Seems simple enough to me, and I've never had an issue. I've been a Linux user for almost 10 years now.

LOL!  I sorta take kidux' approach, too, and I did the same when I used Windows.  And I actually have a real life, too!  I can't say that I closely examine each update, but I do kind of take a look before I update something, and I don't blindly do all of the updates available.  Or, at least I didn't when it I used Windows, and I don't with Ubuntu and Mint.  As I did with Windows, in Ubuntu and Mint I don't even bring in most of the available updates.  As kidux said, "I usually only update if it's a critical update, or something that adds needed functionality."

With Mepis and Debian Stable, I feel more comfortable doing all of the updates without worrying, although I keep an eye out for potential problems at the Mepis forums.  I'm not very diligent about that.  With those two distros, I usually just update everything that comes down the pipe in Synaptic.

I don't know if this is going to sound like a knock on Ubuntu and Mint -- I do love both distros -- but I personally don't feel as comfortable pulling in all of the updates with those two distros as I do with Mepis and Debian Stable.

I understand that many people just want a situation where they don't have to worry about updates wrecking anything.  But really I think it's good to keep an eye on things like that no matter what OS you're using.

One thing that I'd like to add here: Some of my machines came with Linux preinstalled, and I've had very few problems with most of the distros that I've thrown at them.  Seems to me that a lot of the problems people have come from the fact that we're putting Linux on machines that were made for Windows.  I am wondering how folks like the OP and danilius would experience things if they started out with a machine like that, that was actually built for Linux, sort of like you do when you buy a Windows computer.  I think it might be a much more pleasant Linux experience, if things went the way they have gone here so far.  My $.02.

---

### Post by texaswriter on 2010-02-03
> **danilius said:**
> Kidux, I do not want to spend significant amounts of my time researching every possible update. Outside of computing and work I actually have a real life.

That is certainly understood. Please understand most of the posts in this thread are a **specific **response to people who updated their os at a time when they did not need to. As in, they were using an LTS that was still supported and they DID NOT upgrade their hardware... Plain and simple, that's fixing something that's not broken. Both of these people are self-described as having worked with many linux boxes for a long time. So, in that context, those people really weren't acting with anything described as wisdom. The same thing goes for any operating system. Try putting Vista or 7 on your old boxes. 

**IF IT IS NOT BROKEN DO NOT FIX IT!!!!!!!!!!**

That should be in 100 pt size font... Times New Roman, God Font, a hand should materialize out of space and right those words in fire... 

> Now, granted that the complexity of any core update (i.e. anything the system can't really function properly without) is far more complex than updating Thunderbird, for argument's sake, due to the vast array of hardware a given update has to take into consideration.

OK, yes, a system upgrade is different than a program upgrade. 

> For Ubuntu to go mainstream, this sort of experience has to change. We moaners are simply providing the essential feedback to make this possible as opposed to looking for advice that we are fully aware of anyway.

Let's talk about that: For Microsoft to **be **mainstream that sort of experience should not be the same. I mean, what was Vista. Vista was MS telling anybody with hardware 3-5 years old + to throw it out the Window, that it's all garbage. People think Windows 7 is so great, only because of how much Vista sucked. Vista executed programs slower than XP, it lagged like crazy, and it had more bugs than you could shake a stick at. Windows 7 is more comparable to Vista vlited than anything [if you are familiar with what v-lite was]. I don't think Windows 7 has the file copying errors, but I won't laud that: an os should NEVER have problems doing simple file copying/moving when there is no problem with the hardware. Otherwise, Windows 7 does not execute code much [if any] faster than Vista... 

There are certainly good things to say about Vista and 7, actually lots of good things, from XP, but my only point is that putting Vistsa on an old box would have broken it impossibly. 

At the **very **least, if you install Karmic on even a 5-10 year old computer, if hardware doesn't work, there are things you can do without the manufacturer having to rewrite drivers for it. When MS threw Vista out to the masses, if your hardware didn't work, you had to wait for the manufacturer to make drivers or use compatibility drivers [if possible]... 

So, once again, I want to say

[SIZE=5][B]DO NOT FIX IT IF IT IS NOT BROKEN!!!

[/B][SIZE=1]That's what I would like to get across to the people who started this thread. 

[/SIZE][/SIZE]
[SIZE=5][SIZE=1]Otherwise, I will voice my opinions, good or bad, as well. So, in that respect, you are correct: Feedback is very necessary. 


[/SIZE][/SIZE]

---

### Post by Macchi on 2010-02-04
I will try to summarize what I have perceived on this thread so far:

A few people on this thread have reported their temporarily negative experiences with the later releases of Ubuntu. Eventually some of them even admitted to have switched to other OS or distros. One individual (myself!) reported being forced towards multiple Macs in the family after diverse failures of desktops and laptops.  
There have been some discussions on suitable/unsuitable hardware as the cause of problems. Some people claim that these problems have trivial solutions.

The discussion seem to be strongly polarized either around people that have experienced diverse problems and wish improvements and another group that blame those users from the first group for creating the problems themselves.




NOW BACK TO SOME OF MY OPINIONS AND SUGGESTIONS:
As long as the discussion keeps this pattern there will be no closure nor agreement. 
Perhaps many of us agree can that frequent software updates can be both good AND bad:  

1) We may HAVE TO UPDATE & UPGRADE to fix problems or get required functionality. 

And 

2) We sometimes SHOULD NOT UPDATE/nor UPGRADE in order to minimize the risks of less mature software.


Unfortunately there is no simple solution to this dilemma and reality is seldom either black or white. Some things will work fine but other things might be broken after installation on non-customized hardware.

I believe that a more conservative attitude towards updates on mainstream Ubuntu could be favorable for many many users. Perhaps not so conservative as Debian because then the evolution slows down too much.  
Experienced users may still keep on the bleeding edge because they will find the alfas, betas, and RCs.

Less experienced users can start with vanilla releases. Upon eventual panic they should try the LTS releases.
For small office/home office users we could have a much stronger recommendation towards only using LTS releases.

... just a few thoughts.

---

### Post by kidux on 2010-02-04
> **danilius said:**
> Kidux, I do not want to spend significant amounts of my time researching every possible update. Outside of computing and work I actually have a real life.

Now, granted that the complexity of any core update (i.e. anything the system can't really function properly without) is far more complex than updating Thunderbird, for argument's sake, due to the vast array of hardware a given update has to take into consideration.

Granted, too, that I have not paid a penny for the OS either.

I am not moaning about the efforts of all involved. Far from it. What I think this thread is really about is that some decisions being made are quite baffling, and end in even experienced users getting frustrated, but never ungrateful.

For Ubuntu to go mainstream, this sort of experience has to change. We moaners are simply providing the essential feedback to make this possible as opposed to looking for advice that we are fully aware of anyway.

Actually, it takes very little time to do. 15 min most of the time, to scan through the updates available, then check them on the web, before just installing the ones I need. I'm a soldier currently deployed to Afghanistan, so you can imagine my time is limited as is.

As far as OS upgrades go, I usually upgrade 1 release behind current, and don't notice many problems. Even so, someone not wanting to bother with fiddling with it all the time, should go with an LTS release, or perhaps Debian.

---

### Post by Poodle Doodle on 2010-03-22
Re: Shutdown, Logout, Restart ... 60 sec time

Me thinks the 60 second off cycle is too long.


Me thinks OFF means OFF and not "In a little while".



As in 44 magnum hand gun into Toyota Prius engine block, via the dash board and CPU.

"When I say stop, I mean stop"..... "Booyah, Booyah, Booyah, Booyah"

Toyota Prius stops.


Same thing with computer.

Me thinks 5 seconds for reconsideration tops.

Anyone have THE answer to this?

---

### Post by texaswriter on 2010-03-23
Heh, Kubuntu only has a 30 second timer. :popcorn::KS:p

BTW, these people are kind of asking an unnecessary question. In any normal OS, you have to actually select the option. Even in Windows, you have to select to shut down down. 

If you want an easier way to shut down: Cntr-Alt-Del  Down-Arrow Enter. This [in Kubuntu] results in shutting down NOW!!!

teehee, even tested it after i posted here. In Ubuntu it should work just the same. I always use CntrAltDel to shut down, even in Windows...

---

### Post by spegru on 2010-04-06
First, Linux is not windose, so dont expect it to work exactly the same way. It does everything just fine but the key presses etc may be a little different and different systems have their own foibles
eg. Ctrl-alt-del to log into a windows domain - what the heck is that about?!

.....get over it!

Second, use the Ubuntu based Linux Mint 8. It just works with sensible (intel/ nvidia) hardware. I actually started to forget some linux skill s because of that!

Oh yes and pull out a couple of old PCs from the loft/garage whatever and install on that. (I'm still ising an 8yr old ideq - try that with the latest m$ft!). You will find the extra PCs far more useful.

I agree, this was a drive-by troll, or at least someone who didnt want to try

---

### Post by Swagman on 2010-04-07
For instant off

Install Ubuntu-tweak. You can fettle lots of options with that little god-send including deleting old kernels from your grub menu (and off your machine).

My machine now shuts down instantly.

---

### Post by conryf on 2010-05-05
I can kind of understand. 

I'm taking care of my girlfriend's computer this week and she's getting windows 7. I really like Ubuntu 10.04 but the ease of use is not to her level yet. I sort of like having problems to solve now and then and the ease of getting whatever software I need with the right apt-get command means I probably won't go back, but I can understand the original poster not wanting to put his family through the ubuntu odyssey.

---

### Post by Elfy on 2010-05-05
this is old - the OP has not been back since they posted. Thread closed.

---

