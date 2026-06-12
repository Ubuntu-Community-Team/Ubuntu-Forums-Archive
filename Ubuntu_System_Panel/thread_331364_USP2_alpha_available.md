---
title: "USP2 alpha available"
date: 2007-01-04
forum: Ubuntu System Panel
---

### Post by chanders on 2007-01-04
[B]Disclaimer: Do not install this unless you know what you are doing!
I will not be responsible for any losses incurred using this software.[/B]

USP2 alpha (1.90alpha) is now available for testing.

This release is for persons who are willing to mess with their settings just for the sake of testing.

USPconfig will not work with this release. All configuration will need to be done via Gconf-editor until malac releases the latest USPconfig.

The old 'places' plugin is now the 'shortcuts' plugin and a new 'places' plugin is available.

Some functionality is still being worked on so they is not included (such as icons in the toggle pane, sorry delfick)

Individually setting text colour for each plugin was decided against as there is now a way to apply a specific theme just to USP.

For the rest of you guys, if you run Dapper, dont use 'recent' as **burlap** said. As it is not supported...

Remove any previous versions of USP..

Dont use any oldschool plugins in your plugins list, such as USPterm and USPcomputer..

It looks like some menu stuff is being changed in Feisty so it wont run there (until I figure what changed :wink:)

Please report all findings for this alpha code. **This was programmed under Edgy Eft. **I am unable to test under Dapper.

Chanders


Plugins included are

uspuser
system_management
applications
shortcuts
places
computer
recent

Please run

gconftool-2 --recursive-unset /apps/usp
and empty your ~/.usp/plugins folder before installing

---

### Post by stalker145 on 2007-01-04
> **chanders said:**
> [B]Disclaimer: Do not install this unless you know what you are doing!
I will not be responsible for any losses incurred using this software.[/B]

USP2 alpha (1.90alpha) is now available for testing.

AAARRRGGGHHHH!!

And I'm stuck here at work :evil: 

On Windows ](*,)

---

### Post by Nano Geek on 2007-01-04
It installed fine but when I tried to add it to the panel, it crashed.

Hope you can fix this soon.

---

### Post by chanders on 2007-01-04
> **asjdfwejqrfjcvm msz34rq33 said:**
> It installed fine but when I tried to add it to the panel, it crashed.

Hope you can fix this soon.

Post the output of
```

usp run-in-window
```

---

### Post by d3v1ant_0n3 on 2007-01-04
Looks great so far:D  Great work.

I've attatched 2 screenies -1 with the panel in action, the other highlighting 2 minor problems I can see. The 'system management' button looks very wrong to me- this might be down to the icon theme I'm using. The text next to the user icon overlaps a little too.

But still, GREAT WORK:D

---

### Post by Nano Geek on 2007-01-04
> **chanders said:**
> Post the output of
```

usp run-in-window
```
Here it is:

ME@Ubuntu:~$ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful

Warning! - Icon /usr/share/games/pixmaps/briquolo.svg cannot be loaded!


Warning! - Icon /usr/share/icons/Human/scalable/apps/blender.svg cannot be loaded!

Traceback (most recent call last):
  File "/usr/bin/usp", line 602, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 592, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 387, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 248, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 581, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 336, in Todos
    PlaceCategories = grandchild.parent.name
AttributeError: 'gmenu.Separator' object has no attribute 'parent'

I forgot to mention that I am running Feisty.

---

### Post by Carwood on 2007-01-04
Mm, it crashes when I add it to the panel:

```

lazlo@lazlo-desktop:~$ usp run-in-window
Loading plugin 'places' : sucessful
Loading plugin 'system_management' : sucessful
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'applications' : sucessful
Unable to load USPcomputer plugin :-(
Traceback (most recent call last):
  File "/usr/bin/usp", line 602, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 592, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 387, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 140, in PopulatePlugins
    self.plugins[plugins].icon = MyPlugin.icon
KeyError: 'USPcomputer'

```

Ubuntu Edgy Eft 6.10 AMD64

---

### Post by mikemn84 on 2007-01-04
I got mine to sort of run when i installed it without removing USPv1 but the panel was way larger than the plugins inside it so there was a lot of wasted space and I didnt see a way to change it.  Another problem was that when I set border width to 0 and reloaded USP the border width got reset to 8 for some reason :-k all the other values worked fine...  So I tried deleting the .usp folder from /home and reinstalling because I thought maybe the older version of USP was conflicting with the new.

Now it crashes when I try to add it to the panel as others have said:
```

Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
Loading plugin 'shortcuts' : sucessful
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'places' : sucessful
Unable to load USPterm plugin :-(
Traceback (most recent call last):
  File "/usr/bin/usp", line 602, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 592, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 387, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 140, in PopulatePlugins
    self.plugins[plugins].icon = MyPlugin.icon
KeyError: 'USPterm'

```

Will there be a way to start USP with some plugins already collapsed on startup?  Maybe save the last configuration when the computer shuts down or something.

Im running Edgy with Beryl - thanks for your hard work.

---

### Post by burlap on 2007-01-04
For those still on dapper (for the unlikely event there are still some people using dapper and trying to run aplha software):
USP works, except:
1. Recent plugin - which is obvious (due to changes in edgy not related directly to USP, I guess)
2. Random misplacement of the panel. If I add USP in the middle of the panel, only half is visible. Not a big deal, as this is unusual place to put USP and I use pretty large fonts. 

Anyway - congratulations! I'm looking forward to the stable release. Maybe finally I'll have an incentive to upgrade to Edgy?

---

### Post by chanders on 2007-01-04
> **mikemn84 said:**
> Will there be a way to start USP with some plugins already collapsed on startup? Maybe save the last configuration when the computer shuts down or something.

USP2 already does this ;-)

For the rest of you guys, if you run Dapper, dont use 'recent' as **burlap** said. As it is not supported...

Remove any previous versions of USP..

Dont use any oldschool plugins in your plugins list, such as USPterm and USPcomputer..

It looks like some menu stuff is being changed in Feisty so it wont run there (until I figure what changed ;-))

---

### Post by chanders on 2007-01-04
> **d3v1ant_0n3 said:**
> Looks great so far:D  Great work.

I've attatched 2 screenies -1 with the panel in action, the other highlighting 2 minor problems I can see. The 'system management' button looks very wrong to me- this might be down to the icon theme I'm using. The text next to the user icon overlaps a little too.

But still, GREAT WORK:D

Thanks! Can you try with the default Human theme and see if you still get this problem?

---

### Post by deadlydeathcone on 2007-01-04
> **Carwood said:**
> Mm, it crashes when I add it to the panel

Same here, but the following command cleared it up:
```
gconftool-2 --recursive-unset /apps/usp
```

Thanks for the update Chanders, it's been looking very impressive in the short time I've had to mess around with it.

---

### Post by delfick on 2007-01-04
> **chanders said:**
> USP2 alpha (1.90alpha) is now available for testing.

YAAAAAAAAAAAAAYYYYYYYYY!!!!!!!!!!!! :D


what has it been ?? like 6 months ?? (lol) :D worth the wait, i say :D

at the moment i'm in windows (making something in macromedia flash, and while it runs under wine, it doesn't run well ....) and i was so excited that i instantly clicked on the link and downloaded to my desktop...then i realised i was in windows :P

> Some functionality is still being worked on so they is not included (such as icons in the toggle pane, sorry delfick)

i'm patient :D



THANKYOU CHANDERS :D

---

### Post by d3v1ant_0n3 on 2007-01-04
> **chanders said:**
> Thanks! Can you try with the default Human theme and see if you still get this problem?

Yep, it's the icon theme. Or at least, it works with the following icon themes:

Human, Tango, Tangerine.

I tested all the stick icon themes, and Glass Icons (the only non-stock theme I have). Seems to be Tango based ones it's fine with?

The user text by the picture has fixed itself. I think it may have been because I didn't have a picture set when I first started up USP2. I removed it from the panel and readded it and it now displays the pic and text right (no overlapping).

Hope thats of some help?

I prefer this menu system so much more than SLAB (which I really like, but is so slow!)

---

### Post by chanders on 2007-01-04
^^Cool!! You didnt have to remove the whole thing.

Right click on the applet and choose "Reload plugins" ;-)

---

### Post by hanzomon4 on 2007-01-04
> **deadlydeathcone said:**
> Same here, but the following command cleared it up:
```
gconftool-2 --recursive-unset /apps/usp
```

Thanks for the update Chanders, it's been looking very impressive in the short time I've had to mess around with it.

Yes!! You're the man!!

---

### Post by d3v1ant_0n3 on 2007-01-05
Ok, I was bored, wanted to add some new icon themes, and thought this might help a little...

I went to gnome-look.org, and grabbed all the icon themes from the front page of 'Most Downloaded' Icon Themes section (2 dead links in there). Here's how they fare with my above problem:

AquiGnome- no
DropLine Neu 0.6 Preview - Yes, uses custom icon.
Etiquette- no
Glossy Glass- no, but would look REALLY good in a blue theme on KDE.
Human Azul- Yes, uses stock Tango icon recoloured.
NuoveXT- no
OSX- Yes, tango like icon
Snowish (SVG version)- no
Suede -no
Vista-Inspirat- no, although it shares many icons with NuoveXT, so no suprise.

Hope this has been of some vague help to you. If not, I've got a ton of icon themes:D

---

### Post by delfick on 2007-01-05
well it took me a bit longer to boot back into linux than what i thought was gonna happen...

but anyways....

cool :D

though....

what happened to the "compact system management" ?? i can't seem to find it :(

and can we set the colour of the text in the menu yet.....

and as you can see in the attached screenshot, the side bar is black......and i can't seem to change it....

and are we able to edit what appears in the places plugin ??

and the border doesn't want to be set to 0......

and usp run-in-window gives me this

> iambob@bob-linux:~$ usp run-in-window
Loading plugin 'applications' : sucessful
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'places' : sucessful
Loading plugin 'recent' : sucessful

(as well as a few warning messages of couldn't find icon, but that doesn't matter :D)



once again, thankyou for your work chanders :D

---

### Post by Keeguon on 2007-01-05
Good work but there's a little bug with the application plugin. Indeed, the More Apps button in All Applications view is displaced on different categories...

---

### Post by DBO on 2007-01-05
> **asjdfwejqrfjcvm msz34rq33 said:**
> 

Traceback (most recent call last):
  File "/usr/bin/usp", line 602, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 592, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 387, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 248, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 581, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 336, in Todos
    PlaceCategories = grandchild.parent.name
AttributeError: 'gmenu.Separator' object has no attribute 'parent'

I forgot to mention that I am running Feisty.

This issue is caused by having a separator in your menus (you can put these in with the menu editor).  USP needs to remove these from its list before trying to process, however simply removing the separator from your menu will fix the issue for you.  Good luck,

DBO

---

### Post by DBO on 2007-01-05
ok one more bit here, the applications plugin wont launch some apps, and other apps it will.  Nothing on stdout to hint at why, so I will have to look at it a bit more but I am guessing it has to do with how they are being parsed.  Just a WAG.  Oh yeah, if you add them to favorites it works then.

---

### Post by MichalMach on 2007-01-05
Hi,
How to run/start prefs ?
btw. Great work 

 log : 
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'applications' : sucessful
Loading plugin 'recent' : sucessful

Warning! - Icon /usr/share/gTweakUI/g.png cannot be loaded!


(usp:4963): Bonobo-WARNING **: FIXME: verb 'Prefs' not found, emit exception

(usp:4963): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition

---

### Post by vitae on 2007-01-05
it also works quite nice on gentoo.

the translations are missing. are they included (german post here in the forum) in the final?

---

### Post by DBO on 2007-01-05
prefs isnt working yet, he stated that.  However more on the issue with not launching files.  The issue seems to be that sometimes (havent looked into much yet) ApplicationsData[2] does get a .split.  So the Exec is wrong... Doesnt matter at all if the exec= in the desktop file has no spaces, but if it does have spaces it wont work.  However it does properly split it if the file is in your favorites (a custom .desktop file).  Though the output from ParseDesktopFile is the same, so its a locational thing, I imagine a simple typo.

---

### Post by chanders on 2007-01-05
Hey **DBO**! Long time no see ;-) Thanks for all your input. I will try to bump off the bugs as they come.

> Indeed, the More Apps button in All Applications view is displaced
The 'More apps' button bug is known.

>  what happened to the "compact system management" ?? i can't seem to find it Still in testing ;)

>  and can we set the colour of the text in the menu yet.....This was decided against since all plugin creators would need to include in their programming. However USP can use a specified theme that you can set the default text color. Still in testing.

>  and as you can see in the attached screenshot, the side bar is black......and i can't seem to change it....I cant seem to replicate this :-k

> 
and are we able to edit what appears in the places plugin ??Use the 'shortcuts' plugin instead ;)

>  and the border doesn't want to be set to 0......Fixed!

>  the translations are missingTranslations arn't included yet

```
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
```Fixed!

```
 Warning! - Icon /usr/share/gTweakUI/g.png cannot be loaded!
```This is a problem with gTweakUI

> 
This issue is caused by having a separator in your menus (you can put these in with the menu editor). USP needs to remove these from its list before trying to process, however simply removing the separator from your menu will fix the issue for you.Hopefully Fixed! (will need testing)

---

### Post by Nano Geek on 2007-01-05
> **DBO said:**
> This issue is caused by having a separator in your menus (you can put these in with the menu editor).  USP needs to remove these from its list before trying to process, however simply removing the separator from your menu will fix the issue for you.  Good luck,

DBOThanks DOB that fixed it.
You're da' Man!

---

### Post by MichalMach on 2007-01-05
Hi,

I have a one small question about User space in USP2, as we can see on foto, there is showed a name of My Ubuntu Box, and now my question :) 

How Can i change it to current logged User Name?
I have 3 users, and one name :) in USP .

Ok now we have two photos from two profiles.

---

### Post by chanders on 2007-01-05
> **MichalMach said:**
> Hi,

I have a one small question about User space in USP2, as we can see on foto, there is showed a name of My Ubuntu Box, and now my question :) 

How Can i change it to current logged User Name?
I have 3 users, and one name :) in USP .

Actually it is supposed to show the Login name and not the computer name :-k

---

### Post by groggyboy on 2007-01-05
I've noticed a quirk: when i set the icon size for the applications plugin to something larger than 2, the tops and bottoms of all the icons in the "All Applications" pane are cropped.  USP1's behaviour here made more sense - no matter what size i set the icons, it would only affect the "Favourites" pane.  The other icons stayed at 2.  I've attached a couple pictures of what I mean.  The left one is "favorites", and the right one is "all apps".

Also, is there any way to remove the search box?

Otherwise, I'm quite impressed with your work, chanders!  and thanks for letting us play with USP2!

---

### Post by ~LoKe on 2007-01-05
Removed the older version, did the gconf command to clean the old settings.  Added it to the panel, and when I click on it, the menu opens then closes immediately, after that I can't open it again.  It's not crashing, and, as far as I can tell, there aren't any errors.

> loke@x04d:~$ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Unless that widget has something to do with it.

**EDIT:** Well, it **is** coming up, I just can't see it.  I can still open applications from it.

**EDIT:** Resolved.  I had a stupid opacity setting in Beryl.

---

### Post by delfick on 2007-01-05
cool, thnx chanders :D

can't wait till i can set the text colour :D 

also, can't wait till you can put the shortcuts plugin into the side bar (wink wink nudge nudge :D)

also, upon restart the side bar is no longer black :D

two things i have noticed today...

a) is it possible to change the distance between the side bar and the applications in the application plugin, so there isn't such a large space there on the left of them (as pointed out in the screenshot)

b)clicking outside the usp doesn't seem to make it collapse (not sticky)....i remember this problem with the first usp :D

---

### Post by zekopeko on 2007-01-05
Nice dude! very nice!

just a little usability suggestion: when i type in the search and the apps are getting eliminated it would be great when there is just one left (the one you want) you can hit enter and it will open.

 that way you don't have to move you hand from the keyboard and select it.

---

### Post by deadlydeathcone on 2007-01-05
I found a small bug - when menu elements are minimized into the sidebar and the plugins are reloaded the sidebar disappears and a duplicate icon for each plugin is created.

> **delfick said:**
> also, can't wait till you can put the shortcuts plugin into the side bar (wink wink nudge nudge :D)

That would be awesome! That along with a new terminal plugin would be a thing of beauty.

---

### Post by chanders on 2007-01-05
> **deadlydeathcone said:**
> I found a small bug - when menu elements are minimized into the sidebar and the plugins are reloaded the sidebar disappears and a duplicate icon for each plugin is created
Fixed!

---

### Post by M7S on 2007-01-07
Thanks for this new version, chanders.

I found a bug. Sometimes not all places is shown with when using the plugin places. That's because the MakeAButton call in line 124 in places.py has one attribute to much.  The correct line should be:
```
Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, ButtonIcon, self.iconsize, 48, -1, locationName, [""] )
```

Keep on the good work!

Edit: another possible bug (not sure about this one) shouldn't line 131 in the same file be ```
locationName = ["/"]
``` instead of ```
locationName = "/"
```

Edit2:
Bookmarks with none-english chars like å, ä, ö leaves clutter like %3%a4 in the bookmark's name. I've added the code to places.py to replace the clutter with the correct char for all chars that I know the correct code for. Look at the attached file.

---

### Post by chanders on 2007-01-07
^^ Thanks Guys! I am going to get all of this on SVN so then you all can make the changes..

Keep the updates coming :)

> **zekopeko said:**
> Nice dude! very nice!

just a little usability suggestion: when i type in the search and the apps are getting eliminated it would be great when there is just one left (the one you want) you can hit enter and it will open.

 that way you don't have to move you hand from the keyboard and select it.

Being worked on ;-)

---

### Post by delfick on 2007-01-07
hmmm, i used to be able to move the menu by holding down alt and dragging it. (both in beryl and metacity)........

but now i can't ....

---

### Post by Malac on 2007-01-07
deleted. sorry.

---

### Post by chanders on 2007-01-07
> **delfick said:**
> hmmm, i used to be able to move the menu by holding down alt and dragging it. (both in beryl and metacity)........

but now i can't ....

Try middle click ;)

---

### Post by hanzomon4 on 2007-01-07
Hey can I set certain elements to exist in the sidebar like system management?

---

### Post by ~LoKe on 2007-01-07
I seem to be completely missing the "places" section. o_O

---

### Post by chanders on 2007-01-07
Did you remove all oldschool plugins? how about unset all the old keys?
What does usp run-in-window give?

---

### Post by chanders on 2007-01-07
> **hanzomon4 said:**
> Hey can I set certain elements to exist in the sidebar like system management?

I am currently working on this. You will also be able to add custom launchers to the side bar.

---

### Post by ~LoKe on 2007-01-07
> **chanders said:**
> Did you remove all oldschool plugins? how about unset all the old keys?
What does usp run-in-window give?

I unset the keys, but I likely screwed something up on the way.

> loke@x04d:~$ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
/usr/bin/usp:147: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  ImageBox.add( Image1 )
Loading plugin 'applications' : sucessful
Loading plugin 'recent' : sucessful

And just a fyi, it's "successful". ;)

---

### Post by delfick on 2007-01-08
> **chanders said:**
> Try middle click ;)

no....as in the menu itself, not just the button on the bar :D

---

### Post by hanzomon4 on 2007-01-08
I noticed that usp won't open certain apps. Any body else notice this?

---

### Post by Malac on 2007-01-08
> **hanzomon4 said:**
> I noticed that usp won't open certain apps. Any body else notice this?
See this patch by DBO
[http://www.ubuntuforums.org/showthread.php?t=331889](http://www.ubuntuforums.org/showthread.php?t=331889)

Hope this helps.

---

### Post by hanzomon4 on 2007-01-08
Nope, I made the change same problem...  Looking on the bright-side, this is the only issue I've had with usp...

---

### Post by mjpoetic on 2007-01-08
I don't know if anyone else has noticed, but you can launch those "non-launching" applications from the recent menu as a workaround

---

### Post by Malac on 2007-01-08
> **chanders said:**
> [quote=MichalMach;1971444]Hi,

I have a one small question about User space in USP2, as we can see on foto, there is showed a name of My Ubuntu Box, and now my question :) 

How Can i change it to current logged User Name?
I have 3 users, and one name :) in USP .

Ok now we have two photos from two profiles.

Actually it is supposed to show the Login name and not the computer name :-k[/quote]
Okay this is my bad in uspuser.py three numbers need to be changed:
Line 137:
```
        datelogged = userlist[2].split("-")
```should read:
```
        datelogged = userlist[[SIZE=3]**6**[/SIZE]].split("-")
```Lines 143-145:
```
        # Show User
        self.wTree.get_widget('UserLabel').set_label(userlist[0])
        self.wTree.get_widget('UserBelowLabel').set_label(userlist[0])
```should read:
```
        # Show User
        self.wTree.get_widget('UserLabel').set_label(userlist[[SIZE=3]**4**[/SIZE]])
        self.wTree.get_widget('UserBelowLabel').set_label(userlist[[SIZE=3]**4**[/SIZE]])
```Lines 149-151
```
        # Show User Time Logged On
        self.wTree.get_widget('TimeLabel').set_label("Logon Time : "+userlist[3])
        self.wTree.get_widget('TimeBelowLabel').set_label("Logon Time : "+userlist[3])
```should read:
```
        # Show User Time Logged On
        self.wTree.get_widget('TimeLabel').set_label("Logon Time : "+userlist[[SIZE=3]**7**[/SIZE]])
        self.wTree.get_widget('TimeBelowLabel').set_label("Logon Time : "+userlist[[SIZE=3]**7**[/SIZE]])
```
Turns out this bug has been carried over from the previous version so I assume no-ones been running this on multi-user systems until now.

Hope this helps.

---

### Post by groggyboy on 2007-01-08
Malac: in the bugfix you posted above, the lines were different for me (maybe you've added code that's not in chander's version?).  Just posting where they were for me, in case someone else has noticed it too.
137=123
143-145=129-131
159-151=135-137
```
Line **137** (**123**):
Code:
datelogged = userlist[2].split("-")

should read:
Code:
datelogged = userlist[6].split("-")

Lines **143-145** (**129-131**):
Code:
# Show User
self.wTree.get_widget('UserLabel').set_label(userlist[0])
self.wTree.get_widget('UserBelowLabel').set_label(userlist[0])

should read:
Code:
# Show User
self.wTree.get_widget('UserLabel').set_label(userlist[4])
self.wTree.get_widget('UserBelowLabel').set_label(userlist[4])

Lines **149-151** (**135-137**):
Code:
# Show User
Time Logged On self.wTree.get_widget('TimeLabel').set_label("Logon Time : "+userlist[3])
self.wTree.get_widget('TimeBelowLabel').set_label("Logon Time : "+userlist[3])

should read:
Code:
# Show User Time Logged On
self.wTree.get_widget('TimeLabel').set_label("Logon Time : "+userlist[7])
self.wTree.get_widget('TimeBelowLabel').set_label("Logon Time : "+userlist[7])

```

thanks for making this, guys!

---

### Post by Malac on 2007-01-08
> **groggyboy said:**
> Malac: in the bugfix you posted above, the lines were different for me (maybe you've added code that's not in chander's version?). 
I did indeed add something ;).
Thanks for that, groggyboy.

---

### Post by Malac on 2007-01-09
> **chanders said:**
> 
It looks like some menu stuff is being changed in Feisty so it wont run there (until I figure what changed ;-))
Installed a copy on my feisty test machine today and it works fine apart from the favourite applications doesn't get updated when I right click an app and choose "add to favourites". Other than that all seems fine. Just thought I'd let you know.

---

### Post by chanders on 2007-01-09
Good to know! I will have to look into why this would happen when I get Feisty up and running...

---

### Post by chanders on 2007-01-09
> **delfick said:**
> no....as in the menu itself, not just the button on the bar :D

The menu is no longer movable as it is now of type 'Dock' and not 'Normal' or 'Menu' as the original USP.

---

### Post by mucha on 2007-01-09
Great work!

Something that annoys me is that the text "Control Center" is like 3px to the left :P. Think it was the same in USP1 too. But anyway great work :)

---

### Post by delfick on 2007-01-09
> **chanders said:**
> The menu is no longer movable as it is now of type 'Dock' and not 'Normal' or 'Menu' as the original USP.

damn, i take it that can't be changed on a user-specific basis ??

---

### Post by chanders on 2007-01-09
> **delfick said:**
> damn, i take it that can't be changed on a user-specific basis ??

Open up USP2.glade and change the window type to "normal" and then save 8)

---

### Post by delfick on 2007-01-09
> **chanders said:**
> Open up USP2.glade and change the window type to "normal" and then save 8)

THANKYOU :D:D !!

much better... :D


so why did you change it to Dock ??

---

### Post by chanders on 2007-01-11
**New Alpha available (1.91)**

* USPconfig now packaged with USP
* Fixed the running bugs

Will fix the other bugs as they arise..

---

### Post by delfick on 2007-01-11
> **chanders said:**
> **New Alpha available (1.91)**

* USPconfig now packaged with USP
* Fixed the running bugs

Will fix the other bugs as they arise..

YAY :D

thnx :D

---

### Post by MichalMach on 2007-01-11
Anybody HELP !!!!

michal@michal-desktop:~$ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
/usr/bin/usp:618: GtkWarning: Invalid icon size 0

  main_window.show_all()
/usr/bin/usp:619: GtkWarning: Invalid icon size 0

  gtk.main()
Static User Image Used

(usp:18487): Bonobo-WARNING **: Never got frame, control died - abnormal exit 
condition


--------------------------------
Runing Gnome 2.16.1 on edgy 6.10

---

### Post by chanders on 2007-01-11
^^ First off, are you running Gnome? Have you tried a different theme? What flavor of Ubuntu are you running (Dapper, Feisty)?

---

### Post by PsyberOneZero on 2007-01-11
First off, chanders et al, amazing work,, I've been using USP since 0.3something and using it everyday.  I just started testing 1.91 alpha and I've come across a few thing, not bugs but changes.
See Image:
[[IMG]http://img484.imageshack.us/img484/3438/uspchangesqa1.th.png[/IMG]](http://img484.imageshack.us/my.php?image=uspchangesqa1.png)
Green: Icons are too large, either set the icons to a default size (16/32px) or adjustable through USPconfig
Yellow: Applications don't take up full width and the names get cut off
Blue(s): Make places/bookmarks into a toggle option (90% of the time I use bookmarks, it would be batter to be able to switch between them not scroll
Red: Again Icons to large. Set default sizes (16/32px) or adjustable.

Of all the latest batch of new programs This has probably been the best and most used one I have.

---

### Post by MichalMach on 2007-01-11
OK Im running Edgy 6.10 and Gnome 2.16.1 :)
Yes I Have tried a different theme like Murrine or Human Theme.

I think thats all .

---

### Post by delfick on 2007-01-11
> **PsyberOneZero said:**
> Yellow: Applications don't take up full width and the names get cut off

i totally agree with this problem here :D

(and the others as well, but not so much :p :D)

---

### Post by chanders on 2007-01-11
> **PsyberOneZero said:**
> First off, chanders et al, amazing work,, I've been using USP since 0.3something and using it everyday.  I just started testing 1.91 alpha and I've come across a few thing, not bugs but changes.
See Image:
[[IMG]http://img484.imageshack.us/img484/3438/uspchangesqa1.th.png[/IMG]]("http://img484.imageshack.us/my.php?image=uspchangesqa1.png")
Green: Icons are too large, either set the icons to a default size (16/32px) or adjustable through USPconfig
Yellow: Applications don't take up full width and the names get cut off
Blue(s): Make places/bookmarks into a toggle option (90% of the time I use bookmarks, it would be batter to be able to switch between them not scroll
Red: Again Icons to large. Set default sizes (16/32px) or adjustable.

Of all the latest batch of new programs This has probably been the best and most used one I have.

Excellent suggestions. However, I am baffled as to why the icons look so large. I don't seem to have that problem but I will definitely look into it. In your recent plugin you can clearly see two icon sizes :-k but the code says otherwise. This will be put high on the list of things to solve (care to give this a shot Malac?). It shouldnt be to difficult to track down as the icon drawing is done by a separate routine.

Application spacing will be fixed. And I really like the idea for the tabs between places and bookmarks. Look out for it in the near future ;-)

---

### Post by deadlydeathcone on 2007-01-11
> **MichalMach said:**
> OK Im running Edgy 6.10 and Gnome 2.16.1 :)
Yes I Have tried a different theme like Murrine or Human Theme.

I think thats all .

I'm having the same problem, and it seems it's because all of usp's gconf settings that are integers default to 0 because of a bug. It's able to read them okay, so you can set them with uspconfig or the gconf editor as a fix.

---

### Post by chanders on 2007-01-11
Well spotted! I will have this solved quickly ;-)

---

### Post by shiversc on 2007-01-12
soory, but how can i get the places like the picture from PsyberOneZero?

---

### Post by Strash on 2007-01-12
Thanks for this alpha preview !

With this new version I have the same problem than with the old one : When I clic on the Menu button USP displays just 5 pixels too low. I can set the usp_offset value to -5 to solve the problem but with uspconfig this value is forbidden... so I have to use gconf-editor to set it. Does the creator of uspconfig can change the range of this option ?

Thanks

---

### Post by Malac on 2007-01-12
> **Strash said:**
> Thanks for this alpha preview !

With this new version I have the same problem than with the old one : When I clic on the Menu button USP displays just 5 pixels too low. I can set the usp_offset value to -5 to solve the problem but with uspconfig this value is forbidden... so I have to use gconf-editor to set it. Does the creator of uspconfig can change the range of this option ?

Thanks
I didn't realise it needed to have negative values, #-o
I'll get on it straight away. :)

---

### Post by chanders on 2007-01-12
@ PsyberOneZero

I tried to track down the space issue in the 'Applications' plugin but there seems to be something wrong with your plugin. See the attached screenshot of my USP 1.91Alpha, you can clearly see that the text should be left aligned but in your screenshot it's centered.

Can you double check to make sure that you removed all the old plugins / gconf keys etc? I still cant figure why it would do that though..

[IMG]http://img235.imageshack.us/img235/3231/screenshot3ec0.jpg[/IMG]

---

### Post by mjpoetic on 2007-01-12
First of all, great app (even if I am the 9 millionth person to say it!).  I was wondering if with the alpha preview there isn't a way to make the text smaller in the "Applications" section.  I tried using the uspconfig app and gconf-editor to set the text size a bit smaller for the subtext (you know, the text underneath the main text ;)) but no dice.:-k

---

### Post by mrjohnston on 2007-01-12
I am running a pretty standard config here, (32-bit, gneric kernel, etc)  with no major modifications to anything.

My issue is the stuff under the menu sections (ie, application, recent, etc.) are just a blank grey.  I can make them hide, etc fine, but no data shows up.  I tried killing X and gnome-panel and reloading plugins.  USP .41 works fine, everything is there, but I can't get any applications or anything to show up with the new alpha.

Anyone know a solution or experience this?  Any ideas what could cause this?

---

### Post by chanders on 2007-01-12
> **mjpoetic said:**
> First of all, great app (even if I am the 9 millionth person to say it!).  I was wondering if with the alpha preview there isn't a way to make the text smaller in the "Applications" section.  I tried using the uspconfig app and gconf-editor to set the text size a bit smaller for the subtext (you know, the text underneath the main text ;)) but no dice.:-k

Now available in the next release ;-)

@ mjohnson - I have no idea why this would happen :-k. Anyone have any ideas? Or similar problems?

---

### Post by ~LoKe on 2007-01-12
I've having all the same problems.  Empty menus, centered applications, text-size not changing.

No real complaints from me because I still love it much more than the old one, but just thought I'd say it.

---

### Post by chanders on 2007-01-12
Ok well the text size is not configurable till the next release :-) but can you post up a pic to show the empty menus?

---

### Post by PsyberOneZero on 2007-01-12
> **chanders said:**
> @ PsyberOneZero

I tried to track down the space issue in the 'Applications' plugin but there seems to be something wrong with your plugin. See the attached screenshot of my USP 1.91Alpha, you can clearly see that the text should be left aligned but in your screenshot it's centered.

Can you double check to make sure that you removed all the old plugins / gconf keys etc? I still cant figure why it would do that though..


It's wierd USP isn't the only program that's centering text, I'm having the same issue with rhythmbox.  I did reset the gconf settings and removed my old plugins in my home dir but there were some of the older plugins in usr/lib/...  How much of that can I remove but still keep my customizations?  Once I get back to my linux machine I'll try this out (also changing my theme may fix centering)

---

### Post by Fluffy, the jolly sheep on 2007-01-12
usp 2 is shaping up great, thanks

Two problems though:
* since 1.91, I can't hide the toggle pane
* I got desktop as home dir set for nautilus, but home folder and desktop get shown both in places

---

### Post by mrjohnston on 2007-01-12
I attached a pic, sorry its the whole desktop but I only have about 5 minutes before I have to leave.  I hope it helps.  I will try and run through some more stuff and any ideas anyone has when I get back tonight.

Thanks!

---

### Post by Malac on 2007-01-12
> **PsyberOneZero said:**
> It's wierd USP isn't the only program that's centering text, I'm having the same issue with rhythmbox.  I did reset the gconf settings and removed my old plugins in my home dir but there were some of the older plugins in usr/lib/...  How much of that can I remove but still keep my customizations?  Once I get back to my linux machine I'll try this out (also changing my theme may fix centering)
It appears the centred text may be a theme issue with GTK.
@ mjohnson et al with blank menus I tried this on a test system and got the same results. This can happen if you didn't uninstall the previous version of usp (0.33 to 0.41) at all (or it didn't get wiped completely) installing the new version over the top as it were.
Try Synaptic and mark for complete removal then manually check that the following folders have been completely removed:
/usr/lib/python2.4/site-packages/usp
/home/[COLOR=DimGray]*<yourusername>*[/COLOR]/.usp/plugins
/usr/share/usp/

and file:
/usr/lib/bonobo/servers/usp.server

Then re-install the 1.91 deb.
Your settings should be safe as they are in .gconf/apps/usp

Try that and see if that works, then run ```
usp run-in-window
``` from terminal whilst usp is not on the panel if it doesn't and post the output.

---

### Post by hanzomon4 on 2007-01-12
I just reinstalled edgy and now have a blank usp too. 
I did what you suggested above but it's still blank,  here's the output:```
 usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
/usr/bin/usp:618: GtkWarning: Invalid icon size 0

  main_window.show_all()
/usr/bin/usp:619: GtkWarning: Invalid icon size 0

  gtk.main()
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 127, in showuser
    self.anim=gtk.gdk.PixbufAnimation(facepic)
gobject.GError: Failed to open file '/home/hanzomon4/.face': No such file or directory



```
EDIT: I just checked my .usp and I can't find any of the plugins. I tried installing the old one and then reinstalling the new one but that didn't give me anything

---

### Post by deadlydeathcone on 2007-01-12
> **chanders said:**
> Well spotted! I will have this solved quickly ;-)

Thanks!

[QUOTE=hanzomon4]I just reinstalled edgy and now have a blank usp too.
I did what you suggested above but it's still blank, here's the output:[/QUOTE]

You have to set the height value of each plugin manually. Check about two pages back in this thread for details.

---

### Post by mrjohnston on 2007-01-12
I just want to second my output is the exact same as hanzomon's when I ran usp run-in-window.  I also still have the menu empty problem even after a cimplete uninstall and deleting the files/directories you listed before installing 1.91.

Thanks for your time and effort with this.

---

### Post by chanders on 2007-01-13
_**Temporary Fix for Blank Plugins**_

Ok. I think I have tracked the problem down. This occurred when I tried to get the border to 0px as requested by Delfick. So as of now it will be reverted, as that is better than blank plugins!! I have fixed it in the next alpha which I will try to release today.

In the interim you need to manually set all the integer values to some positive value (my guess is they are all zero). The main settings that need to change are **width** and **height** and **icon size** (must be 1<= iconsize <=4) for the main app and the plugins.

I will get right on it..

---

### Post by groggyboy on 2007-01-13
has anyone else noticed that with the latest release, certain options in gconf/uspconfig won't do anything?  two i've noticed: the option to hide the side pane does nothing (it stays visible regardless of what I have it set to) and the option to adjust the icon size in the applications pane does nothing as well.

I also had the problem everyone else has been having with a blank menu after installing the update.  it was fine after i reentered everything.

good job on this, chanders and malac!  i like it alot!

---

### Post by ~LoKe on 2007-01-13
> **groggyboy said:**
> has anyone else noticed that with the latest release, certain options in gconf/uspconfig won't do anything?  two i've noticed: the option to hide the side pane does nothing (it stays visible regardless of what I have it set to) and the option to adjust the icon size in the applications pane does nothing as well.

I also had the problem everyone else has been having with a blank menu after installing the update.  it was fine after i reentered everything.

good job on this, chanders and malac!  i like it alot!

Pretty sure he mentioned that gconf keys aren't working yet, which makes sense to me considering we have uspconfig.

---

### Post by sterlingspork on 2007-01-13
I just upgraded from Edgy to Feisty and all of the text in USP is centered now.  Maybe it is the new GTK?

---

### Post by delfick on 2007-01-13
> **chanders said:**
> This occurred when I tried to get the border to 0px as requested by Delfick. 


....sry people :D :P........

---

### Post by groggyboy on 2007-01-13
> **~LoKe said:**
> Pretty sure he mentioned that gconf keys aren't working yet, which makes sense to me considering we have uspconfig.

unfortunately, changing the settings in uspconfig doesn't do anything either...

way i understand it, uspconfig is just a gui frontend for the gconf settings anyways.

---

### Post by Malac on 2007-01-14
> **groggyboy said:**
> way i understand it, uspconfig is just a gui frontend for the gconf settings anyways.
This is correct.
At the moment the icon_size in applications and the font stuff are not implemented, even though the settings are in uspconfig, sorry but this is alpha software. :)

The Side Pane hiding, however, works for me on all my test machines (Dapper/Edgy/Feisty). It won't hide if you have _any_ plugins minimized to it.

Hope this helps.

---

### Post by Fluffy, the jolly sheep on 2007-01-14
> **Malac said:**
> This is correct.
The Side Pane hiding, however, works for me on all my test machines (Dapper/Edgy/Feisty). It won't hide if you have _any_ plugins minimized to it.


Changing the setting to hide the side pane has no direct effect for me. It's only hidden after toggling a pane on and off. After reloading the plugins, the side pane is there again and I have to toggle a pane on and off again to make it disappear.
Also, I can't seem to send the user pane to the side pane, it seems to be always restricted.

---

### Post by Malac on 2007-01-14
> **Fluffy, the jolly sheep said:**
> Changing the setting to hide the side pane has no direct effect for me. It's only hidden after toggling a pane on and off. After reloading the plugins, the side pane is there again and I have to toggle a pane on and off again to make it disappear.
Also, I can't seem to send the user pane to the side pane, it seems to be always restricted.
Chanders or I will look into the side pane issue, I have only just noticed that this is happening on mine now, strange.
At the moment the user plugin can't be sent to the side pane. On the list. :)

---

### Post by Malac on 2007-01-14
Okay the fix for the sidepane issue is to edit /usr/bin/usp
and change the function SetupUSPBorder to:
```
    def SetupUSPBorder( self, *args, **kargs ):
        self.wTree.get_widget( "window1" ).modify_bg( gtk.STATE_NORMAL, gtk.gdk.color_parse( self.custombordercolor ) )
        self.wTree.get_widget( "border" ).set_padding( self.borderwidth, self.borderwidth, self.borderwidth, self.borderwidth )
        self.SetPaneColors( [self.wTree.get_widget( "sidepane" )] )
        self.sidepanevisible = SetGconf( self.client, "bool", "/apps/usp/show_side_pane", False )
        self.pinmenu = SetGconf( self.client, "bool", "/apps/usp/pin_menu", False )

        if self.pinmenu == False:
            self.wTree.get_widget( "pin_button" ).set_active(False)
        else:
            self.wTree.get_widget( "pin_button" ).set_active(True)

        if len(self.wTree.get_widget( "vbox26" ).get_children()) == 0:
            if self.sidepanevisible == False and self.pinmenu == False:
                self.wTree.get_widget( "sidepane" ).hide()
            else:
                self.wTree.get_widget( "sidepane" ).show()
            

```I'll let chanders know.

---

### Post by DerSkw on 2007-01-14
Hi there,
is it possible to use usp with a .desktop file?

i use kiba-dock (osx like dock-app) and i want to start/open usp by klicking on an dock-item

btw: usp is a really great app :D
is there a date for a beta release or 2nd alpha?

---

### Post by groggyboy on 2007-01-14
malac, thanks for the fix!  the side pane works properly now.

i really enjoy this product.  keep it up.

---

### Post by delfick on 2007-01-14
> **DerSkw said:**
> Hi there,
is it possible to use usp with a .desktop file?

i use kiba-dock (osx like dock-app) and i want to start/open usp by klicking on an dock-item

i might use kiba-dock if that happens :D

especially when this becomes usable [http://forum.beryl-project.org/viewtopic.php?f=38&t=1999](http://forum.beryl-project.org/viewtopic.php?f=38&t=1999)

---

### Post by Malac on 2007-01-15
> **groggyboy said:**
> malac, thanks for the fix!  the side pane works properly now.

i really enjoy this product.  keep it up.
You're Most Welcome.

---

### Post by Petro on 2007-01-18
after playing for awhile with usp 1.91 it stopped showing things and this is what i get from:usp run-in-window

Loading plugin 'uspuser' : sucessful
Loading plugin 'places' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
Traceback (most recent call last):
  File "/usr/bin/usp", line 616, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 606, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 398, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 261, in PopulatePlugins
    self.HidePlugin( self.plugins[plugin].container, self.plugins[plugin].icon, self.plugins[plugin].heading, self.plugins[plugin])
AttributeError: pluginclass instance has no attribute 'container'

oh and by things i mean it wont even wont show the panel button anymore even if i remove it from synaptic and do reinstall
:edit: and now even tried deleting /usr/bin/usp file and after reinstall i got the exact same error

---

### Post by Malac on 2007-01-18
> **Petro said:**
> after playing for awhile with usp 1.91 it stopped showing things and this is what i get from:usp run-in-window

Loading plugin 'uspuser' : sucessful
Loading plugin 'places' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
Traceback (most recent call last):
  File "/usr/bin/usp", line 616, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 606, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 398, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 261, in PopulatePlugins
    self.HidePlugin( self.plugins[plugin].container, self.plugins[plugin].icon, self.plugins[plugin].heading, self.plugins[plugin])
AttributeError: pluginclass instance has no attribute 'container'

oh and by things i mean it wont even wont show the panel button anymore even if i remove it from synaptic and do reinstall
:edit: and now even tried deleting /usr/bin/usp file and after reinstall i got the exact same error
Can you list what the next plugin in your plugin_list is after applications. As it seems to be falling over there.

If it is one of the standard plugins, you could try deleting the .py file for that plugin from /usr/lib/python2.4/site-packages/usp/plugins or ~/.usp/plugins if it is in there.
Then right-click on the .deb file and choose Archive Manager and then open data.tar.gz from there, drill all the way down to /./usr/lib/python2.4/site-packages/usp/plugins/ and extract that file only to /usr/lib/python2.4/site-packages/usp/plugins/
This should just give you the one from a fresh install.

And this may sound obvious but I've done it myself. Just check that if you inserted a "newpane" tag it is spelt correctly and is not "Newpane" or something similar.
Hope this helps.

---

### Post by Petro on 2007-01-18
there should not be any plugins after applications but if there is its supposed to be newpane... but where can i look at this plugins_list ?

---

### Post by Malac on 2007-01-18
> **Petro said:**
> there should not be any plugins after applications but if there is its supposed to be newpane... but where can i look at this plugins_list ?
From a command line run :```
uspconfig
```
The plugins list should be on the right of the Main tab.
Or if the fault is effecting uspconfig too.
Run :```
gconf-editor
``` and navigate to /app/usp in the left pane then double click the "plugins_list" value in the right pane.
You can then add/edit/remove the entries.

Hope this helps.

---

### Post by Petro on 2007-01-18
all the computer needed was a good old reboot damn it :D so now i got like 10 usp 19.1's on my panel :D thanks anyway :) i love usp ^^

but one more thing... how am i able to remove the left little panel cause the Hide Side Pane doesnt seem todo it ? :>

---

### Post by Malac on 2007-01-18
> **Petro said:**
> but one more thing... how am i able to remove the left little panel cause the Hide Side Pane doesnt seem todo it ? :>
This is a known bug which has been fixed in the latest svn but for a quick fix, see page 10 post #96 of this thread.

---

### Post by delfick on 2007-01-20
can it be made so that everytime you open the menu, the applications plugin automatically opens up the "favourties" part please ??

because when it goes into "all applications"  "mode" the menu is wider than my screen and so if it opens up wider, it moves to the left side so that all that is visible is a small portion of the right side of the menu (see attached screenshot)

because i have to manually set the panel as type window (seeing as everytime i update svn the files will be overwritten (am i correct in saying that ??), resetting it to window everytime would get irritating after a while :P (as type window, i can use alt and drag the menu)....

thnx :D


btw, how's it going with the compact system management ??? :D

---

### Post by chanders on 2007-01-20
Compact system management is done! Actually it's not called compact system management, you can add whatever buttons you like to the sidepane, as long as they have .desktop files (tey are easy to make in case there isnt any  ;-))

I will add the option to have the applications reset to favourites everytime it is closed, and yes you will have to always change the window type ;-)

Lots of bugfixes coming up in the next commit (a day or two)

---

### Post by delfick on 2007-01-20
> **chanders said:**
> Compact system management is done! Actually it's not called compact system management, you can add whatever buttons you like to the sidepane, as long as they have .desktop files (tey are easy to make in case there isnt any  ;-))

YAY!!!!

so how do i activate it ?? :D

> I will add the option to have the applications reset to favourites everytime it is closed, 

Thankyou :D

> and yes you will have to always change the window type ;-)

damn....o well....

> Lots of bugfixes coming up in the next commit (a day or two)

awsome :D

---

### Post by compwiz18 on 2007-01-22
A fabulous flop.  The first version is great, so I thought I'd try the second.

First time: failed to fine the .face icon in my home directory.

Second time: after the first failure, hacked the source so that it wouldn't look for that file, and the panel has nothing in it, with the exception of the clickable titles.

Sorry if this has already been reported, I didn't read the entire thread.

Other info: amd64, Edgy, clean install from a server base, with GNOME, installed from deb in first post.

Just so you know, I just installed Ubuntu yesterday, so it is a fresh install (I've been using it for about a year, so I'm not new to this...)

```

**Attempt 1:**
adam@adam:~$ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
/usr/bin/usp:618: GtkWarning: Invalid icon size 0

  main_window.show_all()
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 127, in showuser
    self.anim=gtk.gdk.PixbufAnimation(facepic)
gobject.GError: Failed to open file '/home/adam/.face': No such file or directory
/usr/bin/usp:619: GtkWarning: Invalid icon size 0

  gtk.main()
Traceback (most recent call last):
  File "/usr/bin/usp", line 619, in ?
    gtk.main()
KeyboardInterrupt
adam@adam:~$ 

**Attempt 2:**

adam@adam:~$ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
/usr/bin/usp:618: GtkWarning: Invalid icon size 0

  main_window.show_all()
/usr/bin/usp:619: GtkWarning: Invalid icon size 0

  gtk.main()
Traceback (most recent call last):
  File "/usr/bin/usp", line 619, in ?
    gtk.main()
KeyboardInterrupt
adam@adam:~$ 


```

---

### Post by chanders on 2007-01-22
> **compwiz18 said:**
> A fabulous flop
Not a very nice thing to say..

> Sorry if this has already been reported, I didn't read the entire thread.
Actually if you did read the posts you would have seen that there are solutions to your problem.

For now try to set icon sizes to larger than zero (1-4) and set the width and height to some non-zero value (try 150 and 150 for starters)..


I will be commiting the updates today.
Chanders

---

### Post by compwiz18 on 2007-01-22
AWESOME!

I conquered my lazyness and went back and found the answers.  It is now the most awesomest panel.

Thanks a lot!

---

### Post by chanders on 2007-01-24
Before you guys start asking questions, it seems after updating Beryl to SVN3094 from Treveno, USP no longer reacts to the lose focus event. 

I am not sure what changed and if it will change back but this is a big dent as USP is of type DOCK and I need to have it this way to prevent it from being under the panel, and unless the events are honored for type DOCK we will have some problems... 

Any beryl devs can give some insight? Delfick? Can you talk to your friends? :D I know you are seen in those high circles..

---

### Post by delfick on 2007-01-24
> **chanders said:**
>  I know you are seen in those high circles..

i am ?? :D...

i'll update svn here and see if the actual svn has the problem.... (updating now, to svn revision 3105)

(but first, how do you reproduce the problem ??)

---

### Post by delfick on 2007-01-24
k then, i've updated to beryl svn 3105 and i've got latest usp svn.....

i take it when you say this
> USP no longer reacts to the lose focus event. 

you mean that the usp doesn't close when you click outside or open an app from within the usp..... well

when i click on one of the buttons in the usp to open an app, the usp closes.....
when i click outside the usp, it closes.....

the only time the usp doesn't close apon losing focus to another app, or whatever, is when i open anything from the terminal plugin in the usp, but that's been there for a long time (i'm a bit lazy when it comes to posting bugs sometimes, i should probably work on that :P)....

o ye, and the panel should still be of type dock for me (as in i haven't changed it back to window again :D)

---

### Post by Petro on 2007-01-25
> **delfick said:**
> k then, i've updated to beryl svn 3105 and i've got latest usp svn.....

i take it when you say this


you mean that the usp doesn't close when you click outside or open an app from within the usp..... well

when i click on one of the buttons in the usp to open an app, the usp closes.....
when i click outside the usp, it closes.....

the only time the usp doesn't close apon losing focus to another app, or whatever, is when i open anything from the terminal plugin in the usp, but that's been there for a long time (i'm a bit lazy when it comes to posting bugs sometimes, i should probably work on that :P)....

o ye, and the panel should still be of type dock for me (as in i haven't changed it back to window again :D)

i got the focus issue now with the latest beryl :/ i was just wondering what did i do to deserve this and now i know.

---

### Post by chanders on 2007-01-25
> **delfick said:**
> k then, i've updated to beryl svn 3105 and i've got latest usp svn.....

i take it when you say this


you mean that the usp doesn't close when you click outside or open an app from within the usp..... well

when i click on one of the buttons in the usp to open an app, the usp closes.....
when i click outside the usp, it closes.....

the only time the usp doesn't close apon losing focus to another app, or whatever, is when i open anything from the terminal plugin in the usp, but that's been there for a long time (i'm a bit lazy when it comes to posting bugs sometimes, i should probably work on that :P)....

o ye, and the panel should still be of type dock for me (as in i haven't changed it back to window again :D)

Ok well Treveno hasn't updated his repository so I am still at 3094. But it seems to be fixed in 3105 (Tried and tested Delfick method ;-))

When the repository is updated I'll test it also..

---

### Post by delfick on 2007-01-25
> **chanders said:**
>  But it seems to be fixed in 3105 (Tried and tested Delfick method ;-))


cool :D

---

### Post by chanders on 2007-01-26
> **delfick said:**
> YAY!!!!

so how do i activate it ?? :D

In compact_list add a list of the buttons you want to appear in the sidebar such as 

"/usr/applications/amarok.desktop","/usr/applications/mydesktopfile.desktop"

An they will show up as compact buttons on the plugin pane ;-)

[SIZE=2]
[/SIZE][SIZE=2]**On another note:**[/SIZE]
It seems that with the last SVN update for beryl all my settings were lost and so were others. To get back USP with FOCUS working, set   "Focus stealing prevention" in beryl-settings -> General to "None"

---

### Post by Malac on 2007-01-26
> **chanders said:**
> In compact_list add a list of the buttons you want to appear in the sidebar such as 

"/usr/applications/amarok.desktop","/usr/applications/mydesktopfile.desktop"

An they will show up as compact buttons on the plugin pane ;-)

I've updated uspconfig and uspconfig.glade in the svn as soon as I read this, now at Revision 97.
Just a straight copy and paste of the plugins list code, have tested it but let me know if it throws any errors, either pm me or on the forum. :)

---

### Post by delfick on 2007-01-26
thnx :D :D

only one problem...

it doesn't seem to want to work ...

there's no error messages or anything, they just don't want to appear in the bar........

---

### Post by chanders on 2007-01-26
Update to the latest SVN. I added a line of code that should fix it...

---

### Post by delfick on 2007-01-26
thnx....though i still can't get it to work.... am i doing something wrong ?? (see screenshot)

---

### Post by chanders on 2007-01-26
For some reason the key is not being set by usp config. Malac will take a look at it when he gets up ;-)

In the interim, enter it directly in gconf (without the quotes ;-))

eg;

/usr/share/applications/AdobeReader.desktop

[IMG]http://img408.imageshack.us/img408/7292/screenshot2gs2.png[/IMG]

---

### Post by delfick on 2007-01-27
> **chanders said:**
> In the interim, enter it directly in gconf (without the quotes ;-))

yay :D :D

thnx :D

i tried it in gconf before but had the quotes....

also.... nice pic.....how is it transparent ??? :D :D :p

and how do you get some at the top and some at the bottom ??

---

### Post by Malac on 2007-01-27
> **chanders said:**
> For some reason the key is not being set by usp config. Malac will take a look at it when he gets up ;-)

Just got up :) and had a look, uspconfig is working fine on my system.
Don't forget to hit the [Save] Button or your changes will be lost i.e. it won't be added to the compact_list.
If this is causing confusion I can change it to commit any changes straight away and remove the  [Reset] Button.

I need to tidy the code up anyway as this was just a quick cut and paste last night and still says "Plugin Name" on the input box so will probably add a browse to file facility.

EDIT: uspconfig code updated, now Revision 101.

---

### Post by delfick on 2007-01-27
> **Malac said:**
> EDIT: uspconfig code updated, now Revision 101.

awsome Thnx :D

it works :D

.....now

how do i make my own "compact system management" ??

i can't find .desktop files for them.... :(

---

### Post by Malac on 2007-01-27
> **delfick said:**
> how do i make my own "compact system management" ??
Make your own launchers/desktop files.
Install Software command is "gksu /usr/sbin/synaptic"
Control Center command is "gcontrol"
Lock Screen command is "gnome-screensaver-command --lock"
Quit command is "gnome-session-save --kill"

These are the commands listed in uspconfig System Management config page.

---

### Post by zekopeko on 2007-01-27
me would also want to know how chanders has so good looking USP2.
how to make it look so good?

---

### Post by Malac on 2007-01-27
> **zekopeko said:**
> me would also want to know how chanders has so good looking USP2.
how to make it look so good?
That's Beryl for you. :)
[ATTACH]23973[/ATTACH]
Don't think mine looks too bad, at the mo. :D

---

### Post by zekopeko on 2007-01-27
okey. but how do you get that fancy button in usp (the chanders button :) )?
is it a theme?
and when changing the icons for launchers or USP button can you give an absolute path or only relative, and if relative in what folder are they?

 i hop that you will put a file browser button when you right click an app to change the text/icon so that you can browse to the icon

---

### Post by chanders on 2007-01-27
> **delfick said:**
> and how do you get some at the top and some at the bottom ??
The ones on the top are minimized plugins, the ones on the bottom are your shortcuts :-P

> **zekopeko said:**
> me would also want to know how chanders has so good looking USP2.
how to make it look so good?

> **delfick said:**
> 
also.... nice pic.....how is it transparent ??? :D :D :p

That is just my proof of concept for theming USP. I haven't committed it yet but what you see is true transparency and blur. If you notice the text and buttons are full opacity but the background only, is transparent.

Very soon we will have full theming in USP, transparency and all  :guitar:

BTW: Thanks for the link Malac ;-)

---

### Post by Malac on 2007-01-27
> **chanders said:**
> BTW: Thanks for the link Malac ;-)
Glad I could help.
After mucking up the svn repo, perhaps karmically speaking it makes amends. :)

Mind you, I can see this is going to mean more work on uspconfig.

---

### Post by delfick on 2007-01-27
> **chanders said:**
> The ones on the top are minimized plugins, the ones on the bottom are your shortcuts :-P

can it be made an option to have some shortcuts at the top and some at the bottom ?? please :D (i never minimise the plugins anyways :D)

> Very soon we will have full theming in USP, transparency and all  :guitar:

YAY!!!!

i thought it looked like real transparency :p

you rule :D

[Quote=Malac]Make your own launchers/desktop files.
Install Software command is "gksu /usr/sbin/synaptic"
Control Center command is "gcontrol"
Lock Screen command is "gnome-screensaver-command --lock"
Quit command is "gnome-session-save --kill"[/Quote]

thnx Malac, works well :D

though what do i put as type for the Quit and lockscreen ones ?? (the others are type=application) ...... thnx :D

---

### Post by Malac on 2007-01-27
> **delfick said:**
> though what do i put as type for the Quit and lockscreen ones ?? (the others are type=application) ...... thnx :D

Same thing they are apps too.

---

### Post by zekopeko on 2007-01-27
ok i did something and usp2 is totaly weird. i don't have any apps, images or anything. i only have user, applications, recent (and nothing in it). usp is completely blank.
so....how do i remove it? completely. 

i want to remove every file usp2 uses and the run the svn script to install it again.

---

### Post by delfick on 2007-01-27
> **Malac said:**
> Same thing they are apps too.

k then.... :D

though with synaptic, i have "Exec=gksu /usr/sbin/synaptic" but when i press it, it says starting without administrative privileges......

---

### Post by Malac on 2007-01-28
> **delfick said:**
> k then.... :D

though with synaptic, i have "Exec=gksu /usr/sbin/synaptic" but when i press it, it says starting without administrative privileges......
Try changing it to Exec=**"**gksu /usr/sbin/synaptic**" **and let me know if that works.
Also where is the .desktop file you are using I found without the quotes worked if the file was in /home/~/.local/share/applications folder.

---

### Post by Malac on 2007-01-28
> **zekopeko said:**
> ok i did something and usp2 is totaly weird. i don't have any apps, images or anything. i only have user, applications, recent (and nothing in it). usp is completely blank.
so....how do i remove it? completely. 

i want to remove every file usp2 uses and the run the svn script to install it again.
You need to remove the following:
/usr/bin/usp
/usr/bin/uspconfig
/usr/share/usp/usp2.glade
/usr/share/usp/uspconfig.glade
/usr/lib/python2.4/site-packages/usp/plugins (whole folder).

Then run the update script.

---

### Post by delfick on 2007-01-28
arrgghhh, i had uspconfig using the wrong synaptic.desktop

because i had already added some things from /usr/share/applications before i made the ones that i'm using now (in a random folder in ~) ......

so i made it use the right one, and now all is good :D

now i just need a way to put some at the top and some at the bottom :D

---

### Post by zekopeko on 2007-01-28
> **Malac said:**
> You need to remove the following:
/usr/bin/usp
/usr/bin/uspconfig
/usr/share/usp/usp2.glade
/usr/share/usp/uspconfig.glade
/usr/lib/python2.4/site-packages/usp/plugins (whole folder).

Then run the update script.

ok something isn't right.

i didn't have those files/directory. also didn't have 1.91 deb installed from the thread.

when to ubuntu-system-panel and from there i ran the script as so

./usp_update 

after that logged out and back in. but it doesn't show in Add to Panel...
then i went and looked for the files but they aren't there.

is the script messed up?

EDIT:
i copied manually and that worked. Also i would report a bug. when you remove app from favorites it leaves a button with no icon or text at the top of the list. and you can't remove it. once i clicked it and everything froze.

---

### Post by PsyberOneZero on 2007-01-29
> **zekopeko said:**
> ok something isn't right.

i didn't have those files/directory. also didn't have 1.91 deb installed from the thread.

when to ubuntu-system-panel and from there i ran the script as so

./usp_update 

after that logged out and back in. but it doesn't show in Add to Panel...
then i went and looked for the files but they aren't there.

is the script messed up?

EDIT:
i copied manually and that worked. Also i would report a bug. when you remove app from favorites it leaves a button with no icon or text at the top of the list. and you can't remove it. once i clicked it and everything froze.

When you ran the script again what did it say?
USP is up to date?
if so it wouldn't have copied them over, I'm working on making the script more like a Makefile with options like [update, install, uninstall]  I've been sick the past few days so I'll start working on it this week.

also a quick fix for the bug is to go to ~/.usp/applications.list and remove the first 2 lines, usually the app you removed and a blank line.  then just reload the plugins and it should be fine

---

### Post by zekopeko on 2007-01-29
^^^

the script says that USP is up to date.
since i copied manually those it mean that when i run the script next time that it will work as advertised? ie update the files?

---

### Post by Uncle Spellbinder on 2007-01-29
> **chanders said:**
> ...For now try to set icon sizes to larger than zero (1-4) and set the width and height to some non-zero value (try 150 and 150 for starters)..

Well, I'm back to Ubuntu after nearly 6 months in Windows hell. New computer, reformatted, added Ubuntu Edgy (no dual boot, just Edgy). 

The first things I did were Beryl and USP. Read this lengthy thread and found the above fix for USP. Still tweaking height/width and such, but all is well and seems to work fine for me so far. On to theme/Beryl tweaking next. :D 

*Chanders*, thanks so much for your work on USP. Simply wonderful, as always!

---

### Post by chanders on 2007-01-29
^^ No problem ;-)  Malac, myself and PsyberOneZero have been doing a lot to get it ready... Try out the new features like 

* Adding custom buttons to the sidepane
* New recent plugin!
* New places plugin

Coming soon to SVN True transparency!!

---

### Post by PsyberOneZero on 2007-01-29
> **zekopeko said:**
> ^^^

the script says that USP is up to date.
since i copied manually those it mean that when i run the script next time that it will work as advertised? ie update the files?

It will work fine the next time the SVN repo is updated (which I think just happened).  And I'm working on a version that wont matter.

---

### Post by zekopeko on 2007-01-29
^^^
just to be a little of topic. what do you have on all this drives? :)

---

### Post by delfick on 2007-01-29
> **chanders said:**
> Coming soon to SVN True transparency!!

i'm excited !! (jumping around like little excited child).............

(k then, maybe that is going a little too far....but i don't care :D :P )

---

### Post by PsyberOneZero on 2007-01-29
> **zekopeko said:**
> ^^^
just to be a little of topic. what do you have on all this drives? :)

A media server; TV Shows, Movies, and Music. I've only got ~300gb free :D

---

### Post by Uncle Spellbinder on 2007-01-30
> **chanders said:**
> ^^ No problem ;-)  Malac, myself and PsyberOneZero have been doing a lot to get it ready... Try out the new features like 

* Adding custom buttons to the sidepane
* New recent plugin!
* New places plugin

Thanks to Malac and PsyberOneZero, too!   ;) 

Tweaked to my liking. Not a fan of *recent*. Never use it (even in Windows). I added *places* but I'm not sure how to add custom buttons in the sidepane.  Screenie below.

---

### Post by Malac on 2007-01-30
> **Uncle Spellbinder said:**
> Thanks to Malac and PsyberOneZero, too!   ;) 
You're Welcome.
> **Uncle Spellbinder said:**
>  but I'm not sure how to add custom buttons in the sidepane.  Screenie below.
If you choose Preferences from the right-click menu next to the "Plugins" is "Compact List" click on that, choose [Add].
It should open a file dialog in /usr/share/applications and you can choose a .desktop file from there or create your own launcher and navigate to that.
Click [Open] and then [Save] to save the List.

---

### Post by Uncle Spellbinder on 2007-01-30
> **Malac said:**
> If you choose Preferences from the right-click menu next to the "Plugins" is "Compact List" click on that, choose [Add].
It should open a file dialog in /usr/share/applications and you can choose a .desktop file from there or create your own launcher and navigate to that.
Click [Open] and then [Save] to save the List.

I don't see "Compact List" anywhere. Am I missing something, or am I blind as a bat? :-k

---

### Post by chanders on 2007-01-30
You need to get the latest SVN ;-)

---

### Post by Malac on 2007-01-30
> **Uncle Spellbinder said:**
> I don't see "Compact List" anywhere. Am I missing something, or am I blind as a bat? :-k
Oops sorry, my fault for assuming you had the latest svn.
You can manually add the names of the .desktop files to the /app/usp/compact_list key in gconf-editor.
Or as chanders said get the latest and "greatest" :wink:

EDIT: Scratch that. If you haven't got the latest uspconfig svn you probably haven't got the latest usp.
What can I say, I'm having a dense day................again. :)

---

### Post by jackrobinson on 2007-01-30
excellent effort! USP is a must have applet. 
Two minor suggestions:
1) uspconfig should allow changing the icon size for "System Management" icons.
2) Icons in Applications menu should be allowed to go a notch higher than size 4 (probably size 5?)

-JR

---

### Post by chanders on 2007-01-30
Will put it on the list ;-)

---

### Post by Malac on 2007-01-31
> **chanders said:**
> Will put it on the list ;-)
> **jackrobinson said:**
> 1) uspconfig should allow changing the icon size for "System Management" icons.
 The code is already in the uspconfig section of the .py and .glade files. to do this, it just needs "activating".

---

### Post by chanders on 2007-01-31
Will get right to it!

---

### Post by jackrobinson on 2007-01-31
Please pardon if the following bug has been reported before.
Menu directories in Applications such as Debian and Wine which have subdirectories are displaying the last menu item of the directory just above it. 
For example just above the wine directory lies "System Tools" and in it the last item is Vmware Player. Thus the item showing up in Wine is "Vmware Player" instead of the subdirectory "RealPlayer".
The easiest way to try and reproduce this would be to install the Debian menu

---

### Post by Uncle Spellbinder on 2007-02-01
Two issues I've run across:

1) So far, I've only run across 1 app that will not launch from USP (it will from the standard Ubuntu menu), ***Brasero***. Brasero issue or USP issue?

2) In *Places* everything is shown, including my 2 external hard drives. From USP, only one of the two will open. The other gets an error message (pictured below). Both open fine in the standard Ubuntu menu.

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/MyBookUSP.png[/IMG]

---

### Post by Malac on 2007-02-01
> **Uncle Spellbinder said:**
> 2) In *Places* everything is shown, including my 2 external hard drives. From USP, only one of the two will open. The other gets an error message (pictured below). Both open fine in the standard Ubuntu menu.
I suspect it's the parsing of the name "My%20Book" one or other of the programs is parsing "My Book" into "My%20Book" then when it is opened it's literally looking for the "%20" name.
I've an idea of where it is so I'll run it past chanders.

---

### Post by chanders on 2007-02-01
Fixed! Unzip attached file and put in /usr/lib/python2.4/site-packages/usp/plugins..

---

### Post by motang on 2007-02-01
This is looking very cool, I am stuck at work with a Windows XP machine but you know what I will be doing once I get home. :-)

---

### Post by mostwanted on 2007-02-01
I just installed this on Edgy and adding the applet to the panel doesn't seem to work. Running usp from the cmd-line yields no response and no process is started. Uspconfig works, though.

---

### Post by Malac on 2007-02-01
> **mostwanted said:**
> I just installed this on Edgy and adding the applet to the panel doesn't seem to work. Running usp from the cmd-line yields no response and no process is started. Uspconfig works, though.
From the command line you need to run :```
usp run-in-window
``` and then post the output, we'll try to help.

Also have you installed from the .deb at post #1 or from the svn.

---

### Post by chanders on 2007-02-02
> **Uncle Spellbinder said:**
> 1) So far, I've only run across 1 app that will not launch from USP (it will from the standard Ubuntu menu), ***Brasero***. Brasero issue or USP issue?

Can you post up the .desktop file for Brasero?

---

### Post by zekopeko on 2007-02-02
little question:

i have beryl svn running and usp2 is acting strangley. the search is a no go. i can't write in it.
also i have to click multiple times to open the menu.

any hack to solve this?

---

### Post by chanders on 2007-02-03
Actually not a hack per se, you have to turn off focus stealing in beryl. Set it to 'none'...

---

### Post by zekopeko on 2007-02-03
thnx! looks like this solved it.

---

### Post by _linux_ on 2007-02-03
When will the stable version of USP2 be launched?

---

### Post by chanders on 2007-02-04
Well there are just a few outstanding bugs... As soon as they are out of the way it'll be launched. No time frame as yet

---

### Post by delfick on 2007-02-04
> **_linux_ said:**
> When will the stable version of USP2 be launched?

hmmm, and so it starts again :D :P
[SIZE="1"]
(the asking for next version saga)[/SIZE]

---

### Post by cime on 2007-02-07
This shows up when I click System menu. Anybody knows what could be wrong?

---

### Post by Malac on 2007-02-08
> **cime said:**
> This shows up when I click System menu. Anybody knows what could be wrong?Right-click on "System",
Choose "Preferences"
Check that each plugin has an Icon Size greater than 0
Check the height and width are not 0

OR

Open gconf-editor and go to /apps/usp/plugins/*[COLOR=Gray]<name-of-plugin>[/COLOR]*
Alter height, width and icon_size so they are not 0.

If this doesn't work run ```
usp run-in-window
``` in a terminal and post the output.

---

### Post by Strash on 2007-02-08
Is there a possibility to get a .deb file for the current version (for Edgy) ? I only have the old 1.91 one.

I know that there is a SVN repository but I'm not fond of those things and a DEB is so easy to use...

Thanks

---

### Post by chanders on 2007-02-08
Ok. Will talk to malac and we will try to get a Beta out ;-)

---

### Post by Malac on 2007-02-08
Just committed the tabbed version of USP to the SVN.

If people could let me know how it goes through here or pm that would be cool.

The tabs use the keyword "newtab" (without the quotes) and follow the same principal as the "newpane" keyword except if you want to name the tab in which case you use "newtab=[COLOR=DimGray]*[SIZE=2]<Text-You-Want-Here>[/SIZE]"*[/COLOR] (without the quotes).

e.g. This plugins_list:
newtab=System Stuff
newpane
uspuser
computer
system_management
newtab=Application Launcher
applications
recent
newpane
shortcuts
places
newtab=Extra Stuff
terminal
calculator
notes
newpane
usptime
calrem
newtab=Internet
internet

 would give these tabs :
[ATTACH]24833[/ATTACH][ATTACH]24834[/ATTACH][ATTACH]24835[/ATTACH][ATTACH]24836[/ATTACH]

---

### Post by delfick on 2007-02-08
that's awsome :D

thankyou Malac!!!! :D

attached are some screenshots :D

now we just need the tab bar to be the same colour as the rest of the usp :D

also, can it be made an option to stretch the tabs so that each tab is of equal size but the whole tabbar is still taken up by the tabs.......

and make it so that smaller tabs appear smaller :D


(and while i'm at it, can we have the abliity to put certain shortcuts on the compact list at the top of the sidebar ?? please :D)

thnx for all your work :D

---

### Post by zekopeko on 2007-02-08
hey that looks nice!

i just updated the svn and run ./usp_update.

do i need to restart to take effect or just remove and then add USP2 to gnome-panel?


<heavy_offtopic>

to DELFICK:

i go by the name OmegaBunny on beryl forums. could u point me to a faq for installing screenlets on my beryl? :D

</heavy_offtopic>

---

### Post by PsyberOneZero on 2007-02-08
> do i need to restart to take effect or just remove and then add USP2 to gnome-panel?
Normally you can just remove the applet and re-add it. It was just easier and safer to put restart in the script, every once in a while there's something that needs a restart.

---

### Post by delfick on 2007-02-08
> **zekopeko said:**
> <heavy_offtopic>
to DELFIC:

i go by the name OmegaBunny on beryl forums. could u point me to a faq for installing screenlets on my beryl? :D

</heavy_offtopic>

look at your pm on the beryl forums :D

(also, my name has a k on the end :D)

---

### Post by deadlydeathcone on 2007-02-08
Thank you, this is very cool.

Obligatory screenshot:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=24850&stc=1&d=1170986899[/IMG]

@ Delfick: You can space out the tabs a bit with ludicrous spaces.

---

### Post by delfick on 2007-02-08
> **deadlydeathcone said:**
> @ Delfick: You can space out the tabs a bit with ludicrous spaces.

thanx for that :D

much better :D

(though it proved my idea of having the tabs stretched, is a bad one :P (doesn't look so good when you have two gigantic tabs :D.....but having some space makes it look heaps better)

though can it be made so that the tab bar goes above the sidebar as well ?? (instead of next to it) thnx :D

---

### Post by Malac on 2007-02-09
> **delfick said:**
> thanx for that :D

much better :D

(though it proved my idea of having the tabs stretched, is a bad one :P (doesn't look so good when you have two gigantic tabs :D.....but having some space makes it look heaps better)

though can it be made so that the tab bar goes above the sidebar as well ?? (instead of next to it) thnx :D
I'm afraid due to GTK limitations I can't space the tabs out to use the whole area. (Someone correct me if I'm wrong, preferably with code snippet.):)

Also the SidePane is not part of the tabbed interface, to make the tabs appear above it the SidePane would need to be a separate one for each page.
I'd rather not go down this route as I'd like to keep the original functionality if users are only using one page, sorry delfick.:(

The different colour area in the top right can be changed by tweaking your theme. However come transparency (in USP3 probably) that area should be non-existent.

The next update should allow you to change the position of the tabs.(top, bottom, left, right)

---

### Post by delfick on 2007-02-09
> **Malac said:**
> I'm afraid due to GTK limitations I can't space the tabs out to use the whole area. (Someone correct me if I'm wrong, preferably with code snippet.):)

k then.....spaces will have to do then....

> Also the SidePane is not part of the tabbed interface, to make the tabs appear above it the SidePane would need to be a separate one for each page.
I'd rather not go down this route as I'd like to keep the original functionality if users are only using one page,

fair enough :D 

>  sorry delfick.:(

no probs :D


> The different colour area in the top right can be changed by tweaking your theme. However come transparency (in USP3 probably) that area should be non-existent.

ooohh, USP_3_......i take it that won't  be for a while??

> The next update should allow you to change the position of the tabs.(top, bottom, left, right)

cool :D



also, i keep asking this, (here goes my persistance again :D) can it atleast be made an option to have certain items in the compact list at the top of the sidebar ???? :D

again, thankyou for all your work :D

---

### Post by Malac on 2007-02-09
Actually scratch my last reply about GTK not being able to fill the space.
I've just done a search and sorted it. I've updated the SVN with new version of usp, uspconfig and uspconfig.glade which allows for expanding the tabs and changing the position of them.
 [ATTACH]24869[/ATTACH]
And Yep USP_3_ won't be for a while as the transparency is some major re-coding of the main USP. :)

As for the Compact List, it's all or nothing I'm afraid but if you want them at the top open usp2.glade and navigate to vbox1 and set the "Pack type" to "Start".
If you want them to stay above minimized plugins then also change "Position" to "1".
You'll have to remember to  do this every time you update. I'll check with Chanders if he's okay about me making this an option.

---

### Post by delfick on 2007-02-09
> **Malac said:**
> Actually scratch my last reply about GTK not being able to fill the space.
I've just done a search and sorted it. I've updated the SVN with new version of usp, uspconfig and uspconfig.glade which allows for expanding the tabs and changing the position of them.


awsome :D

> And Yep USP_3_ won't be for a while as the transparency is some major re-coding of the main USP. :)

can't wait till then :D

> As for the Compact List, it's all or nothing I'm afraid 

damn....that's what i thought would be the answer.....

what if the sidepane could be split into two sidepanes, one for the top, and another for the bottom of the sidepane???

(or am i just coming up with impossible-to-do ideas ??)

---

### Post by Malac on 2007-02-09
I think I may have solved your compact list probs, I'm just waiting for chanders to get back to me to okay the changes.
I've tested adding an option to move all the Compact Buttons to the top of the sidepane and that works fine then if you minimize plugins they just get added after the compact buttons.
Having some moved to the top and some still at the bottom is not an option without re-coding the whole sidepane and compact list sections.

As soon as I hear back in the affirmative I'll commit the changes.

---

### Post by delfick on 2007-02-09
> **Malac said:**
> Having some moved to the top and some still at the bottom is not an option without re-coding the whole sidepane and compact list sections.

and i take it that wouldn't happen for quite a while :P :D

it's times like these i wish i knew how to program.....[SIZE="1"].(though i am starting to go through a c++ tutorial and i'm starting university this year to do a bachelor of engineering in software engineering, so i should be able to program some day :D)[/SIZE]

> I've tested adding an option to move all the Compact Buttons to the top of the sidepane 

cool :D

---

### Post by chanders on 2007-02-09
> **Malac said:**
> Actually scratch my last reply about GTK not being able to fill the space.
I've just done a search and sorted it. I've updated the SVN with new version of usp, uspconfig and uspconfig.glade which allows for expanding the tabs and changing the position of them.
 [ATTACH]24869[/ATTACH]
And Yep USP_3_ won't be for a while as the transparency is some major re-coding of the main USP. :)

As for the Compact List, it's all or nothing I'm afraid but if you want them at the top open usp2.glade and navigate to vbox1 and set the "Pack type" to "Start".
If you want them to stay above minimized plugins then also change "Position" to "1".
You'll have to remember to  do this every time you update. I'll check with Chanders if he's okay about me making this an option.

That is one REALLY sweet screenshot!

---

### Post by Malac on 2007-02-09
Second Screenie with Compact List at top.
[ATTACH]24879[/ATTACH]

---

### Post by serlex on 2007-02-09
[QUOTE=Malac;2128093
And Yep USP_3_ won't be for a while as the transparency is some major re-coding of the main USP. :)
[/QUOTE]

date? :)

---

### Post by chanders on 2007-02-09
Coding as we speak ;-)

---

### Post by delfick on 2007-02-09
i think i may have found a temp solution to my wish :D 

basically i have blank spaces between the shortcuts at the top and them at the bottom (see attached screenshot)

(though the blank ones still have the button image....)

> **chanders said:**
> Coding as we speak ;-)

yay!!! :D

---

### Post by PWill on 2007-02-10
With the latest Feisty upgrade, USP won't load. It gives me this error when running:
```
paul@bel-air:~$ usp run-in-window
Using Standard Menu
Loading plugin 'places' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'computer' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 771, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 761, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 550, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 58, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 345, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 605, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 335, in Todos
    openfile = open( GetFilePath( path ), 'r' )
UnboundLocalError: local variable 'path' referenced before assignment

```

---

### Post by Malac on 2007-02-10
> **delfick said:**
> i think i may have found a temp solution to my wish :D 

basically i have blank spaces between the shortcuts at the top and them at the bottom (see attached screenshot)

(though the blank ones still have the button image....)
I can't seem to replicate this. All I can think is that you have some weird entries in the /apps/usp/compact_list key.
Open gconf-editor and navigate to that key and check you haven't got any strange entries or multiple entries pointing to a non existent (or malformed) .desktop file.
Check you have the latest revision which at the mo is 117.

---

### Post by delfick on 2007-02-10
> **Malac said:**
> I can't seem to replicate this. All I can think is that you have some weird entries in the /apps/usp/compact_list key.
Open gconf-editor and navigate to that key and check you haven't got any strange entries or multiple entries pointing to a non existent (or malformed) .desktop file.
Check you have the latest revision which at the mo is 117.

hmm, i don't think i explained myself enough....

i made .desktop files that used a transparent image as it's icon so that there'd be a space between the top and bottom...

though this way of seperating the top and bottom means the buttons still remain in the middle...

is there a way to implement blank spaces for the compact list ??

---

### Post by Malac on 2007-02-10
> **delfick said:**
> hmm, i don't think i explained myself enough....

i made .desktop files that used a transparent image as it's icon so that there'd be a space between the top and bottom...

though this way of seperating the top and bottom means the buttons still remain in the middle...

is there a way to implement blank spaces for the compact list ??
Sorry, I get what you are trying to do now, I've just taken a closer look at your screenie and realised that it's not the minimized plugins at one end but all your own .desktop files.
I'm not sure this is required for the majority of users and yours is definitely a special case. :) I've only implemented code to swap the minimized plugins area and compact buttons area.

I've just uploaded a patch which shouldn't effect anyone else (Revision 118 ).
What you need to do is insert a ^ character before the path to the .desktop file in the compact_list and it will put that one in the minimized plugin area.
See Pic:[ATTACH]24946[/ATTACH]
Note the highlighted one. To do this just click [Add] browse to .desktop file then click [Edit] and insert the ^ click [Save] and voila.
Best of both worlds I hope.

---

### Post by delfick on 2007-02-10
> **Malac said:**
> I've only implemented code to swap the minimized plugins area and compact buttons area..

YOU ARE A LEGEND !!!! :D

thankyou very very much :D

---

### Post by Malac on 2007-02-10
> **delfick said:**
> YOU ARE A LEGEND !!!! :DIn my own lunch time. :)

> **delfick said:**
>  thankyou very very much :DYou're Most Welcome.

---

### Post by Malac on 2007-02-10
> **xiamcitizen said:**
> With the latest Feisty upgrade, USP won't load. It gives me this error when running:
```
paul@bel-air:~$ usp run-in-window
Using Standard Menu
Loading plugin 'places' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'computer' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 771, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 761, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 550, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 58, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 345, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 605, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 335, in Todos
    openfile = open( GetFilePath( path ), 'r' )
UnboundLocalError: local variable 'path' referenced before assignment

```
I am not getting this on my Feisty machine upgraded to latest.
It may be that one of your Applications/Favorites menu entries is damaged or needs recreating in ~/.usp/applications or ~/.usp/applications.list.
Try renaming ~/.usp/applications folder to ~/.usp/applications.orig and renaming ~/.usp/applications.list file to ~/.usp/applications.list.orig then run usp run-in-window and see if that sorts it out or post output.

---

### Post by PWill on 2007-02-10
> **Malac said:**
> I am not getting this on my Feisty machine upgraded to latest.
It may be that one of your Applications/Favorites menu entries is damaged or needs recreating in ~/.usp/applications or ~/.usp/applications.list.
Try renaming ~/.usp/applications folder to ~/.usp/applications.orig and renaming ~/.usp/applications.list file to ~/.usp/applications.list.orig then run usp run-in-window and see if that sorts it out or post output.

Nope, that didn't help. Thanks for the reply though.

---

### Post by 4tro on 2007-02-11
just one simple remark, this would be a good time to change favourites into favorites.

it has been in USP for ages now :P

---

### Post by chanders on 2007-02-11
> **4tro said:**
> just one simple remark, this would be a good time to change favourites into favorites.

it has been in USP for ages now :P

LOL, I guess this will come with translations, as favourites is the UK spelling and favorites is the US..

---

### Post by delfick on 2007-02-11
> **chanders said:**
> as favourites is the UK spelling 

and the aussie spelling :D

---

### Post by Malac on 2007-02-11
Right along with color instead of colo**u**r (the correct way of spelling it):wink:.

---

### Post by 4tro on 2007-02-12
> **Malac said:**
> Right along with color instead of colo**u**r (the correct way of spelling it):wink:.

just looked it up and you're both right...
damn i need to pay less attention to american english sites :P

---

### Post by Mateo on 2007-02-16
will USP2 allow us to use a custom button image?

---

### Post by delfick on 2007-02-16
> **Mateo said:**
> will USP2 allow us to use a custom button image?

yep :D

already in svn :D

---

### Post by chanders on 2007-02-16
Ok guys and gals, I am announcing a feature freeze on USP2Alpha, with a week for final requests/bugs. Please make your requests available and if it is possible myself/Malac will try to accomodate. So far USP2Alpha is stable enough that I use it every day with no problems.

After this week, USP2Alpha will become USP2Beta, with final testing for critical errors/fixes and will be subsequently released as final, hopefully in time for Feisty (All you guys with Feisty running, time to do some hardcore testing!! :))

Like any good developers (or at least trying to be :KS) USP3 is already in the pipeline and I am happy to say that I am extremely pleased with the preliminary code. Just to pique your interest, here are some major advancements:[LIST]
[*] Full **alpha transparency** support.[/LIST][LIST]
[*] Which means it is also fully themable. **Themes** will be easy to write with a little CAIRO knowledge. I am suspecting those guys who write GTK2 themes will have a field day, as writing a theme will take them merely minutes.. RoberTO? :D[/LIST][LIST]
[*] Fear not, those who are not CAIRO inclined :-) I am hoping that Generic themes will have **engine configurations** so you can say adjust the transparency/color/size of a lot of items in the themes (Much like emerald ;-))[/LIST][LIST]
[*]** Drag and drop** for adding/moving/minimizing plugins!! Plugins can be added by dragging from a config window showing all plugins onto USP.[/LIST][LIST]
[*] Drag and drop from USP to any other app/desktop (**Same functionality as the stock menu**)[/LIST]On a sidenote, this might not be included in USP3, but I want to include a new search plugin that has a Tracker backend (Any Tracker developers reading this ;-)

And of course any ideas you guys have! I am all ears and I cant wait for your suggestions. Just to let you all know, I started this project just by viewing one mockup for the SLAB menu, so I would love if you have visual ideas you can give a mockup.

Well thats all for now, looking forward to the future!
USP Developers (Me speaking on behalf of the other guys ;-) Feel free to add anything guys)

---

### Post by Nano Geek on 2007-02-17
I have not been able to get USP to work in Feisty period. You can see from the screenshot below that it is empty. After it runs for awhile, I get a error message. I've tried both the Alpha 2 deb and svn but either work. Does anyone know how to fix this?

Thanks

---

### Post by Mateo on 2007-02-17
That's what mine looked like, on Edgy.  Except it also had a blank Places and System (i think it was system).

---

### Post by delfick on 2007-02-17
> **chanders said:**
> Like any good developers (or at least trying to be :KS) USP3 is already in the pipeline and I am happy to say that I am extremely pleased with the preliminary code. Just to pique your interest, here are some major advancements:[LIST]
[*] Full **alpha transparency** support.[/LIST][LIST]
[*] Which means it is also fully themable. **Themes** will be easy to write with a little CAIRO knowledge. I am suspecting those guys who write GTK2 themes will have a field day, as writing a theme will take them merely minutes.. RoberTO? :D[/LIST][LIST]
[*] Fear not, those who are not CAIRO inclined I am hoping that Generic themes will have **engine configurations** so you can say adjust the transparency/color/size of a lot of items in the themes (Much like emerald)[/LIST][LIST]
[*]** Drag and drop** for adding/moving/minimizing plugins!! Plugins can be added by dragging from a config window showing all plugins onto USP.[/LIST][LIST]
[*] Drag and drop from USP to any other app/desktop (**Same functionality as the stock menu**)[/LIST]On a sidenote, this might not be included in USP3, but I want to include a new search plugin that has a Tracker backend (Any Tracker developers reading this


hmm, i think i've said this before.....YOU RULE CHANDERS !!! :D (and other usp devs (i.e. Malac :D, you rule too :D))

after usp2 is released, will usp3 become uspsvn ?? :D

(also emerald type theme configuration sounds awsome ! :D)

---

### Post by Malac on 2007-02-17
> **asjdfwejqrfjcvm msz34rq33 said:**
> I have not been able to get USP to work in Feisty period. You can see from the screenshot below that it is empty. After it runs for awhile, I get a error message. I've tried both the Alpha 2 deb and svn but either work. Does anyone know how to fix this?
 
Thanks
I have it working on my Feisty Test Machine. The app error report tool seems to be kicking in for every error that USP kicks out this means it is even triggering for minor errors which we allowed to slip through as they didn't effect performance on Edgy.
I think part of the push for Beta Release will be going through the code and inserting some extra error catching of our own in a few places.
If you could find the "Traceback" info from the Bug Report Tool Details and post it in the BUGs thread of this forum that would help, thanks.
 
I can only suggest that you completely uninstall USP manually checking that all usp related directories are also gone then run:
gconftool-2 --recursive-unset /apps/usp
and make sure that the ~/.usp folder is empty.
Then re-install. If this still doesn't work post output of:
usp run-in-window
 
Sorry I can't be more help.

---

### Post by M7S on 2007-02-17
I have a little feature request before the feature freeze. I know this has been requested before but I don't know if there were a sollution for it: I would like favourites to always show when I open the USP. Now it just shows more applications or favourites depending on what was shown the last time.

It would also be nice if the terminal and notes plugins would get focus on mouse over, but I guess this would be hard to code.

---

### Post by Malac on 2007-02-17
> **M7S said:**
> I have a little feature request before the feature freeze. I know this has been requested before but I don't know if there were a sollution for it: I would like favourites to always show when I open the USP. Now it just shows more applications or favourites depending on what was shown the last time.

It would also be nice if the terminal and notes plugins would get focus on mouse over, but I guess this would be hard to code.
Favourites should show when USP starts if you haven't got "Open Showing All Applications" set on Preferences.
I assume you don't mean when it first starts though. I take it you mean each time you click the menu button.

I'll look into changing the "Open Showing All Applications" to work on when the menu is opened as well as when started, today. Or perhaps add a further option to "Remember Last Open View".

---

### Post by M7S on 2007-02-17
Yes I mean each time you klick the button. The first time it starts up with favourits. I simply want it to behave as usp 0.4x did.

Thanks for looking in to it.

---

### Post by Meta on 2007-02-17
I had the same issue with the empty USP. I noticed that all the gconf settings are set to 0 for width height and icon size. If you play with these in gconf in apps/usp/ you can get it to work.

---

### Post by kobewan on 2007-02-17
[double post deleted]

---

### Post by kobewan on 2007-02-17
> **Malac said:**
> Favourites should show when USP starts if you haven't got "Open Showing All Applications" set on Preferences.
I assume you don't mean when it first starts though. I take it you mean each time you click the menu button.

I second this :). The main reason is that whenever you search for something, it automatically switches to All Applications until you switch it back. I would also like to take it a little further and request that you can set the default displays for the Recent and Places plugins. Right now, they default to "Documents" and "Places" whenever you restart the program, and I would love to be able to set them to permanently be "Applications" and "Bookmarks".

A few other feature requests: 

1. Allow using the same plugin on different tabs. For example, put the "Recent" plugin in both the "Documents" and "Applications" tab. I'm pretty sure it would be hard to configure them both individually, so it should be good enough for them to be clones.

2. Make tabs dynamically expand depending on other tab sizes. Not sure how feasible this is, but it's the feature that I want the most. Basically, you set the minimum width of each plugin instead of a fixed width. Then, it will adjust the widths of all plugins when you change the tab, so that each tab will be the same size. Or, if not that, then the ability to set the color of the selected tabs's titlebar (it's currently set the same as the border color).

3. Not sure if this is a bug or not, but if you hit Backspace in the Applications search box, it erases one letter and selects the whole word. This gets a little annoying if you made a typo and want to correct it, since hitting Backspace and then typing will erase the whole word. If this is intentional, please include an option to turn it off. And also, another request related to search: if your search has only one hit, then hitting Enter should open that program.

Sorry to be requesting features so late, but I just found out about this awesome program a couple of days ago.

---

### Post by Malac on 2007-02-17
> **kobewan said:**
> 1. Allow using the same plugin on different tabs. For example, put the "Recent" plugin in both the "Documents" and "Applications" tab. I'm pretty sure it would be hard to configure them both individually, so it should be good enough for them to be clones.

2. Make tabs dynamically expand depending on other tab sizes. Not sure how feasible this is, but it's the feature that I want the most. Basically, you set the minimum width of each plugin instead of a fixed width. Then, it will adjust the widths of all plugins when you change the tab, so that each tab will be the same size. Or, if not that, then the ability to set the color of the selected tabs's titlebar (it's currently set the same as the border color).

3. Not sure if this is a bug or not, but if you hit Backspace in the Applications search box, it erases one letter and selects the whole word. This gets a little annoying if you made a typo and want to correct it, since hitting Backspace and then typing will erase the whole word. If this is intentional, please include an option to turn it off. And also, another request related to search: if your search has only one hit, then hitting Enter should open that program.
1. Done and committed to SVN Rev 130. Allow duplicates is now an option in Preferences.
2. Not sure what you mean by this I'm afraid. The plugins already expand width ways to the widest in that pane.
The colour of the tabs titlebar will be a theme thing this is why a separate theme can be setup so you can tweak something to look good in USP which wouldn't necessarily look good on your main desktop windows.
3. This ones for chanders I think.;)

Don't worry about "so late" stuff.
That's why we called the feature freeze in a week so people can decide what they really want and then let us know so we could try and get it done.

---

### Post by kobewan on 2007-02-17
> **Malac said:**
> 
2. Not sure what you mean by this I'm afraid. The plugins already expand width ways to the widest in that pane.
The colour of the tabs titlebar will be a theme thing this is why a separate theme can be setup so you can tweak something to look good in USP which wouldn't necessarily look good on your main desktop windows.

Let me try to explain more clearly:

If one tab is wider than the others (say it has 3 panes and the rest have 1) and you switch to a thinner tab, the thinner tab will have an ugly gray area. What I was hoping for is that instead of the gray area, the pane will automatically expand its width to that of the whole tab. If there are 2 panes, then they would both widen an equal amount and take up all the available area. Think of it as similar to the "Expand Tabs to fill space" option, only it expands the panes instead of expanding tab  titles.

On the other hand, I never really thought about themes...they sound good enough for my desire to remove the ugly gray area :D.

Also, I thought of something else that I want to see. Any chance of making the Compact List more powerful? For example:

1. The ability to add a separator or space. Also, maybe a drawer (like the standard gnome-panel ones), but I'm not sure that these would be useful.

2. Middle-clicking on a button would launch the application 'in the background'. Basically, it would launch the application but keep the menu open until you clicked out of it. Useful if you have some applications that you like to open together. For example, I generally launch Gaim, Thunderbird, uTorrent and my feed reader at the same time, and this would be much faster than opening the 4 times in a row. This might be useful for the Application plugin instead though...

3. Trilaunchers : the button would launch a different program depending on which of the three mouse buttons you click. This would, of course, be incompatible with the above point.
  
Yeah, I think that would be enough features to keep me happy for several years :D.

---

### Post by plun on 2007-02-17
Thanks Chanders and other devs for an excellent application...:) 

delfick is also here :D 

I am on Feisty and it crashed and crashed (latest svn)

plun@dunder:~$ ./usp_update install   solved it.

First run it was a crash now it runs problaby beacuse of mismatch with Python 2.4 and 2.5.

Thanks....:)

---

### Post by Xgen on 2007-02-18
What am I doing wrong... I installed the usp.deb file in the latest Feisty. No crashes, but the menu is completely blank - other than the plugin titles and separators. I also edited the gconf height/width and icon sizes to >0 and I am not using beryl/compiz. Reboot doesn't solve the problem.

OUTPUT:
> $ usp run-in-window
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 127, in showuser
    self.anim=gtk.gdk.PixbufAnimation(facepic)
gobject.GError: Image file '~/.face' contains no data


---

### Post by delfick on 2007-02-18
> **plun said:**
> delfick is also here :D 

:D

---

### Post by delfick on 2007-02-18
> **Xgen said:**
> What am I doing wrong... I installed the usp.deb file in the latest Feisty. No crashes, but the menu is completely blank - other than the plugin titles and separators. I also edited the gconf height/width and icon sizes to >0 and I am not using beryl/compiz. Reboot doesn't solve the problem.

OUTPUT:

hmmm, i'm unsure, hopefully chanders or malac know....untill then, try

```
gconftool-2 --recursive-unset /apps/usp
```
then empty your ~/.usp/plugins folder 

and try again....

...... :D

---

### Post by Xgen on 2007-02-18
> gconftool-2 --recursive-unset /apps/usp...then empty your ~/.usp/plugins folder 

 Delfick, thanks for the response...but after reediting the 0's in gconf, the outcome is still the same. Hopefully someone else has had the problem - and a solution.

---

### Post by plun on 2007-02-18
> **delfick said:**
> :D

Hi delfick

Well, I am trying to figure out how to download themes..:confused: 
Really difficult to find out "howtos" both for installing USP2 and then change the GUI with themes.  

Or maybe I am lazy...:)  it&#347; often enough to read the 1st message in a thread
and the last ...:)

---

### Post by Malac on 2007-02-18
> **Xgen said:**
> What am I doing wrong... I installed the usp.deb file in the latest Feisty. No crashes, but the menu is completely blank - other than the plugin titles and separators. I also edited the gconf height/width and icon sizes to >0 and I am not using beryl/compiz. Reboot doesn't solve the problem.


OUTPUT:
[System->Preferences->Login Photo]
Then choose a picture.
This should be fixed by beta.

---

### Post by kobewan on 2007-02-18
> **plun said:**
> Hi delfick

Well, I am trying to figure out how to download themes..:confused: 
Really difficult to find out "howtos" both for installing USP2 and then change the GUI with themes.  

Or maybe I am lazy...:)  it&#347; often enough to read the 1st message in a thread
and the last ...:)

Actually, USP just uses standard GTK 2.x themes. You can find several at:

[http://gnome-look.org/]("http://gnome-look.org/")

You should already have several GTK2.x themes installed. Open up Theme Manager (just type in 'theme' in USP to find it quickly:) ) and click on Theme Details. All the themes that are listed in the "Controls" tab can be applied to USP.

For more information, as well as an excellent theme, look at this post:

[http://ubuntuforums.org/showpost.php?p=2130161&postcount=1]("http://ubuntuforums.org/showpost.php?p=2130161&postcount=1")

(Another great theme for USP in my opinion is MacOS-X Aqua Theme from GNOME-Look. Even though I generally don't like the way that Macs look, the theme works excellently for USP.)

---

### Post by Mateo on 2007-02-18
> **Xgen said:**
> Delfick, thanks for the response...but after reediting the 0's in gconf, the outcome is still the same. Hopefully someone else has had the problem - and a solution.

i had the same problem, but couldn't figure it out.  Try the SVN instead, it works perfectly.

---

### Post by Malac on 2007-02-18
Can I just say that you can still get to "Preferences" even if USP won't launch by typing ```
uspconfig
``` into a terminal.
That way you can make adjustments which will hopefully mean USP starts.
Xgen from your output the problem is that the .face file doesn't exist.

---

### Post by plun on 2007-02-18
> **kobewan said:**
> Actually, USP just uses standard GTK 2.x themes. You can find several at:

[http://gnome-look.org/]("http://gnome-look.org/")

For more information, as well as an excellent theme, look at this post:

[http://ubuntuforums.org/showpost.php?p=2130161&postcount=1]("http://ubuntuforums.org/showpost.php?p=2130161&postcount=1")



Well, thanks !  I found out that USP uses the same themes but...  transparency  :confused: 

Chanders showed us USP2 with transparency, I cannot find how he did that trick ?

My "bling" but USP is really ugly...:)   

[[IMG]http://img253.imageshack.us/img253/3096/snapshot15ip3.th.png[/IMG]](http://img253.imageshack.us/my.php?image=snapshot15ip3.png)


What plugins can be used with svn ?

---

### Post by Malac on 2007-02-18
> **plun said:**
> Well, thanks !  I found out that USP uses the same themes but...  transparency  :confused: 

Chanders showed us USP2 with transparency, I cannot find how he did that trick ?

My "bling" but USP is really ugly...:)   

[[IMG]http://img253.imageshack.us/img253/3096/snapshot15ip3.th.png[/IMG]]("http://img253.imageshack.us/my.php?image=snapshot15ip3.png")


What plugins can be used with svn ?
Transparency won't be rolled out for this version of USP it's for USP3.

Looks like you are using the standard "Human" Ubuntu gtk theme.
You need to use the Theme button of the computer/settings plugin(or [System->Preferences->Theme]) to choose the theme you want to use for USP. If it isn't quite right then copy the theme to one called USP and change the .png's or gtkrc to what you like, then put that in the "USP Theme" box of the USP "Preferences" window.

See here for a list of the standard plugins :
[http://www.ubuntuforums.org/showpost.php?p=1967430&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1967430&postcount=1)
and for the Extra/Add-On plugins, here :
[http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2)

---

### Post by kobewan on 2007-02-18
Actually, I think that might (?) be LiNsta3. Anyways, if you change your Ubuntu theme, then you have to restart USP for the theme to be applied to it as well. As far as I can tell, LiNsta3 doesn't to a good job of theming anything *inside* the windows, and all apps look kinda ugly in it so its not really USP's fault. You can copy out the files that are relevant and change it yourself if you want, like Malac said. You can see that mine is themed fully, and differently than the rest of my OS:

[[IMG]http://img01.picoodle.com/img/img01/7/2/18/t_Screenshotm_d89ee4a.png[/IMG]]("http://img01.picoodle.com/img/img01/7/2/18/f_Screenshotm_d89ee4a.png")

---

### Post by plun on 2007-02-18
Thanks Malac and kobewan  !

Maybe I have playing to much with Beryl, Screenlets and Awn...:) 
It is Linsta3 a little modified.

A challenge to find answers for USP inside long threads.  I have learned
it in Beryls fora but everything important there is often also inside an updated 1st message..

Well... transparency...:guitar:

EDIT Followup.....

I got errors when I restart USP...  Python mess... Feisty is on 2.5

plun@dunder:~$ usp restart
/usr/lib/python2.4/site-packages/usp/plugins/usp_util.py:207: GtkWarning: Kan inte hitta temamotorn i "module_path": "pixmap",
  icon_theme = gtk.icon_theme_get_default()

---

### Post by hanzomon4 on 2007-02-18
I installed this on a fresh feisty install and it just crashed. So I re-installed "./usp-update install" an noticed that it reported /usr/share/usp as not existing. I did a mkdir /usr/share/usp and reinstalled, I added usp to the panel and it crashed so I added it again and it worked.

---

### Post by plun on 2007-02-18
More findings, I also installed plugins and several USP crashes, python 2.5...

If Beryl is enabled the terminal cannot be used.
So this is a challenge.

[[IMG]http://img527.imageshack.us/img527/272/snapshot17vv4.th.png[/IMG]](http://img527.imageshack.us/my.php?image=snapshot17vv4.png)

Where is auto generated crash reports stored ?  I looked within /var/logs/ but could
not find any ...

---

### Post by kobewan on 2007-02-18
USP will print some output if you run it with this command:

```
usp run-in-window
```

Please provide this output so that somebody can try to help you :D.

Also, beware that the Extra/Add-On plugins are less stable (I think) than the standard ones.

EDIT: By the way, what dock are you using? Any chance that it works properly without Beryl? I can't seem to find a decent dock that has fake transparency.

---

### Post by hanzomon4 on 2007-02-18
> **plun said:**
> More findings, I also installed plugins and several USP crashes, python 2.5...

If Beryl is enabled the terminal cannot be used.
So this is a challenge.

[[IMG]http://img527.imageshack.us/img527/272/snapshot17vv4.th.png[/IMG]](http://img527.imageshack.us/my.php?image=snapshot17vv4.png)

Where is auto generated crash reports stored ?  I looked within /var/logs/ but could
not find any ...

check /var/crash

I think the dock is the [avant window navigator ]("http://code.google.com/p/avant-window-navigator/") and yes it needs compositing to avoid seeing the big black block...

---

### Post by hanzomon4 on 2007-02-18
I still can't my tabs to look like buttons, here's a screenshot....

---

### Post by plueken on 2007-02-18
> **plun said:**
> 
Maybe I have playing to much with Beryl, Screenlets and Awn...:) 
It is Linsta3 a little modified.


I am a bit curious.  You say you are using Linsta3, and I can see the Vista-ish window decorator, but Linsta looks a bit... wrong.  I know I had a bit of trouble setting up the Linsta theme to look appropriate a while ago (I was trying to create one desktop that was nearly identical to a Vista machine, and one that was nearly identical to an OSX machine, to show off).

Have you installed the pixbuf gtk engine?  I know that I couldn't get any of the Linsta themes to look right until I went and manually installed gtk2-engines-pixbuf from the repos.  I am wondering if that might help with your specific problem.

Hoping I'm not just misunderstanding your problem, and wishing you well with your desktop experiments.

plueken

---

### Post by plun on 2007-02-19
> **kobewan said:**
> USP will print some output if you run it with this command:

```
usp run-in-window
```

EDIT: By the way, what dock are you using? Any chance that it works properly without Beryl? I can't seem to find a decent dock that has fake transparency.

Well, I have run that output but the crash report output is probably much
better to use for a developer. 

The dock is AWN   :)   Great !


plueken:  **gtk2-engines-pixbuf**

Thanks... much better and I installed that package with Edgy but with Feisty
I forgot it.   

Nevertheless with Beryl running I cannot use USPs Notes or Terminal.

And this output when I change theme and restart.

> plun@dunder:~$ usp run-in-window
/home/plun/.themes/Aerials/gtk-2.0/gtkrc:60: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/plun/.themes/Aerials/gtk-2.0/gtkrc:61: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/plun/.themes/Aerials/gtk-2.0/gtkrc:62: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
No recent applications
Loading plugin 'recent' : successful
Loading plugin 'internet' : successful
Loading plugin 'notes' : successful
Loading plugin 'calrem' : successful
Loading plugin 'terminal' : successful
No User Picture Specified or File Not Found
No recent applications

(usp:14237): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition




Clearlooks not supported ?  or is some more package missing ?

Thanks for helping :)

EDIT

hanzomon4, found the crashreport   /var/crash/ 
attached   :)

---

### Post by kobewan on 2007-02-19
> **hanzomon4 said:**
> I still can't my tabs to look like buttons, here's a screenshot....

Hm, you're screenshot looks like you aren't actually using tabs. To find out more on tabs, look here:

[http://ubuntuforums.org/showthread.php?t=361376]("http://ubuntuforums.org/showthread.php?t=361376")

and here, for putting images in tab headers:

[http://ubuntuforums.org/showpost.php?p=2159324&postcount=46]("http://ubuntuforums.org/showpost.php?p=2159324&postcount=46")

---

### Post by delfick on 2007-02-19
> **chanders said:**
> And of course any ideas you guys have! I am all ears and I cant wait for your suggestions. Just to let you all know, I started this project just by viewing one mockup for the SLAB menu, so I would love if you have visual ideas you can give a mockup.

i have another idea...

make some plugins become multicolumn......

it could possibly be worded better, but basically say for example the applications plugin, instead of having the favourites icons in just one column, why not in multiple columns....somewhat like the slab :D

see in the screenshot attached, how the usp (guess which one that is :D) has the favourites in only one column whilst the slab has in two....

basically, can it be made an option for particular plugins like applications, recent, etc to have more than one column for the icons and/or text to be placed in ?? :D (i.e. as many columns as wanted :D)

---

### Post by plun on 2007-02-19
> **delfick said:**
> i have another idea...

make some plugins become multicolumn......

:D)

Well... delfick  :) 

This project is really fun.... I just read your notes within another "room" about more
boring stuff...:)  

kobewan and Malac also wrote great howtos  :) 

I must break the theme challenge...:biggrin: it works with a MacOS theme...:confused:

---

### Post by hanzomon4 on 2007-02-19
Thanks I didn't know that I had to specify tabs in the preferences

---

### Post by Malac on 2007-02-19
.Scratch

---

### Post by delfick on 2007-02-19
> **plun said:**
> Well... delfick  :) 

This project is really fun.... I just read your notes within another "room" about more
boring stuff...:)  

kobewan and Malac also wrote great howtos  :) 

I must break the theme challenge...:biggrin: it works with a MacOS theme...:confused:

??? :D :confused:

---

### Post by Malac on 2007-03-21
As the Beta release seems to be delayed I have taken the opportunity to add a couple of requests to the SVN before it goes Beta.
SVN Revision 221:
Recent now lets you decide whether to start showing Applications or Documents. Also shows Thumbnails for files in Recent Documents
Places now lets you decide whether to start showing Places or Bookmarks.
Applications now let's you decide whether it shows the last tab when USP menu is shown.
All the above plus Shortcuts and System Management, now allow icon and font size adjustment.
Settings/Computer can now change the button "information" font size as well as the bold "title" font size. Added width adjustment and some alignment alterations.


Anything else quick? [SIZE=1]:popcorn:[/SIZE]

---

### Post by delfick on 2007-03-21
> **Malac said:**
> As the Beta release seems to be delayed 

lol :D

> Anything else quick? [SIZE=1]:popcorn:[/SIZE]


copy and paste functionality in the terminal plugin would be nice :D

---

### Post by Malac on 2007-03-21
> **delfick said:**
> copy and paste functionality in the terminal plugin would be nice :D
No sooner said than done. :)
Updated the main .tar and .deb at this post [http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2) , but here are the files on their own.

---

### Post by delfick on 2007-03-22
> **Malac said:**
> No sooner said than done. :)
Updated the main .tar and .deb at this post [http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2) , but here are the files on their own.

YAY!!

thnx :D

much better... 

though can it be as a shortcut please ?? (i.e. <shift><ctrl><v> (to paste, or 'c' to copy and 'x' to paste)

and when can we start to see USP3 in svn ?? :D

---

### Post by Malac on 2007-03-22
> **delfick said:**
> though can it be as a shortcut please ?? (i.e. <shift><ctrl><v> (to paste, or 'c' to copy and 'x' to paste)
Didn't even know the main terminal had this until I tried your key combinations, but I'll look into it. :)

 I'd been using <Ctrl>C and <Ctrl>V when that didn't work I assumed it wasn't available and never checked.
At least I've learnt some thing today. :)

---

### Post by delfick on 2007-03-22
> **Malac said:**
> Didn't even know the main terminal had this until I tried your key combinations, but I'll look into it. :)

 I'd been using <Ctrl>C and <Ctrl>V when that didn't work I assumed it wasn't available and never checked.
At least I've learnt some thing today. :)

lol :D

---

### Post by Malac on 2007-03-23
I've discovered the terminal widget copy/paste from the keyboard is already available. The keys are preset to <Ctrl>Insert to copy selection and <Shift>Insert to paste. I've added them as accelerators to the copy/paste menu.
Also the previous version had reverted to opening in root dir now changed back to users home.
(New version uploaded to previous post.)

I'm not happy with these key combinations, as they are unlike the usual copy/paste keys, so I'll do some checking on how to change it.

---

### Post by delfick on 2007-03-23
> **Malac said:**
> I've discovered the terminal widget copy/paste from the keyboard is already available. The keys are preset to <Ctrl>Insert to copy selection and <Shift>Insert to paste. I've added them as accelerators to the copy/paste menu.
Also the previous version had reverted to opening in root dir now changed back to users home.
(New version uploaded to previous post.)

I'm not happy with these key combinations, as they are unlike the usual copy/paste keys, so I'll do some checking on how to change it.

awsome thnx :D

---

### Post by Malac on 2007-03-24
> **Malac said:**
> I'm not happy with these key combinations, as they are unlike the usual copy/paste keys, so I'll do some checking on how to change it.
Changed the Key combinations to <Shift><Ctrl>C (copy) and <Shift><Ctrl>V (paste) this is now the same as the Gnome-Terminal so should be more instinctive. <Ctrl>Insert and <Shift>Insert still work for pasting to "PRIMARY".
(New version uploaded to previous post and main thread post #2.)

---

### Post by delfick on 2007-03-24
> **Malac said:**
> Changed the Key combinations to <Shift><Ctrl>C (copy) and <Shift><Ctrl>V (paste) this is now the same as the Gnome-Terminal so should be more instinctive. <Ctrl>Insert and <Shift>Insert still work for pasting to "PRIMARY".
(New version uploaded to previous post and main thread post #2.)


YAAAAAAAAAY!!!!

thankyou! :D

---

### Post by Malac on 2007-03-24
Added width, height adjustment, icon selection and sidepane restriction to calculator plugin.
And a slightly better layout.

I'm thinking of doing a resources monitor but I'm unsure if this would be any use.
I've blocked out a simple Memory, Swap and VMAlloc usage version.
If people want it what resources would they want monitoring?

---

### Post by delfick on 2007-03-24
> **Malac said:**
> Added width, height adjustment, icon selection and sidepane restriction to calculator plugin.
And a slightly better layout.

cool :D

is it in svn ?? (because it doesn't seem to be..)

I> 'm thinking of doing a resources monitor but I'm unsure if this would be any use.
I've blocked out a simple Memory, Swap and VMAlloc usage version.
If people want it what resources would they want monitoring?

resource monitor would be cool :D

---

### Post by Malac on 2007-03-25
> **delfick said:**
> is it in svn ?? (because it doesn't seem to be..)
No, none of these Add-On Plugins is officially part of USP so aren't available in the SVN.
 
I suppose I could setup a separate SVN for them or maybe a branch in the main SVN.

---

### Post by delfick on 2007-03-26
> **Malac said:**
> No, none of these Add-On Plugins is officially part of USP so aren't available in the SVN.
 
I suppose I could setup a separate SVN for them or maybe a branch in the main SVN.

sounds good to me :D

---

### Post by cmost on 2007-03-27
You guys keep adding all these cool features.  USP will become a desktop environment eventually!  :-)  Can someone please build a DEB file for the latest SVN snapshot?  I'd really appreciate one for my Edgy X86-64 bit system.  I never seem to have good luck when it comes to building from SVN sources myself.  I'm still using USP 1.0 and the DEB someone posted months ago is hopelessly outdated now.  Thanks guys, you're the best!

---

### Post by delfick on 2007-03-28
> **cmost said:**
> You guys keep adding all these cool features.  USP will become a desktop environment eventually!  :-)  Can someone please build a DEB file for the latest SVN snapshot?  I'd really appreciate one for my Edgy X86-64 bit system.  I never seem to have good luck when it comes to building from SVN sources myself.  I'm still using USP 1.0 and the DEB someone posted months ago is hopelessly outdated now.  Thanks guys, you're the best!

in svn there's no compiling necessary :D

just follow this here [http://ubuntuforums.org/showthread.php?p=2178643#post2178643](http://ubuntuforums.org/showthread.php?p=2178643#post2178643)

 :D

---

### Post by wikiguy on 2007-05-08
Hey man that thing doesnt display my pci what do i have to do](*,) 

THANKS FOR ALLL

---

### Post by sefs on 2007-05-19
currently on 0.41, and thought this project was dead but i see its still very much alive, where can i pick up the latest stable version with noob installation directions.  A beta would suffice as well.  In beryl there is a problem with both this and gnome main menu.  When I click on the menu to open it, it open over all windows, the second time i click on it it opens under allwindows, and so on back and forth.  Can this bug be squashed so it always opens over all currentlly open windows?

Thanks.

---

### Post by flavioamieiro on 2007-05-21
Try setting the Level of Focus Stealing Prevention (on the beryl settings manager > general options > main tab) to none. This should work.

---

### Post by sefs on 2007-05-21
I have to give you the tulop on that one....you are a boss.

> **flavioamieiro said:**
> Try setting the Level of Focus Stealing Prevention (on the beryl settings manager > general options > main tab) to none. This should work.

---

### Post by sefs on 2007-07-09
i just installed usp_1.91_all.deb.  And since a picture is worth a thousand words...here we go.  Let me know what i am doing wrong.

before installing ... i uninstalled the ver 0.14
then i ran the gconf unset thing
then i deleted anyfiles in the plugin folder (which was already empty)


Thanks.

I have again tried reinstalling...

but first i deleted the usp gconf setting
deleted the .usp from hom dir
uninstalled

and reinstalled and same problem....the screens are empty because the heights are all set to "1"  when you increase the height then you begin to see stuff.  Also the text is centered and looks horrible.  only the system managment text is not centered.  How do i uncenter the text for plugins.  Is there a file to edit?

Thanks.

---

### Post by Malac on 2007-07-09
This is a known issue with the deb file which is now hopelessly out of date.

I recommend installing the SVN version and seeing if that works.
Installation instructions and some Troubleshooting tips are here:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps.

---

### Post by sefs on 2007-07-09
should i uninstall the deb first?

Edit: ok i have it installed, how do i turn off tool tips, i can only seem to turn them off in recent as it has a check box to do that.

---

### Post by sefs on 2007-07-10
Unable to launch K9copy from latest svn

EDIT:  The launch command used when k9 is installed is 

k9copy -caption "%c" %i %m  %u

I believe its the "%c" that's the issue here.  Are you filtering for delimiters that can appear as part of an input and escaping them properly?  such as double quotes and single quotes?

---

### Post by Malac on 2007-07-11
> **sefs said:**
> Unable to launch K9copy from latest svn

EDIT:  The launch command used when k9 is installed is 

k9copy -caption "%c" %i %m  %u

I believe its the "%c" that's the issue here.  Are you filtering for delimiters that can appear as part of an input and escaping them properly?  such as double quotes and single quotes?
I suspect you are right, can you try [SIZE=4]**'**[/SIZE]%c[SIZE=4]**'**[/SIZE] (single quotes) instead?

---

### Post by sefs on 2007-07-11
No single quotes are not working either...but it works if i remove the "%c".  So these "unexpected" characters in the input stream are not being properly handled/escaped out when passed to whatever python uses to launch an external app is my guess.

> **Malac said:**
> I suspect you are right, can you try [SIZE=4]**'**[/SIZE]%c[SIZE=4]**'**[/SIZE] (single quotes) instead?

---

### Post by Malac on 2007-07-12
> **sefs said:**
> No single quotes are not working either...but it works if i remove the "%c".  So these "unexpected" characters in the input stream are not being properly handled/escaped out when passed to whatever python uses to launch an external app is my guess.
Okay having had a bit of time to look at the "execute" module it looks like chanders is specifically discounting %c, along with some other args, in this function:
```
def RemoveArgs(Execline):
    NewExecline = []
    Specials=["%f","%F","%u","%U","%d","%D","%n","%N","%i","%c","%k","%v","%m","%M", "-caption","--view"]
    for elem in Execline:
        if elem not in Specials:
            NewExecline.append(elem)
    return NewExecline
```
......so it isn't the quotes at all.
I am wondering if this is a "hold-over" from the launching system of the 0.4x version of USP. I can't see any reason for it to be in there at all but this would need to be checked with chanders as he has obviously filtered out these things for some reason. I will try pm'ing him to see if I can get an answer and post back here.

---

### Post by sefs on 2007-07-12
I note with interest that he says "%c" as opposed to ""%c""  in which module is this? applications.py? 
The actual arg is not %c but "%c" so in that Specials line he may have to do something like 

```

Specials=["%f","%F","%u","%U","%d","%D","%n","%N","%i","/"%c/"","%k","%v","%m","%M", "-caption","--view"]

```

where /" is escaping out those quotes but.  I suspect thought that python has its own way of escaping so I just used /" as an example.

> **Malac said:**
> Okay having had a bit of time to look at the "execute" module it looks like chanders is specifically discounting %c, along with some other args, in this function:
```
def RemoveArgs(Execline):
    NewExecline = []
    Specials=["%f","%F","%u","%U","%d","%D","%n","%N","%i","%c","%k","%v","%m","%M", "-caption","--view"]
    for elem in Execline:
        if elem not in Specials:
            NewExecline.append(elem)
    return NewExecline
```
......so it isn't the quotes at all.
I am wondering if this is a "hold-over" from the launching system of the 0.4x version of USP. I can't see any reason for it to be in there at all but this would need to be checked with chanders as he has obviously filtered out these things for some reason. I will try pm'ing him to see if I can get an answer and post back here.

---

### Post by sefs on 2007-07-12
Update:

I did a little test and change in the execute.py file 

```

Specials=["%f","%F","%u","%U","%d","%D","%n","%N","%i","%c","%k","%v","%m","%M", "-caption","--view"]

```

to

```

Specials=["%f","%F","%u","%U","%d","%D","%n","%N","%i","%c","%k","%v","%m","%M", "-caption","--view","\"%c\""]

```

I added the "%c" parameter at the end, and escaped the quotes, and was able to launch k9copy from the usp panel.

---

### Post by sefs on 2007-07-12
Observe the recent plugin for the apps displayed and the files displayed.

Note the recent apps is formatted properly and recent files is not (its centered) 

How can I get the recent files left aligned like the recent apps.

Thanks.

---

### Post by sefs on 2007-07-12
I edited recent.py ...

from

```

		Label1 = gtk.Label( DispName )
		Label1.set_size_request( AButton.size_request()[0]-20, -1 )
		Label1.set_ellipsize( pango.ELLIPSIZE_END )
		Label1.show()
		LStyle = pango.AttrList()
		attr = pango.AttrSize(self.recentfontsize*1000,0,-1)
		LStyle.insert(attr)
		Label1.set_attributes(LStyle)
		VBox1.add( Label1 )

```

to

```

		Label1 = gtk.Label( DispName )
		Label1.set_size_request( AButton.size_request()[0]-20, -1 )
		Label1.set_ellipsize( pango.ELLIPSIZE_END )
		Label1.set_alignment( 0.0, 0.0 )  #### LEFT ALIGNMENT WAS ADDED ####
		Label1.show()
		LStyle = pango.AttrList()
		attr = pango.AttrSize(self.recentfontsize*1000,0,-1)
		LStyle.insert(attr)
		Label1.set_attributes(LStyle)
		VBox1.add( Label1 )

```

see screenshot

---

### Post by sefs on 2007-07-12
One final question ...

When i open usp and type into the search box and then close the usp panel, and reopen it i see what i last type still in the search box.  Is there a way to not have that happen?  I would like that each time i open the usp panel, the search box is empty awaiting my input (its a privacy issue).

Also the filter function does not seem to be working as it should.  Here is why.

If i begin to enter text into the search box the apps begin to filter to the text entered.  Now if I click on the Accessories button then all apps in accessories are displayed.  If i begin to type text into search box again apps being to filter on what i enter but if I click on the All button nothing happens.  What should happen there is that all applications should show. 

May be you need to define a special case in the Def Filter subroutine for the All button? Whenever that is clicked upon should it not always show all applications?

Thanks.

---

### Post by Malac on 2007-07-12
@ sefs
This left justify problem only showed itself up on the move to feisty as something changed in the python modules, I thought we'd got them all but looks like this one slipped through.:)
Thanks for the fix I have updated the SVN with the patch.
I will look into the filter statements when I can.

---

### Post by sefs on 2007-07-12
> **Malac said:**
> I will look into the filter statements when I can.

Some thoughts on that for when you get the chance to look at it....

If i click on one of the application categories for instance "Accessories" then when the filter routine is ran then "Accessories" is passed in as the categorytext.  

When I Click on the "All" button then "" is passed in as the categorytext 

Maybe "All" should be passed in as the categorytext to the filter routine when that button is clicked upon...

then you could adjust the last piece of code to look someting link this 

from 

```

            if showAllAppsBool == True:
               if not re.search( text, full_label, re.IGNORECASE ):
                   i.hide()
               else:
                   i.show()
                if widget != self.wTree.get_widget( "entry1" ):
                    for i in self.wTree.get_widget( "vbuttonbox2" ).get_children():
                        i.set_relief( gtk.RELIEF_NONE )
                    widget.set_relief( gtk.RELIEF_HALF )

```

to

```

            if showAllAppsBool == True:
		if text == "All":
		    i.show()
		else:
                    if not re.search( text, full_label, re.IGNORECASE ):
                        i.hide()
                    else:
                        i.show()
                if widget != self.wTree.get_widget( "entry1" ):
                    for i in self.wTree.get_widget( "vbuttonbox2" ).get_children():
                        i.set_relief( gtk.RELIEF_NONE )
                    widget.set_relief( gtk.RELIEF_HALF )

```


UPDATE:

Actually you almost have it done further up...
where you set up the "All" button  and then you set up the rest of category buttons in the loop just below.

but here is what you have ...

```

        CategoryButton = MakeAButton( -1, -1, gtk.RELIEF_NONE, "", 0, 0, 0, ["All"], [AppStyle] )

	if self.menustyle == True:
		CategoryButton.connect( "enter_notify_event", self.Filter, "" )
	else:
        	CategoryButton.connect( "button_press_event", self.Filter, "" )

        self.wTree.get_widget( "vbuttonbox2" ).add( CategoryButton )

```

why not do this instead...

```

        CategoryButton = MakeAButton( -1, -1, gtk.RELIEF_NONE, "", 0, 0, 0, ["All"], [AppStyle] )

	if self.menustyle == True:
		CategoryButton.connect( "enter_notify_event", self.Filter, "All" ) ###### MAKE IT HAVE SOMETHING TO PASS TO FILTER INSTEAD OF NOTHING #####
	else:
        	CategoryButton.connect( "button_press_event", self.Filter, "All" ) ###### MAKE IT HAVE SOMETHING TO PASS TO FILTER INSTEAD OF NOTHING #####

        self.wTree.get_widget( "vbuttonbox2" ).add( CategoryButton )

```

That way then in the filter routine the last bit of statments can look like i mentioned above ...

```

            if showAllAppsBool == True:
		if text == "All":
		    i.show()
		else:
                    if not re.search( text, full_label, re.IGNORECASE ):
                        i.hide()
                    else:
                        i.show()
                if widget != self.wTree.get_widget( "entry1" ):
                    for i in self.wTree.get_widget( "vbuttonbox2" ).get_children():
                        i.set_relief( gtk.RELIEF_NONE )
                    widget.set_relief( gtk.RELIEF_HALF )

```


And the all button when clicked upon will always show all applications (when clicked upon) regardless of if text is in the search box or not.

---

### Post by sweetthdevil on 2007-07-14
a little issue with a fresh install,

I did a fresh install of Feisty, so I straight away re-install USP, but my search box doesn't work, 

I checked the focus on Beryl, it's ok.
Checked the search command, it's ok.
Checked the gconf-editor, seems ok to me.

Any idea? 

Many thanks

---

### Post by Malac on 2007-07-15
> **sweetthdevil said:**
> a little issue with a fresh install,

I did a fresh install of Feisty, so I straight away re-install USP, but my search box doesn't work, 

I checked the focus on Beryl, it's ok.
Checked the search command, it's ok.
Checked the gconf-editor, seems ok to me.

Any idea? 

Many thanks
```
gnome-search-tool --named=SEARCH_STRING --start
```
Should be the standard "Search Command" under Preferences, Applications Tab, check this.

---

### Post by sweetthdevil on 2007-07-15
Yes, that&#347; the search command i've..

But even if i clic on the search box, i can not type anything. 

Many thanks for the quick answer.

---

### Post by Malac on 2007-07-16
> **sweetthdevil said:**
> Yes, that&#347; the search command i've..

But even if i clic on the search box, i can not type anything. 

Many thanks for the quick answer.
Just to be clear about beryl focus stealing you say it is "okay" I'm not sure whether you mean it is as it should be(default) as this *must* be set to "None".

---

### Post by sweetthdevil on 2007-07-16
YEs just found, beryl was the problem, After the re-install i use the save file of beryl setup, so i thought it wouldn't the issue.

ANyway, many thanks for the quick help!

---

### Post by Malac on 2007-07-16
> **sweetthdevil said:**
> YEs just found, beryl was the problem, After the re-install i use the save file of beryl setup, so i thought it wouldn't the issue.

ANyway, many thanks for the quick help!You are welcome, glad I could help . :)

---

