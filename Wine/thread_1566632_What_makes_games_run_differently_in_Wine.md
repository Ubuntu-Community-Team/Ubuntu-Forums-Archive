---
title: "What makes games run differently in Wine?"
date: 2010-09-02
forum: Wine
---

### Post by Aydos on 2010-09-02
I am trying to learn more and more about running Linux so I can finally make the final swap. My main problem is I am a gamer and I cannot always play my games on Linux. I do not mind doing some work to get them going, but as we all know some games just wont work properly or at all.

Now I work in IT so I am very knowledgeable about computers, but we do not using Linux at work so I am learning everything on my own. I plan to go primarily into networking down the road so I know that if I have a great understanding of Linux and Unix commands it will be very helpful.

Anyways, sorry for the rambling, I am trying to understand WINE a little better. What is does it do differently for games to make them run so much differently. I know you have to load different winetricks and things to get a game working, but what stops us from getting all the usual background things set up like drivers, directx, .net, vb runtime, etc...

As an example, I love to play MMOs and WoW runs flawlessly in WINE. However, if you look at the AppDB for Warhammer Online it is virtually unplayable. I have not tried it yet, but that is what it says. That is my current game and I play several hours a day so it makes logging into Linux a mute point for me. WoW and WAR have very similar graphics imo so I am not sure why one would run flawlessly and the other would not run in a playable way at all. I see that a newer MMO Fallen Earth runs well in WINE as well.

I also know that some FPS with amazing graphics will run. It just blows my mind that some games can and others cannot even though it seems like we just need wine to trick the OS into thinking we have windows packages running in the background.

I want to have a better understanding of this and I want to use Ubuntu 100%, but I cannot until I can game on it. I know it is the game developers that are to blame for this.

Thanks for any responses or comments.

---

### Post by cwwilson721 on 2010-09-03
You already answered your own question, albeit probably without really seeing it.

You stated:
> ...It just blows my mind that some games can and others cannot even though  it seems like we just need[COLOR=Red] wine to trick the OS into thinking we have  windows packages running in the background[/COLOR].There is the crux of the matter.

Windows, as you know, is "closed source" or "proprietary". MS does NOT want all of their 'secrets' out in the public. Linux is "open source" where everybody can see everything (At least, that's the idea...).

Linux and Windows kernels are as different as night and day. As are their drivers, APIs, modules, and that you can run Linux without a GUI at all. A GUI is just a way to type with your mouse, as far as Linux is concerned.

Linux/wine has to 'divine' what 'hooks' to the various Windows APIs are being used, and how to 'trick' the various programs that those hooks actually exist. Due to the VAST numbers of code written into just the kernel for Windows, not to mention dlls, and the like, I think the wine developers have done a phenomenal job of doing what they have been able to do.

The other issue is the registry. It has so many doo-dads and settings... I believe 'hive' is an apt word the MS used for quite awhile to describe it. Linux/wine just can't 'emulate' (for lack of a better word) all of those settings.

Plus, some programs install other stuff, dll's and other bits of code, all over the Windows system. Again, trying to account for every variation is just mathematically difficult.

That WoW runs so well is partly WoW's fault. It's the BIGGEST game of it's kind, and ***can run from just it's own folder***. Other programs may or may not. Due to it's popularity, and easy of running, wine tends to make sure the WoW community stays happy. The same can be said for Office, too. It's SO popular, wine almost HAS to make sure it runs.

Just wait awhile for the wine developers to get around to focusing on your game/program of choice. When they do, they tend to make it work. 

Sort of. Kinda. Maybe.

---

### Post by Aydos on 2010-09-03
Thank you for the informative post. It definitely gave me a new perspective of the whole thing.

So I am guessing that after a while if you start getting use to all of the background things that WINE needs, your WINE will slowly and slowly be more prepared to run games.

My next step is going to have to be my choice in games lol. I mainly like PvP MMOs and those seem to be less popular to the general public and work much worse in WINE. Aion and Warhammer Online are both hard to get running or make them work properly.

I have already cleared all of the raid content in WoW many times over and generally hate raiding so WoW never keeps my attention long.

Would it not be easier to make a MAC version of a game work in Linux than the windows version ? 

I know that WAR has a mac client and they are both unix based so I was just curious if there was a way to maybe try and make it work.

---

### Post by ajackson on 2010-09-03
I think the Mac version of WAR is just WAR wrapped in Transgamings equivalent to Wine (Cider is it?).

From what I've read Aion runs OK it's just the need to circumvent it's native launcher as the NCLauncher is a .NET app that isn't too wine friendly.

---

### Post by Aydos on 2010-09-03
This is what was confusing me. It does say that the Mac Version of WAR is using cider, but  I know people who play the mac version and it supposedly runs flawlessly, but the pc version in WINE is virtually unplayable. Also if you look at Cedega which as far as I know is the Linux version of Cider, it says that it does not work properly. 

I also heard that the Mac version runs in Open Gl and not DX so I am not sure how to accomplish this.

I just want to 100% swap over to Linux, but me and my friends play this game daily so I am wanting to do what I can to not have to dual boot any further. I was not sure if having a Mac client made it easier or not. 

Any thoughts or ideas would be awesome. I know the game has an endless free trial so I am shocked that there has not been any recent usage of the game in Linux. The free trial is awesome you get the whole first tier of the game to PvP non stop in and there is so many people in the endless free trial. I just hope the exposure helps. Any insight would be awesome and if anyone with further knowledge of setting up games in Ubuntu wants to take a stab at it with the endless free trial from warhammeronline.com please do you would make my day.

Thanks for the responses.

---

### Post by cwwilson721 on 2010-09-03
Eventually, the wine developers will probably turn their collective eyes to Warhammer. It just takes time...

One thing that MAY work (don't know if it's feasible/usable in Warhammer) is to use VMWare Player...I know, I know, the performance hit is HUGE, but it DOES support 3d accelleration better than any other VM out there. BUT, in my case, it goes like this:
(Using WoW as an example):

[LIST]
[*]WoW/wine  FPS about 45-60, 30-45 in raids, 85+ in vacant areas (OpenGL)
[*]WoW on Windows  FPS 40-50, 25-30 in raids, 50-60 vacant (DX)
[*]WoW in VMPlayer FPS 15-20, <5 raid/Dal, 25 vacant (So unplayable for me) (DX) (Have not tried OpenGL on VMWARE. Can't be much better)
[/LIST]
All the above played with exact same options, addons, etc., and pretty average numbers

Haven't tried Warhammer yet. But might be feasible...But since VMware IS a 'emulator', and another layer of software, I don't hold my breath. Performance HAS to get a hit.

Give it a shot. What is the worst that can happen? A few hours tinkering with your computer? (To me, that's FUN anyway)

---

### Post by ajackson on 2010-09-04
> **Aydos said:**
> This is what was confusing me. It does say that the Mac Version of WAR is using cider, but  I know people who play the mac version and it supposedly runs flawlessly, but the pc version in WINE is virtually unplayable. Also if you look at Cedega which as far as I know is the Linux version of Cider, it says that it does not work properly.
You'll find it is a customised version of cider with hacks that solve some of WARs problems but those hacks would cause problems if used in a more generic version of cider/cedega.

---

