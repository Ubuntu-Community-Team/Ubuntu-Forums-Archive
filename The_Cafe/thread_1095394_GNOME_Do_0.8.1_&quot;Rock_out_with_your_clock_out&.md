---
title: "GNOME Do 0.8.1 &quot;Rock out with your clock out&quot; Released"
date: 2009-03-13
forum: The Cafe
---

### Post by DBO on 2009-03-13
Hey all, it's that time again.  GNOME Do is proud to announce our latest and greatest version yet, this time with bug fixes!  The 0.8.1 release is primarily a bug fix release with no new major features (save for a clock docklet).

[IMG]http://do.davebsd.com/images/shot.png[/IMG]

This release features
- 38 bug fixes
- 8 new translations
- 2 new plugins (youtube and emesen)

as a well as a massive overhaul of the docky interface.  Docky ended up being the primary focus of this release since it was the source of most of the bugs in 0.8.0, my bad.  Anyhow it has even more polish now and should work better than before.  Here is to hoping!

[[IMG]http://jassmith.files.wordpress.com/2009/03/docky081.png?w=450&h=114[/IMG]]("http://jassmith.files.wordpress.com/2009/03/docky081.png")

More information here: [http://jassmith.wordpress.com/2009/03/13/gnome-do-081-released/](http://jassmith.wordpress.com/2009/03/13/gnome-do-081-released/)

Everyone who gave feedback after the 0.8.0 release was of tremendous help and really helped contribute to 0.8.1 and what I feel is the most polished GNOME Do yet.

Jason "DBO" Smith

---

### Post by Mr. Picklesworth on 2009-03-13
Okay, that's it. You've won me over. The impossible has happened. A dock has replaced my bottom panel.

If this thing used native menus instead of its own strange things the switch could be permanent.

---

### Post by DBO on 2009-03-13
> **Mr. Picklesworth said:**
> Okay, that's it. You've won me over. The impossible has happened. A dock has replaced my bottom panel.

If this thing used native menus instead of its own strange things the switch could be permanent.

I am not really looking into getting into much of a debate over menus, but I think the Docky benifits from doing things its own way.  Native menus are ugly and very limitting for some things we want to do (like animations).

---

### Post by binbash on 2009-03-13
Nice release, i hope it fixes some of my problems

---

### Post by Rokurosv on 2009-03-13
I loved Do but for me Docky is a little sluggish, but it's a great launcher/dock and using it saves a lot of screen size for me

---

### Post by Mohamedzv2 on 2009-03-13
Is there any way to change the interface for docky to look more like the OS X Leopard dock?

---

### Post by DBO on 2009-03-13
> **Mohamedzv2 said:**
> Is there any way to change the interface for docky to look more like the OS X Leopard dock?

Nope =)  We want to keep our own look.  Some day you will be allowed to change the color and theme a little more, but that day is not today.  Trying to get all the fundamentals right first before we do something crazy.

---

### Post by _sAm_ on 2009-03-13
I love the idea behind Gnome DO; how the dock turns into a search/launcher when you want. I also liked how Gnome DO worked(before the dock came), but now it is to sluggish(so I went back to awn). 

Will try it again when I upgrade to next Ubuntu.

---

### Post by kef_kf on 2009-03-13
omg gnome do changed my life thank yousomuch!!11!

seriously tho, i love gnome do. keep up the great work.

---

### Post by damis648 on 2009-03-13
Can we get a download link?

---

### Post by Muffinabus on 2009-03-13
Being the newbish Linuxer that I am, I can't seem to get it to ./configure correctly.  Is it possible someone could give me a set of instructions to get this to work properly?  The specific problem I'm having is that it doesn't seem to recognize that I have these packages installed and I believe I do.

```
checking pkg-config is at least version 0.9.0... yes
checking for LIBDO... configure: error: Package requirements (glib-2.0 gdk-2.0 gdk-x11-2.0 gtk+-2.0) were not met:

No package 'glib-2.0' found
No package 'gdk-2.0' found
No package 'gdk-x11-2.0' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBDO_CFLAGS
and LIBDO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Jackelope on 2009-03-13
Gnome-Do is the number one thing I miss when I have to use Windows...its so much faster than menus. Serious kudos to everyone involved. I look forward to trying the release.

---

### Post by Stan_1936 on 2009-03-13
> **damis648 said:**
> Can we get a download link?

+1

we NEED a download link.

---

### Post by ad_267 on 2009-03-13
I assume the new release will eventually be available through the PPA if you can wait a little while: [https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

Muffinabus: You need the development packages too, the ones with a "-dev" on the end. But installing from the PPA would be a lot easier.

---

### Post by Muffinabus on 2009-03-13
> **ad_267 said:**
> I assume the new release will eventually be available through the PPA if you can wait a little while: [https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

Yeah, that may be what I end up doing.

And for the people looking for the tarball download, I found it here:

[https://edge.launchpad.net/do/0.8/0.8.1](https://edge.launchpad.net/do/0.8/0.8.1)

---

### Post by Sashin on 2009-03-14
If only there was a deb download...

---

### Post by DBO on 2009-03-14
Debs are being worked on as we speak.  It's always something of a challenge since we have to get it over to debian this time to get it synced into ubuntu and then backport to intrepid.  I hope to have debs very very soon.  Sorry for the delay.

---

### Post by cszikszoy on 2009-03-14
Just wanted to add to what DBO already said.  We actually have 3 new plugins, Youtube, Emesene, and RequestTracker.  In the plugins domain, 29 bugs were fixed.

There's more information on what plugins bugs were fixed here: [http://do.davebsd.com/wiki/index.php?title=0.8.1_Release_Notes](http://do.davebsd.com/wiki/index.php?title=0.8.1_Release_Notes)

---

### Post by ad_267 on 2009-03-14
I don't know if this is a good place to ask this or if it's already been answered elsewhere, but are there plans to be able to use docky without compositing?

---

### Post by Mazza558 on 2009-03-14
If you have an Nvidia card, Docky will be sluggish. If you're using the FOSS ATI drivers, it should be blazing fast.

---

### Post by Tibuda on 2009-03-14
> **Mazza558 said:**
> If you have an Nvidia card, Docky will be sluggish. If you're using the FOSS ATI drivers, it should be blazing fast.
I'm using a proprietary Nvidia (177) card and Docky is not sluggish.

---

### Post by smbm on 2009-03-14
I will install as soon as there is an AMD64 package.

---

### Post by kef_kf on 2009-03-14
> **danielrmt said:**
> I'm using a proprietary Nvidia (177) card and Docky is not sluggish.

i can also confirm docky's non-sluggishness with 180.35

---

### Post by mamamia88 on 2009-03-14
i installed the .8 version waiting for update to hit update channel but how do i add launchers?

---

### Post by damis648 on 2009-03-14
Actually Docky was EXTREMELY sluggish with nVidia 177, it would take about a minute to magnify, bogging down the whole system. Upgraded to 180.35, no more problems. :popcorn:

---

### Post by Tibuda on 2009-03-14
> **mamamia88 said:**
> i installed the .8 version waiting for update to hit update channel but how do i add launchers?Launch Do and search for an application. When you find the application you want, click the (+) in Docky lower left corner.

---

### Post by mamamia88 on 2009-03-14
thanks

---

### Post by Yownanymous on 2009-03-14
I do like the idea of a dock, but I thought the title was rather tacky and uncultured. :P

---

### Post by wersdaluv on 2009-03-14
[B]checking for intltool >= 0.35.0... ./configure: line 3876: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.[/B]

How do I fix this? :)

---

### Post by DBO on 2009-03-14
> **Yownanymous said:**
> I do like the idea of a dock, but I thought the title was rather tacky and uncultured. :P

That was exactly the reaction i was hoping for :D

---

### Post by smbm on 2009-03-14
Any ideas when we might have some 64 bit packages DBO?

Cheers for all your hard work, Gnome Do is awesome.

---

### Post by ArtF10 on 2009-03-14
> **Mazza558 said:**
> If you have an Nvidia card, Docky will be sluggish. ...

Looks like I won't be doing the DO.

---

### Post by Polygon on 2009-03-14
the name of the release angers me.

---

### Post by smbm on 2009-03-14
> **Polygon said:**
> the name of the release angers me.

Why is that?

---

### Post by DBO on 2009-03-14
> **ArtF10 said:**
> Looks like I won't be doing the DO.

[https://answers.launchpad.net/do/+faq/324](https://answers.launchpad.net/do/+faq/324)

There is a fix ;)

---

### Post by SpriteSODA on 2009-03-14
I started using GNOME-DO Docky last week and its totaly awesome, completely changed the way my OS works. i tried Cario-Dock and AWN before, but i really didnt like them. Docky is awesome. Although, I wish there were more effects, i.e. I dont really like the zoom effect, AWN icon-hopping effect is nicer :P

---

### Post by DBO on 2009-03-14
> **SpriteSODA said:**
> I started using GNOME-DO Docky last week and its totaly awesome, completely changed the way my OS works. i tried Cario-Dock and AWN before, but i really didnt like them. Docky is awesome. Although, I wish there were more effects, i.e. I dont really like the zoom effect, AWN icon-hopping effect is nicer :P

It is nice to know you think Docky can stand on its own merits without the zoom effect =)

---

### Post by SpriteSODA on 2009-03-14
> **DBO said:**
> It is nice to know you think Docky can stand on its own merits without the zoom effect =)

I'll try the new-and-improved zoom effect once i get home (currently writing from an XP machine Buhh).
One thing that does bother me is the lack of separation between the launchers and the currently running windows you exhibit in the new version - in 0.8 I liked how it was separated - tasks of existing launchers stacked on the launcher icon and non-launcher were put in the right side of the panel. How is it done now? I'd hate to see a new icon pop between my existing launchers :P

---

### Post by Sashin on 2009-03-14
Why is there only an AMD64 deb?

---

### Post by smbm on 2009-03-14
> **Sashin said:**
> Why is there only an AMD64 deb?

Really? Where?

EDIT: Not to worry I've just found it.

[http://launchpad.net/do/0.8/0.8.1/+download/gnome-do_0.8.1-0~jaunty~ppa1_amd64.deb](http://launchpad.net/do/0.8/0.8.1/+download/gnome-do_0.8.1-0~jaunty~ppa1_amd64.deb)

---

### Post by Polygon on 2009-03-14
> **smbm said:**
> Why is that?

because its a pun and its trying to be funny and witty, but it just comes across as annoying and childish to me.

its like "see what i did there! i changed C*** to Clock!"

*shrugs*

---

### Post by smbm on 2009-03-14
> **Polygon said:**
> because its a pun and its trying to be funny and witty, but it just comes across as annoying and childish to me.

its like "see what i did there! i changed C*** to Clock!"

*shrugs*

Fair enough.

---

### Post by ELD on 2009-03-14
Wow way to overreact about a name, i personally find it amusing and just think people need to lighten up...badly.

Nice release, compiling in a moment :)

Also a question for the dev, is it possible in Docky to have it always be under maximised windows without having it hide? I would love that option.

I tried following the wiki on your website to install from the downloaded source and there is no "autogen.sh" ?

---

### Post by pt123 on 2009-03-14
The clock applet is useful, as I currently need to use a Gnome Panel for the time. 
I like who it expands when you click it
[http://jassmith.files.wordpress.com/2009/03/caly081.png](http://jassmith.files.wordpress.com/2009/03/caly081.png)

But is there a way to have the current date stand out more. Like a different colour or a large font, as the bold which is currently used is hard to see. 

Finally when the clock applet is clicked is it possible to display the current date like in gnome panel like "Sunday 15th March" (like how gnome panel currently does).

Maybe I should post this in launchpad
[https://edge.launchpad.net/do](https://edge.launchpad.net/do)

---

### Post by wersdaluv on 2009-03-14
It's here! It's here!

It's now in the PPA. hehe

---

### Post by days_of_ruin on 2009-03-14
> **Polygon said:**
> because its a pun and its trying to be funny and witty, but it just comes across as annoying and childish to me.

its like "see what i did there! i changed C*** to Clock!"

*shrugs*

Well the previous release was called "Rock out with your dock out".
I thought this was just a play off that.
Unless that was meant to be a perv pun too. >.>

---

### Post by ad_267 on 2009-03-15
What happened to adding a top orientation for docky? Is that scheduled for a later release now?

Edit: Nevermind, I found I just have to edit a gconf key to get the top orientation.

---

### Post by Akkifokkusu on 2009-03-15
I'm running Intrepid 64-bit, and I got the update of the plugins package. Now, I can't remember how I installed Gnome Do in the first place, but I think it was from a deb. There was something wrong with the 64-bit package in the repo (or something like that). But I got the plugins from the repo. So, I go looking for the new plugins (YouTube doesn't seem to be there). But I see that there's now two Banshee Plugins (0.9 and 1.0). So I disable 0.9, and click 1.0. But it automatically gets unchecked. So I try to go back to 0.9... but it doesn't exist anymore.

So I thought maybe I would try to get 0.81 and see if it works with that. I compiled it from source, so I guess I can confirm that it works on Intrepid 64-bit, but the Banshee Plugin still doesn't work and I lost all of my setting, too boot. The settings are fine (although the change of where the open windows get put is a bit off-putting). I just kinda want the plugin back. Did the same thing happen for anyone else?

---

### Post by Eviltechie on 2009-03-15
Gnome do is awesome, the animation was a little funky last time though.

---

### Post by ad_267 on 2009-03-15
> **Akkifokkusu said:**
> So I thought maybe I would try to get 0.81 and see if it works with that. I compiled it from source, so I guess I can confirm that it works on Intrepid 64-bit, but the Banshee Plugin still doesn't work and I lost all of my setting, too boot. The settings are fine (although the change of where the open windows get put is a bit off-putting). I just kinda want the plugin back. Did the same thing happen for anyone else?

Yeah the Banshee plugin does the same thing for me too, just unchecks itself. I'm using 32 bit Ubuntu with Gnome-Do from the PPA.

---

### Post by monkeyKata on 2009-03-15
Hello.

I have the first 0.80 docky release installed from the third-party PPA repository, and I'd just like to know if within a few days the update manager should recognize the new release and prompt me to update through this PPA that I still have check-marked.  No new update prompts yet.  Or is it best to uninstall and install this latest version, or can I just somehow check for an update (in Synaptic the upgrade option is still not available)?

Excuse my lack of certain basics - I've been on Linux since the summer but I definitely don't know everything yet.

And +1 to the request for native menus.  I realize you guys want to do your own thing with the menus, but perhaps an option to switch between gnome-Do and native menus wouldn't be bad. (Another edit: what I took to mean "native menus" is options/theme/functions when right-clicking the different icons)

Edit: I really dig this dock by the way, and all the Do functionality even though I still need to explore it.

---

### Post by ad_267 on 2009-03-15
> **monkeyKata said:**
> Hello.

I have the first 0.80 docky release installed from the third-party PPA repository, and I'd just like to know if within a few days the update manager should recognize the new release and prompt me to update through this PPA that I still have check-marked.  No new update prompts yet.  Or is it best to uninstall and install this latest version, or can I just somehow check for an update (in Synaptic the upgrade option is still not available)?

You can go to System - Administration - Update Manager and click on Check to check for new updates. By default Ubuntu will only check for updates about once a day I think.

---

### Post by monkeyKata on 2009-03-15
> **ad_267 said:**
> You can go to System - Administration - Update Manager and click on Check to check for new updates. By default Ubuntu will only check for updates about once a day I think.

Ok that did it.  I was thinking the update manager would have seen it on its own.

Thanks.

---

### Post by mrphd on 2009-03-15
is there an amd64 deb available for intrepid? i can only find one for jaunty... thanks!

EDIT: amd64 intrepid deb is now up @ [https://launchpad.net/do/+download](https://launchpad.net/do/+download)

---

### Post by ELD on 2009-03-15
I've got it now it's in the PPA, no problems so far, i like the new additions, especially being able to empty the trash on right click.

Would be nice if we could change the clock to digital though.

Also a something that needs to be reverted, the clock window option on right click, did you forget about windows that aren't responding, makes things a nightmare.

---

### Post by SpriteSODA on 2009-03-15
BUG REPORT: EMESSENE launcher doesn't stack the running proccesses of the application.

---

### Post by smbm on 2009-03-15
Have you filed this bug in Launchpad?

---

### Post by dazzlindonna on 2009-03-15
Hmmm...update manager acted like it updated gnome-do this morning. I'm uncertain, however, if it really did or not.  "About Do" still shows 0.8.0 and I'm not seeing new functionality.  For example, ELD above mentions being able to right-click trash to empty it, but I don't have that. I also can't find this clock applet either that everyone is talking about.  Update Manager insists there's nothing to update.  I've restarted but I'm still seeing the same.  Confused...

UPDATE: I made the assumption that Update Manager was lying to me and so I went and grabbed the deb file and installed it.  NOW I have 0.8.1 as I should and I see all the new stuff.  Woot!

---

### Post by smartboyathome on 2009-03-15
> **dazzlindonna said:**
> Hmmm...update manager acted like it updated gnome-do this morning. I'm uncertain, however, if it really did or not.  "About Do" still shows 0.8.0 and I'm not seeing new functionality.  For example, ELD above mentions being able to right-click trash to empty it, but I don't have that. I also can't find this clock applet either that everyone is talking about.  Update Manager insists there's nothing to update.  I've restarted but I'm still seeing the same.  Confused...

You need to restart gnome-do for the updates to take affect.

---

### Post by FuturePilot on 2009-03-15
Looks good. Only 2 issues. The banshee plugin seems broken. Someone already filed a bug on this. The other thing is that I don't see the new Youtube plugin anywhere. :?

---

### Post by RaZe42 on 2009-03-15
Some regressions:

- Some programs show wrong icons, didn't on 0.8 (Update manager shows python icon)
- Some programs show wrong name, didn't on 0.8 (Emesene->"Controller.py", Update manager->"Updatemanager.py"

Seems to be some problems with python apps?

Also my carefully crafted Wine-app launcher with a  custom icon now shows the default Wine glass

---

### Post by DBO on 2009-03-15
> **SpriteSODA said:**
> BUG REPORT: EMESSENE launcher doesn't stack the running proccesses of the application.

[https://answers.launchpad.net/do/+faq/416](https://answers.launchpad.net/do/+faq/416)

---

### Post by Akkifokkusu on 2009-03-15
Little update on the Banshee Plugin...

I launched Gnome Do from terminal (there was something about not being able to index Thunderbird, whatever) and then tried enabling the Banshee plugin. It gave me an error that the file already exists... So I deleted it and tried again. Then it gave me the error:

```
Assembly not found: Banshee.CollectionIndexer, Version=1.4.0.0, Culture=neutral, PublicKeyToken=null
WARNING: [Do.Banshee,1.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
```

Only thing I found on a Google search of this error was a mention that it was in beta, so it doesn't have to be able to run (or something like that). But 0.9 ran for me, and now 1.0 (which I assume isn't beta anymore) doesn't.

EDIT: This was after compiling the plugins from source. Also, it did seem to do something with a Youtube plugin, but there still isn't one on the list.

---

### Post by FuturePilot on 2009-03-15
> **Akkifokkusu said:**
> Little update on the Banshee Plugin...

I launched Gnome Do from terminal (there was something about not being able to index Thunderbird, whatever) and then tried enabling the Banshee plugin. It gave me an error that the file already exists... So I deleted it and tried again. Then it gave me the error:

```
Assembly not found: Banshee.CollectionIndexer, Version=1.4.0.0, Culture=neutral, PublicKeyToken=null
WARNING: [Do.Banshee,1.0] Could not load some add-in assemblies: The classes in the module cannot be loaded.
```

Only thing I found on a Google search of this error was a mention that it was in beta, so it doesn't have to be able to run (or something like that). But 0.9 ran for me, and now 1.0 (which I assume isn't beta anymore) doesn't.

EDIT: This was after compiling the plugins from source. Also, it did seem to do something with a Youtube plugin, but there still isn't one on the list.

Here's the bug on the Banshee plugin [https://bugs.launchpad.net/do/+bug/343158]("https://bugs.launchpad.net/do/+bug/343158")

---

### Post by DBO on 2009-03-15
> **RaZe42 said:**
> Some regressions:

- Some programs show wrong icons, didn't on 0.8 (Update manager shows python icon)
- Some programs show wrong name, didn't on 0.8 (Emesene->"Controller.py", Update manager->"Updatemanager.py"

Seems to be some problems with python apps?

Also my carefully crafted Wine-app launcher with a  custom icon now shows the default Wine glass

Yeah we moved to a more robust matching algo, but there are some regressions in it too.  However we now have the power to improve matching for users on the fly.  If you have emesene in your dock and its not matching when you launch it, open ~/.local/share/gnome-do/RemapFile and add a line that says 
```
Controller.py, emesene
```
Then restart GNOME Do, emesene will now matchd

---

### Post by DarkReaper79 on 2009-03-15
This is awesome, I was using AWM and it started to not autohide. I would have to minimize the window, reopen it, then double click on the page, then it would disappear. Gnome do is alot more fluid movement. But now, I have no plug-ins listed? Im going to have to look closer to see what happened.



EDIT: I had a bit of a brain fart, I didnt install the plug-ins](*,):roll: all better now;)

---

### Post by linuxisevolution on 2009-03-15
I have the older version installed,does it come with the dock? Is there a way to just get docky?

---

### Post by DarkReaper79 on 2009-03-15
> **linuxisevolution said:**
> I have the older version installed,does it come with the dock? Is there a way to just get docky?

I think they both come together. Go to the preferences, appearance, then choose docky.

---

### Post by mrphd on 2009-03-15
I found 0.8.0 as solid as a rock. However, 0.8.1 (running on amd64 intrepid) has crashed on me a few times today. i need to try and find out if anything in particular is causing these crashes. 

has anybody else experienced this?

---

### Post by neal.s on 2009-03-15
Can't believe I hadn't heard about this update! I was just complaining about the lack of clock earlier today.

Big fan of Docky. Keep up the good work!

You guys looking for any help?

---

### Post by RaZe42 on 2009-03-16
> **DBO said:**
> Yeah we moved to a more robust matching algo, but there are some regressions in it too.  However we now have the power to improve matching for users on the fly.  If you have emesene in your dock and its not matching when you launch it, open ~/.local/share/gnome-do/RemapFile and add a line that says 
```
Controller.py, emesene
```
Then restart GNOME Do, emesene will now matchd

Ok thanks, will try.

---

### Post by SpriteSODA on 2009-03-16
> **DBO said:**
> Yeah we moved to a more robust matching algo, but there are some regressions in it too.  However we now have the power to improve matching for users on the fly.  If you have emesene in your dock and its not matching when you launch it, open ~/.local/share/gnome-do/RemapFile and add a line that says 
```
Controller.py, emesene
```
Then restart GNOME Do, emesene will now matchd

works like a charm :)

---

### Post by airtonix on 2009-03-16
wow, docky is made of pure win!

very nice work.

Noob question : where do i submit feature requests if i had any?

---

### Post by Tristam Green on 2009-03-16
Amazing.  Great work, jason!

the only thing I see as a slight hitch is that for me at least, checking the "about Do" page results in the context menu still maintaining focus even after i move away from it or open the "about Do" option.

Not really big, not even altogether that annoying, but it might be something to check into.

---

### Post by FraggedLocust on 2009-03-16
Nice. I'll be sure to do an update tonight. I enjoy using shortcut, and especially the twitter plugin. That's put my useless tweets up like 10x ;) Hopefully this might get around certain programs opening another icon on the trash side of the dock instead of just lighting up the icon I put on it?

---

### Post by treesurf on 2009-03-16
Is it possible to run GnomeDo and Docky on Hardy?  I only see the PPA for Intrepid and Jaunty.

---

### Post by FraggedLocust on 2009-03-16
how do i put the Trash bin back on the side with the clock? I updated but it removed most of the icons except for firefox and flock and terminal. The trash bin is missing, so i checked the gconf-editor, and the docky preferences say that show trash is enabled.

it says that the key has no schema, but this wasn't really a problem with the last version when it did it.

And is it just me, or did the Do icon change? I rather liked the plain one. This one has a crazy starburst like thing.

---

### Post by Tibuda on 2009-03-16
> **FraggedLocust said:**
> how do i put the Trash bin back on the side with the clock? I updated but it removed most of the icons except for firefox and flock and terminal. The trash bin is missing, so i checked the gconf-editor, and the docky preferences say that show trash is enabled.

it says that the key has no schema, but this wasn't really a problem with the last version when it did it.

And is it just me, or did the Do icon change? I rather liked the plain one. This one has a crazy starburst like thing.

Maybe they have changed the gconf path. Right-click the Do icon, and click "Show trash".

---

### Post by PC_load_letter on 2009-03-16
Updated to 0.8.1 this morning, now I can NOT remove items from the dock!!!? Usually, I'd right-click and I can remove any icon that I don't want. Am I missing something?

---

### Post by Tibuda on 2009-03-16
> **PC_load_letter said:**
> Updated to 0.8.1 this morning, now I can NOT remove items from the dock!!!? Usually, I'd right-click and I can remove any icon that I don't want. Am I missing something?

Drag and drop the icons outside the dock.

---

### Post by Twitch6000 on 2009-03-16
I have always been a fan of gnome do so this was great.

I have not been to big a fan of docks though >.>.

I mean heck the only docks I ever liked were kiba-dock and cairo dock.

However docky seems to be extra special or something as it runs great and just works. 

I Like docky as much as I like kiba-dock :O.

---

### Post by Islington on 2009-03-16
DBO: no idea if you answered already, but is there any chance that Docky will support Metacity compositor? if not can it please regress to regular Do when compiz is switched off?

---

### Post by Changturkey on 2009-03-16
The Dock looks really nice.

---

### Post by Twitch6000 on 2009-03-16
> **Islington said:**
> DBO: no idea if you answered already, but is there any chance that Docky will support Metacity compositor? if not can it please regress to regular Do when compiz is switched off?

Last time I checked docky works without compiz,but gets sluggish.

---

### Post by mamamia88 on 2009-03-16
is it in repos yet?

---

### Post by dragos240 on 2009-03-16
How do you enable compositing?

---

### Post by Islington on 2009-03-16
> **Twitch6000 said:**
> Last time I checked docky works without compiz,but gets sluggish.

It works at full speed, except it turns the lower half of my desktop(or upper depending on position) black with nothing other than docky.

---

### Post by Islington on 2009-03-16
> **dragos240 said:**
> How do you enable compositing?

appearance preferences>>visual effects>>normal or extra.

---

### Post by dragos240 on 2009-03-16
thanks ;)

---

### Post by dragos240 on 2009-03-16
Uhh... Maybe this is a stupid question but my gnome-do docky keeps crashing X :(. Also how do you customize whats on the docky?

---

### Post by FraggedLocust on 2009-03-16
> **dragos240 said:**
> Uhh... Maybe this is a stupid question but my gnome-do docky keeps crashing X :(. Also how do you customize whats on the docky?

You can use do to search for a program by clicking the do icon and typing what you want (gnometris) and click the small add button on the lower left. Use the up and down arrow keys to scroll through the search results if you only have part of the word typed out. To remove the launcher just drag it off the dock.

---

### Post by Venku7337 on 2009-03-16
is there a way to make it so that the docky does not take up screen space and that it will hide when i am not hovering over it, i remember being able to do it with the last one. other then that i got rid of AWM for this, because this rocks.

---

### Post by Islington on 2009-03-16
> **Venku7337 said:**
> is there a way to make it so that the docky does not take up screen space and that it will hide when i am not hovering over it, i remember being able to do it with the last one. other then that i got rid of AWM for this, because this rocks.

rightclick on the gnome-do icon and select automatically hide ;)

---

### Post by Venku7337 on 2009-03-16
thank you, i love GnomeDO.

---

### Post by ad_267 on 2009-03-17
> **Islington said:**
> DBO: no idea if you answered already, but is there any chance that Docky will support Metacity compositor? if not can it please regress to regular Do when compiz is switched off?

It works perfectly fine for me with Metacity compositing enabled (using nvdia 6600 gt with 180 drivers).

---

### Post by cdwillis on 2009-03-17
I installed this earlier from the PPA and I have to say Docky is awesome. Mad props to the guys behind this.:o

---

### Post by SpriteSODA on 2009-03-17
One serious suggestion I have is that in the right click menu over a stack of windows, there should be an indicator as to on which of them I am right now, because if the name is almost the same its hard to tell without waiting till the full title pops after a few seconds.

---

### Post by PC_load_letter on 2009-03-17
> **danielrmt said:**
> Drag and drop the icons outside the dock.

Man! I didn't think it would be that cool. Gnome-Do just made my day.

---

### Post by treesurf on 2009-03-17
Is it possible to run gnome-do and docky on Hardy?

---

### Post by Islington on 2009-03-17
> **ad_267 said:**
> It works perfectly fine for me with Metacity compositing enabled (using nvdia 6600 gt with 180 drivers).

must be my 177 drivers :(  damn.

---

### Post by ad_267 on 2009-03-18
> **Islington said:**
> must be my 177 drivers :(  damn.

I think it worked when I had the 177 drivers too...
I had to quit gnome-do and enable metacity compositing, then start up gnome-do again and it worked.

---

### Post by jespdj on 2009-03-18
Nice.

[Is there a build for Hardy?](http://ubuntuforums.org/showthread.php?t=1098633)

---

### Post by CK05 on 2009-03-21
Anyone else have arabic or some foreign language in the preferences? I have no idea what's going on. Added repositories from the official site.

---

### Post by Islington on 2009-03-21
> **CK05 said:**
> Anyone else have arabic or some foreign language in the preferences? I have no idea what's going on. Added repositories from the official site.

try these repos. 

> #Gnome Do Testing
deb [http://ppa.launchpad.net/do-testers/ubuntu](http://ppa.launchpad.net/do-testers/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-testers/ubuntu](http://ppa.launchpad.net/do-testers/ubuntu) intrepid main

---

### Post by CK05 on 2009-03-21
Thank you. 

It's still doing it for me, but one option is in English now. :)

---

### Post by pt123 on 2009-03-21
me too I am getting that also

but 
deb [http://ppa.launchpad.net/do-testers/ubuntu](http://ppa.launchpad.net/do-testers/ubuntu) intrepid main
these aren't the official repositories

Also why is it that when I upgrade Gnome-Do always forgets which addons I had selected. Also the popularity of these.

---

### Post by XProgrammer on 2009-03-23
I'm quite amazed with gnome-do. i love it. But, I'm missing GCalculate plugin is not working. its always says, "Google Calculator could not evaluate the expression.".. Any idea how to fix it ?. I tried looking at /.local/share/gnome-do/.. but couldnt do anything there.

---

### Post by graabein on 2009-03-30
I like the 0.8.1 release and Docky aside from the irritating resize problem of the icons. 

When I launch a program icon or just move the cursor relatively fast from Docky and straight up, the icons return to normal size, then get blown up to full size and shrink again. It works smooth just the one time if I move the cursor slowly. 

I'll check the bug reports later if it's not already reported :)

---

### Post by DBO on 2009-03-30
do you think you could try to get a screencap of this so i can see what is going on?

---

### Post by northwestuntu on 2009-03-30
does the 64bit plugins work yet? i have never been able to get them to work:(

---

### Post by graabein on 2009-04-05
> **DBO said:**
> do you think you could try to get a screencap of this so i can see what is going on?

I guess I could try. What tool should I use?

Edit: Been trying with gtk-recordMyDesktop but I can't figure it out. Leaving for a weeks holiday but I'll try to fix it when I get back.

---

### Post by kimason on 2009-04-05
I have been waiting for some time now and wondering when GNOME would finally release something that can be able to fix and repair bug problems. Now that wait is over, I wonder how can we be able to download one?

---

### Post by 1jackjack on 2009-05-23
> **XProgrammer said:**
> I'm quite amazed with gnome-do. i love it. But, I'm missing GCalculate plugin is not working. its always says, "Google Calculator could not evaluate the expression.".. Any idea how to fix it ?. I tried looking at /.local/share/gnome-do/.. but couldnt do anything there.

I heard that the latest version in the development repos had fixed this bug, and it's true (it worked for me, on jaunty anyway). You can get instructions on how to checkout a copy and compile it from source here:
[http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source](http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source)

---

### Post by davbren on 2009-08-07
Hey all, I have an Nvidia card and I've tried the fix to make docky smooth and I gettin no joy its still juddery...

---

