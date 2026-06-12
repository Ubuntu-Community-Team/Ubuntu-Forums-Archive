---
title: "What about the practical stuff?"
date: 2022-03-14
forum: The Cafe
---

### Post by Shibblet on 2022-03-14
So, this last weekend a friend of mine asked if I would help him with his Ubuntu install, since he was having trouble getting some things working...

There were 4 major problems with his installation.

[LIST=1]
[*]Bluetooth Keyboard and Mouse.
[*]USB Speakers
[*]Video Game Controller
[*]NAS Drive
[/LIST]

[LIST=1]
[*]We could get the BT Keyboard and Mouse connected, but only after login.  So, we had to connect a USB Keyboard to login, then his BT Keyboard and Mouse would connect automatically.  I looked into adjusting the bluetooth settings to start at login, but nothing ended up working.  (Logitech K380 & Logitech Ergo M575)
[*]USB Speakers just would not do anything.  Didn't register at all.  Could not figure out why. (Cyber Acoustics Speaker Bar)
[*]Video Game Controller connected either with USB Cable or Bluetooth, but the OS didn't register that it was a controller.  (8bitdo Pro 2)
[*]Can use the web-interface, but no way to connect directly like a NAS.  Which means uploads and downloads are WAY slower than direct access. (WD MyCloudHome)
[/LIST]

Now, I am aware that most of these problems are no fault of Ubuntu, or Linux in general... but we have to understand that these issues are what cause people to not use Linux.
After hours of frustration, fidgeting, he finally said "F - it..."  He was left with no choice but to reinstall Windows 10, where all of these items that he had purchased, worked flawlessly. (Not out of the box, obviously. With driver installation and software setup.)

His exact words were "What's the point of this?  This is just stupid!  Who want's an OS that doesn't work with my stuff?  I can't really 'use' this for what I need to 'use' it for?  Can't hear anything, can't play games, and have to plug-in a keyboard just to log in.  It's ridiculous."

When people want to transition, they can be left with peripherals that no longer function "correctly," or even "at all."  And the people that attempt to transition have no way to know what kind of things they "should" have purchased in advance to ensure usability and functionality.  

What can be done to assist with this?

---

### Post by #&amp;thj^% on 2022-03-14
1st thing that comes to mind, and yes you are already aware of the fact>>>> HARDWARE HARDWARE HARDWARE they need to know this going in>> otherwise, well you just gave some excellent examples of non compatible hardware issues. That's no fun even for us old timers. And seems to be the biggest hurdle here.
I have vendors that send me 1 year old laptops, and some of them are Strictly written for windows, I then run a few linux os's for compatibility, around 80% of those work OOTB, the  written for windows lappys was then sent to various Dev's for drivers needed. Moral for myself is to inform new linux users was to check with me or forums how nicely or poorly that system ran on Linux. (Breakfast of Champions) :lolflag:

---

### Post by QIII on 2022-03-14
What can we do to assist with this?

We need to stop shooting ourselves in the foot by saying "Linux just works".  It doesn't.  It particularly doesn't with hardware for which no consideration for Linux was made by the OEM.  The newest, most bleeding edge hardware can be completely out of the question.

If their hardware is not compatible or the OEMs do not provide compatible drivers, the only help we can offer is to suggest using Windows if that works for them.  But we should also tell them that Linux does work out-of-the-box without issue for millions of people.

We should be saying "Use what works for you" more often.


An afterthought:  Those who thing Windows "just works" are missing three things:

1.  OEMs put all their efforts into making their hardware compatible with Windows.  Microsoft doesn't lift a finger.  Microsoft does not support hardware.  OEMs have to make their stuff work with Windows.  Then they have to grovel before Redmond to get their drivers into the Windows driverbase.  May the deities that be help them if they make changes that require driver changes, because the grovelling has to start anew.

2.  Software developers put all their efforts into making their software compatible with Windows.  Microsoft doesn't lift a finger.  Microsoft does not support software.  Developers have to make their stuff work with Windows.  Software developers have to grovel before Redmond to get the "Made for Windows" stamp on their software packaging.  May the deities that be help them if they make changes that might affect how the software behaves, because the grovelling has to start anew.

3.  There are Windows forums aplenty -- because Windows users also have problems.

---

### Post by lammert-nijhof on 2022-03-16
It is very simple. If the companies of new peripherals don't provide drivers for Linux, it will not work. If the hardware grows older, the chance increases, that somebody somewhere in the world did write a driver for it. 

Another story: I have an old HP C6180 "All In One" printer. HP stopped the maintenance and it stopped working with Windows. I bought it for $10 and it still works in Ubuntu with the Linux drivers :)

---

### Post by DuckHook on 2022-03-16
Seconding what QIII has already stated. I would also add the following:

We need to acknowledge that Linux is a geek's OS. Rather than keep repeating the refrain that "it works out of the box"&#8212;which, even if true for many, has enough exceptions to render this statement deeply misleading&#8212;we should be emphasizing its power, flexibility, freedom and security, but only for those willing to wrestle with its arcaneries and obscurities. If one is not prepared to deal with these things, then one should stick to Windows.

---

### Post by TheFu on 2022-03-16
We are the problem. We keep buying hardware that doesn't come with tested, validated, Linux support.  It is up to all of us. Stop doing it.

Every hardware vendor creates their drivers to work on Windows. If they didn't, wouldn't the world complain? 

We've all been burned by Windows-only hardware.  Sometimes that support eventually works, but until the vendor makes an effort for minimal Linux support, we need to stop buying their junk.

There are some very large vendors who are known to be less-than-nice towards Linux.  Logitech is one of them. In January, I bought a K845 keyboard (wired, mechanical) made by Logitech. It doesn't know how to use a USB 1.1 port going through a USB-to-ps2 adapter, so it doesn't work with my KVM switch. I contacted Logitech a few times before someone finally actually said the words - we don't support that configuration. In every other contact, they said "we don't recommend that configuration", which isn't the same.  Not recommending, doesn't mean it won't work.  I pressed about Linux and they were clear - not supported.

It was my fault for giving them money. I have the blame.

Update: I ended up replacing a 16+ yr old KVM that was working perfectly for a new 4K HDMI+USB KVM. Just need some more parts before I can swap it into use.

---

### Post by uninvolved on 2022-03-16
> **QIII said:**
> We should be saying "Use what works for you" more often.


Very much ^THIS!

Linux attracts a lot of zealots and people with some rather extreme views. Many of us think that everyone should be using GNU/Linux/FOSS, to the exclusion of everything else. 

Frankly, Linux can be difficult and just won't work on some hardware. By that same token, there's hardware that Windows will not run on.

It's like, "There is no best distro. There's just the best distro for *you*."

---

### Post by DuckHook on 2022-03-16
@Shibblet

We are all in chorus, telling you the same thing in slightly different ways.

[LIST]
[*]Ubuntu/Linux is ***NOT*** for everyone. We need to stop pretending that it is. Trying to shoehorn this geek's OS into general use is neither guaranteed nor productive. When it works, we should consider ourselves lucky and count our blessings. When it doesn't, it can be a nightmarish experience. Your friend went through the nightmare version.
[*]The fact is that Ubuntu/Linux is at the mercy of OEM vendors. We can rant and rave all we like about how unfair or shortsighted this is (with justification too), but the facts do not care about our feelings nor the state of justice in the world. If certain equipment isn't supported, then it isn't supported. Apart from TheFu's suggestion to loudly tell them that we will no longer buy their stuff, there's nuthin' you or we can do about that.
[*]We do need to ***stop*** evangelizing Linux and its distro offspring. Such proselytizing is not helpful. In fact, it is misguided. Coincidentally, I responded to a different thread a couple of days ago which dealt with exactly this same issue. At the risk of quoting myself, those thoughts are applicable in this instance too:
> **DuckHook said:**
> I've taken on the task of moving a number of users to Linux. Mine is not a statistically relevant sampling but, as far as anecdotal evidence goes, here are my experiences:

Such a move only works if the following conditions are met:

[list=1]
[*]While the user doesn't have to be technically savvy, s/he needs to at least be a technophile—someone who enjoys tech. Those who treat technology as just an unpleasant means to an end—a necessary evil—are not good candidates.
[*]The newbie cannot be using this as a production machine. If s/he relies on this for work or to make a living, then even small learning curves become anxiety or panic inducing when confronted with the pressure to grind out a result by deadline.
[*]S/he has to be willing to work with you remotely and will not wilt when confronted with the command line. It's simply a fact of Linux life that some troubleshooting cannot be done on anything other than the old terminal.
[*]Clear and realistic expectations. Support is informal: consisting of you and an eclectic community of online geeks. The ability to take his/her ire out on a support person paid to put up with abusive frustration doesn't exist.
[*]Closely related to expectations, maybe even a subset, is willingness to adapt. This I found to be the toughest one. Some people have no idea what they are really getting into when they try to jump to Linux. It's a whole different world with different apps, different norms and different philosophies. The dev is king; not the user. It's based on community and sharing; not on silos and payment. It focuses on power, flexibility, adaptability and security; not on ease of use.
[/list][/LIST]
What follows is a purely subjective personal opinion, but I'm going to chance stating in all its biased, curmudgeonly glory:

I don't want Linux to be a "popular" OS. I don't want the general public using it. The only way to bring about widespread general use would be to dumb Linux down to the point that it loses all its power, flexibility, freedom and security. That would be a disaster. Were it to happen, it would drive me use something else like BSD.

I get how arrogant that makes me sound. I get how "elitist" that is. But it's also another undeniable fact that doesn't care about hurt feelings: The only way to make something popular is to make it stupid. Linux is not stupid. So it will never be popular. Ergo, that's the way I like it and that's the way I want it to stay.

---

### Post by DuckHook on 2022-03-16
> **Shibblet said:**
> What can be done to assist with this?
It occurs to me that I did not actually answer your question. So here's my answer:

It's actually quite simple: buy Linux machines from Linux vendors. They are "guaranteed" to work in the same way that Windows OEMs "guarantee" compatibility with Windows: because they are built to be compatible in the first place.

The Linux devs have done such amazing work for so long that we overlook the fact that when we try to install Linux onto Windows machines, we are really trying to force square pegs into round holes. It is to their credit that it works as seamlessly as it usually does. But our default expectation ought to be that it won't work (without a lot of kludging and cussing) and that we are lucky when it does. The solution is not to keep making the square pegs rounder and rounder, but to buy a machine with square holes.

---

### Post by TheFu on 2022-03-16
> **DuckHook said:**
> It occurs to me that I did not actually answer your question. So here's my answer:

It's actually quite simple: buy Linux machines from Linux vendors. They are "guaranteed" to work in the same way that Windows OEMs "guarantee" compatibility with Windows: because they are built to be compatible in the first place.

The Linux devs have done such amazing work for so long that we overlook the fact that when we try to install Linux onto Windows machines, we are really trying to force square pegs into round holes. It is to their credit that it works as seamlessly as it usually does. But our default expectation ought to be that it won't work (without a lot of kludging and cussing) and that we are lucky when it does. The solution is not to keep making the square pegs rounder and rounder, but to buy a machine with square holes.

And for peripherals?

---

### Post by DuckHook on 2022-03-16
> **TheFu said:**
> And for peripherals?
I've got no solution for that one other than the one you've already mentioned: complain loudly and vehemently. Expect to be met with deaf ears.

A few other methods:

[LIST]
[*]Forums like ours will help. Check out new gear on Linux forums before making the purchase.
[*]Make sure you buy components that have a good return policy.
[*]State clearly to the sales rep that you are buying for Linux and will expect a full refund if it doesn't work. Get this in writing.
[/LIST]
But none of the above will help if it's a one-of-a-kind peripheral that is a must-use because it is mission critical. I have no solution for something like that.

---

### Post by #&amp;thj^% on 2022-03-16
> **TheFu said:**
> And for peripherals?

Curious? I always thought peripheral is a piece of computer **hardware** that is added to a computer in order to expand its abilities. The term peripheral is used to describe those devices that are optional in nature, as opposed to hardware that is either demanded or always required in principle. There are all different kinds of peripherals you can add your computer. The main distinction among peripherals is the way they are connected to your computer. They can be connected internally or externally.
I guess we all assumed they were included in the term hardware.

---

### Post by TheFu on 2022-03-16
> **DuckHook said:**
> I've got no solution for that one other than the one you've already mentioned: complain loudly and vehemently. Expect to be met with deaf ears.

Or just buy from Linux friendly companies to start. That seems much easier. No belly aching. No hassles.  Plug in the peripheral and use it.  The more we do that, the more equipment will be created that works with Linux out-of-the-box, as it should be.

There are far too many peripherals that are USB connected by still require custom, proprietary, Windows-only, software to work fully being sold. Every sale confirms they can ignore Linux.  Embarrassment might help companies to learn. Some youtubers have been doing that. When a channel with 15M follows does a series about running Linux and nearly all his peripherals fail to work, there is some corporate embarrassment for each of those vendors. Sorta like how Linus gave nVidia the finger. Embarrassing.  Out of that, we got a relatively easy way to get the correct, proprietary, nvidia GPU drivers easily on Ubuntu.  They are still buggy about 20% of the releases.  Someday, perhaps nvidia will finally get over the proprietary aspects and handle it like AMD does.

---

### Post by DuckHook on 2022-03-16
> **TheFu said:**
> Or just buy from Linux friendly companies to start. That seems much easier. No belly aching. No hassles.  Plug in the peripheral and use it.  The more we do that, the more equipment will be created that works with Linux out-of-the-box, as it should be.
I believe that's what I said too in post #9. We are on the same page.
> There are far too many peripherals that are USB connected by still require custom, proprietary, Windows-only, software to work fully being sold. Every sale confirms they can ignore Linux.
Again, we are singing from the same song sheet.

Based on Shibblet's original post, a few of those peripherals are rather off the beaten track, but I would have expected others to work.

You've already alluded to your bad experience with Logitech. I wasn't aware that they had dropped the ball this badly. I have some Logitech components and they work okay. But my peripherals are almost all quite old. I will even go to the trouble of taking old USB headphones apart to replace hardwired batteries not meant for replacement, so I don't suppose I'm a typical user. I have no experience with the models of peripherals mentioned. I have no reason to doubt you and will be avoiding new Logitech devices in future.

I will note one thing: none of these peripherals were bought with Linux in mind. They were bought with Windows in mind. Then an attempt was made to back in Linux after the fact. Square pegs in round holes. If Shibblet's friend did not buy components with Linux compatibility planned out beforehand, then exactly how is it fair to blame Linux for "shortcomings" that Linux has no obligation to meet in the first place? Aren't the "shortcomings" not only on the OEMs but also on the user's failure to plan? Or on unrealistic expectations?
> Embarrassment might help companies to learn. Some youtubers have been doing that. When a channel with 15M follows does a series about running Linux and nearly all his peripherals fail to work, there is some corporate embarrassment for each of those vendors. Sorta like how Linus gave nVidia the finger. Embarrassing.  Out of that, we got a relatively easy way to get the correct, proprietary, nvidia GPU drivers easily on Ubuntu.  They are still buggy about 20% of the releases.
Unfortunately, this won't work as a general strategy. In the Linux-verse, only one person has Linus's clout and that's Linus. I doubt that nVidia would have been embarrassed by any lesser mortal. There are days when I really, really appreciate his penchant for the middle finger. But how many times can even he throw his weight around without fatally diluting his effectiveness?
> Someday, perhaps nvidia will finally get over the proprietary aspects and handle it like AMD does.
:) It's why I bought an AMD GPU again when my last one died.

---

### Post by Shibblet on 2022-03-16
> **DuckHook said:**
> Seconding what QIII has already stated. I would also add the following:

We need to acknowledge that Linux is a geek's OS. Rather than keep repeating the refrain that "it works out of the box"&#8212;which, even if true for many, has enough exceptions to render this statement deeply misleading&#8212;we should be emphasizing its power, flexibility, freedom and security, but only for those willing to wrestle with its arcaneries and obscurities. If one is not prepared to deal with these things, then one should stick to Windows.

There is a major degree of sadness in this option.  All of the other commercially available OS's are exporting your data.  Microsoft Windows, Mac OS, Chrome OS, etc.

Linux is the only OS out there that does not "data mine" your information and send it back to the manufacturer.

> **DuckHook said:**
> It occurs to me that I did not actually answer your question. So here's my answer:

It's actually quite simple: buy Linux machines from Linux vendors. They are "guaranteed" to work in the same way that Windows OEMs "guarantee" compatibility with Windows: because they are built to be compatible in the first place.

The Linux devs have done such amazing work for so long that we overlook the fact that when we try to install Linux onto Windows machines, we are really trying to force square pegs into round holes. It is to their credit that it works as seamlessly as it usually does. But our default expectation ought to be that it won't work (without a lot of kludging and cussing) and that we are lucky when it does. The solution is not to keep making the square pegs rounder and rounder, but to buy a machine with square holes.

Great answer!  Especially when buying new hardware.

The issue here is that this was on a computer that he already had.  Most people aren't going to go out to buy new hardware just to give Linux a try.  And when it doesn't work well on their existing hardware, they will be under the impression that Linux has Hardware issues.

> **DuckHook said:**
> I believe that's what I said too in post #9. We are on the same page.

Again, we are singing from the same song sheet.

Based on Shibblet's original post, a few of those peripherals are rather off the beaten track, but I would have expected others to work.

You've already alluded to your bad experience with Logitech. I wasn't aware that they had dropped the ball this badly. I have some Logitech components and they work okay. But my peripherals are almost all quite old. I will even go to the trouble of taking old USB headphones apart to replace hardwired batteries not meant for replacement, so I don't suppose I'm a typical user. I have no experience with the models of peripherals mentioned. I have no reason to doubt you and will be avoiding new Logitech devices in future.

I will note one thing: none of these peripherals were bought with Linux in mind. They were bought with Windows in mind. Then an attempt was made to back in Linux after the fact. Square pegs in round holes. If Shibblet's friend did not buy components with Linux compatibility planned out beforehand, then exactly how is it fair to blame Linux for "shortcomings" that Linux has no obligation to meet in the first place? Aren't the "shortcomings" not only on the OEMs but also on the user's failure to plan? Or on unrealistic expectations?

Unfortunately, this won't work as a general strategy. In the Linux-verse, only one person has Linus's clout and that's Linus. I doubt that nVidia would have been embarrassed by any lesser mortal. There are days when I really, really appreciate his penchant for the middle finger. But how many times can even he throw his weight around without fatally diluting his effectiveness?

:) It's why I bought an AMD GPU again when my last one died.

[LIST]
[*]Well, the Logitech Keyboard and Mouse did work... but not at the login screen.  I did some serious searching to figure out how to do this.  Ended up editing the /etc/bluetooth/main.conf file and set "AutoEnable=True," but that didn't actually work.
[*]The controller would connect, but games wouldn't recognize it as a controller.  There is an app for Linux that allows you to map keyboard buttons to the controller, so there is a work-around.
[*]And, the MyCloudHome would work through the web-interface, but it's really slow.
[*]The USB speaker bar just didn't work at all...
[/LIST]
So, there were possibilities here, if he was willing to do some work-arounds... but the work arounds are annoying.

Workaround List:
[LIST]
[*]Plug in a USB Keyboard to log in, then you can use your BT Keyboard and Mouse.
[*]Remap your controller to keyboard inputs, and hope all games except the inputs (and sometimes have to change them for new games)
[*]Wait longer to send and receive data on your NAS.  Don't use a file browser, use the web-interface instead.
[*]Use Headphones from your computers Aux instead.  Or get new speakers with an Aux input.
[/LIST]

And this is where Linux loses people.

I have often wondered if this a "jiggle-the-handle" type situation.  People who know they have to "jiggle-the-handle," eventually just get used to "jiggling-the-handle" and don't think much about it...
But then a friend comes over, and wonders why you have to "jiggle-the-handle..."  Why doesn't it just work?

---

### Post by Shibblet on 2022-03-16
> **DuckHook said:**
> Unfortunately, this won't work as a general strategy. In the Linux-verse, only one person has Linus's clout and that's Linus. I doubt that nVidia would have been embarrassed by any lesser mortal. There are days when I really, really appreciate his penchant for the middle finger. But how many times can even he throw his weight around without fatally diluting his effectiveness?

Wow... I never thought about that.  There are only a few people that would have been effective... but Torvalds was definitely the most effective.

When you look at it this way, he may have had no choice but to call them out.  He was the only person that "could" have made that point.

---

### Post by TheFu on 2022-03-16
> **Shibblet said:**
>  Linux is the only OS out there that does not "data mine" your information and send it back to the manufacturer.


I wish that was true.  Canonical tried mining our data by sending local searches to amazon and google for a few releases. There was an opt-out, but the default was a forced opt-in.  

During an install, if they'd asked for access and fully explained the purpose, I bet the outrage would have been 90% less.  Ask and we'll probably agree. Force something ... like snaps ... and outrage happens.

I'm still confused why there is an ubuntu-firefox-something package at all. I don't remember the exact name, 'cause I purge it.

---

### Post by Shibblet on 2022-03-17
> **TheFu said:**
> I wish that was true.  Canonical tried mining our data by sending local searches to amazon and google for a few releases. There was an opt-out, but the default was a forced opt-in.  

During an install, if they'd asked for access and fully explained the purpose, I bet the outrage would have been 90% less.  Ask and we'll probably agree. Force something ... like snaps ... and outrage happens.

I'm still confused why there is an ubuntu-firefox-something package at all. I don't remember the exact name, 'cause I purge it.

I remember this.  The whole Unity Lens.  But it's no longer a thing now, correct?

And I am also aware that Linux (in general) is a broad term.  Most Linux OS's do not, but there are some out there that have EULA's...  Commercial software can have their own agreements.  i.e. VMWare Player.

I've been a solid Ubuntu user since 8.04, and switched to Kubuntu when Unity became a thing with 10.10.  I played distro-hop all throughout Ubuntu 12.04 to 14.04 era... and then went back to Kubuntu until 21.10.

Now, I have found myself running Manjaro, and not missing forced Snaps (I'm looking at you Ubuntu - Chromium).  Also really enjoying the AUR for packages that would normally be a bunch of command line setup... I can now just find it in the AUR and turn it on.

Regardless of my Linux choice, I would agree that Snaps should be optional, and not forced.  But if that's the direction of Ubuntu's Software Center... well, there are other Linux options.

---

### Post by kevdog on 2022-03-20
Sounds stupid to say, however running Linux as a Desktop OS usually is a subpar experience.  I did it for many years.  It works but clearly you're restricting yourself in terms of hardware you can use.  Once i went Mac for desktop I can't say I went back since it functions underneath a lot like linux (being a BSD derivative). Linux excels as a server architecture and is awesome for NAS and about any other server related project. I just kind of use the tool that's best for the job and switch back and forth between Linux, Mac, Windows.  I dont think it should be ever an all or none proposition.

---

### Post by DuckHook on 2022-03-27
> **kevdog said:**
> …running Linux as a Desktop OS usually is a subpar experience.
This just goes to show how different goals lead to different user experiences.

My evolution was exactly the opposite. I was an Apple user for years (both iOS and MacOS). Each successive Apple experience left an increasingly bitter taste in my mouth until I finally couldn't take it anymore and broke with them completely. I detest silos and Apple has turned silo confinement into a cold&#8209;hearted calculus.

I'll be the first to admit that I'm an odd duck in the following way: I don't have any strong feelings about DEs one way or another. I don't find it difficult to adjust to whatever DE is thrown at me and I don't feel that they cramp my style or hinder my workflow or any of the thousand and one complaints that people gripe about with each little change to their DE of choice. Frankly, I am perplexed by the religious fervour that most people bring to something I consider as inconsequential a thing as a DE. I've worked with every flavour of 'buntu, sampled Manjaro, Fedora, Bodhi, Debian, etc etc and found them all pleasant. In fact, I've sampled more esoteric WMs like fvwm and i3wm and was quite happy with them. I've never found a DE so foreign that I couldn't get my head wrapped around it and become productive in it inside of 15 minutes. In fact, I wrote a tutorial based on my experiences that was turned into a sticky. I really don't get why people are so tied to DEs. Therefore, your statement, that "Linux as a Desktop OS is a subpar experience" is a headscratcher to me.

As stated, my experiences are the exact opposite. When Mrs DH insisted on running Windows, not two weeks would go by that it wouldn't break, usually taking her unsaved work along with it. When I was running various Apple OSes, breakages, though less frequent, were not unheard of, but what really got to me was the insane constraints that I had to accept just to run the thing: Job's insistence of a one&#8209;button mouse, the dearth of common software, everything just different enough that files would not translate precisely, but especially how app vendors would leverage the walled silo to milk users for all they were worth (QuarkXpress suffered a well-deserved spanking IMO).

Once Mrs DH made the jump to Ubuntu, she hasn't suffered a single system breakage in seven years. I no longer even maintain her machine because she knows enough to update when the system reminds her and that's all she has to do. I can port my entire user environment from my main desktop to my backup desktop to any of my laptops to, indeed, as many machines as I want without running into EULA restrictions that threaten me with death and dismemberment for daring to offend their precious ToS. I can install Ubuntu on any machine I want. This is not even legal with MacOS, never mind if it is technically possible. In my books, that's far beyond a subpar experience. It is a completely unacceptable one.
> I just kind of use the tool that's best for the job and switch back and forth between Linux, Mac, Windows.  I dont think it should be ever an all or none proposition.
This is a sentiment that I will second. Use what is best for the job and don't make a religion out of it.

---

### Post by DuckHook on 2022-03-27
> **Shibblet said:**
> …I have often wondered if this a "jiggle-the-handle" type situation.  People who know they have to "jiggle-the-handle," eventually just get used to "jiggling-the-handle" and don't think much about it...
But then a friend comes over, and wonders why you have to "jiggle-the-handle..."  Why doesn't it just work?
Belatedly as it is, I thought I would address this.

The problem with this assessment is that the analogy is all wrong.

Linux is not analogous to a car door with a sticky handle. It is far more analogous to a warp&#8209;speed starship with ultra&#8209;sophisticated controls that your friend can't make heads or tails of. And his response is akin to the guy who comes over to try out your starship only to say: "What's the use of your starship? It doesn't have a steering wheel."

Where things went wrong with your friend was in falling into the trap of trying to substitute Ubuntu for Windows. In your friend's case, cussed HW from doubly cussed OEMs torpedoed this attempt. While this is regrettable, it is not surprising (as so many have pointed out), but my point would be that Linux was being improperly positioned in the first place. This led to improper expectations.

Linux is not a *replacement* for Windows. It never has been and ought never to be. Its proper function is as a more powerful *alternative* to Windows. As an alternative, it is far more capable, but only to those willing to accept it on its own terms. Users who wish to shoehorn it into existing hardware are not accepting it on its own terms; rather, they are trying to force it into *their* terms. *This* is the reason that things went wrong. In the end, what sunk your friend was not bad Linux or even bad OEMs but bad expectations.

Please don't get me wrong. I'm not saying that Linux is perfect. Sometimes, this starship breaks down, or the controls do go wonky, or it drops to sub&#8209;light speed and we have to ask Scotty to jerry rig some miraculous kludge to get us out of a pickle. After all, it's an imperfect creation of imperfect humans. But we need to stop treating it as one interchangeable car among a fleet of look-alike cars. It's an altogether different beast: it's a starship.

---

### Post by Tadaen_Sylvermane on 2022-03-28
> [COLOR=#000000]As an alternative, it is far more capable, but only to those willing to accept it on its own terms[/COLOR][COLOR=#000000]

I think people need to understand what those terms are and not expect more than that. That is an issue as well. Saying alternative is a bit of a deception I think. An alternative would have ways to equal something and shouldn't require extensive research to get close to the same result. At the end of the day between Windows & Linux (can't speak to OSX) they have their strengths but aren't on equal ground on plenty of things.

Gaming comes to mind, I can force a few things to work. But it's usually a hacked up mess that works about 80% of the time. The average person won't accept that. Even Steam's proton which is supposed to be a point and click thing you have to force things to work right. Out of the box you have to find a string to put in the configuration for Skyrim to make voices and background noises heard. I don't mess about with many other games much but I can imagine that Skyrim isn't the only one with this problem. [/COLOR]

---

### Post by QIII on 2022-03-28
"Alternative" does not imply "equal" or even "similar".  

Alternatives are things that exist as different possibilities.

In this respect, the word "alternative" fits exactly.  Linux is a different possibility.  Nobody here ever says it is a drop-in replacement for Windows.  In fact, we often say quite clearly that it is not.  But that is not what an alternative is.

Gaming is often brought up in this sort of discussion.  "Gaming problems" are not a fault in Linux, but a condition placed by developers who create their products specifically for Windows.  Gaming shouldn't even come up.  Windows games are for Windows, not Linux.  That some games can be made to work with some effort and that Steam is able provide an environment where many games can be played is actually a compliment to the Linux community.

Gaming is, however, a consideration that is important to some folks and may, in fairness, put them off.  That's fine.  Nothing wrong with that.  If it doesn't work for what you want, don't use it.

---

### Post by DuckHook on 2022-03-28
> **QIII said:**
> "Alternative" does not imply "equal" or even "similar".  

Alternatives are things that exist as different possibilities.

In this respect, the word "alternative" fits exactly.  Linux is a different possibility.  Nobody here ever says it is a drop-in replacement for Windows.  In fact, we often say quite clearly that it is not.  But that is not what an alternative is.
I cannot up-vote this enough. QIII is spot on. This is exactly what I'm getting at and why I took pains to draw the distinction between "replacement" and "alternative" in the first place.
> Gaming is often brought up in this sort of discussion.  "Gaming problems" are not a fault in Linux, but a condition placed by developers who create their products specifically for Windows.  Gaming shouldn't even come up.  Windows games are for Windows, not Linux.  That some games can be made to work with some effort and that Steam is able provide an environment where many games can be played is actually a compliment to the Linux community.

Gaming is, however, a consideration that is important to some folks and may, in fairness, put them off.  That's fine.  Nothing wrong with that.  If it doesn't work for what you want, don't use it.
I consider myself a Linux enthusiast. Some may even call me a fanatic. But, as partisan as I am, even I have two Windows VMs for running things that only run properly in Windows. It's not a religion and I don't treat it as such.

As for gaming specifically: I find it a head&#8209;scratcher that people would expect to play Windows games on Linux. Do people buy Xbox games expecting them to play on Playstations? Of course not. Why this ridiculous expectation for Linux then? It's because people have internalized the idea that Linux should be treated as a ***replacement*** for Windows and **NOT** as an ***alternative***. The almost automatic reference to games underlines exactly the point I was trying to make.

---

### Post by Tadaen_Sylvermane on 2022-03-28
It's not ridiculous when you consider that an Xbox and Playstation are very different machines visibly. People see a computer and it's an automatic assumption that a computer is a computer. The OS it runs is not something most people would think about. This situation is more like PS5's  and one only runs software for the original PS but the other runs the the current stuff. Who is going to even consider that question? All they will notice is one works the other doesn't.

---

### Post by DuckHook on 2022-03-28
I don't want to be argumentative but:

Let's confine the analogy to computers then.

People do not expect Windows apps to run on Macs. There are Windows apps that are not developed for Apple and vice versa. People are fine with that.

But this false expectation is prevalent in Linux. Why? At least in part, it is because we Linux enthusiasts keep pushing Linux as a ***replacement*** for Windows.

It is far past time to stop doing that. These are fallacies that cannot be sustained. Because, in the final analysis, they are fallacies and fallacies can never be sustained.

If people have false expectations about Linux, then the problem is not Linux&#8212;the problem is the false expectations. Let's deal with that; not try to twist Linux into some sort of poor man's pseudo-Windows.

---

### Post by him610 on 2022-03-29
Logitech K380

System Requirements
Bluetooth enabled device 2Bluetooth wireless computers or other devices that support external keyboards (HID profile). For more information, check with the device manufacturer.
Windows 10,11 or later
macOS® 10.15 or later
iPadOS® 13.1 or later
iOS® 11 or later
Chrome OS™
Android™ 7 or later
Works with Surface
An internet connection (for optional software download)

$439.96

No mention of compatibility with Linux. One must be willing to suffer through incompatiblities. 
Great, if one can afford it.

---

### Post by Tadaen_Sylvermane on 2022-03-29
> [COLOR=#000000]At least in part, it is because we Linux enthusiasts keep pushing Linux as a [/COLOR]***replacement** for Windows.*
[FONT=arial]I know I'm guilty of this, like most of us probably. I get your viewpoint clearly. I guess the topic name practical things. At the end of the day everyone's practical things are different. And it can be frustrating to even suggest Linux of any sort to people because there are so many potential problems they will likely face. It's the same as that scenario where you don't dare recommend a person for a job. If it goes bad you get a bit of blame for recommending an unsuitable person (worded nicely). If anything it can almost be bad for Linux and open source in general to recommend it because they already don't understand it. When it doesn't or can't work with some of what they want it just reinforces that problem. Like shooting itself in the foot almost.[/FONT]

---

### Post by DuckHook on 2022-03-29
> **him610 said:**
> …No mention of compatibility with Linux.
I think you've just answered your own question. If one then insists on buying/using this keyboard anyway, how can one blame Linux for problems?

BTW, the second hit from a cursory web search gave me this: [https://unix.stackexchange.com/questions/590221/pairing-logitech-k380-in-ubuntu-20-04/663566](https://unix.stackexchange.com/questions/590221/pairing-logitech-k380-in-ubuntu-20-04/663566)

The truth is that it's not that hard to check for compatibility issues between OEM equipment and Linux. If such issues exist, then unless one is prepared to get ones hands dirty or replace that piece of equipment, the short answer is: "don't migrate to Linux."

---

### Post by DuckHook on 2022-03-29
> **Tadaen_Sylvermane said:**
> I know I'm guilty of this, like most of us probably. I get your viewpoint clearly. I guess the topic name practical things. At the end of the day everyone's practical things are different. And it can be frustrating to even suggest Linux of any sort to people because there are so many potential problems they will likely face. It's the same as that scenario where you don't dare recommend a person for a job. If it goes bad you get a bit of blame for recommending an unsuitable person (worded nicely). If anything it can almost be bad for Linux and open source in general to recommend it because they already don't understand it. When it doesn't or can't work with some of what they want it just reinforces that problem. Like shooting itself in the foot almost.
I am deeply sympathetic to your sentiments. I used to push Linux too. In a way, I still do, but I do it with a very different approach these days (see my checklist in post #8).

If you find it helps, here's what I do now:

I now approach it very carefully—almost reluctantly. I make it clear that Linux will not replace Windows, that it is a very different animal, that it has a learning curve, that they will have to get used to new apps, that they cannot expect the same user experience or conventions; but that if they persevere with it, they will get awesome results that they could not even dream of in Windows.

I'm less enthusiastic, more reserved. I first qualify the candidate using the aforementioned checklist. If they do not pass the checklist, then I politely tell them that they are unlikely to be happy trying Linux and had best stick to Windows. Most are surprised to hear me say that—knowing me for the Linux enthusiast that I am—but it's the best thing I can do for them, myself and the larger Linux community.

Those who pass the checklist get heavily warned. I give them all the caveats: that we may encounter problems migrating, that even after a successful migration they will feel like a fish out of water for some time, that community support is not instant and is filled with geeks who won't put up with outbursts of frustration, that it's a power&#8209;user's OS so it assumes a rudimentary knowledge of technical concepts, that they had best expect at some point to have to use the command line. The good news is that, after the checklist and the caveats, few back out at this point, even with all the warnings.

Once realistic expectations have been set, it's surprising how smoothly things go after that. The reality is that bad OEM experiences are the exception rather than the rule. Most migrations happen without any hitches. On the last one I did, my buddy turned to me afterwards and said: "with all your warnings, I expected the worst, not this 20 minute walk in the park".

---

### Post by ajgreeny on 2022-03-30
As far as I'm concerned there is no point trying to get those people unwilling to accept that Linux is different from Windows into Linux use.

I tried this once for a neice  whose computer had broken completely and all that was available was on old laptop that would not run Windows of any supported version.  I put Xubuntu on it and it ran very well, did everything that was needed, mainly looked just like the Windows of that time, but of course, wouldn't run the Windows applications my neice was used to so it was a non-starter as far as she could see.

Short sighted but pretty normal for most people I think.

---

### Post by Shibblet on 2022-03-30
> **DuckHook said:**
> Linux is not analogous to a car door with a sticky handle.

LOL!  That's not the handle-analogy I was going for!  Definitely not talking about a car door handle!  I absolutely love this take though!
I was referring to another form of "jiggle the handle."

> **DuckHook said:**
> It is far more analogous to a warp&#8209;speed starship with ultra&#8209;sophisticated controls that your friend can't make heads or tails of. And his response is akin to the guy who comes over to try out your starship only to say: "What's the use of your starship? It doesn't have a steering wheel."

Where things went wrong with your friend was in falling into the trap of trying to substitute Ubuntu for Windows. In your friend's case, cussed HW from doubly cussed OEMs torpedoed this attempt. While this is regrettable, it is not surprising (as so many have pointed out), but my point would be that Linux was being improperly positioned in the first place. This led to improper expectations.

Linux is not a *replacement* for Windows. It never has been and ought never to be. Its proper function is as a more powerful *alternative* to Windows. As an alternative, it is far more capable, but only to those willing to accept it on its own terms. Users who wish to shoehorn it into existing hardware are not accepting it on its own terms; rather, they are trying to force it into *their* terms. *This* is the reason that things went wrong. In the end, what sunk your friend was not bad Linux or even bad OEMs but bad expectations.

Please don't get me wrong. I'm not saying that Linux is perfect. Sometimes, this starship breaks down, or the controls do go wonky, or it drops to sub&#8209;light speed and we have to ask Scotty to jerry rig some miraculous kludge to get us out of a pickle. After all, it's an imperfect creation of imperfect humans. But we need to stop treating it as one interchangeable car among a fleet of look-alike cars. It's an altogether different beast: it's a starship.

Great explanation!  I completely agree with this assessment.

I have shown this thread to my friend, and his replay is basically "Well, that's all and good, but it doesn't resolve any of my problems."

---

### Post by Shibblet on 2022-03-30
> **QIII said:**
> Gaming is often brought up in this sort of discussion.  "Gaming problems" are not a fault in Linux, but a condition placed by developers who create their products specifically for Windows.  Gaming shouldn't even come up.  Windows games are for Windows, not Linux.  That some games can be made to work with some effort and that Steam is able provide an environment where many games can be played is actually a compliment to the Linux community.

Gaming is, however, a consideration that is important to some folks and may, in fairness, put them off.  That's fine.  Nothing wrong with that.  If it doesn't work for what you want, don't use it.

Gaming is actually one of the most "tech-heavy" things that people with PC's tend to do.  Most of the "tweaking" PC users do to their PC is to get more performance out of gaming.  ;-)

Even though Gaming is a huge thing for PC owners... It's still not as good in Linux as it is in Windows, even though Steam and Proton have made huge strides, it ultimately comes down to "Linux attempting to run Windows software."

---

### Post by Shibblet on 2022-03-30
> **him610 said:**
> Logitech K380

System Requirements
Bluetooth enabled device 2Bluetooth wireless computers or other devices that support external keyboards (HID profile). For more information, check with the device manufacturer.
Windows 10,11 or later
macOS® 10.15 or later
iPadOS® 13.1 or later
iOS® 11 or later
Chrome OS™
Android™ 7 or later
Works with Surface
An internet connection (for optional software download)

$439.96

No mention of compatibility with Linux. One must be willing to suffer through incompatiblities. 
Great, if one can afford it.

This would make sense ***IF*** he didn't have all of this equipment to begin with.  ***IF*** he started out with a Linux PC, and then decided to buy the equipment.

Apple users tend to have this well understood.  They (mostly) tend to buy equipment that is Apple compatible.  And will specifically look for Apple compatibility.
Windows users sometimes look for compatibility issues... but realistically, it's generally assumed that most hardware you purchase will work on Windows.

> **DuckHook said:**
> BTW, the second hit from a cursory web search gave me this: [https://unix.stackexchange.com/questions/590221/pairing-logitech-k380-in-ubuntu-20-04/663566](https://unix.stackexchange.com/questions/590221/pairing-logitech-k380-in-ubuntu-20-04/663566)

The truth is that it's not that hard to check for compatibility issues between OEM equipment and Linux. If such issues exist, then unless one is prepared to get ones hands dirty or replace that piece of equipment, the short answer is: "don't migrate to Linux."

Are you suggesting coconut's migrate?  :P

That is precisely the point.  Most Linux users did not start with Linux.  They started with another OS, and then "migrated" to Linux.  Even after the migration, Gamers tend to keep a Windows Partition, or a Windows Gaming Computer for their gaming purposes.

Also, remember, that his hardware didn't completely fail to work, it worked... mostly.  The K380 would work, but only after he logged in with another keyboard.  Whereas with Windows, it just worked.

---

### Post by QIII on 2022-03-30
> **Shibblet said:**
> Gaming is actually one of the most "tech-heavy" things that people with PC's tend to do.  Most of the "tweaking" PC users do to their PC is to get more performance out of gaming.


The "tech-heavy" is on the development and hardware side -- and it goes to Windows.  Although some people fiddle with clock speeds and such, they are adjusting things via established hardware interfaces.  They are not doing lithography to make their own silicon.  The people with PCs are generally not the ones "doing the tech".  They just push buttons and wiggle joysticks.  :)

---

### Post by Shibblet on 2022-03-30
> **QIII said:**
> The "tech-heavy" is on the development and hardware side -- and it goes to Windows.  Although some people fiddle with clock speeds and such, they are adjusting things via established hardware interfaces.  They are not doing lithography to make their own silicon.  The people with PCs are generally not the ones "doing the tech".  They just push buttons and wiggle joysticks.  :)

Good point.  Maybe "tech-heavy" isn't the best description...  Tweaking?  Maybe?

Yeah, you are correct, it's all software that does the tweaking.  It's not normally at the HW level, unless of course you are doing some extreme overclocking.  ;-)

---

### Post by DuckHook on 2022-03-30
> **Shibblet said:**
> I have shown this thread to my friend, and his replay is basically "Well, that's all and good, but it doesn't resolve any of my problems."
I feel for your friend. And there is truly no further advantage to be gained for either of you in pushing this topic any further. But, if only as an academic exercise, the proper position I've been advocating would be: "Linux was never meant to resolve any of your problems. It was unwise to try. What's advisable is to try making Windows work for you instead."

I hope your friend finds a good solution.

---

