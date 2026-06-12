---
title: "First Impressions: Jaunty 9.04 (but I'm a windows guy?!)"
date: 2009-07-25
forum: Testimonials &amp; Experiences
---

### Post by artemenko on 2009-07-25
I'm a windows guy, have been forever.  After a visit with a family friend a couple weeks ago, he handed me a CD with the letters spelling "Jaunty" on it.

The thing loaded like lightning.  Recognised my wireless mouse while it was still setting up, and took me about 10 clicks from cold boot to WEP key to Internet.

A few observations:


[LIST]
[*]Terminal is cool, I feel like a mechanic for my PC.  "Sudo Chop!"
[*]Wiggly windows are nice, installed Compiz to get rid of the nasty tearing by adjusting v-blank.  Oh and "sudo apt-get update" is amust before trying to enable extra effects in Appearance>visual effects.
[*]Good Lord -- why is my sound so awful?  "Alsamixer" helped, turned down all the vertical bars that were red by default.
[*]Did I mention this was installed on an older laptop, why is this running so fast?
[*]Most of the compiz/beryl/fusion effects are hokey, but expanding my desktop to 4 sides in the form of a cube is actually useful.
[*]And lastly, I've re-installed the whole thing a couple of times just because it's fast and I'm obsessed with haveing the perfect setup.  If something breaks, I just re-do the whole thing -- is that normal?
[*]Google auto-completes most questions I have about Ubuntu right in the search bar, which gives me confidence to continue... Answers are out there.
[/LIST]

So far this has been a lot of fun.  Who knows what I else I can do with my four year old "gaming laptop"DELL XPS Gen 2.  This is about as powerful as it's ever been.

What else am I missing?

---

### Post by starcraft.man on 2009-07-25
Just a few notes:

I strongly recommend against WEP, even when using it for compatibility reasons (i.e. legacy hardware in house). It's so easily hacked now, it isn't funny. Any variant of WPA gives you infinitely better security.

You shouldn't have to reinstall to fix most problems, unless you remove/cripple critical services, and that's unlikely. Unless you describe the problem with more detail than "something breaks" we can't help. Details on the name of the program and what you did will go a long way. Do a separate thread though.

If you need some documentation to get started, see my sig. Otherwise, have fun playing around. Just make sure you store your data on a separate partition if your doing so much experimentation/reinstalls.

---

### Post by murphykieran on 2009-07-25
> **artemenko said:**
> [*]Most of the compiz/beryl/fusion effects are hokey, but expanding my desktop to 4 sides in the form of a cube is actually useful.In my opinion, all desktop effects are hokey.  It doesn't matter whether you've got Ubuntu, Mac OS X, Windows Vista or whatever, having windows and menus with transparent effects, wobbly effects, etc. doesn't make you any more productive with your PC.  It's all just pointless eye candy and I have most of the effects switched off because it's just a waste of CPU cycles.

---

### Post by infinitejones on 2009-07-25
Oh hell yeah. Welcome aboard. I was in the same position as you about three years ago when I saw a blog post about some weird OS called "Hoary Hedgehog" which I had to download just because of the name. Lo and behold, I was hooked on Ubuntu after ten years of Windows.

Your last point links in with my favourite thing about Ubuntu (and linux in general). When I want to do something, or solve a problem, or just generally experiment with what my PCs can do, I'm 99% confident that someone, somewhere has already done it and posted it online. There are a million Ubuntu blogs (try googling "Tombuntu" or "Ubuntugeek" or "Psychocats Ubuntu"), plus Ubuntu Forums, and they always have the answers.

And the best thing about this is that I *learn* stuff at the same time. Even if the solution to what I'm trying to do involves copying and pasting a load of commands to the command line (btw - 'sudo chop' - brilliant), I take the time to try and work out what it all means, and what the effect will be, before I do it. So even though I'm not a techie/hacker/coder in the slightest, I have learnt more about how computers work in three years with Ubuntu than I have after ten years with Windows.

Examples:

I have a Nokia N95 phone that I use as my portable media player. With the help of Google and Ubuntu Forums, I have written a couple of little scripts that work together to automatically sync the contents of the SD card in the phone with my "Music" directory in my home folder when I plug the Nokia into my laptop. So to get music on my phone, I just rip a CD using Rhythmbox and plug my phone into my laptop. Bored with that album? I delete it from laptop (or move it to another directory) and plug my phone in, and it automagically disappears from my phone.

Yes, I know software exists for Windows that will do the same thing, but this is all done with two one-line scripts - not a 50MB download that uses 100MB of RAM and adds ten seconds to my start-up time (yes, Nokia PC Suite, I'm looking at you).

Second example - your point about re-installing the whole thing - if it's faster and more convenient for you than working out how to fix it, then yeah, why not?! Sooner or later you'll start working out how to fix things without re-installing but for now, knock yourself out.

But one suggestion - next time you re-install, put your home folder in a separate partition. You'll find instructions on how to do this online (just Google "ubuntu home folder separate partition") and the Ubuntu installer makes it really easy when you know what you're doing. Do it because Ubuntu stores almost all your settings in the home folder - everything from what theme you're using, to what applets you have in your panel, to where your music player looks for your music files. Plus all your email, browsing history, browser plugins etc are in your home folder. (Hint - go to the home folder, and hit ctrl-H. See all those extra folders that have appeared? That's where it all is!) 

So if it's all in a separate partition, then when you're re-installing, you just tell Ubuntu **not** to format that partition, and when your nice fresh no-longer-screwed-up install of Ubuntu is ready, all your settings are exactly how you like them. 

Good luck, welcome aboard, and come back here often!

---

### Post by theozzlives on 2009-07-25
> **murphykieran said:**
> In my opinion, all desktop effects are hokey.  It doesn't matter whether you've got Ubuntu, Mac OS X, Windows Vista or whatever, having windows and menus with transparent effects, wobbly effects, etc. doesn't make you any more productive with your PC.  It's all just pointless eye candy and I have most of the effects switched off because it's just a waste of CPU cycles.

But their kewl!

---

### Post by starcraft.man on 2009-07-25
> **murphykieran said:**
> In my opinion, all desktop effects are hokey.  It doesn't matter whether you've got Ubuntu, Mac OS X, Windows Vista or whatever, having windows and menus with transparent effects, wobbly effects, etc. doesn't make you any more productive with your PC.  It's all just pointless eye candy and I have most of the effects switched off because it's just a waste of CPU cycles.

See desktop wall plugin in compiz. Called grid in kwin. Very useful IMO for productivity and multitasking. Allows for expose features (i.e. drawing all desktops and moving windows around em) and at least desktop wall allows you to just drag windows over edge of screen and onto next desktop. There is also an option that just draws all your open windows (not the desktops themselves as with wall) that lets ya move quickly from one to another seamless. 

I'll agree that many other plugins offer no real advantage, like wobbly windows or animations. They are just eye candy. If you want fine control of your compiz plugins and options install and use the compizconfig-settings-manager package. Adds a control centre to System > Preferences  so can turn on and off and configure at will all options.

---

### Post by jmszr on 2009-07-25
artemenko,

Neat,huh?

 I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

That sticky covers a lot of ground.

Part of the fun of Ubuntu is getting into it until you break something and then figuring out how to fix it. And one can always reinstall if you really,truly bork it.

Have fun!

Edit: +1 for a separate /home partition

---

### Post by CatKiller on 2009-07-25
> **artemenko said:**
> 
[LIST]
[*]Most of the compiz/beryl/fusion effects are hokey, but expanding my desktop to 4 sides in the form of a cube is actually useful.
[/LIST]
The Scale plugin (a clone of OS X's Exposé) is useful too, as are the live window previews in the Window List. Offloading the rendering of windows to the GPU rather than having them drawn by the CPU is definitely useful, but then the added overhead of the animations often offsets this advantage.

> 
[LIST]
[*]And lastly, I've re-installed the whole thing a couple of times just because it's fast and I'm obsessed with haveing the perfect setup.  If something breaks, I just re-do the whole thing -- is that normal?
[/LIST]
No, this isn't normal. Re-installing is quick, but you don't learn anything from it. Fixing or removing whichever configuration file you've broken teaches you much more about how it all works. And re-installing is only quick when you haven't done much or generated any data that you want to preserve. It can be a pain for the other users of your machine, too :)

---

### Post by Sef on 2009-07-25
Moved to Testimonials & Experiences.

---

### Post by artemenko on 2009-07-25
Thx Infinitejones

> But one suggestion - next time you re-install, put your home folder in a separate partition. You'll find instructions on how to do this online (just Google "ubuntu home folder separate partition") and the Ubuntu installer makes it really easy when you know what you're doing. Do it because Ubuntu stores almost all your settings in the home folder - everything from what theme you're using, to what applets you have in your panel, to where your music player looks for your music files.

Ha I was looking for something like this.  I am still just playing around, but this helps a lot.

---

### Post by steveneddy on 2009-07-25
Alright! Welcome.

Check out some of the links in my sig for more info that you can actually use.

Cheers

---

### Post by HappyFeet on 2009-07-25
> **artemenko said:**
> If something breaks, I just re-do the whole thing -- is that normal?


At least with me it *was* normal. I know enough now that I don't have to reinstall linux to fix it. But then again, I can't even remember the last time it broke. But I know what you're saying. I have always been in search of the perfect install, no matter what OS I was using, and have come closest to reaching that perfection (nothing's perfect) with Ubuntu. And with linux I now feel truly at peace with my computer. At least now I have total control over my OS.

Btw, when *you* (anyone reading this) daydream or think about computers and tech, do you think in windows terms, or linux terms? I pretty much think in terms of linux most of the time. I know windows *very* well, but it's basically always on the back burner, on low heat.

Anyway, glad to hear you like it.

---

### Post by Chemical Imbalance on 2009-07-25
> **murphykieran said:**
> in my opinion, all desktop effects are hokey.  It doesn't matter whether you've got ubuntu, mac os x, windows vista or whatever, having windows and menus with transparent effects, wobbly effects, etc. Doesn't make you any more productive with your pc.  It's all just pointless eye candy and i have most of the effects switched off because it's just a waste of cpu cycles.

+1

---

### Post by philcamlin on 2009-07-25
> **Chemical Imbalance said:**
> +1

+2 i couldent agree more

---

### Post by Dullstar on 2009-07-26
Good to hear Ubuntu's great for you!

---

### Post by HappyFeet on 2009-07-26
> **philcamlin said:**
> +2 i couldn't agree more

+3  

:p

---

### Post by lykwydchykyn on 2009-07-26
> **murphykieran said:**
> In my opinion, all desktop effects are hokey.  It doesn't matter whether you've got Ubuntu, Mac OS X, Windows Vista or whatever, having windows and menus with transparent effects, wobbly effects, etc. doesn't make you any more productive with your PC.  It's all just pointless eye candy and I have most of the effects switched off because it's just a waste of CPU cycles.

[Them grapes sure are sour, aren't they?](http://aesopfables.com/cgi/aesop1.cgi?sel&TheFoxandtheGrapes2)

Come on, lighten up.  What's your CPU so busy with that he can't make things a little more fun?

> And lastly, I've re-installed the whole thing a couple of times just because it's fast and I'm obsessed with haveing the perfect setup. If something breaks, I just re-do the whole thing -- is that normal?

It's normal for the first few months.  Once you learn more about the system and have some time invested in an install, you'll want to figure out your problems.

---

### Post by HappyFeet on 2009-07-26
Don't get me wrong, I think there is a time and place for visual effects, but lately, I'm into my computer doing what I *want*, *when* I want.

---

### Post by Dullstar on 2009-07-26
I've only reinstalled Ubuntu once, and apparently I started early into Jaunty's life.  The reason?  It was the only way I could recover Ubuntu after I had to wipe Windows and reinstall it.  However, it was just a matter of reinstalling Ubuntu with Wubi, then using the Wubi partition file from earlier.

---

### Post by HappyFeet on 2009-07-26
Partitioning has become a lost art. (cfdisk anyone?) (I like to think I'm good) People expect drives to just magically partition themselves. That's the 1# reason first timers have trouble. To them, there should just be a "next" button, and just move on.

linux may require some re-learning, but it's worth it. It has even made me a better windows tech too. I'm much more aware of problems, regardless of OS.

---

### Post by Dullstar on 2009-07-26
I'm looking for a little help with the partitioning.  I asked my brother for help, but it doesn't look like he's going to get around to it anytime this century.

---

### Post by moster on 2009-07-26
> **artemenko said:**
> 

What else am I missing?

Hell yes!

Hey, push those effect to the max, you only live once! :D 
(and you actually waste GPU, not CPU because compiz work in opengl)

Install emerald. It work with compiz. Then you can apply .emerald themes that has no concurecy on win and mac plus you can edit it and fine tune every aspect of window. Ok, let go.

```
sudo apt-get install emerald
```

It will appear in menu system>preference>emerald

then, to apply it to load ubuntu startup (you can always go back). Go to menu system > preference > compiz config setting manager. When window load, click on "effects" then "windows decoration". Now replace where say "command" this "/usr/bin/compiz-decorator" with this "/usr/bin/emerald". That will ensure that emerald will load at startup. Copy back when you want again plain compiz. Now restart computer or only X.

ok, now go this page and download some .emerald themes. That is under compiz in this page. After download, you can simple add it with button in emerald window.
[http://www.gnome-look.org]("http://www.gnome-look.org")
You can also search synaptic, there are some emerald themes there too.

On the end, make your terminal transparent to start looking even more pro to XP users :) and take a look at this really good looking themes, its really something. Some guy show it to me, and I am not sure why they are not in Ubuntu integrated.
[http://francois.vogelweith.com/?page_id=16&lang=en]("http://francois.vogelweith.com/?page_id=16&lang=en")

---

### Post by infinitejones on 2009-07-26
> **Dullstar said:**
> I'm looking for a little help with the partitioning.

Here's a couple of links thanks to Google:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Psychocats is very much tried and tested from my point of view... highly recommended. \\:D/

---

