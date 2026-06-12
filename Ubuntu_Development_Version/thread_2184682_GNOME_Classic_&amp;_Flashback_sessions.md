---
title: "GNOME Classic &amp; Flashback sessions"
date: 2013-10-30
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-10-30
This thread is for the discussion of the GNOME Classic and GNOME Flashback sessions in development only. [Please refer to my Precise notes for released versions]("http://ubuntuforums.org/showthread.php?t=1966370"). Support questions for released versions should be posted in the [Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329") section of the forums.

**My personal focus is on the Flashback w/Metacity session** but I welcome comments regarding the new GNOME Classic and Flashback w/Compiz sessions. No PPA is needed to test the new GNOME Classic session since Ubuntu GNOME Saucy but [WebUpD8]("http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html") still has the best description I've found.

By now most Ubuntu users know that beginning with Oneiric (11.10) Ubuntu switched to GNOME 3/GTK+ 3 as it's base with Unity as the default desktop environment using the Compiz window manager whereas GNOME themselves used the new GnomeShell DE with the Mutter window manager. As a "fallback mode" for hardware that wouldn't support the Compiz window manager Ubuntu offered the Unity-2D session using the Metacity window manager in both Ubuntu Oneiric and Precise but they dropped Unity-2D in Quantal.

GNOME themselves offered a "fallback" session that was presented as "GNOME Classic" which used the Compiz window manager or "GNOME Classic (no effects)" which used the Metacity window manager at login in Ubuntu Oneiric, Precise, and Quantal if the package 'gnome-panel' was installed and, while the GNOME devs never intended to provide long term support for their "fallback session", Edubuntu will continue to maintain the "flashback w/metacity" session in order to support their LTSP installs.

There has however been continued [session renaming]("http://ubuntuforums.org/showthread.php?t=2185161") to facilitate GNOME's new Classic session that runs on top of the Mutter window manager, but **the safest and sanest way to install the "GNOME Flashback" sessions in Ubuntu or Ubuntu GNOME is still to** **[COLOR="#FF0000"]install the package 'gnome-panel'[/COLOR]** which has a very [light footprint]("http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986315#post12986315"). Of course if you want to run the Compiz session in Ubuntu GNOME you'll additionally need to install the packages 'compiz' and presumably 'compizconfig-settings-manager'.

There have been a number of changes/improvements since Precise, most notably I had not recommended installing 'gnome-tweak-tool' because it had a very heavy footprint but that's [improved greatly]("http://ubuntuforums.org/showthread.php?t=2090021&page=6&p=12851129#post12851129"), and there have been many changes due to the [deprecation of gconf]("http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850768#post12850768").  So after installing 'gnome-panel', logging out, [selecting the desired session]("http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682"), and logging back in **you may wish to install any of the following packages**:

'**indicator-applet**' and/or '**indicator-applet-session**' - as [an alternative]("http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657") to 'indicator-applet-complete'

'**gnome-tweak-tool**' - because it's quite convenient for general theming tweaks such as [having the old-style icons appear on the desktop]("http://ubuntuforums.org/attachment.php?attachmentid=251605"), [setting the key sequence for killing X]("http://ubuntuforums.org/attachment.php?attachmentid=251606"), and [changing themes]("http://ubuntuforums.org/attachment.php?attachmentid=251607").

'**shiki-colors-metacity-theme**' - because it provides a rather [URL="http://ubuntuforums.org/attachment.php?attachmentid=249048&d=1388468652"]retro window management button theme
[/URL]
'**sensors-applet**' - [to display system temps]("http://ubuntuforums.org/attachment.php?attachmentid=249045&d=1388463838")

[Update notifications now show up in the "window list" applet]("http://ubuntuforums.org/attachment.php?attachmentid=248080&d=1385371191") so no tweak is needed in that regard.

With the ability to add 'gnome-tweak-tool' w/o a bunch of bloat that leaves very few "tweaks" that actually require the use of the CLI:

#1: Moving the window-management buttons back to the right:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

#2: Disabling the [overlay-scrollbars]("http://ubuntuforums.org/attachment.php?attachmentid=251984&d=1397309461"):

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

#3: Possibly disabling the Firefox and/or Thunderbird global menu add-ons???????????? I'm unsure about this. I need to play around with fresh profiles and check that out. 

#4: Possibly disabling the [Unity webapps]("http://ubuntuforums.org/attachment.php?attachmentid=248451&d=1386603042"):

[http://ubuntuforums.org/attachment.php?attachmentid=248456&d=1386605099](http://ubuntuforums.org/attachment.php?attachmentid=248456&d=1386605099)

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

#5: Restoring the missing menu icons:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

**Known Issues**:

The most troubling thing I've encountered is the inability to backup or restore configurations:

[http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986410#post12986410](http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986410#post12986410)

***********************************************

Edit: I wanted to add a couple of valuable links:

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

[https://mail.gnome.org/archives/gnome-flashback-list/](https://mail.gnome.org/archives/gnome-flashback-list/)

---

### Post by grahammechanical on 2013-10-30
@kansasnoob

Can I make a few points?

1) Plenty of people are installing or upgrading to the latest Ubuntu release (13.10)
2) Plenty of people want what they call "Gnome Classic."
3) Gnome 3 DE and Gnome 3 Shell are under continued development.
4) Ubuntu is under continued development and is becoming less of a Gnome respin and more of a Linux distribution with its own code base as well as its own design.

I conclude that there is a need for Ubuntu+1 testers to pioneer the way into Ubuntu 14.04 and 14.10 to help bridge the gulf that could _possibly_ form between Ubuntu and those distributions based upon Ubuntu whose developers have their own map into the future. I would say that you have identified a valid Ubuntu+1 testing/research project.

Regards.

---

### Post by kansasnoob on 2013-10-30
> **grahammechanical said:**
> @kansasnoob

Can I make a few points?

1) Plenty of people are installing or upgrading to the latest Ubuntu release (13.10)
2) Plenty of people want what they call "Gnome Classic."
3) Gnome 3 DE and Gnome 3 Shell are under continued development.
4) Ubuntu is under continued development and is becoming less of a Gnome respin and more of a Linux distribution with its own code base as well as its own design.

I conclude that there is a need for Ubuntu+1 testers to pioneer the way into Ubuntu 14.04 and 14.10 to help bridge the gulf that could _possibly_ form between Ubuntu and those distributions based upon Ubuntu whose developers have their own map into the future. I would say that you have identified a valid Ubuntu+1 testing/research project.

Regards.

It's all a bit daunting actually ;)

When I originally pursued that "fallback" thing I fully expected that session to die when Precise reached it's EOL, but it now looks like Edubuntu is going to keep it alive so I need to get on the ball :)

I've been spending a lot of time in Ubuntu GNOME using the standard gnome-shell DE with no PPA's simply because I like it, but I maintain 43 other PC's within a 50 mile radius and many of the users prefer a truly "classic" desktop paradigm. To further complicate things some of those PC's have multiple users and one user may prefer Unity while another may prefer "fallback" or even 'lubuntu-core'.

And I'm kicking myself for overlooking bugs like these during the Saucy dev cycle:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1245209](https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1245209)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915)

Both still effect Trusty at this point, although I'm unsure about converting/blending Ubuntu and Ubuntu GNOME ATM since they use different default settings.

Regardless there is plenty of work to do :D

---

### Post by kansasnoob on 2013-10-30
Many thanks to whoever approved this. My step #1 is to clear up any confusion about the sessions :)

So I'm thinking about posting a thread in Desktop Environments titled:

**Confusion surrounding GNOME classic/fallback/flashback sessions**

*Then I'll continue with text somewhat like this:*

I've noticed a few posts lately indicating some confusion surrounding the new GNOME session options available at login so I hope to clear that up a little bit if possible. A brief history lesson is needed so bear with me.

Beginning with Oneiric (11.10) Ubuntu switched to using GNOME 3 as it's base and Unity as the default desktop environment using the Compiz window manager whereas GNOME themselves used the new GnomeShell DE with the Mutter window manager. 

As a "fallback mode" for hardware that wouldn't support the Compiz window manager Ubuntu offered the Unity-2D session using the Metacity window manager whereas GNOME themselves offered a "fallback" session that was presented as "GNOME Classic" or "GNOME Classic (no effects)" at login in Ubuntu if the package 'gnome-panel' was installed.

The GNOME devs had never intended to provide long term support for their "fallback session" so during Ubuntu's Raring dev cycle they sounded the death knoll for the "fallback" session, but then Edubuntu dev announced their intent to keep it alive in order to support their LTSP installs:

[http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/](http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/)

In the meanwhile Red Hat put some pressure on the GNOME devs to create a new Classic session that runs on top of the Mutter window manager. It should in no way be confused with the earlier "fallback" that Ubuntu called "classic" though. You can get a glimpse of the new "Classic" here:

[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

In order to make the new Gnome Classic mode distinguishable from the the older "classic" mode during the Raring dev cycle the name "classic" was replaced with "fallback", then in Saucy the name was changed from "fallback" to "flashback".

Are you confused yet? I'm almost dizzy just trying to explain it.

---

### Post by grahammechanical on 2013-10-30
I have noticed one difference between Ubuntu Gnome and Ubuntu and the other flavours. And that difference maybe affecting things. May be not. GDM and not lightdm.

When I was testing running with Xmir on Ubuntu and all the flavours Ubuntu Gnome was the only one that did not use Lighdm and Ubuntu Gnome was the only one I could not run with Xmir. 

I also found out that Lightdm does more than manage the login screen. It manages the display from quite early one. I guess that GDM does the same. Anyway by switching to Lightdm I was able to get Ubuntu Gnome running on Xmir. I lost the fine Ubuntu Gnome login screen in the process and I gave up trying to get it back. It did my head in searching for stuff.

So, if flashback (no effects) works in Edubuntu and Ubuntu but not in Ubuntu Gnome there has to be a reason.

[http://ubuntuforums.org/showthread.php?t=2183871](http://ubuntuforums.org/showthread.php?t=2183871)

Regards.

---

### Post by kansasnoob on 2013-10-30
> **grahammechanical said:**
> I have noticed one difference between Ubuntu Gnome and Ubuntu and the other flavours. And that difference maybe affecting things. May be not. GDM and not lightdm.

When I was testing running with Xmir on Ubuntu and all the flavours Ubuntu Gnome was the only one that did not use Lighdm and Ubuntu Gnome was the only one I could not run with Xmir. 

I also found out that Lightdm does more than manage the login screen. It manages the display from quite early one. I guess that GDM does the same. Anyway by switching to Lightdm I was able to get Ubuntu Gnome running on Xmir. I lost the fine Ubuntu Gnome login screen in the process and I gave up trying to get it back. It did my head in searching for stuff.

So, if flashback (no effects) works in Edubuntu and Ubuntu but not in Ubuntu Gnome there has to be a reason.

[http://ubuntuforums.org/showthread.php?t=2183871](http://ubuntuforums.org/showthread.php?t=2183871)

Regards.

Thanks, that gives me cool idea to try :D

I mean regarding this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1245209](https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1245209)

It does look like the X-session is not starting properly so I should try lightdm with all available greeters. Now I need to pull up my notes on lightdm :)

---

### Post by ventrical on 2013-10-31
> **grahammechanical said:**
> I have noticed one difference between Ubuntu Gnome and Ubuntu and the other flavours. And that difference maybe affecting things. May be not. GDM and not lightdm.

When I was testing running with Xmir on Ubuntu and all the flavours Ubuntu Gnome was the only one that did not use Lighdm and Ubuntu Gnome was the only one I could not run with Xmir. 

I also found out that Lightdm does more than manage the login screen. It manages the display from quite early one. I guess that GDM does the same. Anyway by switching to Lightdm I was able to get Ubuntu Gnome running on Xmir. I lost the fine Ubuntu Gnome login screen in the process and I gave up trying to get it back. It did my head in searching for stuff.

So, if flashback (no effects) works in Edubuntu and Ubuntu but not in Ubuntu Gnome there has to be a reason.

[http://ubuntuforums.org/showthread.php?t=2183871](http://ubuntuforums.org/showthread.php?t=2183871)

Regards.

@graham,

 Could you clarify please. Are you talking about the Edubuntu Desktop (downloadable from the repos) or the Edubuntu.iso? because these two are horses of a different colour, the prior bringing in problems and the latter being an extremeley large .iso.

regards..

---

### Post by ventrical on 2013-10-31
> **grahammechanical said:**
> @kansasnoob

Can I make a few points?

1) Plenty of people are installing or upgrading to the latest Ubuntu release (13.10)
2) Plenty of people want what they call "Gnome Classic."
3) Gnome 3 DE and Gnome 3 Shell are under continued development.
4) Ubuntu is under continued development and is becoming less of a Gnome respin and more of a Linux distribution with its own code base as well as its own design.

I conclude that there is a need for Ubuntu+1 testers to pioneer the way into Ubuntu 14.04 and 14.10 to help bridge the gulf that could _possibly_ form between Ubuntu and those distributions based upon Ubuntu whose developers have their own map into the future. I would say that you have identified a valid Ubuntu+1 testing/research project.

Regards.

  I have gnome-flashback working flawlessly in Trusty. Of course it is a higher end machine but I may try it on lower end form factors. There is a need for gnome (no -effects) and thats good news about Edubuntu because some teachers who are transitioning from Windows to Ubuntu (Ed) need the (no-effects) while teaching young children, otherwise it it too complex.

regards..

---

### Post by kansasnoob on 2013-10-31
How factually correct do you think this is:

> I've noticed a few posts lately indicating some confusion surrounding the new GNOME session options available at login so I hope to clear that up a little bit if possible. A brief history lesson is needed so bear with me.

Beginning with Oneiric (11.10) Ubuntu switched to using GNOME 3 as it's base and Unity as the default desktop environment using the Compiz window manager whereas GNOME themselves used the new GnomeShell DE with the Mutter window manager. 

As a "fallback mode" for hardware that wouldn't support the Compiz window manager Ubuntu offered the Unity-2D session using the Metacity window manager whereas GNOME themselves offered a "fallback" session that was presented as "GNOME Classic" or "GNOME Classic (no effects)" at login in Ubuntu if the package 'gnome-panel' was installed.

The GNOME devs had never intended to provide long term support for their "fallback session" so during Ubuntu's Raring dev cycle they sounded the death knoll for the "fallback" session, but then Edubuntu dev announced their intent to keep it alive in order to support their LTSP installs:

[http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/](http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/)

In the meanwhile the GNOME devs responded to user discontent with GNOME Shell by creating a new Classic session that runs on top of the Mutter window manager. It should in no way be confused with the earlier "fallback" that Ubuntu called "classic" though. You can get a glimpse of the new "Classic" here:

[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

In order to make the new Gnome Classic mode distinguishable from the the older "classic" mode during the Raring dev cycle the name "classic" was replaced with "fallback", then in Saucy the name was changed from "fallback" to "flashback".

End of history lesson.

Now let's do a recap:

In Ubuntu & Edubuntu Oneiric, Precise, and Quantal if you installed the package 'gnome-panel' you'd then find the additional login options "GNOME Classic" and "GNOME Classic (no effects)". The standard "Classic" session uses the Compiz window manager whereas the "(no effects)" session uses the Metacity window manager.

In Ubuntu, Edubuntu, and Ubuntu GNOME Raring once the package 'gnome-panel' is installed you'll then find the additional login options "GNOME Fallback" and "GNOME Fallback (no effects)". The standard "Fallback" session uses the Compiz window manager whereas the "(no effects)" session uses the Metacity window manager.

In Ubuntu GNOME Saucy you will find a new "GNOME Classic" session when you login without adding any additional packages, but this session is in no way related to the earlier classic or fallback sessions! The new GNOME Classic session runs on top of the Mutter window manager and could be best described as a 'gnome-shell' session using a popular collection of GNOME Shell Extensions.

In Ubuntu, Edubuntu, and Ubuntu GNOME Saucy once the package 'gnome-panel' is installed you'll then find the additional login options "GNOME Flashback" and "GNOME Flashback (no effects)". The standard "Flashback" session uses the Compiz window manager whereas the "(no effects)" session uses the Metacity window manager.

I'm particularly concerned with saying, "The new GNOME Classic session runs on top of the Mutter window manager and could be best described as a 'gnome-shell' session using a popular collection of GNOME Shell Extensions". Do you think that's accurate and truthful?

---

### Post by kansasnoob on 2013-10-31
> **ventrical said:**
> I have gnome-flashback working flawlessly in Trusty. Of course it is a higher end machine but I may try it on lower end form factors. There is a need for gnome (no -effects) and thats good news about Edubuntu because some teachers who are transitioning from Windows to Ubuntu (Ed) need the (no-effects) while teaching young children, otherwise it it too complex.

regards..

Ditto here. I started with the Oct 21 iso image and other than a slight hiccup with the "extras" repo things are now pretty much OK :D

But the reason I asked permission to do this thread is that I also need to follow up on some Saucy bugs with "classic/fallback/flashback" because I didn't even try it until Saucy was released :(

The beauty of having an Ubuntu +1 thread is that we can test continuously from one cycle to another so this thread should hopefully allow us to record the changes as they occur, I just got lazy about testing the Metacity session so now I have to catch up before the release of Trusty :)

---

### Post by zika on 2013-10-31
Continuity is a benefit, by no means a hindrance...
Eagerly (a)waiting to see development of promised thread...

---

### Post by philinux on 2013-10-31
> **kansasnoob said:**
> 
But the reason I asked permission to do this thread is that I also need to follow up on some Saucy bugs with "classic/fallback/flashback" because I didn't even try it until Saucy was released :(



Just for others. The new package is gnome-session-flashback [https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)
gnome-session-fallback just installs the above package.

Any Saucy related bugs and fixes needs to go in here > [http://ubuntuforums.org/showthread.php?t=2182038](http://ubuntuforums.org/showthread.php?t=2182038)

---

### Post by Elfy on 2013-10-31
>  I think it belongs here because we clearly say that this is not a standard support forum.The notice in this forum is to try and forestall some of those coming here after searching and finding threads started during the dev period.

For example - we've got 6 months worth of Raring followed by 6 of Saucy - shortly we'll have 6 months of Trusty - we don't want people dragging Saucy threads up once we are into Trusty.

This forum is not really the right place for Tutorials of any sort - for one thing just as we made a change and kept the forum open - we could in future decide it doesn't work and go back to previous procedure and close forum at dev end. 

If you want to actually run with a Tutorial for it - and keep it up to date then I'm happy enough to move the thread to the correct place and clean it up a bit.

---

### Post by QDR06VV9 on 2013-10-31
> **kansasnoob said:**
> Ditto here. I started with the Oct 21 iso image and other than a slight hiccup with the "extras" repo things are now pretty much OK :D

But the reason I asked permission to do this thread is that I also need to follow up on some Saucy bugs with "classic/fallback/flashback" because I didn't even try it until Saucy was released :(

[COLOR=#0000ff]_The beauty of having an Ubuntu +1 thread is that we can test continuously from one cycle to another so this thread should hopefully allow us to record the changes as they occur, I just got lazy about testing the Metacity session so now I have to catch up before the release of Trusty _[/COLOR]:)

Much needed! and many thanks kansasnoob.

---

### Post by kansasnoob on 2013-10-31
> **Elfy said:**
> The notice in this forum is to try and forestall some of those coming here after searching and finding threads started during the dev period.

For example - we've got 6 months worth of Raring followed by 6 of Saucy - shortly we'll have 6 months of Trusty - we don't want people dragging Saucy threads up once we are into Trusty.

This forum is not really the right place for Tutorials of any sort - for one thing just as we made a change and kept the forum open - we could in future decide it doesn't work and go back to previous procedure and close forum at dev end. 

If you want to actually run with a Tutorial for it - and keep it up to date then I'm happy enough to move the thread to the correct place and clean it up a bit.

NO! I have nothing worthy of a How To ATM :(

Repeating myself;  I expected the "fallback" session to die when Precise reached EOL in April 2017, but many things have changed :)

If I can't discuss the changes here please move this thread to "recurring" so almost no one will see it and users can remain uninformed.

Another huge reason for having this thread where it's at is that I need feedback from other active testers, but I have no choice other than to live with the forum mods decisions.

---

### Post by kansasnoob on 2013-10-31
> **philinux said:**
> Just for others. The new package is gnome-session-flashback [https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)
gnome-session-fallback just installs the above package.

Any Saucy related bugs and fixes needs to go in here > [http://ubuntuforums.org/showthread.php?t=2182038](http://ubuntuforums.org/showthread.php?t=2182038)

I understand the difference between Saucy and Trusty .............. at this point Trusty is little more than Saucy with some cherry-picked packages ;)

There are no official daily's for the flavors so a user can only upgrade from Saucy to Trusty, but this thread has to do with the evolution of the various gnome sessions available in the repos!

Like it or not 'gnome-panel' is in the repos and Edubuntu uses it:

[ATTACH=CONFIG]247423[/ATTACH]

But the changes are not well documented and unless the next UDS results in killing this session we need to work on improving both the session itself and the documentation.

It's also impossible to NOT mention any previous releases when working on documentation or bugs.

It's also worth mentioning that 12.04.4 is coming soon - probably with a Saucy hardware-enablement-stack :)

---

### Post by ventrical on 2013-10-31
> **kansasnoob said:**
> NO! I have nothing worthy of a How To ATM :(

Repeating myself;  I expected the "fallback" session to die when Precise reached EOL in April 2017, but many things have changed :)

If I can't discuss the changes here please move this thread to "recurring" so almost no one will see it and users can remain uninformed.

Another huge reason for having this thread where it's at is that I need feedback from other active testers, but I have no choice other than to live with the forum mods decisions.


 I am just suggesting in kind, that , perhaps you could ask the mods to drop the  {evolution of gnome classic} and try for somthing like 'Edubuntu/gnome classic/fallback/flashback session Trusty'. This way I think the moderating powers that be may find it more palatable for U+1, it would be a real plug for Edubuntu (which is a diamond in the rough) and you could interject your hypothesis and work with bug fixes without fragmenting the echo.

  You said  "I need feedback".  Please do not take offence at my words. I am hoping to be a helper here. :)

regards..

---

### Post by ventrical on 2013-10-31
@kansasnoob,

 I am currently downloading 13.10 Edubuntu.iso, then will attempt to upgrade that to trusty tahr and run it on gnome flashback .. etc.  Just in case if your thread gets moved I'll start another thread on Edubuntu/Gnome/Flashback (which should get a little more recognition) but I do not want to supersede the moderators either.

regards..

---

### Post by ventrical on 2013-10-31
I see where they are going now .. absolutely awesome.

I am in live session now about to install.

---

### Post by ventrical on 2013-10-31
Install went great. Now in gnome flashback (no effects). Now to upgrade it to trusty. if possible ??

---

### Post by kansasnoob on 2013-10-31
> **ventrical said:**
> I am just suggesting in kind, that , perhaps you could ask the mods to drop the  {evolution of gnome classic} and try for somthing like 'Edubuntu/gnome classic/fallback/flashback session Trusty'. This way I think the moderating powers that be may find it more palatable for U+1, it would be a real plug for Edubuntu (which is a diamond in the rough) and you could interject your hypothesis and work with bug fixes without fragmenting the echo.

  You said  "I need feedback".  Please do not take offence at my words. I am hoping to be a helper here. :)

regards..

No offense taken ... ever :)

The reason I want to work on this here is because we true testers are critics by nature, and only well reasoned criticism results in a good outcome :)

I don't remember the exact words I used to open this thread, but it was something like "May I pursue the 'evolution of gnome classic/fallback/flashback sessions' here?

Then one of the mods shortened the title so I took that as acceptance of pursuing my goals :)

Will we sometimes get off-topic? Absolutely!

Once again look at:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

Had we been Ubuntu +1 then that thread could still be alive, but time rolls on so we have to adapt and as testers it's beneficial to the entire Ubuntu community to share what we know in the most appropriate manner possible.

Appropriate is the key word there. If I'm providing inappropriate or misleading info that's NO GOOD to anyone, and certainly harmful to the project. So I need to share what I plan on doing or saying with a trusted community ............... Ubuntu +1 is that trusted community.

Does that make sense?

---

### Post by ventrical on 2013-11-01
> **kansasnoob said:**
> No offense taken ... ever :)

The reason I want to work on this here is because we true testers are critics by nature, and only well reasoned criticism results in a good outcome :)

I don't remember the exact words I used to open this thread, but it was something like "May I pursue the 'evolution of gnome classic/fallback/flashback sessions' here?

Then one of the mods shortened the title so I took that as acceptance of pursuing my goals :)

Will we sometimes get off-topic? Absolutely!

Once again look at:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

Had we been Ubuntu +1 then that thread could still be alive, but time rolls on so we have to adapt and as testers it's beneficial to the entire Ubuntu community to share what we know in the most appropriate manner possible.

Appropriate is the key word there. If I'm providing inappropriate or misleading info that's NO GOOD to anyone, and certainly harmful to the project. So I need to share what I plan on doing or saying with a trusted community ............... Ubuntu +1 is that trusted community.

Does that make sense?

Absolutely and it is also of great importance in the next 6 months to have Gnome_flashback working properly and effectively because there are several million people who just do not have the economic  means to throw out their old computers at this time and buy new ones. It is imperative that gnome-flashback be effective across a wide spread of legacy form-factors.  Iv'e been able to use most recent kernels on Lucid very effectively . I don't see why it (gnome-flashback) cannot be given the same amount of attention as Unity.

  I will re-read some of your reports and try to get a better handle on it because you spent so much personal time on the project previously.

  I am an experimenter that likes to try exploratory testing and some people get frustrated with my method and understandably so, so I will try to keep on topic as best as I can while still having fun ! :)

Regards..

edit..

Oy ..I basically said the same thing back then in the old thread  :)

[http://ubuntuforums.org/showthread.php?t=1873765&p=11418769#post11418769](http://ubuntuforums.org/showthread.php?t=1873765&p=11418769#post11418769)

---

### Post by grahammechanical on 2013-11-01
> [COLOR=#000000]Absolutely and it is also of great importance in the next 6 months to have Gnome_flashback working properly and effectively because there are several million people who just do not have the economic means to throw out their old computers at this time and buy new ones.[/COLOR]

I will agree with that but we should go further, right into 14.10 because that is where the big, big, changes to Ubuntu are going to come. Perhaps we should say that this is Testing Flashback on Ubuntu+1. Does that cover all the bases, as they say in baseball?

I would also limit this Flashback testing to: a) Ubuntu, because it is the base code for the flavours. b) Ubuntu Gnome, because Gnome shell is the natural home of Gnome Flashback. c) Edubuntu, because? Well, Ventrical said: [COLOR=#000000][I]it would be a real plug for Edubuntu (which is a diamond in the rough)
[/I][/COLOR]

---

### Post by philinux on 2013-11-01
> **grahammechanical said:**
> I will agree with that but we should go further, right into 14.10 because that is where the big, big, changes to Ubuntu are going to come. Perhaps we should say that this is Testing Flashback on Ubuntu+1. Does that cover all the bases, as they say in baseball?

I would also limit this Flashback testing to: a) Ubuntu, because it is the base code for the flavours. b) Ubuntu Gnome, because Gnome shell is the natural home of Gnome Flashback. c) Edubuntu, because? Well, Ventrical said: [COLOR=#000000][I]it would be a real plug for Edubuntu (which is a diamond in the rough)
[/I][/COLOR]

kansasnoob can change the title of the thread by editing the original post then choosing advanced.

---

### Post by kansasnoob on 2013-11-01
This is not even half-baked but I've been keeping some notes while testing Trusty and Saucy. Remember it's only a work in progress and some of it could be incomplete or even inaccurate :)

**GETTING STARTED**

[B][I]This applies to all supported versions
[/I][/B]
```
sudo apt-get install gnome-panel
```

Note: There is a reason to simply install 'gnome-panel' rather than a specific "gnome" or "session" package, specifically the session and package names have changed frequently to accomodate the addition of GNOME's new classic session. This becomes obvious when you log into the new session.

**LOG INTO THE APPROPRIATE NEW (no effects) SESSION**

***In versions 12.04, 12.04.1, 12.04.2, 12.04.3 and 12.10:***

Log out, click on the Ubuntu emblem next to your username, select the "classic (no effects)" session, and then enter your password.

***In version 13.04:***

Log out, click on the GNOME emblem next to your username, select the "fallback (no effects)" session, and then enter your password.

***In versions 13.10 and 14.04:***

Log out, click on the GNOME emblem next to your username, select the "flashback (no effects)" session, and then enter your password.

**CHANGE TERMINAL THEME**

***Applies to all supported versions***

If you find the default terminal theme (white text on a purple background) as atrocious as I do just open the Terminal, click on Edit > Profile Preferences. Then click on the Colors tab and uncheck "Use colors from system theme", then select "Black on white" from the Built-in schemes.

[B]ADDING ADDITIONAL "indicator-applet" OPTIONS
[/B]
[B][I]This applies to all supported versions
[/I][/B]
You may want to install these so they'll be available for placement in the panel (only 'indicator-applet-complete' is installed by default):

```
sudo apt-get install indicator-applet indicator-applet-session

```
You can compare the difference between the three indicator applets here:

[http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657](http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657)

**RESTORE THE "Run Command Prompt" FUNCTION**

[B][I]This applies to version 12.04 only
[/I][/B]
I wanted to get the "Run Command Prompt" back by pressing Alt+F2 just as it was in Gnome 2. This can be quite useful if you should ever do something silly like remove both panels and need to launch the terminal or another application without being able to access the menu(s).

It really couldn't be much simpler, just go to System Tools > System Settings > Keyboard > Shortcuts > System and highlight the line that says "Show the run command prompt". Then just follow the instructions at the bottom of that window.

This can also be done using the CLI:

```
gconftool-2 --set "/apps/metacity/global_keybindings/panel_run_dialog" --type string "<Alt>F2"
```

To revert that to the default setting run:

```
gconftool-2 --set "/apps/metacity/global_keybindings/panel_run_dialog" --type string "disabled"
```

[B][COLOR="#FF0000"]I think this was the default setting in 12.10 and 13.04, but it changed again in 13.10 and 14.04 due to the further depraction of gconf.
[/COLOR][/B]
[B]DISABLE THE SCREEN LOCK
[/B]
[B][I]This applies to all supported versions
[/I][/B]
I find the screen lock very annoying, I live alone and don't like having to enter my password everytime the screensaver acivates. So you can just go to System Tools > System Settings > Brightness & Lock and select Lock = Off.

This can also be done using the CLI:

```
gsettings set org.gnome.desktop.screensaver lock-enabled false
```

To revert that to the default setting run:

```
gsettings set org.gnome.desktop.screensaver lock-enabled true
```

**DISPLAY UPDATE-NOTIFICATIONS IN PANEL**

***This applies to 12.04, 12.10, and 13.04 only:***

In Unity the update-notifications now show up in the Launcher but without the Launcher we now get no persistent update notifications. Still no worries, I got it to show up in either 'indicator-applet' or 'indicator-applet-complete' in gnome-panel by running the command:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

You can revert that by running:

```
gsettings set com.ubuntu.update-notifier auto-launch true
```

[B][COLOR="#FF0000"]In 13.10 and 14.04 the update notifications now appear in the "window list" when using flashback so no change is required.
[/COLOR][/B]
**MOVE WINDOW-MANAGEMENT BUTTONS TO THE RIGHT**

***In version 12.04 only:***

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Note: to restore the defaults run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

In versions 12.10, 13.04, 13.10, and 14.04:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

To move them back to the left:
&#65279;
```
gsettings set org.gnome.desktop.wm.preferences button-layout close,minimize,maximize:
```

**IMPROVE WINDOW-MANAGEMENT BUTTON APPEARANCE**

***In version 12.04 only:***

```
sudo apt-get install shiki-colors-metacity-theme
```

```
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
```

To restore the default theme just run:

```
gconftool-2 -s --type string /apps/metacity/general/theme Ambiance
```

***In versions 12.10, 13.04, 13.10, and 14.04:***

```
sudo apt-get install shiki-colors-metacity-theme
```

```
gsettings set org.gnome.desktop.wm.preferences theme Shiki-Colors-Metacity
```

Or to restore the Ambiance theme:

```
gsettings set org.gnome.desktop.wm.preferences theme Ambiance
```

**DISABLE OR REMOVE THE OVERLAY-SCROLLBARS**

***This applies to all supported versions, and there are two options:***

***Option #1***, safest:

I found the overlay-scrollbars to be inconsistent and annoying in the classic DE and I'd previously recommended just removing them altogether but I believe I've found a much better way to disable them on a per-user basis. Simply run one command:

```
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
```

Then just log out and log back in for that change to take effect.

If you should later wish to revert that just run:

```
sed -i 's/^export LIBOVERLAY_SCROLLBAR.*/#&/' ~/.xprofile
```

***Option #2***, more permanent, possibly very permanent, so proceed with caution:

**[COLOR="#FF0000"]Should you wish to remove them permanently you can run the following command, but be warned - just reinstalling those packages does NOT restore them correctly - so you may never be able to get them back if you change your mind[/COLOR]**:

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar
```

**RESTORE THE MISSING MENU AND BUTTON ICONS**

***This applies to all supported versions***

I also dislike the missing menu and button icons so I run:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

**HAVE FILE MANAGER HANDLE THE DESKTOP**

***This applies to all supported versions***

This one is the hardest for me to explain. By default the GNOME 3 desktop is set to NOT display any icons, but it's possible for the desktop to display any combination of these icons/"actors":

Computer...........(computer-icon-visible)
Home...............(home-icon-visible)
Network............(network-icon-visible)
Trash..............(trash-icon-visible)
Mounted volumes....(volumes-visible)

But to do so you must first set the "stage" by running:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

But that only sets the "stage" for the "actors", now you must decide which actors you want on the stage. You're now the director.

After running that command either reboot or log out and log back in. When you get back to a blank DE background decide what you want displayed. (Hint, the "true" or "false" at the end of these commands is the key):

To show the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible true
```

To hide the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```

To show the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible true
```

To hide the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

To show the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible true
```

To hide the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```

To show the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

To hide the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```

To show Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

To hide Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```

**DISABLE THE FIREFOX AND THUNDERBIRD GLOBAL MENU ADD-ONS:**

***This applies to all supported versions***

You may or may not find that you need to disable the Firefox and/or Thunderbird global menu add-ons. To do so in Firefox just go to Tools > Add-ons > Global Menu Bar integration and select Disable. You'll then be prompted to restart Firefox. I don't use Thunderbird so I can't be sure of the specific procedure with it, but I'd think it's similar.

---

### Post by kansasnoob on 2013-11-01
> **philinux said:**
> kansasnoob can change the title of the thread by editing the original post then choosing advanced.

Thanks for the hint :D

---

### Post by ventrical on 2013-11-01
> **grahammechanical said:**
> I will agree with that but we should go further, right into 14.10 because that is where the big, big, changes to Ubuntu are going to come. Perhaps we should say that this is Testing Flashback on Ubuntu+1. Does that cover all the bases, as they say in baseball?

I would also limit this Flashback testing to: a) Ubuntu, because it is the base code for the flavours. b) Ubuntu Gnome, because Gnome shell is the natural home of Gnome Flashback. c) Edubuntu, because? Well, Ventrical said: [COLOR=#000000][I]it would be a real plug for Edubuntu (which is a diamond in the rough)
[/I][/COLOR]

   Well said....and you know how hard polishing diamonds can be.  :)

---

### Post by ventrical on 2013-11-01
> **kansasnoob said:**
> T...


 No offence but this is where I get lost in following the theme of the thread.  First I have to admit that I had experiemented with gnome-shell .etc.. and I know how many are endeared to it.. but I am a Unity man and gnome-flashback type geek.  :)  

  I am going to just keep reading and working on Edubuntu Trusty Gnome Flashback and if I have anything significant to add, I will.

 Also ... I need to ask a question.  Would you like us to test some of the above ideas you are documenting for this project.?

thanks in advance

edit..

Ok .. I had a second read and understand your meanings now. Most of all those things are in Edubuntu Trusty by default (gnome-no-effects).

Also .. just to make a side note.. I run another machine for Overclocking purpose that uses Gnome-Flashback (with effects) Trusty Tahr, and that was installed on an original Ubuntu (Unity) install and it works seamlessly.

---

### Post by mörgæs on 2013-11-01
> **kansasnoob said:**
> 
Then one of the mods shortened the title so I took that as acceptance of pursuing my goals


I was the one pruning as I often do in order to get a short and precise title. Especially when a growing part of the audience is using mobile devices it's important to be brief. 

There's no hidden interpretation in that.

---

### Post by ventrical on 2013-11-01
With a lot of fanagaling I was able to get gnome (noeffects) to work in 32bit but Ubuntu Trusty on THIS  graphics card:

```


01:00.0 VGA compatible controller: NVIDIA Corporation NV34GL [Quadro FX 500/600 PCI] (rev a1)
ventrical@ventrical-P25G:~$ 

```

---

### Post by Elfy on 2013-11-01
Closed for staff review.

---

### Post by Elfy on 2013-11-02
Re-opened.

While this forum is a 'rolling' one at present - it is for the dev version and we want to keep it as that. 

We would rather that this thread deals with the development version only, if it needs to be about more than one then it will need to be moved elsewhere - at which point no discussion of trusty in it until next year.

[I've not edited this post to remove references to released versions, preferring to keep it as it is.]("http://ubuntuforums.org/showthread.php?t=2184682&p=12835493&viewfull=1#post12835493") But please make sure to keep ontopic for the forum going forward.

Thanks for understanding.

---

### Post by kansasnoob on 2013-11-02
> **Elfy said:**
> Re-opened.

While this forum is a 'rolling' one at present - it is for the dev version and we want to keep it as that. 

We would rather that this thread deals with the development version only, if it needs to be about more than one then it will need to be moved elsewhere - at which point no discussion of trusty in it until next year.

[I've not edited this post to remove references to released versions, preferring to keep it as it is.]("http://ubuntuforums.org/showthread.php?t=2184682&p=12835493&viewfull=1#post12835493") But please make sure to keep ontopic for the forum going forward.

Thanks for understanding.

Many thanks :)

Do the mods agree with my renaming?

---

### Post by Elfy on 2013-11-02
That's fine :)

---

### Post by kansasnoob on 2013-11-02
BTW I'll prune my OP to reflect the change once I know the mods approve of my title change :)

---

### Post by grahammechanical on 2013-11-02
@ventrical

I am sorry that I failed to reply to a question you asked of me. I have only just seen it. This comment was based upon the results that you and kansasnoob had declared. I was just thinking aloud.

> So, if flashback (no effects) works in Edubuntu and Ubuntu but not in Ubuntu Gnome there has to be a reason.

I have now done a little testing of my own. I have just installed Ubuntu Gnome (Trusty) from yesterday's QA ISO image. Things seemed to go well. I get an option for Gnome Classic but no option for Gnome classic (no effects). Which is not consistent with what I found on Edubuntu (saucy converted to trusty - no trusty iso image as of yesterday). I have not yet installed gnome-panel on Ubuntu (trusty).

Now here is a weird thing. The Gnome classic session looks classic enough as I remember it all those years ago. :) But when I move the mouse into the top left corner of the screen the Gnome 3 shell appears as if I had done that action in a Gnome 3 shell session. I suppose that is because Gnome Classic on Gnome 3 shell is a set of Gnome 3 extensions.

So, I am guessing that there are code differences between Ubuntu Gnome - Gnome Classic and Edubuntu and Ubuntu Gnome Flashback. I would also guess that as far as the Gnome Devs are concerned Gnome Classic (no effects) is dead and gone.

I do not use alternative desktops. They bring in more than the User Interface. I am of the opinion that they have reached a point to be too top heavy to be practical.

Regards.

---

### Post by kansasnoob on 2013-11-02
> **grahammechanical said:**
> @ventrical

I am sorry that I failed to reply to a question you asked of me. I have only just seen it. This comment was based upon the results that you and kansasnoob had declared. I was just thinking aloud.



I have now done a little testing of my own. I have just installed Ubuntu Gnome (Trusty) from yesterday's QA ISO image. Things seemed to go well. I get an option for Gnome Classic but no option for Gnome classic (no effects). Which is not consistent with what I found on Edubuntu (saucy converted to trusty - no trusty iso image as of yesterday). I have not yet installed gnome-panel on Ubuntu (trusty).

Now here is a weird thing. The Gnome classic session looks classic enough as I remember it all those years ago. :) But when I move the mouse into the top left corner of the screen the Gnome 3 shell appears as if I had done that action in a Gnome 3 shell session. I suppose that is because Gnome Classic on Gnome 3 shell is a set of Gnome 3 extensions.

So, I am guessing that there are code differences between Ubuntu Gnome - Gnome Classic and Edubuntu and Ubuntu Gnome Flashback. I would also guess that as far as the Gnome Devs are concerned Gnome Classic (no effects) is dead and gone.

I do not use alternative desktops. They bring in more than the User Interface. I am of the opinion that they have reached a point to be too top heavy to be practical.

Regards.

That is exactly what I've been trying to address :D

Classic is now 'gnome-shell' with some cherry picked extensions to make it look like gnome 2, but it's truly gnome-shell running on top of Mutter.

The new "classic" is in no way related to the fallback/flashback sessions ;)

---

### Post by philinux on 2013-11-02
> **kansasnoob said:**
> BTW I'll prune my OP to reflect the change once I know the mods approve of my title change :)

Title fine as elfy said. Dont forget to post any saucy bugs with workarounds in here [http://ubuntuforums.org/showthread.php?t=2182038](http://ubuntuforums.org/showthread.php?t=2182038)

Cheers. Now back on topic. ;)

---

### Post by cariboo on 2013-11-02
> **kansasnoob said:**
> BTW I'll prune my OP to reflect the change once I know the mods approve of my title change :)

Several of the staff discussed the thread, and we all give our approval.

---

### Post by ventrical on 2013-11-02
> **grahammechanical said:**
> @ventrical

I am sorry that I failed to reply to a question you asked of me. I have only just seen it. This comment was based upon the results that you and kansasnoob had declared. I was just thinking aloud.

So, I am guessing that there are code differences between Ubuntu Gnome - Gnome Classic and Edubuntu and Ubuntu Gnome Flashback. I would also guess that as far as the Gnome Devs are concerned Gnome Classic (no effects) is dead and gone.

I do not use alternative desktops. They bring in more than the User Interface. I am of the opinion that they have reached a point to be too top heavy to be practical.

Regards.

@graham

OK.. Thank you grahammechanical for replying to my question. The reason I asked is so that I can better synchronize my responses while doing a duplicate proceedure. Also .. I just wanted to note that  the alternative desktops (xubuntu-desktop,kubuntu-desktop, lubuntu-desktop..etc..) are not officially supported by Canonical (although they may have modules and components that are).

Regards..

---

### Post by ventrical on 2013-11-02
> **kansasnoob said:**
> BTW I'll prune my OP to reflect the change once I know the mods approve of my title change :)

Thats a lot better title kansasnoob.! :)

---

### Post by grahammechanical on 2013-11-02
Ok, I am moving on. I have just installed gnome-session-flashback through the software centre. I now get the option of Gnome Flash back and Gnome Flashback (no effects) as well as Ubuntu. And the Launcher does not make an appearance. So, apart from the Unity type notifications Gnome Flashback seems to be insulated from Unity. 

I noted that software centre describes gnome-session-flashback as built on Gnome Panel 3. And also that Gnome Shell is a separate package as is Gnome Shell Classic. I see that the actual package for Gnome Shell Classic is gnome-shell-extensions.

So, Gnome Shell Classic is for Gnome Shell and is different from Gnome Flashback (gnome-session-flashback) which is for Unity based versions of Ubuntu. Which Edubuntu now is. This is my thinking.

Regards.

---

### Post by ventrical on 2013-11-12
Most recent update for Edubuntu wiped gnome-flashback (no effects) . Will not come up.

---

### Post by kansasnoob on 2013-11-12
I'm running Ubuntu Trusty here and all is well so far :)

---

### Post by kansasnoob on 2013-11-12
Something cool I discovered is that since Precise 'gnome-tweak-tool' now has much lighter demands:

> Commandline: /usr/sbin/synaptic
Install: gir1.2-gdesktopenums-3.0:i386 (3.8.0-1ubuntu1, automatic), gnome-tweak-tool:i386 (3.8.1-0ubuntu1), gnome-shell-common:i386 (3.8.4-0ubuntu5, automatic), gir1.2-gnomedesktop-3.0:i386 (3.8.4-0ubuntu1, automatic)

So when I redo that guide I think I'll include it. It looks like that actually changed sometime in Quantal and I didn't even notice :(

---

### Post by ventrical on 2013-11-12
> **kansasnoob said:**
> I'm running Ubuntu Trusty here and all is well so far :)


Ok.. after a 'hardboot'  it came up.

false alarm..

edit .. with exception that no indicators came up on right side top panel.

.. i know there is another thread..:)

regards..

---

### Post by ventrical on 2013-11-12
Just to update here:

 I am using Edubuntu and testing gnome-flashback (both). Gnome-flashback (both) work fine on Ubuntu. The current problem is with Edubuntu. I removed unity-system-compositor, but, to no avail. Apport will not send internal error report flagging unity-system-compositor.

  I will use the method of creating a new user and see what happens there.

edit:

Nope .. no go, no indicators on top right panel.(Edubuntu 64bit).

---

### Post by grahammechanical on 2013-11-13
Edubuntu fine here, even after to day's update (13th) which brought in a kernel update.

I ran a little memory usage experiment using System Monitor right after loading. Ubuntu = 389 MiB; Flaskback = 335 MiB and Flashback (no effects) = 316 MiB. Total RAM = 1GB.

I have also noticed that when using the flashback session the screen lock log back in screen has a top panel like the one in Gnome 3 Shell. And another thing, Flashback has a Background utility similar to the one in gnome 3 shell but Ubuntu presents the normal Ubuntu Appearance utility. Also this Edubuntu has Ubuntu Web Browser (Browser) as well as Firefox.

Edubuntu is quite a remix! Now, a combination of Edubuntu and Ubuntu Studio would be something. Imagine how long it would take to install that remix.

---

### Post by ventrical on 2013-11-13
For some reason  I decided to use synaptic to download gnome-core, which , of course, is gnome-shell... so.. I'll be looking at fixing this one .. umm.. soon :) lol

---

### Post by kansasnoob on 2013-11-15
I hope the mods are OK with the latest title change.

It's clear to me now that step #1 in this endeavor needs to be defining the difference between what is now "classic" and the "flashback" sessions.

My personal focus will remain on "Flashback (no effects)" but I welcome comments about the other sessions :)

---

### Post by cariboo on 2013-11-15
> **kansasnoob said:**
> I hope the mods are OK with the latest title change.

It's clear to me now that step #1 in this endeavor needs to be defining the difference between what is now "classic" and the "flashback" sessions.

My personal focus will remain on "Flashback (no effects)" but I welcome comments about the other sessions :)

No problems here with the title change. ;-)

---

### Post by kansasnoob on 2013-11-17
Something I had not noticed until Trusty is how much they've improved the dependencies for 'gnome-tweak-tool'.

In Precise it required installing all of this:

> The following NEW packages will be installed:
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gjs gnome-contacts gnome-icon-theme-full gnome-shell
  gnome-shell-common gnome-themes-standard gnome-tweak-tool libcaribou-common
  libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common
  libcogl-pango0 libcogl9 libgjs0c libmozjs185-1.0 libmutter0 mutter-common
0 upgraded, 35 newly installed, 0 to remove and 1 not upgraded.
Need to get 16.8 MB of archives.
After this operation, 38.1 MB of additional disk space will be used.

In Trusty 'gnome-tweak-tool' only installs this:

> Installed the following packages:
gir1.2-gdesktopenums-3.0 (3.8.0-1ubuntu1)
gir1.2-gnomedesktop-3.0 (3.8.4-0ubuntu1)
gnome-shell-common (3.8.4-0ubuntu5)
gnome-tweak-tool (3.8.1-0ubuntu1)

So I definitely need to add 'gnome-tweak-tool' as an optional package to install :)

That makes many of the general theming tweaks much easier for those who prefer using the GUI :D

Just installing 'gnome-panel' is the easiest and lightest way to get started:

> Installed the following packages:
alacarte (3.10.0-1)
gir1.2-gconf-2.0 (3.2.6-0ubuntu1)
gir1.2-panelapplet-4.0 (1:3.6.2-0ubuntu15)
gnome-applets (3.5.92-0ubuntu3)
gnome-applets-data (3.5.92-0ubuntu3)
gnome-media (3.4.0-1ubuntu1)
gnome-panel (1:3.6.2-0ubuntu15)
gnome-panel-data (1:3.6.2-0ubuntu15)
gnome-session-flashback (1:3.6.2-0ubuntu15)
gstreamer0.10-gconf (0.10.31-3+nmu1ubuntu3)
indicator-applet (12.10.2+13.10.20130924.2-0ubuntu1)
indicator-applet-complete (12.10.2+13.10.20130924.2-0ubuntu1)
libgnome-media-profiles-3.0-0 (3.0.0-1ubuntu1)
libpanel-applet-4-0 (1:3.6.2-0ubuntu15)
metacity (1:2.34.13-0ubuntu2)
notification-daemon (0.7.6-1)

Then optionally 'indicator-applet', 'indicator-applet-session', 'gnome-tweak-tool', or 'shiki-colors-metacity-theme' as desired.

Update notifications now show up in the "window list" applet so no tweak is needed in that regard.

With the ability to add 'gnome-tweak-tool' w/o a bunch of bloat that leaves very few "tweaks" that actually require the use of the CLI:

#1: Moving the window-management buttons back to the right:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

#2: Disabling the overlay-scrollbars:

```
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
```

#3: Possibly disabling the Firefox and/or Thunderbird global menu add-ons???????????? I'm unsure about this. I need to play around with fresh profiles and check that out.

---

### Post by zika on 2013-11-17
> **kansasnoob said:**
> #2: Disabling the overlay-scrollbars:

```
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
``````
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

---

### Post by kansasnoob on 2013-11-17
> **zika said:**
> ```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

Thanks, I'll check that out :D

---

### Post by zika on 2013-11-17
> **kansasnoob said:**
> Thanks, I'll check that out :DIf You go with dconf-editor on that address You can choose from 3 different settings, or You can list that switch with the same tool as above.

---

### Post by kansasnoob on 2013-11-17
> **zika said:**
> If You go with dconf-editor on that address You can choose from 3 different settings, or You can list that switch with the same tool as above.

Right, I need all the help I can get :)

I've just been trying to document the deprecation of gconf:

[http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12850034#post12850034](http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12850034#post12850034)

It may seem anal to look backwards but users will ask silly questions and it's beneficial to have a well documented answer easily at hand :D

BTW once I'm satisfied that documentation of the history of the "gnome-panel + metacity" GNOME 3 session is complete enough I need to do some house-keeping on my test box so I can move ahead effectively in Trusty testing. I could really use a couple of new hard drives and some other new hardware, but dental bills and vet bills make that impossible ATM.

---

### Post by kansasnoob on 2013-11-17
I've been searching w/o success, is anyone aware of an upstream bug report requesting that window management buttons be movable in 'gnome-tweak-tool'?

---

### Post by kansasnoob on 2013-11-17
As [compared to the past]("http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12850034#post12850034") metacity settings have now been totally deprecated from gconf:

[ATTACH=CONFIG]247909[/ATTACH]

I think that's a good thing :)

---

### Post by kansasnoob on 2013-11-17
> **zika said:**
> If You go with dconf-editor on that address You can choose from 3 different settings, or You can list that switch with the same tool as above.

Found it:

[ATTACH=CONFIG]247910[/ATTACH]

Time to play :)

Many thanks again.

---

### Post by Cavsfan on 2013-11-18
Since **gnome-session-flashback** is dependant on **gnome-screensaver** being installed there is no way to get a working screensaver (**xscreensaver**) in Saucy 13.10 or Trusty 14.04.
I came up with a little work around that leaves **gnome-screensaver** installed while using **xscreensaver**.

I entered this in a text editor and saved it as **killscreensaver** in my home directory.
[PHP]#! /bin/bash
sleep 60
killall gnome-screensaver  [/PHP]

Made it executable via **sudo chmod +x /home/cavsfan/killscreensaver**.
Then added **/home/cavsfan/killscreensaver** to my startup applications as well as **xscreensaver**.

It seems to like 60 seconds. I tried 20 and less and that didn't work. But 60 seconds will work every time.                 

It is mentioned [_here_]("http://ubuntuforums.org/showthread.php?t=2182038&page=2&p=12827097#post12827097").

---

### Post by zika on 2013-11-18
Wild thought:
OK, GSF needs GS to be installed as a dependency for GSF-install. But You do not need it for DM to run, don't You? 
So, editing /etc/xdg/autostart/gnome-screensaver.desktop, or renaming GS, making a symlink or similar is also a possibility...
Editing /etc/xdg/autostart/gnome-screensaver.desktop looks like a simplest way of all. Just one line to be edited.
Take a look also in ~/.config/autostart ...
It is better not to let GS to wake up, then to kill it... ;)

---

### Post by Cavsfan on 2013-11-18
> **zika said:**
> Wild thought:
OK, GSF needs GS to be installed as a dependency for GSF-install. But You do not need it for D to run, don't You? So, renaming it, making a symlink or similar is also a possibility...

Another way that did work is Mc4man's method of editing the control file for GSF and removing the dependancy, saving the deb file and dpkging it. That worked for me on 13.10.
It is also in the 13.10 work around link at the bottom of my previous post. 
But this is much easier and it works every time. Nothing else I've tried worked.

---

### Post by kansasnoob on 2013-11-18
> **zika said:**
> Wild thought:
OK, GSF needs GS to be installed as a dependency for GSF-install. But You do not need it for DM to run, don't You? 
So, editing /etc/xdg/autostart/gnome-screensaver.desktop, or renaming GS, making a symlink or similar is also a possibility...
Editing /etc/xdg/autostart/gnome-screensaver.desktop looks like a simplest way of all. Just one line to be edited.
Take a look also in ~/.config/autostart ...
It is better not to let GS to wake up, then to kill it... ;)

I'm not quite sure I understand, but if GSF = the flashback session, and if GS = gnome-shell, then that's not quite true ATM :)

On my Trusty if I install 'gnome-panel' I get a working flashback (no effects) session w/o 'gnome-shell':

```
Commit Log for Wed Oct 30 00:15:43 2013


Installed the following packages:
alacarte (3.10.0-1)
gir1.2-gconf-2.0 (3.2.6-0ubuntu1)
gir1.2-panelapplet-4.0 (1:3.6.2-0ubuntu15)
gnome-applets (3.5.92-0ubuntu3)
gnome-applets-data (3.5.92-0ubuntu3)
gnome-media (3.4.0-1ubuntu1)
gnome-panel (1:3.6.2-0ubuntu15)
gnome-panel-data (1:3.6.2-0ubuntu15)
gnome-session-flashback (1:3.6.2-0ubuntu15)
gstreamer0.10-gconf (0.10.31-3+nmu1ubuntu3)
indicator-applet (12.10.2+13.10.20130924.2-0ubuntu1)
indicator-applet-complete (12.10.2+13.10.20130924.2-0ubuntu1)
libgnome-media-profiles-3.0-0 (3.0.0-1ubuntu1)
libpanel-applet-4-0 (1:3.6.2-0ubuntu15)
metacity (1:2.34.13-0ubuntu2)
notification-daemon (0.7.6-1)
shiki-colors-metacity-theme (4.6-1ubuntu2)
```

Even installing 'gnome-tweak-tool' no longer installs 'gnome-shell':

```
Commit Log for Sun Nov 10 12:08:56 2013


Installed the following packages:
gir1.2-gdesktopenums-3.0 (3.8.0-1ubuntu1)
gir1.2-gnomedesktop-3.0 (3.8.4-0ubuntu1)
gnome-shell-common (3.8.4-0ubuntu5)
gnome-tweak-tool (3.8.1-0ubuntu1)
```

---

### Post by kansasnoob on 2013-11-18
> **Cavsfan said:**
> Since **gnome-session-flashback** is dependant on **gnome-screensaver** being installed there is no way to get a working screensaver (**xscreensaver**) in Saucy 13.10 or Trusty 14.04.
I came up with a little work around that leaves **gnome-screensaver** installed while using **xscreensaver**.

I entered this in a text editor and saved it as **killscreensaver** in my home directory.
[PHP]#! /bin/bash
sleep 60
killall gnome-screensaver  [/PHP]

Made it executable via **sudo chmod +x /home/cavsfan/killscreensaver**.
Then added **/home/cavsfan/killscreensaver** to my startup applications as well as **xscreensaver**.

It seems to like 60 seconds. I tried 20 and less and that didn't work. But 60 seconds will work every time.                 

It is mentioned [_here_]("http://ubuntuforums.org/showthread.php?t=2182038&page=2&p=12827097#post12827097").

I personally wonder why anyone wants an actual screensaver running ATM :confused:

I disliked the change to just a blank screen initially but with few CRT monitors left in the world a blank screen makes sense to me now :)

---

### Post by Alan F on 2013-11-18
> **kansasnoob said:**
> I'm not quite sure I understand, but if GSF = the flashback session, and if GS = gnome-shell, then that's not quite true ATM :)



I'm sure that you have realised by now that GS = gnome-screensaver, not gnome-shell.

I agree with you that a blank screen now makes a lot more sense than a 'traditional' screensaver

---

### Post by kansasnoob on 2013-11-18
> **Alan F said:**
> I'm sure that you have realised by now that GS = gnome-screensaver, not gnome-shell.

I agree with you that a blank screen now makes a lot more sense than a 'traditional' screensaver

No I didn't :redface:

If you google "thick" you'll find a link to "thick minded" with a picture of me :)

---

### Post by Cavsfan on 2013-11-18
> **kansasnoob said:**
> I personally wonder why anyone wants an actual screensaver running ATM :confused:

I disliked the change to just a blank screen initially but with few CRT monitors left in the world a blank screen makes sense to me now :)

You want no screensaver? Well I do and that is the only way to accomplish having Xscreensaver work.
I tried killing gnome-screensaver via system monitor but it would re-spawn on it's own. I didn't want to have to do anything manually any way.

Besides it is not a blank screen, at least not on any of my installs. It displays date and time.

This works for those that wish to have a _*working*_ screensaver. ;)

---

### Post by kansasnoob on 2013-11-18
> **Cavsfan said:**
> You want no screensaver? Well I do and that is the only way to accomplish having Xscreensaver work.
I tried killing gnome-screensaver via system monitor but it would re-spawn on it's own. I didn't want to have to do anything manually any way.

Besides it is not a blank screen, at least not on any of my installs. It displays date and time.

This works for those that wish to have a _*working*_ screensaver. ;)

Just "wanting it" **is** a valid enough reason for me :D

So when I do this Trusty "retro" thread I will try to include a link to "how to enable xcreensaver" :guitar:

I'm still trying to wrap my mind around how I should do this. ATM I'm thinking "bite-size" instead of a huge thing like this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Right now I'm still in "figuring out what to do" mode ;)

---

### Post by Cavsfan on 2013-11-20
> **kansasnoob said:**
> Just "wanting it" **is** a valid enough reason for me :D

So when I do this Trusty "retro" thread I will try to include a link to "how to enable xcreensaver" :guitar:

I'm still trying to wrap my mind around how I should do this. ATM I'm thinking "bite-size" instead of a huge thing like this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Right now I'm still in "figuring out what to do" mode ;)

+1 on that there. ;)
I'm still puzzled by the lack of interest in having a working screensaver in Gnome Flashback. It seems fairly simple to remove the requirement for **gnome-screensaver** as a dependency of **gnome-session-flashback**. 
I opened this thread [http://ubuntuforums.org/showthread.php?t=2160563](http://ubuntuforums.org/showthread.php?t=2160563)
and **mc4man** showed me how to edit the deb file and remove the dependency and I'll admit I was pretty slow about understanding how to do it but, I did finally manage it. That is how my Saucy install is right now and it works well.
Jeremy Bicha also mentioned on that thread that it wouldn't be that hard to do. But, since the fix was never put into production I just edited the deb file on Saucy after final release.

I just experimented with the script idea and that seemed like a more simple solution.
Here is the bug with me and 2 others [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)

---

### Post by kansasnoob on 2013-11-20
> **Cavsfan said:**
> +1 on that there. ;)
I'm still puzzled by the lack of interest in having a working screensaver in Gnome Flashback. It seems fairly simple to remove the requirement for **gnome-screensaver** as a dependency of **gnome-session-flashback**. 
I opened this thread [http://ubuntuforums.org/showthread.php?t=2160563](http://ubuntuforums.org/showthread.php?t=2160563)
and **mc4man** showed me how to edit the deb file and remove the dependency and I'll admit I was pretty slow about understanding how to do it but, I did finally manage it. That is how my Saucy install is right now and it works well.
Jeremy Bicha also mentioned on that thread that it wouldn't be that hard to do. But, since the fix was never put into production I just edited the deb file on Saucy after final release.

I just experimented with the script idea and that seemed like a more simple solution.
Here is the bug with me and 2 others [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)

I'm glad we're on the same page :D

While having a working screensaver is not important to me it is important to you. So I think I'll try and link to each individual "tweak" rather than lumping it all into one thread.

That should also make it easier for someone to wikify this.

Right now my biggest challenges are:

(a) Documenting the deprecation of gconf:

[http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12850034#post12850034](http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12850034#post12850034)

[http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12851127#post12851127](http://ubuntuforums.org/showthread.php?t=2090021&page=5&p=12851127#post12851127)

(b) The renaming of sessions:

[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

(c) What was (c) ............... oh yeah, my mind ain't so sharp :(

---

### Post by muktupavels on 2013-11-20
> **Cavsfan said:**
> 
I'm still puzzled by the lack of interest in having a working screensaver in Gnome Flashback. It seems fairly simple to remove the requirement for **gnome-screensaver** as a dependency of **gnome-session-flashback**.

gnome-screensaver is needed for screen lock functionality. If dependency will be removed than gnome-screensaver wont install when installing gnome-session-flashback. This will make new bug/regression. 

So I am pretty sure gnome-screensaver won't be removed as dependency for gnome-session-flashback.

And I think Jeremy Bicha solution probably wont work. Checked gnome-panel code. Gnome screensaver provides dbus service which is required in gnome-panel for lock functionality. In this case it does not matter that XScreenSaver provides lock functionality too.

---

### Post by Cavsfan on 2013-11-20
> **kansasnoob said:**
> (c) What was (c) ............... oh yeah, my mind ain't so sharp :(

LoL I'm right there with you on that point! I've had this neurological disorder for the last 12+ years and take some heavy anti-seizure medication which takes a lot out of me.
I don't like to get out but when I do I get wore out fairly easy. I've been messing with computers since I was 19 and that is probably what keeps me alive today. Always messing with something on here. :)
I can't drive which is frustrating but I ride a bike for exercise and am wore plum out after that. :D

On top of that in a couple months I'll be elgible for a senior citizens discount. :o So, I know exactly where you're coming from. The only thing that could be worse is if I had OCD. And I am not absolutely sure I don't.

Good luck on your goals! :)

---

### Post by Cavsfan on 2013-11-20
> **albertsmuktupavels said:**
> gnome-screensaver is needed for screen lock functionality. If dependency will be removed than gnome-screensaver wont install when installing gnome-session-flashback. This will make new bug/regression. 

So I am pretty sure gnome-screensaver won't be removed as dependency for gnome-session-flashback.

And I think Jeremy Bicha solution probably wont work. Checked gnome-panel code. Gnome screensaver provides dbus service which is required in gnome-panel for lock functionality. In this case it does not matter that XScreenSaver provides lock functionality too.

Gnome-screensaver is worthless IMO. It only provides a lock and I don't like having time and date displayed on my monitor forever when I could have Xscreensaver and many of it's addons displaying a working screensaverr.
Besides that Xscreensaver is being maintained while Gnome-screensaver is not. If it were this would not be a problem.
When I want my screen to lock I can just check the box on Xscreensaver. It locks just fine here.

Tell that to Jeremy Bicha. I am not sure what happened I never heard back from him. But Xscreensaver, which works can be used on Unity, Flashback, etc. and it actually works. So taking out that dependency is simple and will cause no harm that I see.
My saucy install has had the dependency removed and it works well. On Trusty I just have the script to kill gnome screensaver and they both work to my satisfaction.

---

### Post by muktupavels on 2013-11-20
> **Cavsfan said:**
> 
Tell that to Jeremy Bicha. I am not sure what happened I never heard back from him. But Xscreensaver, which works can be used on Unity, Flashback, etc. and it actually works. So taking out that dependency is simple and will cause no harm that I see.
My saucy install has had the dependency removed and it works well. On Trusty I just have the script to kill gnome screensaver and they both work to my satisfaction.

Removing dependency will make part of gnome-panel to not work. If I am not wrong than lock button applet will not work, Lock/Switch Account probably too. If it is not problem for you, it may be for others.

---

### Post by grahammechanical on 2013-11-20
Jeremy Bicha is no longer doing development work on Ubuntu Gnome. Or very little. Personal reasons.

[http://jeremy.bicha.net/](http://jeremy.bicha.net/)

> [COLOR=#555555][FONT=Arial]I&#8217;m sad to announce that due to immense personal and family responsibilities, I simply won&#8217;t have the time or ability to contribute to the Ubuntu GNOME effort much longer. [/FONT][/COLOR]

Regards.

---

### Post by Cavsfan on 2013-11-20
> **albertsmuktupavels said:**
> Removing dependency will make part of gnome-panel to not work. If I am not wrong than lock button applet will not work, Lock/Switch Account probably too. If it is not problem for you, it may be for others.

Maybe there are reasons but, there *is* a solution. The lock on Xscreensaver works just fine.

> **grahammechanical said:**
> Jeremy Bicha is no longer doing development work on Ubuntu Gnome. Or very little. Personal reasons.

[http://jeremy.bicha.net/](http://jeremy.bicha.net/)



Regards.

Yes, I remember seeing that some time ago. 

Regards.

---

### Post by muktupavels on 2013-11-20
> **Cavsfan said:**
> Maybe there are reasons but, there *is* a solution. The lock on Xscreensaver works just fine.

Best solution without much work could be moving gnome-screensaver from Depends to Recommends. This way screensaver will be installed for most users and will allow to remove it without removing flashback session. I created branch with this change and proposed for merging.

---

### Post by Cavsfan on 2013-11-21
> **albertsmuktupavels said:**
> Best solution without much work could be moving gnome-screensaver from Depends to Recommends. This way screensaver will be installed for most users and will allow to remove it without removing flashback session. I created branch with this change and proposed for merging.

That sounds like a good idea. I look forward to seeing it in Trusty. :)

---

### Post by stoneguy on 2013-11-21
Had the bright (?) idea of using Flashback as my desktop in a Lubuntu Trusty base. Appeared to have installed OK, but choosing Flashback No Effects at logon, ended up with a desktop with solid empty black panels (see att). Alt-T into a terminal got kbd operation, but nothing changed the panel contents.

Piggybacked onto Launchpad #1245209. Don't really care whether this gets fixed or disallowed. It was just another way to provide a lighter Trusty.

---

### Post by kansasnoob on 2013-11-23
I was searching for something else and stumbled upon this:

[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)

Really good info so I wanted to share it ;)

---

### Post by kansasnoob on 2013-11-23
> **stoneguy said:**
> Had the bright (?) idea of using Flashback as my desktop in a Lubuntu Trusty base. Appeared to have installed OK, but choosing Flashback No Effects at logon, ended up with a desktop with solid empty black panels (see att). Alt-T into a terminal got kbd operation, but nothing changed the panel contents.

Piggybacked onto Launchpad #1245209. Don't really care whether this gets fixed or disallowed. It was just another way to provide a lighter Trusty.

Mixing desktop environments has become more and more problematic over the past few cycles :(

---

### Post by grahammechanical on 2013-11-23
> **kansasnoob said:**
> I was searching for something else and stumbled upon this:

[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)

Really good info so I wanted to share it ;)

Interesting. And last edited an month ago. Software centre says of gnome-session-flashback - "doesn't have specific hardware requirements." Installing gnome-session-flashback also installs Metacity. Which I guess would make it kind of independent of what happens with LightDM/Compiz/Unity. Although I am curious about its reaction when it sits on top of full Mir. We wait and see.

Regards.

---

### Post by ventrical on 2013-11-23
> **grahammechanical said:**
> Interesting. And last edited an month ago. Software centre says of gnome-session-flashback - "doesn't have specific hardware requirements." Installing gnome-session-flashback also installs Metacity. Which I guess would make it kind of independent of what happens with LightDM/Compiz/Unity. Although I am curious about its reaction when it sits on top of full Mir. We wait and see.

Regards.

However , with gnome-session-flashback (with effects) one can still utilize Compiz/ccsm but there is some fanaggaling that has to be done.  One cannot have Ubuntu-desktop (Unity 3D that is not supported by graphics adapter) and gnome-session-flashback (with effects) on the same machine where Unity 3D graphics is not supported. How I was able to solve some of this quagmire was to install (fvwm-crystal) desktop and use it as an intermediary desktop to try to attempt gnome-session-flashback desktop rips. It works sometimes . It has worked on Trusty and all prior releases.

  There are also stability problems with this method and kernels that used to work on older machines are now outfitted that they shut them (previously working graphical adapters) out. I had thought that it would not be that time consuming to fork flip-back-wise so as to make the newer kernels backwards compatible with older graphics hardware and be able to insert a jockey routine to detect this so as a possible patch can be inserted from an array in the repositories for a lower version X session , or at least be provided while still running on the new release, hypothetically speaking of course. That would be real unity if that were pulled off. :)

Regards..

---

### Post by Cavsfan on 2013-11-23
> **ventrical said:**
> However , with gnome-session-flashback (with effects) one can still utilize Compiz/ccsm but there is some fanaggaling that has to be done.  One cannot have Ubuntu-desktop (Unity 3D that is not supported by graphics adapter) and gnome-session-flashback (with effects) on the same machine where Unity 3D graphics is not supported. How I was able to solve some of this quagmire was to install (fvwm-crystal) desktop and use it as an intermediary desktop to try to attempt gnome-session-flashback desktop rips. It works sometimes . It has worked on Trusty and all prior releases.

  There are also stability problems with this method and kernels that used to work on older machines are now outfitted that they shut them (previously working graphical adapters) out. I had thought that it would not be that time consuming to fork flip-back-wise so as to make the newer kernels backwards compatible with older graphics hardware and be able to insert a jockey routine to detect this so as a possible patch can be inserted from an array in the repositories for a lower version X session , or at least be provided while still running on the new release, hypothetically speaking of course. That would be real unity if that were pulled off. :)

Regards..

How ironic! From this latest install of Trusty I was only in Unity long enough to install everything I needed before going to gnome-flashback with effects. This time I didn't install gnome-flashback with Synaptic, I used apt-get in terminal. I remember it did not install a few things I forget now what the next thing I had to install but I remember gnome was not installed so I installed that and everything has been working fine. I have CCSM all setup and the cube rotating, etc.

I just checked and I do not have ubuntu-desktop installed. :) I think I did on my first install and maybe that is what messed it up. I don't know but from what you are saying that sounds probable.
I have an Nvidia Geforce 9800 GT 1TB with the 331.20 driver which was updated from what was initially on here.

---

### Post by kansasnoob on 2013-11-23
> **ventrical said:**
> However , with gnome-session-flashback (with effects) one can still utilize Compiz/ccsm but there is some fanaggaling that has to be done.  One cannot have Ubuntu-desktop (Unity 3D that is not supported by graphics adapter) and gnome-session-flashback (with effects) on the same machine where Unity 3D graphics is not supported. How I was able to solve some of this quagmire was to install (fvwm-crystal) desktop and use it as an intermediary desktop to try to attempt gnome-session-flashback desktop rips. It works sometimes . It has worked on Trusty and all prior releases.

  There are also stability problems with this method and kernels that used to work on older machines are now outfitted that they shut them (previously working graphical adapters) out. I had thought that it would not be that time consuming to fork flip-back-wise so as to make the newer kernels backwards compatible with older graphics hardware and be able to insert a jockey routine to detect this so as a possible patch can be inserted from an array in the repositories for a lower version X session , or at least be provided while still running on the new release, hypothetically speaking of course. That would be real unity if that were pulled off. :)

Regards..

I've personally never cared much for Compiz but I have found that getting it working somewhat properly is easier if I begin with an installation of Ubuntu GNOME and then install both 'gnome-panel' & 'compiz'.

---

### Post by ventrical on 2013-11-23
> **Cavsfan said:**
> How ironic! From this latest install of Trusty I was only in Unity long enough to install everything I needed before going to gnome-flashback with effects. This time I didn't install gnome-flashback with Synaptic, I used apt-get in terminal. I remember it did not install a few things I forget now what the next thing I had to install but I remember gnome was not installed so I installed that and everything has been working fine. I have CCSM all setup and the cube rotating, etc.

I just checked and I do not have ubuntu-desktop installed. :) I think I did on my first install and maybe that is what messed it up. I don't know but from what you are saying that sounds probable.
I have an Nvidia Geforce 9800 GT 1TB with the 331.20 driver which was updated from what was initially on here.

  I just can't belive this..  I have:

```

01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)
ventrical@ventrical-P4M266A-8237:~$ 


```

which I could only get to work with Unity 2D in Precise. Yesterday I zsynced trusty daily i386 and then installed it on this old machine. For reasons unbeknownst to me I was able to get Unity 3D!! It was a little slow but I wanted to install gnome-session-fallback and i did so from terminal after first loading fvwm-crystal. Gnome-session (no-effects) is just snapping fast!!! on this old machine. The only bug is a white-out at start-up with Plymouth.. but after a few seconds it goes right to lightdm. gnome-session-flashback (with effects) is a little slow , probably because of the driver, but I think the convergence and hardware open-stack endeavour is underway! :)

Thanks for your advice. I think it may be unity that is slowing down the gmone-flashback (with effects) and I'll see if I can try your way.

---

### Post by ventrical on 2013-11-23
> **kansasnoob said:**
> I've personally never cared much for Compiz but I have found that getting it working somewhat properly is easier if I begin with an installation of Ubuntu GNOME and then install both 'gnome-panel' & 'compiz'.


  I zsynced my trusty ubuntu daily and am running gnome-session (no effects) and it is super fast.

WOW! Absolutely awesome.

  Like I say .. it takes  some fanaggaling but mabey UbuntuGnome is the better way. :)

---

### Post by ventrical on 2013-11-23
Oh yeah .. this funny driver..

---

### Post by ventrical on 2013-11-23
Running unity8 on top of gnome-session-flashback (no effects) . Should we not be able to do this ?

---

### Post by Cavsfan on 2013-11-24
Not sure what I have now. I opened that thread about getting an error insalling this kernel:
```
cavsfan@cavsfan-GTO-1969:~$ uname -a
Linux cavsfan-GTO-1969 3.12.0-4-generic #10-Ubuntu SMP Thu Nov 21 22:07:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I have no option to select which session to login to for either that kernel or the previous one. It goes straight to the last session which is flashback and have nothing but a blue screen with no wallpaper and the icons are all messed up.
Might be re-install time. But, I'll play around with it first I guess.

---

### Post by kansasnoob on 2013-11-24
> **ventrical said:**
> Running unity8 on top of gnome-session-flashback (no effects) . Should we not be able to do this ?

I would think NOT! Why would you expect such a session to run on top of Metacity?

---

### Post by kansasnoob on 2013-11-24
> **Cavsfan said:**
> Not sure what I have now. I opened that thread about getting an error insalling this kernel:
```
cavsfan@cavsfan-GTO-1969:~$ uname -a
Linux cavsfan-GTO-1969 3.12.0-4-generic #10-Ubuntu SMP Thu Nov 21 22:07:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I have no option to select which session to login to for either that kernel or the previous one. It goes straight to the last session which is flashback and have nothing but a blue screen with no wallpaper and the icons are all messed up.
Might be re-install time. But, I'll play around with it first I guess.

I don't understand what you're saying :(

If you can't change the auto-login option to "off" this might be helpful:

[http://ubuntuforums.org/showthread.php?t=2183871](http://ubuntuforums.org/showthread.php?t=2183871)

---

### Post by Cavsfan on 2013-11-24
> **kansasnoob said:**
> I don't understand what you're saying :(

If you can't change the auto-login option to "off" this might be helpful:

[http://ubuntuforums.org/showthread.php?t=2183871](http://ubuntuforums.org/showthread.php?t=2183871)

Sorry, I guess that was pretty unclear. When I got the 3.12.0-4-generic kernel in an update yesterday it borked my system and I could not do anything because it got this error:
(below is output from re-installing 3.12.0-3-generic but, both of them got the error.)
The screen was blue and the icons were all hosed.

```
Setting up linux-image-extra-3.12.0-3-generic (3.12.0-3.9) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.12.0-3-generic
) points to /boot/initrd.img-3.12.0-3-generic
 (/boot/initrd.img-3.12.0-3-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-3-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.12.0-3-generic
) points to /boot/vmlinuz-3.12.0-3-generic
 (/boot/vmlinuz-3.12.0-3-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-3-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
update-initramfs: Generating /boot/initrd.img-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
```

I tried re-installing both the 3 and 4 kernels and realized nothing but a clean install would fix it.
I opened up this thread and apparently I'm not the only one:

[http://ubuntuforums.org/showthread.php?t=2189720](http://ubuntuforums.org/showthread.php?t=2189720)

Everything is back running perfectly in Gnome Flashback with effects, Compiz the cube and the whole nine yards. :)

I noticed that gnome-desktop did get installed by installing gnome this time around. This was after I installed gnome-session-flashback.

---

### Post by ventrical on 2013-11-24
> **kansasnoob said:**
> I would think NOT! Why would you expect such a session to run on top of Metacity?

  I didn't expect it to work. I just tired it and it did. (work).

---

### Post by Cavsfan on 2013-11-24
You guys didn't bomb on the 3.12.0-4-generic kernel because you've created your own custom kernel right? That's way above my pay grade. ;)

---

### Post by ventrical on 2013-11-24
> **Cavsfan said:**
> You guys didn't bomb on the 3.12.0-4-generic kernel because you've created your own custom kernel right? That's way above my pay grade. ;)


Nope . Not here . I let those geniuses Paul_in_London and VinDSL  do that ! :) lol

Regards..

---

### Post by Cavsfan on 2013-11-25
> **ventrical said:**
> Nope . Not here . I let those geniuses Paul_in_London and VinDSL  do that ! :) lol

Regards..

Ha!  Thanks for the laugh! You are right lol :)

---

### Post by kansasnoob on 2013-11-25
Things are working fairly well here. I occasionally have an app just freeze causing me to either logout and log back in (or reboot) which is inconvenient, but somewhat expected at this point in the game :)

In fact I used Trusty to produce the Quantal, Raring, and Saucy updates to this thread:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I quickly learned to "save" frequently due to those app freezes. I imagine that's on the kernel level because the moue and keyboard are still functional.

I'd love to know how we can REISUB now though :confused:

---

### Post by Cavsfan on 2013-11-25
> **kansasnoob said:**
> Things are working fairly well here. I occasionally have an app just freeze causing me to either logout and log back in (or reboot) which is inconvenient, but somewhat expected at this point in the game :)

In fact I used Trusty to produce the Quantal, Raring, and Saucy updates to this thread:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I quickly learned to "save" frequently due to those app freezes. I imagine that's on the kernel level because the moue and keyboard are still functional.

I'd love to know how we can REISUB now though :confused:

You might benefit from a new install. The ISO I got yesterday is working way better. Philinux was going to do a clean install today he said as he was also having problems with the latest kernel.
I'm not seeing any freezing of anything currently. I realize we are way early but I've installed twice and this is the best so far. :)

---

### Post by ventrical on 2013-11-25
> **Cavsfan said:**
> You might benefit from a new install. The ISO I got yesterday is working way better. Philinux was going to do a clean install today he said as he was also having problems with the latest kernel.
I'm not seeing any freezing of anything currently. I realize we are way early but I've installed twice and this is the best so far. :)

 Honest .. Gnome(no effects) hasn't worked better than this. And even on legacy machines and graphics adapters. Thats why I was surprised that Unity8 from the archives would even work on gnome-no-effects. I am not being of topic here .. but what I am trying to say is that the Unity8 shell will run this tablet/phone/unity 2D like session from terminal while I am in gnome-flashback-no-effects. Perhaps it is just an anomoly in passing .. but I thought I would report it in this forum.

Regards..

---

### Post by kansasnoob on 2013-11-26
> **kansasnoob said:**
> I was searching for something else and stumbled upon this:

[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)

Really good info so I wanted to share it ;)

I'm finding this mailing list hard to follow:

[https://mail.gnome.org/archives/gnome-flashback-list/](https://mail.gnome.org/archives/gnome-flashback-list/)

But it is certainly active :)

Anyway I noticed that we may be in for another session renaming:

[https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00013.html](https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00013.html)

> today installed trusty in virtualbox to test flashback session. Enabled proposed. After upgrade I was able to login in both sessions - flashback with metacity and flashback with compiz. Only session names seems too long for lightdm. Maybe session names can be GNOME Flashback (Metacity) and GNOME Flashback (Compiz)?


I personally think it would be better to just drop GNOME from the name ;)

Compare the length of the session names:

GNOME Flashback (no effects)
GNOME Flashback (Metacity)

Duh, it's one freaking character!

But it seems that's been approved:

[https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00014.html](https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00014.html)

](*,)

Also worried about Jonathan Carter:

[http://jonathancarter.org/2013/08/25/still-alive/](http://jonathancarter.org/2013/08/25/still-alive/)

> I’ve been really quiet on the blogging front the last few months. There’s been a lot happening in my life. In short, I moved back to South Africa and started working for another company.  I have around 10 blog drafts that I will probably never finish, so I’m just declaring post bankruptcy and starting from scratch (who wants read my old notes from Ubuntu VUDS from March anyway?)

For what it’s worth, I’m still alive and doing very well, possibly better than ever. Over the next few months I want to focus my free software time on the Edubuntu project, my Debian ITPs (which I’ve neglected so badly they’ve been turned into RFPs) and Flashback. Once I’ve caught up there’s plenty of other projects where I’d like to focus some energy as well (LTSP, Debian-Edu, just to name a few).

Anyway I have zero dev skills (+ a bum right arm on top of my brain damage) so I'd love to see someone from Ubuntu jump into the fray and try to create some focus on making this work with the Ubuntu base. If no one else steps up I'll try my best :D

In other news, there was a mention regarding 'gnome-screensaver':

[https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00015.html](https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00015.html)

---

### Post by Cavsfan on 2013-11-26
> **kansasnoob said:**
> In other news, there was a mention regarding 'gnome-screensaver':

[https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00015.html](https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00015.html)

Glad to see they are at least looking at that. Why could they not add xscreensaver as a dependency as it does indeed include a locking feature; probably due to who owns it I expect. 
They could add both gnome-screensaver and xscreensaver as recommends.

BTW I noticed that my xscreensaver didn't start up a while ago after 10 minutes I looked and it was not running.
I added the startup command to the script, logged out and back in and it worked perfectly.

[PHP]#! /bin/bash
sleep 60
killall gnome-screensaver
sleep 10
xscreensaver -nosplash [/PHP]

---

### Post by muktupavels on 2013-11-26
> **kansasnoob said:**
> 
Anyway I noticed that we may be in for another session renaming:

[https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00013.html](https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00013.html)

I personally think it would be better to just drop GNOME from the name ;)

Compare the length of the session names:

GNOME Flashback (no effects)
GNOME Flashback (Metacity)

Duh, it's one freaking character!

But it seems that's been approved:

[https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00014.html](https://mail.gnome.org/archives/gnome-flashback-list/2013-November/msg00014.html)


We have gnome-panel 3.8 in -proposed. Session names: GNOME Flashback (with Metacity) and GNOME Flashback (with Compiz). So it is more than one freaking character.

---

### Post by kansasnoob on 2013-11-26
> **Cavsfan said:**
> Glad to see they are at least looking at that. Why could they not add xscreensaver as a dependency as it does indeed include a locking feature; probably due to who owns it I expect. 
They could add both gnome-screensaver and xscreensaver as recommends.

BTW I noticed that my xscreensaver didn't start up a while ago after 10 minutes I looked and it was not running.
I added the startup command to the script, logged out and back in and it worked perfectly.

[PHP]#! /bin/bash
sleep 60
killall gnome-screensaver
sleep 10
xscreensaver -nosplash [/PHP]

That I would hate!!!!!

Why would I want Xscreensaver as a dependency when I hate it with a passion!

It makes much more sense to have the default gnome-screensaver moved to "recommends" so those who don't want it can remove it w/o forcing a personal choice on all users :D

---

### Post by kansasnoob on 2013-11-26
> **albertsmuktupavels said:**
> We have gnome-panel 3.8 in -proposed. Session names: GNOME Flashback (with Metacity) and GNOME Flashback (with Compiz). So it is more than one freaking character.

But, if I can still read, the original complaint was:

> today installed trusty in virtualbox to test flashback session. Enabled proposed. After upgrade I was able to login in both sessions - flashback with metacity and flashback with compiz. **[COLOR="#FF0000"]Only session names seems too long for lightdm.[/COLOR]** Maybe session names can be GNOME Flashback (Metacity) and GNOME Flashback (Compiz)? 

So you're now going from:

GNOME Flashback (no effects) 

to:

GNOME Flashback (with Metacity)

And from:

GNOME Flashback

to:

GNOME Flashback (with Compiz)

Compare those:

GNOME Flashback (no effects) 
GNOME Flashback (with Metacity)

GNOME Flashback
GNOME Flashback (with Compiz)

How does that even remotely address the issue of "session names seems too long for lightdm" when you're actually increasing the length of the names?

It will only serve to create more confusion:

[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

---

### Post by muktupavels on 2013-11-26
> **kansasnoob said:**
> But, if I can still read, the original complaint was:



So you're now going from:

GNOME Flashback (no effects) 

to:

GNOME Flashback (with Metacity)

And from:

GNOME Flashback

to:

GNOME Flashback (with Compiz)

Compare those:

GNOME Flashback (no effects) 
GNOME Flashback (with Metacity)

GNOME Flashback
GNOME Flashback (with Compiz)

How does that even remotely address the issue of "session names seems too long for lightdm" when you're actually increasing the length of the names?

It will only serve to create more confusion:

[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

You are wrong...

Now (current version 3.6.2):
GNOME Flashback (no effects)
GNOME Flashback

In -proposed (version 3.8.0)
GNOME Flashback (with Metacity)
GNOME Flashback (with Compiz)

And I suggested to rename to:
GNOME Flashback (Metacity)
GNOME Flashback (Compiz)

---

### Post by kansasnoob on 2013-11-26
I'm not going to apply proposed changes right now but here's what the changelog says:

> gnome-panel (1:3.8.0-1ubuntu1) trusty; urgency=low

  * Merge with Debian unstable, remaining changes:
    - Use an epoch in version number.
    - Recommend indicator-applet-complete.
    - Adjust Breaks/Replaces for Ubuntu versioning.
    - Drop 14_revert_timedate_change.patch, we are using timedated.
    - Add patches:
      + 40_unset_menuproxy.patch
      + 41_classic_layout.patch
      + 50_ubuntu_sessions.patch
      + 85_disable_shutdown_on_ltsp.patch
    - Add apport hook.
  * [B]Use new display names for sessions: "GNOME Flashback (with Compiz)"
    and "GNOME Flashback (with Metacity)"[/B].
  * Tweak the session files to always start nautilus-classic.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Fri, 22 Nov 2013 10:20:12 +0400

Those new names are longer than the old names!

---

### Post by kansasnoob on 2013-11-26
> **kansasnoob said:**
> I'm not going to apply proposed changes right now but here's what the changelog says:



Those new names are longer than the old names!

Oh, and Ubuntu GNOME may have to apply some tweaks to NOT display the Compiz session if Compiz is not installed :D

---

### Post by Hazzabin on 2013-11-26
Trusty Flashback, I've got compiz working really well, either with 'wall' or 'cube'

Only downside I've got nothing showing in top or bottom 'task-bar' or 'panels' whatever they is called both top and bottom completely black, lucky I got cairo-dock.

ideas how to fix please

---

### Post by kansasnoob on 2013-11-27
> **albertsmuktupavels said:**
> You are wrong...

Now (current version 3.6.2):
GNOME Flashback (no effects)
GNOME Flashback

In -proposed (version 3.8.0)
GNOME Flashback (with Metacity)
GNOME Flashback (with Compiz)

And I suggested to rename to:
GNOME Flashback (Metacity)
GNOME Flashback (Compiz)

I see now, you were referring to the change that's coming in proposed.

---

### Post by zika on 2013-11-27
Why is the name of the session (so) important?
In how many occasions do You see that name?

---

### Post by kansasnoob on 2013-11-27
> **zika said:**
> Why is the name of the session (so) important?
In how many occasions do You see that name?

Eeerm, it's just the matter of constant renaming creating confusion. I know we had to rename from "classic" to "fallback" to accommodate the new gnome-shell/mutter based classic session, but I never understood the need for the rename to flashback. We need to settle on a sensible session name at some point and stick with it :)

---

### Post by zika on 2013-11-27
> **kansasnoob said:**
> Eeerm, it's just the matter of constant renaming creating confusion. I know we had to rename from "classic" to "fallback" to accommodate the new gnome-shell/mutter based classic session, but I never understood the need for the rename to flashback. We need to settle on a sensible session name at some point and stick with it :)I'm a guy interested (only) in substance... You could call it (random sequence of symbols) and I would not care as long as it works as it should or better... ;)

---

### Post by PJs Ronin on 2013-11-27
Not that I know squat....

But the naming issue is important to me because the last time I tried to use a 'gnome' I couldn't make it do what I wanted it to do and what I believed it could do.   Turns out I was making changes in Compiz that were not being reflected in gnome because the gnome I was using relied on metacity.   As a noob I thought CCSM would make changes across any 'gnome' (wrong!) and at the end of it I don't even know which gnome I was using so I gave the whole thing away and relied on Unity.   I fully admit my inexperience was a major cause of my problems, but the gnome name changes, especially where there is a similarity for different flavors, didn't help.

I'd really like to try gnome again, but until I can get a definitive "who's who in the gnome zoo" I won't touch it with a barge pole.

---

### Post by kansasnoob on 2013-11-27
> **zika said:**
> I'm a guy interested (only) in substance... You could call it (random sequence of symbols) and I would not care as long as it works as it should or better... ;)

It becomes substantive because you have to be able to explain to the uninformed end user what the different session names mean ;)

A few people had posted about confusion with the new GNOME classic session not being "editable" as the older "classic" and "classic (no effects)" sessions were.

Now that I understand what's going on I agree with *albertsmuktupavels*, just dropping the word "with" from the session names in Trusty-proposed makes sense, I was simply confused by what the names are in Trusty-now and who was proposing what :D

Sometimes I'm thick like that :redface:

---

### Post by kansasnoob on 2013-11-27
> **Hazzabin said:**
> Trusty Flashback, I've got compiz working really well, either with 'wall' or 'cube'

Only downside I've got nothing showing in top or bottom 'task-bar' or 'panels' whatever they is called both top and bottom completely black, lucky I got cairo-dock.

ideas how to fix please

I've been focusing solely on Flashback (Metacity) so I'm clueless, but I wanted to bump this so it's not lost in the session name chatter :D

---

### Post by muktupavels on 2013-11-27
> **Hazzabin said:**
> Trusty Flashback, I've got compiz working really well, either with 'wall' or 'cube'

Only downside I've got nothing showing in top or bottom 'task-bar' or 'panels' whatever they is called both top and bottom completely black, lucky I got cairo-dock.

ideas how to fix please

1) Are you only one with black panels or there are other users with same problem?
2) Black panels with both session? metacity and compiz.
3) Can you access panel properties? Alt + Right click on panel.

---

### Post by zika on 2013-11-27
> **albertsmuktupavels said:**
> 1) Are you only one with black panels or there are other users with same problem?
Saucy:zika:super-latestGnome:No, he is not the only one.
> **albertsmuktupavels said:**
>  2) Black panels with both session? metacity and compiz.
Saucy:zika:super-latestGnome:Yes, partly...
> **albertsmuktupavels said:**
>  3) Can you access panel properties? Alt + Right click on panel.
Saucy:zika:super-latestGnome:No.

Not to mention that yesterday I think GnomeClassic showed itself as GnomeShell. No time to go and see what is going on, will do that as soon as I get free man/machine minute.

---

### Post by kansasnoob on 2013-11-27
> **PJs Ronin said:**
> Not that I know squat....

But the naming issue is important to me because the last time I tried to use a 'gnome' I couldn't make it do what I wanted it to do and what I believed it could do.   Turns out I was making changes in Compiz that were not being reflected in gnome because the gnome I was using relied on metacity.   As a noob I thought CCSM would make changes across any 'gnome' (wrong!) and at the end of it I don't even know which gnome I was using so I gave the whole thing away and relied on Unity.   I fully admit my inexperience was a major cause of my problems, but the gnome name changes, especially where there is a similarity for different flavors, didn't help.

I'd really like to try gnome again, but until I can get a definitive "who's who in the gnome zoo" I won't touch it with a barge pole.

I appreciate your concerns, they are shared by me :)

While I try to stay somewhat up-to-date on the changes as they pour in I find that it becomes more and more complicated to explain these changes to others :(

In order to keep this thread on topic I posted a response here:

[http://ubuntuforums.org/showthread.php?t=2090021&page=6&p=12859103#post12859103](http://ubuntuforums.org/showthread.php?t=2090021&page=6&p=12859103#post12859103)

But it's certainly worth following up on here at Ubuntu +1, lets just try to keep it related to Trusty here so the mods don't shut me down.

**Who's who in the GNOME zoo** is a valid question for sure :guitar:

And I hope I began to answer that.

---

### Post by Hazzabin on 2013-11-27
I've only just gotten the choice of 'Metacity' and 'Compiz' for "Flashback"
Metacity totally just doesn't want to work, Compiz is ok-ish but still no nothing in either top or bottom bars, cannot even do a right click for bar properties

I did try and install nvidia drivers thinking that maybe causing some of my issues, it completely crashed.......new install using 26th Nov ISO

Sure is looking like for now staying with the basic 'Gnome' for "Trusty"

ok pass my bedtime, will catch up with this in my tomorrow

---

### Post by muktupavels on 2013-11-27
One more question...

You all get black panel with clean install without adding additional ppa's?

On my main install gnome flashback works with metacity, compiz and even with mutter. I have installed all updates. I have not added any additional ppa's. I have installed nvidia drivers from nvidia.com. I also tried trusty daily iso in virtualbox to test gnome panel 3.8.0 version. I had no problems.

---

### Post by kansasnoob on 2013-11-27
> **Hazzabin said:**
> I've only just gotten the choice of 'Metacity' and 'Compiz' for "Flashback"
Metacity totally just doesn't want to work, Compiz is ok-ish but still no nothing in either top or bottom bars, cannot even do a right click for bar properties

I did try and install nvidia drivers thinking that maybe causing some of my issues, it completely crashed.......new install using 26th Nov ISO

Sure is looking like for now staying with the basic 'Gnome' for "Trusty"

ok pass my bedtime, will catch up with this in my tomorrow

If your login options are already showing Classic (with Metacity) and Classic (with Compiz) then you're using Trusty-proposed.  In that case you should read here what it says about using the proposed repos in testing:

[http://ubuntuforums.org/showthread.php?t=2181769](http://ubuntuforums.org/showthread.php?t=2181769)

Actually just noticed that it says:

> Warning: Unless you are willing to have a broken system, please make sure that that **[COLOR="#FF0000"]Pre-released updates [/COLOR]**are disabled in Software & Updates, as this repository is now used as a holding area while packages are waiting for dependencies to be built.

I'll ask about that :)

---

### Post by Cavsfan on 2013-11-27
> **Cavsfan said:**
> Glad to see they are at least looking at that. Why could they not add xscreensaver as a dependency as it does indeed include a locking feature; probably due to who owns it I expect. 
[COLOR=#ff0000]They could add both gnome-screensaver and xscreensaver as recommends.[/COLOR]

BTW I noticed that my xscreensaver didn't start up a while ago after 10 minutes I looked and it was not running.
I added the startup command to the script, logged out and back in and it worked perfectly.

[PHP]#! /bin/bash
sleep 60
killall gnome-screensaver
sleep 10
xscreensaver -nosplash [/PHP]

> **kansasnoob said:**
> That I would hate!!!!!

Why would I want Xscreensaver as a dependency when I hate it with a passion!

It makes much more sense to have the default gnome-screensaver moved to "recommends" so those who don't want it can remove it w/o forcing a personal choice on all users :D

I did say they could add either as recommends just get it out of dependency. 
Oh yeah I forgot you don't use screensavers.

---

### Post by Hazzabin on 2013-11-27
> **albertsmuktupavels said:**
> One more question...

You all get black panel with clean install without adding additional ppa's?

On my main install gnome flashback works with metacity, compiz and even with mutter. I have installed all updates. I have not added any additional ppa's. I have installed nvidia drivers from nvidia.com. I also tried trusty daily iso in virtualbox to test gnome panel 3.8.0 version. I had no problems.

Correct, least that's what is happening to me

I've got a spare partition and am going to try another fresh install, will report on the outcome of that later

---

### Post by kansasnoob on 2013-11-29
Now that the upstream flashback updates were moved up from proposed I totally see what Alberts was saying. The new session name is too long for 'unity-greeter':

[ATTACH=CONFIG]248188[/ATTACH]

But it's OK in both 'gdm' and the 'gtk-greeter':

[ATTACH=CONFIG]248189[/ATTACH]

[ATTACH=CONFIG]248190[/ATTACH]

Should I file a bug at Launchpad?

---

### Post by muktupavels on 2013-11-29
> **kansasnoob said:**
> Now that the upstream flashback updates were moved up from proposed I totally see what Alberts was saying. The new session name is too long for 'unity-greeter':

[ATTACH=CONFIG]248188[/ATTACH]

But it's OK in both 'gdm' and the 'gtk-greeter':

[ATTACH=CONFIG]248189[/ATTACH]

[ATTACH=CONFIG]248190[/ATTACH]

Should I file a bug at Launchpad?

No.

If it will be approved than upstream will provide 3 session - GNOME Flashback (Metacity), GNOME Flashback (Compiz) and GNOME Flashback (Mutter). There are patches for this already.

My idea for ubuntu was to provide two extra packages for flashback - gnome-session-flashback (default, installs only metacity session), gnome-session-flashback-compiz (new) and gnome-session-flashback-mutter (new).

---

### Post by kansasnoob on 2013-11-29
> **Cavsfan said:**
> I did say they could add either as recommends just get it out of dependency. 
Oh yeah I forgot you don't use screensavers.

I happened to think about this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/988290)

I mentioned it on the forums:

[http://ubuntuforums.org/showthread.php?t=2036864](http://ubuntuforums.org/showthread.php?t=2036864)

So I knew that I could swap 'xscreensaver' for 'gnome-screensaver' at that time and I checked in Precise again and that's still true.

But somewhere between Precise and Saucy they screwed the dependencies :(

---

### Post by kansasnoob on 2013-11-29
> **albertsmuktupavels said:**
> No.

If it will be approved than upstream will provide 3 session - GNOME Flashback (Metacity), GNOME Flashback (Compiz) and GNOME Flashback (Mutter). There are patches for this already.

My idea for ubuntu was to provide two extra packages for flashback - gnome-session-flashback (default, installs only metacity session), gnome-session-flashback-compiz (new) and gnome-session-flashback-mutter (new).

Now you're misunderstanding me :)

Those screenshots are what things look like right now with the current Trusty updates in place using the US d/l mirror.

I understand that you want to shorten them by removing the word "with", which is fine :D

Are we on the same page now :confused:

EDIT: Just jumped over to the mailing list and I see what you mean now. Would it be OK for me to subscribe to that mailing list so I can stay up to date better?

I'm not a dev by any means but the Metacity session is important to me.

---

### Post by muktupavels on 2013-11-29
> **kansasnoob said:**
> Would it be OK for me to subscribe to that mailing list so I can stay up to date better?

Why are you asking this? I think that you can freely subscribe to any mailing list you want. They are not restricted to devs only.

> **kansasnoob said:**
> I'm not a dev by any means but the Metacity session is important to me.

Why Metacity? Have you tried to use mutter? If you have time you could install mutter to test it. Than from terminal run:
```
mutter --replace
```

For me mutter session works, but I have no time to actively test it.

---

### Post by kansasnoob on 2013-11-29
> **albertsmuktupavels said:**
> Why are you asking this? I think that you can freely subscribe to any mailing list you want. They are not restricted to devs only.



Why Metacity? Have you tried to use mutter? If you have time you could install mutter to test it. Than from terminal run:
```
mutter --replace
```

For me mutter session works, but I have no time to actively test it.

I maintain a lot of low-end hardware so I'm always looking at options that use the least resources.

I'll just subscribe I guess but I'm a real dummy :(

---

### Post by grahammechanical on 2013-11-29
I was out and about yesterday so I did not get the change from flashback and flashback (no effects) to flashback (compiz) and flashback (metacity) until just now (early afternoon - UK). This is what I have found in my very unscientific experimentation using System Monitor.

1) there is a long delay for the app indicators (network, sound, calendar, power cog) to appear both with flashback (compiz ) and with flashback (metacity)

2) memory footprint is greatest with Ubuntu+Unity then with either flashback and flashback (metacity) has the lower memory footprint.

3) to have the lowest memory footprint remove (if possible) any app indicators that are useful but not necessary. The app indicators push flashback memory footprint from just over 200 MiB to well over 300 Mib.

Regards.

---

### Post by ventrical on 2013-11-30
> **grahammechanical said:**
> I was out and about yesterday so I did not get the change from flashback and flashback (no effects) to flashback (compiz) and flashback (metacity) until just now (early afternoon - UK). This is what I have found in my very unscientific experimentation using System Monitor.

1) there is a long delay for the app indicators (network, sound, calendar, power cog) to appear both with flashback (compiz ) and with flashback (metacity)

Regards.

+1..

Yeah .. really weird .. I thought the desktop was busted , but it came up after while.

---

### Post by kansasnoob on 2013-11-30
> **ventrical said:**
> +1..

Yeah .. really weird .. I thought the desktop was busted , but it came up after while.

Very, very slowly ........... perhaps two to three minutes.

---

### Post by mc4man on 2013-11-30
> **grahammechanical said:**
> I was out and about yesterday so I did not get the change from flashback and flashback (no effects) to flashback (compiz) and flashback (metacity) until just now (early afternoon - UK). This is what I have found in my very unscientific experimentation using System Monitor.

1) there is a long delay for the app indicators (network, sound, calendar, power cog) to appear both with flashback (compiz ) and with flashback (metacity)


On a fresh install with decent hardware see no delay, Desktop loads with indicators in place (& all fully functional

So maybe old install and or older hardware?

Do see a possible upcoming issue with some possible changes in xorg-xserver that could appear when using a usb mouse but have to wait & see what/if xorg is upgraded to.

---

### Post by ventrical on 2013-11-30
> **mc4man said:**
> On a fresh install with decent hardware see no delay, Desktop loads with indicators in place (& all fully functional

So maybe old install and or older hardware?


nVidia Ge210/218 a@ 4.167GHz .. very slow to load desktop..


```

Linux ventrical-System-Product-Name 3.12.0-4-generic #12-Ubuntu SMP Tue Nov 26 22:41:11 UTC 2013 i686 i686 i686 GNU/Linux
ventrical@ventrical-System-Product-Name:~$ 


```

edit::   Seems to be isolated to nVidia graphics. Works really snappy on Intel Core2Duo, Intel(R) 965Q .

---

### Post by ventrical on 2013-11-30
> **kansasnoob said:**
> Very, very slowly ........... perhaps two to three minutes.


Ran it on an AMD Athlon 6000 2X Dual with nVidia GeForce 210/218 and it took over a minute for the desktop to show up after recent updates. So thats 2 nVidia adaptors emulating this behaviour.

 Looks like nVidia problem with nouveau ?

Gallium 0.4 on NVA8

---

### Post by mc4man on 2013-11-30
> **ventrical said:**
> Ran it on an AMD Athlon 6000 2X Dual with nVidia GeForce 210/218 and it took over a minute for the desktop to show up after recent updates. So thats 2 nVidia adaptors emulating this behaviour.

 Looks like nVidia problem with nouveau ?

Gallium 0.4 on NVA8
I can't ck. nouveau on this machine, it's either Intel or Nvidia thru nvidia-prime. 
The former works great, while the later works there are certainly issues, mainly with gnome-settings-daemon which always crashes. 
In the case of gnome-flashback session,  g-s-d crashing causes all sorts of issues including missing indicators & wrong theming for gtk2 apps

(likely no real comparison between Nvidia or nouveau & nvidia-prime.., but you could check your various logs, probably in .cache/upstart

---

### Post by Alan F on 2013-12-01
Its not just Nvidia that is causing the problem. I am getting the same thing with Intel graphics.

If you watch System Monitor processes you will see that Compiz and Unity-system-compositor come to life when the problem clears (Flashback with compiz)

---

### Post by kansasnoob on 2013-12-01
OK, my Ubuntu install is getting a bit long in the tooth:

> Ubuntu 14.04 LTS "Trusty Tahr" - Release i386 (20131021.1)

But I get the same results from this Ubuntu GNOME install:

> Ubuntu-GNOME 14.04 "Trusty Tahr" - Alpha i386 (20131126)

I should maybe note that I'm sure it's not due to the display manager because Ubuntu uses lightdm with the unity-greeter, while Ubuntu GNOME uses gdm, and I've tried lightdm with the gtk-greeter in Ubuntu GNOME with the same results.

I'm using bare metal:

> Intel Atom CPU  230 @ 1.60GHz
**Intel 82945G/GZ Integrated Graphics Controller (rev 02)**
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

And when I initially boot into Trusty Flashback using either Metacity or Compiz I get a basically blank screen other than gnome-panel:

[ATTACH=CONFIG]248224[/ATTACH]

Then I must wait between 2 to 3 minutes for the rest of the desktop to load and for the menus and apps to respond :(

Edit: I just decided to try the standard Ubuntu/Unity DE and it also loads very slowly on a full reboot.

---

### Post by mc4man on 2013-12-01
Well I resurrected an older laptop (core2duo, nvidia 8400m, 6-7 year old hdd, ect.

On login both the gnome panels show immediately but -
The sound, datetime & session indicators take about 1 min to appear
nautilus is not handling the Desktop until either clicking on anything in Places or waiting until the 3 missing indicators load

---

### Post by Cavsfan on 2013-12-01
Same here. Nvidia driver 319.32 in flashback. The panels appear quickly but, it takes 2-3 minutes (it seems) for the wallpaper, Cairo Dock, etc. to come up.
Compiz also uses a lot of CPU as well. Because of this I haven't been staying in Trusty for all that long at a time.

---

### Post by mc4man on 2013-12-01
The issue with the slow loading indicators & nautilus is likely from the new glib source.
At least here downgrading to previous version & they load up fine (libglib2.0-0 (2.38.1-1) 

So that's repairable, look for new flashback builds down the road

---

### Post by kansasnoob on 2013-12-01
> **mc4man said:**
> The issue with the slow loading indicators & nautilus is likely from the new glib source.
At least here downgrading to previous version & they load up fine (libglib2.0-0 (2.38.1-1) 

So that's repairable, look for new flashback builds down the road

In deed, I've reminded two people in recent days that we're still really pre-alpha ;)

---

### Post by kansasnoob on 2013-12-01
> **kansasnoob said:**
> I was searching for something else and stumbled upon this:

[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)

Really good info so I wanted to share it ;)

Address change:

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

---

### Post by ventrical on 2013-12-01
> **mc4man said:**
> Well I resurrected an older laptop (core2duo, nvidia 8400m, 6-7 year old hdd, ect.

On login both the gnome panels show immediately but -
The sound, datetime & session indicators take about 1 min to appear
nautilus is not handling the Desktop until either clicking on anything in Places or waiting until the 3 missing indicators load


Thats exactly it on my nVidia based machines.

---

### Post by QDR06VV9 on 2013-12-01
> **ventrical said:**
> Thats exactly it on my nVidia based machines.

Well I guess i'll make it unanimous.:D[h=3][/h]

---

### Post by Hazzabin on 2013-12-01
> **mc4man said:**
> The issue with the slow loading indicators & nautilus is likely from the new glib source.
At least here downgrading to previous version & they load up fine (libglib2.0-0 (2.38.1-1) 

So that's repairable, look for new flashback builds down the road

thanks for that info

I can't seem to downgrade as it's only showing the latest libclib (2.39 something) any ideas how to find and re-install that older one

---

### Post by ventrical on 2013-12-01
> **runrickus said:**
> Well I guess i'll make it unanimous.:D

+1 :)

---

### Post by mc4man on 2013-12-02
> **Hazzabin said:**
> thanks for that info

I can't seem to downgrade as it's only showing the latest libclib (2.39 something) any ideas how to find and re-install that older one

Well you go here for i386 
[https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135941](https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135941)

 amd64 users need 2 i386 packages from above  in addition to whichever amd64 ones they need from below link
[https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135938](https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135938)

To see what packages you can either search libglib2 in synaptic or this in terminal, look for 'Installed: 2.39.....'
apt-cache policy libglib2.0*

Download all needed, put in a created folder, cd to in a terminal & run this. If any error then read, fix & rerun command till good
sudo dpkg -i *.deb

typical 4 packages for amd64 shown in screen, the 2 all.debs are from i386 link

---

### Post by Cavsfan on 2013-12-02
> **mc4man said:**
> Well you go here for i386 
[https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135941](https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135941)

 amd64 users need 2 i386 packages from above  in addition to whichever amd64 ones they need from below link
[https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135938](https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135938)

To see what packages you can either search libglib2 in synaptic or this in terminal, look for 'Installed: 2.39.....'
apt-cache policy libglib2.0*

Download all needed, put in a created folder, cd to in a terminal & run this. If any error then read, fix & rerun command till good
sudo dpkg -i *.deb

typical 4 packages for amd64 shown in screen, the 2 all.debs are from i386 link

Kewl mon! That fixed it up for me! Back in the thick of it. :) Thanks!

---

### Post by Cavsfan on 2013-12-02
One question though. How do you prevent it from upgrading back to the 2.39.1 version.
After setting it back to 2.38.1, this is waiting:

```
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libglib2.0-0 libglib2.0-bin libglib2.0-data libglib2.0-doc libnautilus-extension1a nautilus nautilus-data
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,206 kB of archives.
After this operation, 937 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy libglib2.0-0
libglib2.0-0:
  Installed: 2.38.1-1
  Candidate: 2.39.1-0ubuntu2
  Version table:
     2.39.1-0ubuntu2 0
        500 http://ubuntu.wikimedia.org/ubuntu/ trusty/main amd64 Packages
 *** 2.38.1-1 0
        100 /var/lib/dpkg/status

```

---

### Post by Cavsfan on 2013-12-02
Never mind I may have stumbled upon the answer:

**Using apt**
  *you can hold a package using*
  sudo apt-mark hold package_name
  *and remove the hold with*
  sudo apt-mark unhold package_name

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-0
[sudo] password for cavsfan: 
libglib2.0-0 set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-bin
libglib2.0-bin set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-data
libglib2.0-data set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-doc
libglib2.0-doc set on hold.
```

---

### Post by ventrical on 2013-12-02
> **mc4man said:**
> Well you go here for i386 
[https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135941](https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135941)

 amd64 users need 2 i386 packages from above  in addition to whichever amd64 ones they need from below link
[https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135938](https://launchpad.net/ubuntu/+source/glib2.0/2.38.1-1/+build/5135938)

To see what packages you can either search libglib2 in synaptic or this in terminal, look for 'Installed: 2.39.....'
apt-cache policy libglib2.0*




 I checked it out in synaptic and it wants to remove several depends and other programs if one tries to use the >force Version option from Packages.

---

### Post by zika on 2013-12-02
> **Cavsfan said:**
> Never mind I may have stumbled upon the answer:

**Using apt**
  *you can hold a package using*
  sudo apt-mark hold package_name
  *and remove the hold with*
  sudo apt-mark unhold package_name

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-0
[sudo] password for cavsfan: 
libglib2.0-0 set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-bin
libglib2.0-bin set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-data
libglib2.0-data set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-doc
libglib2.0-doc set on hold.
```Beware: hold (i.e. lock on package version) is not always transferable/honored between frontends (synaptic, aptiptude etc...) There was a detailed thread about that in which I've showed certain exceptions.

---

### Post by Cavsfan on 2013-12-02
> **Cavsfan said:**
> Never mind I may have stumbled upon the answer:

**Using apt**
  *you can hold a package using*
  sudo apt-mark hold package_name
  *and remove the hold with*
  sudo apt-mark unhold package_name

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-0
[sudo] password for cavsfan: 
libglib2.0-0 set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-bin
libglib2.0-bin set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-data
libglib2.0-data set on hold.
cavsfan@cavsfan-MS-7529:~$ sudo apt-mark hold libglib2.0-doc
libglib2.0-doc set on hold.
```

> **zika said:**
> Beware: hold (i.e. lock on package version) is not always transferable/honored between frontends (synaptic, aptiptude etc...) There was a detailed thread about that in which I've showed certain exceptions.

I don't have a clue about where this goes from here but it sure did fix the problem. Trusty works in Flashback like a new one. **mc4man** helped the situation tremendously. I'll take my chances with this versus what I had before. 

```
Fetched 27.0 MB in 23s (1,137 kB/s)                                                                                                                                                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
 [COLOR=#ff0000] libglib2.0-0 libglib2.0-bin libglib2.0-data libglib2.0-doc[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
cavsfan@cavsfan-MS-7529:~$ 
```

Plus I always use terminal to get my updates and it seems to be doing well.

---

### Post by ventrical on 2013-12-02
> **Cavsfan said:**
> I don't have a clue about where this goes from here but it sure did fix the problem. Trusty works in Flashback like a new one. **mc4man** helped the situation tremendously. I'll take my chances with this versus what I had before. 

```
Fetched 27.0 MB in 23s (1,137 kB/s)                                                                                                                                                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
 [COLOR=#ff0000] libglib2.0-0 libglib2.0-bin libglib2.0-data libglib2.0-doc[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
cavsfan@cavsfan-MS-7529:~$ 
```

Plus I always use terminal to get my updates and it seems to be doing well.

 But when the fix/upgrade comes in and the old libglib2.0-0 gets obsoleted and the depends also get upgraded then does not the kernel/OS look for the upgraded libglib and not finding it, it breaks the depends eventually? I'm just asking.

Regards..

---

### Post by zika on 2013-12-03
> **Cavsfan said:**
> I don't have a clue about where this goes from here but it sure did fix the problem. Trusty works in Flashback like a new one. **mc4man** helped the situation tremendously. I'll take my chances with this versus what I had before. 
...Plus I always use terminal to get my updates and it seems to be doing well.I did not object to the solution to Your problem You've found.I've just wanted to caution You that Your lock could open if Yuo would use another fontend to try to upgrade. Since You do use only CLI and, probably, only the same frontend all the time, You're safe.

---

### Post by kansasnoob on 2013-12-03
I personally prefer just waiting for the fix to drop ;)

The more I tweak the less I end up knowing about actual existing bugs, and we are pre-alpha :)

---

### Post by Cavsfan on 2013-12-03
I have no idea what I'm doing lol. I just thought I would try **mc4man**'s solution. **Zika** it's not my solution. Look back at post #149. I'm willing to admit that I'm not smart enough to come up with this solution. :lol:

I just checked what is in the updates and there is a kernel and some other stuff. I guess I'll take the hold off those 4 and let it happen. I don't have the slightest clue as to what **libglib** is or does. I was just glad that I found **mc4man**'s post and fix because it made it usable again. If it's still screwed up after these updates I'll probably repeat the fix from post #149. I still have the debs and the folder. 

So, here goes. *holds breath* :lol:

---

### Post by ventrical on 2013-12-03
> **Cavsfan said:**
> I have no idea what I'm doing lol. I just thought I would try **mc4man**'s solution. **Zika** it's not my solution. Look back at post #149. I'm willing to admit that I'm not smart enough to come up with this solution. :lol:

I just checked what is in the updates and there is a kernel and some other stuff. I guess I'll take the hold off those 4 and let it happen. I don't have the slightest clue as to what **libglib** is or does. I was just glad that I found **mc4man**'s post and fix because it made it usable again. If it's still screwed up after these updates I'll probably repeat the fix from post #149. I still have the debs and the folder. 

So, here goes. *holds breath* :lol:


At least you're  having fun:)   Explore away !!!!  :) It's amazing  how things get discovered when we do proceedures ie; as mac4man has suggested.

Regards..

---

### Post by Cavsfan on 2013-12-03
> **kansasnoob said:**
> I personally prefer just waiting for the fix to drop ;)

The more I tweak the less I end up knowing about actual existing bugs, and we are pre-alpha :)

Yes, I am aware we are pre-alpha and letting those 4 files upgrade made it go back like it was slooooooooooooooow after the panels appear.

 Is everyone getting this error when a kernel gets installed as I just did on the 3.12.0-5-generic kernel:
```
Setting up linux-image-extra-3.12.0-5-generic (3.12.0-5.13) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.12.0-5-generic
) points to /boot/initrd.img-3.12.0-5-generic
 (/boot/initrd.img-3.12.0-5-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-5-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.12.0-5-generic
) points to /boot/vmlinuz-3.12.0-5-generic
 (/boot/vmlinuz-3.12.0-5-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-5-generic.postinst line 491.

```
I don't see the CPU being used excessively like before though.

It's a good thing I have VinDSL's conky so I can see what is happening in real time.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2013-12-03125133.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2013-12-03125133.php")

I wonder what **mc4man**'s take is on this. He must have performed the steps he mentioned in post #149.

---

### Post by mc4man on 2013-12-03
I looked for a current bug the other other day, didn't find so filed here &  for the moment  may be applicable -
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

(- I never pin anything, if I don't want something upgraded then I simply don't upgrade it. This can be done easily in synaptic or thru sudo apt-get install --only-upgrade packagename(s) though both are not without potential pitfalls

---

### Post by Cavsfan on 2013-12-03
> **ventrical said:**
> At least you're  having fun:)   Explore away !!!!  :) It's amazing  how things get discovered when we do proceedures ie; as mac4man has suggested.

Regards..

Indeed I am having fun! :lol:

> **mc4man said:**
> I looked for a current bug the other other day, didn't find so filed here &  for the moment  may be applicable -
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

(- I never pin anything, if I don't want something upgraded then I simply don't upgrade it. This can be done easily in synaptic or thru sudo apt-get install --only-upgrade packagename(s) though both are not without potential pitfalls

Thanks and I'll do that with the upgrading but it seems a bit tedious when many files need updated. I added my name to the bug. Are you all getting the error I mentioned?
**doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-5-generic.postinst line 491.**

But I can see doing it with Synaptic pretty easily.

Thanks for the replies. :)

---

### Post by kansasnoob on 2013-12-03
> **mc4man said:**
> I looked for a current bug the other other day, didn't find so filed here &  for the moment  may be applicable -
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

(- I never pin anything, if I don't want something upgraded then I simply don't upgrade it. This can be done easily in synaptic or thru sudo apt-get install --only-upgrade packagename(s) though both are not without potential pitfalls

Me-too'ed & subscribed :)

I suspect at this point we just need to wait for the various teams to get into sync.

---

### Post by mc4man on 2013-12-03
> **Cavsfan said:**
> Are you all getting the error I mentioned?
**doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-5-generic.postinst line 491.**


I don't believe that's an error, while I can't profess to really understand I take "doing nothing" as a message that nothing needs to be done in 'whatever' regard (already properly linked?

So if interested take a look at /var/lib/dpkg/info/linux-image-extra-3.12.0-5-generic.postinst line 491 & see. (as said I don't really understand it, just looking at logically

 ```

489    }
490    else {                  # already have proper link
491      warn "$kimage($vmlinuz_target) points to $target ($real_target) -- doing nothing";
492      $force_move = 0;
493     }
494     return $force_move;
```

---

### Post by ventrical on 2013-12-03
Looks like the libglib2.0-0 is in the upgrade.

Here goes..

edit:

Wrong machine. Belay my last..

---

### Post by ventrical on 2013-12-03
Ok .. got the latest kernel update and it knocked out my 'Ring Switcher' function from ccsm and set it to 'Shift Switcher'. Also reset number of desktops to 1. Now cannot get ring switcher to work  on Trusty gnome-flashback (with compiz).

---

### Post by Cavsfan on 2013-12-03
> **kansasnoob said:**
> Me-too'ed & subscribed :)

I suspect at this point we just need to wait for the various teams to get into sync.

Good deal. I went ahead and downgraded the packages, rebooted and it's back to being very fast. Man it was as slow as my windows 7 booting up. Can't have none of that. ;)
But, this time as suggested I will not lock the packages. I will just selectively upgrade all but those 4 packages.

> **mc4man said:**
> I don't believe that's an error, while I can't profess to really understand I take "doing nothing" as a message that nothing needs to be done in 'whatever' regard (already properly linked?

So if interested take a look at /var/lib/dpkg/info/linux-image-extra-3.12.0-5-generic.postinst line 491 & see. (as said I don't really understand it, just looking at logically

 ```

489    }
490    else {                  #[COLOR=#ff0000] already have proper link[/COLOR]
491      warn "$kimage($vmlinuz_target) points to $target ($real_target) -- doing nothing";
492      $force_move = 0;
493     }
494     return $force_move;
```

So, I take it you're getting the same thing and if you say so I will not worry about it. Looking at the red on the else it does look like it's already linked.
Thanks for showing that.

> **ventrical said:**
> Looks like the libglib2.0-0 is in the upgrade.

Here goes..

edit:

Wrong machine. Belay my last..

Man are we having fun or what? :lol: Thanks to all of you for helping me learn this stuff. I love learning new things.

So, I guess when the new fixed libglib comes down the pipe it will only install the latest version. Would that be correct? What will become of the bad packages when that happens?

---

### Post by Cavsfan on 2013-12-03
> **ventrical said:**
> Ok .. got the latest kernel update and it knocked out my 'Ring Switcher' function from ccsm and set it to 'Shift Switcher'. Also reset number of desktops to 1. Now cannot get ring switcher to work  on Trusty gnome-flashback (with compiz).

I always for the past three or four versions have used Application Switcher in Flashback and have never had a problem. I have had the same problems you mention with any of the other ones so I stick with this one in the top left of CCSM Window Management.
It's not perfect and it appears confusing but it works every time.

---

### Post by Cavsfan on 2013-12-04
> **mc4man said:**
> I looked for a current bug the other other day, didn't find so filed here &  for the moment  may be applicable -
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

(- I never pin anything, if I don't want something upgraded then I simply don't upgrade it. This can be done easily in synaptic or thru sudo apt-get install --only-upgrade packagename(s) though both are not without potential pitfalls

I see what you mean about the potential pitfalls. I had 51 updates this morning and used the sudo apt-get install --only-upgrade command to install just 47 of them. That went fine.
I just checked for updates again and it installed gir1.2-gmenu-3.0 gnome-menus gnome-session gnome-session-bin gnome-session-common libaudit-common libaudit1 libgnome-menu-3-0 libplymouth2 libselinux1 libssl1.0.0 openssl plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text python3-software-properties rsyslog software-properties-common software-properties-gtk xserver-common xserver-xephyr xserver-xorg-core.

But the recommends were rsyslog-mysql rsyslog-pgsql rsyslog-doc rsyslog-gnutls rsyslog-gssapi rsyslog-relp xfonts-100dpi xfonts-75dpi
And when I attempted to install those here's what I got:

```
The following extra packages will be installed:
  dbconfig-common libdbd-mysql-perl libdbi-perl libmysqlclient18 libpq5 librelp0 libterm-readkey-perl mysql-client mysql-client-5.5 mysql-client-core-5.5 mysql-common postgresql-client postgresql-client-9.3
  postgresql-client-common
Suggested packages:
  libmldbm-perl libnet-daemon-perl libplrpc-perl libsql-statement-perl postgresql-9.3 postgresql-doc-9.3 gnutls-bin krb5-user mysql-server postgresql
The following NEW packages will be installed:
  dbconfig-common libdbd-mysql-perl libdbi-perl libmysqlclient18 libpq5 librelp0 libterm-readkey-perl mysql-client mysql-client-5.5 mysql-client-core-5.5 mysql-common postgresql-client postgresql-client-9.3
  postgresql-client-common rsyslog-doc rsyslog-gnutls rsyslog-gssapi rsyslog-mysql rsyslog-pgsql rsyslog-relp xfonts-100dpi xfonts-75dpi
0 upgraded, 22 newly installed, 0 to remove and 4 not upgraded.
Need to get 13.8 MB of archives.
After this operation, 62.3 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

I aborted that operation not knowing what the heck I was doing :lol:

And what about the libglib files when the good ones come down the pipe?

---

### Post by kansasnoob on 2013-12-07
Just thinking out loud here :idea:

Since the new GNOME Classic session is in no way related to the "Flashback" sessions I think I should rename this thread once again.

My thought is that the new GNOME Classic session is no more closely related to the "Flashback" sessions than MATE or Cinnamon. So I'm thinking of changing the name to "Trusty GNOME Flashback sessions".

To take things a step further, *[COLOR="#0000FF"]once again just thinking out loud[/COLOR]*, I wonder why we Flashback devotees are relying on GNOME dev in any way?

Consider this example (read the replies from Matthias Clasen):

[https://bugzilla.gnome.org/show_bug.cgi?id=695088](https://bugzilla.gnome.org/show_bug.cgi?id=695088)

It's almost apparent that GNOME dev not only dropped internal support for 'gnome-panel' and 'metacity', but that they're more than willing to set up roadblocks to prevent Debian and Ubuntu dev from achieving that goal :(

So I'm thinking that we should move our entire movement away from GNOME and onto either Ubuntu or Debian resources .............. including the mailing list!

Please share your thoughts :)

---

### Post by oldfred on 2013-12-07
I thought gnome decided to drop fallback/flashback or whatever, as your link above discusses with 3.7, but then with gnome 3.8 they added it back in.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

But the naming and the underlying tools have me totally confused.

All I really know is 12.04 with kansasnoob's directions for fallback and that has worked well for me.

---

### Post by kansasnoob on 2013-12-07
> **oldfred said:**
> I thought gnome decided to drop fallback/flashback or whatever, as your link above discusses with 3.7, but then with gnome 3.8 they added it back in.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

But the naming and the underlying tools have me totally confused.

All I really know is 12.04 with kansasnoob's directions for fallback and that has worked well for me.

This might be helpful:

[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

Basically Debian and Edubuntu want to keep it alive for LTSP installs, and development is ongoing - albeit somewhat slow.

---

### Post by muktupavels on 2013-12-07
How many of this thread readers are using flashback session with trusty? I would love if you could check something for me. Please open panel properties and try change all properties - orientation, size, expand, show hide buttons. Does it work for you?

P.S. Fallback mode is dropped from gnome as official part and it is not added back.

---

### Post by PJs Ronin on 2013-12-07
[QUOTE=albertsmuktupavels]How many of this thread readers are using flashback session with trusty?[/QUOTE]
I am trying to do this, I really am... but I'm having no luck at all getting Gnome-Compiz or Gnome-Metacity to play nice.
[QUOTE=albertsmuktupavels]I would love if you could check something for me. Please open panel properties and try change all properties - orientation, size, expand, show hide buttons. Does it work for you?[/QUOTE]I, for one, can't even do that.   My top panel is blank and no amount CTRL-ALT left/right mouse on the panel does anything.

I'm really forming the opinion that Gnome-dodo is just that.

---

### Post by kansasnoob on 2013-12-08
> **albertsmuktupavels said:**
> How many of this thread readers are using flashback session with trusty? I would love if you could check something for me. Please open panel properties and try change all properties - orientation, size, expand, show hide buttons. Does it work for you?

P.S. Fallback mode is dropped from gnome as official part and it is not added back.

I've been testing Flashback w/ Metacity in Trusty at least once daily, but things have been quite a mess lately. Not all of the mess is related only to the Flashback sessions however. In fact Lubuntu totally blew up on me :)

I typically use only a bottom panel so I created a top panel just for testing purposes, and I notice when I add hide buttons w/o arrows it looks OK, but when I add arrows to the buttons I just get a "white bar" directly below the panel:

[ATTACH=CONFIG]248423[/ATTACH]

Rather off-topic but I'm sure you're aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

---

### Post by kansasnoob on 2013-12-08
BTW I'm posting in "bits-n-pieces" because Firefox frequently crashes, but that also happens in a standard 'gnome-shell' session so it's not a "flashback" only thing ;)

---

### Post by kansasnoob on 2013-12-08
> **albertsmuktupavels said:**
> How many of this thread readers are using flashback session with trusty? I would love if you could check something for me. Please open panel properties and try change all properties - orientation, size, expand, show hide buttons. Does it work for you?

P.S. Fallback mode is dropped from gnome as official part and it is not added back.

Top and bottom orientation work fine (in a metacity session), but left and right just display a blank white panel.

If I had my druthers we'd eliminate left/right orientation altogether :)

---

### Post by kansasnoob on 2013-12-08
Still in a metacity session expand works fine, but increasing the size results in the same white border as adding arrows to the buttons.

---

### Post by kansasnoob on 2013-12-08
Something I should perhaps mention is that the Saucy version of  [Hardware Sensors Indicator]("https://launchpad.net/~alexmurray/+archive/indicator-sensors") stopped appearing and working in Trusty, but I notice some updates coming for the 'sensors-applet' in Trusty-proposed so maybe at some point that will not be needed any longer.

---

### Post by kansasnoob on 2013-12-08
Oh, both delete and add panel still work as expected in a metacity session.

---

### Post by kansasnoob on 2013-12-08
> **PJs Ronin said:**
> I am trying to do this, I really am... but I'm having no luck at all getting Gnome-Compiz or Gnome-Metacity to play nice.
I, for one, can't even do that.   My top panel is blank and no amount CTRL-ALT left/right mouse on the panel does anything.

I'm really forming the opinion that Gnome-dodo is just that.

This won't make much sense right now so bear with me through a couple of edits :)

The configurability of the "panels" is quite dependent on what session and window manager you're running.

You can run this command to see what session you're running:

```
echo $DESKTOP_SESSION
```

Or you can install 'wmctrl' and then run this command:

```
wmctrl -m
```

For instance I'm currently running a flashback/metacity session so I get this output:

```
lance@lance-desktop:~$ sudo apt-get install wmctrl
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-headers-3.12.0-1 linux-headers-3.12.0-1-generic linux-headers-3.12.0-2
  linux-headers-3.12.0-2-generic linux-image-3.11.0-12-generic
  linux-image-3.12.0-1-generic linux-image-3.12.0-2-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.12.0-1-generic
  linux-image-extra-3.12.0-2-generic linux-image-extra-3.12.0-3-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  wmctrl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.3 kB of archives.
After this operation, 79.9 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe wmctrl i386 1.07-7 [21.3 kB]
Fetched 21.3 kB in 0s (69.5 kB/s) 
Selecting previously unselected package wmctrl.
(Reading database ... 319957 files and directories currently installed.)
Unpacking wmctrl (from .../wmctrl_1.07-7_i386.deb) ...
Processing triggers for man-db ...
Setting up wmctrl (1.07-7) ...
[B]lance@lance-desktop:~$ echo $DESKTOP_SESSION
gnome-fallback[/B]
[B]lance@lance-desktop:~$ wmctrl -m
Name: Metacity[/B]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

```

I'll follow up with more info later :D

More info #1:

As you seemed to imply nothing works in a flashback/compiz session right now as far as editing 'gnome-panel', but I've never focused on Compiz because I find it too "heavy" for most of my hardware anyway. OTOH I've found Metacity to run just as "light" as both Xfwm and Openbox in real-time with as little as an 1100Mhz CPU and 500MB of RAM, although 1GB of RAM is preferable for installation.

Anyway, these are the outputs of those two commands in a Trusty flashback/compiz session:

```
lance@lance-desktop:~$ echo $DESKTOP_SESSION
gnome-fallback-compiz
lance@lance-desktop:~$ wmctrl -m
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF

```

---

### Post by kansasnoob on 2013-12-08
Thinking out loud again :redface:

Why does the small team of Debian/Edubuntu devs interested in the flashback session need to even support a flashback/compiz session? Only Metacity would be needed to support LTSP installs :)

---

### Post by kansasnoob on 2013-12-08
Something odd and interesting, after trying a flashback/compiz session logging out and logging back into a metacity session seems to still display a compiz session for a minute and a half (maybe almost two minutes), so maybe the aforementioned bug has something to do with determining which session should be initiated :confused:

---

### Post by kansasnoob on 2013-12-08
> **albertsmuktupavels said:**
> Why are you asking this? I think that you can freely subscribe to any mailing list you want. They are not restricted to devs only.



Why Metacity? Have you tried to use mutter? If you have time you could install mutter to test it. Than from terminal run:
```
mutter --replace
```

For me mutter session works, but I have no time to actively test it.

This is mostly a reminder to myself ;)

I've not forgotten about trying Mutter but I've found Ubuntu GNOME Trusty to be incredibly unstable out-of-box ATM so I'm just waiting for their Alpha 1.

---

### Post by PJs Ronin on 2013-12-08
Ok, not sure where all this is going, but here's my story.   I rsync'd my saucy partition (has only unity with no xfce/ldx/gnome wizzbangery) into a new partition... then did an insitu upgrade of this new partition to trusty... I then saw a post explaining how to bring in the 'right' gnome so I did a *sudo apt-get install gnome-session-flashback gdm*... at the GDM login I now have 5 options, Ubuntu, Gnome with Compiz, Gnome with Metacity, Gnome and Default Session.   Delete reference to that last option for the remainder of this post.

So, I tried each method, took a screenie and applied the script mentioned above.   Here are the results:

Unity
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m 
ubuntu
-------------------
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
wayne@trusty-gnome:~$ 
```
[IMG]http://i44.tinypic.com/28l3u2u.jpg[/IMG]

Gnome (Compiz) - top panel totally unresponsive
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m 
gnome-fallback-compiz
-------------------
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
wayne@trusty-gnome:~$ 
```
[IMG]http://i43.tinypic.com/2uh4cif.jpg[/IMG]

Gnome (Metacity) - top panel totally unresponsive
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m
gnome-fallback
-------------------
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
wayne@trusty-gnome:~$
```
[IMG]http://i41.tinypic.com/11ch2mr.jpg[/IMG]

Gnome - everything pretty much works
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m 
gnome
-------------------
Name: GNOME Shell
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
wayne@trusty-gnome:~$
```
[IMG]http://i42.tinypic.com/2ry6p6v.jpg[/IMG]

I really don't want to hijack this thread and would prefer you pursue your original thoughts.   Just letting folks know that atm noobs like me are probably going to have problems with gnome-session-flashback installs.

---

### Post by muktupavels on 2013-12-08
> **PJs Ronin said:**
> Ok, not sure where all this is going, but here's my story.   I rsync'd my saucy partition (has only unity with no xfce/ldx/gnome wizzbangery) into a new partition... then did an insitu upgrade of this new partition to trusty... I then saw a post explaining how to bring in the 'right' gnome so I did a *sudo apt-get install gnome-session-flashback gdm*... at the GDM login I now have 5 options, Ubuntu, Gnome with Compiz, Gnome with Metacity, Gnome and Default Session.   Delete reference to that last option for the remainder of this post.

So, I tried each method, took a screenie and applied the script mentioned above.   Here are the results:

Unity
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m 
ubuntu
-------------------
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
wayne@trusty-gnome:~$ 
```
[IMG]http://i44.tinypic.com/28l3u2u.jpg[/IMG]

Gnome (Compiz) - top panel totally unresponsive
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m 
gnome-fallback-compiz
-------------------
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
wayne@trusty-gnome:~$ 
```
[IMG]http://i43.tinypic.com/2uh4cif.jpg[/IMG]to

Gnome (Metacity) - top panel totally unresponsive
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m
gnome-fallback
-------------------
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
wayne@trusty-gnome:~$
```
[IMG]http://i41.tinypic.com/11ch2mr.jpg[/IMG]toto

Gnome - everything pretty much works
```
wayne@trusty-gnome:~$ echo $DESKTOP_SESSION && echo "-------------------" && wmctrl -m 
gnome
-------------------
Name: GNOME Shell
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
wayne@trusty-gnome:~$
```
[IMG]http://i42.tinypic.com/2ry6p6v.jpg[/IMG]

I really don't want to hijack this thread and would prefer you pursue your original thoughts.   Just letting folks know that atm noobs like me are probably going to have problems with gnome-session-flashback installs.

Do you have installed indicator-applet-appmenu? If so uninstall it and try again compiz and/or metacity sessions.

I know that at least on x64 indicator-applet-appmenu is broken causing all other applets to not show. If you can open system monitor, you can try kill that process to see if applets shows on top panel.

---

### Post by PJs Ronin on 2013-12-08
> **albertsmuktupavels said:**
> Do you have installed indicator-applet-appmenu? If so uninstall it and try again compiz and/or metacity sessions.

I know that at least on x64 indicator-applet-appmenu is broken causing all other applets to not show. If you can open system monitor, you can try kill that process to see if applets shows on top panel.
Ty... I'll try that today.

---

### Post by PJs Ronin on 2013-12-08
indicator-applet-appmenu was NOT installed.   After I installed it there was no change to not being able to access the top panel in gnome-compiz, however in gnome-metacity I could now access the top panel... briefly.  I managed to install the clock app before indicator-applet-appmenu crashed.

---

### Post by kansasnoob on 2013-12-08
> **PJs Ronin said:**
> indicator-applet-appmenu was NOT installed.   After I installed it there was no change to not being able to access the top panel in gnome-compiz, however in gnome-metacity I could now access the top panel... briefly.  I managed to install the clock app before indicator-applet-appmenu crashed.

I also found it was not installed.

---

### Post by ventrical on 2013-12-10
It's not installed here either and it still doesn't work after most recent updates. 1  and 1/2 minute before panel and desktop show up. I tried to adjust some compiz settings , but to no avail.

---

### Post by Cavsfan on 2013-12-11
> **ventrical said:**
> It's not installed here either and it still doesn't work after most recent updates. 1  and 1/2 minute before panel and desktop show up. I tried to adjust some compiz settings , but to no avail.

Same here: it wasn't installed but after it was installed it had little effect. Also 1 and 1/2 minutes here for the desktop to show up but after that it's pretty smooth.

---

### Post by ventrical on 2013-12-11
Metacity is affected also. never seen it so bad. Usually we get this long delay before plymouth or before login screen.

 Looks like a traffic cop somewhere in the code. I remember we had something like this during 11.10 or during Precise beta testing . It was just awful.. and it turned out to be one of the devs put a 'wait' command for 2 minutes on a line that should not have been there.  I forget the bug. Hmmmm..

---

### Post by Hazzabin on 2013-12-16
Hey guys

Is there any signs that this is getting a fix sometime soon

---

### Post by ventrical on 2013-12-16
I just zsynced todays daily 386.iso <ubuntu>, fresh installed downloaded gnome-session-flashback and the delay now is worse than before. 2 minutes...

Also .. Ubiquity is showing a 'wide-out' horizontal screen and the automatic partitioner slider is not visible (yet it still partitions the half average size of disk.

---

### Post by Cavsfan on 2013-12-17
Thanks I was just going to ask the same question. I guess I'll stick with what I have for now.

---

### Post by kansasnoob on 2013-12-18
Jonathan Carter is still on board:

[http://iso.qa.ubuntu.com/qatracker/milestones/309/builds/59164/testcases/1300/results](http://iso.qa.ubuntu.com/qatracker/milestones/309/builds/59164/testcases/1300/results)

So wipe the sweat from your brow :D

We'll be fine, we just need to remember that people have lives, families, and careers as well as their involvement in **buntu :D

---

### Post by kansasnoob on 2013-12-21
GNOME Sensors Applet works again:

[ATTACH=CONFIG]249045[/ATTACH]

That should mean we can live w/o this PPA:

[https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors)

So hats off to Alex Murray for his great work :D

---

### Post by Hazzabin on 2013-12-22
Using Trusty Gnome 14.04 behaves for me as it should, attempting to switch into 'with compiz' is a 3 to 4 minute wait and no nothing in either top or bottom bars, 'with metacity' total disaster.

My install is from the iso dated 16.12.2013 with the updates as per synaptic manager.

Trusty Unity works beautifully.

---

### Post by kansasnoob on 2013-12-23
One of the Edubuntu devs posted a workaround for that desktop-loading-slowly bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8)

I gave it a try:

```
lance@lance-desktop:~$ sudo -i
[sudo] password for lance: 
root@lance-desktop:~#  echo '#!/bin/sh
>  /usr/bin/gnome-panel &' > /usr/local/bin/gnome-panel
root@lance-desktop:~#  chmod +x /usr/local/bin/gnome-panel
root@lance-desktop:~# 
```

And it does work in a metacity session :guitar:

So hopefully that will help find a true fix :)

---

### Post by tista on 2013-12-23
Hi kansasnoob ;)

I've also living with this dirty workaround:

**1. Remove the gnome-panel entry within gome-session kicking sequence**
In /usr/share/gnome-session/sessions/gnome-flashback.session, Those components would be defined like this:
```
RequiredComponents=gnome-settings-daemon;gnome-screensaver;nautilus-classic;metacity;[color=red]gnome-panel;[/color]
```
So remove this red part to avoid kicking gnome-panel within session init. 

**2. Add autostart desktop file for gnome-panel with some "Delay"**
Something like this named 'gnome-panel.desktop' in $HOME/.config/autostart/:
```
[Desktop Entry]
Type=Application
Exec=gnome-panel
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
[color=red]X-GNOME-Autostart-Delay=2[/color]
Name[en_US]=Gnome-Panel
Name=Gnome-Panel
Comment[en_US]=
Comment=
```

This could work for my flashback session... :P
I suppose gnome-setting-daemon in trusty might need a bit more time to load their plugins, or indicators-applet would need some tricks to load into gnome-panel?

Regards,
Tista

---

### Post by ventrical on 2013-12-23
> **kansasnoob said:**
> One of the Edubuntu devs posted a workaround for that desktop-loading-slowly bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8)

I gave it a try:

```
lance@lance-desktop:~$ sudo -i
[sudo] password for lance: 
root@lance-desktop:~#  echo '#!/bin/sh
>  /usr/bin/gnome-panel &' > /usr/local/bin/gnome-panel
root@lance-desktop:~#  chmod +x /usr/local/bin/gnome-panel
root@lance-desktop:~# 
```

And it does work in a metacity session :guitar:

So hopefully that will help find a true fix :)

Works in compiz session +1! :)

---

### Post by grahammechanical on 2013-12-23
Would somebody like to help this uneducated peasant and explain what those commands do?

My first guess was that they create a script. But I could not see what was to be put in the script. My second guess, after a little research (including that Launchpad link), is that they change the permissions of a bin/executable file called gnome-panel. I am now guessing that the plus sign ( + ) in front of the x = execute sign causes a delay in the executing of gnome-panel.

Oh, I do already know what the echo command does.

Regards.

---

### Post by zika on 2013-12-23
Create folder (it did not exist on my machine) (it is included in the PATH env.var. before /usr/bin so it is OK) and open file for editing```
sudo mkdir /usr/local/bin
sudo nano /usr/local/bin/gnome-panel
```
Put into that file:
```
#!/bin/sh
/usr/bin/gnome-panel &
```
Make it executable```
sudo chmod +x /usr/local/bin/gnome-panel
```
All this makes easy get-back path:```
sudo rm /usr/local/bin/gnome-panel
```
with possible addition of erasing even folder if iw was not there before this operation...
For the sake of security I will not give code for that erasure since (if it was there before and had some files) that could make certain problems to someone who does copy&paste blindly...

---

### Post by kansasnoob on 2013-12-23
> **grahammechanical said:**
> Would somebody like to help this uneducated peasant and explain what those commands do?

My first guess was that they create a script. But I could not see what was to be put in the script. My second guess, after a little research (including that Launchpad link), is that they change the permissions of a bin/executable file called gnome-panel. I am now guessing that the plus sign ( + ) in front of the x = execute sign causes a delay in the executing of gnome-panel.

Oh, I do already know what the echo command does.

Regards.

I really didn't bother trying to figure it out, I just considered the source:

[https://launchpad.net/~alkisg](https://launchpad.net/~alkisg)

But if I blow up a test install I don't care a whole bunch :D

---

### Post by Cavsfan on 2013-12-23
> **kansasnoob said:**
> One of the Edubuntu devs posted a workaround for that desktop-loading-slowly bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8)

I gave it a try:

```
lance@lance-desktop:~$ sudo -i
[sudo] password for lance: 
root@lance-desktop:~#  echo '#!/bin/sh
>  /usr/bin/gnome-panel &' > /usr/local/bin/gnome-panel
root@lance-desktop:~#  chmod +x /usr/local/bin/gnome-panel
root@lance-desktop:~# 
```

And it does work in a metacity session :guitar:

So hopefully that will help find a true fix :)

+1 That worked great on my compiz session. I just logged out and back in and it worked. :popcorn:

---

### Post by kansasnoob on 2013-12-23
> **zika said:**
> Create folder (it did not exist on my machine) (it is included in the PATH env.var. before /usr/bin so it is OK) and open file for editing```
sudo mkdir /usr/local/bin
sudo nano /usr/local/bin/gnome-panel
```
Put into that file:
```
#!/bin/sh
/usr/bin/gnome-panel &
```
Make it executable```
sudo chmod +x /usr/local/bin/gnome-panel
```
All this makes easy get-back path:```
sudo rm /usr/local/bin/gnome-panel
```
with possible addition of erasing even folder if iw was not there before this operation...
For the sake of security I will not give code for that erasure since (if it was there before and had some files) that could make certain problems to someone who does copy&paste blindly...

Thanks for clarifying that :)

---

### Post by kansasnoob on 2013-12-29
> **tista said:**
> Hi kansasnoob ;)

I've also living with this dirty workaround:

**1. Remove the gnome-panel entry within gome-session kicking sequence**
In /usr/share/gnome-session/sessions/gnome-flashback.session, Those components would be defined like this:
```
RequiredComponents=gnome-settings-daemon;gnome-screensaver;nautilus-classic;metacity;[color=red]gnome-panel;[/color]
```
So remove this red part to avoid kicking gnome-panel within session init. 

**2. Add autostart desktop file for gnome-panel with some "Delay"**
Something like this named 'gnome-panel.desktop' in $HOME/.config/autostart/:
```
[Desktop Entry]
Type=Application
Exec=gnome-panel
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
[color=red]X-GNOME-Autostart-Delay=2[/color]
Name[en_US]=Gnome-Panel
Name=Gnome-Panel
Comment[en_US]=
Comment=
```

This could work for my flashback session... :P
I suppose gnome-setting-daemon in trusty might need a bit more time to load their plugins, or indicators-applet would need some tricks to load into gnome-panel?

Regards,
Tista

I'll try that soon on a fresh install.

---

### Post by kansasnoob on 2013-12-29
I've finally begun updating post #1 for the benefit of those new to Ubuntu +1, please let me know if you see any missing parts ;)

---

### Post by kansasnoob on 2013-12-29
> **zika said:**
> If You go with dconf-editor on that address You can choose from 3 different settings, or You can list that switch with the same tool as above.

Referring to the scrollbar settings in dconf described here:

[http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773](http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773)

Hmmm, one of three is obviously the default, and another is "normal", but what is the third?

---

### Post by zika on 2013-12-29
> **kansasnoob said:**
> Referring to the scrollbar settings in dconf described here:

[http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773](http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773)

Hmmm, one of three is obviously the default, and another is "normal", but what is the third?
1. normal
2. overlay-auto
3. overlay-pointer
4. overlay-touch
(at least on my machine...)
It is not difficult to open dconf-editor on that &#8222;address&#8220; and check...

---

### Post by kansasnoob on 2013-12-29
> **zika said:**
> 1. normal
2. overlay-auto
3. overlay-pointer
4. overlay-touch
(at least on my machine...)
It is not difficult to open dconf-editor on that „address“ and check...

OK, displaying my stupidity here :redface:

How exactly do I check the available options in dconf-editor?

Sorry to be a pain :)

---

### Post by mc4man on 2013-12-29
> **kansasnoob said:**
> 
How exactly do I check the available options in dconf-editor?

click in the Value column to expose the dropdown list (ie. right on 'overlay-auto'

---

### Post by kansasnoob on 2013-12-29
> **mc4man said:**
> click in the Value column to expose the dropdown list (ie. right on 'overlay-auto'

Cool, I honestly never knew that :biggrin:

---

### Post by Hazzabin on 2013-12-29
you were not the only one kansasnoob

As per the image in
[http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773](http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773)

I do not get canonical/desktop, mine only shows canonical/indicator

how can I get canonical desktop   to show
   
I'm using the Gnome Trusty  not a derivative

---

### Post by mc4man on 2013-12-29
> **Hazzabin said:**
> you were not the only one kansasnoob

As per the image in
[http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773](http://ubuntuforums.org/showthread.php?t=2184682&page=6&p=12850773#post12850773)

I do not get canonical/desktop, mine only shows canonical/indicator

how can I get canonical desktop   to show
   
I'm using the Gnome Trusty  not a derivative
I don't use trusty 'gnome' but it's likely it doesn't install those  gschema files, as in 
/usr/share/glib-2.0/schemas/com.canonical.desktop.interface.gschema.xml  & com.canonical.desktop.interface.enums.xml

---

### Post by Hazzabin on 2013-12-29
> **mc4man said:**
> I don't use trusty 'gnome' but it's likely it doesn't install those  gschema files, as in 
/usr/share/glib-2.0/schemas/com.canonical.desktop.interface.gschema.xml  & com.canonical.desktop.interface.enums.xml

Thanks mate, just curious which 'Trusty' are you using
correct that gschema files are not there, any suggestions on how to get/install

thanks in advance

note: think I'll change my 'name' to Aussienoob

---

### Post by kansasnoob on 2013-12-30
> **Hazzabin said:**
> Thanks mate, just curious which 'Trusty' are you using
correct that gschema files are not there, any suggestions on how to get/install

thanks in advance

note: think I'll change my 'name' to Aussienoob

What exactly are you trying to do, add the overlay scrollbars to the gnome-shell DE?

---

### Post by Hazzabin on 2013-12-30
No mate

I was hoping that with adding that schema I might just be lucking and get top and bottom panels/taskbar working in gnome flashback

as nothing else seems to be working, it appears that some 'fixes' have worked with other os'es xubuntu, lubuntu and maybe others

---

### Post by kansasnoob on 2013-12-30
> **Hazzabin said:**
> No mate

I was hoping that with adding that schema I might just be lucking and get top and bottom panels/taskbar working in gnome flashback

as nothing else seems to be working, it appears that some 'fixes' have worked with other os'es xubuntu, lubuntu and maybe others

In Ubuntu GNOME I encountered this bug:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1245209](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1245209)

Maybe look at the screenshots to see if you are encountering a similar problem. If so try installing 'lightdm-gtk-greeter' which also installs 'lightdm'. Then when prompted select to use the lightdm display manager rather than gdm. Then reboot to complete the change.

Note that if you have selected "auto-login" you'll boot into the same session you were using so you'll want to logout and select the Flashback (no effects) session from the drop-down menu in the upper right hand corner of the screen.

And in Ubuntu, Edubuntu, and Ubuntu GNOME there is this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

There is a workaround in post #8 that worked for me, and there is another workaround I've not yet tested here:

[http://ubuntuforums.org/showthread.php?t=2184682&page=21&p=12881058#post12881058](http://ubuntuforums.org/showthread.php?t=2184682&page=21&p=12881058#post12881058)

If your problem is with the Compiz session I'm clueless.

If any of this is confusing please ask questions before jumping in :D

---

### Post by zika on 2013-12-30
> **kansasnoob said:**
> OK, displaying my stupidity here :redface:

How exactly do I check the available options in dconf-editor?

Sorry to be a pain :)Click on field for that entry...

---

### Post by kansasnoob on 2013-12-30
> **zika said:**
> Click on field for that entry...

Thanks, I truly never knew that until now :D

---

### Post by grahammechanical on 2013-12-30
Not too long ago this thread got on to the subject of gnome-screen saver. I am not wishing to take this thread off topic but this link might be interesting for those who care about screen savers and that stuff.

[http://discourse.ubuntu.com/t/wake-from-screensaver-directly-to-the-login-screen/923](http://discourse.ubuntu.com/t/wake-from-screensaver-directly-to-the-login-screen/923)

Regards.

---

### Post by kansasnoob on 2013-12-30
> **grahammechanical said:**
> Not too long ago this thread got on to the subject of gnome-screen saver. I am not wishing to take this thread off topic but this link might be interesting for those who care about screen savers and that stuff.

[http://discourse.ubuntu.com/t/wake-from-screensaver-directly-to-the-login-screen/923](http://discourse.ubuntu.com/t/wake-from-screensaver-directly-to-the-login-screen/923)

Regards.

Very, very much welcome :D

In the past few  days I've begun updating my OP, please have a look and feel free to be critical:

[http://ubuntuforums.org/showthread.php?t=2184682&p=12833089#post12833089](http://ubuntuforums.org/showthread.php?t=2184682&p=12833089#post12833089)

I had planned on asking about that because some people do still want an actual screensaver.

---

### Post by Hazzabin on 2013-12-30
Thanks kansasnoob for your reply, a couple of things worked as in booting into 'flashback with compiz', followed some instructions and boots in way faster, tho still no nothing in top and bottom panels

yes I am using Ubuntu-Gnome with 'Compiz-flashback', it is weird as Classic and base Gnome works fine with top panels etc all working

no matter something will get fixed sometime soon

again thanks

---

### Post by kansasnoob on 2013-12-31
> **Hazzabin said:**
> Thanks kansasnoob for your reply, a couple of things worked as in booting into 'flashback with compiz', followed some instructions and boots in way faster, tho still no nothing in top and bottom panels

yes I am using Ubuntu-Gnome with 'Compiz-flashback', it is weird as Classic and base Gnome works fine with top panels etc all working

no matter something will get fixed sometime soon

again thanks

I recall this being discussed several days ago. Is anyone aware of a bug report? I'd like to add it to the known issues in post #1 :)

---

### Post by kansasnoob on 2013-12-31
I need to post a couple of screenshots of 'gnome-tweak-tool' in order to make my OP make sense :)

[ATTACH=CONFIG]249048[/ATTACH]

[ATTACH=CONFIG]249047[/ATTACH]

---

### Post by kansasnoob on 2014-01-03
Looks like I need to learn some new tricks :)

The past few days I've been testing gnome 3.10 packages from the gnome 3 ppa, some of which will hopefully make it into the repos soon.

On one installation of Ubuntu GNOME Trusty gnome-panel broke badly in the flashback w/metacity session, but I cross-tested with Ubuntu, Edubuntu, and finally another installation of Ubuntu GNOME which worked OK with my typical layout:

[ATTACH=CONFIG]249136[/ATTACH]

So I booted back into the broken OS and tried all of the old tricks to restore the defaults but to no avail :(

What finally did work was totally purging these using synaptic:

> Commit Log for Wed Jan  1 21:39:54 2014


Completely removed the following packages:
gnome-applets
gnome-panel
gnome-session-flashback

Then I rebooted into the default gnome-shell session, reinstalled those three packages, logged out, then logged back into a flashback w/metacity session and all was well.

So I need to develop a decent approach to restoring a default config when things get totally borked.

---

### Post by ventrical on 2014-01-04
Ok.. after yesterdays update it appears that the Gnome Panel bug (delay) has been fixed in Gnome-Flashback-Compiz).

Who-ever fixed it .. Thanks ! :)

Regards..

---

### Post by QDR06VV9 on 2014-01-04
> **ventrical said:**
> Ok.. after yesterdays update it appears that the Gnome Panel bug (delay) has been fixed in Gnome-Flashback-Compiz).

Who-ever fixed it .. Thanks ! :)

Regards..
Might have to give this a Go now! Thanks
Vent its been a while, Hope the Holidays went well for you!

---

### Post by ventrical on 2014-01-04
> **runrickus said:**
> Might have to give this a Go now! Thanks
Vent its been a while, Hope the Holidays went well for you!


Sure did and hope the same for you and yours :)

Ummm... as for this problem being fixed ... I'll have to double check on another PC .

brb

---

### Post by QDR06VV9 on 2014-01-04
> **ventrical said:**
> Sure did and hope the same for you and yours :)

Ummm... as for this problem being fixed ... I'll have to double check on another PC .

brb

Very Nice Thank You my Friend!
I know what you mean checking from another machine, Since I got back into testing seems like I have a least 2 Machines or more running.lol

---

### Post by ventrical on 2014-01-04
> **runrickus said:**
> Very Nice Thank You my Friend!
I know what you mean checking from another machine, Since I got back into testing seems like I have a least 2 Machines or more running.lol


My apologies.  It has been a while since I had checked other systems. The machine I used was one that had the |edited| file. So the fix is not in as of yet.  So... belay my last.  :)

Regards..

|edited file|

[http://ubuntuforums.org/showthread.php?t=2184682&page=21&p=12881077#post12881077](http://ubuntuforums.org/showthread.php?t=2184682&page=21&p=12881077#post12881077)

---

### Post by Cavsfan on 2014-01-04
I guess I should have read further before trying it. I made it unexecutable and logged out.
```
cavsfan@cavsfan-MS-7529:~$ sudo chmod -x /usr/local/bin/gnome-panel

```
 Still the delay. Rebooted and same thing.

So I just made it executable again logged out and back in business. No harm done. 

I'm _***sure***_ they will fix it eventually. :smile:

---

### Post by kansasnoob on 2014-01-05
Still testing the gnome 3.10 packages from the gnome 3 PPA and I found that the new gnome-tweak-tool fails to launch if gnome-shell is not installed:

[https://bugs.launchpad.net/ubuntu-gnome/+bug/1266307](https://bugs.launchpad.net/ubuntu-gnome/+bug/1266307)

[https://bugzilla.gnome.org/show_bug.cgi?id=721613](https://bugzilla.gnome.org/show_bug.cgi?id=721613)

---

### Post by Cavsfan on 2014-01-09
> **kansasnoob said:**
> One of the Edubuntu devs posted a workaround for that desktop-loading-slowly bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961/comments/8)

I gave it a try:

```
lance@lance-desktop:~$ sudo -i
[sudo] password for lance: 
root@lance-desktop:~#  echo '#!/bin/sh
>  /usr/bin/gnome-panel &' > /usr/local/bin/gnome-panel
root@lance-desktop:~#  chmod +x /usr/local/bin/gnome-panel
root@lance-desktop:~# 
```

And it does work in a metacity session :guitar:

So hopefully that will help find a true fix :)

When the 3.13.0-1-generic kernel dropped in yesterday it made my system unbootable. I guess it had something to do with the nvidia driver 331-20 not working with the kernel.
I got the daily ISO and am now almost back in business.

But, the fix above no longer works. With /usr/local/bin/gnome-panel executable you get the same 1 1/2 minute delay but the top and bottom panels never appear up in Flashback (with Compiz).
If you make it unexecutable the initial problem is back: the panels immediately appear with a 1 1/2 minute delay before everything comes up.

I am living with the delay without the above fix for now.

Here's what I now have for Nvidia drivers to work with the new kernel:

[http://ubuntuforums.org/showthread.php?t=2198375&page=2&p=12895677#post12895677](http://ubuntuforums.org/showthread.php?t=2198375&page=2&p=12895677#post12895677)

---

### Post by Alan F on 2014-01-09
Gnome-panel fix still works for me OK. (3.13.0-1 kernel and Intel graphics)

---

### Post by Cavsfan on 2014-01-09
> **Alan F said:**
> Gnome-panel fix still works for me OK. (3.13.0-1 kernel and Intel graphics)

So, you do not have the 331.20 Nvidia driver installed right?

---

### Post by Alan F on 2014-01-09
> **Cavsfan said:**
> So, you do not have the 331.20 Nvidia driver installed right?

Correct

---

### Post by psfal on 2014-01-09
[COLOR=#252525][FONT=Verdana]As an exclusively Gnome Classic user, 12.04 is the last release I can move the min, max, close buttons to the right, where they belong. The inability to install my personal choice of desktop and have it function perfectly in any newer versions of Ubuntu is a deal-killer for me. I've tried the Ubuntu Gnome version and their excuse for "Classic" is very poor indeed. Unless I can find a way to move the buttons to the right where they belong 12.04 will be the very last version of Ubuntu that I use... Don't bother commenting about Gnome Classic no longer being supported, that's bull. I use Debian w/Gnome Classic the majority of the time already as I find ways to get my Netflix Desktop and various other things up and running, preparatory to dumping Ubuntu altogether... All they had to do was leave the original Gnome 2.0 alone and available but they chose to "force" people to move to less appealing DEs... I like my simple and exquisite Gnome Classic 2.0 and my available applets in the top panel and I will keep it as long as it is available in whatever distribution I have to use to have it... There is simply no other DE that I find pleasing... Yes, I've tried them all (MATE sucks, IMHO it's hideous)[/FONT][/COLOR]

---

### Post by Cavsfan on 2014-01-09
> **psfal said:**
> [COLOR=#252525][FONT=Verdana]As an exclusively Gnome Classic user, 12.04 is the last release I can move the min, max, close buttons to the right, where they belong. The inability to install my personal choice of desktop and have it function perfectly in any newer versions of Ubuntu is a deal-killer for me. I've tried the Ubuntu Gnome version and their excuse for "Classic" is very poor indeed. Unless I can find a way to move the buttons to the right where they belong 12.04 will be the very last version of Ubuntu that I use... Don't bother commenting about Gnome Classic no longer being supported, that's bull. I use Debian w/Gnome Classic the majority of the time already as I find ways to get my Netflix Desktop and various other things up and running, preparatory to dumping Ubuntu altogether... All they had to do was leave the original Gnome 2.0 alone and available but they chose to "force" people to move to less appealing DEs... I like my simple and exquisite Gnome Classic 2.0 and my available applets in the top panel and I will keep it as long as it is available in whatever distribution I have to use to have it... There is simply no other DE that I find pleasing... Yes, I've tried them all (MATE sucks, IMHO it's hideous)[/FONT][/COLOR]

In terminal enter 
```
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'

```

Problem solved.

---

### Post by kansasnoob on 2014-01-09
> **psfal said:**
> [COLOR=#252525][FONT=Verdana]As an exclusively Gnome Classic user, 12.04 is the last release I can move the min, max, close buttons to the right, where they belong. The inability to install my personal choice of desktop and have it function perfectly in any newer versions of Ubuntu is a deal-killer for me. I've tried the Ubuntu Gnome version and their excuse for "Classic" is very poor indeed. Unless I can find a way to move the buttons to the right where they belong 12.04 will be the very last version of Ubuntu that I use... Don't bother commenting about Gnome Classic no longer being supported, that's bull. I use Debian w/Gnome Classic the majority of the time already as I find ways to get my Netflix Desktop and various other things up and running, preparatory to dumping Ubuntu altogether... All they had to do was leave the original Gnome 2.0 alone and available but they chose to "force" people to move to less appealing DEs... I like my simple and exquisite Gnome Classic 2.0 and my available applets in the top panel and I will keep it as long as it is available in whatever distribution I have to use to have it... There is simply no other DE that I find pleasing... Yes, I've tried them all (MATE sucks, IMHO it's hideous)[/FONT][/COLOR]

Not a good way to request help my friend!

Have you even read my OP and followed the links:

[http://ubuntuforums.org/showthread.php?t=2184682&p=12833089#post12833089](http://ubuntuforums.org/showthread.php?t=2184682&p=12833089#post12833089)

Buttons still can be moved to the right, the method has just changed due to the deprecation of gconf.

Calm down and request help rather than ranting or the mods will undoubtedly just start moving your posts to some place where you'll be less likely to get help :)

EDIT: You should know this already:

[http://ubuntuforums.org/showthread.php?t=2169915](http://ubuntuforums.org/showthread.php?t=2169915)

Just ask for help instead of ranting and raving.

---

### Post by Cavsfan on 2014-01-09
I now see what you all have been saying about gnome-screensaver. I believe with this recent update it now functions as a lock. My screen goes black and turns off after 10 minutes. Although there is no "screensaver" functionality to it.
Maybe they should call it gnome-lock instead. I would still rather have a screensaver versus a black screen.

On my windows 7 setup, the screensaver kicks in after 10 minutes, the monitor turns off after 30 minutes and the PC goes to sleep after 60 minutes. I would like that in Ubuntu as well but have not seen a way to do it.
Precise goes to sleep mode after 30 minutes but all of the rest of my 'Buntus never go to sleep. But, I can suspend them as needed.

I'll take Xscreensaver ;)

---

### Post by kansasnoob on 2014-01-10
@ Alberts,

I hope your still reading here :)

I signed up for the mailing list and I'm receiving messages OK but not able to send to list yet, I've PMed Jonathan about that so hopefully I can get it straightened out soon. Anyway, after reading [this]("https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html"):

 >      1) The Applications menu is now a mess. Applications that were previously in the Accessories menu now appear in Accessories, Utilities, Sundry and Other. The System Settings submenu was moved under Applications instead of System Tools. Etc etc, the changes don't make much sense except maybe only for gnome-shell.
    Is it possible to somehow ship/use the previous version of /etc/xdg/menus/gnome-applications.menu ?


Can you fill bug for this? I agree with you, I don't like new menu too...

1) Lets ship old applications.menu with gnome-panel. This is simple, I already can upload patch for this. I added applications.menu from gnome-menus 3.4.0. In this case ubuntu should make new patch to add Software center to applications menu.

2) Install old applications.menu file only in ubuntu. I can create merge proposal for this if needed, but I would prefer first solution.

I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

---

### Post by muktupavels on 2014-01-10
> **kansasnoob said:**
> @ Alberts,

I hope your still reading here :)

I signed up for the mailing list and I'm receiving messages OK but not able to send to list yet, I've PMed Jonathan about that so hopefully I can get it straightened out soon. Anyway, after reading [this]("https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html"):

 

I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

I am reading here and i will continue to do it.

Why you are not able to send to mailing list? Just reply to received e-mail.

---

### Post by Cavsfan on 2014-01-10
> **kansasnoob said:**
> @ Alberts,

I hope your still reading here :)

I signed up for the mailing list and I'm receiving messages OK but not able to send to list yet, I've PMed Jonathan about that so hopefully I can get it straightened out soon. Anyway, after reading [this]("https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html"):

 

I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

I me too'ed it. I wondered about how convoluted it had gotten. I believe you can go into Main Menu, which ironically happens to under Applications >Sundry. Well I guess that makes the point well. :lol:

---

### Post by kansasnoob on 2014-01-10
> **albertsmuktupavels said:**
> I am reading here and i will continue to do it.

Why you are not able to send to mailing list? Just reply to received e-mail.

Sort of complicated. The sign up process rejected my yahoo mail acct, the same account I use for everything Ubuntu related:

[https://launchpad.net/~lbsolost](https://launchpad.net/~lbsolost)

So I used an old sbcglobal.net address that still dumps mail to my yahoo account to complete the sign up process, so I'm receiving mail from the list but when I reply it still shows it's coming from yahoo so I always get messages like this:

> Your mail to 'gnome-flashback-list' with the subject

    Re: [gnome-flashback] Regressions from previous gnome-panel
releases

Is being held until the list moderator can review it for approval.

The reason it is being held:

    Post by non-member to a members-only list


I'm not at all interested in creating a new email acct since I use that for Launchpad, Ubuntu QA, and all of my Ubuntu GNOME communications so I'm just waiting for a reply from Jonathan ;)

BTW Bugzilla had no problem with my email when I created an account to file my first bug report there:

[https://bugzilla.gnome.org/show_bug.cgi?id=721613](https://bugzilla.gnome.org/show_bug.cgi?id=721613)

---

### Post by kansasnoob on 2014-01-11
As expected more info has been requested here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

So I'm going to use this as a "whiteboard" to document what I consider to be the most egregious of the changes. The questions are rhetorical ATM, I'll keep rebooting until I'm satisfied that my list is fairly complete :)

(1) System Settings tree view added, but certainly not needed.

(2) Other added - only contains Personal File Sharing in Ubuntu GNOME, not sure how to describe Ubuntu:

[ATTACH=CONFIG]249374[/ATTACH]

(3) Sundry added. Orca Screen Reader moved to Sundry, but Onboard is still in Universal Access. Main Menu was moved from System Tools > Preferences to Sundry.

(4) Utilities added.

(5) It appears to me that we tried to copy the GNOME Classic "Applications Menu" extension, but flashback is not Classic and they're not us :)

*******************************************

I'm thinking I could summarize this along these lines:

It appears to me that an effort was made to copy the appearance of the GNOME Classic "Applications Menu" extension. In so doing the following categories were added:

Other - **This requires some serious thought!** It looks like this needs to stay as not to break Unity because it displays shopping lenses and web-apps!

I'm gaining slowly here. The Other category was added in Quantal to accommodate Unity lenses and web apps were added later:

[ATTACH=CONFIG]249396[/ATTACH] 

Sundry - Orca Screen Reader moved to Sundry, but Onboard is still in Universal Access. Main Menu was moved from System Tools > Preferences to Sundry.

System Settings tree view - just totally unnecessary. 

Utilities

##############################

I want to see what this addendum to the bug report looks like before I post it there:

To explain in greater detail, the sub-menu "Other" was added beginning with Quantal to display shopping lenses and later to also display web-apps which is arguably fine. I personally have no problem with that.

But in Saucy it appears an effort was made to copy the appearance of the GNOME Classic "Applications Menu" extension. In so doing the following sub-menus were added to 'gnome-panel':

(1) System Settings tree view added, but certainly not needed since System Settings also appears in System Tools as well as under the username.

(2) Sundry added, but sparsely populated. Orca Screen Reader moved to Sundry from Universal Access, but Onboard is still in Universal Access (being legally blind myself I refer to such changes as rearranging the furniture while I'm not home). Main Menu was also moved from System Tools > Preferences to Sundry which makes it a bit more difficult to eliminate Sundry if one so wishes.

(3) Utilities added, but also not really needed as all it accomplishes is relocating a large number of apps from Accessories and System Tools to a new location. Again just rearranging furniture.

In summary I'd add that 'gnome-session-flashback' need not mimic the new GNOME Classic session nor vice versa.

Two potential fixes, one upstream and the other at the Ubuntu level, have already been proposed here:

[https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html](https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html)

---

### Post by Cavsfan on 2014-01-11
I can't find the post on here but, I was able to once again add the patch from this bug to get Flashback (with compiz) loading quicker. [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1256961)

When I tried it before it only started fast but the top and bottom panels would never appear, but since the new kernel installed today it works again. :guitar:

Fantastic!!! I'll leave the times in killscreensaver.sh alone because for now it doesn't matter as long as they get executed prior to 10 minutes passing.
But, at least I can get my conky do appear a lot faster. :)

Things are looking up. Glome-flashback dependency of gnome-screensaver has been changed to a depends. Although          albertsmuktupavels mentioned not to remove gnome-screensaver just yet because it will break gnome-flashback.
But, the future is looking brighter. :)

---

### Post by Hazzabin on 2014-01-11
Gnome 14.04 'Flashback with compiz'

As said by Cavsfan "[COLOR=#000000]But, the future is looking brighter. [/COLOR]:smile:"

For the very first time I've got top and bottom panel, and I can't add my normal indicators/apps to the top panel, even time....can't add date to it

meant to mention, right-click top or bottom panels don't do anything either

any help appreciated

---

### Post by kansasnoob on 2014-01-12
@ Alberts,

I was a bit confused about the "Other" section of the menu and since we're focusing mostly on Edubuntu, Ubuntu, etc I spent the time to really dig into this :)

I know that you'd suggested [here]("https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html") that we roll back to "gnome-menus 3.4.0" but I think in order to NOT break Unity protocol we should only roll back to "3.6.0-0ubuntu1" as it was in Quantal because "Other" needs to be present to display lenses and webapps I guess :confused:

But the "System Settings tree view" is an absolute waste of space as are "Sundry" and "Utilities" since they only served to mimic the GNOME Classic "Applications Menu" extension.

Would you agree?

---

### Post by Alan F on 2014-01-12
> **Hazzabin said:**
> Gnome 14.04 'Flashback with compiz'

As said by Cavsfan "[COLOR=#000000]But, the future is looking brighter. [/COLOR]:smile:"

For the very first time I've got top and bottom panel, and I can't add my normal indicators/apps to the top panel, even time....can't add date to it

meant to mention, right-click top or bottom panels don't do anything either

any help appreciated


Hold down the Windows (Super) Key + alt, then right click on the top/bottom panel

---

### Post by muktupavels on 2014-01-12
> **kansasnoob said:**
> @ Alberts,

I was a bit confused about the "Other" section of the menu and since we're focusing mostly on Edubuntu, Ubuntu, etc I spent the time to really dig into this :)

I know that you'd suggested [here]("https://mail.gnome.org/archives/gnome-flashback-list/2014-January/msg00011.html") that we roll back to "gnome-menus 3.4.0" but I think in order to NOT break Unity protocol we should only roll back to "3.6.0-0ubuntu1" as it was in Quantal because "Other" needs to be present to display lenses and webapps I guess :confused:

But the "System Settings tree view" is an absolute waste of space as are "Sundry" and "Utilities" since they only served to mimic the GNOME Classic "Applications Menu" extension.

Would you agree?

I have never installed Edubuntu or any other ubuntu version. I am using only Ubuntu.

In way I would do it, it won't break anything. My idea is to ship new file with gnome-panel - just take menu file from older gnome-menus version ([https://git.gnome.org/browse/gnome-menus](https://git.gnome.org/browse/gnome-menus)) and rename it to for example flashback-applications.menu and use this file with flashback session / gnome-panel.

---

### Post by Hazzabin on 2014-01-12
AlanF, thanks so much for that info

Hazz

---

### Post by PJs Ronin on 2014-01-12
I'm with Hazzabin... I've finally managed to get top and bottom panels that look like top and bottom panels... and with AlanF's input I'm slowly building some functionality into those panels.   If I can just remember why I wanted to do this I'll be batting 1000... oh yeah, random masochistic tendencies.

---

### Post by Hazzabin on 2014-01-13
PJs Ronin, thank you, was starting to think it was only me with those issues

If a solution for "indicator-applet-complete" not wanting to go into the panel I could not find it, and/or is this a bug?

---

### Post by kansasnoob on 2014-01-13
I guess I should try a Compiz session sometime but I'm mostly concerned about the Metacity session :(

If someone does figure out how to get a sweet GNOME Flashback (Compiz) session working I'd love to include a link to it in my OP :)

---

### Post by kansasnoob on 2014-01-13
> **PJs Ronin said:**
> I'm with Hazzabin... I've finally managed to get top and bottom panels that look like top and bottom panels... and with AlanF's input I'm slowly building some functionality into those panels.   If I can just remember why I wanted to do this I'll be batting 1000... oh yeah, random masochistic tendencies.

I think I must also suffer from ***random masochistic tendencies*** :lolflag:

I'm personally very happy with gnome-shell (used to be happy with Unity) but it's not just about me :)

Some people want an older style DE and sometimes you have two or more users in the same household that want different DE's on the same puter. That's why I focus on installing as little as possible, and removing NOTHING!

Keeping as many changes as possible at the user level is a major focus ;)

---

### Post by Cavsfan on 2014-01-13
> **Hazzabin said:**
> Gnome 14.04 'Flashback with compiz'

As said by Cavsfan "[COLOR=#000000]But, the future is looking brighter. [/COLOR]:smile:"

For the very first time I've got top and bottom panel, and I can't add my normal indicators/apps to the top panel, even time....can't add date to it

meant to mention, right-click top or bottom panels don't do anything either

any help appreciated

It look some serious searching. I found it on about page 4 or 5 of the google results but, I finally got the date, time and even the seconds to work. :)

If you don't already have dconf Editor - **sudo apt-get install dconf-tools**. It will be under Applications > Sundry.

I'm pretty sure I had entered this in the top in custom-time-format **%m-%d-%Y %l:%M %p**. (month day year hour:minute AM/PM)
It doesn't show that now but I think it took effect judging by my desktop below.

[ATTACH=CONFIG]249475[/ATTACH]

[[img]http://en.zimagez.com/miniature/screenshotfrom2014-01-13150148.png[/img]](http://en.zimagez.com/zimage/screenshotfrom2014-01-13150148.php)

---

### Post by ventrical on 2014-01-13
> **kansasnoob said:**
> I guess I should try a Compiz session sometime but I'm mostly concerned about the Metacity session :(

If someone does figure out how to get a sweet GNOME Flashback (Compiz) session working I'd love to include a link to it in my OP :)

Here is a brief test session with compiz and ccsm.


[https://www.youtube.com/watch?v=nbXtEpznAkE&feature=youtu.be](https://www.youtube.com/watch?v=nbXtEpznAkE&feature=youtu.be)

---

### Post by grahammechanical on 2014-01-13
Here is my 2 cents worth.

Ubuntu+Unity+gnome-session-flashback+with Compiz+4 workspaces

1) Click on a workspace icon and the top and bottom panels disappear.
2) Wait for app indicator icons to appear. Click on workspace icon and top and bottom panels disappear. Open a utility - Ctrl+Alt+T (terminal) and top and bottom panels reappear. Click on app indicator icon and top and bottom panels disappear.
3) Wait for app indicator icons to appear. Click on app indicator icon - work as normal. Click on workspace icon and top and bottom panels disappear. See item 2.

Ctrl+Alt+arrow keys do not switch workspaces.

I have not tested this on with Metacity. I first need to work out how to increase the number of workspaces.

Regards.

---

### Post by Hazzabin on 2014-01-13
[COLOR=#000000]grahammechanical[/COLOR]

Open CompizConfig Settting Manager

goto 'General Options'

find 'Desktop size'  (far right in General Options)

Horizontal Virtual Size, make it '4'   just also make sure the other 2 listed have no numbers entered

Least I should say this works for me as far as 'workspaces', hope it helps

And check this link out, it may help, tho it does apply to 13.04 I see no reason why it be different

[http://askubuntu.com/questions/300974/workspace-switching-via-ctrl-alt-arrow-not-working-after-upgrade-to-13-04-h](http://askubuntu.com/questions/300974/workspace-switching-via-ctrl-alt-arrow-not-working-after-upgrade-to-13-04-h)

---

### Post by PJs Ronin on 2014-01-13
> **grahammechanical said:**
> Here is my 2 cents worth.
Ubuntu+Unity+gnome-session-flashback+with Compiz+4 workspaces
...
I first need to work out how to increase the number of workspaces.

For all intents and purposes I can replicate this to a 'T', but I also have xfce and kde installed into the same partition.

Anyway, Hazzabin then said:
> **Hazzabin said:**
> [COLOR=#000000]grahammechanical[/COLOR]
Open CompizConfig Settting Manager
goto 'General Options'
find 'Desktop size'  (far right in General Options)
Horizontal Virtual Size, make it '4'   just also make sure the other 2 listed have no numbers entered
<snip>

Ahah !!!!!

I have almost the exact same experience as graham and when I try to adjust the number of workspaces using CCSM, the changes don't stick... keeps reverting to '1'.   Have had this b4 [here]("http://ubuntuforums.org/showthread.php?t=2160962&highlight=workspaces").

---

### Post by grahammechanical on 2014-01-15
Oh, I found out how to increase the number of workspaces when in either of the two Gnome flashback sessions. Right click the single workspace icon (bottom panel). Select Preferences and increase the number from one upwards in the dialog. I have no problems switching workspaces in the "with Metacity" flashback session. 

I was out all day yesterday so I could update my post.

@hazzabin

I have made a note of your suggestion. I will test if it works. Workarounds like this will be useful when 14.04 is released and people come on the forum wanting to know how to do this and that.

UPDATE: In the "with Compiz" session we must set the number of workspaces using CCSM. Then we can switch workspaces using either Ctrl+Alt+arrow or by clicking a workspace. The right click workspace icon>Preferences>Increase number from 1 upwards does not work correctly. Do not suggest that way of doing it.

Regards.

---

### Post by psfal on 2014-01-30
> **Cavsfan said:**
> In terminal enter 
```
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'

```

Problem solved.

Thank you :) This was the missing piece for me, I've installed 13.10 to a VM and gotten my Gnome Classic back almost the way it should be. The only thing missing now is my weather applets. If this carries through to 14.04 I'll replace 12.04 on one of my machines and see how efficiently 14.04 uses my hardware. I would like to have my weather applets back too though... Any idea why I have them in 12.04 but not the 13.10 running in VM?

---

### Post by psfal on 2014-01-30
> **kansasnoob said:**
> Not a good way to request help my friend!

Have you even read my OP and followed the links:

[http://ubuntuforums.org/showthread.php?t=2184682&p=12833089#post12833089](http://ubuntuforums.org/showthread.php?t=2184682&p=12833089#post12833089)

Buttons still can be moved to the right, the method has just changed due to the deprecation of gconf.

Calm down and request help rather than ranting or the mods will undoubtedly just start moving your posts to some place where you'll be less likely to get help :)

EDIT: You should know this already:

[http://ubuntuforums.org/showthread.php?t=2169915](http://ubuntuforums.org/showthread.php?t=2169915)

Just ask for help instead of ranting and raving.

Thanks for your post :) I had actually given up on the issue, I've mentioned it before and gotten no usable info, I was actually sending a message to Ubuntu and Ubuntu Gnome devs, so yeah, it was a rant (I may have been off my meds). I'm a 1 DE kind of guy, and I'm not likely to change my outlook. I'm glad to see I'm not the only one who loves Gnome Classic, admittedly I was perhaps not paying enough attention and missed pertinent info from your OP, my apologies for that...

---

### Post by kansasnoob on 2014-01-30
> **psfal said:**
> Thanks for your post :) I had actually given up on the issue, I've mentioned it before and gotten no usable info, I was actually sending a message to Ubuntu and Ubuntu Gnome devs, so yeah, it was a rant (I may have been off my meds). I'm a 1 DE kind of guy, and I'm not likely to change my outlook. I'm glad to see I'm not the only one who loves Gnome Classic, admittedly I was perhaps not paying enough attention and missed pertinent info from your OP, my apologies for that...

Welcome aboard :)

We all have moments where a rant feels like the best response, but I can assure you that the "flashback" session is under active development. Some things get confusing due to the deprecation of gconf in favor of dconf but IMHO most of the changes have been positive :)

---

### Post by kansasnoob on 2014-02-15
There seems to be [some confusion surrounding how to select sessions]("https://lists.launchpad.net/ubuntugnome-qa/msg00314.html") using the various display managers in Trusty so I wanted to post some brief instructions along with pics. Regardless of which dm is used you must first log out, then before logging back in select the desired session as described below.

**[COLOR="#FF0000"]With gdm[/COLOR]**, which is the default Ubuntu GNOME display manager, after clicking on the user name you must click on the "gear" next to "Sign In" and choose the desired session:

[ATTACH=CONFIG]250348[/ATTACH]

**[COLOR="#FF0000"]With lightdm using unity-greeter[/COLOR]** you must first click on the GNOME foot next to the user name:

[ATTACH=CONFIG]250349[/ATTACH]

Then select the desired session:

[ATTACH=CONFIG]250350[/ATTACH]

**[COLOR="#FF0000"]With lightdm using the gtk-greeter[/COLOR]** the session selection is made in the upper right-hand corner of the screen:

[ATTACH=CONFIG]250351[/ATTACH]

I hope that clears up any confusion.

---

### Post by psfal on 2014-02-17
One thing that bothers me a great deal is the fact that my weather applets are gone in 13.10, while I still have them in 12.04. Any explanation for this or means of getting them back? Still got my cpu scaling applets and system monitor applet, but no weather applets available in the menu

---

### Post by kansasnoob on 2014-02-18
> **psfal said:**
> One thing that bothers me a great deal is the fact that my weather applets are gone in 13.10, while I still have them in 12.04. Any explanation for this or means of getting them back? Still got my cpu scaling applets and system monitor applet, but no weather applets available in the menu

I've never used the "weather applet" so I'm clueless :redface:

---

### Post by kansasnoob on 2014-02-18
Something I found interesting while corresponding with a dev concerning changes to GNOME 3.10 that effected keyboard shortcuts and a disappearing mouse pointer:

> I suspect they will be broken either way, we pass off key grabs to gnome-shell when XDG_CURRENT_DESKTOP=GNOME, this is one of the reasons **[COLOR="#FF0000"]flashback is switching to use Unity profile[/COLOR]**

So hold on tight :)

---

### Post by kansasnoob on 2014-02-20
> **kansasnoob said:**
> Something I found interesting while corresponding with a dev concerning changes to GNOME 3.10 that effected keyboard shortcuts and a disappearing mouse pointer:



So hold on tight :)

That was a bad representation of what was said, this is more correct:

> On 18/02/14 19:39, Erick Brunzell wrote:
> On 02/17/2014 06:11 PM, Tim wrote:
>>
>>
>> Hi Lance,
>> On 18/02/14 11:02, Lance wrote:
>>> Rough going. It seems that X is broken in Edubuntu flashback-metacity with those packages, at least both the keyboard and mouse are non functional.
>>>
>> in the flashback session do you have a process called display-config-daemon running?
>
> Haven't gotten that far yet, but I was mistaken.
>
> The keyboard is working, but none of the shortcuts are. The mouse pointer is just invisible, I discovered this by just pressing the left mouse button and dragging I could see the normal artifacts on the screen.
[B]Mouse pointer missing is due to display-config-daemon not running, however I think that should be fixed for flashback now (with trusty2 version)
if now try the following two command
XDG_CURRENT_DESKTOP=Unity /usr/lib/displayconfig/display-config-daemon -r --debug
and in a second terminal
gnome-settings-daemon -r --debug
[/B]
>
> I'm using a wireless Logitech so I swapped in a Zalman wired mouse but no change. The pointer appears on the login screen but not on the desktop after boot completes.
>
> I need to rinse-n-repeat now because I hadn't paid any attention to keyboard shortcuts before installing your PPA. So I'll retest beginning with a new Edubuntu image, then more thoroughly test the default install before applying changes from your PPA.
**I suspect they will be broken either way, we pass off key grabs to gnome-shell when XDG_CURRENT_DESKTOP=GNOME, this is one of the reasons flashback is switching to use Unity profile**


So, as soon as I catch a few winks, I need to do some more testing ;)

---

### Post by cedric5 on 2014-02-28
hello, I am also interested in flashback gnome panel.

As I also want to use the latest gnome color daemon and wacom panel features, I wanted to ask if it is possible to do that with flashback.

So: Newest wacom panel settings (3.10+) is now dependent on a plugin in gnome-settings manager AND one in gnome-settings-daemeon; I read elsewere that flashback does have to use it's own settings-daemon, which would render that functionality unuseable - is that true? Can this functionality be backported to 3.8, as 3.10 seems to get skipped in flashback?

Colord also acts as a plugin of gnome-settings-daemon, so same issue here... I would really like to have full support for these tools - How difficult could it be to port these new versions of the plugins over?

Also, could it be made possible to add and option to display the system menu again as in gnome2? So that we have applications / places /system . Right now, I use classic-panel , a fallback fork of stefan glasenhardt, in 12.04, which provides this.
[h=2][/h][h=2][/h]

---

### Post by kansasnoob on 2014-02-28
> **cedric5 said:**
> hello, I am also interested in flashback gnome panel.

As I also want to use the latest gnome color daemon and wacom panel features, I wanted to ask if it is possible to do that with flashback.

So: Newest wacom panel settings (3.10+) is now dependent on a plugin in gnome-settings manager AND one in gnome-settings-daemeon; I read elsewere that flashback does have to use it's own settings-daemon, which would render that functionality unuseable - is that true? Can this functionality be backported to 3.8, as 3.10 seems to get skipped in flashback?

Colord also acts as a plugin of gnome-settings-daemon, so same issue here... I would really like to have full support for these tools - How difficult could it be to port these new versions of the plugins over?

Also, could it be made possible to add and option to display the system menu again as in gnome2? So that we have applications / places /system . Right now, I use classic-panel , a fallback fork of stefan glasenhardt, in 12.04, which provides this.
[h=2][/h][h=2][/h]

That's way over my head :redface:

Maybe Alberts has an idea :confused:

My personal concern is just making sure "flashback w/metacity" is working well enough for Edubuntu.

---

### Post by cedric5 on 2014-02-28
The only thing I think that is necessary is that flashback works with the default gnome-settings-daemon of the targeted gnome release.  I hope its realistic to assume that this is possible. Backporting the plugins is a whole other issue.

 I read up about g-s-d and fallback and found that support for fallback was removed from g-s-d recently, but as flashback is at least partly gnome-coupled project now, I thought things could have already changed and someone knows more about this issue...

---

### Post by kansasnoob on 2014-02-28
It's certainly a bit different installing 'gnome-panel' in Ubuntu GNOME Trusty now:

> Commit Log for Fri Feb 28 14:04:47 2014


Installed the following packages:
alacarte (3.10.0-1ubuntu1)
geoclue-ubuntu-geoip (1.0.2+14.04.20131125-0ubuntu1)
gir1.2-gconf-2.0 (3.2.6-0ubuntu1)
gir1.2-panelapplet-4.0 (1:3.8.0-1ubuntu8)
gnome-applets (3.5.92-0ubuntu3)
gnome-applets-data (3.5.92-0ubuntu3)
gnome-media (3.4.0-1ubuntu2)
gnome-panel (1:3.8.0-1ubuntu8)
gnome-panel-data (1:3.8.0-1ubuntu8)
gnome-power-manager (3.8.2-1ubuntu2)
gnome-screensaver (3.6.1-0ubuntu9)
gnome-session-flashback (1:3.8.0-1ubuntu8)
gstreamer0.10-gconf (0.10.31-3+nmu1ubuntu4)
indicator-applet (12.10.2+13.10.20130924.2-0ubuntu1)
indicator-applet-complete (12.10.2+13.10.20130924.2-0ubuntu1)
indicator-bluetooth (0.0.6+14.04.20140207-0ubuntu1)
indicator-datetime (13.10.0+14.04.20140227.1-0ubuntu1)
indicator-keyboard (0.0.0+14.04.20140227.3-0ubuntu1)
indicator-messages (13.10.1+14.04.20140207-0ubuntu1)
indicator-power (12.10.6+14.04.20140207-0ubuntu1)
indicator-printers (0.1.7+14.04.20140213-0ubuntu1)
indicator-session (12.10.5+14.04.20140214-0ubuntu1)
indicator-sound (12.10.2+14.04.20140224-0ubuntu1)
libaccount-plugin-1.0-0 (0.1.7~+14.04.20140211.2-0ubuntu3)
libaccount-plugin-generic-oauth (0.11+14.04.20131126.2-0ubuntu1)
libaccount-plugin-google (0.11+14.04.20131126.2-0ubuntu1)
libaccounts-qt5-1 (1.10+13.10.20131016.1-0ubuntu1)
libgee2 (0.6.8-1ubuntu1)
libgnome-media-profiles-3.0-0 (3.0.0-1ubuntu2)
liblightdm-gobject-1-0 (1.9.8-0ubuntu1)
libmetacity-private0a (1:2.34.13-0ubuntu4)
libpanel-applet-4-0 (1:3.8.0-1ubuntu8)
libqt53d5 (5.0~git20130731-0ubuntu1)
libqt5core5 (5.0.2+dfsg1-7ubuntu18)
libqt5dbus5 (5.0.2+dfsg1-7ubuntu18)
libqt5gui5 (5.0.2+dfsg1-7ubuntu18)
libqt5location5 (5.0~git20130805-0ubuntu4)
libqt5network5 (5.0.2+dfsg1-7ubuntu18)
libqt5opengl5 (5.0.2+dfsg1-7ubuntu18)
libqt5printsupport5 (5.0.2+dfsg1-7ubuntu18)
libqt5qml5 (5.0.2-6ubuntu6)
libqt5quick5 (5.0.2-6ubuntu6)
libqt5sensors5 (5.1.1+dfsg-2ubuntu3)
libqt5sql5 (5.0.2+dfsg1-7ubuntu18)
libqt5sql5-sqlite (5.0.2+dfsg1-7ubuntu18)
libqt5test5 (5.0.2+dfsg1-7ubuntu18)
libqt5v8-5 (5.0.2-3)
libqt5webkit5 (5.1.1-1ubuntu4)
libqt5widgets5 (5.0.2+dfsg1-7ubuntu18)
libqt5xml5 (5.0.2+dfsg1-7ubuntu18)
libsignon-extension1 (8.55+14.04.20131212-0ubuntu1)
libsignon-plugins-common1 (8.55+14.04.20131212-0ubuntu1)
libsignon-qt5-1 (8.55+14.04.20131212-0ubuntu1)
libtimezonemap1 (0.4.1)
liburl-dispatcher1 (0.1+14.04.20140217.1-0ubuntu1)
libxcb-randr0 (1.10-2ubuntu1)
libxcb-render-util0 (0.3.8-1.1ubuntu1)
metacity (1:2.34.13-0ubuntu4)
metacity-common (1:2.34.13-0ubuntu4)
signon-keyring-extension (0.6+13.10.20130626-0ubuntu1)
signon-plugin-oauth2 (0.19+14.04.20131126.2-0ubuntu1)
signon-ui (0.15+14.04.20131024.2-0ubuntu1)
signond (8.55+14.04.20131212-0ubuntu1)
unity-control-center (14.04.3+14.04.20140226-0ubuntu1)
unity-control-center-signon (0.1.7~+14.04.20140211.2-0ubuntu3)


---

### Post by cedric5 on 2014-02-28
ok..You have not installed with --no-install-recommends  - much less dependencies then


> sudo apt-get install gnome-panel  gnome-applets gnome-session-flashback --no-install-recommends

gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel gnome-panel-data gnome-session-flashback libmetacity-private0a libpanel-applet-4-0 metacity metacity-common

I took a look and it looks like right now there is the default g-s-d (which is 3.8 right now - shouldn't be there  a version bump to 3.10 in final? I guess not because of feature freeze time) in as dependency in which is good.
 gnome control-center is still 3.6?!? and I know canonical is doing a quick fork just for LTS..


have to try around if that works out as expected, but I hope so.
only thing which bothers me is dependency on nautilus 3.8+, which is a bit harsh, 3.4 minimum and  nemo  (so nautilus (>=3.4) | nemo) would  be a wiser choice nowadays, because not everyone likes crippled filebrowsers

---

### Post by kansasnoob on 2014-02-28
> **cedric5 said:**
> ok..You have not installed with --no-install-recommends  - much less dependencies then




I took a look and it looks like right now there is the default g-s-d (which is 3.8 right now - shouldn't be there  a version bump to 3.10 in final? I guess not because of feature freeze time) in as dependency in which is good.
 gnome control-center is still 3.6?!? and I know canonical is doing a quick fork just for LTS..


have to try around if that works out as expected, but I hope so.
only thing which bothers me is dependency on nautilus 3.8+, which is a bit harsh, 3.4 minimum and  nemo  (so nautilus (>=3.4) | nemo) would  be a wiser choice nowadays, because not everyone likes crippled filebrowsers

I performed some testing with these additional packages:

[https://launchpad.net/~darkxst/+archive/gnome-desktop/+index?field.series_filter=](https://launchpad.net/~darkxst/+archive/gnome-desktop/+index?field.series_filter=)

But there were bumps in the road :(

You can read starting here:

[https://lists.launchpad.net/ubuntugnome-qa/msg00320.html](https://lists.launchpad.net/ubuntugnome-qa/msg00320.html)

A few things got ugly though, like an invisible mouse pointer and broken keyboard shortcuts.

I'm not sure where Tim is on getting those last changes into Trusty ATM. He had indicated that he'd need to request an exception at this point in development.

Things are a bit on the ugly side ATM though.

---

### Post by cedric5 on 2014-02-28
already found  that in [gnome-flashback-list]("https://mail.gnome.org/mailman/listinfo/gnome-flashback-list").... looks not too bad, but shurely someone capable has to fix it.

---

### Post by kansasnoob on 2014-02-28
> **cedric5 said:**
> already found  that in [gnome-flashback-list]("https://mail.gnome.org/mailman/listinfo/gnome-flashback-list").... looks not too bad, but shurely someone capable has to fix it.

I'm Erick there :D

If I were to guess I'd say they're waiting for the last shoe to drop in this transition from g-s-d to u-s-d, but that's only a guess!

---

### Post by Cavsfan on 2014-03-06
Any one else using flashback (with compiz) and experiencing the problem with the CCSM Windows Decoration is unchecked at startup or after logging out and back in.
It even becomes unchecked when you open CCSM and you have to re-check the box.

I thought with the compiz updates lately that this would be fixed but it is definitely not. I installed Emerald.

I opened a bug on the issue but I am the only one on it.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1284266](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1284266)

Maybe if more people signed onto the bug it might stand a better chance of being fixed.

Regards

---

### Post by xc3RnbFO8P on 2014-03-06
I cant start CCSM anymore.
But Compiz works fine in Flashback sessions,
no problem at all :)

> rig@rig-Aspire-R3600:~$ ccsm
Gtk-Message: Failed to load module "unity-gtk-module"

(ccsm:5183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ccsm:5183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ccsm:5183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(ccsm:5183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
Segmentation fault (core dumped)
rig@rig-Aspire-R3600:~$ 
[[img]http://farm3.staticflickr.com/2851/12972966834_b954d3f585_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12972966834/)
[Screenshot from 2014-03-06 12:04:22](http://www.flickr.com/photos/96052779@N07/12972966834/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by mc4man on 2014-03-06
> **Cavsfan said:**
> Any one else using flashback (with compiz) and experiencing the problem with the CCSM Windows Decoration is unchecked at startup or after logging out and back in.
It even becomes unchecked when you open CCSM and you have to re-check the box.


On a testing install (Ubuntu) with flashback added can't say I see this, the decor plugin is always enabled in a flashback/compiz session, either on fresh boot or via a login. Could be some local issue to you
Create a new user account & see how it fares.

(only issue I see is nautilus can't be resized from cursor grab which is too bad considering the current shrinking window bug in compiz

---

### Post by mc4man on 2014-03-06
> **Ringi said:**
> I cant start CCSM anymore.

likely self inflicted, seg faults should produce a crash report, open it up maybe you can glean some useful info

---

### Post by xc3RnbFO8P on 2014-03-06
> **mc4man said:**
> likely self inflicted, seg faults should produce a crash report, open it up maybe you can glean some useful info

I dont get any crash report, compiz works fine ( cube etc, ), its just ccsm that will not open.

Edit: this has nothing to do with Gnome Flashback sessions.

Solution was to remove **compizconfig-backend-kconfig**

---

### Post by mc4man on 2014-03-06
> **Ringi said:**
> I dont get any crash report, compiz works fine ( cube etc, ), its just ccsm that will not open.

Edit: this has nothing to do with Gnome Flashback sessions.

Solution was to remove **compizconfig-backend-kconfig**
for any future use - usually worth checking /var/crash after a segfault if no popup

---

### Post by xc3RnbFO8P on 2014-03-06
> **mc4man said:**
> for any future use - usually worth checking /var/crash after a segfault if no popup

Yes I do that thanks

---

### Post by Cavsfan on 2014-03-06
> **mc4man said:**
> On a testing install (Ubuntu) with flashback added can't say I see this, the decor plugin is always enabled in a flashback/compiz session, either on fresh boot or via a login. Could be some local issue to you
Create a new user account & see how it fares.

(only issue I see is nautilus can't be resized from cursor grab which is too bad considering the current shrinking window bug in compiz

Indeed you were right. I created another user and windows decorator was checked. I pointed it to /usr/bin/emerald and it worked like a charm. Would you have any idea why my other userid doesn't work?

Thanks

---

### Post by mc4man on 2014-03-06
> **Cavsfan said:**
> Indeed you were right. I created another user and windows decorator was checked. I pointed it to /usr/bin/emerald and it worked like a charm. Would you have any idea why my other userid doesn't work?

Thanks

1st thing to check would be what profile, should be "Default"
(start ccsm from terminal

---

### Post by Cavsfan on 2014-03-06
> **mc4man said:**
> 1st thing to check would be what profile, should be "Default"
(start ccsm from terminal

LOL! I'm pretty stunned!

This is my initial login which I use.
```
cavsfan@cavsfan-MS-7529:~$ ccsm
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
Loading icons...
```


This is the test one I created and it says "Default"
```
test1@cavsfan-MS-7529:~$ ccsm
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
Loading icons...
```

You are good! Is there a way to make my first one default?
Thanks!

---

### Post by mc4man on 2014-03-06
> **Cavsfan said:**
>  Is there a way to make my first one default?
Thanks!
Best case scenario - 
open ccsm > Preferences
In the Profiles box expand & pick Default. (there may be 2, choose the 'middle' one.
Then  enable deco if it isn't, close ccsm & do a log out in & see

---

### Post by Cavsfan on 2014-03-07
> **mc4man said:**
> Best case scenario - 
open ccsm > Preferences
In the Profiles box expand & pick Default. (there may be 2, choose the 'middle' one.
Then  enable deco if it isn't, close ccsm & do a log out in & see

I tried that a few times and it keeps going back to Unity. I've logged off and rebooted and still the same results.
This morning I purged compizconfig-settings-manager, rebooted and logged into the test uid and installed it there.

Logged back out and into my regular account and it still defaults to Unity. I can change it and set the checkmark in window decoration.
Then just by opening CCSM up it removes the checkmark and the window decoration disappears and it goes back to Unity.

Any other possibilities?

---

### Post by xc3RnbFO8P on 2014-03-07
Have you try this:

---

### Post by mc4man on 2014-03-07
If what Ringi suugested doesn't work then a sledgehammer approach - 
Open  ~/.config/dconf
Rename user file to user.bak
You then need to do a restart *without* logging out, either use some means to kill X or otherwise kill your session
If a log out or normal restart is done then the new user file will be the same as the .bak (at least this is what happens in an ubuntu/unity session

Another alternative to above is to access the above location from another install or user, then you 'should' get a new default user file
or
maybe there is a command to reset dconf settings to default for your session, haven't paid attention...

---

### Post by Cavsfan on 2014-03-07
I tried Ringi's approach and it still defaulted back to Unity.

I found this about how to reset the configuration for Compiz:

```
cd /home/cavsfan/; rm -rf .gnome .gnome2 .gconf .gconfd .metacity .compiz-1 .config/compiz-1 .config/dconf
```

I don't have a .gnome folder or a .metacity folder and have .compiz and not .compiz-1. I also have .config/compiz-1 and .config/dconf

Would that be worth a shot or should I do as you said Mc4man?

---

### Post by mc4man on 2014-03-07
> **Cavsfan said:**
> I tried Ringi's approach and it still defaulted back to Unity.

I found this about how to reset the configuration for Compiz:

```
cd /home/cavsfan/; rm -rf .gnome .gnome2 .gconf .gconfd .metacity .compiz-1 .config/compiz-1 .config/dconf
```

I don't have a .gnome folder or a .metacity folder and have .compiz and not .compiz-1. I also have .config/compiz-1 and .config/dconf

Would that be worth a shot or should I do as you said Mc4man?
Me - I'd just whack the user file & see
So - 
if you don't have any easy means to kill x other than holding power button till pc shuts down you can re-enable ctrl+alt+backspace to 'kill xserver' like this

```
gsettings set org.gnome.desktop.input-sources xkb-options  "['terminate:ctrl_alt_bksp']"
```

The either delete that user file or rename to a .bak
As soon as that's done kill X, then see what shakes out when you log back in

---

### Post by Cavsfan on 2014-03-07
> **mc4man said:**
> If what Ringi suugested doesn't work then a sledgehammer approach - 
Open  ~/.config/dconf
Rename user file to user.bak
You then need to do a restart *without* logging out, either use some means to kill X or otherwise kill your session
If a log out or normal restart is done then the new user file will be the same as the .bak (at least this is what happens in an ubuntu/unity session

Another alternative to above is to access the above location from another install or user, then you 'should' get a new default user file
or
maybe there is a command to reset dconf settings to default for your session, haven't paid attention...

I tried this renaming user to user.bak. Then pressed Cntl+Alt+F1, and logged in then issued **sudo service lightdm stop** and it stopped. I pressed Cntl+Alt+F7 and got a blank screen.
Then entered **sudo service lightdm start** and it brought up the login screen.
Checked CSM and it was still set to Unity without windows deco. 
Is there anything I did wrong? This stops X doesn't it?

This is just after logging in:
```
cavsfan@cavsfan-MS-7529:~$ dconf dump /org/compiz/
[/]
existing-profiles=['Default', 'unity']
current-profile='[COLOR=#ff0000]unity[/COLOR]'

[profiles/Default/plugins/thumbnail]
thumb-color='#0000007f'
font-background-color='#0000007f'

[profiles/Default/plugins/wall]
thumb-highlight-gradient-shadow-color='#dfdfdfff'
arrow-base-color='#e6e6e6d9'
arrow-shadow-color='#dcdcdcd9'

[profiles/Default/plugins/composite]
refresh-rate=50

[profiles/Default/plugins/cube]
top-color='#17855aff'
bottom-color='#fe4f4dff'
skydome=true
skydome-gradient-start-color='#0050ffff'
skydome-image='/home/cavsfan/Pictures/The-Sea_1920x1200_cool_twitter_backgrounds1.jpg'
skydome-gradient-end-color='#ff0061ff'

[profiles/Default/plugins/decor]
command='/usr/bin/[COLOR=#ff0000]emerald[/COLOR]'

```

```
cavsfan@cavsfan-MS-7529:~$ dconf dump /org/compiz/
[/]
existing-profiles=['Default', 'unity']
current-profile='[COLOR=#ff0000]Default[/COLOR]'

[profiles/Default/plugins/thumbnail]
thumb-color='#0000007f'
font-background-color='#0000007f'

[profiles/Default/plugins/wall]
thumb-highlight-gradient-shadow-color='#dfdfdfff'
arrow-base-color='#e6e6e6d9'
arrow-shadow-color='#dcdcdcd9'

[profiles/Default/plugins/composite]
refresh-rate=50

[profiles/Default/plugins/cube]
top-color='#17855aff'
bottom-color='#fe4f4dff'
skydome=true
skydome-gradient-start-color='#0050ffff'
skydome-image='/home/cavsfan/Pictures/The-Sea_1920x1200_cool_twitter_backgrounds1.jpg'
skydome-gradient-end-color='#ff0061ff'

[profiles/Default/plugins/decor]
command='/usr/bin/[COLOR=#ff0000]emerald[/COLOR]'

```

So the only issue is current-profile which will not stay at Default.

---

### Post by Cavsfan on 2014-03-07
> **mc4man said:**
> Me - I'd just whack the user file & see
So - 
if you don't have any easy means to kill x other than holding power button till pc shuts down you can re-enable ctrl+alt+backspace to 'kill xserver' like this

```
gsettings set org.gnome.desktop.input-sources xkb-options  "['terminate:ctrl_alt_bksp']"
```

The either delete that user file or rename to a .bak
As soon as that's done kill X, then see what shakes out when you log back in

I renamed the user file and pressed cntl+alt+backspace and it brought me to the login screen.
When I logged in Unity was still in control not default.

---

### Post by mc4man on 2014-03-07
true but not helpful

---

### Post by mc4man on 2014-03-07
looks like I'll need to install flashback as if I change in a unity session to Default profile, log out then in it stays on Default
 If I then remove the user file, log out then back to unity normally  it switches to unity profile. 
Have you tried switching to Default, then delete the user file & do a normal log out/in?

---

### Post by mc4man on 2014-03-07
First - something doesn't quite add up as you've described
When in a flashback compiz session here & the profile is 'unity' then I get a unity launcher & no panel indicators, you don't seem to have that?

Anyway, the only way I found to switch back to Default profile other than doing in ccsm (though again here the switch back in ccsm sticks thru a log out/in

In ~/.local/share there are some files, delete  - 
session_migration-gnome-fallback-compiz
and for good measure - 
gsettings-data-convert

Then do a restart (because I had nothing else  used sudo reboot in a terminal

---

### Post by Cavsfan on 2014-03-07
> **mc4man said:**
> Have you tried switching to Default, then delete the user file & do a normal log out/in?

I just did and got the same results: Unity instead of Default.

Thanks for your help!

---

### Post by mc4man on 2014-03-07
> **Cavsfan said:**
> I just did and got the same results: Unity instead of Default.

Thanks for your help!
Did you try post 301?

---

### Post by Cavsfan on 2014-03-07
> **mc4man said:**
> Did you try post 301?

No I missed that. Trying it now.

---

### Post by Cavsfan on 2014-03-07
> **mc4man said:**
> First - something doesn't quite add up as you've described
When in a flashback compiz session here & the profile is 'unity' then I get a unity launcher & no panel indicators, you don't seem to have that?

Anyway, the only way I found to switch back to Default profile other than doing in ccsm (though again here the switch back in ccsm sticks thru a log out/in

In ~/.local/share there are some files, delete  - 
session_migration-gnome-fallback-compiz
and for good measure - 
gsettings-data-convert

Then do a restart (because I had nothing else  used sudo reboot in a terminal

I tried deleting those files and restarted and same thing Preferences is Unity with no Unity laucher and no panel indicators. I cannot click on the top of any window to move it without Windows decoration being checked. Terminal I can drag around but there is no deco and CCSM is unmovable without deco.
I cannot resize anything without window deco and the only way I can close windows is by clicking on it in the bottom bar and right clicking then close.

Here's a pic with terminal, desktop in nemo and CCSM open:

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-03-07162345.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-03-07162345.php")

---

### Post by Hazzabin on 2014-03-07
I'm a little confused here guys

No where in any of my Ubuntu Gnome 14.04 with compiz flashback do I have the 'unity' showing in ccsm, is it possibly that you guys are running
Ubuntu 14.04 'Unity' with compiz flashback.

A re-install of 14.04 Unity with compiz flashback (latest one dated 6th March) now doesn't have any of those issues, least ways I'm not getting them now

Should also mention a fresh install of Ubuntu Gnome 14.04 with compiz flashback is behaving way better too, tho not as good as with Unity installs

Only thing I did find out that having Gnome with Unity installed and with compiz flashback simiply doesnt work least not for me

---

### Post by Cavsfan on 2014-03-08
> **Hazzabin said:**
> I'm a little confused here guys

No where in any of my Ubuntu Gnome 14.04 with compiz flashback do I have the 'unity' showing in ccsm, is it possibly that you guys are running
Ubuntu 14.04 'Unity' with compiz flashback.

[COLOR=#0000ff]A re-install of 14.04 Unity with compiz flashback (latest one dated 6th March) now doesn't have any of those issues, least ways I'm not getting them now[/COLOR]

Should also mention a fresh install of Ubuntu Gnome 14.04 with compiz flashback is behaving way better too, tho not as good as with Unity installs

Only thing I did find out that having [COLOR=#0000ff]Gnome with Unity installed and with compiz flashback simply doesn’t work least not for me[/COLOR]

That's what I'm thinking: a new install but think I'll hold out a little longer since I can make this one work with a little fiddling. The question is which one to install.
Don't the blue lines in your reply contradict each other? Not sure if I go with the regular Ubuntu ISO and install flashback or the UbuntuGnome ISO and install flashback. I'm confused.

---

### Post by grahammechanical on 2014-03-08
My early testing of Flashback in Trusty Tahr (not to be confused with Fallback) I learnt that in Ubuntu Gnome it is better to install Gnome Classic as it is a Gnome shell extension than to install gnome-session-flashback.

I also learnt that in Ubuntu+Unity it is best to install gnome-session-flashback and not the old gnome classic or Fallback. Or whatever you want to call it. The technology (software libraries) has moved on. What worked in 12.04 is not necessarily good for 14.04.

I also noticed that in Ubuntu+Unity+Flashback (with Compiz) that CCSM collides with Appearance settings and can mess things up with plain Ubuntu+Unity.

It seems that the delay in putting the app indicators in the top panel bug has been solved. At least on my machine as of yesterday.

As a side issue because of having the proposed repository enabled and the Unity 8 preview session installed I now have both the Standard network app indicator and the mobile app indicator and also the standard System Settings and the mobile System Settings. This is not much of a problem until we switch into Gnome Flashback with Compiz or with Metacity it makes no differences.

1) The network indicator icon does not appear in the top panel but Ubuntu still connects to the router and Internet.

2) The System Settings that loads from the menu structure is the mobile system settings.

There is a confusion due to having the same names but in Ubuntu+Unity this problem does not happen. It is something to watch out for as we move into U<code name> development cycle and further convergence.

Regards.

---

### Post by Cavsfan on 2014-03-08
> **grahammechanical said:**
> My early testing of Flashback in Trusty Tahr (not to be confused with Fallback) I learnt that in Ubuntu Gnome it is better to install Gnome Classic as it is a Gnome shell extension than to install gnome-session-flashback.

I also learnt that in Ubuntu+Unity it is best to install gnome-session-flashback and not the old gnome classic or Fallback. Or whatever you want to call it. The technology (software libraries) has moved on. What worked in 12.04 is not necessarily good for 14.04.

I also noticed that in Ubuntu+Unity+Flashback (with Compiz) that CCSM collides with Appearance settings and can mess things up with plain Ubuntu+Unity.

It seems that the delay in putting the app indicators in the top panel bug has been solved. At least on my machine as of yesterday.

As a side issue because of having the proposed repository enabled and the Unity 8 preview session installed I now have both the Standard network app indicator and the mobile app indicator and also the standard System Settings and the mobile System Settings. This is not much of a problem until we switch into Gnome Flashback with Compiz or with Metacity it makes no differences.

1) The network indicator icon does not appear in the top panel but Ubuntu still connects to the router and Internet.

2) The System Settings that loads from the menu structure is the mobile system settings.

There is a confusion due to having the same names but in Ubuntu+Unity this problem does not happen. It is something to watch out for as we move into U<code name> development cycle and further convergence.

Regards.

Thanks for the reply. I gave up and am downloading a new Ubuntu ISO. I already backed everything up so just have to wait for the DVD to finish formatting and the download to complete.
This is an install from January 9th I have and it's probably time to get a fresh copy anyway. I'm currently in Precise (what I consider my main install) and am loving it! :D

Compiz had the burn deco and the beam me up deco. I'm going to miss those. But I will hang on until the very end.

---

### Post by Cavsfan on 2014-03-08
> **grahammechanical said:**
> My early testing of Flashback in Trusty Tahr (not to be confused with Fallback) I learnt that in Ubuntu Gnome it is better to install Gnome Classic as it is a Gnome shell extension than to install gnome-session-flashback.

I also learnt that in Ubuntu+Unity it is best to install gnome-session-flashback and not the old gnome classic or Fallback. Or whatever you want to call it. The technology (software libraries) has moved on. What worked in 12.04 is not necessarily good for 14.04.

I also noticed that in Ubuntu+Unity+Flashback (with Compiz) that CCSM collides with Appearance settings and can mess things up with plain Ubuntu+Unity.

It seems that the delay in putting the app indicators in the top panel bug has been solved. At least on my machine as of yesterday.

As a side issue because of having the proposed repository enabled and the Unity 8 preview session installed I now have both the Standard network app indicator and the mobile app indicator and also the standard System Settings and the mobile System Settings. This is not much of a problem until we switch into Gnome Flashback with Compiz or with Metacity it makes no differences.

1) The network indicator icon does not appear in the top panel but Ubuntu still connects to the router and Internet.

2) The System Settings that loads from the menu structure is the mobile system settings.

There is a confusion due to having the same names but in Ubuntu+Unity this problem does not happen. It is something to watch out for as we move into U<code name> development cycle and further convergence.

Regards.

Got it going pretty smooth at this point. I installed the Ubuntu+Unity ISO and am getting ready to install gnome-session-flashback all by itself as you mentioned. I'd like to give Unity more of a chance but I cannot get the buttons to move to the right as I am used to. I keep pressing the wrong window buttons. Here goes..... What could go wrong right? :)

---

### Post by Hazzabin on 2014-03-09
> **Cavsfan said:**
> Got it going pretty smooth at this point. I installed the Ubuntu+Unity ISO and am getting ready to install gnome-session-flashback all by itself as you mentioned. I'd like to give Unity more of a chance but I cannot get the buttons to move to the right as I am used to. I keep pressing the wrong window buttons. Here goes..... What could go wrong right? :)

The above is what I did and found the Ubuntu Unity with gnome session flashback to be almost perfect, and I also did it for same reasons buttons on the right side.
3 days and still going strong, well least mine is :P

---

### Post by Cavsfan on 2014-03-09
> **Hazzabin said:**
> The above is what I did and found the Ubuntu Unity with gnome session flashback to be almost perfect, and I also did it for same reasons buttons on the right side.
3 days and still going strong, well least mine is :P

Unity is working pretty well is seems like while flashback is semi ok but not perfect. My conky won't run in flashback but it will in Unity which is odd.
It seemed that the gear button at the top right would logout and restart before I installed flashback but, now those 2 items do not work in either flashback or unity.
Here is exactly what installed and I didn't install any suggested packages:

```
cavsfan@cavsfan-MS-7259:~$ sudo apt-get install gnome-session-flashback
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-screensaver gnome-session
  gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base gnome-themes-standard
The following NEW packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-screensaver gnome-session
  gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon
0 upgraded, 21 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5 MB of archives.
After this operation, 51.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

---

### Post by Cavsfan on 2014-03-09
It would seem that when you install Ubuntu+Unity alone everything seems to work pretty well.
But once you throw gnome flashback in the mix, a lot of things break.

IMO the developers have their job cut out for them to get them working together.

Which is why I was thinking that the plain Ubuntu ISO with Unity should not allow gnome flashback to be added.
While the UbuntuGnome ISO should not have Unity on it and just gnome flashback and gnome classic. 
I wonder if that is the way it will pan out.

---

### Post by kansasnoob on 2014-03-09
> **Cavsfan said:**
> It would seem that when you install Ubuntu+Unity alone everything seems to work pretty well.
But once you throw gnome flashback in the mix, a lot of things break.

IMO the developers have their job cut out for them to get them working together.

Which is why I was thinking that the plain Ubuntu ISO with Unity should not allow gnome flashback to be added.
While the UbuntuGnome ISO should not have Unity on it and just gnome flashback and gnome classic. 
**[COLOR="#FF0000"]I wonder if that is the way it will pan out.[/COLOR]**

Not a chance in the world :)

Ubuntu GNOME's focus is on being as close to pure GNOME as possible using Ubuntu as it's base. The GNOME devs have no interest in supporting either the flashback session or compiz.

OTOH Edubuntu, which does receive a lot of internal support from Canonical, does rely on flashback w/metacity for it's LTSP installs so by the time 14.04.1 drops you should be able to expect the flashback w/metacity session to work fairly well.

If I had my druthers I'd prefer we stop offering the flashback w/compiz session altogether because it doesn't really get any love at the *buntu level :D

---

### Post by Cavsfan on 2014-03-09
> **kansasnoob said:**
> Not a chance in the world :)

Ubuntu GNOME's focus is on being as close to pure GNOME as possible using Ubuntu as it's base. The GNOME devs have no interest in supporting either the flashback session or compiz.

OTOH Edubuntu, which does receive a lot of internal support from Canonical, does rely on flashback w/metacity for it's LTSP installs so by the time 14.04.1 drops you should be able to expect the flashback w/metacity session to work fairly well.

If I had my druthers I'd prefer we stop offering the flashback w/compiz session altogether because it doesn't really get any love at the *buntu level :D

Thanks for that inspiring information! :)

---

### Post by Cavsfan on 2014-03-10
> **kansasnoob said:**
> If I had my druthers I'd prefer we stop offering the flashback w/compiz session altogether because it doesn't really get any love at the *buntu level :D

If compiz is so unloved by the developers, then why does compiz come installed on a basic Ubuntu+Unity ISO?

IMHO flashback w/compiz is way more popular than flashback w/metacity. I have heard many, many people say they are running flashback w/compiz.

If you got your druthers, there would probably be many jump from Ubuntu to another disto.

Just sayin... ;)

---

### Post by kansasnoob on 2014-03-10
> **Cavsfan said:**
> If compiz is so unloved by the developers, then why does compiz come installed on a basic Ubuntu+Unity ISO?

IMHO flashback w/compiz is way more popular than flashback w/metacity. I have heard many, many people say they are running flashback w/compiz.

If you got your druthers, there would probably be many jump from Ubuntu to another disto.

Just sayin... ;)

My point is that none of the official Ubuntu flavors focus on, or devote any resources to flashback w/compiz, whereas Edubuntu dev does provide support for flashback w/metacity. Don't worry about me getting my druthers - it seldom happens :)

---

### Post by philinux on 2014-03-10
> **Cavsfan said:**
> If compiz is so unloved by the developers, then why does compiz come installed on a basic Ubuntu+Unity ISO?



Simples. Unity is a compiz plugin. :)

---

### Post by kansasnoob on 2014-03-10
> **philinux said:**
> Simples. Unity is a compiz plugin. :)

Isn't there a planned change in that regard?

I don't mean in Trusty, but in the future getting away from compiz altogether?

---

### Post by philinux on 2014-03-10
[http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/](http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/) 
I think that would be unity 8.

Aka unity next.

[http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced](http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced)

---

### Post by Cavsfan on 2014-03-10
> **kansasnoob said:**
> My point is that none of the official Ubuntu flavors focus on, or devote any resources to flashback w/compiz, whereas Edubuntu dev does provide support for flashback w/metacity. Don't worry about me getting my druthers - it seldom happens :)

I have never been able to get flashback w/metacity to work even slightly. Therefore I will not bother with it. :) I have however gotten flashback w/compiz to work.
Right now though it will not allow my conky to run so I am in Unity with conky working just fine. I don't understand why there would be a difference.

> **philinux said:**
> Simples. Unity is a compiz plugin. :)

Ironic. :)

I re-installed again today and I think I'm worse off than I was a week ago. *sigh*
Guess I'll just ride this puppy out for a while. :)

Screenshot came installed with no functionality. There is no button to click to take a screenie. 
Cairo Dock is a beta version and there is no text to go with the things in the dock so it's hard to tell what is what unless you can tell by the icon like Firefox.
There may be a setting somewhere but you'd think it would come on by default. 8-[

---

### Post by Cavsfan on 2014-03-10
> **philinux said:**
> [http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/](http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/) 
I think that would be unity 8.

Aka unity next.

[http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced](http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced)

I did a find on that page and didn't see compiz mentioned. FWIW

EDIT: Nevermind I see it on the 2nd link. Got ahead of myself. :)

---

### Post by Cavsfan on 2014-03-10
> **philinux said:**
> [http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/](http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/) 
I think that would be unity 8.

Aka unity next.

[http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced](http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced)

I did notice this on the 2nd link: [COLOR=#ff0000]**Notice:** This post is more than a year old. It may be outdated. [/COLOR]

---

### Post by philinux on 2014-03-10
> **Cavsfan said:**
> I did notice this on the 2nd link: [COLOR=#ff0000]**Notice:** This post is more than a year old. It may be outdated. [/COLOR]

Yep indeed. There was a lot of stuff intended for 14.04 that got pushed back to the future.

---

### Post by kansasnoob on 2014-03-10
> **philinux said:**
> [http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/](http://www.jonobacon.org/2013/08/27/ubuntu-in-a-nutshell-unity-and-convergence/) 
I think that would be unity 8.

Aka unity next.

[http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced](http://www.omgubuntu.co.uk/2013/03/unity-next-project-announced)

That's what I thought :)

I must say though that I'm impressed at how well Gallium/w llvmpipe works on really crappy hardware:

[http://ubuntuforums.org/showthread.php?t=2207391&page=3&p=12952358#post12952358](http://ubuntuforums.org/showthread.php?t=2207391&page=3&p=12952358#post12952358)

Sadly I blew it up dinking with resolution changes, but that's how we learn :D

---

### Post by mc4man on 2014-03-10
> **Cavsfan said:**
> 

Screenshot came installed with no functionality. There is no button to click to take a screenie. 
[

Edit: all below plus one on mpv will be fixed in next compiz

known issue, click on title bar of any such window that's missing it's bottom (or move the window, whatever
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/1288408](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/1288408)
related to - 
[https://bugs.launchpad.net/compiz/+bug/1287472](https://bugs.launchpad.net/compiz/+bug/1287472)
which came from fixing this - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1282304](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1282304)

---

### Post by kansasnoob on 2014-03-11
The flashback w/metacity session is working quite well for me in both Ubuntu and Edubuntu ATM, it's a bit problematic in Ubuntu GNOME though.

I do wish we could correct the menu:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

I think Alberts has a patch :confused:

---

### Post by Cavsfan on 2014-03-11
> **philinux said:**
> Yep indeed. There was a lot of stuff intended for 14.04 that got pushed [COLOR=#ff0000]back to the future[/COLOR].

That in red reminds me of a movie. :lol:

> **mc4man said:**
> Edit: all below plus one on mpv will be fixed in next compiz

known issue, click on title bar of any such window that's missing it's bottom (or move the window, whatever
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/1288408](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/1288408)
related to - 
[https://bugs.launchpad.net/compiz/+bug/1287472](https://bugs.launchpad.net/compiz/+bug/1287472)
which came from fixing this - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1282304](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1282304)

Thanks! I signed on to all of them as affected. 
I have one more issue with flashback w/compiz: my conky won't run. It runs fine in Unity. In flashback w/metacity it works but there is a black background and Cairo Dock is all messed up.

It gets some sort of X server error but only in flashback w/compiz.

```
cavsfan@cavsfan-MS-7259:~$ conky -c /home/cavsfan/.conkyrc.vindsl
Conky: unknown variable 
Conky: forked to background, pid is 30059
cavsfan@cavsfan-MS-7259:~$ 
Conky: desktop window (160000b) is subwindow of root window (26e)
Conky: window type - normal
Conky: drawing to created window (0x3800002)
Conky: drawing to double buffer
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x3800003
  Serial number of failed request:  184
  Current serial number in output stream:  186

```

And it only happens on new ISOs within the past week. I installed twice and no bueno. I am just using the 331.38 nvidia driver in the repositories:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                            331.38-0ubuntu4                                       amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                 331.38-0ubuntu4                                       amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.38-0ubuntu4                                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6                                                   amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                       amd64        Tool for configuring the NVIDIA graphics driver

```

Any clue to why this is happening? Am I missing a component?  I surely can't be the only one.

---

### Post by Cavsfan on 2014-03-11
I no more than posted the above and checked for updates:
```
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compizconfig-settings-manager gir1.2-panelapplet-4.0 gnome-panel gnome-panel-data gnome-session-flashback libcompizconfig0 libdecoration0
  libnautilus-extension1a libpanel-applet-4-0 libthumbnailer0 libunity-gtk2-parser0 libunity-gtk3-parser0 libupstart1 nautilus nautilus-data python-compizconfig unity-gtk-module-common unity-gtk2-module
  unity-gtk3-module upstart
25 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

That fixed both the screenshot buttons and now my conky runs in flashback w/compliz. Cooking with gas! :popcorn:

---

### Post by mc4man on 2014-03-11
> **Cavsfan said:**
> I no more than posted the above and checked for updates:
That fixed both the screenshot buttons and now my conky runs in flashback w/compliz. Cooking with gas! :popcorn:
In addition to compiz fixes there was this for gnome-panel (flashback
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1224217](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1224217)
So hopefully the experience is omproved (only have unity here atm

---

### Post by kansasnoob on 2014-03-16
Hat tip to Alberts :D

We may get a sensible menu back:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

I had an opportunity to raise the issue on the Ubuntu GNOME mailing list:

[https://lists.launchpad.net/ubuntugnome-qa/msg00403.html](https://lists.launchpad.net/ubuntugnome-qa/msg00403.html)

Thanks Alberts.

---

### Post by muktupavels on 2014-03-17
Old menu should be back now. :)

---

### Post by kansasnoob on 2014-03-17
> **albertsmuktupavels said:**
> Old menu should be back now. :)

Looks great :guitar:

Many, many thanks.

---

### Post by Cavsfan on 2014-03-17
Yeah I got in updates this morning. It's a huge improvement! 

Thanks Alberts! :)

---

### Post by kansasnoob on 2014-03-29
@ Alberts,

Now that we're in the final stretch of the race toward Trusty final I decided to do some fine tuning to the Main Menu :)

Main Menu appears both in System Tools > Preferences and Accessories and I've tried opening it from both menu items with the same results.

You can open Main Menu but it displays the "old" menu - including Sundry and Utilities - and making changes have no effect at all on the menus :(

Do you want me to file a new bug report?

If so should I file against 'gnome-panel', 'gnome-session-flashback', or 'gnome-menus'?

---

### Post by kansasnoob on 2014-03-29
Well it's crunch time again ;)

In order that others can follow what I'm doing I'll start posting a lot of "thinking out loud" stuff here. In this case I have a fresh install of Ubuntu Trusty final Beta and I want to record what happens when I install 'gnome-panel':

```
lance@lance-desktop:~$ sudo apt-get install gnome-panel
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel-data gnome-session gnome-session-flashback
  gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete
  libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0
  metacity notification-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base
  gnome-themes-standard
[B]The following NEW packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel gnome-panel-data gnome-session
  gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf
  indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1
  libpanel-applet-4-0 metacity notification-daemon[/B]
0 upgraded, 20 newly installed, 0 to remove and 117 not upgraded.
Need to get 10.2 MB of archives.
**[COLOR="#FF0000"]After this operation, 50.5 MB of additional disk space will be used.[/COLOR]**

```

Stay tuned :guitar:

Edit #1: First flashback w/metacity login looks good:

[ATTACH=CONFIG]251562[/ATTACH]

Edit #2: Flashback w/compiz is broken in many ways, but my focus is on the metacity session anyway. Someone else will have to deal with the complexities of compiz. Sorry but that's just the way it is :sad:

Edit #3: I know I'm going to want some additional packages and I'm going to list them one by one:

```
lance@lance-desktop:~$ sudo apt-get install dconf-tools
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dconf-editor
[B]The following NEW packages will be installed:
  dconf-editor dconf-tools[/B]
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 113 kB of archives.
**[COLOR="#FF0000"]After this operation, 528 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
[B]The following NEW packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
  gnome-tweak-tool[/B]
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,001 kB of archives.
**[COLOR="#FF0000"]After this operation, 7,561 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install indicator-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following NEW packages will be installed:
  indicator-applet[/B]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.0 kB of archives.
**[COLOR="#FF0000"]After this operation, 1,197 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install shiki-colors-metacity-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following NEW packages will be installed:
  shiki-colors-metacity-theme[/B]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.0 kB of archives.
**[COLOR="#FF0000"]After this operation, 266 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hddtemp libsensors-applet-plugin0
Suggested packages:
  ksensors
[B]The following NEW packages will be installed:
  hddtemp libsensors-applet-plugin0 sensors-applet[/B]
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 159 kB of archives.
**[COLOR="#FF0000"]After this operation, 898 kB of additional disk space will be used.[/COLOR]**

```

I'll probably want to install more but lets see what happens.

Edit #4: Moving the window management buttons to the right has not changed since my OP:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

Edit #5: Applying the Shiki-Colors-Metacity theme is the same as Saucy:

```
gsettings set org.gnome.desktop.wm.preferences theme Shiki-Colors-Metacity
```

Edit #6: Disabling the overlay-scrollbars seems to still work the same:

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

But I need to rinse-n-repeat because I think an additional option has been added?

Edit #7: I disabled the webapps:

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

Edit #8: I used 'gnome-tweak-tool' to set the desktop to display mounted volumes:

[ATTACH=CONFIG]251605[/ATTACH]

And to set the key sequence for killing X:

[ATTACH=CONFIG]251606[/ATTACH]

It can also be used for changing themes:

[ATTACH=CONFIG]251607[/ATTACH]

But I had to use the CLI to restore the missing menu icons:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

---

### Post by muktupavels on 2014-03-29
I did not understand. :(

Where are you getting Sundry and Utilities?

---

### Post by kansasnoob on 2014-03-29
> **albertsmuktupavels said:**
> I did not understand. :(

Where are you getting Sundry and Utilities?

Main Menu appears in two places:

[ATTACH=CONFIG]251569[/ATTACH]

[ATTACH=CONFIG]251570[/ATTACH]

And both display the same menu:

[ATTACH=CONFIG]251571[/ATTACH]

And edits to the menu(s) do not work :(

---

### Post by muktupavels on 2014-03-29
This is because menu editor by default uses default applications.menu file.

Workaround to this is to open menu editor from terminal:
```
alacarte gnome-flashback-applications.menu
```

That way you will see correct menu, but there is probably other bug too. I was able to hide/show whole group (for example Accessories), but I was not able to hide applications.

---

### Post by kansasnoob on 2014-03-29
> **albertsmuktupavels said:**
> This is because menu editor by default uses default applications.menu file.

Workaround to this is to open menu editor from terminal:
```
alacarte gnome-flashback-applications.menu
```

That way you will see correct menu, but there is probably other bug too. I was able to hide/show whole group (for example Accessories), but I was not able to hide applications.

Let me know if I should file a bug report.

It's not a high priority :D

---

### Post by cedric5 on 2014-04-05
ok, now I have tried to upgrade from 12.04 to 14.04, and using flashback with metacity:

1) the indicator-applet crashs constantly (paste.ubuntu.com/7206916) - while I do not rely on them, it would be nice if these worked. I have also xfce installed, and the indicators work flawlessly there with the xfce-indicator panel plugin... I will provide more info if needed

2) the system menu as I knew it is gone (I have used classic-panel in 12.04, which was a fork of fallback, which had restored the system menu) - Is the the settings.menu file is not used any more? An option (dconf key or so) to get that back would be great.
I do not understand how this new system tools menu works, it is hardcoded? I wanted to get some launchers into it, but I just could place them into the Administration or settings submenus...

3) the tooltips are not word-warped any more, meaning that if you write more text then usual in a .desktops Comment= tag, it spreads text over the whole screen, instead of being warped into a nice formfactor. I also experienced that when I try to alter a value in dconf editor, if tha value has a dropdown menu, it also spreads to the whole width of the screen

4) the size of the menu is not any more controllable? [https://bugs.launchpad.net/ubuntu/+bug/1285683](https://bugs.launchpad.net/ubuntu/+bug/1285683)
gtk-icon-sizes, panel-menu-bar  panel-menu  set to 16,16 does not work any more...:( I really hate these gnome devs](*,)

5) custom keybindings are not possible? the metacity ones do not work anymore, the mutter ones neither...

---

### Post by pfeiffep on 2014-04-05
Installed Trusty from a daily bulid (4.04.14), then immediately installed gnome-session-flashback.:KS
My preference is Metacity. System is pretty responsive for such an old laptop originally purchased with Windows XP.
System details included in my signature.

---

### Post by kansasnoob on 2014-04-05
> **cedric5 said:**
> ok, now I have tried to upgrade from 12.04 to 14.04, and using flashback with metacity:

1) the indicator-applet crashs constantly (paste.ubuntu.com/7206916) - while I do not rely on them, it would be nice if these worked. I have also xfce installed, and the indicators work flawlessly there with the xfce-indicator panel plugin... I will provide more info if needed

2) the system menu as I knew it is gone (I have used classic-panel in 12.04, which was a fork of fallback, which had restored the system menu) - Is the the settings.menu file is not used any more? An option (dconf key or so) to get that back would be great.
I do not understand how this new system tools menu works, it is hardcoded? I wanted to get some launchers into it, but I just could place them into the Administration or settings submenus...

3) the tooltips are not word-warped any more, meaning that if you write more text then usual in a .desktops Comment= tag, it spreads text over the whole screen, instead of being warped into a nice formfactor. I also experienced that when I try to alter a value in dconf editor, if tha value has a dropdown menu, it also spreads to the whole width of the screen

4) the size of the menu is not any more controllable? [https://bugs.launchpad.net/ubuntu/+bug/1285683](https://bugs.launchpad.net/ubuntu/+bug/1285683)
gtk-icon-sizes, panel-menu-bar  panel-menu  set to 16,16 does not work any more...:( **[COLOR="#FF0000"]I really hate these gnome devs[/COLOR]**](*,)

5) custom keybindings are not possible? the metacity ones do not work anymore, the mutter ones neither...

I refuse to respond to posts that include comments like, "I really hate these gnome devs" :mad:

The devs are people just like you and I.

If you'd care to rephrase and ask questions instead of spewing hate some of us may be able to help.

---

### Post by kansasnoob on 2014-04-05
> **pfeiffep said:**
> Installed Trusty from a daily bulid (4.04.14), then immediately installed gnome-session-flashback.:KS
My preference is Metacity. System is pretty responsive for such an old laptop originally purchased with Windows XP.
System details included in my signature.

+1!

The Edubuntu flashback + metacity session is fairly solid.

I'm not totally happy with the menu changes but it's good enough :)

---

### Post by pfeiffep on 2014-04-05
> **kansasnoob said:**
> +1!

The Edubuntu flashback + metacity session is fairly solid.

I'm not totally happy with the menu changes but it's good enough :)

Thanks to you I was able to execute a simple command to move my window control to the right.....Keep up the good work!

---

### Post by Daniel_Pomietlasz on 2014-04-05
It appears that the WINE menu no longer shows up as a seperate menu entry in the Applications menu under Gnome Flashback in 14.04. 

All the installed WINE applications are showing up under the "Other" Menu Item.

Is this a new behaviour in this version or is something not configured correctly?

The ony thing I found that worked was to manually edit the  gnome-flashback-applications.menu to include a WINE entry but that did  not pickup any of the installed applications even when they were reinstalled.

It seems that all local menu configurations are not used any longer correct?

Any help on what to look at would be appreciated.

---

### Post by cedric5 on 2014-04-06
thats not hate I feel, it's being in despair, hence the ](*,).  Sorry if I acted too harsh. At least I know how to patch gtk, so I can  fix this for me, but the extra work is getting more and more,  specifically in things where they remove functionality without  considering that people use the software for many different purposes...

> It appears that the WINE menu no longer shows up
try the MainMenu applet, and see if wine gets shown there

---

### Post by Daniel_Pomietlasz on 2014-04-06
When I look at the main menu editor it shows the WINE entry including all the applicable programs as available and checked as active. But the WINE menu item is not showing in the applications menu. 
[IMG]http://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAABCgAAALhCAYAAACdX5W6AAAABHNCSVQICAgIfAhkiAAAIABJREFUeF7snQdgVMXWx/9b0nuFkIQkBAgklNB770VBEKSIgoWmgE8F5QNsoIgiTYoCAoqgKKAgCEgvUqX3TgKBdEgv274zd3dTN70Y4pn3rps7d bMmd 97M6ce aM7OyZ07qUlBQkJSUhMTERCXSs3X0TnJgAE2ACTIAJMAEmwASYABNgAkyACTABJlAWBGrZxsDc3BwWlhawsrKCjbUNlCpVOtLS0pCamoJvd96GpVsAJkz6X1m0zzKZABNgAkyACTABJsAEmAATYAJMgAkwASaAVb8dQWrUdfil3YZapYJWq4Xs6JHDOuE5MW/zRYwf/aqE6VFsMuNiAkyACTABJsAEmAATYAJMgAkwASbABMqYQExcMtQabbFaUSrkcHGwNlm3ost1tbeU9F6xajV8cBO2trbkQaFWZxgnwqKTTHaMM5kAE2ACTIAJMAEmwASYABNgAkyACTCB0iUgjAix8Um4cmpvsQQHNutCnge6XEaKp0Fu5JMUqc tOz Do/v gG/ybSjVGrW0rEMknU5XLChciQkwASbABJgAE2ACTIAJMAEmwASYABMoPIHY BREP0nEtdP70KXXAKligLdToQVcv/8Ye3dsRp0mnaU6zvZW0mdOuUWRKeqXt1zRprBJpD28Alm3EdN1Q0eOQ3KaSuoMJybABJgAE2ACTIAJMAEmwASYABNgAkygbAlExCbi1KE/0b5bP1R1ti1WYxduPZIMHM3a90YVg4ynTa7o KPoBJzcvQFKIwV2nijW88CVmAATYAJMgAmUjIAmETfPXkGIzh1NG/vCUVEycVybCTABJsAEmAATeDoIyGR6PYVxQkPLNIqT3J3tcI0qClnGOf3TJjdrv7MYKIoHpDgQuQ4TYAJMgAkwgaeVgCr6Kg5diQcc/NCmgTssDYMLqT 6dDy8eA5XngCu9Zog2LkAa4MwTlwKR8fRA9FPfgvTV96Drp5PkY0UparT03pjWG8mwASYABNgAk8ZAbnRkkB6izgSJUlCljFkgym52/f XSjxfbq0yVauILmisJBtb2MJfz8fVKviKtV/8CgSV27cgV81Z3Rr0wD3IlPzlJv1QoaBQssuFNmA8QkTYAJMgAkwgZwEVNHXcE7ZBL/NcYf2zimMWR OWg2r6I0UZJwIO38dXkOex yawOnVW7Akpj4a5mek0KqQorZANWc5FHI7OGrvIl6jg1aes W8z0tdp7yb4itMgAkwASbABJhAKRKQZTVQlHA LmQZ5/R5yf363Wfz1X7C3K0ZMowFC5K7Y99R/N ozrAwk2PxL8ckI4nYLvTW3RBMHdkBTnbW PqXvxEQUDdb21nlZr3ASzzyvUV8kQkwASbABJiAkYAO6Slq2PtaQjhNKGrUw0CXXfg9zhV1HRTQxD1AmHNdvF9Tb11wcjKDKlJNP/QyJIZcx8WHCUjTUEWZGezcPBHg7w47hSPq1krA4i93Yr08FZoa9VFLkYaHN24jlLb8TlbptxxTWNrDw8cX/m6WyG67KK5OCsi0aYgODcHtR0 QTHoprRzh6ecLX2dzyHVpeHSrAB00cbh44jqizT3RvLEnbEgxNXmXHL6WANsaDdG0moXEiRMTYAJMgAkwASZgmoApTwfTJQvO1Xs66MuVRG5OT46C5FpbmsHKXAlHO0u8ObiVZKRISk3HuyPaw93BBpEUBPR RDxq1cruIZJVbtbesQdFwfeaSzABJsAEmAATIAJapKVoYO9iYaBhhe49PbHxx2ik1HdE7L0ktBjqD2fDVXsXc2hD0hAXEoLkwGZYOtoNruZ0UZOCm eu4Ju/7kNT2wmRN9PwwqSeeMYiBNM v4Zb9grUad8Ck o4wsNWKU3yU2MjsWfXaWy Xx2BXlZZjBTF0UkFjUaDB5fvwa11Y8x93QOetA15ctQjbN9 BjvCvOCaEoXq engkY6r5 Px icvoGX8ZUxY8gAungm4adEMW a44e7WbfjwoT8aerCRgv/pMAEmwASYABPIi0AWB4pcngt51ckrX8jK9KDILJVzpYTwkjCVjN4VOcsXJLe2fw18 eMhTH6xPZzJIDHxhdaSHi721pJxYu6Ph1Hb3zdX/7LKzaoPx6AwdXc4jwkwASbABJhALgJaqNN0sHEwoyuJOHJNibZ1AtHXYTd2RScj3q4W3vGX4/HVB1DX9YKdgzl05DIhczSHLIm2ELsYh8cpMrjU8EHrJk3wXtJfeOtMChyytaNFcoICNQJcUc02BZfOheKhzgbBwVXQd2hbJM3fjyNJgfC1NvomFEendMTeCoNtl66Y1tIa0Tfv4o8oBQKbVMegkW2hmn8Af8bZoGN OiR7IedK2VznNDjh7ctzPUScwQSYABNgAkwgg0BJPB1yYixMrAhjnS7tWmSrvvfwiYxz0x4U l95U/q6ODtKv/fCSPEeeU042JK3J1kfYhKSJeOEb3VvVHV3zRVjI6u WZXJMFCkq4TfKScmwASYABNgAkzANAEVktUKeFiLRRap GdPKNwDGqNnZ1f8tiEadQa1Q1VtFJbuD0c3MlC42VtAQVt4y52rQHvlPOb9nQatTA65VThmTGuDRjVdYXMwDqpsM3tat2lsPDkC6zZfQJhCjV9Du2BFPye0DlBi6 0UeGR4JhRDp9QnCFV6YHoLa4pgdRaf/HQPMdSo5U1g4cvV0bWRJbbsMyiRlw630iDMNJmJDCUUOyNr0mm0EGMLXuaRDQufMAEmwASYABPIIJA1VoRYFlGSJGQZ5/QFyc2vrZzXCiM3MSWVxgEaqOiQDA/04y nEYC1pTnlaaUlHzlTVrlZr/ESj5yk JwJMAEmwASYgCkCOjXSdWZwpOUQ5EqBJ1Eh2HCxPmY0CEKnY3fRur4ZEs5cxpFIJdqIubqFJax0CXgcGg1lYGPM61KdPB yCDYzg7lOS6aOHCnrPF9hg6qeWjyISEAynGDraEYbhaih0VGcCFGtODqRESXRpSaqC8uBVyMs qBRNgWUtIRFTnIzkkkdtLk8KHIHHydjC71RYQNFzhvM50yACTABJsAE9ATMFJmRpTQUWFKkU6fPFwpPsyYNpXIKuV6GXC6TjAEimZKbVaixLVMNGa8VVm50TCwiwsPx7ovt4EpLPKLjk2AmV8CRlnhMoJgUX1NMCiHTxdkpT32z6sFLPEzdFc5jAkyACTABJpCTgJbeDOgoCJSII5GWRoYFOe7tv4WIBnUxcoQj7T egPUHH5PxwAkJaVTGwgJW2vsItwzC0meqwz78NpZvokCaMhcMG1oPAZL8nAsjcjQqlkkIUwS9kZDia9LgQ2ZYOiHVLI5OVD/BsOhVdec85ux7jKzvNVQqGSyz7o6ahw70foQMEKQDDYwUNPDIZbLgJR45biafMgEmwASYABPITiDbbhtZLP2F2m3DUN5o4xCyjEsr85JrbD0/I4hxiUdh5T548FDarcPd0RYRFHPiK1rWoVQoKCZFOzhLRorWmLVqH5wcHaXmTcnNSoUNFPyvhAkwASbABJhAYQjo9AYKWrlBBgo1VHJrOMTdxqaQOhjvI4Pm9hXsTXKEtUyDJOGAQB4Ullo1zN0cIX6Sbx65jJ135FDS241wFfQGCprg5zRR5DzPWUIMPqRD6FwcnYTTZWwUHqE6/Ks4QPvwJq7LrGFOeqtUCrhWd4MCcTmIZNdKp5PTEo90RKdQMXtneCuu4Ewk/e2XWU1oyDEocmDkUybABJgAE2ACWQjQe4eMlDP2Q0GgcpYXsoy/u/nJLcj4UVS5KjWNe1K1UkBMYZxwc6sCBRkovqS/hZHC3tYCtaq7mIhBkalv1r7yNqMF3Xm zgSYABNgAkxAECAvATWUsBMeFEkqqGiK7uAhx ldV3CkvR3uHYiFmYcbtGGxFKuCytiYw5JGCGkRsYiBC2r1aonRThGIgj1qiWUiCYXDSraIXEnkSdnF0UmmhL0uDOvPBGFGY1988K4DTl1/gniZBTxdVdi09jKuQ3QyM XSgbZKdbRJwd XU/Bs6yp4a1wbHL6bArMqevdNqabQ0YTu2QTzCRNgAkyACTCB/zCBbJ4OWX4089ppIyuq3LttCA8KfYnylNuwQT0yTByAmVKBqh5V4eik95QQLyo  W6fZJxoHFQLF0Oyv/zQe3zkvvnsQZGbCecwASbABJgAE8hNgJZTaBW017dY6qkmDwqKrmBrQ1t0UiDJlZvuw6qqNzysVOSZoEGKMFAoyUBBBg3H1Bv4/A8LjO3khZ5d3CW5quQk3AxJgs7KDLKU7IGjcs7pc0/ys3hQFEsnDay8PPFg 1589jgYQ1t4oFkjYVhQIybkLjT01iNnyq0DBb6q5omI/YewxKwphjauio6uVEurQgytQz0faw4bC lVTi4PkZyy ZwJMAEmwASYwH VQNZdMYyxH rVCywUjpxxJPLaxaOs5Qpls psbM/G1hYBdfQLWs/dfZyrT3nt4iHrNmK6bujIcbgXnrtSLimcwQSYABNgAkzgv0xA/QQ3Lz9AkmVV1K3tCjEHz5V0aQi/fhPhaTbwq cHB4UGyVEPcT8yngwXevODTGEOK4cq8PNygJkuBWHXbiNK64Cagd6wpXCYD67eQbTOkc69YEsGEW1SGK7cot9plxoI9LLWB8g0NlwsnaiyNh1xkeEIj0kw6EXLNqydUN3PA3byQuqgTUVMWBjCH6fodyOhXUrMLKzhVM0L1ewy3oHkQsQZTIAJMAEmwASYAOBsZ42d2zaifbd iE/KFTa7UIhSacewa6f3oWff5xFLW3uK9LTJFTpraDewk7s3IMNAcfdRbKEAcCEmwASYABNgAkyACTABJsAEmAATYAJMoGQEbKwsaWmEHLu3b4JXnVaSMEcH20ILfRKXiAfXjqFbn4FQqWk7T9ruU6SccosiU9Qvb7miTbGJiTBQcAyKQt9 LsgEmAATYAJMgAkwASbABJgAE2ACTKB0CCQmp8La0hxdeg3A3h2bJaEPiiha1E2jLciTUzOXjOaUW1SZQoXylJu1yxyDoogPABdnAkyACTABJsAEmAATYAJMgAkwASZQGgSSUtLg7GCDvv1fKJa4NJWaPCfE/ubZ09MmlzZTlzrABoqcd5LPmQATYAJMgAkwASbABJgAE2ACTIAJlBOBGNqisyzS0yTXuPOIso5dNH7fdbgseLBMJsAEmAATYAJMgAkwASbABJgAE2ACTIAJFEhA2CYkD4otc15AbEx0gRW4ABNgAkyACTABJsAEmAATYAJMgAkwASbABEqTQNiD 1ix/ED2ncpKswGWxQSYABNgAkyACTABJsAEmAATYAJMgAkwgcISoN3VOTEBJsAEmAATYAJMgAkwASbABJgAE2ACTODfJcAGin XP7fOBJgAE2ACTIAJMAEmwASYABNgAkyACRABNlDwY8AEmAATYAJMgAkwASbABJgAE2ACTIAJ/OsE2EDxr98CVoAJMAEmwASYABNgAkyACTABJsAEmAATYAMFPwNMgAkwASbABJgAE2ACTIAJMAEmwASYwL9OgA0U//otYAWYABNgAkyACTABJsAEmAATYAJMgAkwATZQ8DPABJgAE2ACTIAJMAEmwASYABNgAkyACfzrBNhA8a/fAlaACTABJsAEmAATYAJMgAkwASbABJgAE1AWF0FE CNcPH8OaWlpxRXB9ZgAE2AC RKwsrJCvYbBcHevkqscfwflQsIZTIAJMAEmwASYABMoMwL5jctMNarRaGi eB53791FUmKiqSKcV8kI2Njaws/XDw2CgyGXF88XotgGissXL2LwsBGVDCl3hwkwgYpGYMO6H9CtZ 9calW276A7t2 ihn tXP3kDCbABJgAE2ACTIAJVBQCeY3LTOl3gYwT8fFxGDBwEBwcHEwV4bxKRuBJXBwO7d L83TvGzVqVKzeFdtAkZKSXKwGuRITYAJMoCgE0tPTTRY3fgelpaaavP60ZT56GCYZKCpLf542/qwvE2ACTIAJMAEmUDCBvMZlpmreuXMbg14YAjs7e hMFeC8SkdAGKI6du6Kjb/8XP4GivKgeXFnW6hSY6SmzKxcUb/H4Yxm4xPisWnTBjqXQaNRw8vLB61atmbrXHncGG6DCVQgArpK9pNX2fpTgR4VVoUJMAEmwASYABMoRwIpycmScYLTf4uAnb09kuneFzcV24OiuA0WpZ4wTjTosQrQqXDhr7HZqgqLnEc1T9QLrA tTof7D0Kx7qcf8MrI12BpaVWUZrgsE2ACTzOBymaSr2z9eZqfLdadCTABJsAEmAATYAJMoFwJVDgDRWzYPti7NobSwlEPQpuM5Mc3IJPJsoG5fecW6terDysrSyiVSljVCsA//5wE2So4MQEm8B8iUNk8Dipbf/5DjyJ3lQkwASbABJgAEyhlAqlpqbh56zoehYdBrdaQdBopGSZ84tPMzAw2NrZwsHOEo5MTPD28DMEZjZPC7HPIUlaPxZUBgQpjoHgSfhQ3T7wLZ89OCLv2Dep3 UXqrgxpkCmy91w8jPdDQ9Clczeo0tMQExuNx48fw8nJmQwW7D1RBs8Ji2QCFZdAZbNKVrb VNwnhzVjAkyACTABJsAEypxAyd4e37x5VVom0qBrH5O7Qoil/iq1Guk0J3wU/hDHj65FHX9z2FvdR1r8PzC3awUz  cAhU Z95QbKB0CFcZAcfXIODTq/j0UiniEXlHh8aMjhh6qYGXrTJaKzG1KIiIj4OzsgsTEBIi1TSqNipZ43EetmhU8Ar7qAbbO/Ah7a07F3Jf8YVY695ClMIH/NIESzec1sTjxw7c47PoiJj3jXSH TZaoP//pJ4E7zwSYABNgAkyACVQ4AiWzT B 2H307dUfwpNCq9XQodUfOvFJHhUkX2xnaWFuCf9qkfB3e4z0pFNIDN8LK/cPkfDwMzggDgrrHoB5ywqHhxXKTaDCGCiq1R6JhNgrsDS7DBfPlrh1aiqESYJCYCI57j5kWR7uu3fvwK9GDXLzUUmWMlr/gcjISLRo1ip3DytSjiYGp7fvwNF k6AVeqWcwYwuA7Gr7Trs/aI17EqiqzYR904exR3HluhYx15iJ6XSbKMk nFdJlBGBEq0JEITiSNrV O3Tn3wxjNeqAhfiEXqjzYJIadPIMShGdrWtsv8d19GrFksE2ACTIAJMAEmwATKk0B6ukpa6i/mfcKLXkuGCfGpI0OFdE6fKrqmSTtHn3tha3YF2rTrsHJ7G9Zub5KqCiTHLoGd0obmjDTbMgsqT/W5rWIQyHRLKEbl0qxSvd4EhF5aTtatwZj91hHs2d8fP37XCtNeO4Elc2VYuzrT4iUCZLq7usPaygaenp5SHIqkpGRUrepRbJU04Rsx2NcTnn1WIURVbDFFq6iwhVfN2qjp6VDyN7cpFzB35Ch8sjeaTDpZUmm2UbTecWkmUD4EhPEyz0OLuLNr8f4LHdGwdgBq01G/dV 89sV RKkN9Yxa5ikjP/mleK0weqjDseE56sfQHXgirJwpl7Fo7DjMPhBDP9ilqAvLyueZYs55/3tjNsyGnwF BvgZqPTPgHG8UsjPkg4pNBp93Amj54SOBjw6o5HC8AJbDhXMVNuhiV DJ1H7oNZYwcp1oqShlctIqGhuF3HrM0TfHCJ5V5RUJ65f8DCpkI HyWIV4YWhpJhMroRv8Ayc3LMRvUf0R/u 7fBah4l4aXRv rs9Rnd6SyqnpjVGkVERcHB0oOCYCqSlp0teFNW9vXMF0jTZY5OZ6bi5dgH 1jlAcW4xll8Ygk bWJssWaqZ5rUx5oddGFOqQnMIK482ylJ/ls0ECiCQn8eBJupPvPPyLBzx6IuJn3VDgKMWMbfP4ZLWCdYKqqkx/LLRT5X fwU0Vg6X8 uPFBhK0sGob8XTvxwQcRNMgAkwASbABJjAf4SAiDEhGQSE14TRMJExatOPg2SIRfrjn Hgtw7mtp2ykZHJreAWdIkExCMl9nc8vvUy3Bte Y/Qezq7WWIPigMHDiAwMBC1atUq8BDlzp49mycpF68uuHziMnzq CDucRzSU9My/k5NTsWH3wXi TU2OGA9DWO2 mHUJk/835Gm2BexGFbp9/OUW9AFXfxxLPk DE0/XokZwdHYsGAfoqU1GIakfog/3huI9sE1JY8NT08/NOkzEd8ej8n0VihMmZyKpF/FnFaeaDzjHFKN11SROLjgNXQJ8pba8mnYF7NOJ9FVFW6vHI6m/qJ9Omq2xOCZu/Aoh7fHzc/awVfS0RMDt8cBJtsIx765o9Cprr5cYKdXMG9/BLVg7G8Ytkzuh7YNjf31QlDn17H01BP90hRtAi6snoAe9fU6Cl1GrQvJrJ zn3zOBMqSgAjakMeRdmc/zqY64blZn2DcgO7o3LknBr3 Pj4e0wDWxjqkW Rvb6JjvToICAhE874TsfI0PevG66pwHFw0Hn2aiet10KzPG1h8KAJq6XoCjr7VFAEdv8SVVIMeCX9jYqM66L/2ATRSGQ0iNw9BncCReeop6W9MefQlo49SuSx9prPbc3siiHQT r24i/7dCxlpD7B77uvo3ljkB6Fl/7ex5lycvl/0fbV9 lB0bxUs1RHX2w77CN9/Pxtjn2mDeiIvuBteX3wCj9V5882LO czM34G BngZ4CfAX4GKukzkDliKZe/NGqalBFKsbRDjM30hgrxaRgO0UU5EmgHSF kRK Sxl25E VpkpAc8zsZMJrkvsw5FYpAiT0oOnbsiKVLl2LSpElYuHAhxHnOdOzYMbz11lv45ptv0KhRo5yXM8616nTcuKpEx6QE3L5yF8npybR0I5H voek9ERc1N7DwN4vwtrCnh5QFU0Q0pCQFosdO8nd VwsnrTvDcdqdfOUb/qCBlG7l2AH mDlgBZo4NEdc19fgi33e JVHwMebRyuHDqORwFT8M28hrBJvoeDq fgk4EX8WTHn3ivAe0cUpgyphXIzNUl4cycARi2TIXeUxZhWhNnpEdEw8HbgsrI4daalnCsnICq9Bb44YElmDJ3PKY0Ponv 7hkrD33enU1VgwVwf5ksPGyzd2iLhH/fDoAI1YA/Wcsx0eE68qGWZj14kAkb9uF6Y1ofZY2HteO/IMI6u 3C4JhnXwbuxZ8jE9fMkOd40vQNmwpxk7fiWpvf4PfunpCG3kHsb7uJV mkltbzmECBRLIOrfPWdjMrQ48sA1HNh5AaGBPeFvm2GpKjB2okkWtZzHlteZw1z3AvqWf4csxn6DWnrlob5eMs1 OwOjvgT6TF2BqAHBt81x8 fpLSN6wGZMb2CCgWz0odpzExVgN6lYlr67Qo7iYDMQcuYnE4Z6wRzJuHrwJXe239T mOZXMcZ5ffyRlDSnDjkHn1UYswdcDPSmGhhw2nja0LjMBp2aPwJtbPTH6o /RxeMxDi ejtmvfQSf3V ho1U8rh87i8jab Hr0Q1h9eQsfvhoET47WwP935mKrwOsEbl3AT76 n/4qsUezGzCuyMVcNv4MhNgAkyACTABJmCSQJbBi8nr Wfql3hQGck4kfUNstGrlMZ2MgtYOrZFauxWxN//H yrL8oUqqPXwDQuir1LMQDTQ BUc70Qln jfPVfJVBiA4XQXhglhHFCGCEWLFiQzUhRWOOEkPPo kGolTQQ1skQ9SAGiekJmX nJcCK/BVqqLzgkuZOg35nJFJE1lhZOLbTBKR2vWa4989GBD87o2hAVaHYvOw4HAduQUt7BSzbjcFzLv2xcv11vDg1CMI0YEx2tTugW dgWFJG584NIevYF8u/OoQxa3rA0VCoMGXyUlAXux9zV95Fzcn7sGRSAMxzFLQP7IregfrMxkHOuPprF6w7HII0MlAYpw9WVWqibt0amcaC9OxCtDH7MHd1CPwn78f8sbWlNjq08kfyhS5YPPcAxv3YBy7GvgR0QNdOor8d0No7FHt7/Yo/rqWgpTYMjykebue27dGsoR2ZQoLz6hLnM4EyJ6BS5XjIs7ZYbRC  PAKJs16G912fo22/Qdh2LD aONjozfq0aJEEbvBoW5HdGtXj/69N0dD1zvYO2Qrtl NRwvfQ1i47j583/gNn4yoIf17aR7shcRLz O7hfvx8rJusA/sggB8id0XYtHfxRaPThxBOO2NrL20B9cTWiNYdgN7zyTBZ2AjWgOZj64GvfMto6UgUOI3VUtbapEslUot6W/p4o0aNXwMQT41SIvYi0W/RqHZx2vxRg83qa8BH4zHX70X4Zezj9Gmmb7fdjWaoVVT0e/6cL/7Bw6t8EWvAd3QmuyUCJTjyNaxOPn3PSQ34F2HyvxB5gaYABNgAkyACTCBXAQ0YqcOSkZzhOFE qDYmZKtQUfzQi3coDSzkl5iQxMtdlqgC7Q8RBgo6CWwVh0HK4cW9M7XXaqbLWkeYX2/VpiaNga/bHwPLRyyLDJIPICRwSMRPv0Ito0s24Dq8btHoNFrF9Fn9X4s6OyU8QJar2sarnzVG70WKTHt4HaM9i2VaXxOEhXivMRLPIy9EEYKYZwQRgqx7EOkohgnRPnQM78hjQKhfLvyW w8tB0PnoRg156/cOzcEUQlRtA2MTrc2nkah7euwq4/5 D4ziUI3b9daquKfyvcPbVB rsoKe3GT1hz3QcvDg SDA wboiRw3wR vP3OC9WVuSVrAPQs5UjUq cwP285hyFKZNFfiq9eb2qckOr9tVzGSdAi0DubZuFl7o2QR0fT3jX7Y9vQ2gFR0p6kWyAaaHHcF3tjjbtvTPbMPdBh9YutBrkOO6nme6wedUgVCX3qfB4NayDx2FCqwSsHtAafSd8hc3nonl5h2lsnFsOBDJd/bK6/Rn pql3jQGfYcvff2L1VDImXPgW45/pghGLTuExzfSluqSj3htBf650q0U/cQmIpGc97f4/uKV2RfOWHjAzuhWaeaFVMyek3zxN/17IrdCtBXr6p PCnptIpm1Lz 59iNqvj0Nw0kmmgxGNAAAgAElEQVQcCk1DetgxHI2uik4dPbO4JebW1Ygq3/4Y9BVljeWkekbdDJ9pD87iLsXrOTWtKxo2aIj6dAT3/gI36HskMjJZWnqSvd9KOHqTmTU1GrGphujYSid42gPJj5P05XO0UaCeXD7f 838cv8bYCbMhJ8Bfgb4Gaj4z0CRh3bSgKP4R4YHhTTeMbQunCbIOmE8dDJ7aGR SFdZUlxDS7JLhCIpag2irw9HSsyvZLAIp3wrimWooIrkYW5KHyH6xrcY9eZPuCfmdlnLGNs2Va/U8tR4EhoF i 2fPwdron1/1lkax7 gZnf3KbMODx8QpHeS63dHH0tLbmGW1Wcj1I1vRiNFGK5x7Bhw7B58 YCl3VkKE2D2eiQc/h04dd4 OAhWb800I19RtrXVtfUF6OGt0EMvblXypR69x4qT37MEtGJsmFw8qpHD58aKXHhZB2rWkgWSTj//Qbc10bjy06 9A40a4rByhPT0Kyzg2SAM5VkCroiBWuhq3kUylbGlJCseWK7HBJkSlT61UUYMeZbKIZ/hmVfNkYV3S2sGT2efEfKJ8kUStqkR6t/e2tVF N/OY0eB9Zj eIlmNBnEZZP2oKNk4Nha0r58lGRW/mPEhCDmYKSzNIDjZ8dh8bPvIQXV7yCYUtnYFXX3/C/GsaahgGBOKWAvQr6l6iRokQbvqUNk219aZEv/hLfQfS3oiradquOeRt34kZkG y46Yau73eDw5EV2HD0AZ5R7kaIC3lo Job5OWvbb79Ee1J1TMHMJk6Ga JryXxXWKDzrNWYEJgVj8wOe0J7kTbNj82KJHZb4W5WBimpsjX4jtN2K4VsKBfCC0ZcqQ1n/mrzVeZABNgAkyACTABJlDqBDT0wkUkMUPSyWimJNwmss29hKGCNlKQNYGZQz/Eh85B3IMVsLCuAitbF8SHLUbkjWjIaGdDj B5 evn0QpeJ6bj1a/qYMt7TfKe16Q/wM550/D52oO4m6SAc2BvvPHpLLzSSIGjb7bE8DPD8ef qQgSQ7DEwxjXfATuvXcEf7wsPDC0iNj4PFq8b4nFJ9ehr7Nx8qTG41Aan1l6wvneKny5 2V811fvBUuvi3D 269wlF4q26VH4mFcljgbeeriADnFHNs6fQLm7b6CuzEpEkXHgJ4Y9 lsjG7qCHnScUxsOQSXx /HrnF kieu t5y9Oq4GEEbjmFBC FSW/6pVA0UQn3jcg9hpFizZk2 MSeydjfm/nl4BnaEvWs1KOVkthIBTmiQLX0KYwUZArx0BEk6z8w3lpEpzVHFtwHio 4U2kChiz JVVujUWviWizo5ZrpRqONxB8TXsbKlQcR3fFZeptqIqnu4 ipx1DWbAJP8fCZ2po0ZxmDd4J 8pBbpoV3U/gr1uLvQ6FIb5x9iUfS7eO4g4ZY8O5wdHKnyYPaFrUcssiQW8CWXECSHyfrA1nmFi/lWFRvidrKH3D08H1qQ7/EA7Qe6 DRGJjVaQEp3IWpvuSUJ7eFf fRmNNpCJ6b3gkDV63AhTeW6F3Dc5blcyZQpgSKMHWWWaNm2 aounQ9rkfS90wNY12DIULSMzPP3Ksx/JW/4tSJMKQ30C/xAAXkPfbPY5jVbARPc1FWierdeqH6N5uw4beHuGDXFm94e8Cquxfm/rEZG2W34dp1GmpZFFbP/Mrl0FduBhv6N5vyhLwiSG/jF7q5ZwP4yDfiOhnaPfv6ZVuqJnUxPa9 Gznk5JGfTmV6c1k4E2ACTIAJMAEm8BQTyHfpaiH6ZfSgECMRyWNCvMqVG17oSueGJHOEznoonGrXhoLiFhpfxti4e2DvoTto1e5/NFZyhMbUcluNfgmt3PdFfP2BO4aPew3vBW3DVz3doKDltNKoiMqoqa6OAqSf/HgwxvzuiTEz16I7xfk6uOj/MPPlqai bx4adqXYZNuO4mxkCmqL2GS3D E8xSaLPnAZT4a50yL5RFzZe51ik72DIGuVtAWqPqUg9mEcZLUn46PAbzBp7mpc7vgW6tA4TxO FZ//9Bjtpn8K y8m42EkbSahohdL eoyH52sYnDlyGmE1/4fvn6tPsUVvIs9S2Zj9ity1CRdO5ip9H3TimXDeq98tVqMKMVqYqFbXssEjDqXzWepGyiEmsJIcfLkSVhYZH1zl38Hwi79RTtW9IKZuRVsnL3pKcgyUBZ/5zwX6LLkKcztyMDRAQkUsLFKzdb5NyZd1SH28CrsTgjE 0PaI9gYEFO6poLt0AAsnb0KeyL6YKghKEPEjgVYUGsgmnnpcH3j55h7hx7gzzsgw/BFNfMto7BHVTIqPDr4O/bfrIEePtnVlLt1x9tDPTD4y EYq5mCIc08oIx/iAT/PlS2MbywHN/MXw XAfXgqgjDvcQs9S280byWEmt/ hIrGr2CIDxEVJWeeL5BjjZcumDyKB/0 2Ik3rachsEUJPPyz7Mw764vxi7qlK0v2WtmnqlCt P7g0DdIE/Y0E4Bh6/SrgH2VWBXJk9TXlpwPhPQE9B7M5imkXLpW3y0IR0NWtSDj7MlNE9u4cAPGxAuD8TLfuQCaJx3G75OpG8d8bdBnIwCLo1/wRMvL3kLH1hMQr9a9G//94X4JtQbL89qQz8y vJK7x541u9bLP4mGlVHvAFfc/LC6NAbngu xg 0OOqlj2pB2DKMck1rW3B/9L8imeV0Zp5oVEOJX39fhh/rD0GALgIxbp3QtwFtzdzfHWNXT8Tb8vF4vmk1mCc9xJ3H/nh2QH3Ym q3QalsX7ciLwub/PTma0yACTABJsAEmAATyEkgX8/QnIVNnKtp b9ICvKqF0nyoDAaKsSfRhOF9LcTvajtSu yn9DkPVYqb2Hji/PXv0WLthR/LK9BI Xrh0ZyuHb EMvGDMLgKVPQKmg5BjtmDppEXzTR 7FwQyRafPYL3jZ4OATNCseuLvPwC8UHaNewJ piNnZfTMCgKraIPKWPTaa5tBe3kjuisewO9lFsMt/BFJxdbvTKJUUpVsbj6FQoHGkpMXnJN9w0H8uOjcT8Dpa4/uMSnHQego09/PDnUh2uhMVBpXOBIl9dEtGxhV53u5pt0LFdfQpn0AbNPe9j/4DfsP1GCtpTbEOphDTW0zPIuF/iPC9eEtmyS2U2pSyKcUJ079bRH3B   fkfkNu0GShKmqSyRVQmJkhoMPrhauqjcKB1YeQGjgd3T1zYjCDd6/BCPh0Jtb8 QCDRuhFKsxjsHfeG/g6SgNLr1Z4dcmX L829pmWOyqWbxmz6hj4f69i /9W44NVfdHxY vsutL6qTaztmCNC0XbX/UORs0jTxFrX/SZ3QZ9Bk7CipkRmLJwGkb8oHd1snTyoW1HHcgRmxIFfOnz RwcHPMxZo/eA5h5oMPUJuifw0Ah1l01nbYJP9hMxcz5o/EbxSG1r02GkbWfY2Jjm2x9yQtketQFbJu/HB9GCKuaEq71euODZZP0bkx5VeJ8JlBGBPL78lTLnGEX/QtWzVyNGMkIbI1qDbph0rK3MMiTFnKQJ4H qztzqUPGd7H0RW2DBpNWYJH155i/fDJ2kFHQrkYHjPl6Kl6rJwL6GuorvdB7SBAWz36MXn38yBhBUj07o1/NrzFfMxDP RdueYfQML/ ZLQnlBZtU/86T/0/9H1vPha9e5j 3buj1Zv10YO8PVpMWYUFzl9iycZP8dZ39OOucEStHu iS/96sDPqTT3M/EEy3iDDD5KJMmV0C1ksE2ACTIAJMAEmUEkJ5DuuKUSfJQ8KYXyguZ7wlsgae0JUlwwWwkyR4UpBp3JXGuEY3jDLbWj5qvDGz2fCLcZtBjuEjsaKDd5YiMnHn8NH//sBjZfVMEzi9fXT7p/GHVp2EjWlLWjDw2zJPIICGLZshd610vDtX9eR3MkPp/8KQ8C4CbBcvRkHKDZZPeXfOBLlgS6dvaHMGGuRGE0ixVykkaqXNcyr9cHEXgsxetFW2oXOC0t/ikDjyS8j0CYVR2n4mRiVIG13rypAF2PMMdE543jPzD0AVciLIyKOvCdEv6VkYjyYH6/s3S71s5wz81JvoLACe03eg5/fD0S1DlORGkoDbeNTUigBMihtq DJ5V9QveEzhaohJvQDN4ZgYB6lzfzGYl/YWP3V9KvSp2uXmfhjpn4XjzyqFVBGAfeun2DbxU8yqr93LAzvZRVGb0S7TVlNR 4WGrzyNXbSkVey8B ChXvoyFEgdxv0j2LyGjrykGReFznryFyew5aw5wwVpuL3M1PzqMzZTKB8CeT3w2dTdyD bwkdplQSX7xmNfHG1n/whrhu/JFw7IHVp3tINSTZCne0HTuPjhxCsv6o0AKxqs9/jzPP68vo63ljxIZ/oLdvii9 U0rkzsuvP5C5Y8CP/2CAXjtJprnPs/jkZzqyipL6VhXtx31FR8426Jo8d79t2i/D6dNZ9DerQe6L/2CMyMrW15zy JwJMAEmwASYABNgAqYJ5DuuMV0lW66GlhwILwm58JrI65AsGKKawUphHLcYBl8ailNYkIFCP0wzTNTN/fHSl1Ox/9lP8c4a2rZU0shwTZJti25z1uCtIGmLBUOSwbqKM71s16J9Dx988fN2XItoh 3X3dB9Rk84HvwG646Eor9yB0JcO6OnX46XV pExNBSEEsHsQLBDs1Hv4Tqz36Dz75wxCFlb6zsWYVGmxGwt9IhJVYfwFxWkC4GLxJpHGdkQrHW5FJcQdEPGURIRXWa2BVOnBvGvqKvhv5m6WC5/VlhDBRmVg4UewJo2yQAyc4hRCfrPrcF8JBRIE0zR y5KoeTN295WQAtvswEKhcBw49PpelUZetPpbkx3BEmwASYABNgAkygqARKbKAwLPEwGifkNO TiRgUkrGC/jYaLQxeFJKhwTghN4ypNGrDDmV5jbGM cZ6JELhPQifT9 DPtPnQoSXrGO4Zl6tIXzlP PqTXKWfbaGfhfILFBEoHGfHn3hs/gXrPs1DOfsO2CCdzVY9/LC579txM/yW3Dt/rEUmyybOppkUChBWNqa0/IUiivmOwBjmy/DlC3R8J84H03E5iM6c9iK2GOxybTEg8wkBeli0lPY6CpC7cvtUI3WK  6ch/J2hqwJ2OFZKTIwrCo97s0ylcIA4WWgmEmJNBaAwEkXf9ZpM7RDdKmxUuWoejoaLi4uECprBBdK1I3uDATYAJFJ1DSH76it1i2NSpbf8qWFktnAkyACTABJsAEKjKBko5rjDEoRB/18SeMvdVHnzAs8MhiqBATbLGbWWbSasUSD6N3gAla4pohO8PTgPwMPPp9hKl/PIMPTtBOBwYDhZx2Zhs/0B2vrByHifIJGNzcExZJYbj9uCaee74h7OmFu7J6LzxXYwkWLImCx8iJqGFOoQg6PQPPufOxGh4YNasWLIS8rKqoU/CELCHmZIGQPCPktCvcu2/j bVx6DHYx7AcRAEbawU0cY RSrus2RWkS0an9H2XjA8ZjVIbFH6gW09vLF3xMWYsfwfP1XOENuQypL3eDP01QavMsyrELF5F4UsfPoqg9UIKWlNzG1ZONcmBQuzvSg8TPVD6XTzoU3q4xKdw0yEPC mcypGBIykugiKzKnDp0iU0bdoUDg5Zt7goIUcTSx5ySSxMmVyVOIMJMIGSEsjx9V5Scf96/crWn38dKCvABJgAE2ACTIAJ/GsESmqg0EoeFPpZdXZZWjJDkAcFXZWJ aEUOFOf9BNxYXXQ1xNxLPJdspBhLBBeDVlGYvJq6P/R29jcZzZ5URiv2aHl//2IJS6fU7DMj/HmchHnywm1e7 HbgMawE4oofRG3 H1sWBmLPo 66 PTebVFQNqz8eX6sEYWNNEbDJNCuLJDiI8KCTjAImxrDsCn3xm6JPUFzkZMGhZyaNYJJGBwlVZgC4m mVkKPWTPDJqj12CT5/MwILFk7FLhDlU2qNaYCvUc6ZYbQZ Bqzl9lEhDBRyispqYWlFriz9sPuXr8TzJSXJCCE xXaj4jZJkA1mn5zAaD0NvJ BpaUlFAopbCQnJsAE/gME/q0vz7JCW9n6U1acWC4TYAJMgAkwASZQ8QmUxrhGq9XP/4TXffY4FCLfGCDTaJ4QTMS8MZONioJaSvPInPNHYxGKTThow0UMkqpmMVDQqcJ7GNZdGKYvabxGmxF0fHMhHZltGAqI6pTI  KF9bj8grEaZSqqY TmixgpZQld9Ncy/mvbEd9duGiskFX9LAWt0GLucVzOKiM/XeS1MGnnRUySmjT0y6k3frzUWy9BKGHhh/4f/khHDn2kKjmVzF2mLHIqhIFCLMfw8vKC3YufIjl5GjlEFCH RBYq5ubmcHR0hLV1jt0xyoIcy2QCTKBCEPiXvjvLrO VrT9lBooFMwEmwASYABNgAhWeQEkmucLL3rOaJy5euoAG9Rvql3gUsce3bt2Au6s7VCo1xEtxThWfQIUwUAhLmPB8EAcnJsAEmEBhCZz95xRu3rhW2OIVupyntzcqU38qNGxWjgkwASbABJgAEygXAiV58RIdHQNrK1v89dcurPvpR2jIE0IvT 8NIb3fN3oGiE99RsanmGO6urnDz9sXERER8PT0ZCNFudz1kjVSIQwUJesC12YCTOC/SqBR02YQR2VKla0/lenecF YABNgAkyACfzXCaxdvbKICIq/TMDZ2Ql1Auqgpr9/EdvMXlxB3vru7m5knBDLQIqvT4mU4MqFJsAGikKj4oJMgAkwASbABJgAE2ACTIAJMAEmUFgCJVniYWZmhurVvQvbVIHlSqJLgcK5QKkRYANFqaFkQUyACTABJsAEmAATYAJMgAkwASZgJMBGAX4Wikqg0hkooo8fx9mZMxG1Zw/SA siuXNHKOsEwMnJKRcbLS1UEgE57WztUKOGP rWCSxW8JVcgjmDCTABJsAEmAATYAJMgAkwASbwHyZgRRsXJCUl8QYG/7FnICk5uUT3vFIZKIRx4nC/fqgRHIyg119HXGgorv74E6rN wq 7TrCxdlZCowSE/sYR4 fgJK2I 3dswfE3rg3KcLr5t83YuBz0gYznJgAE2ACFYLAge1r8ce6BdCqVfotmCngk1ymk4ypNjb2GPjaB6jfoluF0JWVYAJMgAkwASbABJiAkUBtih/xz8mTaNqsGYSxglPlJ5CSkoLTp06gdp26xe5spTJQXP/qK/jUrw8nGrirduyAW6NGkLVqhZurVsEmuD5sbW1gZWkFdzc39OvbR9rbVaNRQ00RYesSxOMnjhcbJFdkAkyACZQFge0/LUbbXiPIuKokjy N/tBopc 0lERsXPERXD184FG9dlk0zzKZABNgAkyACTABJlAsAsHBjXD27Bns2vknUlPTiiWDKz1dBCwtLRBAqxLEvVfTy7XipEploAj9/Xe0fuklpGzZAjPylEg/fx5Vn30WZxYtgk4DMk5YIy09DXv2bkNSYhJsyGDRtXM3mJmZIzk5RYruyokJMIH/LoGQu3cK3XnhwVDd16/Q5YtbMD09VTKmXr90KpcIe0cXeNQIxpIZQ majjwroF mRp9y0o/ DwsLS3Qe8CaadRmSqz5nMAEmwASYABNgAkygrAiIF8FNmzZFy5ateBl9WUGuYHLFmFUYJtLT04utWaUyUGjJE0Im4kqkkYXO0hK61FQoaISuo3xhhBDLO/bs/Qsd23eCvb0D4uPj8OeObejfbwC2bvsd3bv2KDZIrsgEmMDTTSDk7l2cPXMaJ04cK7AjCloe1qx5C1Tz8oJSaVZg RIVoN2wkpMSTIqIfxIDOwdn DboKnlU6Cimjt7LQpvxtzo9GXs3LmQDhUmCnMkEmAATYAJMgAmUJQExUS3JZLUsdWPZFZNApTJQCMQ6VQ5XEjJOiCSME KNZ1xcHBQKfbeFkeL2ndtY PV8DHlhOFxcXCvmXaoIWqWcwYwuA7Gr7Trs/aI17CqCTqwDEyhVAjqcojVzH3z8KaysrExKfvz4MbaQh9YLL7yATz/5AH2e6WeyXOlm6pCcGJ9LpBJpcDWLhCzhVq5rOTNkznKc2bkUjXuOz3nJ9Lk2CltHdsC4vXEZ1y1ca6FZt6F4891X0K5qGRtlTGvFuUyACTABJsAEmAATYAKVnEClNVDUiIpCmLd3hsHiz53bcOqfE3j4MAzfrvgGb46fAHNzc7w3 f9KdIs14RsxtOUk/B00E0d/fwU lXXcrrCFV83aqOnpgMraxRI9CFy5UhAQu/rkZZwIpaC7w4YNw13ytKhdu7YUXLc8knCVS0rMNBSINhVQwVEeAf/mg FUrU6BaqjTknFm62eFN1Do1IiPojZrTcKqzzvAXpWIqFtHsH7BJxiy5wrW7puPzmT04MQEmAATYAJMgAkwASbABEqTQKUZYYbeD5G4iOUctUNCoA4LQ5X9 yn2hH4S0bB Q3To0AmvjHwdHdp3wM8b1ktbjJYspePm2gX4W cAxbnFWH4huWTiKnJt89oY88MurJ8UBMuKrCfrxgTKgEB8fDyGDh2Ke/fuYdq0aWjdunUZtJJb5O1zuxHkaw/bpItwUl3PPHT34deoD xc/RAbeR xEaH5HkkJT6BSFcOg4lQXzVu0QKt2XfDsqA xatXLcI/6HctPkEeHOhK7Z45A1ya14OnpSUcghv4cBslnTRWOfXNHoVNdke JwE6vYN7 CDKrZElU//DXY9GjQXV9fZ 6aNFjFBZdTs1Htgq3Vw5HU3 9XM aLTF45i48MgpWh2HL5H5o08DfoJMPGj03FStWfoSXuzSEr9CzVmuMmH8UsUYc2gRcWD0BPep76 uQzFHrQrLrmvvWcA4TYAJMgAkwASbABJhAGRCoFAaKuLgn2LFzu4RHLPG4Xr06VLdvI7xjRxoo60eu7lWqoppHNbi6uqBxoyZo0qQptm3fKgWfK27SxR/Hku/D0PTjlZgRHI0NC/YhOqfNQxWJgwteQ5cg/eDXp2FfzDqdpG8yv2vp97HjsxfRNkAMxKujfvfxWH4mDpL4/AbU V0TdQuaOOQ16Ui/ijmtPNF4xjnQ9EGfiqujsT5/MoEKSkDs2Z01zZgxQzJOvP/  xg/vpDLJEqhb0d X4QGXV9DqxdmZh5DZqH58x/CwaM2nsQ8goYCEYkgVPkdcoqTodIU/7vO2BWllT0ZKNUUiVtNMS5icObPfbjnNx7L1v2KX9bOwxvt3aHUJeKfTweQEeA6Aictx/r1yzGh7lV89eJAzDlr4KpLwpnPB2DI5yfg8fI8fP/zT1g9qxc0l/bhRDgFVcpLNvmOuLUehU9WbsIf237Ft2/449I34zHlrxjDd2M8rh35B5F1J2HFz79g3bK3Ue/6D/jo4/1wGvQxvlu/Bl8MssKBuWMx 7TeoJx bSnGTt8Ju5Hf4Lc/t2PTsikY1NydPcVK4fllEUyACTABJsAEmAATKCqBp36Jhwi6smnzrxj8/FD8OfoNyYNCpIcDBsCCAmVSGFHp3IwG6CKivXDLFkaJwLqBSElJpqCZu9Gta/eicqPyGkTtXoId6IOVA1qggUd3zH19Cbbc74lXfQxYxSB8zgAMW6ZC7ymLMK2JM9IjouHgbUGWlPyuxePYRwPx2iZvvPn5r hZ7TH2zXsHHw9/H/7HlqLdQ/2AutrbNKDu6glt5B3E uoH1MbBtqlrME4cVgD9ZyzHR7Q97ZUNszCLJg7J23ZheiObLBODd7HsqxZw0cZDV4cmHcixBl5XfB2LAZurMIFyI7B27VosWbIEv/76K7xpmdjhw4exadMmyWvijTfeKDc9RENxsRHSV1hUWOF3FzGloJnSHOriGCi06UhLS0VyejzCrx3G2k WI1TeCK83doAMUVJT9nU7oXvH4AzPKm30DsxdHQL/yfsxf2xtmFOZDq38kXyhCxbPPYBxP/aBc wBfPXdXVR/cye eae VFdT6wHc39 UTf2csqX2Aruid6C WOMgZ1z9tQvWHQ5BWh8XGCOH2NVuj87thE7N4XVvM/YtqoXnXuyPDrZUr7E5Dm4ahmNH7kPVPADquDA8hgM6t22PZg3tqF/B2XTgEybABJgAE2ACTIAJMIHyI/DUGyi2/blVWrrh5OQkUZOCZGbxijAaLG7cvCGtG9dqxZtGDe4/eIC4 GRo6c3jlauXyWARVDTqqlBsXnYcjgO3oKW9ApbtxuA5l/5Yuf46XpwaBDJBQBe7H3NX3kXNyfuwZFKANFA3Jl3MzjyvaaP24qt1EWj11Ta895w7hJtL/S8eYUfrz7H XCJaWeQ9oM5vsK2N2VfgxMHFoGCuiUGOnWK00cXXsWiguTQTKH8CD j74fnnn5eMFB9//LEUr2bOnDnlvkWWWqOFgowLaaklWz4mV5iRgSKne1chuP4zEU38J2YUVHp3wsTv52KECLaTx 5RaaHHcF3tjp7tvTO/88x90KG1C btOY77aX1gE3oUV9Jd0a1bzSIuGUvFvW1z8cGC33DyZjiSlHawIJcu85R02mTVVDKDi58zkBKJmFQqYUtWanNX DgCp2KSycwMWAePw4RWu/DpgNY4O2AkXn31ZTwT7MoeFKZwch4TYAJMgAkwgSIQEHOui fP4 69uxRPK7EINbno00rAxtYWfr5 aBAcLG1SUZz0VBsorly5JG0X6l jprRlqEgZu3iQkUJ4ShgNFNHRkTh67AhatWwjxZ5wJoPGP6fPoFFwI/x99KC0/MPRUW/kKAzItBs/Yc11H7y41BCTwbohRg7zxdofv8f5iV gOTkjpNIg/KrKDT3aV89mnBDy87uWdv8kbtNr08hJjeA9Kbs2FuHJsOyX94A6v8F2YSYOLoV8jkqiY2H4chkm8G8RGDFihNT01KlT0bNnT2nnn5deegk1atQod5WE14OSjCMaTY7diYqoiY62IC2WB0XAu1g7pz2cLGzgVNUb3u42tMii5ElHhmItmV7NFGQwKEJKv7oII8Z8C8Xwz7Dsy8aooqDRiRUAACAASURBVLuFNaPHY1s MhQW5D1HESU0WmHCoPZkSljSL5 O2EpGDau6GP/LafQ4sB7LFy/BhD6LsHzSFmycHCzZMzgxASbABJgAE2ACxSNwgYwTYo42YOAgODg4FE8I13qqCDyhcfOh/Xtxnu59o0aNiqV7IaejxZJdppVSUlJw O9D6Ni E6Kjo/Drxl k9rQ0sReDzoy3aYYYFKNGvgoLC0ts m2jVM6WrDt9e/eCT3Vv9OrRGydOHi Cvkk4//0G3NfexpedfA3B2PzQZcE9IHorVp6I07dPhhAdDYhNjnHzuyYMK7SRZ6 FO7CfAn1mHgfxbW8XyA0D6kNrJ6Be2A80oG6CZ744h0TR6fyuFaGHBRYtiY4FCucCTODfJSCMFLNnz6Yf1XjJa2LMmDH/ikIqtU7aFllD32slOdJSkyBkFTk51ESjpk3QqEEd BbSOGFRvSVqK8kgfPh ppNFeggOHo2BWZ0WECvczKs1hBcicfzEoyIFo0y6fRx30BBvvDscnRoFIbBBMGqVxnhHbgv/zqMxZxMt5xnpiourVqAyxzwu8nPAFZgAE2ACTIAJFIPAnTu30alLV9iTccI4P NP/Ty1snIQhqiOnbvi7u1bxXhi9FWeWgPFmbP/oEf3XoiMjMAf27dgyAvD9D2imBRZk3EXD5HXtEkztGvTDr/8 jP27NktvRnV6bRwc3PHQ9r1o7BJF38Sq7ZGo9bEtdi Ywd2GI/t32N8jQTsXnlQCpZp4d0U/opI/H0oNJc3dEHXasgTcPmGDNVpWYpYmqI/asLL3uD0kt AOo9rhZk4FJaB0L9EOha2IS7HBP4lAkYjRQvaxcLX1/df0UIsy9CoNSUyTgjDRnJiQvGWeBSj13KXLpg8yge3vhiJt7/djkOHtmPZW6Mw764vXn23E5zJYquo0h1v9rbDtc9ew7Q1u3D06G789M3PuFFAe9Y jcmwcQHfzF PfafO4cKFS7hXQo9RVeh2rFy7HX fOYdzxw/h8FXyxrOvArun2r wAJB8mQkwASbABJhAORBISU6GnZ19ObTETVQkAnb29kime1/c9NQOwYQHhXi7efHieQwbMoK8I0TUB7JIiYhyIgaFMQ6FIUimEVDVqh54acQoREVF4uKlC3j46KG0JiolNUVaEiLeluafdIg9vAq7EwLx/pD2CDYGxJQqqWA7NABLZ6/Cnog GFq1O94e6oHBXw7HWM0UDGnmAWX8QyT498GzdfK71g3/G1oVQ5a8hNcVU/BiK29YJN7HjZgAvDC8MawfbMf3B4G6QZ6wSXuQbUAtBtt5XTNOHPqJiYPlNAymIJmXf54lTRzGLtJPHPLve ZVuVvxdSxsG1yOCZQ3AbFWTny3WFnpwy0KI0WPHj1yqSG dBWK0ljskEt0tgyxLCM1JaHESzxSkp4Ub4lH/uqZviqzRdNpm/CDzVTMnD8avyXQfL82fd t/RwTG9voPcrkrugx71fM/mAalsx BesSLeFVz0fyN5Pn8x1sUY9255gZgSkLp2HED/oAyJZOPrTtKG31bFqbAnPToy5g2/zl DBCGLeVcK3XGx8sm4Qg/U9KgfW5ABNgAkyACTABJsAEmEDpEXh6DRSpqbh27SoGDxoKMzMK2GZIGTEo6FyKQWFY4iF2 5BWHNP/hTFDeE107tRVCpgpJhoiLkXBxgkSqo3CgdWHkBo4Hd09c Izg3evwQj4dCbW/PkAg171QZtZW7DGZTpmr3oHo aRW4W1L/rMboM db3yvdaO6q12/QBz1r6PVxbRQFzpjDr9PkafoY2hzGdAnZLPNVrYUvDEobDPlswBxdWxsE1wOSZQvgRkaN6iJT795APpeyG/JL4zRNmyTnIzK9rJIxJS ASj0VWyoWZZOmac0Buu6xdy6L/rREnxPZga9xhCVqGTwgMv7gjDi/lVMK L946F4T1TZcw80GXyGjpMXdTnye3q46X5W nQn6dfm0tuoOvg5Ujfq3nJltmhwStfYycdJpOJevbdf8GDrA5y5gF45 8wvGMU0GQqfj8z1aQ4zmQCTIAJMAEmwASYABMoXwI5Z9jl23pJWqNB9/MDB eKDqolg4RxTY8QbwySuXjJ1/DwqIpI8pwYS0HVRFT Y8eP4vLli7CytkbdOoEIqF1Hik2Rb5K7Y DGEAzMo5CZ31jsCxubedXME92mrKbDRIX8rpl7ofuUVXSYqJfPgNomn2uSpIImDiYG FI9U/nF1NFEjziLCfzrBHz8/ODp7YU z/QrtC5K2r64rJKavL8sbJwQHfkI9s5uUiwKGXl4yGR00Kdc iRDBX2KJJarCUOr NRJnzrpXKNKR0JCHCxtnGnLUjWUyorwtZ GWxvX4G FH2pUc4TiyVVsW7gE96oNx8KAIhhSygo y2UCTIAJMAEmwARKiYD 1UkpCWMx/wECFWGkWizMz/TNPYmQ08BbTZ4SCuOWJvSWU5WWRkHbleSm3ZO2Eg3Exk0bcO36VZy/cBaNGzXFq6 MhooG8LcpkMfq77/DhDdybJtRLO24EhNgAk8jgbI0OBSFhzAupNF3V1W/YDy4dQa1yIiqNhgiiiJHlNXSDh6PQm/Bu3YzSabw/iiUt1hRGypKeU087p7aiq 3XMKjBPIQUziiZvuRWLr4PTShHZA4MQEmwASYABNgApWEANsnKsmNLL9uPLUGClOIvPv1Q zBg6hKgTlk5EkhJ2 IhxERsGjdAgmJcTQ4T0W7dh1x9eplDHxusORFER//hN4omqEOeVCcv3DelFjOYwJMgAmUKwFhoBDLTLyD2uPC2RMI3/1bido3s6uGFnVaSzILF2unRM0VXFnhhm5zttNRcFEuwQSYABNgAkyACTCBggis3nEFq/68DBUFGDdTyPFK7yCM6hVYUDW XgEJPPUGCjHYFgHrkpKS4DB8OC7/ SfM7Ozg6uiIh5QX8uQJvD78AN5e1aXlIFWrVJUMErv37ZeCsfXu2V0atF 7dgXRMdEV8BaxSkyACfzXCAgPBxErJ6heQyhHzUBMTEyJEDg5OaFu3bqSzH/de6JEPeHKTIAJMAEmwASYwNNEoLwcKL4j48TbQ5vDXCnHjQdPsGLbBYxkA8XT9Khk6PrUGyiEy7KIui MFHLajtPxiy9w67sVCLl8FelBgUgc0B9RifG4d4i2vTCRfly/loJsKlEnIBCjXn7VRAnOYgJMgAmULwFhRBDBf11dXWFPHmHCEFuSJOQJjzERf4INFCUhyXWZABNgAkyACTCBikhAbM0u4oafuh4BG0szpKfrd/uqiLqyTvkTeOoNFJaWltKaajH4Fn9b9uoFr44dJaOFiC0hkvCcEIN9a1rHbWNjI32KQ9STyxXZdgHJHxdfZQJMgAmUDwHj91bWXYpK2jIbJ0pKkOszASbABJgAE2ACFZGAljziU1LViE9Mg5aMFTqKwcXp6STw1BsoBHYxgBeHeNPIiQkwASZQWQiwQaGy3EnuBxNgAkyACTCB/yqBknmBFpaa2LksNU2FuKR0/U5m0pbx5dN2YXUsdjltEu6dOop7ji3RPsAO v3bii2twlesFAaKCk ZFWQCTIAJMAEmwASYABNgAkyACTCBEhNYue0yVv95CSq1CP6t31rd2c4KSakq8qBIgYyWxlpbmKHhiyskY4U4KG4mRvdvgvHPN82/fc0jrO/XClPTxuCXje hhUMWc0DiAYwMHonw6UewbaQXymwibdTBcjHO/doXTikXMe/V13H5jf3YxQaK/O8fX2UCTIAJMAEmwASYABNgAkyACTABJmCSQBk4MXy3/QKebRcAS3OF1KS0 5kWuHI3GnG0xCMtXYPurQNgQddF8yKUV0JyKpZtPIHxAwswUBj1vfEtRr1ZHX9 Nxy ZoaeGa9JQk32tnQys8rO2lZZt1s62pdYSmX3ECkxIBbABJgAE2ACTIAJMAEmwASYABNgAhWDgIoCYKbSseXwLfx2SH/8fvgGzt6MRGKKCjHxKfjrnxBsP3YXO47fw84TIbgaGgdRr9DJoxW8TkzHq1 dRmJ xoj0B9j5 cvoGOQLH19/NOo9ASvPxkGLRBx5sx58Ws/G5TRDq4mHMS7QF72 fwC9JlpEbBwA35rDsC02v0b09W/N6QR/X9GOLwbviNNn5tk XVY/xNb3B6JD4zpSHR/fmmg2aDq WzUTr/RogpoiL7ADXl54HLEVKGRHmXmmFPrmc0EmwASYABPIRuDChQtISEiQdtzIuoNH1r/Fjhx fn6oUqVKRt3o6Gjs2LEDiYmJUKvVUl0hQ5S1o 2Xe/ToATc3N6bNBJgAE2ACTIAJMIFyIWDctKA0G5PJdDh9IxJODtbSzh0iyeh/qeQ5kUxGCBta3mFtmblzmRgLpdO4SE71CtRHo4KGbAVy3xfx9QfuGD7uNbwXtA1f9XSDQkVjK2pLR2XUtBmDTpeAkx8PxpjfPTFm5lp093iMg4v DzNfnorq  ahYdd6UGw7irORKahdVYG024dwPhmIPnAZT4a5w4GMGFf2Xoeu9jsIslaRbgZKBh2gU0vtqNQqqV3Pl5ZhySCxtEQGWy9zMrjE5NP fHSyisGVI6cREfA2lowNhvXjM1jz4QJ8croGBkyehqV1rBG5Zx5mzB P2c3347OmVqV5m4otq9IZKDRaHeatPYzN y4hKSUdNau74IPXuyA4oFo2SBdvheOz7/bjRkg0rCyUeL5rfUwc1oYeXMNTXmykXJEJMAEmUDICcXFxaNasmcltQY2BM8XWyufPn5d2MHJycoKGgkH9/PPP0nmDBg3g5eUlGS8iIiIQGhqKK1euYMOGDRg3bpy0gxEnJsAEmAATYAJMgAmUNYGSbpVuSr Xe9bF6m0X6WWMiEEhYkxoKeaEBZ7t3hh/X3oIR4pHce3yDSQkpZA1QR jQiGXYczAZtle/JiSLdaD6H0Z5HDt/CGWjRmEwVOmoFXQcgx2NHo56ONaaKL3Y GGSLT47Be83ddNCl4ZNCscu7rMwy/nk9CuYU/UxWzsvpiAQVVsEXnqCMJlCmgu7cWt5I5oLLuDfWeS4Du4OdzlQqZBI6MOdK7vn35FiaV7DQQE GbEvsi//UR0bKEXaFezNdq3qg9LNEa10K04uNQfzwzpg7Y21F5DMxz /VWcPHof6U1qwbiaxSSbcsqsdAaKH7adxq97LuP1QW3oht9HXEIiXvloI9bOegFB/vo3jVfvRuLFaRswZnAbaMxsaEsaFdbvuggne2u8/EzjckLPzTABJsAETBMQkaiFISL5wndQP7mVq5DSsSZsGr6GOnXqQHhbiPJia2UL nHu37 /ZKyIiYlBWFiYtLuR8LQIDAzEtm3bILwssnpd5BLOGUyACTABJsAEmAATKCUCZWGgeK1PPbzaOyibhk1GroKdtTksLS1hYWlGwTKTcH7dmGxlcnqmmuyisBIYDAUUahMN3liIycefw0f/ wGNl9XQX5KMIjqk3T NO SZETWlLQKmZJdmHpEEtGyF3rXS8O1f15HcyQ n/wpDwLgJsFy9GQdC01BP TeORHmgS2dvKDMMIyQnQwd9O5kMDeeGplILaF TIdNYTwmn6k5AahRiUshwY00v5pXO8HYATscmQU3lK4JxoCLoYPLZKCgz9PEVVHcKzFVs26FrqOLhip93nkF45BN4VnWGl2cVCMPFnEm9pfLfbz0NHy93bD14FY8iY Hu6kgDdhdsO3yFDRS5iHIGE/jvEAi5e6fQnRU/ctV9/QpdvigFhYFBGB0s643Ks5ooI5ZttGzZUvqRFB4Scrkcjo6OUl3hJWFrayst99i3bx CgoKk88jISDZQ5EmVLzABJsAEmAATYAKlSaC0DRRijCMOsZRVK03k9dYELUXJNDNTknHCnF7YmJHjhP7ljdQXGrMJL3mx5FWMlcSRZ8o5qTf3x0tfTsX Zz/FO2v B3upYqbhQAdbdJuzBm8FWWYRKYN1FWfIFFq07 GDL37ejmsR7bD9uhu6z gJx4PfYN2RUPRX7kCIa2f09DPP7tmRUwdDHyXvjoxrBu K/NrXxep1ylJPbm5GC0RoiQrx0ekEB2JGFgEdrWsRPI1OHHnyKYcLT62B4p3fW2F0q3noVufVbJiu3I34f/bOA77G6//jnztys/feexIJMWNvFUpRmypaSlV/bVE/5V9aP6UobVVLt9KqqlGlWitVmyBGRBaSyB6yc29y7/97npubRGQTEj2nr9skz3OeM973eu45n c70LaNN2Ji4vHTinEYOW8L2rf1xe8kXGgEin1/R8Df3xM3Lt3AL6smYuzCHxHQxguXwuObDnlJCo5u3oRLni9jTj/rZqFONd1kecucQMsjcDsuDhfDLuDMmVN1Dp5t/jt07AQ7cqOQSh 9MRz78mECBCuJuxbQ/ kLpCbvs7JvkoR8c iIS5B5MQdFJSLEXf4HmRlpKGZRmKitqzf3QWrdGjFp4XT/869zjrzCIyZQGIbFfUfiYLetOLwqGIaPuHneHCfACXACnAAn0BwJNIVAIZfLBctRQaSgjXapIFqUQqqlRRYUWpS9Q1tAkZmVRelF1YIEEyd0dXUFV1iNu2y1vKoRAySOz ODdw4h5J3VIKcR JRt GV2AXAR/4SIKIoP8awbuVDcX5gA4DxwCJw//RlbdyTiklFPzHG0g94zDvhg1y/4SRwNiwFL4aldyb2DNaEZg/ArnRNpQV8GFGQXCFYOGkfdOvuXawSHCmFD834I7bJ yvoSarJj1UJ5vAdbrEAhLynCbxGf4vLdo3i1  fQ0TIQyAX52JNbRwFsyXJizIJtENNGgn0gGey7aTmCekZZaIRj7E0YOe97ONvbID vAIFe9k1HXxGPAxs/x6mpY/EqCRRNWpR5uHX2JGJNOqOXj5HgDyUUvkBuUuy88ZZOQIVz585gydLlwhdYdSWLvuj27NmDMWPGYPmyJQgZOqy6ag99TPOFK5giUkAm2x596V5GQgj5T6qVirIvFHZjI99Kkrxx7Wwa7O11oevgjSJy78hT6lOqLYrwTE8TIGPXyem p0J KX3D1VWU6fj9lcGYsy8RmsDTUiNHtO46DDPenouhHhSUqq42mul5Zd4N7P1kNb745SjCk4tolAZwCOyBkXOX4Y0BtjWLx8o07J3SE68cLouaTQT0bHzQvtezmPTKNDzjoV87Ewn14 EFD3vjZuHf2UzfHj4sToAT4AQ4gaeMwKMWKDQba/XDHLUwweJysSUSSy9qaaKPoiI5WZKKUZCfDz09PWEPLpGUbdI1G/OaOLMlVtk5oS/hdzFsh72Lhb8NxZIztDIqa0Ns3ovSllph6pev4DXxHIzuaA/t/ETEZHnguVEBMKJNmNTpGTzntgHrNqTBdsprcKPUp5LeQ2G/ iN8A1u8 L4ntKsKA5oxlPWj0rJHO3cpfvrlY3znP4EEkmSkW/XFsMA6 i fSJnQQTPRHNLMoVyU0PRVE5fHeLzFChSM0bTey3D42o94fVd7LOz3C5zNWmPswAAs/eIwPdm0QVCQlSBIJKVmCT/DLl4gk2gjWkSqkJqehU4d1E8R8yiASkJCEt6Z1rt 6EuT8MOQ9lgQ/mB1t3nHcOT1JxxgpDAcq6e8iKtzjqN7ZYGCL5AffMP4EU6gEgGmwtckTrBAk PHj0ccWVp4eXmVWzg0BUBmPaGxoGBPBCRaMsjzrtP3I/taKZMcBWGC/qS6KhIosnN0cfiXbeg56mVkX7uG1E83QDc7F0oycyyVSaGUiiEd Rxy/HzrHrJKgaw7JE54z8OWD4KhV5yDlJhT2L7uU7wyPBnGJ9ahp3HLkyiU2SewbPhobI6yR6 pb2JNB2cYyFMQcfoU0hWS2gUGiqSdk0bihNdcfL28G12Xi To8/hj60d4qedWjPp8F1YPtatZfJB5Ycb3B3G/N2zdbwWvwQlwApwAJ8AJtGQCj1qg0GQn01hDKCj1BXsN6WSDT7/aS8si5uYqFv7WIosKVo/9ZNav7AF1nXEoysWCCqsDgb/YDsPffQO/hqwgKwrNOXK1/e8P2GD AQXLXIpXN5H1q8QUXoMXoP INjBkSyWpI4ZM8Me69zIx5Fl3yJha4tAPI7w woclozHSo4p7B ur6hhE5ui/5P8w7I1VWPt6KD18skbX1wMwONC99v6rtqNuWphOVQsKJl1UCDJClSdWWrRAIRZJ0cNvOJwsfLBo/wC80P49DOkxDQZ62li04SDCr6qfdJka6WBsJ9p4SBW4cOYo/S7CzvPJiI2NFxQ1c1La3p81AAO7eDXsjfD6D75Z3lX94ROuFEPfmYKcNKyVx1ebL5AfH2ve01NFICcnB PGjcPt27exaNEiBAcH47fdvzTZHDUxKNSRp0mFoC9a9mhARD9FZKooqN/0HUjegoIULiKBIicPSAm9BpOJ tAmvw5jcyuYe/pAx8ICShJo8ykWRWJBKe6WNsAlxcwb7Tt2VPtbdu HntbX0Gb6WZy q0BP/Wz8teJNrNx9GhHJlDOLkmX1WPMXtoy1h1SRjCPrF K9r/7EzRw64zUQ05eswJze1rSBz8XxmR0wNmwiDh5/B62ZFWbu33g5aBxuLTyN/S yeyjlBf95OILm6WDj S/hvG8R5q3djauZNF9dRwxYuh2bJjirxQA5WaetXojl3x1FXJ4EZq2GYM4HKzC9nXGF9RjjRanAzqyYTeKED bu2415bQ3LBYkho6YK72Vp6u94uf8sXOy3BYdW90C1GoyJLzp2CYYpW3T0GoiRkydi27T mDf3DXRtvxWjLTOq5zIiB2t69sP2fr/j5HtuODk9CJOuTcNfoW/DTzBqKUXCdyHotNQSX134HoP0E o3L2HkvHACnAAnwAlwAs2TwKMWKNgsWQwJJjowwYG92AOmyYNaYVQPF F3dl5PT1 IvcUECiZOMGFC49pR65jEVnh  xU8zzqqYtkgcRyPreHj1aA157Rs0evV9fSqyp9t IXRwnbMNlwbo7mMDkqcMOXXK5giHNLUq3R95TGUnZe5DMf/fqVXpWrC GrrX yJuX9cwVyhG7U1iEGvL3H1qroRgYOWO2btv4JZlepU7uJJ/N5s99L1gkFQI 8dh4OJP2b0 R92nFlf7vJx4ptXypuIjYvB3r274ebqQen4zHAs9Bj2rhlNgeJshTpaWpLGpRc18UaHLl3UC9UqA1YVRmPn wuw6sfTSCyWwrp1AGQUp6R8a5B/Eq8GPS9YOfw12004rrj1OQZ2XY/Wv5zHx10o74siFaEb/otlmw/iRrYSUou2eOnr7XgnSIaYL6dgzIpjSGIWyrRg7/rCUqx/eyBsK 09ov7XHS5ln LOm65jZ/ 7WFm QA5U 0nVupGgtksSsWfhLHz45zXEpTOvKxFMvJ/B7JUfYmYHk/s3AFUY8D85gZZKIJ9MAvX1We4ldVm8eDFu3bqFhQsXYtYs4RbepEVttkiBMssEiAq3Dmb/RYV9oQi/sN9ZkKMSuo pEEX/PuNzc3GH0pReiY4W4hywaiyaBUut7UIWICKwoBQNLEo57sWfxdbvL6LUagi62tONRpmBsP1HcMv1LWxc0wnmyhyofKwoCnUezi8fgUmbgeGLN FdMti4vv19vD9xJAr2HcQ7bQ3gN7gNpL dwuXMUrS2pbzgt4 DsnEh7Vgk8kmgMEY IllecJ F8EvaiEnv/AG7Nz7Hrn72UKbGItPFSn0vVeXg1LsjMX2nI179YAcG2WXhyNo3sXTC23A/9Rn6mlSy8sg9h80702A4dB1mBlaIE/eTID9WcqkpYQnQ61tkzhi16GVs6PsRNu9PwIhJBdVzASk15cUQAcOCID1wGKeS34KfE3M5zMbF/RGQBExDO6NcnFpcz3nVd5y8HifACXACnAAn8AQI1CoGPMR4KgsOzI2DCRUlJSaCFYDGyoLFm2DiROWgmE01noeYCr 0CoEWLVCwJaRSWYI7eRdhInPA5O6LERqxA3PJ5eO/ZS4fbL63b9 CtY01BVApIRVNh/y0bREVFQknR8em UAos3Ds7ZGYu9MQIxZtxHM Wrh7ehvWkFpV72eXqnyErRyB8RsVGDz/YywKMoM8JR3GjuxxoxiWwS9i2ZdzYGOixN1jGzB/9SzMb3cW34WYl4sGDtO weZxjtSnCPoO6hgd9024zo0EbdBo03Hjn/NIodw5X6wLhF5BDA6uW4rlk7Xgc3oD lT7iLFpsPJWOYHHQWDLli3YsGEDduzYAUe6Rxw/fhw7d 4UrCZmz579OIYguHewl0jJZAUqTJAQXDnIgoBtntlPup p2IvlAC9VwNlcCpvANjhz6BCMyWoigb6ojSh4FGWOEoQKU3pyYOLpAVlxA4IBn5oO3/tC8zhi7FcL0NmINv5y9dCMfHtjQK8ywZMOKdMPYPU3t E 7yg mukFZhzQs4s7pUzti09XH8MrP4TApN0Q OFd/BGei/G2Bkg5E4oksogrDf8TUYX90F4Ug0Pn8 A6oQss8jcgi2bRp1sPdAhgwkKgumOhr8NYszUFXdbsw4LnyKWPjvmvSsKB4A w7VIe vaqCEWpSL2KGNJY3bp7Q78G7xSJ1VB8dX1oefv1/UXm0BF esCJ8LuExUS4rCoXDS91myKYdhyJIMkb2HMyHVOcbCDOCcOvF5RovYRE78z6z6u Y T1OAFOgBPgBDiBJ0FAbUXQdD2LROTCSgHLJRKKOVipM42AoXbpaLr ecuPnkCLFijYol1Jps26YkNkFychT56JYK9n4UBmyRqXD1mqGxITE9CNFrdZOemCuU fXv3w /59OP7P3 hOxxtdzs5Ea4eZFZfrD8H2sC8QXHAYH/ aDu9Fu7D2FbV1BDpbIvzHI6g7P4C6OVXmUaz Mg4e845gw1xvYZFfuRj59cPgsiyr7VqZIWJHX2w9fhvFJFBowvvpWnvA17esf3Zx2YZC044y40idC2k2fwAAIABJREFUGwnzssqG3j3RrzfbhPREsOMdHH5mB367UYg nWhVzgsn8JQRSEhIwKhRowSRYunSpULE55UrV9Ye9fkRMih38ShRQFlKEapL5FAVkYmBiJnnMYGC XcwYYIEitJiqOTFcNHPgeeg/oj8/Cu4mpvDmwQKYxIoKNu14KJhPno0RY82gnf2P/Ufqf//YddH3WFAFhT5aTE4tX0NVk17BtjyFz7sVn0zxXdOIbLECoN6OFbct8jKoGewOdYeOo344hCYW3fHs97F JQsBgr6u P8gXj4kouEzqbtOHxbjgDp3whNtcfAAS4wdn8Fc7ocxPIRwbg4YgqmTXsBQwMtBLG3mKw6YmiOqXPbwlGwX6wo2uR2oiRppjxIsJqckGqsBn2i gnV92gDjC5Yk2LLHhjfQYw3d/yDjNGjoHPxF5ySt8GivrYoadC86jtAXo8T4AQ4AU6AE3gSBBr4BdmIIdJXe9karbpv KbvvxFD5pfUQqBFCxSClTMz4yGPZVUJ WVThPrIe3/Dwbg1pvZYioNHf4NTUS9Me2EGsrOzcCnsMjq27wwLNyv07tNHcPuwsbGBJ0VWb1TxfRvb1/Ysy4dL/zBkpnCj/Xpx5HnEKa0wuHMtAdPq6LDozklEKCwxsIfTA IEUIRb 1ZjybpdOBuVjHypIbTJ1UNWSJuYOtqtfLpeG4mK1X35pTKbVrDB10jOaYSpeAPGx6tyAk CwKRJk4RumTvHoEGDcI/cJSZPngw3N7fHNhxNjm8VCRSlheQ6UZSL0vxUsphQ0D2PrCqY5QSJE2B/k0hL5mEkRCjR3pL nvoCdI7 DSuyuGACoyWJK2Ia/3lvL/iLz0BWlFT/eRg4wsfXt weF4AOnd2QcTYE331zEf/Xza7 7VStqeWAPkNc8f6WvZQXvDf2RNhg8PvPwvTIx/g29Dael 5DnOUAyhZCFmM6vpj18wUMPLYNmyjw55yQj7Fp7h78Mi8QErr/q0iEeGb9z5jfpnJyL/I9tamwJmPdSylWkROpGhfPxKJgvA3l7nh0RR5/CtfIOsO jR3dr1k8jnoUsSV6TOwM8evbSIzpC4sfQ1EU9C762VDysOT6z6sePfEqnAAnwAlwApzAEyPAXSqeGPoW23GLFiiUtFBni3MxmfUcOLcVnX0GwcbUCfE54dDKtYVdbg MHT9JEDHyC/JRWFRI8SeOwJMi8GvJtCj4Wwcc ON3mI03h7mZxlagAe loQta bd5IAZFofCETm3dUWNrZI7E4t6VyGvY5JMJN5NeqtMB5REfY9KMLyCZ8D9s/LAdrFXR PblWdhXY2eP9oSITKgktBlqiJv2ox0Bb40TaFoClUUKZho4Y8aMpu2wSutCTm/m0qEgy4WkGJTmpaIkO1F4 l9RmCUFC6zEfjLXDyVctG9Dal2E8726oahrVyApCVfJTaWI7jVtpcdhr4xDIhM0GllU8jyyVqPNPuUYr0a7FFrVduoML n3OHk8HvJ2ahcPyG8j9GQGtHw6QfBSI/sHt5ARcF2zBd9uS0CYcV/Mc3WA3lBnLP15G34QR8IyZBV8NJqD2ADufV7Gyt5j8dw7vTHy680In70BnR3bw028BdduiuA0yuuB/OOVpyky6oDJ/Q1xdDe5f8z6GS97V81W3kgoxbHYvuxL3JZ1w0fPUIBQigRSv0Kuer2no6/ONHyz/VeYHytF97X9Yc2SmzdgXvXri9fiBDgBToAT4ASeDAEuUDwZ7i251xYtUMhLyWKAFueUNIby3hbh3I0jcLP1g79TVySe18WwkOEwNTEVrCeOnwyFgYMCgU59ERp6DD169IS8uAjt2gVh956dmPbiy4/sfdR27AxPWqD/fSiWnoi1qn7RLDWh4J7A/qvxKFB5PRAtXpsWqO6SLTjx9x1a5N/v4pEfcxqxCMC6tyagtxVTOQzgyRzNNUWsDQNaexdkMRPnmku9NhJlLvA1t8LPcAJPJwGNSLF79264uLg81kmWkNuCIFCQBYXgO8lcPIrpH2NVxZJZEDDBQXiRqEkve0k8cozFuJTri2J3d QX5yFI 5ogTqioTSW96l0yI3DmpDH0FAXISriKQz9swC9ZNpj4QiD0QYJJNUVsTmLDi84YtmoK3tBZhNEUJPPaT 9jbZwLZn7cG2Zlc9ByexajPddg5dojsJ8xH56UDlU8cASclq/AF7DHjLW wr1Tced3fBcK Layh35xAo5HUHYmI2sY0reX2LI//jPOBmM3TMZLkvmY2MUR2nnxuJnhjTET2oEwVBSxGfos/R8Gn56DpYMG49IrUzAwgNoszcKtK cQ5zoLS3pdxZy6snhkXiPxxQQGilykxrA0o1/jj2grSjP6EZ6zo0FVcaWrBlH5IZFJF0wfaoqRq5ZQkJAR LG7mVr4aci8auuAn MEOAFOgBPgBJ4gAV0KXskCj7Mglrz8ewjkFxQ81HveogWKUjJvVtICnWwRhHd83Yhz OjoFJw9fQHtLEfD1dUN93KySaDIRlpWMo5d34TbJadhn9UfOTn3YGFuAyMDE0TeiKAI/XG0CXFt2Ccn6zpO/WMiBKDTFImBMwID mLBVBc8 /F4TFO jRe6OUE75xxiKA1geZG5YjA9LVz36duY9 kijAkwgzLuCijRh1DEZN78xjhbjP5wAmaWzsfYDraQ5txFrnsIBjq3gwM24fOPtsF8RGtYSBJxq3Lb2o7o6CnFlh8/xOa2U9EKd5FmPQij2lTqn/VRz43E/VfxvziBp5cAi/JcWFgopKRihYkUAwcOfGDCBXTjZVGhm6poLCiUZEHBikpO1mLF9Pt9FhRqFzcWi6dCoFALFd7SaFyVekFEQYG1kQcv1Q0hmCYLtKkk8aPOQgErTR3JXeH3NZgi5NmirvWt4RU0HEt fBNTuxlBJK9eoIDIAO0X7cT3 pRm9KOXsSuX9AQvup9t QCvtdOv0Fi0XDBiaiBWLszAc6O8aZxUnEIwxmcF3iudiPE whHI08Kx76NN L8UxkIKi9aDsWTjXLQSThuj /t78I3FEqzc8jamfkxzk5rBZ9hShIyrIlCwq 1G4LPDNvhu9Tp8/91i7MlmLGQw92iPgS/JhWwnwpOe6oxMiImRBUXzOPIJXh73CescutY aN/7DXz51TQM8qg0N FsfYoB2k2fCJcf16Fk7MvoxIKPsiJq2Lzq0xOvwwlwApwAJ8AJPG4CXt4 OH/2LNp36AAmVvDy9BNg6 gL587Ay4eeUDWytGiBokRJweGYi4cQpUGFadvcBQwdil9Dh67ByMm9R64dedh/cB9ydWPQO2A4cmSRuCT6HtI/xJg0YSoUcrkgTJy/cK7hAkXUx3hp7Mf3o3d6DYdCFyCIAmRuN38Xy79aiBc/ZWYIMpi5dESIl1GZabQ2/F7/Dh9lv4EVq2fjd7ZOlhrDwb87AizIUVqkj6608P7W/B2s PpNvLiWbCH0XBCyoitCRs7F5vdSMH/9Ikz6Xr3Z0DF1Rnt3Y7VUQ7lzQz5YidAZS7Hi5UNkTW2LnguDMLyKQFHvjUQjP1z8Mk6gZREQoWOnzli bIlgvVBbYeIEq9tURRMkkwXIVJE7mEpBYixZUKj1CY0ZBXPvoBEIG2qNBYX6J3P3MBQXIE9JT/opWw8odSaznmDHS8kqo85C8RFCNp1DSG0VZb5YcCoRC6qrQ/ecvvO pVd1JzXHpHCY/DsSJ1eqo WKmYcTUSn0MPSDFmJ32MKaG6IMTgPmf02vmqtUPqNlFYzpq9iruvqe2Bx p7oTTDXGs1si8Gz1ZyuO1sSlhuMyn3k4kVgNqAbOq65h8fOcACfACXACnMDjJhAY2BYXL4bh4B/7UVREPqK8PPUEdHS04e3jB/bel9RnzVkNkRYtUCg0Lh4iCV7q877w0EtF /jre4rh6OCElLREsGj8cmk2be4LILIuRaBNTyQYRSHq8hnE3e4FZ0cXWFlb4crVK9XgqeGQxBYTDyRiYg2n1Yet0O3Vz3Dg1ZoriXQ9MXrlb/SqoY6WPfrP/4ZeD55vM/UT/EGvmoq2 1isP0SvKhUe2FDUtZGoZlEtMn8OexKfq6lrfpwTaJEEnF1dYe/ogJChw o9fpbWqimKJkhmKbOgUJGLB/1kLh706/1F87RfI1BorClIiNBT5SCj2AyWlCpYRQIFEzHUgkZTjJi3yQlwApwAJ8AJcAKcwP0ESulBS/v27dG5c5fHlgmNvwdPlgCzRGXChJyMABpbWrRAUUKp75gFxe2cK VmuQyKzMAH YV50NLSwemzp5FpTUEz9ZSQ6mpRAM0ImBnYQTewFHv27cSrM16HrbU9TE3NGsuQX8cJcAJPCYGmEhwaikfj4sGsHQThtVoXjzJXBEGkUL8qx6MwEGVCKXaEoZIEWkGZUBeRuKrK0dDR8fqcACfACXACnAAnwAnUjwDbqD7MZrV vfBaTxOBFi1QKEqLYWfgh8Jzv0K73XBBpJCH7UW2aSsyZwYuX74AmU0 nKzcoRd/FDK3IWpL6PD9MPQfhBK7AvxzKhSd2neFvqna3/lpenP5XDgBTqBlEtAEySzJTQfTE0oy7tQQJJPmV0mgKFFJcF3kj3tSC9zTsiHXDuCOQQdkKd2hXZgKl LrEEkyWiYUPmpOgBPgBDgBToAT4AQ4gaeeQIsWKDYffkd4g2yLVUg6Fqb vYil96T0bf 44WZsOP7K RCIKoUdLfLTM8KFp5E2VP/u3YsQlUqRdetN8slW4kD0p8DpNIzs9Bo3QXrqP/Z8gpxA8ybAgnRmZFBazphT0C/JhSI5mqwoHgySWdkyQknRbQ5ph8DX3RleOkUozM/FwTsSXAg9CLFMF0OHj0KsogtlvzjSvCfPR8cJcAKcACfACXACnAAn8K8l0GIFim9GJlGwlaJq3zhmRrRv/x507dgfwy0mCHWkUqnwYlH6WQA6zRPKpKS7uBZxFYuHb4OhoSEXJ6olyg9yApzA4yTQtm1b/HPkILwv/SRkrcxK0fROSusDHhrqAyqKxVPsXopSkS7ySqQUF1MBUwqQOWFIP1i5 cHC2Q h//wNPTufxzkV3hcnwAlwApwAJ8AJcAKcACdQbwItVqAwM6s9ZsT4cZNgVo 4Et7e3vBv0wbmZub1hsYrcgKcACfQlAQCAgLAXgUFr6KA8ocXF1PGIooALKTALMuByWQJ9d9lI6FzHpRC9GrENSTcu0e1bKBnL0Eypf64eycLuukX0KVzVzi5eTXl0HnbnAAnwAlwApwAJ8AJcAKcQKMJtFiBoq4Z10ec0LTBxYm6aPLznAAn8CQI6FHOcPZqSHH14AJEQ3jxupwAJ8AJcAKcACfACXACzYfAUytQNB/EfCScACfACXACnAAnwAlwApwAJ8AJ/LsIsKxksdHRSE6 i6LCwn/X5P ls9WhOGo2NnZw8/AQQis0pnCBojHU DWcACfACXACnAAnwAlwApwAJ8AJcAI1EoiNjiJ31Xx069EL gYGNdbjJ54eAvl5eQi/FIbYmGh4eDbOqpcLFE/P54HPhBPgBP4lBI4dO4bIyMjyYL9s2hKJBFpaWmBxdXr27PkvIcGnyQlwApwAJ8AJcALNlUDS3UT06N0XuuSuel/crOY6YD6uhyagp6 PgLZB PvYES5Q1EQzPuEOjhw5hG6LlwpVji9bjL59B8DRwammS/hxToAT4ASaLYEjR47g6tWrcHZ2hpubGxwdHYWxxsfHIzY2FpcvXxYyFfXp06fZzoEPjBPgBDgBToAT4ASefgIsyLeOji5UShbkm5d/CwH2nhfXkG2zPgyeegsKJk4EtWuPzIICgYenpycOH/4TU16YXh8 vA4nwAlwAs2KQB6ZzvXo0QMuLi7IycnBzZs3hRTKpqamCA4Ohr29PRITE5vVmPlgOAFOgBPgBDgBTuDfSUBVln3s3zl7PuvGEHjqBYrklGS4u3vgKKXqY6Wtqzv OXGiMaz4NZwAJ8AJPHECqamp6NWrF4yMjGBiYgJLS0vk0/2NvbKzs6FLwYlYHV44AU6AE AEOAFOgBN44gSEFOm8cAL1J/DUCxQaFFk8cmz9PxW8JifwLyVwOy623jMXiURwcnGtd/1HUZGZSioUCkGcYKWALMOYGMEsKYrIlE4ul5MppY7wk9XV1tZ FN3yNjgBToAT4AQ4AU6AE2gUAS5PNArbv/qiZiNQsKBv7KlgQ0tubq4QGI4txNmGoabidPwY0tP5U8Wa PDjnMC/ncDtuDhcDLuAM2dO1YmCBaTs0LET7BwcyL1Cq876j6oCEyI04gQTKpJv30ZkWBgKyXpCTEGJRPSS0b2QWVGwusz1g90XmaVFcy3KnEv4asFbWP9bBLJoFeP82mH8MXQvnhv6I3y OIxP pmhcUmqmsGMC8OwuO9IHOy2FYdXBcOwGQyJD4ET4AQ4AU6AE3isBLgFxWPF/TR01mwEilmzZuGzzz5rsEihVCkRfuUyUlJSoVSWws7OHm0D2woL88oluEs33Lhx5Wl4z/gcOAFOoEkIqHDu3BksWbpc2OBXV7KysrBnzx6MGTMGy5ctQcjQYdVVa7JjTHRQkhjx64IFcPTxQeSPPyI7NBQyJs6S5QRkMkjJukLyn/ AubdFRFyjsYgoMHA/mJuZN3hcyrwb2PvJanzxy1GEJxfR9QZwCOyBkXOX4Y0Btnj4L5BCXFo5Fe8e88W8jUvR1VYGbUc36BTawd3THY4mWjT6J13kuP5BT/Tf6IRNl35CiGntI8o MA4B05Mw//hfmO1AvDy84GFvjMcnYz1pXrx/ToAT4AQ4AU6gggDXJ/inoaEEHn592dAea6jPngbOnTsX69evb5BIYWxkjI4dOpE4ocS9e9n4ecd2ZGVlYkD/gTX09OgOP7h414ald0cMfGER3pnsD8Pa17GPbiC8JU6AE3gkBNh9pCZx4s6dOxg/fjziyNLCy8tLyJTxOEohuaddvRqO5ORk0hpEuH36FIKMTaBH1mPWFAzTgdw59GkgInLpUNLP5LQ0ZFJGj/Nh5zCwX39yCZHTffEnvDJjdoOGq8w gWXDR2NzlD16TX0Tazo4w0CeggjqP10heTTCgeIuTp5IgeWwzZgxNAgVstBEbPpjYoPG23SVZXBo7wlZyXWciy8mgYKEIFaKruDDCa/hVMf12LqgTdnYixF/Lholhp3Q1pokCZkXZnx/EDOabnC8ZU6AE AEOAFOoJkT4E4ezfwNanbDa1aWs0yceP3118HcPRpaxGIxRbE3w4ABg/Drrp0NvbzB9YXF 5C mP3pFZiFvIW1n2/ChtWLMCXYGFk5YmhxcaLBTPkFnEBzJcAsF8aNG4dbt25h0aJFQraMx1WYYKJN6ZqU9J8PWU20GhqCGKkELE/HKRIvQuned4hcTnbT39/RayeJGHlmpjAgd4 oqBv4 /hx9O83oGHDVeXizIrZJE74YO6 w/jhvVkY 2wIhoyainmrN2NliBUkrEVFMo6sfhG9fe2F7CF vadi7dEUKDS9lSRiz7xh6BbgIZy3t3dAqz4v4bNz2YKYApUc cVA2pZnycpA3Ub3dVEouPU5 th745UT6uDGKEnF8U9mYmAbJ3U7zr7oNPBFfHyNrDryT JVHxJRNsSW96sQrvfFa6foerr2r/cmoV QZ9kY/DDup0SUsP7l8Tjwv4no5s36doL/gFnYFHZPPbZKxHTdu8AVSbhwgyxYyo4XRe7E9tM3cWb7z4hkxiWsKO8h8sJdwL0r3JiOIY/Ayi72aLf4EoQqdfFgdeo5JqE/XjgBToAT4AQ4gWZOgFlQ8NdjZKAsQX5GMlJzFGDZXZ8U 4f5WDYbCwo2CRaDYt26dYJIwX6yv tTIiNv4PCRv5CblytUd3V1wcoP/1frpT9s/Q79 w CtZV1rfWqPVm ePfCa3v3Yn6QYaWnidMqXaJAzJdTMGbFMSSx1amuI7q sBTr3x4IW2bvyxarC2dh1cGruJXBKkhh1XE8ZoVo458fdyH0RjoUes7oM2s11r8WDDNhR0CFLWBXL8Ty744iLk8Cs1ZDMOeDFZjezhhiZS7Cv/sv5q3djauZtJSmPgcs3Y5NE5y5iXEZPv6DE6iLAMuIoU8bfE1ZvHixIE4sXLgQzB3tcRUWAJNl6Wjj3wbm5uaIjIxAT7ov/kLWHPdInEg1NkYsWX0Y0ICM6cViHPgOexYG1pTZg 6HyWTl0bdPf8H1rUEl9xw270yD4dB1mBlY f5WqRVVHs4vH4FJm4HhizfhXV/g vb38f7EkSjYdxDvtCV yhzc Oc8Urzn44t1gdAriMHBdUuxfLIWfE5vQJ8ykwnTYZ/ghzm oEhC0LGie5X6Vq7uTJWPsA9GYOzGfPR/Yy3mdbSC8tZu/PftnTiTLAdc6piZMgNh 4/glutb2LimE8xpTCofK0hVOTj17khM3 mIVz/YgUF2WTiy9k0snfA23E99hr4mFSqzlnUQ2poB 49Ho3C0FVmsFCNqz36kWrWCReoB7LyxCIGBNJmiWFAV2I/zhym7X1c1sqmLh1FuvcdUx6z5aU6AE AEOAFOoJkQaKAFhaoQ8f/8hatKD3QK9oVZ5ae 9NDh/J nUeTbD11d9R6NNWe1lFRQZN1CxPVoJGcVCl/nYm1DmDv4wd/HGtrN UF0aRaizp5BjtdA9DTWIi DBvKvlsfjPdisBAo2dY1IUV93j7z8PBz86w MGzMeBgZsmX5/ fjTdVUPCX/36NELP/60FS  MBXGZC7doFK2eDcYvBYz29WweBcalMAy EUs 3IObEyUuHtsA avnoX57c7iuxBzEhPUi/dU3wXY/GoQ9LLO46u3V Hd8x54ftFSfOWrj SDH Dt1TOxoutpfNhRj2Sw2hfV3e9 hpnv/AG7Nz7Hrn72UKbGItPFiosTDXqDeeV/M4EtW7Zgw4YN2LFjBxwdHXGcLBB27twpWE3Mnt0wN4mH5Xgh7LwQW4eJDCwzBws1UVCYD3t3d x/j2JlkEjhTp3Q3hnsLmbQqSO0hw2FQqmAo4MTubo906ghKFKvIqYQcOvuDf0avoSVGUew pvbcJ93FB/N9IKMeurZxR0F4X3x6epjeOWHEGiiXhh690S/3oHQQU8EO97B4Wd24LcbhejTVj08mbkbfHx96by6KCoJFKrMY1jzVRycXv0Dn7/pL9Qp9UyAFQkUDSlGvr0xoBcbg7oo0/ZhzdYUdFmzDwuesxICcfqvSsKB4A w7VIe vaqFNJS14OsRCT46fI5JCmC4VEagR17U E/dz2G/TgGn/14DQsD20Mr QLCs/UQ0M2ZxJaaS008erkdrv Yam6en EEOAFOgBPgBJoNAVVDg1Cwp/5s9LnRuHDZGN3a2UFHsxYpa0usawg9LSUK5Bq7xkc7XVVxIi6fvoJ0XSf4dnSGKQ2gOCcNWUoTGOhIoShSqMf4aLt9NK2V8RNp6UCbdvoFxVygeCRgmUjBfL2ZSHH27NlaU WFh19GQJtApJGZ7fGl7wr9e77zDhwmT0IO WjXVLQpmFxQu/a4Qr7d3br2qKlatcfLF 89fWFQw JdfaEYRn79MNhP/Ve7VmaI2NEXW4/fRjEJFBp/a0OvHujTnS2cO8Lh1q848rEnnps4HD2Z3tJOhtCd43Hqn3goOnpDkl77AraLdiKy6Flqn2490CGAiSeB1c6BH QEOIGaCSQkJGDUqFGCSLF06VKKPSnDypUra80UVHNrjT/j5OSMtLQU/EkiLBtDQEAb5BfmwdrOFoETJyDr08 EDTcTAsRDQqAYMQyKUgXs7MlyqpHihHq0KvUXLykiNd3iiu cQmSJFQb1cBTECaHInNEz2BxrD51GfDEJFNU4EcpsWsEGXyM5R3CyqLMU3zmJ63ILsnjzKBcX6ryoHhWK488ipqQEqXPbwnHu/RdoJxeQK4dhRfYQkSFa9/EAloeSADEHdnE/4rfMQCwYGIRgVSu8v2YLLr7TDj7XQhEr8sEMnwrrm7qGUplHg8ZUV8P8PCfACXACnAAn0JIJ6NlAP 0CwmIN0dm90ndy1TkpC5By8woib6eioEQEmZEd3Fr7w5mCWmeG/YVz2c4I7uUHI7YmKUnDpcOnUeDdF11cmAWGCsUJJ3A0XILAfl1gU7agUealIKtUBqfOXdHaQkmp2xUoNbOArVgKMbmnCqXGfinAN1mBJF 9iKiUbHJlFewvoGNiB2ffVnAxk5WtrZTIjzuLc5FpKGJVJHowd25FFho2akFGVYTUG5cRdTcDuUIFLZi36Yn2jtooqO069eiQe3kPfr2s/sM0aBA62ZD5PrWZFkWsbiUjj/xxtQxs4OznD3dLHfWYauxTt8b1YFl3j/RHs7OgYLM7deoUfv31V3z77be1ihNMkbscfhGjRjyPY88Oh/m9ewKcG//3rlqgyMm DxaLU6EpLBq/NwW6  XXHega3L1hGw/ql2lRYknVxXsxrq0cgrEHu2PL/iUI1CnCrX2rsWTdLpyNSka 1BDa5MkhK5TXoLrRB8 VnoUWpiKjiHpg6ofMAs70aPRcRoFgXlRSx6JaZ9grmNPlIJaPCMbFEVMwbdoLGBpowS0o7vsk8D84gZoJTJo0STjJ3DkGDRpEwXfvYfLkyXBzc6v5oiY64 Xphejom jQoQNlJpJATgEvZVrasLC0QIde3XHRQB9aN24ikwJkxtH9yPzuXbRt1w7PDAp5qBFJLXzgRN9jF8/EomC8jeBC8qiKSCIl2zIlSusp6KvIl1JJX xaNL9qi0gMCd3aS T1EzzK2xDu44Z4Zv3PmN9GY1fBzoqhZ0MWbvd1pgXbbn3goPwBh26kwGL7PuR2XI6 1jKYDZyEwHeX4psz8zHt8DWUeMxCx qUmWoHT8FNK/No0JhqaJAf5gQ4AU6AE AEmhGBhltQqBcIIkNvBAfp4OjxU4gw6Q0/M9q23meNQd/jKgUyr5/ExUQ9eLQPrM4GAAAgAElEQVTrAyejEqRcPYVr567DuG8ADGxMIErKhpzWTuKSIijy03CPlgvyLCXFsRZBTsJDbio90DYKhL2FAUQ5uVBQ9yJtI3qQnIjU2ARkaZuQKKFZtJSJExTJqrZ TSBHTnoGiozboLMv7cNK85B88xIiT5GbaY9ucDVQrzJkZi7w69QGJgYSFCZdxYUrYbhhNRCBZmKolMXITibRxdAfnTrZQFdEVhsmzM00FyW1XVe2y9Tz6o2uHpSCnv7T0jeGtjwDieEncCEOsPPvirYWEuTEhuHy2dNA9 5wN6Qx1dhnHvKbyFqluo9qNc 3qqv2 I4xcYLFoPj888/Rtm2Z/W8N3cfGxsDC3JJ8xQ3gQ9YT2Rbmwov9zgr7B2FoYIiYmGhBgDA3t0JsXIwQPK6UzKYN6JyJsSlu37lVQw/VH5ZaesORFu 3TtPi/b4q5K Ul4HM9DyU0OdYHvExJs34AnfavY6Nu//EwR0rMcK2 jY1RyXaLK0eLd41/kIiKciSCCpazQv/NMoXsAdw9OjRSq9QfDGYFtW6vpj18wX8vWUOWid jzkhQRi66hLy6rkZqH10/Cwn8O8gwESKFStWgAXHZPeOGTOeTB4GLS0t lLqgqtXrpI12XmEXbiEK FX6UtLiaKCQgS2C4SytR/STYyQSFYfZhSnYvAzQx/6TRIZdcDk/obI3k3uDuURIO9vVtupM7ykqTh5PJ6 hsuK/DZCT2ZAy6cTSOB/JEVmFwAHpOL0maSK4JuVW5aawIFE3JSr8ShowH1O27E93MS5uHZTBCcSq1lmFvXLAw5GD2r32m790dWUYkT89B02/KVE7 m9YEHfoBKb/pjWtQRHNnyL7SeyYde7O zp 6ExpaFjakwf/BpOgBPgBDgBTqBlECCrA1t/tPXURsL5y0gtj8BdMXpVcQpi7hTBvG1PtHW3pn2fGZxa 8KIsoQlFGlB19SWHkVkIzFbRQ8zyFoik6wVaKdVmpmAfBFlJCPhIC2rBPoOJAAo5eUPT0T6LmhDgbklccfx18FjCLseh7T8kvIHzHX1Ky17pqJl4gA7azMYm9vDq2NXuOvl0L40T3jIzdLAS42sYWVuBD0dPZg6 cBZvxTZGUpoV4q7oWXqCHtrYxgYkXsJWWYU0yazPtdJdI1gqKsFKT3FURXloqAgBdG3CqDv1wfB/i6wMLGAg38neBvkIjY6lx6YVDwIerDPpnGlqelz OAqrKaaj F4Q8QJNpywSxfI5DkQJWSmy1w62Kty0ZLKKDicLUWxD8XvB/YJp5g4waLJy2jhX1pagkC6nrmJuDi71nuGbPE qZ8Bju1eiW2zt Nlr8pP3yqayY85jVgEYN1bE9Dbij3iM4Ani2T3EEW9gN2iXlSP8qre5FlsAPc L2Nl77F47p3eGPn1ZoTP3oDg lsdP8QI aWcwNNBQGNJsXv3bri4uDyxSdlY28CGshOxdKPMzSMjIwMH/jxIgTP9BOsOLy9PGJsYw8zMDNOnPSIhRWyGPkv/h8Gn52DpoMG49MoUDAywhz4FXrp15RziXGfh3ef7Yt6Lzhi2agre0FmE0RQk89pP72NtnAtmftwbZjUYPDQUpMR6AF4dvAzT/zcdi3TmY7iXGLF//oSb1FAn1pjMFYOHOmPdp29j3qeLMCbADMq4K8isoyOxZX/8Z5wNxm6YjJck8zGxiyO08 JxM8MbYya0g3FV V7PDyN6GWH7rk QajEOv3ahpzKsD7EFer/UH7KJn2EHrDB5qGet8SdqG1aDx1RbY/wcJ8AJcAKcACfQDAgoKIZWgwq5UJRbWdK WM/RH57pp3A5LAHd2ojLsoDRM9sSBcWFSKeHsCrIz/2KHefu70VSSJYDZiawMijFnXiyXPAtQXpSAQy8/KEdG4ekAn/Y5yYjrVgXtg5GtInPRnEla0xtK190fqY1FCRmxN2MRFjoDZi4tYO/qynEdfQr1SHrT/bQhF4qRSEK81nMCjHFPaT9ZxYlQZAYQ0XruoKUGNyMS8I9SmlWQg lJTRfsUIJkVhJlqHqLBzlbRRo4l6UorCu68pQqBRFKCpUR wuvZeGXJU27B0MocrPQk6Z4GJgLIOShBuF1BQiGud94y7vs0Hv4ENXblYCRX0tJzSzjouLxWAyZVaQ2XN1xcrKUjjs5sbCyFUUmZZMSElaShHuWRC8/X/8Xt3lNR8Tm6MfW7yfeY0W70No8/8ingl0gL4yHecjcsqv03NuR0/ NuHzj7bBfERrWEgScSuv5mbrc6auBaxewu/4LpQi beizURxAo5HkNsLqXOGzeqdrs9MeR1O4PETYG5gTAhgqT1ZYSLFwIEDHxhIQUEBJJTa83EWzZjO38zEV0fyMFkVBRcHS8i0ZTAyNCJLi074 ecfabzPwMJCfe97mPFJ7Ubgs8M2 G71Onz/3WLsyWYuFDKYe7THwJfkUIoM0H7RTnyvvxDvffQydjELSa8BeGPLB3itHTMpfESFBICBa3dgxZJF2LBiKrbm6cChtbNgsihmUUNJDvB7/Tt8lP0GVqyejd/ZMKXG9FSgOwIsajFlEBmj /t78I3FEqzc8jamfkwXSs3gM2wpQsZVI1DQM5g2z/eC4a69MH5 CgLLBV8RjDpNx3Cr37BF2R8jfDTRhRox/waPqRF98Es4AU6AE AEOIHHSKABxo3lo6p8jUqsDzs/P2ScvowrSX73rS/U9bRg36U//JkLSKUi1dOFpFAXZlb6iL57GwU xkilNYRNe1fop15DbIocNkUpKJTZwoksMYvvlVZxwVehlAQLsaE9fIJd4ErWFKHXriPZqSfUudFq6TefRbeoKGVaBVRs2aIiAYIeoqvyr HyldsQOQWiQydbGEhyEfPPcSRQHWa9q7lG04rmb2VeXJ3XVeagGYf6J62dSOKRy0vL06YLx0nkEUnJip/6rm7cldt7HL83m20rM2Wuj1uHBgqzmmAuHGxDoaOjK7yqK8yto6ZSVFQotMGECoVCATaG hap/UhavNuqF 9f/xe7hMW7FIa27gge1BGWRFa79Vxsfi8F89cvwqTv1f7ROqbOaO9uTD7YjSx1LGClaeHY99Em/B/9o2PjsWg9GEs2zkWrR2Ru3chR88s4gRZAQISOnTpj bIlwj2htsLECVb3cZf9/9zAe5uP4j9TB LYpRjcuZcNd7MUdAwKQFLiXbT298fBPw gdas2gnXZwxYtq2BMX8VeNbSkZYu 876lVw3nZb5YcCoRCyqdFpk/hz2Jz5UdMXrgPDuh5TITRxJnll8lJv/LyR/tpZf6kPzGavTuu5VcO9RfYSJdT4xe Ru9qhvHg2MoryVzwID5X9OruusePGbUcyNuJG588IRee3xwMREfVD1Tdf5V/6b69/OgAw0cU9Uu d cACfACXACnECzIlAev6Geo2L1y3fn7HfaPOvYwMsnBWevXRNi8qkN0mkfqG0MPVE8sul5rNSsBEXMx76slORQDAgyxdC1soFebDxiyIrintQa/iY6UFnpIp9CBSRQynSZXWey ixGTgmZL1TenWsaUpVAUUj7OH0jsly/gxyVPrwopkOt/ZIVRHkR5kMvCqqZna2AyNACehIV7uVlUqgAE7QPagU7iiuRVyCheFvqqkL9ymPRtEGNlubXdV1FbC6hiTL Yh0TyswWj9TkfPjYVYwpM0sOsRHFtqC 73OVrdRnxWQez2/NRqDYunVrnTEnKiPJLcvQkXA3nsx2blEqvob7xjBxw8nRRWiWmUqbk/82U6zqW pcvLMnblM/wR/0qrZUs1g1GvAzEhIr1ZZ5480TiXizcgO1LWCDFmJ32MJqu MHOQFOoGYCzq6usHd0QMjQYTVXqnJGSmrz4yqnwm9j2abDeG3qIBw5HyUEcMoiS46friRQ3JvD6NenhxAzw8 vFRLu3kHc7ViEUDyKhgivj2suDeunGNG/fIsTEle42ZlAkh2Bfes34JbdBKz3rl6Yblj7vDYnwAlwApwAJ8AJNBWB6vb8dfV1396cKpNEAW1rb3imZOJGeqnwpF8o2pRMwE4Hl68fxfkSD1jqU4aMEnKdUBjAxs4YLBaESNca1voxiLtKFrIe/WEiViDHgjJl3IxAFPTg1skSInLvYNqGpt/SnFhEJpTCyNQYujLauSvykH4nHkUiU3iTS4RWiWXt/ZY1VJQYjgg9snYVlSAvKRpxBdpw6mgP7VKKYqhrQoLHbURdjaTgl RXSvElWGYNTanKjf3NXuK6rhPrwJhyxN NuYxoAztIivJQrG0Fa2MLuDjq4WI4ZSQr9YCZrBR5d6Nwq4AYBDtAVpJHLiAV/bPfNH3ef7Tp/2o2AkVdATGromBZOB5lYX7dzIe7IQLFo yft8UJcAJPnsDjFBwaOtvNv55DSP/2 PtiLD1lN0bpvbv0JCERHuZFFIW6FKGhf5M44QcnJyeYW5ghLjYOv 7eiTHPj21oV82rfmkO4s7txSd7riIpl55gSEzg0WMKPvt0AYJ4XJ3m9V7x0XACnAAnwAlwAg8QqLrVfqBCHQfKrhfpwJoCWidnRJTVZ8elMPXqgLYGcYi9dRVXiumYSAYDu9Zw1KVtbhHFbRDrwtrRGHE3SuHsaQlxcRaUOlawMYhGjJgCZFOu9qIsFt9BM072GwWXlKchPvIWhCyh1I uqR18e1KAcIppkZcuqb3fMlMEkbgIyZGXkE3ZGcW65nDpEIwgOykKs4oBQxe09i1FdNx5XIhS9y3W0oOZIUtDyh68V ZWIRWI67qO5m/pQ3HKrkfh6rkEUjR0YO5tDSdyezX2CEJb3VjE3LyIeBJDpAbW8AwORgA5HBRmFlGv1fdZxxv0yE83G4GioTOTU8AVTdpQFyfXhl5eXl9J5iusnWJK08cLJ8AJcALNlYCthSHi7qSTlYc97lLmofCbSRjVxwvuxpmIjLyJixdO0n1MjsTERLQJ8EerVv6UonSX4MbWooVXiSX6r/ydXs31neHj4gQ4AU6AE AEOIGaCJR5GNR0uprj2rDtMBBu5Kavpcq639tBxx4B/bxgZslSghaovRdE2jByaIVO3l1goKcDqRDkmoJMFuYgu5CCPjLrC7sO6ONhAQsjID dpS/Xg0PHQfCimF2GylxkkPlExThFkBg6wKu9F2UF0Ye2TEoxr1ibFBaAgk7mZ5KLBfPcr63ffLW8oG3bEX3bUVBKEg3YuFSlchRmZyCvmEkBUujb pDrfyfqRxdaZcG5VZRpUkFuHCqK9eUSPAitKUOlpDi9Eoc6rmMaja4tvDq5I8jEELrqjiEnlxK5nFjZt0Zn72BKHEGsWMwJSr9akJWJPDm7sKY q3mbmvBQixUoWDR7lnljz57dwgK8sYUt3J2dXKCtzYM0NJYhv44T4ASalgCLiTHt2UCMf cXRETHIyc3H8O6UQaNYEdkZunR/UsPkya QKmTDXDt2hUc usQZfYwgSV98TLrMHa/ZEE2W767R9Ny5q1zApwAJ8AJcAKcwKMm0Jh9WgkKM 6isLqhUGrQzOQqWQcoTkQxbcCLa0lGUFqQhhTyrKgoChSk36U4ENUXlSIfOVmkNNRWauy3Ys7K4nvIytFk4KjamAqKgixk0qvaolIgL 0uHpxWHddRY6oSGn86vR5ouA5WNfb5QENNdqDFChSmpqYUVKQjAtq0fSiBgpFli3YjI6OW/ZSxyT4ivGFOgBNoDgSszQ2wd/VoHD5zk/JWkJ9gVhJOnjoBCSnjOjo6OH3mpBDc08TEFKNGjkFySjKsLK2EbCPsPBcnmsO7yMfACXACnAAnwAn8uwg8xHPklguqTJ8QftD/hHiTLXc2j33kLVagMDQ0FKweGhMcsypl5uLBFu8t2gy66qT435wAJ/DUEGAig76 vvAaN7R KUSdnZ2fmvnziXACnAAnwAlwApxASyXwL9yaU2pUly4D0dqS3DOK0uiN xcyeIiPa4sVKKRSKdiLF06AE AEOAFOgBPgBDgBToAT4AQ4geZH4F9pQcHeBnKVyE1JpASivDSUAN/hN5QYr88JcAKcACfACXACnAAnwAlwApwAJ1APAtx6oB6QeJVKBLhAwT8OnAAnwAlwApwAJ8AJcAKcACfACXACj54A1ycePdOnvEUuUDzlbzCfHifACXACnAAnwAlwApwAJ8AJcAJPggAl8HwS3fI WzCBsoyrLXgGDzn0uIv7Ebr9/YdshV/OCXACnAAnwAlwApwAJ8AJcAKcACegIaCtrQN5UbE6RiTTKfjrX8FAXlwMbcog19jyVFlQlMrzkRl1CGlXdiIv6TLk ZlQ0jEtPRMY2AbA2KUrjBw7wMS1OyAS4/qRz1EQdxDatgMby49fxwlwApwAJ8AJcAKcACfACXACnAAnUIWAI2UUi4mOgpunJ2QyGefzLyBQolAgNjoaTs4ujZ7tUyNQ3Lt9GhE/TYKBfQAs/YbCtf870NK3glgig6IgnQSLi8hPvoo7oWsQs38h8vT9YS7NQlxyIUZNndFogPxCToAT4ASamkDa7UvYujCo3t0oLTuh1DIYEEuhb2IDqZYOOnXsjICAwHq3wStyApwAJ8AJcAKcACfwMAQ8PL0RpbqBy2EXIJfLH6Ypfm0LIcCEKEdnV7h7eKGkRNGoUT8VAkVWTChu7poFr fWQt8mEMySIu3qHrKk2AMJmRZZB46CmH5qG1vBdcASHPrmPxBnXUZcVjZ6Tv8KIpGoUfD4RZwAJ/B0EbgdF1vvCbH7hpOLa73rN7aiRpx4 bM7SI/ GwW596gptT nmG5dYvY/KhL6wcYkor9/PZONQGcTODvZY/9n09B6/Gb8 dfBf6dAoUjA3vfexWGPhVg92R1aVf9u7BvDr MEOAFOgBPgBDiBWgmwDaq3jy9atW7D91u1knp6Tqooryx73x9GkHoqBIrkc1/Dpe98iGW6yLt7GkkXfoa59xAEzT6OrJijiP59Hpx6voK0m7tw4fuluKeygbGBEfJKixC1byFcfI7Qor6FoSjNwMmvPkWo5RS89ZwztJ6ezzWfCSfwRAjcjovDRVL4z5w5VWf/EokEHTp2gp2DA6TSpvvXpxEnpq6 hEKyArv 1ydIT4oTxiehCELm1g7QImVCSi9DEyvhp0rHEm4ufeEb1AUpsWEIHLkKSdcO0LFuyMm5ByMj4zrn98gqFIZhcd RONhtKw6vCobhwzSszMOtsycRa9IZvXyMUO8ASnSvvPD7AZwcNhdK1n/Vvx9mTJprH U8H8V4qmlDmXMJXy14C v3RSCLQFgM/hJHPu O3HONYFpN /wQJ8AJcAKcACdQHQG2UX2YzWp1bfJjTzeBeq/xmjOGTBIhjGnxnRW9FypVCUSk3NxXmJJTKsfp0DDkyrxh03ooYqKuoMvIebC2s0XMgYXNeXrVj600Fce/2YQdYVkora4GWzAHu6Lj/JPIre48P8YJcAJVCKhw7twZLFm6HCtWra32NX/hYnj7tcGiJctw7uyZJiWYn50kuHW8uPoyeWrIkB53FiVyCjRVVkppk1lYkI/8/Hzk5uYhKzMdmfSKSZFDryQNhroiWDn7QZSfCFef9rh9YTeuhh2v35jlkVjT1R6eLx1H3n1XFOPKsg6wb/U6zhTUoymJARzIxM/D3vjhRdTCcKye8iKWHU6v/p5Xj HUXkWO6x90gb3zGPyeVXfE8ewD4 Bs3wsbYsl88VHO84FBKnEv7Gv8Z1hHeNrbw55ebm37YNLyQ0gteaByDQcKcWnlVLx7zBrTP/sZu3f9jA1zOsK4qKmZ1jAcfpgT4AQ4AU6AE AEOIEaCLQws4HqZ2FkH4jinAToWfqiMOMqLNsMQdL57Yj67Q3oW/nAIuBZnDu0FwqrHnDyD8GZba jTZAvZLmn4dJ7LrmHvIHUyz/DKmB09R3UcFSZdwN7P1mNL345ivDkIqqlDUvvjhj4wiK8M9kfhk/Sc6RJF8w1AOGHOYEWTkCpVEJXV7faWdy5cwfjx49HHFlaeHl5obS0Wmmw2msbc3DzLAe8sOoiWXdpIXz/h2jTfybs/AeTCKskazH9B5oUS9XjPnLiPFoH KOwsAgXDu9D9MV/oGVqAQvH1jh5cAuCew154NomOyDzwozvD6JlRPmRwaE9BfEquY5z8cUIMS2LPl10BR9OeA2nOq7H1gVtoKZcjPhz0Sgx7IS21mRB04TzLE3di1efX4xj9s/hrTXPwNdUifSoC7isNId fb/BFXdx8kQKLIdtxoyhQWVzoHc9v8need4wJ8AJcAKcACfACXACjSLwVFhQ2Hd9DbcOrYKuaRuY 0yArrknuXS8jNaTNsOh 4sIP3cCGQpTOLUfi6v7lsLF0wWFOq549w97bNoXBeMe7 Lmb29Bpaz34ygos09g2ZC mP3pFZiFvIW1n2/ChtWLMCXYGFk5Ymg9SXGCfRTKFszb5rZC45O8NOozxS/iBJ46Ajk5ORg3bhxu3bqFRYsWITiYAlA hpIUfQ4JN/5Bq94vQZkeDhUJsOxVevcUShL/QUnC3yiJPwbFnSMojvkNxdF7kBAdgb8X/B8St/4K8cyFaLvxADxWbYPx5z8DWtaPdtQlidgzbxi6BXgIT/bt7R3Qqs9L OxcttqdQh6BlV3s0W7xJTAJlwZde31lLsK/mYOB/o7q9jw648Wtt1E5xFLU/7rDpcySYOTvLB6HAjFfTkB7d7V1gT1dM/q9g0hqRFwmXfcucEUSLtzIUY fWi K3Intp2/izPafESlMgoryHiIv3AXcu8KN3WAbOk/WhjweB/43Ed282bid4D9gFjaF3Svvt6wnFEUfwrkiM4xevQpzx4ZgwMChGP/qu1j5WluUy1SKZBxZ/SJ6 6oZ PWeirVHUyq4qeTIJ ObtC3PkjWLuk73dVHl5 9nmoDjM31g3/F9XNUY7OT jZe97DHgm3iovyWVSPn5WTg4j8ZvGfLa Zek4q/3JqFfkGfZZ8QP435KVLdTTwYaFvwnJ8AJcAKcACfACTz9BJ4KgcLMsx 8hn MlEs7EL13HgXH3AcdEy/cu3MQf3y3DNkKY9h3mIjbf2 Atq4WJFZ  OxSR7w0aTQs3TvjzzhbRIh6IedOPU22Vbk4s2I2Nkd54bW9h/DDslcwZmgIho bhtff/wKb5pSJAjUuzOpYUJfcxW8LRqJHoGbR74qgkNfwxemMB0ybU3ZMQwcXtuB0rH1jwD7LilSErpuOvq3Ui3/ngCF4/wI9QqvHpuDp/6fAZ8gJVBBgbhOVy LFiwVx4u2338asWbMeG6o/N70M9hKrKlw76upcBRHu5hQiIy8fcQYGuGNriyR9AyQXFEFEriKPtChzcOOf80jxnoMvftiGLZuWYYjkTyyf/F8cu1eNm0Qd9eU3PsPMd/6A4ZTPsWv/79i5cT6e72h1n3uIw7RvcODQIRw6dBgf9TCg6UhgGUyuH1/uxG/7duCL2e64 vkszP8z44HNfl1z17IOQlszIPp4NAqFysWI2rMfqVatYJF6ADtvqI iKBZUBfZd/GEqqabVOuYJVQ5OvTsS078rRMgHO7Dv142YYnoESye8jaPZ93OT2fjBHpk49uNh3C6qhqkqD eXj8CkjyLhN3cTtm3bhDm EVgzcSRWXrz/c2w67BP8Xsbu 0nO0Bhg3M/UBn6D20CaeAqXM9VWQsW3j MyNRV9LLLM6CIfkYcjofIZjEBjae38lRkI238Et1xnYePWHfh5y1rM7kHxUhrAoBrC/BAnwAlwApwAJ8AJPKUE6msg2uynr2vuDs9n1wnjvPzNUJjnp9FCLJayeLSGe8dpyIz4DWlJkejevyukeoYoOVOMEzezUayUQEWm2k7m3ZAReYBiWXSte66557B5ZxoMBq/FzHaGtB2ooZQvzN7CxjWdYE6LVpUPLczKF9RzYGOixN1jGzB/NS2o253FdyHmENPTuet/U7BP7/n4fG0A9AtuIfSblVg28gqyD zHgjYVJuja3qOweHYXWCvj8ee6xcLGwOf0BvSpaqWuykfYyhEYv1GBwfM/xqIgM8hT0mHsqA35jTXCpsDuDdoU9LOHMjUWmS73bwpqmCE/zAk8dQS2bNmCDRs2YMeOHXB0dMTx48exc dOwWpi9uzZj22 r28rRfbda/j2rTYkTGpBbNFW6Ftzv6m476g3rZqtq63zFfyWuAsG5IYSRUKL1b17sKTrnMeMhrJd9yYZv6F3T/TrHUjWWj0R7HgHh5/Zgd9oM99HPeQH qypfmdlIrJgjD7deqBDALu3PpgWVdfaA76 bveJFkZ /TDYT91Nu1ZmiNjRF1uP30Yx3U r3gofGEzlA7oeZIUgwU Xz5EFRjA8SiOwY28q/Oeux7Afx CzH69hYWB7aCVfQHi2HgK6OZNjX82lpnn2cjuMNVtT0GXNPix4jtJhUxP q5JwIPgDbLuUh769KsKJarm iI2rrmPaf2cieJ8H oyZhBenjkUvNwPhOmXGEaz 5jbc5x3FRzO9wCSonl3cURDeF5 uPoZXfgiBedkQZeZu8PH1rbCqK9MvqjItbTcEfngXf4TnYrytAVLOhCJJJEVp J IKuyH9qIYHDqfB9cJXWAjJYvBevA38u2NAb3YZ0RdlGn76s2gZsL8DCfACXACnAAnwAk8bQSeGoGi8hsjz0vGhch0yFyfI19xb8SGUxrSY9vR 9m sLUxhb6eNlQSbfx1NAwODtYw0hZjcn9LpJ/YCLeB79f5HitSryKGHqS59fSFQY3qREUzVRdm7Ex9FtSGXj3Rv496QdenTwBE5Du ac3fmPHtQJiUNW/S5hk8O0Bdp7NdLP585udqNwaqzKNY/WUcPOYdwYa53sIiVlMKYureFFSqzn/lBJ56AgkJCRg1apQgUixduhQsp/PKlSsfe4osE7tW6DbuA3z73271Zq6SGsA9ZBxyj51GB4qp4SQWw3jCeFxs5YtxffrVu53GVtowj/8AACAASURBVJTZtIINvkZyTv1c5irX1 v2CuZ0OYjlI4JxccQUTJv2AoYGWtQRYLMIt/atxpJ1u3A2Khn5UkNokyuGrFBeloy1ATMRGaJ1Hw9geSgJEHNgF/cjfssMxIKBQQhWtcL7a7bg4jvt4HMtFLEiH8zweTAWSE29VZ5ncfxZxJSUIHVuWzjOvf8K7eQCsvwwrMhSItKF1wTK2PTcgv9n7zwAqyrPPv6/eyU3e 9FCCQQwt5LlrhQHNTxqXXVftYORa3VT6sVqdU6iq1oSxVXHcU9EcUBMmWvDEJC9k7unt/znptAgOwAGTwvHnPvOe/8nRO47/8 A5s/ehOvvvw0rp26HDm/ehmv3D0J2qKNOOgKx/xpccf/XlcnYPqkEDy19kcU20mg6KatpCJiKi5Kt Nvn yHZU4Ktn5ajIw7fwvtyv/gqyMOjFR i/WVMZg3N5HuTc/4d4tBe1D5PBNgAkyACfRrAiK2V0FeHsrLS2GzNlsh9usZ8 R6S0BLsdwiI6ORnJoKOX0G7UkZdAKFy9YAsywChwpKseSqa/He  8iL3c/Js bgqioUBgD9RKnp64sg5/Wiw9 KkFUoAzJCXPx06dlXWNIWUHEt5VySul3oj5hx97lF Cqz6di9ScPIrvde9KDD3T6dMyfGIgXN2xCsYMEijaEERWZAkdQzo62Nga2og3Y7wzDvGnxJ4gTYsH67J5sCrqGimsxgYFG4Nprr5WmfN9992H /PloIAuE6667DsnJyX2ylDEX3o3v37gX86/8Lerzvu7SHBzePdh /izY5p6HPKUSHqMR19x4M/T6Lm6oZSpoKfajw2w9yU3CDWs9fcBQaduNsyNTCBsxD9xteCO0NfkT6usycPtb2zDvm9ex8m8rcMfCZ7Hyzvfxzt3ZEM4cbRXH/mdx7a0vQHH1Y/j7EzmI8Obh37fcjo/aqtzpORWipsxCrOdVrD1QgdD/fISmcX/C7Ag1guddi yHHsaqTUvx86/2wpV6O8Z1Y d/wjqlf0P8seCZt7B0ROsoQXLoI8mKro15yvVxmHDF3Zhw S9w8zOLcP4Tv8GKhd/id23U7fUpVSxmXZCER1d/gAMVM/H /kic/ hFCFr3LP69/gguV36Ew2FzcWEqWeDt/3PP PeAQa/XxR0wASbABJjAWSVQkJcLC2UcmzJtBgzkdspl8BMwm0zYtWM7CvLzkJo2pEcLbutzUI866i N6o/Qt0nyabjggkvww4ZvUVlZhlFZYRTMKw5hYQGUrk8FR5UF7r ugfO17/DzkZW4dDxFU5PRp mT05O2syhlWDri6MN74Y8FODHTnhdOUw1qq01wdfDhvOUDdVHOr/H3977A528vx6VR7QzW6rSMBBGK5NnuNDvcGJCCKXzT29A1gOZNwber70BmySu0KRiNC/ 8A6YO1tD5bLkGExi4BIRIsWzZMojgmDKZDLfe2vd5KNQaPQxGytzQhSMowICp4bvQ6G9AHSkN193yCxgMXRQnxG1ThWJ4mgGuXR9he tYEpZD Oz7OsiSRiOmI9 G3tx6OVmAzLoFy98l15rrQ7H7Xy9il/iLVq4hURmw1AkLg PFnP8jCjASv7zraswcNRzDRmQjLeDUCXilvwOPl5Pft1zRJM/B5KAmbHzzZaz40oOZN81AKP1LqYicg59PdmHdin/jPz/UI3rmVMTQvwM9KZq4MUiWN2HvIRniyRVHZIXxHamINXbyvYHMD0NnTUE0BfPcW26HJn4ChigrseG7YjhaJuM4gvUbaqAaOh7kxdd aYcpPQBIXngpkio/w79fX43tAbMxOykWUy5MwJG3Xserbx5E2MLFGEr3o6v8T55Erxic3Bm/ZwJMgAkwgX5JoKy0BCNHjYaePoN4hTDNx6BnIO61uOfi3ve0dPJJqKfd9l27r9d/h zRC/HTT1txcP8eDI8uR3SYEhGhfrTRIH9dlwd5v/4EOcuegLegAJt  zRGvXQjXXDC08UsHjLjWFx7nh  eW85Xv/lfyi6effyZLR8oHtafKAOp0  Lr82P1CfQNFZjA1b6qBMbd4YdDNCvfgwmKJYjR  LYIj50QXD2mclk3BzKuw6A8zcZnYFPxyBSZ1Y0/Td3edR2YCp59AiyXFe  9h8TExNM/QDd7VGsomoKRIjh2sYhfXQp7Q6ImaZA6n VYF5tSNSPG33EjUj95DjdeocBvf34ekpXllKL5KbxUEo4lT8xB2BmQt51FH Pl9UDG8BgY7JRNYj9l6TBGwF/8S6WKw7g0JVa/8QReHHUjhqMUVRHzcWFCDmKxEv/46 sIuTQToYoSFJparVRhRCQJFmXr38PXucmYl3jS 7RW7hSimX4YLp1hxH/WPIfK0CX4L1muScKuPBQzb54D9TXP422E47oL0zqMP9ERa3nYHPxmSSSuWnEdblYsxTUT46AxFeNQTTquvDoHAa3YWnY8hd tsmP01Gwkh rgrj2Iz/ xCqXyEfhFmg7ykNm4 4YEXPzn6/Fb7f24IgPY  ajeOpwIm57diaC21Slm2enaZvp4jFBUCVfhCvSnsTyp9Yh5talSNNQHJR5lyL T8vwAoXtvPUpXywLWWf82wHRHQbtdMGnmQATYAJMoJ8TsNvt0Gp19P0qf vZz2/VaZ2euOd2W0vqs 53PagEiuKjxbBoEnG0pARHDu9DdkIFgunz/Cb7DmgrNJgUkgn3nmqkzF0AxY4dIP8PhNW4YDpghzooH/rQlK4RlIfgvIcfw/mbfoWH519AG/kbsCA7FgZPNbbuFzuCjou ix/oKj59Gk nXYaxsV4cfOdx/KUgHFc/Pr3jD5ztDC0nc9zfLonCFU9cjdvcS3HV2CgoG0vRlLIQCwzr8Up7m4J2 uPTTGAwEhC clbykdSR/5woQqSYN2/eKUu1WCxQKNpK33BK1V6dEN80CCsOUVQ6A5TdECiODyxDTU0NgoKCuuULqBtxF955OwB//NNLeOo3b1E CyVChtHG t8P41fTA9t0Q jVYqmxo2oXPvrrSvxfhbAFUCI083w8 Pc7MVyyAginjBfLsf7Wh7HslrUEJArT7xuNS265Ey8 UoGlz9yPa1/xxb3QBiVQ2tEAcjUR4OJx2e9/jo9/swoP/usCzFiWfdL70ScF0vTHiMtnwH/NBwi4/HpkHxNpZTCOvwmXhH I1Z45uHRot8JvnohGFoCpj76PVaEPYvnqe3HjszRvZTCGXvwwFi5pLVB44JKRa2Llv7Fi6d9QKSVz8UPc6Itw/38ewHUJwoRDhTH3v4tXDPfhkb/egjVNpOkMob/vVz OX UY2raaa5mNvB2mJFCoVYm49MZsLL vBosWp/vEmPiFuHLoMjzivgY/G ozzdBkdsL/xJUff9dlBu11wOeZABNgAkxgIBDwOcYPhJnyHPsLAdkdt9/mfXbF31FbU92tOX38wXu49oabutXmTFV 44038H8PPQSP24Xrb7gWRqMe2dGFiAjXYUXlB5gz6iYcMn Nw/t3496YJci96J8YFREFJwUpK6WNhvGR38EVuhcKbSyS5zzU5Wk6Kzfg5b88jVc 3oT8evHBWAn/qBRkzbodf/nTYiR492P59PPwn/M xoZHjkcvB6Up3bXq9/SB gPsrm71gfqWf KVX2VA4/C1WyHLQbplJ/ZVuaGNnYir73sCv78kyRcFvblO6769NWtwyYg7oFm1D2/NKDl1bGcJvvzrH7Ds5bU4WE9G0vpELFz2HzyRtBr/c/NKbGm1Kbj9scdx82hyiekyDa7IBM4MgdWrXsLCiy45pfPT/XfQkcOHsWPHNmzZvAluyuzTURHixLjxE3D BRdBSW5jZ6o4nU4pBsarv4rA//zhLXhsnQugjRYX9pfaYPFokV9cJU0tOSkZxoBATBg3EQEBbfg/nKkFcL9MgAkwASbABJjAoCLQ3ueytha59vNPccHFi9q61KVzbo8btXW1MJtN8Eiu MIl39dUCB8KuQIq hymVmvIUoNcQQ2UAUyYzHPpcwIfvb8G581b0K15lJCxwYsrVx5Lg96txv2pclVVFZ5//nncdtsvUF9fh3 tfAHvvbMS/u4alDrLMSyZ0opSGrRq2QHYAyxkFFwH3ZKR2P36TpgzghE77VJYCnLRUP4VRv9yQ7eWpgqfhJv LI72mmXgno0luOfkyxQpfsSNz EzOjoqobMfwYethY3WldWn9i0LWYT3S1r EjCeOrYqBnOWrqLj5FHvw3vb7zv5JL9nAucUgYSkJMTExWLhhRd3ed1nUpwQk1CpVPD390fWnF/i5Uev6NK8PBm/RM64qYjQKWFqssBFdgSxMQlwuZx46503cfPP z6eRpcWwpWYABNgAkyACTCBAU gN84dNbW1JDxoKQtjdJvCg8gSIg43fUndRMEZDxcdRkhQCH1ZzV/GDOQHZ8C7eNxxxx2kqAFffPUVdKSc1dQ1IdLopA/2mZDVurEy/yUcVnwFt8wBu8WNsJAAaG YCNOUoQibMJ3MXzU4 N5DZEp8O7zqoIF8L3nuTIAJ9JLAmRYcejI9jUaD2Tc8i2nXPCm5nzQ1NVFEbAuEX6eLrMBarD2Ee4qSMnZ4KZDu0ZJiEmxdiE5MpwDAMpRXlkJD3y5ceflVPZkCt2ECTIAJMAEmwASYQM8IdDEJQVudN5kaEE3ihPi8c2qATV/IbGExoaQMYkEBQdJRWV2BwsICxMbG0/kz747b1rz5XO8IDFiB4rPPPsPrr7 O7777DkMyhsLlsCKvqBChwUYc eLPGHrpYwiJCsGVlHb0zX3vwOq0UwYPGRq8cgSFZsMYQwk5S3/Cke9WQxYxA6qUxTCR8iZUOi5MgAkwgf5GQFhTiMNIKUNbivjHuqW0NmkcMWJkf5s z4cJMAEmwASYABM4Bwn0Qp Am5IbiC9a3GQlIdIYSn8kTw9fZAtJtKBrwm3fZrfBoPcjF/8oaFQaFNG MCE qVvxt87B29MvlzxgBYoNGzbgtddeQ0RkBAry8tDY0IiUlBS88Po7UFR9g92rb0FY1nyMT5mOjIjpsLus2FG5CbHB49BYtAclmx Bk6I5yFOuhl/S7GOqXL 4S224b/SLefEkmAAT6FcE2M yX90OngwTYAJMgAkwASZwCoGeO3kI8YFykknWoS2ihAhCcUyokAJS A4VWZHW1laTW2scgihLgrA0PVpahLiY DbdQ06ZJp/oNwQGrEDxxz/ EYsXL8bBgwclH20R C08PFx6AD3hV8AvcSqa8r9A1WfPwWOpJPVNjliZAgfwPWTGJMpj9xvoI0ZKFhN6vV7qQ0S558IEmAATYAJMgAkwASbABJgAE2ACvSfQKwsKEiak9uTPL9lMSP81Cx4tHTdrFApydXW73FJKU7EfDA PgKXICpPZTMEz/Xq/EO7hrBEYsAKFIJSVlYVhw4ZJfkkiQIrwwRbR9cVD6XbHwZkyiq5Rho5mP23hqy0OcV3UU6vVkkAhfLyF7zYXJsAEmAATYAJMgAkwASbABJgAEzhdBHppQdEsSvj0CF9fx7WJ1n1TLAraz Xl50qZPRISEhHgb6SA4Y0kUBzLGX66FsX9nEECA3pXLgVFoQexLXFBnBPCAxcmwASYABNgAkyACTABJsAEmAATOPsEWsfL6u7oHneLO0ezBUVzBy1WFM1yBVnKCw8QL3R6HcWrcKO rh779u9FfHwCGstKEBER2d2hB0Z9rwuWumqYVSEI9VcJDL7irsP bzegInQCpmSFDLi0nQNaoBgYTw7PkgkwASbABJgAE2ACTIAJMAEmwAS6Q0CKPUHlmFuH783xLkiUMJstOHKkkL6wVpC7fjBCQ0MRGBgIp9MpWc3bbDZJvGg3bpfXjrKtX2NnpfNYv3K1H4Ii4pE8JAkhWnl3pnx267obkLtlC5qGzEVEIIU5IEFHKjIltH7 MAYGwZ/SztuslAXl7M6sV6OxQNErfNyYCTABJsAEmAATYAJMgAkwASbABNoi0BsLCrcUHJN6bTmaTQRkZCsg3PaFq4eXforrIzKzUVVdibraOgRTkEy1Sg29Ti81bQkF0Nb8KGgFXHYSJ4xZmDwuGmqPE7bGchTs2YctVWaMnZaJYMoE2T LT3aQqXTQKkiscbUIFH5IHDMD6eTaInObKYTHQJInMOAsPvrns8GzYgJMgAkwASbABJgAE2ACTIAJMIHTRsCXxUN4cMjglfk22ULwqKmpwdGjR5GWmkZ5EORSTEGRtSMyIgq7du UEh IeIPC58HtdnVtPuoghIUY4bI6ofcLQKDBjq/XF6DImoNwfxPKDuxEbmkNmmwkiECFkBHTMDpWB5nXhqq83ThUWAET6Rwqv0gkZGQiOUzrc7nwWlG 9yfkVTTAbBdt5dAERiFx6HAkBKuPu2V4LKjIpX6OVMHikkFtjEJSZhYSAsl1g6w8qg62MX6Ub2lNO9/Hf3f6XgflzMO4cCtyv/0WJeFTMHVYIIgEqTQd9e iLJe7sTe3FI0O4qzQI3zYBGTH6Y/Pr2sUT0utQWdBUVxej/2HK nmViOvuBpWesh0WhWSY4MxNCkCw5LDERsRcFrgcSdMgAkwASbABJgAE2ACTIAJMAEm0DYBp8PR9oUunHWRm4awlHAJKwlhC0H/uUhwKC0tQXJyMoqPFiM2Ng4qlQq1dbVS/MG01CEoKipEbFw8uTx4KLOHC2IOIplCm8XrQItnBDx2WC3kEkIVPTaPkEVoPCXUXgtqyyph8RuOceOjoZc54Q0Mh8FVjaJdP2B7kQxRwychO1yJpoLt2LnlR3gnTUSCnhQSEgYaqmphIwuN8RlhZKFhQvmhHTj4449wTxqPeFEHLtQf2IAdZXokj5pBooQHlXs2Yu WfTBOHw5/atPm LYCSsIK6IfMxORUspagPypDANSmwyLxCWQqI/w1XjQ2WVHXQf GpoPYsbccuiETMD0xEHJ7E x odDLm9BoFezPbmnnTp3dSZyO0ewOF557/Vs88 rXks9RdnoUfrVkEpbeOA0XzhwGPz8NtuwtxB//8RmefXU9RH0uTIAJMAEmwASYABNgAkyACTABJnBmCIjNfk8Pd7NrgpxiSbTEkHA4RGwJOYyUoSOCUokeJZFCWE I12IkIVLU1deTIOFzy3BLKUo7nwPZWkhiiNtlh7m DPkHjsAqC0ZsqNoXhJP6UAUlIDbMD1q9HzQOE0ymShQUW2HIIIFgZCJC/AMRmTEGaX4mHD5shVIlJA7f2KrAOMSEB8BgDEdyzkQk6xtx IiNMo5Q7AhHFQpK7AjOno7RaREwaI2ITk H0VmGUpcWKtqxi35OHt/s9MXoUOiM8FPTWBQg1NFUiyYHpWdtdTs761/pscEJNYLi4xFMMStUugD4wQYb9d8Vdm3V6c3TNCgsKHYcKMZjL3yKi2dn4/J5s1FRZ0WwQQajXg6H0439xbVoNNvhUagwY0I6DuaXYPGvX8Ajv7oY2UNje8OP2zIBJsAEmAATYAJMgAkwASbABJhAWwR6Ef/ASxYQ5N8gCQRy p bXostv0qlRG1tDQXEDJOCYgrrCJG9Qy5FLxABMamJ B 9FvEnfMEqWm/ZW01UCmRB76t/wIf/PX5epgtH2uQpJDa4Yan0CQHiqpcEDAfFrBBN3KYamL0axMQZ4TXVocksglHK4R ghqe2Gm5tEOS2430eb6tAQIAK7roaqhMAb3UdLDQPx7Y1eHtbq7nRS4VVQS4hbfUhJtBqTR4XXM7mL CPT1dau8fScf/6oERyN9mC/LXvoSY6FtExsQg3tnI/OXFKZ/zdgBcotu4pxEPPrcHfHrgKGq0BJiupWBRtVZj/HDxSi5JaG6KD9bDYXEgI0yE9zoBpI8cid0wy7lr2OpYvvQKjhyeecdA8ABNgAkyACTABJsAEmAATYAJM4Fwi0I4s0CUEHuGnINQJSWwgkYKECCW5cwRSdoqio0XQ6HRkNeChDB6UtUKrg4MCXAphQqPToqGhQRIwxHXRS0fzkK4FjMTUcVFQ0xfaGp0fDGRJIHMLa4p6WE7ycmjpz9enjCQJDxwOt RuIYqkydD/ZEra5Pum3nzFN49jc6EAnaKOz9hDhZiJc5AVfOL2XEmpUxXmEztpaz1tnWsZ1DdeB/1bjYgbNROx9loUH9qLfVsKcDRlPEYm vviVxyb/dl5MaBdPKw2B37z2Gv42x uoJurocfXgyC9CqEhpKQp1AgOi0YkmfvIFErEkTjhcZhxsLAaWjK3GTUkAv93xwX4xYOrIPrhwgSYABNgAkyACTABJsAEmAATYAKnk0Dr7Xz3Xnu9PmVA2p7TTl8IFCo1ZefQ62Ew KOsrBRqjRpqtQZmi5lcO8hqvrEBQ4dkoLyiXIpLIVlQHJMo2hq/ea2qAIQEaWlD7obTWofaqnJUVtdSYEthlXBMUjihL7kuCAaZDZXllCmjZQyKOVFXTzEvyJXDQJk12mzroZgQDSSm FOcB4pgKScrChHXor5BZLBwwuVyHDtsjdVopHgYx0vrNcigoN28i0IXnOrI0tKCbDo67d8X40OmCUbSmFmYlKKjoJnlgJZEmg7ZtcXz5DW3mnoXXw5oC4qHV7yP 2 bB6NBTejc9Nx6UFXTiAZ7A5ISk0jNcsFKD5WqDhQo040xOZnk5yMnQYseITpGDonG9YvG4cFn/4snll7VRWQ9qEaBTQo3b0BB4ATMGGqkefVx6W/z6WMcPDwTYAJMgAkwASbABJgAE2ACp59ALzw8yG2DNrvN 90WkUIhV0jWEmH0hXRNTS32UjpQEW9CnPeQoJFIe0CL2UQixVAcPHjQ11x001pjaL3M1ufJTUIE1GwtB0hVm6fR0qzFKwSqECRSpoufdq3HLncqglVuNJXlotBCwS4nxULtpCCTwsOEGtpKdmG/PpTyf7hhLs jOhrEjYuBhtKANqpCER txa59X2OrKxWh9IW7zG2DxWFAZHQAlO2NL9PRPliG0vydyPeLgtxqhl0Thgj/E2URqDvuX26rRFktYPAjgYayjtTU2EkpodSllKYUtnqIxB5ns/T5Xrmni82lVC65h0uRQzEkRLoZEbW0uqZBytyhNkZAxAxRKxVQkqykU8vJzcOAdRu24Wh5NQXR9KlxTqcD50/LwtZdBdifX9r1qbjL8OqCGMQs hB1Xblh1l34y/U34I9fkS9S10c5czX723zO3Eq5ZybABJgAE2ACTIAJMAEmwAT6jIDYLPXsEF8oUxoMqb1kISBcIkipUFMMCoOfAVHRkUgfkobUlFRER0dDp9OjsJAyWJDVhM1uQzoFmgwNDobZ3NTJHFrDaW uLXVaX1fAmDKakjMY0XDoJ zcsQtFZiPSJs1DTjhgMdmaLSvIAISCUZRTqtDdO3ejsFGPxLFzMS5aAauJ4iSS3URQ2ljqJwTWI3uwZ8d27N6ThwoTfdFOYgV9vd5qgq3Gl6kQlp6BaF0l9mzZQgJHAaotMslb4HgR9TvuX ZoQFXhHuzcthnbt 9BmScCGROyECgTbivt8ejsfGum3Xs9YC0oNpOo8LOFOSQ22CnPrQ4VFFykpt6MUWPGSfFC1GQuIwJkuii4SklJKRTh5EOjD8aL722GxWrD5eeNRE5GPFRkejNzXAp 3JmPjJTo7tHj2kyACTABJsAEmAATYAJMgAkwASbQJoF2LRfarH3iSfEF9DEjCukLaV8RcSZELAoFufH7xA yoKA4FGLLXFPjRV5BPoakDYGTUozGxiag0dRIMSKcUjrSU4sGkWPmIjk0gtKJ1vniaZ5cSeaHxInzkRkWAoWt6qQ6ahijh2N8 iT4G7SgpBzwuMj6gYJ4moTpQbO2oI4ah9k5/vDK1CCDfngpvoW1vgZN9uaMG3TeGDMM49Inwl9P/UhmBB64rA2os7Q/vkwXhTTay44ONEInpftww95Ug6ST59tR/8ZUZM/IQVCggfbQgjIF1nTaYKo3SV/6n 0yYC0oftyVj5S4YFQ3WnG4pAa7D1E 3NR0yvVKMU7oEP5D9SYrTBY7Qv2VGJ2VijljU/G7a6Zj6f ch5gwXzjUvMISjBkei807C3rO3lWC9   GFNGpiImhiwrKPLp8Fk34/kt9SeYCOU NhWJ0vUYXPYxORmJ4ijGp49dgynp4nw8subejpXbG3ztXJX48pFrcd7otOZ h2HJmyXkk9SF8Trqt3mlbc6n5xS4JRNgAkyACTABJsAEmAATYAJMoBWBzr5pb/u6mxIeCCuJSooloVKpoaE4EyLWhJpei/fip0gpqtFo6byaYlIYKDNGAMIp/qBBb8Ch3EO0ZyJ3f5sFwRRUU0mW9e1bcrhgqS5BeY2lfYsBrwOmyhJUNjp81hwnWBa4JFGgupz6KKM6VSROHItd0axQ0OgeWwNqKnx1KioptoRVZANptX5vcz/NdcrLylBdb6FdrRA62h/f6zKjobpMGru8vBx1Zuq3rfod9O8lK4raylJfHxTbQ4q/QYE/22fW9n07Xr/nvwQD1oJi98Fiiq46EZ9vLUEYqVlB4bGoohtotjklPyRhPdFotqH46FESJoZJbiDi8Dfo4Kf3YtvewxRMxYR6isxq9/hhx/6inlP0NOLA91tRkb4ULzydDb0lH58//TD dJ0KQ39cgVnNlGN/vgovLokj3yMZDLF dP8asfGhy3DTu3H438ffxvzoOqx76nd4 Op7kbLxeczW12D7J tQmHQX/v7keITQON6h4VB68joez9jUcb/N4uEp8 k5AW7JBJgAE2ACTIAJMAEmwASYABM4gUBPLSgsFitZEaiQm5eLnXt2kWFAy0Zf7OlahvBt71usFMReT7h3eCjlqLCWcLvdiImKgclkIvcPXd/cGaEtNM9X2tKL930zkwEz6oAVKIpLa1BPOV/GpOixu7ieRIlgeKobodVQtFEy 3G6KACJ1YHSogLIx6fSwyACY4qHwidUjMpIwNsfut3EZAAAIABJREFUfQ27zQaFToEGsrbobfFPn47zZmZDi mYFFeErxa8jQ8PWDEr09ezLiIVGRnJJFD4iqfqKzz5WgUmPvkR7lkULgXPzPpzGT6d9Dhe32HC7Em esaMmZg7Q/TbXJqTjrQ33ozkTvod2/Z8Wrrnn0yACTABJsAEmAATYAJMgAkwgd4T6Nl2XEepQkNCghEU5LN678k8bLTPE19Ih4eFN6f77NlcejL2sTZyA7mHzEVWuHAPqaTTfTCHXi3g7DcesAJFVEQw9hU14uCRSqRGaDAiXo8msxX7i6ugUBso9oRbyuDR6NajoLAIifGx0gPRIlCYKbrrSHKreGXNRmRnxyPISFFKT2NRRw5HJP6F8kaRmqbtYi/ejHwyPaq8cxTi7jyxjqZcmBh1vbQe73T22/UZcE0mwASYABNgAkyACTABJsAEmEArAj3cj4usHAHGgNOHsofzOC0T8DrRVH4UIlQnl84JDFiBImdYAgopY4fDo0BhjQvztTKEBZKrB6Uc/e93 XDJtbBRTlizU41/fLCDXm DzNGIJ5f TIrkKnLkCveOOosctQ1WjKL TmeRUdAWSnYjBexstwhrDvhjwTNvYemIY/YRVF0OfWQI/Z/yvXSxnDBep/3md7FXrsYEmAATYAJMgAkwASbABJgAE gZgWYnjJ415lbnJIEBK1BMzE7BV1vyEBkTCX 1DQ0NIuqqF4EBfrhm3nB8sXEfvjtoIisKUqzMCgqY6YS90YwSCvrhdTvJF6kRX2w4iGjyS6pusGBsVuKZewDkGlBaWVjqTrSK0MSNQbJ8NfYekiF 8ZDjLhwtM2l25ejuxDrt19r2fLo7DtdnAkyACTABJsAEmAATYAJMgAm0RUAEsHTY7FBTMEsu5w4Bh8MOjbb1l /dW/uAFSjGj0zGilfXYkJOKrbur0UdWUOIQCgGg5 UA1fusqC4rIpSo8gpragdLpuZ0rTYsP9gHiJC/GAhfySN1oDMzFSsencdbr1ySvfIdae2Jg7j0pRY/cYTeHHUjRiOUlRFzMfi0XPwmyWRuGrFdbhZsRTXTIyDxlSMQzXpuPLqHPTUqEke1km/7c1nTJAUB4MLE2ACTIAJMAEmwASYABNgAkygNwTiEhKQT0Euk9PSpEwbXAY/AZfTiYK8PMQnJPZ4sQNWoEiOC8ecyZnYvG0/hqTG4YONxVg4NgJWqwVarY5Ei2LUUfwHj9Mh5XF120mgsDVRUEwTWVs4yKLCgbTUDOw6WITpY9MxJDGyxxA7bSgPx8LHl2P9rQ9j2S1rAVUUpt83GpeMGYKpj76PVaEPYvnqe3HjsxSvQhmMoRc/jIVLei5QQBbQcb/K9uYTBP6ro9O7yRWYABNgAkyACTABJsAEmAAT6IRAalo6cr0HsHP7NjgcPTQN72QMvty/CAghKi4hCSmpQyjNq7NHk5Pdcftt3mdX/B21NdXd6uDjD97DtTfc1K02p7uyw nCzGuXYfG80WigAJkzMv0orYwLu3Mr8Oa6PNjdCnhdPoFCiBRyiviwZEEmhqWEwyEPhcUdgH  tRZf/vtuyqU7YLWa042V 2MC/YrA6lUvYeFFl5wyp/7wd9Apk ITTIAJMAEmwASYABMYxATa 1zW3pLFhlWpVElZFrkMfgIi5IIQJnoiSJUcLcaLK1diQO/K5fSc//muy/Drx97EtRePhd4vAFZzI pMbiRHB8PUZIbVYodOa6QUNYkUnyIQQWGhiCWTk7xSJ1547VP85e7LoFSwY8Pg/3XhFTIBJsAEmAATYAJMgAkwASZwNgmIjWpPNqtnc448Vv8iMGAFCqHOmM1mJEQacc/107Dsn sQGTwbsZERiIp0ITCQLCSsTnhJrVMrNfD394O/nx/CQgLw1pe7sW7DTjx421wkRgVQPAoL/OgaFybABJgAE2ACTIAJMAEmwASYABNgAkygbwgMWIFCmAkpFArpSIkLwa8vH45X3/kKlWY1Jo1KRUpCJEYkh8FP70s3erS8HrsPFeP77Z8jTOvEXUtGUrtQyOVyqQ8uTIAJMAEmwASYABNgAkyACTABJsAEmEDfERiwAoVAJqwelEolVCoVAgICEBMdhZ1787AnLx/v7d6JqiZQHAoZtLTKcKMc8REGXDk1BqOyhiCBosoaDAayrPCX2nNhAkyACTABJsAEmAATYAJMgAkwASbABPqOwIAWKAQ2LeVYFUdISAhiYmIwZswY2O2UVtTlgpPSnIjUoy0ihvipoTy8oj6LEn330PHITIAJMAEmwASYABNgAkyACTABJsAETiYw4AWKlgUJlw8hPoiDCxNgAkyACTABJsAEmAATYAJMgAkwASYwsAgMGoFiYGHn2TIBJsAEmAATYAJMgAkwASbABAYvAY/Hg4K8PJSXl8JmtQ7ehfLKjhHQ6nSIjIxGcmqqFOuxJ4UFip5Q4zZMgAkwASbABJgAE2ACTIAJMAEm0C6BgrxcypZoxpRpM2DgjIntchpMF8wmE3bt2I6C/Dykpg3p0dJYoOgRNm7EBJgAE2ACTIAJMAEmwASYABNgAu0RKCstwbSZs6HT6 H1eturxucHEQE9JaEYOWo0vv1m3bkpUAizIVF6aj7S8ixs WAZEkeej7CEkYPo8eClMAEmwASYABNgAkyACTABJsAE oaASFyg1erg9bA40Td3oG9GFffcbrP1ePABa0Fx8OABrF33BYRIMXvmeRg2LLNHELau SO2fPw0Rsy rUftuRETYAJMgAkwASbABJgAE2ACTIAJnErACxYnTqXCZzoiMGAFis //BTBQWHIycnBF/S6sKgQ58 /oKO1nnJt63uPoqlqD8KiU6AxBJ1ynU8wASbABJgAE2ACTIAJMAEmwASYQA8JsGtHD8Gdu80GrEChUqnw3zX/hVKhgFwmx949e8i3CVi4oGsiRW3pATSU7UL67MthWrPy3H0CeOVMgAkwASbABJgAE2ACTIAJMIEzQKDf2E Q1b2nuBie8nK4S8vgra31rTYoCIqYaCgiIiCPjxexA84ABe6yOwQGrEDhdrkxbdoUFBTmYcL4ycgYmoFXX38FLrcbF19wcacMtq15CDExwdj77v1QGrI6rc8VmAATYAJMgAkwASbABJgAE2ACTKAbBPqBBYWnrg7OL74AaJ8opzSYKhIl5EmJEN9ue6qr4TpyBPaDB FVKqGdPx9yus6l7wgMWIkoJSUV4aR0iRgUW7dsQU1NDa752XU4RLEp3lmzpkOijVWH4Xaa4K4/gNoGOcZf9kiH9Xt70dO4Ay/ 4jxkxsaQKELHxe gkoLFmPevxq8XjESCOBczCr//qRH5L1yItOH/gzUV7t4Oy 2ZABNgAkyACTABJsAEmAATYAJ9RkDoE3120H7LuW077Gveg5IyiaiS4qEICYDH1AjHzp1w7NoFj8UknVPHRUOlVsPyzruwb90mBfbss3n3JbPTNHZvHrgBa0ExedJUrHr5n5g8eRp  P5bfPLJxzj//IWSSCEsKV598w1MnjAOjU2NMJmbYLNZpSiyfgZ/FH75RyTFhqHs4F5ojckIjhnWI4aepgN4f8WTeOmdr7GjzAooQ5A 9SLc8OvfYMmYEPjgWrFj Y146JsM3P33hzE5UgGP/1CEuA7gLzfdiw/Dfomn3jgPCToNoobqICtMRlpaIELUsh7NiRsxASbABJgAE2ACTIAJMAEmwAT6B4G c/Jwbt8Gz779UMVEwWuxwL3vIBSZw6EYngRVeLiEx1NVCU9FBdx79kLm7wdNWCjsJFx4vR5oxozpHwjPsVkMWIHCaDRiOGXucDrsmDZ9Fr5dv 4UkSI3PxhjR4 DVqOBUqmCw FAbXkBCm3VkNtMqGzwYuJ1v /RLXfXfI0HLroGLxcnYd4t9 KZ7Cgoavdi7Sv/wL0Xf4Qf/vYJnltESpyzFBt qEDYxS/i1gtHQ9c8mrv0Q3xTqMPMZb/CZdP8js9h0TP4ZFGPpsSNmAATYAJMgAkwASbABJgAE2AC/YZAX3l4eCjGhHPHTmjI4t5dWg55YCA0V14JmTFAYiNr/i5Y5m EIjkVyuGZcHy5Fp6aWmgCAmD aQcUiUlkXRHSb1ieKxMZsC4e4gZNmjgZ QV5JECoMX7idDicNkmkaHH32E3q1649B CieBVNTU2SQLHvi78gPj4W1aX5kKmCsGFPcffvtbcRG/90J14uysLST77AP/9wExZfsBCLrluKFR9/iUcnNuLDpb/H51UesmlywGwHqlZfhFTJlSMGU5/Ohd1hhh1WfLok3ef2ETMGD 2yoOqdCxETvwRrG5un5azE qdvwuzhcVK9hJEX4NFtZt9FRzE fewaTEkX/cYja 7tWLm9ATQqFybABJgAE2ACTIAJMAEmwASYQB8TEBYUZ/fwetywffYpVAFGcucwSeKEetEiSZwQwoRMUid8h3gtnaNrmksXQR4cTG4fFmgNephoX l1u87s/D1mlO3djF1HmmgPd3Y5ndn70vPHbsBaUIgl68mXaPbMOXj/wzVQKDXIGjUOe3ZskUSKCRMm0DkFDpZaoAusRkqUEeb6CjSW7kRsehSqzAZMuek1vPnf97pPr2kzXnq/BgGXPI8bM/XS432saFJw1f1X47kLVuHFb6pwfnO8zqCLn8Ord2RAQ7W14QlQNYkWGkz789t4MEdPvxVqhCRpgEOt vKasX35pfjZ3504f mzuH90MBwV1QiIo3pCJHnoMtz0bhz 9/G3MT 6Duue h0evvpepGx8HrMD2UWk zeWWzABJsAEmAATYAJMgAkwASZwugh4 8CEQgS9pMwJ8OrJtZ4CZGovOJ ycwAbftxAX1jbMXHCJHL910pLtNls2LDhB2jo/UTaPyrPmwXbG29C7kcW7g4nHIWFUCcnny4cp/bjsaOurAy18SOgUclofp181ex1wVJXDbMqBKH qhP3oaf2PiDPDGiBQhAfMiQdS668Gq 9 Rp0KgUUKiUFaHVi46YfEBkdD4O/DNv2FUIlT0TVxpVIyJ6L0sZG1ERMhdYvuEc3zVm5D4dtQPLUITC00YMuZQqGKP6FQ7vK4LiYxAQq6pBkDM3IgO9XAXBKAoUKgYlDkZHR0osHVa3689Z jb 8dBipd6/DijvToW51zVP1FZ58rQITn/wI9ywKF79zyPpzGT6d9Dhe32HC7Bn rWrzSybABJgAE2ACTIAJMAEmwASYwOAnIGJKKCkjh5esJ0TMiRa3DjuJEbV1tVj/7TeYPm2GBEK8Fpb2Ic2uHKKuaOPefwBqhQIu6qtNgcJrR9nWr7Gz0nkMqEJrRGBYNOKTkxDh181ttlwJhbwLXzC7G5BLCSKahsxFBH0h7XH3XYyPM/UkdZPcmZpG7/qNjY3D7bfeDn/yIfppx1ZcvOgK1DdZEE4RWY8UFqC25CDWfroJAQFpCKI/4UkhuCp7LL0P7OHAFNVVtOzsGerl82Ir2oD9zjDMmxZ/gjghhrYXb0a y4XKO0ch7s4Tl6Ept5CJkL8kWnBhAkyACTABJsAEmAATYAJMgAn0BYG sKBwlpRCLZdLrhrK8AgpjYjXK8OE8RPx3XffoqmxCd98vU7CYTKb4e/nj/FjJ1DmDnHGC3lEFFw7d0spSW1HS6BrywqEKrvsJE4YszB5bBRUHgesjVUoyd2Pn9YXITZnEoZFajvdLkqpQo4VMc/ONpC 6zKVDloFZYV0dVa/VfcD5OWgECgEayFOtJSM9CEoKKlHYnQAUpKSMHHiVIpD4ZDMFhxN5TA5FOQeYmj2P r nVKFDUMiGUZs z4X5svDSQo4sdgKNiCXsoTGZkWRsFDb/QFaWlAKVS891m3qIOIXjUZe8MxbWDqixS5DNJRDHxnC4kTPqXNLJsAEmAATYAJMgAkwASbABAYoAVd1FdRBwfDa7ZCFhkkagEzmhYYSJ0ydOk2ymhDChCgGg0E6J64JcULUlUeEw0tfBIv4FA7K8tFhUQchLDQALquTLPfpdWw8wjZ/iZ927kF46FiEKalDjwUVubtx6EgVLC4Z1MYoJGVmISGwHReNLtRv2vk /rvTN7OgnHkYF6nq/jgdLqzvLg4ageJkhIkUc0LkryXvI5TVNMBUtgd 8gYUHT6EmMz58NDmv8fFOA43XhiEr9Y8hpdvfQe/HEbpQVs6cxzGW4 9inLtLDwwM5SEgp4LFJq4MUhRrMYP3xbBkXOii4e4lixfjb2HZIhfPOSY60iP18QNmQATYAJMgAkwASbABJgAE2ACp5GAk5IUnO3idLrgcjrhJpHBTUEufYEufcEwXdI5t3SIIn6Kc0qKXegzXvDCQ /FOTn1IZIttLkGSoRwzLuC4khYLTafhT31GZCYCH1ZHgpqPGTRb0Xlvg3YUaZH8qgZJEp4ULlnI/Zu2Qfj9OHw97hAW1ZfoTAFLocNdQc6qE91xC5WP2QmJqfSF 70R2UIgNpSjiN7Omg3gNIoDFovAKF4KRRyyMmXx2lpgtGghpsyZ1RbDThcI  x9YT09MgCMPWBZ3BNzA4sW7AAty5/Ge9//gU eu2vuPOiubjvBz0WLF GheGK5qetZz/kYXPx2yVRyH/iatz25Fv44tvvsO6j/ D9/SbIwubgN0siUbTiOty8/A18/u33 OaTN7By9XY09EJ76dlMuRUTYAJMgAkwASbABJgAE2ACTOBEAmLvfbYPWQhZT5C4QKoD3JWVktuEOKxWG777/luYyXpCWE6IQ7wW58S1lnoihgVtIknYcEMu upgDa1X21JPpgmAgbaBllonRRysIct O4Kzp2N0WgQMFKciOj0dRmcZSl1aipPo49PSj8dR1Wl9UVehM8JPLaMv5N3kIVCLRlNFh 06WsOZuNab34NBa0HR4r8jhAp/DdlReINQYyqFXRNNfkTmY6pZT EpQmdj2eefY wzT2Llmw/j9mcpl6gyCKkTLsUj796F6yaEoddwZUZMfvR9/DvkD1j2r9/hhqdIedAnYuGyyViYEYupdG1V6INYvvpe3PgspcBRBmPoxQ9j4ZIcBAxa6amnd4zbMQEmwASYABNgAkyACTABJnBWCXQaU H0z0YZGQl3fgGJDDK4KUOGIiVZ nJ685YfYTI1wY8ydEyZPEUa PsfvpfObdq0EdOmTZNECldJCShkhWSBoYqOlmJYnFLEuWOnxevWdXyvxSmZox4WeuHYtgZvbzuxF4VVAdIyTigeS13X65P1hYusRURxmztu5/UTgQMGRun1Hro/LlM8WEINE ljhL RnO5bU10T6qwe6NS0ZApiUl1djbi4uF5NX27MxOIHVtHRQTfqDNyzsQT3nFRFlXgb1pXcdtJZOcIWf4iSxa1Oq2IwZ kqOtoYQx2LuUv/RUcb1/gUE2ACTIAJMAEmwASYABNgAkygDwm0sbU/47ORRUTAdvAgpe1UwbFzJ2XlyIQ8MAAqtRqBgUEYN24cvfZlWpw0aTK2bN0CNV3z0B7SU98Ax44dkFFMCiu5h2ipr/bWcLIk0fLeY61DE3mQ6EMM8NnTqxAzcQ6ygk/ceiv1OihMx2UD0d7XRwf1m9qq33k7U21ju s44zekmwMMKoFC BApKB2M2WxCI6USFUVND6abctg2NdZB7UeBS5Q6yXrCSWY/4hD1K8n0JywsrHduH90Ez9WZABNgAkyACTABJsAEmAATYAKDm0B72/szt2p1fBzMtMfTkuDgpb2g7csvobvsUowdM7Z5UHKNaLZ4UJNQMZlEClG8FKNQ1PVSWyEDOMhFJCAhXlzpZLLHpQURELM8twg2eRgy4wyA2Qi97AhI9yBjdydsrbJuuBqrYXX6YmH45kNfrGsDqP7R9utTSA KYkCxKii2xjHnEzIW6aRd52voZIln8fKgEigaGhoQFRWDDRt/wOicsZLgICP/IScpYC5/f2hkSnInkiM0NFQ6Nm36kXLehqGujsQLSVHradrRs3jHeCgmwASYABNgAkyACTABJsAEmMAAIHCC58PZmq9cAb/589H47n8pDqEB7uoaWN9dA83s2RRKUGR JHcH2ieK0iJUeBsaYf/qK3iqqiEnUaOWUpQGX05m7dRXm2to0Szstagsd8DcaIHN3ICa0mJUW9SIHj8FiToHZQsJRny0Frv2fY2trlSE6ilzh9sGi8OASMo4qaQ/wsDfVlaIipgY2pOGdlJfR2uSoTR/J/L9oiC3mimEQRgiAjppN1D8O ieDCqBQjxkI0dkSz5EFRXlyBk1VnLjCAgMlg5hVVFbW4ujJcXkb QLkDJ06DDp4fSllpFecmECTIAJMAEmwASYABNgAkyACTCBXhPozPqg1wO02YGSgltqskfAvHsPDDodPBRnwvrO21AOHwZFRCTk4WFSO09lFdy0b3Tt3UemCQrINWo0Wq3Q52RDFRpCNdqfv0IoCzV7sOE73xQUGn8ERgzFuOEjkBgkh62eLCTcSgSljUW232EcLtyDPXbqT6aGX/RwxAmxwqpFREoCag8ewM4jYZiYouqkvhdh6Rlo3J HPVuOCtMJhKSHIyG043Ze69nPptLmjenCyUElUAQFBUnpQydPmorCwsPYtHkjvvr6Szgcdum8sJ6Qkwqm0 ooX204UlOGSJYUQsQQ8Sq4MAEmwASYABNgAkyACTABJsAEmMDpIdCm9cHp6brDXhyU3tQzNAMOsxW2/fsRRNb0MjrcJaVwFxXDa7dL0oOcrOiFMEEpPSjtBqUEpS 0lcOHQzNsOO0hKUimqr3tshphI6YjLjgSgZrj2Qm8lAbUabeivsp83J2DBAljzDCMS58If70WSqm6By5rA oslCY0JBXZM0cjKFAPua0G1U5vB/VJ39BFIW1cCkYHGqGT0oC4YW qgd3R/jjVlg5x9auL7RHvV5Ps6mSEqY4QHEJCQiTRwWQywULmOeKw00OoJD8iYSmh1 vhTw oSC2jIhMeLkyACTABJsAEmAATYAJMgAkwASZwugm0b4Fwukdq6U/EG3RTgEs3peA0JSbApFLASpYUeopTaKAvpcWeUIgSMhGjgqwlRFxCk80GK 0lLaNzEEhxJ9z05babxAYlqQkt7iBtzddWW4byti6cfM7r8okITSdf8L332OtRU1F//GIn9b0uMxqq6Ti5u07anVy9P74fVAJFC2DxELXktu2P0HlOTIAJMAEmwASYABNgAkyACTCBwU6gLywohMW8SqWWYkcEBQdLVvQNfv6oPXoU8vp66JuaoKYvr0Wxk2BhpWuIjIIqLhZB9EW32EeK IS L7JFQM3Bfpf61/oGpUDRvxDzbJgAE2ACTIAJMAEmwASYABNgAucigb7Z3Sso1YVOp4WOkPsZ9JRIIZJcPtLhcrngIgsLkbFDFCFmKJUKKbOjEDLEzxMtJvpm/ufik9KyZhYozuW7z2tnAkyACTABJsAEmAATYAJMgAmcKQL9YH8vl1EcQpGbk0JNqMmyotPSD bc6RwHcQUWKAbxzeWlMQEmwASYABNgAkyACTABJsAE ooARXnoq6F53AFKYFAKFLs/mwInRUAVRaULRda85twv9L6xqRHvvvsfeiWTgqfExiZg4oRJCAgIGKC3kKfNBJgAE2ACTIAJMAEmwASYABPoXwQ0Gi0cNjvUlKSAy7lDQGTQ1PQiQ agFCiEODFi3r8o5YoTu7647YSnoaAgH1HRMcgclgUPRTwpPlqE1954BTdefxOlGhVeSlyYABNgAkyACTABJsAEmAATYAJMoDcE4hISkJ Xi S0NCnoJJfBT8BFGVEK8vIQn5DY48UOGoGitmQdjKE5UGoCfTA8lF607tApaWHyC/KQlZklBU0RKWZ0aenYunUzR2ft8SPEDZkAE2ACTIAJMAEmwASYABNgAicSSKV9Vq73AHZu3waHw8F4zgECQoiKS0hCSuoQCkjq7NGKB7xAUV  Abmb7kJwzEyUHPgHsma/JYGQwQ4ZBUJpXbzCYqLoCGbPmgMnmZ7U1Fajrq4OQUHBJFiw9USPniBuxASYABNgAkyACTABJsAEmAATOImA2KCmD83A8MwRp3xpzLAGJwGx3xb3vTeC1IAXKPZ//wuMmvsypYRpRNE J rKvm  207o/IJJqaCIrc2lorICwcEhMJmaYLVY4HQ7ycWjGGmpaWf/CXHXYMM//4b1YdfjrkUJUJ39GfCITIAJMAEmwASYABNgAkyACTCBM0ZAbFR7s1k9YxPjjvstgeO79347xY4nFj3kejTV7oOt/nOExExA/pb7pAYUAhPWhmLIWgWOPXy4AEnJyZKqU1ZeiurqalRWViKRzFDOWPGYUPjjF1h3oBG bLvNI7kr8d2qlXh7ex3NlAsTYAJMgAkwASbABJgAE2ACTIAJMIFzm8CAFyjiM 9A0Z6VUOivwLJff4 1X1 CV/85EffftAkr/iLD6lUTjt1hESAzPDQcep0BMTExUhwKs9mCyMioHj0FnqYDWPP4zVg4JlXqLyZhBGZd8wes3loDV0uP1l34y/U34I9fVbMQ0SPK3IgJMAEmwASYABNgAkyACTABJsAEzgUCA16gkMmVSMx AJvXvoPzr70E9zz1WzQ0GDD/Z fjnr/ Fo31euk ulwuVFZVICAwgIJjKmAncyNhRREfF9cjnyh3zdf4w/zZ N/n9yPiknvxzAsr8bdHrkFG eu492I6v6YUPQsLci48drxGJsAEmAATYAJMgAkwASbABJgAE2ACJxIY8AKFWE5I7Gzs3bQXCUMT0FDXIOXbbXlts9jwf/8chsX/NuAb/f249YMk3PBuDH7//Risq/gbdI7i7j8T3kZs/NOdeLkoC0s/ QL//MNNWHzBQiy6bilWfPwlHp3YiA X/h6fVx136sh9bCoShZUFHZd93HBszIq3f46xieJ8HIbPuhnPb6k/7gpCc/v0sWswJV1cj0fW3NuxcnuD77qrEl8 ci3OG53ms96IGYYlb5Yct9zo/qq4BRPj4cN8AAAgAElEQVRgAkyACTABJsAEmAATYAJMgAkwgT4jMOCDZApyHpcDh/YrMcPchPx9h2FxWMh1w0SvC2F2mLDbU4jLzr8Geo0RHq8TLq8dTfZafPrZp6jfUYv6aecjMDqj6zehaTNeer8GAZc8jxsz9RTvolXRpOCq 6/GcxeswovfVOH8833XYn9O75fEUTBMGQyxfscaaNIX44FfTkSEpxhfPP0A/nTd7zH0xxWYZWzCxocuw03vxuF/H38b86PrsO6p3 Hhq 9FysbnMVtfg 2frENh0l34 5PjEeJphHdoOAbFDe36neCaTIAJMAEmwASYABNgAkyACTABJjBICAyK/WzZwfVwKSlNqFeGqqM1MDmajr 2N0FH0R SnbEIsYfDiGCY0IBaWTk xkcYkjkWhVvfQfZFD3T5ljor9 GwDUieOgSGNlrpUqZgiOJfOLSrDI5mgUIXkYqMjOTj2TqaUwEHjliAi ZmQ0v9TIguwBcL3sKHB6yYkfwVnnytAhOf/Aj3LAqHMHXJ nMZPp30OF7fYcLsSb6BjRkzMXeGr30bU FTTIAJMAEmwASYABNgAkyACTCBs07A4/GgIC8P5eRWb7Naz/r4PODZJ6DV6Si YzSSU1Mhl/fMWWNQCBRF29fA7nbjhZdeQGO1CUfrj DztV/gyKEiVJkqEFTqRd5n27DPVkbxJ9xQyN3QaoUkAESkTMTWT57qlkBB6gf9oXKC6UQbD0CrDCJtXD3llCpyGCLQhPJGF zFm5Ev4mbcOQpxd55YVVNuOTEjyCk98QkmwASYABNgAkyACTABJsAEmEDfESjIy4XFYsaUaTNg8DtuQd53M KRzzQBs8mEXTu2oyA/D6lpQ3o03MAXKLxeVB/ZgT898xxKj5aSC4cb3tsulBQb75hE3HD1ZNR4SqCUKeH1UkwIqg/xkySGX8l hqDYTMDtopSk5dAFRHYJoipsGBI1wLbvc2G PBz J7WyFWxALuUOjc2Kghr5XepTVJIplFCQ9OAWwgbN00s9L3jmLSwd4RNTfB3JoY8MIYuK2i73yxWZABNgAkyACTABJsAEmAATYAJnk0BZaQmmzZwNnV5PW5tufnN7NifKY502AnqDASNHjca336w7dwWKmuKdiBk2A8bQaCjl5DdBAgXInEj6KcQKEiNiveSIIb0/fr6ljkypRkTiCDRWFXRZoIBxHG68MAhfrXkML9/6Dn45THfcmMJxGG899irKtbPwwMxQEkqOwo/0BUtd96weNHFjkCxfjb2HZIhfPERyATmhNLuInHya3zMBJsAEmAATYAJMgAkwASbABPqagN1uJ6t1HW3BWJzo63txNscX99xuo3gIPSwD3oKiZM8XSBi5ACq1DobgOMnyQFhHSIdkLXHS 5bzzXUUan8SOKajqbIAEanNgR06gykLwNQHnsE1m6/DsgULsOv2G7AwOwqK6r34cvXzeGe3niwflmFhuILEkjiMS1Ni9RtP4MVRN2I4SlEVMR LR3Q8iDxsDn6zJBJXrbgONyuW4pqJcdCYinGoJh1XXp2DgI6b81UmwASYABNgAkyACTABJsAEmECfEmh2jO/TOfDgA4vAgBco8ja8gp0fP07uEWoyknB2m75MroBCpUL69Ju71VYROhvLPv8cY595EivffBi3P2sHlEFInXApHnn3Llw3IcyXUUMejoWPL8f6Wx/GslvWAqooTL9vNC7pRKCAEEEefR rQh/E8tX34sZnXdR/MIZe/DAWLmGBols3iyszASbABJgAE2ACTIAJMAEmcPYJnEbXDje55dfW10nZGnU6PUKCQii 4IDfzp79e9LPRxzwd3TB3Wvx5r3DED39PtiKviPc3TEhkkHpF4H6vW8hfuSF3b5VcmMmFj wio6Om2pSrsIza k4qdo9G0twT6tzspBFeL9k0fEz6ljMXfovOtrqPwMnt2 rFp9jAkyACTABJsAEmAATYAJMgAn0BYHu7Mw6m19NXS38DP6IoiwRDY2NqK6pRkRE12IIdtY3X 8/BAa8QKHSBVDsCWDK6HRYgo/44kx0la MAmmqArF2vxxBcdldbcX1mAATYAJMgAkwASbABJgAE2ACTKAzAqfRgsJkakJ0ZAycDid0Gg1KmhoQER7R2Qz4 gAjMKAFCpFbt6mpSULudfh dos//cJ47I1SVNnq6mqEhLCZULf4cWUmwASYABNgAkyACTABJsAEmEA7BE6jPgGdVk9WE1XQkntHTXUV9DqDL9xgO2Pz6YFJYEALFE6nE6VlFQDFkTBV5UMXlEpRYilWg8je4WnJ4iGyeohsHuKnS8rq4XtP9UjgMDdUwE3JPffs2YMxY8YgIIDDTw7MR5lnzQSYABNgAkyACTABJsAEmED/InD6nDxCgoNRRV8qV1SUw2DwQ1hoGC319PXfv7idu7MZ0AKFXC6HhtKYKBMvxpdvPQmZzHcjJRFCPK4i3Whz1o5jEWRPlvHkhCDuQkqBo4VCQVk3uDABJsAEmAATYAJMgAkwASbABJhArwmcvPXqTYcKhQqREVGAOJrL6ey/N3PjtqePwIAWKETU1tjYWPhf8ydYLPeTQYRPmOguHrVajcDAQOj1 u425fpMgAkwASbABJgAE2ACTIAJMAEm0CaB02fhIKznK6sr0djYAH8/oxR/QkXZGLkMLgIDWqCQkcmEsHwQBxcmwASYABNgAkyACTABJsAEmAAT6D8ERKy/01UqKisQFBiExIQk1FFGj7LyUsTFxp u7rmffkJgQAsU/YQhT4MJMAEmwASYABNgAkyACTABJsAEeknA7XahqqoaDU31kpVEaEgohLW7KMJyIikpGcKSQq83oKAg/5hAYbPZcPRoMeqpjhAx4uPiO7SucFb8iHVb6xE5dhZGhKvRHCmgefaUiOHQevyQK0P6jGlIMlDKyLNZvHaUbf0aOyudx0ZVaI0IDItGfHISIvwG9xZ cK/ubD5IPBYTYAJMgAkwASbABJgAE2ACTIAJHCPQXQuKcmElERCEOBIYbDYrDhw6gBQSJTQarRQYs6y8DP7iZwX9JAFD9G 1WrH/wD6MyMrGMIMBtbU1OFJ8hNqltHMnvHCY7RSp0ImyAyXIiEiCynPc0sNrO4r9 SZqq4dH4we1zAx7zyIJtDN J6cpnqLLTuKEMQuTx0bR3BywNlahJHc/flpfhNicSRgWqT1JVOmkzwF0mQWKAXSzeKpMgAkwASbABJgAE2ACTIAJMIHBSqCxsRFJCcJKwiG58Q8bOhy79 5GWkoqIiIiUFZWhuKjRQjwD0B0VLQkTuzbvw jsnMkSwthZaHRaFBdVdWBQOGB0 oAFAZomg5gf20SsgMpwaME1Y2GgoOolRtIGLDD4vBCrhb2FSRgeG2oytuNQ4UVMJF oPKLREJGJpLDhFjgRPW2tdjWlIRJ04bCXzK6IPHkyPf4dr8Go2aNQ7jSgopcan kChaXDGpjFJIys5AQqGpbbFAHUaaSALisThj86TW5s4Rt/hI/7dyD8NCxCFN2NicXan5ai631CZg4PQNGMSdXFXZ8tQmWobMwMUFP43phP7oB3 xWYOSskfAe2o68ikZaN2XApKLyF3McgcSgduYo1Tq9hQWK08uTe2MCTIAJMAEmwASYABNgAkyACTABIuB0kBDQjaKhoJc1NdWSOGGxmMmVww8ZQzOwe/dOSaSIjoySDlGEW8c spzIGTVaysZYU1stiRRVFVUwkoDR/tgu2CzCQiETOSF7sXF3ITKmxNBkPaRBlOJQkRMhI3Kg37sRFmE6oXNQX040HNqI7UUyRA2fhOxwJZoKtmPnlh/hnTQRCXoZ9OGBkFXUwKpUwc9uhsvrQG1ZI2SB4xAXqkL5Dxuwo1SP5FEzSJTwoHLPRuzdsg/G6cPh3yyPSAujdu4Wgw4SSawW27FkqgGJidCX5aGgxoPwECuqDnQ8J12oEbKyejiJq9dmhqOxAg2kPTjqvFAnu2Gx2lFf0UQsRiI2RIkD1XWwB2Rh/LBwqN2NKN27DYe27kMgzdGv9Ry7cU 7W/UsO9R0d3pcnwkwASbABJgAE2ACTIAJMAEmwAQGIgGxz 7OERoWgfyCPDQ1NZHoQCKAqRFq2lxn0bf4B3MPwkqihOhP/GwRJ4QoUVdXI8WcaKhvwOHDBYiOielgXA8cZCEgU/sjYsgQBJoPIteshELmgeloPurUichKDoSGLBTsJge8chk8jmoUFFthyJiJySMTEeIfiMiMMUjzM9F4VihVMigCoxAgq0dRlRcK2mV7nQ0ob6C9f0IM1OYi5B61Izh7OkanRcBAMSWi09NhdJah1KWFStQ/iVXr 91yTaYJgEEBWGqdUKO28zkFRJCwUI SBpqfjNZTXwM72U14ao/CQnzhMaO63gV9TBR0HqckQagC4xATZoTBGIGk4UnQOitRCd0p8zt5vq3f9 ZZZQuK3tDjtkyACTABJsAEmAATYAJMgAkwASbQNoFuZvEQFhTJicnIy89FfHwC/Pxoe91QhwBjoBRj4qeftiM IQGFhw8jJ2c0VGqyuCDLCS25dTQ01CM3Nxcjs0ZAR 8pQEU7c3LB4QKUASrIdZFIitiPnXvKkT7Kg0ISEQIzMxGmsOAoiQZOcq QCYHCUguzV4OYOIp7YapDk9lFG3Y5/APUtNmvhlsbBIU9GFHkKnLgcBUw1h uhlLUewKQGaeHs6aK2lPsi21r8Pa2E6elsCqg0ZFVQ4vZhJj3samL163X4XstnXLUdWlO4X5uFBeT4DOUrEAqrfAbkglNQSHKbJmIsdag1q5DlFiXrf6YjYTXZYeD4mB4oCUhhGJgOCmdq3ApOQvlnBMofvppG5YtX9Ym2gULzscN/3Njm9f4JBNgAkyACTABJsAEmAATYAJMgAl0nUBPtrRqEhdSyJ3j0KFDiE/0iRS19bVSdo6Ro0Zh06aNGD9uIokTalTTxl9LATTrGhqQR LEiBEjodXpj /v25qqlwQKcnOQq2kr7JWRhUM8dJv2Yl eEtXyaExMJXHB0gA5CRRuGykZctqcS0VGkoTP qIlZqYkFND/ZErKBCJXIyg6GLJ9uahBDuylNfAEZiPW4IK1XLJNQMzEOcgKPnELrtTroLCaaM7HaZ0sSbS891hJHKG560MMNJeuzEmL4HA98kuPwJxuRIVJi8gxSTBU7kNBhRMR1gpYNVGIJ2HFXuuLO Fba7NGIpNLcSo8XnnHTFsanYaf55SLx7btW7H 229IhPg5Ro/OOeX49NNPTgNS7oIJMAEmwASYABNgAkyACTABJsAETnVckHb0nR4i0GVaWhoOFxRQ4Evh5qEmS4ka6ef0aTOlWBPVNZXQqDVkYdGAXBIzRowYAb2OTBE6658ECiftxRVq8pXweCDX0wY92I7SI03wSx2BaKUNZrsXSiFQ2IVAQf/pgmCQ2VBZbiaJonn Hgvq6h34f/buAzyqKu0D H9KJr1X0nuhhhYg9NCkSBELKrCiIuqCrAXE5dOV3bWgiIAgigUVe28sooAUBZQiPdQEEgLpvUzLzHfuhAnpjQCZ8L8 18zcueWc3x332fvOe94jd/ISwy4qQggqd3 4K7JwKjUDF3KMcIsMho2 FDqVM xkOtFWkYggCmrq9drKVV2YjUK1FBwwu1T93lSxEsMx0k lQC33RESAvRiiIoZ7NNomGWy9OsBOnYqk8 dRqPSGn4stXLxsUSKmaU27UAyVbxjcxHk0lYUvpOtXvUfm9jR 3 ruQ9X NP76hsqgkLInpk29B6 99poYs3Skls7IEaNqbeOGFgiU7cfTwyZj44CPsPmleFH0hQsFKEABClCAAhSgAAUocKMJ1DfKoikO0tSiUZHR4rntKIKDQuDo6Ijs7EzTcI 8/DzYikKa eKJ/9TpU4jtGivei8yJijhBw6cX03iaAhRWChhF3QUjrOEeGgl/BzG8JNpNDOfIhtYgsiUUIndADHUwyOxF8oM7gsVQjb8ObcOh8nC4WZWj6OIpnC0VRS/j/aHSFaFQJEkYla7w81LhwKG/AJU/4gNsoCsphEHlgUBfGxw69iv26sPhYSdmxShXi9ky7OHj6wylNFGIeTH3QZMrAiJalBSWQl1SgJwLqcguVcG3zwAEi8KdxSVuTWqTzMYL3vZnkHykDLZhI Aq16LA3Qc2JxNxSkylGtrHEzJ1nlQjtFqWhHmkibk5TbJtWL5Jn95QAQqpcEp5eTlCQgPx2OOPiequTk1CqrWTIQvf3zMYD20WIbBLi7VHBHqPuBOzn7gXA33MaUC1jrwxNigc4B8eiXA/Z5HIxIUCFKAABShAAQpQgAIUuDEFmhIxqF/GxsbaNIvHkaNHRW2KYFOQIic3S8zuYS yEUTNiTOn0V0EJ zEMInqj9f1n1NEHcQz4aUMCvHULf2jcPRDuJs9HI3FKBIzfEitlkspFKIYp6hCIf5RwCmsJ2Jtk5B08i kiklAlA7eiIiPRzcvUbQyR30ps0IBR39f2F1IBsK6oYPIxijUSNkRSrhG9EasQzKSzx7BEZGhIVIg4ODbCQFSsEJMe2oeNiK1XCENP8k5gp07KvqhsHaEi3c04jpJU37Koc7PRll5E9skt4WXvzOST5QjKNITcnUuDDae8HYQs4HIIxHpLrqZJ/W56r2SXptXs WV3csG7ki1j26oAIVOJ6qdinSgcpHK0 LghMQnvtSFWSI4ETEX7744WFRfLRZz4v6Gj5f9G1M2HcO6La8iwe2GGj1T/fumisSsDzZiVlO/hdyPAhSgAAUoQAEKUIACFGh3Aq3xq7uNqCDZKaYTDh85hJCQELi4uiI3NxenT59B924ic0KqOdGcZ2eFJ7okjIWbjx1QUFR5rFFbgoLKWVEVcOk0FMNdfeCoKIJanF9MzAknEVDoEyUyxO1tTFkPBr3IghBDT4q1lxsgsw8VP1x3g4enyCMvzhLZGJdCJyIg4eTXEXFR/eBoJ443PS4aoC8rQF5p1fCKCp5dhyLAzQsu1pefKY3lOug0ZcjPKoFab75eU9okg7VvLwwN94CnM1CSrRdXtYN/71GI8vSCo6EQ2ToRnpA5ILjfTejs6Q6FOsvkYlT6IHZYCNy9RTHSi9fm69muAhRGoVhcXIzCokKkpZ1HZmYGMrMykSVWaXFycoI0nqnVFtcYxPXpA1cpJWfgMAzvqkH/8R9hzR LkDBCi19eeByLv92NxHTxjYMzBr3yC9ZN8YNSl44ty5/Cf975GScLxSeRo3D/My9gzlDvyxkH kzsWP0M/vvW/3AkR0TdlE7wj 6Lu5euxiNRhfWc2wvn3r4Hd7ywVVRlFZe0DUD/vy3C8gWj0EFKZdCn4bunHsZLG4/grIjySZE8r7i78PBYa/z2yTfYdjwbOrsgJDy8BMsfiYebGJbVomO0iVg8eDg G74eO/8TK8ZdVVz35Z PIjm7TJxUBpeo0fj74pfxYG XigIvDfW3k02r3TKeiAIUoAAFKEABClCAAhS4VgLNiRzU3Sa9Xi/qNejg7 9vmmrUS0xFmpFxEWEh4SITouIzpbKZj7XGMuReTKv7gpVbxawbeReQXm0vPTRFYqrOooYPNeoLkXVRPOjVXMQP3U05XlS/gDr3Yo1r1zyZ X3TzllemgXTY2nlokNJVhpKqm4yiqEjmWkorrpN1NrIuVjtwPoa0irbm3knW WarXoSKSghDdtIu3Ae 0WNCWnOXLVIxXF2dhFpQGHoGNMZLi4u4kucgZ9 Xm/aV1qk42SyqoN9rrxZSlsnMRGLXlxfTDtjyMH /23B2ZAnsPqVPnAXkSljtJeYnaUYe5 7BdPeAiY vQbPxgDHPvsv/jt1Mkp/3Ij/6y7GOBlLsP/FWzBldQlGPLYU8 K8YDj7Lf654Cv8IcYhIaKec4vUI8/4Gfj323Pg42LAha2rMH/Jw5jf40 8P9YdctGG47/tRWbMk3hrdk/Y5e3FOwtewrN7w3HbwkV4J8Ye6RtfxIIlD KF/rvxcpyIKrbkmJqUl86RETUfby4TKVilZ7Bx2SI8N90K0btXIcGptOH MkBRU5TvKUABClCAAhSgAAUo0OYFmpXZUE9vtFodpNUgijh6uHoi42IGPDy8RX1LEUAQ2xUKpWnl0j4ELPpO5oviKHv37UFuXi6Sk5PQpUs3UUglBh18OogvqcK0ShG3zZs3m bEHTJkiPgiS1PDaEyBCrmYO0ZaW7wYtNBopOImhUg/vgPr/r0GKfLumNnDWeQIiPlvxeIUMxQjh4gsgksXMWRvwJK15xA271e8 mCkSBQCBvcLQ mhYVi5ZCse lCkG VuxSvvJCNw9k944/EupmPLI87DSwQoqi41z226XsfhGNOxYq8endyQ MUwfLTjHDQiQCGNzJIWx8hBSBgotSkO/me/xpYVEZg0dSIGO4gPe6iw7au7sOu3VOjioiozOlpyzKXLVf5xjBqM4UOl6w4WBWNSsHn0F/jheJlIN2paf2uej 8pQAEKUIACFKAABShAgbYscOUZFLa2NiILXtRrcLAXPzw7w9fXVzzDySDVF5QyJyqe5678Om1Z8UZqm8UGKE6Lgig//7LBlDERHz8A48aMN903KXtCWrVarZgTVwznEFkSfcQwjEGDBonxSbawt7cXQQUNDh48gE6dOpu 1FIgo0XZFHsfQc wRyq/L8qAoXjk/SWYFiTGU1SOX6r ddKk7MIJvRduGhRgCk6YFlUQBse7Y mm3UjVjIV9yk4c03pgxIjwysBG9bPU906Nsz8uwTPLvsGfp9JRonSEtRjJoRJFV r T9YK7iFuQFkmcqSBVQ4io0RUmA0S8 DuySkViUXSbL01l5YcU/Mc4jI neCDd5FeKFKSWtzf2uflFgpQgAIUoAAFKEABClCgjQjU/RDS7MbJZXLTFKPSWmtppWvUOi83XBcBiw1QbPn1F1NwYvbDc03RM2l XCkwIWVISMM3pL9qEYiQAhVStkRpaamoSZGJvLw8zJ3zGF5dvkR8rkbnTiJDQUxRI52j2dkUUU9g3eJBcLW2h6tPAAK87MUgiytfjAapcIkcVmJqm Ys2sQVmDbrTSjufh6rX 4Bb NpvPfAw/ixgZMorEXVWFGbtlykSEm1ISBTwkZ8K4wihaq /9ZbckzNJsikVCzRS2m63Zb2t Y5 Z4CFKAABShAAQpQgAIUaDsC9T9RtJ02siVtS AKxjdc344MGTwMrq5uePOt1/HHnt2m7AgvLy/4 IhKq2L6GfOUoqaAhWiqVFhFWqR6FEeOHMGjc58Q09UcwklRaEUKXkhDQZq9OIeje6 eYmqbaAQ3MThhHdgXkcpMMWVM6uUkC 05bNuZA6voPggQSR8q327wRyZ2/3FRhA6avpSc2Y0kdMPfn7gbQ7t3Qkcx5U6EqNTa1peW9ret94vtowAFKEABClCAAhSgwI0qYG1tA61aUzE9hfRAxvWGMNCKJAFrkQDQ0sViMyh8vH0wZNBQZIisiH17/8TOnb JAIUPJo6fVDmUQ8qoyMrKQrnIolBWzOMisikqsiuOHDmKWTMfxmurlsHTw8uURSEFM5qdRdFMebn7MMybEYQJL92Dx2wW4nZRJPPop//F0uRgPLhiKNykJAbvkZg95t 4//n7sdBmPiZGypH086c4Ka7Vp4Hr2QX1EIGNNXjj1Y/hfktneCjScLZaCdYGDr6OHyla2N/r2GRemgIUoAAFKEABClCAAhRoQCAgKAhnTp9CaEQEVKo6hmY0cCw/skwBvU6HpNOnERgU3OIOWGyAQqobIc3UIUXmpKyIMpEFcfDQX/jksw h0 kRGBAoCmZGiXly3RAYGGgCko6RFikQIa1lZWWmtaSkWAwL8WoxYrMOFPPL9lr4FT6wF9OMvvoAvhFT1DhFjsRj617EIz3spUEWgNwDo5Z gReeWYhVL9yLj4pt4N85SHwmg7yBmUesO8/FW//JwPzlCzHtg4qMEBvXIPQKc26VoSfN6mdzdm5hf5tzCe5LAQpQgAIUoAAFKEABClw7gfCIKJwyHsfB/ftMw 65tH8BKRAVEBSCsPDIyhEMze21bM7DDxpXrFqN3JzsZh27/vtvMW3G/c06pjV3lr7kUrFLaTW/lv7qRNRGJ4ZznDp1EgUF ShTl4naFGWmIphSbQpplRbpvbR6i0wMqcCmg4ODaVhIi4pltmbH6jmX9vgSDB32EQb9sBMv9DDPx1HPzu1g843W33Zwy65aF9atfRtjx0 sdf7r/b9BtRrEDRSgAAUoQAEKUKCdC9T3/8vq67b0wKpUtt1nrPraze0tE5CetaXSCi0JSKWdT8Vba9bAYjMozFPKSEEFKRtCqiEhQUh/paKYnh6elQEJc1BC isN4ZCCEFI2hXSs9B NtZjtQzpf2wlOaHD6y/fwuyIEob4uUOQn4sflq3DW924sj2qPwYkbrb8t w eR1GAAhSgAAUoQAEKUMCSBKTns5Y8rFpSH9nW1hWw2ABF1UCDOTPCzs7OFJwwz JhppLeS9vNixSckFbpHOa/bSc4IVpZXojkPd/jte O4GKRGKqhcEH4oHvw son0dO db8AbeJsN1p/2wQ6G0EBClCAAhSgAAUoQAEKUKBtCVhsgEJiNAcVqgYXpEwIc8ZEQ9TSMdJ bSowYW6wwhMjFq8Xa0M9aEef3Wj9bUe3jl2hAAUoQAEKUIACFKAABSjQWgIWHaCoD6GpQYem7lffdbidAhSgAAUoQAEKUIACFKAABShAgdYRkLfOaXgWClCAAhSgAAUoQAEKUIACFKAABSjQcgEGKFpuxyMpQAEKUIACFKAABShAAQpQgAIUaCWBdjnEo5VseBoKUIACFKAABShAAQpQgAIUaIGANNNi0unTSE /AHVZWQvOwEMsTcDG1hY Pr4IDQ83TUjRkoUBipao8RgKUIACFKAABShAAQpQgAIUqFcg6fQplJaWYI oq QAACAASURBVMCgIbB3cKh3P37QfgRKiotx6MB JJ05jfCIyBZ1jAGKFrHxIApQgAIUoAAFKEABClCAAhSoT DihTQMGjoMtnZ2TZplsb7zcLvlCNjZ26Nb957YvnXLjReg0Ov1Il3oIi5cvIC0tPPib5opQufk5IKgwEAMHToc1ipry7mbbCkFKEABClCAAhSgAAUoQIF2IqDRaGBjYwujwdhOesRuNEVAuucatbopu9a5j8VmUHzy6Ydw8rKB3i8J2k75UEZfgFGbiRKNC7JKu P7H4pw2 QpdXaaGylAAQpQgAIUoAAFKEABClDg6goYweDE1RVuf2e32ABFt27dcT71HGyUnvjp7MewLw2GV24CLugPYp/NcnTJ Hv7u1vsEQUoQAEKUIACFKAABShAAUsRMF77AIVOpxWZ9unw9vGBykplKVJs5yUBiw1QdO3SDedSzsIqNRBT/VZj44m3sKP8ZdgbPTEu4EmkpFdUir0gxj7t/nM3cnKyUVRUiCJRuEOjUcPa2hoODo5wcnSCp6cnevfqAz9fP34xKEABClCAAhSgAAUoQAEKUKAVBK51eEIKTqSeT4G3tw/OiR zA/2DoFIxSNEKt/KancJiAxSS0E0jx2Dpspcxs csDC/5O7rb3o6srGz09u PlD1fIDk5Ces fh8JQ4aha5cuIihhC4WY7sRgNIi/ChOyUUT1MrIy8O57b2HqndMREhJ6zfB5IQpQgAIUoAAFKEABClCAAu1W4BpmUGil4ERqCkJDwk0/RtvZ2OPkqRMIDg5mbUIL oK1bHLSNtJBKysrU0vkItiwzWe2qUCmFCGzF9VDpUWKno0cfhN69OgFZ2dXGAzlSBMZFTt3/o4zYuqTktJSODg6onu3Hrj7zmkiI Pc1e9Z2X48HR CuPk7UXT1r8YrUIACFKAABShAAQpQgAIUuC4CUnziWqwarVY8y6WIH5vDoRTPiGXqMtPfCDHV5ZmkM1CrNdekHdeir5ZwjSv5sll0gKKy4zVyh6SsCGnp1SsOP/7ve jEF9bW1hbeXj6IFbUrbrv1DsTF9YVvhw6Qy QoLCoQGRRvi2EecU20NKBg/7t4dEIcIvz84CfW0O4JmPbcJmTqGzmFwgH 4ZEI93NGRXilkf35MQUoQAEKUIACFKAABShAAYsUkJ7Lru6q1WqQIob h4WGwcpKCa1WDZlMZvor/aAdHRWNU2dOimH UgmAq9sWnt/s2/Ivq0UP8TB3u2Z1WMOlAIWdrR10Op2IoKlNNSjKy8vF3xxcFFOTOjs7i9UFLi4uInDhbdrPnHnRGGd55veYfdvT2Oo3CU 8MhoxrgZkn9qHgwZ32DcmqorErA82YlZjF HnFKAABShAAQpQgAIUoAAFLFjgao/w0IofolNSzyI8LBJWSitoxdSmUna9lDkv/ZXeq1TW6BjTCUeOHEaE KHYxsbGgkXbf9PbRQaFOWNCul0Gg0EM7UhFbl4ePvzwA2RmZGHdh 9j3/6DKNTbYcl357FyG/D6L7l4d9N5nM9Rizha88q3qE9vwh61G25f8hLmThmLkaNuxl2zn8XiR7qjYnCJaIguE9uW3Y9hnQJMGRZB3cbhv/tKAG0iFvfzQ4 nD6BydlhtKjY8PxUDoqRsjEB0Gfkw1uwvgEHqkD4N382bgAHdwk3n8fPzR6eEmXh9T37F59I 9V1L qyhc0ufc6EABShAAQpQgAIUoAAFKHBVBK5exoKUOXEuNbkiOCEyJaT3UlCiuLgIR44eNv01BSnEdmk2j86duuDEyeNiuAczKa5 pkfLv0yN/d7f8jNfyyOrhOYKCgrx808/4YH7ZsHV1Q0DBw0W6Twa7PpzL1JP7ce/Om9AjHMWEgs88WlyF7z8UQHW/NO3Wa1V XSEH77B1k8241zXcQiykVU/3liC/YtvwV2rdRgzfwUW9nSDNiMbzgHWta9jLMSuZyfj/q8CMPvFL3CTbx62LH0ci 5egLBdr2OYXSGO/7YXGVHz8eayWNiVnsHGZYvw3HSRrrR7FRKcSuu/VmPndqnR7tqt4xYKUIACFKAABShAAQpQgAItEqj6Q3KLTlDPQVLmxFmROREZHiVqTSihEcM5pGBEUXEhzp47iwD/QJxJPoOQ4BA4ipqDajG8w9raBl3ExAkHDh4wDfuwtbGt5 zcfD0F2kWAwhyf OqEPcr10egb5YKzZ5NNM3I4OTmZsip /uELRPS6CYt2jUZuqQz2CjUMZdl4zPA8HGwmNuseWIXMwOqXjuG fz6I B/DkXDHNMy4dwqGhDpASkkx5v6KJW LaN68LVg1NwrVJrbRVr UIXszXvkoA/1e RFPTvIyHd/lpYvYEP8iPj5QjGHxFfs7Rg3G8KGxsMFgxAekYPPoL/DD8TIMDa//WoasRs49xLFZ/ebOFKAABShAAQpQgAIUoAAFrqeANDT/bEoyIiOiTTUmqmZOJJ8Tz2Ch4bARwYgI6wicELN4mIMUpaUloi6hHbp1jcX v/ahc8dOYrhH/UEKXcZubNmbD5/eCejqpUL1n3YNKDq5Db fkiFqyCCE2F/jgQmGIpzevhXJjn0xtKcnLj/UG1CYuAU7Uz3QZ1gsXCsmrryet6vZ177Gks1uX5MOMA/R6BHqCgcHB1Nk7LsfvkNZWZmp OXZs2ehLy1EB1crPDHBH7dGpSPCuA 60 vhZ0ht9hAPyGwRefdKbEvcja eGwfnv5Zh2sDumLB4J/LEuAx1yk4k6jzRb1Bg9eBEHb3RpP6JM3o9ds3tjoBLBTeD4v FRJQhPb308jCOKseqfDrBR8wBkl6ob/BaLTl3HU3kJgpQgAIUoAAFKEABClCAAs0WkDIoWnvNyskSQYiIyzUnxKQHRYWFSE5OQlhImGlKUema0lSjkaLmxJkzZ1BQUGDKsCgRwz6k4R7dunQTmRbnGmibAdoSMfMHdLh4PA06EZ2o2g9D2XkknikWHuUwWDtAJWv9fjbuJi5v5QBHOxGFqOYstsusYOdoB4X0pHsV7kFj52z2F6XKAe0ig8I0Z4xYft5zDidOpyFaqUPC0ATT0A5pkQpkenj74pdNG9Gje8/aXs0rQVF5vNwuAH1vn4e tz2EmcsnYczLj2LV2O14XGRsGEWMrUkDKKQvDBwxevnnmN 1asEWOex83EVGRW6t9soUSvFlM6BcandD12r03LVOzQ0UoAAFKEABClCAAhSgAAXarEChCEYEB4aIZ72K2ToKi4pM2fPhYeEiCCEXRTNTkF QD2dHZ3QQszZGRUbhWOIx0ywf0nCPkpJi2NnZi6BFfgN9NEBXJlLfFfawLjqOxNwQxLqIRy/TEeUoSDqBXLk9rAwalGqNkKukJz/xcGZUI v0YZw8m4FinRQ/8EFQTGeEetqIZ0Mdsvdtwr6iEMQPioajKVXAiLJzv2F7ojW6J8TBS1mKjFPi HNZKNXLoHLqgJDOXRDkYtW0Z8uaPTKKH72P/IXTGQUo0ZSLT WwdumA4OhOCHKrmRVS8 Dr875dBCiqjm1yFEUl5QofDBwwCFIaj7ScPZuEjl27I237TpwT2RQ1l YWyax5PGQOiE4YAN X38HRdA2su/ZCmGIdft eAm2PGkM8ahxsHdALofJ1OHpShsBbRVXZmievMSSk5sfS8fVdq9Fz1zwZ31OAAhSgAAUoQAEKUIACFGglAZ2oFdHai521LTIy0sUMjA6iEGahKJR5DuEh4VCI4ERqaircPTwQKjIpckSmRUrKOQQFBolMiggcTTyKQPHaRczkKBXLdHRwRP3tE5nqpSLC4NQZPdyPYtfhs4gZ4CcmJxA/RKsv4GSKDu5de8Du6C6UakTYwlYrzqVDwcld2J8iQ4dO8Yj1UqIoaT8O7tkNY3w/BNnJYOflAllGDsrEjCMOmhLojVrkXiyEzCUOAR5WSP99Jw5csENo9yEiKGFA5pFdOLrnGJwGdxI/aVeER0yeBl3FO9MP1npTPyp czdAb7hUmNRYDr2mFAVZuVA7dUGfGE oDMVIP3kAJ3bvRnl8HwSKNrW1xaIDFBt Wi/GHkVBX643uRrVBehgW4Sbxz2AVPVfKLcvg3rwDziTfwqnC/1x96TV GDtGjg6ucLFkIdY 5yK45qZQVF6YCkeX6tBz4GxCPWwRXnuCWx8Yy0uyLvioQhbyD1H4rE7O D2l /Gg XzMaV3BygLL6AobCzGh1X/Csg9R DRO30wZdV0zFTMx9R AbAuTsXJnCjccXcPODfyjWnwWtGNnLtdDPBpBIgfU4ACFKAABShAAQpQgALXRaCZj1lNaqMUgMjIzDAVybQXNSXCRM0JaSpR6Vr5hfmIjIyGVKfCQQQgpBoUUlDCWkwt2lFkMly4kIYkMRTE3c0dAQGBlx7q67qsGOKhLYfM2hHekZFwSUrEqZIgRFurkX/ DPJUwaL oAvOnzAir1gEB9xkMGizkZRaBvuYsejfzRm64mLxuhdKc7aKgp1lCIu1h0FkLzjLjiIlywgfkZGhE8 v6QUiDtLVD6qSczh1XgO3HqPRM0KFsqIS EZFIXXbcVzQ90RnVSm0VWIUVW0vhSRMHalru5WLmFnSy1r8gC CHz36oXz7NiSfUyOsix20 qtxl oybdo2iw5QHD12BHfdOU1Ezopx9PulUBTvx5jRo/Dl4cXoFBiHUMeuGOH9GNIcE7Hn9E84lboBsX720O9ag/52WpR3DYA85gmUlZZBqVQiLS3NNJVnw4uISsk84JT5HlbNX4lM0ygSBwT0HI Fnz2N6UFW4r0V v/3O7zn/n944d3HMWOp CbZBWPsC/0xtkaAAjJnDBT7rvV4BovXLcC9K0SwRemG6AmLMPbOxgMUkDnVf60Y/4bPzQBFw7ean1KAAhSgAAUoQAEKUIACLRcwz2bQ8jPUOlKpUMCvg69prVwuXUfKikhLO2 aKOG8 CsN8zCXA7CxVonMihDTWvO4Whcx6sWDu3gsc7aC3NYHId6JOHgkHVHdDTgrgggunTvDU1GK8 J5Slemg0wuAhSluSgxWsMvwAnG4jwUlehFsEAOR2cVDLnZKLdxhULjhg4iMHE8OQvo7Qh9wQXkG5zROcAOOpHxUSL6od33Db7YV71FijIFROIItKYx/mKp6iq9rnwvva5ybJXXRr0GWo1OfKyAs hXeV6OaJMzZEVSrY22s1h0gEJilGbokIILvUNssTc1D12jg/D8rvdw3u1H2IoviHnJlufil5wCzBjyBn4otoFzj14oLy9Htphy5vDnH4rqrmGmQEfjixxO3aZj8SdibWhnKz MmL9WrLV3enJXGp6sulnlj5Hz3xVr7X2BGNTcX Y Cd lTbq8cwPXQoPnrut63EYBClCAAhSgAAUoQAEKUODKBa71g6 PdwekXUwT2QHJ4iHcWQQx/Fv28C0FKETJBrlKPC4bZXAKCoTtH0dx7LQS2XJf9AsXwYVSqfCmqEihFpEMufQjtbTIREiiIvvCnOxgih2If8mUouaDXAVXXzfIjp1CDnpAcyFHZFXEwt9ej7J06Qgr PUbgS5u1R/TlXa2UJQVi75cEhWFQUVMRIzuKDdtMa/Sq3KdaLhMafq8pv/l/aSDDKY2yWUaMdSkovVt4d8WHaAID4vAxo0b0LlLVwzr6IS84wq4O1qbvhbpqblw83KEg5MtigvLUCqqsJaUJpuqmJ5JOiOCEaKCq0gFksYuhYdGiaEikfD1rRKFawt3h22gAAUoQAEKUIACFKAABShgsQLX9slXpbJCSFAwEFQVrAVtEAEK6TlfoRIzZIgaD3K7Dgh0S0LiuTI4dhwIX6UahRojlFKAQlMRoJDbusJedh6Z6SWI9r0UCjCUIi9fC7mTF wVRpSKZqnc/eGuOCSy zOgzDHCrVcwbPSlKFE5w04cny GfCjddFBXiRroC7NRJn5cr1zELB0O9mKOjtxzyNV3NM3WYVrKi5GdJ2pnOHjATm6EulqIwtymMuQViKwPR7GP6F5JrTBGVbtr/9qiAxSDBg7BH3/uxqGDB1AkAg6FohLrd99/i8cGf4afz6zBscM7kFeWLL4MHgiw6YZbImdi3769YvqZcNNsHj4 Pqb0H3d3d9P0pDJZ2ysScu2/ErwiBShAAQpQgAIUoAAFKECBKxeoOhLhys/W Bk0olhkWloqcvNy4ersCv8AUd9P/Cjd7EVkF5gCFFbi0V8UpBSTlsI9NBL DlYIjXYTwzmyRT0I8bO4QgZp6IRBZi SH9wRLIZq/HVoGw6Vh8PNqhxFF0/hrFT3Id4fKp14XhVJEkalq6gHocKBQ3 JaIU/4gNsoCsphEHlgUBfGxw69iv26sPhYSdm7ihXi1lC7OHj6wxltUdVpSmrwz4zCb/vMCC0gxNU0CD/QhLS1NYI6BMAm/IyFEvXE51Xpx1Cop2HyM8oR0n6adEmsU cH6zLSyra1Gygq3eARQco3NzcMCxhOLKzs5GbmyuqtKZg3/49 HV9MQb2eRCDXB9CnvhynhNz3MpLFdi//ZgIQsgxYvhIeHt7mzImpKlouFCAAhSgAAUoQAEKUIACFKBAawu0IHvhCpqQdj4VXuJH6C6duyJdFNKUZvGIEDN4NHsRGRRSwoIpg0JEWaR/FI5 CHezh6OxGEVihg pZ3IphUKtFhOIysQ/CjiF9USsbRKSTv6FVJHIoHTwRkR8PLp5QRTLVIvBH9JRCjj6 8LuQjIQ1g0dTNkYUnaEEq4RvRHrkIzks0dwRGRoQKaCg28nBEjBCjHtaZUamaI9IejW2x6pSeJ6x86K0IM0LakPIvv3QVc/JdR55uuJ08jVSD9xEPlqURXDVgRSesejp68CZbkiuMIMimZ/PRo8QKVSmQIN0hoeHo7OomDJ4SOHsXPnTlPkTJpqVCFqVEgFU0JCQhEdFQ0XFxdT1gSDEw3S8kMKUIACFKAABShAAQpQgAItFrjWGRTZOTmm4f9aMYuHs8iUP3L4EKSyAM1eFJ7okjAWbj52QEFRZQ1Ko7YEBZUzpyrg0mkohrv6wFFRBPHsLx71VXASAYU UfFwtLcxZT0Y9CILIjcHxdrLwRqZfSh6j gGD09HoDjLNDuH6VMRkHDy64i4qH5wtBPHm35LF5M0lBUgT4wPqR7ukZkCIGG9whDrZA8bke0hJVkYdOJ6edkoUYvQw6UDVB3iMKyHoyinoTKd01iuQVl DorEFKnVz9lsqVY/wKIzKGpq2IjpYwJEGo npyfiesehpKREBLTUpqEb1tbWsLOzg6OjI6T9OJyjph7fU4ACFKAABShAAQpQgAIUaE2Ba/P4q9eLIpNlZabnvXPnzsLV1RVJIrPA3s4eRUWFsLW1NU2s0KzFWIZcUXCz4UXMupF3AenVdtJDU5Qj1kaO1Bci62Jh7Z1E9kZTjjcfaNAWoSBbrLXPJLZc9jeIKU1zC8WUqHXu13Y2NvMutZ2G19cSKfAgfQGlVQpUcKEABShAAQpQgAIUoAAFKECBay9wrTIotFodpFUKSKSI4f3HTxyHjbUNPNw9TNsVCqVpveEWEY0w3wMpMCG9ZoDihvsWsMMUoAAFKEABClCAAhSgAAUocK0eh21tbUTGvKjX4GAPDw93GAyi1oKYZ9PKysqUOVExtL tP5pfhe L3B7B/Uaii5c7FOpMcYG2b3ADhpGuwo3nKSlAAQpQgAIUoAAFKEABClCgusA1fB6Wi8kQVFYq01pruYbtqHXt673BqENR nk0MuLkerey8voMULSZW8GGUIACFKAABShAAQpQgAIUaD8C0uwXXCjQHAGLDlBcvHgBHTr4QvprLQpfKq1FFdQqi15UJtGIIpnmfaS/XChAAQpQgAIUoAAFKEABClDg6gpYixoQWrUGKjFZAZcbR0Cr1ZiezVu6WHSAYt  fSImt9c0lMbbxxuBEd2qOaScPoWMjAzTNmlm2nHjGKBo6ReFx1GAAhSgAAUoQAEKUIACFGiqQEBQEM6I57HQiAioVHUMu2jqibifxQjoxfSuSadPIzAouMVttugAxZ59e7DoX//GvxY9g6jISHSN7VUNYov4D LEyZOV 4wbd3OLoXggBShAAQpQgAIUoAAFKEABCjRNIDwiCqeMx3Fw/z4xk4a2aQdxL4sWkAJRAUEhCAuPhF6va1FfLDpAcfLECdw 5VZTBoWdnQ2WL1tcCyEx8RjuuPM2lHTcgdc3F Gufk/Bxc6r1n7cQAEKUIACFKAABShAAQpQgAKtIyA9oEZFx6BT566QyWStc1KepU0LGMU8ptJ9v5KAlEUHKMoN5fj80y8rghTiVnn3uKPaDcvY/5np/WeffIERL6pwoOgb/PTme7ip6z3tM1Chz8Cvb63BgYgHMGe4N9rUzW3LbWvT/5mzcRSgAAUoQAEKUIACFLBMAelB9UoeVi2z12z1lQjIr Tg632sQq6ozKCQ2tIpyLXaam7fAw/eb3oZ2t0VcWMCTIGK6W9GiYyKR5FfKs0H204WXSo2rH4DXx8pvLb1csv24 n4EMTN31n/9DXXq23t5NayGxSgAAUoQAEKUIACFKAABdq7gEUHKMwZFKL pWnpFOBUbTXfvDVvvG16WW7QQ24ta4VAhQEF 9/FoxPiEOHnBz xhnZPwLTnNiFTb75qW/yrRcr3CzGhe6CpzZ1G/QOfnCqrO5hhyMK3dwTBr9t8/Flauy le59ErF8E7v05H0aFA/zFOKNwP2dY1d6VWyhAAQpQgAIUoAAFKEABClCAAo0KtKlRAI22tsYONTMoXlvxUp2neHLBPMBFBCjK9UjcngcHVxU6RDuaAhWBMU44kPgNfnnrQ3wzN6vO42tuLM/8HrNvexpb/SbhiVdGI8bVgOxT 3DQ4A77NixafvFr/GPup5D/40NsGaPEL09Nx4In mDI13eig6JGL UeGPS3QbCZuR4fHXgGcfEOVXYowcGP/4csp5G4p68LZCoXzPpgI2bVhOJ7ClCAAhSgAAUoQAEKUIACFKBAEwXaVQaFVIOi6mo2WPziy6aXepFBkZ2ZizjXu3Dgpws4tScHWjEVihSoKC4raCIZoD69CXvUbrh9yUuYO2UsRo66GXfNfhaLH kOe/NZdOnYsmQGhsZUZFh0HHovlv6agcpapiU7MTvaD0NWJVVu0519Awl MXhkV4lobBq mzcBA7qFm7Id/Pz80SlhJl7fkw/DpWsYy07jy4WTERcqfR6EHhP/je259XdDl34YyeWRmHxbf0RF9Ma44YFAfjZKzSesdqgMrv1nIMEhHxs/2o/Cqp8VHcAnP XCbcw09HQSH2gTsbifH3o8fQDq5rRNK4akPD8VA6Kk9geiy8iHsWZ/QWX/0Jhh/V3lJxSgAAUoQAEKUIACFKAABShgYQIWHaComUFRXw2KF158znRbpCEe0jJzyIv4 KEkDPSegX0bUyu3N/XeqXw6wg 52PrJZpxTiylEai7GYux97hZMe/UEOs5dg48/XoM5MYl4ZepkLP5LBB ashgKcfy3vciImoM3P/wY69b8G MUP O56f/E1gJxTUMeti6YjLnvZ6DPvNVY9 EbeGyIMzR1NMd8OeuQBPRxOIb3Pz KrONf4Lk3LqDv/eMRWM 4DJlzHGaMcUPRpnXYK13z0lK4/0P8XNABt0yLvRyQqdqnprTNWIhdz07G/e XYeyLX DHr1fjHtctWHT3AvyaL67VGoZNceY FKAABShAAQpQgAIUoAAFKNAmBNrwgITGfWrO4iHVoKi6bLn05qkFC7HlxUUiEHF5LlYHG1fcM3ARPvr9BdPQj YsViEzsPqlY7jvnw8i/sdwJNwxDTPunYIhoQ6QIj6GnC1YsvYcwub9ilcfjIRKbBvcLwylh4Zh5ZKteOjDsXBv4gUdowZj NBY2GAw4gNSsHn0F/jheBmGhGzGiq zEbXwGyx9KLSi9kNfTxz6ZAt21XNumUt/zH0gHMNfHo3YpUG4dfG3WDYlqIG6EQ7oMeNW H7 Ad7fmYeho90gMxZgz4ebURTyIO7qZFPnlQzZjbdN2ueVjzLQ75Uf8eQkL5Nbl5cuYkO8CB4dKMbQzr82bsjZiur050YKUIACFKAABShAAQpQgAKWKNCuMiikGhRVV/MNWf3m66aX9QUizJkVTb6BMltE3r0S2xJ346vnxsH5r2WYNrA7JizeiTwxXEKTsgsn9F7oPyjAFJwwLaogDI53F6MhdiNV0 QrVdtR5dMJPmKejPRCPTSpe5Fs8ELfvr4NBBiqHG7Ix67nJ HWL7tg8TvPIMEpEydT8qATyQqlfz2Pu2a g9Pa2u2yibkb0yPV2Prur8gSfTPkbMe7m0vRZcZkhNWTedGUtmlS/8QZvR675nZHwKVCo0Hx/0IiypCeXoqyq2RYu4fcQgEKUIACFKAABShAAQpQgAJtQaBdZVBI9SfMi7ujNQzpe Dg4ISHZj2Mr1/8h5itou7xD1JtipYscrsA9L19Hvre9hBmLp EMS8/ilVjt PxppxMJodChIf02qZfW6ZQQiEqNJRL3ZDJxOQlRhgMdfepZhO0x8UQkFVZuG39N5gaa43JwQrcM/EuTC5bhceLv8QBw0vwqCvgYBWCW2f1wZIn3sH/zo/DyB1v4zcMxPKbA1Dvl6cpbTNKd8MRo5d/jvldq2ZiyGHn4w756Zo94HsKUIACFKAABShAAQpQgAIUaM8C7SqDwlyDok UJ6Dci4/PzcX/ihdi5GJrKJQ1p6m4fFubnUFR8xshc0B0wgD44iKOpmtgHdgXkcpM7NyRisqkBO05bNuZA6voPgiwFidQusBfzCyScSQVpU2LMVS7qnVAX0Qos7B9U1JlYcqazar6XpOeiHSIWUvcpbCCDLbR9 HdL fBed1MzPzEClPm9IdLnUMmFPC56WGMtD INe9vwLo398Jh3MNI8Kz/q9OUtlkH9EKovAhHT8oQGBmJyMo1HP5OyqYZNtRhK4OeIAAAIABJREFUfkYBClCAAhSgAAUoQAEKUIACFiVQ74/gltCL mpQKOUy/Ou7v6NDFyt09BuLDg6RSCn5C2fLdtfZraq1KercocbG0gNL8fhaDXoOjEWohy3Kc09g4xtrcUHeFQ9F2ELuPgzzZgRhwkv34DGbhbg9Bjj66X xNDkYD64YCjcpEKAKwZibg7Bs5QLMW7kQd3RzgyH5sCi92bRF7jEMT94bjPEr7sJ9hgX424BAWBfuwZniuo 36zge8TaPYPWSr9H7/8YiTJmNw4fToBFxBpkIrGxdfxj/6BoHpzriDlLtir/f5Yuxb8zGCgThkTf7wKnOYEbFtZvSNrnnCDx6pw mrJqOmYr5mNovANbFqTiZE4U77u4B56YY1t1VbqUABShAAQpQgAIUoAAFKEABCxSw6ABFzVk8pPoT0tIxphO0Wi1KdWU4XvgrTpVtQbnWiOJcHdycvGrdJqMYbtD0xQC9zANOme9h1fyVyDTVk3BAQM/xWPjZ05geJI2TsEKvhV/hA/un8J9XH8A3RYBT5Eg8tu5FPNLDXgQEpMUaHf/xPl7NfwwvLPk71ksjPZTO8O8yEN3qHGtRo4Uia6OnKJD5mfuzeO6dpzBjpVQAVAW34DiMjXQyFZ2suih8JmHVZ7l4 pkXMC72UejF9b26DsfU137DWpd1uOW2 7Cg169YOcqj1rGALTrP Dti31qII3GPYFpkZWWNGle59LYpbZM5Y B/v8Naj2eweN0C3LtCACjdED1hEcbeKQIUSocmGNZ9eW6lAAUoQAEKUIACFKAABShAAcsTkM15 EHjilWrkZuT3azWr// W0ybcX zjmntnW fcis //RLSH979uwBcw0KT2cb5JTuxPoDT6BYkw 9UUQRDAp08AjA7GEr0CtkZGVTRryoQrexrji4Pg /LKijSmRrN5rnowAFmiWwbu3bGDt Yq1j2sL/BtVqFDdQgAIUoAAFKECBdixQ3/8va8ddZteukUDa VS8tWZN/XUOr1E7rugyNTMopBoU5iXYeySc8l5FWloaiouLceDQAbz38Wf4M kn3PN2NPKLs1GmLYa1jVQQggsFKEABClCAAhSgAAUoQAEKUIAC11Og5kiA69mWZl87OCTElEERFh6ODj4d0CXQuXIN83ZAYWEBzosAxZPzn4K0r7Qs2XAfHMKKMHrsSPx92gLE39Sx2dflARSgAAUoQAEKUIACFKAABShAAQq0roBF16CIjorG2vfeRWREJHx9/fHbji3VdKRt5WJOTmkfaV/zotFXrU1hELUp9HXWpmhdap6NAhSgAAUoQAEKUIACFKAABShAgfoELDpAIQUm vWLx65dO Hq5gobl4Bq/VTnp8Lezr5yH nDBwcsxzu/P4n0slxo9KWwUtjAwdoFt8QsQHZ2Njw8POqz4nYKUIACFKAABShAAQpQgAIUoAAFrpKAZQcoIqOQk5uDSPFXpVLB2tauGpPGzh enl6V 0gf9o0YgzCX3rh48SIyMjJMx3l6esLb2xuurpdrWFwlb56WAhSgAAUoQAEKUIACFKAABShAgToELDpA4e7uXkeXLm9SOTrW tzOzg5BQUGmlQsFKEABClCAAhSgAAUoQAEKUIACbUPAootktg1CtoICFKAABShAAQpQgAIUoAAFKECBKxVggOJKBXk8BShAAQpQgAIUoAAFKEABClCAAlcswADFFRPyBBSgAAUoQAEKUIACFKAABShAAQpcqYBF16Cor/OHfxoAnTrH9LGVrQe6jNpRuWthUSG  uoz8V4mpiDVw98/CP36xsPZ2bm 03E7BShAAQpQgAIUoAAFKEABClCAAldZoF1mUEjBia6j3kXXkW9CV1YRqDA7JiWdQQdfP4wYPgojR46Bo5MjPvrkA6jVZVeZmqenAAUoQAEKUIACFKAABShAAQpQoD6BdhOgyE3bAr0m/3I/DaUozT0KmUxWre9nkk4jNCQUtrY2cBbBiciIKOh0OhiN9RFxOwUoQAEKUIACFKAABShAAQpQgAJXW8DiAxT56Tux57t45F3cjMTfHqj0kkEDmaI6n1FEIVJTzsHLywcGgwE5udlISUmGq6ubCFjYXm1rnp8CFKAABShAAQpQgAIUoAAFKECBegQsPkCR NtD6DL0dQTGjIKdU7AIVPx2qas62Dq4iVITl7uYkZkBNzd3FBcXIT8/H2qNBqnnUxERHlEPTxvarM/Ar6v/g1c3ZUDfhprFplCAAhSgAAUoQAEKUIACFKAABVpDwOIDFL6R96Ao9xjU Rvh7tcXZ/Y8ZXIRJTBRVpAKWZWhG8nJSQgJDYVer8PF9AvIzs5GZmYmgoNCWsPy6p5Dl4oNq9/A10cKwdEoV5eaZ6cABShAAQpQgAIUoAAFKECBay9g8QGKwM5zkHJkDRR2t OFf/yGTb9OxIfv9MPC //AqiUyrFvbt1JVKpDp5eEFO1t7 Pn5mepQlJSUwsenQzPlDSjY/y4enRCHCHEe6Vyh3RMw7blNyGR6QzMtuTsFKEABClCAAhSgAAUoQAEKUACw GlGZXIlgmOfxp bvsSYaRMxaNxA3D/4EUx/YIx4PQgPDP2H6T7r9XpkZmXA2cUZSqUCGq3WlEURGBBQq5BmY1 M8szvMfu2p7HVbxKeeGU0YlwNyD61DwcN7rC3eNHGes/PKUABClCAAhSgAAUoQAEKUIACrS9g8RkUEom7/zAc/eMogqKDUJBXAK1aU/laXarGv97piFvfs8dWu4WY9X0IZnzlh3/ 1gtbMlbCVpvabFX16U3Yo3bD7UtewtwpYzFy1M24a/azWPxId9hLZyvZidnRfhiyKgm6S2fXnX0DCX4xeGRXiYiWpOG7eRMwoFu4KfvCz88fnRJm4vU9 TBc2t9YdhpfLpyMuFDp8yD0mPhvbM t0lR9Jn75zzQM7xlx6Rwdceenx/HLfeJ9v8VI1Jr31SJxcT/4dX4Uf5Q2u6s8gAIUoAAFKEABClCAAhSgAAUocE0E2sXv/Qa9FicTlRhSUoQzx5JRqi0VQzeKxeuzKNEW47DhLCaPmQo7aycYjDrojRoUaXKx4acNyD Qi/xBY DiG9NkcJVPR/jhG2z9ZDPOdR2HIJvqU5k2eiJDIY7/thcZUfPx5rJY2JWewcZli/DcdCtE716FBMd8bF0wGXO/csQtC1djUrQVLuz GK8cAazMJzfkYP//tuBsyBNY/UofuItzGqNDEG0bC VPm7Er/XHEBIrbWy72254CVewziOJEJY3eGu5AAQpQgAIUoAAFKEABClCAAtdHoF1kUFw8sQ16pXj6NsqQdT4Hxdqiy681RaJcZjlCdSJLoTAc/Yv6o2dxT3TVdxHZCuWI7NwbZ/d 2Sx9q5AZWP3SJNh9/SDiuwzBtP97G1uSiiuzH5p6MseowRg dDASxt6LRa/MQIfCbfjheBkM2Zux4utsRC38AEsfGo EoaMx9R9zMcK99pmdYoZi5JB49E 4CQN8reHa51Z0VxzDN79nid6JpeQYNp2Qo PobnBsZhyl9tW4hQLXRyDl7FlYWalMF6/6 vq0hlelAAUoQAEKUIACFKAABa6GQLsIUKTs/waa8nK8 fab Gn7epzPP4eNm37GrgO/Ias4A0UXjDj90z7s P5dbPzfYuz aRVSfl1v8vQO64fkPZ81z1Zmi8i7V2Jb4m589dw4OP 1DNMGdseExTuRZx6j0bwzQuXTCT4oQnqhHprUvUg2eKFvX9/LGRNNPJ/Cawim9lbg4Oc7kCUiFGViOMoBdQTG9/eEoonn4G4UaGsCSisrEaCoyB q rqttZPtoQAFKEABClCAAhSgAAVaLmD5QzyMRmSfO4Dnlr GC cviCEc5TA eDPkcjmMvYIx4 7 yDGkQSlTwmgU0QOxP6S/YrLOR2R3wdW/sxgGoRdTkqbD1tmnWZJyuwD0vX0e t72EGYun4QxLz KVWO34/9C5VCI0I9e2/QpPWQKpQggiJwOaQ5RmUxMk2qEwdCCCUXlnhj8twFQzl6HzRk3o fmbcgOvhVD/CoHhzSrj9yZAm1BICg4BDpdRUWXqq/bQtvYBgpQgAIUoAAFKEABClCgdQQsPkCRk3oQfh2HwMnDF0q5qAwpAhTiyb7irxSsEMEIf6MoXSltNwUopL X95EpVfAO7orCrKRmBygqb4HMAdEJA D78js4mq4BIl3g7wL870gqSo2RcG7m0ArrgL6IUH6A7ZuSoO7ZCTbNutdyeAyZhTEOd HdL3Ygc30aAieOQQjjE81S5M5tS DMqZMIi4g0Narq67bVSraGAhSgAAUoQAEKUIACFLgSAYsPUKQd RlB3UbDSmULe7cAEXyQsg4uraZsiRrvpc qbFOoHEWAYzCKMpPgHR7fJMvSA0vx FoNeg6MRaiHLcpzT2DjG2txQd4VD0WIWhiqEIy5OQjLVi7AvJULcUc3NxiSD6PqJBwNXUjuMQxP3huM8Svuwn2GBfjbgEBYF 7BmeKGjrr8mcwpDrPu8sNNSx/HGX0A5twciorR 007nntRoK0JmId16HRacIhHW7s7bA8FKEABClCAAhSgAAVaR8DiAxSnd36Ag tfhEyhEokR5kk9m44jkyugEGPbowbPbOJBBuhlHnDKfA r5q9EpkiYABwQ0HM8Fn72NKYHVaQqdPzH 3g1/zG8sOTvWC N9FA6w7/LQHTzaEIqg8jI6LnwG3zm/iyee cpzFgp9UsFt A4jI10QuOFQ2wQM2MOeq95Ens6zsHkUIYnmnhzuVsbFeAQjzZ6Y9gsClCAAhSgAAUoQAEKtKKAxQcoRs/bhE8XdITv4KegTtkhaJpTt0EGpYM38o9 jsBuNzeRVQ6nbtOx BOxNnCEzDYCty/ Qax17RSDJ3el4ckqH8ncJ G7tEmXtyi9MGD269gwu67jxTZV7XNU3VPpEoloD3tYzxqPgCbEROq5CjdToE0IcIhHm7gNbAQFKEABClCAAhSgAAWuqoDFByisbJ1F7QlgQM8olLqdq6gz0VQymSikaeWCTYlyuAbENvWotrufsRSpB08gHwXY 9Z8fO50L74d68PZO9ruHWPLmijAIR5NhOJuFKAABShAAQpQgAIUsGABiw5QGEQxzKKiIhO/UVvxt1n3QtSiMGgKRUkKMRNIdjbc3d2hVFowifYMPpw7DitPK DVazqWr3scXUVJDC4UsHQBDvGw9DvI9lOAAhSgAAUoQAEKUKBxAQt Godp2sELFzMAUUeiOOsMbF3DxUQdouCDNHuHoWK2DqNpxg5pNg/pr940q0fFe7GfCHCUFGSgXOQYHDlyBL169YKzs3Pjam11D sueGpbGp5qq 1juyjQQgEO8WghHA jAAUoQAEKUIACFKCABQlYdIBCLpfD2sYWyuAJ OXzVyC7NJ2nKQghFqM03eilWTuM5toUphk8qixyQRBwM2xsbKBQKKp/xncUoECbEOAQjzZxG9gIClCAAhSgAAUoQAEKXFUBiw5QSMMx/P394Tj1OZSWLhQJERWBieaKqVQquLi4wM7OrrmHcn8KUOAaCHCIxzVA5iUoQAEKUIACFKAABShwnQUsOkAhEykTUuaDtHKhAAXarwCHeLTfe8ueUYACFKAABShAAQpQwCwg5r/gQgEKUKBtC5iHeEitrPq6bbearaMABShAAQpQgAIUoAAFmiPAAEVztLgvBShwXQQ4xOO6sPOiFKAABShAAQpQgAIUuKYCDFBcU25ejAIUaImANMTDvFR93ZJz8RgKUIACFKAABShAAQpQoG0KMEDRNu8LW0UBClQR4BAPfh0oQAEKUIACFKAABSjQ/gUYoGj/95g9pIDFC3CIh8XfQnaAAhSgAAUoQAEKUIACjQpY7CwexcXF2LbjVxw/ngi9Xt9oR vbQaFQICamIwYPHAoHB4f6duN2ClDgOgpwFo/riM9LU4ACFKAABShAAQpQ4BoJWGyAQgpOuDi7YtbMh6BUVnTDaJTUTP9CxeuK9 bXxssbK3ml4MbhwwdNwY6xo2  Ruy8DAUo0BwB8xAPnU7LWTyaA8d9KUABClCAAhSgAAUoYEECFhugkDInpOCEVquBWl1mIpfiDxVBCGPla n95bXic/N76Ri5XI4uXbrh7XffZIDCgr64bOqNJcAhHjfW/WZvKUABClCAAhSgAAVuTAGLDVBImQ9S5oQUnHh49sO17t7KFSvFNlmN7VJ2xeVtUqDCYDCYzlNeXl7rHNd8g6EYZ//ciSSXvhgS7QSLKRBSX7vr2162H08Pm4yNAz7C5pfi4XjNoXlBSxPgEA9Lu2NsLwUoQAEKUIACFKAABZovYDHPwI117fNPv4R5lfaVyWQYOW4CRt08ETeNn2R6L61jJ03GuFtuxc2TbzO9b9liQMH d/HohDhE PnBT6yh3RMw7blNyGx5OQyg7BCW3DMD/96cjWsbLrnC/tTX7vq2KxzgHx6JcD9nWLXsBvCoG0yAs3jcYDec3aUABShAAQpQgAIUuCEFLDaDQrpbFUM6Ku7bL1s2VLuBUvBBpbr8 GsORlTfJh3S/CBFeeb3mH3b09jqNwlPvDIaMa4GZJ/ah4MGd9hboOg1748qErM 2IhZN R/cux0SwQ4xKMlajyGAhSgAAUoQAEKUIACliVg4RkUFfUlJPK31rxTuVbcAhkcxawc5lXaNvfRRxAS4FO5Pj7vsRbdLfXpTdijdsPtS17C3CljMXLUzbhr9rNY/Eh32KMQW 6LgF /xUjUmk vReLifvDr/Cj KC7CobVzMKpLgCnzwi 8L2Z8dA66Ki059fxABF/KzJi8vqDiE20qNjw/FQOipIyNQHQZ TDW7C AQfpUn4bv5k1A/65hFef0C0L3SU/hrbefxd Gdas4V0Q8pr26E7l1pGY03J9LDWvo pd2qbPd4rNa27WJWNzPDz2ePgB1lfYP6BZ qf3 6JQwE6/vya/on2mfTOx47UGM6hpYsU9QDPqMmoEVR8UZDI2bXmoi/1iogDTEw7xUfW2h3WGzKUABClCAAhSgAAUoQIE6BCzw9/7LvTAXxVy5YhVmPnS5DsW7a94w7eToYF 5szmDQhoGYl5un3Jri4Z5qHw6wg/fYOsnm3Gu6zgE2VTNwnBA1/GxUP60GbvSH0dMoCAuz8H 7SlQxT6DkHOvY L//QTfx97AN8P9YMhMQm6wV7WhDv73rcVbdwaIbTLY 4upT42F2PXsZNz/VQBmv/gFbvLNw5alj2PR3QsQtut1DLMrxPHf9iIz5km8Nbsn7PL24p0FL HZveG4beEivBNjj/SNL2LBkgfxQv/deDnOrtpXoeH iF0bu/6lRJVa7b50lfq2VzbCUNH jKj5eHNZLOxKz2DjskV4broVonevQoJTKfa/eAumrC7BiMeWYl6cFwxnv8U/F3yFP9K10MpW48FGTKt1mG8sToCzeFjcLWODKUABClCAAhSgAAUo0GwBiw5QSL01Tx3qUCUYUdc2s0ztoSDNNoNVyAysfukY7vvng4j/MRwJd0zDjHunYEiogyhsKYdrn1vRXfE4vvk9C38L7ABFyTFsOiFHx0XdYFu4AXlwRsKAQejdzVGEIGJrNcDWOxwxMaGVQQtD1ma88lEG r3yI56c5GUqntnlpYvYEP8iPj5QjGHxFadwjByEhIGxsEEc/M9 jS0rIjBp6kQMFjEO9FBh21d3YddvqdDFRVULiDTcH5GgkN3I9XtXXL9mu1FSz/bKzJLqXXeMGozhQ6X2D0Z8QAo2j/4CPxwvw9DwrXjlnWQEzv4JbzzeRXwuYj4R5 ElAhTSoi9Ia9S0 pX4ztIEOMTD0u4Y20sBClCAAhSgAAUoQIHmC1j4EI/L04ZK2RLmtWIa0YoMCvM2cz3MuoaCNJtNZovIu1diW JufPXcODj/tQzTBnbHhMU7kSfGXCi8hmBqbwUOfr4DWWJIRZkYEnJAHYHx/T3hGPsQ5vQrwtpb4jFuziv4 kB2teEddbVFk/onzohZS3bN7Y6AS0M/guL/hUSUIT299PIwiMqDreAe4iYunIkctTRziVhUHghyAUpySmsX4GykP82/fl29aN42lU8n KAI6YV6aFJ24pjWAwNHhJuCEzUXuxaY1jwH37dtAQ7xaNv3h62jAAUoQAEKUIACFKBAawhYdIBCmiK0IhhhrAxOSAEJaejH3 c8jNycrMp19iOz8drylQgKCq5cly1dLoZ4tJxRbheAvrfPw8ofd N/84Kxf8WjWHVMA8g9MfhvA6Dctw6bM8pwbvM2ZAePwxA/MRbCNgYPf74P29fNQee0DzBnbE/c/NIBFF KI9TZGtEh0UOMXr4Bv/76a5V1G94c417ndKQKa2mAiAHlhksnlilhI/JljOXSuepe6u1PC65f9xWavlWmUEIhtV801mjQi1dyWCnquVktMW16U7hnGxDgLB5t4CawCRSgAAUoQAEKUIACFLjKAhYdoDAHJ6S/Do72lat5iEfNqUcly6r7mW3N 7fYWuaA6IQB8MVFHE0XAQrxMO0xZBbGOPyFd7/YgQ3r0xA4cQxCzJOKyB0QlvAAFn 1A1/d44HD776FQ6XSYdZwECkCpXnVsyKsA3ohVF6EoydlCIyMRGTlGg5/p6swSqdGfxq9fj3trq8/zXVW XaDPzKx 4 L9Web1Gfa3Itx/zYpwCEebfK2sFEUoAAFKEABClCAAhRoVYGr8HTbqu1r8GTmoRziN3ZYq1SV 5oDDjXrTUjbq 5XcYCsso5Fgxer8mHpgaV4fK0GPUW9h1APW5TnnsDGN9bigrwrHoqwNe0pc4rDrLv8cJMoZnlGH4A5N4dCaqEuZT3e3wbEdPKDveY8diSKWTqcvOEo3QmrAMRFKLHuk5fxVvd70QkXkOV9E27tOQKP3umDKaumY6ZiPqb2C4B1cSpO5kThjrt7iIoWV7Y01h 5ZyPXt66n3T3q2d61ee1VeI/E7DH/xv3P34 FNvMxMVKOpJ8/hTSvQ5/GTJt3Ke7dRgWkIR5hEZGm1lV93Uaby2ZRgAIUoAAFKEABClCAAi0QsOgAhdRfczBi2t1/E 9kpiEb5m1SvYmay9 mzajcZN6vecM8DNDLPOCU R5WzV JTClhAg4I6DkeCz97GtODzGkSNoiZMQe91zyJPR3nYHJoRQBFm3UIP766Bv/KkCpFKuHReQyeWT0Xnayl83hh7IuLsW3WIrzwwCYRsOiAwU/1xMRekRj43  w1uMZLF63APeu0ItD3RA9YRHG3nmlAYqm9Me54esr6293nf1pZoACcg MWvoFXnhmIVa9cC8 KraBf cg6W5DLm5ew6Y1vwF8b4kCnMXDEu8a20wBClCAAhSgAAUoQIHmCcjmPPygccWq1aJWQ3azjlz//beYNuP Zh3Tmjsvfvl5zJ3zGLKzs0VAQlSmNAUnKgIU5kDF5b 1r3x5WIcMbm5uWP7aUjw575 1d7ySLSV/YsHAqUj 53Z8fKuPqKnApbUEtMeXYOiwjzDoh514oUdF1kprnZvnaVsC69a jYmTbzc1SqfTwsqqItj37VefX9f/DWpbSmwNBShAAQpQgAIUuPoC0v8vGzt 4tW/EK9wwwmknU/FW2vWiJ/wLXjRarXw9fWFXN7yUhrl5eUoKBDDLFprMZYi9eAJ5KMAe9 aj8 d7sW3YxmcuDJeDU5/ R5 V4Qg1NcFivxE/Lh8Fc763o3lUQxOXJmtZRzNIR6WcZ/YSgpQgAIUoAAFKEABClyJgMUGKBQKBYqLi5GWlgYpyFBRj0LMUCHNOCFN4yGWmtvq kw6j6enJ5TKVqLQnsGHc8dh5WkFvHpNx/J1j6Mrn6Gv5DsKlBciec/3eO27I7hYJIa3KFwQPugevL7ySfS0v7JT82jLEOAQD8u4T2wlBShAAQpQgAIUoAAFrkSglZ7Kr6QJLTs2QhTMS01NgZ fv2loR13BB/OZawYsam4/n5aKDh18odfrrzxQYd0FT21Lw1Mt6xaPqktA4YkRi9eLta4Pue1GEOAsHjfCXWYfKUABClCAAhSgAAVudAGLDVD07zcQP2/6Cdt/2wqDQapB0bJFGh7i4uKK3j37QMqm4EIBCrQ9AQ7xaHv3hC2iAAUoQAEKUIACFKBAawtYbIDCw8MD48dNxIULF0xZDy2pQyEFNoqKiuDl5WVapUwMLhSgQNsT4BCPtndP2CIKUIACFKAABShAAQq0toDFBigkCAcHB0RGRra2Cc9HAQq0MQEO8WhjN4TNoQAFKEABClCAAhSgwFUQaPn0F1ehMTwlBShAgboEpCEe5qXq67r25TYKUIACFKAABShAAQpQwDIFGKCwzPvGVlPghhIwD/GQOl319Q2FwM5SgAIUoAAFKEABClCgnQswQNHObzC7R4H2IMAhHu3hLrIPFKAABShAAQpQgAIUaFig3QUoNBo1tFqtqdcFBfl4c80q/PDDt6b3UlHM8 dTodFoGlbhpxSgQJsS4BCPNnU72BgKUIACFKAABShAAQpcFQGLLpJZU0QKQHzw4fsoKSnBrbfchnPnziKuRxz2H9qPrKxM7NnzB86nnYevnx/GjRlf83C pwAF2qgAZ/FoozeGzaIABShAAQpQgAIUoEArCrSrDAopQCFlTUyfMhVff/MlDh85hOjoGIxMGIUPP/oAWpE5MUlMTVpYUGAiLCwsgE6na0VOnooCFLgaAhzicTVUeU4KUIACFKAABShAAQq0LQGLz6CQAgwfrFsrhm8YERsbCyulEs4urnho5sMoN5QDunJ4e3qZ3ivFZ qyMuSLIMY3IoCRej4FdvYOuP/eB9rWXWFrKECBagLSEI wiIophau JhMFKEABClCAAhSgAAUo0H4E2kwGxdatW1ukWlZWKoZ0FGP8qLEwaHW4dcKt0Ks1plUpV0BhbQWZQg65TAZ1QSGsFEpMuGk8YmO64Naxk2CNiEP9AAAgAElEQVQUWRdcroGA7jy f Z zP3gDJizcg2829klOItHO7uh7A4FKEABClCAAv/P3n3AdVX1fwD//AZ7b/THEhBEHCgucO8SK9MyZ4 rNHvMpk0tW2apmf/MUh9HppWrNI0sF1ruiQO3DJG992/ z/2BhiiIigr6Oc/rBtx77jnnvi9Pr35fzvkeClCAAjcQqDUzKMaPH49vvvkGXbp0ucEwKz9la2sHTw8vFIpARfMmzSETgQi5QoGEuAScvXAOsQmxxpu9RR1/b194e/vA1twCMksrHD5xVMy6aAGtVgu5XAQxxHFfiz4fsft24YJ9O3RpZIv7PJqapdBl4ODGSOx6YiIYEqpZ2oehNS7xeBjeMp RAhSgAAUoQAEKUOBhF6g1AQppqcbEiRPx1VdfVStIIe3E8deWTcZ8EtnZ2WjZNAR6EWjQGYAtOzahoKgAoaGtEda o/EdJ6ckYf/B/ThxOgZdwjtBYTDAzdEFG7ZtQtSO7bC1scN/nh0BMzPzavxOiFwXh5bgg6nfYsOBRBSKO8xcA9H qXcw880ecL1d1aJozBgxEscn7ETHexWg0MZhQe9wfHCqssduji8O/oYh7orKKvA8Be66gEZTujOP1FH57 96x yAAhSgAAUoQAEKUIACFLhnArf7UfquDFAKTrz88suYPXv2TYMU0q4c8XFx6NO9N6xFHgkrMSNCrOPA5s1/wNHVFf06DrhmjPb29mgUGCSCEduwded29OzYBU7Wthg1YIhxh4 NO7eK2RfVm7OgS12P/z49GdtVT L1mY8iyEGP9LMHcVTvBKtaJVqN16RwR99Zq9AoV TrQAlOzXsBHxzuiE/mjoSfiTilsEOgI4MT1ZBkFQpQgAIUoAAFKEABClCAAhS4A4HqfSK/gw5u5VZpeYcUnJCCFDfLSVG/vgo YrnG7gN7YCmWbGiKinH 3FkUlhSjswg VFY6d qKIm0Jzp0/a8xTUVxYZAxOPDVgIExNTSu77Zrzxec2Y3 xIwbO BwTB0WgV /HMOS/H2D6Sy1ghVxsHd0QqrDpiLn6R181YqaHQdXkFezNz0P04gno3dQTKrHdqcq/HUYuj7smL8PZTzvCR7omjgEbS3ccgToBkZ8OQ4dA6bwXmvYaj/mHckqXS2gTse6NJ9C mV9pmypvtHjybSxY AH 0715aVsNwzH8y13IlOIQ5YvMDPWah6Njx47iCEdIfTGDxNITLcKln8UR3gyusmRsnTESXYNKx9S46yjM2pZybS4JTTXqlO9Xf3OHar0MVqIABShAAQpQgAIUoAAFKECBB0KgVgUoJNErQQppuUdVQQopX0Tr1m2RnJqKvLxcyMTPZy9eMC7ruFlp1aoNYi8nilwVYlePwkIoxdfYuFjjFqXVKabujaFCJrb/uAVxxWJNyTXFGs0eD4Eyfgt2J2tLr4j8C4d2xMM0pBcaxH2Dce/9AZsR3 KX3zdizbxJeLqNK6TJCleKx jFiNy8WcwG2YIvO1kDhlzs/mAAxiwtQsRnq7Bh7TyMcNiKqUPfwrZs0b8 F6f PoDUoIlY8NNKLJ/3Kpqc/l4sQdkGh6en4n8rluDzpy2wfcY4TDsoLUi5hWLIx4FP ovgxmk0njgfK1bMx4SgGMwcNgDTDxeUNlSdOhW6VJ 6ucMtjJJVKUABClCAAhSgAAUoQAEKUKCOC9TKBQlSkGLIkCHGnBT79u0TeSHMrmP 7bdfkZh4CR1btYWpovTjfWJyIrr26Hld3Yon3N3qYVvmZhjE/AOZmEXRo3lrnEuIx4/HjmLcuP9WrH7dzyYNRmLe5ycx p1xCN/gj27PDMfIUYPQxddaJLaUw6HtU2iheA2//JOG/3jVg6LgJDaflqPx1OawyI1EFuzQrUMntG5uAxlCrmvfws0fQUG V4MW rQtmLk8BWEzN DNJ12NyTObfp6EyPDPsOJIPrqHlzZhE9AJ3TqGwBxt4BG7FlvnNMSTw/qhs4hxoKUpotYMwe6/E6BpE3hNQOS6AZQ7oc/YihmL4 D3xjZ8OS4A0hyTzmF KIzujq9nbMcLP0TAoRp1nCp0os1JvKlDVePiNQpQgAIUoAAFKEABClCAAhR4sARq3QwKiXf37t1Yu3YtlixZcsPghFTnclKiWLrgCSd7B hFwkwxzcD4v oWhdjpQyZNPtDocDktGXHpyahXr371bpdZIGDo14iK2YM1n/SF3eHZGN6xBZ6YvgtZYosKhWsXDGutwNGVO5EmllQUiSUhR4ob4vH2LrAJeQETwvKwuH84 k6YibVH0m 67WZJwj6cFwlAd09sAc ypR/e4e8jBkVITi68wa4YJnBq4Cg6TkXGlRkeps7wtgcKMgpRcZVHVQ9dEr8bp7WuaN/J0xicMBZTb3QOd4JaPH CoK9OnYp9WN6GQ8U2 DMFKEABClCAAhSgAAUoQAEKPDgCtS5AIQUnpBwU3377LVq0aFGp9KBnhsLa0REbtm9Bdm4uxFQEeLrXN 7WcbMi1fGq7ym2F9UgtzAfR POY AzQ/DEE/1vdus11 UiV0O7gW/g6w178PsbPjg05xXMPSk sctd0Pk/HaA8uAxbUooQtyUK6T590UUlZnpYBGH8yoPYsWwCmiR jwkRoXjs8yPIryq2InYcMcAGj34ViW3btpU7ovBdH6cbbkeqMDMRJHro9GUNy5QwF/NlDGKbk6q6uiWAO6l8Ow530h/vpQAFKEABClCAAhSgAAUoQIFaLVCrAhTVDU5IonZ29sYkmXq9DjKd CCu1sLfxw8HD y7KfiB/Xvh7 kDdV4hTLXio7 ZBfbt3SPaEtMfbqfIrNGoWwfURxJOJEuzOeRw7jIWfawPY9GqnYjcmAivfn3Q4EqiCbk1/Lo9j lrdmLNCGccW7QA0VJqCLkZrEWOysKsa2dFmHm2gq88DyfOyOAVEICAq4c/PGzv7iodM692CFCmYtfOBPyb8zMOUbsyYNKoLTzF6pvq1LnCahDGVwMklTnczjvgPRSgAAUoQAEKUIACFKAABShQpwXu7qfbW6SpzsyJK02q1WqsWr0SHYNDIBezBPJT0 Hn3xCnzp0xbiUq7dZxoyJdc3dyg4ujE LPH0a2mEHhbWGP42dPo/nlFvDw8LzRbdecKzwyC68tLkGoyPfg62wBXeZpbPp2MS7Lm GFhhbGujLbNhg7RIVHZr0mlmd4YsJjvsYlEpr4jVgaBQQFq2BVcgk7Y8QuHbZusJHehIkn2jRUYtmPX2BBi1EIxmWkuT2Cp0J74pXB7hg091k8p5iEYWGeMMtPwJmMQDwztKXIaHH3itypO94Y6Y0nPh BV83fxcAg4MRPH2PWRR Mm9MVjmLmiqwadaCwhbsYaFLUr9h21hfdzHZgWWUOd 9x2DIFKEABClCAAhSgAAUoQAEK1FKBWhOgMDExuemyjvKGBoMeVlaW2H7sAAxiCUTLBo3QzNoKEX0ew19//YEfli FtFuHlBBTKtKyDmnmhMq1Hjp26ozYnXuRkJmGCyXZsLe1h78Ibri4uFbjNemhlTnDNnUJ5k76GqnShAlYwzP0cbz782Q8631lmoQ5gkZOQOv5b2J/4wkY4FuawUGdFo0NX87H ynSfAQlnJv0wZR5ExFszAPqKnbpmI6osVMx7fnNImBRD53fDkW/VgHo PE6LHaegunL3sKoOWJ3EKUjGj0xFRGD726AAmJ2SKt31 B7q7fx0ZfP45c8EU8J6IVXl32Gl1paSStrRISiGnVMvDDgndHY MpiTFnUF62fqsqhGq BVShAAQpQgAIUoAAFKEABClDggRKQTRg/zjBn7jxkZqTf0oNtXP8rho8cc0v3VFX58OHDVeacuNG90pIM6Th85CAunohBS09/WLs6wyXAFwkXLuJ87AVcvBQHU1MTeNfzQqPARrCzt0fC3kMoSM9EQn4WNI7W6D9g4I2av/NzBfvwVsdhuPjODqx4yh2KO2 RLVDgoRNYtnghIh7vd91z1/S/g67rgCcoQAEKUIACFKAABa4RqOy/y8hEgTsVSLyUgAXz54s/4deSUlVCzMqGKJeLTT3FcfjwIQQ7q3Ah9TJkKZfRICUd9l4qtG3ZGp27dode7IBRlJUjghIZOL37MBLyMpCtKYarwgLn4mORm5sDW9saWihhKETC0dPIRg4OLJiElbaj8GsEgxOVvUOepwAFKEABClCAAhSgAAUoQAEKSAK1JkBxu6 juLjYuMRjb wpuDi7IisrE9ZKU5Tk5yOvuBBWClNIiRnz1MVQiOyM0t4WJ7OS0ahRkAhOxMPS0krs5qGDTqeDtPXoHRf1efwwsS  PqeAa6tn8dWy19CsNC3FHTfNBihAAQpQgAIUoAAFKEABClCAAg qQJ0OUEjBiXwRiOjWtacxMKETu3kcOXIARSIYcfjyBRRq1PCzc4azmRX2psZDJhImNBUJKaWv1la2aNM2HNbW1igqKoJSqYSNjY24ZsyqcPvFrCnejkrE27ffAu kAAUoQAEKUIACFKAABShAAQo8dAJ1OkBhZmYmZj9oRbJMK OLKygogIWlJQ4nxxuDDfVd3BCbkohCseOHjY2dMRhxNOkSzEzNjPdYWFgYD6mudO2OgxMP3a8PH5gCFKAABShAAQpQgAIUoAAFKFAzAnU6QCEFFKTAghRskJJlajQasU2oB5KTk4w5JaStSPfs/geZOZnoEt4dDg6OxpwVUtJMa2sb46wJaVkHAxM188vEVihAAQpQgAIUoAAFKEABClCAArcrUKcDFFceWgowSIEG6TA3N4ezs/NVD39//9u14X0UoAAFKEABClCAAhSgAAUoQAEK3CMB T3qh91QgAIUoAAFKEABClCAAhSgAAUoQIFKBRigqJSGFyhAAQpQgAIUoAAFKEABClCAAhS4VwIMUNwrafZDAQpQgAIUoAAFKEABClCAAhSgQKUCD0QOivJPl5tfhH3HYnHoZDz2Rsfi5PlE4 XGfiq0beaDlo290KapD2ytLSpF4QUKUIACFKAABShAAQpQgAIUoAAF7q3AAxWgWL/1KN6e/Qu8PevDzc0VQU2D0btXJ6NofFIGYhLTsf3QTsQl/IxpLz Jx7s1v7fa7I0CFKAABShAAQpQgAIUoAAFKECBGwo8EAGKzJwCvPb5akSfTcIjvXugnpsD1Fo9SoqLcepsHLQ6PewcnOHf0A Bgf5ITc/G1G8j8cuWI5g56Sk42lndEIcnKUABClCAAhSgAAUoQAEKUIACFLg3AnU B4UUnOg6YiYSc4BHHu0FU0tLxKUWIDW7GJbyEkx4ug1eGdQO1ko10nKKcSmjEAaFGXr26mm8R7pXaoOFAhSgAAUoQAEKUIACFKAABShAgfsnUOcDFNLMCQc3DwQ3C0ZmvgbZ4jAYAL04nu4ejAYqR MhfS dgziyCjQ4fTkPXv4BxnulNlhuIKC5hPVTxmDi9 ehucFlnqIABShAAQpQgAIUoAAFKEABCtSUQJ0OUEg5J/afvISAoCAUFGmgEUs59CI6oRORCL045Ip/V7DI5AokpBXgeFw2zibmGmdYnJeCFH4Bxjaktu55KTqEyeEN0GbSLuTd886r0aEuAwc3RmJXbCH01ajOKhSgAAUoQAEKUIACFKAABShAgdsVqLMBCmm3jre XAuvQCnRpQwlGhGcKAtMXAlSrPknAReS83FOBCRmrI5BalYRNBqdmGFhkCZSGPNUZOSp4RnQzNiW1Ga1ivo0ZrZXoeFzO5F/zQ0lOPZha6iCX8bewmq0pLCGh5jF4a yg0k1qtfWKrrk1Rjoo4IqYhHiONWitr4mjosCFKAABShAAQpQgAIUoECtFqizSTKlrUQtrO3g4uyIgmItZCLUkhl/ATKDDnK5zHikxcmw8tetSM28NowgvREzK1s4efiKJSFquNjZGNuS2uwRFnTvXphpAMZ vwlj712Pd6EnNc4um41/DHZQHPka86MH4ZNQy7vQD5ukAAUoQAEKUIACFKAABShAgQdZoM7OoDh0Mh4yEyvIZKVLOpQiQjF/ylNY/NFgLPpwEP73wTOYP3kANswZiQPLX8LBHyfi8E v4OjKVxG96jV8996Aq 9VrdUZ25LarNGiTcS6N55Ah b UKnEDAOVyJXR7Tl8sz 7dMmEOgbTw1RoOfkIipGLrWMaQhX2GU6qr4xCh0tLH4HKdzj yBJzPtQJiPx0GDoESm15oWmv8Zh/KKe0LW0q/vpoOHqEijaMfTXG4J8SodXnIXrxBPRu6ll63r8dRi6PK8spocH5hUPRyk qLw5xbeBHm5B0C7MgDLl7MHdpIlpNXYjJIen4efZWpFdcD6JJRdTsMegeXDoG7 Z98fHBssSkVV2r6nmreq6qrtXoC2ZjFKAABShAAQpQgAIUoAAFKFBTAnV2BsXeaDGDwsZWbCEqEmKKpR0l4pv3lx1FoIctGqps0MBdHG5WsLYoXTyRL3JUHIvNxpELWTh8LgMxCblXDTVag5hRYQOpzRot lyc vsAUgIn4bvZIbAsPI9Ns6fik2dN0GjPXHSzKN bDZo/EQpl5BbsTn4djb3EqzFk4/DvMVA0H42WtnnYLQIuY9Z44r frcIj9bOwddZrmDr0Lfjt/gbdLTNw6PetiG3wOubNbAsn0behkSv0p2Zh3Ht/oP6r3 KXHiroUy8g08e1bEmJAi7hI/Hhwglwt9fj8va5mDRjPCa13IelEU64efRKh7S/5iISEVjYvy2a1euFGc/NxbqERzDau xXy1CAQ9P7Y8g8DfpMmoN3Qx2hTkmHnaeZeL6qruVi9weVP2/Hy99U lzqU5Vfq9H3y8YoQAEKUIACFKAABShAAQpQoMYE6myA4uT5RHg38RS5J7SQy2RQiBkUUk4JKfBwJjEPKdklcLM3w3cvtTVivb8sGific4z5J6QkmiYKOXTG2Rd6cZ/OuOTj5KlTNQZbviGbwM7o0TUE5uiMcM94bHl0FX47VYRuLcrXksGhzQCEKl7Ful3pGOHlDnnuIaw9qEeTKWFwyNyCmctTEDZzA9580tUYPGj6eRIiwz/DiiP56B5e2pZtUFf06iL1VVoK4xKRBTt069AJrZvbiGwdIeU6lcO2cQ/0aVx6qmWwI2JWdcfynXEoEQGKa In5Yd65XtNPNbO2wP7AevQzlYB845j8aRTPyxccRrD3g6GCEHAkLkNMxZehP8bWzF3YiBMy7VjyPij0mv6tKqfN8ys8ufS5lR 7UaPwXMUoAAFKEABClCAAhSgAAUocP8Fbv5H8vs/xkpHIOWZUBjzTcihUEjfy425J4zbiYryWDuPq/c HuYJMxMFTE2UZV/F90oFTMQhtXGviql7MNzFnh3JudrrupS7dMKQ1nIcXfU3MsQyibzDq7Fb3QyDu9eDNmEfzmu12D2xBTyNSzhU8A5/HzEoQnJy5btsWIa8gAlheVjcPxx9J8zE2iPp5bYMLUbsho/xbI9QNPJWwTOoH76LEytJitTGJKI3KyVnfsSS094YNjS4NCBi2Rwjhvgg/qelOFq2gqM4fhdiNC4I6 R1TXBCaruqayU3eV7zKp6r6me 2VPxOgUoQAEKUIACFKAABShAAQrcD4E6G6BoLPImlBTkwdxUWRakEAEKMStCKY4SMZPC1tIE3Zq7G2dLSMs72jd2gau9xTXBCVMTuQhSyGFlbgJNYT6kNqtVZCYQt0BdUFRh 00dirLFTiAm5jCpJOYhE1ufKsRduhtFAOQu6DSsHeQHViAqNUvkzYhCcajIK GuEFMRpJ1HbPDoV5HYtm1buSMK3/WpYjmGRRDGrzyIHcsmoEni95gQEYrHPj CfCmlRcwcDB/7HeJbvox5v/6JTaumo3 9agmISgU4uvRnJOjP44uuPmV5Lxqg  xYIH09Fu4Vs1WkpsQMFYOYt3FDjqqu3ex5q3guVHWtuo/HehSgAAUoQAEKUIACFKAABShwTwXqbICibTMfFOXnGmdBGGdQSIe01MP4VY5OTV1haabAX4eTsWJ7vAhcyNA7tJ6YQVE6c0IKTkizJ5QKsTRBBDnURbmQ2qxWMXFGcEMraKM34FBOuUhD4Rn88XcWZA1CoZLWN9xykcOlq0gmaX4Ai39ei0Xbdeg4pifcRHzCzLMVfOV5OHFGBq AAARcPfzhYXuTlTpya/h1ex7T1 zEmhHOOLZoAaLFNqgF5/fgAprjxdeHomuLYDRuFoKGdtcP2mAMJFxbDLn7sGh9Ohq tAwbIyMReeXYuBTjffPw18IoY7JMadx ilT8syMeV3N/ljV1s2s3fd5KnsvYfFXXrn9EnqEABShAAQpQgAIUoAAFKECB yxwk0 293l0VXTfsrEXVm NgVzMmJCLJJdSHgrpe MyDxGM6NbcDRl5akQeSEaxWo9TIjeFdO73/UnQiLoanfQ3ffHBW/yl3kIEMvTqAkhtVq/You2EUfD//f8waqACr47uAV9lMvaumIWFia4Y/EVPuNxm6EdmH4YxjzlgwOdTAIf  LGjY2mySpeeeGWwOwbNfRbPKSZhmLRkJT8BZzIC8czQliLLxI2LJn4jlkYBQcEqWJVcws6YHMDWDTbizVt6t4QH5uPbL1fAqX8TOCsSEVt R1aFLdxFw0lRv2LbWV/0bmhTljjTgMydi/BXXmO8NagTQq4kxDQOQQPrwYH4ZtoibE6JwGD3Xnh1cD0M/GIoxukmYVDrelDmXkaeXwQeb1TVtaqf1/JS5c9V1TPfWIlnKUABClCAAhSgAAUoQAEKUOB C9TZAEWbpj7Iz81GfnYWHJ2cUCyWdUgLCUTsAT6u1vB1t8b8yAvCVyZmSCiwcuclvPNMEFoFOGH/mYyyGQFi0YSFGQpyc4yH1GZ1i0Wz17F6lR0 /GQhZr2yEiVQwqmx FC9ZCpe6mxfjR0wKuvJGi3HDIPPj7OhHfQ82tqWLY6Q2aHjx uw2HkKpi97C6PmiBwWSkc0emIqIgZXHqBQp0Vjw5fz8X6KNH9BCecmfTBl3kQEixke8iYTseCjFEz66l0M/740J4a5g7fYdtROLEMRxcQLA94ZjY2vLMaURX3RZVpoaeJMfRq2L96B4sbvoZeq4q QCTwfHYjATz7Ckt8v4enR3mgvxr3E6T1MW/QaRs4S0yosfRAxrT0igjyqvFbV8yqreK6iKq5Vps7zFKAABShAAQpQgAIUoAAFKHB/BWQTxo8zzJk7D5kZ6bc0ko3rf8XwkWNu6Z6arrx 61FMnrsREY89ipwivQgKlC7xeLK9CvZWpli2Nd6YNFPK36AVuSh6hriK7UetMGPNKWhEQENcgLONCTZv2oSPXhR/0e/WvKaHyPYoQIE7FFi2eCEiHu93XSu14d9B1w2KJyhAAQpQgAIUoMADLFDZf5c9wI/MR7tHAomXErBg/vw7 EP/PRpoVd1IAYVQ8Vf46KPHUd/Bwrh1qJRK0k4kyFy357LIMSEXySxLd qQclBsjU41JmuUdu0wFzkovFytcOrkSWMbDE5UJc1rFKAABShAAQpQgAIUoAAFKECBuytwm5kS7u6gbqX1GW8MwKW4WBw5clTMjrCEq50ZFv0Zi5wCjTG/hLSLh17aEUJkedSIXBVz1p Fm705GnnY4OSx40iMj8UXr/e/lS5ZlwIUoAAFKEABClCAAhSgAAUoQIEaFqjTAQop8CDt1LHmy1Ew0eRi2fJfoDQUo6WfPfzqWcHZ1lTMljBATJYwBi78xblQfwdYKtRY8fN6mGhzsPKLZ2Em0ijodLoapmVzFKAABShAAQpQgAIUoAAFKEABClRXoGKGw red9/r6cXWl0XFxcjLzYW2uAAvDwrFn7tPY9GytQjw9YKfrycaeLqhRQMn41jjL2fg7JlkXLgodr64kIChvQPRvU1DlBTnIytbIWZa6GFlaQmlss6S3Pd3wgFQgAIUoAAFKEABClCAAhSgAAVuV6DOfhqXi 1ELS0sYGFuDhdXV2g1GgQGBmDI452x99hFRJ9KxJ9bzuB8QmnyT18PJzT1c8Wgno3Ebh2PwMXJHqYmJjA1MzNuUSorO24XkvdRgAIUoAAFKEABClCAAhSgAAUocPsCdTZAIT1y aCCQgQaTE1NYWtjAx v ngmwljBmBTzSpHyUEg7d0j3SeXK139r8DsKUIACFKAABShAAQpQgAIUoAAF7odAnQ5QVAS7WeChNC5RPmRRsQX TAEKUIACFKAABShAAQpQgAIUoMD9EKjTSTLvBxj7pAAFKEABClCAAhSgAAUoQAEKUKDmBRigqHlTtkgBClCAAhSgAAUoQAEKUIACFKDALQowQHGLYKxOAQpQgAIUoAAFKEABClCAAhSgQM0LPFA5KCQend6AWct2Yu3W4ygoUsPfywlTnuuOkMD61 gdO5eMT/ 3DWfi0mFhpsRTPZripSHtjTt6sFCAAhSgAAUoQAEKUIACFKAABShwbwUeuBkU3284iFWbT2DUgPYIbuyPYoMJRn2wGifOp1yVjbmYimHv/oyOrRrCz98bDi6uWLHpGJZtOHxv9dkbBShAAQpQgAIUoAAFKEABClCAAkaBOhugiM86ecNXuGHHKbjVc8ZPfxxC9PGz0JaUwEPlBilwcaUsXX8Q3h6uWB8Vg9NnLqK4MB9ubk7YsPPGbd6wI56kAAUoQAEKUIACFKAABShAAQpQoMYE6myA4rVfw/DXqf9dB3HyYgpsrCyQlJKFHz8dhIsJKbCytsRGEbi4UjbsiIGVjTUuxCdj2YcDkZiUAWtR53i5WRbXNXw3T2guYf2UMZj4/Xlo7mY/bJsCFKAABShAAQpQgAIUoAAFKFBLBepsgEKtLcZvMV9jxtZhKNbkX UNbaRCXl4h6rk74pk3V0CuUECpVMIgalxOy0Vyeh704nvpHAwGDHjje9QXsycK8gsREqCq2dekz0fsnj x9VSusc rpegQJoc3QJtJu2eVvToAACAASURBVJAnndRl4ODGSOyKLSytV/F6ddup2dGzNQpQgAIUoAAFKEABClCAAhSgwD0TqLMBCklodNcPITfT4 VfWiEu87gRbVDv5khOShUzIqwRGhqEtqGNkZyWZUx eejwQZw ewYyEa5ITc9C29ZN0a51M9jY2SApOU3c26x68OrTmNlehYbP7cS/oRHp1hIc 7A1VMEvY2 h LEoGjNGjMSHW9KhK9 ywhoe/gHwV9nB5EY9Vrx u 3cqG2eowAFKEABClCAAhSgAAUoQAEK1EKBOr2Lh1ymRKfG/eDl3Ajv/t4L/2n1Efp2Gg1rSzO8O3eTyEGRYyR3sDXHoLZ6WCg1OLh3m/hehjUHknHhQoI0iQJO9lb4eHwv9A4LuDevyDQAY7/fhLGV9Xaz61fuq269yvrheQpQgAIUoAAFKEABClCAAhSgQC0RqNMzKKTowumcnXCxd8fYbp9eXfLRrrkr/ln8Ai5ufMt4rP70MViZAr4N/NGlcxfxvQHrZz6N46tfw4k1r2H39y/e1eDE2U87wkelgkocAzaKoIk6BtPDVGg5 QiKb/SLUMn1arWjTkDkp8PQIVDqzwtNe43H/EM5pUtH9HmIXjwBvZt6Gsei8m HkcvjmPfiRu A5yhAAQpQgAIUoAAFKEABClDgngrU6RkUUl4JvV6L PzDsDf1wLMdJyMqZhUmiiUf7/RYDW/HJkbMuLhYuLm7QSfqWliYiw/n9XD27Gl4eXreE2yP0YuxYLCnWM4hg5WH9W33edN2DLnY/cEAjFnjif9 tgqP1M/C1lmvYerQt C3 xt0vPwNxr33B q/ i1 6aGCPvUCMn1cb7zM5LZHyRspQAEKUIACFKAABShAAQpQgAK3LlCnAxTSDAq93gALuQ2yS5KQr85EeMDj8HAMvLrkwzTVF4mJl9ChQydk5abD0tIK3br0wMbfN2Dn3zvQUZy/28XCzR9BQb7/BgLUt9fjzdrRp2/BzOUpCJu5AW8 6WrcQ7bp50mIDP8MK47kI8wsEVmwQzfxzK2b24hwScjtDYR3UYACFKAABShAAQpQgAIUoAAFaligTi/xkPJHGMQ/ZBC7dGjlxu9P5 yAk50LRnWais17f8PxmKN4asBAmJuZ4ciho9AW6 Hs7Iqu3brhyNGDOHvuTA2T3r/mShL24bxWi90TW8CzbEmJd/j7iEERkpMLYR7yAiaE5WFx/3D0nTATa4 kc3nH/Xtd7JkCFKAABShAAQpQgAIUoAAFygnU6QCF3qCBQcygkMtMELl/OdKyUsRsCnsk5EbjclIi6ud1wqCnhxsDFwWFBSgqLsL2qK3QaDUwMTVBqzatEfnHRmRkZtzaL4Xoz1xsv6EuKLp2 1CxV0dRdhFgYg4T2a01WSO1xXMaYINHv4rEtm3byh1R K6PE QWQRi/8iB2LJuAJonfY0JEKB77/AjypbUyLBSgAAUoQAEKUIACFKAABShAgfsoUKcDFGqd2hh8UIgZFCXqYuw/tRUnYvfBWumG9AMWeDyiHxzsHVBUVISdu6Jg7aFBx46dERW1HU4OLqjn5o6WLUPx67o1t/YKTJwR3NAK2ugNOJRT7tN94Rn88XcWZA1CoTITTcrNYG0OFGYVVghk3Lg7g14vAgw3KNVsx8yzFXzleThxRgavgAAEXD384WFbtppHbg2/bs9j pqdWDPCGccWLUC0tCUqCwUoQAEKUIACFKAABShAAQpQ4D4K1OkcFDq9BnoRoJCLEIVUZvffjy 3jcC PQfR0mUgGjTwRU5uNrKzs8XsimRsPzkfcdo9UGX1RG5uDpyd3GFrbY/Tp2IQG3sRPj4NqvkqbNF2wij4//5/GDVQgVdH94CvMhl7V8zCwkRXDP6iJ1yk0I ZJ9o0VGLZj19gQYtRCMZlpLk9gqeaVehGYQt3OyAp6ldsO uL3t4VrlezHblLT7wy2B2D5j6L5xSTMCzME2b5CTiTEYhnhraE5aWNWBoFBAWrYFVyCTtjxI4itm6wqdO/BdV8ZaxGAQpQgAIUoAAFKEABClCAArVaoE7PoNDqS0qXeEDsISrmHoxe4YfjSTthl9sYrUPDkZuXI5Z25OP3TRuQZ3EeXZv3g8Y0B0dk34ulHb/BSiTMlMnkxsDEgYP7b lFWTR7HatXvYcI5Q7MeuV5PDfhQ/ySE4ZXlmzAp53tjQkqIXdFxGfT8VS9fZj2/BAMe3Emfj2YBm3Fnky8MOCd0WiRvhhTFp1BScXr1W1HZoeOH6/DYpGD4vIPb2HU4Gcw9IVP8fP WOTrxZKUtGhs PK/GPhYBCKeehE/FPTElHkTESzN9mChAAUoQAEKUIACFKAABShAAQrcR4E6/bdzzZUlHjIFnuv2sXF5hEF8ED 5rgSeHl5ISUvEpUuXoFZmA5aFkLnpEOLeGZdsz Ls0b24GNcF3p4 cHVzxbHjx27xNSjhEv4C/m jOKq408xvEL7aLI4Kdd7cnYg3r55TwLXHh9hw7MOrZ669LiZjVKsdcbvYbrXXpEXiuMGgQt/Gr4fevsEFnqIABShAAQpQgAIUoAAFKEABCtxfgTo g0LkoBBJMuNyjyFWJMaMyxFH7lGYWgMFRfkwEckq9 zbg0zbaChs1FBa6EUCzRg4WLvCK8QW6zasEduU6kQuChUcHBzv75tg7xSgAAUoQAEKUIACFKAABShAgYdYoE4HKDS6EtS3bgzHmFOobxmEepaN4Hz6LCwcFDDogKNiG1FT9wJ4ufnBL/sS6lk3hLulP5QntsPGxgrm9Qvx9 4oWIqlHlYOXOfwEP//gI9OAQpQgAIUoAAFKEABClCAAvdZoE4v8Viw5T0jX70SA5K2Hyr9vtggZkXI4fK3L85ciMZfuV8AZ3WoL7b9TM INi4DcRf1L18 DJlOiazY16DT6hF57mtgTxoGtH1J5KW4H3uE3uffBHZPAQpQgAIUoAAFKEABClCAAhS4jwJ1NkCxeEASiouLb0inVqux4fd1aN mJ/o5DzXWUSqVxkMul0On00Gr1Rq/JiVdxomY45jcb4WYVWHD4MQNRXmSAhSgAAUoQAEKUIACFKAABShwdwXqbIDC0bHqnBFDBg HYzXySgQGBqJps2ZwcnS6u9JsnQIUoAAFKEABClCAAhSgAAUoQIFKBep0DopKn0pcqE5w4sr9DE5UJclrFKAABShAAQpQgAIUoAAFKECBuy/wwAYo7j4de6AABShAAQpQgAIUoAAFKEABClCgpgQYoKgpSbZDAQpQgAIUoAAFKEABClCAAhSgwG0LMEBx23S8kQIUoAAFKEABClCAAhSgAAUoQIGaEmCAoqYk2Q4FKEABClCAAhSgAAUoQAEKUIACty3AAMVt0/FGClCAAhSgAAUoQAEKUIACFKAABWpKgAGKmpJkOxSgAAUoQAEKUIACFKAABShAAQrctgADFLdNxxspQAEKUIACFKAABShAAQpQgAIUqCkBBihqSpLtUIACFKAABShAAQpQgAIUoAAFKHDbAgxQ3CqdPg2/PuMNVfNJ2Fd4/c2FB95EiKohRv2ZDYO4nPvnEHirgvHfLVnQX1e9BCe/6AyVqhu i9Vcd7W2ndAlr8ZAHxVUEYsQV8lw9fmn8Ou0MXg01E88l6irCkTbiOfw Z9J0OqS8MOj0rnrj46zz6KSJmsbA8dDAQpQgAIUoAAFKEABClCAAndBQHkX2nywm5Q7o9N/OsH8uY1YfmQK2oRbl3veAhxd8TvSbHthRDt7yKBFVlyq Gc2fnl/PsZ3eBONzf6trktahw  OSdOuCMxWye mtRiOzXOLpuNfwx2UBz5GvOjB GTUMtrxqvP/gcf9huIBWdV6DLqNcxs7Q1rdQpi9uxGukYhPKRnFCXgFSz pD1sZFdul8PK2xP8ZazFr59DowAFKEABClCAAhSgAAUocJcFOIPiloFlcGg/Et2ss7Fp SHklr8/7wh /CMTjn2GI9RWuiACFPGZgLkHHC/ D5/9mVpuFkUhjnzzOf4x84YNcpCYoxX187BzXCOo2nyM4yVlDeftwPMBKvRanCBak4oeKSsfh4f3QPyWocb5hUPRyq9sRoJ/Owz8aBOSrkxF0Kbir4 Go0dow7JZC40x KfE0nbUCYj8dBg6BEr3eqFpr/GYfyjnBrM8SsdhyN2DuUsT0WrqQkwOScfPs7civfyUEEMe9k57UQQnGmHihi344aPxGPR4BPo NQpvzFiA6RGuUJQ9EuwD0TosDGFXj7ZoVt9cBDBYKEABClCAAhSgAAUoQAEKUOBhFWCA4jbevMyuDUb2cUTe5mU4kCMt5CgtuYd wJ859dB/eAisjKe0yE3KhazRWHw6zApbpy/B6bLAgy5pA6Ytz0aXd99AV5sSpKUXiSUh1mjcpxmUibtxNLN0tkFJ3E4cLQDObT8N8UWUApzechqGRn0QYqeES/hIfLhwDX7bsArfveiH49 Ox6Q/M0oDDfoMHPp9K2IbjMe85auwctksvNjJFUpDLnZ/MABjlhYh4rNV2LB2HkY4bMXUoW9hW/a/z1P2WOKLDml/zUUkIvBK/7YY8FIvKKLmYl1CacjEWC9vPxasSYPNY5MxLsSGwYZ/8fgdBShAAQpQgAIUoAAFKEABClRDgAGKaiBdX8UaLUc hfr5W7F0V5Yx1wQMOdj/wxbkNRiCIcHmpbcYSpApAg8KB290ePFltLi0BHP kXJTlODU0tnY4zQMb/T1Qz0bA7Iv5Yhwhgz2LfuiMWLwR3SeqKdFyt4oJMmUKIn E2eLRLPF57H5QD4a9A6Du1IO28Y90KdrO7RsEY6 L07GSO9iHNsZJ3r4t9gGdUWvLuFo3 0RdKhvAn36FsxcnoKwT bhzSfD0aJtBCZ /jqCcv/CiiP51z uJh5r5 2B/YAxaGergGPHsXjSKRoLV5y 2o8m9TjOi/H5dgyE1c2mQuwbhyYe5fJQBIzF3zfo9vqB8AwFKEABClCAAhSgAAUoQAEKPKgCDFDc5ps1DxqKZwOKsX3RNqSJpQ76jB1YtKUQTUcOgN VVBK6fKTlAZaOljDzfBKvPy7H7zN/QXzaTny1NAmtX34OTayt4CBSOeSl5RszNCjcOuLxwBIx8yEGhfpMHIhMQNDEV9Eq/29siVNDc2kHolJV6N3LR2SsKEbsho/xbI9QNPJWwTOoH76LA9RF6tKgSSXPVpKwD e1Wuye2AKeZQkrvcPfF2GRIiQnF163zKPkzI9Yctobw4YGwxh6sWyOEUN8EP/TUuPsjtJiKO1TJrv57Imgt/BzZCQiy44/1r HFtems6hk5DxNAQpQgAIUoAAFKEABClCAAg qAPMS3u6bNWmAp8a2xYzX/4ffL/VFr50L8Tc64qvHyiV71BcgQ z0YWFvAbnMFuH/HQOf7nPwwccO2GryBJY/Vh9KeRLsLQ0oyigoTSFp4oFufRvg42XrcSqlK9bFuKPPx4/DYescLImKw9PKDbjo0guP ZtBHfM5ho/9Doqhn2LeFy3hZjiHJc Px4abPZNBCibY4NGvVmJSs7LZHsZ75LB0dxL/LF9E4s lPyNBn44vuvrgi2uuZWDh3nfRupsdlM6N4CUCM4f3XkDhEHexWKWKYuOD4KbN4HCzmRZVNMFLFKAABShAAQpQgAIUoAAFKPBgCTBAcdvvUwH3R8aj1/v/wfylkUj56wCs /6Ebi7lPt7rCpEpZhiY25gbP/Sb A3GS Gz8dLqVDSc9C3a2opP6AZz2IqdPQpFxdKsEybwjeiPBjOXYcmKSzhk1x1vNPCA5WPemLpyBX6Qn4ZLxOdoJOIKBef34AKaY/brQ9HVVfSgtUZDu5s/kJlnK/jKl HEGRm8ngoonRVRyW2G3H1YtD4dDV9ahtmPOv8bvNCn4rcJ/8HChVFI7/I4XGxb49meNtj262dYMX4lng8sH/iopHGepgAFKEABClCAAhSgAAUoQAEKlAkwQHEHvwoy /Z4cUh9RHz7X8yBN176ri2kmMPVoitClsjLIAUojKcVbnj0vXcwZGE2Iob6lW4qKvJLWFspocvOQrFYKmIr4gwmvo9jYMOZmD5rK1RjJ6GhmQnkvfvD65Np A4qjJ0VZAwqyLxbwgPz8e2XK DUvwmcFYmIrUYuB7lLT7wy2B2D5j6L5xSTMCzME2b5CTiTEYhnhraE3dUYiwGZOxfhr7zGeGtQJ4R4l/910cB6cCC mbYIm1MiMLieI7pN/RR99kzA1Ef64MgLI9C7uQpWuizEHtuPiyJR5wcDTEtpsk5i99/2Yg7Hv0Vh7Y2QEC9YclZFORV SwEKUIACFKAABShAAQpQ4OERYIDijt61BZqMfBEhC97F8TYvYXhA2QfwK23qi5BbLAUozK7OPLBs jy  Kp8pwqYiQAGLmegQJpCYZxq4YP o0Iw/e0MPPlUIMQEC8ArAs80moaPdMMwpJHxDMyaTMSCj1Iw6at3Mfz70h01zEVCzlZ dv9u6Vm qyvfy zQ8eN1WOw8BdOXvYVRc8S9Skc0emIqIgaXC1Do07B98Q4UN34PvVQVf1VM4PnoQAR 8hGW/H4JT4/2hrJ f3yzxR1LZ8zG90snY122NCZTOPm3Qu/n1CK3RZnP2Tl4btCca0fm9RI2R72JoAqENxo z1GAAhSgAAUoQAEKUIACFKDAgycgmzB nGHO3HnIzEi/pafbuP5XDB855pbuYWUKUIACtyqwbPFCRDze77rb O g60h4ggIUoAAFKEABCtxVgcr u yudsrGHwqBxEsJWDB/foV8iA/Fo/MhKUABClCAAhSgAAUoQAEKUIACFKhtAtxmtLa9EY6HAhSgAAUoQAEKUIACFKAABSjwEAowQPEQvnQ MgUoQAEKUIACFKAABShAAQpQoLYJMEBR294Ix0MBClCAAhSgAAUoQAEKUIACFHgIBRigeAhfOh ZAhSgAAUoQAEKUIACFKAABShQ2wQYoKhtb4TjoQAFKEABClCAAhSgAAUoQAEKPIQCDFA8hC dj0wBClCAAhSgAAUoQAEKUIACFKhtAsraNqA7HU9CcjZiLqbiTFw6ziWko6hIAwtzE/h6OKJRAzc09nWFh5vdnXbD ylAAQpQgAIUoAAFKEABClCAAhSoQYEHJkBRotZi/updiLucga5tAhASWA99OgTAIP4Xm5SDuKQs7D8Ri9V/HkITP3eMHdgeZqYPzOPX4K8Em6IABShAAQpQgAIUoAAFKEABCtx7gQdiiceRUwkY/uYiONqa4/WR3eFR3xne7lZwspFDnEJMQiaSc4qhV5igS7tAZOTm46mXv8ORU5fuvTh7pAAFKEABClCAAhSgAAUoQAEKUOA6gTo/heDA8Vh88H /4OvJg2BmboX8oiJYmcuh1WlxOi4TiZnFqO9oicJiLbxdLBDoaYVOzVvjbCtfvD5tBaZPGojQYJ/rYHiCAhSgAAUoQAEKUIACFKAABShAgXsnUKdnUBQVq/HKp8vx9XsDIVOaQQY9HCxN4OzkDLnCFI4u9eHu6gaZQglPEZzQqwtwOjYd5iYytAhww/sT uKFKYshtVMrii4De/73CT5fFw9NrRhQhUFoLmH9lDGY P352jm 2mjGMVGAAhSgAAUoQAEKUIACFKBAtQTqdIBi6tx1eHdcb9hamcLaVAdThRbpmdk4cyEWlrZOcLC1hLWlGUzEUzqY6/Bo yaIaN8ISoUcBoMezQPqY8STbTBlztpqYd31SrpURC38Bj8dyITurnd2Gx2IAMrBjZHYFVsoQkGiFB3C5PAGaDNpF/Juo7lrbtHnI3bPn9h6Kre07SsXa7KPOx0j76cABShAAQpQgAIUoAAFKECBuyZQZwMUZ2NTcPbiZbRs5CGCDQYxe0KG9Iwc484dprZu0IhP0KZKhTEYYWEqF8s8rLB110FcSk6HRlP68V jUaNPp6Y4EH0BMecvVxNZjZOfhUHl/Qw2Zhluek925GB4q7pg7oW7OydCl7waA31UUEUsQtzd7erfZ1ZYw8M/AP4qO5jcVOImFYqiMWPESHy4Jf3a4ExN9nGTIfAyBShAAQpQgAIUoAAFKEABCtw/gToboNgnggpDIlqKYEOJUS8lPQupmXlo0aoNnOwsxWwKQC0CEVqdHomJl5GZUwiFpSMW/LoP7879DQfEjh5SMVEYxK4ffthz9Hw134IpPFo1hKn2PPYnlPZtvLH4GL4Y0BX9p0ej6GpLJUjYfw5amyZo4XbHH GrGJ8aZ5fNxj8GOyiOfI350YVV1K3BS6YBGPv9JqyYGAyRi/TulHvRx90ZOVulAAUoQAEKUIACFKAABShAgVsQqLMBij3R5 Hn6Yj03CJcTMzAsTOJ8PUPhI0ZYCcOhfg7fHZ EfILS Bso0RoU3/0bO2P14Z1xqT/9IDKxd7IdC42Ea2CPbDv6IVqs1n4haEBknCw3HKE4tNr8POeM9j780qcLi5rSp D0wfFzAy/9vC98glenYDIT4ehQ6CY7aDyQtNe4zH/UM41yxrSt0zGYy28xXUV/No9jffXXcSVJm80SEPuHsxdKp5j6kJMDknHz7O3It24BqOsaC/jtzcHoFOIv7FNlaoBQiNewnd7Mv6drVCdOhU7V8dgepgKLScf Xd8GrFMZfYYdA/2NPbl3bwvPj5YIO7U4PzCoWjlJ/UvDv92GPjRJiRVmO1x9tOO8DGOUYUBG3NElOlGfSRj64yR6BpUWq9x11GYtS3l37wY2kSse MJdGh 5Xk9ENztOXyzP7vUWZ H6MUT0Ltp6RilsYxcHse8GhXfL3 mAAUoQAEKUIACFKAABShwDwXq7C4ex04nwMoiDJsOJMLFReSbcPVAWnYhCoo1kMtlxtkTuQXFSLh0SQQmGhuXgUiHjZWFyEthwMETF1FQmI/s7GyU6K1xJCa 2uwmbqFo4Qj8vvMciga6wgolOLvud6S6BsM5NRJrTr2LkBALMaviAkQVqAY3hYOY0QFDLnZ/MABj1njiv5 twiP1s7B11muYOvQt O3 Bt0tS4egK3FEt5f/D2 qdIhZ/Tk G98fRc5RmN7eVixkqVh0SPtrLiIRgYX926JZvV6Y8dxcrEt4BKO9y16vCJSc3LEHSYGT8O2s5rAqjEXU4un4cMAxZEf jjebibFWp07Friv bCjAoen9MWSeBn0mzcG7oY5Qp6TDzlNEjCCHS7hYwrFwAtzt9bi8fS4mzRiPSS33YWmEk7haWjxGL8aCwZ5iyYgMVh7WFXsQhvk48El/DF8A9Js8Hx8EASd//hgfDxuAwg2b8F4LK/EsuTj19wGkiOf9bnYILAvPY9PsqfjkWRM02jMXHRK/wbj3/kD9V7/FLz1U0KdeQKaP650vU7l tDxDAQpQgAIUoAAFKEABClCAAtUUqLMBioTLGcgu1Im/yFviWEK2CEo4Qp eC3MzJWQyGTRaHQqK1LgcfwHytv7GpJgiPnE1UNEiyBurNmxDSXExFBYK5IjZFtUuFv7ir/cK/HR0v5gBEA5/XQxWrU9F04lf4Ykfn8E3P57A2yGtYJJ8ENHZlmjewRvSR3R9 hbMXJ6CsJkb8OaTrsYP5U0/T0Jk GdYcSQf3cNLR DW5xW88p8Q47KJHp2DoT3RFbP/Lwpvhj8Gp4oRCk081s7bA/sB69DOVgHzjmPxpFM/LFxxGsPeDjb2e6XYBHRGz26l7Xbr1hyyLn0xf YOjF3SG6XzSYDq1CnX5DXfGjK3YcbCi/B/YyvmTgyEaYWKto17oE/j0pMtgx0Rs6o7lu MQ4kIUIgQibFYuPkjKMj332BBhQ1W9BlbMWNxHPze2IYvxwUY  gc5ofC6O74esZ2vPBDBJzK2rIJ7IweXaXn7Yxwz3hseXQVfjtVhHb6RGTBDt06dELr5jYiFBJSdge/UIACFKAABShAAQpQgAIUoMD9EqizSzzquTniZHwu1u9LhUJfjGZelnC2EDkfEpOQmJqDy2k5SM7IQ67OEhdi46HXSzMopCBF6UyKgoJ8NBfLLE5dSIWJianY8UP85b26RWaDJt38gYtRIgChFx Of8RvmSEY3jsUjwwKRubGZTicp0fuiShckDVC90albZck7MN5rRa7J7aAZ9kyBu/w9xEjslYkJ5ftjFFxDCYeCG/tAO25g0gsl/LiSrWSMz9iyWlvDBtalgfCsjlGDPFB/E9LcVRaWVFZsQzEI2H2KD65FwmV7bJanTrl2i O34UYjQvCOnldF5wQ00kQu FjPNsjFI28VfAM6ofv4sQKDhFEunmq0X87KYnfjdNaV7Tv5PlvH6be6BzuJFaD7EH5tCDlH93UPRjuYq R5FwtLENewISwPCzuH46 E2Zi7RGROLUyJ56nAAUoQAEKUIACFKAABShAgXsiUGdnULRs7I1YsWOHWq9AbIYWj5jL4GIvlnqILUfX7jwPrdwcxWotCjSm Ha9yJGgPgiZOhczJw1BQYEIXOTmGJd3ZBXKRQLNIrQQ7VW/mKBeh27w0P AzadS4PzzBuS1 QTd3Uzh2Hs4Qj6YisV7J2H0lhPQ o9HG6eyOJAUHIENHv1qJSY1K59WUg5Ld2mZQ YNh2AQwRUxLUQcFS8X4OjSn5GgT8cXXX3wxTWXM7Bw77to3c3u tvK6skUosGymSWVVbqmTsXuK/6sFwEg434q1xd1zBwMH/sdFEM/xbwvWsLNcA5Lnh PDddXvStnZAqlyEuih06KhlgEYfzKg i9fQXmfz0XEyLmYP7EdVj9RgisbzT4uzIiNkoBClCAAhSgAAUoQAEKUIAC5QXq7AyKsBA/JCSlw1xs12FjqkFOThaKigphb2eNYb2DUd 6BIliFkVSRi6S8hS4mKFHTGIBEpMuIysr01j/z12nUb eCulih4/WTX1u6TfDzLcn2jvkYbeYqTD3Lz26jukCZ6GpcO J0e212Dp3CX7 Jxv1u3aEqmwDDzPPnqtILgAAIABJREFUVvCV5 HEGRm8AgIQcPXwh4dtJbGiwjNinNkwC2oLzwprJgy5 7BofToavrQMGyMjEXnl2LgU433z8NfCqGuTZZZ/Qk0Cdu3PgtI/FKry60CqUcdgDERcX6Tn81Ok4p8d8ag4KaPg/B5cQHO8 PpQdG0RjMbNQtDQrlwbcjNYi5hNYVYlM0nKqpp5tUOAMhW7dib824c6DlG7MmDSSBhV9iwVhyu3hl 35zF9zU6sGeGMY4sW4F5tflJxKPyZAhSgAAUoQAEKUIACFKAABYBKPhXXfpq2zX0x94fNaNfSHwdiMpElZkPodDpYWVnDwsIScm2hCGCkQaOXo7CoBNriAmiLihFz hzcnKxRKBJkmplboUkTfyxesxVjn lwaw9t2Rj9u9ji51/ D6nOg7FWLJcw/vFd7oyuz/WE6bBvsAquePaxhlfzQMhdeuKVwe4YNPdZPKeYhGFhnjDLT8CZjEA8M7SlyIpQWvLO7MSWHQWwKRLJLBdNw3eJDfHSgk5wuOav wZk7lyEv/Ia461BnRByJSGmsQkNrAcH4ptpi7A5JQKDy5IypETOxuyGA9Daw4DTqz/DjAuuGPpZZziWa7fKOgpbuItBJkX9im1nfdG7wqQTuUsvvDq4HgZ MRTjdJMwqHU9KHMvI88vQtRtCQ/Mx7dfroBT/yZwViQiNr8cuZkn2jRUYtmPX2BBi1EIxmWkuT2Cp5qVqyPxOnXHGyO98cTnI/Cq bsYKJJknvjpY8y66INxc7pe8yzX3vnvT5r4jVgaBQQFq2BVcgk7Y8RuIbZuEJu9sFCAAhSgAAUoQAEKUIACFKDAfRKosx/JfD1d0bN9E w7GIMAf0 s352AiNZuxlkU5uYWImiRgCyRb0CvUYujGLoSEaAozhNJMfPF7Am12IJUjYb QYg HY/OrQMR4ON i6/ABs2e7gKbX9bD7ukRCLmawkIG27Zj0M/1NyzT90T/RlfSP4rmZXbo PE6LHaegunL3sKoOVoRInJEoyemImKwCFDI7dCoQyu4RM7E84OlrAimcAvpi8mrP8Bzzcu2 LgySn0ati/egeLG76GXquJrNIHnowMR MlHWPL7JTw9vPQmhWkGtsx6Ef XpoO5RxhGz/0C71TYGaTKOiZeGPDOaGx8ZTGmLOqLLlMrjElmi/bi ZY4vYdpi17DyFlir1NLH0RMa4 IAROx4KMUTPrqXQz/Xjy3KOYO3iLJqZ1YeiGK3BURn01H1NipmPb8ZsCkHjq/HYp FQIUkFmj1btr8L3V2/joy fxS56ILQSIwMiyz/BSS6sbLi 5QnblqzotGhu nI/3U6R5Hko4N mDKfMmIri6sy8qNsifKUABClCAAhSgAAUoQAEKUOCOBWQTxo8zzJk7D5kZ6bfU2Mb1v2L4yDG3dE9NV1ZrtOg6fBqeEskpcwqK0KWJtUiGqcWxsyn4aes5lOgUMGhLAxRSkEIuFiYMfrQJGvu5Qi1mOhTq7PC/lZvx15I3YGpS8UN TY/2PranjsH0zj3wc4 N2PVR6S4e142mOnWuu4knKHD3BZYtXoiIx/td11Ft HfQdYPiCQpQgAIUoAAFKPAAC1T232UP8CPz0e6RQOKlBCyYP9 402WdLXKxNOHz1wdgxW974GhjCktr8dd4hQmy8nXwre8IT3slXCwN8HGzRWjTRujaIQwOLg3g4R0MvcIR3/30Jz577UkoFXWaoc6 Pw6cAhSgAAUoQAEKUIACFKAABShwRaDOThuQtgstKCiAt7st3hzRCdP txXujt3h4e6Geu5a2NuLGRJFGhjE7hemSjPY2FjDxtoaLk52WPnXMWzddRRTxvWCTz07kY iENbiGgsFKEABClCAAhSgAAUoQAEKUIAC90egzgYoZCLwoFAojIefpxNefjoYP6zegtQCU4S38Ieftzua brA2rJ0u9FLydk4diYBfx/aBBdzDV4f3Fzc5wy5XG5s44EupkF4c3ci3qzqIatTp6r7eY0CFKAABShAAQpQgAIUoAAFKHAHAnU2QCE9szTrQalUwsTEBHZ2dlDVr4ejJ87h Lnz PXYUaSJBIolOhnMxVO62srh5WaFZzqq0KJpALy9vcWOH1ZiZoWN8X4WClCAAhSgAAUoQAEKUIACFKAABe6fQJ0OUEhs5ubmxsPJyQkqlQqtWrVCSYnYVlSrhUajMW49eiWIIX01MzMz1mdQ4v790rFnClCAAhSgAAUoQAEKUIACFKBARYE6H6C48kDSkg8p CAdLBSgAAUoQAEKUIACFKAABShAAQrULQFuX1G33hdHSwEKUIACFKAABShAAQpQgAIUeCAF7mgGxQ87Ux5IFD4UBShAAQpQgAIUoAAFKEABClCAAvdW4I4CFNJWnywUoAAFKEABClCAAhSgAAUoQAEKUOBOBe4wQHGn3d d 4sSD0OdFQsYdDDo9aWdyOSQyZUwdfCGharF3emYrVKAAjUuIKvxFtkgBShAAQpQgAIUoAAFKFAbBe4wQFH7ZlAUXToIdeYFKG3cYWJbH0prN6O7Ji8ZurwklKSfFUELHSw8Qmvj  CYKECBCgIMUPBXggIUoAAFKEABClCAAg HwB0GKGofkl5diOatwhEc6Ie8vFykpqRAoVDA3l8FS6tAxJy5gNPn4sHVKbXv3XFEFKAABShAAQpQgAIUoAAFKPDwCtxZgAK1bwaFrjgb5/Ls4FRogjy1PbIU4mtePjISslBQlAxLpR76oiwx8to39of315BPTgEKUIACFKAABShAAQpQgAIPu8CdBShq2Wd8g04D6LWwsLSBXCZDdm4 TpxNRHFhHnSaEui0WshtLWCi14hqGshE8IKFAhSgAAUoQAEKUIACFKAABShAgfsv8EAFKPTqAshMrGBtrhDBCA2yEhOQefwgdCWFMFhYQW9hCZnWHC6mZpDqys3t7 0bUJgirK0TvDIzsfZUCUQ4hYUCFKAABShAAQpQgAIUoAAFKEABIXCHAYraNYVCV5IvkmHmIfP7aXBu3gTFK35EvZ1RMBGzKQxm5tApTWCwsobJa6 KoEU ZGZ2t/FLIIOjvyv6e uwZUc6Lt4kymDm6oyhzRQ4uCsFR4t1yCvQIkd81YskGLVL7zYoeAsFKEABClCAAhSgAAUoQAEKUKCGBO4wQFFDo6ihZgyaImTv/xtB9evBrjAfXimXoRQzKaxE 3KNGtKGo2k5mUhLvozC kW3mSjTgLxsLXQ JnA1l GCuizMIDdBaEtH1M/OROQ5DbTGZ5LB2k4JubYEKcXSrqdaRB9ORXQNPS boQAFKEABClCAAhSgAAUoQAEKPCgCdxaguIM5AJqifOSlJ4ggwc3nEcjEDAhbVx8ozSyqdpeLYICHD05ejoOiQQPsKRJBCLkcpuL Qp0OOeLuPHG0sLWFQq647USZmoIS5MIcbtZiA8RcvVFBaW2JQAclrCwt4XAhG6lSNEQmh72dAhD1c/RixoQIYrQOd0NgWip Oq2GVqaAX5ATWrmYwM60dDPFkvwiHInJQnR2absQ4/Txc0BbD3OIWAeK8wpxOCYbx3PKrlctwqsUoAAFKEABClCAAhSgAAUoQIE6IXBnAYqbxxYqRVCaW8PayRNFmZfQv0cI/Dydr6sbdzkTqzYfhYWjBxSmFjed8SCzcoOdRz3s/WExPENCkGL3/ 3dB2AUxdvH8V96SAMCUkINhC5VqdKbBRWlKIoFQUGRZkVFBewVBREU7Nj 9q7oq4KoiAUV7NIhSG8ppN69s5tcCCEJacCS/e77nsnt7c3OfJ49/jdPZmYrao3HY4 gsCZzRJlHu9atzTSPcPmH1zhseYdUKHtHZkqatqZJDaIDFRCfadaS8FPF6hUUlpqu/SaJEhexV1v3GhyTMKllTp4Yn6b9JmHh9c8qwGKz8jJek8CIjg5WeOJefbYuXekBgarfoKI6tq2knUt2aWO6v2o2rqb NTNM0mK71qb4q65JVnRuV0l7zOsbDjO9pKD6sx8BBBBAAAEEEEAAAQQQQAABpwmUMkFRigyFkQgMDVdodC29 fmvGtyn9UFJinUmOfGGSU6EVq6lgKDQIo20UECISTxUVYMzz9ZHTz6pKsHBamjOU9k8rOUwo83ohpChQ7UtKFLWsUUZvZFvwDLStDFRahoVrDC/FO1RkBrX8Nf2NTu1qlY1tY0J0nd7UuUJCdIJQV5t35mhDDsj4Vt3wvy0fs9 npqYovXbzYgKc7LNyQGq1zlcDU1iY2NSiE6u7a/Nv 3Uss2Z9kiN7fvNiIruFc25/bR hzVMgw0BBBBAAAEEEEAAAQQQQACB41 gVAmK1PTM0gsEVFBgZI2DkhS 5ERAZE1l gWbW4QW4zw1OqpKy72KCjDDFT771EzEkKyxGdXNyImEc85RfAWTnKjTXaWru0ebt5rhC01DTPIjU7vCw9QwOE3fxu/Xxsw0dW4cpujfk7UjzEzLUJp 2p1uzmcqYaZrZFpZBjOqwzp/Rt7n5qW0xFQzDSVSFfw8yjAJlkpmekpYyxiNaXkwdUagR2mmjNKliEofPkpA4EgLWCOg2BBAAAEEEEAAAQQQQKD8C5QqQVGE5SOKJOgfHG7WcDBJiv/7RSe3qKvlf8bL3yQn/AKtkRNFKuLAQX5mHYr6fRXk8VdQk8aqun69Qk1H/5 YGHPnjFBlxPY1a0OYZhe33IOq4dW 7cna1yxS9SMClFQ3XME7d2pNilf7tyRoS4vKamWmf/xyQrD8zfSNeGuBTOt81iAKqxzrp  R 7n1klmrwl6 wvrdPtijVT9v0bfWlJFcW8Z 604gB 3iCQIIIIAAAggggAACCCCAAALHrUDpEhSl6 UfhOYXEqYA1dQPv29QYMVa8gsyUzBKWn5AkNSwj1LWvq ddesoPd2s72B6/IEN 5l1K60ml75nn5GYrI1pFVW/rhntUF1auzxZSVZGISVJP  IVv 4SKVV8FfCf/u1N3sqh  8Vrt8/2chHPzMx JVxv4U7fZG6oRIr/ZuypoCctxeaVQcAQQQQAABBBBAAAEEEEAAgUIESpegKH0//6Cq QWHKSi6gRk 4Ff8kRN5G2lGSfhVaaWMPX8o0yw 6V/VzJEw 4o9IiNvub7nZh2KP82tOlrUrqTw1AT9z6wHkTVKIlNrVycrs1NFNTfTP341C2Rm JysURPZ7z9oBIXZZz 3Xss wHru2Z spRsyNCSuhs70mjt77DC3Nw0MVLSZTvLHhlSZARtsCCCAAAIIIIAAAggggAACCJQLgVImKI5QD7mssghBUWYaRNZilH7m9xIviplvqDO1ZWOy0mpHKGXjXm1JPzDeI2XHXv2VGq7WStKf1u1Ac2clrLKy65RTH9/z7Nfs09n7PFq/YrPeSa2irvWraGAjMwzEm6kdm3bq3/Up2n E PNtLjsRQAABBBBAAAEEEEAAAQQQOIICpUxQHMGalUXRAWFmgc10MyjBIz/ze1nlPXxVS9m6TbPe2XZoTTNS9NnHa/RZ3lfMAppLPl2jJb79eZ9b 1MT9fI75hYhOcdkaNUfW80jb2E8RwABBBBAAAEEEEAAAQQQQKD8CJQyQeHwP EHhJoRFNbtM8zAA/N7mWcoys91QEsQQAABBBBAAAEEEEAAAQQQOKYCpUtQHNOqF3Ly/dulfWsU5JciKz1hTaWosPMr7c8MlCewovyim5v1KMxtSNkQQAABBBBAAAEEEEAAAQQQQMARAqVLUJT1nImyIEncoKi01WrQqotSM/214e/vtXnDWi1a8pE6deqoLp3qaflvZvJF7X7mbNbNPNkQQAABBBBAAAEEEEAAAQQQQOBYC5S/BIVJmgSYu3aEBgXYi0xWqVZPXr8Q9T1jiGpXr6iU5ER5V/7GdI9jfeVxfgQQQAABBBBAAAEEEEAAAQRyCZQyQeFAy/C62pVSQUt//Emh/umKrOCnKuGB vePn/TTco8yAitJMX1NgoLREw6MHlVCAAEEEEAAAQQQQAABBBBwqUApExTOXCTTG1JVMo9kE1TrYW R2Q/fcydOT/HVjZ8IIIAAAggggAACCCCAAAIIuEygdAkKl2HRXAQQQAABBBBAAAEEEEAAAQQQODICpUpQTBna MjUilIRQACBbIEFz36FBQIIIIAAAggggAACCLhAgHttuiDINBEBBBBAAAEEEEAAAQQQQAABpwuQoHB6hKgfAggggAACCCCAAAIIIIAAAi4QIEHhgiDTRAQQQAABBBBAAAEEEEAAAQScLlCqNSic3rjC6rfowwV6/6VH5clIl591x1HzH38/r/nhp/DwKA2 /Ha17NivsCJ4DQEEEEAAAQQQQAABBBBAAAEEykjAtQmKD1 Zra6nXyx//0B5PJlZj0yP/TN1f6LemD9NVWvWU826LARaRtcaxSCAAAIIIIAAAggggAACCCBQoMBxn6BYtGiRevbsWWADC3ohLS1FXq9Xf//2wyGHRFWqopoN2ujx2y4wr3nNyAprgIX1H5nf/ewRFyEhoeo9aJza9xl2yPvZgQACCCCAAAIIIIAAAggggAACxRM47hMUY8eO1Zw5c4qfpPBKyUkJ Wrt27NTkRWjVb9VX3tEhdeTNbLCY376fs9IS9bnb8wkQZGvIDsRQAABBBBAAAEEEEAAAQQQKJ7Acb9IZnp6uiZOnChrJEXxNq SE/cd8pZApapG0EZFJHyvkF1fq8KepQrbt0wRiT8qKnm5Kqb8osppK3WCVqt2tL WfzLnkDIK3OHZrvcuaa5atWrlPBq07qnzr39SS7akF/g2XkAAAQQQQAABBBBAAAEEEECgvAsc9yMorADNnDlTkyZN0qOPPlrkkRTW9I6kxL0HxTdA6arkv1UNO5ynyjFNDxv7jNRkLX/vHrU7bexhj7UP8GZo33ZzzkYT9cx9PRSVnqjtq77Wy4/eoWH/94cWfPGIepukBxsCCCCAAAIIIIAAAggggAACbhMoF71haw0KKzlhJSmKMpJi9S fqUX9KEUkrVTl9L8PPLwbFdt2gCKrxmrXto3atXVDoY khD1KT88s/jVTuZk6dOyozt366OzLpuqZZy5Vte3vaN4yM6IjY5s u/Ni9T2pUfYoi a64NV4ZVhnSd iLx66TL2aZY3AaN5rpGZ8udWkVXJt5v1LHrtSp7aqm/X es3U8dTLNOv3lELKTtfqp4br5IbZIzviOum8OxfqP1/BGfF694aBOqVVw w61VPbc2/W/Kem6dI rVXfGhHSqIsufuRb7fJxeBK04tnxOrVlnaz3mDIve2n9wXUtvhzvQAABBBBAAAEEEEAAAQQQKKcC5WIEhRUbX5LCmu5hjagobOHMr9 ZpVZ9L1dkldoHwmrfa1RKM6Mi9uz8zyyg6TlsyINCKig90yxmUcotsEKUQk0KIiUlw6xxsVPLP/pC62Kv19yHO6qKZ5 8Tasp0JuoH 8epIvnS fcNk/Tmkl//O8u3XXRYCV/sFC3tg03IzSStPy QRo2N0n9rp2hGzpUk2fdO7rlpje1bEuaGblRQNkK0AldLtMdT41XjUoebV70uG58aKxubPe9nh9QRf6mDn99/aO2NZus eNOUtjuH/X0TQ9o2o9xGjplup5uFq4tC /TTQ9dqXtP U4PdghT2l9zdOWtnyjm2if0dt9a8mxbo131qymolFa8HQEEEEAAAQQQQAABBBBAoHwKlJsEhRUeKylx4YUX2mtSfP 9WUMiJCTfqO3dtVUZZkjC9vg1 b5e1J1BgcHKKEmCwpOm1NQUJaft05a/lmjBHfO0wb trmhX0dwoZLt9 qhmvdS/ZxuTuMjaPDs 1kPPrlfDG77UI1c2VrDZ3aNzQyWv6KPZDy3SVS8OUPSuRXr46bWqO 4TPXFdS/u9mY02qZpJUOTe8pZtn695X53RPOuodi2i9efrffTSkvVKNQmKCtlvjmzcXb27WXXqoNrr3tIXsxrp3IvOUY8Ic0C7YC1 80It/Xqj0js0UcbeeO1WRfXu2l3tW0eadrU5qA48QQABBBBAAAEEEEAAAQQQQCC3QLlKUCxdulRvvfWWnnvuuQKTE1bjMzI9CjDJhdSU5FJdDf4BQXZZxd5 nKCTGk7IeVtgnV6a8PxDurieGV9gBjrkt6VuWKq/M6rptO517OSEvQXXU48uVTTj/77TxtQBCt/wrf5Iq6p /eJyEhv5lXXovhSt  Ah3f7o2/r 3y1KCoxUiJkRErw/zdxkNb8tSFVio6X927QzxRwRYUafBFdVvUrSDzuTZc3yCGtzlcZ3Xqi7B3XRz4NGaNSoS3VWm6qMoMiPk30IIIAAAggggAACCCCAAAIqNwkKKzlhrUHxxBNPqG3btoWG1hr1EBgcrMzM0t05w2tuQVqiERRNrteC 7urcki4KteoozrVws0ki9JvXk GPPJXUEDWdJWilpj25yxdPOZJBQy/R3MfbKfq3lV6bvRYfVBIAQEhQWZURLoyPVYKw5zPL1Ch5mryGls7qVGhmca 9pNOXfSy5s1 XOMHzNK8ie/qjRva2PkMNgQQQAABBBBAAAEEEEAAAQRyC5SLRTKLk5ywGp e4VVAQKAyzTyP0jxSU5Lssoq9VYxT25NPUttWTVW/iMmJkLqd1Dhwm75dsvHAIIu09Vr87U4FNe2oOmY2S3BMa9XWNn237L9iLUaZtPo7rVFrXX39cPVq20LNW7VRo4rFbtWhb/CPUMPeo3X/m0v05oiqWvnMfK0o3aCVQ8/BHgQQQAABBBBAAAEEEEAAgXIhUC5GUBR15IQvYta0jMyMTDs5UZotOTGhZFM8SnBS/yp9dMNl9TTwgRG6NnSKzjOLZP7 6l2asba rpzVS9HWIIbq/TXujDt0 T2Xa0rojTqnsb/WfPqq/jHn61jIOcPqtTOJjXl64pGXVWXQiaoaEK91iYW8oQgvpW/4UM8vlpq1qKXw1E1a8qe5vWpUdUWWiyuuCAAcggACCCCAAAIIIIAAAgggUCyB4767GBQUVKRpHblVrGkZKfsTSj3FY3/SnpJN8ShWiLIP9ovQyVPe1AvhN vOR0br7QTT32/cX9cuuE8T2oVbkywk/6o6dcbruvf2KXr83pF6KTFUtU sZ17zk3/2XUryO3XIiRM1/86tunHmFF38QlbSJrRyPXPb0YolnnqStn2FPnhknqZutRbVCFTVE8/Q7XMnqkX 65bmVy32IYAAAggggAACCCCAAAIIuEjguE9QvPTSS4ddcyJvPP2DKmjvrm2yl0/wZk/RsHv4Vlc e/N16LNfzzrK/Df7cK/Zn7J3t6yyirwF1NRFH8frosLeENxMk5fGa3J xwTVVJ8bnjOP/F7M2ucf2VKXPPKeeWQ9T/vrIfXq85JqVzKhLqhsv0i1GvmYPjGPfLd83hfV/zVtis91dHATXfdNvK7z7TrpZr2z/OZ8i2MnAggggAACCCCAAAIIIIAAAnkFjvsExeEWxMzb4AwzrSMkvLJ2bPtPUdEn2GtR Pn7y8/PPMxPf/unSVSYn9bm9Xrk8Xjsn177p9d npmepoSEvQoNjza3LM1QYKATKFO16o3n9E1ArBrEVFLAnj/1wczHtS5muGY2KUYiJS8azxFAAAEEEEAAAQQQQAABBBA4wgJO6FUf4SYeKN5KLqSmpqpGbBttWrVcjcLClJGdiChuJTzmDh7/bVilOo3b22UGBASYpMYxvj1F5j6t/eE9Pfbub/ovwUzVCKikuO4jNGf2ZJ0UXtwWcjwCCCCAAAIIIIAAAggggAACR0/AdQmKzMxM1WnRXSt XqYtn71dKumgyBh1bNrFrGWRaY sOOYJioAT1O/ D82jVM3izQgggAACCCCAAAIIIIAAAggcdQFXJSisBEJISIhanNhagZfdpp07d5YKvHLlymrWrJld5jFPTpSqJbwZAQQQQAABBBBAAAEEEEAAgWMr4LoEhXXXj6pVqyoqKsoe9VCazUpKBAcH2 tPkKAojSTvRQABBBBAAAEEEEAAAQQQcLuAqxIUVrD9zUKYVpLCepTVRnKirCQpBwEEEEAAAQQQQAABBBBAwK0CrktQWIEmoeDWy512I4AAAggggAACCCCAAAIIOFUg616aTq0d9UIAAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJALXokkvAAAgAElEQVQIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIIAAAggggAACCDhbgASFs ND7RBAAAEEEEAAAQQQQAABBBBwhQAJCleEmUYigAACCCCAAAIIIIAAAggg4GwBEhTOjg 1QwABBBBAAAEEEEAAAQQQQMAVAiQoXBFmGokAAggggAACCCCAAAIIIICAswVIUDg7PtQOAQQQQAABBBBAAAEEEEAAAVcIkKBwRZhpJAIIIIAAAggggAACCCCAAALOFiBB4ez4UDsEEEAAAQQQQAABBBBAAAEEXCFAgsIVYaaRCCCAAAIIIICAswW8Xq88Ho sn2wIIIAAAu4UIEHhzrjTagQQQAABBBBAwFECmZmZmjJlipKSkuxEBRsCCCCAgPsESFC4L a0GAEEEEAAAQQQcJxAenq67rvvPt14443avXs3SQrHRYgKIYAAAkdeoMQJiuDg4CNfO86AAAKuFwgJCcnXgH D8mVhJwIIIHDcCvhGTbz33nuaOnWq9uzZQ5LiuI0mFS vAgV9Lyuv7aVdR18gsKSnbNWmrd587RUlm2F4bAgggMCREKhQIUxtTzo536L5NyhfFnYigAACx61AamqqXffFixerY8eOWrt6lc468wxVCA2Vv3 J/6Z23HpQcQScJlDY9zKn1ZX6HL8CJU5QVK9RU9aDDQEEEDgWAvwbdCzUOScCCCBw5ASstSekcWrQoIGWLFmirl276sSWrXTVVVcqIiKCJMWRo6dkBBBAwDECJU5QOKYFVAQBBBBAAAEEEECg3AhYi2U2a9ZMX3zxhXr27ClrSPnIUSMVER5OkqLcRJmGIIAAAvkLkKDI34W9CCCAAAIIIIAAAsdAICMjQwEBAWrdurUWLlyofv36KSQ0RBcNv8iMpAiXn5/fMagVp0QAAQQQOBoCJCiOhjLnQAABBBBAAAEEECiSgDWCwnoEBgaqQ4cO vDDDzVgwACFhoRq6NAhCjcjKUhSFImSgxBAAIHjToAExXEXMiqMAAIIIIAAAgiUXwFrBIWVnLAe1matRfHmm29q8ODB9kiKgWefrbCwMJIU5fcSoGUIIOBiARIULg4 TUcAAQQQQAABBJwmYI2e8E3z8CUp vbtq5dfflnDhw9XiLnV/WmnnUaSwmmBoz4IIIBAGQiQoCgDRIpAAAEEEEAAAQQQKBsB3wgK3zQPX6nWNI/58 dr9OjRZiRFqPr07q1Q85PpHmXjTikIIICAEwS4qbQTokAdEEAAAQQQQAABBGwB3wgKK1FhPXJvQ4cO1WOPPaZJk66xb0Wampoqr9eLHAIIIIBAOREgQVFOAkkzEEAAAQQQQACB8iDgWyTT99Pj8ahly5b24pjWY8yYMdqzZ4/GXj1OK1assBMabAgggAAC5UOAKR7lI460AgEEEEAAAQQQKBcCvvUndu7cqW   UYjRozQFVdcoTlz5mjkZZcpKirK3IbUX0FmLQpriodvSki5aDyNQAABBFwuUOIERUamR28v lNLf9 oHXuSXc54oPlVK4Wpc4s6OrdnMwWa//FkQwABBBBAAAEEECi6gDUiIj4 XkOGDNHu3bs1cOBAXX755Zo fbp9Z49u3bqZkRRhMotPKMg8DzaJCjdslsvKX3/V2nVrlZSY6IYm00YEjqhAeESEYuvHqlWbNvL3z7/fRp 3eCEoi75wiRMUb5nkREqmn64ZMcBksQOKV/NyfHSmJ1NfLv1Nby3 U f1blGOW0rTEEAAAQQQQACBshfYtGmTLrzwQrVu1Urbd zQ7Nmzddttt2nChAl66 231f/U/oowHYuCOhRlXyNnlLjCJCf27durQYOHqmLFis6oFLVA4DgW2LN3r7768nP9aj5bbdu2zbcl9HnzZSlwZ1n0hUucoPh6xXrdePnZiq0errDg/DNOBda8HL QlJop/y6t9MD890hQlOM40zQEEEAAAQQQODICw4YNU4f27XXJpZcoZX KxpvEhJWcmDhxombMmKEVv65Q5R7dVaFChSNTAYeWumbNag09f5giI6PEsqAODRLVOq4ErERfz9599cZrrxaYoKDPW7yQlkVfuMSZhT0JKfIzQ2FIThwctPAQM5rEDDncnbC/eNHkaAQQQAABBBBAAAF1795NI0eOtEdQdO3a1f75 OOPm455pN2J G7Zd0pJSXHd3Tv2JyfbyQk2BBAoO4FIs6ZNsvlsFbTR5y1IJv/9ZdEXLvEIivyrxF4EEEAAAQQQQAABBIovYE3ZmDz5RvXt01exsfXtaQzWLUStkROXmoUyv/rqK61cuVKnmikefuaPQWwIIIAAAuVP4IgnKL5btlRLv/umxLeAshZD6tzpFHXs0Kn86dMiBBBAAAEEEEAAAVvAWuzyyiuvVIBJVFjTN3xrTHTo0F5PzJ2jxYu/0oAzTlenTp3t10lScOEggAAC5U gDBIUhc Cs5ITE8dfo6Cgkq2wbN06auZjM0yComP506dFCCCAAAIIIIAAAraAlZCICA 3Ew 5kw8hISHq2bOnOnToYO8PCwsz3yuDXKpW Pdul6LQbASOggCfvaOAbJ i9AmKw8TKuiWSlZxYv2mN/P387XUr/O3/4TG/Z/8P0MH/Q QbsmcKNv9/QtXq9v2tWQ3oaF0SnAcBBBBAAAEEEDj6AnkTE74aWPutJIX1cP12mO/drvcBAIEjJcBn70jJHlJu6RMUhxSZ/w6TktDatauVmpaW/wF59oaGhKpZM27TWSQsDkIAAQQQQAABBBBAAAEEEDhmAnv37tGcJ Zozdq1OqVzFw0eNMRe3De/LSkpSa /8Zq Xfqt6tarp7Fjxio6Ojq/Q123r9QJiqImk6zsd4OGjexRFNYQPuu576eVvLCH8tmDJw6MoDDrIuVsRT2P6yJIgxFAAAEEEEAAAQRcIcD3YVeEmUY6UKAon73H5sxWYIC/ vfvpzVr1uj26bdp tQ7D0lSJCYmavodU1WlahVzbH tXr1Ks fO1m1Tbndgy49 lUp8m9HiVtVKQKxZ/a9 /2OlVv72q1as/EW//LpcP//yk5b/8qN  vkH/bTcenxvP6zjrKkgbAgggAACCCCAAAIIIHCMBTyJWrfsMy36O0GeY1yVMj19eW1XLiRPwi96etxpalO/nuqZv9Z3e/AvJfzxkE5tcrImfL7r2MWzIPv9P2tq90bqfNNSJZZpsI9sYfGbNim2Qax27dypuLg41atbV9PvnKaEhIScE9vJiTunqmbNmmrWtJl279ll7lrUQPHxm45s5Y6j0ks9gqLIbTXJhri4JvaoiayRE9bPPGtRWKMnrJyEnaLymltLFbn00h YEa/375quLxrepAcubiC3Lr1UekhKQAABBBBAAAEEEDjqAp4den9Ub437Ym/OqUOrNlaHU4dr3HUXqWOVUn7t379SM0Zdrt v/lILm0TqqP2VM6c1Hu39 QXdeeeT vCnzUo2 0NOaKLOgyfrwRv6qFpJm3eM2 VJ/FvvP/6w5r 1WCu3pJhWhatWm 4aNG6qJvWrWQYLBu7Xrw M1h2Lm q62berS81ghdRuoJD9MWoQ11C1KwXnjF8/6tdsQfYBEaplRt7H1apYBu0/eq1q27atWdJgnRo3bqzNm NVPzbWXnfxjrumaept0 2K3GESFrViYtTQJDA2mYRGTM0Y/f3P32rTpm3pK1pO rMl/SjnAixaFsE3jcO3ANLvi79UfEqqduzcYZdVtUpV1YsIV vefe0khddrJStyl12085Q4shk7tPzjhfrurPEmi3iEz1XiSvJGBBBAAAEEEEAAAfcKFPId1ZumhO0mORE3XvPv6aao9ERtX7VECx6eqvOWrNebH9 mkyPKanRyIfU4QsHJ3Pa Jgybqq9iBuraB05V08oe7Vy1XCs80QoPLKv6lFU5RUPw7PlWdw2 UE vilGPEZP0wMn1FJG2VX8t 0470s2U LLok2Rs1tJvt6rq2XN1xZntVCGnahdo7ocXZD87uu3OXydXHYLjNPrZDzXaPtAJdStaPS68YLimTZ9qL gbWz9WW7b8Z5Y4aGAvZWBN6bB 1qpdW40axdkjJmqb362pINu3bdfVV40rfVvLSX/2qCU/7SUmzH/2bd uTwaeo9R3P1Sv7j00auQVumzEKHXrcooSXn5N7w44Swk7dtqjK4o0xSPzP718Zn3VG/KBdue5fvd fJ4ZxjRAC Iz8/8csBcBBBBAAAEEEEAAgfIkULmJ2ptbsnbq2ltnjbhdT80 S5EbXtMLK60xB2ZL26RP7rtUPZub78/1Gqrt6eP11M97s4b5myH3K5 fpDPaNjCvmdebdtXlr2yQuZ9ezrbqvl5qaL1mHud9nD1aI2OLvpxxhfq2zNrfqu8VenTR1gPvy9im/7t7hE7r2Dyr3HqtddH/Nme9Xlh9cp03ZfXn iklWkMeuFfjzz9D/fqfqWFjb9c949qYMQf79OVoU3bXB/Vnznr8afrzwW6q1 Z6fW G1ZeoXYXVzXT835s8WD3aNc1uU5zaD7lVTz9zp0aeepLiLKNmPXTpzO 0K7 uiDdR398/wSQnmmj8O5/q elX6vyzTteAwSN03QNP6N4zqinAav9hbbPq0bNds x6xKp1/6v0xI97smOapqRUaceLg9Q0O269Zq1S8rp56levhcZ9m5SlnLFdXz8 Tme0a5hVTsNW6nLGFZr9hxnVkfSdJpxYX33mrs2JaYb9/laa9J15f4HxTdeaZy5RpyZZ14V1PV1w92f6L/cFZc5 yDWV9pce7FpfHab KmtMib2V1sFXzhH8GW5ukzz19mmK3xRvL5RZK6a2naSIMwmJuEaN1LBhQzVt0lhbt2xRTEwts/bEansUhfUe671F2awRN /eP0ZndvRddy3UZeBVeuiz/w76nBalLKceU/oRFEVNamWvJ7F09JVqfckINTMrmyasXKltzZvYiYuoP/9Sz uv1x9LvtIXF12scz9daMxyFV7QeXLvz3tMYa/ljUhxjs37Xp4jgAACCCCAAAIIIHCkBfJ 1819vny/y/opuGIVhZlu3t5kc4AnQd/dcZ7GvFVbY 95Vf1r7tKimTfqzkumqMFXj6nrf3M19vZPFTPpcb3RO0aebWu1u/4JsgcoZJdf67L5evL8OmbovZ8iakeYMpP00z3nacTT0sBb5uj2ptKfr9 rey49X8nvfKhb2piOV Yu/fzxIq2rf41mP9BBVTIT5G1iyj1MfXpXOjDiI6R6M9XSu/rq1S 04cQBqhuaezRIhFqd2VqBC7/Usi3XqFkd08XJ3KlflmxUcKtbVX/9XA0udrsKt odtk9/f/OTtjW9QU9e1VYV9vykZ6Y8rDt aqghN03VvKZh2vrZg7plxljd3/lr3d8 7OCrY98PevrtHYo4c4ZGt444eOC470hvUWyz6rG1yfWaM6aVwpPW6NPH7tK9lwWq6ZJZ6pk9ZKLyWY/quaubyrpZb2i1ugral30SK64mhj8/MFTDn0xW30kP6LqTq8mz/j2zaOPb v6/dKlurmN911nu662g HoDVLXTpZr25NWqXtGrzYvn6OZHxuvmtt/qmdOj5V/QNZX3Wi4Lh4qlHD2Uu04HR/KgZxHhEWY6xzQzrWO6 WO7zGiJRnaSIqZmDfmZpQ62bttq1p I0T///KPN8Zs19dZpst5TlIEi9oibIXlG3KSaETffmxE3aQFHdfJBIQSlfqn0CYoiVsGa4vH755/rBLNYSFMzxybt7ru1ccd2fXv26fYcti6ffqmGZoGQZsPO15YlX uXhR rzamnF7H0Ih5mZUFnTNF9CxZrbVKAopufoavvvksj21Y8dB6dyYp cPskPfzpSq3Zsd cIFg1Wg/QqFtu06iO0VkZzSKelsMQQAABBBBAAAEEEDh6Al5lpOzV1n /1Yt3vKqtoV10S4sK8uz8QI 8sk2dHnhHNwysZn//bXnvFi3s/qBeXZGkTiGbtUcV1atLN53cynSa1fqQKleoFmcW94vNWRvAs/NLzXh gxpc 5keGt3IfGOWundqoOSVp2nOjMUa8/wZqpJdSlTTnurXvbVCs597dnxUaH16dzcdt wtsP6lmn3vnxp92zh1  gR9Rw6XCNGnK8eseGmHf6q1H6Q2gTcqHe 3a6Lz6 pgKQ/9fk//mp e0uFJXxS/Hbt KLwunXKqlhko67q2dVqU3vVXv OFs2O08DhZ6u79QfxdsH66q1LtOybTUpv3/igNe7St/ h1aaL0eCURgovoO/s2VV028jG3dSnh1WP7upUZ6O OOtNffD3fvVsk1XP4Cqxatq0aY59hi9BYV727l6sR55dpzpXfaDHJ51oH5MZF69ZJkFRnC1vfK33RjXro9OaZZXStnll/fXWqXr56/VKNQkK33STvNeUckbBZL2vTBw65EkQFadhxTw2IiJCt9861U5SBJvpHtaCmNu2b7PXYaxiljVYv36dPXLCOsY6tkibNeLmAd Imzd1XRvr85m1WaNu7C1ly6FFWSNPHrtNdz/7mf41Ma/YqJ9G3nqXxvWonvUZtkZNLbhVk2e p993meVvK9RWv9tf1hMX1M16vTj950PPXqI9pUpQeM0qlunpea6gQqqxxZuprnfeoYTff1f8jm36xwy3OnvQUIPrp29efFWBJoA1khLV J479dOvv6ht9qgLq8gCz5OZrkwro5W5X0mJCQrK9QFPTLHGU3mVaeqYnpas76ebjPE7tTTmzgUmY7xbi2fdojsvvVl1v3hEvUIy5DHleD3p9rn803bqt6  13 NrtGse09U2P71 nrBo7r7/JXa/fabuvbEAzO48jbZcmFDAAEEEEAAAQQQQKAsBQr8PmydxPed IdxahNrzWfP2gJiT9XkZ /UadGZSvxlmVZnZGj7tR0Ue 3BNQuK36OAASN1ZYdP9cB53fTL2Rfpkksv1IBWVbI6Khnp9h95vR7zvdp8V/Z9292/5lv9nXGC neuJj/rO7dVrF9NdTF/0Hv0y6Vam9hXUf5Z39e9ngz7vfbUBbPtX1t4fVLTg3P9ETFA9Yc8qE8GTNKPH7 hV1 cpRHPP6g2V83TU5M6qlLlzjq/nb9uen2x/hs4SFF//59 SYnT5e0rKaRaCdp12Lod2qao2pVMo7ZpW0Kq0oOtTklFswil9OOOvUrJ02dKN3HI8sxQhnktvzujlNTWL7qxqilBm3fvN96H1tOyz8jItM/vMXFNXPONmRpTRb161lFAdgwz7de98mSamOYT 9zvL gcpses9R/P0l2Pv68fVm9VcmCkQsycjeB2yUoz5wnMp1z7wshT57QSXmMHO5S821vcPm Wr/m8eD12EsHr8chjHlY51k9rs17LMO0v9DNtH5m97Vuq daImzPu12XNg 1r5pAtPU9/1ow8WX7vUI14Vjpr8ixNsUY3vfmA7jejmxLfeEeTW4cp7a/ZumrqQsWMn6lXe9WUZ/s67a5XUV7rOvAmFN5/LmBUSmn7wiWPVLZIUStgTePYsXOXIipXVmK71vrGzLE689yh5h8TM7zHZJO6vfOO3n/7dZ3dppUiTSi3mbUqrPf4tgLPYwJt/wO5/Aad0vKGQ IkNbeuAGXu FIz/7dNHe95TdeeeYL9j12Lu0zGuM8MvfZronq2zy7HKi/7YRUWGXeKevVoaTKJXdWjx4nyO/08PTPrG418oo8KiEk dWAXAggggAACCCCAAAKlEyjw 7BVrO87cZNr9fy9XRWZ9KtmXz1dS2NO0amtzGhh63Wrk6QI9X/gBV1zojXY37f5q0L1aPmFnqArXliiPkte17NPztN1g fombGv6qWJZuqA9Yc8 zzWqbK/N9untbvZB31/znqeXXau79V2HXO/93D1yXWsr6Z oTFqf 4EtT9nlEbMuVCDZk7WE6d osnNq6jr8M4KvO5VfbnV3FJz0dfaWW gutUMkDeocfHbddi67cqqUq42 ZAXpFsAABMXSURBVAcHmV7MfmVkWp1Rq7cRoBDT2/KY5548bQmIbqTa5raBv/6wVslDq5l1NA7dSmwbEGDObHWKs7ztkvPa23GzXzD1y1Cm6R0FmSr7rrGca82ut58CzGuZqVYHOCv2B73uKyvPOdL nqvLJzwj//OmauZdrVXNu0YvTrhWn1jH28daZ7ercNB1Yb9g7899XZXgGsvPIavkYv 30M9entKsW4nee/89ql2njr0opjXFw7ohhLXtNDeIqF27jlJT03T3vXfp5sm3FGkUhTXiZo0ZcRPbJc5M2cqyO6QR2bHxuWXuXKRHF2xU7MQPdd oOHt00yntY5X821l6cuZXuvypU1Vh72btNYm0nmb5hXYnWqMyWtrFWu31HK7/3K2Ioz8OqWjhO0q5SOaBC8X xyafR97TWxe1v7 ZI2Ou8qzbjVq3Gs263aj5RQHmQrL 8bS2vAmK/Mq3LxbrGm5kVix  WW9 sqBx1MTG1u8dr1SNv6kNSZTuezGrmrSuIkamUfTPvfob5PZ27I1yYzC8H1Isz8gvgDn gfXG9pIfTtUVMpfP2hjav7tzbp4D5SVt/08RwABBBBAAAEEEECgJAIFfRf27be/E0fUUbPmzXVih/N1/ zhqvzNdE149l lmO 2wbXaqL5/ov74V Y2jg3tRfuyHrGKifDP i7vF6bY7pfqjhc/0UvDq r3Bc9phVm/wmsmKESYnMb PUnKyPWdP7j2yYoL3KHvzDSGVN/ 1I36etkuBTU SbWCs78z2w0  PtzkeqT61wHtd900xr16Kya2qo/t6SauvspuutI9Q//VS 8/a0 /SRedQb0V12zgIb9vuK2qyhWeduUE1RfO7N3 DrgudqiiLa6oHeE9r4/Q6/ sz/fflTJbbPOa0XNbnveetr1yD7G/BJU40Szvsd2ff/DFvNX81wxskNmnvtHKaaitPWPjUrKTnr43m /XsA5ktb8oLWmwzt64lB1a9VUTU5sqYZRdqHZ78n/mspbXpk55G5brt zo1TIj1wmBZThuzYTEhJ0131320mIevXq2VM5atSoafqbW/Xflq2qXr2G4jdvUv3Y nYC425zrPWew322fSZ22Aqpg68R1vEpG77XvxlV1blLLQX53hNUR6d0iFba399rY4pXoSeO0pgOCVpwYV8Nue4xvbtiR841UJT c371zuqcF8J5mJdKN4Ii 8N2mHPkvFwluqq5Q8d2Re3areZbd2nJZSPU47kFVl5Ciy4arhYXDFOguYPHrvRUVTuhuj31IzdyvufxfSCiYtXK3Hs211o62rvd gRYK9P6PgQR6nf/c5rUwjfzzSrRT2FWxti7NevDm/di9T23T24abK12YobkeO0PZ741Km1MCiiU3QgggAACCCCAAAJuFrA6AwVuvu/EOd97zSL07a/Vo6OW6LyHb9BzPV/V6Ia9dPWQ6rps/hiN95 o8zvGKCRps1btitO5Q1srbPOnZn0AqUmzmgpLi9c3f5u7dERUU4RZzdAbVEsnNQzUK6/P0nOtLlIz7xZtr9ZH57TpoYnD62jYzKt0c j1OreJV3  8ZAeW19Xox7opkrZ9bHrfdD3avMtvErh9amY60 p 1c8rlteTlWbTq1Uv2qoMnf/q8 feVH/ bfQqAahdgfP6vRfNrSmBs2eorUZtTXmdLMYpNmftqkk7TpM3XyxyNWmrF0HOrNZ7bUbnqsTnx1Bv0rqcdPtOvX7G3WfmfK ctQF6nNijMI8e7Tht VaX3 UbjmnZLY5HfzsuuVnn3MtmWP8T il0f0jNe7h8ZoWMkFnxvlr3RdvapV548lWGUF11e 0Onp83jTd uT1GtSysjzrftduq12FxDe0TmvF6Dk9Pft1RZ/VTFUC/tP6xKyukl3H4AKuqRY52RPbza9yGTpk8xfrRxH7vNbICSvhUNesuVjHJB82btxgftY1txJdrY0bNtl/fE9LS1WD2AZ24qKeOc5q311mJMWUm6YUOpIiIDrOHnGz4kcz4mZI/iNu7OvNvtx811vW84NilHVE9iVhXgltrMufW2xGTb2hZ fP1/VD5urZq17WggmtskZdmRFXBfefs8 XF7OQf6byHprf81IlKKxzF/oPZZ4z1jBB e/yMYq5bKTaNW hgJBgvfvWayY54FXbiy5SazO0xG/x19r27DOqd5OZrlHEKR6 0 R8GHN2ZP1i7Q OaW0yxq/qTytjfHaDnAVicg41GSRr82ZmZg1d8gU49z8o6Zv03fI9CoxtrRp2NjhPA7OfFrA7/4PZiwACCCCAAAIIIIBAEQQK/d6d64vpge/EFdTyyrt0wfuXaNYd7 nMZwar85SXNCf6Hj36v6ka 6RZry2gshoPuFn9B7dS4Pbf9Mmc53XPNmt e6CqNOunyTPGqKn1vdcsddlv6jSdc839enjCIimouk65prUGtGmoNtc/ryfC7tSDcybq/QSzMKJJhIx7cqqubGXWbMvpLFkN9HWcfI2NLLQ UTl/q/Qo3S9akdte0byp87XD3DZTZlJErTan6fpnbtQFdcwIbLv9IWoyfLTaPTdNy5teobPqBdn700rYrsKsovLpK/jiY/tb9cmOid2Nyzne13bzd88aZ rh96rppFlz9crLd vDvdb6ecGKbtBGfS5NN7eNDCuRbc51Uoi93Y zqmIdY2x73/2spobfpfkzxum1pBDFNKtr/ozrrwDrb7PeYDW5aq7u3TNFMx67Xgut24QGmlEVzTurZeUs  yelN1uX18ouOkYPTZlq2574g5d8UrWvVZDK9VW2/rWXUus8xZwTTX3leG7XsrG4YB88X6zrbJjWdg73//wfXO3jppm9ERtbdi43k5OrF 33vy QZPGX2td/Zo56xF76k2D2PrauGmj6ppj0sx0j fNSKWxV15dcPHWiJteEVry/qP636hndFlc7j 4Z7/Nd71l92eDa52sRoGv2ou0prZqaE/xUNqGrNFNjXyjm8w M7qofvdLNL3buTrzrrN18YsvaOXlD6r94frPBZj44l9wYwp/xW/82Cu9sx6fq11mPkxxtkvueEt3X3OeYisX/q658 Zo8g23aMu2zfaUji/6n66OZnhPTI8eSm5/kvzr11dgYKC8u8wwsI8XapO508cP//6jIcuWKdNM9QgJDtH9D96jq0aPzf9EmVv12rDemhrysJYuOO2gERT7Pr1UHScl6fbP/6cLaiRp6bSBGvm6V91Hj9d5HWqZjHG8Vu82GeMhrRXlWa nB52hh7yX6rGZY9W79mbNOvNcPZneU6PHnKV2MV6teu9RPfRRqoY  76md7RWysh/W7tbmvKIud/07YPyP4C9CCCAAAIIIIAAAggUQ DFF57XiJGjivEOlx6avFzTzxijddd8oKcGVufOeyW8DNL na2zBr6uLq8s1NTW XSGS1iuE9/23DNP66JLLs23akXt81oJjOsnX6/evXrbd yoVq2aGUGxUevWr9fokaNVqVJFe4HMlJQUzXlijp3EiG0Qqx1mdkGVKifo448/0h1T71BohQqqEJq/d aWD3Tt4Mn6NKmRzhg5zIy4MSOdMs2Im99/1vp6o3TzWR49n7s/G unX 8fpAtf8NOZN1yXNbrprYdNf9ZfI195U9ebRTIzNn2mV76RGjfNGjW1yNxEYu7mYXrzoxvUPHhf4f3nAhaLKGlfON4kbObPm5dzh6B8A1KUnUXJJvnKsaZsdHjpBS278GLVWbdWJ3Q6SRHJSXY2KWH3Du147lnFm2Evfd57Nyfz5ntvgefJydL5MmwHap2TvbGPiVSnW17U41XuM4tlTte4edkZ4zMmq98gszBnQC2dfc1wfXrry7r7xf46ZXIFuw4BweZuH4/foHk7TbIkpr0uenCaru1g3av2QHbwUKeCUheHHskeBBBAAAEEEEAAAQSKIlDg9 GivLk8H Pdr/jf/zWL/SXo5 en6e2I4Xqxv7mNaqHf18szSHHblqo1772iZQH1VL GWVB17z/69ImntaHGEN0bF1Kk0QPFPePxdvzhPnvJyclqHNdIq1avUlzDOK1ds8ZOTgwbOszcrSNDSUlJCgoOti0vHHahFry0wNzJJF2N4rKOrW4SGnv27FG42Wf1M0PzSVL4Vx gh96pplcee8Ksu3iPPvKNuIlto96XpinDxO g/uxtrdXmuuc11xrdNHeSPjDTayKtaV5P3KYx2aOb7NFFc1/QvdmjpqKb9dUND41WE3vU1GH6zwV2eQt8oUhhL9UUD2tgUGHBSk21x1/lbFYzK5qFQfp/8X/6deFC/fDrSnNnj6y7dVQ7oZrqXnedBg8caI83sm69YgXHt1nZphBzG9JDNv9qGvq/lRpqv2DV58ARkX2f1e /ZT236xlUUz3HzTSPvKVY7zP3pe1xk15ZclPWi2n/2PWw9r18c9b9gHPexT92eQF5jgACCCCAAAIIIHCEBQr73n2ET 3s4lPX6n83Xain1vqrapvzdc/cq9Q85OB gbMbcIxrl5mg9T9/onkf/amtieaPuP4Vzd0ihunB yeodQUcD9fntaJnJSF69eythZ9 ok8/ 9SeunH2mQPtREOAuTlEsJkVUKFCqJLNsVFRUbrwAvOH8f9bqE9Mn7hKlWj17dXH3M7V3E3FTM wPucFfdYDqpysi6Y9ZR75XDPZfdec/qxVTkA1dR/3mHnkOT67P1uh9US9 MXEQwvz9XcL7T8f ray2FO6BIWdSMiVEchTox07dtgBse7xWqNazEGv9ho2vEj1t4Jk3dnDKism5uAyilRASQ/yBSX7Aim4lfmcwKwizIYAAggggAACCCCAQFkKFPa9uyzPc9yVFdxUk95boUm5Ko5VMaLoH60et72sz2/L5z38YTb7j eF9watP6RXrlxZZ5810NxCNNVONFh9WGu/lZCIjDTLA5j1Fa3n1mKa1tIH55x9rjKsERNmCwwKsqd2hIWFmWRG1kiLfKJxfOwqZV 4VAkKK0yF5Cfs1xrENtKjsx42Qcq6dWhxVa3ANoiNs8sq7FzFLfewx e Bq1zH/YNBw4ozrHFKJZDEUAAAQQQQAABBFwscFS/C7vYmaYjkFvgcH1e69jAwCCToDALuUZGKd0kHawEmbXOYpBJPFiJCWuzPr8BAYGqWLGSwsMj7FEX1sNKVgRYx5qH9bvv2Nx1OJ5 L21fuFQJiiyogqtgDVdprEbmFir1SmUaYrJIVlnFSxOU6pRmAd1GmvDxr5qQdYmUsjDejgACCCCAAAIIIIBAaQUK/t5d2pJ5PwIIFCZQtM9eYGCASUwE5Cno0PceOC7vEgaHHltYrcrja6VOUBQ2fMoanlLT3GqlrLbCzlVW56AcBBBAAAEEEEAAAQScKMB3YSdGhTq5QYDP3tGL8hFNUBy9ZnAmBBBAAAEEEEAAAQTKtwCdpPIdX1rnXAE e0cvNiVOUFSKrCBPRqZSM8xsiACGovhClprpJ29mhiobHzYEEEAAAQQQQAABBMpCoIJZPM 6VaG1iB4bAgiUjUCSuT1oYZ8p rzFcy6LvnCJExQ9T2qoRct U89OLc1iHty1whc6j1kM9Mtlv6vnyQ2LF02ORgABBBBAAAEEEECgAIHGTZrqx  /18nt28tKVrAhgEDpBPbv36 fflimxk2bFVgQfd4CafJ9oSz6wiVOUAzp1UKvf/GbHnrmfe1LSsu3gm7cGRUerN4nN9Lgni3kycy6bYwbHWgzAggggAACCCCAQNkJtGnTVj//vFwLP/lIKSmpZVcwJSHgUoHQ0BA1adpc1mcrIyP/fht93uJdHGXRF/YbP/ZK76zH52rXzh3FO7s52loE07qliu/WKcUuoBy wZqfZF3gaWkkbcpheGkSAggggAACCCBwzAT47n3M6DlxORQoar Nz13Rg19UU6vE/1v4sc4ZfJ4SExPsE8Rv2qj58 apxCMorEKsTjgd8aIHjCMRQAABBBBAAAEEECipAN 9SyrH xAouQCfu5LbFfZOKzmR31aqBEV BbIPAQQQQAABBBBAAAEEEEAAAQQQKEjAN3Ii7 v eXfwHAEEEEAAAQQQQAABBBBAAAEEEChLAWtaR0REpF1k7t9zn4MERVmKUxYCCCCAAAIIIIAAAggggAACCBwikHtaB1M8DuFhBwIIIIAAAggggAACCCCAAAIIHA2B3NM6mOJxNMQ5BwIIIIAAAggggAACCCCAAAII2AIFTetgigcXCAIIIIAAAggggAACCCCAAAIIHDWBgqZ1MMXjqIWAEyGAAAIIIIAAAggggAACCCCAQEHTOpjiwbWBAAIIIIAAAggggAACCCCAAAJHVKAo0zqY4nFEQ0DhCCCAAAIIIIAAAggggAACCCBQlGkdTPHgOkEAAQQQQAABBBBAAAEEEEAAgSMqUJRpHUzxOKIhoHAEEEAAAQQQQAABBBBAAAEEECiNQKDvzfGbNpamHN6LAAIIIIAAAggggAACCCCAAAIIlFjAb/zYK70lfjdvRAABBBBAAAEEEEAAAQQQQAABBMpA4P8BPsUKMWE0158AAAAASUVORK5CYII=[/IMG]

---

### Post by kansasnoob on 2014-04-07
I don't use Wine but wanted to be sure you're aware that after we got [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787") fixed we can no longer edit the menus using the Main Menu buttons, but the command here does work:

[http://ubuntuforums.org/showthread.php?t=2184682&page=34&p=12971626#post12971626](http://ubuntuforums.org/showthread.php?t=2184682&page=34&p=12971626#post12971626)

[ATTACH=CONFIG]251791[/ATTACH]

[ATTACH=CONFIG]251790[/ATTACH]

---

### Post by kansasnoob on 2014-04-07
> **cedric5 said:**
> thats not hate I feel, it's being in despair, hence the ](*,).  Sorry if I acted too harsh. At least I know how to patch gtk, so I can  fix this for me, but the extra work is getting more and more,  specifically in things where they remove functionality without  considering that people use the software for many different purposes...


try the MainMenu applet, and see if wine gets shown there

I've forced myself to use Trusty since March 27th and I share in your frustrations :(

Those frustrations are not just limited to the flashback + metacity session though - I definitely plan on using Precise until at least 14.04.1 unless something huge changes within the next several days.

I'm glad Ubuntu Precise is supported until April 2017 :)

But hating devs in not acceptable, they are just people after-all.

---

### Post by frank18 on 2014-04-07
> **kansasnoob said:**
> Well it's crunch time again ;)

In order that others can follow what I'm doing I'll start posting a lot of "thinking out loud" stuff here. In this case I have a fresh install of Ubuntu Trusty final Beta and I want to record what happens when I install 'gnome-panel':

```
lance@lance-desktop:~$ sudo apt-get install gnome-panel
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel-data gnome-session gnome-session-flashback
  gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete
  libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0
  metacity notification-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base
  gnome-themes-standard
[B]The following NEW packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel gnome-panel-data gnome-session
  gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf
  indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1
  libpanel-applet-4-0 metacity notification-daemon[/B]
0 upgraded, 20 newly installed, 0 to remove and 117 not upgraded.
Need to get 10.2 MB of archives.
**[COLOR=#ff0000]After this operation, 50.5 MB of additional disk space will be used.[/COLOR]**

```

Stay tuned :guitar:

Edit #1: First flashback w/metacity login looks good:

[ATTACH=CONFIG]251562[/ATTACH]

Edit #2: Flashback w/compiz is broken in many ways, but my focus is on the metacity session anyway. Someone else will have to deal with the complexities of compiz. Sorry but that's just the way it is :sad:

Edit #3: I know I'm going to want some additional packages and I'm going to list them one by one:

```
lance@lance-desktop:~$ sudo apt-get install dconf-tools
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dconf-editor
[B]The following NEW packages will be installed:
  dconf-editor dconf-tools[/B]
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 113 kB of archives.
**[COLOR=#ff0000]After this operation, 528 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
[B]The following NEW packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
  gnome-tweak-tool[/B]
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,001 kB of archives.
**[COLOR=#ff0000]After this operation, 7,561 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install indicator-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following NEW packages will be installed:
  indicator-applet[/B]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.0 kB of archives.
**[COLOR=#ff0000]After this operation, 1,197 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install shiki-colors-metacity-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following NEW packages will be installed:
  shiki-colors-metacity-theme[/B]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.0 kB of archives.
**[COLOR=#ff0000]After this operation, 266 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hddtemp libsensors-applet-plugin0
Suggested packages:
  ksensors
[B]The following NEW packages will be installed:
  hddtemp libsensors-applet-plugin0 sensors-applet[/B]
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 159 kB of archives.
**[COLOR=#ff0000]After this operation, 898 kB of additional disk space will be used.[/COLOR]**

```

I'll probably want to install more but lets see what happens.

Edit #4: Moving the window management buttons to the right has not changed since my OP:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

Edit #5: Applying the Shiki-Colors-Metacity theme is the same as Saucy:

```
gsettings set org.gnome.desktop.wm.preferences theme Shiki-Colors-Metacity
```

Edit #6: Disabling the overlay-scrollbars seems to still work the same:

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

But I need to rinse-n-repeat because I think an additional option has been added?

Edit #7: I disabled the webapps:

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

Edit #8: I used 'gnome-tweak-tool' to set the desktop to display mounted volumes:

[ATTACH=CONFIG]251605[/ATTACH]

And to set the key sequence for killing X:

[ATTACH=CONFIG]251606[/ATTACH]

It can also be used for changing themes:

[ATTACH=CONFIG]251607[/ATTACH]

But I had to use the CLI to restore the missing menu icons:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```


Hi KansasKoob isn't all that software comes with the install of Gnome-session metacity desktop out of the box?

---

### Post by kansasnoob on 2014-04-07
> **frank18 said:**
> Hi KansasKoob isn't all that software comes with the install of Gnome-session metacity desktop out of the box?

The package 'gnome-session' does not include the 'flashback' sessions.

Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.

Those additional packages are not direct dependencies or even recommends so they require separate installation if they're desired.

---

### Post by kansasnoob on 2014-04-08
> **albertsmuktupavels said:**
> This is because menu editor by default uses default applications.menu file.

Workaround to this is to open menu editor from terminal:
```
alacarte gnome-flashback-applications.menu
```

That way you will see correct menu, but there is probably other bug too. I was able to hide/show whole group (for example Accessories), but I was not able to hide applications.

Hi Alberts. Things have been hectic here but I finally had a chance to give this some serious play-time and opening either of the existing Main Menu listings after using that command I can then select Properties and change the Command from "alacarte" to "alacarte gnome-flashback-applications.menu" and I can then edit all of the menus just as I wish :)

I do have two stupid questions though:

(1) What's the proper path to "gnome-flashback-applications.menu"?

(2) What file would I back-up to restore my custom config? Or how would I restore the default if I totally broke things?

---

### Post by muktupavels on 2014-04-08
1. /etc/xdg/menus/gnome-flashback-applications.menu
2. Your edited files might be stored in ~/.local/share. To restore to default you need just delete your custom config. I am currently writing from mac so I can not check where exactly files are stored.

---

### Post by kansasnoob on 2014-04-08
> **albertsmuktupavels said:**
> 1. /etc/xdg/menus/gnome-flashback-applications.menu
2. Your edited files might be stored in ~/.local/share. To restore to default you need just delete your custom config. I am currently writing from mac so I can not check where exactly files are stored.

Many, many thanks :)

Restoring most defaults used to be this easy:

[http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600](http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600)

But the changes between Precise and Trusty are fairly extreme :(

I certainly wish that GNOME dev would have chosen to use 'gnome-panel' + 'mutter' to produce their new Classic session instead of choosing the path they did ;)

---

### Post by kansasnoob on 2014-04-10
I went ahead and filed a bug report using a fresh Edubuntu install:

[Can't edit drop down applications menus in Edubuntu Trusty flashback session]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1305348")

Please confirm if it effects you too :)

---

### Post by kansasnoob on 2014-04-10
[Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=trusty") is now working but may cause the panel to load a bit more slowly.

---

### Post by Smask on 2014-04-10
> **kansasnoob said:**
> Well it's crunch time again ;)

Edit #6: Disabling the overlay-scrollbars seems to still work the same:

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

But I need to rinse-n-repeat because I think an additional option has been added?



org.gnome.desktop.interface ubuntu-overlay-scrollbars?

Found that with dconf-editor.

---

### Post by kansasnoob on 2014-04-10
> **Smask said:**
> org.gnome.desktop.interface ubuntu-overlay-scrollbars?

Found that with dconf-editor.

Is that from an Ubuntu GNOME installation, or Ubuntu?

---

### Post by kansasnoob on 2014-04-10
> **kansasnoob said:**
> I went ahead and filed a bug report using a fresh Edubuntu install:

[Can't edit drop down applications menus in Edubuntu Trusty flashback session]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1305348")

Please confirm if it effects you too :)

I'm getting ready to wipe some old installs to prepare for the final round of Trusty testing so I'm going to post some stuff here that doesn't even make total sense to me.

This is from an Ubuntu GNOME install w/o flashback installed running the new GNOME Classic:

```
lance@lance-desktop:~$ ls /etc/xdg/menus
gnome-applications.menu  gnomecc.menu  gnome-flashback-applications.menu

```

Now the content of each with NO edits:

First "/etc/xdg/menus/gnome-applications.menu":

```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Applications</Name>
  <Directory>X-GNOME-Menu-Applications.directory</Directory>

  <!-- Scan legacy dirs first, as later items take priority -->
  <LegacyDir>/etc/X11/applnk</LegacyDir>
  <LegacyDir>/usr/share/gnome/apps</LegacyDir>

  <!-- Read standard .directory and .desktop file locations -->
  <DefaultAppDirs/>
  <DefaultDirectoryDirs/>

  <!-- Read in overrides and child menus from applications-merged/ -->
  <DefaultMergeDirs/>

  <!-- Accessories submenu -->
  <Menu>
    <Name>Accessories</Name>
    <Directory>Utility.directory</Directory>
    <Include>
      <And>
        <Category>Utility</Category>
	<!-- Accessibility spec must have either the Utility or Settings
             category, and we display an accessibility submenu already for
             the ones that do not have Settings, so don't display accessibility
             applications here -->
        <Not><Category>Accessibility</Category></Not>
        <Not><Category>System</Category></Not>
        <Not><Category>X-GNOME-Utilities</Category></Not>
      </And>
    </Include>
    <Exclude>
      <!-- Exclude everything we put in the X-GNOME-Utilities whitelist.

           Please keep the list alphabetically sorted! -->
      <Filename>deja-dup-preferences.desktop</Filename>
      <Filename>eog.desktop</Filename>
      <Filename>evince.desktop</Filename>
      <Filename>file-roller.desktop</Filename>
      <Filename>gcalctool.desktop</Filename>
      <Filename>gnome-dictionary.desktop</Filename>
      <Filename>gnome-disks.desktop</Filename>
      <Filename>gnome-font-viewer.desktop</Filename>
      <Filename>gnome-screenshot.desktop</Filename>
      <Filename>gnome-terminal.desktop</Filename>
      <Filename>gnome-tweak-tool.desktop</Filename>
      <Filename>gucharmap.desktop</Filename>
      <Filename>seahorse.desktop</Filename>
      <Filename>vinagre.desktop</Filename>
      <Filename>yelp.desktop</Filename>

      <!-- Exclude Sundry items -->
      <Filename>alacarte.desktop</Filename>
    </Exclude>
  </Menu> <!-- End Accessories -->


  <!-- Accessibility submenu -->
  <Menu>
    <Name>Universal Access</Name>
    <Directory>Utility-Accessibility.directory</Directory>
    <Include>
      <And>
        <Category>Accessibility</Category>
        <Not><Category>Settings</Category></Not>
      </And>
    </Include>

    <Exclude>
      <!-- Sundry exclusions -->
      <Filename>orca.desktop</Filename>
    </Exclude>
  </Menu> <!-- End Accessibility -->

  <!-- Development Tools -->
  <Menu>
    <Name>Development</Name>
    <Directory>Development.directory</Directory>
    <Include>
      <And>
        <Category>Development</Category>
      </And>
      <Filename>emacs.desktop</Filename>
    </Include>

    <Exclude>
      <!-- Sundry exclusions -->
      <Filename>jhbuild.desktop</Filename>
      <Filename>java-1.7.0-openjdk-jconsole.desktop</Filename>
      <Filename>java-1.7.0-openjdk-policytool.desktop</Filename>
      <Filename>log4j-chainsaw.desktop</Filename>
      <Filename>log4j-logfactor5.desktop</Filename>
    </Exclude>
  </Menu> <!-- End Development Tools -->

  <!-- Education -->
  <Menu>
    <Name>Education</Name>
    <Directory>Education.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
        <Not><Category>Science</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Education -->

  <!-- Science -->
  <Menu>
    <Name>Science</Name>
    <Directory>GnomeScience.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
        <Category>Science</Category>
      </And>
    </Include>
  </Menu> <!-- End Science -->

  <!-- Games -->
  <Menu>
    <Name>Games</Name>
    <Directory>Game.directory</Directory>
    <Include>
      <And>
        <Category>Game</Category>
        <Not><Category>ActionGame</Category></Not>
        <Not><Category>AdventureGame</Category></Not>
        <Not><Category>ArcadeGame</Category></Not>
        <Not><Category>BoardGame</Category></Not>
        <Not><Category>BlocksGame</Category></Not>
        <Not><Category>CardGame</Category></Not>
        <Not><Category>KidsGame</Category></Not>
        <Not><Category>LogicGame</Category></Not>
        <Not><Category>Simulation</Category></Not>
        <Not><Category>SportsGame</Category></Not>
        <Not><Category>StrategyGame</Category></Not>
      </And>
    </Include>
    <DefaultLayout inline="true" inline_limit="6" inline_header="false">
      <Merge type="menus"/>
      <Merge type="files"/>
    </DefaultLayout>
    <Menu>
      <Name>Action</Name>
      <Directory>ActionGames.directory</Directory>
      <Include>
        <Category>ActionGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Adventure</Name>
      <Directory>AdventureGames.directory</Directory>
      <Include>
        <Category>AdventureGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Arcade</Name>
      <Directory>ArcadeGames.directory</Directory>
      <Include>
        <Category>ArcadeGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Board</Name>
      <Directory>BoardGames.directory</Directory>
      <Include>
        <Category>BoardGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Blocks</Name>
      <Directory>BlocksGames.directory</Directory>
      <Include>
        <Category>BlocksGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Cards</Name>
      <Directory>CardGames.directory</Directory>
      <Include>
        <Category>CardGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Kids</Name>
      <Directory>KidsGames.directory</Directory>
      <Include>
        <Category>KidsGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Logic</Name>
      <Directory>LogicGames.directory</Directory>
      <Include>
        <Category>LogicGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Role Playing</Name>
      <Directory>RolePlayingGames.directory</Directory>
      <Include>
        <Category>RolePlaying</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Simulation</Name>
      <Directory>SimulationGames.directory</Directory>
      <Include>
        <Category>Simulation</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Sports</Name>
      <Directory>SportsGames.directory</Directory>
      <Include>
        <Category>SportsGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Strategy</Name>
      <Directory>StrategyGames.directory</Directory>
      <Include>
        <Category>StrategyGame</Category>
      </Include>
    </Menu>
  </Menu> <!-- End Games -->

  <!-- Graphics -->
  <Menu>
    <Name>Graphics</Name>
    <Directory>Graphics.directory</Directory>
    <Include>
      <And>
        <Category>Graphics</Category>
        <Not><Filename>eog.desktop</Filename></Not>
        <Not><Filename>gnome-eog.desktop</Filename></Not>
        <Not><Filename>evince.desktop</Filename></Not>
      </And>
    </Include>
  </Menu> <!-- End Graphics -->

  <!-- Internet -->
  <Menu>
    <Name>Internet</Name>
    <Directory>Network.directory</Directory>
    <Include>
      <And>
        <Category>Network</Category>
	<Not><Category>X-GNOME-WebApplication</Category></Not>
      </And>
    </Include>

    <Exclude>
      <!-- Utilities exclusions -->
      <Filename>vinagre.desktop</Filename>

      <!-- Sundry exclusions -->
      <Filename>javaws.desktop</Filename>
    </Exclude>
  </Menu>   <!-- End Internet -->

  <!-- Web Applications -->
  <Menu>
    <Name>Web Applications</Name>
    <Directory>X-GNOME-WebApplications.directory</Directory>
    <Include>
      <And>
	<Category>Network</Category>
	<Category>X-GNOME-WebApplication</Category>
      </And>
    </Include>
  </Menu>

  <!-- Multimedia -->
  <Menu>
    <Name>Multimedia</Name>
    <Directory>AudioVideo.directory</Directory>
    <Include>
      <And>
        <Category>AudioVideo</Category>
      </And>
    </Include>
  </Menu>   <!-- End Multimedia -->

  <!-- Office -->
  <Menu>
    <Name>Office</Name>
    <Directory>Office.directory</Directory>
    <Include>
      <And>
        <Category>Office</Category>
        <Not><Filename>evince.desktop</Filename></Not>
        <Not><Filename>gnome-dictionary.desktop</Filename></Not>
      </And>
    </Include>
  </Menu> <!-- End Office -->

  <!-- Sundry -->
  <Menu>
    <Name>Sundry</Name>
    <Directory>X-GNOME-Sundry.directory</Directory>
    <Include>
      <Filename>alacarte.desktop</Filename>
      <Filename>authconfig.desktop</Filename>
      <Filename>dconf-editor.desktop</Filename>
      <Filename>fedora-release-notes.desktop</Filename>
      <Filename>firewall-config.desktop</Filename>
      <Filename>flash-player-properties.desktop</Filename>
      <Filename>gconf-editor.desktop</Filename>
      <Filename>gnome-abrt.desktop</Filename>
      <Filename>gnome-power-statistics.desktop</Filename>
      <Filename>ibus-setup-anthy.desktop</Filename>
      <Filename>ibus-setup.desktop</Filename>
      <Filename>ibus-setup-hangul.desktop</Filename>
      <Filename>ibus-setup-libbopomofo.desktop</Filename>
      <Filename>ibus-setup-libpinyin.desktop</Filename>
      <Filename>ibus-setup-m17n.desktop</Filename>
      <Filename>ibus-setup-typing-booster.desktop</Filename>
      <Filename>im-chooser.desktop</Filename>
      <Filename>itweb-settings.desktop</Filename>
      <Filename>jhbuild.desktop</Filename>
      <Filename>javaws.desktop</Filename>
      <Filename>java-1.7.0-openjdk-jconsole.desktop</Filename>
      <Filename>java-1.7.0-openjdk-policytool.desktop</Filename>
      <Filename>log4j-chainsaw.desktop</Filename>
      <Filename>log4j-logfactor5.desktop</Filename>
      <Filename>nm-connection-editor.desktop</Filename>
      <Filename>orca.desktop</Filename>
      <Filename>setroubleshoot.desktop</Filename>
      <Filename>system-config-date.desktop</Filename>
      <Filename>system-config-firewall.desktop</Filename>
      <Filename>system-config-keyboard.desktop</Filename>
      <Filename>system-config-language.desktop</Filename>
      <Filename>system-config-printer.desktop</Filename>
      <Filename>system-config-users.desktop</Filename>
      <Filename>vino-preferences.desktop</Filename>
    </Include>
  </Menu>

  <!-- System Tools-->
  <Menu>
    <Name>System</Name>
    <Directory>System-Tools.directory</Directory>
    <Include>
      <And>
        <Category>System</Category>
        <Not><Category>Settings</Category></Not>
        <Not><Category>Game</Category></Not>
        <Not><Category>X-GNOME-Utilities</Category></Not>
      </And>
    </Include>

    <Exclude>
      <!-- Utilities exclusions -->
      <Filename>baobab.desktop</Filename>
      <Filename>gnome-system-log.desktop</Filename>
      <Filename>gnome-system-monitor.desktop</Filename>
      <Filename>gnome-terminal.desktop</Filename>

      <!-- Sundry exclusions -->
      <Filename>dconf-editor.desktop</Filename>
      <Filename>fedora-release-notes.desktop</Filename>
      <Filename>gconf-editor.desktop</Filename>
      <Filename>gnome-abrt.desktop</Filename>
      <Filename>gnome-power-statistics.desktop</Filename>
      <Filename>dconf-editor.desktop</Filename>
      <Filename>setroubleshoot.desktop</Filename>
    </Exclude>
    <Menu>
      <Name>Preferences</Name>
      <Directory>Settings.directory</Directory>
      <Include>
        <And>
          <Category>Settings</Category>
          <Not>
            <Or>
              <Category>System</Category>
              <Category>X-GNOME-Settings-Panel</Category>
              <Filename>alacarte.desktop</Filename>
              <Filename>caribou.desktop</Filename>
              <Filename>dconf-editor.desktop</Filename>
              <Filename>fedora-im-chooser.desktop</Filename>
              <Filename>fedora-release-notes.desktop</Filename>
              <Filename>firewall-config.desktop</Filename>
              <Filename>flash-player-properties.desktop</Filename>
              <Filename>gconf-editor.desktop</Filename>
              <Filename>gnome-abrt.desktop</Filename>
              <Filename>fedora-abrt.desktop</Filename>
              <Filename>gnome-orca.desktop</Filename>
              <Filename>gnome-power-statistics.desktop</Filename>
              <Filename>gnome-user-share-properties.desktop</Filename>
              <Filename>ibus.desktop</Filename>
              <Filename>ibus-daemon.desktop</Filename>
              <Filename>ibus-setup-anthy.desktop</Filename>
              <Filename>ibus-setup.desktop</Filename>
              <Filename>ibus-setup-hangul.desktop</Filename>
              <Filename>ibus-setup-libbopomofo.desktop</Filename>
              <Filename>ibus-setup-libpinyin.desktop</Filename>
              <Filename>ibus-setup-m17n.desktop</Filename>
              <Filename>ibus-setup-typing-booster.desktop</Filename>
              <Filename>im-chooser.desktop</Filename>
              <Filename>itweb-settings.desktop</Filename>
              <Filename>jhbuild.desktop</Filename>
              <Filename>javaws.desktop</Filename>
              <Filename>java-1.7.0-openjdk-jconsole.desktop</Filename>
              <Filename>java-1.7.0-openjdk-policytool.desktop</Filename>
              <Filename>log4j-chainsaw.desktop</Filename>
              <Filename>log4j-logfactor5.desktop</Filename>
              <Filename>nm-connection-editor.desktop</Filename>
              <Filename>orca.desktop</Filename>
              <Filename>setroubleshoot.desktop</Filename>
              <Filename>authconfig.desktop</Filename>
              <Filename>system-config-date.desktop</Filename>
              <Filename>system-config-firewall.desktop</Filename>
              <Filename>system-config-keyboard.desktop</Filename>
              <Filename>system-config-language.desktop</Filename>
              <Filename>system-config-printer.desktop</Filename>
              <Filename>system-config-users.desktop</Filename>
              <Filename>vino-preferences.desktop</Filename>
            </Or>
          </Not>
        </And>
      </Include>
    </Menu>
    <Menu>
      <Name>Administration</Name>
      <Directory>Settings-System.directory</Directory>
      <Include>
        <And>
          <Category>Settings</Category>
          <Category>System</Category>
          <Not>
            <Or>
              <Category>X-GNOME-Settings-Panel</Category>
              <Filename>alacarte.desktop</Filename>
              <Filename>caribou.desktop</Filename>
              <Filename>dconf-editor.desktop</Filename>
              <Filename>fedora-im-chooser.desktop</Filename>
              <Filename>fedora-release-notes.desktop</Filename>
              <Filename>firewall-config.desktop</Filename>
              <Filename>flash-player-properties.desktop</Filename>
              <Filename>gconf-editor.desktop</Filename>
              <Filename>gnome-abrt.desktop</Filename>
              <Filename>fedora-abrt.desktop</Filename>
              <Filename>gnome-orca.desktop</Filename>
              <Filename>gnome-power-statistics.desktop</Filename>
              <Filename>gnome-user-share-properties.desktop</Filename>
              <Filename>ibus.desktop</Filename>
              <Filename>ibus-daemon.desktop</Filename>
              <Filename>ibus-setup-anthy.desktop</Filename>
              <Filename>ibus-setup.desktop</Filename>
              <Filename>ibus-setup-hangul.desktop</Filename>
              <Filename>ibus-setup-libbopomofo.desktop</Filename>
              <Filename>ibus-setup-libpinyin.desktop</Filename>
              <Filename>ibus-setup-m17n.desktop</Filename>
              <Filename>ibus-setup-typing-booster.desktop</Filename>
              <Filename>im-chooser.desktop</Filename>
              <Filename>itweb-settings.desktop</Filename>
              <Filename>jhbuild.desktop</Filename>
              <Filename>javaws.desktop</Filename>
              <Filename>java-1.7.0-openjdk-jconsole.desktop</Filename>
              <Filename>java-1.7.0-openjdk-policytool.desktop</Filename>
              <Filename>log4j-chainsaw.desktop</Filename>
              <Filename>log4j-logfactor5.desktop</Filename>
              <Filename>nm-connection-editor.desktop</Filename>
              <Filename>orca.desktop</Filename>
              <Filename>setroubleshoot.desktop</Filename>
              <Filename>authconfig.desktop</Filename>
              <Filename>system-config-date.desktop</Filename>
              <Filename>system-config-firewall.desktop</Filename>
              <Filename>system-config-keyboard.desktop</Filename>
              <Filename>system-config-language.desktop</Filename>
              <Filename>system-config-printer.desktop</Filename>
              <Filename>system-config-users.desktop</Filename>
              <Filename>vino-preferences.desktop</Filename>
            </Or>
          </Not>
        </And>
      </Include>
    </Menu>
  </Menu>   <!-- End System Tools -->

  <!-- System Settings -->
  <Menu>
    <Name>System Settings</Name>
    <Directory>X-GNOME-SystemSettings.directory</Directory>
    <Include>
      <Category>X-GNOME-Settings-Panel</Category>
    </Include>
  </Menu>

  <!-- Utilities submenu -->
  <Menu>
    <Name>Utilities</Name>
    <Directory>X-GNOME-Utilities.directory</Directory>
    <Include>
      <Category>X-GNOME-Utilities</Category>
      <Filename>baobab.desktop</Filename>
      <Filename>deja-dup-preferences.desktop</Filename>
      <Filename>eog.desktop</Filename>
      <Filename>evince.desktop</Filename>
      <Filename>file-roller.desktop</Filename>
      <Filename>gcalctool.desktop</Filename>
      <Filename>gnome-dictionary.desktop</Filename>
      <Filename>gnome-disks.desktop</Filename>
      <Filename>gnome-font-viewer.desktop</Filename>
      <Filename>gnome-screenshot.desktop</Filename>
      <Filename>gnome-system-log.desktop</Filename>
      <Filename>gnome-system-monitor.desktop</Filename>
      <Filename>gnome-terminal.desktop</Filename>
      <Filename>gnome-tweak-tool.desktop</Filename>
      <Filename>gucharmap.desktop</Filename>
      <Filename>seahorse.desktop</Filename>
      <Filename>vinagre.desktop</Filename>
      <Filename>yelp.desktop</Filename>
    </Include>
  </Menu>

  <!-- Other -->
  <Menu>
    <Name>Other</Name>
    <Directory>X-GNOME-Other.directory</Directory>
    <OnlyUnallocated/>
    <Include>
      <And>
        <Not><Category>Core</Category></Not>
        <Not><Category>Screensaver</Category></Not>

        <!-- Really Fedora ??? -->
        <Not><Filename>gnome-eog.desktop</Filename></Not>
        <Not><Filename>gnome-file-roller.desktop</Filename></Not>
        <Not><Filename>gnome-gucharmap.desktop</Filename></Not>
      </And>
    </Include>
  </Menu> <!-- End Other -->

   <Layout>
     <Merge type="menus" />
     <Menuname>Other</Menuname>
     <Merge type="files" />
   </Layout>

<Include>
  <Filename>ubuntu-software-center.desktop</Filename>
</Include>

<!-- Separator between menus and gnome-app-install -->
<Layout>
  <Merge type="menus"/>
  <Merge type="files"/>
  <Separator/>
  <Filename>ubuntu-software-center.desktop</Filename>
</Layout>

</Menu> <!-- End Applications -->
```

And "/etc/xdg/menus/gnomecc.menu":

```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
  <Name>Control Center</Name>
  <Directory>gnomecc.directory</Directory>

  <!-- Read standard .directory and .desktop file locations -->
  <AppDir>/usr/share/applications/</AppDir>
  <DefaultDirectoryDirs/>

  <!-- Read in overrides and child menus from gnomecc-merged/ -->
  <DefaultMergeDirs/>

   <!-- Sort the control center categories -->
   <Layout>
     <Menuname>Personal</Menuname>
     <Menuname>Hardware</Menuname>
     <Menuname>System</Menuname>
     <Menuname>Other</Menuname>
     <Merge type="all" />
   </Layout>

  <!-- Stuff in the toplevel (Other category) -->
  <Include>
    <And>
      <Category>Settings</Category>
      <Not>
        <Or>
          <Category>X-GNOME-PersonalSettings</Category>
          <Category>DesktopSettings</Category>
          <Category>HardwareSettings</Category>
          <Category>X-GNOME-SystemSettings</Category>
          <Category>System</Category>
        </Or>
      </Not>
    </And>
  </Include>

  <!-- Avoid the shell having a launcher for itself -->
  <Exclude>
    <Filename>gnome-control-center.desktop</Filename>
  </Exclude>

  <!-- Personal category -->
  <Menu>
    <Name>Personal</Name>
    <Directory>Personal.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>X-GNOME-PersonalSettings</Category>
        <Category>X-GNOME-Settings-Panel</Category>
      </And>
    </Include>
  </Menu> <!-- End Personal -->

  <!-- Hardware category -->
  <Menu>
    <Name>Hardware</Name>
    <Directory>Hardware.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>HardwareSettings</Category>
        <Category>X-GNOME-Settings-Panel</Category>
      </And>
    </Include>
  </Menu> <!-- End Hardware -->

  <!-- System category -->
  <Menu>
    <Name>System</Name>
    <Directory>System.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>X-GNOME-SystemSettings</Category>
        <Category>X-GNOME-Settings-Panel</Category>
      </And>
    </Include>
  </Menu> <!-- End System -->

  <!-- Other category -->
  <Menu>
    <Name>Other</Name>
    <Directory>X-GNOME-Other.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>X-GNOME-Settings-Panel</Category>
        <Not>
          <Or>
            <Category>X-GNOME-PersonalSettings</Category>
            <Category>X-GNOME-SystemSettings</Category>
            <Category>HardwareSettings</Category>
            <Filename>gnome-control-center.desktop</Filename>
          </Or>
        </Not>
      </And>
    </Include>
  </Menu> <!-- End Other -->

</Menu>     <!-- End CC -->
```

And finally "/etc/xdg/menus/gnome-flashback-applications.menu":

```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Applications</Name>
  <Directory>X-GNOME-Menu-Applications.directory</Directory>

  <!-- Scan legacy dirs first, as later items take priority -->
  <LegacyDir>/etc/X11/applnk</LegacyDir>
  <LegacyDir>/usr/share/gnome/apps</LegacyDir>

  <!-- Read standard .directory and .desktop file locations -->
  <DefaultAppDirs/>
  <DefaultDirectoryDirs/>

  <!-- Read in overrides and child menus from applications-merged/ -->
  <DefaultMergeDirs/>

  <!-- Accessories submenu -->
  <Menu>
    <Name>Accessories</Name>
    <Directory>Utility.directory</Directory>
    <Include>
      <And>
        <Category>Utility</Category>
	<!-- Accessibility spec must have either the Utility or Settings
	     category, and we display an accessibility submenu already for
	     the ones that do not have Settings, so don't display accessibility
	     applications here -->
        <Not><Category>Accessibility</Category></Not>
        <Not><Category>System</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Accessories -->

  <!-- Accessibility submenu -->
  <Menu>
    <Name>Universal Access</Name>
    <Directory>Utility-Accessibility.directory</Directory>
    <Include>
      <And>
        <Category>Accessibility</Category>
        <Not><Category>Settings</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Accessibility -->

  <!-- Development Tools -->
  <Menu>
    <Name>Development</Name>
    <Directory>Development.directory</Directory>
    <Include>
      <And>
        <Category>Development</Category>
      </And>
      <Filename>emacs.desktop</Filename>
    </Include>
  </Menu> <!-- End Development Tools -->

  <!-- Education -->
  <Menu>
    <Name>Education</Name>
    <Directory>Education.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
        <Not><Category>Science</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Education -->

  <!-- Science -->
  <Menu>
    <Name>Science</Name>
    <Directory>GnomeScience.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
        <Category>Science</Category>
      </And>
    </Include>
  </Menu> <!-- End Science -->

  <!-- Games -->
  <Menu>
    <Name>Games</Name>
    <Directory>Game.directory</Directory>
    <Include>
      <And>
        <Category>Game</Category>
        <Not><Category>ActionGame</Category></Not>
        <Not><Category>AdventureGame</Category></Not>
        <Not><Category>ArcadeGame</Category></Not>
        <Not><Category>BoardGame</Category></Not>
        <Not><Category>BlocksGame</Category></Not>
        <Not><Category>CardGame</Category></Not>
        <Not><Category>KidsGame</Category></Not>
        <Not><Category>LogicGame</Category></Not>
        <Not><Category>Simulation</Category></Not>
        <Not><Category>SportsGame</Category></Not>
        <Not><Category>StrategyGame</Category></Not>
      </And>
    </Include>
    <DefaultLayout inline="true" inline_limit="6" inline_header="false">
      <Merge type="menus"/>
      <Merge type="files"/>
    </DefaultLayout>
    <Menu>
      <Name>Action</Name>
      <Directory>ActionGames.directory</Directory>
      <Include>
        <Category>ActionGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Adventure</Name>
      <Directory>AdventureGames.directory</Directory>
      <Include>
        <Category>AdventureGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Arcade</Name>
      <Directory>ArcadeGames.directory</Directory>
      <Include>
        <Category>ArcadeGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Board</Name>
      <Directory>BoardGames.directory</Directory>
      <Include>
        <Category>BoardGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Blocks</Name>
      <Directory>BlocksGames.directory</Directory>
      <Include>
        <Category>BlocksGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Cards</Name>
      <Directory>CardGames.directory</Directory>
      <Include>
        <Category>CardGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Kids</Name>
      <Directory>KidsGames.directory</Directory>
      <Include>
        <Category>KidsGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Logic</Name>
      <Directory>LogicGames.directory</Directory>
      <Include>
        <Category>LogicGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Role Playing</Name>
      <Directory>RolePlayingGames.directory</Directory>
      <Include>
        <Category>RolePlaying</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Simulation</Name>
      <Directory>SimulationGames.directory</Directory>
      <Include>
        <Category>Simulation</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Sports</Name>
      <Directory>SportsGames.directory</Directory>
      <Include>
        <Category>SportsGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Strategy</Name>
      <Directory>StrategyGames.directory</Directory>
      <Include>
        <Category>StrategyGame</Category>
      </Include>
    </Menu>
  </Menu> <!-- End Games -->

  <!-- Graphics -->
  <Menu>
    <Name>Graphics</Name>
    <Directory>Graphics.directory</Directory>
    <Include>
      <And>
        <Category>Graphics</Category>
      </And>
    </Include>
  </Menu> <!-- End Graphics -->

  <!-- Internet -->
  <Menu>
    <Name>Internet</Name>
    <Directory>Network.directory</Directory>
    <Include>
      <And>
        <Category>Network</Category>
	<Not>
	  <Category>X-GNOME-WebApplication</Category>
	</Not>
      </And>
    </Include>
  </Menu>   <!-- End Internet -->

  <!-- Web Applications -->
  <Menu>
    <Name>Web Applications</Name>
    <Directory>X-GNOME-WebApplications.directory</Directory>
    <Include>
      <And>
	<Category>Network</Category>
	<Category>X-GNOME-WebApplication</Category>
      </And>
    </Include>
  </Menu>

  <!-- Multimedia -->
  <Menu>
    <Name>Multimedia</Name>
    <Directory>AudioVideo.directory</Directory>
    <Include>
      <And>
        <Category>AudioVideo</Category>
      </And>
    </Include>
  </Menu>   <!-- End Multimedia -->

  <!-- Office -->
  <Menu>
    <Name>Office</Name>
    <Directory>Office.directory</Directory>
    <Include>
      <And>
        <Category>Office</Category>
      </And>
    </Include>
  </Menu> <!-- End Office -->

  <!-- System Tools-->
  <Menu>
    <Name>System</Name>
    <Directory>System-Tools.directory</Directory>
    <Include>
      <And>
        <Category>System</Category>
        <Not><Category>Settings</Category></Not>
	<Not><Category>Game</Category></Not>
      </And>
    </Include>
    <Menu>
      <Name>Preferences</Name>
      <Directory>Settings.directory</Directory>
      <Include>
        <And>
          <Category>Settings</Category>
          <Not>
            <Or>
              <Category>System</Category>
              <Category>X-GNOME-Settings-Panel</Category>
            </Or>
          </Not>
        </And>
      </Include>
    </Menu>
    <Menu>
      <Name>Administration</Name>
      <Directory>Settings-System.directory</Directory>
      <Include>
        <And>
          <Category>Settings</Category>
          <Category>System</Category>
          <Not>
            <Category>X-GNOME-Settings-Panel</Category>
          </Not>
        </And>
      </Include>
    </Menu>
  </Menu>   <!-- End System Tools -->

  <!-- Other -->
  <Menu>
    <Name>Other</Name>
    <Directory>X-GNOME-Other.directory</Directory>
    <OnlyUnallocated/>
    <Include>
      <And>
        <Not><Category>Core</Category></Not>
        <Not><Category>Screensaver</Category></Not>
        <Not><Category>X-GNOME-Settings-Panel</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Other -->

   <Layout>
     <Merge type="menus" />
     <Menuname>Other</Menuname>
     <Merge type="files" />
   </Layout>

  <!-- The Debian menu -->
  <Menu>
    <Name>Debian</Name>
    <MergeFile>debian-menu.menu</MergeFile>
    <Directory>Debian.directory</Directory>
  </Menu>

<Include>
  <Filename>ubuntu-software-center.desktop</Filename>
</Include>

<!-- Separator between menus and gnome-app-install -->
<Layout>
  <Merge type="menus"/>
  <Merge type="files"/>
  <Separator/>
  <Filename>ubuntu-software-center.desktop</Filename>
</Layout>

</Menu> <!-- End Applications -->
```

I think using 'alacarte' directly breaks the new GNOME Classic menu but I'm NOT sure by any means :confused:

---

### Post by kansasnoob on 2014-04-10
I'm dropping Trusty from the title of this thread since we know that flashback will continue to be supported.

---

### Post by muktupavels on 2014-04-10
I created two merge proposals...

1) gnome-panel - [https://code.launchpad.net/~albertsmuktupavels/gnome-panel/update-xdg-menu-prefix-environment-variable/+merge/215275](https://code.launchpad.net/~albertsmuktupavels/gnome-panel/update-xdg-menu-prefix-environment-variable/+merge/215275). With this one alacarte will use correct menu file in gnome-flashback-session. You can manually apply this fix:
```
sudo gedit /usr/share/applications/gnome-panel.desktop
```
Replace this line
```
Exec=gnome-panel
```
with this
```
Exec=env XDG_MENU_PREFIX="gnome-flashback-" gnome-panel
```

2) alacarte - [https://code.launchpad.net/~albertsmuktupavels/alacarte/fix-creating-new-menus-and-items/+merge/215284](https://code.launchpad.net/~albertsmuktupavels/alacarte/fix-creating-new-menus-and-items/+merge/215284). This will fix new menu and/or item creation. If you are using x64 I can upload deb package with this fix.

---

### Post by kansasnoob on 2014-04-10
> **albertsmuktupavels said:**
> I created two merge proposals...

1) gnome-panel - [https://code.launchpad.net/~albertsmuktupavels/gnome-panel/update-xdg-menu-prefix-environment-variable/+merge/215275](https://code.launchpad.net/~albertsmuktupavels/gnome-panel/update-xdg-menu-prefix-environment-variable/+merge/215275). With this one alacarte will use correct menu file in gnome-flashback-session. You can manually apply this fix:
```
sudo gedit /usr/share/applications/gnome-panel.desktop
```
Replace this line
```
Exec=gnome-panel
```
with this
```
Exec=env XDG_MENU_PREFIX="gnome-flashback-" gnome-panel
```

2) alacarte - [https://code.launchpad.net/~albertsmuktupavels/alacarte/fix-creating-new-menus-and-items/+merge/215284](https://code.launchpad.net/~albertsmuktupavels/alacarte/fix-creating-new-menus-and-items/+merge/215284). This will fix new menu and/or item creation. If you are using x64 I can upload deb package with this fix.

Hi Alberts, I test both i386 and amd64 so a .deb would be great.

---

### Post by kansasnoob on 2014-04-10
> **albertsmuktupavels said:**
> I created two merge proposals...

1) gnome-panel - [https://code.launchpad.net/~albertsmuktupavels/gnome-panel/update-xdg-menu-prefix-environment-variable/+merge/215275](https://code.launchpad.net/~albertsmuktupavels/gnome-panel/update-xdg-menu-prefix-environment-variable/+merge/215275). With this one alacarte will use correct menu file in gnome-flashback-session. You can manually apply this fix:
```
sudo gedit /usr/share/applications/gnome-panel.desktop
```
Replace this line
```
Exec=gnome-panel
```
with this
```
Exec=env XDG_MENU_PREFIX="gnome-flashback-" gnome-panel
```

2) alacarte - [https://code.launchpad.net/~albertsmuktupavels/alacarte/fix-creating-new-menus-and-items/+merge/215284](https://code.launchpad.net/~albertsmuktupavels/alacarte/fix-creating-new-menus-and-items/+merge/215284). This will fix new menu and/or item creation. If you are using x64 I can upload deb package with this fix.

Part #1 works nicely :D

Will test part #2 when you get it built.

Many thanks.

---

### Post by muktupavels on 2014-04-11
[ATTACH]251927[/ATTACH]

Seems this .deb is for both i386 and amd64 systems.

---

### Post by kansasnoob on 2014-04-11
> **albertsmuktupavels said:**
> [ATTACH]251927[/ATTACH]

Seems this .deb is for both i386 and amd64 systems.

That works fine. I tested it pretty thoroughly - restoring defaults, creating a Sundry Menu item & then creating a new gnome-terminal Item within it. The only thing I was not sure of was where to place an icon for a new menu item but I'm sure some googling would tell me.

---

### Post by muktupavels on 2014-04-11
Alacarte fix should be available now with apt-get.

To set icon you need click on icon (when creating new item and/or editing existing one) and than choose icon file.

---

### Post by kansasnoob on 2014-04-11
> **albertsmuktupavels said:**
> Alacarte fix should be available now with apt-get.

To set icon you need click on icon (when creating new item and/or editing existing one) and than choose icon file.

I see that:

> alacarte (3.10.0-1ubuntu2) trusty; urgency=medium

  * Backport upstream patches to:
    - fix creating new items.
    - fix creating new menus.
    - make the restore button work.
 -- Alberts Muktupavels <alberts.muktupavels@gmail.com>   Thu, 10 Apr 2014 22:28:53 +0300

What package updates apply to part #1?

---

### Post by muktupavels on 2014-04-11
> **kansasnoob said:**
> What package updates apply to part #1?

gnome-panel

---

### Post by Smask on 2014-04-12
> **kansasnoob said:**
> Is that from an Ubuntu GNOME installation, or Ubuntu?

Plain Ubuntu with Flashback

---

### Post by kansasnoob on 2014-04-12
> **Smask said:**
> Plain Ubuntu with Flashback

I see what you mean:

[ATTACH=CONFIG]251985[/ATTACH]

But if I set this back to overlay-auto:

[ATTACH=CONFIG]251984[/ATTACH]

Then I still get the overlay-scrollbars even if change the setting there:

[ATTACH=CONFIG]251986[/ATTACH]

Probably something to do with flashback using unity-settings-daemon instead of gnome-settings-daemon :confused:

---

### Post by kansasnoob on 2014-04-13
> **kansasnoob said:**
> Well it's crunch time again ;)

In order that others can follow what I'm doing I'll start posting a lot of "thinking out loud" stuff here. In this case I have a fresh install of Ubuntu Trusty final Beta and I want to record what happens when I install 'gnome-panel':

```
lance@lance-desktop:~$ sudo apt-get install gnome-panel
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel-data gnome-session gnome-session-flashback
  gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete
  libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0
  metacity notification-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base
  gnome-themes-standard
[B]The following NEW packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel gnome-panel-data gnome-session
  gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf
  indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1
  libpanel-applet-4-0 metacity notification-daemon[/B]
0 upgraded, 20 newly installed, 0 to remove and 117 not upgraded.
Need to get 10.2 MB of archives.
**[COLOR="#FF0000"]After this operation, 50.5 MB of additional disk space will be used.[/COLOR]**

```

Stay tuned :guitar:

Edit #1: First flashback w/metacity login looks good:

[ATTACH=CONFIG]251562[/ATTACH]

Edit #2: Flashback w/compiz is broken in many ways, but my focus is on the metacity session anyway. Someone else will have to deal with the complexities of compiz. Sorry but that's just the way it is :sad:

Edit #3: I know I'm going to want some additional packages and I'm going to list them one by one:

```
lance@lance-desktop:~$ sudo apt-get install dconf-tools
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dconf-editor
[B]The following NEW packages will be installed:
  dconf-editor dconf-tools[/B]
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 113 kB of archives.
**[COLOR="#FF0000"]After this operation, 528 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
[B]The following NEW packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
  gnome-tweak-tool[/B]
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,001 kB of archives.
**[COLOR="#FF0000"]After this operation, 7,561 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install indicator-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following NEW packages will be installed:
  indicator-applet[/B]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.0 kB of archives.
**[COLOR="#FF0000"]After this operation, 1,197 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install shiki-colors-metacity-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following NEW packages will be installed:
  shiki-colors-metacity-theme[/B]
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.0 kB of archives.
**[COLOR="#FF0000"]After this operation, 266 kB of additional disk space will be used.[/COLOR]**

```

```
lance@lance-desktop:~$ sudo apt-get install sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hddtemp libsensors-applet-plugin0
Suggested packages:
  ksensors
[B]The following NEW packages will be installed:
  hddtemp libsensors-applet-plugin0 sensors-applet[/B]
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 159 kB of archives.
**[COLOR="#FF0000"]After this operation, 898 kB of additional disk space will be used.[/COLOR]**

```

I'll probably want to install more but lets see what happens.

Edit #4: Moving the window management buttons to the right has not changed since my OP:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

Edit #5: Applying the Shiki-Colors-Metacity theme is the same as Saucy:

```
gsettings set org.gnome.desktop.wm.preferences theme Shiki-Colors-Metacity
```

Edit #6: Disabling the overlay-scrollbars seems to still work the same:

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

But I need to rinse-n-repeat because I think an additional option has been added?

Edit #7: I disabled the webapps:

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

Edit #8: I used 'gnome-tweak-tool' to set the desktop to display mounted volumes:

[ATTACH=CONFIG]251605[/ATTACH]

And to set the key sequence for killing X:

[ATTACH=CONFIG]251606[/ATTACH]

It can also be used for changing themes:

[ATTACH=CONFIG]251607[/ATTACH]

But I had to use the CLI to restore the missing menu icons:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

The footprint is a bit larger installing 'gnome-panel' in Ubuntu GNOME:

```
lance@lance-desktop:~$ sudo apt-get install gnome-panel
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte geoclue-ubuntu-geoip gir1.2-gconf-2.0 gir1.2-panelapplet-4.0
  gnome-applets gnome-applets-data gnome-media gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session-flashback
  gsettings-ubuntu-schemas gstreamer0.10-gconf indicator-applet-complete
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-qt5-1 libgee2 libgles2-mesa
  libgnome-media-profiles-3.0-0 liblightdm-gobject-1-0 libmetacity-private0a
  libpanel-applet-4-0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libtimezonemap1 liburl-dispatcher1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 metacity metacity-common
  signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  unity-control-center unity-control-center-signon unity-settings-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base click
  lightdm unity-greeter-session-broadcast url-dispatcher
Recommended packages:
  indicator-applet indicator-renderer
The following NEW packages will be installed:
  alacarte geoclue-ubuntu-geoip gir1.2-gconf-2.0 gir1.2-panelapplet-4.0
  gnome-applets gnome-applets-data gnome-media gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session-flashback
  gsettings-ubuntu-schemas gstreamer0.10-gconf indicator-applet-complete
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-qt5-1 libgee2 libgles2-mesa
  libgnome-media-profiles-3.0-0 liblightdm-gobject-1-0 libmetacity-private0a
  libpanel-applet-4-0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libtimezonemap1 liburl-dispatcher1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 metacity metacity-common
  signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  unity-control-center unity-control-center-signon unity-settings-daemon
0 upgraded, 66 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.0 MB of archives.
After this operation, 126 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

And for now I want to use the Ambiance theme so:

```
lance@lance-desktop:~$ sudo apt-get install light-themes
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gtk2-engines-murrine gtk3-engines-unico ubuntu-mono
Suggested packages:
  murrine-themes
The following NEW packages will be installed:
  gtk2-engines-murrine gtk3-engines-unico light-themes ubuntu-mono
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 443 kB of archives.
After this operation, 6,043 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

And a bit more:

```
lance@lance-desktop:~$ sudo apt-get install shiki-colors-metacity-theme dmz-cursor-theme
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dmz-cursor-theme shiki-colors-metacity-theme
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 215 kB of archives.
After this operation, 3,811 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main dmz-cursor-theme all 0.4.4ubuntu1 [193 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/universe shiki-colors-metacity-theme all 4.6-1ubuntu2 [22.0 kB]
Fetched 215 kB in 0s (366 kB/s)                       
Selecting previously unselected package dmz-cursor-theme.
(Reading database ... 185424 files and directories currently installed.)
Preparing to unpack .../dmz-cursor-theme_0.4.4ubuntu1_all.deb ...
Unpacking dmz-cursor-theme (0.4.4ubuntu1) ...
Selecting previously unselected package shiki-colors-metacity-theme.
Preparing to unpack .../shiki-colors-metacity-theme_4.6-1ubuntu2_all.deb ...
Unpacking shiki-colors-metacity-theme (4.6-1ubuntu2) ...
Setting up dmz-cursor-theme (0.4.4ubuntu1) ...
update-alternatives: using /usr/share/icons/DMZ-White/cursor.theme to provide /usr/share/icons/default/index.theme (x-cursor-theme) in auto mode
Setting up shiki-colors-metacity-theme (4.6-1ubuntu2) ...

```

---

### Post by kansasnoob on 2014-04-13
I'm editing my OP so it makes sense moving into 14.10 dev, and also so it's useful to noobs. Therefore I need to lump a few things into simple posts that can be referenced easily and just make sense :)

The footprint of installing 'gnome-panel' in Ubuntu ATM is quite light:

```
lance@lance-desktop:~$ **sudo apt-get install gnome-panel**
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel-data gnome-session gnome-session-flashback
  gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete
  libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0
  metacity notification-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base
  gnome-themes-standard
[B]The following NEW packages will be installed:
  alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets
  gnome-applets-data gnome-control-center gnome-control-center-data
  gnome-media gnome-panel gnome-panel-data gnome-session
  gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf
  indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1
  libpanel-applet-4-0 metacity notification-daemon[/B]
0 upgraded, 20 newly installed, 0 to remove and 117 not upgraded.
Need to get 10.2 MB of archives.
**[COLOR="#FF0000"]After this operation, 50.5 MB of additional disk space will be used.[/COLOR]**

```

The footprint of installing 'gnome-panel' in Ubuntu GNOME is a bit heavier since "flashback" now uses 'unity-settings-daemon' and 'unity-control-center' instead of the GNOME versions of those same packages:

```
lance@lance-desktop:~$ **sudo apt-get install gnome-panel**
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte geoclue-ubuntu-geoip gir1.2-gconf-2.0 gir1.2-panelapplet-4.0
  gnome-applets gnome-applets-data gnome-media gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session-flashback
  gsettings-ubuntu-schemas gstreamer0.10-gconf indicator-applet-complete
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-qt5-1 libgee2 libgles2-mesa
  libgnome-media-profiles-3.0-0 liblightdm-gobject-1-0 libmetacity-private0a
  libpanel-applet-4-0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libtimezonemap1 liburl-dispatcher1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 metacity metacity-common
  signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  unity-control-center unity-control-center-signon unity-settings-daemon
Suggested packages:
  tomboy gnome-netstatus-applet deskbar-applet cpufrequtils desktop-base click
  lightdm unity-greeter-session-broadcast url-dispatcher
Recommended packages:
  indicator-applet indicator-renderer
[B]The following NEW packages will be installed:
  alacarte geoclue-ubuntu-geoip gir1.2-gconf-2.0 gir1.2-panelapplet-4.0
  gnome-applets gnome-applets-data gnome-media gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session-flashback
  gsettings-ubuntu-schemas gstreamer0.10-gconf indicator-applet-complete
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-qt5-1 libgee2 libgles2-mesa
  libgnome-media-profiles-3.0-0 liblightdm-gobject-1-0 libmetacity-private0a
  libpanel-applet-4-0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libtimezonemap1 liburl-dispatcher1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 metacity metacity-common
  signon-keyring-extension signon-plugin-oauth2 signon-ui signond
  unity-control-center unity-control-center-signon unity-settings-daemon[/B]
0 upgraded, 66 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.0 MB of archives.
**[COLOR="#FF0000"]After this operation, 126 MB of additional disk space will be used[/COLOR]**.
```

---

### Post by kansasnoob on 2014-04-13
One of the most troublesome things I've encountered is the inability to backup and restore a total "out-of-box" configuration, or a custom config :mad:

It used to be this easy:

[http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600](http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600)

Now I find myself sometimes having to actually purge entire packages and sometimes even having to reinstall the OS altogether if i mess up :oops:

Any thoughts?

---

### Post by kansasnoob on 2014-04-13
I see the new 'gnome-panel' is in Trusty-proposed so give me a bit to test thoroughly. It'd be easier if the daily images weren't borked ATM.

---

### Post by kansasnoob on 2014-04-14
> **kansasnoob said:**
> One of the most troublesome things I've encountered is the inability to backup and restore a total "out-of-box" configuration, or a custom config :mad:

It used to be this easy:

[http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600](http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600)

Now I find myself sometimes having to actually purge entire packages and sometimes even having to reinstall the OS altogether if i mess up :oops:

Any thoughts?

I gained a tiny bit by renaming additional hidden-dots in Home:

```
lance@lance-desktop:~$ ls -a
.              .config           .gconf_OLD       Pictures
..             .config_OLD       .gphoto          .profile
.adobe         .dbus             .gstreamer-0.10  Public
.bash_history  Desktop           .ICEauthority    purge_flashback
.bash_logout   .dmrc             .local           Templates
.bashrc        Documents         .local_OLD       Videos
.cache         Downloads         .macromedia      .Xauthority
.cache_OLD     examples.desktop  .mozilla         .xsession-errors
.compiz_OLD    .gconf            Music            .xsession-errors.old

```

But that does NOT restore the out-of-box panel configuration so I'm still fiddling ;)

---

### Post by muktupavels on 2014-04-14
You can reset gnome-panel settings to default:
```
dconf reset -f /org/gnome/gnome-panel/
```
Than logout and login or restart pc. Or you can simply restart gnome-panel:
```
XDG_MENU_PREFIX="gnome-flashback-" gnome-panel --replace &
```

---

### Post by kansasnoob on 2014-04-14
> **albertsmuktupavels said:**
> You can reset gnome-panel settings to default:
```
dconf reset -f /org/gnome/gnome-panel/
```
Than logout and login or restart pc. Or you can simply restart gnome-panel:
```
XDG_MENU_PREFIX="gnome-flashback-" gnome-panel --replace &
```

Thank you :D

---

### Post by zika on 2014-04-15
Comming (at last) from 13.10 to 14.04 with full Ricotz and G3 ppas I've lost flashback...
```
The following packages have unmet dependencies. gnome-session-flashback : Depends: unity-settings-daemon but it is not going to be installed
```
```
The following packages have unmet dependencies. unity-settings-daemon : Depends: gnome-settings-daemon-schemas (< 3.10) but 3.12.0.1-0ubuntu1~trusty1 is to be installed
```
Any idea(s) (other than, I presume, purging Ricotz's ppas) how to get {it,them} back...?
Also, while on that subject, Classic is unusable, it just stall at the entrance... In 13.10 last weeks it was the same as vanilla GnomeShell...
So, I'm doomed just to use GS, Unity or (better) awesome, razor, etc... ;)

---

### Post by cariboo on 2014-04-15
Keep the faith zika, we've only got a week and a few days, before the toolchain for the next version is uploaded. :)

---

### Post by ventrical on 2014-04-15
> **kansasnoob said:**
> One of the most troublesome things I've encountered is the inability to backup and restore a total "out-of-box" configuration, or a custom config :mad:

It used to be this easy:

[http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600](http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600)

Now I find myself sometimes having to actually purge entire packages and sometimes even having to reinstall the OS altogether if i mess up :oops:

Any thoughts?


What helped me in a lot of cases is that just after install I would create another aternate user with privlidges. If lighdm  or gdm were still working (and the desktop I was using was borked) I could login to that user and have a pristine config. It's sort of like  a mini back-up system .. but perhaps this may not apply to the case in point now , this far into the cycle.

---

### Post by ventrical on 2014-04-16
> **kansasnoob said:**
> I see the new 'gnome-panel' is in Trusty-proposed so give me a bit to test thoroughly. It'd be easier if the daily images weren't borked ATM.


Just did a fresh install here of yesterdays i386 iso and put gnome-flashback-compiz. Works great! :)

---

### Post by zika on 2014-04-16
> **cariboo907 said:**
> Keep the faith zika, we've only got a week and a few days, before the toolchain for the next version is uploaded. :)I've never even scratched my faith, let alone lost it... ;)
What about „devel“ branch?

---

### Post by cariboo on 2014-04-16
> **zika said:**
> I've never even scratched my faith, let alone lost it... ;)
What about „devel“ branch?

As far as a devel branch is concerned, I wish :)

14.10 should be the start of some pretty amazing development on the desktop, with Mir and Unity 8, for those that prefer the old style Windows type desktop, Xubuntu. Lubuntu and Kubuntu, we should see a more polished desktop environment.

**Note:** Please don't quote me six months from now, as I've been known to be wrong a time or two. :)

---

### Post by kansasnoob on 2014-04-16
> **cariboo907 said:**
> As far as a devel branch is concerned, I wish :)

14.10 should be the start of some pretty amazing development on the desktop, with Mir and Unity 8, for those that prefer the old style Windows type desktop, Xubuntu. Lubuntu and Kubuntu, we should see a more polished desktop environment.

**Note:** Please don't quote me six months from now, as I've been known to be wrong a time or two. :)

It's NOT a matter of being wrong, it's a matter of these darn faulty time machines they're building these days :lolflag:

---

### Post by Hazzabin on 2014-04-16
> **kansasnoob said:**
> It's NOT a matter of being wrong, it's a matter of these darn faulty time machines they're building these days :lolflag:

Most certainly, the older we get the worse the time machines are :guitar:

---

### Post by grumblebum2 on 2014-04-16
> **Hazzabin said:**
> Most certainly, the older we get the worse the time machines are :guitar:
Mine's working fine and I knew you were going to say that. :p

---

### Post by kansasnoob on 2014-04-29
A question has been asked by Jonathan Carter at the mailing list:

[https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00010.html](https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00010.html)

> Hi!

Mate has steadily been making its way into Debian and Ubuntu:
[http://www.omgubuntu.co.uk/2014/01/mate-desktop-ubuntu-1404](http://www.omgubuntu.co.uk/2014/01/mate-desktop-ubuntu-1404)
[https://packages.debian.org/unstable/x11/mate-desktop](https://packages.debian.org/unstable/x11/mate-desktop)

Originally there was a lot of doubt whether that would ever happen, and
I think that it negates the need for Flashback. Also, the upstream Gnome
software (like Nautilus, Gnome Control Center, etc) are diverging faster
and faster and either doesn't fit in or doesn't work well with Flashback
anymore. Not that it's a big surprise, it was going to come at some
point. But I think it's time to rather have a new, minimilistic Mate
session available for some of the usecases that Flashback was good for
and lay Flashback to rest.

Personally I never put in the amount of energy in to this that I
originally hoped to, and I think it might be better to put it to rest
than to drag it out much further.

Any thoughts? Or in particular? Any good reasons to keep Flashback on
life support?

-Jonathan

I already weighed in:

[https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00016.html](https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00016.html)

> Hi Jonathan,

I'd first remind everyone that I'm not a developer, only an end user/tester, and my recent experience is limited to the Ubuntu family.


My first concern is that someone will read this, cherry-pick the list, and declare "flashback" dead before any official decision is made.


At the Ubuntu level we first need to clarify that since Ubuntu and Edubuntu Precise are supported until April 2017, and Trusty until April 2019, that Precise and Trusty flashback will continue to be supported throughout the lifespan of those two releases.


On 04/28/2014 01:41 PM, Jonathan Carter wrote:

    Hi!

    Mate has steadily been making its way into Debian and Ubuntu:
    [http://www.omgubuntu.co.uk/2014/01/mate-desktop-ubuntu-1404](http://www.omgubuntu.co.uk/2014/01/mate-desktop-ubuntu-1404)
    [https://packages.debian.org/unstable/x11/mate-desktop](https://packages.debian.org/unstable/x11/mate-desktop)


Just tried Mate in Ubuntu Utopic which is now installable (and bootable) simply by installing 'mate-session-manager'. The footprint is certainly light enough - 64.2 MB, but also pulls in 'caja' and I suspect that Edubuntu (which offers flashback as an option during installation) would prefer to use whatever file manager is default in Ubuntu whether that be nautilus, nemo, or whatever Ubuntu chooses in the future. I still happen to prefer nautilus.


I should note that the Mate session in Utopic is buggy ATM but that's to be expected this early in a dev cycle. I did not parse packages to see if I was missing any recommends, etc.



    Originally there was a lot of doubt whether that would ever happen, and
    I think that it negates the need for Flashback. Also, the upstream Gnome
    software (like Nautilus, Gnome Control Center, etc) are diverging faster
    and faster and either doesn't fit in or doesn't work well with Flashback
    anymore. Not that it's a big surprise, it was going to come at some
    point. But I think it's time to rather have a new, minimilistic Mate
    session available for some of the usecases that Flashback was good for
    and lay Flashback to rest.


Since flashback in Ubuntu now uses 'unity-settings-daemon' and 'unity-control-center' (at least in some regards) does that make things simpler or more complex? I'm admittedly more than a bit confused in that regard :^/



    Personally I never put in the amount of energy in to this that I
    originally hoped to, and I think it might be better to put it to rest
    than to drag it out much further.

    Any thoughts? Or in particular? Any good reasons to keep Flashback on
    life support?


I personally don't think it should even be considered until Mate changes to GTK+3, presumably in version 1.10, and even then we should approach such a change with great caution - almost certainly waiting until Mate has their full DE working well in Ubuntu at which point Edubuntu may want to consider the change.


A bit off-topic here but if I'd had my druthers, which seldom happens, I'd rather see a flashback w/mutter session as a more easily configurable alternative to GNOME's new classic session ;^)


Lance




Please add a comment to the list if you have an opinion either way.

---

### Post by ventrical on 2014-04-30
> **kansasnoob said:**
> A question has been asked by Jonathan Carter at the mailing list:

[https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00010.html](https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00010.html)



I already weighed in:

[https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00016.html](https://mail.gnome.org/archives/gnome-flashback-list/2014-April/msg00016.html)



Please add a comment to the list if you have an opinion either way.


ATM I am using an install with gnome-flashback (compiz) Utopic and it is running just fine. I do not use it regularly, just mostly for experimentation and minimalist jobs. Ronac used to say "If it ain't broke, don't fix it!"

This may be topical. fvwm-crystal had some big updates as of recent.  It is an older , more vintage DE/WM but it appears it is still maintained from time to time. My opinion is  - take gnome-session and mate one day at a time. Do what can be done, fix it when time permits and patch it when time permits but keep options open - don't drop it completely. Somebody else will pick up the slack. That's how things work around here. :)

Regards..

---

### Post by redman5087 on 2014-04-30
> **albertsmuktupavels said:**
> 1) Are you only one with black panels or there are other users with same problem?
2) Black panels with both session? metacity and compiz.
3) Can you access panel properties? Alt + Right click on panel.

With the Radiance and Ambiance I DON'T have the problem with black panels.
With others themes from gnome-look I DO have the problem with the black panels.

The theme needs to be changed I suppose.

How to change the theme?

In the gtk2 or gtk3 theme?
In the gnome-shell theme?
Or the unity theme?

Thanks for the help.

---

### Post by muktupavels on 2014-04-30
> **redman5087 said:**
> 
How to change the theme?

You need to edit .css files.

> **redman5087 said:**
> 
In the gtk2 or gtk3 theme?
In the gnome-shell theme?
Or the unity theme?

gnome-panel uses gtk3 themes.

You could look at Ambiance theme for example how to style gnome-panel.

In Ambiance theme:
1) gnome-panel related styling are stored in separate file - /usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css
2) gnome-panel.css file is imported in this file - /usr/share/themes/Ambiance/gtk-3.0/gtk-main.css
3) gtk-main.css is imported in this file - /usr/share/themes/Ambiance/gtk-3.0/gtk.css

So if you want edit xTheme to add gnome-panel styling you can add directly styling in gtk.css file - /usr/share/themes/xTheme/gtk-3.0/gtk.css.

But I would suggest to add new file in your theme directory and simply add import line in gtk.css file:
1) create gnome-panel.css in - /usr/share/themes/xTheme/gtk-3.0/
2) add import line '@import url("gnome-panel.css");' at end of file - /usr/share/themes/xTheme/gtk-3.0/gtk.css

Remember that when there will be update for theme you edit your changes will be lost on update. So backup your created files. If you will use separate file for styling than after update you will only need to re-add import line.

---

### Post by redman5087 on 2014-04-30
Thanks

---

### Post by cedric5 on 2014-05-01
hello, 
again, now with 14.04 running these are the issues I have (also with a fresh user!)

- custom keybindings are not possible!!! the gconf ones are ignored, the dconf ones in org.gnome.settings-daemon.plugins.media-keys too!
- the tooltips are not word-warped any more
- login lasts 10+ seconds

---

### Post by kansasnoob on 2014-05-01
Just a friendly reminder :)

Since Trusty (14.04) has been released support questions regarding it or any prior release should be asked here:

[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

Or directly to me here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

### Post by cedric5 on 2014-05-01
thanks! will do so

---

