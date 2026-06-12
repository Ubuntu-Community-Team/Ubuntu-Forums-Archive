---
title: "A Gnome Fork - Mate Desktop Environment"
date: 2011-07-11
forum: The Cafe
---

### Post by neu5eeCh on 2011-07-11
I **did** try to see if this info has already been posted.

[http://matsusoft.com.ar/redmine/projects/mate](http://matsusoft.com.ar/redmine/projects/mate)

Looks like at least one individual (?) is creating a fork of Gnome, called Mate Desktop Environment. I'm not endorsing or promoting, just FYI. (Others have asked if there were any forks of gnome.) Gnome2 is still widely available, but will not always remain so.

---

### Post by 3Miro on 2011-07-11
Metacity and Gnome-panel are still under development and included in default Gnome 3. They are available (not by default) for 11.10.

I don't see the point of such project. They should just join Gnome 3 and work with them to keep Metacity and Gnome-panel as viable options.

---

### Post by neu5eeCh on 2011-07-11
My understanding is that Gnome3 does **not** intend to keep Gnome panel alive and is not interested in contributions to that end. I could be wrong... (?)

---

### Post by lucazade on 2011-07-11
> **VTPoet said:**
> My understanding is that Gnome3 does **not** intend to keep Gnome panel alive and is not interested in contributions to that end. I could be wrong... (?)

They need to keep gnomepanel 3 alive and develeloped because it is the only fallback session available for graphic cards without 3D extensions (vesa and fbdev)

---

### Post by neu5eeCh on 2011-07-11
> **lucazade said:**
> They need to keep gnomepanel 3 alive and develeloped because it is the only fallback session available for graphic cards without 3D extensions (vesa and fbdev)

Since I've never used Gnome3 in fallback mode, I have no idea what the difference between that and Gnome2 would be. Why would someone bother forking Gnome2, and why all the calls for a fork, if Gnome3 in fallback mode is little different (?) than Gnome2?

---

### Post by lucazade on 2011-07-11
> **VTPoet said:**
> Since I've never used Gnome3 in fallback mode, I have no idea what the difference between that and Gnome2 would be. Why would someone bother forking Gnome2, and why all the calls for a fork, if Gnome3 in fallback mode is little different (?) than Gnome2?

I don't know why a fork of gnome2, I don't get the reasons as well. 

Gnome fallback session is a port of old gnome-panel with a part of its applets, the classical main-menu for apps and metacity (this is still gtk2)
So the result, when it will be stable, should be the same of gnome2.
My question instead is why develop gnome-shell without thinking directly to both 2D/3D support from the beginning, avoiding two completely different sessions?
Unity at least provides the same ui for both situations.

---

### Post by BigCat4 on 2011-07-11
Maybe I am confused but is not Mint using/promoting/contributing the Gnome 2.xxx desktop?

---

### Post by el_koraco on 2011-07-11
> **VTPoet said:**
> My understanding is that Gnome3 does **not** intend to keep Gnome panel alive and is not interested in contributions to that end. I could be wrong... (?)

That was the original idea, but they've changed their minds in the meantime. Too many complaints, and no way to deal with insufficient hw reqs.

---

### Post by 3Miro on 2011-07-11
> **el_koraco said:**
> That was the original idea, but they've changed their minds in the meantime. Too many complaints, and no way to deal with insufficient hw reqs.

+1. That was my information. It seems the panel is still under development, a lot of code has been cleaned/redone. I am pretty sure the panel is GTK3. Metacity is probably still GTK2.

Natty calls the package "gnome-fallback-session", but the GDM menu calls it "Gnome Classic (No Effects)". I think Gnome-classic would be around as part of Gnome 3 at least for the foreseeable future.

---

### Post by Dry Lips on 2011-07-11
I've tried the fallback mode, and it seems just like Gnome2
with *lots* of options missing. But from what I hear it'll
eventually come closer to the functionality of gnome2.

We'll get there!

---

### Post by 3Miro on 2011-07-11
> **Dry Lips said:**
> I've tried the fallback mode, and it seems just like Gnome2
with *lots* of options missing. But from what I hear it'll
eventually come closer to the functionality of gnome2.

We'll get there!

11.10 is still in early Alpha. Gnome Classic and Gnome-shell are there, but they don't work. It will take time (obviously), but they will be available at final release.

---

### Post by Dry Lips on 2011-07-11
> **3Miro said:**
> 11.10 is still in early Alpha. Gnome Classic and Gnome-shell are there, but they don't work. It will take time (obviously), but they will be available at final release.

Actually I tried the fallback mode in Fedora 15... I'll wait with Oneric until
the final release.

---

### Post by Bandit on 2011-07-11
There seems to be to many hands in the cookie jar in regards to Gnome at this point in time. :(

---

### Post by MrNatewood on 2011-07-11
> **BigCat4 said:**
> Maybe I am confused but is not Mint using/promoting/contributing the Gnome 2.xxx desktop?

The latest Mint 11 is using gnome2. This is to my understanding mostly because Ubuntu has stayed with gnome2 for 11.04. I reckon that Mint 12 will use gnome3, only without the gnome-shell and provide an experience similar to gnome2(This is what they said they would do for Mint 11 but couldn't, again to my understanding, because the Ubuntu base stayed with gtk2/gnome2, this will change with 11.10).

---

### Post by neu5eeCh on 2011-07-11
> **Dry Lips said:**
> I've tried the fallback mode, and it seems just like Gnome2
with *lots* of options missing. But from what I hear it'll
eventually come closer to the functionality of gnome2.

We'll get there!

So... Gnome is now creating two parallel DE's? That says something. Not sure what, but something.

Are there some links that discuss the development of this "fallback" mode, or "Gnome Classic"? Reminds of Coka-Cola. First they introduced their new flavor. They announced that the old flavor was dead. The new flavor flopped. There was an outcry. Coke relented. They kept the new flavor but reintroduced the old, calling it Coke Classic. Some called it brilliant marketing, others called it a fiasco. Is the Gnome desktop a repeat?

Well... here's to Gnome Classic! I guess...

---

### Post by CraigPaleo on 2011-07-11
There's a blog post by one of the devs. I haven't checked to see if there's anything more recent. [Long Live Gnome Panel]("http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel!")

---

### Post by 3Miro on 2011-07-11
> **VTPoet said:**
> So... Gnome is now creating two parallel DE's? That says something. Not sure what, but something.

Are there some links that discuss the development of this "fallback" mode, or "Gnome Classic"? Reminds of Coka-Cola. First they introduced their new flavor. They announced that the old flavor was dead. The new flavor flopped. There was an outcry. Coke relented. They kept the new flavor but reintroduced the old, calling it Coke Classic. Some called it brilliant marketing, others called it a fiasco. Is the Gnome desktop a repeat?

Well... here's to Gnome Classic! I guess...

Not so much two different DE as two different UI. Only Metacity + Panel vs Gnome-shell is different, the rest is the same (gconf, nautilus ...)

Good point for the Coke, but I am wondering if Gnome devs actually anticipated that. I am guessing that they did not.

I think what is happening is that people are getting overly existed about phones and tablets and the new shiny interfaces. Both Unity and Gnome-shell seem to be a way of porting those to the Desktop, however, desktops are very different. For the mouse + keyboard combo of controls, the classic interface of panels and windows is the best you can get (Gnome 2, KDE, XFCE, LXDE). So I think Gnome devs realized that and hence decided to keep both the Classic Desktop UI and the new Tablet UI.

---

### Post by tobydeemer on 2011-08-18
> **3Miro said:**
> I think what is happening is that people are getting overly existed about phones and tablets and the new shiny interfaces. Both Unity and Gnome-shell seem to be a way of porting those to the Desktop, however, desktops are very different. For the mouse + keyboard combo of controls, the classic interface of panels and windows is the best you can get (Gnome 2, KDE, XFCE, LXDE). So I think Gnome devs realized that and hence decided to keep both the Classic Desktop UI and the new Tablet UI.

I heartily agree- the tablet / post-pc-era / phone UI 800lb gorilla right now is "infecting" other areas.

Personally, I have really enjoyed the function one can get from gnome-panel, its applets, nautilus, and a well configured desktop. But it seems like the developers are insulated from their audience, and the audience in turn is definitely not the easiest to deal with. So this has led to our current disconnect.

And what's happened as a result is that we're losing the functionality, reconfigurability, and work flow modification ability that we've come to depend on. It's being replaced with what "seemed like a good idea at the time" but without more thorough consideration and authentic usage studies. 

Forgive me for possibly being harsh, but- graphic designers feeding developers do not UI experts make. I do come from an industrial and graphic design background, and I can tell you- human interaction intuition is an incredibly hard thing to capture well on a broadly applicable scale; meaning, it's friggin' hard to make something that flows for a large percentage of the audience.

So ultimately, I think we're seeing the pursuit of pretty phone UIs in the search for the "next big thing" in desktop interaction. Meanwhile, us sysadmins are now struggling to get work done........

---

### Post by DangerOnTheRanger on 2011-08-18
> **3Miro said:**
> Not so much two different DE as two different UI. Only Metacity + Panel vs Gnome-shell is different, the rest is the same (gconf, nautilus ...)

Good point for the Coke, but I am wondering if Gnome devs actually anticipated that. I am guessing that they did not.

I think what is happening is that people are getting overly existed about phones and tablets and the new shiny interfaces. Both Unity and Gnome-shell seem to be a way of porting those to the Desktop, however, desktops are very different. For the mouse + keyboard combo of controls, the classic interface of panels and windows is the best you can get (Gnome 2, KDE, XFCE, LXDE). So I think Gnome devs realized that and hence decided to keep both the Classic Desktop UI and the new Tablet UI.

This. Just this.
GNOME and Unity are both acting like PCs suddenly have multitouch-enabled touchscreens. How in the world can a menu at the top of the screen (or bottom, in KDE) be more "complex" than implicit keyboard shortcuts!? On a touchscreen-less device, no less?

> **CraigPaleo said:**
> There's a blog post by one of the devs. I  haven't checked to see if there's anything more recent. [Long Live Gnome Panel]("http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel%21")

Anyone else notice the username of that live session? ;)

---

### Post by simpleblue on 2011-08-18
The trend:

Home computer -> Laptop -> Tablet


I think many of us are living in year 2003. If you like Gnome 2 then you can download it, but spending time developing it.. well, that's your call... As far as I can see the trend is that people are transitioning to laptops and Tabs. They want slick portable devices, not clunky cumbersome tower computers. Gnome 3 looks like it would be a great UI for a Tablet. Imagine running all your favorite Linux apps on a shiny Samsung Tablet. I think that would be awesome.

Even KDE is focusing on the touch enabled UI as they have announced their plans for KDE 5. People will complain, people will hate it, but in a few years most people will love it and wonder why they didn't embrace it earlier. Linux on tablets will rock. Might as well stay up to date so we can compete.

Also, please try to think of new users. They don't want a UI that looks as aged as Windows XP. They want a simple, streamlined, and polished interface that's easy to use, sexy, and fun. I think Gnome 3 gives that experience.

I read a HUGE article from a Gnome Developer and he has some great points. Keep in mind that GS has only be out for about 6 months. Gnome has been around for about 9 years.

GNOME-Designer Jon McCann about the future of GNOME3:
[http://derstandard.at/1313024283546/Interview-GNOME-Designer-Jon-McCann-about-the-future-of-GNOME3](http://derstandard.at/1313024283546/Interview-GNOME-Designer-Jon-McCann-about-the-future-of-GNOME3)

It like it's a baby and we're all yelling at it because it's not doing all the cool things we want it to yet. Instead of helping it we decide to continue to yell at it. Does it really help to bicker and complain so much? Save your energy. Gnome and Linux are on your side.

---

### Post by wolfgar on 2011-08-19
> **3Miro said:**
> Metacity and Gnome-panel are still under development and included in default Gnome 3. They are available (not by default) for 11.10.

I don't see the point of such project. They should just join Gnome 3 and work with them to keep Metacity and Gnome-panel as viable options.


Linus Torvalds, Linux’s creator, really, really dislikes the GNOME 3 Linux desktop. He would like to see a GNOME 2 fork.  Linus Torvalds Drops Gnome 3 for Xfce, Calls It 'Crazy' 

[http://www.zdnet.com/blog/open-source/linus-torvalds-would-like-to-see-a-gnome-fork/9347](http://www.zdnet.com/blog/open-source/linus-torvalds-would-like-to-see-a-gnome-fork/9347)      

[http://news.softpedia.com/news/Linus-Torvalds-Drops-Gnome-3-for-Xfce-Calls-It-Crazy-215074.shtml](http://news.softpedia.com/news/Linus-Torvalds-Drops-Gnome-3-for-Xfce-Calls-It-Crazy-215074.shtml)

Too many other links to post here:

If the creator of Linux thinks it's crazy than a GNOME 2 fork is necessary.

---

### Post by cariboo on 2011-08-19
> **wolfgar said:**
> Linus Torvalds, Linux’s creator, really, really dislikes the GNOME 3 Linux desktop. He would like to see a GNOME 2 fork.  Linus Torvalds Drops Gnome 3 for Xfce, Calls It 'Crazy' 

[http://www.zdnet.com/blog/open-source/linus-torvalds-would-like-to-see-a-gnome-fork/9347](http://www.zdnet.com/blog/open-source/linus-torvalds-would-like-to-see-a-gnome-fork/9347)      

[http://news.softpedia.com/news/Linus-Torvalds-Drops-Gnome-3-for-Xfce-Calls-It-Crazy-215074.shtml](http://news.softpedia.com/news/Linus-Torvalds-Drops-Gnome-3-for-Xfce-Calls-It-Crazy-215074.shtml)

Too many other links to post here:

If the creator of Linux thinks it's crazy than a GNOME 2 fork is necessary.

Linus has said bad things about every desktop environment at one time or another. He isn't a god, he puts his pants on one leg at a time just like the rest of us. I suppose if he said he was going to quit development on the kernel tomorrow, and started using OSX, we should all do the same thing. :)

---

### Post by Perfect Storm on 2011-08-19
Big deal what Linus says. He have every rights to his opinion as everybody else, and he have his own taste and idea like all of us. Just because he likes blueberries doesn't mean I have to like blueberries. If he dislike strawberries doesn't mean I have to dislike strawberries.

I can think and make my own decisions, thank you.

---

### Post by Erik1984 on 2011-08-19
> **cariboo907 said:**
> Linus has said bad things about every desktop environment at one time or another. He isn't a god, he puts his pants on one leg at a time just like the rest of us. I suppose if he said he was going to quit development on the kernel tomorrow, and started using OSX, we should all do the same thing. :)

Exactly. As a desktop user Linus' opinion is just as special as any other individual using a Linux distro. He is a kernel specialist, not a UI specialist.

---

### Post by wolfgar on 2011-08-19
You are all correct.  Everyone to there on taste.  However, if I want a cell phone desktop interface, then I will buy a cell phone.  Mini touch screen windows on the side of my desktop is a a bit dysfunctional for us old timers.  

Just don't take away the choice of Gnome 2 or the functions of Gnome 2!

---

### Post by cariboo on 2011-08-19
> **wolfgar said:**
> You are all correct.  Everyone to there on taste.  However, if I want a cell phone desktop interface, then I will buy a cell phone.  Mini touch screen windows on the side of my desktop is a a bit dysfunctional for us old timers.  

Just don't take away the choice of Gnome 2 or the functions of Gnome 2!

Nobody is taking your choice away, you can still use the gnome 2 desktop, just don't expect it to be available on newer releases. Development has stopped, and it seems the subject of this thread has given up as well, as the web page is no longer available, and the developer hasn't posted in forum since mid July.

---

### Post by Dry Lips on 2011-08-19
> **cariboo907 said:**
> Nobody is taking your choice away, you can still use the gnome 2 desktop, just don't expect it to be available on newer releases. Development has stopped, and it seems the subject of this thread has given up as well, as the web page is no longer available, and the developer hasn't posted in forum since mid July.

From what I understand the fallback mode of Gnome 3
will eventually get the functionality of Gnome2...

In that case, we who aren't comfortable with Unity have
no reason to complain... 8)

---

### Post by cariboo on 2011-08-19
Here's a screenshot of my desktop running gnome-session-fallback. I'm running Oneiric, with the choice of Unity, Unity-2D, Gnome-shell and Gnome classic, all selectable from the login screen.

---

### Post by neu5eeCh on 2011-08-19
> **cariboo907 said:**
> Here's a screenshot of my desktop running gnome-session-fallback. I'm running Oneiric, with the choice of Unity, Unity-2D, Gnome-shell and Gnome classic, all selectable from the login screen.

So Gnome Classic is GTK3, not Gnome2? Just to be ultra clear...

---

### Post by danyc05 on 2011-08-19
with this whole movement that gnome is doing.. i have a feeling that xfce and kde will be growing in the next few months/years..

---

### Post by Erik1984 on 2011-08-19
> **danyc05 said:**
> with this whole movement that gnome is doing.. i have a feeling that xfce and kde will be growing in the next few months/years..

That's the impression one gets from reading the forums yes. Especially KDE seems to get pretty much positive attention since KDE 4.6 en the recent release of 4.7. I've contributed to that too. However I switched to 11.04 with Unity from Kubuntu recently because I got homesick. So a. not all switches are definitive and b. people switching to another distro are often more vocal about that than those who just stick with Ubuntu.

---

### Post by cariboo on 2011-08-19
> **VTPoet said:**
> So Gnome Classic is GTK3, not Gnome2? Just to be ultra clear...

Yes gnome-classic on Oneiric is based on gtk3. There a few differences, to add applets to the top panel you have to Alt-right-click, and there aren't as many applets yet, but otherwise it seems to work the same.

---

### Post by danyc05 on 2011-08-19
> **Euroman said:**
> That's the impression one gets from reading the forums yes. Especially KDE seems to get pretty much positive attention since KDE 4.6 en the recent release of 4.7. I've contributed to that too. However I switched to 11.04 with Unity from Kubuntu recently because I got homesick. So a. not all switches are definitive and b. people switching to another distro are often more vocal about that than those who just stick with Ubuntu.

Yea i know what you mean and I do the same exact thing.. Ive tried alot of distros but no matter what i do or what i say about Ubuntu, I always end up coming back just to see whats going on with it.

---

### Post by neu5eeCh on 2011-08-19
> **cariboo907 said:**
> Yes gnome-classic on Oneiric is based on gtk3. There a few differences, to add applets to the top panel you have to Alt-right-click, and there aren't as many applets yet, but otherwise it seems to work the same.

How resource intensive is Gnome Classic? I've gotten used to XFCE and its speed, but would consider moving back to Gnome Classic just because I miss some of the themes available to Gnome (assuming they would work in Gnome Classic).

---

### Post by wolfgar on 2011-08-19
Why would I want to replace this?

---

### Post by cariboo on 2011-08-19
> **wolfgar said:**
> Why would I want to replace this?

Why wouldn't you:):)

Like I said in a previous post not all the applets have been ported to gtk3, and there is a new themeing engine, so there aren't many themes yet, but give it time. By the time support ends for 10.04, there should many more applets and themes available.

---

### Post by wolfgar on 2011-08-19
> **cariboo907 said:**
> Why wouldn't you:):)

Linux has always been about freedom of choice, not lack of choice. Ubuntu will learn that very important lesson soon. If I wanted touchscreen mini windows, I would get a bigger cell phone, or buy a square monitor.  :p

Nothing else to say, just compare. :p

---

### Post by cariboo on 2011-08-19
Sigh, Unity and gnome-shell were never designed for a touch screen of any sort, there have been reports in the mega thread, that they are actually pretty horrible to use with a touch screen. As far as customization goes I can't speak for gnome-shell, as I don't use it enough, but Unity is getting much more customizable as time goes on. 

I don't suppose you were around when gnome 2 was released, but there were many of the same complaints, I found it so horrible, I changed to KDE and didn't go back to gnome until I started using Ubuntu in 2006.

---

### Post by Perfect Storm on 2011-08-20
> **danyc05 said:**
> with this whole movement that gnome is doing.. i have a feeling that xfce and kde will be growing in the next few months/years..

That was the exactly the same respond people said when KDE moved from 3 to 4. ;)

---

### Post by nynoah on 2011-08-20
I am sorry to the Gnome3 Unity lovers.  But if ubuntu does away with Gnome 2 in the future, then I will have to move to KDE or Xfce or off Ubuntu entirely.  This new UI is horrible.  Its even dumber than the first few tries of KDE4 compared to KDE3.5.  In both instances, the programmers have gone for shiny over functionality.  Shiny pretty is nice, but if I lose function what good is it?

---

### Post by walt.smith1960 on 2011-08-20
> **wolfgar said:**
> **Linux has always been about freedom of choice**, not lack of choice. Ubuntu will learn that very important lesson soon. If I wanted touchscreen mini windows, I would get a bigger cell phone, or buy a square monitor.  :p

Nothing else to say, just compare. :p

And there are more than a few people that will pick the screen on the left.  They just don't hang out on forums, they have other more pressing things to do. Your screen shots are very impressive but not to everyone's taste.

---

### Post by BigSilly on 2011-08-20
> **nynoah said:**
> I am sorry to the Gnome3 Unity lovers.  But if ubuntu does away with Gnome 2 in the future, then I will have to move to KDE or Xfce or off Ubuntu entirely.

Oh well I'm sure we'll get by somehow.

> **walt.smith1960 said:**
> And there are more than a few people that will pick the screen on the left.  They just don't hang out on forums, they have other more pressing things to do.

Yup. I know which one I'd pick myself. Unity is really coming into it's own with Oneiric.

---

### Post by cariboo on 2011-08-20
> **nynoah said:**
> I am sorry to the Gnome3 Unity lovers.  But if ubuntu does away with Gnome 2 in the future, then I will have to move to KDE or Xfce or off Ubuntu entirely.  This new UI is horrible.  Its even dumber than the first few tries of KDE4 compared to KDE3.5.  In both instances, the programmers have gone for shiny over functionality.  Shiny pretty is nice, but if I lose function what good is it?

There is no if, about it. Gnome 2 isn't being developed or maintained anymore. You don't have to tell us that you won't be using Unity or Gnome-shell, just do it, use whatever works best for you. We won't hold it against you.

---

### Post by nynoah on 2011-08-20
> **cariboo907 said:**
> There is no if, about it. Gnome 2 isn't being developed or maintained anymore. You don't have to tell us that you won't be using Unity or Gnome-shell, just do it, use whatever works best for you. We won't hold it against you.

The point I am trying to make is Ubuntu and Gnome are shooting themselves in the foot.  They are doing the same stupid thing that Coke did with "new" coke.  Its all flash and less functionality.  We are now going to go through 2 years of bugs and "fixes" to get Ubuntu back to the functionality of Gnome 2.  Its a step backwards in the name of flashy shiny stupid.

---

### Post by Famicube64 on 2011-08-20
> **wolfgar said:**
> Linux has always been about freedom of choice, not lack of choice. Ubuntu will learn that very important lesson soon. If I wanted touchscreen mini windows, I would get a bigger cell phone, or buy a square monitor.  :p

Nothing else to say, just compare. :p
I threw up in my mouth after looking at that desktop.

---

### Post by cariboo on 2011-08-20
> **nynoah said:**
> The point I am trying to make is Ubuntu and Gnome are shooting themselves in the foot.  They are doing the same stupid thing that Coke did with "new" coke.  Its all flash and less functionality.  We are now going to go through 2 years of bugs and "fixes" to get Ubuntu back to the functionality of Gnome 2.  Its a step backwards in the name of flashy shiny stupid.

You don't have to use Unity or Gnome-shell, there are plenty of other desktop environments you can use instead. 

Have you actually used Unity or Gnome-shell, they are both quite functional in Oneiric. For most people that have used them, they feel that they can get just as much if not more work done, than with the two panel interface.

If you are set on using the two panel interface, there is a new version available in Oneiric. It isn't installed by default, but you can use your favorite installation method to install it, then select from the new login interface.

---

### Post by Tibuda on 2011-08-20
> **wolfgar said:**
> Linux has always been about freedom of choice, not lack of choice. Ubuntu will learn that very important lesson soon. If I wanted touchscreen mini windows, I would get a bigger cell phone, or buy a square monitor.  :p

Nothing else to say, just compare. :p

I dont like Unity, but your unity shot is 10^9999999999 better than the other shots. They hurt my eyes.

It's a matter of opinion, so YMMV.

---

### Post by nynoah on 2011-08-20
> **wolfgar said:**
> Linux has always been about freedom of choice, not lack of choice. Ubuntu will learn that very important lesson soon. If I wanted touchscreen mini windows, I would get a bigger cell phone, or buy a square monitor.  :p

Nothing else to say, just compare. :p

The UE desktop is not for all.  The people who want simplistic will not like it.  It does however have all the best programs out there preinstalled.  Gnome2 under UE is the best top UI in my opinion too.  Saved me a weeks worth of work to make mine similar.  Ultimate Edition OZ team has a Unity version.  But it still makes no sense in the end.  I hope that someone in the Linux world will fork Gnome 2 and keep it going, because Gnome 3 just makes no sense.  I don't want simplistic everything.  I don't want flashy menu systems that in the end function worse.   I want function first and Gnome 2 does that better hands down.  Gnome 3 looks nothing like Gnome 2.  There should be no reason to abandon Gnome 2 either.  I hope that Linus's words will be taken into account and a team will pick up the slack and continue the Gnome 2 interface.  If not, then I am pretty sure most people will switch to something that functions more in the end.  KDE just got its best gift ever, but I would still prefer Gnome 2 over KDE.

---

### Post by walt.smith1960 on 2011-08-21
> **nynoah said:**
> The UE desktop is not for all.  The people who want simplistic will not like it.  It does however have all the best programs out there preinstalled.  Gnome2 under UE is the best top UI in my opinion too.  Saved me a weeks worth of work to make mine similar.  Ultimate Edition OZ team has a Unity version.  But it still makes no sense in the end.  I hope that someone in the Linux world will fork Gnome 2 and keep it going, because Gnome 3 just makes no sense.  I don't want simplistic everything.  I don't want flashy menu systems that in the end function worse.   I want function first and Gnome 2 does that better hands down.  Gnome 3 looks nothing like Gnome 2.  There should be no reason to abandon Gnome 2 either.  I hope that Linus's words will be taken into account and a team will pick up the slack and continue the Gnome 2 interface.  If not, then I am pretty sure most people will switch to something that functions more in the end.  KDE just got its best gift ever, but I would still prefer Gnome 2 over KDE.

Have you installed a recent 11.10 build plus Gnome-Panel?  Applications and Places seem identical.  System entries now being located in two different locations, some under Applications -> other and some under "system settings" under the upper right user-name drop-down.  I don't see much difference between 10.10 classic and 11.10 Classic-no effects.  What IS missing are applets.  GTK2 applets won't work in 11.10, they need to be reworked to function with GTK3.   The basics are in 11.10 classic but not much else.  11.10 Classic or 11.10 Classic-no effects seem pretty functional though.  I'm getting pretty used to Gnome-shell though, I prefer it to Unity for now.

---

### Post by tobydeemer on 2011-08-31
Just curious- how much of Gnome3 and/or Unity are using Mono? (Haven't looked, but thought occurred to me whilst surfing at work. Ssshh.)

---

### Post by cariboo on 2011-08-31
> **tobydeemer said:**
> Just curious- how much of Gnome3 and/or Unity are using Mono? (Haven't looked, but thought occurred to me whilst surfing at work. Ssshh.)

Banshee is the only app installed by default in Oneiric using mono.

---

### Post by evgeny12 on 2011-09-12
The most important feature of Gnome 2 is its greatest choice of themes, styles, programs to fit needs of many people. I think that Gnome 2 in original form is not too much better than KDE or XFCE, but Gnome2+Compiz+(Cairo-Dock, Docky, classical panel)+emerald gives very big freedom to get shiny staff far beyond of Gnome3+whatever without too much downgrading in functionality. I have to switch to Debian Squeeze just to keep Gnome 2 + (all I like) as long as possible without losing any functionality in programs I need, because computer for me is not just for fun, but it is my tool for scientific job. From this point of view Gnome 3 fallback mode is not the option, because I like to customize my Desktop style to whatever I like. Only few small bugs in Gnome2+Compiz+Emerald sometimes bother me. So it is very pity that people have no interest to support this great and highly customizable Gnome2. What about Gnome 3? If developers will save compatibility with Gnome2 and don't lose too much efficiency of Gnome2,  than they will succeed in popularity, but instead of this we have what we have.

---

### Post by Lucradia on 2011-09-12
> **lucazade said:**
> I don't know why a fork of gnome2, I don't get the reasons as well. 

Gnome fallback session is a port of old gnome-panel with a part of its applets, the classical main-menu for apps and metacity (this is still gtk2)
So the result, when it will be stable, should be the same of gnome2.
My question instead is why develop gnome-shell without thinking directly to both 2D/3D support from the beginning, avoiding two completely different sessions?
Unity at least provides the same ui for both situations.

Any option to use fallback by default and use 3D Composition with it?

---

### Post by screaminj3sus on 2011-09-12
> **Lucradia said:**
> Any option to use fallback by default and use 3D Composition with it?

There is an option in the gnome 3 control center to set fallback as default, for compositing you can always use compiz... I am also fairly sure you can just use mutter as well, with mutter --replace. I haven't tried this in a long time though.

---

### Post by earthpigg on 2011-09-12
[https://github.com/Perberos/Mate-Desktop-Environment](https://github.com/Perberos/Mate-Desktop-Environment)

> MATE Desktop Environment, a non-intuitive and unattractive desktop for users, using traditional computing desktop metaphor.

lol

---

### Post by Lucradia on 2011-09-13
> **screaminj3sus said:**
> There is an option in the gnome 3 control center to set fallback as default, for compositing you can always use compiz... I am also fairly sure you can just use mutter as well, with mutter --replace. I haven't tried this in a long time though.

Then there's no reason to fork?

---

### Post by evgeny12 on 2011-09-20
> **screaminj3sus said:**
> There is an option in the gnome 3 control center to set fallback as default, for compositing you can always use compiz... I am also fairly sure you can just use mutter as well, with mutter --replace. I haven't tried this in a long time though.

Hmm, thanks, I did not know that it still can work with Compiz. I even found video about this, so I have to try Gnome3+Default Fallback mode+Compiz+Emerald+Cairo Dock. If it will work fine, well, then it will make me quite happy. But I still curious about some rumors, that Fallback mode will not be supported in future. Is it true?

---

### Post by screaminj3sus on 2011-09-20
> **evgeny12 said:**
> Hmm, thanks, I did not know that it still can work with Compiz. I even found video about this, so I have to try Gnome3+Default Fallback mode+Compiz+Emerald+Cairo Dock. If it will work fine, well, then it will make me quite happy. But I still curious about some rumors, that Fallback mode will not be supported in future. Is it true?

I think those rumors are mostly FUD.

---

### Post by ondrejch on 2011-10-19
> **cariboo907 said:**
> Linus [..] isn't a god

Actually he is, and Gnome3 is crazy. I am keeping my main machine back on Natty because of this disaster until there is a working fork of Gnome2.
The boxes I (foolishly) upgraded to 11.10 switched to xfce4 or e17. I dont really like either but even twm is better than this Gnome3  mess.

---

### Post by ondrejch on 2011-10-19
> **Lucradia said:**
> Then there's no reason to fork?

The "classic" in 11.10  is a pathetic joke, it does not even work with gnome-themes. 
Get the GNome2 back! I am considering switching back to Debian.

---

### Post by kaldor on 2011-10-19
> **ondrejch said:**
> The "classic" in 11.10  is a pathetic joke, it does not even work with gnome-themes. 
Get the GNome2 back! I am considering switching back to Debian.

Debian will be getting GNOME 3 soon as well. Give it time and things will mature.

I recommend you start using GNOME Shell, since overall it's a much nicer and smoother experience ;)

---

### Post by nikko_bosatsu on 2011-10-21
The main reason I use linux because I can customize it the way I like, now I even can't move the darn panel. 
I'm so frustrating which this new UI. If the developer want to adopt the shiny touch interface why don't adopt the way Windows 8 behavior. They give the choice to use the old windows Interface(the one with taskbar and start menu). Also OS X interface not the same as iPad or iPhone (maybe only the Icon is the same). 
And the funny thing I use keyboard much more often. Thank god for the Gnome-do

---

### Post by Seb71 on 2011-11-08
After "upgrading" from 10.04 to 11.10, my biggest complain against Unity and Ubuntu 11.10 is that it turned a functional and usable computer into a 486.

I would keep 10.04 if it was easier to update the software I use to current versions (Firefox, LibreOffice, Thunderbird, printer drivers, etc.). Windows XP approach is better on this matter. I can easily run current software on it 10 years after that OS was launched.

---

### Post by never-never-land on 2011-11-12
Well I saw all the fuss around this issue and thought I'd lay my opinion about it too::popcorn:
FIRST I must say I TOTALLY agree with Linus, and not because who he is but because what he said. I think gnome 3 is definitely a TABLET/SMART-PHONE Intended UI, non of it make sense on a pc desktop, its usability is really really !@#$ and the looks of it is far from enough to compensate for it [NO MINIMIZE BUTTON!!! / SUSPEND instead of SHUTDOWN!!! what on earth are they thinking??? reinventing the Wheel and making it NOT elliptic but square (totally doesn't work)].
SECOND I'd like to say that Unity in my opinion is just a bit better but considering the fact that this is the first UI Ubuntu develops & perhaps they did it because they knew gnome 3 is Drifting off course (meaning they had a very good intention) then it is forgivable though still not usable.
THUS: I"m now using debian with gnome 2 and I really hopes that a gnome fork will be freshening breeze...

ahhh, that was liberating:P

---

### Post by kurt18947 on 2011-11-12
> **never-never-land said:**
> Well I saw all the fuss around this issue and thought I'd lay my opinion about it too::popcorn:
FIRST I must say I TOTALLY agree with Linus, and not because who he is but because what he said. I think gnome 3 is definitely a TABLET/SMART-PHONE Intended UI, non of it make sense on a pc desktop, its usability is really really !@#$ and the looks of it is far from enough to compensate for it **[NO MINIMIZE BUTTON!!! / SUSPEND instead of SHUTDOWN!!!** what on earth are they thinking??? reinventing the Wheel and making it NOT elliptic but square (totally doesn't work)].
SECOND I'd like to say that Unity in my opinion is just a bit better but considering the fact that this is the first UI Ubuntu develops & perhaps they did it because they knew gnome 3 is Drifting off course (meaning they had a very good intention) then it is forgivable though still not usable.
THUS: I"m now using debian with gnome 2 and I really hopes that a gnome fork will be freshening breeze...

ahhh, that was liberating:P

Both easily fixed but those fixes should have been there out-of-the-box.  I've tried all the gnome 3 variants -- gnome classic, gnome classic no-effects, unity, and gnome-shell as well as Lubuntu & Xfce-desktop.  So far, gnome-shell is my default though Xfce-desktop is quite good and Lubuntu is excellent on older/netbook class machines.  I think we'll see many fixes & add-ons for gnome-shell in the near future.  I don't think Unity will see the same efforts.

---

### Post by neu5eeCh on 2011-11-12
Just noticed, this morning, that RC-1 of Mint 12 has been [released at Distrowatch]("http://distrowatch.com/table.php?distribution=mint"). Looks promising. Uses G3 with MGSE and also offers MATE, though CLEM states that MATE is still rough around the edges. I have high hopes for Mint 12; am downloading it now. It may just become my primary distro (next to Xubuntu), since I like neither G3 nor Unity.

---

### Post by Gremlinzzz on 2011-11-12
The first release candidate for Mint 12, an Ubuntu-based distribution with a choice between a highly customised GNOME 3 and MATE (a fork of GNOME 2) desktops, is out and ready for testing: "The team is proud to announce the release of Linux Mint 12 'Lisa' RC. Linux Mint 12 is a new step forward, using new technologies and a brand new desktop, built with GNOME 3 and Mint GNOME Shell Extensions (MGSE). MGSE is a desktop layer on top of GNOME 3 that makes it possible to use GNOME 3 in a traditional way. You can disable all components within MGSE to get a pure GNOME 3 experience, or you can enable all of them to get a GNOME 3 desktop that is similar to what you've been using before. The main features in MGSE are: the bottom panel, the application menu, the window list, a task-centric desktop (i.e. you switch between windows, not applications), visible system tray icons.

Just tried the live cd seems like a pretty nice system,didn't use it long enough to find bugs or all its assets.but going to use it see if its for me
:popcorn:

---

### Post by cwklinuxguy on 2011-11-12
In case anyone finds this interesting, I am currently working on a derivative/fork of Ubuntu 11.10, which I am calling Paradise OS. It will eventually use Mate as it's main DE. For now it is extremely buggy, but the Alpha 1 will be out in the next few days, or sooner (hopefully). More info is [here]("http://paradiseos.wordpress.com").

---

### Post by Gremlinzzz on 2011-11-12
> **Gremlinzzz said:**
> The first release candidate for Mint 12, an Ubuntu-based distribution with a choice between a highly customised GNOME 3 and MATE (a fork of GNOME 2) desktops, is out and ready for testing: "The team is proud to announce the release of Linux Mint 12 'Lisa' RC. Linux Mint 12 is a new step forward, using new technologies and a brand new desktop, built with GNOME 3 and Mint GNOME Shell Extensions (MGSE). MGSE is a desktop layer on top of GNOME 3 that makes it possible to use GNOME 3 in a traditional way. You can disable all components within MGSE to get a pure GNOME 3 experience, or you can enable all of them to get a GNOME 3 desktop that is similar to what you've been using before. The main features in MGSE are: the bottom panel, the application menu, the window list, a task-centric desktop (i.e. you switch between windows, not applications), visible system tray icons.

Just tried the live cd seems like a pretty nice system,didn't use it long enough to find bugs or all its assets.but going to use it see if its for me
:popcorn:
no bugs to report cool system ,i mean the kernel they are using has keep my computer cool.11.10 was making my computer run hot.
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
:popcorn:

---

### Post by intheup on 2011-11-15
Im sorry but I prefer to have my desktop with some icons and the menu bar just like old style, gnome2, xfce, lxde, etc..

The idea in Gnome3 is great... great for an notebook or an netbook.. but not for desktop.

Im waiting for the MATE to be fully ported to Mint so I can stay with mint in my desk but if that becomes a crap de so ill back in debian too.


sorry about my english.

---

### Post by cariboo on 2011-11-16
> **intheup said:**
> Im sorry but I prefer to have my desktop with some icons and the menu bar just like old style, gnome2, xfce, lxde, etc..

The idea in Gnome3 is great... great for an notebook or an netbook.. but not for desktop.

Im waiting for the MATE to be fully ported to Mint so I can stay with mint in my desk but if that becomes a crap de so ill back in debian too.


sorry about my english.

Why wait for something that might never be completed, you can have Gnome 3 with the two panel interface now. Have a look at the Gnome Classic thread in Precise testing and discussion:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

---

### Post by &quot;Lex on 2011-11-17
> **cariboo907 said:**
> Why wait for something that might never be completed, you can have Gnome 3 with the two panel interface now. Have a look at the Gnome Classic thread in Precise testing and discussion:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

Because we like it better<snip> !

---

### Post by neu5eeCh on 2011-11-18
Just noticed at Linux Today that [one can install MATE & Mint's MGSE in Ubuntu]("http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1975-install-linuxmint12-extensio"). Haven't tried it because I'm using Xubuntu 11.04. MATE, however, doesn't look like it's going to fade into the wordwork any time soon. May try it on a separate partition just to see.

---

### Post by l0vot on 2011-11-19
There is a good reason to continu the development of Gnome2x, it is the only desktop environment (out of gnome2,kde,xfc,unity,gnome3,lxde,windows,and apple) that gives me the freedom to change everything to the way I want it, and gives me more choices than any other, and the choices are better than anywhere else.

 I really don't care what the "default setup" of a UI is, i only care about the heavily modified setup i created specifically for my use, and gnome2x will allow me to modify it until it is unrecognizable to anyone who has only used the default configuration of gnome, while i can also do that in KDE, XFC, and LXDE, they don't have the vast amount of choices that Gnome2x has.

When i learn a couple programming languages, i will continue to develop gnome2x myself, or at least help other people who are willing to do it. Gnome2x is too good to just throw away in exchange for a desktop environment that i cant even move/autohide the panels in.

For those of you who happen to like gnome3, that is perfectly fine, as long as gnome2x continues to be developed and available for the people who enjoy using it.



all the panels are on auto-hide, so they take up no space normally, also note that is a screenshot of debian, not LinuxMint (the computer tri-boots, but shares user-accounts), I have the same setup on ubuntu 10.10 (there were some functions missing on ubuntu11 fallback mode, and compiz fusion caused MASSIVE problems,like compiz always does on my computers, so i also disable compiz as well)

---

### Post by cariboo on 2011-11-20
@l0vot, what's your point again? Check the screenshot, this is gnome classic, that took me about 10 minutes to setup. The bottom panel is set to auto hide, and I installed docky.

---

### Post by daniel4m on 2011-11-20
> **cariboo907 said:**
> @l0vot, what's your point again? Check the screenshot, this is gnome classic, that took me about 10 minutes to setup. The bottom panel is set to auto hide, and I installed docky.

What is your point? Gnome fallback is not Gnome 2.x and it never will be. Gnome fallback mode will disappear soon, when the Gnome shell (Gnome 3 in  the future) reaches a better hardware support. Mate desktop will become stable relatively quickly.

---

### Post by Off Topic on 2011-11-21
Two problems.  If I set the panels to autohide when I reboot they disappear completely.  And I hate having icons on the desktop and I cant get rid of the 3 that are there.

---

### Post by sdavmor on 2011-12-21
I Installed MATE yesterday following the latest directions for Ubuntu 11.10.  20 minutes later I had logged back in with my old Gnome2 desktop.  MATE looks to be a very solid fork of Gnome2 for those of us that like it and want to keep using it.  My only gripe would be fonts.  They don't seem to render as crisply as they do when I login with Gnome Classic fallback or Unity.  But I'm sure that will be addressed shortly, and it's a minor issue for me. Well done you chaps who picked up the Gnome2 ball! (applause).

---

### Post by KBD47 on 2011-12-23
> **sdavmor said:**
> I Installed MATE yesterday following the latest directions for Ubuntu 11.10.  20 minutes later I had logged back in with my old Gnome2 desktop.  MATE looks to be a very solid fork of Gnome2 for those of us that like it and want to keep using it.  My only gripe would be fonts.  They don't seem to render as crisply as they do when I login with Gnome Classic fallback or Unity.  But I'm sure that will be addressed shortly, and it's a minor issue for me. Well done you chaps who picked up the Gnome2 ball! (applause).

Had the same problem with the fonts. I'm using MATE on Mint 12. I just right-clicked on the desktop, clicked on change desktop background, and adjusted the font settings to smoothing subpixel (lcd) and hinting to slight. That fixed it for me.
KBD47

---

### Post by masque7 on 2012-02-24
> **KBD47 said:**
> Had the same problem with the fonts. I'm using MATE on Mint 12. I just right-clicked on the desktop, clicked on change desktop background, and adjusted the font settings to smoothing subpixel (lcd) and hinting to slight. That fixed it for me.
KBD47
That's, that also worked for me!

---

