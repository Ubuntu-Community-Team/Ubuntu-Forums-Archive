---
title: "Windows chokedown"
date: 2010-06-19
forum: The Cafe
---

### Post by del_diablo on 2010-06-19
Just played a game for about an hour, had 2 background applications running.
Windows caches everything except the game to disk after about 1 hour.
I close the game, I spend the next 5-6 minutes watching the computer just lagging!
And this really bothers me when my HD is capable of reading 50mb on a straight segment, which means that somebody did not cache everything as a ramdisk, but rather as random read material.
I can even BET that the applications did not leave as much as 100mb worth of data in the cache, which should be read in 2-3 seconds... NOT 4-5 minutes.
So the options are:
A: Remove the 500mb swap file, which results in RANDOM popups of "DOOOOM!", which can not be disabled.
B: Don't have background applications............ right
C: Hope Microsoft fix their ****
D: Find a registry hack for it
E: Find a random pay applications which fixes it....

None of these options are feasable, and it REALLY REALLY bothers me.
On the other hand, why won't Mass Effect run under wine? :(

(Yes, I am aware of the appdb entires, but they do not mention problems)

---

### Post by Queue29 on 2010-06-19
And on the other hand, describe what happens when you try to run your game in Ubuntu.

---

### Post by Timmer1240 on 2010-06-19
We know we know we know about Windows!And all the fun!And thats why Im running Linux you dont have to tell ME about it!Karmic Koala 9.10 Fast as a bullet absolutely no lag all this for only what FREE priceless!I would pay 100 bucks for this Operating system!But its free fast secure capable customizable loads of free software its AWESOME.Windows no thanks keep it!

---

### Post by Xianath on 2010-06-20
Sounds like a classic PEBKAC. 512MB swap implies you have 256MB of RAM. If you don't, then you're doing it wrong. If you do, then gaming with apps in the background is wrong. In other words, you're doing it wrong either way. One more thing - ever tried one of [these]("http://www.mydefrag.com/")? Seriously. Do your homework first, then blame others.

---

### Post by del_diablo on 2010-06-20
512 swap implies I hardset it to 512. it originally wanted to be flexible(read: wants to eat up the partition).
Why would anything run completely decrapted code except for anything coded by Adobe? 
And I defrag regularly, the consequense of not doing so is far too great. Besides this is not XP, which saves me some minor inconviences.

_Queue29:_ Something about MSV80C.dll or something missing, tried to import before. DX10 also missing, but I got it running before and it did not do the trick completely. Appdb does not mention the VCR2005 redist, why not?
Frankly Mass Effect 1 is harder to get to run :(

---

### Post by Rainstride on 2010-06-20
> **del_diablo said:**
> 512 swap implies I hardset it to 512. it originally wanted to be flexible(read: wants to eat up the partition).
Why would anything run completely decrapted code except for anything coded by Adobe? 
And I defrag regularly, the consequense of not doing so is far too great. Besides this is not XP, which saves me some minor inconviences.

_Queue29:_ Something about MSV80C.dll or something missing, tried to import before. DX10 also missing, but I got it running before and it did not do the trick completely. Appdb does not mention the VCR2005 redist, why not?
Frankly Mass Effect 1 is harder to get to run :(

use winetricks.

---

### Post by del_diablo on 2010-06-20
After some searching:
[QUOTE="hidden somewhere on the appdb"]
- d3dx9
- d3dx10
- vcrun2005
- physx[/QUOTE]

Installed.
The game complains about a bunch of .dll, the result is windows ripping.
Which leads to 2 problems.
```
wine MassEffect2Config.exe 
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": libxml2.so.2: wrong ELF class: ELFCLASS64
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"msxml3.dll"
err:ole:create_server class {2933bf90-7b36-11d2-b20e-00c04f983e60} not registered
err:ole:CoGetClassObject no class object {2933bf90-7b36-11d2-b20e-00c04f983e60} could be created for context 0x7
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": libxml2.so.2: wrong ELF class: ELFCLASS64
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"msxml3.dll"
err:ole:create_server class {2933bf90-7b36-11d2-b20e-00c04f983e60} not registered
err:ole:CoGetClassObject no class object {2933bf90-7b36-11d2-b20e-00c04f983e60} could be created for context 0x7
```

How do I get around this? Dumping msxml13.dll into the folder does not do the trick, I need to run that util to import mass effect 1 savegames.
So how do i get it to run?

Another note: Using a pure wineprefix and installing the needed 4 packages results in interisting errors when attempting to run:
```
WINEPREFIX=~/.war3 wine MassEffect2.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\Maxtor\\Atle\\Spill\\Mass_Effect_2\\Binaries\\MassEffect2.exe" failed, status c0000142
```
Running without prefix on the other hand:
At the least i got further than last time, now the crash is before the "open sequencese" itself is loaded, after the open cryptic plot talking.

:(

---

### Post by pwnst*r on 2010-06-20
> **Timmer1240 said:**
> We know we know we know about Windows!And all the fun!And thats why Im running Linux you dont have to tell ME about it!Karmic Koala 9.10 Fast as a bullet absolutely no lag all this for only what FREE priceless!I would pay 100 bucks for this Operating system!But its free fast secure capable customizable loads of free software its AWESOME.Windows no thanks keep it!

Where's the Linux tattoo and fan boy flag?

---

### Post by Timmer1240 on 2010-06-21
> **pwnst*r said:**
> Where's the Linux tattoo and fan boy flag?

Ya I guess I get carryied away in my excitement windows can be usefull too for gaming ect.Its just that I seem to have a lot less trouble with Ubuntu!Tattoo and flag on the way!Guess you Pwned me!

---

### Post by Xianath on 2010-06-21
> **del_diablo said:**
> 512 swap implies I hardset it to 512. it originally wanted to be flexible(read: wants to eat up the partition).
Why would anything run completely decrapted code except for anything coded by Adobe? 
And I defrag regularly, the consequense of not doing so is far too great. Besides this is not XP, which saves me some minor inconviences.

What I was referring to was that 512 MB of swap are most commonly used on systems with 256 MB of RAM (old rule of thumb, somewhat invalidated by modern kernels but still quite true). Also, the Windows defrag doesn't take care of swap, you need a third-party app, which is what I believe you alluded to in your original post. I just pointed you to a free one that works better than all the commercial ones I've tried.

If this is not XP, then it's either 9x/ME (hope not!) or Vista/W7. If the latter, we go back to the original argument of RAM vs. swap. If you have enough RAM, disable swap altogether -- which, if I am interpreting "RANDOM popups of DOOOOM!" correctly, is not the case. Therefore you need to increase swap to 2x your RAM if you have less than 4GB) or make it the size of your RAM if you have 4GB or more. Then, defrag everything INCLUDING swap using whatever util catches your fancy. I've seen dozens on Windows and Linux machines brought down to their knees by fragmentation. Yours is probably not very different.

Also, the fact that your HDD reads 50MB/sec in linear burst puts it on the slow side of things. What's seek latency like? How much on-board cache? 

And I'm sorry if I totally can't make sense out of your second sentence.

---

### Post by del_diablo on 2010-06-21
Still, if the apps was coded in such a wrong way they would have crippled performance under normal useage. Which means its irrelevant for the case.
*sigh*
And the random popups exists, a noticeable one was that I would get popups when I had roughly 1 and a half gigabyte of RAM left to use, which would in any case never be used. There is no ways to disable these popups, which makes them bloody useless.
Adding 500mb of SWAP would disable the popup, sadly.

---

### Post by Xianath on 2010-06-21
A smart virtual memory manager would swap out unused data to make room for disk cache and other I/O buffers, not to mention dynamic memory allocation from apps that do need it. If you haven't used an app in an hour, it would be stupid of the OS to keep all of it around, eating memory that could speed other apps. That's why you should have at least as much swap as you have RAM (unless you have TONS of it). You apparently have 2GB of RAM, so give it that much swap and enjoy. If you have a relatively smaller amount of RAM, then swap is not just a luxury, it becomes a necessity, hence the 2xRAM rule of thumb.

---

### Post by del_diablo on 2010-06-21
But on the other hand, why would the OS use 10 minuttes to read less than 100mb of data?

---

### Post by murderslastcrow on 2010-06-21
If you write the software platform poorly, you can count on the third programmers for that platform to care less about optimizations. It seems the large companies and open source programs are the ones most concerned with speed on Windows.

Especially if you're building on top of DirectX, you can count on having all that comes with it, including the higher memory requirement.

I'd just stop running so much crap when you're already busy with a game.

---

### Post by del_diablo on 2010-06-21
Windows default -some deamons
+ Opera(light)
+ Miranda IM(light)
And sometimes skype.
I think thats light enough.
So can should we change thread to "why can't people listen?!" xD

---

### Post by Xianath on 2010-06-21
Skype itself is a resource hog. Miranda is the archetypal spaghetti (a.k.a. G7, or Great Green Gobs of Greasy Gooey Gopher Guts) and Opera, while light, really depends on what you have loaded in it. As to why it would take 10 minutes -- no, it doesn't. It keeps on swapping because it can't figure out what you want to do with your system that very moment. Certainly it doesn't want to swap *everything* back in, just what you're requesting at the moment. So you alt-tab to Miranda and it starts swapping that in. You alt-tab to Skype and it does that, too. Meanwhile your game has gloated on all that RAM and filled it up with textures and other junk that you now don't need so they get swapped *out*. And if you don't have enough swap and/or it's fragmented, your disk starts to thrash. Don't forget all the other happy stuff that Windows likes to do for you when you least expect it.

You have to know how to get the best of your system. Mine has 4GB and no swap (no hard drive, that's why) and it runs like a charm. The only thing that can tax its RAM is Lightroom and when I use that, I don't multi-task (the mere task-switching to, say, Firefox, messes up my color perception for a minute). In the two years since I've had it I am yet to experience what you describe. So maybe you should listen, too. Or not. It's your system, your call. Mine works, I'm happy :)

---

### Post by ikt on 2010-06-21
> **del_diablo said:**
> Just played a game for about an hour, had 2 background applications running.
Windows caches everything except the game to disk after about 1 hour.
I close the game, I spend the next 5-6 minutes watching the computer just lagging!

That's interesting, I play games all the time and don't have this issue, running windows 7.

Are you sure you didn't mis-configure something?

---

### Post by del_diablo on 2010-06-22
*sigh* Why can't people stop gloating?

Edit: What I mean is that you are not helping.
To disable the "likely low memory if major memeory leak presenmt"-popup i need to do a registery hack, which in turn allows some bug related to writing to RAM..... :(
The OS lacks registery hacks and all that, simply because i never bothered so far(read: the last attempt on that did not yield extra performance).

I guess I am just sick and tired of things not working properly, without any good reason for it:
*Bugs in the ATI drivers
*The FLOSS ATI drivers are incomplete
*Windows with its major unreasonable creeps
*And games said to be running in wine is not running at all
*And the "force lock to window"-button in winecfg will never work

In the end, there is no good option at the moment

---

### Post by MCVenom on 2010-06-22
> **del_diablo said:**
> *sigh* Why can't people stop gloating?

Edit: What I mean is that you are not helping.

If you wanted support, I don't think posting in the Community Cafe was a good idea. Also, I haven't really seen anyone 'gloating', per se. And I don't mean to be rude; but you seem to be having trouble articulating some of the things you're trying to say. For example, this:
> Why would anything run completely decrapted code except for anything  coded by Adobe?
seemed a bit hard to make sense of. 

> I guess I am just sick and tired of things not working properly,
It's okay, it happens to the best of us :P 

> without any good reason for it:
Let's take these case by case.

> *Bugs in the ATI drivers
I assume we're talking about Ubuntu here. Yeah, it'd be nice if ATI put more effort into their drivers, or open-sourced them so others could do it. Unfortunately though, considering how things could be I have to give them points just for providing them.
> *The FLOSS ATI drivers are incomplete
Once again, it'd be nice if ATI open-sourced their drivers, it'd help alot. But it's unlikely so far.
> *Windows with its major unreasonable creeps
Yeah Windows has issues, though your problem doesn't seem to be something inherent within Windows itself, per se.
> *And games said to be running in wine is not running at all
It's hit and miss. :P
> *And the "force lock to window"-button in winecfg will never work
Wouldn't know anything about this; but if there's a bug you should report it to the devs so it can be fixed.

> In the end, there is no good option at the moment.

Unfortunately, it doesn't seem so right now, though reinstalling Windows might fix the issue.

---

### Post by RiceMonster on 2010-06-22
> **BlackOtaku said:**
> I assume we're talking about Ubuntu here. Yeah, it'd be nice if ATI put more effort into their drivers, or open-sourced them so others could do it. Unfortunately though, considering how things could be I have to give them points just for providing them.

Once again, it'd be nice if ATI open-sourced their drivers, it'd help alot. But it's unlikely so far.

They released the specs, which is a lot of help to the open source driver devs as is.

---

### Post by MCVenom on 2010-06-22
> **RiceMonster said:**
> They released the specs, which is a lot of help to the open source driver devs as is.
Thanks for the info, I was not aware of that. :)

---

### Post by Windows Nerd on 2010-06-22
> **RiceMonster said:**
> They released the specs, which is a lot of help to the open source driver devs as is.
They did? Maybe I won't have to replace my ATi card in the computer my dad is giving me...(he got a new one and gives me his old computers).

---

### Post by del_diablo on 2010-06-24
> **BlackOtaku said:**
> Wouldn't know anything about this; but if there's a bug you should report it to the devs so it can be fixed.

[QUOTE=winehq]You can prevent the mouse from leaving the window of a DirectX program (i.e. a game.) and the default is to have that box checked. There's lots of reasons you might want to do that, not the least of which includes it's easier to play the game if the cursor is confined to a smaller area. The other reason to turn this option on is for more precise control of the mouse - Wine warps the location of the mouse to mimic the way Windows works. Similarly, "desktop double buffering" allows for smoother updates to the screen, which games can benefit from, and the default is to leave it turned on. The tradeoff is increased memory use.[/QUOTE]

Its a well known bug, its been open from some version earlier than 0.4-5 or something, and its well known. It was not fixed in 1.44, and it may not be fixed in 1.2.rc3.

And you are more or less gloating. :( Just not in the usual manner for the word.

And yes, the ATI open drivers are quite good. The problem is that you can not use them for anything yet(running Archlinux with newest drivers).

---

### Post by MCVenom on 2010-06-24
Gloating? I'm not familiar with it because I don't use WINE often, that's all.

Also, just because someone's sharing their own experience (or lack thereof) with your issue does not mean they are gloating. Often times it is this that helps us get to the root of the problem.

Good luck with your issue man... But don't shoot the messenger. :P

---

### Post by del_diablo on 2010-06-24
Well said.

---

