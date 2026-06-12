---
title: "Steam coming to Linux..?"
date: 2010-04-22
forum: The Cafe
---

### Post by portets on 2010-04-22
sorry if someone posted this already. didn't see anything.

anyway, i just read on phoronix that a script for the mac version of steam mentions linux (original article _**[here]("http://www.phoronix.com/scan.php?page=article&item=steam_linux_script&num=1")**_). 

and here's the script:

```
#!/bin/bash

# figure out the absolute path to the script being run a bit
# non-obvious, the ${0%/*} pulls the path out of $0, cd's into the
# specified directory, then uses $PWD to figure out where that
# directory lives - and all this in a subshell, so we don't affect
# $PWD

STEAMROOT=$(cd "${0%/*}" && echo $PWD)

#determine platform
UNAME=`uname`
if [ "$UNAME" == "Darwin" ]; then
   PLATFORM=osx32
   # prepend our lib path to LD_LIBRARY_PATH
   export DYLD_LIBRARY_PATH="${STEAMROOT}"/${PLATFORM}:$DYLD_LIBRARY_PATH
[B]elif [ "$UNAME" == "Linux" ]; then
   PLATFORM=linux32
   # prepend our lib path to LD_LIBRARY_PATH
   export LD_LIBRARY_PATH="${STEAMROOT}"/${PLATFORM}:$LD_LIBRARY_PATH
fi[/B]

if [ -z $STEAMEXE ]; then
  STEAMEXE=steam
fi

ulimit -n 2048

# and launch steam
cd "$STEAMROOT"

STATUS=42
while [ $STATUS -eq 42 ]; do
        ${DEBUGGER} "${STEAMROOT}"/${PLATFORM}/${STEAMEXE} $@
        STATUS=$?
        # are we running osx?
        if [ $STATUS -eq 42 -a ${PLATFORM} == "osx32" -a -f Info.plist ]; then
                # are we running from in a bundle?
                exec open "${STEAMROOT}"/../..
        fi
done
exit $STATUS
```the linux section should be in bold.

so, i think this confirms that steam has private linux builds. (someone in the phoronix forums said they had seen a linux build a while back).

what i don't understand is: why don't companies just release linux builds of their products and make it clear that they are unsupported?

---

### Post by AllRadioisDead on 2010-04-22
> **portets said:**
> 
what i don't understand is: why don't companies just release linux builds of their products and make it clear that they are unsupported?
 Perhaps because they're planning on supporting it...?

---

### Post by Zintha on 2010-04-22
> **ihermit said:**
> Perhaps because they're planning on supporting it...?
Thats the impression I was under.

Then again, if it already exists, there are a million and one people who understand Linux enough to support it in the community that already exists for the mean time.

Then again i've heard a million and TWO rumors about Steam coming out on Linux next week/month/year/decade/century/second with 1/2/7/20/400/1213/all/none of the games there.

---

### Post by Tigersmind on 2010-04-22
If they do it, they get my game money for sure.

---

### Post by mastablasta on 2010-04-22
It woul dbe much better to see games coming to linux than Steam.

---

### Post by ndefontenay on 2010-04-22
Having the intention to support it doesn't mean they are going to support it anytime soon.

It's good they are in a frame of work that gives them options to open to the linux world if they feel the need.

Now when is that going to happen is another question really.

---

### Post by ELD on 2010-04-22
I saw this on slashdot earlier and it provided me a moment of joy that's for sure but...

I don't see it as evidence of anything more than someone was testing it and accidentally left it in (as one example), there are many reasons it could be there, Steam coming to Linux officially may not even be one of them.

Nothing is for sure until Valve announce it, i will not get my hopes up that's for sure.

---

### Post by u235sentinel on 2010-04-22
> **ELD said:**
> I saw this on slashdot earlier and it provided me a moment of joy that's for sure but...

I don't see it as evidence of anything more than someone was testing it and accidentally left it in (as one example), there are many reasons it could be there, Steam coming to Linux officially may not even be one of them.

Nothing is for sure until Valve announce it, i will not get my hopes up that's for sure.

until then it's mostly working in crossover games for me.  At least I don't need a windows computer to play it anymore :D

---

### Post by ElSlunko on 2010-04-22
I'm hopeful, that's for sure. I've never really been against buying video games or one company controlling the means of distribution as long as the infrastructure of the client is well built. Only problem I see here is the obvious -- just because the client is available for Linux doesn't mean the games will be. Nevertheless, it would be a swing in the right direction.

---

### Post by Simian Man on 2010-04-22
Even if Steam worked on Linux, the vast majority of the games there wouldn't.  Why does anybody care about this??

---

### Post by efikkan on 2010-04-22
Let's take a look at the facts:

 * [Valve has been looking for an engineer to port Windows games to GNU/Linux]("http://www.phoronix.com/scan.php?page=news_item&px=NjA1NQ")
 * Source games has servers for GNU/Linux.
 * Source games are being ported to Mac OS X, so OpenGL support is added.

Now take a look at the following files from steam:
[http://store.steampowered.com/public/client/public_all.zip.42037f1079151a7bfb225ef0ac9bd5b3b3840ce9](http://store.steampowered.com/public/client/public_all.zip.42037f1079151a7bfb225ef0ac9bd5b3b3840ce9)
[http://store.steampowered.com/public/client/skins_all.zip.6a58428db616736d79a3374ba75abd29e2c1276f](http://store.steampowered.com/public/client/skins_all.zip.6a58428db616736d79a3374ba75abd29e2c1276f)
[http://store.steampowered.com/public/client/bins_linux.zip.dc36f31374267ad4a740762a6cf1925ed30bcab9](http://store.steampowered.com/public/client/bins_linux.zip.dc36f31374267ad4a740762a6cf1925ed30bcab9)
[http://store.steampowered.com/public/client/steam_linux.zip.52367793a26b83abc84871770277e1b8d77608bc](http://store.steampowered.com/public/client/steam_linux.zip.52367793a26b83abc84871770277e1b8d77608bc)

Inspect the files yourself, and you'll se it actually contains binaries and libraries for GNU/Linux (32 bit). It also links to OpenGL, X server and steam's gui, so this is not a game server for GNU/Linux. The steam executable also contains the names redhat, fedora, slackware, debian, mandrake, yellowdog, gentoo, lsb and suse.

Noone seems to get it running yet, and it does not look complete. It looks to me like an early test.

It's not a matter of if Steam is coming to GNU/Linux, but when.

---

### Post by u235sentinel on 2010-04-22
> **Simian Man said:**
> Even if Steam worked on Linux, the vast majority of the games there wouldn't.  Why does anybody care about this??

Fortunately I'm only interested in the Valve games like HL2, TF2, CSS and L4D2 :-)

---

### Post by antenna on 2010-04-22
Exactly, Valve make some decent games.  There would be lots to get excited about for some of us that have been on Linux so long we haven't played all or most of them. ;)  

Anyway, I have a lot of doubts this will ever happen.

---

### Post by HHx66 on 2010-04-22
Steam would be awesome on Linux, and would certainly gain Linux some more support as a desktop OS.

---

### Post by Simian Man on 2010-04-22
> **u235sentinel said:**
> Fortunately I'm only interested in the Valve games like HL2, TF2, CSS and L4D2 :-)

> **antenna said:**
> Exactly, Valve make some decent games.  There would be lots to get excited about for some of us that have been on Linux so long we haven't played all or most of them. ;)  

Anyway, I have a lot of doubts this will ever happen.

So does porting steam to Linux imply porting all of Valve's games to Linux?  Because then, yes, that would be exciting :).

---

### Post by handy on 2010-04-22
This is pretty exciting:

[I]**There Is No Doubt, Steam Is Coming To Linux!**

Posted by Michael Larabel on April 22, 2010

Yesterday we showed proof of Steam's Linux client existence via its Mac OS X launcher that is currently in closed beta, then this morning we showed further signs of Linux support. Since 2008 we have known that Steam and the Source Engine would come to Linux. As an update, we even pointed out the download link for the Steam Linux binary from their store.[/I]

For more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODE3Mw](http://www.phoronix.com/scan.php?page=news_item&px=ODE3Mw)

---

### Post by Marshalus on 2010-04-22
Fantastic!

---

### Post by u235sentinel on 2010-04-23
> **Simian Man said:**
> So does porting steam to Linux imply porting all of Valve's games to Linux?  Because then, yes, that would be exciting :).

If they were to announce it then I'd give it a strong probably :-)

They have announced that they are porting it all (Valve games) to Mac... At least that was my understanding.

---

### Post by ELD on 2010-04-23
After reading the latest article i am now swaying towards the thought of it actually coming to Linux for real, good job i own quite a few Source games since those will work on Linux :D

---

### Post by Noraphalem on 2010-04-23
I think it is a logical step forward.

If you look at the os market you will see there is a trend to split into different ones. The time of one big system dominating all pcs is slowly going over.

If you think a few years back: Mac and Linux was not really known by the majority of the pc users.

Today: They know it and more often use it.

So it is only a logical step that softwaredeveloper have to develop on different platforms. How many games are ported from/to XBOX (360) or PS 1, 2, 3.

---

### Post by Bölvaður on 2010-04-23
> **Noraphalem said:**
> 
If you think a few years back: Mac and Linux was not really known by the majority of the pc users.

If you think a few years back further than that: Mac and Unix was really well know by the majority of the pc users while Windows wasn't.

It's an ever changing landscape that has just begun emerging. Don't expect things to be static just because of lack of experience.

---

### Post by Noraphalem on 2010-04-23
> **Bölvaður said:**
> If you think a few years back further than that: Mac and Unix was really well know by the majority of the pc users while Windows wasn't.

Yes thats right. But the last few years Windows was dominating. Most people are brainwash of Microsofts marketing which would like to  vanish all other oses from the users mind.

> **Bölvaður said:**
> It's an ever changing landscape that has just begun emerging. Don't expect things to be static just because of lack of experience.

Yes I may have a lack of experience but I have sayd "I think" not "it is"! It is changing. Definitely.

---

### Post by u235sentinel on 2010-04-23
> **Noraphalem said:**
> Yes thats right. But the last few years Windows was dominating. Most people are brainwash of Microsofts marketing which would like to  vanish all other oses from the users mind.



Yes I may have a lack of experience but I have sayd "I think" not "it is"! It is changing. Definitely.

I remember a day when It was said "nobody ever got fired for buying IBM products".  Now I hear the same thing with Microsoft.  In the future it will be someone else.

At one point WordPerfect was the standard for word processing.  Then we had standards which changed over time to today's standards.  Tomorrow will change again.

I used to run only Windows on the desktop.  Now I have one windows desktop at home and several Ubuntu desktops and servers.  Heck, even my TV runs Linux 2.6 kernel.  How cool is that :-)

Things change.  always do.

---

### Post by RambJoe on 2010-04-23
Can't wait for this. Valve is the best company to be mult-OS imo, as they don't just make games, they sell them.

DICE have said they are thinking of porting BC2 to OSX.

---

### Post by Optln on 2010-04-24
> **Simian Man said:**
> Even if Steam worked on Linux, the vast majority of the games there wouldn't.  Why does anybody care about this??

Steam is the biggest platform for indie PC games. Currently most releases in Steam are indie games and many developers will probably try to port their games to Linux too. This means, we will at least get decent independent titles for Linux.

By the way Valve ported Source Engine to OpenGL for Mac support. So Half-Life series, CS, TF2, L4D series will be coming to Linux.

---

### Post by Chame_Wizard on 2010-04-24
I damn hope Valve does it,cause I want to play HL1 again(my very first torrent in January 2005).:lolflag:

OpenGL 3.3/4.0 is just too cool to be ignored right now.:guitar:

---

### Post by ELD on 2010-04-26
> **Chame_Wizard said:**
> I damn hope Valve does it,cause I want to play HL1 again(my very first torrent in January 2005).:lolflag:


Not something to shout about. So let me guess you will just fire up the torrents for the Linux version too? Besides it's on about the Source engine, hl1 is not using Source.

---

### Post by Modplanman on 2010-04-26
> **ELD said:**
> Not something to shout about. So let me guess you will just fire up the torrents for the Linux version too? Besides it's on about the Source engine, hl1 is not using Source.

Original Half-Life engine already runs OpenGL. Half-Life Source uses the (you guessed it) Source engine.

---

### Post by ELD on 2010-04-26
> **Modplanman said:**
> Original Half-Life engine already runs OpenGL. Half-Life Source uses the (you guessed it) Source engine.

I know that, it is what i was basically pointing out since all the chat is about valve and source.

I'm pretty sure half life 1 has a linux port, but just to point out that using OpenGL != working on Linux.

---

### Post by quadomatic on 2010-04-26
> **ELD said:**
> 
I'm pretty sure half life 1 has a linux port

No it doesn't :(

---

### Post by RastaCalavera on 2010-04-26
> **Chame_Wizard said:**
> I damn hope Valve does it,cause I want to play HL1 again(my very first torrent in January 2005).:lolflag:

OpenGL 3.3/4.0 is just too cool to be ignored right now.:guitar:

Half Life is a great game and Valve does its best to make it avaible to everyone. Last year it was only a penny on the birthday of HL. I find it hard to see someone support value with mention of a torrent. I am not one to judge pirates but to "support" a franchise and not pay for it is just WRONG! So I hope I am just interpreting your post wrong.

---

### Post by murderslastcrow on 2010-04-26
OpenGL- fast, full-featured, and available everywhere but the Game Boy Advance I guess. Woot.

---

### Post by torturednacho on 2010-04-28
What about running steam on wine? My main OS is windows, but I'm not a stranger to nix* systems. I'm thinking about switching completely over to nix on my main system. But I won't if I can't play my L4D2 and TFC. 

Anyone installed steam with wine and if so how does it work? Loading problems? Any unexpected lag? I was reading that there is a font that sometimes doesn't get installed thus causing some issues with the in game chat and steam look. :popcorn:

---

### Post by dmn_clown on 2010-04-28
> **Zintha said:**
> Then again i've heard a million and TWO rumors about Steam coming out on Linux next week/month/year/decade/century/second with 1/2/7/20/400/1213/all/none of the games there.

And how many of those rumors were started by Michael Larabel of Phoronix to drive up his site traffic and increase his ad revenue?

**If** Valve is going to port a Source client to the platform, they will announce it.  The announcement will not come from a blog that has nothing to do with them.

---

### Post by Cavsfan on 2010-04-28
> **torturednacho said:**
> What about running steam on wine? My main OS is windows, but I'm not a stranger to nix* systems. I'm thinking about switching completely over to nix on my main system. But I won't if I can't play my L4D2 and TFC. 

Anyone installed steam with wine and if so how does it work? Loading problems? Any unexpected lag? I was reading that there is a font that sometimes doesn't get installed thus causing some issues with the in game chat and steam look. :popcorn:
My son tried loading Steam and running L4D and the system froze. We had to turn it off and back on. He plays L4D, L4D2, COD and GTA4. I would like to see it work though.

---

### Post by torturednacho on 2010-04-28
> **dmn_clown said:**
> And how many of those rumors were started by Michael Larabel of Phoronix to drive up his site traffic and increase his ad revenue?

**If** Valve is going to port a Source client to the platform, they will announce it.  The announcement will not come from a blog that has nothing to do with them.

[Steam on linux]("http://developer.valvesoftware.com/wiki/Steam_under_Linux")  <--Valve

---

### Post by torturednacho on 2010-04-28
> **Cavsfan said:**
> My son tried loading Steam and running L4D and the system froze. We had to turn it off and back on. He plays L4D, L4D2, COD and GTA4. I would like to see it work though.

I'm all about Steam and how they get the games across. I've been playing valve games since they were on mPlayer. 

Although they do have the wiki it looks like valve/steam still say to use wine. I'm alittle 
[SIZE=3]sceptical about using wine for games for loading/lag reasons.[/SIZE]

---

### Post by ELD on 2010-04-28
> **dmn_clown said:**
> And how many of those rumors were started by Michael Larabel of Phoronix to drive up his site traffic and increase his ad revenue?

**If** Valve is going to port a Source client to the platform, they will announce it.  The announcement will not come from a blog that has nothing to do with them.

Who doesn't post news to drive traffic? That is a given.

Fact is his posts are worth a read and provide us with some nice incite

---

### Post by torturednacho on 2010-04-29
From the archives of the Phoronix chat. Looks like getting the client to work is the hard part at this moment. steamui.so errors

---

### Post by u235sentinel on 2010-04-29
> **ELD said:**
> Who doesn't post news to drive traffic? That is a given.

Fact is his posts are worth a read and provide us with some nice incite

If the information he provided was unsubstantiated then I believe he's right about the ad revenue bit.  However since it has been substantiated by other independent sources than I'm not worried.

Plus I've been on valves site poking around.  It's not hard to see they want to do this.  But in the end will they?

It wouldn't be the first time someone started a project and decided it wasn't worth completing for whatever reason.

---

### Post by phoronix on 2010-04-29
> **dmn_clown said:**
> And how many of those rumors were started by Michael Larabel of Phoronix to drive up his site traffic and increase his ad revenue?

**If** Valve is going to port a Source client to the platform, they will announce it.  The announcement will not come from a blog that has nothing to do with them.

You'll see soon enough that the Steam client and select games are indeed coming to Linux. If you don't want to believe it now, that's fine, then just wait and see.

-- Michael Larabel

---

### Post by ELD on 2010-04-29
> **phoronix said:**
> You'll see soon enough that the Steam client and select games are indeed coming to Linux. If you don't want to believe it now, that's fine, then just wait and see.

-- Michael Larabel

I hope you are right mate it would be pretty awesome for a lot of reasons.

Would be giving Linux some well deserved recognition in the gaming community and to be honest i think it will make us more a force to be reckoned with.

---

### Post by antenna on 2010-04-29
Shame it would be their dodgy custom UI just when I get every app on my system in nice GTK.  Take what you can get I suppose. :)

---

### Post by naikon89 on 2010-04-30
> **phoronix said:**
> You'll see soon enough that the Steam client and select games are indeed coming to Linux. If you don't want to believe it now, that's fine, then just wait and see.

-- Michael Larabel

Evidence would help your assertion somewhat. How do you KNOW steam is coming to Linux? Valve have said nothing. Sure, the linux libraries in the client look promising, but the libs alone do not point to a confirmed Linux client. 

Evidence > Opinion

---

### Post by phoronix on 2010-04-30
> **naikon89 said:**
> Evidence would help your assertion somewhat. How do you KNOW steam is coming to Linux? Valve have said nothing. Sure, the linux libraries in the client look promising, but the libs alone do not point to a confirmed Linux client. 

Evidence > Opinion

I have my sources that have certainly proved themselves over the years. There is more than Linux *libraries* that are already publicly available, there is the Steam client binary itself (not to be confused with the server binary) that continues to be updated [there's a whole discussion about it [here]("http://www.phoronix.com/forums/showthread.php?t=23328")].

---

### Post by naikon89 on 2010-04-30
Fine, you have proved that the client exists. This does not mean the Linux client will be actually released to the public for consumption. WoW are rumored to have had internal Linux builds for years
yet no Linux client exists despite a Mac client. I still don't think it's fair to presume Linux is getting Steam/games just because Valve have worked on a client. It's promising, but we are only speculating
until Valve make their position clear.

---

### Post by phoronix on 2010-04-30
> **naikon89 said:**
> Fine, you have proved that the client exists. This does not mean the Linux client will be actually released to the public for consumption...It's promising, but we are only speculating
until Valve make their position clear.

As I have said, according to my reliable sources it will indeed be publicly released and you can expect an announcement as soon as June.

---

### Post by naikon89 on 2010-04-30
We will just have to wait and see then. I owe you an apology if this turns out true. I am still skeptical at this point however.

---

### Post by Modplanman on 2010-04-30
Copied from the Steam thread on the subject:

> The timestamp for steam_client_linux changed and the files were updated. Here is where the updated one fails on my machine:
[http://paste2.org/p/802750](http://paste2.org/p/802750)

I won't post instructions on where to get the files and what to do and i hope the link above isn't against the forum rules, and if it is, please remove this post.

[http://forums.steampowered.com/forums/showpost.php?p=14705073&postcount=557](http://forums.steampowered.com/forums/showpost.php?p=14705073&postcount=557)



There's been one or two updates it seems. It's also been noted that the Steam client attempts to draw a UI but fails.

---

### Post by ELD on 2010-04-30
Well it is exciting i personally cannot wait to see how this unfolds, my Windows 7 partition hasn't been booted for weeks but i do now and then for games i own on Steam. Mostly gaming on the 360 nowadays so my PC is near enough 100% Linux ;)

---

### Post by williamdabastrd on 2010-04-30
This will be the greatest thing for me EVER. Ubuntu has support for my iPod touch AND Steam may be ported over with the only games I really play. 

I have already gotten completely rid of my Win7 partition despite paying $100 for it with my new PC build. I figured I just wanted to game and play with my iPod, plus some school work. This just seals the deal for me and many of the people I sell PC's to.

---

### Post by phoronix on 2010-05-01
Here's an independent screenshot of the genuine Linux Steam client: [http://www.phoronix.com/scan.php?page=news_item&px=ODIwNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODIwNQ)

---

### Post by ELD on 2010-05-01
> **phoronix said:**
> Here's an independent screenshot of the genuine Linux Steam client: [http://www.phoronix.com/scan.php?page=news_item&px=ODIwNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODIwNQ)

Well it does seem more and more likely a client is coming out, i hope Valve do make an announcement, if it does come in June that would be one heck of an early birthday present for me!

---

### Post by Technophobia on 2010-05-01
I'm starting to believe.

---

### Post by efikkan on 2010-05-02
We all know Steam is eventually coming to GNU/Linux, Valve has hired engineers to port games and has created the test version of the steam client for GNU/Linux. Both of these are proven facts, and a company like Valve does this for a reason. If you don't take my or any others word for it, examine the binaries yourself. You'll see they do in fact link to OpenGL, X11 and other libraries, and the client clearly contains a GUI library. This proves this is a GUI steam client, and not to be confused with the existing CLI client for steam (server).

I agree that Phoronix has been overdoing this a lot, claiming every phrase containing the word "linux" is worth an article, but they are not the ones hurting the case. Publicity is advertisement for Valve, and does only promote the Steam client for GNU/Linux. The people who hurts this case are the crackers wich are modifying the binaries. Valve does not like this at all, and there is no good reason to do this. It has been proven Valve is working on the Steam client for GNU/Linux, so they are not going to prove something more by modifying the client since they can't bypass the server side authentication. So everyone please stop doing this!

So let's instead spread the good words that Steam is _someday_ coming to GNU/Linux, even though I _believe_ it's going to take a while.

---

### Post by ELD on 2010-05-02
I have yet to see any member of Valve comment on any of this. I don't agree or disagree with the crackers playing around with it, if they didn't want them to maybe they should have had some form of security for the files. As far as i can tell and I'm sure i read in the article the files they are playing with are just scripts which anyone could look into, so there is no reason to think they would frown upon it?

I don't think Phoronix is overdoing it at all, Steam naturally would be massive recognition from such a big company (Valve) for Linux gamers. It would change the face of Linux gaming and I don't say that lightly.

Not that i am a fan of WoW but i don't want it to end up like that, remember they built a Linux client and later decided to drop it, let us just hope it doesn't end up being like that.

---

### Post by Blacksheep01 on 2010-05-04
Being new to Ubuntu, and a lifelong PC gamer, I've been scouring the net looking for official word about Steam on Linux. All of this evidence looks great, even engadget has spotted the code an written about it. However, on the official Steam forums I found [this person ]("http://forums.steampowered.com/forums/showthread.php?t=1252380&highlight=Ubuntu")who received a very disappointing reply from a Valve employee indicating they would not be supporting Linux. 

I hope it is just a smoke screen or some kind of required official response, but still breaks my heart a little :(

---

### Post by ELD on 2010-05-04
That email is a standard response, they don't currently support it and will say so until they officially announce otherwise.

Also that thread angers me, to think Windows gamers are so ignorant of what Linux is nowadays i just had to make a reply pointing a few things out.

---

### Post by Blacksheep01 on 2010-05-04
> **ELD said:**
> That email is a standard response, they don't currently support it and will say so until they officially announce otherwise.

Also that thread angers me, to think Windows gamers are so ignorant of what Linux is nowadays i just had to make a reply pointing a few things out.

Nice reply if that last one [COLOR=black](liamdawe[/COLOR]) was yours! I read through the whole thing also, the guy indicating "Windows is it for gaming" and that "graphics have only improved because of DirectX" represents the worst of the pretend know-it-alls. My old PC games, which I still run from time to time, were all run in OpenGL, I remember tweaking settings for them and even selecting Direct3D or OpenGL API from options. The advice on several of those old games was to choose OpenGL to improve performance lol, not to mention PS3 is OpenGL! 

I'm glad that just appears to be a standard response. I've only been on Linux for over a week now, but I love it. I learned of Virtual Box and may use that for now, but emulators are always a weak solution to me, prone to glitches and errors when the client updates. I'd love to see a native steam client for Linux.

---

### Post by ELD on 2010-05-04
Yes liamdawe is indeed me and thank you :).

Since you are pretty new i might also suggest DosBox i have never personally got it to work properly (i get impatient) but i have heard good things about it.

---

### Post by Blacksheep01 on 2010-05-04
> **ELD said:**
> Since you are pretty new i might also suggest DosBox i have never personally got it to work properly (i get impatient) but i have heard good things about it.

I actually used that in the past but didn't even think about it for Linux! I used it in Windows to run the CD ROM update of a very old Sierra game called Hero Quest/Quest for Glory. I ran the original game on my Tandy (big laugh for that dinosaur lol) back in 1990, it was my first computer game and first RPG. DOS box actually ran it perfectly within Windows, I will have to check it out.

---

### Post by torturednacho on 2010-05-04
This would be amazing, I do hope we hear something about this in June as Phoronix mentioned.

---

### Post by efikkan on 2010-05-04
> **ELD said:**
> I have yet to see any member of Valve comment on any of this. I don't agree or disagree with the crackers playing around with it, if they didn't want them to maybe they should have had some form of security for the files. As far as i can tell and I'm sure i read in the article the files they are playing with are just scripts which anyone could look into, so there is no reason to think they would frown upon it?
I don't think you got my point.
Playing with scripts is one thing, but cracking to create patches for the executables to bypass security is something different. And this is exactly what several people are trying to do, and Valve does not like this. What would they think of GNU/Linux users if they crack their software like this?

> **ELD said:**
> I don't think Phoronix is overdoing it at all, Steam naturally would be massive recognition from such a big company (Valve) for Linux gamers. It would change the face of Linux gaming and I don't say that lightly. Again, I think you missed my point.
Phoronix is overdoing it because they publish a new article for every tiny phrase of "linux" they can dig up in the files. One of these articles describes the phrase in the Windows binaries, wich evidently has been present there for years (most likely because the CLI-client), but Phoronix present this as news "proving" the upcoming Steam client for GNU/Linux. Let me tell you the binaries also contains phrases such as the following: "macos", "win311", "win95", "winNT" etc. This has to do with the platform detection (even though steam don't run on win 3.11). So this does not prove anything, and Michael at Phoronix knows this. 

The actual GNU/Linux client linking to GNU/Linux libraries and GUI is proof.

But I agree with you, Steam for GNU/Linux would change Linux gaming completely, and would the following years after release bring a lot of more games to GNU/Linux. And many users who dual boot for gaming will stop using windows after a while. So Steam coming to GNU/Linux is really the biggest news in several years, but the case loses credibility when Phoronix creates extra articles about this "faulty evidence". (But they can of course create articles about the real evidence)

---

### Post by handy on 2010-05-04
I think some people with Steam accounts that use both windows & Linux are trying to be able to get the in house Linux Steam client found on the web to work with their accounts.

It is a challenge that I would be attempting if I was in their situation also.

They aren't trying to steal anything, they are testing their skill, learning & getting stimulation out of the attempt which they know has very little chance of success.

The Steam people would have to consider this a normal response from the small section of the Linux community that fit into this profile.

Steam are getting plenty of free publicity on the forums & such, regarding the possibility of an official Linux client, I'm sure that they would also be happy with that.

---

### Post by keljaden on 2010-05-04
I think they are leaking information on purpose to see what kind of response they would get.  Perhaps to see how much potential there really is.  I for one have been doing my best to boycott PC products.  I have only bought one or 2 things in the past two years (perhaps less) (I am given windows and microsoft software for free, yet I still choose to run linux).

I use crossover for now though.

---

### Post by ELD on 2010-05-04
@[efikkan]("http://ubuntuforums.org/member.php?u=125774") for the first point i may have missed that yes i didn't realise they are bypassing Valve placed security measures by simply trying to get a piece of software to run...i say it again i cannot see anything wrong, point me to somewhere that shows them bypassing security?

As for the second bit, no i didn't miss your point, as i actually said in my post, i DON'T think they are overdoing it, is that hard to understand? I think you missed my point, i welcome the news and i find it interesting as do many other people, so no i again don't think Phoronix is overdoing it.

And yes it would be Huge if Steam did come for Linux, we can hope!

---

### Post by rifter on 2010-05-04
> **mastablasta said:**
> It woul dbe much better to see games coming to linux than Steam.

If Steam came to Linux, doesn't that imply that games delivered via Steam would run on Linux?

---

### Post by ELD on 2010-05-05
> **rifter said:**
> If Steam came to Linux, doesn't that imply that games delivered via Steam would run on Linux?

To put it simply No.

The Source Engine games would be a Yes since they will be able to run on Linux as for everything is No.

Why? You should look-up what Steam is, hardly any games on their are made by the Steam developers Valve.

---

### Post by R.A.W.R. on 2010-05-05
> **rifter said:**
> If Steam came to Linux, doesn't that imply that games delivered via Steam would run on Linux?

Not all games on Steam would run with Linux. However, if Steam does a Linux native version of their program they will most likely have a game library that would sell linux native games on their steam store.

Not to mention it would give an instant boost to native linux game developers as their public awareness would be increased dramatically. More money to the games that support linux will most likely lead to better game development.

Also, it may very well push Nvidia and AMD/ATI to code better drivers for linux when the demand for it goes up.

Steam and Valve making linux native versions of their software available would be the last step in making linux a rock solid desktop OS being able compete with Microsoft on all fronts.

Linux and Ubuntu has come a long way.....lets not stop now.

---

### Post by Nico0020 on 2010-05-06
one thing i always wondered is; if we do get steam and the source games, would source mods be pretty easy to make a linux version of, or would that require a whole bunch of work.  Only games I play on Steam are HL1 mods and source mods.  Is OSX just getting source games, or will the HL1 games make it also?  worst case is I would have to continue using crossover games for HL1 mods.

---

### Post by ELD on 2010-05-06
> **Nico0020 said:**
> one thing i always wondered is; if we do get steam and the source games, would source mods be pretty easy to make a linux version of, or would that require a whole bunch of work.  Only games I play on Steam are HL1 mods and source mods.  Is OSX just getting source games, or will the HL1 games make it also?  worst case is I would have to continue using crossover games for HL1 mods.

Well mods as far as i know are just a form of package for a specific engine, mods are usually platform independent as they simply use the engine, so mods should work fine.

---

### Post by efikkan on 2010-05-06
> **ELD said:**
> @[efikkan]("http://ubuntuforums.org/member.php?u=125774")As for the second bit, no i didn't miss your point, as i actually said in my post, i DON'T think they are overdoing it, is that hard to understand? I think you missed my point, i welcome the news and i find it interesting as do many other people, so no i again don't think Phoronix is overdoing it.I'm sorry, you still don't seem to get it. You are of course allowed to have your own opinion. But I'm not talking about the amount of articles Phoronix writes on the subject (I think more is better), but the articles that contains false claims. Michael at Phoronix posts extra articles with claims that he knows isn't true, maybe to just to get attention or to earn money from ads (but I don't care why), but it hurts the credibility of the case.

---

### Post by ELD on 2010-05-06
> **efikkan said:**
> I'm sorry, you still don't seem to get it. You are of course allowed to have your own opinion. But I'm not talking about the amount of articles Phoronix writes on the subject (I think more is better), but the articles that contains false claims. Michael at Phoronix posts extra articles with claims that he knows isn't true, maybe to just to get attention or to earn money from ads (but I don't care why), but it hurts the credibility of the case.

Really and what has he said that isn't actually true, I'm not even sure if i have read all of them to be honest so i might have missed something, can you point me in the right direction?

If he is indeed giving us false hope then he will have gone down in my good books.

---

### Post by u235sentinel on 2010-05-06
> **efikkan said:**
> I'm sorry, you still don't seem to get it. You are of course allowed to have your own opinion. But I'm not talking about the amount of articles Phoronix writes on the subject (I think more is better), but the articles that contains false claims. Michael at Phoronix posts extra articles with claims that he knows isn't true, maybe to just to get attention or to earn money from ads (but I don't care why), but it hurts the credibility of the case.

{Citation required}

---

### Post by efikkan on 2010-05-06
> **ELD said:**
> Really and what has he said that isn't actually true, I'm not even sure if i have read all of them to be honest so i might have missed something, can you point me in the right direction?

If he is indeed giving us false hope then he will have gone down in my good books.
Take a look:
[Yet More Signs Of Valve's Steam On Linux]("http://www.phoronix.com/scan.php?page=news_item&px=ODE3MQ")
Notice Linux 2.2 and "X360", Windows 3.11, 9x and NT has been removed from the list because it would be too obvious then. Conclusion: this does not mean anything at all.
Phoronix's follow up article:
[Yes, More Steam & Source Engine Linux Details]("http://www.phoronix.com/scan.php?page=news_item&px=ODE4Mw")
> Even the Steam.exe Windows binary features a string that reads "Bad eCurrentLinuxClientVersion field in CClientConfigRecord"
Check the following replies in the forum:
> This string, and some of the others, are also present in the old, non-webkit version. So it isn't really a sign of anything? 
> There was a linux version of the steam client for ages - cli only however. Wow, you found now strings of it in the Win version, impressive. What do you think is this?
Regarding the "LINUX" phrase:
> This string is also present on my system, in a file last updated April 16. 
These phrases has been present for quite some time, and does not prove a gui Steam client for GNU/Linux.

The actual client however, is actual proof: [http://store.steampowered.com/public/client/steam_client_linux](http://store.steampowered.com/public/client/steam_client_linux)

---

### Post by ELD on 2010-05-06
Hmm interesting thanks for highlighting me to that :KS. I'm not keeping my hopes up over it with all the indie titles available at the moment i'm pretty stuffed full on gaming hehe.

It is a nice thought but as i've said to a few people now from the very begging it means nothing until Valve confirm it.

Also like i said before we don't want this to turn into another WoW where they have a client in testing, massive hype and devotion towards Blizzard and they just drop it.

---

### Post by handy on 2010-05-07
> **Nico0020 said:**
> one thing i always wondered is; if we do get steam and the source games, would source mods be pretty easy to make a linux version of, or would that require a whole bunch of work.  Only games I play on Steam are HL1 mods and source mods...  

I know that with Oblivion & mods, all you really had to do was make sure that all of the files & directories had the same case first letter, as windows is not case sensitive & the distro's are.

There were a few sophisticated mods that handled multiple mods that are (or at least were) not compatible with Linux, from memory I think they were .NET based.

---

### Post by portets on 2010-05-07
> **efikkan said:**
> Take a look:
[Yet More Signs Of Valve's Steam On Linux]("http://www.phoronix.com/scan.php?page=news_item&px=ODE3MQ")
Notice Linux 2.2 and "X360", Windows 3.11, 9x and NT has been removed from the list because it would be too obvious then. Conclusion: this does not mean anything at all.
Phoronix's follow up article:
[Yes, More Steam & Source Engine Linux Details]("http://www.phoronix.com/scan.php?page=news_item&px=ODE4Mw")

Check the following replies in the forum:


Regarding the "LINUX" phrase:

These phrases has been present for quite some time, and does not prove a gui Steam client for GNU/Linux.

The actual client however, is actual proof: [http://store.steampowered.com/public/client/steam_client_linux](http://store.steampowered.com/public/client/steam_client_linux)

the only thing i'm getting from your post is that he probably didn't realize that older clients contained linux strings.

but i agree that he seems to get overexcited to bring attention to the site. but personally, i have no problem with that. most people would do the same.

---

### Post by TehWhale on 2010-05-08
I really want a native version just to chat with Steam friends. Right now it's horribly buggy (on wine).

---

### Post by Modplanman on 2010-05-08
Linux client has now been updated again, and with some work, phoronix guys we able to get the main client window going!

[IMG]http://www.phoronix.net/image.php?id=0x2010&image=steam_2010_almost_med[/IMG]

[http://www.phoronix.com/scan.php?page=news_item&px=ODIyOQ](http://www.phoronix.com/scan.php?page=news_item&px=ODIyOQ)

---

### Post by ELD on 2010-05-08
Heh that is pretty awesome to see they have gotten that far.

As time goes on i have mixed feelings towards this, i would love it don't get me wrong, but i do fear all the effort is for nothing as Valve will never announce a Linux version.

---

### Post by efikkan on 2010-05-08
They would not be able to test any of Steam's features without a beta account, and anyone would not get one without signing a NDA. The client does most likely look a bit different once signed in with a valid account. I'm pretty sure Valve is farther in the development process than getting a black empty window when they send their software to beta testers. (the main executable is over 4 MB, excluding all the libraries and GUI, and the sizes of the files are approx. the same as the Mac OS X version, don't tell me that's not experimental features.)

---

### Post by Chame_Wizard on 2010-05-09
Hurry up Steam.:guitar:

---

### Post by efikkan on 2010-05-09
Since there has been no announcement and the GNU/Linux client has to be bug tested on more distributions than the Mac OS X client, I think it would still be a while before we see a final client.


BTW: has anyone been able to figure out if the GNU/Linux steam client uses X for rendering or just for setting up an OpenGL context?

---

### Post by ELD on 2010-05-09
> **efikkan said:**
> They would not be able to test any of Steam's features without a beta account, and anyone would not get one without signing a NDA. The client does most likely look a bit different once signed in with a valid account. I'm pretty sure Valve is farther in the development process than getting a black empty window when they send their software to beta testers. (the main executable is over 4 MB, excluding all the libraries and GUI, and the sizes of the files are approx. the same as the Mac OS X version, don't tell me that's not experimental features.)

lol wut

You would be able to use any feature built into the client as long as you are signed in.

Why would the client look different? The reason it was recently updated was for it to be cross-platform, they wouldn't change it again just for Linux users.

Your right for one thing, yeah they are more than likely much further than we can see, but we don't have everything they do, we are only going by what people could pinch off their servers remember.

---

### Post by efikkan on 2010-05-09
> **ELD said:**
> lol wut

You would be able to use any feature built into the client as long as you are signed in.

Why would the client look different? The reason it was recently updated was for it to be cross-platform, they wouldn't change it again just for Linux users.

Your right for one thing, yeah they are more than likely much further than we can see, but we don't have everything they do, we are only going by what people could pinch off their servers remember. Different than the pictures posted on the phoronix forums, _not_ different than the other clients.

---

### Post by ELD on 2010-05-09
> **efikkan said:**
> Different than the pictures posted on the phoronix forums, _not_ different than the other clients.

Not how you explained it :P

> 
The client does most likely look a bit different **once signed in with a  valid account**
What your saying by that is a "valid" account whatever that means would look different.

It's painstakingly obvious that it would look more complete than what Phoronix shows us.

Sorry to nitpick but chose how you talk errr type carefully :P

Edit > Just had a thought.

I've seen a few people say none of this matters, the Linux stuff has been there forever etc etc etc.

But if they weren't developing it then it would of an old version, it wouldn't even remotely resemble the new-look, which from Phoronix scans we can see it is using the latest look.

---

### Post by efikkan on 2010-05-09
As you might be aware of, the users who are experimenting with the GNU/Linux client do bypass the login to get to the main window. And it's quite obvious that this window would be rather empty then. And this is exactly what I was talking about. The client does most likely look pretty "complete" for those who got a valid beta account, but those had to sign a NDA. My point is, we can't see the development progress from these pictures. I suggest you read my previous comment one more time.

Yes as you can see in the pictures, or in the attached files in the GNU/Linux client, this is clearly the new 2010 Steam client, not some old client that's been there forever.

---

### Post by ELD on 2010-05-09
My bad didn't realise they are bypassing the login altogether.

Not sure if it has been posted, but found this on the steam forums from someone:
[http://www.youtube.com/watch?v=iTgqdlA_jE8](http://www.youtube.com/watch?v=iTgqdlA_jE8)

Only a few days away from the Mac release now (3 days), I'm kinda hopeful that we get some more hints after then, i mean bigger hints, or for it to even be confirmed.

Something I wish to know is where exactly Phoronix got that "June" date from. In the articles he mentions June a specific month...why, does he know something we don't or is he just ramping up the hype machine?

---

### Post by efikkan on 2010-05-09
Don't you agree it makes no sense to send a client wich looks like this to beta testers? I'm pretty sure that if I got a beta account and logged in, it would appear more or less complete (except for bugs and some minor features of course). It makes no sense for Valve to send a graphical layout to beta testers when the layout design is complete on other platforms.



If Michael at Phoronix knows something we don't, then he wouldn't be allowed to tell us.

---

### Post by ELD on 2010-05-09
> **efikkan said:**
> Don't you agree it makes no sense to send a client wich looks like this to beta testers? I'm pretty sure that if I got a beta account and logged in, it would appear more or less complete (except for bugs and some minor features of course). It makes no sense for Valve to send a graphical layout to beta testers when the layout design is complete on other platforms.



If Michael at Phoronix knows something we don't, then he wouldn't be allowed to tell us.

Then the June date he mentioned he fabricated for the hype machine on his site then.

Personally I don't think it will come to life this year.

I do agree that it would make no sense, but then who knows what is really going on, we sure don't :(

---

### Post by efikkan on 2010-05-09
I guess it would take 6 months or more.

Since they has started to send it to testers outside the company, this most likely means a prototype client got the main features working. I think the announcement will come when there is only a handful of minors bugs left to fine tune, when Valve is able to put a release date.

---

### Post by ELD on 2010-05-09
> **efikkan said:**
> I guess it would take 6 months or more.

Since they has started to send it to testers outside the company, this most likely means a prototype client got the main features working. I think the announcement will come when there is only a handful of minors bugs left to fine tune, when Valve is able to put a release date.

Well we can speculate as much as we like, but in the end i guess they will announce it if/when they are ready to.

The if meaning if they ever do...

---

### Post by rasmus91 on 2010-05-09
> The if meaning if they ever do...
Well, why wouldn't they?

Just consider how many people would enjoy playing games in Linux. The majority of people i know who are using windows is using it because they can't game on Ubuntu.

Just think about the potential!

say Steam comes out for Linux within this year. That would include: The source engine, and probably every game that valve has released. and with a bit of luck, all games running on the source engine.

Now, with the Unreal 3 engine being open source, theres a possibility that we get those games as well.

Just the fact that valve releases games for Linux would, IMO, be enough for other companies to consider making the games run on Linux as well. just write them for OpenGL instead of Direct 3D. I think this would open a world of gaming on Linux. this would make me switch completely to Linux, as the only reason that i have windows is to game on it.

Hope my optimistic point of view has a influence on you. from here's left to say; Goodnight, sweet dreams. And may the Source be with you.

Rasmus

---

### Post by efikkan on 2010-05-09
Don't forget all the id tech games, world of goo and a bunch of others. Maybe even Torchlight will finally be ported (the graphics engine supports GNU/Linux).

And take a look at [the Humble Indie Bundle]("http://www.wolfire.com/humble"), 76.000 downloads in 5 days.

---

### Post by ELD on 2010-05-09
@[rasmus91]("http://ubuntuforums.org/member.php?u=489295") wishfull thinking is great but companies like Valve think about Profit and not Potential, they are a business remember.

I cannot find any articles on UE3 being open source?

"The majority of people i know who are using windows is using it because  they can't game on Ubuntu."

A very very common statement made, but it generally means squat to a business.

No amount of optimism will change my views, sorry. I want the Steam client to be on Linux, but i honestly don't think it will happen this year.

@[efikkan]("http://ubuntuforums.org/member.php?u=125774") some old idtech games have a native port yes, but they are unsupported and new idtech games are not to have a Linux client (Rage comes to mind).

---

### Post by efikkan on 2010-05-09
> **ELD said:**
> @[rasmus91]("http://ubuntuforums.org/member.php?u=489295") wishfull thinking is great but companies like Valve think about Profit and not Potential, they are a business remember.

I cannot find any articles on UE3 being open source?

"The majority of people i know who are using windows is using it because  they can't game on Ubuntu."

A very very common statement made, but it generally means squat to a business.

No amount of optimism will change my views, sorry. I want the Steam client to be on Linux, but i honestly don't think it will happen this year.

@[efikkan]("http://ubuntuforums.org/member.php?u=125774") some old idtech games have a native port yes, but they are unsupported and new idtech games are not to have a Linux client (Rage comes to mind).

Rage is not released yet.
id tech 4 games such as Quake 4, Doom 3, Prey and Enemy Territory: Quake Wars are available for GNU/Linux. Only Wolfenstein is not ported as I can see.

All of id's games are available on Steam, and most (if not all) has been ported to GNU/Linux, but some of these may be difficult to install in GNU/Linux for some users. That's why I think these games will be even more successful when Steam comes to GNU/Linux.

---

### Post by ELD on 2010-05-10
They already stated Rage is not having a Linux client.

Also for the other idtech games like i mentioned they are unsupported by anyone, i doubt Steam would want the headaches of unsupported games.

---

### Post by darklegion on 2010-05-11
> **ELD said:**
> They already stated Rage is not having a Linux client.

Also for the other idtech games like i mentioned they are unsupported by anyone, i doubt Steam would want the headaches of unsupported games.

From Wikipedia: Three weeks later Timothee Besset, the person in charge of porting id's products to Linux, discussed the future of the Linux port in a more positive light, stating on September 13, 2009 that "Fundamentally nothing has changed with our policy regarding Linux games... I'll be damned if we don't find the time to get Linux builds done."

That's not a flat out confirmation, but it's certainly not a flat out no either.

Also Wolfenstein is the only example of an id4 game not coming to Linux, and it wasn't developed by id software. There is the upcoming game, Brink, but even that has a small chance of getting a port (and also isn't developed by id)

---

### Post by ELD on 2010-05-11
@[darklegion]("http://ubuntuforums.org/member.php?u=490592") Carmack himself said " a Linux port is unlikely" and he is still the top man when it comes to the decisions on it regardless of whatever anyone else says.

As for brink there is nothing what-so-ever to say it will come to Linux.

---

### Post by phoronix on 2010-05-12
[http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1) :)

---

### Post by Sockerdrickan on 2010-05-12
> **phoronix said:**
> [http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1) :)
  Finally :)

---

### Post by Naegling23 on 2010-05-12
yeah!!!!

Time to dust off my old copy of half-life 2

This means more games of course, but holy crap, it should make installation a breeze!

and of course, we have id, ut3, and source game engines.  Nice.

---

### Post by Chame_Wizard on 2010-05-12
Damn good.:guitar:

---

### Post by qualtch on 2010-05-12
This... is... just... terrific!

Valve's official announcement is still missing though but I think we have a good reason to believe this article. I got no reason to use Win7 with dual-boot anymore if this becomes reality sometime :) Sadly though, I already purchased retail Windows 7 this spring... Now that's truely wasted money if this Steam client on Linux will be true :-s darn... But I would still switch completely to Ubuntu!

---

### Post by JMisczak on 2010-05-12
[Source]("http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1")

*Valve Corporation has today rolled out their Steam Mac OS X client to the general public and confirmed something we have been reporting for two years: the Steam content delivery platform and Source Engine are coming to Linux.*

*We have confirmed that Valve's latest and popular titles like Half-Life 2, Counter-Strike: Source, and Team Fortress 2 are among the first of the Steam Linux titles, similar to the Mac OS X support. The released Linux client should be available by the end of summer.*

Keep in mind that's "end of summer" Valve time - which could easily mean Halloween. But I suspect we'll be playing some Source games by the end of the year on Linux boxes.

---

### Post by Random_Dude on 2010-05-12
Not my favourite games, but still it's good to see companies slowly starting to get interest in Linux.

Cheers :cool:

---

### Post by zekopeko on 2010-05-12
Valve didn't actually confirm it. There is no official announcement from them.

---

### Post by efikkan on 2010-05-12
Phoronix has used two articles as source for this "official" announcement, but none of the articles has sources, and Valve has still not announced anything (as far as I can see), so how can we know that these two source articles did not get this from Phoronix or one of the hundreds of articles based on the news from Phoronix? Is Phoronix once again jumping to conclusions too fast?

---

### Post by Vakman on 2010-05-12
Read this before. Saw the article on Engadget as well. This is awesome. Finally, this is a very, very good thing.

---

### Post by LowSky on 2010-05-12
Sweet I can play all my 3 year old window's games again.

What I really care about is when is Half Life2: Episode 3 coming out?

---

### Post by Vakman on 2010-05-12
Valve has not confirmed yet but they will.
So happy about this, one of the main reasons for my dual boot.
Team Fortress 2 :D

---

### Post by DeadSuperHero on 2010-05-12
I'd only really be happy if I could get some Portal goodness.

---

### Post by Kafubie on 2010-05-12
Just to want to put it out there.
[http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1)

---

### Post by pwnst*r on 2010-05-12
I'm thinking most of you won't be happy.  Ever. 

A company like Valve heading in the right direction and people still cry.

---

### Post by DrMelon on 2010-05-12
Portal is free for a short time. If you don't have it, get it now.

---

### Post by RiceMonster on 2010-05-12
This would indeed be cool if it actually gets confirmed by Valve. There's been speculation about this for years, and it's always nice to see more software ported to Linux. I'll probably give it a shot. I'm not much of a gamer though.

---

### Post by Tristam Green on 2010-05-12
> **DeadSuperHero said:**
> I'd only really be happy if I could get some Portal goodness.

I'm down for Day of Defeat, Team Fortress 2, and Counter-strike :O

Those would actually get me back to Linux lol.

> **pwnst*r said:**
> I'm thinking most of you won't be happy.  Ever. 

A company like Valve heading in the right direction and people still cry.

You of all people shouldn't be surprised anymore, dude.

> **DrMelon said:**
> Portal is free for a short time. If you don't have it, get it now.

It is?  I gotta get this :|

---

### Post by Method X on 2010-05-12
Oh great.
I have Orange box. Wanna play it in linux :)

---

### Post by dondiego2 on 2010-05-12
> **JMisczak said:**
> [Source]("http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1")

*Valve Corporation has today rolled out their Steam Mac OS X client to the general public and confirmed something we have been reporting for two years: the Steam content delivery platform and Source Engine are coming to Linux.*

*We have confirmed that Valve's latest and popular titles like Half-Life 2, Counter-Strike: Source, and Team Fortress 2 are among the first of the Steam Linux titles, similar to the Mac OS X support. The released Linux client should be available by the end of summer.*

Keep in mind that's "end of summer" Valve time - which could easily mean Halloween. But I suspect we'll be playing some Source games by the end of the year on Linux boxes.


Being a Chemical Engineer, software and games was not what I first thought of when I saw the words Steam and Valve in the subject line :-)

---

### Post by ubunterooster on 2010-05-12
LOL, I saw thread title and thought "blowing off steam"

Thanks for the info.

---

### Post by snip3r8 on 2010-05-12
Steam is great if you dont have internet limits....this basically means that here in darkest Africa it really sucks,right now i cant even get onto google or even click on that dam link

---

### Post by Kafubie on 2010-05-12
There was a other article talking about the mac's version.
At the end it said " Valve confirmed that steam will be on the linux platform too _"in the following months."_

---

### Post by forrestcupp on 2010-05-12
Steam is the client they use to manage and download games and patches.  "Source" is the engine they use to make the games.  It doesn't do a lot of good to have a Linux client for a download manager if the things it downloads aren't ported to work with Linux.

---

### Post by Tristam Green on 2010-05-12
> **forrestcupp said:**
> Steam is the client they use to manage and download games and patches.  "Source" is the engine they use to make the games.  It doesn't do a lot of good to have a Linux client for a download manager if the things it downloads aren't ported to work with Linux.

shh.  let me dream.

---

### Post by ELD on 2010-05-12
I do hope it is true, noted the article on [GamingOnLinux]("http://www.gamingonlinux.info")

---

### Post by screaminj3sus on 2010-05-12
This doesnt mention l4d. Articles about OSX said they are porting L4D and L$d2 to OSX, will they port them to linux as well?

---

### Post by Crunchy the Headcrab on 2010-05-12
> **forrestcupp said:**
> Steam is the client they use to manage and download games and patches.  "Source" is the engine they use to make the games.  It doesn't do a lot of good to have a Linux client for a download manager if the things it downloads aren't ported to work with Linux.
We remain confident that Valve is aware of this.

---

### Post by Ylon on 2010-05-12
[http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html](http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html)

"*Valve has also confirmed that it will make Steam available to Linux users in the coming months. *"

---

### Post by Objekt on 2010-05-12
I hope this turns out to be true.  I bought the Half Life: Game of the Year Edition package in early 2003 and have enjoyed free Counterstrike, Day of Defeat, America's Army etc. through Steam ever since.  It would be nice not to have to reboot into Windows XP to play Steam games.


I also hope Valve's sound implementation plays well with PulseAudio.  The biggest problem I have with gaming in Ubuntu is that the Linux version of Teamspeak 3 is buggy and worthless.  I therefore have to either reboot into Windows, or not talk to my friends when playing games in Ubuntu.  I would rather use the voice chat built into Steam games than run a separate app.

---

### Post by Mr. Picklesworth on 2010-05-12
Can Phoronix go one day without posting &#8220;definitive proof&#8221; that Steam for Linux exists?

Granted, I would be very happy if it *was* rolled out, because then they would have no choice but to be silent and stop polluting my feed reader with the same story again and again and again&#8230;

---

### Post by ELD on 2010-05-12
> **Ylon said:**
> [http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html](http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html)

"*Valve has also confirmed that it will make Steam available to Linux users in the coming months. *"

Yeah but who is their source? Phoronix lol.

I keep saying this and no one seems to listen but a few i can see have some common sense.

Valve has NOT confirmed anything, until they do officially it doesn't exist.

Deal with it :)

---

### Post by Yvan300 on 2010-05-12
This would be awsome if only ATI released a driver for my card :(

---

### Post by Ylon on 2010-05-12
[http://socialmediaseo.net/2010/05/12/steam-for-mac/](http://socialmediaseo.net/2010/05/12/steam-for-mac/)

6 hours ago
"[I]Steam for [SIZE="6"]Linus[/SIZE] Coming Soon

Runic Games has also confirmed that Stream will be available to Linus users in the coming months.

According to the Steam website, you can instantly access your favorite games with over 1,100 games are available to purchase, download, and play from any computer.

Stream features new releases, indie hits, casual favorites, and everything in between.

There is also a Steam community where you can talk non-stop, 24 hours a day about anything and everything relating to gaming.[/I]"
Trovalds should be happy <_<

---

### Post by SamD42 on 2010-05-12
> **Objekt said:**
> I hope this turns out to be true.  I bought the Half Life: Game of the Year Edition package in early 2003 and have enjoyed free Counterstrike, Day of Defeat, America's Army etc. through Steam ever since.  It would be nice not to have to reboot into Windows XP to play Steam games.


I also hope Valve's sound implementation plays well with PulseAudio.  The biggest problem I have with gaming in Ubuntu is that the Linux version of Teamspeak 3 is buggy and worthless.  I therefore have to either reboot into Windows, or not talk to my friends when playing games in Ubuntu.  I would rather use the voice chat built into Steam games than run a separate app.

Ts3 recent builds play fine with pulseaudio for me, no more 100% cpu bug. Regardless, if you disable pulseaudio autospawning then you can just kill pulse before you use it, and start it again afterwards.

As to the prospect of native steam and source games on Linux, I am rather ecstatic!

---

### Post by beastrace91 on 2010-05-12
> **JMisczak said:**
> [Source]("http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1")

*Valve Corporation has today rolled out their Steam Mac OS X client to the general public and confirmed something we have been reporting for two years: the Steam content delivery platform and Source Engine are coming to Linux.*

*We have confirmed that Valve's latest and popular titles like Half-Life 2, Counter-Strike: Source, and Team Fortress 2 are among the first of the Steam Linux titles, similar to the Mac OS X support. The released Linux client should be available by the end of summer.*

Keep in mind that's "end of summer" Valve time - which could easily mean Halloween. But I suspect we'll be playing some Source games by the end of the year on Linux boxes.

All I have to say is - consider your source. Until I hear it from the horse's mouth I won't believe it.

~Jeff

---

### Post by CharlesA on 2010-05-12
Don't forget to mention that Linux support will be [coming soon]("http://developer.valvesoftware.com/wiki/Valve_Time").

---

### Post by Xbehave on 2010-05-12
[http://store.steampowered.com/public/client/steam_client_linux](http://store.steampowered.com/public/client/steam_client_linux)

and the bash snippet are pretty good proof that it is in the works. TBH i always just wanted the client, then individual games can be/not be available.

---

### Post by ad_267 on 2010-05-12
**THIS IS NOT OFFICIAL**.

Valve hasn't said anything themselves. It's just two random websites that probably got their information from Phoronix, and when they published one sentence saying Source is coming to Linux, Phoronix took that as confirmation.

---

### Post by phoronix on 2010-05-12
> **ad_267 said:**
> Valve hasn't said anything themselves. It's just two random websites that probably got their information from Phoronix, and when they published one sentence saying Source is coming to Linux, Phoronix took that as confirmation.

I have my own sources.

---

### Post by Legendary_Bibo on 2010-05-12
Sweet, I bought several games through steam when I had windows. Here's to hoping those games can run better on linux than Vista :popcorn:!!!

---

### Post by ELD on 2010-05-12
> **phoronix said:**
> I have my own sources.

As you keep saying.

But as i keep saying until Valve officially announce it on their website it doesn't exist.

I do hope they release it though, would sure make a lot of people happy.

---

### Post by dragos240 on 2010-05-12
> **Xbehave said:**
> [http://store.steampowered.com/public/client/steam_client_linux](http://store.steampowered.com/public/client/steam_client_linux)

and the bash snippet are pretty good proof that it is in the works. TBH i always just wanted the client, then individual games can be/not be available.

I downloaded the files, and extracted the contents to ~/steam

It updates for about 30 seconds, and then complains that steamui.so isn't there, it is. Well, it IS in development, I didn't expect it to work.

---

### Post by naikon89 on 2010-05-12
An official response would be nice. You can't say the client is official when Valve have not said anything in relation to the client. At present, there is no linux client and you damm know it.

---

### Post by Groucho Marxist on 2010-05-12
It blows my mind that I will soon be able to play Sid Meier's Civilization V on my laptop without having to jump through VirtualBox hoops.

---

### Post by naikon89 on 2010-05-12
> **ELD said:**
> @[darklegion]("http://ubuntuforums.org/member.php?u=490592") Carmack himself said " a Linux port is unlikely" and he is still the top man when it comes to the decisions on it regardless of whatever anyone else says. 

TTimo has stated his intentions. Carmack does not care if it's off company time. Also, considering he is a big OSS advocate, I can't see him blocking Linux ports. Infact, since 2000, id have given their usual response:
"We will consider a port when we ship to windows" Check his old postings in the slashdot archives. Anyway, higher quality control results from this process, so It's a win-win for id and the community at the end of the
day. Carmack was probably pissed because I pestered him more than I should have. The man has enough on his plate with Rage and such. Check out the news comments for RTCW on Linuxgaming.com. Surprising.

---

### Post by themusicalduck on 2010-05-12
> **dragos240 said:**
> I downloaded the files, and extracted the contents to ~/steam

It updates for about 30 seconds, and then complains that steamui.so isn't there, it is. Well, it IS in development, I didn't expect it to work.

How did you manage to download the files from that link exactly?

---

### Post by pizza-is-good on 2010-05-12
nice, now I have something renowned to tell people about when they accuse linux of not playing games.

---

### Post by JDShu on 2010-05-12
> **Crunchy the Headcrab said:**
> We remain confident that Valve is aware of this.

I lol'd.

---

### Post by Sealbhach on 2010-05-12
> **Kafubie said:**
> There was a other article talking about the mac's version.
At the end it said " Valve confirmed that steam will be on the linux platform too _"in the following months."_

Please be aware of[ Valve Time]("http://developer.valvesoftware.com/wiki/Valve_Time").


.

---

### Post by dragos240 on 2010-05-12
> **themusicalduck said:**
> How did you manage to download the files from that link exactly?

The file is a text file. Containing valid links to zip files. Extract all of them to a directory, and then chmod +x steam.sh. Run, and it will fail with my error.

---

### Post by themusicalduck on 2010-05-12
> **dragos240 said:**
> The file is a text file. Containing valid links to zip files. Extract all of them to a directory, and then chmod +x steam.sh. Run, and it will fail with my error.

I'm still not quite following you :neutral:

That text file doesn't contain any links but just looks like a script to me. I'm probably missing something obvious here!

---

### Post by dragos240 on 2010-05-12
> **themusicalduck said:**
> I'm still not quite following you :neutral:

That text file doesn't contain any links but just looks like a script to me. I'm probably missing something obvious here!

[1st link]("http://store.steampowered.com/public/client/public_all.zip.24b5c965743bf147f8cee0d075259ccdd985e948")
[2nd]("http://store.steampowered.com/public/client/skins_all.zip.6a58428db616736d79a3374ba75abd29e2c1276f")
[3rd]("http://store.steampowered.com/public/client/bins_linux.zip.fe49bbc71b714853c42bb28442fff5b0c47d027c")
[Last]("http://store.steampowered.com/public/client/steam_linux.zip.9030a2f3cefcbe80f0924426ed4bcf7b5b03cd5a")

---

### Post by pizza-is-good on 2010-05-12
> **Sealbhach said:**
> Please be aware of[ Valve Time]("http://developer.valvesoftware.com/wiki/Valve_Time").


.

Good point!

---

### Post by themusicalduck on 2010-05-12
> **dragos240 said:**
> [1st link]("http://store.steampowered.com/public/client/public_all.zip.24b5c965743bf147f8cee0d075259ccdd985e948")
[2nd]("http://store.steampowered.com/public/client/skins_all.zip.6a58428db616736d79a3374ba75abd29e2c1276f")
[3rd]("http://store.steampowered.com/public/client/bins_linux.zip.fe49bbc71b714853c42bb28442fff5b0c47d027c")
[Last]("http://store.steampowered.com/public/client/steam_linux.zip.9030a2f3cefcbe80f0924426ed4bcf7b5b03cd5a")

Ah, thanks! I thought it would be something like that but didn't quite type it in right.

It downloaded a load of updates and seemed to be installing them, but then go stuck on a loop trying to download a file and failing to.

---

### Post by yester64 on 2010-05-12
What is this blog? The reference to the telegraph did not mention linux at all. So i am not sure about this at all.
It seem to me more wishful thinking than actual proof.

Steam on Linux as a server makes absolute sense, but not really on the client site.
How many people game on linux. I think you can count them.
So it would not make any financial sense to develop a steam client for linux.

But i really like to proofen wrong if it hits linux in reality.

What will they use for the windows games. Wine or something different that actually works out of the box?

---

### Post by dragos240 on 2010-05-12
> **yester64 said:**
> What is this blog? The reference to the telegraph did not mention linux at all. So i am not sure about this at all.
It seem to me more wishful thinking than actual proof.

Steam on Linux as a server makes absolute sense, but not really on the client site.
How many people game on linux. I think you can count them.
So it would not make any financial sense to develop a steam client for linux.

But i really like to proofen wrong if it hits linux in reality.

What will they use for the windows games. Wine or something different that actually works out of the box?

Well.... Steam will port their games, I have no clue about other games. But anyway, see the links to the client, on the OFFICIAL VALVE WEBSITE. That is proof.

---

### Post by Merk42 on 2010-05-12
> **dragos240 said:**
> Well.... Steam will port their games, I have no clue about other games. But anyway, see the links to the client, on the OFFICIAL VALVE WEBSITE. That is proof.

VALVE would port games.
Also IF Steam comes to Linux that doesn't mean the entire catalog of games suddenly works in Linux

**Steam is only the distribution model**
The games themselves would need to be ported as well. Given some of Valve's Source games were ported to OS X it wouldn't be as much work to port them to Linux.

---

### Post by cisforcojo on 2010-05-12
ELD, I just read this from the Telegraph:
> 
Valve has also confirmed that it will make Steam available to Linux users in the coming months.


[http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html](http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html)

This isn't Valve's website, but it's a pretty reputable source.

---

### Post by P1umb3r on 2010-05-12
> **yester64 said:**
> What is this blog? The reference to the telegraph did not mention linux at all. So i am not sure about this at all.
It seem to me more wishful thinking than actual proof.

Steam on Linux as a server makes absolute sense, but not really on the client site.
How many people game on linux. I think you can count them.
So it would not make any financial sense to develop a steam client for linux.

But i really like to proofen wrong if it hits linux in reality.

What will they use for the windows games. Wine or something different that actually works out of the box?

The number of gamers on Linux is tiny because there are no games for Linux.  Once all the source based games are ported, tons of dual booters who have windows just for gaming will almost certainly play their games on Linux.

---

### Post by sandyd on 2010-05-12
> **yester64 said:**
> What is this blog? The reference to the telegraph did not mention linux at all. So i am not sure about this at all.
It seem to me more wishful thinking than actual proof.

Steam on Linux as a server makes absolute sense, but not really on the client site.
How many people game on linux. I think you can count them.
So it would not make any financial sense to develop a steam client for linux.

But i really like to proofen wrong if it hits linux in reality.

What will they use for the windows games. Wine or something different that actually works out of the box?
heres real proof: [https://twitter.com/NixiePixel/status/13883784596](https://twitter.com/NixiePixel/status/13883784596)
+ you can download the client... and run it... even though it fails to run.

---

### Post by Yes on 2010-05-12
Still not seeing where Valve has officially said they will be porting it to Linux.  So far everything just points back to the Phoronix article which presents compelling evidence, but is certainly not an official word.

It'd be very cool if it were true though.

---

### Post by yester64 on 2010-05-12
Mm... i am not convinced. 
But who am i.
If Valve is really working on a linux client now, then we never will see HL2 Episode 3 for another 3 years.

I did not want to ruin everyones hope. So i am out.

---

### Post by 3rdalbum on 2010-05-12
> **Yes said:**
> Still not seeing where Valve has officially said they will be porting it to Linux.  So far everything just points back to the Phoronix article which presents compelling evidence, but is certainly not an official word.

The Telegraph article that was linked at the start of this thread mentions it. The very last sentence.

---

### Post by doorknob60 on 2010-05-12
Why should I believe a Phoronix article just because it says "confirmed." I do believe that it will happen, and sooner rather than later, but it's not confirmed yet, as far as I can see. For example, look at the date on this "confirmed" report: [http://www.phoronix.com/scan.php?page=article&item=steam_confirmation&num=1](http://www.phoronix.com/scan.php?page=article&item=steam_confirmation&num=1) Still, I thinks it's a close as we can get to being "confirmed" without official announcement, so I can live with that.

---

### Post by ELD on 2010-05-13
> **cisforcojo said:**
> ELD, I just read this from the Telegraph:


[http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html](http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html)

This isn't Valve's website, but it's a pretty reputable source.

They don't provide any evidence either, for all we know they could be using Phoronix articles as their source.

I keep saying it and will say it again, don't believe squat until it is actually CONFIRMED, valve haven't confirmed it, don't get your hopes up over nothing people!

---

### Post by AxelMan0 on 2010-05-13
THIS MEANS I CAN FINALLY _**[COLOR=Green]ELIMINATE WINDOWS FROM MY SYSTEM!!!:guitar:[/COLOR]**_

---

### Post by 3rdalbum on 2010-05-13
> **AxelMan0 said:**
> THIS MEANS I CAN FINALLY _**[COLOR=Green]ELIMINATE WINDOWS FROM MY SYSTEM!!!:guitar:[/COLOR]**_

Yes, if all the games you play are based around the Source engine.

Steam coming to Linux **doesn't mean that all the games available on Steam will come too**. It just means that, should a developer make a Linux version of their game, they can use Steam to distribute it.

Steam on Linux is a positive step, and I'm looking forward to playing the planned ports of Source-based games (Half-Life, Postal, Counter Strike etc) but it's only a first step.

---

### Post by Cavsfan on 2010-05-13
Check this out, although there are no dates listed, it is new news!

_[http://www.geeky-gadgets.com/valves-steam-platform-headed-to-linux-13-05-2010/](http://www.geeky-gadgets.com/valves-steam-platform-headed-to-linux-13-05-2010/)_

---

### Post by Modplanman on 2010-05-13
If Valve don't debunk this by tomorrow, then it's official. If indeed this is all false hope, then Valve are not gonna let this get reported everywhere as if it's fact (which is exactly what's happening) as this can cause harm both in PR and professionally.

The complete and total silence at the moment seems just as telling as the public and partially working version found (and still being updated by the way).

---

### Post by u235sentinel on 2010-05-13
> **Modplanman said:**
> If Valve don't debunk this by tomorrow, then it's official. If indeed this is all false hope, then Valve are not gonna let this get reported everywhere as if it's fact (which is exactly what's happening) as this can cause harm both in PR and professionally.

The complete and total silence at the moment seems just as telling as the public and partially working version found (and still being updated by the way).

Personally I'm not worried either way.  The argument is pointless anyway.  If we want to play the games either use Wine/Crossover Games or get Windows on a partition.

I've got both worlds.  My preference is Linux.  I have Valve games running just swell under Crossover Games.  I also have a computer running XP and can also play those games which are hard to get working under Linux.

Then I have Linux...   for everything else.  I've bought a dozen or so games for it.  All so far are very nice.  If valve brings their games to Linux then I'll be running those natively as well.  If they don't then I'm not happy about that however I am still a customer and playing the games just fine.

If the rumors are true then I'm so there.  I've made my opinions known to them on several occasions and look forward to the future.

Windows isn't always going to be top dog you know.  At one point is was OS/2 (I know that's debatable),  Before that various flavors of DOS and so on.

Things change always do...

---

### Post by Objekt on 2010-05-13
Regardless of whether there is or isn't a Linux Steam client on the way, Valve is giving away the game Portal, complete and free, from now until the 24th.  Anyone with an existing Steam account is eligible, as is anyone who signs up for one between now and then.  I reinstalled Steam on my Windows XP partition & downloaded Portal overnight.  

That goes for Mac users as well.  In fact, it looks like you will get to play a game on any platform you have, once you buy it.  That's pretty cool, and typical of how Valve does business.  Electronic Arts or Ubisoft would demand you pay $49.95 all over again for the Mac version of one of their games, if they even made any Mac games.

Those stuck on dialup Internet might want to start downloading Portal now, to beat the deadline. :P

We now return you to our regularly-scheduled speculation.

---

### Post by CharlesA on 2010-05-13
I wouldn't want to think about how long it would take to download the 3.8GB on a 56K modem.

It hurts just to think about it!

---

### Post by efikkan on 2010-05-13
More articles on this subject are appearing all over the web, I can't find any wich contains a reliable source. Until Valve publish something official, it's not official. Claiming anything else is simply not true.

If anyone claims Valve spoke to them about this matter, then how can we know you are not making it up?

---

### Post by Objekt on 2010-05-13
Assuming a best-case, steady 52 kilobyte/s dialup connection, it would "only" take about 24 hours. 

Nope, I still don't miss those days at all.

---

### Post by Shakz on 2010-05-13
Well if steam currently has 25million users.....and ubuntu has 12 million users and supposedly fedora has 24 million users along with the other distros following. I can see where the attraction for steam would be. 

Considering thier current PC based user count, Linux offers a significant market share.

---

### Post by LeifAndersen on 2010-05-13
> **Objekt said:**
> Regardless of whether there is or isn't a Linux Steam client on the way, Valve is giving away the game Portal, complete and free, from now until the 24th.  Anyone with an existing Steam account is eligible, as is anyone who signs up for one between now and then.  I reinstalled Steam on my Windows XP partition & downloaded Portal overnight.  

That goes for Mac users as well.  In fact, it looks like you will get to play a game on any platform you have, once you buy it.  That's pretty cool, and typical of how Valve does business.  Electronic Arts or Ubisoft would demand you pay $49.95 all over again for the Mac version of one of their games, if they even made any Mac games.

Those stuck on dialup Internet might want to start downloading Portal now, to beat the deadline. :P

We now return you to our regularly-scheduled speculation.

I think when they say free until May 24, they mean you can play it until the 24th of May, and then the game expires, like a 12 day free trial sort of thing.

---

### Post by Crunchy the Headcrab on 2010-05-13
> **LeifAndersen said:**
> I think when they say free until May 24, they mean you can play it until the 24th of May, and then the game expires, like a 12 day free trial sort of thing.
I don't think so.
> "Capital news! But the excellent puzzle adventure Portal won over 40  Game of the Year awards; Surely it must cost at least five or six    hundred dollars."    
     You'd think that, especially since it actually won over ***70***  Game of the Year Awards. But, like we keep saying, Portal is   free.  Free on the Mac. Free on the PC. But only until May 24th. [COLOR=Red]So you only  have a few days to decide if your free copy of Portal is worth the price  we're   currently charging[/COLOR] - which is you ever-so-slightly moving your  index finger just barely enough to **click the big red "download"  button right there to the left.**
Valve

---

### Post by Objekt on 2010-05-13
No, it's not a trial version.  It's the complete Portal game, yours to keep, for as long as you want (barring Valve turning off their DRM servers anyway...).

Here's the page: [http://store.steampowered.com/freeportal/]("http://store.steampowered.com/freeportal/")

---

### Post by Tristam Green on 2010-05-13
qualifications for an "oh snap!" met.

issuing "oh snap!"







oh snap!

---

### Post by LeifAndersen on 2010-05-13
Oh, really, cool, thanks people.  It previously wasn't worth it to me to have to boot into windows, download steam (while figuring out how to create an account, etc. etc.), and then download it...but now it is.

So I would assume that it's tied to your steam account though, right?  (Aka, I would be able to blow away my windows partition, and be able to redownload it after May 24, if I already got it).

---

### Post by Tristam Green on 2010-05-13
> **LeifAndersen said:**
> Oh, really, cool, thanks people.  It previously wasn't worth it to me to have to boot into windows, download steam (while figuring out how to create an account, etc. etc.), and then download it...but now it is.

So I would assume that it's tied to your steam account though, right?  (Aka, I would be able to blow away my windows partition, and be able to redownload it after May 24, if I already got it).

Yes.  I redownload all my Steam games when I rebuild, and I actually do it as well on every computer in the house.  I can only be logged in on one computer at a time though.

---

### Post by Objekt on 2010-05-13
Yes, the free Portal install is tied to the Steam account.  So yeah, you could re-download it later, as long as you originally installed before May 24th.

I keep Steam on a different partition from Windows itself, so that I don't have to re-download everything after reinstalling Windows.

---

### Post by u235sentinel on 2010-05-13
> **efikkan said:**
> More articles on this subject are appearing all over the web, I can't find any wich contains a reliable source. Until Valve publish something official, it's not official. Claiming anything else is simply not true.

If anyone claims Valve spoke to them about this matter, then how can we know you are not making it up?

Why would we lie?

;-)

---

### Post by Cavsfan on 2010-05-13
You get to talk to a pretty girl
She's everything you dream about... 

 But don't fall in love
She's a beauty
She's one in a million girls
She's a beauty
Why would I lie
Why would I lie?

(Couldn't help myself)

EDIT: It's from an 80s song by the Tubes, probably before most of your times.

---

### Post by PurposeOfReason on 2010-05-13
This all means nothing without good graphic drivers and other companies taking notice.

---

### Post by Tristam Green on 2010-05-13
> **PurposeOfReason said:**
> This all means nothing without good graphic drivers and other companies taking notice.

Even if it were only Valve to release their games with a Linux Steam client, that'd be enough for me in the interim.

---

### Post by Objekt on 2010-05-13
Having Linux versions of Valve titles would allow more meaningful testing of Nvidia's and ATI's proprietary driver packages for Linux.  We could find out for sure whether, for example, ATI's Linux drivers are actually crippled compared to the Windows version, by running Half-Life 2 on both platforms.  

I know there are a few games which are both cross-platform, and able to max out current graphics hardware, but not many.  Nexuiz is actually the only example I can think of.  You can turn its graphics pretties up until your video card smokes.  

Any others?  There was a Linux version of Simcity 3000, and Urban Terror 4.1 covers all 3 platforms (Mac, Windows, Linux).  But it is based on the Quake 3 engine, so not exactly a great challenge to recent graphics cards.

---

### Post by ghindo on 2010-05-13
> **zekopeko said:**
> Valve didn't actually confirm it. There is no official announcement from them.Exactly.  Until there is an official announcement or download available from Valve, I'll remain skeptical.

---

### Post by gemmakaru on 2010-05-13
Well time will tell exactly what will be ported and what the quality will be but I think this is a huge step forward.  Finger corssed it works out.  I hope Vampire the masquerade Bloodlines gets ported.  It runs on the half life two engine so it should work!  I am crossing my fingers but not holding my breath if you know what I mean.

---

### Post by Smart Viking on 2010-05-13
This is such good news! I am looking forward to playing TF2 again, since i have not touched my Valve account in some time.

I am 100% this is true, for everyone saying something else, i will brake a window!

---

### Post by ELD on 2010-05-13
> **Cavsfan said:**
> You get to talk to a pretty girl
She's everything you dream about... 

 But don't fall in love
She's a beauty
She's one in a million girls
She's a beauty
Why would I lie
Why would I lie?

(Couldn't help myself)

EDIT: It's from an 80s song by the Tubes, probably before most of your times.

Your a strange man :P

Anyway, Valve has NO WHERE confirmed it, why are all these websites stating it as a fact, it's frustrating.

---

### Post by Cavsfan on 2010-05-13
> **ELD said:**
> Your a strange man :P

Anyway, Valve has NO WHERE confirmed it, why are all these websites stating it as a fact, it's frustrating.

True! :P (the "Why would we lie?" comment reminded me of the song. The song was popular probably before any of you were born!)

But, since the Mac version was just released, it can only be a matter of time before they satisfy the only other sector. 
I believe we'll hear something from Valve within a couple weeks. But, that's just my guess.

---

### Post by Mr. Picklesworth on 2010-05-13
> **Smart Viking said:**
> 
[EMAIL="contact@valvesoftware.com"]contact@valvesoftware.com[/EMAIL]  <--- SPAM THIS E-MAIL

Uh, no, don't spam Valve, please. I like them.

---

### Post by pwnst*r on 2010-05-13
> **Smart Viking said:**
> This is such good news! I am looking forward to playing TF2 again, since i have not touched my Valve account in some time.

I am 100% this is true, for everyone saying something else, i will brake a window!



[EMAIL="contact@valvesoftware.com"]contact@valvesoftware.com[/EMAIL]  <--- SPAM THIS E-MAIL

1) I'd love to see you brake a window.
2) Spamming Valve's inbox(es).  Really?

---

### Post by Smart Viking on 2010-05-13
> **pwnst*r said:**
> 1) I'd love to see you brake a window.
2) Spamming Valve's inbox(es).  Really?

2) Thats what you do. :P

---

### Post by Bölvaður on 2010-05-13
I will keep my money locked away and will not get the key out until I can see something official about the linux client on their website.

---

### Post by pwnst*r on 2010-05-13
> **Smart Viking said:**
> 2) Thats what you do. :P

What?

---

### Post by Bölvaður on 2010-05-13
> **pwnst*r said:**
> What?
he's trying to get Valve to think if they make a linux client they will be flooded every day with rants from linux users complaining about something... like some windows only games are not playable....

---

### Post by madhi19 on 2010-05-13
Correct me if am wrong but every game that Valve will port to Mac will need to support OpenGL so from mac port to a Linux port it only the next logical step!

---

### Post by pwnst*r on 2010-05-13
> **Bölvaður said:**
> he's trying to get Valve to think if they make a linux client they will be flooded every day with rants from linux users complaining about something... like some windows only games are not playable....

Oh.

Thanks.

---

### Post by fatality_uk on 2010-05-13
It is happening!!
[http://www.valvesoftware.com/job-SenSoftEngineer.html](http://www.valvesoftware.com/job-SenSoftEngineer.html)
Valve wouldn't offer jobs if it wasn't on the cards!

---

### Post by mamamia88 on 2010-05-13
cool.  not that my laptop can really handle games but it's good to know for the future.

---

### Post by Smart Viking on 2010-05-13
> **fatality_uk said:**
> It is happening!!
[http://www.valvesoftware.com/job-SenSoftEngineer.html](http://www.valvesoftware.com/job-SenSoftEngineer.html)
Valve wouldn't offer jobs if it wasn't on the cards!

Thanks for the link, now we definitely know for sure! :D

---

### Post by Brent0 on 2010-05-13
This is a MAJOR leap forward in the Linux community. I can't wait!!! :popcorn:

---

### Post by themusicalduck on 2010-05-13
> **fatality_uk said:**
> It is happening!!
[http://www.valvesoftware.com/job-SenSoftEngineer.html](http://www.valvesoftware.com/job-SenSoftEngineer.html)
Valve wouldn't offer jobs if it wasn't on the cards!

I think I've seen that link before. Valve have had a job listing for people with Linux experience for years I believe. Besides, if the job listing is still there, then that just means they have no one employed (or not enough people) to do the porting.

If anything that link just tells us that it's more ways off..

I'm still somewhat hopeful though.

---

### Post by murderslastcrow on 2010-05-13
I look forward to the day that Wine has no purpose, since most programs will be cross-platform, anyway. XD Then again, that's a horrible thing to hope for. Those poor souls slaving away at Wine, all for nothing.

Nah, Wine rocks, and hopefully the games that don't get ported to the Linux Steam client will be made to work in Wine, so that people don't have to pick and choose so much.

Still, this'll make Linux a primary OS for a lot of gamers I know.

---

### Post by dearingj on 2010-05-13
Can't wait to hear an official confirmation of Steam and Source supporting Linux. I do think they are going to sometime.

What I'd also like to know is if/when Steam's [stats page]("http://store.steampowered.com/stats/") will show the number of users per operating system, as opposed to just the total number as it does now. It'll be interesting to see how many Linux and Mac gamers there really are on Steam, and how much the Windows number goes down as a result of users switching to their preferred non-Windows OS. There's a [thread on this subject]("http://forums.steampowered.com/forums/showthread.php?t=1266834") on the Steam forums.

---

### Post by 3rdalbum on 2010-05-14
> **Objekt said:**
> Assuming a best-case, steady 52 kilobyte/s dialup connection, it would "only" take about 24 hours.

More like 10 days; dialup modems get up to around 5 kilobytes per second, not 50 kilobytes per second.

---

### Post by murderslastcrow on 2010-05-14
That'd be a very good idea, and would give some statistics that could be useful to businesses considering porting their software to other platforms.

---

### Post by yester64 on 2010-05-14
> **fatality_uk said:**
> It is happening!!
[http://www.valvesoftware.com/job-SenSoftEngineer.html](http://www.valvesoftware.com/job-SenSoftEngineer.html)
Valve wouldn't offer jobs if it wasn't on the cards!

> 
      **Employment opportunities**

     
         [IMG]http://www.valvesoftware.com/img/arrow.gif[/IMG] **Senior Software Engineer**
        
        **Description**
      Lead engineer and architect on product integration into the highly  available digital distribution platform called "Steam".  Utilize  business/commerce background and engineering skills to drive next  generation features for software developed by Valve.
      
           **Responsibilities**
.....
[IMG]http://www.valvesoftware.com/img/blacksquare.gif[/IMG][SIZE=4][COLOR=Red]** Port Windows-based games to the  Linux platform.**[/COLOR][/SIZE]
        [IMG]http://www.valvesoftware.com/img/blacksquare.gif[/IMG] Test, document, and maintain  large scale networking installations and their assorted protocols
        [IMG]http://www.valvesoftware.com/img/blacksquare.gif[/IMG] oversee and implement quality  assurance of applications in house and third party games distributed on  Steam™
.....
 

This could be indeed a hint.
At least this is the strongest hunch so far. Still doesn't mean that it will happen eventually. But at least its a hint.

---

### Post by fatality_uk on 2010-05-14
BTW, that's an old link, the position is now closed. Has been for months.

---

### Post by formaldehyde_spoon on 2010-05-14
I haven't bought a game since my Atari ST days, but if this happens I'll get my wallet out...

---

### Post by AxelMan0 on 2010-05-14
> **3rdalbum said:**
> Yes, if all the games you play are based around the Source engine.

Steam coming to Linux **doesn't mean that all the games available on Steam will come too**. It just means that, should a developer make a Linux version of their game, they can use Steam to distribute it.

Steam on Linux is a positive step, and I'm looking forward to playing the planned ports of Source-based games (Half-Life, Postal, Counter Strike etc) but it's only a first step.

I'm aware of that, but most of my games are on the source engine, and I'm willing to sacrifice unreal tournament 3 and Crysis to move to an all-linux system. Not to mention Wine for other non-source games.

---

### Post by MrNatewood on 2010-05-14
> **fatality_uk said:**
> BTW, that's an old link, the position is now closed. Has been for months.

If it's closed for a few months it means someone is already working on it for a few months ;)

---

### Post by Objekt on 2010-05-14
> **AxelMan0 said:**
> I'm aware of that, but most of my games are on the source engine, and I'm willing to sacrifice unreal tournament 3 and Crysis to move to an all-linux system. Not to mention Wine for other non-source games.

I'm nearly with you there.  Crysis is fun, but it's very, very mean to my graphics card.

---

### Post by Meep3D on 2010-05-14
> **Objekt said:**
> Assuming a best-case, steady 52 kilobyte/s dialup connection, it would "only" take about 24 hours. 

Nope, I still don't miss those days at all.

kilobits != kilobytes.  It would in fact take (best case) eight days.

Also why the appeal of this?  Isn't Steam closed source DRM, and features just about everything complained about in the Badvista, Windows 7 sins etc campaigns?  Surely if you're going to go for a proprietary solution for games such as Steam you might as well go for Windows as well - at least then you can play the whole range rather than just a subset.

---

### Post by Tristam Green on 2010-05-14
> **Meep3D said:**
> Also why the appeal of this?  Isn't Steam closed source DRM, and features just about everything complained about in the Badvista, Windows 7 sins etc campaigns?  Surely if you're going to go for a proprietary solution for games such as Steam you might as well go for Windows as well - at least then you can play the whole range rather than just a subset.

Not all Linux users buy into the whole Windows 7 Sins mess.

---

### Post by RiceMonster on 2010-05-14
> **Meep3D said:**
> kilobits != kilobytes.  It would in fact take (best case) eight days.

Also why the appeal of this?  Isn't Steam closed source DRM, and features just about everything complained about in the Badvista, Windows 7 sins etc campaigns?  Surely if you're going to go for a proprietary solution for games such as Steam you might as well go for Windows as well - at least then you can play the whole range rather than just a subset.

What if they simply *prefer* Linux, and only really use Windows for a few games or 1 or 2 apps. Wouldn't you think it would be good for them to get some of those apps they use Windows for on Linux?

It's not all about being anti-proprietary or anti-Microsoft.

---

### Post by Trilby on 2010-05-14
I think it's worth spreading the news:

[http://www.itproportal.com/portal/news/article/2010/5/14/valve-rumoured-be-launching-steam-linux/](http://www.itproportal.com/portal/news/article/2010/5/14/valve-rumoured-be-launching-steam-linux/)

---

### Post by TheBuzzSaw on 2010-05-14
We've been discussing it. ;)

[http://ubuntuforums.org/showthread.php?t=1466438](http://ubuntuforums.org/showthread.php?t=1466438)

---

### Post by ELD on 2010-05-14
> **TheBuzzSaw said:**
> We've been discussing it. ;)
 
[http://ubuntuforums.org/showthread.php?t=1466438](http://ubuntuforums.org/showthread.php?t=1466438)
 
Was just about to post as well, there are many topics on it. Search is there for a reason, although it's on the first page so it's not hard to miss it....

---

### Post by donkyhotay on 2010-05-14
I don't consider it official until I see it on the steam website, even then I'll consider it probable vaporware until the download is available. Course since I hate steam (it's the reason I stopped playing HL1 mods on windows) I couldn't care less if they came out with a linux version.

---

### Post by cariboo on 2010-05-14
Merged two threads on the same subject.

---

### Post by pwnst*r on 2010-05-14
> **donkyhotay said:**
> I couldn't care less if they came out with a linux version.

You cared enough to write a paragraph.

---

### Post by fatality_uk on 2010-05-14
How fecked off are we going to be if the first game on launch is Checkers 3D :) Just a thought!!

---

### Post by gemmakaru on 2010-05-14
I just logged into vista to claim (download) my free copy of Portal.  I am amazed by how slow my mousepointer is I mean did I seriously used to use it like this. </tangent>

---

### Post by Ylon on 2010-05-14
In the end.. all the fuss about is not even Steam:but the tie Valve had with other *big* companies of games.




Instead, do really we *need* "steam" as engine? I mean, as platform to buy games?


To tell the truth, I would be more inclined to hope that someone will come up with a "online store" for gaming... but "linux community way"?

Consider this: even goin on Ubuntu, the main clients for Steam are, and will be, Windows.. then Mac... and in the very end... Linux.

Slow bug fix of the engine (comparated to winmancs)
Slow integration of winmacs features

No matter how many £$€ profit Valve would get from linux/ubuntu.. for them.. we would be always the "1%" ones. ~1% worthy clients.


On contrary if a company like Canonical will "enter the business"... well.. ."linux" will be _all_ their business.

Here's my idea in opposition to Steam:


A "Gaming" Ubuntu derivate (**P**ubunt*lay*: **P**ortable and **P**lay). With a special kernel *heavily* maximized for gaming: all "not for play" modules and feature removed (it would boot in ~2seconds?)
Pratically the only thing that "boot" is this special kernel with the essential driver for: video/audio/controls/network. <--- make your pc (**any** pc) work like a console.
No matter if you've installed Windows/Linux/BSD/Haiku/Dr-Dos whatever... the pc boot from a usb _only_ the kernel and very essential stuff: all the resources goes for opengl and network.

All the "system" goes over there:
[img]http://www.gadgetsnews.co.uk/images/Micro-SD-Card-Reader.jpg[/img]
and you can boot it from usb.

Maybe they (Canonical) could try to sell it (the microsd+usb adactor) in a package with a special edition of nvidia agp card (they got kicked out from the old xbox by microsoft... so maybe they would enjoy the idea to get back *ingame*)






I am thinking to put this in brainstorming portal.. what do you think?

---

### Post by earthpigg on 2010-05-14
i haven't read through this whole thread, but here is some very solid 100% undeniable evidence that Valve is putting their money where their mouth is (in case it hasnt been posted yet):

[http://www.valvesoftware.com/job-SenSoftEngineer.html](http://www.valvesoftware.com/job-SenSoftEngineer.html)

>  Senior Software Engineer

Description
Lead engineer and architect on product integration into the highly available digital distribution platform called "Steam". Utilize business/commerce background and engineering skills to drive next generation features for software developed by Valve.

Responsibilities
 Develop an understanding of Valve's Internet business and player community and contribute creative web-focused design solutions to improve the experience of using Valve's products
 Manage the operation of large clusters of machines running both Windows and Linux in a highly available system.
 Utilize knowledge of networking technologies and their appropriate use in large scale digital distribution systems and gaming platforms.
[I][B] Port Windows-based games to the Linux platform.
[/B][/I] Test, document, and maintain large scale networking installations and their assorted protocols
 oversee and implement quality assurance of applications in house and third party games distributed on Steam&#8482;

---

### Post by pwnst*r on 2010-05-14
> **Ylon said:**
> **stuff**

So basically what you're saying is that you don't want to play any top tier games.

---

### Post by sudoer541 on 2010-05-14
OMG!!! thats ..... [I am panicking!!!!] aaawwwww... thats Xciting!!! I cant believe it!!!! I am opening my wallet right now!!! OMG!!! I am very pleased!!!!! [I am panicking!!!]


how... exciting I mean OMG!!!
anyone else feel the same way?

---

### Post by sudoer541 on 2010-05-14
> **pwnst*r said:**
> So basically what you're saying is that you don't want to play any top tier games.

LOL ya just like me "I hate using the terminal"...everyone has his/her own preferences.

---

### Post by MilesRdz on 2010-05-14
I'm optimistic that we will get a native Steam client, it's just a matter of time.

---

### Post by fatality_uk on 2010-05-14
> **earthpigg said:**
> i haven't read through this whole thread, but here is some very solid 100% undeniable evidence that Valve is putting their money where their mouth is (in case it hasnt been posted yet):

[http://www.valvesoftware.com/job-SenSoftEngineer.html](http://www.valvesoftware.com/job-SenSoftEngineer.html)

Already done ;)

[http://ubuntuforums.org/showpost.php?p=9295122&postcount=79](http://ubuntuforums.org/showpost.php?p=9295122&postcount=79)

---

### Post by Ylon on 2010-05-14
> **pwnst*r said:**
> So basically what you're saying is that you don't want to play any top tier games.
While building steam, Valve had _only_ their game own game onto it (which were already on other channel too).

---

### Post by ELD on 2010-05-14
"Port Windows-based games to the Linux platform." Well that's pretty solid evidence since that is an official steam posting, but if memory serves hasn't that ad been there a few years now?

---

### Post by tmette on 2010-05-14
Man if this turns out to be true, then I'm going to have to build another Ubuntu machine.  The nettop I just ordered from Sys76 will not be near powerful enough to play games through Steam.

---

### Post by pwnst*r on 2010-05-14
> **Ylon said:**
> While building steam, Valve had _only_ their game own game onto it (which were already on other channel too).

What.

---

### Post by ELD on 2010-05-14
> **pwnst*r said:**
> What.

+1 lol epic fail.

I think he means when they first made steam, they only had their own games to put up which where available elsewhere anyway.

I don't get why he posted that, has nothing to do with the reply he quoted...nor this topic.

---

### Post by Objekt on 2010-05-14
> **pwnst*r said:**
> What.

He's saying the first games on Steam were Valve originals: Half-Life and all the mods.  For example, Day of Defeat, Counterstrike, and less popular ones like Ricochet.

It was only later that other publishers signed on to sell their games via Steam.

Most probably, only Valve's games will be available through the Linux Steam client at the start.  Other publishers may see a Linux port of existing or upcoming games as worthwhile, once Linux Steam takes off.  It probably is already working that way for Steam on the Mac.

---

### Post by pwnst*r on 2010-05-14
ELD and Objekt, thanks.

---

### Post by MilesRdz on 2010-05-14
[http://forums.steampowered.com/forums/showpost.php?p=14951457&postcount=856](http://forums.steampowered.com/forums/showpost.php?p=14951457&postcount=856)
Hmm... :)

---

### Post by yester64 on 2010-05-14
Well just like to say that a job posting from valve (or any other company) is a more relevant indication than a dubious blog post.
If days are long people write a lot and most is not even hold water. But if the add was indead a year old, then you certainly have to wait a long time before something will surface.
Remember Episode 3, remember. Valve you hear me?!?!?!

---

### Post by ELD on 2010-05-15
> **MilesRdz said:**
> [http://forums.steampowered.com/forums/showpost.php?p=14951457&postcount=856](http://forums.steampowered.com/forums/showpost.php?p=14951457&postcount=856)
Hmm... :)
 
I'm pretty sure that is the same thing that Phoronix has covered...

---

### Post by themusicalduck on 2010-05-15
> **ELD said:**
> I'm pretty sure that is the same thing that Phoronix has covered...

Phoronix covered the script that runs the Steam client. But the script in that screenshot looks to be a script to launch Portal.

---

### Post by Rustybolts on 2010-05-16
Someone posted this link in steam forums regarding Valve jobs. Don't know if it's already been mentioned.
[COLOR=Red]>>[/COLOR][HERE]("http://www.valvesoftware.com/job-SenSoftEngineer.html")[COLOR=Red]<<
[/COLOR]
Quote from Job advertisement
> Port Windows-based games to the Linux platform.

---

### Post by ELD on 2010-05-16
> **Rustybolts said:**
> Someone posted this link in steam forums regarding Valve jobs. Don't know if it's already been mentioned.
[COLOR=Red]>>[/COLOR][HERE]("http://www.valvesoftware.com/job-SenSoftEngineer.html")[COLOR=Red]<<
[/COLOR]
Quote from Job advertisement

It has been mentioned multiple times.

---

### Post by Rustybolts on 2010-05-16
> **ELD said:**
> It has been mentioned multiple times.
Sorry np :( (crawls back under his rock)

---

### Post by ELD on 2010-05-16
> **themusicalduck said:**
> Phoronix covered the script that runs the Steam client. But the script in that screenshot looks to be a script to launch Portal.

Yeah i think you're right, still wish Valve would make an announcement.

---

### Post by Ylon on 2010-05-16
> **fatality_uk said:**
> Already done ;)

[http://ubuntuforums.org/showpost.php?p=9295122&postcount=79](http://ubuntuforums.org/showpost.php?p=9295122&postcount=79)


That stuff is from sep. 2007 (and even before maybe):

[http://web.archive.org/web/20070921230928/http://www.valvesoftware.com/job-SenSoftEngineer.html](http://web.archive.org/web/20070921230928/http://www.valvesoftware.com/job-SenSoftEngineer.html)

---

### Post by ELD on 2010-05-16
> **Ylon said:**
> That stuff is from sep. 2007 (and even before maybe):

[http://web.archive.org/web/20070921230928/http://www.valvesoftware.com/job-SenSoftEngineer.html](http://web.archive.org/web/20070921230928/http://www.valvesoftware.com/job-SenSoftEngineer.html)

"but if memory serves hasn't that ad been there a few years now" - myself

Yeah i pointed that out before not with the link though. I knew it was there for ages. So it doesn't mean squat. But then all the other evidence coming out seems solid.

All we need is Valve to make an announcement.

---

### Post by RambJoe on 2010-05-16
[http://media.steampowered.com/apps/mac/MacSteam_AlfredJasonGabe.jpg](http://media.steampowered.com/apps/mac/MacSteam_AlfredJasonGabe.jpg)

Notice the penguin?

Also that is Alfred Reynolds.

[http://valvesoftware.com/company/people.html](http://valvesoftware.com/company/people.html)

>  					 						Alfred Reynolds											
 					Software Developer
 					 Alfred joined Valve as a software  engineer in 2002. Since his arrival, he has contributed to the  development of Counter-Strike, Half-Life   2, and Steam. _**He also does his best to maintain the Linux ports of our  games.**_ Most recently, he lead the Steam development efforts to bring  third party applications to the leading online distribution   platform. Prior to his arrival at Valve Alfred worked for an Australian  research organization and would be forced to kill anyone who discovered  the true nature of his work there. He was also to blame for   starting plugins on Half-Life servers, in particular creating Admin Mod.
 				


---

### Post by efikkan on 2010-05-16
That's the "Madagascar" penguin: [http://aliceteh.com/photos/Madagascar_Penguin.jpg](http://aliceteh.com/photos/Madagascar_Penguin.jpg)

---

### Post by ELD on 2010-05-16
> **efikkan said:**
> That's the "Madagascar" penguin: [http://aliceteh.com/photos/Madagascar_Penguin.jpg](http://aliceteh.com/photos/Madagascar_Penguin.jpg)

Indeed nothing to do with Linux just happens to be there.

---

### Post by RambJoe on 2010-05-16
Well there is another penguin to the right of it. I'm guessing it was the coolest penguin toy he could find.

---

### Post by efikkan on 2010-05-16
I don't know if that is even a penguin, but it's certainly not our beloved [Tux]("http://en.wikipedia.org/wiki/Tux"). If he was running Ubuntu with steam in the background, that would be a clue, but this penguin stuff does not mean anything. It's probably just a toy from his kid or something random.

---

### Post by rasmus91 on 2010-05-17
> Keep in mind that's "end of summer" Valve time - which could easily mean Halloween. But I suspect we'll be playing some Source games by the end of the year on Linux boxes.

Oh i don't really mind it being by halloween, as long as it's not much longer than that.

> All we need is Valve to make an announcement.  and please do so soon!

---

### Post by ELD on 2010-05-17
It kinda looks like one but it's nothing to do with us, as efikkan pointed out it is not Tux. It's just random desk objects, we all have them.

---

### Post by s3a on 2010-05-17
It's true!!!!! Here is the link: [http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1)

---

### Post by doorknob60 on 2010-05-17
Old. Was hoping this was actually CONFIRMED...still not.

---

### Post by pwnst*r on 2010-05-17
Psyche!

---

### Post by jpeddicord on 2010-05-17
Removed some off-topic posts from the thread; please keep this steered in the right direction. :)

And count me in as one who's excited for some sort of announcement from Valve on Steam & Source.

---

### Post by Frak on 2010-05-17
I've been able to view the source for the Source engine a few times, every so often. Here's what I have to say:

1. The source contains OpenGL code
2. The source contains Macintosh specific code
3. The source contains Linux client code
4. The Linux client code is horribly broken
5. From release-to-release, the Linux code is very minutely changed, with no real effort going into improvement at the builds I viewed

Thought I'd give a heads up.

---

### Post by formaldehyde_spoon on 2010-05-17
> **Frak said:**
> I've been able to view the source for the Source engine a few times, every so often. Here's what I have to say:

1. The source contains OpenGL code
2. The source contains Macintosh specific code
3. The source contains Linux client code
4. The Linux client code is horribly broken
5. From release-to-release, the Linux code is very minutely changed, with no real effort going into improvement at the builds I viewed

Thought I'd give a heads up.

Is there any source code for anything that you haven't seen?
Anyone could have guessed points 1 to 5 and have almost no chance whatsoever of being wrong, let alone ever being proven wrong.

---

### Post by Frak on 2010-05-18
> **formaldehyde_spoon said:**
> Is there any source code for anything that you haven't seen?
Anyone could have guessed points 1 to 5 and have almost no chance whatsoever of being wrong, let alone ever being proven wrong.
I have the source code for DOS 6.22 to Windows NT 6.1, all builds of Mac OS, and Yoshi's Island (actually, very short and simple).

What I'm saying is, while there is Linux code in the Source engine, it's terribly incomplete, and nowhere near production value.

---

### Post by s3a on 2010-05-18
But the link I posted says that "The released Linux client should be available by the end of summer." ([http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1))

---

### Post by formaldehyde_spoon on 2010-05-18
> **Frak said:**
> I have the source code for DOS 6.22 to Windows NT 6.1, all builds of Mac OS, and Yoshi's Island (actually, very short and simple).

What I'm saying is, while there is Linux code in the Source engine, it's terribly incomplete, and nowhere near production value.

I'm not sure that the current state of the Linux client is relevant to whether or not a Linux client will be released in the future.

Anyway, time will tell.

---

### Post by Frak on 2010-05-18
> **s3a said:**
> But the link I posted says that "The released Linux client should be available by the end of summer." ([http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1))
I take everything Phoronix says with a grain of salt. The source code tells a much different story.

---

### Post by Old Marcus on 2010-05-18
Since Valve *haven't* officially confirmed anything, isn't the title a bit misleading?

---

### Post by phrostbyte on 2010-05-18
> **Frak said:**
> I have the source code for DOS 6.22 to Windows NT 6.1, all builds of Mac OS, and Yoshi's Island (actually, very short and simple).

What I'm saying is, while there is Linux code in the Source engine, it's terribly incomplete, and nowhere near production value.

I think if you hax0r the Gibson you can get the source code for Windows 7 and Kentucky Fried Chicken's website as well.

---

### Post by ELD on 2010-05-18
> **Frak said:**
> I take everything Phoronix says with a grain of salt. The source code tells a much different story.

I take everything you say with a grain of salt too. We are just supposed to trust your word with no evidence? You say you have all these source codes, then you either worked for one of them at some time and took them home which would be illegal or you downloaded them, again illegal.

Good going. Stop trying to stir up trouble.

@s3a I keep saying this and i am repeating myself, Valve have not actually confirmed anything, Phoronix is just working the hype machine for the moment. Until Valve officially announce it, for all of us it doesn't exist.

---

### Post by Ylon on 2010-05-18
Please, fix the title of this thread :P

---

### Post by pwnst*r on 2010-05-18
> **Ylon said:**
> Please, fix the title of this thread :P

^this.

---

### Post by jpeddicord on 2010-05-18
Removed the Valve bit, how's that? :P

---

### Post by Merk42 on 2010-05-18
> **jpeddicord said:**
> Removed the Valve bit, how's that? :P

Add a ? to make it better...

---

### Post by efikkan on 2010-05-18
To access the complete source code of Windows releases you have to work in the development team, and many only got access to parts of the source code. Microsoft partners don't get access to the complete source code, and it's under a very strict license.

However the source code for several Dos versions and most of the code for Win 2k has been leaked.


The source engine got GNU/Linux support for the server for quite a while now, so what's missing is the client. The graphics engine from the Mac OS X port can be used with minimal modifications. I don't develop for the source engine myself, so I don't know wich libraries they use for audio or networking. But can one of you who are supposed to have this code tell me wich library is used to set up an OpenGL context and link with X11? It's either SDL, glut(I seriously doubt it) or something custom made.

---

### Post by Frak on 2010-05-18
> **ELD said:**
> I take everything you say with a grain of salt too. We are just supposed to trust your word with no evidence? You say you have all these source codes, then you either worked for one of them at some time and took them home which would be illegal or you downloaded them, again illegal.

Good going. Stop trying to stir up trouble.

@s3a I keep saying this and i am repeating myself, Valve have not actually confirmed anything, Phoronix is just working the hype machine for the moment. Until Valve officially announce it, for all of us it doesn't exist.
Sorry for trying to help.

---

### Post by fatality_uk on 2010-05-18
> **jpeddicord said:**
> removed the valve bit, how's that? :p

*chuckle*

---

### Post by ELD on 2010-05-21
Well no more news at all on this, anyone else think it's a dudd?

---

### Post by ad_267 on 2010-05-21
> **ELD said:**
> Well no more news at all on this, anyone else think it's a dudd?

I think it just jumped the bullet by a long way. Those sites that Phoronix took as "confirmation" were probably just basing their claim on what they'd seen on Phoronix.

---

### Post by fatality_uk on 2010-05-21
There will be an official announcement sometime between now and 2012.

---

### Post by ELD on 2010-05-21
> **ad_267 said:**
> I think it just jumped the bullet by a long way. Those sites that Phoronix took as "confirmation" were probably just basing their claim on what they'd seen on Phoronix.
 
That is exactly what i was thinking, i don't honestly think it is coming, i wish it was though but i am also thinking all the other sites took it from Phoronix and then Phoronix used them as confirmation.
 
I find it funny how the telegraph said Valve has confirmed it, but they haven't!

---

### Post by TheBuzzSaw on 2010-05-22
What else do you expect to happen? They're still working on it. It's not like they just force it to be finished right now.

---

### Post by ELD on 2010-05-22
> **TheBuzzSaw said:**
> What else do you expect to happen? They're still working on it. It's not like they just force it to be finished right now.

Have you read up on all the articles or bothered to read a few replies on this topic at all?

Phoronix claims Valve have CONFIRMED Steam for Linux, they haven't. They also quoted the Telegraph as a source for this. Telegraph simply said Valve has confirmed it, citing no sources...it doesn't take a genius to discover what has happened.

---

### Post by jpeddicord on 2010-05-22
> **ELD said:**
> Phoronix claims Valve have CONFIRMED Steam for Linux, they haven't. They also quoted the Telegraph as a source for this. Telegraph simply said Valve has confirmed it, citing no sources...it doesn't take a genius to discover what has happened.

While I agree with the suspicion, I do think there's good reason to believe that there will be something official soon, especially with the existence of the strangely-not-yet-pulled Linux binaries on their site.

---

### Post by zekopeko on 2010-05-22
> **jpeddicord said:**
> While I agree with the suspicion, I do think there's good reason to believe that there will be something official soon, especially with the existence of the strangely-not-yet-pulled Linux binaries on their site.

Linux binaries could simply be for internal testing. They don't necessarily point to a Linux release.

Phoronix also claimed that Steam was coming to Linux in 2008. How did that work out?

---

### Post by ELD on 2010-05-22
> **zekopeko said:**
> Linux binaries could simply be for internal testing. They don't necessarily point to a Linux release.

Phoronix also claimed that Steam was coming to Linux in 2008. How did that work out?

Exactly, another point they used as a fact is the job position while that in itself is a good idea since it mentions porting games to Linux, that advert has been there for years itself.

What i find funny is Phoronix keeps mentioning June as if he knows something we don't, but we shall see.

---

### Post by Merk42 on 2010-05-22
At this point I'm just disappointed there was no official announcement from Valve.

"Yes it's coming"
"No it's not"
"We can neither confirm nor deny it coming"

---

### Post by efikkan on 2010-05-22
> **zekopeko said:**
> Linux binaries could simply be for internal testing. They don't necessarily point to a Linux release.

Phoronix also claimed that Steam was coming to Linux in 2008. How did that work out? Valve has already hired programmers to work on porting games to Linux, and now they want a senior programmer with expertise in GNU/Linux platform. Valve is spending a lot of money on porting Steam and the Source engine to GNU/Linux, this is actually a project they intend to complete, not like UT3 wich never were a priority.

Valve is eventually going to release a GUI Steam client for GNU/Linux when it's ready, they don't spend this amount of cash on projects they don't intend to complete. But of course company's economy may collapse next week, the share holders may do something crazy or something else horrible may happen, but otherwise Valve will release it someday.

---

### Post by zekopeko on 2010-05-22
> **efikkan said:**
> Valve has already hired programmers to work on porting games to Linux, and now they want a senior programmer with expertise in GNU/Linux platform. Valve is spending a lot of money on porting Steam and the Source engine to GNU/Linux, this is actually a project they intend to complete, not like UT3 wich never were a priority.

Valve is eventually going to release a GUI Steam client for GNU/Linux when it's ready, they don't spend this amount of cash on projects they don't intend to complete. But of course company's economy may collapse next week, the share holders may do something crazy or something else horrible may happen, but otherwise Valve will release it someday.

Or they simply hired a Linux programmer for their server products. There are servers for Half-Life and other Source Games that can run on Linux.

---

### Post by efikkan on 2010-05-22
> **zekopeko said:**
> Or they simply hired a Linux programmer for their server products. There are servers for Half-Life and other Source Games that can run on Linux. The server version existed before they started to hire more.

---

### Post by jpeddicord on 2010-05-22
> **efikkan said:**
> The server version existed before they started to hire more.

Indeed. Why would they create a client Steam UI just for their server launchers? People have gotten the friends interface to load as well, so there's definitely something more going on...

Unfortunately they seem to have restricted the [linux checksums]("http://store.steampowered.com/public/client/steam_client_linux") so you can't easily get a copy to play around with anymore.

---

### Post by efikkan on 2010-05-23
They seem to appear and disappear from time to time, maybe they will show up again :)

---

### Post by ELD on 2010-05-23
@efikkan the senior job posting you are referring to has already been pointed out that it has been there for a good number of years to no effect.

@jpeddicord i've pointed this out to others too, WoW had a fully functional Linux client that got dropped, UT3 also worked on Linux with shots of it running and got dropped etc etc it's happened a good number of times.

I am just not wanting everyone to get worked up to be disappointed as we have so many times now.

---

### Post by jpeddicord on 2010-05-25
Here's a fun little tidbit:

[http://en.wikipedia.org/wiki/Postal_III](http://en.wikipedia.org/wiki/Postal_III)

Note the target platforms and the engine. :KS

---

### Post by ELD on 2010-05-26
> **jpeddicord said:**
> Here's a fun little tidbit:
 
[http://en.wikipedia.org/wiki/Postal_III](http://en.wikipedia.org/wiki/Postal_III)
 
Note the target platforms and the engine. :KS
 
This has been known for a long time now ;).
 
Valve still hasn't made any annoucement about source or steam though.

---

