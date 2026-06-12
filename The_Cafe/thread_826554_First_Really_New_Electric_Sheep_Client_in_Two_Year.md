---
title: "First Really New Electric Sheep Client in Two Years"
date: 2008-06-12
forum: The Cafe
---

### Post by spotspot on 2008-06-12
Dear Users,

For the past couple of years I have been primarily working on the High Fidelity end of [Electric Sheep]("http://electricsheep.org").  Development of a so-new-it's-incompatible version of the free screen-saver has gone on behind the scenes.  Finally version 2.7 is in public beta, and Ubuntu is the primary platform.

Get it [here]("http://community.electricsheep.org/node/237").  Update: we now have binary packages you can install from our PPA, see [this]("http://community.electricsheep.org/node/271").

Reports of any problems or bugs as well as successes are most welcome.   Thanks!  You can comment on either forum, or send [me]("http://scottdraves.com") email.

We have noticed that sometimes mplayer and electricsheep processes get left hanging and blocking it from working.  Killall -9 these processes somestimes fixes it.  Or restarting the X server...  we don't know what's going on yet, so if you are capable, please poke around and let me know what you think the problem is.  Thanks.

You can browse the [new flock]("http://v2d7b.sheepserver.net/cgi/status.cgi") here even without the client.  Note that this flock is at 1/10th quality since there are hardly any users yet.  I'll crank it up as people join.  The advantage of few users though is it starts in seconds :)

Main improvements are: a more expressive visual language, a dynamic filter in the renderer to smooth out the dust, and h264 of double the pixels per sheep (800*600*160/(640*480*128) = 1.95).

Thank you so much, -Sp0t

ps.  credits are all the [web page]("http://electricsheep.org/index.cgi?&menu=credit") but special shout-outs to keffo sandberg, erik reckase, and daniel summer for this release.

---

### Post by rabid9797 on 2008-06-12
sweet i cannot wait to try this out! its been a long time coming :popcorn:

---

### Post by mrgnash on 2008-06-12
Very very cool indeed, cheers.

---

### Post by spotspot on 2008-06-12
Thanks!

Btw the process of getting this solid would be greatly aided if someone could package FLAM3: [https://bugs.launchpad.net/ubuntu/+bug/198136](https://bugs.launchpad.net/ubuntu/+bug/198136)

-Spot

---

### Post by DigitalDuality on 2008-06-12
d

---

### Post by EReckase on 2008-06-12
First, I want to stress that while the linux client is in beta, it works *extremely* well right now.  I can't recommend the new version enough - the new variations in flam3 make this version almost a completely new experience.

I also want to point out that 64-bit users should have no trouble at all with the new beta - to make sure the process was streamlined, today I followed the instructions in Spot's post on my fresh 64-bit Hardy installation, and it looks spectacular.

Comments / criticisms are welcome.

--Erik

---

### Post by zachtib on 2008-06-12
I love electric sheep, and use it as my screensaver, but I'd rather if there was a way to try the new beta without installing from source...  I like as much of my software as possible to be installed through apt so that it can all me managed in one central location.

Have you considered launchpad's PPA service for distributing Ubuntu packages?

---

### Post by spotspot on 2008-06-12
> **zachtib said:**
> I love electric sheep, and use it as my screensaver, but I'd rather if there was a way to try the new beta without installing from source...  I like as much of my software as possible to be installed through apt so that it can all me managed in one central location.

Have you considered launchpad's PPA service for distributing Ubuntu packages?

Thank you and thanks for the tip, I didn't know about PPA, we will get on it ASAP.

---

### Post by bruce89 on 2008-06-12
> **spotspot said:**
> Finally version 2.7 is in public beta, and Ubuntu is the primary platform.

What's wrong with other Linux distros? I don't like the whole Ubuntu = Linux attitude.

---

### Post by spotspot on 2008-06-12
> **bruce89 said:**
> What's wrong with other Linux distros? I don't like the whole Ubuntu = Linux attitude.

I welcome your help porting it to your favorite distro.  Please email [me](http://scottdraves.com) to coordinate.  Thanks, -Spot

---

### Post by bruce89 on 2008-06-12
> **spotspot said:**
> I welcome your help porting it to your favorite distro.  Please email [me](http://scottdraves.com) to coordinate.  Thanks, -Spot

Surely there is no porting involved, programs tend to be rather portable across distros saying as they're essentially the same.

I am not criticising your hard work on this noble project.

I was really referring to Adobe Flash 10's release notes saying "Compatible with Ubuntu". That makes no sense.

---

### Post by zachtib on 2008-06-12
> **spotspot said:**
> Thank you and thanks for the tip, I didn't know about PPA, we will get on it ASAP.

awesome, I'm looking forward to it :)

---

### Post by Anduu on 2008-06-13
Man this is great news :KS
The install script worked great and I was up and running in no time :)
I have been using Electricsheep forever...it's the only screensaver for me!

Now what to do with the 13 gigs of old sheep I have accumulated over the years?I tried dropping a few into the ~/.electricsheep folder but it doesn't use them.If I converted my old sheep to the proper format would they work or would they just mess everything up?

Anyways thanks again spot.Your the best =D>

---

### Post by synd7 on 2008-06-13
Just installed and it looks wonderous, great work, can't wait to see what full quality will be like:popcorn:

Is voting going to be enabled for the linux version? or is that an issue with something outside electric sheep?

---

### Post by EReckase on 2008-06-13
> **Anduu said:**
> 
Now what to do with the 13 gigs of old sheep I have accumulated over the years?I tried dropping a few into the ~/.electricsheep folder but it doesn't use them.If I converted my old sheep to the proper format would they work or would they just mess everything up?


You could potentially convert them, but I think you'd be better off just enjoying the new feed (or concatentating them together yourself into movies, etc.)  It'd be an awful lot of work and there'd be no edges between the new and old sets, and since the frames are different sizes...

> **synd7 said:**
> Is voting going to be enabled for the linux version? or is that an issue with something outside electric sheep?

Voting is an issue because, while there was a patch for xscreensaver to allow keystrokes before, there isn't one for gnome-screensaver yet.  We'd love some assistance on that, if anyone has intimate knowledge of it.

--Erik

---

### Post by Polygon on 2008-06-13
does this version actually work? i mean, i tried the last one, and not only was it restricted to like 800x600 or something of my screen when i tried it, but the bittorrent part that was supposed to download new 'sheep' never did

i shall look forward to seeing if this actually functions properly on linux a bit later ;)

---

### Post by EReckase on 2008-06-13
> **Polygon said:**
> does this version actually work? i mean, i tried the last one, and not only was it restricted to like 800x600 or something of my screen when i tried it, but the bittorrent part that was supposed to download new 'sheep' never did

i shall look forward to seeing if this actually functions properly on linux a bit later ;)

It works - but your problem is that you expect it to provide frames larger than 800x600.  The frames are rendered one at a time and sent to a central server, which compiles the movies and sends them to the clients as a reward.  The old version of the screensaver was 640x480 with less effective compression; the new version is 800x600 and better compression - so it's better than it was before, although not at your native resolution.

---

### Post by spotspot on 2008-06-13
> **Anduu said:**
> Man this is great news :KS
The install script worked great and I was up and running in no time :)
I have been using Electricsheep forever...it's the only screensaver for me!

Now what to do with the 13 gigs of old sheep I have accumulated over the years?I tried dropping a few into the ~/.electricsheep folder but it doesn't use them.If I converted my old sheep to the proper format would they work or would they just mess everything up?

Anyways thanks again spot.Your the best =D>

Thanks :)

The new generation of sheep is not compatible.  It would be possible to convert them in theory, but they wouldn't look very good, and soon enough you'll forget all about them.... ;)

---

### Post by spotspot on 2008-06-13
> **Polygon said:**
> does this version actually work? i mean, i tried the last one, and not only was it restricted to like 800x600 or something of my screen when i tried it, but the bittorrent part that was supposed to download new 'sheep' never did

i shall look forward to seeing if this actually functions properly on linux a bit later ;)

sounds like zooming wasn't working.  can you get mplayer by itself to zoom full-screen?  the linux version doesn't have bittorrent at all, it just downloads with http, and it actually works really well now, since the server isn't overloaded (yet).

---

### Post by SteveNorman on 2008-06-13
I cant get the script to work,,do I need to change the permissions? 

```
steve@teampeanut-desktop:~$ ls makesheep.sh 
makesheep.sh
steve@teampeanut-desktop:~$ .makesheep.sh 
bash: .makesheep.sh: command not found
steve@teampeanut-desktop:~$ ls .makesheep.sh -l
ls: cannot access .makesheep.sh: No such file or directory
steve@teampeanut-desktop:~$ ls makesheep.sh -l
-rw-r--r-- 1 steve steve 761 2008-06-13 10:49 makesheep.sh
steve@teampeanut-desktop:~$ chmod 755 makesheep.sh 
steve@teampeanut-desktop:~$ ls makesheep.sh -l
-rwxr-xr-x 1 steve steve 761 2008-06-13 10:49 makesheep.sh
steve@teampeanut-desktop:~$ .makesheep.sh
bash: .makesheep.sh: command not found
```

sorry,,noob here

---

### Post by bruce89 on 2008-06-13
> **SteveNorman said:**
> I cant get the script to work,,do I need to change the permissions? 

```
steve@teampeanut-desktop:~$ ls makesheep.sh 
makesheep.sh
steve@teampeanut-desktop:~$ .makesheep.sh 
bash: .makesheep.sh: command not found
steve@teampeanut-desktop:~$ ls .makesheep.sh -l
ls: cannot access .makesheep.sh: No such file or directory
steve@teampeanut-desktop:~$ ls makesheep.sh -l
-rw-r--r-- 1 steve steve 761 2008-06-13 10:49 makesheep.sh
steve@teampeanut-desktop:~$ chmod 755 makesheep.sh 
steve@teampeanut-desktop:~$ ls makesheep.sh -l
-rwxr-xr-x 1 steve steve 761 2008-06-13 10:49 makesheep.sh
steve@teampeanut-desktop:~$ .makesheep.sh
bash: .makesheep.sh: command not found
```

sorry,,noob here

```
./makesheep.sh
```

makesheep.sh or .makesheep.sh aren't in your PATH.

---

### Post by spotspot on 2008-06-13
> **zachtib said:**
> awesome, I'm looking forward to it :)

here ya go:  [https://launchpad.net/~flam3/+archive](https://launchpad.net/~flam3/+archive)

That's the FLAM3 module, the actual screen-saver is harder, but shouldn't take too long.

---

### Post by spotspot on 2008-06-13
> **SteveNorman said:**
> I cant get the script to work,,do I need to change the permissions? 

```
steve@teampeanut-desktop:~$ ls makesheep.sh 
makesheep.sh
steve@teampeanut-desktop:~$ .makesheep.sh 
bash: .makesheep.sh: command not found

```

sorry,,noob here

You should put a space between the dot and the filename: ". makesheep.sh".

---

### Post by SteveNorman on 2008-06-13
got it to work,,

Its amazing,,thank you very much!

---

### Post by zachtib on 2008-06-13
> **spotspot said:**
> here ya go:  [https://launchpad.net/~flam3/+archive](https://launchpad.net/~flam3/+archive)

That's the FLAM3 module, the actual screen-saver is harder, but shouldn't take too long.

Cool.

On the subject of electric sheep, is there a way to download the source for certain sheep and rerender them at 1080p or 1920x1200?  I've got some high def displays it'd look cool on, and CPU cycles to spare.

---

### Post by synd7 on 2008-06-13
Is there a bug tracker for this?

Only one i've found is that it doesn't zoom to fullscreen when using x11.

---

### Post by spotspot on 2008-06-13
> **synd7 said:**
> Is there a bug tracker for this?

Only one i've found is that it doesn't zoom to fullscreen when using x11.

The x11 driver doesn't support zooming like the xv and gl ones do.

---

### Post by spotspot on 2008-06-13
> **zachtib said:**
> Cool.

On the subject of electric sheep, is there a way to download the source for certain sheep and rerender them at 1080p or 1920x1200?  I've got some high def displays it'd look cool on, and CPU cycles to spare.

Each sheep has its own web page where you can download its genetic code, eg: [http://v2d7b.sheepserver.net/cgi/node.cgi?id=3418&detail=genome](http://v2d7b.sheepserver.net/cgi/node.cgi?id=3418&detail=genome) (the file link goes to the raw xml).

You can then use the command line tools from the FLAM3 package to render it at whatever resolution and quality you want.  The documentation is in the wiki: [http://electricsheep.wikispaces.com/](http://electricsheep.wikispaces.com/)

---

### Post by Polygon on 2008-06-13
it works, but some things:

on your website, you need to tell users to 

```
chmod + x makesheep.sh
```

then

```
./makesheep.sh 
```

the thing you said on the website didnt work for me

also, I had to manually edit the prefs file (/home/NAME/.electricsheep/preferences.xml   open with a text editor) and put in the videodriver="" space, i had to put x11 or else electricsheep would not run at all.

And also, even though that made it work, when the screensaver ran, it would show up as 800x600 and there would be black bars around it. You said i needed to enable mplayer scaling, so i searched around and found that if you run this:
```

 sudo gedit /etc/mplayer/mplayer.conf  
```

then UNCOMMENT (delete the # )

```
#zoom=yes
```

then the electricsheep will scale to your resoultion and everything will be fine

and while the downloading seems to work (got 6 sheep in like 2 minutes) having bittorrent downloading would be very nice for linux.

---

### Post by Polygon on 2008-06-13
> **spotspot said:**
> The x11 driver doesn't support zooming like the xv and gl ones do.

and see my post above about uncommenting #zoom=yes ;)

---

### Post by Anduu on 2008-06-13
> **spotspot said:**
> Thanks :)

The new generation of sheep is not compatible.  It would be possible to convert them in theory, but they wouldn't look very good, and soon enough you'll forget all about them.... ;)

I suspected as much.From what I have seen so far I'm sure my old sheep will be a distant memory and my harddrive will be 13 gigs lighter ;)

Anyways I have however run into a small problem.Fullscreen and zooming work fine however my display refuses to go to sleep while electricsheep is running.Anyone else run into this?I have tried x11,xv and gl modes and no dice.

For the record I run an Nvidia FX 5500.

---

### Post by smartboyathome on 2008-06-13
Would anyone port this to windows? Or is there a way to? I would like to use it, but am stuck with windows for now. :(

---

### Post by Anduu on 2008-06-14
There has pretty much always been a Windows version of Electricsheep so I'm willing to bet it will get there eventually.

Oop see here [http://community.electricsheep.org/node/251#comment-1005](http://community.electricsheep.org/node/251#comment-1005)

---

### Post by spotspot on 2008-06-14
> **Anduu said:**
> There has pretty much always been a Windows version of Electricsheep so I'm willing to bet it will get there eventually.

Oop see here [http://community.electricsheep.org/node/251#comment-1005](http://community.electricsheep.org/node/251#comment-1005)

Yea we have a Windows Beta, please give it a whirl (comment on our forum not here).

The first Linux client came out in 1999, the first Mac client in 2001, and Windows in 2003, so not exactly always, but yea it's been a while :)

---

### Post by Polygon on 2008-06-14
> **Anduu said:**
> I suspected as much.From what I have seen so far I'm sure my old sheep will be a distant memory and my harddrive will be 13 gigs lighter ;)

Anyways I have however run into a small problem.Fullscreen and zooming work fine however my display refuses to go to sleep while electricsheep is running.Anyone else run into this?I have tried x11,xv and gl modes and no dice.

For the record I run an Nvidia FX 5500.

yeah i noticed that too. I took a nap and 4 hrs later my display was still on and running electric sheep although my display is supposed to turn off after 20 minutes. This only happens with ES cause with my old screensaver it turned off when it was supposed to.

---

### Post by spotspot on 2008-06-14
> **Polygon said:**
> yeah i noticed that too. I took a nap and 4 hrs later my display was still on and running electric sheep although my display is supposed to turn off after 20 minutes. This only happens with ES cause with my old screensaver it turned off when it was supposed to.

Is that a bug or a feature ;)

Just kidding, thanks for the report.  Let me see what I can do....

---

### Post by Polygon on 2008-06-14
Also, look at my attachment. It seems that electricsheep is spawning but not killing mplayer processes so i have like 7 in my process list, each taking up 6mb of memory......

---

### Post by spotspot on 2008-06-14
> **Polygon said:**
> and see my post above about uncommenting #zoom=yes ;)

yes but that's software zoom which eats a lot of cpu, xv and gl should be hardware.  i would only recommend the x11 driver if the others don't work.

---

### Post by spotspot on 2008-06-14
> **Polygon said:**
> yeah i noticed that too. I took a nap and 4 hrs later my display was still on and running electric sheep although my display is supposed to turn off after 20 minutes. This only happens with ES cause with my old screensaver it turned off when it was supposed to.

try putting

```
stop-xscreensaver = "no"
```

in your ~/.mplayer/config file.  I am going to test this more and if it works, make it automatic (with a different mechanism than editing your config file of course).

---

### Post by spotspot on 2008-06-14
> **Polygon said:**
> Also, look at my attachment. It seems that electricsheep is spawning but not killing mplayer processes so i have like 7 in my process list, each taking up 6mb of memory......

I have seen it happen rarely.  The sheep client calls setpgrp() to create a process group and uses kill(0,SIGTERM) to exit so all child processes should also be killed.

However if the sheep client just segfaulted, i think it would exit without cleaning up and killing its children.  Maybe I should install more signal handlers just in case.

I can run it from the command line and it goes reliably for days without crashing but running as a screensaver is a lot harder.

---

### Post by Polygon on 2008-06-14
Well I dont think it crashed, I was using it normally and then i just saw all those mplayer processes.

But i will try what you suggested about the xscreensaver thing

---

### Post by spotspot on 2008-06-14
> **Polygon said:**
> Well I dont think it crashed, I was using it normally and then i just saw all those mplayer processes.

But i will try what you suggested about the xscreensaver thing

Thanks for helping with the beta testing.  I can't explain it, I also don't think it's crashing.

I used "gnome-screesaver-command --activate" to bring it up and each time immediately killed it by hitting a key.  After about 10 times I saw an extra mplayer process appear.  Just killing this process did not remove it, I had to kill -9 it.  

Then I tried to make it fail again, and I must have started and killed 50 times when suddenly, when the screensaver came up, it was just black.  But still no extra processes, and starting it again continues to work fine.... And then it drops another process.

When electric sheep exits and kills its children, it uses SIGTERM.  If mplayer has become stuck enough that it requires a SIGKILL then I think this behavior would result.  Perhaps because the process which mplayer is reading from through the pipe is killed first?  Could it be an mplayer bug?

Maybe we could work around it like this: on exit, delivering SIGTERM to mplayer, sleep a bit, and then SIGKILL, then killing the process group with SIGTERM, including myself.  I would rather really know what was going on before I do this though...

I noticed that according to ps the leftover mplayer process is in state SN and the tty associated with it is just "?".

---

### Post by Anduu on 2008-06-14
> **spotspot said:**
> try putting

```
stop-xscreensaver = "no"
```

in your ~/.mplayer/config file.  I am going to test this more and if it works, make it automatic (with a different mechanism than editing your config file of course).

That was the first thing I thought of trying but it didn't help.

---

### Post by spotspot on 2008-06-15
> **Anduu said:**
> That was the first thing I thought of trying but it didn't help.

Yea didn't work for me either.  It did allow the screensaver and power-saving to come on while playing an movie from the command line with mplayer, but it did not allow the power-saving to come on when mplayer is running as the screensaver (getting a video feed from electric sheep).

---

### Post by spotspot on 2008-06-16
> **spotspot said:**
> Yea didn't work for me either.  It did allow the screensaver and power-saving to come on while playing an movie from the command line with mplayer, but it did not allow the power-saving to come on when mplayer is running as the screensaver (getting a video feed from electric sheep).

ok well i guess it will remain a mystery a little longer.  i'm going to package what we have, it seems to basically work, and maybe with more eyes we can iron these out.

---

### Post by Anduu on 2008-06-16
> **spotspot said:**
> ok well i guess it will remain a mystery a little longer.  i'm going to package what we have, it seems to basically work, and maybe with more eyes we can iron these out.

Oh well...I'm sure somewhere along the line the light bulb will come on ;)

I fiddled a bit.Tried changing the nice level but it wouldn't launch at all.I blame that on gnome-screensaver because launching from the command line with nice worked fine.

Everything else for me has been working great...no orphaned mplayer instances floating around.

As always thanks spot! :KS

---

### Post by spotspot on 2008-06-25
Ok now we have a PPA with FLAM3 and Electric Sheep working:
[https://launchpad.net/~flam3/+archive](https://launchpad.net/~flam3/+archive)
Thanks Erik!

---

### Post by EReckase on 2008-06-25
Note: These are still works in progress.  I've identified a few issues with the gconf keys that I've just fixed, as well as some other issues, so there will be numerous builds over the next few days.

That said, here's the apt line you need to add to your sources.list:

deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main


Please let me know if you have any issues with these new packages.

Thanks!  Special thanks to joaopinto at #getdeb for his assistance & advice in getting the electricsheep package built.

--Erik

---

### Post by zmjjmz on 2008-06-25
Just to be sure, the Electric Sheep in the etch repos isn't a new one, right?
Because it's only displaying on a portion of the screen on my T20.

---

### Post by smartboyathome on 2008-06-25
How would one get this to go fullscreen from the terminal? I can only make it run in a window using mplayer, which is not what I want. :(

---

### Post by zachtib on 2008-06-25
the new version in the PPA doesn't seem to work as a screensaver for me...

---

### Post by EReckase on 2008-06-25
> **zmjjmz said:**
> Just to be sure, the Electric Sheep in the etch repos isn't a new one, right?
Because it's only displaying on a portion of the screen on my T20.

Correct.  The etch repos has 2.6.8, I believe, and the one in the Launchpad repos is 2.7b5.

> **smartboyathome said:**
> How would one get this to go fullscreen from the terminal? I can only make it run in a window using mplayer, which is not what I want. :(

If you're running this from the terminal, hit 'f' while the mplayer window is selected, and it'll go fullscreen.  I do this all the time :D.

--Erik

---

### Post by EReckase on 2008-06-25
> **zachtib said:**
> the new version in the PPA doesn't seem to work as a screensaver for me...

Make sure you're using version ~ppa22 - I didn't want to install multiple copies of the electricsheep exe all over the system (like in /usr/lib/xscreensaver) and I didn't realize that that was the one that was being used.  There's a script called electricsheep-saver that's used now.  I'll have another look to make sure.

Whoops.  Looks like I forgot to change the .desktop file.  I'll put a new build out there shortly. ppa23 will be the good build.

---

### Post by Anduu on 2008-06-25
> **EReckase said:**
> 
Whoops.  Looks like I forgot to change the .desktop file.  I'll put a new build out there shortly. ppa23 will be the good build.

*---Points---> Ha! Ha! 

Just kidding :p ....I was just about to post that something was broken.

It's great we have a repo now.Thanks for all the hard work guys :KS

---

### Post by chronographer on 2008-06-25
I get this error when running electricsheep-preferences > agl@agl-desktop:~$ electricsheep-preferences 

(electricsheep-preferences:9337): libglade-WARNING **: could not find glade file '/usr/share/electricsheep/electricsheep-preferences.glade'

(electricsheep-preferences:9337): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed
nickEntry not found


how can I fix it?

---

### Post by EReckase on 2008-06-25
> **chronographer said:**
> I get this error when running electricsheep-preferences 

how can I fix it?

Looks like I missed another file for the installation.  I'll get that built tomorrow...check for updates in the morning.  It'll be ~ppa24.

---

### Post by smartboyathome on 2008-06-26
Nice, it runs great now! Good job! :D

---

### Post by spotspot on 2008-06-26
> **smartboyathome said:**
> How would one get this to go fullscreen from the terminal? I can only make it run in a window using mplayer, which is not what I want. :(

press "f" to go full screen after it starts.

---

### Post by EReckase on 2008-06-26
I just updated the package again - the gconf changes weren't being applied appropriately.  electricsheep_2.7b5-0ubuntu1~ppa25 should be a fully functional package.

--Erik

---

### Post by EReckase on 2008-06-26
Two more updates for those of you interested:

*First, the flam3 package was being build with -O2 instead of -O3 - this has been fixed, and these executables will render frames faster than the previous package.*

**<edit> Note: for whatever reason, the default flags are set to -O2 on the Launchpad build machines, and I don't know how to override them.  If anyone has advice on this aspect of things, please let me know!**

Second, the electricsheep package has been updated to provide CORRECT gconf setting functionality, and dropped the priority of the defaults file to 16.

These work better each time I upload them, so give them a try!  The screen should fade to dark at 30 minutes (system default) now (we were overriding it before, and we're no longer doing that).

--Erik

---

### Post by spotspot on 2008-06-26
> **EReckase said:**
> Two more updates for those of you interested: ...
These work better each time I upload them, so give them a try!
--Erik

thank you erik!

---

### Post by EReckase on 2008-06-27
Note: I did manage to get the flam3 package compiled with the proper optimization flags.  Please update your flam3 packages as soon as possible to take advantage of these optimizations!

Erik

---

### Post by spotspot on 2008-06-30
It should work much better with dual-head machines now.  The fix is in SVN and will go into the PPA later.

---

### Post by spotspot on 2008-07-19
Ok v2.7b8 has been released on the PPA.  It works better with dual heads, and has a big fix that makes a larger variety of sheep show up.

---

### Post by evaarties on 2008-07-22
Do you have a GPG-Key for that ppa repository?

---

### Post by fluteflute on 2008-07-22
[QUOTE=evaarties]Do you have a GPG-Key for that ppa repository?[/QUOTE]

PPAs cannot have GPG keys yet. :(

[Bug report]("https://bugs.edge.launchpad.net/soyuz/+bug/125103").

---

### Post by evaarties on 2008-07-23
To bad, well, than do not update that often :P so I don't have to click warnings away.

---

### Post by Capt_Zaphod on 2008-08-17
Great looking stuff!
Which download works with Ubuntu though?  It's not on the list.

Thank you

---

### Post by EReckase on 2008-08-17
Here's the [Launchpad]("https://launchpad.net/~flam3/+archive") page - add the listed repositories to synaptic and then you'll be ready to install!

--Erik

---

### Post by JMorg on 2008-08-26
So this may be a noob question, but when I try to load electricsheep within screensavers via system/preferences I get nothing but a screen that states please wait while the first sheep is downloaded. And yes I took the advice and waited, but it has been quite a while now and still no go lol, any updates for me please? :)

---

### Post by bonzodog on 2008-08-26
> **JMorg said:**
> So this may be a noob question, but when I try to load electricsheep within screensavers via system/preferences I get nothing but a screen that states please wait while the first sheep is downloaded. And yes I took the advice and waited, but it has been quite a while now and still no go lol, any updates for me please? :)

It can take a good hour or two to download the first one (in my experience), which means leaving the machine unattended so it can do it.

Next Question;

Does anyone know if there is an AUR pkgbuild of this for Arch Linux?

---

### Post by EReckase on 2008-08-26
> **JMorg said:**
> So this may be a noob question, but when I try to load electricsheep within screensavers via system/preferences I get nothing but a screen that states please wait while the first sheep is downloaded. And yes I took the advice and waited, but it has been quite a while now and still no go lol, any updates for me please? :)

Are you sure you're running the version from the launchpad repository?  The version in the standard ubuntu repositories is very old and takes much longer to download sheep.

---

### Post by spotspot on 2008-08-27
> **JMorg said:**
> So this may be a noob question, but when I try to load electricsheep within screensavers via system/preferences I get nothing but a screen that states please wait while the first sheep is downloaded. ... 
What version are you running?  You can tell by looking in synaptic or running the command "dpkg -l | grep electricsheep".  What do you get if you run "electricsheep --debug 1" and collect several minutes of output, and then look for errors or just email it to me.

---

### Post by mindhog on 2008-08-27
I'm seeing the same problem.  Version of electricsheep ("dpkg -l | grep electricsheep") looks to be: 2.6.8-9ubuntu1

One other note, I am behind a NATting router.  Not sure what the program is using to do downloads, if it's TCP there should be no problem.

---

### Post by smartboyathome on 2008-08-28
You are running the old version. Read the first post on how to instal the PPA, and then try updating it.

---

### Post by spotspot on 2008-08-28
The Electric Sheep client has just received a substantial upgrade: it now supports authentication.  Users that register on the new drupal will get better bandwidth.  See the [forum]("http://community.electricsheep.org/node/299").  Thanks, -Spot

---

### Post by JMorg on 2008-08-28
Ok so I am now going to install electricsheep through launchpad, however I would like to remove all the old files before I install the new. Is there a quick terminal command I can run to do this?

---

### Post by spotspot on 2008-08-28
> **JMorg said:**
> Ok so I am now going to install electricsheep through launchpad, however I would like to remove all the old files before I install the new. Is there a quick terminal command I can run to do this?
```
rm -r ~/.sheep
```

note that in the 2.7 series the files are stored in ~/.electricsheep instead.

when the windows version is uninstalled it deletes the sheep that it cached.  should the linux version do the same thing? ie execute this command when the package is removed (for all users)?  i think the package system does support this cleanly.

---

### Post by mindhog on 2008-08-30
> **smartboyathome said:**
> You are running the old version. Read the first post on how to instal the PPA, and then try updating it.

Yep, helps if I read the entire thread :)  Thanks for your patient response.

Looks great, BTW.  Only disappointment was that I can't figure out how to run it full-screen in the root window.  But I should probably read the rest of the thread for that, too...

---

### Post by Hells_Dark on 2008-09-10
Hi, whow to have a fullscreen electric sheep screensaver ? (no black parts)

---

### Post by spotspot on 2008-09-11
> **Hells_Dark said:**
> Hi, whow to have a fullscreen electric sheep screensaver ? (no black parts)

it should work out of the box, but if the X server and mplayer don't get along, then you might be able to fix it by changing graphics drivers (try x11 and gl after running "electricsheep-preferences").  Also try editing your mplayer config to turn on zooming (put zoom="yes" into ~/.mplayer/config) for the x11 driver.

---

### Post by spotspot on 2008-09-11
i think i fixed (or at least avoided) a major bug that was causing crashes on startup.  the new code is in svn, will publish with the PPA after confirmation.

---

### Post by spotspot on 2008-09-16
> **spotspot said:**
> i think i fixed (or at least avoided) a major bug that was causing crashes on startup.  the new code is in svn, will publish with the PPA after confirmation.

2.7b10 has been published on the PPA and is looking good...

---

### Post by DarkDead on 2008-11-02
Thank a lot EReckase!! It just worked out of the package. I run the script and everything worked. (I was really amazed as I have to make some workaround to get any more exotic application to work).

I'm using intrepid. I believe you should add a folder for the intrepid distribution to the repositories. You can just copy the hardy package and put it there, as it worked with no problems.

By the way, now I want to set the background to electric sheep. Is there any method that doesn't use compiz?

Can we expect support for votes in the future?

--Edit
As we can't contribute to the evolution of the flocks by vote we could create some new ones. "[_qosmic_]("http://code.google.com/p/qosmic/") is a graphical interface for creating, editing, and rendering flam3 fractal images." The only one native to linux. Is anyone able to make a .deb package for it? Perhaps it could be included on the PPA.

---

### Post by macogw on 2008-11-03
The following packages are BROKEN:
  electricsheep 
The following NEW packages will be automatically installed:
  flam3 
The following NEW packages will be installed:
  flam3 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3109kB of archives. After unpacking 4432kB will be used.
The following packages have unmet dependencies:
  electricsheep: Depends: mplayer which is a virtual package.

---

### Post by Phreaker on 2008-11-03
Electric sheep looks really nice

---

### Post by spotspot on 2008-11-05
> **DarkDead said:**
> Thank a lot EReckase!! It just worked out of the package. I run the script and everything worked. (I was really amazed as I have to make some workaround to get any more exotic application to work).

I'm using intrepid. I believe you should add a folder for the intrepid distribution to the repositories. You can just copy the hardy package and put it there, as it worked with no problems.

By the way, now I want to set the background to electric sheep. Is there any method that doesn't use compiz?

Can we expect support for votes in the future?

--Edit
As we can't contribute to the evolution of the flocks by vote we could create some new ones. "[_qosmic_]("http://code.google.com/p/qosmic/") is a graphical interface for creating, editing, and rendering flam3 fractal images." The only one native to linux. Is anyone able to make a .deb package for it? Perhaps it could be included on the PPA.

1) we will release packages for 8.10 soon.

2) i don't know how to set it as the background.

3) i hope to get voting working eventually, but it's not easy because it requires a patched version of gnome-screensaver.  plus i have to write a new output driver.  in the meantime you can vote through the [server interface]("http://v2d7c.sheepserver.net/cgi/status.cgi").

4) we have already offered to the qosmic author to host a deb in our PPA, but none of us knows how to make it.  it's different because it uses qmake.  if anyone can help with this, please send me email!

---

### Post by spotspot on 2008-11-05
> **macogw said:**
> The following packages are BROKEN:
  electricsheep 
The following NEW packages will be automatically installed:
  flam3 
The following NEW packages will be installed:
  flam3 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3109kB of archives. After unpacking 4432kB will be used.
The following packages have unmet dependencies:
  electricsheep: Depends: mplayer which is a virtual package.

How is it broken?  I don't understand.  I really want this to be totally bullet-proof, and any help you can give us getting there is much appreciated.  Thanks, -sp0t

---

### Post by macogw on 2008-11-05
> **spotspot said:**
> How is it broken?  I don't understand.  I really want this to be totally bullet-proof, and any help you can give us getting there is much appreciated.  Thanks, -sp0t
It depends on a virtual package rather than on the actual player, so it's freaking out.

---

### Post by spotspot on 2008-11-05
> **Phreaker said:**
> Electric sheep looks really nice

thanks :)

---

### Post by spotspot on 2008-11-06
> **macogw said:**
> It depends on a virtual package rather than on the actual player, so it's freaking out.

What's wrong with depending on virtual packages?  What is "it" that is freaking out?  We have been publishing it this way for 6 months without any complaints.

---

### Post by spotspot on 2008-11-14
an updated renderer (the FLAM3 package) is in the PPA for Intrepid and Hardy.  screen-saver for Intrepid is forthcoming.

---

### Post by Anduu on 2008-11-14
> **spotspot said:**
> an updated renderer (the FLAM3 package) is in the PPA for Intrepid and Hardy.  screen-saver for Intrepid is forthcoming.

Cool beans! :KS

Is anything changed from the Hardy version?...I've got some issues so far using the Hardy version under Intrepid but I'll wait until the new one before I start whining about it ;)

---

### Post by spotspot on 2008-11-15
> **spotspot said:**
> an updated renderer (the FLAM3 package) is in the PPA for Intrepid and Hardy.  screen-saver for Intrepid is forthcoming.

2.7b11 is published for hardy and intrepid.  the code is identical.  bugs, suggestions, and other reports from the field are most welcome.

---

