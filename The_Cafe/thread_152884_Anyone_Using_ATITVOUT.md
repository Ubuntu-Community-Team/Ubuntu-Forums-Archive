---
title: "Anyone Using ATITVOUT?"
date: 2006-03-30
forum: The Cafe
---

### Post by nalmeth on 2006-03-30
[atitvout is a tool for enabling/disabling the TV out connector and switching of TV standards (PAL, NTSC, etc.) of ATI Rage graphics boards from within Linux on IA32.]("http://ubuntuforums.org/newthread.php?do=newthread&f=11")
(from freshmeat.net)
The homepage is [http://0pointer.de/lennart/projects/atitvout/]("http://0pointer.de/lennart/projects/atitvout/")
Some guy aparently made this app, but stopped all support, because he was being harassed by everyone wanting him to make it work on their special video card. Understandably. He states on the site that he won't answer any support mail, so I can't contact him about this.
There are some directions on his site, but he doesn't really outline how it is supposed to work. From what I can make out of it, you have to give the right command to load it, and then everytime you boot it should be loaded. 
I tried some of the commands, and I got my screen to flicker, making me think it worked, but no image on the tv..
There is good news though.
He made the app for this particular card:
```
[lennart@whiskey] ~$ /sbin/lspci -vs 1:0.0

        VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: FIRST INTERNATIONAL Computer Inc: Unknown device 1730
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 5
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=256]
        Memory at fc100000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at <unassigned> [disabled] [size=128K]
        Capabilities: <available only to root>
``` and this is mine:
```
sdcb@vaiobuntu:~$ lspci -vs 1:0.0
        VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: Sony Corporation: Unknown device 80e3
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 5
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 9000 [size=256]
        Memory at e8100000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 18000000 [disabled] [size=128K]
        Capabilities: <available only to root>
``` Almost identical, so in theory this should work on my laptop.
Anyone have any experience with this app?
Or have any ideas on what it would take to get it off the ground?
Do I have to make another screen in my xorg.conf or something?

---

### Post by Robstero on 2006-05-03
I'm in pretty much the same situation as you, Nalmeth. ](*,)  Installed atitvout on my HP Compaq nx9005 laptop but can't get it to play. It doesn't detect the video card that's in there, but even if I force it to use the Radeon Mobility card (using the -r flag, I think) things still don't seem to work. Am now wondering, like you, if I need to change xorg.conf. 

Things are also a bit more complicated for me since I got the laptop I'm using for nothing because it's got a bust screen, but I thought, "hey, it's still a good machine, I'll get some use out of that". Which is true, but I've also read somewhere that there might be some doubt over whether using the vga out AND the s-video out at the same time isn't a go-er. 

All very complicated, at least to me since I still consider myself a linux rookie. But I'll get this working, by hook or by crook! Shall keep you posted with my progress and hopefully we'll get this all fixed before long (if you haven't got it sorted already).

Cheers,
Robstero

---

### Post by nalmeth on 2006-05-04
Yes, likewise Robstero
let us become the Ubuntu ATITVOUT team
Two noobs will rise to the challenge, and (slowly, very slowly) surely will rise to victory
I have no progress yet, unfortunately..
I noticed that in totem, there is an option to enable tv-out, but haven't tried it yet.
Maybe you have to run atitvout, make sure there are no problems, then with totem, play a video with tvout enabled.
Also, in dapper, in system settings you can control the use of extra screens.
A couple of bait's we might bite on

---

### Post by Robstero on 2006-05-09
Haha! May our legion of two be successful at one thing, and one thing only: being able to watch films from ubuntu on our tellies. Sounds simple when put like that. Ho hum.

So anyway, now the plot's thickened for me a wee bit. In fact right now the plot's just about solidified.

Turns out my laptop won't even play XVids on the VGA screen! At least not without a lot of stuttering. It's a decent fast laptop and should be able to play them with no probs. Did a bit more digging and found out (from xorg.conf) that I'm actually using the crappy VESA driver rather than a driver specific to my video card. So I'm currently trying to get a proper driver, which is proving a bit of a pain. Got a few leads though, I'm going to give them a bash tonight.

Also,  I've found a few links on my travels. Dunno if they're any use to you or not, but here ya go anyway:

[http://koti.mbnet.fi/~keiky/misc/linux/amilo/amilo_ainfo.html#tvout](http://koti.mbnet.fi/~keiky/misc/linux/amilo/amilo_ainfo.html#tvout)
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)
[http://ubuntuforums.org/showthread.php?t=152884&highlight=atitvout](http://ubuntuforums.org/showthread.php?t=152884&highlight=atitvout)

Those last to are about installing/configuring the fglrx driver for ATI cards, which might be an option if you're not using it already. Think already it comes installed with Dapper (oh yeah, don't suppose you know the whereabouts of the extra screens settings in Dapper? I installed it over the weekend and I'm liking it a lot) so in that case you'll just need to change xorg.conf to tell your machine to use it. Think there are details on how to go about that in one of the links above. You've probably gone through all that stuff already but I just thought I'd mention it just in case;) 

I'm still a bit unclear about how xorg.conf works, but right now I'm suspecting that we *will* need to specifiy another screen for using TV-out... any good howtos about xorg.conf about, anyone?

---

### Post by nalmeth on 2006-05-09
Yeah, you will definately need the ati driver to make it work. 
fglrx is for 3D, which, unfortunatly, my crappy little card can't handle. The ATITVOUT program was *fortunately* built using my identical card though, so no hope is lost!
Thanks for the links, there is indeed some new information there for me. I will read into this stuff and of course post any new information I find.

If you're using dapper, I suggest you get your ATI driver's installed WITH fglrx, then install kubuntu-desktop. In KDE (dapper anyway) in System Settings, you can configure the extra screen which may be what we need. This is the first place I have seen GUI configuration of extra screens, so we should start here. Gnome may have it too, I just haven't come across it.

Now that I think about it, I have read some good howtos on xorg.conf.
Check back here later as I will post them.
I am at work, but may be able to do this up anyway. If not, I'll be home in 4 hours, and will work away at it, as I can't sleep at night these days...
Depending on where you live, you might just check tomorrow.

LET'S DO THIS THANG!! 
Against all odds, TEAM UBUNTU ATITVOUT will accomplish it's primary objective.
Ubuntu on the telly!

---

### Post by nalmeth on 2006-05-10
[> http://koti.mbnet.fi/~keiky/misc/lin...nfo.html#tvout]("http://koti.mbnet.fi/%7Ekeiky/misc/linux/amilo/amilo_ainfo.html#tvout")
>  This link seems to have really important steps.
I did not know that you have to have the TV connected before even starting the laptop
Perhaps we won't need to create another screen on on xorg.conf after all. You said it! Actually _***I***_ said it.
Following the very simple instructions found there, I get my display on the TV.
SUCCESS!!!
yeah baby!

I'm going to go try the totem TV-OUT, to see if we can just restrict video to the television.

Exciting times

---

### Post by Robstero on 2006-05-12
Nice one! Glad you've found success with atitvout!

I had some partial success last night (I'm in Scotland, by the way): I discovered that if I just point xorg.conf to the VESA driver, atitvout works fine! But then I get crappy video playback quality so it's a success tainted with a slightly sour taste of rubbishness. But still a partial success, and it's spurred me on to keep on at it (I was starting to wane a bit).

It seems to be a problem I've got when I try to use the x's built-in ATI (or radeon) drivers. Whenever I use those drivers I get some nice 2D acceleration (not sure exactly which 2D accelerated features are working OK but video certainly plays without a hitch) but then atitvout won't play. So I reckon that's a good shout on the kubuntu thing, I reckon I'll give that a shot. 

I tried installing ATI's proprietary drivers last night (the fglrx ones; the ones that ATI's site says are for notebooks) but x wouldn't start up. So it's back to the drawing board. 

Anyways I've got a few more avenues to try (got hold of a couple of alternative drivers, now I just need to work out how to install them, to get the modules to load etc etc)

Yeah, apparently if you don't specify extra displays in xorg.conf and you connect another display, x will just "clone" the settings you've on the fly and you'll end up with two displays working. Nice work, the X guys.

I read somewhere that if you do a "man xorg.conf" or something similar then you'll get some help with xorg.conf. Not tried it yet, though. But I also found this:

[http://ubuntuforums.org/showthread.php?t=96765&highlight=howto+xorg.conf+screens](http://ubuntuforums.org/showthread.php?t=96765&highlight=howto+xorg.conf+screens)

Which might be handy. Seems you can set up which portion of the main screen you'd like to display on your TV, which might help you out a wee bit.

Team ATITVOUT has prevailed! Or at least in part. Some parts of the batallion are lagging a bit (i.e. me) but they'll catch up with the rest sooner or later! :)

---

### Post by Robstero on 2006-05-15
Sorted :D 

As it turns out, the Radeon driver that's built in to x.org turns off VBE (Vesa Bios Extensions) calls that ATITVOUT relys on. This explains why all was fine when using the VESA driver but not the Radeon one (or the ATI one, which I'm led to believe is different). So if you go into xorg.conf and add the line

```
Option "BIOSHotkeys" "true"
```

to the device section and reboot, all is well. Probably should've paid more attention to atitvout's error messages at the outset ](*,) 

I got the answer here:

[http://groups.yahoo.com/group/amilo/message/748](http://groups.yahoo.com/group/amilo/message/748)

But there's also a bug report on the Debian lists here:

[http://lists.debian.org/debian-x/2005/11/msg00137.html](http://lists.debian.org/debian-x/2005/11/msg00137.html)

So all's well now. Weirdly I've noticed that if I boot with a monitor connected as well as the TV, atitvout doesn't seem to work (it reports the same VBE related errors). But if you boot with only the TV connected, all is well. I've yet to confirm this though, I'll do a couple of experiments tonight.

Anyways I'm a happy chappie now. Currently working my way through the 3rd series of Curb Your Enthusiasm.

Next up: getting a remote control to work!

Team atitvout member Robstero, signing out.

---

### Post by nalmeth on 2006-05-16
ha interesting find
 
Good work, primary objective completed
 
It's sweet ain't it.
> So all's well now. Weirdly I've noticed that if I boot with a monitor connected as well as the TV, atitvout doesn't seem to work (it reports the same VBE related errors). But if you boot with only the TV connected, all is well. I've yet to confirm this though, I'll do a couple of experiments tonight.
Not so cool. There must be a fix for this or something. Just to clarify, you're using the extra "cloned" monitor out on your laptop right? I will try this when I can to see if I get the same problem.
 
I've never seen your VBE errors on my machine though!
 
I'm now trying to figure out how to use totem to display only video's on the TV. I have some idea's and starting point's, but not getting anywhere fast.
 
I will share the progress I make with this.
 
Anyone else using atitvout (un)successfully?

---

### Post by lorenzo on 2006-06-08
I've used it some time ago. I had to:

1) turn on the laptop with s-video cable plugged
2) once in linux, going in a NON X session (ex: Ctrl-Alt-F3)
3) switching with atitvout from l to t (to television)
4) viewing movies with mplayer specifying vesa driver

I COULD NOT
- Start X on television
- Having both laptop screen an television on
- using totem (or whatever else graphic program)

So, in the end, when I have to watch a movie I reboot with XP...:( 

THE ATI DRIVER issue:
I have a nx9010 (IGP 340 ati driver RS200): If you have such a driver: FORGET about fglrx. It doesn't work!!!!!

So atitvout is your only solution (as far as I know).:???: 

If anyone has more interesting news....... go ahed!

Ciao,
Lorenzo

---

