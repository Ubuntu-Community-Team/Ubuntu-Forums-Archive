---
title: "Re: Ubuntu's overlay scrollbars, on the way out, but not this time"
date: 2015-02-06
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-02-06
It would appear Ubuntu's overlay scrollbars will be history, maybe in 15.04 with gtk-3.16 which is being strongly considered
( and one major reason for using  would be Ubuntu's overlay scrollbars which they don't want to keep supporting anymore

The new ones are probably better anyway, bigger & no, annoying at times, thumb 
(- can't do a screen as screenshot is broken, maybe gtk-3.16

Desktop test of gtk-3.16 - 
[https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa)

---

### Post by VinDSL on 2015-02-06
Ooooh, I like that! 

I've always been neutral on the overlay scrollbars, since I scroll using a mouse-wheel (or two-finger it on touchpads), but the overlay in GEdit was killing me -- distracting as ^!%# when I was trying to concentrate on coding .  The GTK+2.0 upgrade killed that pesky nuisance :D

Thx for posting this!

---

### Post by mc4man on 2015-02-06
The break here in a ubuntu session on screenshots is definitely from gtk-3.15.4
Also the scrollbar in current gnome-terminal is now pretty crappy in  - 
it shows, (or area it occupies shows) when not needed at all
looks bad & hard to see when usable

known issues - 
> Some known issues which we'll try to fix for the release:

  - There's a black notification shown in the greeter
  - Not all apps have overlay scrollbars (devhelp, gnome-terminal, ...)
  - gnome-terminal shrinks to 1x1 sometimes (cherry-pick
    07fe194eb60aa9ec2eacdafdb4ba6ac91a636f34, but we suspect this may be
    incomplete)
  - Overlay scrollbars aren't styled like ours were
  - They hide completely when inactive, meaning that you don't know how
    far you've scrolled

i'm not of the opinion that hiding completely when inactive is an 'issue', seems one of those rare,  to me, good moves upstream

---

### Post by VinDSL on 2015-02-06
> **mc4man said:**
> The new ones are probably better anyway, bigger & no, annoying at times, thumb 
(- can't do a screen as screenshot is broken, maybe gtk-3.16

Here's a screenie of GEdit... ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-6-feb-2015-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-feb-2015-1.png")[/INDENT]

---

### Post by VinDSL on 2015-02-06
Everything looks great, to me.  Screenshot is working fine, too.

I should probably mention, the only packages I installed from that repo were the scrollbar twins and their depends...

```
Commit Log for Fri Feb  6 17:14:00 2015

Upgraded the following packages:
gtk2-engines-pixbuf (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgail-common (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgail18 (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgtk2.0-0 (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgtk2.0-bin (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
overlay-scrollbar-gtk2 (0.2.16+r359+15.04.20150202-0ubuntu1) to 0.2.16+r359+15.04.20150202-0ubuntu1+ppa1
overlay-scrollbar (0.2.16+r359+15.04.20150202-0ubuntu1) to 0.2.16+r359+15.04.20150202-0ubuntu1+ppa1

```

Afterwards, I disabled the repo.  I don't want any unexpected surprises, you know? :)

---

### Post by kansasnoob on 2015-02-06
Tim Lunn just put out a Call for Testing GTK 3.15.4 on the Ubuntu GNOME QA mailing list and it appears to point to the same PPA:

[https://lists.launchpad.net/ubuntugnome-qa/msg00733.html](https://lists.launchpad.net/ubuntugnome-qa/msg00733.html)

Good riddance to the overlay-scrollbars. That was always one of the first things I axed, but then the contrast between the scrollbars and scrollbar buttons was not really sufficient in either the Ambiance or Radiance themes.

---

### Post by VinDSL on 2015-02-06
> **kansasnoob said:**
> Tim Lunn just put out a Call for Testing GTK 3.15.4 on the Ubuntu GNOME QA mailing list and it appears to point to the same PPA[...]

Oh, Dear!  

Guess I'll get out the shotgun, reload that repo, and pull the trigger.  :)

---

### Post by VinDSL on 2015-02-06
Interesting!

I re-enabled that repo but the packages wouldn't auth.

```
vindsl@Zuul:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  2CC98497A1231595

```

...fixed the problem.

Okay, here goes nothing.  :)

---

### Post by VinDSL on 2015-02-06
> **mc4man said:**
> (- can't do a screen as screenshot is broken, maybe gtk-3.16[...]

Confirmed.  Screenshot is definitely rekt now... ;)

---

### Post by mc4man on 2015-02-06
There is some minor likely theme based issues, those will be taken care of without much issue. One is DnD shows more than the object.

With 3.15+ not changing this I guess Gnome decided text previews in text icons is not useful though I do really like them.  (not sure if gtk or nautilus is the actor there

---

### Post by mc4man on 2015-02-06
> **VinDSL said:**
> Confirmed.  Screenshot is definitely rekt now... ;)

Just for you - 
you can use gnome-screenshot from a terminal & send to clipboard ( -c option
Then paste into gimp or similar..

---

### Post by VinDSL on 2015-02-07
Great idea!

I thought, "Why not just make a keyboard shortcut?"

Guess what?!?!?  Surprise, surprise... :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-feb-2015-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-feb-2015-1.png")[/INDENT]

---

### Post by mc4man on 2015-02-07
> **VinDSL said:**
> Great idea!

I thought, "Why not just make a keyboard shortcut?"

Guess what?!?!?  Surprise, surprise... :D
Cool, never noticed..
ot - just curious - what happens on your setup with the (I assume) 4:3 monitor if you were to open a 1920:1080 image, eg. if I was to take a full screen here & when attaching the [forum didn't scale down]("http://ubuntuforums.org/showthread.php?t=2247726") like they currently do. (or use an image host instead.

---

### Post by VinDSL on 2015-02-07
Close. I'm running a Dell UltraSharp 1907FP.  The aspect ratio is 5:4  Dern thing just won't quit working :)

Funny story:  I bought this like 8 years ago, because that's what the State Lottery Commission was using for displays at all their retailers - stores, gas stations, etc.  I figured if they can run them 24/7/365 without the backlights burning out, they must be okay - and I haven't been disappointed.

Anyway, if I understand your question correctly...

When I look at a bigger image than the native res supports, the Chromium browser automagically scales it down to fit the screen.  If I want to increase the image to full size, all I need to do is click it with the mouse, and I use the scrollbars .

The problem is when a web site is coded to display images at a fixed size, e.g. the original size.  Then, Chromium doesn't compensate for it.

Generally speaking, it not a prob...  ;)

---

### Post by mc4man on 2015-02-12
gtk-3.15 has been put off until whinoceros

---

### Post by Cavsfan on 2015-02-12
> **mc4man said:**
> gtk-3.15 has been put off until whinoceros

Ha! :lolflag:

---

### Post by mc4man on 2015-02-12
> **Cavsfan said:**
> Ha! :lolflag:

That was from one of the main ubuntu dev's (wobbly whinoceros

---

### Post by VinDSL on 2015-02-12
> **mc4man said:**
> That was from one of the main ubuntu dev's (**wobbly whinoceros**

That name sounds familiar...

I think he's a DJ on [my SoundCloud Stream]("https://soundcloud.com/vindsl")   :D

**EDIT**

In order to stay OT...

Are we supposed to keep rolling with gtk-3.15 in the dev branch.

They haven't given up development.  It just isn't making it into Vivid, right?

---

### Post by mc4man on 2015-02-12
> **VinDSL said:**
> 
In order to stay OT...

Are we supposed to keep rolling with gtk-3.15 in the dev branch.

They haven't given up development.  It just isn't making it into Vivid, right?

Nah - you may want to purge. The gtk sources have been removed from the ppa so I wouldn't expect anything new for a while.
(- what may go on in any of the gnome 3 ppa's is another matter.

It seems work on the Desktop is a bit like a crockpot, low & slow

---

### Post by VinDSL on 2015-02-12
> **mc4man said:**
> Nah - you may want to purge. The gtk sources have been removed from the ppa so I wouldn't expect anything new for a while.[...]

Okay - I'll dial it back to here:  [http://ubuntuforums.org/showthread.php?t=2264318&p=13223392&viewfull=1#post13223392](http://ubuntuforums.org/showthread.php?t=2264318&p=13223392&viewfull=1#post13223392)

Plan A :D

---

### Post by VinDSL on 2015-02-12
Interesting!

Looks like they emptied the repo: [https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa)

And, drained the pool: [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/pool/main/o/overlay-scrollbar/](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/pool/main/o/overlay-scrollbar/)

Guess I'll need to go to Plan C  :p

---

### Post by Cavsfan on 2015-02-12
> **mc4man said:**
> Nah - you may want to purge. The gtk sources have been removed from the ppa so I wouldn't expect anything new for a while.
(- what may go on in any of the gnome 3 ppa's is another matter.

It seems work on the Desktop is a bit like a crockpot, low & slow

I was just about to add that PPA when I seen your **wobbly whinoceros** post. :lolflag:
Lol! Bummer just when I was starting to get interested too. :p

---

### Post by VinDSL on 2015-02-12
> **Cavsfan said:**
> I was just about to add that PPA when I seen your **wobbly whinoceros** post. :lolflag:
Lol! Bummer just when I was starting to get interested too. :p

You're lucky!

Looks like downgrading the gtk-3.16 libs isn't going to be easy... :)

---

### Post by mc4man on 2015-02-12
> **VinDSL said:**
> You're lucky!

Looks like downgrading the gtk-3.16 libs isn't going to be easy... :)
I'll have to check that out...
regarding prior plan... Lp saves alot, usually at least 1 build back
[https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa/+builds?build_state=built](https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa/+builds?build_state=built)

---

### Post by mc4man on 2015-02-12
> **VinDSL said:**
> You're lucky!

Looks like downgrading the gtk-3.16 libs isn't going to be easy... :)

Nice of them to dump so quickly. I believe I got it here manually, a log out is final test.
List here to revert glib, gtk3, gtk2 (probably should also do the overlay scrolls, anyway for amd64 - 
> gir1.2-atk-1.0_2.14.0-1ubuntu1_amd64.deb   
gir1.2-gtk-3.0_3.14.8-0ubuntu1_amd64.deb 
libatk1.0-0_2.14.0-1ubuntu1_amd64.deb
libatk1.0-data_2.14.0-1ubuntu1_all.deb     
libglib2.0-bin_2.43.3-1_amd64.deb  
libglib2.0-data_2.43.3-1_all.deb
libglib2.0-0_2.43.3-1_amd64.deb
libgtk2.0-0_2.24.25-0ubuntu2_amd64.deb 
libgtk2.0-bin_2.24.25-0ubuntu2_amd64.deb    
libgtk2.0-common_2.24.25-0ubuntu2_all.deb
libgail18_2.24.25-0ubuntu2_amd64.deb 
libgail-common_2.24.25-0ubuntu2_amd64.deb      
libgtk-3-0_3.14.8-0ubuntu1_amd64.deb
libgail-3-0_3.14.8-0ubuntu1_amd64.deb      
libgtk-3-bin_3.14.8-0ubuntu1_amd64.deb 
libgtk-3-common_3.14.8-0ubuntu1_all.deb
gtk2-engines-pixbuf_2.24.25-0ubuntu2_amd64.deb

In this case as long as no log out till right a few broken packages along the way is ok, just fix before leaving session.-
gtk2-engines-pixbuf_2.24.25-0ubuntu2_amd64.deb

---

### Post by VinDSL on 2015-02-12
I went through the commit logs and have a pretty good idea how to put humpty dumpty back together again :D

Here are the changes AFAIK:

```
gir1.2-atk-1.0 (2.14.0-1ubuntu1) to 2.15.4-0ubuntu1~ppa0
gir1.2-gtk-3.0 (3.14.7-0ubuntu3) to 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
gtk2-engines-pixbuf (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libatk1.0-0 (2.14.0-1ubuntu1) to 2.15.4-0ubuntu1~ppa0
libatk1.0-data (2.14.0-1ubuntu1) to 2.15.4-0ubuntu1~ppa0
libgail-common (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgail18 (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgail-3-0 (3.14.7-0ubuntu3) to 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
libglib2.0-0 (2.43.3-1) to 2.43.4~20150205.r1+git7417198-0ubuntu1~ppa0
libglib2.0-bin (2.43.3-1) to 2.43.4~20150205.r1+git7417198-0ubuntu1~ppa0
libglib2.0-data (2.43.3-1) to 2.43.4~20150205.r1+git7417198-0ubuntu1~ppa0
libgtk2.0-0 (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgtk2.0-common (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgtk2.0-bin (2.24.25-0ubuntu2) to 2.24.25-0ubuntu3~ppa0
libgtk-3-0 (3.14.7-0ubuntu3) to 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
libgtk-3-common (3.14.7-0ubuntu3) to 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
libgtk-3-bin (3.14.7-0ubuntu3) to 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
overlay-scrollbar-gtk2 (0.2.16+r359+15.04.20150202-0ubuntu1) to 0.2.16+r359+15.04.20150202-0ubuntu1+ppa1

```

Still...

I like those new scrollbars, bugz and all.

I'm thinking about just leaving it be.

---

### Post by VinDSL on 2015-02-26
Interesting!

The screensaver just starting working again, after the last update - and I'm still running the same gtk libs:

```
vindsl@Zuul:~$ apt-cache policy libgtk-3-0
libgtk-3-0:
  Installed: 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
  Candidate: 3.15.5~20150206.r1+git0b06b1e-0ubuntu1
  Version table:
 *** 3.15.5~20150206.r1+git0b06b1e-0ubuntu1 0
        100 /var/lib/dpkg/status
     3.14.8-0ubuntu1 0
        500 http://mirror.picosecond.org/ubuntu/ vivid/main i386 Packages
vindsl@Zuul:~$
```

Hrm...

---

### Post by VinDSL on 2015-03-03
Default screensaver quit working again, but...

I discovered scrot still works a treat.  ;)

---

