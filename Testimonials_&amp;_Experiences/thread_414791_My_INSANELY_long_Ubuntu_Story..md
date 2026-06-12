---
title: "My INSANELY long Ubuntu Story."
date: 2007-04-20
forum: Testimonials &amp; Experiences
---

### Post by Gustave on 2007-04-20
Just to let ya know in one line... I'm having lots of fun with Ubuntu, and I just wanted to share my experiences as a Linux newbie.

This isn't my first attempt at using Ubuntu.  I had tried it before, in November, I believe, and actually I had tried Red Hat several years ago, one of the earlier versions.  Got RedHat installed and dual booted it with Windows 98 (which was new at the time, too) but I got bored with it because I was a gamer and game support on Linux was non existant.  I later tried MandrakeMove (a LiveCD kinda thing) and later Mandriva on a USB key.  Not sure why I was so into either of them.  I guess I thought I had to pay to get a decent system.  MandrakeMove ultimately bored me, and the other Mandriva (there was a name change between one and the other, but it's the same company) was only on a 2gig key, and I found it very difficult to install stuff I wanted.  

However, it got me the itch to do what I finally did.  Putting together some old parts I had lying around, and seeing if I could get Linux working again.  Ubuntu has really interested me.  This was actually my third attempt at getting it going.  The first was with 6.06, which I did get going.  It bored me, after a while, though, because I didn't wanna take the time to learn about it and how to get stuff installed for it.  6.10 didn't wanna work for me at all.  Tried for a couple days, but ultimately failed because I didn't take the time to read the forums.

This time though, things went well.  After I got the hardware together for the desktop, things went VERY smoothly.  I installed a bunch of stuff, including BOINC, so now I have three boxes going running that program.  I had one hiccup, though, that through me for a loop.  I have no idea how I caused it, but it seems I did because I can't figure out how else it would have happened.  I couldn't move any of my windows any more.  There were no boxes around them to resize any of them either.  As a clueless newbie, I was at a total loss.  From my last Ubuntu attempt, I remembered the forums, and I've used forums exensively for other things, so I thought I'd give it a wack before I erased my system out of frustation.  I don't think it was 10 minutes before I got an answer.  Metacity.  I typed it in and it fixed the problem!  I added it to my sessions area so I wouldn't have that problem again.  

Things weren't flawless, but they went well.  I'm still having a couple minor problems, but I'm having fun trying to figure them out on my own.  I actually caused another problem when I copied my Thunderbird folders from my Windows box to this box (Ubuntu).  I copied over extensions, too, and they did NOT like Linux.

Oh, my current setup is like this.  I made the new Ubuntu box and put it behind my flat panel monitor.  I have an XP box on my desk, too.  I installed Synergy (coolest program EVER) so I could share my mouse and keyboard with them.  My monitor has inputs for DVI from my XP box and VGA from my Linux box.  I push a button on the monitor and it swaps between them.  Synergy I have set up with the server on xp and client on Ubuntu.  This worked out better for me because I have a wireless mouse and keyboard.  I didn't have to configure any of the mouse or keyboard keys in Linux.  They're mapped in windows and work in Linux the way I have them configured through windows.  VERY convenient.  At this point, I haven't switched everything over to the Ubuntu box, but things are slowly going over there as I have time.  I still need to pop by radio shack so I can share my speakers with a wire I need to get from them.

After my positive experience on my desktop, I felt a little edgy and wanted to try it out on my laptop.  I had tried this before with a live cd and it really didn't like my laptop and I didn't wanna figure out what was goin on.  This time I was fairly determined to get it workin.

I burned a desktop copy for my laptop.  Tried to do an install and it failed pretty quick.  The forums, I knew, were the place to go, and what do you know!  I found out really quick that there was a problem with the ATI video card I had.  And there was a detailed work around to get it going!  Great!  I'll do that!  

By this time, I had done a lot of reading around on the forums and found out where things were.  I did a lot of reading to get a good foundation.  Lotsa neat stuff in the newbie area to read.  And I found some neat stuff in the install and hardware areas, too.  All this reading actually paid off in helping me get installed on the laptop.

The work around had me download the alternate install, and install with text mode.  During the install it asked for monitor resolutions amongst other things and it proceeded along.  All pretty routine, and easy.  Around 85% of the package install, it failed, and I couldn't immediately figure out why.  So I rebooted.  Only to find out my windows partition wasn't booting any more!  oh, no!  well, not a HUGE oh, no, as I thought about it.  The only thing on there that I really didn't wanna lose was my BOINC credit.  And I'd deal with that, I guess.  So I calmed down and went back to the forums to read.  I looked around and found a couple possible answers.

One suggested using fixmbr from the windows recovery console.  I tried it and it, it said it fixed it, but windows still wouldn't boot.  

It looked to me like I had a dead laptop.  So I did what any sane person would do at this point.
I made a pizza.  
I knew I had to walk away and think about it for a minute.  So while I was makin the pizza (I make them by hand, and I make my own dough, which happened to be rising at the time, so it was all ready to go), I thought about what was goin on.  I determined the best way to go was to try to install Ubuntu again and get grub going, as someone else on the forums suggested.  So I attacked it from that angle, cuz I really wanted to get it on my laptop.

While goin through the install again, I realized the first time through, I had picked a bad resolution for my laptop.  It fully clicked now, too.  At 85% last time, it had stopped on one of the X11 files.  This time I chose correctly, it fully installed, and in the end only 'failed' to complete because I hadn't set up the network.  That was the other thing.  The first time through, I couldn't get the network working either.  I have a wireless laptop, but for this install, I had it hardwired to my router.  I wasn't concerned yet, though, because things were falling into place.

Anyway, I rebooted, cuz I really wanted to see if windows was up.  It was!  However BOINC was screaming at me to let it out over the network so it could report some work it had done!  It wouldn't connect to the internet and for the life of me, I couldn't figure it out!  My firewall wasn't the cause because I was connecting to my local network and router.  Just in case I shut it down. However, the log files didn't record any blockage, and it had always been very good at that.  Anyway, after foolin around with it for a bit, I decided to cold boot, and wammo, it worked.  I hadn't done a cold boot through this entire thing.  Guess it really wanted one.

Got my BOINC projects updated, at least!  That worry was over!

So I reboot again.  I stick the CD back in to fix my network.  I'm sure there's a lot easier way to do this, but I had no idea how to do it.  I did a repair install, and I walked through it and set up the network.  It failed to attach again, but the pizza and the garlic was kickin in, getting my brain to function again, and I realized I needed to set up my router for the network card.  It was set up for the wireless, but the wired card had a different MAC address.  I have MAC filtering set up on the router.

I fixed that up on my other computer and I just retried to connect to the network and ANOTHER wammo!  It worked!  Automatically configured, too, with the DHCP I have set up.

It finished installing, came up told me X11 had problems loading, ya ya, I know.  It failed out, I logged in the terminal and followed these instructions: 
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Only minor problems with it.  Because I was doing this on Release day, well, for me it was techinally after cuz it's now 3:30am and this was a couple hours ago, the connections were timing out and I kept having to retry them a few times before I got all the updates.  GREAT easy to follow instructions btw!  Thanks to that poster for sure!

After the update, reboot, Wammo!  Ubuntu's brown screen shows up on my lappy!  As a TRUE bonus, it IMMEDIATELY recogized my wireless card, and asked to set it up right then and there!  WOW!  I was REALLY pleased with that!  I have an Intel 3945abg card.  It hasn't let me down yet.  I just had to remember what my WPA password was.  Hadn't typed it out in ages, and it was LONG.  I had it written down, though, and secured on my TrueCrypt volume on my xp box, so I got it in and good to go.  That's one thing I haven't sucessfully set up on here yet.  TrueCrypt.  Hope there's a nice alternative that I haven't found yet.

So what was the first thing I installed?  BOINC!  Got it up and running fast so I wouldn't miss out on any more credit than I had to!

So what's the moral of this insanely long story?
1.  Pizza is good brain food! (it was a vegetarian pizza, too!)
2.  Have patience with your install!  
3.  The forums are your friend!
4.  Who needs sleep when you're having this kinda fun!

Thanks to all the posters that made it possible for this newbie to get Feisty Fawn installed on TWO of my systems!  One of them dual boots, too!  You guys are great, and I hope I can help the community in some way once I figure out what the heck I'm doing!  I'm having fun and learning lots of new stuff every minute I spend working on these systems.
:popcorn:

---

### Post by rajeev1204 on 2007-04-20
Welcome :) :)

---

### Post by ImpelGD on 2007-04-20
Thanks for the nice read!

> **Gustave said:**
> ...I'm having lots of fun with Ubuntu...
...
You guys are great, and I hope I can help the community in some way once I figure out what the heck I'm doing!  I'm having fun and learning lots of new stuff every minute I spend working on these systems.
I echo those sentiments. :)

> **Gustave said:**
> 4.  Who needs sleep when you're having this kinda fun!
'Tis true! I was up until after 3am this morning getting Ubuntu installed and fixing what Windows Vista (which I've now uninstalled - feels exactly like XP but with a nicer GUI and lack of driver support) had done to my WinXP boot sector, but it feels great to a fresh, real OS to use and learn about. :grin:

Hmm... pizzaaaa.

---

### Post by ironfistchamp on 2007-04-20
Hehe "wammo"

Glad everything is working for you now. Sounds like it was quite a trip. 

Oh and btw, pizza is not just brain food... it is the only food that is worth your time :p 

Mmm pizza. Damn wish I wasn't in a lesson right now I would go and get some.

Ironfistchamp

---

### Post by eentonig on 2007-04-20
Funny reading story. The way you wammo'd in there, sounded like you were heading for a first class crash against the wall....


I'm glad you made it alive and kicking. Guess it wouldn't have been this much fun if you would encounter those kind of problems during a Windows install. :mrgreen:

Have fun learning.

---

### Post by Gustave on 2007-04-20
> **eentonig said:**
> Guess it wouldn't have been this much fun if you would encounter those kind of problems during a Windows install. :mrgreen:


Are you kidding?  I've been using windows since 3.0 and I actually had a copy of an older version in one of the places I worked.  I've had MUCH MUCH MUCH worse problems with that system and needed to figure out problems without the aid of the internet.  I recall arguing with hardware vendors while I was working in one place over the phone.  Thankfully I wasn't paying for those phone bills.  Bad drivers are the bane of any operating system.  But I still enjoyed working with the systems.  I dunno what it was.  They always held an appeal for me.

There were some really nice posts on what I should expect from my Ubuntu experience.  Entering with an open mind was one of the things that really stuck out and it's true.  Can't focus on what was with whatever I was using before.  This is new territory.  

Treat her well, get to know her, and she'll respond appropriately!

---

### Post by verb3k on 2007-04-20
Welcome Home :) :)

---

