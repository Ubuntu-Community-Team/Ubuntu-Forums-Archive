---
title: "Losing Patience With Linux"
date: 2005-12-19
forum: The Cafe
---

### Post by mrgnash on 2005-12-19
Ok, this is not another 'Here's what's wrong with Linux' thread, but I too had to blow off a little steam.

Before I begin, let me get one thing straight - I love Linux, and I hate Windows. In fact, my frustration comes from the fact that in order to perform certain tasks I *have* to boot into Windows -- I really don't want to, and I resent the space *it* is taking up on my HD :(

A big part of the problem is that I'm using an Acer Travelmate 4402WLMi, which right from the beginning has done it's best to let me know that it was never designed with Linux in mind. 

First it was the screen, which didn't display at all necessitating a manual fix. 
Then it was the Wireless card, which was a complete nightmare which took three days and a kernel recompile to get right (even so, it's still slow) and that was WITH a Linux guru on-hand; I wouldn't have stood a chance on my own.

Then it was Opera, my preferred browser, which because they don't have a 64bit version didn't install with a chroot force architecture, so it doesn't run properly at all. Same goes for Mozilla, my second favourite browser.

CD playback was an issue -- hell it's still an issue, in that it doesn't work on any but a couple of my players. The ones it does work on don't seem to support playlists or any of that other nice stuff.

DVD playback is the same, except that thanks to a helpful forum member here I finally managed to get it to play smoothly... on Gxine at least. 

To top off the list, browsing the Samba network never worked properly in Gnome so I had to switch to KDE, which doesn't work 100% the way it should. And Fluxbox wouldn't install properly either -- I booted into it and there was NO menus at all, so I had to kill XWindows and restart GDM.

Most of the above issues have been resolved, but there are still a couple of niggling things which necessitate keeping XP... such as the lack of a streaming media app on par with Winamp, the ability to play World of Warcraft (STILL can't get Wine to install/compile properly) and support for my USB headset which is the only alternative I have to my rather lacklustre laptop speakers.

So in the end, the only reason I have to use Ubuntu/Linux is one of principle. Before I made the crossover, I had Windows XP almost completely stocked with GNU software - I even replaced the shell with BBLean (think Fluxbox) and ditched Photoshop for GIMP... **not** an altogether easy or painless transition. I sure hope that support for 64bit architectures improves for Linux in the future, because I believe this is the source of most of my troubles... and I'm just so sick of having to do everything the long way around and making-do with makeshift solutions that lead to software which is only semi-functional a lot of the time.

/rant

---

### Post by aysiu on 2005-12-19
Well, next time you're in a position to buy (or otherwise own) a new computer, you'll know to look for something Ubuntu-compatible. Sorry it's been such a painful journey.

---

### Post by arpunk on 2005-12-19
I agree with aysiu. When you have the chance next time, try googling all the hardware and make sure its supported by linux, and that it works in ubuntu. You will see, when things work 100% alright, that linux is the best thing that can happen to your computer :P

---

### Post by greenway on 2005-12-19
Yeah, sorry here too. I also experienced a lot hassle installing Linux on some of my systems. Long frustrating nights filled with blood, sweat and tears. On the other side, I have learned so much using Linux (and Ubuntu) which, for me, compensates a lot the trouble I had to go trough to get stuff to work the way it should.

I really hope things will get better for ya! And just so that you know, the Ubuntu community will always do it's best to help you with every problem you will encounter...

-mattijs

---

### Post by nalmeth on 2005-12-19
sounds like you know a bit about linux, and didn't post here to ask questions, but like you said, blow off some steam. That's pretty fair, because it looks like you're going thru hell to get what should be an easy desktop going..

If I may offer a suggestion

From a distance, a lot of problems seem to be oriented around the 64-bit platform. (Wine (not 64-bit supported), Opera, etc)

I had a few problems as well with the 64-bit kernel, and after juggling chroots and band-aid solutions (for A LOT of things), I finally said screw it, and installed the i386 version, and everything unfolded perfectly out-of-the-box, and works great. 

To be honest, I think the only reason there is a 64-bit kernel is that all computers are heading that way, and Ubuntu is just staying ready for it. Good on 'em.
It did not perform well for me in A LOT of faculties, but I understand why those problems are there, and won't be bashing Ubuntu anytime soon.

keep with it

---

### Post by mrgnash on 2005-12-19
Thanks for the support guys, I'm glad the Ubuntu community is such an understanding one, unlike some forums where any criticism of GNU/Linux is considered blasphemous ;) 

As Greenway pointed out though, the upside to experiencing so many difficulties is that you learn a lot more about Linux (or any other OS) than you might might under more 'ideal' conditions. I came to Ubuntu as a very n00by *nix user, having only toyed around with Cygwin and a few live CDs like Knoppix, Mepis etc. and have learnt a fair bit in a relatively short amount of time. Of course, a lot of that is also due to doing a lot of reading beforehand, asking a lot of dumb questions here and on IRC and having a Linux guru to brain-drain a lot of knowledge from. So from that angle, I'm almost glad that the road so far has been a little bumpy.

I'm reluctant to install the 32-bit version because I have a lot of data on here that would take an age to back up -- not to mention all the time I've spent in configuring the damned thing so far; and I'm _assuming_ that the only way to switch to the 32-bit kernel is to do a clean install :(

If I can only get the few things I mentioned to work, such as WoW and my headset I'll be pretty much set. It's already 96% operational, but I'm a bit of a desktop perfectionist... anyone who has seen what I did to XP on my old box could attest to that :p

---

### Post by nalmeth on 2005-12-19
Don't take my words as gospel truth here, but I've heard from other users you can reinstall Ubuntu without erasing the home folder. As far as how to actually do this I don't know. Maybe they meant creating a new partition for it, or maybe there really is an easy way? It would be worth looking into.
Maybe you could install the kernel from synaptic?

I'm sure you'll figure something out.

EDIT:
If wine is all you need to run WoW then try this link, and you'll get it going 

[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)

(hoary should be breezy in *all places*)

---

### Post by codejunkie on 2005-12-19
[QUOTE=nalmeth]Don't take my words as gospel truth here, but I've heard from other users you can reinstall Ubuntu without erasing the home folder.[/QUOTE]
you can do that only if you partitioned your hard drive with /home on a seperate partition. if you just did the standard ubuntu install it's quite a bit harder.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=mrgnash]Ok, this is not another 'Here's what's wrong with Linux' thread, but I too had to blow off a little steam.

Before I begin, let me get one thing straight - I love Linux, and I hate Windows. In fact, my frustration comes from the fact that in order to perform certain tasks I *have* to boot into Windows -- I really don't want to, and I resent the space *it* is taking up on my HD :(

A big part of the problem is that I'm using an Acer Travelmate 4402WLMi, which right from the beginning has done it's best to let me know that it was never designed with Linux in mind. 

First it was the screen, which didn't display at all necessitating a manual fix. 
Then it was the Wireless card, which was a complete nightmare which took three days and a kernel recompile to get right (even so, it's still slow) and that was WITH a Linux guru on-hand; I wouldn't have stood a chance on my own.

Then it was Opera, my preferred browser, which because they don't have a 64bit version didn't install with a chroot force architecture, so it doesn't run properly at all. Same goes for Mozilla, my second favourite browser.

CD playback was an issue -- hell it's still an issue, in that it doesn't work on any but a couple of my players. The ones it does work on don't seem to support playlists or any of that other nice stuff.

DVD playback is the same, except that thanks to a helpful forum member here I finally managed to get it to play smoothly... on Gxine at least. 

To top off the list, browsing the Samba network never worked properly in Gnome so I had to switch to KDE, which doesn't work 100% the way it should. And Fluxbox wouldn't install properly either -- I booted into it and there was NO menus at all, so I had to kill XWindows and restart GDM.

Most of the above issues have been resolved, but there are still a couple of niggling things which necessitate keeping XP... such as the lack of a streaming media app on par with Winamp, the ability to play World of Warcraft (STILL can't get Wine to install/compile properly) and support for my USB headset which is the only alternative I have to my rather lacklustre laptop speakers.

So in the end, the only reason I have to use Ubuntu/Linux is one of principle. Before I made the crossover, I had Windows XP almost completely stocked with GNU software - I even replaced the shell with BBLean (think Fluxbox) and ditched Photoshop for GIMP... **not** an altogether easy or painless transition. I sure hope that support for 64bit architectures improves for Linux in the future, because I believe this is the source of most of my troubles... and I'm just so sick of having to do everything the long way around and making-do with makeshift solutions that lead to software which is only semi-functional a lot of the time.

/rant[/QUOTE]

If anything we can be sympathetic. Read the whole rant. Its good to blow off steam if its constructive. A little advice from reading:

Vlc works most consistent for me for everything (including CD playing) in Ubuntu, but I like Totem-xine best

And really try Epiphany the browser. Its good with its extensions- some are far better than the Firefox equivilents I think!

Its sometimes hard to be 100% Linux compatible. My friend just did it- I made made him a list with a dream system (that is the best I could think of for out of box awesome in Ubuntu and more) and it took me a LONG time to make a good list. Far to long. And until he tries I just don't know. But I tried my best and he wanted a system (that would work with Ubuntu best- he likes it more than me) and he went to a local retailer and bought near what I said from a merchant that was a friend of mine (and knew the important of the list) and he bought it and put it together in the store. But there were many steps that were far more harder than calling the local Dell, and somethings that were far more expensive. But he told me he just wanted the best I could do for a non-gamer and the Dells of the world cannot supply a 100% compatible machine. 

But when you do get it working, it works well. Then its all worth it. Its like the opposite of the Apple experiance in many ways, but in some cases it is far better (aka a few online retailers that have all the custom parts together but for less amazing prices) than the "biege box." But its way worth it when your stuff works in Linux (I felt my once pointless loyalty to HP printers paid off in a serious way when I switched for instance).



And thats for desktops. On laptops.....hmmmm....a few online retailers do that...but.....I might buy one of these:

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)

When they get cheap.

But for you- you seem almost done. Good luck for the rest.

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=codejunkie]you can do that only if you partitioned your hard drive with /home on a seperate partition. if you just did the standard ubuntu install it's quite a bit harder.[/QUOTE]


 I do it.

---

### Post by bikeboy on 2005-12-19
Hi mrgnash, I notice you're from Aus. Are you a member of the Whirlpool broadband forums? [www.whirlpool.net.au](www.whirlpool.net.au) if you are not.

There is a good linux forum there (not that these forums aren't awesome) with people in our time zone that can always help you through problems with quick replies. Sometimes that is important for keeping the frustration at a manageable level :)

I'm sure 64bit linux has a way to go but it's lucky you aren't trying to get XP-64bit working. I haven't heard too many success stories there.

Good luck!

---

### Post by arctic on 2005-12-19
> Most of the above issues have been resolved, but there are still a couple of niggling things which necessitate keeping XP... such as the lack of a streaming media app on par with Winamp, the ability to play World of Warcraft (STILL can't get Wine to install/compile properly) and support for my USB headset which is the only alternative I have to my rather lacklustre laptop speakers.To be honest: There is no "need" for streaming media apps or games or a USB headset. These are luxury-things you are asking for that may or may not work with any OS you decide to try out. You NEED to play World of Warcraft? You must be kidding...

And one final note: Laptops are primarily designed for work, not for gaming.

---

### Post by Mr. Electric Wizard on 2005-12-19
If your ever in the market to get another laptop, I'd seriously have to suggest an HP.
I just bought one the of Wal-Mart specials a couple of weeks ago ($378 - ze2308wm) and I am totally in love with it...
But...   It has been the most difficult install of Ubuntu I have done yet.
Complaining aside, once dialed in, this is a _rock solid_ install.
Laptops bring lots of different "variables" to the equation.

Some of the things I encountered:
-ATI card not found, and X not starting with fresh install.
-WIFI not working, had to use Ndiswrapper (broadcom chip)
-Double clock speed bug (noapic nolapic) kernel option.

All wonderful learning experiences!:p 

So, basically what I'm saying from one n00b to another n00b is that if you stick with it long enough it will pay off for you!
If you stick with it long enough also, it'll probably turn into obsession!

Do they have a twelve step program for Linux?:D

---

### Post by prizrak on 2005-12-19
I would never advise an HP laptop to anyone I don't hate, same with Toshiba actually those things tend to die randomly (hardware). I do believe that if you want to move to 32bit all you have to do is install the regular 386 kernel. I'm not sure though, if you do install it just don't remove your old kernel and boot into 386 if it don't work you can just reboot into your regular one :) 
Since you got a Linux guru around maybe you should try Gentoo, it is very good for complete customization. It is a VERY difficult OS to install and get stuff running on, so approach with caution :)

---

### Post by Freddy on 2005-12-19
> A big part of the problem is that I'm using an Acer Travelmate 4402WLMi, which right from the beginning has done it's best to let me know that it was never designed with Linux in mind.
You know that it wasn't designed for XP either? The usual XP that most people use, isn't compiled for a 64bit architecture either and the one that are, is a big joke with little support, such as drivers. Most of the 32bit programs will run on a 64bits XP but a lot slower then on a 32bit system.
So if you used a 32bits XP, why not just use a 32bits Ubuntu? If you made a /home partition you can backup in that and mount your old home when making the new install.

WoW should work with Cedega (wineX) (not sure that Cedega will work on your 64bits system though), using Cedega will cost you some but atleast you could play WoW from your Ubuntu.   /// Freddan

---

### Post by Kerberos on 2005-12-19
[QUOTE=Freddy]You know that it wasn't designed for XP either? The usual XP that most people use, isn't compiled for a 64bit architecture either and the one that are, is a big joke with little support, such as drivers. Most of the 32bit programs will run on a 64bits XP but a lot slower then on a 32bit system.[/QUOTE]
I'm 99% sure thats not true (unless your dealing with Itanic).  You shouldn't lose performance running 32bit apps on a 64bit OS.  They should run at the roughly the same speed they would have on a similar 32 bit system.

I run Windows x64 on my laptop (Ubuntu refuses to even boot on it) and don't notice any slowdown running 32 bit code.  Drivers admittedly are a bit of a joke (Flash card reader and Intel wireless* drivers are unavailable) but apart from that I've got no real problems with it.

** According to Intel, "Windows x64 is 'unsupported'" (you betcha it wouldn't be if Intel made x64 chips - talk about anti-competitive)*

---

### Post by Emerzen on 2005-12-19
[QUOTE=arctic]To be honest: There is no "need" for streaming media apps or games or a USB headset. These are luxury-things you are asking for that may or may not work with any OS you decide to try out. You NEED to play World of Warcraft? You must be kidding...

And one final note: Laptops are primarily designed for work, not for gaming.[/QUOTE]

Every computer use is a luxury!  Who are you to decide what is a computer necessity for someone else's needs?

---

### Post by mrgnash on 2005-12-19
Yeah arctic, I don't need you or anyone else to tell me what I should do with **my** computer. Perhaps you think that no-one should ever leave Bash, or they might be spoilt by all those 'luxuries' that come along with a... *gasp* window manager! :O Oh well, there's always one in every thread I guess. Anyways, the advice from the rest of you guys is much appreciated :) Unfortunately I didn't mount my home directory on a separate partition. And I'm also aware that XP 64 is another minefield... that's why my lappy comes with XP Pro 32 instead -- hell, it's even using a FAT32 filesystem just so it can use it's 'eRecovery' system (which I had to uninstall because it didn't like the fact that I modified the partition table to accommodate Linux) and backing up the hardware profile alone consumes about 3 CDs as it is. So don't worry, I don't have any illusions about the compatibility of XP but because it was pre-configured on this machine, it has meant less work for me :P

And thanks, I'll be sure to check out those forums :D

---

### Post by arctic on 2005-12-19
Man, I only wanted to point out that there is a difference between the word "need" and "want". If you fail to see that I am sorry. I am simply struck by the way some people use their language... without care to detail. I do care... although english is not my native language.

And Emerzen, not every computer is a luxury. I would say that in hospitals, computers are a necessity. But ...we are going off-topic, so I better stop before a flame-war breaks out.

---

### Post by mrgnash on 2005-12-19
[QUOTE=arctic]Man, I only wanted to point out that there is a difference between the word "need" and "want". If you fail to see that I am sorry. I am simply struck by the way some people use their language... without care to detail. I do care... although english is not my native language.

And Emerzen, not every computer is a luxury. I would say that in hospitals, computers are a necessity. But ...we are going off-topic, so I better stop before a flame-war breaks out.[/QUOTE]

Before you dig yourself a deeper hole you mean? If you reread what I said carefully, you'll realise that my point was that: if I want to do these things, then with the way things currently stand with my system, I have to switch to XP. Therefore, for me to do what I want to do with my system, keeping XP on my HD is necessary. 

Maybe these things seem frivolous to you, fair enough; but it's my computer, I paid for it and it's up to me to decide what I want to do with it, whether that be work or play (I happen to use it for both). Oh and the old fall-back of 'My original statement only concerned semantics' is a coward's way out.

---

### Post by prizrak on 2005-12-19
Hey I NEED to game, otherwise I get real irritable and beat up on people IRL or drive much too  fast :)

---

### Post by Emerzen on 2005-12-19
[QUOTE=arctic]Man, I only wanted to point out that there is a difference between the word "need" and "want". If you fail to see that I am sorry. I am simply struck by the way some people use their language... without care to detail. I do care... although english is not my native language.

And Emerzen, not every computer is a luxury. I would say that in hospitals, computers are a necessity. But ...we are going off-topic, so I better stop before a flame-war breaks out.[/QUOTE]

I beg to differ.  If computers were a necessity to hospital care, then how did hospitals get along before they were incorporated into health care?  So, to be careful of your use of language you should say that computers are very *important* to *current* hospital care.  

Even now you could argue that they are far from necessary and, from some perspectives, are a significant detriment to good medical practice.  For example, something like 80% of a person's total expenditure towards health care is spent on their last year of life; i.e., on the "heroic" measures--most of which are technological.   Unfortunately, as this cost of high technology health care increases, it contributes to the average person's higher cost of living, and the now standard 60, 70, or 80 hour work week and fewer people having access to any health care.  So, for some technology (not computer's per se) have meant that they get no hospital care.  And, it wouldn't be irrational for society to say, "I'd rather work less for 79/80th of my life and have a higher quality of life, and let that last year of Gamma-radiation and month long ICU stays go, thank you very much but you can keep your computer."  

I do agree that you could draw a distinction between say, military or health care, related computer use on the one hand and gaming on the other.  And you could say that the former computer use is highly valued and important while the latter use is frivolous and a luxury.  But, that is a relative and context based value judgement that many would agree on, but has no absolute basis (for example, capitalists might argue that the revenue generated from gaming computer uses far outstrips all others combined, and it is this revenue that is a "necessity" for the economy and, hence, the welfare of such and such country).  

My point is that it is his computer and, therefore, his decision to decide what is necessary or not for its use.  And there is no external, absolute, value standard by which one could condemn that use as a luxury.  Above and beyond all this is the possibility that he uses streaming media, etc..., etc... to make his living and, in that sense, is very necessary to him?  

Food for thought and in the spirit of friendly debate.  I'll keep an open mind to your reply.

---

### Post by aysiu on 2005-12-19
Hospitals probably didn't save as many lives before computers came around. What does *need* mean anyway?

Hate to bust out the dictionary, but if you're going to argue semantics... >    1. A condition or situation in which something is required or wanted: crops in need of water; a need for affection.
   2. Something required or wanted; a requisite: “Those of us who led the charge for these women's issues... shared a common vision in the needs of women” (Olympia Snowe).
   3. Necessity; obligation: There is no need for you to go.
   4. A condition of poverty or misfortune: The family is in dire need. Technically speaking (if we go by whatever definition you're hinting at), the crops don't *need* water--they'll just die without it. No one *needs* affection--they'll just suffer without it. Hospitals may, in fact, need computers, if "need" means they can't save as many lives without computers.

There are varying degrees of "need" (oddly enough, one definition is something *wanted*--definition #2), and clearly the "need" to conduct business, save lives, and communicate with others is more pressing to day-to-day living than the "need" to play video games, unless you're a video game addict.

And... who knows? Maybe the person in question *is* a video game addict. Nevertheless, video games are a recreational activity... a luxury. You can be addicted to any luxury or leisure activity, but they are nevertheless *luxuries*.

---

### Post by prizrak on 2005-12-20
> And... who knows? Maybe the person in question is a video game addict. Nevertheless, video games are a recreational activity... a luxury. You can be addicted to any luxury or leisure activity, but they are nevertheless luxuries.

Unless you are a paid beta tester/QA for a gaming company ;)
Anyways you can't say "Laptops are for work not gaming so STFU and delete Windows" computers are known as "universal tools" which means that gaming is one of the things they can do. I game in dosbox cuz I like the old games, this man/woman pays for WoW and probably spent a good amount of time on it already so he wants to play it. Doesn't matter what we think, I personally don't like any RPG's MMO or otherwise but he/she isn't gonna stop playing it just because I have a different opinion.

---

### Post by Freddy on 2005-12-20
> If I can only get the few things I mentioned to work, such as WoW and my headset I'll be pretty much set.
If you would like to try, I belive that there exit a Cedega package compiled for 64 bits computers, Cedega will cost you some, but you could always try the time limit version and at least try to make WoW work from within your Ubuntu.

A suggestion regarding you backup problem, can't you make your backup to your FAT32 partitions ? and reinstall eith the 32bits version of Ubuntu ?.   /// Freddan

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=Freddy]If you would like to try, I belive that there exit a Cedega package compiled for 64 bits computers, Cedega will cost you some, but you could always try the time limit version and at least try to make WoW work from within your Ubuntu.
[/QUOTE]

Since the game binaries are 32 bit, that won't help much. Unless you add the 32 bit libs to 64 bit Ubuntu.

---

### Post by Gowator on 2005-12-21
[QUOTE=nalmeth]sounds like you know a bit about linux, and didn't post here to ask questions, but like you said, blow off some steam. That's pretty fair, because it looks like you're going thru hell to get what should be an easy desktop going..
[/quote]
posting REAL questions on this forum tends to be a waste of time because by the time someone who actually understanbds that question looks its lost on the 50th page of unanswered posts....  

> 

If I may offer a suggestion

From a distance, a lot of problems seem to be oriented around the 64-bit platform. (Wine (not 64-bit supported), Opera, etc)

I had a few problems as well with the 64-bit kernel, and after juggling chroots and band-aid solutions (for A LOT of things), I finally said screw it, and installed the i386 version, and everything unfolded perfectly out-of-the-box, and works great. 

Agreed ... and posting from it with streaming media players etc.  

> 
To be honest, I think the only reason there is a 64-bit kernel is that all computers are heading that way, and Ubuntu is just staying ready for it. Good on 'em.
It did not perform well for me in A LOT of faculties, but I understand why those problems are there, and won't be bashing Ubuntu anytime soon.

Most of the problems are in non-free software like flash or real player plugins etc.

---

### Post by aysiu on 2005-12-21
[QUOTE=Gowator]posting REAL questions on this forum tends to be a waste of time because by the time someone who actually understanbds that question looks its lost on the 50th page of unanswered posts....[/QUOTE] It depends on what you mean by "real questions." If you mean questions that address obscure problems that only a small handful of experts on this forum know how to answer... then, yes, what you're saying is true.

However, the response time to my "real questions" has been anywhere between two minutes to an hour.

---

