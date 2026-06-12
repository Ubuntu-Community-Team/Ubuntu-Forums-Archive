---
title: "Running 10.04 after official support ends? (eldery users)"
date: 2012-07-06
forum: The Cafe
---

### Post by QwUo173Hy on 2012-07-06
My parents are happily running 10.04 at the moment. I'm using 12.04 and I find it great.

When support for 10.04 is up in April 2013, I would ideally like to wait for the next LTS, which will be a year later (or more if I wait for a point release).

The only concern I see with leaving 10.04 running until 2013 is security of the web-browser. Am I right in thinking that if I keep firefox up-to-date myself manually, that I can leave them running it until 14.04.1 comes out? They use credit card transactions online and e-mail. That's about it.

Any advice appreciated!
Jarlath

---

### Post by kurt18947 on 2012-07-06
I think you could use a firefox ppa to keep firefox up to date.  That doesn't help with non-browser security updates though.  Have you looked at 12.04's 'classic no-effects' mode?  There are threads in these forums on how to get12.04 to look and act very much like gnome 2.  I think it'd be pretty easy to get 12.04 classic to where light users could not tell the difference.  This might be a better bet than waiting for 14.04 - there is no assurance that 14.04 will have 'classic' mode AFAIK.

Are you aware of MATE and Cinnamon?  These are desktops supported by Mint but installable in Ubuntu 12.04.  MATE is supposed to be an updated Gnome 2 with Gnome 3 underpinnings.  I've installed Cinnamon via a  ppa in 12.04 and it works pretty well.  I did not install muffin and Cinnamon still works.    I have had Cinnamon freeze in Mint Maya so wouldn't recommend that for elderly users.

---

### Post by CharlesA on 2012-07-06
12.04 has Gnome classic running off Gnome 3, which is pretty close to the Gnome 2 version.

Also: Running an OS without security updates, even if you only use the browser and are upgrading the browser, is a bad idea. You really wouldn't want to have a box owned and not know about it, right?

---

### Post by pqwoerituytrueiwoq on 2012-07-06
just hoping mate is good enough for me by 10.04 eol (same goes for compiz)
at least the best (imo) theme (Albatross) in xubuntu got the needed fix the other day not sure when it will be in the repos
i am confident we will be able to have 12.04 good enough by late april 2013 (via ppa updates to the DE/compiz)
if not at least server related parts of 10.04 will be supported still 

if cinnamon gets the compiz features i need (window management) i may use it instead

---

### Post by SeijiSensei on 2012-07-06
If the issue is Unity, I'd consider switching to KDE and using Kubuntu 12.04.  Toss in Firefox and Thunderbird, and you'll be set for years to come.  I doubt your parents would find it any more difficult to use than GNOME.

---

### Post by Linuxratty on 2012-07-06
I'm using the latest ltr but not using Unity. There is no reason they can't do the same.Different strokes for different folks and all.
 i had the same worries but went with fallback gnome and all is good.
  It has some very nice features and a couple sweet surprises.:)

[http://www.youtube.com/watch?feature=player_embedded&list=UUIiSwcm9xiFb3Y4wjzR41eQ&v=DIQXKrH46wI](http://www.youtube.com/watch?feature=player_embedded&list=UUIiSwcm9xiFb3Y4wjzR41eQ&v=DIQXKrH46wI)

---

### Post by CharlesA on 2012-07-06
> **SeijiSensei said:**
> If the issue is Unity, I'd consider switching to KDE and using Kubuntu 12.04.  Toss in Firefox and Thunderbird, and you'll be set for years to come.  I doubt your parents would find it any more difficult to use than GNOME.
This, totally.

---

### Post by kansasnoob on 2012-07-07
I highly recommend NOT running an OS w/o adequate security updates!

I maintain a total of about 43 PC's, about 36 of which are used by fellow seniors, and most of them simply find learning a new OS too challenging. They simply want something familiar. That's why I started working on this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I can now get Precise (12.04) to look and behave very much like Gnome 2, and I had quite a few of them test-drive my loaner PC with those tweaks applied and with some minor menu edits and adding a few of their favorite apps they're quite happy :D

But I'm waiting until 12.04.1 releases next month to begin the upgrades.

---

### Post by Duncan J Murray on 2012-07-07
I agree with those suggesting 12.04 fallback.

I run 10.04 at present, but have a netbook running 12.04 fallback without compiz - and it's terrific.  So far, I can't tell the difference between it and 10.04.

All best,

Duncan

---

### Post by SeijiSensei on 2012-07-07
> **kansasnoob said:**
> That's why I started working on this: [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370).  I can now get Precise (12.04) to look and behave very much like Gnome 2

I skimmed that thread but couldn't really tell whether you were installing GNOME 3 or GNOME 2.  Is it essentially a GNOME 3 installation without the Unity interface?

Obviously if it's based on the now-obsolete GNOME 2, it wouldn't be a very good solution for a system intended for long-term unsupported use.  So I'm guessing it's GNOME 3, yes?

---

### Post by Duncan J Murray on 2012-07-07
Certainly gnome-fallback is gnome3 and gtk3 based.

---

### Post by kansasnoob on 2012-07-08
> **SeijiSensei said:**
> I skimmed that thread but couldn't really tell whether you were installing GNOME 3 or GNOME 2.  Is it essentially a GNOME 3 installation without the Unity interface?

Obviously if it's based on the now-obsolete GNOME 2, it wouldn't be a very good solution for a system intended for long-term unsupported use.  So I'm guessing it's GNOME 3, yes?

It's absolutely still Gnome 3. In fact step #1 installs very few packages:

alacarte
cups-pk-helper
gir1.2-gconf-2.0
gir1.2-panelapplet-4.0
gnome-applets
gnome-applets-data
gnome-panel
gnome-panel-data
gnome-session-fallback
indicator-applet-complete
libpanel-applet-4-0 python-gmenu

I include step #2 because I find most of my peers prefer the standard clock applet combined with the standard indicator-applet. 

And I include 'shiki-colors-metacity-theme' to restore a more "retro" window button appearance.

Caffeine requires a PPA but it's an excellent replacement for the now non-existent 'gnome-inhibit-applet' so a person can easily inhibit the screen-saver for viewing videos and such.

So very, very little is installed and NOTHING is removed. Since nothing is removed it's quite easy to set up a PC for multiple users. One user can login to their classic session with their settings and another user can login to their Unity session with their settings :)

And I've found the Kukitwo themes in webupd8's theming ppa to provide dependable alternatives that don't break anything.

Currently there are only two minor issues that effect me; hplip-gui launches too quickly and crashes, and libre-office launchers don't work as they should if added to the desktop. But both of those issues also effect other DEs as well and they can be worked around.

I personally find this solution much easier than installing Mate or Cinnamon.

---

### Post by xedi on 2012-07-08
Have you actually shown Unity to your parents? Maybe they would like it in which case there would be no issues just upgrading. Especially considering that they only use the browser and email, the transition should be not very difficult.

Edit: Thinking about it, you mentioned upgrading in 2014, so Unity is apparently not the issue which is what most here assume, what is the issue then upgrading now?

---

### Post by kansasnoob on 2012-07-08
> **xedi said:**
> Have you actually shown Unity to your parents? Maybe they would like it in which case there would be no issues just upgrading. Especially considering that they only use the browser and email, the transition should be not very difficult.

Edit: Thinking about it, you mentioned upgrading in 2014, so Unity is apparently not the issue which is what most here assume, what is the issue then upgrading now?

Very good question :)

---

### Post by sakamoto on 2012-07-29
nah - grandparents dont like such huge GUI changes :) they do not see any benefits in changing anymore. they want easy way for browsing internet, collecting pictures,...

they just do not want change :)

---

### Post by cariboo on 2012-07-29
Unity with the icons for all the programs they use in the launcher, and autohide turned off, isn't that much of a change, I know my Mom only uses 4 or 5 different programs, so it wasn't a problem for her to switch to Unity.

Where the big problem lies, is if you don't know how to use Unity fully yourself, you're going to have a hard time showing someone else how to use it

---

### Post by kurt18947 on 2012-07-29
> **cariboo907 said:**
> Unity with the icons for all the programs they use in the launcher, and autohide turned off, isn't that much of a change, I know my Mom only uses 4 or 5 different programs, so it wasn't a problem for her to switch to Unity.

Where the big problem lies, is if you don't know how to use Unity fully yourself, you're going to have a hard time showing someone else how to use it

Correct.  SWMBO has 3 launchers on her desktop running gnome-shell (yes, you can put launchers on a gnome 3 desktop - you just have to search a bit.)  She spends 90% of her time in Firefox,  8% in Thunderbird and 2% in L.O. writer.  So yeah .......

---

### Post by click4851 on 2012-07-29
I think you would be fine waiting for the next LTS.

---

### Post by sakamoto on 2012-07-29
is there a possibility the LTS period will be extended for 10.04?

---

### Post by chili555 on 2012-07-29
> **SeijiSensei said:**
> If the issue is Unity, I'd consider switching to KDE and using Kubuntu 12.04.  Toss in Firefox and Thunderbird, and you'll be set for years to come.  I doubt your parents would find it any more difficult to use than GNOME.Exactly! And someone in this household who is in her 70's agrees fully. There are so many variant windowing managers available such that you needn't sacrifice security to find one the 'elderly' will like. A great opportunity to use a live CD, I believe; try before installing.

---

### Post by vexorian on 2012-07-29
I would stick with 10.10 and old firefox version. There are two ways to accomplish good security, the first one is to get the most recent patched version so that no novel security bug hits you. The other is to keep using a version so old that nobody targets it anymore. ;)

But I guess the ppas will probably work.

GNOME fallback is really not at all like the real deal. It is far more limited, less supported and in 12.04 some stuff won't work as well as before.

---

### Post by kevinmchapman on 2012-07-29
There are a lot of assumptions about the requirements of elderly users here. Has anyone asked them?

There are plenty of threads stating that geeks on this forum are different from the "average user", so why assume that you know what the average elderly person wants?

---

### Post by Althusian on 2012-07-29
I want to say a big thankyou to Ubuntu and the Ubuntu community for making Linux work for me. 
Me and Mrs Althusian have three computers running Ubuntu with Windoze (rarely used) on one of them for one or two special tasks. 

BUT I think that Unity isn't as efficient at conventional WIMP GUIs. At least, not on a desktop/PC. 
(Where efficiency is defined as how fast I can get through work and how easily I can customise).
It also seems to have more hiccups and generally start and run and shut down more slowly.
Using 12.04 LTS in Classic mode is just about workable (the other two machines run unsupported version 10. something. Goodness knows what security holes there are...)

Two questions:
-- do you think Classic will be quietly dumped?
-- should I bite the bullet and go to KDE and Kubuntu?

Apologies if this is off topic.

---

### Post by vexorian on 2012-07-29
> -- do you think Classic will be quietly dumped? It will be dumped loudly, but I think MATE will be in a stable, updated state when that happens.

If you can use 12.04's classic GNOME, it should last and be support at least until the end of the Precise LTS cycle.

> -- should I bite the bullet and go to KDE and Kubuntu?KDE4 is as crazy of a change as unity and GNOME-shell. I wouldn't recommend if the users are already used to classic GNOME.

---

### Post by CharlesA on 2012-07-29
Gnome 2 is dead and has been for a while. There is still Gnome Classic on Gnome 3, and a fork of Gnome 2 named MATE. I have only used Gnome Classic a couple times before going back to Unity.

Use whatever DE suits your needs.

[SIZE="1"]Also Fedora..[/SIZE]

---

### Post by Irihapeti on 2012-07-29
> **kevinmchapman said:**
> There are a lot of assumptions about the requirements of elderly users here. Has anyone asked them?

There are plenty of threads stating that geeks on this forum are different from the "average user", so why assume that you know what the average elderly person wants?

Thank you.

I happen to be an older user and a grandmother, and the stereotypical assumptions are starting to annoy me.

I mean, was I supposed to lose my mind when my first grandchild was born?

---

### Post by sanderella on 2012-07-30
I'm an elderly user, too. I'm unhappy with 12.04, but slowly getting used to it. I wish there was a *very* long term LTS.

---

### Post by -jay- on 2012-07-30
> **sanderella said:**
> I'm an elderly user, too. I'm unhappy with 12.04, but slowly getting used to it. I wish there was a *very* long term LTS.

same here

---

### Post by chili555 on 2012-07-30
> **Irihapeti said:**
> 
I mean, was I supposed to lose my mind when my first grandchild was born?LOL! 

My GREAT-grandson will be ready for his first tablet soon. I'll make sure he gets an Android and I'll help configure his wireless. 

I think some elderly persons *are* resistant to change and I think some are not. Generalizations are inaccurate, generally.

---

### Post by kevinmchapman on 2012-07-30
> **chili555 said:**
> I think some elderly persons *are* resistant to change and I think some are not. Generalizations are inaccurate, generally.

Yes, agreed. I see a lot of posters suggesting that older people do not like change. It is my observation that young conservative people turn into older conservative people, and  young more adventurous types become older more adventurous types. A quick read of these forums tends to confirm that to me :)

---

### Post by CharlesA on 2012-07-30
> **kevinmchapman said:**
> Yes, agreed. I see a lot of posters suggesting that older people do not like change. It is my observation that young conservative people turn into older conservative people, and  young more adventurous types become older more adventurous types. A quick read of these forums tends to confirm that to me :)
This is so true.

Also generalizations sucks.

---

### Post by vexorian on 2012-07-30
^ Including that one.

---

### Post by CharlesA on 2012-07-30
> **vexorian said:**
> ^ Including that one.
Which was exactly my point. ;)

---

### Post by kevinmchapman on 2012-07-30
> **vexorian said:**
> ^ Including that one.

Glad you spotted it. Not all my posts get replyed to so quickly... ;)

---

### Post by kurt18947 on 2012-07-30
> **chili555 said:**
> LOL! 

My GREAT-grandson will be ready for his first tablet soon. I'll make sure he gets an Android and I'll help configure his wireless. 

I think some elderly persons *are* resistant to change and I think some are not. Generalizations are inaccurate, generally.

And some persons don't have to be elderly to be resistant to change.  Exhibit A:  Gnome 3 & Unity:lolflag:

---

### Post by kd5mkv on 2012-07-30
I am waiting as well,I tried 12.04 on Virtualbox lokked and ran nicely.
Did upgrade and nada, no desktop enviroment, I tried sudo everything and it
is gone. I think by April 2013 the LTS version should be sorted.

---

### Post by CharlesA on 2012-07-30
Always test a distro on the physical hardware before deciding to update.

A livecd works wonders.

---

### Post by QwUo173Hy on 2012-07-31
> **xedi said:**
> 
Edit: Thinking about it, you mentioned upgrading in 2014, so Unity is apparently not the issue which is what most here assume, what is the issue then upgrading now?

OP here! Thank you for replying and I'm sorry for not mentioning why I'm reluctant to upgrade. I don't think I was sure myself.

The reasons I don't want to upgrade them are:
[LIST=1]
[*]Since putting 10.04 on the brand new Dell laptop, I have had no complaints! (I would have been happy to leave windows there but they found various popups confusing as well as locating files).
[*]Getting wireless working was an incredible PITA that I wouldn't wish on my worst enemy - I don't want to go through that again (and no, liveCD doesn't give you the full picture as you can't install proprietary drivers - they need a reboot to work!)
[*]If it doesn't work on their hardware, we're even more screwed - 10.04 will be gone and I'll have to buy a windows licence.
[/LIST]

So yeah, call me lazy but I can't afford to help out friends and family with Ubuntu if each install takes a full day of tinkering (I know this isn't Ubuntu/Canonical's fault, but it can be a reality some times).

So I was hoping to hold out until the next LTS entirely. I'm not concerned about them using Unity at all. Mum's a dab hand on Ubuntu and Dad learns from her, slowly :)

Some of you mentioned the box being "owned". Does it matter if it's owned if the browser is secure and stores details securely? It's all web-apps they're using so the only problem I can imagine is a keylogger.

---

### Post by QwUo173Hy on 2012-07-31
> **kurt18947 said:**
> And some persons don't have to be elderly to be resistant to change.  Exhibit A:  Gnome 3 & Unity:lolflag:
Very funny, and very true :)

---

### Post by kurt18947 on 2012-07-31
I can't speak for others but for me, wireless in 12.04 is far easier than 10.04.  Of course my adapters were chosen because they were known to be Linux friendly.  Newer Ralink and Broadcom chips are known for requiring post install additional drivers.  I'd still be inclined to try a 12.04 live CD/USB and see how things behave.  Your current installs will not be touched unless you choose to install from the live.

---

### Post by vexorian on 2012-07-31
> **jarlath said:**
> Very funny, and very true :)
It is an attempt to cover up that g3 and unity are just not well received. Misses that most of the Linux community started on as windows users and *have* coped with plenty of change. I think it is a very unfair dismissal of criticism. Some changes are a benefit and some changes are not, and I think I can decide which one is a benefit to *me*.

---

