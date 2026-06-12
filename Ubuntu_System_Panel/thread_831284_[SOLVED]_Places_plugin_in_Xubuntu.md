---
title: "[SOLVED] Places plugin in Xubuntu?"
date: 2008-06-16
forum: Ubuntu System Panel
---

### Post by santiagoward2000 on 2008-06-16
HI!
First of all, congrats for this project!! It's great!
Now, I have a question about it. I just installed it on my Xubuntu, but I can't add the Places plugin. I installed it using this guide: [http://xubuntu.wordpress.com/2007/07/12/howto-usp-setup-tips-and-tricks/]("http://xubuntu.wordpress.com/2007/07/12/howto-usp-setup-tips-and-tricks/")
Am I missing something?
Thanks!

---

### Post by santiagoward2000 on 2008-06-17
Oops! I finally figured out what was happening. After adding the plugin, I didn't click on the **Save** button. :oops:
But now I have a new problem. The **Home**, **Computer** and **Network** buttons don't show up. I'm adding a screenshot so you can see the problem.
Am I doing something wrong?
Thanks!!

---

### Post by tier on 2008-06-17
I think that the problem in the icon theme. Try standart "gnome" icon theme.

---

### Post by santiagoward2000 on 2008-06-17
> **tier said:**
> I think that the problem in the icon theme. Try standart "gnome" icon theme.

Thanks for the reply. I just tried that, but it didn't fixed the problem :(
I tried changing the GTK theme too, just in case, but it didn't helped.

---

### Post by tier on 2008-06-17
I look at the code. Icons are taken from /usr/share/applications/nautilus-home.desktop, /usr/share/applications/nautilus-computer.desktop, /usr/share/applications/network-scheme.desktop files. You can install nautilus or copy attached file in /usr/lib/python2.4/site-packages/usp/plugins/ (from root, of course):
extract places.py from archive and ```
sudo cp places.py /usr/lib/python2.4/site-packages/usp/plugins/
```
But I remove "Computer" and "Network" items (because I don't think that thunar understand "computer:///" and "network:///" paths).

---

### Post by santiagoward2000 on 2008-06-17
THANKS! That did it! :)
Now, there's one other small thing. My gtk-bookmarks don't show up unless I load the Xfce places plugin. Can you help me with that??
Thank you!

---

### Post by santiagoward2000 on 2008-06-17
I guess I just had to reload it, because now they bookmarks are there!
Thanks for your patience!

---

### Post by tier on 2008-06-17
> **santiagoward2000 said:**
> THANKS! That did it! :)
Now, there's one other small thing. My gtk-bookmarks don't show up unless I load the Xfce places plugin. Can you help me with that??
Thank you!

I'm glad to help you. But I don't understand "unless I load the Xfce places plugin" :) I don't use xfce very long time.

---

### Post by santiagoward2000 on 2008-06-17
> **tier said:**
> I'm glad to help you. But I don't understand "unless I load the Xfce places plugin" :) I don't use xfce very long time.

Well, a "Places" plugin was added to xfce's panel sometime ago. It's like Gnome's places menu, but it's a separate plugin. When I added USP using xfapplet, I removed that plugin. But when I opened USP, the bookmarks menu was empty. So I added the plugin again and they appeared. So I thought I had to have both USP and the Places menu on my panel. But then I removed the Places menu again and the bookmarks stayed there, so I guess I just had to reload them.
Thanks!

---

### Post by santiagoward2000 on 2008-06-17
My Bookmarks disappeared again! :(
Does anyone know how to use them with USP in Xubuntu?

---

### Post by santiagoward2000 on 2008-06-17
Well, I tried linking the file **~/.usp/places/.gtk-bookmarks** with the **~/.gtk-bookmarks** file. And it seems to be working! :)

---

### Post by tier on 2008-06-18
Yes, usp takes bookmarks from ~/.gtk-bookmarks file. I don't have ~/.usp/places/.gtk-bookmarks file :)

---

### Post by santiagoward2000 on 2008-06-18
> **tier said:**
> Yes, usp takes bookmarks from ~/.gtk-bookmarks file. I don't have ~/.usp/places/.gtk-bookmarks file :)

I do (because I had to create one according to the guide I used), but it wasn't linked to the original .gtk-bookmarks file. I guess there was my problem.

---

### Post by Malac on 2008-06-20
Sorry, I've been away on holiday for a week so I haven't seen this until now.
I'm glad this has been solved.

Any further problems I will try to tackle, although I only have minimal knowledge of XFCE/Xubuntu.

Many Thanks to tier for dealing with these problems.

---

### Post by santiagoward2000 on 2008-06-25
> **Malac said:**
> Sorry, I've been away on holiday for a week so I haven't seen this until now.
I'm glad this has been solved.

Any further problems I will try to tackle, although I only have minimal knowledge of XFCE/Xubuntu.

Many Thanks to tier for dealing with these problems.

Don't worry about it. Tier did a great job! :)
How were those holidays?

---

### Post by Malac on 2008-06-25
> **santiagoward2000 said:**
> How were those holidays?
Great thanks, went camping and walking in the Kielder National Park, very beautiful and great fun with my partner and the two dogs.

---

### Post by santiagoward2000 on 2008-10-23
Hi!
Sorry for reviving this thread, but I installed USP on a new computer with Xubuntu, and I'm having problems getting the Places plugin working again. I already copied tier's script, but the panel is empty, I mean, there's the drop-down menu places/bookmarks, and a completely white box underneath, no matter which I choose.
Another thing, since I copied the script, the **Places** tab in uspconfig changed to **Warnings**, and in it it says:
> Plugins without Config Section, With Coding Errors Or Not Found:
places
Thanks!

---

### Post by Malac on 2008-10-23
> **santiagoward2000 said:**
> Hi!
Sorry for reviving this thread, but I installed USP on a new computer with Xubuntu, and I'm having problems getting the Places plugin working again. I already copied tier's script, but the panel is empty, I mean, there's the drop-down menu places/bookmarks, and a completely white box underneath, no matter which I choose.
Another thing, since I copied the script, the **Places** tab in uspconfig changed to **Warnings**, and in it it says:

Thanks!
Hi santi,
I haven't looked at the xubuntu install for ages but I will try to get on it this weekend.
I'm snowed under with work at the mo'.
Which install method did you use i.e. is it from SVN or one of the .deb packages?
tiers places.py replacement may not work now as places has undergone a few changes.
I've attached a new copy which should work with latest SVN.
If this doesn't work it's probably another dependency issue.

---

### Post by santiagoward2000 on 2008-10-23
> **Malac said:**
> Hi santi,
I haven't looked at the xubuntu install for ages but I will try to get on it this weekend.
I'm snowed under with work at the mo'.
Which install method did you use i.e. is it from SVN or one of the .deb packages?
tiers places.py replacement may not work now as places has undergone a few changes.
I've attached a new copy which should work with latest SVN.
If this doesn't work it's probably another dependency issue.

It's working now! :) Just in case, I've installed it from SVN.
Thank you! And good luck with all the work!

---

### Post by Malac on 2008-10-24
> **santiagoward2000 said:**
> It's working now! :) Just in case, I've installed it from SVN.
Thank you! And good luck with all the work!
Glad it's sorted and Thanks. :)
I'll give the xubuntu install the once over anyway as I'm trying to get usp on launchpad (having a bit of trouble with files in source) so I can release .deb's for different versions, 32 and 64 bit, and possibly a specific xubuntu/xfce package, and then people can just install through regular apt,synaptic,etc...

---

### Post by santiagoward2000 on 2008-10-24
> **Malac said:**
> Glad it's sorted and Thanks. :)
I'll give the xubuntu install the once over anyway as I'm trying to get usp on launchpad (having a bit of trouble with files in source) so I can release .deb's for different versions, 32 and 64 bit, and possibly a specific xubuntu/xfce package, and then people can just install through regular apt,synaptic,etc...

That'd be cool! :) I hope you can do it sometime soon!

---

### Post by santiagoward2000 on 2008-11-12
Hi!
Sorry for being such a nuisance, but the patch no longer works with the lastest SVN revision, and when I add it, it breaks the applications plugin too (it appears empty).
Sorry again, and thanks in advance!

---

### Post by Malac on 2008-11-12
> **santiagoward2000 said:**
> Hi!
Sorry for being such a nuisance, but the patch no longer works with the lastest SVN revision, and when I add it, it breaks the applications plugin too (it appears empty).
Sorry again, and thanks in advance!
Hi again ;)
Can't see how it would have effected the applications plugin.
Sorry to ask, but have you rebooted since updating?
Have you tried "_R_eload Plugins" from the Right-Click Menu?
Can you post the output of ```
usp run-in-window
``` from a terminal please. Thanks.

I've added a new places.py to this post to try also.

In the meantime you can checkout an old version using this command in the initial folder you installed usp to.
```
svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ **-r 999** [COLOR=SeaGreen]*<folder-you-installed-to>*[/COLOR]
``` where **999** is the previous working revision number.

---

### Post by santiagoward2000 on 2008-11-12
> **Malac said:**
> Hi again ;)
Can't see how it would have effected the applications plugin.
Sorry to ask, but have you rebooted since updating?
Have you tried "_R_eload Plugins" from the Right-Click Menu?
Can you post the output of ```
usp run-in-window
``` from a terminal please. Thanks.

I'd love to, but luckily, it suddenly started working. I've got no idea about what happened. I had reloaded the plugin, and even rebooted the system before making the post. But when i used the **usp run-in-window** command, I got no errors and USP was working fine. I readded it to the panel (because I had replaced it for the Xfce menu) and it was working.
Sorry about it! And thank you for the trouble! :)

---

### Post by Malac on 2008-11-12
> **santiagoward2000 said:**
> Sorry about it! And thank you for the trouble! :)No problem. :D

---

### Post by santiagoward2000 on 2008-11-12
Just FYI, I tried the new patch and it works fine, although I don't know what's the difference... :)
THANKS!

---

### Post by Malac on 2008-11-12
> **santiagoward2000 said:**
> Just FYI, I tried the new patch and it works fine, although I don't know what's the difference... :)
THANKS!
Just some code layout tidying to the spaces and tabs on that one.

---

### Post by santiagoward2000 on 2008-11-12
OK, for some reason it stopped working again after I turned my laptop off (although now I'm not sure if it's related to the patch). Here's the **usp run-in-window** output: ```
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
places: loaded successfully
shortcuts: loaded successfully
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
recent: loaded successfully
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
Static User Image Used
Static User Image Used
Traceback (most recent call last):
  File "/usr/bin/usp", line 1042, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1027, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 732, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 72, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 476, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 559, in do_plugin
    self.do_standard_places()
  File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 240, in do_standard_places
    Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, PlaceData[3], self.iconsize, 48, -1, [PlaceData[0]], [[pango.AttrSize( self.fontsize*1000, 0, -1 )]] )
IndexError: list index out of range

```
Thanks!

---

### Post by Malac on 2008-11-13
> **santiagoward2000 said:**
> ```
File "/usr/lib/python2.4/site-packages/usp/plugins/places.py", line 240, in do_standard_places
    Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, PlaceData[3], self.iconsize, 48, -1, [PlaceData[0]], [[pango.AttrSize( self.fontsize*1000, 0, -1 )]] )
IndexError: list index out of range

```Thanks!Can you check the line in bold 240 to check that it reads the same as this one, including commas and ' ' marks. Thanks.
```
    def do_standard_places( self ):

        #PlaceData = ParseDesktopFile( "/usr/share/applications/nautilus-home.desktop" )
        **PlaceData = ['Home Folder', 'Open your personal folder', 'thunar', 'gnome-fs-home']**
        Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, PlaceData[3], self.iconsize, 48, -1, [PlaceData[0]], [[pango.AttrSize( self.fontsize*1000, 0, -1 )]] )

```

---

### Post by santiagoward2000 on 2008-11-15
> **Malac said:**
> Can you check the line in bold 240 to check that it reads the same as this one, including commas and ' ' marks. Thanks.


Well, aparently there's a problem there. I can't find that line. Line 240 in my **places.py** file says:
```
	def do_standard_places( self ):

		PlaceData = ParseDesktopFile( "/usr/share/applications/nautilus-home.desktop" )
		Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, PlaceData[3], self.iconsize, 48, -1, [PlaceData[0]], [[pango.AttrSize( self.fontsize*1000, 0, -1 )]] )
		Button1.connect( "button_press_event", self.ButtonClicked, self.home )
		Button1.connect( "key_press_event", self.ButtonPressed, self.home )
		Button1.connect( "button_release_event", self.ButtonReleased )
```
This is from the lastest patch you've uploded.
Thanks!

---

### Post by Malac on 2008-11-15
> **santiagoward2000 said:**
> Well, aparently there's a problem there. I can't find that line. Line 240 in my **places.py** file says:
```
    def do_standard_places( self ):

        PlaceData = ParseDesktopFile( "/usr/share/applications/nautilus-home.desktop" )
        Button1 = MakeAButton( 160, -1, gtk.RELIEF_NONE, PlaceData[3], self.iconsize, 48, -1, [PlaceData[0]], [[pango.AttrSize( self.fontsize*1000, 0, -1 )]] )
        Button1.connect( "button_press_event", self.ButtonClicked, self.home )
        Button1.connect( "key_press_event", self.ButtonPressed, self.home )
        Button1.connect( "button_release_event", self.ButtonReleased )
```This is from the lastest patch you've uploded.
Thanks!
Okay you need to replace the line that has ParseDesktopFile(", etc
with the line in bold in my previous post.
**PlaceData = ['Home Folder', 'Open your personal folder', 'thunar', 'gnome-fs-home']**
Sorry about that I did the second patch in a rush and that's what happens. :)
I'll try and get to a proper patch for this this weekend that works if places is on xubuntu.

---

### Post by santiagoward2000 on 2008-11-15
> **Malac said:**
> Okay you need to replace the line that has ParseDesktopFile(", etc
with the line in bold in my previous post.
**PlaceData = ['Home Folder', 'Open your personal folder', 'thunar', 'gnome-fs-home']**
Sorry about that I did the second patch in a rush and that's what happens. :)
I'll try and get to a proper patch for this this weekend that works if places is on xubuntu.

Thanks!
I'll try that later. Right now I'm using the previous one and (at the moment) it's working fine. I'll try the new one tonight.

---

### Post by Malac on 2008-11-16
Okay I've updated the SVN with a new version of places.py with comments on which section needs altering for xubuntu installs. Rev # 372
This is a temporary fix for now until I can get the deb packages sorted and on launchpad.

---

### Post by santiagoward2000 on 2008-11-19
> **Malac said:**
> Okay I've updated the SVN with a new version of places.py with comments on which section needs altering for xubuntu installs. Rev # 372
This is a temporary fix for now until I can get the deb packages sorted and on launchpad.

HI!
I just updated my USP version (I've been a little busy lately) and commented/uncommented the lines marked in the Places.py file; and everything is working fine.
THANKS!!

---

### Post by Malac on 2008-11-20
> **santiagoward2000 said:**
> HI!
I just updated my USP version (I've been a little busy lately) and commented/uncommented the lines marked in the Places.py file; and everything is working fine.
THANKS!!You're Welcome.

---

### Post by santiagoward2000 on 2008-11-29
> **Malac said:**
> I'll give the xubuntu install the once over anyway as I'm trying to get usp on launchpad (having a bit of trouble with files in source) so I can release .deb's for different versions, 32 and 64 bit, and possibly a specific xubuntu/xfce package, and then people can just install through regular apt,synaptic,etc...

_A little OT:_
OK, if you're planning a Xubuntu specific version, there's a small thing with the **execute.py**. By default, when trying to run an app in a terminal, it tries to open:
```
/usr/bin/gnome-terminal
```
I changed that to:
```
/usr/bin/xfce4-terminal
```
on the **execute.py** file and it's working fine, both when I check the "Run in Terminal" on my favorite applications list, or when using the $ symbol on the search line.
Another function that doesn't work on Xfce is the "Add to Panel" on the Applications plugin. This one I have no idea if it can be done, because Xfce doesn't store the .desktop file for the panel launchers, but a **launchers-(somenumber).rc** file.

---

### Post by Malac on 2008-11-30
Thanks for the info santi it will be useful but at the moment I am having problems getting the normal usp deb's on launchpad. I can build working deb's myself but you can't upload these to launchpad it seems.

I've followed the howto's on this forum and on launchpad's site to upload source files but the "build" keeps failing even though it's python so shouldn't need building.

I'm obviously missing something somewhere but at the moment I haven't the time to sit down and spend a long time on usp in one go to get all the stuff sorted out that needs doing.

As to your other post I would like a right click menu with a remove option on the compact list rather than have to go into Preferences everytime you want to remove one.
I'll add it to my list :)
I'm currently working on the duplicate plugins issue.

---

### Post by santiagoward2000 on 2008-11-30
> **Malac said:**
> Thanks for the info santi it will be useful but at the moment I am having problems getting the normal usp deb's on launchpad. I can build working deb's myself but you can't upload these to launchpad it seems.

Sure! I just wanted to mention it before you started working on the Xubuntu specific package.

> **Malac said:**
> As to your other post I would like a right click menu with a remove option on the compact list rather than have to go into Preferences everytime you want to remove one.
I'll add it to my list :)

That'll be great! :)

> **Malac said:**
> I'm currently working on the duplicate plugins issue.

Thanks for the hard work!! :)
And good luck with the Launchpad problem!

---

### Post by santiagoward2000 on 2009-02-10
Hi there! Here I am again...
I just got the lastest version working on my Xubuntu Intrepid. I see you've separated the **End Session** and **Quit** buttons, as Ubuntu did on Intrepid. The thing is that on Xubuntu, they're still on the same menu. Is there any way I could make it work like it does on Hardy?
Thanks!

---

### Post by Malac on 2009-02-11
> **santiagoward2000 said:**
> Hi there! Here I am again...
I just got the lastest version working on my Xubuntu Intrepid. I see you've separated the **End Session** and **Quit** buttons, as Ubuntu did on Intrepid. The thing is that on Xubuntu, they're still on the same menu. Is there any way I could make it work like it does on Hardy?
Thanks!
I haven't checked Xubuntu yet sorry.
This is another reason I need to get .deb packages done for the different deployments.
**Anyone out there who has managed to get a python program onto launchpad to compile to .deb who wants to lend me a hand fewel free to pm me.**

To your problem.
Edit /usr/lib/python2.4/site-packages/usp/plugins/system_management.py
Go to Line 149 and change it to this:
```
if 1.00 <= 8.04: # Check Version as Shutdown Changed after Hardy
```
As 1.00 is always less than 8.04 it should always use the old method.

Hope this helps.

---

### Post by santiagoward2000 on 2009-02-11
> **Malac said:**
> Edit /usr/lib/python2.4/site-packages/usp/plugins/system_management.py
Go to Line 149 and change it to this:
```
if 1.00 <= 8.04: # Check Version as Shutdown Changed after Hardy
```
As 1.00 is always less than 8.04 it should always use the old method.

Hope this helps.

Thanks! That did it!
However, on uspconfig I still have both **Logout** and **Shutdown** options. Are they supposed to stay there?

---

### Post by Malac on 2009-02-12
> **santiagoward2000 said:**
> Thanks! That did it!
However, on uspconfig I still have both **Logout** and **Shutdown** options. Are they supposed to stay there?
Sorry, you will have to do the same thing at line 230 as before in system_management.py.

Hope this helps.

---

### Post by santiagoward2000 on 2009-02-12
> **Malac said:**
> Sorry, you will have to do the same thing at line 230 as before in system_management.py.

Hope this helps.

It did! Thanks! :)

---

