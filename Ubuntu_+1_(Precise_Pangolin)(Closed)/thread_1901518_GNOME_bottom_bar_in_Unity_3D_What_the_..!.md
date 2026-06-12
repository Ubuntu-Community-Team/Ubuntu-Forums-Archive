---
title: "GNOME bottom bar in Unity 3D? What the ..!"
date: 2011-12-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-28
Just started working on an install and noticed that I have the GNOME bottom bar on my Unity 3D desktop.


I'll update and see what happens.

---

### Post by effenberg0x0 on 2011-12-28
LOL

Unwillingly installing the old menubar is step 1.
Step 2 is threatening everyone to move to Mint.

:)

---

### Post by ventrical on 2011-12-28
hehe...

  I have no idea how it got there. However it seems to be hooked with compiz because now the wallpaper <cycle> function all of a sudden works.

---

### Post by effenberg0x0 on 2011-12-28
> **ventrical said:**
> hehe...

  I have no idea how it got there. However it seems to be hooked with compiz because now the wallpaper <cycle> function all of a sudden works.

Me too! Maybe they gave up the Unity madness and are coming back to gnome-panel?
Look at the screenshot!
[ATTACH]209854[/ATTACH]
I'll have to report a bug: gnome-panel covers the trash can icon...

Regards,
Effenberg

[SIZE=1][COLOR=Gray]PS: I'm just kidding lol...[/COLOR][/SIZE]

---

### Post by ventrical on 2011-12-28
Below are three screenshots.

 The first one Unity panel covers the bottom bar. but where you choose preferences and choose , say , 6 desktops it will then cover the Unity Launcher.

---

### Post by effenberg0x0 on 2011-12-28
> **ventrical said:**
> Below are three screenshots.

 The first one Unity panel covers the bottom bar. but where you choose preferences and choose , say , 6 desktops it will then cover the Unity Launcher.

The top panel is a mess too... They should fix it :) Let's post a bug report on Unity saying that it is not compatible with gnome-panel.

---

### Post by ventrical on 2011-12-29
Well.. I have to check somthing out because I did an experiment a few days back before Christmas.  What I'm saying is that  I am not sure how the bar got there in the first place unless I put it there by installing GNOME regular or somthing. I think I installed GNOME regular on a machine but I am not sure which one.

 So either it is a phenomenon-hybrid-bug or I did somthing , installed somthing, that did this.

  I'll have to check.

---

### Post by ventrical on 2011-12-29
Nope! It's a phenomenon-bug of some sort because I did no do that experiment on this PC .. so we should file that bug straightaway :)

---

### Post by ventrical on 2011-12-29
Here is screenshot.

---

### Post by ventrical on 2011-12-29
> **effenberg0x0 said:**
> The top panel is a mess too... They should fix it :) Let's post a bug report on Unity saying that it is not compatible with gnome-panel.

Done.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/909742](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/909742)

although I have initially chosen xorg to be deferred to Unity.

---

### Post by Bowmore on 2011-12-29
Are you sure that you're not running the GNOME Classic session, because that session just looks like this and has done so for a while now.

GNOME Classic sets up its panels and on top of that the Unity panel and the Launcher are drawn. I guess that you have the GNOME Classic top panel under the Unity panel. Just check that by changing the opacity of the Unity panel and you'll most probably see the GNOME panel.

Here Unity and GNOME sessions work just fine but not the GNOME Classic one.

---

### Post by ventrical on 2011-12-29
> **Bowmore said:**
> Are you sure that you're not running the GNOME Classic session, because that session just looks like this and has done so for a while now.

GNOME Classic sets up its panels and on top of that the Unity panel and the Launcher are drawn. I guess that you have the GNOME Classic top panel under the Unity panel. Just check that by changing the opacity of the Unity panel and you'll most probably see the GNOME panel.

Here Unity and GNOME sessions work just fine but not the GNOME Classic one.


Wow.... boy oh boy oh boy. I took 48 off hours for Christmas holidays and since I have been back I have been having one brain fart after another !!

Thanks for pointing that out to me Bowmore.

  I am going to have to undo that bug report.

My apologies again to all.

---

### Post by BC59 on 2011-12-29
Well your experience is interesting....we could get something useful from this.

---

### Post by ventrical on 2011-12-29
> **BC59 said:**
> Well your experience is interesting....we could get something useful from this.

Thanks for your kind words.  I'll post an edit in Testimonials.

Thanks.

Regards, ventrical

[http://ubuntuforums.org/showthread.php?p=11573044#post11573044](http://ubuntuforums.org/showthread.php?p=11573044#post11573044)

---

### Post by Bowmore on 2011-12-29
I've made some research now and noticed that this unity/gnome-panel mix doesn't show up for other users which implies that the issue has to do with user configs. I've further narrowed it down to that it has to do with some setting in gconf.

If you want to try, rename your ~/.gconf and relogin to gnome classic. That works for me. So next step now is to find out what gconf setting it is.

---

### Post by ventrical on 2011-12-29
> **Bowmore said:**
> I've made some research now and noticed that this unity/gnome-panel mix doesn't show up for other users which implies that the issue has to do with user configs. I've further narrowed it down to that it has to do with some setting in gconf.

If you want to try, rename your ~/.gconf and relogin to gnome classic. That works for me. So next step now is to find out what gconf setting it is.


Well.. how I ever got into GNOME classic with this install is beyond me at this point (and I am not trying to excuse my error here) but I am quite sure that I made a change in gconf. I think it had to do with Nautalis./show-desktop  because I was experimenting with Compiz/Wallpaper. A tool that will allow different desktop backgrounds for each desktop. It works great in Lucid.

I'll have to check into this further.

thanks again.

---

### Post by ventrical on 2011-12-29
> **Bowmore said:**
> I've made some research now and noticed that this unity/gnome-panel mix doesn't show up for other users which implies that the issue has to do with user configs. I've further narrowed it down to that it has to do with some setting in gconf.

If you want to try, rename your ~/.gconf and relogin to gnome classic. That works for me. So next step now is to find out what gconf setting it is.

qestion:

How do I run gconf from terminal.again?

thanks

Ok.. I recall now . I used gconf-editor then went to apps>nautalis>preferences and enabled start with sidebar.

  I disabled that, log off and then log back on with Gnome Classic and I still have the same thing.

---

### Post by keithpeter on 2011-12-29
> **ventrical said:**
> qestion:

How do I run gconf from terminal.again?

thanks

would that be gconf-editor ?

Has to be installed, not part of default

---

### Post by ventrical on 2011-12-29
> **keithpeter said:**
> would that be gconf-editor ?

Has to be installed, not part of default


Yep.. got it!!  I just realized that I have GNOME CLASSIC working with compiz settings mananger.

WOW!

---

### Post by ventrical on 2011-12-29
> **Bowmore said:**
> I've made some research now and noticed that this unity/gnome-panel mix doesn't show up for other users which implies that the issue has to do with user configs. I've further narrowed it down to that it has to do with some setting in gconf.

If you want to try, rename your ~/.gconf and relogin to gnome classic. That works for me. So next step now is to find out what gconf setting it is.


 I am not 100% sure on this but I was doing some trouble shooting a while back with @effenberg. We were testing  Window Rules in the Compiz Configuration&Settings Manager. Anyways , as I said , I did some configs in gconf-editior from terminal.

This weird beahviour started yesterday and it appears that we have a sort of belated Christmas Gift :) that being  CCSM working with Gnome Classic.

I am going to check some of my other machines.

---

### Post by Bowmore on 2011-12-29
Yep found that out too, so back to square one :(

Not sure but I guess classic should run metacity. Anyway the crazyness of intergrate a DE (unity) in a WM (compiz) has spoken. I do understand that a plugin is easier as there probably is no compiz api to separate them yet.

So next step is to find out why compiz is activated.

---

### Post by ventrical on 2011-12-29
Thats an affirmative! CCSM working on multiple PCs with Gnome Classic.

---

### Post by ventrical on 2011-12-29
> **Bowmore said:**
> Yep found that out too, so back to square one :(

Not sure but I guess classic should run metacity. Anyway the crazyness of intergrate a DE (unity) in a WM (compiz) has spoken. I do understand that a plugin is easier as there probably is no compiz api to separate them yet.

So next step is to find out why compiz is activated.

  I think it may be that Canonical and Gnome are trying to breath some new life into the legacy Gnome DE. It works great with Unity/ Cairo Dock, why not Unity/ Gnome Classic.

Smart move all around.

---

### Post by Bowmore on 2011-12-29
Well, it's not intentional and not a compromise but open doors :)

Gnome2 and Unity was separated by using compiz and compiz-1 so why not implement that again? May be too much testing and bug triaging worth it facing an LTS. The interesting thing though as you bring up is that it seems to work and why shouldn't it.

---

### Post by ventrical on 2011-12-29
> **Bowmore said:**
> Well, it's not intentional and not a compromise but open doors :)

Gnome2 and Unity was separated by using compiz and compiz-1 so why not implement that again? May be too much testing and bug triaging worth it facing an LTS. The interesting thing though as you bring up is that it seems to work and why shouldn't it.


  I just set it up in a newuser account as logged on to GnomeClassic and all the horizontal lines(while dragging windows) that were on the Windows title bars and tabs are gone!! They did it !! They finally patched it ! (err except for wobbly windows)  :)

  This is good news for more legacy Gnome users. As I wrote back a while (as did others) , our captain and commander, Mark Shuttleworth, would be wise to include Legacy Gnome if he were to reach that 200 million user mark ! :)


  I think it's just awesome.  I thought I was hallucinating!!  or that my memory was going on me. .. but .. nope ...:)


  Thanks to you guys, if you didn't followup I would have never known about it .

---

### Post by ventrical on 2011-12-29
> **effenberg0x0 said:**
> Me too! Maybe they gave up the Unity madness and are coming back to gnome-panel?
Look at the screenshot!
[ATTACH]209854[/ATTACH]
I'll have to report a bug: gnome-panel covers the trash can icon...

Regards,
Effenberg

[SIZE=1][COLOR=Gray]PS: I'm just kidding lol...[/COLOR][/SIZE]


They even fixed that overlay problem now.

---

### Post by ventrical on 2011-12-29
Another major development is that  the CCSM settings in user <same> Gnome Classic will not affect the settings in user <same> Unity 3D!!!  So if Compiz settings get borked in Gnome they will not affect Unity 3D (theoretically) and vis a versa.

Just beautiful..

---

### Post by ventrical on 2011-12-29
Also Unity Plugin can be disabled and Gnome Classic then works like a souped -up Hemi, RamCharger version of Maveric.!!! and CCSM settings can be manouvered without reset, crash or flicker.

 And I'll bet there is a grab-bag of other goodies that came with the last piniata' (omnibus update) :)

lol  :)

---

### Post by ronacc on 2011-12-29
@ effenberg0x0 , I like the wallpaper you show in post 4 , they even got uranus's plane of rotation right ! where did you find it ?

---

### Post by Bowmore on 2011-12-29
@ventrical
You're definitelly right, I've missed that. Normally gnome classic runs on metacity but it's obvious that this has been changed so both unity and gnome classic now use compiz as default wm. However, they do run different sets of compiz plugins defined by its compiz profile found at ccsm > preferences. Unity runs on profile Unity and gnome classic on Default.

The reason why it doesn't work for my main user where gnome classic gives a mix of gnome panels and unity stuff is that for som reason they both use the same profile, i.e Default. However profile Unity exists too but not used so what remains is to find out why they don't run separate profiles and then fix it :)

---

### Post by effenberg0x0 on 2011-12-29
> **ronacc said:**
> @ effenberg0x0 , I like the wallpaper you show in post 4 , they even got uranus's plane of rotation right ! where did you find it ?

I love this wallpaper! But I'll never remember where I got it from. It's 1920x1080 (1,5M). I have just tried to compress it, but couldn't get it to be small enough for an attachment here. PM me an e-mail address and I'll mail it you.

**EDIT:** No need to e-mail. I found the source.
[http://www.wallpapercasa.com/Planets_Aligned-39715.html](http://www.wallpapercasa.com/Planets_Aligned-39715.html)

---

### Post by ronacc on 2011-12-29
got it , thanks .

---

### Post by lolpenguin on 2011-12-30
[woops i wasn't supposed to post here]

---

### Post by ventrical on 2011-12-30
> **lolpenguin said:**
> [woops i wasn't supposed to post here]

Don't worry about it. It had regressed to the eccentricity of Uranus by the two guys from Linux Mint already - so it's all lost on me...

lol  :)

---

### Post by ronacc on 2011-12-30
the only time I ever ran mint was a couple of years ago for about 1 hr just to see what it was like .


edit: and BTW it was the polar orientation to the plane of the ecliptic of uranus not its orbital eccentricity .

---

### Post by ventrical on 2011-12-30
ehehehe... ohh   ! lol :)

---

### Post by ventrical on 2011-12-30
> **ronacc said:**
> the only time I ever ran mint was a couple of years ago for about 1 hr just to see what it was like .


There is always Unity 2D ya know :)

Thanks anyways ronacc.  :)

---

### Post by ronacc on 2011-12-30
gnome-shell

---

### Post by ventrical on 2011-12-30
> **ronacc said:**
> gnome-shell

Is that working stable now ?
Because it wasn't the last time I tried it.

---

### Post by ronacc on 2011-12-30
its been stable for me . I am careful with my updates , I use synaptic and watch what it wants to do . I haven't updated yet today so things are subject to change .:lolflag:

edit :  did todays update no dammage seen , whats giving you the problem I'll give it a try here .

---

### Post by ventrical on 2011-12-31
> **ronacc said:**
> its been stable for me . I am careful with my updates , I use synaptic and watch what it wants to do . I haven't updated yet today so things are subject to change .:lolflag:

edit :  did todays update no dammage seen , whats giving you the problem I'll give it a try here .

 I'll install it  and see if there is any improvent and get back to you. Gnome shell just didn't make any sense the last time I tired it. I liked the way it worked with Fedora. The Unity panels are easier on my eyes. Otherwise I would work Gnome shell more often.

I'll look.

---

### Post by ventrical on 2011-12-31
@ronacc,

I just don't get it. I installed gnome-shell and got the same stuff as last time.  When the windows minimizes (hovermouse in top left corner) it won't scroll using firefox. It's like I still have to do all these extra mouseclicks. It doesn't make any sense.  Mabey it's just me.

---

### Post by ronacc on 2011-12-31
we all have our preferences . I just find unity so aesthetically unpleasing and unsuited to my work style that I can not use it at all . Really I find GS only marginally better . I rarely use firefox  I'm an Opera fan , I haven't noticed a problem with there , I'll give FF a try and report back .

no scrolling problem in FF here either with wheel or bars maximized or unmaximized .

---

### Post by Bowmore on 2011-12-31
> **Bowmore said:**
> The reason why it doesn't work for my main user where gnome classic gives a mix of gnome panels and unity stuff is that for som reason they both use the same profile, i.e Default. However profile Unity exists too but not used so what remains is to find out why they don't run separate profiles and then fix it :)Just for the record, I splitted Unity and Gnome Classic by configure them using separate compiz profiles. As they both used the Default compiz profile I just exported that and then created a new profile that I assigned to Unity. Then I used the Default one just for classic. All this done under Ccsm > Preferences.

So now this issue too is solved as for my setups.

---

### Post by ventrical on 2011-12-31
> **Bowmore said:**
> Just for the record, I splitted Unity and Gnome Classic by configure them using separate compiz profiles. As they both used the Default compiz profile I just exported that and then created a new profile that I assigned to Unity. Then I used the Default one just for classic. All this done under Ccsm > Preferences.

So now this issue too is solved as for my setups.

Thanks Bowmore.

 The 'preferences' function was in really bad shape for a long time on some installs.

  I can just disable Unity Plugin using CCSM while I am in Gnome Classic or  enable it. I'm not sure of the mechanics behind this but I do know that they had it working great (still do) with Cairo Dock <unity3D/CCSM>

---

### Post by Bowmore on 2011-12-31
Assuming, it's a must, you're using separate compiz profiles for unity and gnome classic, they have different sets of compiz plugins. So when running classic you should disable the unity plugin which probably also disables some other plugins as well. Then activate the plugins you need for classic. When you got it functioning do a backup of the settings by exporting those, including the defaults values, to a file. If something then goes wrong later on you can always import those to your profile again.

Just as kansasnoob wrote in other thread you e.g have to change metacity to compiz in the file /usr/share/gnome-session/sessions/gnome-fallback.session for oneiric, just forgot to tell you about that.

Btw, if you have autostart applications that you just want to start up in classic but not in unity (e.g docky) you can fix that by adding the line NotShowIn=Unity; into the corresponding .desktop file under ~/.config/autostart/. The vice versa scenario is to add the line OnlyShowIn=Unity;

---

