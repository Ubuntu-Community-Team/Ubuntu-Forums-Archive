---
title: "Broken WoW Lottery"
date: 2009-11-15
forum: Wine
---

### Post by bwisdom on 2009-11-15
Hello, Ive posted a couple times in the past few days about a few problems Ive come across with installing and trying to run WoW and now there is a new problem. Before I spoke of being disconnected while trying to login to the wow servers after updating to the current patch. Well I've been able to reproduce the error and it is only because I didn't have the SET gxApi "opengl" line in my Config.wtf. Well all would be awesome if WoW happened to work after that. Now that I have put that line in the Config.wtf I get one of three problems.

1) The game crashes with a "Error #132". Ive read on this and from what I can tell it has something to do with memory problems and Blizzard themselves don't know how to fix the error

2)A box will pop up saying something about hardware changes and wanting to use them. Ive come across this box a few times and a few different things will happen (even after clicking the same answer). It will either pop a Error #132 again or it will just do nothing.

3)Everything will start fine and I start to believe that it is going to start then it flashes to login screen and the program disappears, its not in the system monitor or anything, it is just gone.

Ive recently deleted the whole Config.wtf file and tried again without the file at all and now just with the "SET gxApi "opengl"" line. What will happen is that it will start the video and it doesn't matter if I watch the video or not, as soon as its done or I hit escape it crashes to the Error #132.

Im using:
wine 1.2
ubuntu 9.10
ATI Technologies Inc M71 [Mobility Radeon X2100] (graphcis card)

Thanks in advance

---

### Post by CDNeh on 2009-11-16
Common Problems that cause "Error #132 "


[LIST=1]
[*]RAM issue. Download memtest86 (The CD-Boot version, also a Floppy Disk version too if you still have one of those). Turn off your PC and remove all but your first stick of RAM, turn it back on and run the first test. The test takes about 30mins if pass turn off your PC and place another stick of RAM in the first slot and test that one. Repeat the same steps for any other sticks you have.
[*]Sound Card/Driver Issue.  Update to the newest driver versions.  In some cases, the newest drivers caused a conflict and to fix it you would have to revert back to an old driver.
That doesnt work, try disabling sound all together. If it works when you do that, you know where your problem is.
[/LIST]

Hope that helps.

---

### Post by bwisdom on 2009-11-16
I guess its my fault for not specifying, but I play on a laptop. Im not sure if I can still do the memtest thing and if I cant Im not sure im comfortable with taking apart my laptop to remove RAM. Ive checked into the memtest thing and it doesnt saying anything about removing RAM. I may try it later without having to touch anything. Right now though I am studying for an accounting test.

On number 2, how do you disable the sound if you cant get past the intro video? As far as drivers go, the hardware manager thing says I have no drivers to download. Ontop of that I dont have any snazzy sound card (again cause its a laptop) so Im not sure there is anything out there besides the ubuntu standard one.

I also read what you put in the post where I linked this thread, I tried that cause your problem sounded similar to mine except I could get past the video and it would crash at the login screen with the 132 error and the sound still playing in the background.

---

### Post by CDNeh on 2009-11-17
If your laptop is under warrenty still i would not suggest opening it up and removing ram.  With my laptop there is a small square on the bottom with 2 small screws..  If i open it, there is the 2 sticks of ram.  Which i have removed and upgraded since purchase.
The reason why you take one out and leave the first stick in, testing one at a time making sure one works, one at a time  Just the way i have always done it.

Sound drivers in your bios?  everything is onboard on a laptop.  There should be somewhere in your bios to turn on and off your onboard sound.

As for you having the same problem i had..  When i closed WoW after it crapped out, my screen resolution was still all pooched.  When i ran it again with my Ubuntu resolution all crap it loaded fine but the WoW folder was locked with permissions.  I just had to manually change the permissions(no idea why it did that).
After that i went into wine and checked off Emulate a virtual desktop and left it at the original settings.  Once in game i changed my settings to what i wanted and now it works great.

I did a google search on your error and its clearly some kind of hardware problem.  Either drivers or just not good enough to run the game.  Have you tried running another Windows based games to see what happened?

---

### Post by bwisdom on 2009-11-17
Ok so I ran the memtest anyway to see if there were errors and there were none although I did learn something. Apparently I am running the dreaded GM965/GL960 chipset which I have heard has a lot of problems with WoW and maybe other games too.

I didnt see any sound anything in the BIOS so instead I just disabled it in wine to maybe try that. It was a no go either.

Id just dual boot Windows but I can't, the damn install CD doesn't see my harddrive so I am stuck doing this.

Also when mine crashes it does the exact same thing (messed up resolution and all) the only thing is that when I try and run it again it just crashes again. I dont have a problem with permissions because I found a script for it. The reason the permissions change is because blizzard screwed up somewhere and now the permissions will just keep changing themselves.

---

### Post by Alatar1 on 2009-11-17
You can avoid the permissions problem by not using the launcher for wow...
and as for the crashes im not sure, I do know that ATI+ubuntu = bleh

---

