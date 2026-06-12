---
title: "Guild Wars, wine and nvidia"
date: 2006-04-19
forum: Wine
---

### Post by conedude13 on 2006-04-19
Hi all.  To start out this post, here are my system specs:
Intel P3 @ 1.8 GHz
NVIDIA geforce 4 ti 4600 @ 128 mb ddr
1 Gb ram
Ubuntu Breezy 5.10 (no xp)

I recently had trouble with xp, so I decided to go all in on Linux and everyone suggested Ubuntu.  So here I am!  My problem today is that I want to play Guild Wars.  That’s it, that’s the only thing that I want to do.  I will find a Linux version of everything else and will be fine with it, but I only really really want guild wars to work to make my whole ubuntu experience perfect.

That being said, here is what I have done so far.  When I first started with ubuntu, I downloaded everything for the NVIDIA drivers through the Synaptic Package Manager and followed [This Guide]("http://pcmech.com/show/os/917/") for beginners.  I installed Guild Wars (gw) with no problems since wine was installed from synaptic.  When I tried to play gw, however, I got an error saying that at least directx 8 should be installed for me to be able to play.  So I thought it was a wine problem.  So I then got xwine, dx9wine, wine cvs...and nothing worked.  I kept on getting the same error.

So then I did a clean re-install of the system, only this time, instead of getting everything about NVIDIA from synaptic, I followed [This Guide]("http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+driver+testers+needed") on installing the latest and greatest drivers for my NVIDIA card.  And this time, gw would start up!  I experienced a ton of lag for downloading the updates when you first log into the game.  To fix this, I added
Option          "NoLogo"
Option          "RenderAccel"           "true"
to the section "device" area of my /etc/X11/xorg.conf.  Then the downloads went blazing fast, and I made it to the log in screen of gw.  Which leads me to my next, and present, dilemma.  There was soooo much lag!  I would type in my user info for logging in and it would take about 7 seconds for it to catch up with me.  And I can forget about logging into the game.  It takes forever, and will eventually just crash.

So, that is where I am right now.  I feel that I am extremely close to finding a solution to my problem.  I have searched all over these forums, as well as other forums, for a practical solution that does not involve me getting cedega, which I refuse to pay for.  And I also would like to get to stay away from having to install a small xp partition on my hard drive to just play this one game.  Any help, any help at all, is extremely appreciated!

Thank you for your time.

---

### Post by handy on 2006-04-19
Hi, it's great that you can now get **GW** to run under **Wine**, it would not a few months ago!

Both **Wine** & **GW** are in perpetual developement, so I guess that explains it.

I did battle with **GW** via **Ubuntu** a few months back, & have been playing happily **without lag** ever since using **Cedega 4.4.3**.  

**What a fantastic game!** :KS 

[**See this link for the blow by blow details!**]("http://ubuntuforums.org/showthread.php?t=123715") :KS 

Even though you are using **Wine**, you should be able to use the same settings in the **GW Options Menu** & get the same results: **NO post zoning lag!**

If not try the [**Cedega time demo**]("http://www.transgaming.com/") to be sure that Cedega will be fine on your hardware (I'm sure it will).

*Could you please post your results on the end of my thread (this [I]**[blow by blow]("http://ubuntuforums.org/showthread.php?t=123715")*** one) I am trying to keep all relevant **GW** stuff happening there.  There's not been a lot of **GW** posts, I believe because there are no great problems running it on cedega with the appropriate simple settings in place.  **Now having [B]Wine** working with **GW**, as well as **Cedega!!** THAT would be a really BIG bonus. Which would bring a lot of Ubuntu (linux) users into the wonderful world of _Guild Wars_[/B][/I] :KS:KS:KS  

I have to say it again: **What a fantastic game!** :KS

**[EDIT:]**

Have a look at [**Automatix**]("http://ubuntuforums.org/forumdisplay.php?f=77"), it makes initial setup of a Ubuntu box soo much easier for both new & old hands alike!

---

### Post by conedude13 on 2006-04-19
My graphics isn't really up to par.  When the login screen comes up it is very choppy and you can't see any of the mountains and stuff.  Anyone out there proficient enough in wine and have similar system specs to mine that tinkered with their wine config files?

Hey Handy, are you in a guild?  If so, are their any guild mates of yours that have gw up and running on a Linux box using wine instead of cedega?

---

### Post by handy on 2006-04-19
[QUOTE=conedude13]My graphics isn't really up to par.  Anyone out there proficient enough in wine and have similar system specs to mine that tinkered with their wine config files?

Hey Handy, are you in a guild?  If so, are their any guild mates of yours that have gw up and running on a Linux box using wine instead of cedega?[/QUOTE]

I am the sole member of my own guild! :KS 

No disputes with members that way... :D 

Really, I just created one for the educational experience.

No, I haven't spoken to anyone else whilst playing GW who runs linux, mostly they have never heard of linux!  There are a lot of kids playing the game, which could explain some of the ignorance about linux.

You have tried playing with all the graphics options turned right down?

Screen res' down too?

I would have thought that it would work ok with your machine spec's...

Try the cedega demo, & see how it goes, if you find that performance is better, that will add to our knowledge base.

**[EDIT:]**

The cedega demo is really easy to install, & runs GW straight away.  Well it did for me anyway!

If GW ran ok under windoze, it will under linux.

---

### Post by zgerrz on 2006-04-20
I wish I could get this game to work with my ATI Radeon 9800 Pro...

---

### Post by handy on 2006-04-20
[QUOTE=zgerrz]I wish I could get this game to work with my ATI Radeon 9800 Pro...[/QUOTE]

That's a problem I can't help you with, I'm sorry.

Some users have dumped the ATI's out of frustration & bought nVidia graphic cards so as to be able to play their game(s) of choice on Ubuntu (linux).

The only consolation I can offer, is that at least you can get into a card that is a reasonable gameing card for linux for not too many dollars these days.  But, I also know that what is not many dollars in one part of the world is prohibitively expensive somewhere else.  Or if you are a student, or what have you...

---

### Post by conedude13 on 2006-04-20
I actually kind of gave up last night.  It has been over 2 weeks since I have last played gw!!  So i just slapped xp on a 20 gig partition of my hard drive and plan to install ubuntu on the rest tonight, again.

If you are the only member in your guild, would you consider joining mine?  If you play often that is.

I ran with all of the graphics all the way down to the left as far as they could go in the game options menu.  But the graphics in the backgroud of the login screen still look like garbage.  Maybe it's the graphics card driver?  I have nvidia-settings, but the only thing you can do in that is check a few boxes.  In xp, with the latest drivers for the card, I have a lot of tweaking options.  I never really tinkered with them though, just with the ingame stuff.

Oh, and if you are interested in the guild at all, here is the site: [The Dragons of the Lost Star Main Page]("http://www.dragonsoftheloststar.com/")

---

### Post by zgerrz on 2006-04-20
Yeah, I've begun searching eBay for an nvidia card. I'm tired of ATI's poor drivers.

Anyone know the nvidia equivalent (performance wise) to a Radeon 9800 Pro? I'm looking to get an nvidia card that performs a little better than what I have now. I've been looking at the 6600 GT (AGP only).

---

### Post by handy on 2006-04-21
[QUOTE=conedude13]I actually kind of gave up last night.  It has been over 2 weeks since I have last played gw!!  So i just slapped xp on a 20 gig partition of my hard drive and plan to install ubuntu on the rest tonight, again.

If you are the only member in your guild, would you consider joining mine?  If you play often that is.

I ran with all of the graphics all the way down to the left as far as they could go in the game options menu.  But the graphics in the backgroud of the login screen still look like garbage.  Maybe it's the graphics card driver?  I have nvidia-settings, but the only thing you can do in that is check a few boxes.  In xp, with the latest drivers for the card, I have a lot of tweaking options.  I never really tinkered with them though, just with the ingame stuff.

Oh, and if you are interested in the guild at all, here is the site: [The Dragons of the Lost Star Main Page]("http://www.dragonsoftheloststar.com/")[/QUOTE]

The thing that you loose that makes a noticable difference when you turn the graphics right down in GW options, is reflections.  That's why the login screen looks like crap.  As far as game play is concerned you will rarely notice that reflections are not there, (well I don't anyway).

As far as I am concerned, loosing the bloom effects & reflections is a tiny price to pay, to be able to otherwise have a perfect GW gameplay experience, **WITHOUT** windoze!!

I haven't even bothered with the nVidia settings, you can spend a lot of time & gain b' all, in my opinion anyway.

As far as your kind invitation to join your guild is concerned:  Thanks very much for the invite, but I will stay a loner for a while yet, I am slowly polishing my skills & still learning new ones.

I am not at all interested in the GvG part of the game, I like the role playing best of all.

So, to some up my thoughts:  If you didn't, & I can't tell from your post, try the game with all the settings turned down as per my findings in [**THAT**]("http://ubuntuforums.org/showthread.php?t=123715") other thread?  Try it, you may be pleasantly surprised.  The loss of reflections is really not a biggy, once you get past the login screen.

---

### Post by handy on 2006-04-21
[QUOTE=zgerrz]Yeah, I've begun searching eBay for an nvidia card. I'm tired of ATI's poor drivers.

Anyone know the nvidia equivalent (performance wise) to a Radeon 9800 Pro? I'm looking to get an nvidia card that performs a little better than what I have now. I've been looking at the 6600 GT (AGP only).[/QUOTE]

You can't go wrong with a 6600GT, try for as much on board ram as possible.

I bought my 6800GT on ebay, 2nd hand for half the new price, back when the 6800 ultra was the ducks guts!  So, if you are game to do it on ebay, you may be able to get more bang for your buck, so to speek! :grin:

Good Luck! :KS

---

### Post by Perfect Storm on 2006-04-21
I have a 6600GT with 256mb (agp x8 ). No problem whatsoever. It's rockin' and with two easy commandlines it's up and running.

---

### Post by conedude13 on 2006-04-21
[QUOTE=handy]So, to some up my thoughts:  If you didn't, & I can't tell from your post, try the game with all the settings turned down as per my findings in [**THAT**]("http://ubuntuforums.org/showthread.php?t=123715") other thread?  Try it, you may be pleasantly surprised.  The loss of reflections is really not a biggy, once you get past the login screen.[/QUOTE]

Ok, I'll give it another whirl.  One more question, since I am at work and wont be able to try this out until tonight, when you go to log in, is there a long lag in typing in your login info?  I'll try and get some screen shots of what my login page looks like for ya.  I know that I have tried turning the graphics all the way down.  It seems like it's not getting enough speed to wine from my internet connection.  Last time I tried to login with the graphics turned all the way down, it hung at the "connecting..." screen after hitting enter to log in and soon crashed.  But just to make sure, I will try again tonight.

I now have a fresh install of ubuntu on my box dool-booting with xp.  So I'll hit that one thread for starting up ubuntu, download the graphix driver, download wine and give it a go.

---

### Post by handy on 2006-04-21
From what you just said in your previous post, I'm thinking that your problem is Wine related.  I hope I'm wrong, but I doubt it.

If you can't get satisfaction with Wine, try the cedega demo.  

The older version 4.4.3 is THE version for best performance with GW. 

All the best!

---

### Post by conedude13 on 2006-04-21
Nah.  If i cant get it to work with wine I don't want to test it with cedega.  I got guild wars to get away from the monthly payments of 15 a month with city of heroes and city of villains.  I saw it's 15 for three months of cedega, but I don't really want to have to pay anything to play a free game.  So if I can't get it to work with wine, I will keep my xp partition for that game and just that game.  I'll still give it a shot though and bring on some screen shots.  BTW, how do you take screenies with ubuntu?  Does the print screen button work?  I would normally do that and then paste it into paint in xp.

---

### Post by Perfect Storm on 2006-04-21
It's only $15 and you can stop paying after the 3 months and cedega will still working. You can just not update it.

---

### Post by conedude13 on 2006-04-21
[QUOTE=Artificial Intelligence]It's only $15 and you can stop paying after the 3 months and cedega will still working. You can just not update it.[/QUOTE]


Well if you put it that way, I will most definitely be testing out the time trial tonight! Thanks for pointing that out to me.  So if I get the paid version, I just pay the 15 bucks and stop paying and then I cannot get future updates.  But how often is cedega updated?

---

### Post by Perfect Storm on 2006-04-21
At least once a month is my experience. So for the 3 months you should get ~3 updates for the 15 bucks. Just make sure to backup the cedega.deb file so it aren't gonna be lost.

---

### Post by siorai on 2006-04-21
If you go the Cedega route, I strongly suggest using 5.1.1 to run Guild Wars. I was trying 5.1.3 at first, but it kept crashing at exactly the same spot no matter what I did. I tried running it with 5.1.1 and it runs perfectly. No crashes and even runs noticeably smoother with the settings higher than what I could use with 5.1.3.

---

### Post by handy on 2006-04-21
The general consensus is, & I have verified it with testing, that the **Cedega version 4.4.3 is the fastest, smoothest version of Cedega for Guild Wars**.

You will have to sign up for a monthly subscription ($5- US / month) with Transgaming for Cedega, then cancel it at the end of the 3rd month.

You will be able to download all the previous versions of Cedega very easily via the Cedega GUI front end.  Which also allows you to very easily manage which version you want to associate with what game.  So, you can if needs be run different games with different versions of Cedega, all from the one simple interface.

So, if you subscribe, make sure that you download **ALL** the different versions, & backup the .deb files on a CD/DVD (just to be sure).  In case you get a game in the future that runs better on an older version.  Which is highly likely!

I only use Cedega at this stage to play **GW**.  Because **GW** is all the game that I need these days! :KS

---

### Post by flaak_monkey on 2006-04-21
Guild wars is by far my favorite MMO. So this is good news o hear you can play it on Linux. :cool:

---

### Post by conedude13 on 2006-04-21
Hey Handy,
What guide did you use, if any, to install the drivers for your nvidia card?

---

### Post by handy on 2006-04-21
[QUOTE=conedude13]Hey Handy,
What guide did you use, if any, to install the drivers for your nvidia card?[/QUOTE]

I used [Automatix]("http://ubuntuforums.org/showthread.php?t=138405"), which offers over 30 choices of things which it will do the entire installation for!!!

I have used it multiple times on different machines, on both 64 & 32 bit Ubuntu Breezy 5.10.

I can't recommend it highly enough.  There is plenty of time to delve into the depths of the operating system later at your leisure, in my opinion!

---

### Post by conedude13 on 2006-04-21
I TOTALLY GOT IT TO WORK!! It was a bit laggy, but still playable.  And will be getting the paid version tomorrow or sunday to get the 4.4 version.  Guild Wars does work on ubuntu breezy badger!  With my pc specs, posted in the first message of this thread, I got it installed and then started tinkering with the settings.  

After the install, I right-clicked on the gw icon and went into "edit profile".  I kept it win98 (and will be testing it on xp version) in the general tab.  Later, I had some trouble with the keyboard.  It wasn't typing.  It was beeping whenever I hit a key, just not typing.  So I unchecked the "free type and xrender" option in the general tab.  For audio, I moved it to alsa for my turtle beach santa cruz card.  The graphics tab is where it all comes together.  I put vid ram to 128, what my vid card has, and agp vertex data to 64, half of 128.  Pixel shaders defaulted to 1.3, and then unchecked vertex shaders, nv_var extension and arb_vbo extension.  It ran, it was playable, but it could definiatly be better.  So later this weekend I'll be testing out the pay version and see what build 4.4 is made of.

I'll post my results here and then copy the overall results in that one big gw/cedega thread of yours, handy.  Thanks all for your help and suggestions and replies!

---

### Post by handy on 2006-04-22
Hey, great work, it sounds like you are getting there:  There?  Yea!  Great work, 4.4.3 will be a boon to you.  You will soon be totally  imersed in the game...  Have a look for "sub liminal" on the web!

---

### Post by conedude13 on 2006-04-24
Thanks for all the help handy.  4.4.3 works a lot better!  But there are a few differences that may or may not be able to be fixed.  The entire time I play the game, the mouse arrow, as well as the map magnifying glass, looses it's "shine".  It's a bit hard to explain, it's like someone used the smudge tool on them.  I swapped back and forth between xp and 98 in the cedega settings and got the same mouse.  So I was just wondering what you settings are in each tab for gw when you right-click on the game and edit the profile.

One more thing is that all the buttons on my mouse do not work in game.  I have a Microsoft iniellimouse explorer 3.0, so I may have just answered my own question.  But just to make sure, I thought I would ask just to make sure.  It is a 5 button mouse, with 2 of them on the side where you thumb sits.  I use these 2 buttons to target dropped items with my name on them.  But when ever I hit it now, in cedega, the mouse just jumps a bit and nothing happens.  So I was just wondering if you, or someone else out there, uses a 5 button mouse on ubuntu breezy on cedega on guild wars.  I did not download any drivers for the mouse when i installed ubuntu.  I did have a Microsoft Ethernet pci card that never worked on ubuntu (i ended up having to go out and buy a new one and it work perfectly).

Other than that, the game plays great.  I am also getting a new vid card this week and hope that it will look even better when i get it.  While on the subject, should I go with ati or stick with nvidia?  I was going to get an nvidia one.  Anywho, thanks for the help man!  Look me up in-game if you want a drok's run or something! (Ukko Boreas or Flaming Hemmy)

---

### Post by handy on 2006-04-24
Sounds like it's all going well for you really.  You have to expect the odd minor inconsistancy running a game on a different OS than it was intended.

If you go back & look [**here**]("http://ubuntuforums.org/showthread.php?t=123715&page=5"), you will find my entire Cedega config' file.  If you back yours up, for future reference, (always a good idea anyway) & replace yours with mine, the only thing you will need to change is re: vid' memory, my card has 256Mb, so change settings appropriately.

Whilst we are on video cards, don't go near the ATI ones, their linux drivers are vastly inferior.  A few people with a few cards, will refute that, but the vast majority of ATI card owners, wish that they had bought nVidia!

Once again I'll plug,[** Automatix**]("http://ubuntuforums.org/showthread.php?t=138405"), for those of us who like safe sure shortcuts!  It will install the latest nVidia drivers, amongst the other installation options that you may choose.

I use the same mouse as you, have had it for years.  I have never used the 2 side buttons, so I have no problem with them...  I found when I first started using the mouse, & I tried using the buttons, that I was too often accidently using them.  So, I turned them off!

My mouse pointer looks fine, I usually have to select the game play area, post zoning, to make it appear.  The only other problem that I have with the mouse, & I'm not sure that it is the mouses problem, is that I can loose it in frantic fighting situations!?  It could just be a combination of old eyes & very high screen resolution making the mouse pointer even smaller!  If you use the rmb to look, which i do all the time, then the pointer dissapears then too.  I think that, that, is supposed to happen though!

I think that you may very well find that when you replace your display card that your mouse problem goes away!

I'll write down your names, & whisp you from time to time, to see if I can catch you online.  The character that I'm using these days is called ***Sub Liminal***.

Cheers! :KS

---

### Post by zgerrz on 2006-04-27
So I just got my nvidia 6800GT, installed the drivers, but now Guild Wars won't run at all.

What are the recommended Cedega settings to run Guild Wars pixel shaders, etc)?

I also tried running C + C: Generals, but it is very slow. Is there any sort of nvidia setup tweak I am missing here? I get around 9000 on glxgears.

---

### Post by handy on 2006-04-27
As you have probably noticed, I run the same gfx card.  It is more than adequate for anything you can run on linux, as I expect you allready know!

Have you installed the nVidia, closed source drivers?  

[**Automatix**]("http://ubuntuforums.org/showthread.php?t=138405") is a very easy way to do it!

---

### Post by handy on 2006-04-27
Ok, my settings:

Video Ram:  256Yes
AGP Vertex Data:  128
(yes) Pixel Shader: 1.3
(yes) Vertex Shaders
(yes) NV Var Extension
(yes) ARB_VBO Extension
Fixed Program: YES
Fragment Offset:  Auto
Non Power:  YES
(yes) Clip Space Fix
(no) Anisotropic Filtering
(yes) Frame Buffer

Any other settings on the Graphics Tab, just leave blank.


**[EDIT]**
I get about 13000 in glxgears.  It is not a true benchmark, but it does give us a rough idea of how our openGL is going.

I don't tweak the **Menu: Applications / System Tools / nVidia Settings** at all.  The cards performance is awesome, & really doesn't need me to waste time to perhaps gain a small improvement in performance.

---

### Post by zgerrz on 2006-04-27
I'm using the latest nvidia drivers (1.0-8756) compiled by myself for my custom kernel.

---

### Post by zgerrz on 2006-04-27
I also tried a native game (Neverwinter Nights), that crashed upon loading up a saved game.

I'm thinking theres a problem with how 3D acceleration is working, even though the drivers are passing all of Cedega's tests.

Wow, now I see that it passes all the tests EXCEPT for OpenGL rendering.

---

### Post by handy on 2006-04-27
Have you tried re-initialising xorg?

I forget the command, it won't take long to find it here, if you don't know it allready?

I think your problem will be quickly fixed, after the solution is found! :KS

---

### Post by zgerrz on 2006-04-27
I looked over my xorg config file and I have some remnants from my ATI card, so I ran sudo dpkg-reconfigure xserver-xorg to fix it up.

I'll reboot tomorrow and post results then.

In any case, happy to be rid of ATI!

---

### Post by siorai on 2006-04-28
[QUOTE=handy]Hey, great work, it sounds like you are getting there:  There?  Yea!  Great work, 4.4.3 will be a boon to you.  You will soon be totally  imersed in the game...  Have a look for "sub liminal" on the web![/QUOTE]

Is there any way to have both 4.4.3 and 5.1 installed at the same time? I'm mainly playing Guild Wars now, but I do like to play Halflife2 from time to time so I doubt 4.4.3 will cut it for HL2.

---

### Post by handy on 2006-04-28
Read [**my GW thread**]("http://ubuntuforums.org/showthread.php?t=123715"), you will find many questions allready answered there, & this is one of them.

Yes, Cedega handles all of it's previous versions very nicely, as nice as could be actually :)

---

### Post by siorai on 2006-04-29
Well, Guild Wars is borked now... I installed 4.4.3 and tried to check it out. Guild Wars is now showing as a 800x600 section of my monitor (monitor is 1680x1050) and the mouse is completely off from where it is actually pointing. I tried putting the exact same settings that I was using in my 5.1.1 profile, but it's still hooped. The best part is that if I go to use the 5.1.1 profile now, it's borked as well... ](*,) Here's the settings I've currently got set in the 4.4.3 profile:

[IMG]http://siorai.com/stuff/cedega/general.jpg[/IMG]

[IMG]http://siorai.com/stuff/cedega/audio.jpg[/IMG]

[IMG]http://siorai.com/stuff/cedega/graphics.jpg[/IMG]

Any pointers on what needs to be changed would be greatly appreciated.


Edit: Well, I reinstalled Guild Wars and it was working fine. Well, almost.. I went through all that just to realize that 4.4.3 does not support widescreen monitors. So I'm back to using 5.1.1.. But at least it works fine.

---

### Post by handy on 2006-05-02
[QUOTE=siorai]Well, Guild Wars is borked now... I installed 4.4.3 and tried to check it out. Guild Wars is now showing as a 800x600 section of my monitor (monitor is 1680x1050) and the mouse is completely off from where it is actually pointing. I tried putting the exact same settings that I was using in my 5.1.1 profile, but it's still hooped. The best part is that if I go to use the 5.1.1 profile now, it's borked as well... ](*,) Here's the settings I've currently got set in the 4.4.3 profile:

[IMG]http://siorai.com/stuff/cedega/general.jpg[/IMG]

[IMG]http://siorai.com/stuff/cedega/audio.jpg[/IMG]

[IMG]http://siorai.com/stuff/cedega/graphics.jpg[/IMG]

Any pointers on what needs to be changed would be greatly appreciated.


Edit: Well, I reinstalled Guild Wars and it was working fine. Well, almost.. I went through all that just to realize that 4.4.3 does not support widescreen monitors. So I'm back to using 5.1.1.. But at least it works fine.[/QUOTE]


I hope someone helps you there, it is beyond my  knowledge.  This reply is basicly to give you a bump, & put it in peoples faces, so that hopefully you will get a solution.

If you have worked one out, let us know for both reasons:

1: You can tell us what you have learned

2: Some of us are concerned about your problem, even though you hear nothing on the forum ... :confused:

---

### Post by conedude13 on 2006-05-08
I got factions, the expansion to guild wars, and my weird looking cursors are now gone.  They look like they normally would look like if you used the game in xp.

---

### Post by handy on 2006-05-08
[QUOTE=conedude13]I got factions, the expansion to guild wars, and my weird looking cursors are now gone.  They look like they normally would look like if you used the game in xp.[/QUOTE]

Good to hear, kind off! :confused:

---

### Post by kspn on 2007-08-09
Hi,

I am running Guild Wars quite happily on WINE at the moment however after reading this I am wondering what sort of performance increase I would see using cedega.

I have a dual core AMD 4000+ with integrated graphics (I am planning on buying a new Card when I get paid next) 

At the moment my average Frame rate is around 16 which is quite playable.
My only issue is that I have to go to my inventory to get a mouse cursor (change the mouse shape)

I have 2 questions.
1) Will I see an improvement in the game between Cedega and WINE?
2) Can I run both at the same time on my system and switch between them as I choose depending on my needs, eg game running better under one and not the other.

Thanks All :D

---

### Post by buttons on 2007-08-09
AUGH! Evil dredged thread!

But since you asked:
1) No.  Not even close.
2) Yes, absolutely.  Cedega is specifically built to run totally independently of wine.  They will not butt-heads.

Which is good, because then when you go and remove cedega in a fit of holy fury, you won't break anything.  Except the keyboard.

---

### Post by kspn on 2007-08-09
I would rather dredge up an old thread than start a new duplicate :D

In that case I think I will install Cedega, Mainly so that if a game doesn't work in WINE I can try it in Cedega as an alternative.

---

### Post by adam_kimber on 2007-08-12
> **kspn said:**
> I would rather dredge up an old thread than start a new duplicate :D

In that case I think I will install Cedega, Mainly so that if a game doesn't work in WINE I can try it in Cedega as an alternative.

I have discovered the complete opposite. Cedega gives me a black screen with a pointer the size of everest when running Guild Wars but in Wine it runs smoothly without any problems. :D

---

### Post by kspn on 2007-08-12
I am running Guild Wars quite Happily in WINE Although I think I need a new Graphics Card, 5fps is really annoying).

However some of my games are throwing fits when I try running them and I don't know if it is WINE or Setup related.

For example 'Masters of Orion 3' Throws an error when changing the screen res to 16bit (non configurable :()

---

