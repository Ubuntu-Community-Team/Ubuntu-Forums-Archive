---
title: "Does Quantal include Gnome Classic?"
date: 2012-05-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VanillaMozilla on 2012-05-23
I really, really need a stable system, and I'm trying to avoid all this churning.  I have seen reports that Classic is just temporary.  Any update on that?  Is it available in Quantal?

---

### Post by VinDSL on 2012-05-23
I read, somewhere that "Classic", so called, isn't going to be included in Ubu QQ.

Read it in this forum, if I remember correctly...  ;)

---

### Post by Mr. Picklesworth on 2012-05-23
> **VinDSL said:**
> I read, somewhere that "Classic", so called, isn't going to be included in Ubu QQ.

Read it in this forum, if I remember correctly...  ;)

You might be thinking Unity 2d. I don't actually know this, but personally I doubt gnome-panel 3 is going anywhere for the foreseeable future, as long as people are interested in it: it still works and it needs very little maintenance. However - and this is where we start talking semantics - I wouldn't be surprised if some of the helpful surrounding bits were removed, like Ubuntu's default configuration. It might stop coming with gnome-shell, too, since the goal for both Unity and Gnome Shell is to stop needing a 2d fallback session.

---

### Post by VanillaMozilla on 2012-05-23
Thanks.  That's a little confusing.  I guess gnome-session-fallback is the 2d fallback session you were referring to?

But Quantal does have gnome-session-fallback available, right?

---

### Post by xebian on 2012-05-23
> **VanillaMozilla said:**
> **]I really, really need a stable system,**[/COLOR] and I'm trying to avoid all this churning.  I have seen reports that Classic is just temporary.  Any update on that?  Is it available in Quantal?


If you "[COLOR="Red"]**really, really need a stable system**[/COLOR]" as you said then Precise (aka 12.04) is your system.

---

### Post by VanillaMozilla on 2012-05-23
> **xebian said:**
> If you "[COLOR="Red"]**really, really need a stable system**[/COLOR]" as you said then Precise (aka 12.04) is your system.
Because it's LTS.  Good point.  For now I'm just trying to plan ahead.  It's an option, of course, now that the dust is beginning to settle on all the changes.

The one problem with that (which I'm not asking you to help with) is that it can be difficult getting current applications and keeping them running without updating the system.  Updating with PPAs has not been good to me.

---

### Post by pressureman on 2012-05-23
Fedora proved last year that GNOME Shell could run without GPU support - [http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjI](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjI)

So there isn't really any reason for GNOME Panel to continue to be shipped (apart from that some people prefer it). I remember reading in the early days og GNOME Shell, the GNOME developers saying that the fallback/panel session would be deprecated at some point.

You could always try Cinnamon for a GNOME Panel-like DE.

---

### Post by VanillaMozilla on 2012-05-23
I'm a little confused by the terminology.  The Gnome panel is the bar that you put little system notifiers and applets on?  The thing the "Applications Places" menu goes on?  That will be discontinued?  Because if that stuff disappears, I might as well plan my exit now.

(Without getting into contentious matters, let me just say that personal preferences aside, two of my computers will probably not run Unity, and will just barely run Gnome 3 shell.  And Cinnamon is not only new, but my understanding is it's also heavy-weight.)

---

### Post by grahammechanical on 2012-05-23
You really need to read this:

[http://en.wikipedia.org/wiki/GNOME_Panel]("http://en.wikipedia.org/wiki/GNOME_Panel")

It all comes down to this: Ubuntu sits on top of the Gnome 3 desktop top environment.

[http://en.wikipedia.org/wiki/GNOME]("http://en.wikipedia.org/wiki/GNOME")

but it uses the Unity user interface that relies on the Compiz compositing/window manager. This is what gives us the 3D effects.

For those machines that do not have a video card capable of running Unity 3D there is a fall-back mode. It is called Unity 2D and it uses the Metacity compositing manager.

The Gnome developers have their own user interface for Gnome 3. It is called Gnome Shell. It uses the Mutter window manager. There is also a fall back mode for Gnome shell for when the Mutter window manager cannot be run. It is called Gnome Panel. 

Note this quote:

> The version of GNOME Panel available in the repository for Ubuntu 12.04 is a modified version of Fallback Mode with the addition of a custom theme and ports of Ubuntu's own Indicators from their old GNOME 2.x desktop

Gnome 3, Gnome Shell and Gnome Panel are the responsibility of the Gnome organization and not Ubuntu. So, the real question is this: For how long will Ubuntu use resources to make a user interface that they have rejected compatible with Ubuntu?

If you want stability then use 12.04 for 12.10 is still being developed. For machines that cannot run Ubuntu Unity 3D then use Unity 2D or install Xubuntu or Lubuntu.

They look more like what has been called Gnome classic. But there is always the issue that the developers have their own ideas about what they want to do and those ideas may not fit what you want.

You can of course install on to 12.04 Gnome shell and its fall back mode because 12.04 is already based upon Gnome 3 desktop environment.

Regards.

---

### Post by VanillaMozilla on 2012-05-23
Thanks very much for that detailed explanation, grahammechanical.  I was not aware of some of the details.  In particular, I was not aware of the Ubuntu modifications of the Gnome panel.

---

### Post by nll on 2012-05-23
Surely if (when?) the gnome devs decide to stop maintaining gnome-panel there will be someone stepping in for the job. Maybe by then the very Mate and Cinnamon folks will realize they are wasting their time because if one wants a Gnome2 experience what they need is gnome-panel, not buggy forks.

I don't think there's any reason to worry about gnome-panel going away.

---

### Post by jbicha on 2012-05-23
Hi, I help maintain gnome-panel in Ubuntu. gnome-panel will continue to be in GNOME (although probably not in "core") as long as it continues to work, and as long as it continues to work it will continue to be available in Debian & Ubuntu. There are no plans to remove gnome-panel from the Ubuntu repositories.

> **grahammechanical said:**
> 
Gnome 3, Gnome Shell and Gnome Panel are the responsibility of the Gnome organization and not Ubuntu. So, the real question is this: For how long will Ubuntu use resources to make a user interface that they have rejected compatible with Ubuntu?


gnome-panel is in universe and is community maintained in Ubuntu.  Canonical the company is not really spending resources on GNOME Classic, but GNOME Classic doesn't need Canonical resources either except for the minimal  costs of storing a few extra packages in the repositories and pushing updates for those packages. Universe packages like GNOME Classic add value to Ubuntu and almost everyone uses at least some stuff from universe.

> **Danillo_Alvarenga said:**
> Surely if (when?) the gnome devs  decide to stop maintaining gnome-panel there will be someone stepping in  for the job. Maybe by then the very Mate and Cinnamon folks will  realize they are wasting their time because if one wants a Gnome2  experience what they need is gnome-panel, not buggy forks.

I don't think there's any reason to worry about gnome-panel going away.

I tried telling people last fall that Mate was the wrong decision. I believe the gnome-panel maintainer would be happy to turn over maintainership to one or more competent developers. It may also be possible to revert some of the UI changes made in version 3.0 since with llvmpipe being adopted by distros later this year, there's no longer a need for gnome-panel to be GNOME Shell's fallback.

As far as Cinnamon goes, I think it would be best if it were handled as a GNOME Shell extension.

---

### Post by VanillaMozilla on 2012-05-24
Thanks.  If I understood what you said, this is good news.

And while you're here, as an off-the-wall, partly off-subject question, do you know where the top-level menus (Applications Places) are defined?  There's some Gnome documentation on definition files, but anything I could find seems to be out of date, i.e., not working any more.

---

### Post by ELD on 2012-05-24
Not even sure if this topic is anymore fit for the QQ forum?
 
I don't see why "MATE" is a wrong decision, again it's what the GPL and open source is there for - people who want to keep things alive. Just because it is a fork doesn't mean it's any less stable than gnome 2 was, a large part of what MATE is all about is fixing bugs...
 
Then again once Unity doesn't need 3D and runs the exact same on non-accelerated tech then it's win win because I personally am loving it nowadays.

---

### Post by pressureman on 2012-05-24
> **jbicha said:**
> I tried telling people last fall that Mate was the wrong decision. I believe the gnome-panel maintainer would be happy to turn over maintainership to one or more competent developers. It may also be possible to revert some of the UI changes made in version 3.0 since with llvmpipe being adopted by distros later this year, there's no longer a need for gnome-panel to be GNOME Shell's fallback.

I agree that MATE is largely a waste of time/effort. GTK+ 2.x is obsolete, and apps are slowly migrating to GTK+ 3. Continuing development on a DE that will eventually be unsupported by apps is futile. If the MATE developers go through with their plan to port it to GTK+ 3, they will have invented.... GNOME fallback session.

> **jbicha said:**
> As far as Cinnamon goes, I think it would be best if it were handled as a GNOME Shell extension.

Didn't Cinnamon essentially start life as the Mint GNOME Shell Extensions anyway? It's a pity that it did't continue down that path.

---

### Post by jbicha on 2012-05-24
> **pressureman said:**
> Didn't Cinnamon essentially start life as the Mint GNOME Shell Extensions anyway? It's a pity that it did't continue down that path.

Yes, but I guess GNOME Shell/Mutter wasn't flexible enough for their extensive changes, so instead of patching GNOME Shell and trying to get that patch into GNOME, they are trying to maintain their own version of GNOME Shell & Mutter which is actually a lot more work. Also, every major distro has GNOME Shell (& access to extensions) in their repositories, but only a few have Cinnamon.

It's similar to what I meant when I said Mate was the wrong decision. Instead of improving gnome-panel 3 (which has a number of improvements over gnome-panel 2) and porting a few applets over to the newer API, one guy decided that he would attempt to maintain all of the pieces of GNOME 2 in his free time! It should be even more obvious now that Mate should be dumped since gnome-panel needs a maintainer and is still in every single major distro.

---

### Post by VanillaMozilla on 2012-05-24
> **ELD said:**
> Not even sure if this topic is anymore fit for the QQ forum?
Thanks.  Actually, this thread is about fallback mode and its continued support.

---

### Post by xebian on 2012-05-24
> **jbicha said:**
> Yes, but I guess GNOME Shell/Mutter wasn't flexible enough for their extensive changes, so instead of patching GNOME Shell and trying to get that patch into GNOME, they are trying to maintain their own version of GNOME Shell & Mutter which is actually a lot more work. Also, every major distro has GNOME Shell (& access to extensions) in their repositories, but only a few have Cinnamon.

It's similar to what I meant when I said Mate was the wrong decision. Instead of improving gnome-panel 3 (which has a number of improvements over gnome-panel 2) and porting a few applets over to the newer API, one guy decided that he would attempt to maintain all of the pieces of GNOME 2 in his free time! It should be even more obvious now that Mate should be dumped since gnome-panel needs a maintainer and is still in every single major distro.

IDK about the details as much as you do but perhaps Gnome doesn't want the patch?  Cinnamon is open source (?) so I don't see why can't Gnome take the patch themselves instead if they want it?

If you put yourself in the other distro's shoes they would think the same way as you do on Unity.  So far only Ubuntu has unity?

---

### Post by kansasnoob on 2012-05-24
> **jbicha said:**
> Yes, but I guess GNOME Shell/Mutter wasn't flexible enough for their extensive changes, so instead of patching GNOME Shell and trying to get that patch into GNOME, they are trying to maintain their own version of GNOME Shell & Mutter which is actually a lot more work. Also, every major distro has GNOME Shell (& access to extensions) in their repositories, but only a few have Cinnamon.

It's similar to what I meant when I said Mate was the wrong decision. Instead of improving gnome-panel 3 (which has a number of improvements over gnome-panel 2) and porting a few applets over to the newer API, one guy decided that he would attempt to maintain all of the pieces of GNOME 2 in his free time! It should be even more obvious now that Mate should be dumped since gnome-panel needs a maintainer and is still in every single major distro.

I agree with everything you're saying but beyond 'gnome-panel' (aka: Gnomes fallback session) I'm particularly curious about the future of Metacity.

I'm not at all impressed with Mutter, although the name Clutter is appropriate IMHO, Metacity + Clutter = Mutter ;)

I just prefer an uncluttered Metacity :lolflag:

I'll grant you that Unity-2D had some lag time opening the dashboard or some apps, but with Ubuntu eliminating Unity-2D, and Gnome going with Mutter I'm curious about the future of dependable, plain-Jane Metacity.

I'll grant you that I could easily live with openbox, but IMHO it's just not as good as Metacity.

---

### Post by nll on 2012-05-24
> **jbicha said:**
> Hi, I help maintain gnome-panel in Ubuntu.

Kudos for your work, Jeremy!

---

### Post by VanillaMozilla on 2012-05-24
> **kansasnoob said:**
> I'm curious about the future of dependable, plain-Jane Metacity.

I'll grant you that I could easily live with openbox, but IMHO it's just not as good as Metacity.
Yes, thank you.  That's what I had in mind when I said "Gnome Classic".  As close as possible to Gnome 2 with Metacity.

Bottom line: if Gnome fallback with Metacity is going to stay around, I guess I'm in, otherwise, not.

Since you mentioned OpenBox, from very limited experience with it, I love it, although to use it I would have to spend time recreating what I already have.  Parts of OpenBox actually run faster from a CD than Ubuntu Precise does from the hard drive.

Thank you all for information on continued support for Gnome Classic.

---

### Post by VinDSL on 2012-05-24
> **VanillaMozilla said:**
> I was hoping not to get into polemics on personal preferences and usefulness, but..
Heh!  Can't speak for others, but...

I H-A-T-E it when things "just work".  And, I L-O-V-E Ubuntu dev releases because of the breakage, not despite it.  LoL!  :D

We just happen to be in that sweet spot, right now -- pre-alpha -- the calm before the storm -- and the threads reflect that.

Put another way, I judge that ppl are bored.  That's all.

Once alpha 1 hits the repos, the +1 Forum will become less pedantic! ;)

---

### Post by VanillaMozilla on 2012-05-24
Thanks for your humor, Vin.  I edited out some of the opinions.

But I have to say I'm not bored here because there's plenty that's broken.  :)

P.S. I edited out the pithier comments.

---

### Post by cariboo on 2012-05-24
Removed double post

---

### Post by BigCityCat on 2012-05-24
You should try Kubuntu it's very stable and much better.

---

### Post by MadmanRB on 2012-05-24
Or xubuntu as XFCE is very much like the old Gnome

---

### Post by jerrylamos on 2012-05-24
I run -2D on a couple latest pc's, Lubuntu on a couple older, and 10.04 LTS on one notebook - it's plenty fast enough for -2D but Precise/Quetzal don't support its wireless.  Connects, gets started, then the ubuntu kernel decides to disconnect.  The launcpad bug is un-answered. 

BTW, 10.04 on the notebook boots way faster than -2D or -3D on my fast tower.  Testing I do a lot of installs and boots.

Jerry

---

### Post by kansasnoob on 2012-05-25
> **VanillaMozilla said:**
> Yes, thank you.  That's what I had in mind when I said "Gnome Classic".  As close as possible to Gnome 2 with Metacity.

Bottom line: [B]if Gnome fallback with Metacity is going to stay around, I guess I'm in, otherwise, not.
[/B]
Since you mentioned OpenBox, from very limited experience with it, I love it, although to use it I would have to spend time recreating what I already have.  Parts of OpenBox actually run faster from a CD than Ubuntu Precise does from the hard drive.

Thank you all for information on continued support for Gnome Classic.

I'm not too worried since Precise is a five year LTS. I only have one minor bug in Precise that I'm sure will be fixed by 12.04.1 :)

It's gonna' be awesome to monitor the upcoming changes.

---

### Post by VMC on 2012-05-25
I just tried OpenBox. It works much faster than Unity and without the focus delay that I experience with nvidia drivers installed, but kept crashing. I just wanted to test another windows manager.
Not sure about this statement thought:

> Openbox is a lightweight window manager using
freedesktop standards. It can be used either as a
**replacement** for the default Gnome window manager **
Metacity ** **or as a standalone** desktop environment.


Does that mean I can remove Gnome?

---

### Post by zika on 2012-05-25
> **VMC said:**
> I just tried OpenBox. It works much faster than Unity and without the focus delay that I experience with nvidia drivers installed, but kept crashing. I just wanted to test another windows manager.
Not sure about this statement thought:
Does that mean I can remove Gnome?I'm using OB from .Xsession (using startx) most of the time... Question You've posed is a bit to much general... There are some apps from Gnome that You might (and will) need... Only if You are in dire need of disk space You should consider that... In my opinion. Using OB &#8222;directly&#8220; You do not load Gnome components and that's it...

---

### Post by forcecore on 2012-06-03
+1 from me too, i tried use Unity but still falled back to gnome-session-fallback, so for me Gnome panel is fastest and best usability. 

This opening bug needs to be fixed when installing panel:
[http://ubuntuforums.org/showthread.php?t=1987735](http://ubuntuforums.org/showthread.php?t=1987735)

/usr/share/applications/nautilus.desktop
/usr/share/applications/eog.desktop
StartupNotify=false
.... and others .desktop too that may cause disturbing "opening" anomaly.

---

### Post by ventrical on 2012-08-06
fvwm-crystal DE is still in the universe repos for quantal. It's not the best but it works on slower machines.

---

### Post by kansasnoob on 2012-08-06
> **forcecore said:**
> +1 from me too, i tried use Unity but still falled back to gnome-session-fallback, so for me Gnome panel is fastest and best usability. 

This opening bug needs to be fixed when installing panel:
[http://ubuntuforums.org/showthread.php?t=1987735](http://ubuntuforums.org/showthread.php?t=1987735)

/usr/share/applications/nautilus.desktop
/usr/share/applications/eog.desktop
StartupNotify=false
.... and others .desktop too that may cause disturbing "opening" anomaly.

I really don't see why the "opening" thingy bothers people. It perfectly coincides with the mouse cursor turning from a whirling thing-a-ma-bob back to a pointer.

It's just a progress indicator :)

---

### Post by guimaster on 2012-08-09
I'm hoping and assuming that at some point - If Ubuntu drops "Classic" - that someone will create an Ubuntu based distro with Classic as the default DE. That'd be sweet. Gubuntu with Classic, not with Gnome Shell.

Also, is there an official webpage for the Gnome Classic project? Do they take donations? Because throwing some money their way may help keep it going.

---

### Post by Mr. Picklesworth on 2012-08-09
> **guimaster said:**
> I'm hoping and assuming that at some point - If Ubuntu drops "Classic" - that someone will create an Ubuntu based distro with Classic as the default DE. That'd be sweet. Gubuntu with Classic, not with Gnome Shell.

Also, is there an official webpage for the Gnome Classic project? Do they take donations? Because throwing some money their way may help keep it going.

GNOME Classic is all the current stuff with GNOME Panel + Metacity instead of Unity or GNOME Shell. GNOME Panel and Metacity are still being happily maintained at [gnome.org]("http://www.gnome.org/"). So, there shouldn't be much to worry about here, as long as the project has the resources. You might want to [adopt a hacker]("http://www.gnome.org/friends/") if you feel that a particular person is instrumental here.

---

