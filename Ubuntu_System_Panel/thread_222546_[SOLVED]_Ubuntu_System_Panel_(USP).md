---
title: "[SOLVED] Ubuntu System Panel (USP)"
date: 2006-07-25
forum: Ubuntu System Panel
---

### Post by chanders on 2006-07-25
After the release of the SLED menu and seeing that it was so popular with Ubuntu users, I took it upon myself to do something of our own. So for the past few weeks I have been studying mockups for GNOME and trying to bring it alive and today, I offer it to you...

Bear in mind that this is alpha software and there are bugs, either because I didn't come across them before or because I cannot solve them myself. That being said this system panel offers (at least to me) a convenient place to do everything I need to do, with efficiency...

Ver 0.31
Wed, 02 Aug 2006 05:30:10 -0400
* 'Places' and 'Application' icon size configurable (size 1-4)
* USP returns to 'Favourites' after close if show_allapps_on start is not set
* 'All Application' sub-section is now highlighted
* Applet text and icon is now configurable
* Fixed 'Filter' bug
* Fixed Alt-F4 bug
* BASIC translation for 'All Applications' section (thanks vonpmg)

Other features are already in the pipeline...stay tuned

Notes:
See 'currently working on' thread to know what is in the pipeline
Add your wishlist to the 'What I would like to see' thread
Add screenshots to 'Screenshots' thread

Features
* Supports drag and drop
* USP is pin-able to allow you to drag items from the original ubuntu menu
* Show only the pane, you want to see
* Filter applications/places
* Search computer
* 'All Applications' pane showing all applications as icons
* Configure frequently used items directly from USP
* Right click to edit labels directly in Applications/Places panes
* Fully configurable search, more-applications and system items
* Fast
* Supports 'Plugins' if developers are willing to write them

Notes
* Configuration can be done via gconf-editor in '/apps/usp'
* To pin USP, click on the small toggle button in the uppermost left of the panel. Pressed=pinned, unpressed=normal
* Depending on your theme, the colours may look off (not my fault!) Open gconf-editor and check 'Use custom colors' and enter the colour you would like to use. the default is a nice gray
* Change network_interface to your network interface such as eth0 or wlan0 etc.
* To use beagle instead of nautilus search change search_command to  'beagle-search SEARCH_STRING'
* To use the application browser that came with sled edit more_applications to show 'application-browser'
* Each system_command maps to the system buttons in the USP
* Translation will not be available until this app reaches production quality

Quick-Start
1.) Install .deb attached
2.) Right click on panel and add 'Ubuntu System Panel' located in Miscellaneous (next to SLED if you have it installed)
3.) Click on the applet (the USP will open)
4.) Click on the pin button (Uppermost left tiny button)
5.) Drag applications from your ubuntu menu onto the USP
6.) Drag places onto the places pane
7.) Right click on items to edit labels and their launcher
8.) If you dont like the colors, open gconf-editor and check 'use custom color (This requires a restart of the applet by removing and re-adding)
9.) Un select the pin button
10.) Select the panes you want to see by toggling the buttons on the left

And now for the screenshots

Here is the full USP
[IMG]http://img239.imageshack.us/img239/254/uspiv2.jpg[/IMG]

Only the applications pane showing
[IMG]http://img105.imageshack.us/img105/2932/applicationsvm6.jpg[/IMG]

User selected combination
[IMG]http://img147.imageshack.us/img147/443/combinationni3.jpg[/IMG]

Here is the .deb. I take no responsibility if your dog elopes with your cat or your goldfish commits suicide by going for a walk.. I hope you like it, a lot of work went into it. Please comment and feel free to request features (not sure I will be able to fulfil them all but its worth a shot ;) )

Get it [here]("http://www.ubuntuforums.org/showthread.php?t=229014")

---

### Post by darkmatter on 2006-07-25
Excellent work chanders, job well done :)

I await the next addition to your arsenal of toys :p

---

### Post by it.henrik on 2006-07-25
This looks cool. Will try it right away :)

---

### Post by swamytk on 2006-07-25
Great man! Cool and more **professionalism**!!!

---

### Post by darkmatter on 2006-07-25
Hmmm... schema??? no schema installs here so it makes the System Panel dead weight...

Sources?? ;)

---

### Post by lazyd2 on 2006-07-25
It will not run. Can't be added to the panel...

---

### Post by chanders on 2006-07-25
run this in a terminal and post your results... This is my first panel applet so I guess hickups are in order ](*,) 

usp run-in-window

---

### Post by chanders on 2006-07-25
> **darkmatter said:**
> Hmmm... schema??? no schema installs here so it makes the System Panel dead weight...

Sources?? ;)

When it is run it creates the schema directory structure on the fly.... Open the deb with archive-manager. The source is in the /usr/bin file named usp ;)

---

### Post by lazyd2 on 2006-07-25
> **chanders said:**
> run this in a terminal and post your results... This is my first panel applet so I guess hickups are in order ](*,) 

usp run-in-window

```
Traceback (most recent call last):
  File "/usr/bin/usp", line 1242, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1233, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1116, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 88, in __init__
    self.get_gconf_info()
  File "/usr/bin/usp", line 1017, in get_gconf_info
    self.wTree.get_widget("label9").set_label(resolution+" px")
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'

```

---

### Post by augied on 2006-07-25
This is great, thanks!
Is there any way to use the same places as nautilus does?

---

### Post by chanders on 2006-07-25
> **augied said:**
> This is great, thanks!
Is there any way to use the same places as nautilus does?

Did this install properly for you?

---

### Post by augied on 2006-07-25
> **chanders said:**
> Did this install properly for you?
Yes

---

### Post by chanders on 2006-07-25
> **lazyd2 said:**
> ```
Traceback (most recent call last):
  File "/usr/bin/usp", line 1242, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1233, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1116, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 88, in __init__
    self.get_gconf_info()
  File "/usr/bin/usp", line 1017, in get_gconf_info
    self.wTree.get_widget("label9").set_label(resolution+" px")
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'

```

Seems your gconf is different from mine.... standby for a fix

---

### Post by DeeZiD on 2006-07-25
Hi, nice looking menu :D
I'll try it this evening after work.

And, what I want to let you know is, that I'll put a few mockups this evening from the xorg configuration tool this evening on this page ;)


regards Dennis

---

### Post by chanders on 2006-07-25
New fix!

Open system monitor and make sure you dont have 

python /usr/bin/usp ..... running

If you do, kill the process and _do not reload the applet_ when prompted.... 
Then install the newer deb (0.11). 

Let me know if it works..

---

### Post by chanders on 2006-07-25
> **DeeZiD said:**
> Hi, nice looking menu :D
I'll try it this evening after work.

And, what I want to let you know is, that I'll put a few mockups this evening from the xorg configuration tool this evening on this page ;)


regards Dennis

Excellent! Looking forward to it... I just saw a post about something similar... we will have to look at that too...

---

### Post by outdooricon on 2006-07-25
Wow, Impressive screeshots. Does this need to be done in edgy or can I try it out in dapper?

---

### Post by chanders on 2006-07-25
> **outdooricon said:**
> Wow, Impressive screeshots. Does this need to be done in edgy or can I try it out in dapper?

Indulge yourself ;)  Dapper or Edgy welcome!

---

### Post by Viper550 on 2006-07-25
OH NOES! You just trumped my slab...but due to the amount of (possible) bugs, and the fact that it looks a bit too complex for the average user, I think people won't be intimidated by Uslab as much as THIS complex thing.

---

### Post by chanders on 2006-07-25
> **Viper550 said:**
> OH NOES! You just trumped my slab...can I have the source code so I can mod it further for the next version of Uslab?

LOL, you'll never give up, will you 8)   The source is distributed in the .deb. Open with package manager and look in /usr/bin filename is usp

Have fun! :-D

---

### Post by chanders on 2006-07-25
> **Viper550 said:**
> OH NOES! You just trumped my slab...but due to the amount of (possible) bugs, and the fact that it looks a bit too complex for the average user, I think people won't be intimidated by Uslab as much as THIS complex thing.

*Possible *bugs? Are you for real? You _[SIZE="4"]DEFINITELY[/SIZE]_ need to read my sig!

---

### Post by Note360 on 2006-07-25
I can't get this working. I installed from the .deb (thanks for supporting PPC) and rebooted whent to add panel and moved it over to the panel and it did nothing. Good job from the looks of it though

---

### Post by Squalor on 2006-07-25
Are you going to attach the .po file(s)? I'd love to translate this. :)

---

### Post by chanders on 2006-07-25
oops :-#  double post

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> I can't get this working. I installed from the .deb (thanks for supporting PPC) and rebooted whent to add panel and moved it over to the panel and it did nothing. Good job from the looks of it though

run this in a terminal and post your results... 

usp run-in-window

I will try to help...

@Squalor - it's way too early to do any translation but when I am ready I will pm you ;)

---

### Post by Note360 on 2006-07-25
Here is what I got. Thanks for the fas service to.

```

/usr/bin/usp:483: GtkWarning: Attempting to add a widget with type GtkImage to a container of type GtkHBox, but the widget is already inside a container of type GtkHBox, the GTK+ FAQ at http://www.gtk.org/faq/ explains how to reparent a widget.
  HBox1.add(PlaceIcon)
Warning! - Icon for item not found!
Traceback (most recent call last):
  File "/usr/bin/usp", line 1249, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1240, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1123, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 92, in __init__
    self.Todos()
  File "/usr/bin/usp", line 457, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 415, in get_proper_icon
    Image1 = gtk.image_new_from_icon_name(None, icon_size)
TypeError: image_new_from_icon_name() argument 1 must be string, not None

```

---

### Post by darkmatter on 2006-07-25
All in all its quite nice chanders... save for one smallish usability issue.

And that would be regarding the 'All Applications' 'menu'... 

Having such small icons and no text is a bit of a hinderance... it is my suggestion to perhaps replace the current view with an embedded list... or better yet, a treeview... so by clicking on the All Applications.. it would then display a list of categories (Accessories, Games... blah blah) and clicking on each would extend the category, displaying the apps within. And it would have text!!!! :p

*Disclaimer*: The preceeding has been a random thought, and the author takes no resonsibility for any damage it may cause :mrgreen:

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Here is what I got. Thanks for the fas service to.

```

/usr/bin/usp:483: GtkWarning: Attempting to add a widget with type GtkImage to a container of type GtkHBox, but the widget is already inside a container of type GtkHBox, the GTK+ FAQ at http://www.gtk.org/faq/ explains how to reparent a widget.
  HBox1.add(PlaceIcon)
Warning! - Icon for item not found!
Traceback (most recent call last):
  File "/usr/bin/usp", line 1249, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1240, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1123, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 92, in __init__
    self.Todos()
  File "/usr/bin/usp", line 457, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 415, in get_proper_icon
    Image1 = gtk.image_new_from_icon_name(None, icon_size)
TypeError: image_new_from_icon_name() argument 1 must be string, not None

```

I know how to solve this. It's just I havent slept for 36hrs trying to get this ready so I am going to take a nap and when I wake up later it will be solved... have no fear ;)

---

### Post by chanders on 2006-07-25
> **darkmatter said:**
> All in all its quite nice chanders... save for one smallish usability issue.

And that would be regarding the 'All Applications' 'menu'... 

Having such small icons and no text is a bit of a hinderance... it is my suggestion to perhaps replace the current view with an embedded list... or better yet, a treeview... so by clicking on the All Applications.. it would then display a list of categories (Accessories, Games... blah blah) and clicking on each would extend the category, displaying the apps within. And it would have text!!!! :p

*Disclaimer*: The preceeding has been a random thought, and the author takes no resonsibility for any damage it may cause :mrgreen:


In the next release, (few hours) the user will have the option to see all the applications as a list, a-la SLED also, hopefully categorised...

That was just a last minute 'feature' ;)

---

### Post by chanders on 2006-07-25
Standby for a fix.... for the problem, before I sleep....

---

### Post by jarsonic on 2006-07-25
Chanders.  We can wait.  Get some sleep  :)

---

### Post by Viper550 on 2006-07-25
> **Note360 said:**
> I can't get this working. I installed from the .deb (thanks for supporting PPC) and rebooted whent to add panel and moved it over to the panel and it did nothing. Good job from the looks of it though

> **Note360 said:**
> Here is what I got. Thanks for the fas service to.

```

/usr/bin/usp:483: GtkWarning: Attempting to add a widget with type GtkImage to a container of type GtkHBox, but the widget is already inside a container of type GtkHBox, the GTK+ FAQ at http://www.gtk.org/faq/ explains how to reparent a widget.
  HBox1.add(PlaceIcon)
Warning! - Icon for item not found!
Traceback (most recent call last):
  File "/usr/bin/usp", line 1249, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1240, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1123, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 92, in __init__
    self.Todos()
  File "/usr/bin/usp", line 457, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 415, in get_proper_icon
    Image1 = gtk.image_new_from_icon_name(None, icon_size)
TypeError: image_new_from_icon_name() argument 1 must be string, not None

```

See, dissatified customers! And, let me rephrase what I said: USlab is easy enough, but this seems more like a Power-User version of USlab. If it were to be included ALONGSIDE USlab, that's fine with me!

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Here is what I got. Thanks for the fas service to.

```

/usr/bin/usp:483: GtkWarning: Attempting to add a widget with type GtkImage to a container of type GtkHBox, but the widget is already inside a container of type GtkHBox, the GTK+ FAQ at http://www.gtk.org/faq/ explains how to reparent a widget.
  HBox1.add(PlaceIcon)
Warning! - Icon for item not found!
Traceback (most recent call last):
  File "/usr/bin/usp", line 1249, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1240, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1123, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 92, in __init__
    self.Todos()
  File "/usr/bin/usp", line 457, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 415, in get_proper_icon
    Image1 = gtk.image_new_from_icon_name(None, icon_size)
TypeError: image_new_from_icon_name() argument 1 must be string, not None

```


Anyone with this error, try the new .deb (.12) and let me know if it works.. 

Install the deb (.12) and then logout and then log back in...

---

### Post by handy on 2006-07-25
USP installed fine on my system.

The **Control Center** does nothing when I click on it though.

I'm running 1600x1200 screen res', with all my fonts set at 22, to keep my old eyes from having to strain. 
 
I had to set the font size down to about 12 for the written word to fit in USP, if you know what I mean.  

Is there an easy solution to this.  This problem does happen with other softwares occasionaly too.

Due to the fact that I set my computer display differently than the vast majority, I bring a problem or 2 upon myself...

I've learnt to live with it, sometime I won't use the software due to fonts not fitting properly, occasionaly I temporarily change my screen res'!

As far as USP is concerned, I won't be able to use it, due to the font size problem. :( 

So, I do hope that there is a simple fix, it could be something simple that I don't know about yet in Ubuntu settings...  I hope so!


Anyway, I think you have done a great job, & many people will be delighted with your work! :KS

---

### Post by handy on 2006-07-25
While I was composing my previous post, there were a few more posted, that I've just read...

I agree with them, get some sleep, it's such a nice thing to do... :)

---

### Post by chanders on 2006-07-25
> **handy said:**
> USP installed fine on my system.

The **Control Center** does nothing when I click on it though.

I'm running 1600x1200 screen res', with all my fonts set at 22, to keep my old eyes from having to strain. 
 
I had to set the font size down to about 12 for the written word to fit in USP, if you know what I mean.  

Is there an easy solution to this.  This problem does happen with other softwares occasionaly too.

Due to the fact that I set my computer display differently than the vast majority, I bring a problem or 2 upon myself...

I've learnt to live with it, sometime I won't use the software due to fonts not fitting properly, occasionaly I temporarily change my screen res'!

As far as USP is concerned, I won't be able to use it, due to the font size problem. :( 

So, I do hope that there is a simple fix, it could be something simple that I don't know about yet in Ubuntu settings...  I hope so!


Anyway, I think you have done a great job, & many people will be delighted with your work! :KS

Control center does not work because you dont have my Ubuntu Control Center installed :D  You can download it in the other thread or you can just change then control center item in gconf-editor to 'gnome-control-center' or 'control-center' (if you have SLED installed)

As for the fonts, I might be able to create a 'large fonts' version... I will see what I can do. I know my friend **Viper550** did some hacking to get the fonts bigger in USLED so maybe you can use that if it will suite you better...

Anything else, let me know ok?

---

### Post by nicky.7 on 2006-07-25
Running from a terminal  usp run-in-window i get this error:

/usr/bin/usp:483: GtkWarning: Attempting to add a widget with type GtkImage to a container of type GtkHBox, but the widget is already inside a container of type GtkHBox, the GTK+ FAQ at [http://www.gtk.org/faq/](http://www.gtk.org/faq/) explains how to reparent a widget.
  HBox1.add(PlaceIcon)
Traceback (most recent call last):
  File "/usr/bin/usp", line 1249, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1240, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1123, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 92, in __init__
    self.Todos()
  File "/usr/bin/usp", line 439, in Todos
    openfile = open(self.get_file_path(path), 'r')
IOError: [Errno 13] Permesso negato: '/usr/share/applications/net-gsambad.desktop'

If I run the same command with sudo it starts but i see a lot of glitches..

PS:You're doing a really good job man!!!!

---

### Post by chanders on 2006-07-25
> **nicky.7 said:**
> Running from a terminal  usp run-in-window i get this error:

/usr/bin/usp:483: GtkWarning: Attempting to add a widget with type GtkImage to a container of type GtkHBox, but the widget is already inside a container of type GtkHBox, the GTK+ FAQ at [http://www.gtk.org/faq/](http://www.gtk.org/faq/) explains how to reparent a widget.
  HBox1.add(PlaceIcon)
Traceback (most recent call last):
  File "/usr/bin/usp", line 1249, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1240, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1123, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 92, in __init__
    self.Todos()
  File "/usr/bin/usp", line 439, in Todos
    openfile = open(self.get_file_path(path), 'r')
IOError: [Errno 13] Permesso negato: '/usr/share/applications/net-gsambad.desktop'

If I run the same command with sudo it starts but i see a lot of glitches..

PS:You're doing a really good job man!!!!


It seems that you do not have permission to read this file - '/usr/share/applications/net-gsambad.desktop' 

Open up /usr/share/applications as root and right click on the file, go to permission and make sure 'read' is checked for 
'owner', 'group' and 'others'.... 

repeat for all files that you have this error for...

Let me know if it works....

I will fix this in the next release....

---

### Post by nicky.7 on 2006-07-25
It works now! Thanks a lot.
Some suggestion for you. Copy something from sled menu!
- Border
- Application browser with favourite apps in the main menu.

---

### Post by JoWilly on 2006-07-25
Great stuff ! Installed on edgy64.

Problems:

1.Places & Applications: no places/applications are listed (they are listed if I click on "all applications)

2. Settings menu: Icons and title texts are too big (its bigger than the menu width (in system management sub menu its good). Icons in settings should be 1 size smaller, title text should be smaller, it is enough if its in bold. (I'm using 1280x1024)


Suggestions:

1."All applications" sould list all the apps one under the other (icon + text, so we can scroll through the list (better than only the icons).

PS : I have slab working very well.

---

### Post by chanders on 2006-07-25
> **JoWilly said:**
> Great stuff ! Installed on edgy64.

Problems:

1.Places & Applications: no places/applications are listed (they are listed if I click on "all applications)

2. Settings menu: Icons and title texts are too big (its bigger than the menu width (in system management sub menu its good). Icons in settings should be 1 size smaller, title text should be smaller, it is enough if its in bold. (I'm using 1280x1024)


Suggestions:

1."All applications" sould list all the apps one under the other (icon + text, so we can scroll through the list (better than only the icons).

PS : I have slab working very well.


When you say SLAB you mean  NDL SLAB right?

You have to pin the USP and drag items in places and Applications for yourself... It comes blank for you to customize it yourself! ;) 

I will try to make the font size and icon size configurable 

In the next release, 'All Applications' will have an option to view as a list with labels so you can scroll to your heart's content (most likely it will be categorised too)

---

### Post by JoWilly on 2006-07-25
> **chanders said:**
> When you say SLAB you mean  NDL SLAB right?

Yep. Said it was working so you know apps are displayed fine with slab.
> **chanders said:**
> 
You have to pin the USP and drag items in places and Applications for yourself... It comes blank for you to customize it yourself! ;) 

Jeezzz ! Yeah, ... it was the same with slab... sorry for that.
> **chanders said:**
> 
I will try to make the font size and icon size configurable 

In the next release, 'All Applications' will have an option to view as a list with labels so you can scroll to your heart's content (most likely it will be categorised too)

Excellent ! Looking forward to it :)

---

### Post by Note360 on 2006-07-25
> **Viper550 said:**
> See, dissatified customers! And, let me rephrase what I said: USlab is easy enough, but this seems more like a Power-User version of USlab. If it were to be included ALONGSIDE USlab, that's fine with me!
I aint dissatisfied I had worse problems with USlab. I just got it working. All the dependancys and it still looks like crap and hardlye works, and dont forget the right click

---

### Post by Note360 on 2006-07-25
Ok, this is amazing I got it working in the window, but I can't add it to the panel.

---

### Post by Note360 on 2006-07-25
Wow, this is great I just got it working. Good job chanders

---

### Post by outdooricon on 2006-07-25
I won't get to install this app untill tonight... does it match whatever current theme is being used in gnome? If not, that's probably a good feature to plan in..

---

### Post by lazyd2 on 2006-07-25
> **outdooricon said:**
> I won't get to install this app untill tonight... does it match whatever current theme is being used in gnome? If not, that's probably a good feature to plan in..
Yes it does match the current theme

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Wow, this is great I just got it working. Good job chanders

You're welcome... It's amazing how much we can do by being positive... and offering a *helping* hand.... Some people will never learn.... But we shall continue to provide great software...

Thanks again Note360!

---

### Post by lazyd2 on 2006-07-25
One more thing chanders, could the panel button be placed a little bit more to the left(less space between the ubuntu logo and the left edge of the panel)?

---

### Post by chanders on 2006-07-25
> **lazyd2 said:**
> One more thing chanders, could the panel button be placed a little bit more to the left(less space between the ubuntu logo and the left edge of the panel)?

You got it! - Next release...

---

### Post by lazyd2 on 2006-07-25
> **chanders said:**
> You got it! - Next release...
Just to clarify, not only the ubuntu logo but both(logo+"System")

Thank you for your great job:)

---

### Post by Note360 on 2006-07-25
Wow, chanders get some sleep. Don't worry about it I remember the trouble I hade with USlab It was like a week of twiddling around getting things working then I gave up and eventually tried again. Oh and Viper never helped me. It is still buggy but what do you want from a .12 release (what is it super Alpha right now). Last thing you really should get this included into Edgy Eft.

---

### Post by YourDoom123 on 2006-07-25
wow, this menu looks great. i've never really liked the idea of having a single menu, ala windows, but i'm sorely tempted by this one. i'm away from my comp for the next 3 weeks, but once i get back, i'll give it a try, and post my feedback...

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Wow, chanders get some sleep. Don't worry about it I remember the trouble I hade with USlab It was like a week of twiddling around getting things working then I gave up and eventually tried again. Oh and Viper never helped me. It is still buggy but what do you want from a .12 release (what is it super Alpha right now). Last thing you really should get this included into Edgy Eft.

I am so happy to help, I cant sleep LOL, but I am sure I'll crash later... I will make a proposal to see how far it gets... the most frustrating thing is trying to get things done in the app the long way around when I am sure some guru could do it in a few lines.... There are some bugs, I could do with some help to squash...

So - Any pygtk / python developers, please let me know who you are (and you wont mind answering some questions)...



@YourDoom123 - The more the merrier :D

---

### Post by chanders on 2006-07-25
Bugfix!

0.13 now solves the problem of the USP not showing up on the correct desktop sometimes... (thanks to Mat)

Download in the first post...

---

### Post by Note360 on 2006-07-25
Unfortuantly I am not a pythong programmer so I can't help you If I could I would. (I am a perl programmer). You know what we need next somethign to replace SUSE's Gnome-Application-Browser. That is the final piece.

Oh, and as for Viper don't mind him he is trying to copy off of SLED you are doing something much mroe valuble you are reinventing what Suse has to what it should be for Ubuntu.

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Unfortuantly I am not a pythong programmer so I can't help you If I could I would. (I am a perl programmer). You know what we need next somethign to replace SUSE's Gnome-Application-Browser. That is the final piece.

Oh, and as for Viper don't mind him he is trying to copy off of SLED you are doing something much mroe valuble you are reinventing what Suse has to what it should be for Ubuntu.

maybe if I can integrate it properly, we wont need a whole application browser.... will come up with something...

---

### Post by jimmygoon on 2006-07-25
I agree. I don't like the way it handle "all applications" sorry... Otherwise... it looks interesting. I will test more tonight when I am more free

---

### Post by Note360 on 2006-07-25
Hmm, sounds good. Don't know where to start but we probably should do something like that just to finish up the whole "We are better than SLED 10" thing.

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Hmm, sounds good. Don't know where to start but we probably should do something like that just to finish up the whole "We are better than SLED 10" thing.

Yeah, thats the main reason I wrote the app (from scratch I might add ;) ) with bits and pieces from tutorials and sample code I found scattered around the web....

This community just gives you wings (sorry couldnt resist)...

---

### Post by Note360 on 2006-07-25
Ok I am working a a patch that will change the more app viewer to the gnome-application-browser but I need to package that with it or you have to have vipers pre installed. Vipers source is free so I assume we can go through and pickout the application.

Oh and I need help pakcaging it into a .deb file.

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Ok I am working a a patch that will change the more app viewer to the gnome-application-browser but I need to package that with it or you have to have vipers pre installed. Vipers source is free so I assume we can go through and pickout the application.

Oh and I need help pakcaging it into a .deb file.

No patch necessary! Just edit /apps/usp/more_applications in gconf-editor and put your favourite application browser there ;)  

Foresight...

---

### Post by Note360 on 2006-07-25
Lol, thats what I did actually I was just trying to make it the default but couldn't.

Nevermind I don't lnow enough about Python. I thought it would be simple.

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Lol, thats what I did actually I was just trying to make it the default but couldn't.

Nevermind I don't lnow enough about Python. I thought it would be simple.

Yeah, I could have put it as default but not all users have (or even want) the application-browser.....So I opted for something that will work on all machines...

---

### Post by chanders on 2006-07-25
Going to grab some zzzzz's see you all in a few hours.... Have fun playing with the menu and have many questions for me when I get back ;)

---

### Post by lazyd2 on 2006-07-25
Sweet dreams lol

---

### Post by Note360 on 2006-07-25
Good night.
Any way I think that we probably should make our own Application Browser. However as previously stated I don't know python or how to work gtk. (Parrot will be a godsend)

---

### Post by melalcoolique on 2006-07-25
Mayday, I've got a serious problem here...

I'am running Edgy since the repositories are up. However, USP has killed my Gnome session. This happened when I launched "ALL APPLICATIONS" and tried to add "Archive Manager".

Actually, I'am in the failsafe session and I've absolutely no way to get my normal session working. I removed, purge USP and the applet and restarted but with no luck.

I've no clue about my problem except it could be related to D-bus.

I am absolutely zen but I'am affraid this time I'am stuck for real. Bad move. :mrgreen:

---

### Post by Note360 on 2006-07-25
Hm, it's probably edgy.

---

### Post by augied on 2006-07-25
Weird bug.
I drag something into the places or the applications area.  A few minutes later, I see the icon float across the screen and then disappear (like what happens if you try to drag a file in nautilus where it is not allowed.)  If I had dragged multiple icons into the menu, the all float by one by one.

---

### Post by kpolice on 2006-07-25
haha I got the same, icons floating all around.

---

### Post by lazyd2 on 2006-07-25
> **augied said:**
> Weird bug.
I drag something into the places or the applications area.  A few minutes later, I see the icon float across the screen and then disappear (like what happens if you try to drag a file in nautilus where it is not allowed.)  If I had dragged multiple icons into the menu, the all float by one by one.Just log out and login again.

---

### Post by augied on 2006-07-25
Just to clarify, the bookmark/application does show up in the menu.  This just happens about five minutes later.  There is no missing functionality, it's just wierd and I wish it would stop.

---

### Post by augied on 2006-07-25
Feature request/suggestion: Have the places section work with the gtk-bookmarks file.  The syntax of the file is a little different from the places.list file that is currently used, but I don't think it would be too hard to do (that said, I I'm not sure how to do it.)  If someone could work out a way to have the other items in the gnome places menu show up, like the cd and usb drives that automatically appear, that would be great.
Also I'd love to have a recent documents section.

---

### Post by cbudden on 2006-07-25
I am getting nothing in the places section or the application section.  If I press All Apps they show up.

Chanders, your doing some great work here, thanks very much!

---

### Post by _simon_ on 2006-07-25
The places window does not auto populate - you need to drag and drop what you want in there. :)

---

### Post by PsyberOneZero on 2006-07-25
I'm loving the work on this and gControl.

I just had a few suggestions:
1) Be able to add seperators (hlines) not just spaces.
2) Integrate either Deskbar (I think that's python) or atleast a run dialog
3) Add a small border around the box, just a few pixels to set it off the desktop
4)Keep up the great work!

---

### Post by augied on 2006-07-25
> **PsyberOneZero said:**
> 1) Be able to add seperators (hlines) not just spaces.

Crap, I was going to suggest that but I forgot.

---

### Post by sethmahoney on 2006-07-25
I tried the modified slab, and got rid of it within 5 minutes.  This, however, is awesome!  Thanks for the fantastic work!

The only issues I'm having is that there doesn't appear to be enough room in the settings panel, leaving me with a funkity scroll bar on the far right (fortunately the settings panel can be hidden - nice touch!), and that it is labeled "System" rather than "Apps" or something, but that I can get used to.

---

### Post by lazyd2 on 2006-07-25
> **sethmahoney said:**
> I tried the modified slab, and got rid of it within 5 minutes.  This, however, is awesome!  Thanks for the fantastic work!

The only issues I'm having is that there doesn't appear to be enough room in the settings panel, leaving me with a funkity scroll bar on the far right (fortunately the settings panel can be hidden - nice touch!), and that it is labeled "System" rather than "Apps" or something, but that I can get used to.Check posts #103, #104 [here.;)]("http://www.compiz.net/viewtopic.php?id=2112&p=7")

---

### Post by Who on 2006-07-25
Chanders, 

Nice work :D - it was beginning to worry me slightly that we keep playing with Novell toys - who else is innovating... Looks like that question has been answered :)

Are you going to write a spec for this, put it on Lunchpad and mail the devel list? Even if you target Edgy+1 or +2 Launchpad seems to be TUW (the Ubuntu Way)... (if you want to work on the code/don't have any interest in Launchpad (and you ask very nicely :P) I may have time to do some speccing for you)

---

### Post by mattisking on 2006-07-25
I like to use Transparency on my Gnome panels. Is there any way we could get transparency support into this applet? The standard "Menu Bar" works great for this. Also, is there a nice ReadMe that lays out how everything should work? Would you be accepting of ideas and feedback towards this? Also, what language is used? I might enjoy helping out on this. My C is rusty but workable, but I don't know Python at all (wouldn't imagine it would be hard to learn though).

---

### Post by chanders on 2006-07-25
> **augied said:**
> Weird bug.
I drag something into the places or the applications area.  A few minutes later, I see the icon float across the screen and then disappear (like what happens if you try to drag a file in nautilus where it is not allowed.)  If I had dragged multiple icons into the menu, the all float by one by one.

Lol, thos ghost icons are a known issue, I will look into it as soon as the app gets a little more polished..

> **augied said:**
> Feature request/suggestion: Have the places section work with the gtk-bookmarks file.  The syntax of the file is a little different from the places.list file that is currently used, but I don't think it would be too hard to do (that said, I I'm not sure how to do it.)  If someone could work out a way to have the other items in the gnome places menu show up, like the cd and usb drives that automatically appear, that would be great.
Also I'd love to have a recent documents section.

The nautilus bookmark file is a good idea, and could probably be done as long as i figure out the file layout... The USB and CD drives may require D-BUS and I havent dabbled into D-BUS yet but I am getting there...

> **PsyberOneZero said:**
> I'm loving the work on this and gControl.

I just had a few suggestions:
1) Be able to add seperators (hlines) not just spaces.
2) Integrate either Deskbar (I think that's python) or atleast a run dialog
3) Add a small border around the box, just a few pixels to set it off the desktop
4)Keep up the great work!

*Hlines sound great and most likely will make it into the nextversion ;)
*Integtrating deskbar is also D-BUS so when I get on that train we could solve all of those requests..
*Border will be added and I will try to make it configurable
*Trying my best to keep up the good work :-D 

> **sethmahoney said:**
> I tried the modified slab, and got rid of it within 5 minutes.  This, however, is awesome!  Thanks for the fantastic work!

The only issues I'm having is that there doesn't appear to be enough room in the settings panel, leaving me with a funkity scroll bar on the far right (fortunately the settings panel can be hidden - nice touch!), and that it is labeled "System" rather than "Apps" or something, but that I can get used to.

Yeah, the settings panel will lose the scroll bar, have no fear...

> **Who said:**
> Chanders, 

Nice work :D - it was beginning to worry me slightly that we keep playing with Novell toys - who else is innovating... Looks like that question has been answered :)

Are you going to write a spec for this, put it on Lunchpad and mail the devel list? Even if you target Edgy+1 or +2 Launchpad seems to be TUW (the Ubuntu Way)... (if you want to work on the code/don't have any interest in Launchpad (and you ask very nicely :P) I may have time to do some speccing for you)

Glad you liked it! My hands are so full with coding but I am asking nicely ;), would you mind terribly helping out with the speccing? 


> **mattisking said:**
> I like to use Transparency on my Gnome panels. Is there any way we could get transparency support into this applet? The standard "Menu Bar" works great for this. Also, is there a nice ReadMe that lays out how everything should work? Would you be accepting of ideas and feedback towards this? Also, what language is used? I might enjoy helping out on this. My C is rusty but workable, but I don't know Python at all (wouldn't imagine it would be hard to learn though).


Getting the applet itself (on the panel) transparent will be one of the first things I will try to address.. As for the readme, if someone would like to host a small site I could come up with a really good manual (This app is only 16kb!).. The introduction in the first post should get you started however...

I would love ideas and feedback, please feel free...  This app is written in PyGTK with the backend as Python... If you would like to help, just let me know ;-)

---

### Post by Iandefor on 2006-07-25
works OOB here. Love it!

Excellent work, Chanders!

---

### Post by chanders on 2006-07-25
> **Iandefor said:**
> works OOB here. Love it!

Excellent work, Chanders!

Glad you like it!

---

### Post by sethmahoney on 2006-07-25
> **lazyd2 said:**
> Check posts #103, #104 [here.;)]("http://www.compiz.net/viewtopic.php?id=2112&p=7")

Fantastic news (and the icon size thing was bugging me a little too, so hey, good news there, too!)!  Thanks!

---

### Post by Iandefor on 2006-07-25
Just hit the ghost icon issue, but I trust you'll have a fix at some point soon :twisted:.

---

### Post by Note360 on 2006-07-25
Wow dude you need a server I got one (small), justdont over flood my bandwith cause I have another site on it

---

### Post by Note360 on 2006-07-25
Defending you guys against Viper is tough work. That guy is a pompous ***.

---

### Post by chanders on 2006-07-25
> **Note360 said:**
> Wow dude you need a server I got one (small), justdont over flood my bandwith cause I have another site on it

Nice! I am currently coding the next release... When I am finished with the web site/manual  I will pm you... Hopefuly others with more bandwidth would offer their services too... Thanks so much...

---

### Post by Note360 on 2006-07-25
Well think of it as that crummy motel (I think in metaphors to much) your welcome in for as long as you want for cheap until you can get your bearings. (no prostitutes allowed though).

Edit: Oh I think you should roll your little collection of apps into one package as well as distribute them seperatly. (Ubuntu Control Pack?)

---

### Post by Iandefor on 2006-07-25
> **Note360 said:**
> Well think of it as that crummy motel (I think in metaphors to much) your welcome in for as long as you want for cheap until you can get your bearings. (no prostitutes allowed though). ROFL... oh dear.

---

### Post by Note360 on 2006-07-25
What I can't joke around? LoL

---

### Post by Iandefor on 2006-07-25
> **Note360 said:**
> What I can't joke around? LoL No... I was just laughing lol.

---

### Post by Note360 on 2006-07-25
I too was just joking when I said what I can't joke.

---

### Post by handy on 2006-07-25
> **chanders said:**
> Control center does not work because you dont have my Ubuntu Control Center installed :D  You can download it in the other thread or you can just change then control center item in gconf-editor to 'gnome-control-center' or 'control-center' (if you have SLED installed)

As for the fonts, I might be able to create a 'large fonts' version... I will see what I can do. I know my friend **Viper550** did some hacking to get the fonts bigger in USLED so maybe you can use that if it will suite you better...

Anything else, let me know ok?

Thanks Chanders, you are a cool frude! 8)

I will be watching this thread like a hawk, you respond so quickly... :KS

**[Edit:]**

Even if the window could be resized & set to allways open at that size, that would solve my font problem, providing the **System Management** options expanded proportionately?

---

### Post by chanders on 2006-07-26
> **handy said:**
> Thanks Chanders, you are a cool frude! 8)

I will be watching this thread like a hawk, you respond so quickly... :KS

**[Edit:]**

Even if the window could be resized & set to allways open at that size, that would solve my font problem, providing the **System Management** options expanded proportionately?

Right now I am coding the font settings... You will now bw able to set the font size according to your liking... Having the menu resizeable would not be such a good idea though...

Can you tell me exactly *which* labels are too large? That way I can put a setting in for it...

---

### Post by jimmygoon on 2006-07-26
[LEFT]The red was the default color, I was too lazy to change the text size and I only did this because I like what you've made and I want to see it get even better!
[/LEFT]

---

### Post by handy on 2006-07-26
> **chanders said:**
> Right now I am coding the font settings... You will now bw able to set the font size according to your liking... Having the menu resizeable would not be such a good idea though...

Does that mean that the fonts will be adjustable seperately for the menu?

I have installed GCC, great stuff. :KS 

I then posted on that thread that the font problem exists in GCC too.  I sound like a whinger! :( 

I'm not, I think your work is positively wonderful! 8) :KS

---

### Post by chanders on 2006-07-26
> **jimmygoon said:**
> [LEFT]The red was the default color, I was too lazy to change the text size and I only did this because I like what you've made and I want to see it get even better!
[/LEFT]

LOL...Ok... 

* The in the places area I will try to have computer there by default... 
* The small button (pin button) doesnt have any graphic because I couldnt find a good one to put ;-) (ideas?) 
* Tiny text on button will be increased
* Large text in system is/will now be configurable... Icon sizes in a subsequent release..
* I Cant really do anything about the missing title other than put a placement like "Edit me!" or something....
* What do you suggest for the alignment of the system management buttons?

---

### Post by zacbarton on 2006-07-26
This is great Chanders.

On my desktop I use just the bottom panel and its set to 49px in height. It looks like the USP menu is sitting behind my gnome panel and I cant see the bottom of the USP menu.

A screenshot displays this easier.
[IMG]http://www.zacbarton.com/USP.png[/IMG]

Keep up the great work :-)

---

### Post by Horizon on 2006-07-26
Great App. Although not as polished as the slab menu applet it's getting there. I'm really tempted to keep using the slab menu because it's more polished but I guess I'll use this for a while and see if it doesn't grow on me. 

If it was a bit smarter about placement (like drawing over the panel shadow instead of under, because it looks really wrong with the shadow over it) and the look was a bit more customisable (like the option to add a border that looks like the slab menu applet's border because it looks way too flat right now) it would blow slab out of the water. I think it also needs an option to have it forget the layout. So I can click places and go to my music folder but when I come back to the menu it goes back to a specific arrangement (like having only the applications section showing).

Well, I'm looking foward to seeing how this develops, it looks really promising. 

Here's a screenshot:
[[IMG]http://img154.imageshack.us/img154/6313/screenshot58thumbmc3.png[/IMG]]("http://img213.imageshack.us/img213/5203/screenshot58bs7.png")

PS: This really needs a preferences dialogue/window. Are you planning to have one?

---

### Post by Who on 2006-07-26
Hiya Chanders,

A little bug I have noticed
*When I start the panel (from my double height panel) it is slightly underneath the panel

I think you could do away with the need for your own application organiser by adding the current applications menu to the side of the usp - It means we don't regress on any fuinctionality and makes transition (for users and devs) much easier


so for example
```

|F       |S     |Accessories > |
| a      | y    |Education >   |
|  v     |  s   |Internet >    |
| A      |C     |Office >      |
|   p    | o    |System Tools >|
|     p  |   n  |Blah >        |
|       s|     f|Places >      |

```

Also, I'd love to see it possible to make plugins (probably whenDbus comes along) so that you can have things like
'Current Song'
'Next Tasks'
'New Emails' in a new pane aswell

Keep going, it's wicked!

Who

---

### Post by chanders on 2006-07-26
> **Who said:**
> Hiya Chanders,

A little bug I have noticed
*When I start the panel (from my double height panel) it is slightly underneath the panel

I think you could do away with the need for your own application organiser by adding the current applications menu to the side of the usp - It means we don't regress on any fuinctionality and makes transition (for users and devs) much easier


so for example
```

|F       |S     |Accessories > |
| a      | y    |Education >   |
|  v     |  s   |Internet >    |
| A      |C     |Office >      |
|   p    | o    |System Tools >|
|     p  |   n  |Blah >        |
|       s|     f|Places >      |

```

Also, I'd love to see it possible to make plugins (probably whenDbus comes along) so that you can have things like
'Current Song'
'Next Tasks'
'New Emails' in a new pane aswell

Keep going, it's wicked!

Who

Already Implemented! See new version;) 

As for the plugins I am in the process of writing an API for them. DBUS will have to come along a little later as i couldnt find too much on the net to learn from... But I will get there...

---

### Post by Who on 2006-07-26
> **chanders said:**
> Already Implemented! See new version;) 

As for the plugins I am in the process of writing an API for them. DBUS will have to come along a little later as i couldnt find too much on the net to learn from... But I will get there...

Have you talked to iXce from Compiz.net - didn't he do the Compiz DBus stuff?

---

### Post by Who on 2006-07-26
> **chanders said:**
> Already Implemented! See new version;) 


Wicked - does anyone have any screenshots?

---

### Post by chanders on 2006-07-26
> **Who said:**
> Wicked - does anyone have any screenshots?

Go for it... Post them up when you do ;)

---

### Post by Who on 2006-07-26
> **chanders said:**
> Go for it... Post them up when you do ;)

I'm not actually on Ubuntu now :S I was hoping someone else could post some

---

### Post by lazyd2 on 2006-07-26
Some screenshots

[[IMG]http://img73.imageshack.us/img73/9946/screenshotco2.th.jpg[/IMG]]("http://img73.imageshack.us/my.php?image=screenshotco2.jpg") [[IMG]http://img239.imageshack.us/img239/995/screenshot2ku6.th.jpg[/IMG]](http://img239.imageshack.us/my.php?image=screenshot2ku6.jpg)
[[IMG]http://img83.imageshack.us/img83/6325/screenshot1xf7.th.jpg[/IMG]]("http://img83.imageshack.us/my.php?image=screenshot1xf7.jpg") [[IMG]http://img239.imageshack.us/img239/8852/screenshotrk4.th.jpg[/IMG]](http://img239.imageshack.us/my.php?image=screenshotrk4.jpg)

---

### Post by atie on 2006-07-26
I have few wishes with 0.20-1 version.

1. I had changed "search command" with beagle-search by gconf, but unexpectedly USP keeps filtering programs as seen on the attached. However, pressing "search" button brings beagle UI though. If possible, I'd like to have both command filter and search filter independently(?).

2. I could use "use custom color" to distinguish border from background color, but overall it's quite difficult to users so a menu with USP to control border, color and font   would be nice.

3. Compared to gnome-main-menu, I think I am missing "recently used documents".

4. Depending on font, small size fonts are not so looking good so that same size font with regular/bold combination may better, IMO.

5. I'd like to have smaller "Place" section and bigger "Application" section so maybe have two-colums list for programs same as gnome-main-menu.

Thanks for nice program, Chanders :)

---

### Post by Note360 on 2006-07-26
Looks good (just woke up) installing the new version now.

---

### Post by Note360 on 2006-07-26
Cant believe how stupid I was. I got it jut upgraded to .21.

---

### Post by outdooricon on 2006-07-26
> **chanders said:**
> 
* The small button (pin button) doesnt have any graphic because I couldnt find a good one to put ;-) (ideas?) 


How about something like the one here... [http://chakuriki.sakura.ne.jp/wema/image/pin.png](http://chakuriki.sakura.ne.jp/wema/image/pin.png)

---

### Post by jarredmt on 2006-07-26
So far USP is looking great. I made some mock ups on how I feel the USP show look and feel. Take a look and see if you like any of the ideas to implement into USP. Most of the changes are reorganizing of items. I do feel that the three sections are out of order. It should stick to the order of the Menu Bar (Applications, Places then System)

[IMG]http://ubuntuforums.org/gallery/data/4/jarred.jpg[/IMG]

[IMG]http://ubuntuforums.org/gallery/data/4/Favorites.jpg[/IMG]

BTW, I just updated USP and the new Applications USP is great.

---

### Post by Iandefor on 2006-07-26
I like how USP .21-1 has the ability to filters apps by type, but it's a little screwy in how it does it. Unless the menu editor was really just a boring game all along and you just got it sorted right, and "apply theme" is appropriate for an office environment :-D.

---

### Post by augied on 2006-07-26
Small annoyance: When you use the filter and open an app, the filter does not reset, meaning that you have to manually reset it.  The same happens when you run a search.  Maybe this should be a setting (autoclear.)
I think someone already suggested having a configurable default layout that the menu always resets itself to when reopened.  Maybe there could be a set default button on the menu.

Also, when the applications menu is in the favorite apps view and you start typing, the filter loses focus.

---

### Post by augied on 2006-07-26
> **Iandefor said:**
> I like how USP .21-1 has the ability to filters apps by type, but it's a little screwy in how it does it. Unless the menu editor was really just a boring game all along and you just got it sorted right, and "apply theme" is appropriate for an office environment :-D.
Software Update appears to be a game.

---

### Post by Iandefor on 2006-07-26
> **augied said:**
> Software Update appears to be a game. It is! What a boring game... watch the progress bar go... *yawns*.

I like tetravex better!

---

### Post by chanders on 2006-07-26
Ok guys, just got up after a few hours sleep :yes: Iwill be looking at the suggestions and the bugs and will be working actively on USP today...

---

### Post by augied on 2006-07-26
> **Iandefor said:**
> It is! What a boring game... watch the progress bar go... *yawns*.

I like tetravex better!
Personally, I like the one where you try to turn all the little boxes green by double clicking on them.  What's that one called?

---

### Post by augied on 2006-07-26
> **chanders said:**
> Ok guys, just got up after a few hours sleep :yes: Iwill be looking at the suggestions and the bugs and will be working actively on USP today...
That's the problem with writing good software.  We never let you sleep.  We may tell you to, but that's just to guilt you into working harder.

---

### Post by Note360 on 2006-07-26
Yerp we are just that cruel

---

### Post by chanders on 2006-07-26
> **Note360 said:**
> Yerp we are just that cruel

LOL, I have fun doing it so no worries ;)

@Note360 - Havent got around to the site yet thats why I havent contacted yu... I am still coding like crazy...:D

---

### Post by Note360 on 2006-07-26
Lol, sorry just wondering I woke up and I am like wow this .21 is great wonder why chanders didnt contact me. HMMM. Let me ask him.

Oh also I am thinking about learning python.

---

### Post by chanders on 2006-07-26
> **zacbarton said:**
> This is great Chanders.

On my desktop I use just the bottom panel and its set to 49px in height. It looks like the USP menu is sitting behind my gnome panel and I cant see the bottom of the USP menu.

Hmmm... If you have SLED installed, how does it show up? In line with the panel or on top the panel? (will help with coming up with a solution) 

> **atie said:**
> I have few wishes with 0.20-1 version.

1. I had changed "search command" with beagle-search by gconf, but unexpectedly USP keeps filtering programs as seen on the attached. However, pressing "search" button brings beagle UI though. If possible, I'd like to have both command filter and search filter independently(?).

2. I could use "use custom color" to distinguish border from background color, but overall it's quite difficult to users so a menu with USP to control border, color and font   would be nice.

3. Compared to gnome-main-menu, I think I am missing "recently used documents".

4. Depending on font, small size fonts are not so looking good so that same size font with regular/bold combination may better, IMO.

5. I'd like to have smaller "Place" section and bigger "Application" section so maybe have two-colums list for programs same as gnome-main-menu.

Thanks for nice program, Chanders :)

* Not sure how to implement a search and filter simultaneously without adding two entry boxes :-k Any ideas?
* Custom color for the border is #1 on the list today
* Recently used not implemented yet... stay tuned
* Font sizes are now customizable not weight though
* Will look at it, not a priority though..

> **Iandefor said:**
> I like how USP .21-1 has the ability to filters apps by type, but it's a little screwy in how it does it. Unless the menu editor was really just a boring game all along and you just got it sorted right, and "apply theme" is appropriate for an office environment :-D.

Yeah, it was late/early :D  Not sure how GNOME does the sorting though but This will be fixed in the next release

> **augied said:**
> Small annoyance: When you use the filter and open an app, the filter does not reset, meaning that you have to manually reset it.  The same happens when you run a search.  Maybe this should be a setting (autoclear.)
I think someone already suggested having a configurable default layout that the menu always resets itself to when reopened.  Maybe there could be a set default button on the menu.

Also, when the applications menu is in the favorite apps view and you start typing, the filter loses focus.

* Will add auto-clear on search/minimise
* Will fix focus bug in the next release

---

### Post by Hells_Dark on 2006-07-26
Hi, i posted my problem on the compiz forum.
I put it here too :
[quote=Hells_Dark]Hi,

Great stuff.
But i have a few problems. The main problem have been resolved with the new deb version, but i still have a problem with the icons (Gnome theme) :
[[img]http://pix.nofrag.com/4e/07/fd9364d229f5834e7043c925fde2t.jpg[/img]](http://pix.nofrag.com/4e/07/fd9364d229f5834e7043c925fde2.html)
(lock screen icon "for the size", computer icon "for the icon"..)

Thanks[/quote]
Is anybody have a similar problem ?

---

### Post by augied on 2006-07-26
Can we get a way to remove the text from the panel button? (thus making the button much smaller)

---

### Post by chanders on 2006-07-26
> **Hells_Dark said:**
> Hi, i posted my problem on the compiz forum.
I put it here too :

Is anybody have a similar problem ?
have you tried changing the theme? See if it works then... USP uses the default gnome names for icons so it has to do with your icon theme is my guess....

The 'size' problem will be fixed in the next release...

> **augied said:**
> Can we get a way to remove the text from the panel button? (thus making the button much smaller)
This is not usually configurable, but I will se what I can do ;)

---

### Post by Note360 on 2006-07-26
I think the order of the different areas should be configurable.

ex)
Applications Places System

or

System Places Applications

I should be able to change the order. (Plugin support might be a good idea to include at some point, so you dont have to do everything)

---

### Post by Hells_Dark on 2006-07-26
> **chanders said:**
> have you tried changing the theme? See if it works then... USP uses the default gnome names for icons so it has to do with your icon theme is my guess....

I tried a lot of themes.
I have the same problem with a lot of them (crux,crystal svg,flat blue, GNOME....)
And it works with a few ones (Human, Tango, Tangerine..)

Strange :sad: 

And i wanna keep my gnome icon theme.
> The 'size' problem will be fixed in the next release...
Thanks ;)

---

### Post by v8YKxgHe on 2006-07-26
Great work! I like it, BUT It's too big IE it takes up a lot of desktop screen space. I've seen a lot of linux users complain how big the XP Menu is, well this is like twice as big - maybe even more. I think for the next version(s) you should aim to make it smaller

---

### Post by lazyd2 on 2006-07-26
> **AlexC_ said:**
> Great work! I like it, BUT It's too big IE it takes up a lot of desktop screen space. I've seen a lot of linux users complain how big the XP Menu is, well this is like twice as big - maybe even more. I think for the next version(s) you should aim to make it smallerYou can make it quite smaller...Since it has 3 tabs you select what you want. If it starts getting smaller (IMO) there gonna be problems with fonts, icons, etc.

---

### Post by v8YKxgHe on 2006-07-26
> **lazyd2 said:**
> You can make it quite smaller...Since it has 3 tabs you select what you want. If it starts getting smaller (IMO) there gonna be problems with fonts, icons, etc.
I know you can enable/disable the different tabs, I mean - the height and way it's laid out makes it feel big, and the use of big fonts/icons really doesn't help. I don't know why but most linux dev's make there applications phyiscaly big and use big icons/text - just using smaller fonts and icons can make the application much much smaller in size ( desktop wise ).

---

### Post by NNois on 2006-07-26
Hello thanks chandler for this great app ! Very good work !
I have a small problem and can't found the solution on the last version 0.21
when I launch app with the new "all app" mostly of this apps won't run because a parameter %U is passed. but when this app is in favorites no problem... Did I'm alone with this problem ?

---

### Post by chanders on 2006-07-26
> **NNois said:**
> Hello thanks chandler for this great app ! Very good work !
I have a small problem and can't found the solution on the last version 0.21
when I launch app with the new "all app" mostly of this apps won't run because a parameter %U is passed. but when this app is in favorites no problem... Did I'm alone with this problem ?

Will fix this in the next release.. ;)

---

### Post by ironfistchamp on 2006-07-26
Woah this is amazing. Worked straight away. Wish I had skills to do this. I still can't create a glassy effect in GIMP.

Anyway I really like this. Has replaced my main menu thingy.

Couple of issues/suggestions. I am comapring v20 and v21. In v20 there was a regular window border. Hitting the X messed it up but I like the border (maybe just remove the X). In v21 it was gone and looked very odd. Didn't fit in the with the whole scheme. Can it be put back or have it as some configurable option. 

In v20 mine seems to hover an inch or so above the panel. Odd.

In both of them places that I have dragged into the places area don't do anything. Are they ment to yet?

Some screens

[http://i104.photobucket.com/albums/m163/ironfistchamp/panelv20.png](http://i104.photobucket.com/albums/m163/ironfistchamp/panelv20.png)
[http://i104.photobucket.com/albums/m163/ironfistchamp/panelv21.png](http://i104.photobucket.com/albums/m163/ironfistchamp/panelv21.png)

What does the pin button acutally do? Also it would eb great if the menu closed when I clicked outside of it like a normal menu. Just a suggestion.

Thanks for some wonderful work. You have done an amazing job.

Ironfistchamp

---

### Post by Note360 on 2006-07-26
The places work on mine and try fooling around with the border length in gconf. (The pin keeps the window open even after a app is launched I think)

---

### Post by chanders on 2006-07-26
> **ironfistchamp said:**
> Woah this is amazing. Worked straight away. Wish I had skills to do this. I still can't create a glassy effect in GIMP.

Anyway I really like this. Has replaced my main menu thingy.

Couple of issues/suggestions. I am comapring v20 and v21. In v20 there was a regular window border. Hitting the X messed it up but I like the border (maybe just remove the X). In v21 it was gone and looked very odd. Didn't fit in the with the whole scheme. Can it be put back or have it as some configurable option. 

In v20 mine seems to hover an inch or so above the panel. Odd.

In both of them places that I have dragged into the places area don't do anything. Are they ment to yet?

Some screens

[http://i104.photobucket.com/albums/m163/ironfistchamp/panelv20.png](http://i104.photobucket.com/albums/m163/ironfistchamp/panelv20.png)
[http://i104.photobucket.com/albums/m163/ironfistchamp/panelv21.png](http://i104.photobucket.com/albums/m163/ironfistchamp/panelv21.png)

What does the pin button acutally do? Also it would eb great if the menu closed when I clicked outside of it like a normal menu. Just a suggestion.

Thanks for some wonderful work. You have done an amazing job.

Ironfistchamp

That border was a bug :D  You will be able to add your own in the next release... 

The window closes when you click away... You need to un-pin it by clicking on the smallest button on the top left...

Glad you like it ;)

---

### Post by Note360 on 2006-07-26
Wow how many lines of code is it now?

---

### Post by sethmahoney on 2006-07-26
> **Horizon said:**
> I think it also needs an option to have it forget the layout. So I can click places and go to my music folder but when I come back to the menu it goes back to a specific arrangement (like having only the applications section showing).

I second this idea.  I usually only have applications open, then I open places to go to my home folder, and have to manually make it close places (so once again only applications is showing).  It would be nice if it did this automatically.

---

### Post by handy on 2006-07-27
Hi Chanders,

I have changed the font size a variety of times, all the way down to 2.  Does not solve my problem.  I still have unusably large fonts in USP... :( 

I've attached an image for your perusal... :?:

---

### Post by chanders on 2006-07-27
> **handy said:**
> Hi Chanders,

I have changed the font size a variety of times, all the way down to 2.  Does not solve my problem.  I still have unusably large fonts in USP... :( 

I've attached an image for your perusal... :?:

WOW :shock: From the looks of it, no matter what size of fonts you use, USP wont work well because of the layout of the panel :-(

---

### Post by zacbarton on 2006-07-27
> **chanders said:**
> Hmmm... If you have SLED installed, how does it show up? In line with the panel or on top the panel? (will help with coming up with a solution)

Heres a screenshot with USP and SLED, hope it helps :-)
[IMG]http://www.zacbarton.com/USP2.png[/IMG]

---

### Post by chanders on 2006-07-27
> **zacbarton said:**
> Heres a screenshot with USP and SLED, hope it helps :-)


Thanks... There is one critical item I need to solve for this to work.... Will work on it as soon as is possible..

---

### Post by handy on 2006-07-27
> **chanders said:**
> WOW :shock: From the looks of it, no matter what size of fonts you use, USP wont work well because of the layout of the panel :-(

Is there a solution?

---

### Post by the_thunderbird on 2006-07-27
Is there any CVS or Subversion access? I would like to do some work on the source, to see if I can add a bit of extra polish to it.

---

### Post by handy on 2006-07-27
I haven't looked, but I think the source is supplied in the .deb...

---

### Post by Hells_Dark on 2006-07-27
Hey,

What people think about the order of names in favorite applications ?
I mean the name in small and the generic name in strong..

I find it weird, i would prefer the opposite, don't you ?

---

### Post by augied on 2006-07-27
> **Hells_Dark said:**
> Hey,

What people think about the order of names in favorite applications ?
I mean the name in small and the generic name in strong..

I find it weird, i would prefer the opposite, don't you ?
I agree.  It looks especially wierd when the app doesn't have a generic name (which is often the case) or if it's a (semi) long description.

---

### Post by Horizon on 2006-07-27
> **Hells_Dark said:**
> Hey,

What people think about the order of names in favorite applications ?
I mean the name in small and the generic name in strong..

I find it weird, i would prefer the opposite, don't you ?
Nope, i find this better. Because I have one application of each type in there (browser, email client, irc client etc.). Some of their names are long and it looks much neater this way. Kind of like the "Internet Browser" and "Email" entries in the XP start menu.

Maybe this could be an option? I'd love to be able to specify which two labels from the launcher show...then I could have say, the japanese name in big (GenericName['jp'] or however they list it in the launcher file) and the english name below for when I forget what the japanese means XD

> **augied said:**
> I agree. It looks especially wierd when the app doesn't have a generic name (which is often the case) or if it's a (semi) long description.

When they don't have a generic name you can right click and edit the labels for now...

---

### Post by bojzi on 2006-07-27
**This is very nice chanders! Thank you for this great panel app! :)**

I've tried it on Dapper and I noticed a few bugs.
1. When I click on it, it's displayed like a new window, not like a menu (meaning it has a titlebar with an x button to close it). 
Screenshots: [[IMG]http://img143.imageshack.us/img143/3840/usp1dc2.th.jpg[/IMG]](http://img143.imageshack.us/my.php?image=usp1dc2.jpg) [[IMG]http://img143.imageshack.us/img143/114/usp2ba1.th.jpg[/IMG]](http://img143.imageshack.us/my.php?image=usp2ba1.jpg)
(could this be dapper related?)
2. When I click on the System button and try to click elsewhere (not on the menu) it won't disappear. I have to first click on the menu (to make the window active) and then it'll close with clicking outside of it.
3. Clicking on the x to close it really closes it but the System button stays activated (like being pushed) and I can't access the menu again. I have to remove it from the panel and add it again to be able to use it.
4. It can't be moved with the middle mouse button (like the other stuff on the panel). I have to choose move and then move it.

That's all for now. Again, thanks for this I really like it!

---

### Post by Hells_Dark on 2006-07-27
> **bojzi said:**
> **This is very nice chanders! Thank you for this great panel app! :)**

I've tried it on Dapper and I noticed a few bugs.

Some of those bugs have already been fixed in the new version (i mean the 1, 2 and 3. The 4 still remaining..).
If you don't find it here, try there : [http://www.compiz.net/viewtopic.php?id=2112&p=1](http://www.compiz.net/viewtopic.php?id=2112&p=1)
Edit : this one : [0.21-1 version](http://ubuntuforums.org/attachment.php?attachmentid=13248&d=1153912534) ;)

---

### Post by bojzi on 2006-07-27
Ouch, now I see that I took the .20 version from the first page of this thread... Thanks! *feels stupid :)*

---

### Post by ironfistchamp on 2006-07-27
Used this some more after having some coffee so I am fully alert. 

Anyway this is even better than I thought it was. I got the places working. I re-dragged them and all was well. Could have been v20 probs I don't know. I love the fact that this worked and Sled 10 complained of broken pipes (I thought electricity used wires :p  ).

Yeh it doesn't close when I click outside. Sometimes it will loose focus but will still be up. 

On the All Applications bit some apps are listed twice (Synaptic, Bug Report) and others are not listed at all (amarok, Banshee). Why might that be?

Keep up the good work.

---

### Post by chanders on 2006-07-27
> **handy said:**
> Is there a solution?
Not without hacking the panel... I will give you some tips to get this done as soon as I get some spare time..


> **the_thunderbird said:**
> Is there any CVS or Subversion access? I would like to do some work on the source, to see if I can add a bit of extra polish to it.
I dont have a CVS setup for this yet but I will hopefully soon... You can hack the source code (it's the /usr/bin/usp file) and post up your hacks ;)


> **augied said:**
> I agree.  It looks especially wierd when the app doesn't have a generic name (which is often the case) or if it's a (semi) long description.
Right click, make it what you want ;)


> **bojzi said:**
> 
4. It can't be moved with the middle mouse button (like the other stuff on the panel). I have to choose move and then move it.

That's all for now. Again, thanks for this I really like it!
This stems from the fact that I dont have too much experience with panel buttons but it is on my list of things to do...


> **ironfistchamp said:**
> 
Yeh it doesn't close when I click outside. Sometimes it will loose focus but will still be up. 

On the All Applications bit some apps are listed twice (Synaptic, Bug Report) and others are not listed at all (amarok, Banshee). Why might that be?

Keep up the good work.
Make sure you dont have it 'pinned' (small button top left) for the focus to work...

Double applications fixed in the next version ;)

---

### Post by Hells_Dark on 2006-07-27
> **chanders said:**
> 
Right click, make it what you want ;)

Yeah, but it would be great nevertheless if we could switch generic name and name emplacements in a configuration pannel.

---

### Post by bojzi on 2006-07-27
Just one little request that would mean the world to me... :)
Can it be made so that when I select "All Aplications" it stays remembered after restarting?

And a bigger but not so important thing... Can it be made so that we could switch the placement of the parts of the menu (as in switch the places of the applications part and the places part, for example)?

---

### Post by melalcoolique on 2006-07-27
> **melalcoolique said:**
> Mayday, I've got a serious problem here...

I'am running Edgy since the repositories are up. However, USP has killed my Gnome session. This happened when I launched "ALL APPLICATIONS" and tried to add "Archive Manager".

Actually, I'am in the failsafe session and I've absolutely no way to get my normal session working. I removed, purge USP and the applet and restarted but with no luck.

I've no clue about my problem except it could be related to D-bus.

I am absolutely zen but I'am affraid this time I'am stuck for real. Bad move. :mrgreen:

Well, I saved my Good old Ubuntu installation but it was very very close.

Very surprised to be the only one to report a breakdown like this.

I will stick a bit with the Gnome menu.

Phewww...

---

### Post by LordMau on 2006-07-27
This is a great project. No problems so far. No wonder no ones posting on the other slab related threads!

Err please verify, is this still dependent on nautilus?

---

### Post by reacocard on 2006-07-27
Wow. Just installed this, and it's awesome. no more boring old gnome menus for me!

---

### Post by Note360 on 2006-07-27
was it ever dependant on nautalius (just for the more app button I think which is by default hidden).

---

### Post by monchichi on 2006-07-27
Thanks, Chanders.

I hated slab until I came across your version-- it's way better! Good work! Intuitive, functional, and nice looking...

---

### Post by LordMau on 2006-07-27
Bug (on my system):

Clicking an item on Places starts nautilus but without --no-desktop option. This causes my xfce handled desktop via xfdesktop to be killed then the desktop overwritten by nautilus. Closing the browser window doesnt close the desktop handling, had to kill the nautilus process then manually restart xfdesktop.

Can you let nautilus handle folders as browser and with --no-desktop on? Can we manually set this? Checking via gconf I didn't see how.

Also, quit doesn't work in the USP.

Thanks.

EDIT: Also noticed, aside from killing xfdesktop, it also kills the xfce session manager. This also prevents quitting via the desktop menu.

---

### Post by LordMau on 2006-07-27
> **Note360 said:**
> was it ever dependant on nautalius (just for the more app button I think which is by default hidden).

Like I noted in other thread re: slab, any version of the slab always crashes on my system unless I installed nautilus. Note I had an xfce desktop with minimal gnome deps as much as possible.

---

### Post by Hells_Dark on 2006-07-27
Can we already do that :
[IMG]http://img105.imageshack.us/img105/1299/allapplicationswh9.jpg[/IMG]
I don't know how -_-

---

### Post by chanders on 2006-07-27
People we have a problem.

I have spent all morning trying to solve the zombie problem. Essentially when applications are closed they are zombied(takes no resources and does not use any cpu but unsightly). I have tried double forking, waiting etc but to no avail... Anyone with any info/ help please come forward... It really breaks my spirit when I cant solve things like these....

In the mean time I will do something  a little less brain killing and try to finish up some more features... Just to keep you piqued on the next release..

* The border is working now. Color and size configurable 138
* Entry focus fixed
* Double entries in 'All applications' removed
* Now lists kde and other apps previously missing
* No more %U problems
and more...

To all the posts I havn't replied to since this morning I will shortly... 

Quickly... 
* The nautilus dependency can be easily fixed
* The above feature was removed... people didnt seem to like all the icons...
* Placement of panes coming soon...
* Should work with no problems on edgy .. dunno what happned with yours

---

### Post by Note360 on 2006-07-27
Well edgy is edgy it could be anything. Oh and I am liking Python alot ( much neater than Perl but a few things bug me (the lack of confusion :p  is one I grew so used to the Perlisms I almost cant live without em) )

---

### Post by chanders on 2006-07-27
> **Note360 said:**
> Well edgy is edgy it could be anything. Oh and I am liking Python alot ( much neater than Perl but a few things bug me (the lack of confusion :p  is one I grew so used to the Perlisms I almost cant live without em) )

Glad to know! Learn quickly so you can help me with the zombie problem :(

---

### Post by chanders on 2006-07-27
Zombie problem - Solved!

---

### Post by ironfistchamp on 2006-07-27
Wahey no more zombie... whats zombie?

---

### Post by reacocard on 2006-07-27
I have the zombie effect and I'm using Dapper.

---

### Post by chanders on 2006-07-27
> **reacocard said:**
> I have the zombie effect and I'm using Dapper.

Well guess what?! You wont have it in the next release... I just solved the problem....Yay!

---

### Post by augied on 2006-07-27
> **chanders said:**
> Zombie problem - Solved!
How?

---

### Post by Amaranth on 2006-07-27
I _really_ don't want to read through all of those posts so I'm not sure if someone has suggested it yet or not but you should use python-gmenu to read the applications menu. It's a python wrapper around the actual code that the applications menu uses so you get the same result (no permissions bugs, sorting oddities, etc). Also if you're using edgy alacarte 0.9.x has a python package 'Alacarte' installed with some code to do this and feed you menu items.

---

### Post by chanders on 2006-07-27
> **augied said:**
> How?

Here is the code, basically spawn a child process of a child process and kill the first one. The Grand child is then inherited by init so when it exists, the system cleans up the zombie...

```
    def RunControl(self,widget,cmd):
    	pid = os.fork()
    	if pid:
            os.spawnvp(os.P_NOWAIT,cmd[0], cmd)
            os._exit(0)

```
> **Amaranth said:**
> I _really_ don't want to read through all of those posts so I'm not sure if someone has suggested it yet or not but you should use python-gmenu to read the applications menu. It's a python wrapper around the actual code that the applications menu uses so you get the same result (no permissions bugs, sorting oddities, etc). Also if you're using edgy alacarte 0.9.x has a python package 'Alacarte' installed with some code to do this and feed you menu items.

Thank you very much Amaranth. I wish I had found this earlier as I did everything from scratch! I am tempted to use 'import Alacarte' but I am sure there are lots of dapper users who would like to use USP... 

I will definitely take a look at python-gmenu. If you have a link for the docs, please post... Thanks again

---

### Post by Hells_Dark on 2006-07-27
> **chanders said:**
>  I am sure there are lots of dapper users who would like to use USP... 

I approve :smile: 

Well done for the zombie bug (even if i love zombies....brains, eat brains...).

That smell good for the next release.
Anyway, think to sleep...a little a least ;-)

---

### Post by dcubed20 on 2006-07-27
This might have been said earlier, but I didn't see it. I think that whenever the menu window gets smaller, for whatever reason, it should shrink from the top instead of from the bottom. I don't really like the gap between it and the panel, and it only gets worse if I select/deselect one of the panes and the whole thing shrinks upward.

Otherwise, impressive work.

---

### Post by Note360 on 2006-07-27
Congrats on the zombie problem that was an annoying little bug.

---

### Post by Amaranth on 2006-07-27
There are no docs, sorry. :/ btw, the following code does "daemonize" the "correct" way, which is what I think you're trying to do.```
import os
import sys
import resource

UMASK = 0
if os.getuid() == 0:
	WORKDIR = '/'
else:
	WORKDIR = os.getcwd()
MAXFD = 1024

if (hasattr(os, 'devnull')):
	REDIRECT_TO = os.devnull
else:
	REDIRECT_TO = '/dev/null'

def createDaemon():
	try:
		pid = os.fork()
	except OSError, e:
		raise Exception, '%s [%d]' % (e.strerror, e.errno)

	if (pid == 0):
		os.setsid()
		try:
			pid = os.fork()
		except OSError, e:
			raise Exception, '%s [%d]' % (e.strerror, e.errno)

		if (pid == 0):
			os.chdir(WORKDIR)
			os.umask(UMASK)
		else:
			os._exit(0)
	else:
		os._exit(0)

	maxfd = resource.getrlimit(resource.RLIMIT_NOFILE)[1]
	if (maxfd == resource.RLIM_INFINITY):
		maxfd = MAXFD
  
	for fd in range(0, maxfd):
		try:
			os.close(fd)
		except OSError:
			pass

	os.open(REDIRECT_TO, os.O_RDWR)
	os.dup2(0, 1)
	os.dup2(0, 2)
	return (0)

```

If you rely on paths for anything you probably want to change WORKDIR.

---

### Post by Amaranth on 2006-07-27
Quick python-gmenu example:
```

import gmenu
class MenuExample:
	def __init__(self):
		self.tree = gmenu.lookup_tree('applications.menu')

	def getMenus(self, parent=None):
		if parent == None:
			#gives top-level "Applications" item
			yield self.tree.root
		else:
			for menu in parent.get_contents():
				if menu.get_type() == gmenu.TYPE_DIRECTORY and self.__isVisible(menu):
					yield menu

	def getItems(self, menu):
		for item in menu.get_contents():
			if item.get_type() == gmenu.TYPE_ENTRY and item.get_desktop_file_id()[-19:] != '-usercustom.desktop' and self.__isVisible(item):
				yield item

	def __isVisible(self, item):
		if item.get_type() == gmenu.TYPE_ENTRY:
			return not (item.get_is_excluded() or item.get_is_nodisplay())
		if item.get_type() == gmenu.TYPE_DIRECTORY and len(item.get_contents()):
			return True
```

This code has one known bug: if all of the items in a menu are hidden it should be hidden too. For a solution to this look at Alacarte 0.9's /usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py

---

### Post by chanders on 2006-07-27
Thank you so much for the tips! I am about to release the next version, I will try to include your code in this release+1. Thank you again..

---

### Post by chanders on 2006-07-27
New release

Ver 0.25-1 Jul 27 23:00 (GMT -4)
   * Border added
   * Able to configure border size and color
   * Able to set pane order in /apps/pane_order
   * Added swap generic name and app name
   * No more zombie apps
   * Entry focus fixed
   * Double entries in 'All applications' removed
   * Now lists kde and other apps previously missing
   * No more %U problems
   * Added setting item to 'All Applications'

Known bug : Sometimes hiding 'Places' also hides 'Applications'.... will fix later 

When you all have it configured properly, post screenshots.. I am writing a site for UCC and USP and I need some screenies 

Chanders

---

### Post by mattisking on 2006-07-27
Unfortunately, this one isn't working for me. :( When I add it to my panel all I see is a small DOT that I can't select. I saw this same behavior on one of your first versions but that went away later.

I can remove the dot by dragging the entire panel to the side instead of top of the screen at which point it shows up I can then right-click it to lock it in place or unlock it but that's it. I removed it, and when I try to add it now, it just blows up.

---

### Post by lazyd2 on 2006-07-27
Yeap, he's working on it....

---

### Post by mattisking on 2006-07-27
Well, I'm not really sure what "Ver 0.26-1 Jul 23:25:00 (GMT -4)" means about fixing a no KDE dir... whatever as I'm running Gnome... but this version appears to be working fine.

I still wish I had transparency though. (hint) :)

---

### Post by agurk on 2006-07-27
> **mattisking said:**
> Unfortunately, this one isn't working for me. :( When I add it to my panel all I see is a small DOT that I can't select. I saw this same behavior on one of your first versions but that went away later.

I can remove the dot by dragging the entire panel to the side instead of top of the screen at which point it shows up I can then right-click it to lock it in place or unlock it but that's it. I removed it, and when I try to add it now, it just blows up.
I confirm seeing this with version 0.26-1.

---

### Post by chanders on 2006-07-27
> **agurk said:**
> I confirm seeing this with version 0.26-1.

Install 0.27 and logout/log back in.... let me know if it works...

---

### Post by mattisking on 2006-07-27
Working for me.

---

### Post by zacbarton on 2006-07-27
Looking good Chanders

One thing I have noticed is USP is still sitting behind my gnome panel. It seems to sit infront of the panel until I close the "add to panel" window. After that it sits under the panel again.

Im using a panel of 48px high and USP .27-1.

Another thing that would be good to have is make the "System" button grow in height when a panel does so are equal height.

Keep going its getting better and better.

Z

---

### Post by augied on 2006-07-28
Great updates!
I have a few complaints which may have been mentioned already, but I'm too tired to remember.
1. The icons in the places pane aren't lined up perfectly.
2. It would be nice if you could make the panes auto-resize to fit long text (I know you can change the font, but still.)
3. I really want the search field to auto-clear.
4. Apps that I had hid from the gnome menu show up here (maybe that will be taken care of if you use gmenu)
5. The menu appears to be pinned whether or not the pin button is selected.
6. It's just too damn pretty.  WTF!

P.S. I'm also waiting on the edge of my seat for a default layout setting.

---

### Post by agurk on 2006-07-28
> **chanders said:**
> Install 0.27 and logout/log back in.... let me know if it works...
Yep, works now, thanks! The USP button doesn't adhere to the opacity level set for the panel though (see pic).
Oh, and the Screen Resolution button text did not show my resolution until I had run the screen res selection app once.

---

### Post by Hells_Dark on 2006-07-28
Thanks for the new release.

But i still having some problem with my GNOME icon theme.
[[img]http://pix.nofrag.com/d0/ae/5abab79760ea40b574fea23c4061t.jpg[/img]](http://pix.nofrag.com/d0/ae/5abab79760ea40b574fea23c4061.html)

Is anybody have the same problem or, could tell me if he have the same when he put the GNOME theme icon ?
Edit : i asked to some people (2), they say they have the same.

---

### Post by bojzi on 2006-07-28
Very nice! It looks much more polished now!

Could you just please add an option to gconf that could remembers if All Applications are selected? I don't use the favorite applications part and this would be a very nice finishing touch. :)

For all those using the Gilouche theme - set the border colors to (59637, 55705, 48496) if you want to have the border somewhat darker but still in theme with the background or put in (24914, 36061, 45896) if you want to have it like SLAB (blue).

If anybody needs I type a little tutorial here on how to get these colors (it's the same for custom_color and custom_heading_color)...

---

### Post by lazyd2 on 2006-07-28
> If anybody needs I type a little tutorial here on how to get these colors (it's the same for custom_color and custom_heading_color)...
Reply With QuotePlease do...

---

### Post by outdooricon on 2006-07-28
I ahven't gotten to install this yet, grr... but there is someting I've noticed from the screenshots... the 'Quit' text doesn't line up with the other two above it... It's looking great though otherwise.

---

### Post by fuoco on 2006-07-28
I thought the whole idea started with novell doing research to see exactly what makes the best usability. Is it really a good idea to deviate from that just for the sake of being innovative and unlike suse ?

---

### Post by Hells_Dark on 2006-07-28
> **fuoco said:**
> I thought the whole idea started with novell doing research to see exactly what makes the best usability. Is it really a good idea to deviate from that just for the sake of being innovative and unlike suse ?

Of course, it's a good idea to create our own pannel !
And the choice always do linux better.

---

### Post by bojzi on 2006-07-28
**HOW TO GET THE COLOR YOU WANT FOR YOUR BORDER** (or else colors in this format)

1. Choose which color you want to use on your desktop, a web site, a screenshot or something else. I'll be using a SLAB screenshot for this one.
[IMG]http://diego.aureal.com.pe/wp-content/uploads/wii.png[/IMG]

2. Now open up gimp and load up this image. Now, use the color selection tool 
(either clicking or typing "O" on the keyboard) and select the blue border color.
After you do that the Color Picker will pop up with some information. The important information are the percentages (Red, Green and Blue - if you don't have the percentages select RGB from the drop down menus).

3. Fire up your Calculator and make the calculations yourself. You have to multiply 65535 with the percentage of the color.
In my example Red is at 38% so you have to multiply 65535 by 0.38 and you get 24903,3 - just round it up to the smaller or bigger number, I usually take the bigger one so I get 24904 for Red.
Do the same for the other colors.

4. Input the colors in the same orders (Red, then Green, then Blue) into the field in the gconf utility.

That's it! :)

---

### Post by the_thunderbird on 2006-07-28
> **agurk said:**
> Yep, works now, thanks! The USP button doesn't adhere to the opacity level set for the panel though (see pic).
Oh, and the Screen Resolution button text did not show my resolution until I had run the screen res selection app once.

I've just fixed this and Chanders will release it when he comes online ;)

---

### Post by Note360 on 2006-07-28
Another great improvement chanders.

---

### Post by ironfistchamp on 2006-07-28
Just got the new version. It's looking great. Something I notcied on two machines is that if I log off or shutdown with programs open I get a message saying that X doesn't support session saving. 

I think it is related to the panel. Maybe you could look into it. Has anyone else noticed this?

Ironfistchamp

---

### Post by Hells_Dark on 2006-07-28
> **Hells_Dark said:**
> Thanks for the new release.

But i still having some problem with my GNOME icon theme.
[[img]http://pix.nofrag.com/d0/ae/5abab79760ea40b574fea23c4061t.jpg[/img]](http://pix.nofrag.com/d0/ae/5abab79760ea40b574fea23c4061.html)

Is anybody have the same problem or, could tell me if he have the same when he put the GNOME theme icon ?
Edit : i asked to some people (2), they say they have the same.
So what's about this ? There is this bug with a lot of themes, that's quite important, isn't it ? :sad:

PS: i was already talking about it [here](http://ubuntuforums.org/showpost.php?p=1303250&postcount=126).

Another screenshot to visualize problems :
[[img]http://pix.nofrag.com/20/aa/67a5871d011a2fda963e44b07129t.jpg[/img]](http://pix.nofrag.com/20/aa/67a5871d011a2fda963e44b07129.html)

(I just ask if that's a priority, i know Chanders is sooo busy ;-) )

---

### Post by xtacocorex on 2006-07-28
This is by far the fastest I've seen development on a program that is very usable. 

I will have to get the newest version tonight (since I'm about 3 or so behind now), when I get home.

Keep up the good work chanders!

An idea for the tall panel height problem:
Is there a gconf entry that specifies the height of the gnome-panel? If there is, couldn't you read that entry, and then have it draw the menu starting from that height location? From the little GTK I know, I'm sure that you can control where the window goes with coordinates.

(Opened up X forwarded ssh to find info)

Ok, that's way to slow for me to use to find useful stuff.

Back to the idea. Once you read the panel height, you'd also have to read the panel location and then draw the offset accordingly, who knows, someone may have a really thick panel at the top, odd to me, but useful to them. 

Sorry for the randomness in the idea, I was trying to inline prove some of the concepts, but couldn't as ssh with -X is slow at my office for my work computer.

EDIT: (To clean up the idea after slowly searching around gconf-editor for a fifth time)
1 - On add to panel, USP sets a gconf key telling itself what panel it is set on
2 - On add to panel/panel size change, USP (re)sets a gconf key telling itself the height of the panel
3 - USP sets menu offset coordinates based upon the above 2 items (also gconf keys so it knows what to load on login/logout)
4 - User click will draw menu offset from panel as it knows what to do

I'll keep researching this option.

---

### Post by Amaranth on 2006-07-28
Icon loading code: (never tested, based on alacarte's code)
```
def getIcon(item):
	pixbuf = None
	if item == None:
		return None
	if isinstance(item, str):
		iconName = item
	else:
		iconName = item.get_icon()
	if iconName and not '/' in iconName and iconName[-3:] in ('png', 'svg', 'xpm'):
		iconName = iconName[:-4]
	icon_theme = gtk.icon_theme_get_default()
	try:
		pixbuf = icon_theme.load_icon(iconName, 24, 0)
	except:
		if iconName and '/' in iconName:
			try:
				pixbuf = gtk.gdk.pixbuf_new_from_file_at_size(iconName, 24, 24)
			except:
				pass
		if pixbuf == None:
			if item.get_type() == gmenu.TYPE_DIRECTORY:
				iconName = 'gnome-fs-directory'
			elif item.get_type() == gmenu.TYPE_ENTRY:
				iconName = 'application-default-icon'
			try:
				pixbuf = icon_theme.load_icon(iconName, 24, 0)
			except:
				return None
	if pixbuf == None:
		return None
	if pixbuf.get_width() != 24 or pixbuf.get_height() != 24:
		pixbuf = pixbuf.scale_simple(24, 24, gtk.gdk.INTERP_HYPER)
	return pixbuf

```

Of course to use this as-is you have to be using python-gmenu.

---

### Post by _profox on 2006-07-28
> **chanders said:**
> * I Cant really do anything about the missing title other than put a placement like "Edit me!" or something....
You could use the "subtitle" (Name) to become the title (Generic name) and make the "subtitle" (Name) empty, perhaps?

---

### Post by LordMau on 2006-07-28
Hi. Just upgraded to 0.27 USP. With reference to my previous posts some comments:

a) Nautilus now behaves properly, doesnt override xfce desktop nor sessions manager; Places now opens ok!

b) Quit.. button still doesn't work.

c) Thunar (and its other .desktop variations) do not open, either as a Favorite in the main panel, or via the application browser. So far this is the only app that does this.

So far those are what I've seen. Otherwise great update, and I hope the above can help in tweaking USP.

Thanks!

---

### Post by chanders on 2006-07-28
> **_profox said:**
> You could use the "subtitle" (Name) to become the title (Generic name) and make the "subtitle" (Name) empty, perhaps?

This was addressed in 0.27-1, you can now swap between Name and Generic name, so no more spaces :D 

> **LordMau said:**
> Hi. Just upgraded to 0.27 USP. With reference to my previous posts some comments:

a) Nautilus now behaves properly, doesnt override xfce desktop nor sessions manager; Places now opens ok!

b) Quit.. button still doesn't work.

c) Thunar (and its other .desktop variations) do not open, either as a Favorite in the main panel, or via the application browser. So far this is the only app that does this.

So far those are what I've seen. Otherwise great update, and I hope the above can help in tweaking USP.

Thanks!

* Quit will not work as USP is using gnome's logout command. If you can tell me what is the command to logout of the XFCE desktop I could probably include it..
* Post the lines in your thunar.desktop file here so I can look at it.. (without the translations so it will be smaller)

---

### Post by Hells_Dark on 2006-07-28
> **chanders said:**
> This was addressed in 0.27-1, you can now swap between Name and Generic name, so no more spaces :D 


Yeah, that's great !
But there is a bug :
When we edit the labels, it switch automatically..

---

### Post by _profox on 2006-07-28
> **chanders said:**
> This was addressed in 0.27-1, you can now swap between Name and Generic name, so no more spaces :D 

Oh, sorry ;) I was reading all 21 pages and came across this in the middle.. Anyway, you're razing along with development! And you listen to your userbase alot.
Very good :) very good :)

I am hacking into the python code a little bit to try to fix some bugs and/or add some functionality, but I'm not very experienced with python yet :) but it's a good way to learn.

About the website; is it taken care of?
Is 25GB bandwidth/month enough?
Then I can probably create and host a website for you on my hosting :)

---

### Post by chanders on 2006-07-28
> **Hells_Dark said:**
> Yeah, that's great !
But there is a bug :
When we edit the labels, it switch automatically..

Ahh.. oversight... will be fixed in the next release..

---

### Post by LordMau on 2006-07-28
> **chanders said:**
> * Quit will not work as USP is using gnome's logout command. If you can tell me what is the command to logout of the XFCE desktop I could probably include it..

Not sure if I can tell the command, may ask around, but I'm not sure there's any difference between gnome and xfce logout. Curious though as the default Gnome Menu and gnome-main-menu/slab/uslab logout/exit button work fine.

> **chanders said:**
> * Post the lines in your thunar.desktop file here so I can look at it.. (without the translations so it will be smaller)

Here's the default one:

```

[Desktop Entry]
Encoding=UTF-8
Name=Thunar File Manager
<snip>
Comment=Browse the filesystem with the file manager
<snip>
GenericName=File Manager
<snip>
Exec=Thunar %F
Icon=Thunar
Terminal=false
StartupNotify=true
Type=Application
Categories=Application;System;Utility;Core;GTK;FileManager;

# vi:set encoding=UTF-8:
X-Ubuntu-Gettext-Domain=Thunar


```

Here's the one in the .usp folder:

```

[Desktop Entry]
Encoding=UTF-8
Name=Thunar File Manager
Comment=Browse the filesystem with the file manager
Exec=Thunar %F
Icon=Thunar
GenericName=File Manager
Terminal=false

```

Also launching via nautilus or thunar the .desktop file in .usp also successfully launches Thuanr.

Thanks.

---

### Post by chanders on 2006-07-28
Ok just as a test, remove the %F in the file in .usp folder...
Remove the applet and re-add it..
Tell me if it works...

---

### Post by Note360 on 2006-07-28
I think I have the hosting all patched up with 50gb per month, however I have   another site running on the server so we will see how good it holds up. Just send the stuff over when your ready chanders. i'll put it up at zephyrwood.org/chanders

---

### Post by chanders on 2006-07-28
> **Note360 said:**
> I think I have the hosting all patched up with 50gb per month, however I have   another site running on the server so we will see how good it holds up. Just send the stuff over when your ready chanders. i'll put it up at zephyrwood.org/chanders

Excellent... New release in a few hrs ;)

---

### Post by gruvsyco on 2006-07-28
Here's something, perhaps not related directly to USP...  I notice some of my apps when favorited, are only one line.  If I add Rhythm Box for example, it shows in the menu like:

Music Player
Rhythm Box Music Player

But, if I certain other apps like, Blender, it only shows:

Blender 3D modeller

and, the text appears as if it is the second line and the first line is blank.  So, is there a way to fix this either by:
A.  adding the appropriate text for items missing it.
B.  removing the first line from the ones that do have it.
C.  centering the ones that don't so it's inline with the icon


BTW, I switched from Slab to USP this morning... far enough along now I like it better.

BTW 2.0, Congratulations on getting your own forums for USP and UCC!

---

### Post by chanders on 2006-07-28
> **gruvsyco said:**
> Here's something, perhaps not related directly to USP...  I notice some of my apps when favorited, are only one line.  If I add Rhythm Box for example, it shows in the menu like:

Music Player
Rhythm Box Music Player

But, if I certain other apps like, Blender, it only shows:

Blender 3D modeller

and, the text appears as if it is the second line and the first line is blank.  So, is there a way to fix this either by:
A.  adding the appropriate text for items missing it.
B.  removing the first line from the ones that do have it.
C.  centering the ones that don't so it's inline with the icon


BTW, I switched from Slab to USP this morning... far enough along now I like it better.

BTW 2.0, Congratulations on getting your own forums for USP and UCC!

Thanks!

Ok, two ways to solve your problem...
1. Right click on the item, select edit, and enter the labels yourself
2. In gconf-editor, check swap_generic_name (that way you wont have any blanks ;-) )

---

### Post by _profox on 2006-07-28
> **augied said:**
> Feature request/suggestion: Have the places section work with the gtk-bookmarks file.  The syntax of the file is a little different from the places.list file that is currently used, but I don't think it would be too hard to do (that said, I I'm not sure how to do it.)
Where is the gtk-bookmarks file? I can't find it :confused:

---

### Post by gruvsyco on 2006-07-28
> **chanders said:**
> Thanks!

Ok, two ways to solve your problem...
1. Right click on the item, select edit, and enter the labels yourself
2. In gconf-editor, check swap_generic_name (that way you wont have any blanks ;-) )

Thanks that worked but I just realized something else now... "All Applications" is not showing all my applications now.  They still show in the original Gnome Menu and are available via Alt-F1

---

### Post by chanders on 2006-07-28
Are thay showing any at all?  Applications that dont have proper .desktop files are not shown (for now) I will have to fix that later

---

### Post by _profox on 2006-07-28
> **_profox said:**
> Where is the gtk-bookmarks file? I can't find it :confused:
Seems like Nautilus doesn't make use of this file for its locations.

I was working on an option to "sync with nautilus locations" but it seems like the nautilus locations aren't very user configurable by default.
Maybe you mean something else with the gtk-bookmarks file? what do you have in the file? It could be that you added some custom stuff somewhere..

But since this certainly isn't the case for most people, I think I am going to do it like this:

When you open the new USP the first time it will check wether you already have places or not, if you have no places, these default places will be added automatically:

Default places is: desktop, home folder, computer, cd/dvd, networkservers

If you already have places, your places will remain the same.

But: 2 new options will also be added to the right click menu of "Places"
edit: this will be a new popup menu when you right click the LABEL Places
- Clear all places [needs confirmation]
- Add default places

The first option will clear all your places, and the second option will append the default places to your current places.

Is this a good way to solve this? Now the only thing I'm looking for is an easy way to find the information I need. Are those default locations saved somewhere? They are taken from the default ubuntu menu -> locations, but I don't know where it gets its info from...

Edit: think I found it, give me some time

---

### Post by gruvsyco on 2006-07-28
> **chanders said:**
> Are thay showing any at all?  Applications that dont have proper .desktop files are not shown (for now) I will have to fix that later

Yes it does show some apps.  Come to think of it, an early version of your USP that opened a window to an apps folder, I think was missing these same apps so, likely they don't have a proper .desktop file associated with them.

---

### Post by dcubed20 on 2006-07-28
This is really great. I have a few feature requests, though. First off, I think it ought to behave like the gnome-menu does with respect to when you click off it. When I want to close the gnome-menu, I never re-click the menu icon; i just click somewhere else on the screen and the menu closes. I think USP should do the same thing. Also, I like the "quick find" feature for applications, but it would be nice to be able to operate the entire thing from the keyboard. Here's an example:

The way it works now: you click in the quick find box, you type whatever you want, you click the option(s) that appear above.

The way I think it should work: you click in the quick find box, you type whatever you want, you either press enter (if there is only one result) and the program opens, or you choose which result you want with arrow keys and press enter.

I think these things would do a lot for functionality, and I bet other people would agree too. Thanks for all the hard work you're putting in to this.

---

### Post by _profox on 2006-07-28
> **dcubed20 said:**
> This is really great. I have a few feature requests, though. First off, I think it ought to behave like the gnome-menu does with respect to when you click off it. When I want to close the gnome-menu, I never re-click the menu icon; i just click somewhere else on the screen and the menu closes.
This should happen with USP too, IF you have the Pin button in the off state (small button in the upper left corner) Try it, if it doesn't work, you are the 2nd person that has experienced this. This shouldn't happen if the Pin button is off.

> **dcubed20 said:**
> Also, I like the "quick find" feature for applications, but it would be nice to be able to operate the entire thing from the keyboard. Here's an example:

The way it works now: you click in the quick find box, you type whatever you want, you click the option(s) that appear above.

The way I think it should work: you click in the quick find box, you type whatever you want, you either press enter (if there is only one result) and the program opens, or you choose which result you want with arrow keys and press enter.
This is already in the feature list :) In the future it's probably going to be user configurable. Atleast if chanders finds the time to program all these wishes, AND fix the little bugs ;) But he's doing his very best.

---

### Post by _profox on 2006-07-28
I have to catch some sleep now, but the 'auto populate' for the places menu, when it's empty, should be done tomorrow :) maybe in some hours if I can't sleep. (It's late here)

---

### Post by dcubed20 on 2006-07-28
> **_profox said:**
> This should happen with USP too, IF you have the Pin button in the off state (small button in the upper left corner) Try it, if it doesn't work, you are the 2nd person that has experienced this. This shouldn't happen if the Pin button is off.


Oh so thats what that does. Lol, thanks.

> 
This is already in the feature list :) In the future it's probably going to be user configurable. Atleast if chanders finds the time to program all these wishes, AND fix the little bugs ;) But he's doing his very best.

I didn't see it in the list, but that's good to know. Don't get me wrong, I don't want to rush chanders, and I really appreciate all the hard work he is putting into it. I thought I'd contribute my two cents, that's all.

---

### Post by chanders on 2006-07-28
Ver 0.28-1 28 Jul 21:30:00 (GMT -4)
* Applet follows panel transparency settings (Thanks the_thunderbird)
* Search entry set to auto-clear when clicked
* Icon theme problems fixed
* 'Quit' text mis-alignment fixed
* Fixed bug when entry was edited and swap_generic was set
* Filter now includes application command name
* 'Filter' label removed
* 'More Applications' button repositioned and white space removed
* Now accepts color in the format #RRGGBB (Thanks PsyberOne)

Notes:
See 'currently working on' thread to know what is in the pipeline
Add your wishlist to the 'What I would like to see' thread
Add screenshots to 'Screenshots' thread

---

### Post by Note360 on 2006-07-28
What happened?

---

### Post by chanders on 2006-07-28
> **Note360 said:**
> What happened?

Huh? ;)

---

### Post by delfick on 2006-07-28
i think he just woke up after a big night with lots of alcohol and doesn't know where he is :p

---

### Post by chanders on 2006-07-28
@Note360
You mean getting the forum dont you :)

---

### Post by Note360 on 2006-07-28
Ya I went to see a Jazz Saxaphonist and eat and stuff for the past 4 hours and I have no Idea what is going on with the forums I come back and I am like wtf

---

### Post by chanders on 2006-07-28
> **Note360 said:**
> Ya I went to see a Jazz Saxaphonist and eat and stuff for the past 4 hours and I have no Idea what is going on with the forums I come back and I am like wtf

Tell me about it ;) Now we have our own little place to do all the configuring and tinkering that we like...

---

### Post by Note360 on 2006-07-28
Lol without Viper

---

### Post by lazyd2 on 2006-07-28
> **Note360 said:**
> Lol without Viper:lol::-\"

---

### Post by Note360 on 2006-07-28
dang my panel border wotn change colour

---

### Post by lazyd2 on 2006-07-28
Remove it and add it again.

---

### Post by Note360 on 2006-07-28
Er thanks that was a stupid problem

---

### Post by chanders on 2006-07-28
Ver 0.29 out (fixes window settings especially for compiz users)

---

### Post by darkmatter on 2006-07-29
ummm... bugs r back (looks mostly like gconf stuff)

```
Traceback (most recent call last):
  File "/usr/bin/usp", line 1517, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1508, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1373, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 93, in __init__
    self.Todos()
  File "/usr/bin/usp", line 584, in Todos
    openfile = open(self.get_file_path(path), 'r')
IOError: [Errno 13] Permission denied: '/home/darkmatter/.local/share/applications/googleearth.desktop'
```

---

### Post by delfick on 2006-07-29
> **chanders said:**
> Ver 0.29 out (fixes window settings especially for compiz users)

where can this gotten from?

---

### Post by augied on 2006-07-29
> **delfick said:**
> where can this gotten from?

There should be a separate thread for releases and release notes

---

### Post by delfick on 2006-07-29
just found it...the first post of this thread....:D

thnx Chanders...it wobbles again :D

---

### Post by LordMau on 2006-07-29
> **chanders said:**
> Ok just as a test, remove the %F in the file in .usp folder...
Remove the applet and re-add it..
Tell me if it works...

Great that worked! Thanks. Hope you can also check out the logout/ exit button thing.

---

### Post by Hells_Dark on 2006-07-29
Hi,

Thanks for the new release.
My Gnome Theme icon is supported :)

Anyway, i still have a size problem with it :
[[img]http://pix.nofrag.com/54/64/996caaa6844f6e6c673b0f58c8eet.jpg[/img]](http://pix.nofrag.com/54/64/996caaa6844f6e6c673b0f58c8ee.html)

(i'll post it in the bugs topic ;))

But, that's a really good job Chanders ;)

Edit : and what about the languistic support ?
How to translate the app' ?

---

### Post by _profox on 2006-07-29
Languistic support is also planned for the future :) but we have a very big wishlist that is being added to daily ;) hmm.. I think we should make a little php page so people can vote for the most wanted features/wishes.

---

### Post by Hells_Dark on 2006-07-29
> **_profox said:**
> Languistic support is also planned for the future :) but we have a very big wishlist that is being added to daily ;) hmm.. I think we should make a little php page so people can vote for the most wanted features/wishes.

Ok, thanks :)
My main wish remains the bugs suppression ^_^
And this ugly size icon problem, i talked about earlier.

---

### Post by _profox on 2006-07-29
Hey guys, I need some help, so I can continue with the auto-population.

The only thing I miss is the cd/dvd right now. I don't know where the gnome menu gets that information from.
It doesn't appear when unmounted, so how does it know?
Someone please enlighten me.

---

### Post by _profox on 2006-07-29
Maybe I can check "mount" and find iso9660 and use that mount point to create a .desktop file? would this be a good solution?

---

### Post by _profox on 2006-07-29
I came across some bugs:
+ Can't drag desktop to places (Fixed! Also fixed icon. See below.)
+ The ".." delimiter that is used when place/app names are too large doesn't care about the font size or about the width of the letters ~ low priority
+ Can't drag cd drives from Computer into USP
+ cd drives dragged from menu have no correct icon
And the "ghost icon drag" bug is still flying across the screen ;) :(

In my auto populate function I also ran into a problem. I'm searching for a good way to find all cd/dvd devices attached to the computer. Until then I'm stuck here. But I will auto populate with "Home, Desktop, Computer and Network servers" in one of the following releases :) cd/dvd devices maybe later. (when I find some info for the cd/dvd devices)

Here is the fix so you can drag the desktop:
I hope it's clean enough :)

(manually delete the lines with - and add the lines with +, i used diff so it is more clear in which context you need to change things, paste the code in an editor that supports syntax highlighting for .diff files, like gedit, and use diff highlighting (or save as a .diff file) and you will see in colors what you need to change)

EDIT: Removed patch. See next post.

---

### Post by _profox on 2006-07-29
I modified the source code to add 4 places if you start the program for the first time (if you have none that is)

I also want to create a popupmenu. Rightclick on the label "Places"
~ Clear all (backs up current places.list and /places to places.backup and /places-backup, then removes places.list and /places, then removes all the places buttons)
~ Restore cleared (removes current places.list and /places and places the backups back, and reloads the places buttons)
~ Add default places (appends 4 default places like happens in my code below to the current places)

I am able to write the code for this, but I'm not sure how/where to add the code for the popupmenu. I'm a rookie in Python :) 1 day now, but I like Python, and I love the way you HAVE to structurize your sourcecode :)

And I still have the second problem, but I will just leave it as it is for now, with the CD/DVD devices. I'm not sure what's the best way to obtain all CD/DVD devices attached.

----

Patch Description: On startup we check wether there are places or not. If there are none, 4 default places  (5 if you count the space) get added automatically. (home, desktop, [space], computer, network servers)

Includes the fix of my previous post so you can add the Desktop entry to your Places

Includes the fix of my previous post so you can hardcode other icon entries for directories (like we did for Desktop)

Attached patch:
```
--- usp	2006-07-29 05:43:27.000000000 +0200
+++ usp	2006-07-29 17:58:21.000000000 +0200
@@ -148,8 +148,16 @@
 
         PlacesFile = open (os.path.join(os.path.expanduser("~"), ".usp/places.list"),"r")
         PlacesList = PlacesFile.readlines()
-        for i in range(len(PlacesList)):
-            self.Add_Button(PlacesList[i][:-1],"place",True)
+        if len(PlacesList) == 0:
+            print "Empty places.list: Populating"
+            self.Add_Button("/usr/share/applications/nautilus-home.desktop","place",False)
+	    self.Add_Button(os.path.join(os.path.expanduser("~"),"Desktop"),"place",False,"gnome-fs-desktop")
+	    self.Add_Button("space","place",False)
+            self.Add_Button("/usr/share/applications/nautilus-computer.desktop","place",False)
+	    self.Add_Button("/usr/share/applications/network-scheme.desktop","place",False)
+        else:
+            for i in range(len(PlacesList)):
+                self.Add_Button(PlacesList[i][:-1],"place",True)
 
         ApplicationsFile = open (os.path.join(os.path.expanduser("~"), ".usp/applications.list"),"r")
         ApplicationsList = ApplicationsFile.readlines()
@@ -456,6 +464,9 @@
         return True
 
     def got_data(self, widget, context, x, y, selection, targetType, timestamp):
+        customIcon = ""
         if widget.name == "scrolledwindow1":
             Add_to = "application"
         if widget.name == "scrolledwindow2":
@@ -472,9 +483,12 @@
         if selection.data[:-2] == 'x-nautilus-desktop:///network':
             data = '/usr/share/applications/network-scheme.desktop'
             specialcase = True
-
+        if selection.data == 'Desktop':
+            data = os.path.join(os.path.expanduser("~"),"Desktop")
+            specialcase = True
+            customIcon = "gnome-fs-desktop"
         if specialcase:
-            self.Add_Button(self.get_file_path(data),Add_to,False)
+            self.Add_Button(self.get_file_path(data),Add_to,False,customIcon)
         else:
             self.Add_Button(self.get_file_path(selection.data),Add_to,False)
 
@@ -676,7 +690,7 @@
 
 
 
-    def Add_Button(self,selection,where,Init):
+    def Add_Button(self,selection,where,Init,customIcon=""):
 
         PlaceName=PlaceComment=PlaceExec=PlaceIconName=GenericName=WhatWasDropped=""
         FileExists=False
@@ -915,7 +929,11 @@
 
                 print PlaceName
                 PlaceExec = "nautilus "+ self.get_file_path(selection)
-                PlaceIconName = "gnome-fs-directory"
+		if customIcon == "":
+		    PlaceIconName = "gnome-fs-directory"
+		else:
+		    PlaceIconName = customIcon
+
                 PlaceIcon = self.get_proper_icon(PlaceIconName,icon_size)
 
                 Button1 = gtk.Button(Button_Name,"ok",True)

```

---

### Post by chanders on 2006-07-29
> **_profox said:**
> I modified the source code to add 4 places if you start the program for the first time (if you have none that is)

I also want to create a popupmenu. Rightclick on the label "Places"
~ Clear all (backs up current places.list and /places to places.backup and /places-backup, then removes places.list and /places, then removes all the places buttons)
~ Restore cleared (removes current places.list and /places and places the backups back, and reloads the places buttons)
~ Add default places (appends 4 default places like happens in my code below to the current places)

I am able to write the code for this, but I'm not sure how/where to add the code for the popupmenu. I'm a rookie in Python :) 1 day now, but I like Python, and I love the way you HAVE to structurize your sourcecode :)

And I still have the second problem, but I will just leave it as it is for now, with the CD/DVD devices. I'm not sure what's the best way to obtain all CD/DVD devices attached.

----

Patch Description: On startup we check wether there are places or not. If there are none, 4 default places  (5 if you count the space) get added automatically. (home, desktop, [space], computer, network servers)

Includes the fix of my previous post so you can add the Desktop entry to your Places

Includes the fix of my previous post so you can hardcode other icon entries for directories (like we did for Desktop)



Good work.. I will try to implement it in the next release.. It seems a lot of people have gripes with the way the All Applications section works/sorts, so I am going to focus on getting this working before any more cosmetic items are done.

Feel free however to hack the code and come up with new and interesting ideas.. I will need them when I am ready to continue with the layout/looks ;)

---

### Post by Note360 on 2006-07-29
I have one question how did you make it I mean where did you start and how did you make a panel applet? It all seems so impossible to me.

---

### Post by chanders on 2006-07-29
> **Note360 said:**
> I have one question how did you make it I mean where did you start and how did you make a panel applet? It all seems so impossible to me.

Hours and hours of digging and asking... The hardest part and the one tha really gets me angry is that we have all of this technology and no documentation for it...

I will gladly write a howto but I really hope the GNOME devs are listening! and in the words of **the_thunderbird** "Shame on you GNOME devs!!"

---

### Post by Note360 on 2006-07-29
Hey if you want to document your adventures that would be great and also be a great insight on how to do something like this and would become a very nice learning tool

BUT for now please concentrate at working on this.

---

### Post by _profox on 2006-07-29
I didn't know Python was this fun ;) and it's pretty straight-forward :) I've been using it for 1 day now :D I love this language.

---- And now some real news ;) ----

Fixed another bug! Applications that needed = in their filename (example: evolution --component=mail) would stop working after they were edited by the EditDialog. The EditDialog didn't correctly read out lines with multiple ='s

EDIT: I changed the patch to be a few microseconds FASTER :) The old code is commented out, you don't have to include it anymore

Patch:

```
--- usp	2006-07-29 05:43:27.000000000 +0200
+++ usp	2006-07-29 21:44:33.000000000 +0200
@@ -38,11 +38,11 @@
         #Get the actual dialog widget
         self.dlg = self.wTree.get_widget("dialog1")
 
-        self.wTree.get_widget("entry2").set_text(Data[2][:-1].split("=")[1])
-        self.wTree.get_widget("entry3").set_text(Data[6][:-1].split("=")[1])
-        self.wTree.get_widget("entry4").set_text(Data[3][:-1].split("=")[1])
-        self.wTree.get_widget("entry5").set_text(Data[4][:-1].split("=")[1])
-        self.wTree.get_widget("entry6").set_text(Data[5][:-1].split("=")[1])
+        self.wTree.get_widget("entry2").set_text(Data[2][:-1][Data[2][:-1].find("=")+1:])
+        self.wTree.get_widget("entry3").set_text(Data[6][:-1][Data[6][:-1].find("=")+1:])
+        self.wTree.get_widget("entry4").set_text(Data[3][:-1][Data[3][:-1].find("=")+1:])
+        self.wTree.get_widget("entry5").set_text(Data[4][:-1][Data[4][:-1].find("=")+1:])
+        self.wTree.get_widget("entry6").set_text(Data[5][:-1][Data[5][:-1].find("=")+1:])
 
         #run the dialog and store the response
         self.result = self.dlg.run()
```

Function from the old code, but you DO NOT need this anymore! :)
```
@@ -58,6 +58,19 @@
         self.dlg.destroy()
         return GotData
 
+# (debug)
+# I optimized this code by using .find instead of split.
+# directly in the code above (def run)
+#
+# Please remove these comments
+# if the new method works better
+#
+#    def GetAllData(self,Data):
+#	strResult=""
+#	for i in range(len(Data.split("="))-1):
+#	    strResult = strResult + Data.split("=")[i+1]
+#
+#	return strResult
 
 class MainWindow:
     """This is the main class for the application"""
```

---

### Post by Hells_Dark on 2006-07-29
Really nice _profox :)

If you could find an answer for my bug...
To visualise it, just take the GNOME icon theme, and you'll see.

I would like to start to make python too..
It's a pretty language :P.
I don't know where to start.

---

### Post by Note360 on 2006-07-29
Lol i feel so behind I have been reading through the official Python manual for a couple of days now. (I am a failure) Lol. but seriously how did you progress so fast?

---

### Post by chanders on 2006-07-29
> **Note360 said:**
> Lol i feel so behind I have been reading through the official Python manual for a couple of days now. (I am a failure) Lol. but seriously how did you progress so fast?

Dont be fooled. Python is easy *if you have done programming before*. Have you done any programming before? 

I am happy that **profox** is able to work out some of the bugs while I work on the important things. What programming background do you have **profox**? Keep up the good work (and document your patches well). I am nearly through with the gmenu (Yay!) so we could hopefully expect a new release...hmmmmm.... today? ;)

---

### Post by lazyd2 on 2006-07-29
> so we could hopefully expect a new release...hmmmmm.... today? Gimme....

---

### Post by _profox on 2006-07-29
Yes, I've done programming before. But I'm ashamed to admit that it was on Windows with Visual Basic.

My last projects were my own multisock webserver + web interpreter language and my own multisock messenger server + clients

I read 0 documentation about Python, I just opened the source and tried to understand it. If you've done programming. Alot of things in the source make sense. It's not a complicated language.

When I encounter a problem, or I want to write some code myself, I just search Google, or I visit the official Python documentations, that's what I did to improve my previous patch, and I found String Methods. Which is a very nice/flexible thing by the way! Python rocks

I am planning to borrow/buy a Python book sometime soon, but for now, I'm just hacking and getting familiar with the code, and it's turning out well. I can't do complicated tasks, but I will be able to solve some small bugs and maybe even program some small wishes.

I'm nothing compared to chanders when it comes to programming in Python, because I have to relearn a whole new language, but because I have done programming before I have the ability to analyse and debug, and that's the most important thing in programming.

@chanders, I really do use too many smilies don't I? "You have included 9 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again."
Just because of that: a smilie-less post now :) (pun intended)

---

### Post by Note360 on 2006-07-29
Ya I know some basic Perl but I left that for Python. What really gets me is OO Programming.

---

### Post by Note360 on 2006-07-29
Oh I think I am going to join the project it is probably the best thing for me. So let me at it (or more correctly) please let me get into a elevator with padding bring me up to the top level of the tower of terror and drop me at freefall while have some one banging coconuts they got off a swallow with a low wing velocity behind me.

(lol one of the reasons I want to learn python is because of monty python)

---

### Post by _profox on 2006-07-29
Which is a very good reason! :) Monty python for teh win !! ;)
Anyway, most source code is available after installation here:

/usr/bin/usp

So to get your paws/hands on it, here's what I do:

I make a copy of it:
sudo cp /usr/bin/usp /usr/bin/uspx

And I start hacking by opening uspx in a text editor like "gedit", but I'm going to try out something else soon. Chanders uses "easyeclipse for python"

That's all you need, basically.
The Glade file for the GUI can be found in /usr/share/usp/usp.glade
But I haven't worked with that yet

After you made some changes, just save the uspx file (you don't need to close the editor ofcourse)
and then to try it out, execute this command:

/usr/bin/uspx run-in-window

It will create a new window with the button, so you can still use your real USP (which runs as /usr/bin/usp)

good luck :)

---

### Post by Note360 on 2006-07-29
k sounds good but we should set some sort of thing up where we all decide to fix certaint bugs because if we all start fixing the same bug its pointless.

---

### Post by Note360 on 2006-07-29
dang, I have to reinstall cause I was fooling around with Xubuntu and it uninstalled all my c gnome packages (I was trying to get gnome applets in xfce). This sucks.

---

### Post by _profox on 2006-07-29
a bugtraq would be nice, yes... you were working on the site, right? create a bugzilla or launchpad page or something like that :)

---

### Post by _profox on 2006-07-29
Are there any more bugs that you would like to see fixed? Try some things and let me know! :) I want to fix some (easy) bugs ;)

---

### Post by Note360 on 2006-07-29
Oh I didnt work on the site yet. Er I have to back up I'll be back tomorrow.

---

### Post by Hells_Dark on 2006-07-29
> **_profox said:**
> Are there any more bugs that you would like to see fixed? Try some things and let me know! :) I want to fix some (easy) bugs ;)

My bug, my bug ^^ 
[http://ubuntuforums.org/showpost.php?p=1314048&postcount=5](http://ubuntuforums.org/showpost.php?p=1314048&postcount=5)
That's probably an easy bug, isn't it ?
There's a size icon bug with a lot of themes :)

---

### Post by chanders on 2006-07-29
> **Hells_Dark said:**
> My bug, my bug ^^ 
[http://ubuntuforums.org/showpost.php?p=1314048&postcount=5](http://ubuntuforums.org/showpost.php?p=1314048&postcount=5)
That's probably an easy bug, isn't it ?
There's a size icon bug with a lot of themes :)

LOL... I think this is a theme bug.. In fact I am SURE it is a theme dependant bug but _profox can take a look if he's bored ;)

---

### Post by _profox on 2006-07-29
> **chanders said:**
> LOL... I think this is a theme bug.. In fact I am SURE it is a theme dependant bug but _profox can take a look if he's bored ;)
Yes, but you are rewriting this piece of code with gmenu... So I better wait for the next version :)

Anyway, just ask about bugs in the bugs thread :) I will check there for the bugs

---

### Post by handy on 2006-07-30
Perhaps the following link to a **[learning how to program in Python course]("http://www.freenetpages.co.uk/hp/alan.gauld/")** published on the web & downloadable too! Will be of use to someone, who has become inpired by this thread to take up Python developement?

I am constantly amazed by how we continuely effect each other by our actions...  Most often without any intention to do so, or any idea that we have done so!?  

Eh! Chanders? :KS

---

### Post by chanders on 2006-07-30
New Release 0.30 on the 30th ;)

Date: Sun, 30 Jul 2006 00:44:10 -0400
* Fixed 'All Applications' to follow GNOME menu
* Added option to show 'All Applications' from start
* Added option to filter/not filter application on entry
* Places now auto populate if empty (thanks profox)
* Entry always gets focus on USP open
* Fixed evolution '=' bug (thanks profox)
* USP now auto-apply settings when changed in gconf-editor
* Added option for Toggle icons
* Added option to hide Toggle bar
* 'Computer' label set higher
* Quit icon changed to match theme
* Removed space between applications and search entry
* Entry grabs focus when USP is open
* Entry auto-clears when USP is closed

I couldnt add all the features (not enough hours in the day ;) but I will continue work tomorrow)

Tip: Try out the toggle button icons...

---

### Post by delfick on 2006-07-30
cool....:D

i like the toggle button icons...
and the removal of space between search bar and applications...
and the other things you fixed...:D

will it be possible at some stage to be able to add icons to the toggle bar side thing...like the places icons?

that would be cool....

ur menu rocks!

edit: like my (dodgy) mockup here....(basically the places icons on the left) [http://delfick755.googlepages.com/icons.png](http://delfick755.googlepages.com/icons.png)

---

### Post by chanders on 2006-07-30
> **delfick said:**
> cool....:D

i like the toggle button icons...
and the removal of space between search bar and applications...
and the other things you fixed...:D

will it be possible at some stage to be able to add icons to the toggle bar side thing...like the places icons?

that would be cool....

ur menu rocks!

edit: like my (dodgy) mockup here....(basically the places icons on the left) [http://delfick755.googlepages.com/icons.png](http://delfick755.googlepages.com/icons.png)

Sure! that would be easy, but what would they be for?

---

### Post by gruvsyco on 2006-07-30
Chanders, I don't know if you have Slab installed but... since you have mostly incorporated the features of its seperate application browser right into USP, I was wondering if you could also add a little more...

right now, if I'm in All Applications on your menu, when I right click on an item I get:

Add to Faovrites

However, when I right click in Slab's App Browser I get:

Start *Application name*
------------------------
Help (or Help Unavailble greyed out)
------------------------
Add to Favorites
Add to Startup Programs
Upgrade
Uninstall

I mostly want the Start App and the add to startup but the others might prove useful to someone else.

---

### Post by lazyd2 on 2006-07-30
Thank you again for this release...

"Swap generic name" will not auto-apply(must restart usp)<--- I don't really mind:)

and if possible at all [little bigger icons in "Places"]("http://ubuntuforums.org/showpost.php?p=1312575&postcount=14")[-o< :grin:

---

### Post by delfick on 2006-07-30
> **chanders said:**
> Sure! that would be easy, but what would they be for?

becuase i don't like having three panes as that makes the meny look worse than just two panes imho. 

i also like having the left "mini-column" with the shutdown, lock screen, and synaptic icons on the bottom and pane togglers on the top
though this means there is a big gap between the these icons. So why not add the places icons (or any other icons for that matter)  to fill the space?

that way i can still have my places icons and the menu still looks good...:D

(it makes sense to me :D)

---

### Post by chanders on 2006-07-30
> **gruvsyco said:**
> Chanders, I don't know if you have Slab installed but... since you have mostly incorporated the features of its seperate application browser right into USP, I was wondering if you could also add a little more...

right now, if I'm in All Applications on your menu, when I right click on an item I get:

Add to Faovrites

However, when I right click in Slab's App Browser I get:

Start *Application name*
------------------------
Help (or Help Unavailble greyed out)
------------------------
Add to Favorites
Add to Startup Programs
Upgrade
Uninstall

I mostly want the Start App and the add to startup but the others might prove useful to someone else.
Why would you want "start app" when you can just click it? :) 


> **lazyd2 said:**
> Thank you again for this release...

"Swap generic name" will not auto-apply(must restart usp) 

and secondly if possible at all [little bigger icons in "Places"]("http://ubuntuforums.org/showpost.php?p=1312575&postcount=14")[-o< :grin:
LOL, this is DEFINITELY going to make it in the next release, so dont worry...

---

### Post by lazyd2 on 2006-07-30
[QUOTE=chanders]LOL, this is DEFINITELY going to make it in the next release, so dont worry...[/QUOTE]Fantastic....
now I can go to sleep :mrgreen:

---

### Post by gruvsyco on 2006-07-30
> **chanders said:**
> Why would you want "start app" when you can just click it? :)
Because I accidentally, right clicked instead of left clicked, silly :P

---

### Post by _simon_ on 2006-07-30
What does "Added option to filter/not filter application on entry" mean?

I have tried enabling / disabling in gconf but can't find any change.

Edit: Worked out what the toggle icon does ;)

---

### Post by chanders on 2006-07-30
> **delfick said:**
> becuase i don't like having three panes as that makes the meny look worse than just two panes imho. 

i also like having the left "mini-column" with the shutdown, lock screen, and synaptic icons on the bottom and pane togglers on the top
though this means there is a big gap between the these icons. So why not add the places icons (or any other icons for that matter)  to fill the space?

that way i can still have my places icons and the menu still looks good...:D

(it makes sense to me :D)

I'll see what I can do... shouldnt be too difficult...:D

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> What does "Added option to filter/not filter application on entry" mean?

I have tried enabling / disabling in gconf but can't find any change.

if /apps/usp/do_not_filter is checked, applications are not filtered when you type

Try leaving the toggle pane open but check /apps/usp/use_toggle_icon and see what you get ;)

---

### Post by delfick on 2006-07-30
> **chanders said:**
> I'll see what I can do... shouldnt be too difficult...:D

awsome :D

---

### Post by _simon_ on 2006-07-30
> **chanders said:**
> if /apps/usp/do_not_filter is checked, applications are not filtered when you type

Try leaving the toggle pane open but check /apps/usp/use_toggle_icon and see what you get ;)

That sort of works for me.

If I have "All Applications" open when i try typing then nothing changes - which is great.

If I have the favourite applications open then it changes to "All Applications"

EDIT: Added to Bugs thread.

---

### Post by Note360 on 2006-07-30
> **chanders said:**
> I'll see what I can do... shouldnt be too difficult...:D

Sounds good but make it so we can toggle it off please (maybe I'll work on it)

Also please report the bugs in the Bugs topic and new Features in the What do you want to see topic please. Thank you very much. You can still  post them here, but to make things easier for me to put stuff into the bug tracking topic please post them into bug tracking.

---

### Post by LordMau on 2006-07-30
Looking good with 0.30 BTW relative to:

> **chanders said:**
> 
* Quit will not work as USP is using gnome's logout command. If you can tell me what is the command to logout of the XFCE desktop I could probably include it..

I've checked a bit, and so I see that xfce has two relevant commands:

```

 xfce4-session
 xfce4-session-logout 

```

xfce4-session more or less is the equivalent to gnome-session. To log out, x-session-manager (linked to xfce-session) calls xfce4-session-logout (I think). Hope this helps in getting USP quit to work on my hybrid system.

Thanks!

---

### Post by chanders on 2006-07-30
> **LordMau said:**
> Looking good with 0.30 BTW relative to:



I've checked a bit, and so I see that xfce has two relevant commands:

```

 xfce4-session
 xfce4-session-logout 

```

xfce4-session more or less is the equivalent to gnome-session. To log out, x-session-manager (linked to xfce-session) calls xfce4-session-logout (I think). Hope this helps in getting USP quit to work on my hybrid system.

Thanks!
I didnt know you could run GNOME applets in XFCE :D  Well I will include an option to use whatever file manager you choose (Nautilus, konqueror, Thunar.. etc) and your quit command will also be configurable...

---

### Post by Note360 on 2006-07-30
actually I use a xfce setup to I dont know why but I do. It is, on my machine, gnome light I have the gnome panel running with USP

---

### Post by chanders on 2006-07-30
> **Note360 said:**
> actually I use a xfce setup to I dont know why but I do. It is, on my machine, gnome light I have the gnome panel running with USP

The next fix will help you too ;)

---

### Post by Note360 on 2006-07-30
Sounds good. Eventually I am going to redo the Ubuntu Control Center for Xubuntu users I just need a list of the apps (I dont use them much).

---

### Post by LordMau on 2006-07-30
> **chanders said:**
> I didnt know you could run GNOME applets in XFCE :D  Well I will include an option to use whatever file manager you choose (Nautilus, konqueror, Thunar.. etc) and your quit command will also be configurable...

Well not directly, gnomeapplets still run via gnome-panel. Had to kill xfce-panel to do so, since I just WANTED to run USP ahehe.

Great to hear your considering our inputs. Eagerly awaiting the final ready for primetime version.

Thanks.

---

### Post by Note360 on 2006-07-30
He has to consider my input I run to much stuff now. :p

---

### Post by outdooricon on 2006-07-30
Ok, I finally installed this.. Great App! I've immeadiately removed the default Ubuntu menu's. I've been watching this thread very closely and with much excitement. So, I must start off to say this is an amazing app and I think it will be part of the future of ubuntu. Now's the part where I list my suggestions :) .

1. I don't think System is the best word to have on the bar next to the ubuntu logo to run this app. Sstem applied to administrator related activities in the main Gnome/Ubuntu menu and I think that using this word is somewhat confusing to the user. This may be worth some extra thought but some Ideas I have for it are "Menu", "Go", "Ubuntu"... Also, I remember someone commenting on getting rid of the word all together which may not be a bad idea as well.

2. As a typical user, I have no idea how to populate the Places area in this App. I can't drag things on, so I assume there is another way, however right-clicking provides me with no options, therefore I must assume I cannot edit this Places section which causes me to wonder why the area is so large. (NOTE: I am sure I could dig into the config files behind this app and add things, however I role-playing a typical user).

3. As a typical user, I punch in the file I am looking for into the search field and it doesn't find anything. Also, I am confused by why the applications menu switched. So, I assume that the search doesn't work correctly. Only by accident later do I realize that the search is for finding and application instead.Perhaps this could be remidied by saying "Find Application:".

4. The "Settings" button doesn't match the "Computer" pane, IT should be one of the other.

5. AATU (I'm abbreviating As A TYpical User now :) ) I find a lot of things listed in the "Computer" pane useless. Only on rare occasion would I click the Screen Resolution button which doesn't show my resolution on the Pane anyways (iirc this was already listed as a bug). I don't really need to know what theme I am currently using. It makes more sense for the Control Center link to be listed under System Management as that is what it's really related to. The Date/Time is somewhat useful, as well as Computer. The Network one doesn't work for me as I am using Network Manager (I am using wireless currently and it states "Wired Netork" followed by the next line saying "Device not configured"). The computer one is somewhat useful as well. I say all of this to lead up to an idea. What if, this area was instead used for miscellaneuos plug-ins. I'm picturing an optional Weather Applet showing up, perhaps a stock ticker, also, an actual Beagle file system search utility.

6. AATU, I find this panel very flat looking and have no idea that I can acutally give it a border. A small border by default would look nice. Then, if it were given a small border, it would look nice enough that it could be moved right next to the gnome bar, instead of having a gap between the two.

7. The applet doesn't disappear when I click out of it and it isn't pinned, iirc this was already listed as a bug though.

Well, I hope this feedback helps. Great app and I'm looking forward to seeing where it ends up!

---

### Post by puelocesar on 2006-07-30
Man, your app is awesome! I immediatelly removed SLED menu after installing yours :p 

I liked very much, it's beauty and very usable!

The only thing I can complain is the search.. I think that when you use the search field and it return only one result, it could launch that result when you hit Enter, instead of opening a search tool. Besides that I loved the menu. Using it as default now! 

Thanks!

---

### Post by _profox on 2006-07-30
> **outdooricon said:**
> Ok, I finally installed this.. Great App! I've immeadiately removed the default Ubuntu menu's. I've been watching this thread very closely and with much excitement. So, I must start off to say this is an amazing app and I think it will be part of the future of ubuntu. Now's the part where I list my suggestions :) .

1. I don't think System is the best word to have on the bar next to the ubuntu logo to run this app. Sstem applied to administrator related activities in the main Gnome/Ubuntu menu and I think that using this word is somewhat confusing to the user. This may be worth some extra thought but some Ideas I have for it are "Menu", "Go", "Ubuntu"... Also, I remember someone commenting on getting rid of the word all together which may not be a bad idea as well.
Already taken care of this in a patch, it is configurable in gconf-editor. I will probably release the patch tomorrow.

gconf entries are: button_text and hide_button_text, there's also hide_button_icon, but if you try to hide both, the icon will still be there, you can only hide 1 (otherwise you'll have nothing to click...)

---

### Post by Note360 on 2006-07-30
Did you fix that problem we where talking about?

---

### Post by _profox on 2006-07-30
> **Note360 said:**
> Did you fix that problem we where talking about?
To bring the menu on top of gnome-panel? No, I haven't. I've done some research and I checked the C code of the SLED menu (SLAB), but I haven't come up with a solution yet. Maybe create a seperate developers thread to discuss it :)

---

### Post by Note360 on 2006-07-30
get on the irc channel it is faster.

---

### Post by outdooricon on 2006-07-30
I also forgot to mention one other thing... 

8. When using All Applications, if you select one of the menu choiced (like "Games"), it would be nice if there was a selection box around it showing that it was the one currently being viewed.

---

### Post by lazyd2 on 2006-07-30
He's gonna do it on the next release...

---

### Post by originof on 2006-07-31
hi, i've a problem, in usp, when i click on the control panel icon, the control panel doesn't open....:sad:

---

### Post by gruvsyco on 2006-07-31
> **originof said:**
> hi, i've a problem, in usp, when i click on the control panel icon, the control panel doesn't open....:sad:

did you install [this]("http://www.ubuntuforums.org/showthread.php?t=207894")?

---

### Post by originof on 2006-07-31
> **gruvsyco said:**
> did you install [this]("http://www.ubuntuforums.org/showthread.php?t=207894")?

thanks :D

---

### Post by chanders on 2006-07-31
> **outdooricon said:**
> Ok, I finally installed this.. Great App! I've immeadiately removed the default Ubuntu menu's. I've been watching this thread very closely and with much excitement. So, I must start off to say this is an amazing app and I think it will be part of the future of ubuntu. Now's the part where I list my suggestions :) .

Thank you! I Am glad you like it...

> **outdooricon said:**
> 1. I don't think System is the best word to have on the bar next to the ubuntu logo to run this app. Sstem applied to administrator related activities in the main Gnome/Ubuntu menu and I think that using this word is somewhat confusing to the user. This may be worth some extra thought but some Ideas I have for it are "Menu", "Go", "Ubuntu"... Also, I remember someone commenting on getting rid of the word all together which may not be a bad idea as well.

Agreed! Maybe we could make it configurable? But Menu/Computer will most likelt be the default...

> **outdooricon said:**
> 2. As a typical user, I have no idea how to populate the Places area in this App. I can't drag things on, so I assume there is another way, however right-clicking provides me with no options, therefore I must assume I cannot edit this Places section which causes me to wonder why the area is so large. (NOTE: I am sure I could dig into the config files behind this app and add things, however I role-playing a typical user).

For places.. pin USP (top right button, See How-To section), Drag items
For Applications... Click on All Applications..Right click choose 'Add to favourites' or drag as above


> **outdooricon said:**
> 3. As a typical user, I punch in the file I am looking for into the search field and it doesn't find anything. Also, I am confused by why the applications menu switched. So, I assume that the search doesn't work correctly. Only by accident later do I realize that the search is for finding and application instead.Perhaps this could be remidied by saying "Find Application:".

An indicator will be placed later.. Right now there is a gconf key to stop the filtering of the applications (Patch to be applied soon)

> **outdooricon said:**
> 4. The "Settings" button doesn't match the "Computer" pane, IT should be one of the other.

Fixed in the next release ;)

> **outdooricon said:**
> 5. AATU (I'm abbreviating As A TYpical User now :) ) I find a lot of things listed in the "Computer" pane useless. Only on rare occasion would I click the Screen Resolution button which doesn't show my resolution on the Pane anyways (iirc this was already listed as a bug). I don't really need to know what theme I am currently using. It makes more sense for the Control Center link to be listed under System Management as that is what it's really related to. The Date/Time is somewhat useful, as well as Computer. The Network one doesn't work for me as I am using Network Manager (I am using wireless currently and it states "Wired Netork" followed by the next line saying "Device not configured"). The computer one is somewhat useful as well. I say all of this to lead up to an idea. What if, this area was instead used for miscellaneuos plug-ins. I'm picturing an optional Weather Applet showing up, perhaps a stock ticker, also, an actual Beagle file system search utility.

As you can tell, the "Computer" pane has recieved the least love.. This is because I have big plans for it as soon as we iron out the main apps bugs. It is going to be my pet project. Right now most settings are done via gconf-editor. A configuration panel will arrive shortly... You have to remember USP is only a week old! 

Thanks for all your advice. PS: Take a look at /apps/usp in gconf-editor, it has a load of goodies ;)

> **outdooricon said:**
> 6. AATU, I find this panel very flat looking and have no idea that I can acutally give it a border. A small border by default would look nice. Then, if it were given a small border, it would look nice enough that it could be moved right next to the gnome bar, instead of having a gap between the two.

There should be a default border *scratches head*

> **outdooricon said:**
> 7. The applet doesn't disappear when I click out of it and it isn't pinned, iirc this was already listed as a bug though.

Well, I hope this feedback helps. Great app and I'm looking forward to seeing where it ends up!

This seems to be a Metacity problem(or you have USP pinned) Currently the window state and type will take priority major projects until we get it sorted..

---

### Post by _simon_ on 2006-07-31
any news on when your next release will be out? ;)

---

### Post by chanders on 2006-07-31
> **_simon_ said:**
> any news on when your next release will be out? ;)

I am in the process of moving development from one machine to another (which involves de-windoze xpeeing) and installing Ubuntu. Hopefully I will have it done by this evening and offer a release sometime later on tonight...

@profox - If you wnt me to apply the patches, email them to me so I will review and try to include them I the next release...

---

### Post by Note360 on 2006-07-31
Sounds good.

---

### Post by Note360 on 2006-07-31
For the next release can you all please submit your bugs to the launchpad([http://www.launchpad.net/products/usp](http://www.launchpad.net/products/usp)) so we can better organize the whole thing. Thank you.

---

### Post by _profox on 2006-07-31
> **outdooricon said:**
> 

1. I don't think System is the best word to have on the bar next to the ubuntu logo to run this app. Sstem applied to administrator related activities in the main Gnome/Ubuntu menu and I think that using this word is somewhat confusing to the user. This may be worth some extra thought but some Ideas I have for it are "Menu", "Go", "Ubuntu"... Also, I remember someone commenting on getting rid of the word all together which may not be a bad idea as well.


I patched this into the application, see this post with the patch: [http://ubuntuforums.org/showpost.php?p=1322400&postcount=12](http://ubuntuforums.org/showpost.php?p=1322400&postcount=12)

---

### Post by puelocesar on 2006-07-31
> I think that when you use the search field and it return only one result, it could launch that result when you hit Enter, instead of opening a search tool.

How about implementing this?

And another thing, now difficult is to show nautilus bookmarks somewhere?

---

### Post by ironfistchamp on 2006-07-31
One thing I noticed is when you hit Alt+F4 (usualy accidentally) it messes up. It closes but it is still open. I could only get it back by removing and readding.

---

### Post by _profox on 2006-07-31
> 6. AATU, I find this panel very flat looking and have no idea that I can acutally give it a border. A small border by default would look nice. Then, if it were given a small border, it would look nice enough that it could be moved right next to the gnome bar, instead of having a gap between the two.

> There should be a default border *scratches head*

There isn't by default, you have to switch it on by hand in gconf-editor:
/apps/usp/border_width

---

### Post by _profox on 2006-07-31
> **ironfistchamp said:**
> One thing I noticed is when you hit Alt+F4 (usualy accidentally) it messes up. It closes but it is still open. I could only get it back by removing and readding.

Please post this bug on [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs)

---

### Post by lazyd2 on 2006-07-31
> **_profox said:**
> Please post this bug on [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs)
Bug has been submitted [USP stops responding when "Alt"+"F4" are pressed]("https://launchpad.net/products/usp/+bug/54739") ;)

---

### Post by Note360 on 2006-07-31
that is a nasty bug.

---

### Post by denisesballs on 2006-08-01
Sorry if I missed it, but is there a way to make the menu disappear after launching a program, like the regular menus do? I couldn't find it in the gconf.

EDIT

and can you make it so it disappers if you click off of it?

---

### Post by lazyd2 on 2006-08-01
> **denisesballs said:**
> Sorry if I missed it, but is there a way to make the menu disappear after launching a program, like the regular menus do? I couldn't find it in the gconf.

EDIT

and can you make it so it disappers if you click off of it?You probabbly have the menu pinned. Try clicking on the liitle button on the top left corner

---

### Post by denisesballs on 2006-08-01
> **lazyd2 said:**
> You probabbly have the menu pinned. Try clicking on the liitle button on the top left corner

Yep. I guess I feel like a retard now...

I guess I didn't think it would stay pinned after i closed it. ](*,)

---

### Post by denisesballs on 2006-08-01
One more thing. Is there a way to have a startup notify when I open something like the original menus do? Spinning mouse, and window list entry?

---

### Post by lazyd2 on 2006-08-01
lol, it happens to everyone from times to times...

---

### Post by lazyd2 on 2006-08-01
> **denisesballs said:**
> One more thing. Is there a way to have a startup notify when I open something like the original menus do? Spinning mouse, and window list entry?
I don't know, but you can post it in "What I would like to see"...

---

### Post by _profox on 2006-08-01
or better, report it as a bug (type: wish) on our launchpad, so you can track it better, and so we can see everything organized :)
[https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs)

---

### Post by denisesballs on 2006-08-02
Submitted here - [https://launchpad.net/products/usp/+bug/54883](https://launchpad.net/products/usp/+bug/54883)

I couldn't find where to define the type as Wishlist though.

---

### Post by _profox on 2006-08-02
> **denisesballs said:**
> Submitted here - [https://launchpad.net/products/usp/+bug/54883](https://launchpad.net/products/usp/+bug/54883)

I couldn't find where to define the type as Wishlist though.

That's normal :) me or another dev (chanders, note360) has to set the type.. didn't know you couldn't do it yourself, sorry :) i changed it to wishlist

---

### Post by LordMau on 2006-08-02
FYI USP under xfce-panel...

[[IMG]http://img142.imageshack.us/img142/6986/xfceusp800aq7.th.png[/IMG]](http://img142.imageshack.us/my.php?image=xfceusp800aq7.png)

---

### Post by zootreeves on 2006-08-02
For me, using the latest USP, there is a gap between the menu and gnome-panel (see screenshot). Not sure if that is meant to happen, but I think it would be better without the gap. (btw i'm using AIGLX, compiz & cgwd)

Also another small thing. When the menu is open you should e able to close it again by clicking back on the white space or one of the other drop down menus on the gnome-panel.

---

### Post by _profox on 2006-08-02
That's a bug that some people have... including me on my laptop. I am going to research it.

---

### Post by denisesballs on 2006-08-02
On my install at the shop, there is an almost 10 pixel space between the panel and the menu. I took a screenshot here: [http://jessejoe.com/~jesse/Screenshot.png](http://jessejoe.com/~jesse/Screenshot.png)

---

### Post by _profox on 2006-08-02
Yes, I have the same problem on my laptop, I think it's related to bug 54814 [https://launchpad.net/products/usp/+bug/54814](https://launchpad.net/products/usp/+bug/54814) what do you think denisesballs?

---

### Post by lazyd2 on 2006-08-02
Regarding the space between the panel and the menu problem, you should check the option "panel_size" in usp(in gconf-editor). See what the numerical value is and set it to 1. Restart usp and everything should be ok.

---

### Post by pump on 2006-08-02
I've tried it a moment ago and It's great!

---

### Post by SishGupta on 2006-08-03
This is amazing. Great work.
If it's not allready planned, this should be in Ubuntu 6.10.

---

### Post by _profox on 2006-08-03
> **SishGupta said:**
> This is amazing. Great work.
If it's not allready planned, this should be in Ubuntu 6.10.
It's not planned yet. And right now we still have alot of features and bugs to resolve, but I think we can get a good working version by october (edgy eft's release)

If everybody wants it, maybe it will get included! :)
We would be honored.. =D>

I checked our current memory footprint and we actually use about 50% less memory than the "Novell Main-Menu (SLAB or USLAB)"
And we have a specification set up to improve the speed of our applet (it's not slow, but it can always get faster :))

---

### Post by delfick on 2006-08-03
> **SishGupta said:**
> This is amazing. Great work.
If it's not allready planned, this should be in Ubuntu 6.10.

TOO RIGHT ! :D

this menu is better than any other menu ever made (even if there are still bugs and functionality still to be added) :D

---

### Post by Note360 on 2006-08-03
I think Viper is being included but I am not sure. Maybe, just in the respitories. Then again you cant trust anything he says, that rat.

---

### Post by _profox on 2006-08-03
When we are done with cleaning our code up and cleaning most bugs, the choice should be obvious ;) let the voting begin! ;) (not yet)

---

### Post by passonno on 2006-08-03
I would love to use usp, but I am stuck here:


Traceback (most recent call last):
  File "/usr/bin/usp", line 1720, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1711, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1543, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 140, in __init__
    self.Todos()
  File "/usr/bin/usp", line 760, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 699, in get_proper_icon
    Image1.set_from_pixbuf(gtk.gdk.pixbuf_new_from_file(icon_description).scale_simple(width,height,gtk.gdk.INTERP_BILINEAR))
gobject.GError: Image file '/usr/share/pixmaps/deng.png' contains no data


Any idea as to what's going on here?



EDIT:  It was hanging on deng.png, which was a 0 byte file, somehow there from a failed Doomsday install.

---

### Post by passonno on 2006-08-03
Is there any way to add a keyboard shortcut, perhaps <Super_L>, to launch the panel?

---

### Post by chanders on 2006-08-03
> **passonno said:**
> I would love to use usp, but I am stuck here:


Traceback (most recent call last):
  File "/usr/bin/usp", line 1720, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1711, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1543, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 140, in __init__
    self.Todos()
  File "/usr/bin/usp", line 760, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 699, in get_proper_icon
    Image1.set_from_pixbuf(gtk.gdk.pixbuf_new_from_file(icon_description).scale_simple(width,height,gtk.gdk.INTERP_BILINEAR))
gobject.GError: Image file '/usr/share/pixmaps/deng.png' contains no data


Any idea as to what's going on here?



EDIT:  It was hanging on deng.png, which was a 0 byte file, somehow there from a failed Doomsday install.


Did you remove this 0byte file? It should work fine if you do ;)

---

### Post by chanders on 2006-08-03
> **passonno said:**
> Is there any way to add a keyboard shortcut, perhaps <Super_L>, to launch the panel?

Will look into it...:)

---

### Post by gruvsyco on 2006-08-03
Chanders, I'm just curious if you're still submitting debs to Quinn's repos.  I'm getting my updates from here now but some may not.

---

### Post by chanders on 2006-08-03
> **gruvsyco said:**
> Chanders, I'm just curious if you're still submitting debs to Quinn's repos.  I'm getting my updates from here now but some may not.

I usually post them here first so that major bugs are ironed out and then they are submitted to Quinn..

---

### Post by LordMau on 2006-08-04
Just did an update and was pleasantly surprised that USP is now included in xgl.compiz repo. Great!

---

### Post by chanders on 2006-08-04
> **LordMau said:**
> Just did an update and was pleasantly surprised that USP is now included in xgl.compiz repo. Great!

Pleasing the customer - #1 rule in management ;) 

Not that it helps management... I guess the customer wins all around :D

---

### Post by delfick on 2006-08-04
> **chanders said:**
> Pleasing the customer - #1 rule in management ;) 

hmmm...u've definitely achieved that ! :D

---

### Post by gborzi on 2006-08-04
This Ubuntu System Panel application is great. I'm using it as a substitute of the Applications/Places/System menus of the gnome panel. Up to now I have seen only two minor problems:
1) The window is not transparent. I have seen screenshots of USP with transparent window, but I'm unable to get the transparency. My gnome-panel is transparent as those of the screenshots.
2) I have modified the menu adding a Science submenu with Alacarte. But this submenu doesn't appear in USP window. It seems USP use the default system menu and not the user menu.
Any help on both this points will be greatly appreciated, expecially on point 1.

PS. Many thanks to the author, Chanders.

---

### Post by _profox on 2006-08-04
> **gborzi said:**
> This Ubuntu System Panel application is great. I'm using it as a substitute of the Applications/Places/System menus of the gnome panel. Up to now I have seen only two minor problems:
1) The window is not transparent. I have seen screenshots of USP with transparent window, but I'm unable to get the transparency. My gnome-panel is transparent as those of the screenshots.
2) I have modified the menu adding a Science submenu with Alacarte. But this submenu doesn't appear in USP window. It seems USP use the default system menu and not the user menu.
Any help on both this points will be greatly appreciated, expecially on point 1.

PS. Many thanks to the author, Chanders.

1. Those people with the transparant USP are using the Compiz window manager, which is able to make every window you want transparant. (it is alpha software and works through XGL/AIGLX)

2. This is indeed still a big problem. It's static hardcoded information. But we are going to make it more dynamic in the future!

---

### Post by Prism on 2006-08-04
One thing I didn't catch: how can I add more places to the places area? Or add/remove/configure items from the computer area? For example, I have two network cards, and USP displays the IP of the local one. How can I change it?

---

### Post by _profox on 2006-08-04
> **Prism said:**
> One thing I didn't catch: how can I add more places to the places area? Or add/remove/configure items from the computer area? For example, I have two network cards, and USP displays the IP of the local one. How can I change it?

In the top left corner, click on the pin button, then drag places to the places section.

You can only display 1 network card right now, but you can choose which one in gconf-editor with network_interface

---

### Post by gborzi on 2006-08-04
> **_profox said:**
> 1. Those people with the transparant USP are using the Compiz window manager, which is able to make every window you want transparant. (it is alpha software and works through XGL/AIGLX)

2. This is indeed still a big problem. It's static hardcoded information. But we are going to make it more dynamic in the future!

Thanks for the informations. I had installed XGL, but later removed it because it was a bit unstable.

---

### Post by Prism on 2006-08-04
> **_profox said:**
> In the top left corner, click on the pin button, then drag places to the places section.

You can only display 1 network card right now, but you can choose which one in gconf-editor with network_interface

Cool, thanks. :)

---

### Post by Oppi on 2006-08-05
hi

i got messed up with the settings in gconf apps/usp. first i had it, like i wanted it with big icons and big fonts. then i did a little config and messed all up. 
now the icons are tiny and i do not get the big again. also i think the gconf file does not save my settings. 
installed/reinstalled usp, removed some files in /usr/bin/.. with name ups etc...

can anybody tell me the standard settings to get big icons back? i also want the icons in the places menu as big as the other ones. how can i get this to work ?

take a look at the screenshots to see what i mean. 
first one: like i had it at the beginning and want to have it again
second: like it is now

the next question i have i about translations of usp to german: is there any? where can i download it? or do i have to set the language somewhere in the prog. ?

any help would be great.

sorry for my non-native english and for any spelling and typing faults. i spent some hours now before my pc. maybe tomorrow when i turn on the pc again all works fine agien. who knows?


greets, Oppi

---

### Post by Oppi on 2006-08-05
Got it going!!! :D :D :D :D :D 

Just in the moment before i wanted to turn off the Pc to sleep about it I gave it one last try. And it works !!! Yeahhhh

The solution was 4. i thought icon_size must be 10 and bigger to get such big icons - but 4 worked.

For now, I am not quite sure where to put the Launcher. down left corner (lil' bit windows style) or up left (ubuntu style). thats my only question i have to dream of now.

Really great work. I love USP. Thx! :-P :D 

greets, Oppi

"good night and good luck"

---

### Post by chanders on 2006-08-06
> **Oppi said:**
> Got it going!!! :D :D :D :D :D 

Just in the moment before i wanted to turn off the Pc to sleep about it I gave it one last try. And it works !!! Yeahhhh

The solution was 4. i thought icon_size must be 10 and bigger to get such big icons - but 4 worked.

For now, I am not quite sure where to put the Launcher. down left corner (lil' bit windows style) or up left (ubuntu style). thats my only question i have to dream of now.

Really great work. I love USP. Thx! :-P :D 

greets, Oppi

"good night and good luck"

Glad you got it going! We will have a configuration panel soon so you wouldnt have to be digging in gconf-editor ;)

---

### Post by Note360 on 2006-08-06
back

---

### Post by punkdigerati on 2006-08-07
Hi, I've been using USP for a couple of days now, and it's the best menu I have used on any gnome system I've ran. I was wondering if there will be any features to set the escape key to close the menu. Also, if when you release the config panel, will the ability to add things to the System Management area be added? thanks.

---

### Post by chanders on 2006-08-07
> **punkdigerati said:**
> Hi, I've been using USP for a couple of days now, and it's the best menu I have used on any gnome system I've ran. I was wondering if there will be any features to set the escape key to close the menu. Also, if when you release the config panel, will the ability to add things to the System Management area be added? thanks.

Full keyboard support is planned... and with the new plugin system, 'System Management' plugins will allow you to add what you like ;)

---

### Post by orb9220 on 2006-08-07
Great App just itstalled .33 and works beatifully. But how do you get a  frame around it like I have seen in other pics?

And isn't ubuntu menu developers going to be pissed being replaced?
Keep up the great work and I shall:

"Sacrifice one virgin Microsoft employee to the fires of Goddess Ubuntu"

In tribute.

---

### Post by chanders on 2006-08-07
> **orb9220 said:**
> Great App just itstalled .33 and works beatifully. But how do you get a  frame around it like I have seen in other pics?

And isn't ubuntu menu developers going to be pissed being replaced?
Keep up the great work and I shall:

"Sacrifice one virgin Microsoft employee to the fires of Goddess Ubuntu"

In tribute.

Run gconf-editor and go to /apps/usp  

There are a lot of goodies in there to play with. You might want to read the first post in this thread for a proper introduction and also the HowTo thread...

---

### Post by fantan on 2006-08-07
Hi Developers,

Today morning I downloaded the next version of the USP (0.33-1), and I found the new feature - the Hungarian surface - in it, which is very nice.
Also I found a new thing, the "Favorite applications" menu item in the "All applications" area, but I don't know, how or where add other applications to it. I tried to add new items as it is writed down in the How-to posts, but it isn't work for the "Favorite applications" menu area. 

Can anybody help me, how to add new intems to it?

fantan

---

### Post by chanders on 2006-08-07
> **fantan said:**
> Hi Developers,

Today morning I downloaded the next version of the USP (0.33-1), and I found the new feature - the Hungarian surface - in it, which is very nice.
Also I found a new thing, the "Favorite applications" menu item in the "All applications" area, but I don't know, how or where add other applications to it. I tried to add new items as it is writed down in the How-to posts, but it isn't work for the "Favorite applications" menu area. 

Can anybody help me, how to add new intems to it?

fantan

Right Click -> Add to Favourites

---

### Post by Malac on 2006-08-07
Small gripe :)
I have the latest USP but I seem to have a small useless button in the top left of my panel above places. Am I missing some function or is this an error.

---

### Post by chanders on 2006-08-07
> **Malac said:**
> Small gripe :)
I have the latest USP but I seem to have a small useless button in the top left of my panel above places. Am I missing some function or is this an error.

Read the first post in this thread...

---

### Post by fantan on 2006-08-07
Hi, 

Thank you very much for the quick answer, but I tried this method and it isn't work at me.

At any case, if I select any of the applications from any menu item and right click on it, select "Add to favorites", and restart X, I can't find the selected application on the "Favorite applications" area.

What to do?

fantan

---

### Post by chanders on 2006-08-07
> **fantan said:**
> Hi, 

Thank you very much for the quick answer, but I tried this method and it isn't work at me.

At any case, if I select any of the applications from any menu item and right click on it, select "Add to favorites", and restart X, I can't find the selected application on the "Favorite applications" area.

What to do?

fantan

When you click "Add to favourites" then you click "Applications" and you will see the item added to your favourites...

---

### Post by fantan on 2006-08-07
Hi again,

No, this isn't work for me.

I can't add applications to the "Favorite applications" menu item at all.

I tried all possibilities but I can't get any results.

Can you explain me in details, how to do it?

fantan

---

### Post by chanders on 2006-08-07
> **fantan said:**
> Hi again,

No, this isn't work for me.

I can't add applications to the "Favorite applications" menu item at all.

I tried all possibilities but I can't get any results.

Can you explain me in details, how to do it?

fantan

Going to sleep now :( Been up all night finishing Ver 0.33. Will try to help you when I get up in a few hrs k? Try reading the HowTo and the first post  in this thread also in the mean while...

---

### Post by fantan on 2006-08-07
OK, I'll wait.

Good night!

fantan

---

### Post by vonpmg on 2006-08-07
Fantan, i think you used the Hungarian translation which had one error, as you reported.
I think this is preventing you from adding the favourites apps.
If you want, you could try to copy this updated translation (yours) and see if it fix the problem.

Make a backup copy of the file **/usr/share/locale/hu/LC_MESSAGES/usp.mo**
and unzip the attached file with this same name. (**/usr/share/locale/hu/LC_MESSAGES/usp.mo**)
Restart The Ubuntu System Panel and try it.
Please report your result.

---

### Post by Malac on 2006-08-07
> **chanders said:**
> Read the first post in this thread...
 :oops: Sorry for the dumb question. :oops:
Will read instructions next time I try something.
Excellent Panel app.

---

### Post by lazyd2 on 2006-08-07
Hmmm, I'm using Greek language(just to test the translation), but USP is still in English....Am I being stupid? Do I have to do something else?

---

### Post by chanders on 2006-08-07
> **lazyd2 said:**
> Hmmm, I'm using Greek language(just to test the translation), but USP is still in English....Am I being stupid? Do I have to do something else?

What is you locale? From the po file you posted I saw el_GR so the translation was for that locale. Let me know so I can recompile it for the next version...

---

### Post by fantan on 2006-08-07
Hello vonpng,

Thank you very much for the newly compiled usp.mo file.
Now everithing is OK with it.
But, as for the "Favorite applications", I think, I figured out, what is the problem with it.

Firstly, I'm very sorry for my bad English, but I try to explain:

The USP panel contains of three parts:
Applications, Places, Configuration.
On the Application part there is a button which can be named "All applications" or "Applications". When I click on this button, on the screen of this part of the USP panel there are eider favorite applications (although the name of this part of the sreen is "Applications" and not "Favorite applications"), which I can add to here by the Chanders's How-to; and if I click on the button again, this place becomes "All applications" and on the left hand side of it you can find the folders from Gnome main menu, and on the right hand side you can see the applications of the selected folders. Between the folders I found a folder named "Favorite applications", but this folder is missing from the Gnome main menu. There is one application in it: VMware. I don't know, how I got this folder. Of course I have the VMware on my computer, but I don't know, from where I got the folder, I don't created it sure.
My proposal in accordance with this problem is:
Rename the afore mentioned part of the USP panel insteed of "Applications" to "Favorite applications", and the double name of the button to "All applications"/"Favorite applications". I think, it would be much more logic.
As for the folder named "Favorite applications" I think, this is just my problem. I try to find the solution anyhow.

best regards,

fantan

---

### Post by chanders on 2006-08-07
> **fantan said:**
> Hello vonpng,

Thank you very much for the newly compiled usp.mo file.
Now everithing is OK with it.
But, as for the "Favorite applications", I think, I figured out, what is the problem with it.

Firstly, I'm very sorry for my bad English, but I try to explain:

The USP panel contains of three parts:
Applications, Places, Configuration.
On the Application part there is a button which can be named "All applications" or "Applications". When I click on this button, on the screen of this part of the USP panel there are eider favorite applications (although the name of this part of the sreen is "Applications" and not "Favorite applications"), which I can add to here by the Chanders's How-to; and if I click on the button again, this place becomes "All applications" and on the left hand side of it you can find the folders from Gnome main menu, and on the right hand side you can see the applications of the selected folders. Between the folders I found a folder named "Favorite applications", but this folder is missing from the Gnome main menu. There is one application in it: VMware. I don't know, how I got this folder. Of course I have the VMware on my computer, but I don't know, from where I got the folder, I don't created it sure.
My proposal in accordance with this problem is:
Rename the afore mentioned part of the USP panel insteed of "Applications" to "Favorite applications", and the double name of the button to "All applications"/"Favorite applications". I think, it would be much more logic.
As for the folder named "Favorite applications" I think, this is just my problem. I try to find the solution anyhow.

best regards,

fantan

I am glad you got it working ;) I just got up... I will consider changing the label to 'Favourite Applications'... Enjoy!

---

### Post by fantan on 2006-08-07
Hi Developers,

In conjunkcion with the afore mentioned problem, to solve it, I made a new Hungarian translation of the locale file.
Please compile it again, and change the originale usp.mo with the new version, and at the same time send it to this forum too.
> 
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Albert Fazakas <fantan@axelero.hu>, 2006.
# This is the second fix.
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-07 11:24+0100\n"
"Last-Translator: Albert Fazakas <fantan@axelero.hu>\n"
"Language-Team: Albert Fazakas <fantan@axelero.hu>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=hu_HU.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Helyek"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Alkalmazások"

#: usp.glade:247
msgid "Settings"
msgstr "Beállítások"

#: usp.glade:598
msgid "System Management"
msgstr "Adminisztráció"

#: usp.glade:663
msgid "Install Software"
msgstr "Szoftver telepítés"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Vezérl&#337;központ"

#: usp.glade:788
msgid "Lock screen"
msgstr "Képerny&#337;zár"

#: usp.glade:852
msgid "Quit..."
msgstr "Kilépés..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Számítógép"

## 
#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Minden alkalmazás</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Minden alkalmazás"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"   # fix
msgstr "<span size=\"small\"> Kedvencek</span>"     # fix

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Kellékek</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Játékok</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Iroda</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programozás</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio és Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Rendszereszközök</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Beállítások</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Minden</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">További alkalmazások...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Írd be, mit keressek"

#: usp.glade:2216
msgid "Search"
msgstr "Keresés"

#: usp.glade:2516
msgid "Network"
msgstr "Hálózat"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Dátum és id&#337;"

#: usp.glade:2764
msgid "Theme"
msgstr "Téma"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Képerny&#337; felbontás"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Rendszerkonfigurálás"

#: usp.glade:3133
msgid "Move up"
msgstr "Mozgatás fel"

#: usp.glade:3142
msgid "Move down"
msgstr "Mozgatás le"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Cimkék módosítása"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Elválasztó csík beszúrása"

#: usp.glade:3169
msgid "Insert space"
msgstr "Üres hely beszúrása"

#: usp.glade:3178
msgid "Remove"
msgstr "Eltávolítás"

#: usp.glade:3187
msgid "Edit item"
msgstr "Tétel módosítása"

#: usp.glade:3256
msgid "Name"
msgstr "Név"

#: usp.glade:3300
msgid "Generic name"
msgstr "Általános név"

#: usp.glade:3343
msgid "Comment"
msgstr "Megjegyzés"

#: usp.glade:3386
msgid "Exec"
msgstr "Futtatás"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Hozzáadás a kedvencekhez"


Thank you very much in advance.
This application becomes better and better! I like it very much!

fantan

---

### Post by bulldog on 2006-08-07
Wrong answer at the wrong place :(

---

### Post by chanders on 2006-08-07
> **fantan said:**
> Hi Developers,

In conjunkcion with the afore mentioned problem, to solve it, I made a new Hungarian translation of the locale file.
Please compile it again, and change the originale usp.mo with the new version, and at the same time send it to this forum too.


Thank you very much in advance.
This application becomes better and better! I like it very much!

fantan

New hungarian translation attached..


@bulldog - huh?

---

### Post by fantan on 2006-08-07
Thank you very much, Chanders!

fantan

---

### Post by lazyd2 on 2006-08-07
> **chanders said:**
> What is you locale? From the po file you posted I saw el_GR so the translation was for that locale. Let me know so I can recompile it for the next version...
Maybe I made a typo. Where can I look? ](*,) :mrgreen:

*edit* Is this what I should be looking for?
```
/etc/environment:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_GR:en"
```

---

### Post by bulldog on 2006-08-07
@Chanders
Too many tabs open,got messed up with a reply on something else.:)

---

### Post by LordMau on 2006-08-07
Just installed 0.33 ... thanks for the Quit... option!

---

### Post by fuoco on 2006-08-07
I am using ubuntu on powerpc, do I have any chance of getting usp to work ? I added the compiz repository but I don't get usp or any other thing there...

---

### Post by _profox on 2006-08-07
> **fuoco said:**
> I am using ubuntu on powerpc, do I have any chance of getting usp to work ? I added the compiz repository but I don't get usp or any other thing there...

Yes, USP works on all platforms. It relies on Python and GTK.
Just download the .deb file in the "new releases" topic and install that.

Or try to "sudo apt-get install usp" with the compiz repo enabled.

---

### Post by fuoco on 2006-08-07
What I get is:

```
$ sudo apt-get install usp
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package usp
```

I have in /etc/apt/sources.list :

```
deb http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
```

---

### Post by chanders on 2006-08-07
> **lazyd2 said:**
> Maybe I made a typo. Where can I look? ](*,) :mrgreen:

*edit* Is this what I should be looking for?
```
/etc/environment:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_GR:en"
```

Hmmm... Isnt en 'English' ? Maybe thats why USP is in English...
eg. pt_BR is portugues(pt) but the Brazillian(BR) version

_UCC_ should show this if run from a terminal ;)

> **LordMau said:**
> Just installed 0.33 ... thanks for the Quit... option!

Did it work well?

---

### Post by _profox on 2006-08-07
> **fuoco said:**
> What I get is:

```
$ sudo apt-get install usp
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package usp
```

I have in /etc/apt/sources.list :

```
deb http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
```

You need "deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main" I think

---

### Post by Anduu on 2006-08-07
Hmmmm...what is the status on theme bugs?

Dunno if anyone really cares but this is what I get using the "Amaranth" theme :p

---

### Post by lazyd2 on 2006-08-07
[QUOTE=chanders]UCC should show this if run from a terminal
[/QUOTE]
```
:~$ gcontrol
Your locale is el_GR
('el_GR', 'utf-8')
```
Everything else its in Greek, exept USP :-k :-k

(Dunno, it's all "Greek" to me...):mrgreen:

---

### Post by fuoco on 2006-08-07
> **_profox said:**
> You need "deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main" I think

It's not what shows up in [http://xgl.compiz.info/](http://xgl.compiz.info/)

---

### Post by chanders on 2006-08-07
> **Anduu said:**
> Hmmmm...what is the status on theme bugs?

Dunno if anyone really cares but this is what I get using the "Amaranth" theme :p

Will fix this in the next release..

---

### Post by chanders on 2006-08-07
> **lazyd2 said:**
> ```
:~$ gcontrol
Your locale is el_GR
('el_GR', 'utf-8')
```
Everything else its in Greek, exept USP :-k :-k

(Dunno, it's all "Greek" to me...):mrgreen:

All Greek to you ha ha ha ha.....good 1...

Hmmm have to look over the translation code...

---

### Post by coubi64 on 2006-08-07
> **LordMau said:**
> FYI USP under xfce-panel...

[[IMG]http://img142.imageshack.us/img142/6986/xfceusp800aq7.th.png[/IMG]](http://img142.imageshack.us/my.php?image=xfceusp800aq7.png)

I'm a French user. I'm in this case (I have Xfce and I'd like to use USP).

I didn't find how to do this, could you explain me what to do?

Thank you.... :( :-k

---

### Post by plb on 2006-08-09
Just tried it out, very nice though I think System should say Ubuntu =)

---

### Post by _profox on 2006-08-09
> **plb said:**
> Just tried it out, very nice though I think System should say Ubuntu =)

Open "gconf-editor" and goto "Apps > USP" and change "applet_text" ;)

---

### Post by orev on 2006-08-10
USP is sweet!  Thanks for the effort!

---

### Post by Polygon on 2006-08-10
USP is looking good!

only two things:

one, i cannot drag the "system" button on my panel, i dont know if this is a problem with me or the program

and clicking "control center" on the actual USP window does seem to do anything

otherwise great work!

---

### Post by _simon_ on 2006-08-10
> **Polygon said:**
> USP is looking good!

only two things:

one, i cannot drag the "system" button on my panel, i dont know if this is a problem with me or the program

and clicking "control center" on the actual USP window does seem to do anything

otherwise great work!

The control center it's calling is this one:

[http://www.ubuntuforums.org/showthread.php?t=207894](http://www.ubuntuforums.org/showthread.php?t=207894)

So if you install that it will work.

No sure what you mean by cannot drag the system button. Do you mean move it's position? Check that the button is not locked and that the location you are trying to drag to hasn't got locked items in the way (right click on them to see)

---

### Post by simone.brunozzi on 2006-08-10
This Ubuntu System Panel is a wonderful idea. Congrats!
Can't wait to see it in the final stable Edgy (prerequisite to suggest it to my many ungeeky friends using ubuntu :-P).

Cheers,

---

### Post by Oppi on 2006-08-10
@polygon

I don't know if I get u right, but if u want to have the "System"-button on any panel you have to right-click the panel where you want to have it and choose "apply new app". Then scroll down until you come to "Ubuntu Sytem Panel" and choose it. Now it should appear unless u have installed it. If u start USP out of terminal a window is opened which u cannot apply to an panel.

Was this the problem you asked ? 

greets, Oppi

---

### Post by BitTorrentBuddha on 2006-08-10
Is there anyway to map this to a shortcut yet? I believe that's one of the few things this is missing. You've really put together the greatest menu in my experience with any operating system (yes, better than the K menu IMO.)

---

### Post by Polygon on 2006-08-10
> **Oppi said:**
> @polygon

I don't know if I get u right, but if u want to have the "System"-button on any panel you have to right-click the panel where you want to have it and choose "apply new app". Then scroll down until you come to "Ubuntu Sytem Panel" and choose it. Now it should appear unless u have installed it. If u start USP out of terminal a window is opened which u cannot apply to an panel.

Was this the problem you asked ? 

greets, Oppi

nope, sorry

what i meant was, its ON my panel, but i cant move it anywhere. You know that if you have like stuff like icons (shortcuts) on your panel, you can move it? Well usually for me, i can move it with the middle mouse button, but for some reason, it wont let me do it with USP. I had to right click it and choose "move" then move it. Not really a big problem, but yeah :D

and thanks simon for the link for ubuntu control panel. that is a very cool program too =P

---

### Post by chanders on 2006-08-10
> **Polygon said:**
> nope, sorry

what i meant was, its ON my panel, but i cant move it anywhere. You know that if you have like stuff like icons (shortcuts) on your panel, you can move it? Well usually for me, i can move it with the middle mouse button, but for some reason, it wont let me do it with USP. I had to right click it and choose "move" then move it. Not really a big problem, but yeah :D

and thanks simon for the link for ubuntu control panel. that is a very cool program too =P

The middle click to move will be added... please file it as a wish on the wishlist at launchpad.. [https://launchpad.net/products/usp](https://launchpad.net/products/usp)

Glad you like both programs ;)

---

### Post by iGama on 2006-08-11
Nice app, i just installed it and i like it :D

just 1 question, when i press on the "Control Panel" icon nothing appens, is that normal?

thanks and good work

---

### Post by vonpmg on 2006-08-11
Chandler, i think you should incluse Ubuntu Control Center with USP or make a Big Tooltip when someone without it press the "Control Panel" ;) 

Please, if the "Control Panel" button is not working install Ubuntu Control Center.
```
sudo apt-get install gcontrol
```
(You should have Quinn Repository. See [http://xgl.compiz.info]("http://xgl.compiz.info") for details)

Or you could get if from the project ( version 1.38 ):
```
http://ubuntuforums.org/attachment.php?attachmentid=12831&d=1153073005
```
See the Forums of UCC to view screenshots and information aboit it.
```
http://ubuntuforums.org/forumdisplay.php?f=157
```

---

### Post by Polygon on 2006-08-12
> **chanders said:**
> The middle click to move will be added... please file it as a wish on the wishlist at launchpad.. [https://launchpad.net/products/usp](https://launchpad.net/products/usp)

Glad you like both programs ;)

ok i added that suggestion, and i added some others. good luck with this program!

---

### Post by _simon_ on 2006-08-13
still can't change text colour! :(

---

### Post by Malac on 2006-08-13
> **_simon_ said:**
> still can't change text colour! :(
I think you need to tick use_custom_color as well in gconf-editor.

By the way how do you get horizontal seperators to appear on the menu.

---

### Post by _simon_ on 2006-08-13
custom color only does border, background and headings.

If you right click on USP you can add a space or a separator - the separator is the horizontal line.

---

### Post by reggaemanu on 2006-08-15
Hi,

USP no longer works for me since version 0.33, and i don't really know why, i have the button on the panel, but nothing appens when i click it.
Here is the output i have with the version 0.41 when i run it in a window :

> reggaemanu@ubuntu:/opt$ usp run-in-window
Dir exist
Dir exist
Dir exist
Application added - /home/reggaemanu/.usp/applications/hadjaha-001c3515c2.desktopApplication added - /home/reggaemanu/.usp/applications/aMSN.desktop
Traceback (most recent call last):
  File "/usr/bin/usp", line 1769, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1749, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1565, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 174, in __init__
    self.PopulateApplications()
  File "/usr/bin/usp", line 188, in PopulateApplications
    self.Add_Button(ApplicationsList[i][:-1],"application",True)
  File "/usr/bin/usp", line 1048, in Add_Button
    PlaceIcon.set_size_request(60,-1)
UnboundLocalError: local variable 'PlaceIcon' referenced before assignment
reggaemanu@ubuntu:/opt$


If that can help...

---

### Post by cbudden on 2006-08-15
Hey 

I'm having a few problems with the latest USP (0.41)

The button on the panel looks like this : 
[IMG]http://img434.imageshack.us/img434/5572/uspie0.png[/IMG]

Note the gray bar at the bottom and the "shifting" of the panel in the background.

Also, the theming of the program is broken compared to 0.3 ish:
[IMG]http://img434.imageshack.us/img434/7311/usp2bj1.png[/IMG]


Here is an older version:
[IMG]http://img339.imageshack.us/img339/7136/uspolderfk1.png[/IMG]

Is anyone else getting this?

thanks

Chris Budden

---

### Post by sefs on 2006-08-15
Nice panel.

1) How do i put a border on it so it doesnt get lost away when covering other windows of same color.

2) How do i change thte height of the panel.  Its too short and some of the icons in it are cut off

3) since installing it i have a weird probloem where i see these small documents flying from top of screen to bottom of the screen like when you drag a document someplace and its not suppose to go there how it flys away.  Only thing i'm not dragging anything... its just happening by itself.

Thanks.

---

### Post by sefs on 2006-08-15
by the way ... with the scroll bar when is that gonna be converted to one of the nice fancy scrolls taht we see in the favoites menus of the most current browsers or the ubuntu menu when a menu is too long :)

---

### Post by _simon_ on 2006-08-16
> **cbudden said:**
> Hey 

I'm having a few problems with the latest USP (0.41)

The button on the panel looks like this : 
[IMG]http://img434.imageshack.us/img434/5572/uspie0.png[/IMG]

Note the gray bar at the bottom and the "shifting" of the panel in the background.


Is anyone else getting this?

thanks

Chris Budden

Chris,

To solve the theming problem - i.e. different colours you need to do the following:

Gconf -> apps -> usp

Scroll to the very bottom and tick "use_custom_color"

Your panel will then be all one colour.

To change your colours, scroll back up and change:

custom_border_color
custom_color (this is your usp panel background colour)
custom_heading_color

Can't help you with your button problem. I use the same Linsta-GTK2 theme without that problem.

Edit: What size is that panel? (right click and choose properties) mine is 24

---

### Post by cbudden on 2006-08-16
> **_simon_ said:**
> Chris,

To solve the theming problem - i.e. different colours you need to do the following:

Gconf -> apps -> usp

Scroll to the very bottom and tick "use_custom_color"

Your panel will then be all one colour.

To change your colours, scroll back up and change:

custom_border_color
custom_color (this is your usp panel background colour)
custom_heading_color

Can't help you with your button problem. I use the same Linsta-GTK2 theme without that problem.

Edit: What size is that panel? (right click and choose properties) mine is 24


Thanks for the colour suggestion, it worked.
I have found the problem with the button, it is the icon theme i'm using.  If I use Human the ubuntu icon is not scaling properly, but if I pick Tangerine or anything else, the icon is correct and fits and the button is fine.  I shall look about changing the Human icon with one from another set, as I want the Human icon theme.

Thanks again

edit

It is the human icon which is causing the problem for sure, and my panel size is 24.

---

### Post by cbudden on 2006-08-16
Hello again.

After switching themes again, but this time differently, buy going back to straight Human and switching controls back to Linsta, my USP is again beautiful.

Thanks

---

### Post by Uncle Spellbinder on 2006-08-17
> **cbudden said:**
> Hello again.

After switching themes again, but this time differently, buy going back to straight Human and switching controls back to Linsta, my USP is again beautiful.

Thanks

My GTK theme of choice. *Linsta* rocks!

---

### Post by frouxguillaume on 2006-08-17
hello, I wanted to know how to change the menu button (USP) to replace by a picture.
Thank you

---

### Post by sefs on 2006-08-17
After installing a new app it did not appear in USP listed under all applications neither could it be found in the search box.   I had to remove the applet from and replace it on the panel for the progam launcher to appear.

Is there a way around this?

Thanks.

---

### Post by lazyd2 on 2006-08-17
> **sefs said:**
> After installing a new app it did not appear in USP listed under all applications neither could it be found in the search box.   I had to remove the applet from and replace it on the panel for the progam launcher to appear.

Is there a way around this?

Thanks.
I think they are working on that...

---

### Post by em3raldxiii on 2006-08-17
Fantastic idea ... consider this thread bookmarked :D

---

### Post by ADRez on 2006-08-18
Thanks for this great panel!! I love it!

But two questions for making it better for me:

1. Is it posible to change between categories in applications (accesories, graphics, internet...) without clicking on them, just only pointing them with the mouse?

2. Is possible to hide the titles (places, applications, system management...) or make panels not to hide when clicking on titles?

Thanks!

---

### Post by chanders on 2006-08-19
> **ADRez said:**
> Thanks for this great panel!! I love it!

But two questions for making it better for me:

1. Is it posible to change between categories in applications (accesories, graphics, internet...) without clicking on them, just only pointing them with the mouse?

2. Is possible to hide the titles (places, applications, system management...) or make panels not to hide when clicking on titles?

Thanks!

Hmmm... 
1. That option is not available now but I will consider adding it...
2. Why would you click the titles if you didnt want to close them? :-k

---

### Post by compwiz18 on 2006-08-19
I like!  Very nice, I think I'll keep it.  Far better then SLED/SLAB (however it's spelled).

Anyway, a couple of suggestions:

1. When I type an app name in the app search bar, and I type enough that it narrows it down to only one app, and I press enter, can you make 

2. When I click the system button and the menu pops up, it is a few pixels down from the panel that the button is located on (see screenshot)  I'm not sure if this is intentional or not...but it bothers me for some reason.

Otherwise, it's great :D

(sorry if I came across as not liking it.  I really do.)

---

### Post by oncemore on 2006-08-20
is there any possibility to add support for "recent documents"?
thanks

---

### Post by ADRez on 2006-08-20
> 1. That option is not available now but I will consider adding it...

Thanks!

> 2. Why would you click the titles if you didnt want to close them?

I have the toggle panel disabled, so if I click without wanting on them then the toggle panel appears again, and I think it's annoying.

---

### Post by chanders on 2006-08-20
> **compwiz18 said:**
> I like!  Very nice, I think I'll keep it.  Far better then SLED/SLAB (however it's spelled).

Anyway, a couple of suggestions:

1. When I type an app name in the app search bar, and I type enough that it narrows it down to only one app, and I press enter, can you make 

2. When I click the system button and the menu pops up, it is a few pixels down from the panel that the button is located on (see screenshot)  I'm not sure if this is intentional or not...but it bothers me for some reason.

Otherwise, it's great :D

(sorry if I came across as not liking it.  I really do.)

I will add the ENTER button to run in the next release. It seems you are running Metacity, try changing /apps/usp/panel_size option to 1 and restart USP...

Glad you like it ;-)

> **oncemore said:**
> is there any possibility to add support for "recent documents"?
thanks

This is going to be added as a plugin shortly :-)

---

### Post by delfick on 2006-08-20
Chanders....out of interest...how's it goin for a configuration window?

---

### Post by chanders on 2006-08-20
> **delfick said:**
> Chanders....out of interest...how's it goin for a configuration window?

To be honest, delfick, right now I am working on making the plugin system better, especially for places to show mounted volumes and the nautilus bookmarks file.. It seems unlikely that I would be able to start the configuration window soon...

I have placed prority on getting the plugin stuff done. Any budding developers who are willing to give the configuration window a shot please pm me. Even if you can design the glade file, I will try to do the coding behind it..

Sorry guys but myself and the other developers are working as hard and as fast as we can. We just can't do it all at once...

---

### Post by bulldog on 2006-08-20
Take it easy,Chanders :D 

It's already a fine application.
Do what you think that's important and take your time.

Don't rush it,take it step by step, we have to wait with all our wishes.

You and your team do a hell of a good job and we all appreciate it.

---

### Post by Uncle Spellbinder on 2006-08-20
Ditto ^^

Plenty of wishes, not enough *thanks*. I officially add my mnay thanks for a wonderful USP! ;)

---

### Post by ashrack on 2006-08-20
> 7.) Right click on items to edit labels and their launcher
When I do tha all I get is the 'add to favourites' menu
How do I change the names??

---

### Post by bulldog on 2006-08-20
Put an app. in your favorites and then right-click again.
You'll see a menu to change your preferences.

You can't changes the default names in all applications.

---

### Post by ashrack on 2006-08-20
SO in order to change the names in all apps my only option is to use ALACARTE, correct?
If so will this feature be implemented, so I would be able to rename/delete the programs from withing USP??

btw. congrats on your great work

---

### Post by compwiz18 on 2006-08-20
[QUOTE=chanders]
I will add the ENTER button to run in the next release. It seems you are running Metacity, try changing /apps/usp/panel_size option to 1 and restart USP...
[/QUOTE]

Works great.  thank you :D

---

### Post by delfick on 2006-08-20
> **bulldog said:**
> Take it easy,Chanders :D 

It's already a fine application.
Do what you think that's important and take your time.

Don't rush it,take it step by step, we have to wait with all our wishes.

You and your team do a hell of a good job and we all appreciate it.

i agree... :D

waiting for each new release is worth it :D

---

### Post by lazyd2 on 2006-08-20
> **delfick said:**
> i agree... :D

waiting for each new release is worth it :D

> **bulldog said:**
> Take it easy,Chanders :D 

It's already a fine application.
Do what you think that's important and take your time.

Don't rush it,take it step by step, we have to wait with all our wishes.

You and your team do a hell of a good job and we all appreciate it.
++1

Good things come to those who wait...:biggrin:

---

### Post by | MM | on 2006-08-20
Hello, in accord with everyone else i want to thank the creator of this wonderful utility!!

I have some questions :)

How do i use the tangerine Ubuntu icon and change the name of the button from *System*?

And also, i am not sure if this is a feature deficit or a bug but in my applications pane, i would quite like to be able to see recently used applications.  However, currently, unless i select all apps on start up my apps pane is empty until i search.  See attachment.

Oh and wheres the best place to keep an eye on recent updates, because synaptic is ~0.33 or something while there us a 0.44 file floating around.

I also think it would be good to have a recently installed section under applications.

Oh yea, and my colours are foo.


Cheers, and keep up the good work.

---

### Post by cptnapalm on 2006-08-20
I'm kind of torn on USP vs default 3 button approach.

On USP's side, it is very attractive, much more so than the default.  The lay out for things, with the large clickable areas, is superior.  Its clean and easy to use (the gap, notwithstanding).

The one thing which prevents me from using it much is that it pops up too much stuff.  If I want to hit the filesystem or launch an application, having Networking as a presented option doesn't do anything for me.  I much prefer the three separated menus to the one unified one.  There are some oddities with it, such as why there is a System Tool menu under Applications, when there is a System menu and the two submeus of the System menu could really use some grouping.  UCC would be a good one stop shopping for much of it.

Anyhow, just throwing this out there.

---

### Post by delfick on 2006-08-20
would it be possible to have user-specific plugins as extra menus instead of extra panes (as an option) ??

---

### Post by chanders on 2006-08-21
> **delfick said:**
> would it be possible to have user-specific plugins as extra menus instead of extra panes (as an option) ??

Off course! That is why I implemented the plugin system! What extra menus would you like to see?

> **ashrack said:**
> SO in order to change the names in all apps my only option is to use ALACARTE, correct?
If so will this feature be implemented, so I would be able to rename/delete the programs from withing USP??

btw. congrats on your great work

I think this would be a duplication of effort as Alacarte is an excellent program to edit the GNOME menu. I can however add an option to 'Edit with Alacarte' ;)

> **| MM | said:**
> Hello, in accord with everyone else i want to thank the creator of this wonderful utility!!

I have some questions :)

How do i use the tangerine Ubuntu icon and change the name of the button from *System*?

And also, i am not sure if this is a feature deficit or a bug but in my applications pane, i would quite like to be able to see recently used applications.  However, currently, unless i select all apps on start up my apps pane is empty until i search.  See attachment.

Oh and wheres the best place to keep an eye on recent updates, because synaptic is ~0.33 or something while there us a 0.44 file floating around.

I also think it would be good to have a recently installed section under applications.

Oh yea, and my colours are foo.


Cheers, and keep up the good work.

99% of all your questions are answered in this forum. Please do a search!

As for the latest release you can find it in the "New Release!!" sticky in the main forum...

> **cptnapalm said:**
> I'm kind of torn on USP vs default 3 button approach.

On USP's side, it is very attractive, much more so than the default.  The lay out for things, with the large clickable areas, is superior.  Its clean and easy to use (the gap, notwithstanding).

The one thing which prevents me from using it much is that it pops up too much stuff.  If I want to hit the filesystem or launch an application, having Networking as a presented option doesn't do anything for me.  I much prefer the three separated menus to the one unified one.  There are some oddities with it, such as why there is a System Tool menu under Applications, when there is a System menu and the two submeus of the System menu could really use some grouping.  UCC would be a good one stop shopping for much of it.

Anyhow, just throwing this out there.

Thanks for your input... You do know that you can minimize plugins to the plugins tray on the left? Just click the Plugin Label and it will be minimized. To un-minimize just do the opposite... That way you can hide items you dont want to see ;)

---

### Post by compwiz18 on 2006-08-21
Found something a little funny, I guess it's a bug, but not really that important (read: low priority ;)):

If you wanna see it, try this:

open a Terminal and **killall gnome-panel**
When it restarts, move your mouse over any of the headings (the things that you click to make the category disappear, i.e. Applications) and note that it pops out.

Click it.  Now click the little picture that means it's minimized (I guess that's the word...anyway just make it come back to its big state) and move your mouse over the heading again.  Note that it pops in now.

Any reason for that or am I just going crazy?

If you have something that I could do, I'd love to help...

---

### Post by delfick on 2006-08-21
> **chanders said:**
> [Quote=delfick] would it be possible to have user-specific plugins as extra menus instead of extra panes (as an option) ?? Off course! That is why I implemented the plugin system! What extra menus would you like to see?[/QUOTE]


what i meant was basically, add a new option to the plugins_list key in the options called "new_menu"..... then for example, if i had
applications
newpane
USPcomputer
new_menu
places
USPcalendar


then that would mean the first menu has two panes, one with applications and one with usp computer, whilst the second menu has one pane, with places on top and calendar on bottom....
then add the toggle bar as it's own plugin so that you can have that exactly where you want it....

that would be cool :D

---

### Post by Colonel Kilkenny on 2006-08-23
Hi. I didn't find anything with search regarding this: 

username@box:~$ usp run-in-window 
Traceback (most recent call last):
  File "/usr/bin/usp", line 1769, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1749, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1565, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 101, in __init__
    self.lang=self.language[0:2]
TypeError: unsubscriptable object

When I try to add the app to the panel, it goes there but isn't visible. When I move panel (from bottom to top for an example) it appears and after that I can move the app but still it cannot be clicked. 

Any ideas? All dependencies are ok.
edit. And this is happening in gnome, I'm not using kde (some kde libraries are installed because of amarok).

---

### Post by chanders on 2006-08-23
> **Colonel Kilkenny said:**
> Hi. I didn't find anything with search regarding this: 

username@box:~$ usp run-in-window 
Traceback (most recent call last):
  File "/usr/bin/usp", line 1769, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1749, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1565, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 101, in __init__
    self.lang=self.language[0:2]
TypeError: unsubscriptable object

When I try to add the app to the panel, it goes there but isn't visible. When I move panel (from bottom to top for an example) it appears and after that I can move the app but still it cannot be clicked. 

Any ideas? All dependencies are ok.
edit. And this is happening in gnome, I'm not using kde (some kde libraries are installed because of amarok).

This seems to be a problem with the translation. Since USP changed so much in the last release the translation doesnt work well and it was missed when we released the last version. The next version will have translation disabled until most of the changes are done..

Quick fix:
Locate this line in /usr/bin/usp

```
self.lang=self.language[0:2]
```

and change it to 

```
self.lang = "en"
```

That should help until the next release (in a few days ;-))

---

### Post by Colonel Kilkenny on 2006-08-23
Thanks! That worked like my charm in local pub.

---

### Post by H.E. Pennypacker on 2006-08-23
When USP opens up, after selecting what it is you want, ideally, it should close, or it should close when someone clicks outside of USP.  Does this make sense?

If I open something up with USP (e.g. XMMS), and click outside of it (e.g. the desktop), the USP won't close automatically.  It needs to close better, because it a pain to click several times to get out of it on the deskopt, or to go back to the USP, and click on its icon.   

I am sure this makes sense, but if it doesn't, I'll elaborate.  Is there a fix for this, and if not, will it ever be fixed?

---

### Post by chanders on 2006-08-23
This should happen automatically... Are you sure you dont have it pinned? (small icon in the top left)

---

### Post by cbudden on 2006-08-23
> **chanders said:**
> This should happen automatically... Are you sure you dont have it pinned? (small icon in the top left)

I get a smiliar thing happen, but just with items on the right (date and time, theme etc), the other things cause the menu to close.

---

### Post by H.E. Pennypacker on 2006-08-24
> **chanders said:**
> This should happen automatically... Are you sure you dont have it pinned? (small icon in the top left)

Do you mean locked? No, I don't have the USP locked to the panel.  By the way, the main panel is on the bottom of the screen (i moved it down - there's only one panel now).

Do you know why it doesn't close when you click outside of the USP?  It makes sense that it should close immediately if the mouse leaves its window (the USP).

---

### Post by Uncle Spellbinder on 2006-08-24
> **H.E. Pennypacker said:**
> Do you mean locked? No, I don't have the USP locked to the panel.  By the way, the main panel is on the bottom of the screen (i moved it down - there's only one panel now).

Do you know why it doesn't close when you click outside of the USP?  It makes sense that it should close immediately if the mouse leaves its window (the USP).

The top left of the USP itself has a small bar that when clicked either "pins"  or "unpins" the USP .

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/USP_Pin.png[/IMG]

---

### Post by H.E. Pennypacker on 2006-08-24
Uncle Spellbinder, that small thing (the bar - the rectangular thing above "Places") in the top left corner has somewhat solved the problem.  Now, when I click on a USP entry (e.g. RealPlayer), the USP will go away.  

But, when I don't click on anything and change my mind about using the USP, it won't go away if I click on, say, the desktop.  It will close, however, if I open up another window, and *then* click on the desktop.  So, closing it requires opening up another window and then clicking on the desktop, which is somewhat of a pain.

Is there a solution?

---

### Post by ashrack on 2006-08-24
> **H.E. Pennypacker said:**
> But, when I don't click on anything and change my mind about using the USP, it won't go away if I click on, say, the desktop.  It will close, however, if I open up another window, and *then* click on the desktop.  So, closing it requires opening up another window and then clicking on the desktop, which is somewhat of a pain.

Is there a solution?
same here!!!

---

### Post by chanders on 2006-08-24
> **ashrack said:**
> same here!!!

Are you guys running compiz or metacity? When USP is unpinned, it supposed to go away as long as it loses focus. When it is pinned it will only go away if you click the button...

Make sure you have the pin button Unpressed...

---

### Post by lazyd2 on 2006-08-24
> **chanders said:**
> Are you guys running compiz or metacity? When USP is unpinned, it supposed to go away as long as it loses focus. When it is pinned it will only go away if you click the button...

Make sure you have the pin button Unpressed...
I'm running compiz and I don't have this problem..

---

### Post by Uncle Spellbinder on 2006-08-25
> **lazyd2 said:**
> I'm running compiz and I don't have this problem..

Ditto

---

### Post by chanders on 2006-08-25
Figured as much... I dont use Metacity myself so I guess that's where it crept in. Will have to remember that for future development... ;)

---

### Post by scolex on 2006-08-25
just for inspiration: [http://home.kde.org/~binner/kickoff/sneak_preview.html](http://home.kde.org/~binner/kickoff/sneak_preview.html)

---

### Post by Malac on 2006-08-25
For reference; I am using metacity and my USP panel does disappear when I click the desktop.
Just to throw in more confusion. :)

---

### Post by Paool on 2006-08-25
I can't add usp to panel, error says that's problem while loading "OAFIID:GNOME_USP" :(

---

### Post by monktbd on 2006-08-25
> **chanders said:**
> Are you guys running compiz or metacity? When USP is unpinned, it supposed to go away as long as it loses focus. When it is pinned it will only go away if you click the button...

I guess the confusion comes in because people think it should go away on a mouse_out-event (i.e. the mouse pointer leaves the menu and after some time the menu closes automatically).

Mine works well and I really like it (metacity). 
Thanks for the efforts so far!

---

### Post by H.E. Pennypacker on 2006-08-25
> **chanders said:**
> Are you guys running compiz or metacity? When USP is unpinned, it supposed to go away as long as it loses focus. When it is pinned it will only go away if you click the button...

Make sure you have the pin button Unpressed...

When running Metacity, this problem does occur, but with Compiz, it doesn't.  I switch between the two window managers.

---

### Post by chanders on 2006-08-25
> **scolex said:**
> just for inspiration: [http://home.kde.org/~binner/kickoff/sneak_preview.html](http://home.kde.org/~binner/kickoff/sneak_preview.html)

See [this]("http://www.compiz.net/topic-3514-new-kde-start-menu-suse") thread ;)

> **Paool said:**
> I can't add usp to panel, error says that's problem while loading "OAFIID:GNOME_USP" :(

This had occured before with someone on this thread (sorry, didnt do a search), but I think it was because his install was messed up. Do you have a defauly dapper installation, and did you remove / change any python packages?

---

### Post by ADRez on 2006-08-25
[http://www.ubuntuforums.org/showthread.php?t=235887](http://www.ubuntuforums.org/showthread.php?t=235887)

I had that problem and it was solved installing python2.4-gnome2-desktop

---

### Post by Theava on 2006-08-26
For some reason usp does not show up in /apps/usp . its just not there at all? any ideas?

---

### Post by monktbd on 2006-08-26
> **Theava said:**
> For some reason usp does not show up in /apps/usp . its just not there at all? any ideas?

Do you look in the file system or in the gconf editor?

Just asking cos this (file system) is what i thought at first as well when i read all the references to /apps/ups :oops: .
It should be in the gconf editor.
Type
> gconf-editor
on the command line for that.

---

### Post by Uncle Spellbinder on 2006-08-26
> **Paool said:**
> I can't add usp to panel, error says that's problem while loading "OAFIID:GNOME_USP" :(

I had the same problem a couple weeks ago. This fixed it:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by ashrack on 2006-08-26
but am using COMPIZ and it doesnt dissappears when clicking on the desktop! BUt it does disappear when clicking on an app from withing USP!

Just had to add even more confusion,

---

### Post by cbudden on 2006-08-26
> **cbudden said:**
> Hello again.

After switching themes again, but this time differently, buy going back to straight Human and switching controls back to Linsta, my USP is again beautiful.

Thanks

Hello again. 

I have installed Ubuntu on my new laptop and the same problem has occured, same user profile as on the old system where the icon is fine, but now i have that annoying grey line again.  I tried the theme switching but its stuck.  Any ideas?

---

### Post by Theava on 2006-08-26
> **monktbd said:**
> Do you look in the file system or in the gconf editor?

Just asking cos this (file system) is what i thought at first as well when i read all the references to /apps/ups :oops: .
It should be in the gconf editor.
Type

on the command line for that.

Yeah I was in gconf-editor

---

### Post by chanders on 2006-08-26
> **cbudden said:**
> Hello again. 

I have installed Ubuntu on my new laptop and the same problem has occured, same user profile as on the old system where the icon is fine, but now i have that annoying grey line again.  I tried the theme switching but its stuck.  Any ideas?

Mind reminding me of the problem cbudden?

> **Theava said:**
> Yeah I was in gconf-editor

/apps/usp isnt created until USP is launched. Also be sure you are not looking under schemas, as one user was doing that ;)

---

### Post by Theava on 2006-08-26
Its launched, i tried that, and rebooted. Still cant seem to find it, definatly not in schemas... have a look.. This darn thing is so cool, just wish i could config it...

[Screenshot here]("http://i1.tinypic.com/25pogaa.png")

---

### Post by cbudden on 2006-08-26
[QUOTE=chanders;1426355]Mind reminding me of the problem cbudden?


[http://ubuntuforums.org/showpost.php?p=1382919&postcount=412](http://ubuntuforums.org/showpost.php?p=1382919&postcount=412)

Thanks


Along with the screenshot from that post, here is one with the icon displayed properly, with the Tangerine icon theme

[IMG]http://img172.imageshack.us/img172/6663/screenshot2yp7.png[/IMG]

---

### Post by chanders on 2006-08-26
> **Theava said:**
> Its launched, i tried that, and rebooted. Still cant seem to find it, definatly not in schemas... have a look.. This darn thing is so cool, just wish i could config it...

[Screenshot here]("http://i1.tinypic.com/25pogaa.png")

OK, try running this in a terminal...

usp run-in-window

and post your output for me...

> **cbudden said:**
> [QUOTE=chanders;1426355]Mind reminding me of the problem cbudden?


[http://ubuntuforums.org/showpost.php?p=1382919&postcount=412](http://ubuntuforums.org/showpost.php?p=1382919&postcount=412)

Thanks

Along with the screenshot from that post, here is one with the icon displayed properly, with the Tangerine icon theme

[IMG]http://img172.imageshack.us/img172/6663/screenshot2yp7.png[/IMG][/QUOTE]

The size of the button iz determined by the size of the icon. It should be fixed in the next release. Make sure you have an icon size 24 in your current theme to use. Maybe you can make one called usp-icon or something and set it in gconf-editor...

---

### Post by cbudden on 2006-08-26
> **chanders said:**
> OK, try running this in a terminal...

usp run-in-window

and post your output for me...



The size of the button iz determined by the size of the icon. It should be fixed in the next release. Make sure you have an icon size 24 in your current theme to use. Maybe you can make one called usp-icon or something and set it in gconf-editor...

Thanks for the tip re the icon.  What folder should the icon I make go into?  I want to use Human as a theme.

Here is the output :

```

Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Dir exist
Dir exist
Dir exist
Application added - /home/cbudden/.usp/applications/gnome-terminal.desktop
Application added - /home/cbudden/.usp/applications/firefox.desktop
Application added - /home/cbudden/.usp/applications/xchat.desktop
Application added - /home/cbudden/.usp/applications/gconf-editor.desktop
Application added - /home/cbudden/.usp/applications/democracyplayer.desktop
Application added - /home/cbudden/.usp/applications/avidemux.desktop
Application added - /home/cbudden/.usp/applications/vmware-server.desktop
Application added - /home/cbudden/.usp/applications/google-picasa.desktop
Application added - /home/cbudden/.usp/applications/Flickr.desktop
Place added - /home/cbudden/.usp/places/nautilus-home.desktop
Place added - /home/cbudden/.usp/places/-home-cbudden-Desktop.desktop
Place added - /home/cbudden/.usp/places/nautilus-computer.desktop
Place added - /home/cbudden/.usp/places/network-scheme.desktop
Place added - /home/cbudden/.usp/places/file:---home-cbudden.desktop

```

---

### Post by Theava on 2006-08-26
> **chanders said:**
> OK, try running this in a terminal...

usp run-in-window

and post your output for me...



Great, that worked. Now the /apps/usp/ exists.It doesnt seem to have any effect on the menu when they are changed... thanks for the help.

```
theava@theava-laptop:~$ usp run-in-window
Dir exist
Dir exist
Dir exist
Application added - /home/theava/.usp/applications/firefox.desktop
Application added - /home/theava/.usp/applications/gaim.desktop
Application added - /home/theava/.usp/applications/gnome-terminal.desktop
Application added - /home/theava/.usp/applications/eclipse.desktop
Application added - /home/theava/.usp/applications/MySQLAdministrator.desktop
Application added - /home/theava/.usp/applications/gimp-2.2.desktop
Place added - /home/theava/.usp/places/nautilus-home.desktop
Place added - /home/theava/.usp/places/-home-theava-Desktop.desktop
Place added - /home/theava/.usp/places/nautilus-computer.desktop
Place added - /home/theava/.usp/places/network-scheme.desktop
Place added - /home/theava/.usp/places/-home-theava-Downloads.desktop
Place added - /home/theava/.usp/places/-home-theava-Documents.desktop

(usp:15264): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition


```

---

### Post by Theava on 2006-08-26
Seems to be working now.

---

### Post by chanders on 2006-08-26
Excellent!

---

### Post by lassegs on 2006-08-28
Hi

Thanx for a great app. The only thing that bugs me is that my Codeweavers Crossover Windows-apps doesnt show up in the applications list, even though they are shown in the regular gnome menu and in alacarte.

Also, i was wondering if you could bind some key to the application filter button, so it could work a little like desk bar (quicksilver thingy)?


Cheers

Edit: huge typo

---

### Post by PWill on 2006-08-29
I love this! I am running 0.41, but I have a few issues. First, I don't have the names of the plugins, like Apps, Places, etc., on the left panel, as you can see in the screenshot.

Also, my wireless card is eth2, so even though I am connected wirelessly, it still says "Wired Network." It can get the IP, but I'd love if it said the wireless info. I tried wlan0, and all that, but not good results.

Where is the weather pluging grabbing its info from? It doesn't match the info from GNOME's Weather applet.

Cheers,
Paul

---

### Post by wouterommeslag on 2006-08-29
I've just installed it. It's cool, I like it a lot !! :)

---

### Post by senectus on 2006-08-29
This is rather interesting... I'll be watching this closely for a semi stable/reliable release, cause I really liked that part of SLED.

---

### Post by macewan on 2006-08-29
installed without problem - thanks

---

### Post by phido on 2006-08-29
> **xiamcitizen said:**
> I love this! I am running 0.41, but I have a few issues. First, I don't have the names of the plugins, like Apps, Places, etc., on the left panel, as you can see in the screenshot.


Close the open tabs by clicking on the headline eg. "Applications" and you should get an icon on the left panel.

---

### Post by Captain Rotundo on 2006-08-29
I just learned about this on digg, and have never used SLED, I've downloaded several versions of the deb, and none of them work.  It installs fine but nothing gets added to the panel when I select it from the "Add to Panel" dialog.

---

### Post by chanders on 2006-08-29
try running 

usp run-in-window

and post your output..

---

### Post by jam1n on 2006-08-29
I love it. great work

---

### Post by Odice on 2006-08-29
I did'nt like the last 0.40-1 version, the replace of the words of the panes with icons, and one icon is broken. So i'll stay with the version in the repos, that looks really great.

Nice job!

---

### Post by lost.sync on 2006-08-29
first of all, this is crazy slick.  thank you for sharing it with us.  it works really well, not to mention giving me like three inches of my top panel back from gnome's stock menu.

and secondly, as an above poster mentioned, is it possible to get the vertical text instead of the icons for the system shortcuts on the left, as shown in the screenshot on the 1st post?  i like that better for some reason, probably because the icons are pretty small and it'd be easier if i could just read some text, as my eyesight rather blows.

thanks again!

---

### Post by chanders on 2006-08-29
Sure thing! It is customizable in the next release ;)

---

### Post by ricperry1 on 2006-08-29
Thanks for the very awesome software.  I will be following this one closely.  
Feature request:  Can you replace the Search Bar with the Deskbar panel applet?  For that matter, is it possible to allow the docking of any panel applet into USP?  That would really make USP stand out far above SLED menu.

Rich
[http://ricperry.homeip.net/news](http://ricperry.homeip.net/news)

---

### Post by spyke01 on 2006-08-29
amazing work, are there any themes available for it?

---

### Post by thekidder on 2006-08-29
-deleted-

---

### Post by lazyd2 on 2006-08-29
> **spyke01 said:**
> amazing work, are there any themes available for it?
Not yet ;)

---

### Post by captainpotato on 2006-08-30
FWIW, I've just downloaded USP and think it's great - thanks very much :)

---

### Post by Captain Rotundo on 2006-08-30
Installed 0.41 and this is the output:

~/Desktop $ usp run-in-window
Traceback (most recent call last):
  File "/usr/bin/usp", line 1769, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1749, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1565, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 101, in __init__
    self.lang=self.language[0:2]
TypeError: unsubscriptable object
~/Desktop $

---

### Post by Captain Rotundo on 2006-08-30
I seems that for some reason the default language on my dapper install was screwed up, I went in and changed it to English (which it should have been I assume) and USP seems to be working.

---

### Post by Tonren on 2006-08-30
Unfortunately, this does not show up properly in my dark system theme.  Perhaps some changes to the color code would fix the problem shown below:

---

### Post by ahawks on 2006-08-30
Just wanted to say I love it!  I tried one of the first releases and liked the concept, but being as early as it was, wasn't too impressed at the time.

I just got version 0.41-1, and I have to commend you for USPs quality, customizability, and features. Also, I think you've done a great job listening to suggestions. 

My only requests:
- Keyboard support (I already read you plan on putting this in)
- A run box / have the app search box search $PATH. 
- Possibly tied to the run box, deskbar-applet functionality.

---

### Post by Horizon on 2006-08-30
Once you have all the plugin stuff done are you thinking of allowing customizable layout? I think it would be great if I could say...organize two columns into a similar layout to slab. Although I think there's better configurations than the slab one which could be thrown together. You've basically got all the infrastructure for this already. All you would have to do is create a system for creating new custom columns and adjusting column width and the height of the whole applet.

---

### Post by DBO on 2006-08-30
you will be happy to hear that there is rumor of a SLAB plugin that makes USP look and act just like SLAB! =)

---

### Post by chanders on 2006-08-31
> **Tonren said:**
> Unfortunately, this does not show up properly in my dark system theme.  Perhaps some changes to the color code would fix the problem shown below:

You need to check use_custom_color and set your color to match your theme in custom_color all done in gconf-editor

> **Horizon said:**
> Once you have all the plugin stuff done are you thinking of allowing customizable layout? I think it would be great if I could say...organize two columns into a similar layout to slab. Although I think there's better configurations than the slab one which could be thrown together. You've basically got all the infrastructure for this already. All you would have to do is create a system for creating new custom columns and adjusting column width and the height of the whole applet.

Already coded in the next release you can set indivudal width and height of each plugin so you can customize it just as you please..

---

### Post by benclinch on 2006-08-31
Hi,
I just got usp, really good, its very useful to me.
But I have one problem with it...
When i click on System and it opens, it isn't right next to the panel!
It is perfectly alligned to the left, but about 20 pixels away from my panel at the top of the screen, I can see any window or the desktop that is behind, how can I fix this please?

Ben

---

### Post by bulldog on 2006-08-31
Startup gconf editor and go to apps->usp.
Set panel size =1 and there is a good chance that your problem disappear.

You can find a whole lot of settings here,wich can be altered to your liking.

---

### Post by Malac on 2006-08-31
A small thing I know but my panel still reads 08-31-2006 can I set it to read 31-08-2006 UK like?
I've tried eu_date_format but this doesn't seem to do anything.

---

### Post by chanders on 2006-08-31
> **Malac said:**
> A small thing I know but my panel still reads 08-31-2006 can I set it to read 31-08-2006 UK like?
I've tried eu_date_format but this doesn't seem to do anything.

eu-date does not work for the time plugin. This is added in the next release..

---

### Post by Malac on 2006-09-01
Thanks very much. This is a great app by the way. :)

---

### Post by jackdirt on 2006-09-02
After all the painful sudo apt-get permission config utilities i have installed this by far has been the most painless and most useful installation to date. Truly fantastic

---

### Post by florizs on 2006-09-02
I Agree Terific ap :-) I was waiting for something like this!

---

### Post by Malac on 2006-09-02
> **chanders said:**
> eu-date does not work for the time plugin. This is added in the next release..
I've done a temp fix for the date thing by changing USPtime.py code.
Here's what I did if anyone wants to do it.
```
sudo gedit /usr/lib/python2.4/site-packages/usp/plugins/USPtime.py
```
and change line 50:
```
self.wTree.get_widget("label1").set_label('<span size="large" weight="bold">' + datetime.datetime.today().strftime("%m-%d-%Y") + '</span>')
```
to read :
```
self.wTree.get_widget("label1").set_label('<span size="large" weight="bold">' + datetime.datetime.today().strftime("[COLOR=DarkRed]**%d-%m**[/COLOR]-%Y") + '</span>')
```
Easy. :)

---

### Post by Polygon on 2006-09-02
well, i really dislike having to set manually the custom colors using conf editior, not to mention my theme is tan and the header text is now like invisible cause its silver on tan, and i dont see any option for custom text color.

Maybe just make it so the color matches the theme like in previous verisons? and add a way to change the font color =P

---

### Post by chanders on 2006-09-02
> **Polygon said:**
> well, i really dislike having to set manually the custom colors using conf editior, not to mention my theme is tan and the header text is now like invisible cause its silver on tan, and i dont see any option for custom text color.

Maybe just make it so the color matches the theme like in previous verisons? and add a way to change the font color =P

@ Malac - Great patch ;)

@ Polygon - I will add the text color in the next release, as for the app using the gtk theme color, I will see what I can do. Curently I dont know of a way to resd this information from the current theme... If anyone does, let me know...

@ florizs, Malac, captainpotato- i am glad you guys like it... And we are improving all the time... :-D 

@ Bulldog. Phido - Thanks for helping us out by answering all the questions =D>

---

### Post by delfick on 2006-09-04
so how's the next release going?

---

### Post by ADRez on 2006-09-04
Another little hack:

I think it's line 795:
CategoryButton.connect("button_press_event", self.Filter, child.name)

By this:
CategoryButton.connect("enter_notify_event", self.Filter, child.name)

That's for not having to click on application groups to select them.
I like it a lot :-D

---

### Post by neymac on 2006-09-05
I'm using USP 0.33 working fine, installed with synaptic.

I forgot wich is the repository for the last stable version.

Is 0.33 the last stable version of USP?
If not, which is it's repository?

---

### Post by bulldog on 2006-09-06
Look under topic "New Release" and you will find this one :D 

[http://ubuntuforums.org/attachment.php?attachmentid=14269&d=1155524787](http://ubuntuforums.org/attachment.php?attachmentid=14269&d=1155524787)

---

### Post by Malac on 2006-09-07
Okay I seem to have fixed the eu_date_format thing for computer plugin.
Could someone confirm this works on their system too.
In USPcomputer.py change this section:
```
    def date_time(self):
        try:
             if self.eudate == False:
self.wTree.get_widget("label9").set_label(datetime.datetime.today().strftime("%m-%d-%Y"))
            else:
self.wTree.get_widget("label9").set_label(datetime.datetime.today().strftime("%d-%m-%Y"))
``` to marked in [COLOR=Red]red[/COLOR]:
```
    def date_time(self):
        try:
             if self.eudate == [COLOR=Red]0[/COLOR]:
                self.wTree.get_widget("label9").set_label(datetime.datetime.today().strftime("%m-%d-%Y"))
            else:
                self.wTree.get_widget("label9").set_label(datetime.datetime.today().strftime("%d-%m-%Y"))

``` 

This now seems to work for me. I can change between eu and us date formats. :)


Edit :
New USPtime.py
I've just had a go at re-writing USPtime to take this into account and it seems to work. Some of the code could be superfluous as I have just cut and pasted some of the code from USPcomputer.py taking out what didn't seem right.
I've never coded in python before so this may not be correct, please could someone (chanders?) let me know.
```
# Basic USP plugin

import gtk
import gtk.glade
import sys
import os
import gobject
import datetime
import gconf
import commands
from execute import Execute
from easygconf import SetGconf

class pluginclass:
    """This is the main class for the plugin"""
    """It MUST be named pluginclass"""

    def __init__(self):

        #The Glade file for the plugin
        self.gladefile = "/usr/lib/python2.4/site-packages/usp/plugins/plugin1.glade"

        #Read GLADE file
        self.wTree = gtk.glade.XML(self.gladefile,"window1")

        #These properties are NECESSARY to maintain consistency
        #throughout USP

        #Set 'window' property for the plugin (Must be the root widget)
        self.window = self.wTree.get_widget("window1")

        #Set 'heading' property for plugin
        self.heading = "Time and Date"

        #This should be the first item added to the window in glade
        self.content_holder = self.wTree.get_widget("eventbox1")

        #Specify plugin width
        self.width = 150

        #Plugin icon
        self.icon = 'gnome-set-time'

        self.gconf_dir = '/apps/usp/plugins/computer'
        self.client = gconf.client_get_default()
        self.client.add_dir('/apps/usp/plugins/computer', gconf.CLIENT_PRELOAD_NONE)
        self.client.notify_add('/apps/usp/plugins/computer/eu_date_format',self.RegenPlugin)

        self.RegenPlugin()
        gobject.timeout_add(1000, self.date_time)

    def RegenPlugin(self, *args, **kargs):
        self.GetGconfEntries()
        self.get_gconf_info()

    def SetupEvents(self):
        #Connect event handlers
        dic = {"on_window1_destroy" : gtk.main_quit}
        self.wTree.signal_autoconnect(dic)

    def GetGconfEntries(self):
        self.client = gconf.client_get_default()
        self.eudate = SetGconf(self.client,'bool','/apps/usp/plugins/computer/eu_date_format', False)

    def get_gconf_info(self, *args, **kwargs):
        resolution=freq=gtktheme=icontheme=None
        resolution = self.client.get_string('/desktop/gnome/screen/default/0/resolution')
        freq = self.client.get_int('/desktop/gnome/screen/default/0/rate')
        icontheme = self.client.get_string('/desktop/gnome/interface/icon_theme')
        gtktheme = self.client.get_string('/desktop/gnome/interface/gtk_theme')

    #Actually do something with the plugin
    def date_time(self):
        try:
             if self.eudate == 0:
                self.wTree.get_widget("label1").set_label('<span size="20000" weight="bold">' + datetime.datetime.today().strftime("%m-%d-%Y") + '</span>')
            else:
                self.wTree.get_widget("label1").set_label('<span size="20000" weight="bold">' + datetime.datetime.today().strftime("%d-%m-%Y") + '</span>')


            self.wTree.get_widget("label2").set_label('<span size="20000" weight="bold">' + datetime.datetime.today().strftime("%H:%M:%S") + '</span>')
        except:
            pass
        return True
```

---

### Post by chanders on 2006-09-07
Looks great! I will add your patch for the next release ;-)

Check your pm...

---

### Post by Yemoke on 2006-09-07
i like usp really really much, but do you have any idea when you release the next release? because the little bug that it doesnt remember all the positions etc is a little bit annoying:-k i hope it's coming fast, nice job dude! :)

---

### Post by arkan over ip on 2006-09-07
I'm good with USP. Thanks for doing it, bud.

---

### Post by Malac on 2006-09-07
Wondered if you would like to take a look at my version of the USPtime plugin.
I've created a slightly different layout for the plugin1.glade file and altered the USPtime.py.
plugin1.glade now has a button to set the date and time.
USPtime.py adds the following keys to /apps/usp/plugins/datetime

eu_date_format (for switching mm/dd/yyyy to dd/mm/yyyy this can also be read from the USPcomputer.py file so everything is in one place)
settings_date_bold (fairly obvious) :)
settings_date_font_size (as per the one in the other plugins)
settings_date_sep (this is the character to use as seperator in numeric date as in - or / )
settings_date_string (shows the date as text as in "Sep 8, 2006")
settings_day_string (show the day as well if date_string is set as in "Fri. Sep 8, 2006")
settings_time_12_hour (shows the time in 12 hour am/pm format)
settings_time_bold (fairly obvious) 
settings_time_font_size (as per the one in the other plugins)
system_command1 (this is set to run 'gksu time-admin' as per the USPcomputer.py command structure)

I've attached the files if you want to give them a look.

Edit:
** Don't forget to back up or rename the original files before you unpack or you will lose your originals.**

As you can see from the attached thumbnail I've also altered the USPcomputer plugin to show or hide the date too so you haven't got both.
This can be done with any of the buttons in this version.
Using keys in gconf at
/apps/usp/plugins/computer/hide_computer
/apps/usp/plugins/computer/hide_control
/apps/usp/plugins/computer/hide_date
/apps/usp/plugins/computer/hide_net
/apps/usp/plugins/computer/hide_screen
/apps/usp/plugins/computer/hide_theme

Plus a calendar that opens evolution when a date is double-clicked, unfortunately not on the date clicked but I'm working on that.

Plus User display of Name and Face which also adds font alteration with gconf entries at:
/apps/usp/plugins/user/font_bold
/apps/usp/plugins/user/font_size
 /apps/usp/plugins/user/hide_logged_on
/apps/usp/plugins/user/name_below


Get plugins here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by nazionlinux on 2006-09-08
I would like to translate USP in italian... what can i do?

---

### Post by neymac on 2006-09-08
> **neymac said:**
> I'm using USP 0.33 working fine, installed with synaptic.

I forgot wich is the repository for the last stable version.

Is 0.33 the last stable version of USP?
If not, which is it's repository?

I found it.

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

But at [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) the last version is:

```
usp (0.33-1) [Download]
Ubuntu System Panel
Simple launcher for the GNOME desktop, providing easy access to Places, Applications and common configuration items for your computer.
```

---

### Post by chanders on 2006-09-08
@ Malac - Congrats, you just made/edited the first plugin that I will be including in the next release ;)

---

### Post by Malac on 2006-09-08
> **chanders said:**
> @ Malac - Congrats, you just made/edited the first plugin that I will be including in the next release ;)
Thanks, it's much appreciated.
Couldn't e-mail with attachments so I have attached the USPtime and USPcomputer files to the first post. #522
Plus a clickable calendar.py and plugin2.glade that opens evolution on double-click can't get the date selection on open to work so it just opens on today
Created key /apps/usp/plugins/calendar/system_command1

---

### Post by Skoezie on 2006-09-09
Maybe i'm missing something, but how can I change from the icons on the left in the menu to just the name??? And how do i prevent these buttons from disappearing when I click them? Using 0.41 @ the moment.

Edit: reverted back to 0.33.1 and looks ok now :-D

---

### Post by bulldog on 2006-09-09
You want to change the icons in place menu or get them out?
You can choose another theme to change them.
If you right click on one off them and choose edit you can see in the little menu that opens at the bottom a place where your icons get from.
Maybe,but I didn't try that,you can change this or remove it for no icon.

---

### Post by toasted on 2006-09-12
Chanders...
Thanks a bunch for all the work!

I did not read all 50 some pages... close though!
Is there a plan to make it so right click enables the add to desktop or add to panel or edit feature for Applications and Computer items? As is is now, mine only has this on the Places menu. If I right click something in Applications menu it offers to "add to favorites" only.

Also I have seen screenies of people's USP that had their log in name and photo on there... I didnt see this in gconf editor. Is it there?

---

### Post by Skoezie on 2006-09-13
[http://www.ubuntuforums.org/showthread.php?t=255381](http://www.ubuntuforums.org/showthread.php?t=255381)

---

### Post by toasted on 2006-09-13
Thanks!

---

### Post by Malac on 2006-09-13
Okay, took me all day but here is my terminal emulator first draught.
it requires libvte4 package.
It creates two keys for width and height under /apps/usp/plugins/terminal
Unfortunately these don't alter dynamically yet but I'll work on it.
Other than that it's a terminal. :smile:
[ATTACH]15687[/ATTACH]
Edit: 
Uploaded a new USPterm to this post and a new USPconfig to post 541 page 55 which now add colour to the terminal. This is a bit hit and miss at the moment due to colour calculations for the vte palette I think and it does require that you remove USPterm from the plugins list then add it again. If that doesn't work restart USP and repeat the process. Don't know why this works but as you can see from the next attachment it does.
[ATTACH]15880[/ATTACH]
Now does Background Picture if you want.
[ATTACH]16311[/ATTACH]

Get plugins here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by chanders on 2006-09-13
I must say, you are doing some excellent work, not to mention knocking off plugins like crazy! Brilliant!

Quick note: The Terminal starts up in the root directory. By adding this line 

os.chdir(os.path.expanduser("~"))

just before

self.terminal = vte.Terminal()

It will start up in the users home directory..

---

### Post by Malac on 2006-09-13
okay chanders, I'll update the tar now. 
Edit : Or after they've finished updating the database. :) 
Any ideas on the width and height not updating immediately?

'Tis Done.

Edit :
Is there a good online reference to what all the widget methods and properties are, preferably with some code examples?
Most of the time spent so far has been trying to find out what they are and how to alter them in Python.

---

### Post by chanders on 2006-09-14
> **Malac said:**
> Is there a good online reference to what all the widget methods and properties are, preferably with some code examples?
Most of the time spent so far has been trying to find out what they are and how to alter them in Python.

I am afraid not.. I just like you, have learnt PyGTK by trial and error. This makes development time consuming. There is an online reference that I make reference to [here]("http://www.pygtk.org/pygtk2reference/") and a good FAQ to help with some examples [here]("http://www.async.com.br/faq/pygtk/index.py?req=all")... Hope it helps you continue your excellent work

---

### Post by Malac on 2006-09-14
Cheers chanders,
I'll checkout the links tomorrow, very tired as I'm working on a major upgrade to some of my win32 progs at the mo.
Dive in at the deep end, has always worked for me.
Did the same when I learned C, C++, dBase, DBC, Clipper, etc.

---

### Post by vishytk on 2006-09-15
Can i get the source for USP

---

### Post by Malac on 2006-09-15
.

---

### Post by chanders on 2006-09-15
> **vishytk said:**
> Can i get the source for USP

Download the .deb file, extract it or install it and look for the file "usp" in /usr/bin

---

### Post by fantan on 2006-09-16
Hi chanders,

I would like to know, how to add new items to the Computer pane.
In the gconf I find just six system_commands:
system_command1=gnome-system-monitor
system_command2=gksu network-admin
system_command3=gksu time-admin
system_command4=gnome-theme-manager
system_command5=gnome-display-properties and
system_command6=gcontrol, but
I would like to add another one jet: gconf-editor.
I tried do that but no success!
I added in the gconf-editor: 
apps/usp: name=syste-command7, type=string, value=gconf-editor,
apps/usp/plugins/computer: name=/apps/usp/plugins/computer/system_command7, type=string, value=gconf-editor.
But on the USP screen, on the Settings pane I don't see the new item.
How should I do properly?

Thank you very much for advance.

fantan

---

### Post by Malac on 2006-09-16
Okay another **"experimental"** plugin.
USPconfig
This has settings to alter USP instead of opening gconf-editor.
It works with my current set of plugins, post #522 on page 53 and post #532 on page 54 of this thread.
As I don't have an untouched copy of USP 0.41.1 or the standard plugins I haven't tested it on them. Worst case you can still go back to gconf-editor. :)
Here are some screenshots:
[ATTACH]15812[/ATTACH][ATTACH]15813[/ATTACH][ATTACH]15814[/ATTACH][ATTACH]15815[/ATTACH]
I have not done the syscommandx actions on purpose.
 I think I've got all the other relevant settings, if I've missed any settings out please let me know.
Hope you enjoy.

Edit:
As a few people have asked how to install this here are the instructions these should work for my other plugins too.
Untar the files in USP---------.tar.gz into either /home/YOURUSERNAME/.usp/plugins hidden folder or as root in /usr/lib/python2.4/site-packages/usp/plugins.
And add USP-------- to the plugins list in gconf-editor at /apps/usp/plugins_list.
Replacing YOURUSERNAME with your username
And USP--------- with name of plugin, e.g. USPconfig, USPtime, etc.

Edit new USPconfig for changing new USPterm terminal(post 532 page 54) colours.

---

### Post by toasted on 2006-09-16
Maybe you guys missed my post a while ago. When I have a panel on top of the screen with USP on it, I cannot maximise a window, or have one closer than about 1/4". If I do, the USP panel will open, but once the mouse moves into the USP panel the panel closes on its own. If I move the window down just a bit then its fine.

---

### Post by fantan on 2006-09-16
Hi malac,

Your new 'experimental' plugin (USPconfig) is very-very nice and I think it is also very-very useful. My congratulations!

I've downloaded and installed it, everithing goas fine on my system.
It's true, that I use your plugins as well. 
Yust one thing: How can one localize (translate to other languages e.g. Hungarian) the content of the panels? I tried it but modify the file USPconfig.glade will be take a lot of time!

But if you thing I can make the Hungarian translation.

Best regards,

fantan

---

### Post by Malac on 2006-09-16
> **fantan said:**
> Hi malac,

Your new 'experimental' plugin (USPconfig) is very-very nice and I think it is also very-very useful. My congratulations!

I've downloaded and installed it, everithing goas fine on my system.
It's true, that I use your plugins as well. 
Glad you liked it fantan. \\:D/
> **fantan said:**
> Yust one thing: How can one localize (translate to other languages e.g. Hungarian) the content of the panels? I tried it but modify the file USPconfig.glade will be take a lot of time!

But if you thing I can make the Hungarian translation.

Best regards,

fantan
I don't know how glade handles localized strings if someone wants to let me know what I have to do in glade to make it except some sort of external input or translated labels.
If you want to send me a list of the translated phrases I will try to do a new glade file or feel free to do one yourself. :grin:

---

### Post by -fin on 2006-09-16
honestly, i'm not fond of the idea of having a plugin to configure the applet itself. it is surely a good intermediate solution, but i hope for it being deprecated soon.

why?
because all other applets have own configure-functions in the context menu of the applet. to ensure a consistent user experience, one would have to create such an entry and open this function in an own window. one example for this would be the deskbar applet.

i still appreciate the work done, because i suppose one can easily move this to an own window whenever neccessary (hooray for glade and copypaste ;))

---

### Post by fantan on 2006-09-16
Hi malac,

I don't know exactly ho to attach pictures or other things to my message here, because I never did that before. But I'll try.
See:
[ATTACH]15824[/ATTACH]

[ATTACH]15825[/ATTACH]

[ATTACH]15826[/ATTACH]

[ATTACH]15827[/ATTACH]
These pictures are part of the USPconfig pane after I started translate the USPconfig.glade file. Of course these are not all but just some templates.

To make a full translation I must find in the USPconfig.glade file all source phrases and write the translated words insteed.
For example:
.
.
.
 <child>
  <widget class="GtkLabel" id="SettingsLabel">
    <property name="visible">True</property>
insteed of this line:
    <property name="label" translatable="yes">Main Settings</property>
this one:
    <property name="label" translatable="yes">Beállítások</property>
.
.
But it takes a lot of time and not effective at all.
Do you know any other solution?

fantan

---

### Post by Malac on 2006-09-16
> **-fin said:**
> honestly, i'm not fond of the idea of having a plugin to configure the applet itself. it is surely a good intermediate solution, but i hope for it being deprecated soon.

why?
because all other applets have own configure-functions in the context menu of the applet. to ensure a consistent user experience, one would have to create such an entry and open this function in an own window. one example for this would be the deskbar applet.

i still appreciate the work done, because i suppose one can easily move this to an own window whenever neccessary (hooray for glade and copypaste ;))

Yes I thought of doing this as a standalone app but I've only just started coding in glade and python, about 3 weeks ago now I think, and this was all I could manage at the moment with my limited knowledge.(Thanks to chanders for help and code comments in the original app/plugins and some web crawling.)

I thought of adding it to the right-click menu of the app button, where the "About" entry is, but my attempts at this just kept screwing USP up so I aborted them for now. 

This was just a quick solution as I had seen a lot of requests for another way to configure USP. And as you say someone else may be able to re-use some of my work from the glade or python files.

---

### Post by Malac on 2006-09-16
> **fantan said:**
> 
[ATTACH]15824[/ATTACH]

[ATTACH]15825[/ATTACH]

[ATTACH]15826[/ATTACH]

[ATTACH]15827[/ATTACH]
These pictures are part of the USPconfig pane after I started translate the USPconfig.glade file. Of course these are not all but just some templates.


Looking good so far fantan. I think, as I don't read Hungarian. :)

 > **fantan said:**
> 
To make a full translation I must find in the USPconfig.glade file all source phrases and write the translated words insteed.
..........
But it takes a lot of time and not effective at all.
 Do you know any other solution?
 
That is what I would have done .
I'm afraid I don't know any other solution other than searching for all the "translatable=yes" parts of the tags.
Sorry.

---

### Post by chanders on 2006-09-16
Great work Malac. Just to let you know I will be packaging all of your plugins with USP2 when it is released..

Just for the benefit of our users, I will be modifying the config plugin to be a stand-alone config shortly (Before USP2 is released) so Malac if you like you can continuine working on it without worrying if it is taking too much space in the menu ;-)

---

### Post by fantan on 2006-09-17
Hi malac,
I thought that there isn't such method I'm looking for.
Because of this I began do the translation as you proposed.
The first tag of the USPconfig pane after Hungarian translation looks like this:
[ATTACH]15861[/ATTACH]

I'm going translate all tags to. But in this case the problem is that if anybody will modify anything in original file (USPconfig.glade), I will have to retranslate all the "translatable=yes" parts of the tags.

In any way I'm looking forward for all new versions too.
  
Best regards,
fantan

---

### Post by toasted on 2006-09-17
Is there somewhere else that I should post for support, or did you just miss my post?

---

### Post by Malac on 2006-09-17
Posted updated USPterm and USPconfig.
The USPterm now does colour and the USPconfig has been altered to take that into account.
So as not to upload multiple versions I've changed the originals at :
USPterm is at post #532 page 54
USPconfig is at post #541 page 55

---

### Post by chanders on 2006-09-17
> **toasted said:**
> Is there somewhere else that I should post for support, or did you just miss my post?

Actually I didnt miss your post... It's just I cant make anything of why USP would open if you maximize a window *scratches head*

USP is a button on the GNOME panel. The only way it should open is if it is clicked...

What happens if the USP button is placed at different places on the top panel?

---

### Post by toasted on 2006-09-17
> **chanders said:**
> Actually I didnt miss your post... It's just I cant make anything of why USP would open if you maximize a window *scratches head*

USP is a button on the GNOME panel. The only way it should open is if it is clicked...

What happens if the USP button is placed at different places on the top panel?

No, it doesnt open on its own, sorry I should have worded it better. If a window is maximised or within 1/4" of the top panel, and usp is installed in top panel on left...

Then when you click and open USP, you cannot move the mouse into the USP menu because it closes. If you move the window down a little (more than 1/4") then the menu works fine. 

See now?

Edit, attached a screen shot. In this scenario if I open the USP menu by clicking the panel button, I cannot move the mouse into it because it disappears. This really is where I want to use it but cannot due to this trouble. I'm running xgl/compiz, cairo-clock and kiba-dock if that matters

---

### Post by bryanchapman9999 on 2006-09-18
This looks great - good work.

However, the control center does nothing for me - I'd happily remove it if I could, but I'd prefer it to work.

Any ideas?

Cheers
Bryan

---

### Post by toasted on 2006-09-18
> **bryanchapman9999 said:**
> This looks great - good work.

However, the control center does nothing for me - I'd happily remove it if I could, but I'd prefer it to work.

Any ideas?

Cheers
Bryan

Yea, you have to install the control center before it will work. Check Synaptic.

---

### Post by Uncle Spellbinder on 2006-09-19
> **toasted said:**
> if I open the USP menu by clicking the panel button, I cannot move the mouse into it because it disappears. This really is where I want to use it but cannot due to this trouble. I'm running xgl/compiz, cairo-clock and kiba-dock if that matters

I use my panel at the bottom. I moved it to the top (with USP top left) and followed you description:

> **toasted said:**
> If a window is maximised or within 1/4" of the top panel, and usp is installed in top panel on left...
Then when you click and open USP, you cannot move the mouse into the USP menu because it closes.

No problems here. Compiz AIGLX, Edgy. Maybe different on Edgy?

---

### Post by toasted on 2006-09-19
> **Uncle Spellbinder said:**
>  Maybe different on Edgy?

It might be yea but this trouble i'm having is on Dapper. It has been like that since I installed USP as I run kiba-dock at the bottom and panel at top (thats my preference anyway). I can run it at the top as long as I keep windows away from it. For now I just dont use it, it's too annoying like this.

Thanks for checking it out anyway :)


Edit:
I must be the only one that has this trouble...  very odd

---

### Post by Malac on 2006-09-19
> **toasted said:**
> It might be yea but this trouble i'm having is on Dapper. It has been like that since I installed USP as I run kiba-dock at the bottom and panel at top (thats my preference anyway). I can run it at the top as long as I keep windows away from it. For now I just dont use it, it's too annoying like this.

Thanks for checking it out anyway :)


Edit:
I must be the only one that has this trouble...  very odd
Perhaps it's something to do with kiba-dock?

---

### Post by toasted on 2006-09-19
> **Malac said:**
> Perhaps it's something to do with kiba-dock?

If I close Kiba-dock it still does it... but it must be something specific to my system.

I went through all the csm settings turning them off one at a time and checking the USP menu each time. Nothing made the trouble go away. Switching to Metacity in csm does make the trouble go away however. 

I guess I have been running compiz since I first installed UPS so that must be the conflict. I have the install where I can choose xgl or metacity at boot screen so I will boot into metacity there and see what happens.

---

### Post by toasted on 2006-09-19
Ok I am now in a normal Dapper Gnome session and USP behaves correctly regardless of window position. Im current with compiz Quinn-Storm updates and just got the updated 686 kernel today. 

Any suggestions?  Its not a biggie but I thought you guys would like to know......

Edit:
sorry I didnt think to try this before....

---

### Post by toasted on 2006-09-20
Ok I found out what does it. I had unchecked "click to focus" in general options of CSM. In this condition one simply has to mouse over a window to give it focus. 

When I checked the 'click to focus' box then USP started to behave as it should. Now, this is probably a compiz thing so I will post there. 

Thanks for listening  :)

---

### Post by ahawks on 2006-09-20
I love USP, but I have a request:

Instead of a 55+ page forum thread tracking releases, plugins, etc... would it be possible to create a DEB repository with USP and all the plugins?  Reading through page upon page of the thread looking for the latest "download it here" link is getting a bit tedious. 

I have never set up a deb repo before, but back in my Fedora days I set up plenty of yum servers, and it's pretty simple.

---

### Post by chanders on 2006-09-20
I will talk to Quinn and see if we can get that done. For now I will make a new thread just for plugin downloads.

---

### Post by Malac on 2006-09-22
[SIZE=2]Hi chanders and all,
I finally ported the USPconfig plugin to a seperate standalone app which I have attached to this post for you to checkout.
As ever if there are some settings missing let me know.
Perhaps a pre-defined button in USP could launch this.
[/SIZE][ATTACH]16270[/ATTACH]
[SIZE=2] Anyway, I'm working on the USPuser plugin at the mo as I see some people like the picture above the name so I will see about incorporating that.

And still trying to see if I can figure out the USPterm colour issues.

[B]Edit:
[/B]USPconfig Application now at post #573 page 58.
[/SIZE]

---

### Post by delfick on 2006-09-23
> **Malac said:**
> [SIZE=2]Hi chanders and all,
I finally ported the USPconfig plugin to a seperate standalone app which I have attached to this post for you to checkout.
As ever if there are some settings missing let me know.
Perhaps a pre-defined button in USP could launch this.
[ATTACH]16146[/ATTACH]
Anyway, I'm working on the USPuser plugin at the mo as I see some people like the picture above the name so I will see about incorporating that.

And still trying to see if I can figure out the USPterm colour issues.[/SIZE]


how do we use it?

---

### Post by pantless on 2006-09-23
pretty.... thank you...

---

### Post by Malac on 2006-09-23
[SIZE=2]> **delfick said:**
> how do we use it?
Untar the files into your home folder somewhere or /usr/bin.
If in /usr/bin you will need to do this as root.
Right-Click, change Permissions to Execute for Owner, Groups and Others
```
./USPconfig (from the folder)
```Or within nautilus double-click USPconfig or set up a shortcut.

I've also re-done the USPuser plugin to allow for changing Username position to below the picture and hiding/showing of logged on time.

[B]Edit : Please re-download the file from original post as there was a bug with the plugins list in the previous version.
[/B]I see 8 people have downloaded it.Sorry for the bug but it should not have effected your USP.[/SIZE]

---

### Post by delfick on 2006-09-23
> **Malac said:**
> [SIZE=2]
Untar the files into your home folder somewhere or /usr/bin.
If in /usr/bin you will need to do this as root.
Right-Click, change Permissions to Execute for Owner, Groups and Others
```
./USPconfig (from the folder)
```Or within nautilus double-click USPconfig or set up a shortcut.


thnx for that (though i prefer it in /usr/sbin so that typing USPconfig in the terminal from within any folder, opens it up :D)

good stuff too :D much better than as a plugin in the USP menu.....

though, can it be made as another icon in the system plugin thingo so it appears on the toggle pane when compact_system_management is chosen? (speaking of which, where is that option in USPconfig?)

thnx for all ur hard work :D :D

---

### Post by Malac on 2006-09-23
> **delfick said:**
> thnx for that (though i prefer it in /usr/sbin so that typing USPconfig in the terminal from within any folder, opens it up :D)

good stuff too :D much better than as a plugin in the USP menu.....

though, can it be made as another icon in the system plugin thingo so it appears on the toggle pane when compact_system_management is chosen? (speaking of which, where is that option in USPconfig?)

thnx for all ur hard work :D :D

I'm not sure how integrated chanders wants to make this with USP itself.
At the moment I just made an entry in my 'Applications' section to launch it.
Sorry about the compact system toggle I wasn't sure what was happening with this as it is now a seperate plugin so I left it out.
If it is staying in then I'll include it in the next posted version.

---

### Post by .nat on 2006-09-29
help me plz. i put c:Usp:90 in csm but nothing  result(sorry my english)

---

### Post by cbudden on 2006-09-29
> **.nat said:**
> help me plz. i put c:Usp:90 in csm but nothing  result(sorry my english)

Use w:Menu:80 , For 80 transparency.

---

### Post by Malac on 2006-10-02
New plugin USPnotes.
[ATTACH]16714[/ATTACH]
A sort of quick notes thing.
Save Button saves the file to the users Desktop with the name from the current time in the form yyyymmdd-hh:mm:ss e.g. 20061002-10:53:24 if no filename is provided or it will append the text from the filename field to the beginning e.g. SomeFile20061002-10:53:24.
Clear Button clears the "pad" and filename field.

GConf Keys:
/apps/usp/plugins/notes/height
/apps/usp/plugins/notes/width

I have also uploaded a new USPconfig App. to this post which incorporates this plugin.

[SIZE=2][/SIZE]Get them here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by delfick on 2006-10-03
> **Malac said:**
> New plugin USPnotes.
[ATTACH]16714[/ATTACH]
A sort of quick notes thing.
Save Button saves the file to the users Desktop with the name from the current time in the form yyyymmdd-hh:mm:ss e.g. 20061002-10:53:24 if no filename is provided or it will append the text from the filename field to the beginning e.g. SomeFile20061002-10:53:24.
Clear Button clears the "pad" and filename field.

GConf Keys:
/apps/usp/plugins/notes/height
/apps/usp/plugins/notes/width

I have also uploaded a new USPconfig App. to this post which incorporates this plugin.

let the attached screenshot speak for me :D......
(look at the quick notes section of the menu...:D)

---

### Post by Malac on 2006-10-03
> **delfick said:**
> let the attached screenshot speak for me :D......
(look at the quick notes section of the menu...:D)
Thanks delfick, :)
Cheered me this morning.

---

### Post by Malac on 2006-10-03
***Very Basic*** Recent Documents Plugin :)

USPrecent
[ATTACH]16805[/ATTACH]
Gconf Keys:
/apps/usp/plugins/height
/apps/usp/plugins/width
/apps/usp/plugins/recent_font_size
/apps/usp/plugins/num_entries

If someone wants to improve this by adding icons, changed background colour etc., please feel free.

[SIZE=2][B]Edit : Fixed the colour issue.

[/B][/SIZE]Get it here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by chanders on 2006-10-03
> **Malac said:**
> If someone wants to improve this by adding icons, changed background colour etc., please feel free.

Will be making all items into buttons for easy access..

Ok an update for all the USP/Malac fans ;-).

USP2 is done. But I am not goint to release it until I am sure we have met all our goals. And so far we are nearly 100% there. 

I am trying to get all the requests in and I have to thank Malac for really helping out with all the work he has been doing.

Currently I am working on USPslab as it was supposed to be the highlight of this release, but now we have so much more to offer with all the new plugins.

USP2 will be released as a Beta for beta testing and when the bugs are ironed out we will have the final release...

Chanders

---

### Post by Malac on 2006-10-03
> **chanders said:**
> Will be making all items into buttons for easy access..

It doesn't show up on the screenshot but they already are buttons. :)
Just couldn't get the background colour to take.

---

### Post by delfick on 2006-10-03
> **chanders said:**
> USP2 is done. 

:D:D:D:D:D:D:D

> USP2 will be released as a Beta for beta testing and when the bugs are ironed out we will have the final release...

that sounds cool :D

---

### Post by smdeep on 2006-10-04
> **ahawks said:**
> I love USP, but I have a request:

Instead of a 55+ page forum thread tracking releases, plugins, etc... would it be possible to create a DEB repository with USP and all the plugins?  Reading through page upon page of the thread looking for the latest "download it here" link is getting a bit tedious. 

I have never set up a deb repo before, but back in my Fedora days I set up plenty of yum servers, and it's pretty simple.

I absolutely second it, after using USP for 24 hours, I would love to have the configuration tool and the plugins but it is very confusing. For example, I cannot figure out where to download the configuration tool from.

Great work! USP is fantastic.

---

### Post by Uncle Spellbinder on 2006-10-04
> **chanders said:**
> Will be making all items into buttons for easy access..

Ok an update for all the USP/Malac fans ;-).

USP2 is done. But I am not goint to release it until I am sure we have met all our goals. And so far we are nearly 100% there. 

I am trying to get all the requests in and I have to thank Malac for really helping out with all the work he has been doing.

Currently I am working on USPslab as it was supposed to be the highlight of this release, but now we have so much more to offer with all the new plugins.

USP2 will be released as a Beta for beta testing and when the bugs are ironed out we will have the final release...

Chanders


Good news!. Thanks so much for the work with USP. And Malac, too. :-D

---

### Post by Eversmann on 2006-10-05
USP is really great. Thanks for this great work, i'm looking forward for USP2 :-D

---

### Post by Malac on 2006-10-06
USPconfig Application and all my plugins will now be at this thread.

[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

Please don't post on that thread.
If you have a plugin that you want added to the list send it as attachment to: Malac[at]tiscali[dot]co[dot]uk
         [at]=@
         [dot]=.
with "USP plugin" as the subject line.

Thanks.

---

### Post by kwalo on 2006-10-06
What is the reason of makeing usp 2? Is something wrong with usp?

---

### Post by chanders on 2006-10-06
> **kwalo said:**
> What is the reason of makeing usp 2? Is something wrong with usp?

LOL, no. USP2 is actually a complete rewrite of USP. I had no idea USP would have been so popular, so while I was coding it, I used less than efficient methods to achieve the look and feel. Now because of inputs from all the users, I am now ironing out the bugs not to mention make a product that is a little more refined, both technically and graphically.

This also makes it easier for users to write plugins and help in the bug fixing. USP2 also allow users to create their own mini menus than can look totally different from USP. That way if a user is using a screen resolution that is small for example they can load a mini version of the menu. 

Also, the idea for USP came after using SuSE's Slab menu. So with USP2 I am including a USPSlab plugin which effectively gives users the Slab look with a lot more configurability than they could ever get without having to compile everything like you had to do with Slab. USPSlab would only be possible by adding to the existing USP API, hence USP2.

---

### Post by kwalo on 2006-10-07
So, when usp 2 becomes stable, can you call it usp version 1.0 ? I know the name doesn't matter, but, if you abandon a project, that din't make to 1.0 release and start another project and call it 'beta software' that wouldn't make it more popular.

---

### Post by chanders on 2006-10-07
It will still be called USP and probably be bumped up to Ver 1.0 :-D  USP2 was more of a codeword for the rewritten version..

---

### Post by DBO on 2006-10-07
but but... but we want to try it now...  =)

---

### Post by Mr. Picklesworth on 2006-10-09
Sorry, I can't read through 59 pages of thread...

Is there a package repository for this (or is this on a package repository) so I could hopefully get updates as soon as they come available?
USP is a wonderful piece of software and I didn't realize how many new features have been added since the first time I installed it :)

---

### Post by ashrack on 2006-10-09
I believe repo doesn't exist yet! We would need a vollunter that would host the repo

---

### Post by Malac on 2006-10-17
Uploaded a new version of USPconfig to here.
This was a bug fix for the plugins list in USPconfig re-populating on certain setting changes. It should not have affected USP itself at all.

[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by Gargamella on 2006-10-17
i liiiiiiiiiiiiiiiiiiike it very good,i think i will go on edgy...do you if it will work on edgy, do you tested it on the beta?

however..nice job ;D

---

### Post by Malac on 2006-10-17
> **Gargamella said:**
> i liiiiiiiiiiiiiiiiiiike it very good,i think i will go on edgy...do you if it will work on edgy, do you tested it on the beta?

however..nice job ;D
I'm glad you liiiiiiiiiiiiiiiiiiiiike it. :)
I haven't tested it on edgy myself yet but I see no reason why it wouldn't work okay.
A few of the other USP users on this forum have used it on edgy already so it would seem to be okay.

Hope this helps.

---

### Post by ~LoKe on 2006-10-17
I'm running USP on Edgy and it works just fine.  Only problem I found is that the menu doesn't follow with my theme, but perhaps I'm missing a setting.

---

### Post by Hobbes on 2006-10-26
not to sound whiney or anything, but any updates on getting closer to USP2? I check up on forums every once in a while and I'm just a little nervous by the lack of posts/activity.  

Basically, are there still plans for this to come out in the near future?

That is all. Thanks for the time and effort you guys put into this project, making the Ubuntu world a better place.

---

### Post by Uncle Spellbinder on 2006-10-26
@ Hobbes

From the *_Your last screenshot before USP 2..._* thread:

20, October - 2006
> **chanders said:**
> ...I have lots of real life stuff to do, so USP has to be done in my spare time. I changed jobs and have exams for my masters in December. But I still try my best. I can release it but what is the point if there will still be a lot of little fixes that people want and cant be fixed until later?

Sorry again guys, but I haven't given up on you all....

---

### Post by zman3 on 2006-11-01
is there any plans to let the user use a png of any size for the "start button" so i could make one that say looked like the xp green button or some crap?

---

### Post by DBO on 2006-11-01
USP2 is supposed to include that feature... but chanders is rather busy right now, so release date on that is undetermined.

---

### Post by Ademan on 2006-11-17
Dunno if anyone mentioned/asked this, but why isn't this in the repositories?

---

### Post by anarky on 2006-11-18
beautiful! need a bettter image host though ;)

---

### Post by chanders on 2006-11-19
Actually, an earlier version is in Quinn's repository (see wiki.beryl-project.org for repository details)

When USP2 comes out I willtry to get it its own repository...

And yeah the images was caused by the DIGG! effect ;-)

---

### Post by delfick on 2006-11-20
> **chanders said:**
> When USP2 comes out

............

what can we expect from this release ??  :D

---

### Post by BLTicklemonster on 2006-11-27
This is really smooth. How can I get it to load automagically; can I add launchers to it (unreal tournament and such), and control center does not work for me. 

Here's what I get when I launch it from terminal:

```
ticklemonster@MSHOME:~$ usp run-in-window
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Directory created
Directory created
Directory created
Empty places.list: Populating
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-home.desktop
Place added - /home/ticklemonster/.usp/places/-home-ticklemonster-Desktop.desktop
Place added - /home/ticklemonster/.usp/places/nautilus-computer.desktop
Place added - /home/ticklemonster/.usp/places/network-scheme.desktop

(usp:7064): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
ticklemonster@MSHOME:~$ 
```

---

### Post by gborzi on 2006-12-05
I don't know if this bug has been pointed out before, the thread is so long to check. Today I installed a package I made myself from source for a program that find italian zipcodes. After installing usp didn't started. Running it with *usp run-in-window* it gives the following error messages:
> gborzi@evo610:~$ usp run-in-window
Warning! - Icon for item not found!
Traceback (most recent call last):
  File "/usr/bin/usp", line 1769, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1749, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1565, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 145, in __init__
    self.Todos()
  File "/usr/bin/usp", line 829, in Todos
    PlaceIcon = self.get_proper_icon(datalist[i][5:],icon_size)
  File "/usr/bin/usp", line 757, in get_proper_icon
    Image1.set_from_pixbuf(gtk.gdk.pixbuf_new_from_file(icon_description).scale_simple(width,height,gtk.gdk.INTERP_BILINEAR))
gobject.GError: Failed to load image '/usr/share/pixmaps/trovacap.xpm': Invalid XBM file
i.e. an invalid pixmap can crash usp. I think that in such cases usp should give a warning and use the default icon (that for programs missing their own icon).

---

### Post by Choxo on 2006-12-13
I Didn't found an answer using the forum search,
and I'm to lazy to read all the 61 pages, so I ask my question hoping it isn't answered yet:

Is it possible to open the USP-menu on hitting the windows key?
I 've been trying some things in the gconf-editor > nautilus > shortcuts, But running usp doesn't open the menu.

thanks anyway!

---

### Post by Malac on 2006-12-13
> **Choxo said:**
> I Didn't found an answer using the forum search,
and I'm to lazy to read all the 61 pages, so I ask my question hoping it isn't answered yet:

Is it possible to open the USP-menu on hitting the windows key?
I 've been trying some things in the gconf-editor > nautilus > shortcuts, But running usp doesn't open the menu.

thanks anyway!
Sorry for the "non-answer" but this has been requested before and is hopefully on the list of things to do once it can be figured out how to do it. :)
At the moment I think it is someway down the list of todo's.

---

### Post by Permafrost91 on 2006-12-14
where can I find the latest version of USP to try out?

---

### Post by Malac on 2006-12-14
> **Permafrost91 said:**
> where can I find the latest version of USP to try out?
[http://www.ubuntuforums.org/showthread.php?t=229014](http://www.ubuntuforums.org/showthread.php?t=229014)
Posts 3 and 4

---

### Post by M7S on 2006-12-14
> **Malac said:**
> Sorry for the "non-answer" but this has been requested before and is hopefully on the list of things to do once it can be figured out how to do it. :)
At the moment I think it is someway down the list of todo's.
Is it even posible to do it without patching gnome? At least to get alt+F1 to open slab in Ubuntu you had to patch gnome and recompile gnome.

---

### Post by Malac on 2006-12-14
> **M7S said:**
> Is it even posible to do it without patching gnome? At least to get alt+F1 to open slab in Ubuntu you had to patch gnome and recompile gnome.
It would to use the Alt+F1 but it may be possible but needs to be looked at.

---

### Post by Petro on 2006-12-15
waiting for usp2 ^^ i just need that "bigger" image support so i can replace old menu totally :>
really cool btw ;)

---

### Post by chanders on 2006-12-15
M7S is right. We wont be able to assign a hotkey unless GNOME is patched so it wont be included in USP2 (unless someone writes the patch ;-)) sorry...

---

### Post by hoagie on 2006-12-15
The System managment in the USP doesn't look well. It's icons look weird, any ideas?

---

### Post by Malac on 2006-12-15
> **hoagie said:**
> The System managment in the USP doesn't look well. It's icons look weird, any ideas?
Screenshot?

---

### Post by hoagie on 2006-12-16
[[IMG]http://img522.imageshack.us/img522/305/2269zo8.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=2269zo8.jpg)

---

### Post by delfick on 2006-12-16
> **hoagie said:**
> [[IMG]http://img522.imageshack.us/img522/305/2269zo8.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=2269zo8.jpg)

go into gconf >> apps >> usp >> and tick the option that says "compact system management"

and then it will be as icons on the side bar....much better in my opinion

(can't wait till we're able to add user-defined shortcuts to that bar :D)

---

### Post by hoagie on 2006-12-16
Yeah but still the icons don't look nice.

---

### Post by chanders on 2006-12-16
This is already fixed in USP2 ;-)  When it comes out you'll have no problems...

---

### Post by Permafrost91 on 2006-12-16
how come I can't slide USP to anywhere on the panel? It behaves as if "Lock to Panel" is enabled although it is not

---

### Post by chanders on 2006-12-16
> **Permafrost91 said:**
> how come I can't slide USP to anywhere on the panel? It behaves as if "Lock to Panel" is enabled although it is not

I haven't been able to figure out how to get this done in python as yet. Any gurus out there? Also, how do I add an Item to the right click menu on applets?

Thanks!

---

### Post by Malac on 2006-12-16
> **Permafrost91 said:**
> how come I can't slide USP to anywhere on the panel? It behaves as if "Lock to Panel" is enabled although it is not
Strange this works for me with metacity and beryl, I can slide it about anywhere I like.
Have you tried using one of the <Alt>, <Shift> or <Ctrl> keys and making sure the other things on the panel aren't locked so stopping usp from taking up that space.

---

### Post by delfick on 2006-12-16
i can move mine

using gnome and beryl...

---

### Post by Malac on 2006-12-16
> **chanders said:**
> Also, how do I add an Item to the right click menu on applets?

Thanks!
Hi chanders,
This code adds a "Preferences" entry to the right-click menu as well as the "About" entry.
The function for "Prefs" here is set to None at the mo but can be any function or to launch USPconfig or something. :)
Mine is set up to run USPconfig.
```
 [SIZE=1]       self.propxml="""
               <popup name="button3">
                <menuitem name="Item 1" verb="Prefs" label="_Preferences..." pixtype="stock" pixname="gtk-properties"/>
                   <menuitem name="Item 1" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
                 </popup>
                 """
        self.verbs = [ ( "Prefs", **None** ),( "About", self.showAboutDialog) ][/SIZE]

```

---

### Post by Permafrost91 on 2006-12-16
Malac, I can move everything else on my panel, like I said, USP is not "Locked to Panel" ... I have even created a new panel with only USP on it just to try it - no luck. Alt/Ctrl/Shift/etc doesn't help either.

By the way, what language is USP written in?

---

### Post by Malac on 2006-12-16
> **Permafrost91 said:**
> By the way, what language is USP written in?
USP is written in Python.
If you right click on USP and choose "Move" from the menu you should get a changed cursor and it should be move-able.
At the moment USP can't be "grabbed" with the mouse and dragged.

Hope this helps.

---

### Post by chanders on 2006-12-16
This will off course be the default for USP2 ;) 
 
> **Malac said:**
> Hi chanders,
This code adds a "Preferences" entry to the right-click menu as well as the "About" entry.
The function for "Prefs" here is set to None at the mo but can be any function or to launch USPconfig or something. :)
Mine is set up to run USPconfig.
```
 [SIZE=1]      self.propxml="""[/SIZE]
[SIZE=1]              <popup name="button3">[/SIZE]
[SIZE=1]               <menuitem name="Item 1" verb="Prefs" label="_Preferences..." pixtype="stock" pixname="gtk-properties"/>[/SIZE]
[SIZE=1]                  <menuitem name="Item 1" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>[/SIZE]
[SIZE=1]                </popup>[/SIZE]
[SIZE=1]                """[/SIZE]
[SIZE=1]       self.verbs = [ ( "Prefs", **None** ),( "About", self.showAboutDialog) ][/SIZE]

```

---

### Post by Permafrost91 on 2006-12-16
> **Malac said:**
> USP is written in Python.
If you right click on USP and choose "Move" from the menu you should get a changed cursor and it should be move-able.
At the moment USP can't be "grabbed" with the mouse and dragged.

Hope this helps.

thanks, that did the trick ...

---

### Post by oyvindaa on 2006-12-23
Just stumbled upon this one this morning. It works great here, well done chanders :)

---

### Post by Permafrost91 on 2006-12-29
This is great work! I've been using it for a few weeks now and really love it! Here are some things I'd like to see in future versions:

(1) the app finder (the search box on the bottom of the application menu) should be able to run a command like Alt-F2 does in addiition to searching for applications in the menu

(2) a file system browser like KDE has in its menu where each folder is a submenu with the files of the folder displayed as menu items (I'd actually like to see this in Gnome, period)

(3) recently used files

Lemme know what y'all think ... and do keep up the good work!

---

### Post by chanders on 2006-12-29
> **Permafrost91 said:**
> This is great work! I've been using it for a few weeks now and really love it! Here are some things I'd like to see in future versions:

(1) the app finder (the search box on the bottom of the application menu) should be able to run a command like Alt-F2 does in addiition to searching for applications in the menu

(2) a file system browser like KDE has in its menu where each folder is a submenu with the files of the folder displayed as menu items (I'd actually like to see this in Gnome, period)

(3) recently used files

Lemme know what y'all think ... and do keep up the good work!

See here [http://www.ubuntuforums.org/showthread.php?t=327001](http://www.ubuntuforums.org/showthread.php?t=327001) for starters ;)

---

### Post by neoflight on 2007-01-20
> * Depending on your theme, the colours may look off (not my fault!) Open gconf-editor and check 'Use custom colors' and enter the colour you would like to use. the default is a nice gray

i dont have a place to check it...where is it?](*,)

the colors i am getting by default is give in the screenshot....using version 0.41...help!!!

---

### Post by Permafrost91 on 2007-01-20
the setting is under apps->usp in gconf-editor

---

### Post by delfick on 2007-01-20
anyone seen this gimmie menu thingo [http://www.beatniksoftware.com/blog/?p=53](http://www.beatniksoftware.com/blog/?p=53) ?? (of course you have :D)

what do people (you) think of that ??

(i still prefer usp :D)

---

### Post by chanders on 2007-01-20
I think it's a nice piece of software. It's a bit different from USP so it's not really a preference between the two. I think  he is also planning to add plugins. It would be interesting to see how it turns out..

Maybe one day there might be an app that would give all the functionality of both USP and Gimmie..

---

### Post by delfick on 2007-01-20
> **chanders said:**
> It's a bit different from USP so it's not really a preference between the two. 

true :D

> Maybe one day there might be an app that would give all the functionality of both USP and Gimmie..

lol.......maybe......:D

---

### Post by Papillonrus on 2007-01-24
Can you tell me how to resize minimized and Maximized windows to fit in a 12.1 TFT Flat Panel?

    I have a Dell Latitude LS P3 500, 256MB, 20 GB, with external media bay and installed Ubuntu 6.10.  The screen size is to small for the default window sizes.  The laptop is currently configured to display 800x600 @60hz @16bit depth.  I have already edited the xorg.conf to display 1024x768 and it will not give me to change the resolution to 1024x768.  So perhaps editing the window sizes to fit 800x600 with a 12.1 in screen might be the answer.  The screen is a Samsung LTN121S6-T01
While the specs that I have found state that native resolution is 800x600 svga.  I have been able to use 1024x768 in win98SE, winXP, Mandrake 9.2 and Xandros 2.0.  I am having problems with the apply, change, close, forward and back  buttons not appearing due to size of minimized window. 
I need help with either solution.  Screen resolution or window sizes.  Thanks, Darrell

---

### Post by jourdanritchey on 2007-01-25
This USP looks like a good replacement for those cascading gnome menus, but before I install it... is there a repository somewhere with USP in it?

Brand new to Ubuntu here!

Cheers

---

### Post by Permafrost91 on 2007-01-25
you can find the latest version here:
[http://www.ubuntuforums.org/showthread.php?t=229014](http://www.ubuntuforums.org/showthread.php?t=229014)

download the .deb file and install it

---

### Post by domino on 2007-01-28
Gimmie constantly crashes on my beryl install and it still lacks the functionality compared to USP.

Can someone tell me exactly what to do with USP and the latest Beryl SVN? USP always wants to open under all windows and sometimes it doesn't want to close until you click the icon again. It's driving me $%&% nuts! How do I give USP priority focus?

---

### Post by Permafrost91 on 2007-01-29
open gconf-editor apps->usp and make sure pin_menu is unchecked (if it's checked, the menu will stay open)

---

### Post by chanders on 2007-01-29
Also you **have** to set focus stealing in Beryl to 'none' to have it stay on top.

---

### Post by Choad on 2007-02-14
ok, newbie question: i can run it in a window from the cli, but how do i add it to the panel? it cant see it when i right click> add to panel.

---

### Post by chanders on 2007-02-14
You may need to logout of GNOME and then log back in or in a terminal type 
> 
killall gnome-panel

---

### Post by Choad on 2007-02-14
> **chanders said:**
> You may need to logout of GNOME and then log back in or in a terminal type
thanks, and thanks for usp. its wicked

---

### Post by Omnios on 2007-02-15
Hi I have been playing around with ideas ob how to change the Gnome panel. Anyways I was thinking of making a tweek where the menu is located on a left side bar instead of launching  from the top panel. This has a few slight advantages in that you do not have to travel to the top panel to launch it and just have to go to the left side of the screen which you already have to do to get into the menus. 

 My idea goes a bit beyond that though the above might be highly desirable sort of a Ubuntu solution to the mac bar. I also currently use a left panel as an app launcher with big icons. 

 Another thing I was playing with is a more interactive left menu pannel with Ubuntu updater like pop ups with with menu info poping up. Your menu looks really nie and is kind of similar to what I had invisioned. 

 The number one reason for doing this is it will be 100% linux and hopefully becomes a Ubuntu feature in the Future

---

### Post by Mateo on 2007-02-15
I really like USP.  I have looked in this thread a bit but haven't seen this.... what happens when an icon of one of your launchers doesn't show up?  what's the deal with that, and how to fix?

---

### Post by Mateo on 2007-02-16
never mind, USP doesn't like GIFs while 'main menu' doesn't care.  converting to PNG did the trick.

---

### Post by Mateo on 2007-02-16
programs that are supposed to run in the terminal are launched but don't appear, if that makes sense.  they run behind the system... don't know how to explain.  seems to be a major bug.  hope you understand.  tried with hellanzb, works fine wih main menu but with USP it runs without the actual terminal window appearing.

---

### Post by chanders on 2007-02-16
I will look into this...

---

### Post by H.E. Pennypacker on 2007-02-25
How do we know where the latest versions are kept?  I am totally confused here, because it seems no single thread controls all versions.  In one thread, the last update was in August 2006, which can't be true.  

It would be very handy if USP had a website where you could check out its information, and also know what version is currently in use.  This forum is making it only more confusing.

---

### Post by Permafrost91 on 2007-02-25
[http://www.ubuntuforums.org/showthread.php?t=229014](http://www.ubuntuforums.org/showthread.php?t=229014)

the latest release was 0.41 in August 2006 as far as I know ...

---

### Post by PsyberOneZero on 2007-02-25
0.41 was the last release in USP1

1.92 alpha will be released soon-ish as USP2 and can be downloaded from SVN
here is a really good howto on installing it
[Guide to USP2 SVN]("http://www.ubuntuforums.org/showthread.php?t=365147l")

and USP3 is currently in development, you can see a few screenshots / screencasts / mock-ups in this thread
[Vertical USP]("http://www.ubuntuforums.org/showthread.php?t=354872")

I agree that the thread is a little cluttered. If there is anyone who can donate server space for a trac/SVN page that would be great.

---

### Post by H.E. Pennypacker on 2007-02-25
> **PsyberOneZero said:**
> 

I agree that the thread is a little cluttered. If there is anyone who can donate server space for a trac/SVN page that would be

I am willing to donate space, although that means I will have to upgrade my current plan, which I was already intending on doing anyway.  I will need to know how much space is needed, and what kind of a setup is planned.  I also need to know what kind of bandwidth is needed.

---

### Post by PsyberOneZero on 2007-02-25
Here is the information on what you need to set up a track server.
[Trac]("http://trac.edgewall.org/")

Size requirements would be the size of the needed packages + the SVN repo.

I really don't know what the bandwidth is like, you might want to talk to [zachtib]("http://www.ubuntuforums.org/member.php?u=3818"), he is the lead developer of Deluge and has a Trac page setup.

Now this is kind of behind chanders back, I don't know if he has any plans for a site, hopefully he'll see this post.

---

### Post by H.E. Pennypacker on 2007-02-25
> **PsyberOneZero said:**
> Here is the information on what you need to set up a track server.
[Trac]("http://trac.edgewall.org/")

Size requirements would be the size of the needed packages + the SVN repo.

I really don't know what the bandwidth is like, you might want to talk to [zachtib]("http://www.ubuntuforums.org/member.php?u=3818"), he is the lead developer of Deluge and has a Trac page setup.

Now this is kind of behind chanders back, I don't know if he has any plans for a site, hopefully he'll see this post.

I am familiar with Trac (installing it shouldn't be difficult - using it is very easy), and I am sure the space it takes up will not be an issue, but bandwidth likely will be.  As far as Deluge goes, the bandwidth really depends on the popularity of a website.  I am pretty sure USP is more popular than Deluge, and it would attract far more hits.

---

### Post by delfick on 2007-03-07
is it possible to use the usp whilst not touching any files outside the home area ??

that way i'd be able to use the usp on the linux computers at my uni :D

(the engineering programming department uses linux (they use fedora 6 (i hate fedora :( ))

:D

---

### Post by chanders on 2007-03-07
It shouldnt be to difficult to make it portable. You will need to make sure you have the right version of python installed tho...

I can send you some steps to make your own portable version if you want the challenge ;-)

---

### Post by delfick on 2007-03-07
> **chanders said:**
> I can send you some steps to make your own portable version if you want the challenge ;-)

i'd like that very much :D

thnx :D

but for now, i go to sleep :D :p
(11.30pm over here :D and uni means i get up early...)

---

### Post by delfick on 2007-03-12
> **chanders said:**
> I can send you some steps to make your own portable version if you want the challenge ;-)

excuse my persistence (and excuse me for persisting to excuse my persistence :p) ......what happened to that ?? :D

(no rush...just curious :D)

---

### Post by Fajer on 2007-03-30
Hi,
is there USP still being developed and active?

---

### Post by Malac on 2007-03-30
> **Fajer said:**
> Hi,
is there USP still being developed and active?
Yes it is. We are all working very hard to get it to release state. :D

Seriously, chanders, myself and all, are working whenever we can on USP, unfortunately other commitments sometimes get in the way. We hope to have a beta release very soon.

---

### Post by Fajer on 2007-03-31
I'm asking, because I saw it on screens and it looks great. And I saw that last version 0.41 is from last year.

I tried to install 0.41 on Feisty and it broke my apt :(
Now I can't even upgrade my system and install anything :(

---

### Post by Malac on 2007-03-31
> **Fajer said:**
> I'm asking, because I saw it on screens and it looks great. And I saw that last version 0.41 is from last year.

I tried to install 0.41 on Feisty and it broke my apt :(
Now I can't even upgrade my system and install anything :(

Sorry to hear it broke your Feisty install. Boot into recovery mode and then run ```
aptitude remove usp
``` or ```
aptitude purge usp
```See if that works.

Here is a link to the 1.9x (Alpha):
[http://www.ubuntuforums.org/showthread.php?t=331364](http://www.ubuntuforums.org/showthread.php?t=331364)
Although this still has some bugs in it.

Or the Latest copy in SVN.
[http://www.ubuntuforums.org/showthread.php?t=231574](http://www.ubuntuforums.org/showthread.php?t=231574)

There is a Wiki which has explanations on how to install and configure the SVN version here:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps.
If not let me know.

---

### Post by greymongrey on 2007-05-04
I'm running the 1.92 Alpha on Feisty and I must say, it's an excellent piece of work. It beats the heck out of any other start menu I've worked with.

---

### Post by Fajer on 2007-05-04
I had problems with instalation usp, so I'm using verion of usp taken from LinuxMint (mintMenu). 
You are doing great job people :)

---

### Post by Maggot on 2007-05-17
Installation and operation went smoothly here on Fiesty.

Nicely done :)

---

### Post by justin13 on 2007-06-01
very wow!

---

### Post by NeoLithium on 2007-06-06
Ok, so I just happened to find USP after browsing through the June Desktop Screenshots.  So I figured I'd give it a try. WOW.  This is absolutely beautiful and exactly what I was looking for!

The SVN install went perfect, looks absolutely clean and stunning.  Dev Team: Thanks for one GREAT app!

---

### Post by Bill Cosby on 2007-06-16
Just wanted to tell, that I, too, just discovered this excelent piece of code and wanted to express my greatfulness to the developers, please keep going :D

I bow to you.
Bill

---

### Post by LordMau on 2007-08-04
> **Fajer said:**
> I had problems with instalation usp, so I'm using verion of usp taken from LinuxMint (mintMenu). 
You are doing great job people :)

How about a how-to for mintmenu over ubuntu? Thanks!

---

### Post by JoshA on 2007-08-06
Well I installed the SVN version of the panel and I do really like it but i have two problems:

1. There is no panel for "Places"
2. The "Control Center" button doesnt work

---

### Post by smartboyathome on 2007-08-06
The "Control Center" button doesn't work with the latest stable version of USP either. I am going to guess there is no command programmed into the button for it.

---

### Post by Malac on 2007-08-06
> **JoshA said:**
> 1. There is no panel for "Places"
Have you added it to the plugins list?
> **smartboyathome said:**
> The "Control Center" button doesn't work with the latest stable version of USP either. I am going to guess there is no command programmed into the button for it.
This is set to gcontrol initially which isn't installed by default. This can be changed using right click on main button and choose "Preferences"

---

### Post by JoshA on 2007-08-06
> **Malac said:**
> Have you added it to the plugins list?

I tried to but everytime I refresh it goes away.:confused::confused:

> **Malac said:**
> This is set to gcontrol initially which isn't installed by default. This can be changed using right click on main button and choose "Preferences"

Oh I fixed this.  I changed gcontrol to gnome-control-center.  Thanks :)

---

### Post by Malac on 2007-08-07
> **JoshA said:**
> I tried to but everytime I refresh it goes away.:confused::confused:
You need to click [Save] to have the new list used [Refresh] is to reset the list back to the original order if you have made a mistake or similar. Perhaps I ought to change it from "Refresh" to "Reset".

---

### Post by JoshA on 2007-08-07
> **Malac said:**
> You need to click [Save] to have the new list used [Refresh] is to reset the list back to the original order if you have made a mistake or similar. Perhaps I ought to change it from "Refresh" to "Reset".

Hah I feel like an idiot.  Thanks :popcorn:

---

### Post by Malac on 2007-08-09
> **JoshA said:**
> Hah I feel like an idiot.  Thanks :popcorn:
Not at all, this is what Beta testing is all about.
If that button said "Reset" instead of "Refresh" you may have not had the problem. I think I will change it and add some tooltips too. Thanks JoshA :)

---

### Post by Mayfairy on 2007-08-12
This USP is awesome. Just what I was looking for (actually a bit more than what I had asked for but extra never hurts) to pimp my Ubuntu system. 
Thanks for making this system possible and available to us all. Great work!

---

### Post by dasbooter on 2007-08-19
> **Malac said:**
> Have you added it to the plugins list?

This is set to gcontrol initially which isn't installed by default. This can be changed using right click on main button and choose "Preferences"

Sorry what do you mean by the main button can you be more descriptive. Right clicking anywhere in usps menu gets me nowhere. Right clicking on the ubuntu system button that is placed when once selects ubuntu systme panel from add to panel doesnt do anything either. I was also curious about the weather plugin. I installed the latest stable not from svn should I be seeing stuff llke weather in my home/user/.usp directory, there is nothing in there now. Cool app is this going into the next ubuntu release because it definitely should :)

EDIT: I made all of these changes with gconf-editor changing gcontrol to gnome-control-center or whatever was the command to launch control center this had to been done in two places. Then I added the plugins in the plugins string according to their names listed on the page where I dl'd the package and all seems to be working. I dont know if that was supposed to be how it was done but that is how I did it. It has been along time since I had to use gconf-editor. The svn version looks nice with transparency and a little user gif. Hope it is ready for stable soon.

---

### Post by Malac on 2007-08-19
@[dasbooter]("http://ubuntuforums.org/member.php?u=309063")
You should be able to right-click on the button that is added to the panel when you choose Ubuntu System Panel. This should bring up a menu that will definitely have an "About" option on it if it has no "Preferences" option then it maybe it wasn't enabled on early stables. If you let me know what version number the about dialog gives you I can probably help you.
Try running ```
uspconfig
``` in a terminal if it is there it should bring up the configuration window.

You should consider using the SVN as a lot of improvements and features have been added since the last .deb release, not to mention it is actually more stable now than the last */stable/* release. :)

Full instructions on how to install the SVN version are at the wiki:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
and choose "Installation"

Hope this helps.

---

### Post by r_l on 2007-08-23
It is a great menu - but I am so used to accessing my menu using super-L.  Is this feature implemented yet?  I have seen a couple of posts in this thread mentioning about this back in last Aug, but I don't know if I can do it with this new version... thanks.

---

### Post by Malac on 2007-08-25
> **r_l said:**
> It is a great menu - but I am so used to accessing my menu using super-L.  Is this feature implemented yet?  I have seen a couple of posts in this thread mentioning about this back in last Aug, but I don't know if I can do it with this new version... thanks.
Yes this is implemented in the SVN version.
It is set to "<Ctrl><Alt>U" by default but this can be changed in the "Preferences" to what ever you want.
Depending on keyboard layout this can be "Meta_L" or "Super_L".

Hope this helps.

---

### Post by cawill on 2007-08-25
Excellent menu, but how can you change the icons at the far left side to text and how can you reduce the gap the menu has from the panel?

---

### Post by r_l on 2007-08-27
> **Malac said:**
> Yes this is implemented in the SVN version.
It is set to "<Ctrl><Alt>U" by default but this can be changed in the "Preferences" to what ever you want.
Depending on keyboard layout this can be "Meta_L" or "Super_L".

Hope this helps.

Wow, the screenshot looks good!  Thanks.  I will try to install the SVN version, then.

---

### Post by Malac on 2007-08-28
> **r_l said:**
> Wow, the screenshot looks good!  Thanks.  I will try to install the SVN version, then.
Here's some of my current Edgy menu.

---

### Post by delfick on 2007-08-28
> **Malac said:**
> Here's some of my current Edgy menu.

I'm surprised you not using some beta version of usp3 ...

or is chanders the only one with that ?? :D

---

### Post by Malac on 2007-08-28
> **delfick said:**
> I'm surprised you not using some beta version of usp3 ...

or is chanders the only one with that ?? :D
The USP3 I have is still nowhere near ready as a usable menu yet. :(
And I still can't seem to dedicate enough time to the project as I'd like to do.

---

### Post by delfick on 2007-08-30
> **Malac said:**
> The USP3 I have is still nowhere near ready as a usable menu yet. :(
And I still can't seem to dedicate enough time to the project as I'd like to do.

damn......

oh well, it will be one day :D

---

### Post by voided3 on 2007-09-06
Where can I download the latest version of USP? I have 0.41

---

### Post by Phil-Towers on 2007-09-06
I am also interested in discharging the it finishes version of the USP, I would also like to know if there is translation to Spanish.  
  
Thank you.

---

### Post by Malac on 2007-09-06
@voided3 and Phil-Towers

Latest recommended version is the SVN beta which can be got by following the instructions here.
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list) 
Under "_Installation_".

Hope this helps.

---

### Post by Phil-Towers on 2007-09-06
Thank you for their information Malac.  
  
Greetings from Mexico
:)

---

### Post by Geekkit on 2007-09-06
It's nice but .... is there a chance you might make a native (C) version of this? I hardly see the 10 MB hit being well worth a menu bar. GTK+ in native C would only cost you about a MB or so or even less.

---

### Post by Mayfairy on 2007-09-08
I'm trying to get rid of gnome-panel for good. Using Screenlets to replace parts of gnome-panel, but I'd still need USP and Notification Area so I don't have to use autohide function for gnome-panel. 
So I'd like to know if it's possible to create a launcher to fire up USP. 'usp -open-iin-window' (or whatever the command was) isn't good enough. :|

---

### Post by pixeltarian on 2007-09-22
is there any way to get submenus to show up in the application list? the applications I put in a submenu aren't even listed in "all" 

thanks, 

- pix

---

### Post by DeadSuperHero on 2007-09-23
Just installed the latest version (or at least, the latest one I'm aware of, 0.41)
I've only got a few gripes with it.
1. When I install new programs, they won't show up in it. However, I can remove and re-add the applet, and there it is.
2. When I start up Banshee through it, it claims that dbus is not working in Banshee. But, when I run it through the GNOME menu bar, it works fine.
3. Control panel does not come up when I click it...I get nothing at all.
4. Various Bonobo errors when I try to run GNOME configuration tools, mainly the theme manager.

These problems only happen with the Ubuntu System panel, so I know that everything works fine, it's just a few bugs.
I really love it, though. I think it looks awesome, and can't wait to see the finished product.
Erm...Also, where's the setup/configuration tool for this? I can't find it anywhere!

---

### Post by Malac on 2007-09-23
> **pixeltarian said:**
> is there any way to get submenus to show up in the application list? the applications I put in a submenu aren't even listed in "all" 

thanks, 

- pix
This is being looked into at the moment.

> **Mr. Psychopath said:**
> Just installed the latest version (or at least, the latest one I'm aware of, 0.41)
I've only got a few gripes with it.
1. When I install new programs, they won't show up in it. However, I can remove and re-add the applet, and there it is.
2. When I start up Banshee through it, it claims that dbus is not working in Banshee. But, when I run it through the GNOME menu bar, it works fine.
3. Control panel does not come up when I click it...I get nothing at all.
4. Various Bonobo errors when I try to run GNOME configuration tools, mainly the theme manager.

These problems only happen with the Ubuntu System panel, so I know that everything works fine, it's just a few bugs.
I really love it, though. I think it looks awesome, and can't wait to see the finished product.
Erm...Also, where's the setup/configuration tool for this? I can't find it anywhere!
The 0.41 is actually quite out of date now, the latest version is available through the SVN repo.
Go to this link:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
Choose "Installation" for instructions for downloading/installing.

If you want preferences/config  for usp 0.41 only, do a search on this forum for uspconfig or use gconf-editor /apps/usp/ key.

Hope this helps.

---

### Post by llamakc on 2007-09-30
Thanks Malac. The instructions for checking out the recent build from svn work perfectly.

---

### Post by IceReaver75 on 2007-09-30
> **Malac said:**
> This is being looked into at the moment.


The 0.41 is actually quite out of date now, the latest version is available through the SVN repo.
Go to this link:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
Choose "Installation" for instructions for downloading/installing.

If you want preferences/config  for usp 0.41 only, do a search on this forum for uspconfig or use gconf-editor /apps/usp/ key.

Hope this helps.

I followed the directions from the webpage here and now want to un-install it and it won't let me.  

I cd to the folder and type ./usp_update uninstall complete and it keeps telling me there is now such file for usp_update 
so how do i go about un-installing this?

Nevermind I figured it out.  I had to cd to the exact sub-folder it was in instead of just the SVN folder.

---

### Post by IceReaver75 on 2007-10-01
How do I install the extra plug-ins.  I really don't understand the directions on how to do it.  I tried to put them in the same folder as the standard plug-ins but everytime I try to start one it says the is no module for the plug-in.  If i download the deb pakages it just wont install cause it says dependicies not meet: USP:   like it isnt even installed. So if someone can tell me how to do this it would be greatly appreciated.  Thank you

---

### Post by Malac on 2007-10-01
> **IceReaver75 said:**
> How do I install the extra plug-ins.  I really don't understand the directions on how to do it.  I tried to put them in the same folder as the standard plug-ins but every time I try to start one it says the is no module for the plug-in.  If i download the deb packages it just wont install cause it says dependencies not meet: USP:   like it isn't even installed. So if someone can tell me how to do this it would be greatly appreciated.  Thank you
Hi,
Go to this page :
[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)
and download the extra plugins from there.
The .deb file on the forum is for USP 0.41 and is not compatible with USP 2.00-beta.

Extract the files in the downloaded .tar.gz archive into:
/home/[COLOR=SeaGreen]<your-username-here>[/COLOR]/.usp/plugins
Then just add them to the plugins list.

I'm not brilliant with command line tar so you may want to do this through the graphic Archive Manager but this should work from where you downloaded the file to.```
tar xvpfz "USP2 Add-On Plugins.tar.gz" -C /home/[COLOR=SeaGreen]<your-username-here>[/COLOR]/.usp/plugins
```If the directory doesn't exist then```
mkdir -p /home/[COLOR=SeaGreen]<your-username-here>[/COLOR]/.usp/plugins
```Then run previous command.

Hope this helps.

---

### Post by IceReaver75 on 2007-10-01
> **Malac said:**
> Hi,
Go to this page :
[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)
and download the extra plugins from there.
The .deb file on the forum is for USP 0.41 and is not compatible with USP 2.00-beta.

Extract the files in the downloaded .tar.gz archive into:
/home/[COLOR=SeaGreen]<your-username-here>[/COLOR]/.usp/plugins
Then just add them to the plugins list.

I'm not brilliant with command line tar so you may want to do this through the graphic Archive Manager but this should work from where you downloaded the file to.```
tar xvpfz "USP2 Add-On Plugins.tar.gz" -C /home/[COLOR=SeaGreen]<your-username-here>[/COLOR]/.usp/plugins
```If the directory doesn't exist then```
mkdir -p /home/[COLOR=SeaGreen]<your-username-here>[/COLOR]/.usp/plugins
```Then run previous command.

Hope this helps.

Didn't work.  I didn't have the directory so I did the mkdir first then did tar command next and it said no such file or directory.

Alright I finally got it to work.  I wouldn't work at all until I un-hid the .usp folder in my home directory for some reason.  Thank you very much for all the help.  Everything is installed now

---

### Post by pt123 on 2007-10-13
Will USP be included in Gutsy

---

### Post by delfick on 2007-10-13
> **pt123 said:**
> Will USP be included in Gutsy

seeing as gutsy is released in a few days, I doubt it ......

(and the issues with the panel when compiz is running in gutsy doesn't help :D)

---

### Post by sefs on 2007-10-20
Hi all i cant type into the search box of usp with compiz fusion enabled on gutsy any fixes?

---

### Post by delfick on 2007-10-21
> **sefs said:**
> Hi all i cant type into the search box of usp with compiz fusion enabled on gutsy any fixes?

that's my problem too

with an updated compiz/compiz fusion it doesn't happen (not even playing with focus prevention settings works in gutsy install)

....

---

### Post by sefs on 2007-10-21
gutsy seems to have broke every damn thing. this is a dud on arrival.

---

### Post by mnml on 2007-10-21
work fine for me thanks for the dev, but the button for the control center doesn't work;
I have to type /usr/bin/gnome-control-center
in the terminal to launch it.

---

### Post by sefs on 2007-10-22
mnml are you saying that...

1) you are on gutsy
2) you have compiz fusion enabled and running
3) you are able to type text into the search box at the bottom of the usp applet?

> **mnml said:**
> work fine for me thanks for the dev, but the button for the control center doesn't work;
I have to type /usr/bin/gnome-control-center
in the terminal to launch it.

---

### Post by mnml on 2007-10-22
> **sefs said:**
> mnml are you saying that...

1) you are on gutsy
2) you have compiz fusion enabled and running
3) you are able to type text into the search box at the bottom of the usp applet?

1) I am on gutsy
2) I have compiz fusion enabled and running
3) I am able to type text into the search box at the bottom of the usp applet

:)

cf: screenshot

---

### Post by sefs on 2007-10-23
First of all I love your windows/theme, how can I get my windows to look like that? what theme is it???

Second...what are you focus stealing prevention settings for compiz?  did you have to tweak it? or did it just work.

> **mnml said:**
> 1) I am on gutsy
2) I have compiz fusion enabled and running
3) I am able to type text into the search box at the bottom of the usp applet

:)

cf: screenshot

---

### Post by sneax on 2007-10-24
Hello, I'm now using this menu too and have some remarks:
- I too can't use the search field
- How can I use 'tabs'? I tried a bit but couldn't get it to function properly. I would want 2 tabs taking in 1 pane, first tab 'applications' second tab 'recent'.
- The userinfo thing doesn't show correct information (no username, bad 'logged in since'-time etc...
- I would like to be able to widen the categories in 'applications'. Right now some names are cut off (sound&video for example). Widening the whole applet doesn't work
- Is there an applet that somehoew replaces the 'places' menu?
- Where can I see which the available applets are?
- Is it possible ot have a searchbox that uses tracker to search? A bit like vista - would be very easy!

Really an awesome concept! It has a lot of potential.

---

### Post by delfick on 2007-10-24
> **sneax said:**
> Hello, I'm now using this menu too and have some remarks:
- I too can't use the search field
- How can I use 'tabs'? I tried a bit but couldn't get it to function properly. I would want 2 tabs taking in 1 pane, first tab 'applications' second tab 'recent'.
- The userinfo thing doesn't show correct information (no username, bad 'logged in since'-time etc...
- I would like to be able to widen the categories in 'applications'. Right now some names are cut off (sound&video for example). Widening the whole applet doesn't work
- Is there an applet that somehoew replaces the 'places' menu?
- Where can I see which the available applets are?
- Is it possible ot have a searchbox that uses tracker to search? A bit like vista - would be very easy!

Really an awesome concept! It has a lot of potential.

hmm, which version you using ??

also, this might be useful for you [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

:D

---

### Post by sefs on 2007-10-26
maybe it would be helpful for those with the search box working to state what their compiz focus stealing preventions are set too in gutsy.

---

### Post by mjpoetic on 2007-10-26
For whatever reason...I can't get usp to load for other users.  I think this is probably a permissions issue but I can't figure it out because everyone should be able to access it.

---

### Post by sneax on 2007-10-29
> **delfick said:**
> hmm, which version you using ??

also, this might be useful for you [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

:D

Thanks for the link!

I'm using the SVN.

---

### Post by delfick on 2007-10-29
> **sneax said:**
> Thanks for the link!

no probs :D

> I'm using the SVN.

still have problems ??
(or were you using svn before as well ?)
:D

---

### Post by sneax on 2007-11-02
I still can't use the serach field but that's no bother!

Also, I can't seem to find how to make a newpane with in that pane 2 tabs and then another newpane which is always showing. I think you need something like an 'newpane' and 'endpane' same as for 'newtab' and 'endtab' so you can steer nesting behaviour.

---

### Post by annoia on 2007-11-04
Ok, now for a challenge! I'm on Debian (sid) so it's not quite your standard system. Anyways, it should still work (right?). When I add it to the panel I get no reaction. Not until I move the entire panel to the side of the screen does it show up, and it stays there when I move it back. However, nothing happens when I click it.

The command 'usp run-in-window' yields an error, though:
Traceback (most recent call last):
  File "/usr/bin/usp", line 1769, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1749, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1565, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 100, in __init__
    self.language,self.encoding=locale.getdefaultlocale()
  File "/usr/lib/python2.4/locale.py", line 346, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.4/locale.py", line 278, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_DK

---

### Post by g3eb4y on 2007-11-06
great panel - love it

but there are 2 things that bother me (think they are connected):
1st: When I click on the "System" Icon and then click on the desktop or any other window, the menu does not disappear... (but this is not the main problem)

the main problem is 2nd: When I launch an application through this panel, th panel remains "marked" ... I have to click on the panel to "unmark" it.. when i click a second time the menu appears again....

hope you understand my problem^^

maybe there are solutions, but i did not found anything for this problem...

so big thanks for your suggestions
g3eB4Y

EDIT:
my system: Ubuntu 7.10 (gutsy)

---

### Post by geber on 2007-11-14
hello, 
I'm newbie in linux especially in ubuntu
I like this panel, but still have a problem to using search box.
is this possible to change default search engine with google desktop for example?
I'm using USP SVN and compiz-fusion are enabled on ubuntu feisty.
can anyone tell me how to fix it?
btw I've just fixed control center button to working correctly, just replace "gcenter" with "gnome-control-center" in the preferences>system management

---

### Post by delfick on 2007-11-14
> **geber said:**
> I like this panel, but still have a problem to using search box.

as in you can't type into it?

what version of compiz-fusion you using?

---

### Post by oneadvent on 2007-11-15
Ok apparently I am slow. I installed USP2 and do not have the user plugin.

What am I doing wrong? Is there a guide on how to set this all up.

I just found this yesterday, and it is a huge improvement!

---

### Post by delfick on 2007-11-15
[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)

:D

just put [http://ubuntu-system-panel.googlecode.com/files/USP2%20Add-On%20Plugins.tar.gz](http://ubuntu-system-panel.googlecode.com/files/USP2%20Add-On%20Plugins.tar.gz) into 
~/.usp/plugins

and restart gnome-panel
(sudo killall gnome-panel)

.... :D

---

### Post by geber on 2007-11-15
> **delfick said:**
> as in you can't type into it?

what version of compiz-fusion you using?


yes, i can't type anything in the search box
I'm using compiz-fusion version 0.52 git20071007

thanks

---

### Post by oneadvent on 2007-11-15
Ok, last question, and then I think I got it.

I dragged an icon into both the shorcuts and the favourites menus, but neither show either words or the icons.

I know they are there because they are "raised"

any ideas on why the picture/words is not there?

---

### Post by oneadvent on 2007-11-15
> **geber said:**
> yes, i can't type anything in the search box
I'm using compiz-fusion version 0.52 git20071007

thanks

I know that there is a bug with compiz and input boxes. It happens in frostwire to me all the time.

Have you tried to copy and past into the box?

---

### Post by delfick on 2007-11-16
> **oneadvent said:**
> Ok, last question, and then I think I got it.

I dragged an icon into both the shorcuts and the favourites menus, but neither show either words or the icons.

I know they are there because they are "raised"

any ideas on why the picture/words is not there?

hmm, personally I'm not sure on that...
someone else might though :D

> **geber said:**
> yes, i can't type anything in the search box
I'm using compiz-fusion version 0.52 git20071007

thanks

hmm, works here
(mind you I use 0.6.0 git...)
try looking in the ccsm -> General Options -> Focus & Raise Behaviour -> Focus Prevention Windows

if it already has nothing, try
!type=DOCK

and if that doesn't work, try starting a thread in the general usage section of [http://forum.compiz-fusion.org](http://forum.compiz-fusion.org)

....

---

### Post by oneadvent on 2007-11-16
> **delfick said:**
> hmm, personally I'm not sure on that...
someone else might though :D


Actually it goes further too. It seems that even the wordless/iconless shortcuts do not work. Here is the catch, they are for a wine application.

Also, I added it to my normal gnome menu, and it showed up in the right place under "games" on USP, but that wont work either. It works on the main menu still though.

Maybe there is special instructions on wine applications?

Josh

EDIT: Actually HTOP doesn't work either from the menu. Its not just wine. I am using 7.10, and a pretty much fresh install. What am I doing wrong? Konsole works, and so does java management....

---

### Post by delfick on 2007-11-16
hmm, wierd

it works for me..

sure you're using uspsvn ? :D

also, as for wine applications, I suggest using [winefix](http://ubuntuforums.org/showthread.php?t=533257) because otherwise you have to set the folder in the shortcut...
(wine needs to be in the folder where you're executing the program from, winefix doesn't)....

:D

---

### Post by oneadvent on 2007-11-16
Well that didn't help, although that is a crazy cool program. I did install it and I think I will use it....

this is really frustrating, it cant only be happening to me.

Is there a forum just for the USP?

---

### Post by delfick on 2007-11-17
> **oneadvent said:**
> Well that didn't help, although that is a crazy cool program. I did install it and I think I will use it....

this is really frustrating, it cant only be happening to me.

damn

unfortunately Malac and Chanders, the people who pretty much made the usp (not too sure on who else really contributed to it, sorry to those people if they exist :p)

anyway, those two both moved house (seperately :D) and haven't been active over here for a while, so we can't really ask them.....
(unless they see this :D)

> Is there a forum just for the USP?

this is the forum just for usp :D
(well this section of the forum anyways)

used to be a single thread in compiz.net right at the beginning but then it moved here....

---

### Post by oneadvent on 2007-11-17
> **delfick said:**
> damn

unfortunately Malac and Chanders, the people who pretty much made the usp (not too sure on who else really contributed to it, sorry to those people if they exist :p)


So, will there be no more updates?

I think this is a great menu, but I am still having a hard time replacing the normal menu, (Which is kinda sad in a way), but mostly because of the few programs that wont start. 

I have both running until I get used to the new one sufficiently.

I would say that it could use an upgrade to fully utilize more compiz than it does.

If it isn't a frozen project, who is updating it now? I think it is a great thing for gnome/linux/ubuntu


Josh

---

### Post by delfick on 2007-11-17
> **oneadvent said:**
> If it isn't a frozen project, who is updating it now? 

I believe it is a frozen project for the time being until chanders and Malac have the time to work on it again, if that ever happens.......

though there is this here [http://ubuntuforums.org/showthread.php?t=602835](http://ubuntuforums.org/showthread.php?t=602835)
though not sure what's happening there either...

It's been quiet for a really really long time now, but I still have hope :D

---

### Post by Quikee on 2007-11-18
> **delfick said:**
> I believe it is a frozen project for the time being until chanders and Malac have the time to work on it again, if that ever happens.......

though there is this here [http://ubuntuforums.org/showthread.php?t=602835](http://ubuntuforums.org/showthread.php?t=602835)
though not sure what's happening there either...

It's been quiet for a really really long time now, but I still have hope :D

Don't worry.. I have still plans to work on it - however I had a wicked idea for another application which I am currently working on and like to present it shortly. After that I will continue working on USP2 when time allows.

---

### Post by delfick on 2007-11-18
> **Quikee said:**
> Don't worry.. I have still plans to work on it - however I had a wicked idea for another application which I am currently working on and like to present it shortly. After that I will continue working on USP2 when time allows.

cool :D

---

### Post by camnor on 2008-01-16
WOW~! I like that soo much thank you it works great for me! I was kinda starting to miss my searchable start menu.... haha looks amazing keep up the good work!:KS

---

### Post by garyedwardjohnston on 2008-01-24
this is coming from a total NOOB!!!

worked great thanks!

link to theme and control centre are broken though but everything else is flawless and EASY.

:)

---

### Post by #Reistlehr- on 2008-02-07
Great App, better than the gnome-main-menu, more customizable. Love it!

---

### Post by geekcliff on 2008-02-08
> **#Reistlehr- said:**
> Great App, better than the gnome-main-menu, more customizable. Love it!
How can i get my hands on the last version of it.

---

### Post by delfick on 2008-02-08
> **geekcliff said:**
> How can i get my hands on the last version of it.

[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

:D

---

### Post by #Reistlehr- on 2008-02-08
i was using .41-1 and i hated the toggle button for the app. Just donwloaded the svn version, looks great, works better. So many fixes. Great job.

edit: i lied. I made sure that pin menu was off, which it is, but i still have to keep toggling the menu. Is there anyway to get it to automatically close on off focus?

Also, do the plugins randomize? A bunch of times so far the plugins keep changing everytime i open the menu.

---

### Post by Scarecrow__79 on 2008-02-10
awesome!

took me two goes to get it installed, but i love it. I can't wait for Version 3 to come out...

---

### Post by geekcliff on 2008-02-11
> **delfick said:**
> [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

:D

Thank you delfick ive just got it, and its up and running, looks great.:guitar:

---

### Post by delfick on 2008-02-11
> **geekcliff said:**
> Thank you delfick ive just got it, and its up and running, looks great.:guitar:

no probs :)

---

### Post by #Reistlehr- on 2008-02-11
is it normal behavior for the menu to be toggle?

---

### Post by delfick on 2008-02-11
what do you mean?

---

### Post by #Reistlehr- on 2008-02-12
When you open the menu, the menu opens, obviously, but in order to close it, you have to hit the button again. Hence toggle. 

Is it possible to disable the toggle to achieve the effect of the menu closing when you take the focus off the menu by say, clicking on anther app, or clicking on the desktop?

Pin Menu is not checked in gconf.

---

### Post by delfick on 2008-02-12
hmmm, that behaviour seems to happen for me....

when you open the menu, there's a little button on the top left, that isn't selected is it?

(if it isn't selected, then I'm not sure, sorry )

---

### Post by #Reistlehr- on 2008-02-12
Yeah happens whether it is selected or not. Default behavior was the side panel was hidden.

I've never gotten into python before, but im extremely fluent in php, so im going to attempt to mod it. I love the menu, it's just, a pet peeve of mine when it doesn't close. 

:) Thanks for the help.

---

### Post by Krydahl on 2008-02-12
Just installed this - looks great. 

A couple of questions. I seem to have a grey border around it. I'd assumed that ticking the hide border box would get rid of this. It doesn't seem to. Is there any way to hide it, or at least change the color? It doesn't fit too well with my theme.

Also, is it possible to control where on the screen USP appears? Thanks.

---

### Post by Krydahl on 2008-02-12
OK I take it back, It seemed to work great, but then I restarted my PC. USP disappeared off my panel and attempts to add it back seem to add a single white pixel.

Help!

---

### Post by lurchnz on 2008-02-12
Fantastic menu system, coming along nicely. Ubuntu should put their weight behind this and release it as part of their package. With a little bit of a clean up and closer links to Ubuntu, it would finish the deskop gui off.

Good work :-)

---

### Post by Krydahl on 2008-02-13
Re-running the install seemed to fix my disappearing icon. Let's hope it hangs around a bit longer this time.

---

### Post by geekcliff on 2008-02-29
Is this project dead?:confused:

---

### Post by delfick on 2008-02-29
> **geekcliff said:**
> Is this project dead?:confused:

I like to think it's in hibernation :)

gives the hope that it might wake up one day and continue to move forward :p

(the two developers, Malac and Chanders both moved houses and since then not much has happened)

---

### Post by Malac on 2008-02-29
> **geekcliff said:**
> Is this project dead?:confused:
Hopefully not.
 
I am currently trying to find time to work on USP2 now I'm more settled in my new home (still loads of boxes to unpack but at least my computers are up and running again).
 
I had a bit of a delay after doing the overdue upgrade from Feisty to Gutsy trashed a few things and I had to track them down.
 
I have still not heard anything from chanders so I have no idea where we stand on USP3 dev or whether he wants to go on with USP project at all...... I do.
 
Also Quikee has started work on another version of USP2 in which he has "re-designed" the core and plugin code which I have not really had any time to look at either. I'm unsure as yet if this "re-designed" USP2 is intended to replace the original USP2 or if they are to be integrated at some point taking the best bits from each.
Hopefully Quikee won't mind if I stick in my twopenneth if the "re-designed" core is to be the way forward.
 
Hope this helps.

---

### Post by Malac on 2008-02-29
hi delfick, you got in first :).

---

### Post by delfick on 2008-02-29
> **Malac said:**
> hi delfick, you got in first :).

does that mean I get a gold star ? :) lol

One day I'll learn python and get joined in usp development :D
(uni just started again so that goal is once again pushed back)
(was too interested in flex during these holidays ([http://code.google.com/p/flashbsm/](http://code.google.com/p/flashbsm/)))

---

### Post by Malac on 2008-02-29
> **delfick said:**
> does that mean I get a gold star ? :) lol
 
One day I'll learn python and get joined in usp development :D
(uni just started again so that goal is once again pushed back)
(was too interested in flex during these holidays ([http://code.google.com/p/flashbsm/](http://code.google.com/p/flashbsm/)))
Another gold star to delfick. :)
 
I'll checkout the flashbsm tonight.
I'm on a clients computer at the mo' supposedly working on there code but waiting for compile thought I'd scan the forum, better get off.
Au revoir

---

### Post by delfick on 2008-02-29
> **Malac said:**
> Another gold star to delfick. :)

yay ! :D
 
> I'll checkout the flashbsm tonight.

cool

> **I'm on a clients computer**

lol :D

---

### Post by geekcliff on 2008-03-03
> **Malac said:**
> Hopefully not.
 
I am currently trying to find time to work on USP2 now I'm more settled in my new home (still loads of boxes to unpack but at least my computers are up and running again).
 
I had a bit of a delay after doing the overdue upgrade from Feisty to Gutsy trashed a few things and I had to track them down.
 
I have still not heard anything from chanders so I have no idea where we stand on USP3 dev or whether he wants to go on with USP project at all...... I do.
 
Also Quikee has started work on another version of USP2 in which he has "re-designed" the core and plugin code which I have not really had any time to look at either. I'm unsure as yet if this "re-designed" USP2 is intended to replace the original USP2 or if they are to be integrated at some point taking the best bits from each.
Hopefully Quikee won't mind if I stick in my twopenneth if the "re-designed" core is to be the way forward.
 
Hope this helps.

This is great news, USP is just what linux gnome needs, it may tempt more windows people over, if i ever do a demo to anyone i always use linux mint3, cos it use your menu and beryl works on the live disc, that usualy gets the real geeks drueling, if you show anyone the standard gnome menu they usualy compare it to win98, at least USP looks 21st century. 
(I Think most people regard me as a Linux bore, but i dont care, cos I LOVE IT!)

---

### Post by Malac on 2008-03-03
Thanks geekcliff. :)

---

### Post by myname on 2008-03-07
I just installed USP_0.41-1 in Gutsy, and all of the Control Center buttons/links do not bring up the Ubuntu control center.  

Is there a way to modify/customize the menu?

--kevin

---

### Post by delfick on 2008-03-07
> **myname said:**
> I just installed USP_0.41-1 in Gutsy, and all of the Control Center buttons/links do not bring up the Ubuntu control center.  

Is there a way to modify/customize the menu?

--kevin

hello

firstly, 0.4.1 is old, you'll want the svn version :) [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

once that's installed, right click on the usp and choose preferences.

you should have a tab for each plugin you have chosen in the list on the right there.

the one you want is the settings tab, (should be self-explanatory when you see it :p, if not please say)

...

---

### Post by myname on 2008-03-08
ok, got that installed, Thanx.

however, the command for the "control center" is gcontrol.  I typed that into a command window and received "Command not found". 

What is the command to bring up the Ubuntu control center, if there is one?

--Kevin

---

### Post by delfick on 2008-03-08
> **myname said:**
> ok, got that installed, Thanx.

no probs :)

> however, the command for the "control center" is gcontrol.  I typed that into a command window and received "Command not found". 

What is the command to bring up the Ubuntu control center, if there is one?

--Kevin

I don't believe there is one by default in ubuntu...

but there is this [http://ubuntuforums.org/showthread.php?t=207894](http://ubuntuforums.org/showthread.php?t=207894)

---

### Post by myname on 2008-03-08
Thanx, the command is gnome-control-center.  It appears it's already installed in gutsy, hopefully the correct version of UCC is installed.

This seems to work only under the Control Center option from "System Management" and does not work from the Control Center under "Computer" from within USP.

Any ideas?

-Kevin

---

### Post by Malac on 2008-03-09
> **myname said:**
> Thanx, the command is gnome-control-center.  It appears it's already installed in gutsy, hopefully the correct version of UCC is installed.

This seems to work only under the Control Center option from "System Management" and does not work from the Control Center under "Computer" from within USP.

Any ideas?

-Kevin
I have tested this with my own setup and it should work fine from USP Computer/Settings plugin(still don't know why this isn't just called Settings).

Here is how my config page looks: [ATTACH]62135[/ATTACH]

If after checking this it still does not work,
 then remove USP from the panel,
 open terminal (Applications->Accessories->Terminal)
type ```
usp run-in-window
```Some messages will appear telling you what usp is doing.
Hit the Control Center button and see what errors, if any, are listed then post them here.

Hope this helps

---

### Post by geekcliff on 2008-03-10
I See on the above screenshot, you got all the plugins, ive tried this but cant get them to work, i followed the instructions on the download page, which was add them to "/home/<yourusername>/.usp/plugins", the plugins folder i created, i did unzip them first, was this correct?

---

### Post by geekcliff on 2008-03-10
Its ok, i sorted it out, it was me being a numpty.:lolflag:

---

### Post by LordOfThePigs on 2008-03-10
Hello,

I'm trying to get compiz to make the USP window transparent, but I can't figure out how to do that. Does anybody know the exact settings for compiz to make it work?

Ideally, I would like to make it both transparent and blurred.

Thanks for your help.

---

### Post by delfick on 2008-03-10
you won't be able to make it have "real transparency" (where the icons and text are not transparent, but the background is) 

but you can use this guide here [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching) to fill out the window match option for:

ccsm -> general options -> opacity settings -> window opacities : for making the window transparent

and 

ccsm -> blur -> alpha blur windows : to make everything behind the menu blurred...

good luck :)

---

### Post by LordOfThePigs on 2008-03-10
thanks, I made it work the way I wanted. The matching rule I used is name=usp. At an opacity of about 80%, even if the text is not fully opaque, it still looks like it is, so the effect is convincing enough. Real transparency would be great though :)

---

### Post by Krydahl on 2008-03-17
I have a minor issue with USP2 at the moment. Quit doesn't work. 

The command in System Management (gnome-session-save --kill) works fine from a terminal, but doesn't seem to do anything when I click the link in USP2. Anyone got any ideas?

---

### Post by Malac on 2008-03-20
> **Krydahl said:**
> I have a minor issue with USP2 at the moment. Quit doesn't work. 

The command in System Management (gnome-session-save --kill) works fine from a terminal, but doesn't seem to do anything when I click the link in USP2. Anyone got any ideas?
Try running USP from a terminal, like so: ```
usp run-in-window
```and choosing Quit and see if there is any output from it.

Actually this would be the first thing to try for any problem with USP as sometime this throws out an obvious answer.

---

### Post by Krydahl on 2008-03-20
Thanks for responding.

I tried running from the terminal. As it loaded I got the following:
```
*********** Keybind Failure **************
Using Standard Menu
system_management: loaded successfully
applications: loaded successfully
places: loaded successfully
Hotkey Binding Error
```

However, when I clicked quit from the instance started from the terminal it worked correctly.

Quit from the version on my panel still doesn't do anything. Weird.

Anything else I can try?

---

### Post by dasbooter on 2008-03-20
I still have the problem where you cannot type in the search box. Also clicking on the desktop with usp open doesnt close usp as it used too. I remember having similiar issues with an svn install in feisty with beryl and I thought it was fixed by changing focus stealing to none in beryl manager. I am now using gutsy, usp svn as of todays post, and compizfusion git .I have googled and read extensively on the problem and I have tried entering a number of things ccsm's focus prevention windows. I have even tried altering ```
sudo gedit /usr/share/usp/usp2.glade

``` to change it to a menu type from another thread but have had no success. Please enlighten me usp is far and ahead anything else in Ubuntu as far as I am concerned... it is just being difficult right now :(

hilarious... 2 seconds later I tried removing usp from the panel and re-adding and now it is working fine. I have typed "!type=MENU" in the aforementioned window b/c of the line I altered as mentioned before. I swear even a restart of the system did not fix this... how is that possible.

---

### Post by Malac on 2008-03-23
> **Krydahl said:**
> Thanks for responding.

I tried running from the terminal. As it loaded I got the following:
```
*********** Keybind Failure **************
Using Standard Menu
system_management: loaded successfully
applications: loaded successfully
places: loaded successfully
Hotkey Binding Error
```However, when I clicked quit from the instance started from the terminal it worked correctly.

Quit from the version on my panel still doesn't do anything. Weird.

Anything else I can try?

I can't understand this one at all this works perfectly on my Gutsy and Hardy test systems. Can you do a Backup of your USP settings ( right-click->Preferences->Backup ) and add it as a post attachment on this thread. I'll test it here and see if that throws out anything.


> **dasbooter said:**
> I still have the problem where you cannot type in the search box. Also clicking on the desktop with usp open doesnt close usp as it used too. I remember having similiar issues with an svn install in feisty with beryl and I thought it was fixed by changing focus stealing to none in beryl manager. I am now using gutsy, usp svn as of todays post, and compizfusion git .I have googled and read extensively on the problem and I have tried entering a number of things ccsm's focus prevention windows. I have even tried altering ```
sudo gedit /usr/share/usp/usp2.glade

``` to change it to a menu type from another thread but have had no success. Please enlighten me usp is far and ahead anything else in Ubuntu as far as I am concerned... it is just being difficult right now :(

hilarious... 2 seconds later I tried removing usp from the panel and re-adding and now it is working fine. I have typed "!type=MENU" in the aforementioned window b/c of the line I altered as mentioned before. I swear even a restart of the system did not fix this... how is that possible.
It's a strange thing with Gnome/Compiz that I have noticed a reboot doesn't always commit changes with applets/or focus settings (not just USP), sometimes I have had to remove applet, reboot, re-add the applet then reboot to get changes to "take".

Glad your problem is sorted though.

---

### Post by Krydahl on 2008-03-23
This is obviously something weird with my install. I've recently added USP to my laptop and this works find on that. The machine that's playing up is the one in my sig. The onboard graphics for this mobo are nvidia GeForce 6150.

The backup file you asked for is attached. Thanks for looking at this.

---

### Post by Krydahl on 2008-03-23
Damn - file didn't attach. You can't upload xml files to this site apparently. Saved as txt instead,

---

### Post by Malac on 2008-03-23
> **Krydahl said:**
> Damn - file didn't attach. You can't upload xml files to this site apparently. Saved as txt instead,
I have attached a slightly different version of the system_management plugin to this post.
If you could download this to the /usr/lib/python2.4/site-packages/usp/plugins folder and then from a terminal run:
```
usp run-in-window **-v**
```This should print out exactly what the plugin is trying to execute when you click the Quit button, hopefully this may help diagnose what the problem is.

---

### Post by Krydahl on 2008-03-23
OK, done that. This time I got:```
*********** Keybind Failure **************
Using Standard Menu
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'places' : successful
Hotkey Binding Error
<gtk.Button object at 0xfccfa0 (GtkButton at 0xdb6ce0)> ['gnome-session-save', '--kill']
```

But do bear in mind that it always worked ok when run in the terminal.

---

### Post by Malac on 2008-03-23
> **Krydahl said:**
> OK, done that. This time I got:```
*********** Keybind Failure **************
Using Standard Menu
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'places' : successful
Hotkey Binding Error
<gtk.Button object at 0xfccfa0 (GtkButton at 0xdb6ce0)> ['gnome-session-save', '--kill']
```But do bear in mind that it always worked ok when run in the terminal.
Okay, well that's correct.
As this seemed to work on your other machine and it is working on both of my test rigs and normal machine,
all I can suggest now is re-install gnome-session in synaptic or with aptitude:```
sudo aptitude reinstall gnome-session
```and hope this solves the problem.
If not try reinstalling python.

Sorry for vague response but I'm flummoxed.

---

### Post by Krydahl on 2008-03-23
That's all right. Thanks for looking at it. It's not a big deal. As a workaround I've just added a quit button to my panel.

If you want bugs to look at :) here another minor glitch (and this does happen on both my machines).

I click the USP button, the menu appears. I select the app I want, click it, the USP menu disappears and the app starts - **but the USP button stays clicked**.

Now, if I want to start another app, I click the USP button and that deselects it. No menu. I have to click the USP button again to get the menu back.

Not that I want to sound like I'm complaining. USP2 is way ahead of any of the other menu options I've tried. Keep up the great work. One day I'll learn python and glade and start helping on projects like this instead of just using them.

---

### Post by nymusicman on 2008-04-06
You know what would make this application complete, at least for me (and hopefully a few other people out their as well). The search box to also be a command line run box. Or at least add a command line run box or access to the run feature.

---

### Post by Malac on 2008-04-06
> **nymusicman said:**
> You know what would make this application complete, at least for me (and hopefully a few other people out their as well). The search box to also be a command line run box. Or at least add a command line run box or access to the run feature.
Have you tried the terminal plugin it can be sized to be just one line if you like, this might work for you.

It's available in the tar.gz here [http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)

Just extract the terminal py and glade files to /home/*<username>*/.usp/plugins/ folder or to the main plugins folder. Then add it to the plugins list.

Hope this helps.

---

### Post by Mazza558 on 2008-04-07
I'd just like to say... this thing is incredible. I love it!

---

### Post by Mazza558 on 2008-04-07
Is there a plugin to open folders? That'd be awesome.

---

### Post by Malac on 2008-04-10
> **Mazza558 said:**
> Is there a plugin to open folders? That'd be awesome.
There's the places plugin which lists either your mounted drives plus Home, Desktop, Computer and Network. This also shows the gtk bookmarks (the ones in the side pane of nautilus windows) you can set it to show the bookmarks by default in Places section of Preferences.

Or there's the shortcuts plugin which you can add folders to by dragging the folder from an open nautilus window, hold it over the USP menu button until it opens, then onto the space below the Shortcuts heading. First one is a little tricky as the target area is only one line high (you'll know when you see a black line that you've got it) but gets easier after that.
You can add spaces and/or separators to the list, change icons and/or names to help organize them using the right click menu.
Once the shortcuts are added it will need a reload or logoff/logon to activate them, this is a small bug.
I'm currently working on this plugin to try to get rid of this and also to change some of the underlying files to make it more logical and get font size changes to take effect immediately.

**(Edit : Done this now. If any one updates can they redo their shortcuts lists by renaming /home/[COLOR=DimGray]*<username>*[/COLOR]/.usp/places folder to shortcuts and /home/[COLOR=DimGray]*<username>*[/COLOR]/.usp/places.list file to shortcuts.list then edit shortcuts.list and replace all occurences of "places" with "shortcuts", reload USP. Thanks).**
The code below should do this :
```

cd ~/.usp
mv places shortcuts
mv places.list shortcuts.list
sed -i 's/places/shortcuts/g' shortcuts.list

```

[ATTACH]65516[/ATTACH]
Any problems let me know here.

Hope this helps.

---

### Post by Malac on 2008-04-13
Updated shortcuts Drag/Drop again (Rev# 276)
Got rid of the first shortcut being a bit tricky to get the Drop by making the whole plugin below the title receive Drop info.

Hope this makes it more usable.

---

### Post by Malac on 2008-04-14
Updated recent plugin to hide thumbnails as this was slowing down people who had lots of recent files.
Added more explanation to "Number of Document Entries" spin to limit the number of thumbnails generated in Preferences(uspconfig)

added boolean gconf entry /apps/usp/plugins/recent/hide_document_thumbnails 

Now on Rev #277.

---

### Post by Malac on 2008-04-17
Now at Rev #279.
Added Edit Menu option to right-click which opens alacarte.
Updated applications to show any menu changes immediately without having to call Reload.

---

### Post by delfick on 2008-04-17
> **Malac said:**
> Now at Rev #279.
Added Edit Menu option to right-click which opens alacarte.
Updated applications to show any menu changes immediately without having to call Reload.

very nice :)

---

### Post by Malac on 2008-04-18
> **delfick said:**
> very nice :)
Thank you :)

Working on sub-folders now as I remember seeing this asked for somewhere.

---

### Post by Mazza558 on 2008-04-18
Hi,

It'd be cool if you created the option for the categories of apps to show their icons too. also, a small divider between the categories and actual apps would be nice. Thanks...

---

### Post by Mazza558 on 2008-04-18
I've also found a strange bug where adding a shortcut to the Shortcuts plugin works with some and not with others. I drag 2 shortcuts to exactly the same place on the panel, one works and the other doesn't. They have the same icon and command.

---

### Post by Malac on 2008-04-19
> **Mazza558 said:**
> It'd be cool if you created the option for the categories of apps to show their icons too. also, a small divider between the categories and actual apps would be nice. Thanks...
I will look into these.

> **Mazza558 said:**
> I've also found a strange bug where adding a shortcut to the Shortcuts plugin works with some and not with others. I drag 2 shortcuts to exactly the same place on the panel, one works and the other doesn't. They have the same icon and command.
I hope I'm understanding you correctly but here goes; you can't drag two shortcuts to the plugin if they have the same command and icon this is not a bug it is intentional but thanks for reporting it.

---

### Post by Malac on 2008-04-19
Okay I have a test version of applications.py to try on anyone willing to give it a go.
I thought I'd post it here instead of to SVN as it still needs testing and is nowhere near ready.
At the moment the folders are using bold text to distinguish them hence the Category Buttons are too. I can make this an option. if it is preferred.
Side effects so far; the lower folder apps are taken out of the Filter and All Category.
This also has Mazza558's category icon buttons.(sort of)

Any thoughts/comments/(abuse:()  post/pm me.
It is still in heavy test mode [SIZE=3][B]please backup your applications.py or rename the test one and add it as a separate plugin by that name.

Test File Update now on Page 81 post #807
[/B][/SIZE]

---

### Post by Mazza558 on 2008-04-20
> **Malac said:**
> Okay I have a test version of applications.py to try on anyone willing to give it a go.
I thought I'd post it here instead of to SVN as it still needs testing and is nowhere near ready.
At the moment the folders are using bold text to distinguish them hence the Category Buttons are too. I can make this an option. if it is preferred.
Side effects so far; the lower folder apps are taken out of the Filter and All Category.
This also has Mazza558's category icon buttons.(sort of)

Any thoughts/comments/(abuse:()  post/pm me.
It is still in heavy test mode [SIZE=3][B]please backup your applications.py or rename the test one and add it as a separate plugin by that name.

[/B][/SIZE]

Hi, I gave it a go, and there's no difference between this one and the older one - I tried reloading the plugins and even the whole applet, with no difference.

---

### Post by Malac on 2008-04-20
> **Mazza558 said:**
> Hi, I gave it a go, and there's no difference between this one and the older one - I tried reloading the plugins and even the whole applet, with no difference.
Sorry, my bad, I thought I'd typed it in but I didn't, the gconf key is:
```
/apps/usp/plugins/applications/show_category_button_icon
```this needs to be set to True (ticked in gconf-editor).
If you have no sub-folders this won't be any different apart from the icons on Category Buttons (they are currently being clipped as well).

---

### Post by Lostincyberspace on 2008-04-21
I have the latest USP from svn how do I use the config and where do I find it?

---

### Post by Malac on 2008-04-22
> **Lostincyberspace said:**
> I have the latest USP from svn how do I use the config and where do I find it?
Either in a terminal :
```
uspconfig
``` or :
right-click USP button and choose "Preferences" or:

Open gconf-editor [Applications->System Tools->Configuration Editor] and navigate to /apps/usp

Hope this helps.

---

### Post by MemoryDump on 2008-04-22
excuse my ignorance and not having gone through all 81 pages of this thread.. but where do I download the latest version of this app? or should I say how?
I was looking at: [http://ubuntuforums.org/showthread.php?t=229014](http://ubuntuforums.org/showthread.php?t=229014) which is on the first post, however it seems like it hasn't been updated in quite some time.

thxs :D

---

### Post by Malac on 2008-04-22
> **MemoryDump said:**
> excuse my ignorance and not having gone through all 81 pages of this thread.. but where do I download the latest version of this app? or should I say how?
I was looking at: [http://ubuntuforums.org/showthread.php?t=229014](http://ubuntuforums.org/showthread.php?t=229014) which is on the first post, however it seems like it hasn't been updated in quite some time.

thxs :D
Installation instructions are here:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps.

---

### Post by MemoryDump on 2008-04-22
> **Malac said:**
> Installation instructions are here:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps.
ahh cool.. I had just found this before your reply. thanks :)

>  Installation   
Installation and updating of USP SVN.
Introduction

Installation Instructions provided by kobewan
Details

Please Note:- If you are running beryl you will need to set focus stealing to "None" to use USP.

Installation All you need to do is make sure that you have Subversion, so that you can download the SVN. Run this command:

sudo apt-get install subversion

Alright, now cd to the directory that you want to download it to. For example, I like to use ~/Downloads/SVN , so that's where I'll go:

cd ~/Downloads/SVN

now run

svn checkout [http://ubuntu-system-panel.googlecode.com/svn/trunk/](http://ubuntu-system-panel.googlecode.com/svn/trunk/) ubuntu-system-panel

This should download all the correct files that you need. Now, put in

cd ubuntu-system-panel

and then

./usp_update install fresh

That should install it for you, as well as clearing out the old version!

Before you finally get to add the applet to your panel, do this:

killall gnome-panel

Your Panel(s) will disappear for a few seconds then re-appear. Don't worry this is correct.

Now you can right click on any empty panel area, and select 'Add to Panel'. You should see 'Ubuntu System Panel' under the 'Miscellaneous' group.

Updating Whenever you want to get the latest SVN version of USP, 'cd' to the directory that contains the SVN files (in the above example it was ~/Downloads/SVN) and type

./usp_update update

This should display a log of all the changes that were made between the version that you have and the newest version. It will then download all the files that you need and attempt to install them. You will most likely need to enter your password before USP is updated.

Uninstallation

You can also uninstall USP by going to the directory that contains the SVN files (in the above example it was ~/Downloads/SVN) and typing in

./usp_update uninstall

If you want to uninstall completely, including removing your settings, put in

./usp_update uninstall complete


from the wiki: [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

---

### Post by Malac on 2008-04-22
New test applications with glade file and py file not sure if this is the way to go or whether popup menu maybe better for sub-folders. Thoughts.....................

---

### Post by bijeeshvs on 2008-04-28
hi guys i installed USP and i am pretty impressed with the concept anyhow i would like to suggest a few modifications
1) to click to get the applications list is a bad idea if the menu could learn and display the most used and recently used list on its first appearance that could be great 
2) my theme was unable to theme the panel it was able to cover the gnome menu but USP was not covered 
if these things are done then i will say goodbye to the gnome menu..........................
thanks for the effort

---

### Post by Malac on 2008-04-28
> **bijeeshvs said:**
> hi guys i installed USP and i am pretty impressed with the concept anyhow i would like to suggest a few modifications
Thanks :)
> **bijeeshvs said:**
> 1) to click to get the applications list is a bad idea if the menu could learn and display the most used and recently used list on its first appearance that could be great
There is a recent plugin, I'm at a Win machine and can't check but I'm not sure it's enabled by default.
Just go to "Preferences" on the right click menu and add recent to the plugins list hit "Save" and it should appear. It tracks recent applications and documents.
I'm currently working on this plugin as at the moment it only tracks the most recent not the most _used_ applications.
> **bijeeshvs said:**
> 2) my theme was unable to theme the panel it was able to cover the gnome menu but USP was not covered 
if these things are done then i will say goodbye to the gnome menu..........................
thanks for the effort
USP use the current gtk theme that is used by Gnome at all times unless in "Preferences" the box on the first page has something in it. Check there is nothing in there. Also a change of theme will require a logout/login or restart of USP.
 
Hope this helps.

---

### Post by bijeeshvs on 2008-04-28
first of all i am sorry, i was using your first version as it was not clear which version i was using and upto which version u have reached. Now i got the latest version and its running fine and thank you for such great software, but i was a bit confused to track the versions as its not easy to go through all those pages (81 i think) and on the last page i found how to get the latest version. So make some transparency in getting the files the plugins were easier to get , maybe its my fault any how thank you  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Malac on 2008-04-28
> **bijeeshvs said:**
> first of all i am sorry, i was using your first version as it was not clear which version i was using and upto which version u have reached. Now i got the latest version and its running fine and thank you for such great software, but i was a bit confused to track the versions as its not easy to go through all those pages (81 i think) and on the last page i found how to get the latest version. So make some transparency in getting the files the plugins were easier to get , maybe its my fault any how thank you  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
You are right.
It's a mess at the moment.

I would like to get a version into the Ubuntu repos soon as I think we are missing a lot of people who might find it useful.

We could do with removing the 0.41 thread or at least !un-stickying! it.
I suppose I could start a thread for the latest .deb file and try to get it stickied.

Sorry for the confusion.

---

### Post by Malac on 2008-04-28
Okay I've added the extra plugins to the SVN (Rev #284).
They still need to be manually installed at the moment from the "usp-extras" folder where you download the SVN.
Perhaps PsyberOne can amend the usp_update file with an "extras" command line option to install into the /home/<username>/.usp/plugins location.

---

### Post by amerioz on 2008-04-28
great Panel , I love it
I've searched gnome-look and other websites for USP themes but didnt find any! does anybody know where to find good USP themes?

---

### Post by delfick on 2008-04-29
> **Malac said:**
> Okay I've added the extra plugins to the SVN (Rev #284).
They still need to be manually installed at the moment from the "usp-extras" folder where you download the SVN.
Perhaps PsyberOne can amend the usp_update file with an "extras" command line option to install into the /home/<username>/.usp/plugins location.

cool :)

for now I'm just gonna make a link in ~/.usp called plugins that will point to the usp-extras folder....

---

### Post by Malac on 2008-04-29
> **delfick said:**
> for now I'm just gonna make a link in ~/.usp called plugins that will point to the usp-extras folder....
Hadn't thought of that (bit of a dense day, need more sleep)but it just might work. :)
> **amerioz said:**
> great Panel , I love it
I've searched gnome-look and other websites for USP themes but didnt find any! does anybody know where to find good USP themes?
All GTK themes are compatible with USP some look better than others.
The only purpose written USP theme I know of is by roberTO and you can find info here:
[http://ubuntuforums.org/showthread.php?t=357368](http://ubuntuforums.org/showthread.php?t=357368)

Hope this helps.

---

### Post by amerioz on 2008-04-29
Thank Malac
I know all gtk themes applies on USP too , but I was looking for customized USP themes , I've checked the url you gave me but for my bad the links provided in the thread arent available !

---

### Post by Malac on 2008-04-29
> **amerioz said:**
> Thank Malac
I know all gtk themes applies on USP too , but I was looking for customized USP themes , I've checked the url you gave me but for my bad the links provided in the thread arent available !
Found this one but have not tried it out.
[http://elgg.org/tom/files/9/380/USP-theme.zip](http://elgg.org/tom/files/9/380/USP-theme.zip)

And attached my copy of solidwhite but I think it's an old one.

---

### Post by BlackDex on 2008-04-29
Hey Malac, thx for this greate menu.
I Used gimmie before, but this is so much better.

But i have found a small buggy, and fixed it localy.
The uspUser doesn't show my username and login correctly.
I use Hardy Final, and this is what my 'who -s' outputs.
```
blackdex tty7         2008-04-29 21:20 (:0)
blackdex pts/0        2008-04-29 22:03 (:0.0)
blackdex pts/1        2008-04-29 22:05 (:0.0)
```

At line #174 of uspuser.py there is a check if the len is more then 5, if so the offset is set to 4 so it will get the next line, but this gives the wrong username etc..
I commented out line #174 and #175, and it now works as it should.

I hope you can fix this small problem.
Thx again for this nice menu.

---

### Post by amerioz on 2008-04-29
Thanx Malac , I was looking for that
but you know I just found out that I can apply GTK themes to USP without applying them to whole system =)
thanx alot mate

---

### Post by Quikee on 2008-04-29
> **BlackDex said:**
> Hey Malac, thx for this greate menu.
I Used gimmie before, but this is so much better.

But i have found a small buggy, and fixed it localy.
The uspUser doesn't show my username and login correctly.
I use Hardy Final, and this is what my 'who -s' outputs.
```
blackdex tty7         2008-04-29 21:20 (:0)
blackdex pts/0        2008-04-29 22:03 (:0.0)
blackdex pts/1        2008-04-29 22:05 (:0.0)
```

At line #174 of uspuser.py there is a check if the len is more then 5, if so the offset is set to 4 so it will get the next line, but this gives the wrong username etc..
I commented out line #174 and #175, and it now works as it should.

I hope you can fix this small problem.
Thx again for this nice menu.

To get the username in a safe way use:
```
import getpass
getpass.getuser()
```

No need to parse what 'who' returns.

---

### Post by bijeeshvs on 2008-04-30
hello friend your menu is soo cool and effective and i love it a lot, i think after building such a great menu u are after adding more options to it. I mean like the calender and calculator stuff , i have one request to you  please find time to stream line the menu make it more intelligent, make it learn things thereby making it more user friendly. I have one suggestion if u provide an edit mode for the menu that is rather than entering the values in the combo boxes ( for size and orientation )  and reload the menu to see the changes , in the edit mode an user can freely manipulate the menu ( resize, shift, add and move objects resize objects that is each pane in the menu) on the fly that could be cool. i know it may be complex i was just making a wish 

Also make it more effects friendly ( like transperency ) if it was as transperent like a emerald title window glass that could be fantastic 



only my wishes dont think i am asking for too much ..........


but i love the whole thing


its great................................

---

### Post by Krydahl on 2008-04-30
I can't help with all the technical stuff, obviously, but if you're running Compiz you can get the usp panel transparent easily. 

In the advanced-desktop manager, go into General Options -> Opacity Settings.

Add an entry using name=usp and set the Opacity to whatever value you like.

---

### Post by bijeeshvs on 2008-05-01
Thank you for that information, actually i didnt know that ( setting transparency for a specific window can be done)
and  i was not asking about how to do that i was just making a suggestion in these type of transparency every thing in the window get transparent that makes it unreadable, i was talking about making it transparent like the avant window navigator icons and details are visible but the menu is transparent like glass thats it once again Thank you .............

---

### Post by Malac on 2008-05-02
> **Quikee said:**
> To get the username in a safe way use:
```
import getpass
getpass.getuser()
```
 
No need to parse what 'who' returns.
Thanks, I'll check into that Quikee but I would like to include the uptime as well and I'm not on an ubuntu machine at the mo' to check out what that module reports.
> **bijeeshvs said:**
> hello friend your menu is soo cool and effective and i love it a lot, i think after building such a great menu u are after adding more options to it. I mean like the calender and calculator stuff
Thanks.
The calendar and other extra plugins are now in the SVN repo.
If you make a link in /home/<username>/.usp called plugins to the usp-extras folder in the folder you downloaded the svn to these will be available to add.> **bijeeshvs said:**
>  i have one request to you please find time to stream line the menu make it more intelligent, make it learn things thereby making it more user friendly. I have one suggestion if u provide an edit mode for the menu that is rather than entering the values in the combo boxes ( for size and orientation ) and reload the menu to see the changes , in the edit mode an user can freely manipulate the menu ( resize, shift, add and move objects resize objects that is each pane in the menu) on the fly that could be cool. i know it may be complex i was just making a wish 
 
Also make it more effects friendly ( like transperency ) if it was as transperent like a emerald title window glass that could be fantastic 
Drag/Drop and other layout adjustments were being looked into for USP3 and that is on hold at the moment. I will add it to my list.
> **bijeeshvs said:**
> only my wishes dont think i am asking for too much ..........
No problem
> **bijeeshvs said:**
> 
but i love the whole thing
 
its great................................
Thanks again.

---

### Post by Malac on 2008-05-03
Updated uspuser to SVN now Rev #289 using getpass as Quikee  suggested (cheers).
Still have to parse "who" for times but only if user wants it displayed.
Unless anyone can help translating /var/log/lastlog.
Added /apps/usp/plugins/user/show_full_name option to gconf
Altered Preferences section for User to allow for this.

---

### Post by Quikee on 2008-05-03
> **Malac said:**
> 
Still have to parse "who" for times but only if user wants it displayed.
Unless anyone can help translating /var/log/lastlog.


[PHP]#! /usr/bin/env python

from __future__ import with_statement
import struct
import time
import pwd
import os


class LastLog(object):
	def __init__(self, logName):
		self.logName = logName
		self.logStruct = 'i32s256s'
		self.logStructLength = struct.calcsize(self.logStruct)

	def getLoginTime(self, pid):
		with open(self.logName, 'rb') as file:
			file.seek(self.logStructLength * pid, os.SEEK_SET)
			entry = file.read(self.logStructLength)
			if not entry:
				return 0
			login = struct.unpack(self.logStruct, entry)
			return login[0]
			
	def getLoginTimeAsString(self, pid):
		return time.ctime(self.getLoginTime(pid))
		   
lastLog = LastLog('/var/log/lastlog')
for userData in pwd.getpwall():
	pid = userData[2]
	print userData[0], lastLog.getLoginTimeAsString(pid)[/PHP]

Yey.

---

### Post by Malac on 2008-05-03
> **Quikee said:**
> [php]#! /usr/bin/env python

from __future__ import with_statement
import struct
import time
import pwd...................
<><><><><><><><>
......og = LastLog('/var/log/lastlog')
for userData in pwd.getpwall():
    pid = userData[2]
    print userData[0], lastLog.getLoginTimeAsString(pid)[/php]Yey.
Thanks Quikee,
I tried something similar but my login kept coming back way out, i.e.  Thu Mar 20 18:14:32 2008 for today.
While the one from "who -u" was coming back as 2008-05-03 16:13 which was right at the time.
My /var/log/lastlog must be screwed or the code is not adding up correctly from the ticks.
This is why I went back to "who -u" with getpass it means I can do a search of the output and seek the right login.
My only idea why it would be wrong is that it's something to do with English dates as opposed to US format. in the calculations.

Thanks.

---

### Post by Quikee on 2008-05-03
> **Malac said:**
> Thanks Quikee,
I tried something similar but my login kept coming back way out, i.e.  Thu Mar 20 18:14:32 2008 for today.
While the one from "who -u" was coming back as 2008-05-03 16:13 which was right at the time.
My /var/log/lastlog must be screwed or the code is not adding up correctly from the ticks.
This is why I went back to "who -u" with getpass it means I can do a search of the output and seek the right login.
My only idea why it would be wrong is that it's something to do with English dates as opposed to US format. in the calculations.

Thanks.

When I checked it now it doesn't work for me also (however the program parses it fine because it adds up with the 'lastlog' command). Looks like when you login in gdm it doesn't count as a login that goes into lastlog but only if you login in terminal (tty) or via ssh. 

If I am not mistaken, who reads its data from /var/run/utmp which could also be parsed. The structure is well defined ('man utmp') but I don't have time currently to mess with it. ;)

---

### Post by Malac on 2008-05-04
> **Quikee said:**
> When I checked it now it doesn't work for me also (however the program parses it fine because it adds up with the 'lastlog' command). Looks like when you login in gdm it doesn't count as a login that goes into lastlog but only if you login in terminal (tty) or via ssh. 

If I am not mistaken, who reads its data from /var/run/utmp which could also be parsed. The structure is well defined ('man utmp') but I don't have time currently to mess with it. ;)
Cheers Quikee that was my next one to look at too. :)

I've found python-utmp which gives the struct of the utmp and wtmp files but there should be a utmpaccess as well but I can't find it at the mo'.
I may revert to using the output of 'last -f var/run/utmp' instead as an easy option.

---

### Post by nymusicman on 2008-05-08
This would be the most ultimate start menu ever made for gnome if:

the filter/search box was also a run box.

So the question goes out, will this ever happen?

---

### Post by Malac on 2008-05-08
> **nymusicman said:**
> This would be the most ultimate start menu ever made for gnome if:

the filter/search box was also a run box.

So the question goes out, will this ever happen?
The search box is already, if the application is at the top of the list of filtered apps when you are entering letters then just hit enter.
As for a specific run box so you can enter command line and switches,etc. the only thing I can suggest at the moment is to use the terminal plugin and make it one line high.
But I may add a separate run box if I can find the time.

Hope this helps.

---

### Post by tier on 2008-05-09
Mm, i edit the code of applications.py. You can run programs which are not present in the list (just type the text, for example "xterm", and press enter).

PS. Sorry for my poor english :)

---

### Post by Malac on 2008-05-09
> **tier said:**
> Mm, i edit the code of applications.py. You can run programs which are not present in the list (just type the text, for example "xterm", and press enter).
 
PS. Sorry for my poor english :)
Thanks tier, I'll look into it tonight.

---

### Post by Malac on 2008-05-11
Added a run box to SVN Rev #308
This is set to hotkey <Ctrl><Alt>R this can be changed in Preferences.
or gconf key /app/usp/hot_key_run_box for those who prefer gconf-editor.
[ATTACH]69673[/ATTACH]
There is a pull-down list  of past commands which can be cleared using the Clear Button.

Hope this helps.

---

### Post by delfick on 2008-05-11
cool

is it possible to put it into the menu itself as well ? :)

---

### Post by tier on 2008-05-11
But it is very similar with standard gnome run dialog :)

PS. In SVN Rev #308 if unchecked Places -> Show Tabbed Selection Method, in the Places i see tabs. It's bug?

---

### Post by Quikee on 2008-05-12
> **Malac said:**
> Added a run box to SVN Rev #308
This is set to hotkey <Ctrl><Alt>R this can be changed in Preferences.
or gconf key /app/usp/hot_key_run_box for those who prefer gconf-editor.
[ATTACH]69673[/ATTACH]
There is a pull-down list  of past commands which can be cleared using the Clear Button.

Hope this helps.

How is this different to the standard gnome "run box" (alt-F2).. ?

---

### Post by Malac on 2008-05-12
> **delfick said:**
> is it possible to put it into the menu itself as well ? :)
Knew I should have done a poll first as to whether people wanted it integrated or as a plugin or as a run dialog.
I've added tier's alterations to allow the search box to execute if there are no apps left in filter list.
> **tier said:**
> But it is very similar with standard gnome run dialog :)
> **Quikee said:**
> How is this different to the standard gnome "run box" (alt-F2).. ?
Well, it's the same but with _less_ ( #-o)features. :oops: (alt-R in compiz)
Went ahead and coded it and didn't even think of this. Thought it was odd that people kept asking for it.:oops:
> **tier said:**
> In SVN Rev #308 if unchecked Places -> Show Tabbed Selection Method, in the Places i see tabs. It's bug?
Works on mine. Have you tried a "killall gnome-panel" to force reload usp. I'll re-upload places.glade and .py files to the SVN this will be Rev#311.

---

### Post by Quikee on 2008-05-12
> **Malac said:**
> Well, it's the same but with _less_ ( #-o)features. :oops: (alt-R in compiz)
Went ahead and coded it and didn't even think of this. Thought it was odd that people kept asking for it.:oops:

Maybe just make the existing "apllications" entry box smarter - the effect would be the same I think (because the entry box has focus when you trigger the key binding). ;) You also could for example in the "new applications" plugin I had the ability to execute shell commands if the prefix was "$", with prefix "?" for example you could add a simple expression evaluator, ...

---

### Post by tier on 2008-05-12
> I've added tier's alterations to allow the search box to execute if there are no apps left in filter list.
Thanks :)
> Works on mine. Have you tried a "killall gnome-panel" to force reload usp. I'll re-upload places.glade and .py files to the SVN this will be Rev#311.
Rev #331. 1) Go to the Preferences -> Places
2) uncheck Show Tabbed Selection Method. I see combobox instead tabs in USP menu.
3) reload USP, or "killall gnome-panel". I see tabs instead of combobox :(
4) In the Preferences -> Places Show Tabbed Selection Method still unchecked.
I tried it on Ubuntu 7.10 and Archlinux.

---

### Post by Malac on 2008-05-13
> **tier said:**
> Thanks :)

Rev #331. 1) Go to the Preferences -> Places
2) uncheck Show Tabbed Selection Method. I see combobox instead tabs in USP menu.
3) reload USP, or "killall gnome-panel". I see tabs instead of combobox :(
4) In the Preferences -> Places Show Tabbed Selection Method still unchecked.
I tried it on Ubuntu 7.10 and Archlinux.
Sorry, I get it now.
Yes it's a bug, I'll get on it straight away.

**EDIT:**
Okay fixed. Rev #314
This has highlighted that the plugins need a complete tidy-up/standardisation of the code too.

I've added the option to launch in terminal by prefixing the search with $ character, i.e. $sudo gconf-editor would launch a terminal then those commands.

---

### Post by tier on 2008-05-13
> Okay fixed. Rev #314
Thanks, I'm very glad :)
> I've added the option to launch in terminal by prefixing the search with $ character
This is very useful innovation!

---

### Post by Malac on 2008-05-13
> **tier said:**
> Thanks, I'm very glad :)
You're Welcome
> **tier said:**
> This is very useful innovation!
Credit to Quikee for the idea.

---

### Post by Mazza558 on 2008-05-13
I have an idea. It'd be VERY cool if there was some way to have single-key hotkeys to select tabs quickly. I have the terminal as one of my tabs, and it'd be nice to switch to it straight away.

EDIT: Even cooler than that would be an option to use different buttons on the taskbar to show different tabs separately...

---

### Post by Malac on 2008-05-14
> **Mazza558 said:**
> I have an idea. It'd be VERY cool if there was some way to have single-key hotkeys to select tabs quickly. I have the terminal as one of my tabs, and it'd be nice to switch to it straight away.
 
EDIT: Even cooler than that would be an option to use different buttons on the taskbar to show different tabs separately...
I have been thinking of the hotkey opening specific tabs for a while now, so it is on my list.
 
Trying to avoid more buttons on the panel/taskbar as I didn't want to use up valuable "real estate". :)

---

### Post by Malac on 2008-05-14
Okay added hotkey switching to tabs. SVN Rev #315

It is done the same way icons are added to tabs but using curly brackets {} instead of square brackets [] e.g.

newtab=Extra/Add-On Plugins[add]**{<Shift><Super>E}**

gives a tab called "Extra/Add-On Plugins" with an icon using "[add]" on hotkey using "{<Shift><Super>E}"

Please test and let me know if any problems.
Thanks.

---

### Post by ricochet1269 on 2008-05-17
I seem to be having trouble installing UPS.  I followed the instructions on the googlecode website, but when I get to:
> ./usp_update install fresh
I get:
> bash: ./usp_update: No such file or directory

Any ideas where I messed up?

Nevermind, I got it

---

### Post by Phristen on 2008-05-22
Where is all the configuration stored?
There is .usp folder in home directory but it only contains the lists of recent apps & files.

Also, isn't the Run... thing redundant of Alt+F2?

And the panel seems to be about 5 pixels lower, so its edge overlaps with the gnome panel. How do I fix that?

---

### Post by Malac on 2008-05-23
> **Phristen said:**
> Where is all the configuration stored?
There is .usp folder in home directory but it only contains the lists of recent apps & files.
The settings are stored in gconf "database", to access this :
Open gconf-editor/"Configuration Editor" on menu
navigate to /apps/usp all the settings for usp itself are there.
/apps/usp/plugins contains plugin specific settings under plugin's name.
 
> **Phristen said:**
> Also, isn't the Run... thing redundant of Alt+F2?
Yes, completely redundant really. I never use the run dialog at all. Thought the gnome one had been removed as everyone kept asking for it so I wrote one. I will probably remove this when I have the time as it is just extra space taken up.
 
> **Phristen said:**
> And the panel seems to be about 5 pixels lower, so its edge overlaps with the gnome panel. How do I fix that?
Have you tried the usp_offset value in gconf-editor or on "Main" tab in "Preferences"?

---

### Post by Phristen on 2008-05-23
> navigate to /apps/uspAha! ;)
> Have you tried the usp_offset value in gconf-editor or on "Main" tab in "Preferences"?Yes, but it has no effect.

Also, when I move the mouse over the USP button (i.e. on the GNOME panel), it has no mouseover effect, like the standard gnome-main-menu button. Is that expected behaviour?
And finally, when compiz is working, the USP window is not animated (i.e. open/close animations do not apply to it), whereas gnome-main-menu is fully animated.

Just though I'd post my feedback... Great project overall, I'd love to see it incorporated in GNOME release some day ;)

P.S. I installed from SVN, btw.

---

### Post by simpson-fan on 2008-05-31
Hi!

From where can I get the USP and it is installable?

okay I found it: [http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

---

### Post by magnus0 on 2008-06-14
The application categories should have icons, like in the original gnome applications menu. It's easier to find something then.

---

### Post by magnus0 on 2008-06-14
> **magnus0 said:**
> The application categories should have icons, like in the original gnome applications menu. It's easier to find something then.

Oh sorry. I didn't look into the preferences.

---

### Post by magnus0 on 2008-06-14
Am I missing something or there isn't any option to show Places menu? I downloaded the latest version from svn

---

### Post by tier on 2008-06-15
Add plugin "places" in the Preferences :)

---

### Post by bijeeshvs on 2008-06-15
hello malac hope u r doing good...................


can u integrate the "AWN Dock" rendering technique into USP if USP looks like a glass bar that could be awesome ( not transparency effects in compiz ) icons and text must be 100% opaque

---

### Post by Malac on 2008-06-15
> **magnus0 said:**
> The application categories should have icons, like in the original gnome applications menu. It's easier to find something then.
This feature has only just been added so it's easy to miss. :)
> **bijeeshvs said:**
> hello malac hope u r doing good...................
Doing fine thank you bijeeshvs
> **bijeeshvs said:**
>  can u integrate the "AWN Dock" rendering technique into USP if USP looks like a glass bar that could be awesome ( not transparency effects in compiz ) icons and text must be 100% opaque
This would require a re-code pretty much from scratch and I do not have the time at the moment. It is definitely on the cards.
This is so far for the widgets.
[ATTACH]74157[/ATTACH]
And there is a demo of chanders work on usp3 which he was trying to make "skin-able" and/or transparent which I have been working on when I have the time.
[ATTACH]74161[/ATTACH]

For the moment Quikee's version may be more what you want.
It doesn't have as many features yet but does handle transparency.

---

### Post by bijeeshvs on 2008-06-17
Well, Malac take a look at this...............

---

### Post by chanders on 2008-06-17
[quote=bijeeshvs]hello chanders, malac told me that u are working for a transparent version of usp and he showed me two screen shots, can u use the glass rendering engine instead (AWN or Cairo) its much appealing than simple transparency 

i have made a post in your thread about it but i don't see u there so sending this private message[/quote]

Hey, actually all of the rendering is done in Cairo which makes for a beautiful render, however getting Cairo to work with native GTK elements is very tricky, and nothing short of redoing the entire widget in cairo (read:TONS of work)

I wasn't aware AWN had its own rendering engine/widget set? Do you have any reference to that?

---

### Post by bijeeshvs on 2008-06-17
hello chanders, sorry i am not that technical but how is emerald rendering the title bar, can we use that?

---

### Post by chanders on 2008-06-17
> **bijeeshvs said:**
> hello chanders, sorry i am not that technical but how is emerald rendering the title bar, can we use that?

NO probs ;-)  I will do some research into the rendering done by emerald... If I am not mistaken they use cairo but do not need to integrate it with GTK widgets which is where the work really starts..

---

### Post by tweezyturtle on 2008-07-28
hey, I don't know if this has been covered before (this being such a long thread) but I installed USP panel .41 via a .deb and I can no longer find the settings for USP, the only options I get when I right click on it are "About, Remove from panel, Move, and Lock to panel" there are a bunch of things I want to add and change but I can't, can anyone help me?

here's an image of the messed up USP .41 menu...
[http://img510.imageshack.us/my.php?image=uspmenuscreenshotkw3.png]("http://img510.imageshack.us/my.php?image=uspmenuscreenshotkw3.png")

---

### Post by Malac on 2008-07-28
> **tweezyturtle said:**
> hey, I don't know if this has been covered before (this being such a long thread) but I installed USP panel .41 via a .deb and I can no longer find the settings for USP, the only options I get when I right click on it are "About, Remove from panel, Move, and Lock to panel" there are a bunch of things I want to add and change but I can't, can anyone help me?

here's an image of the messed up USP .41 menu...
[http://img510.imageshack.us/my.php?image=uspmenuscreenshotkw3.png](http://img510.imageshack.us/my.php?image=uspmenuscreenshotkw3.png)
0.41 is now out-of-date.
The latest version is 2.0 Beta, installation instructions are available here:-
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
If you wish to use 0.41 instead of the latest SVN version then I will try to help.
There is no Preferences option in the 0.41 version. You can download uspconfig app from here:-
[http://ubuntuforums.org/showthread.php?t=272372](http://ubuntuforums.org/showthread.php?t=272372)
This works with versions up to 0.41

If you wish to run 0.41 version then:

[LIST=1]
[*]Plugins must be in the folder /usr/lib/python2.4/site-packages/usp/plugins or in ~/.usp/plugins to work.
[*]You can configure usp options using the Configuration Editor (Applications->System Tools->Configuration Editor) or run ```
gconf-editor
``` in a terminal. Info is stored here under /apps/usp
[*]Open a terminal and run```
usp run-in-window
```and post the output to help with troubleshooting.
[/LIST]
Hope this helps.

---

### Post by Krydahl on 2008-07-28
Hi Malac,

A quick question while you're around. I upgraded to the latests version a while back and I've noticed a change of behaviour. In the applications plugin, if you select 'all applications' USP now groups the application by type (accessories, games etc) where it used to list them alphabetically. I found the old behaviour more useful. Is there a way to change it back? I can't see anything in the preferences.

Thanks.

---

### Post by Malac on 2008-07-29
> **Krydahl said:**
> Hi Malac,

A quick question while you're around. I upgraded to the latests version a while back and I've noticed a change of behaviour. In the applications plugin, if you select 'all applications' USP now groups the application by type (accessories, games etc) where it used to list them alphabetically. I found the old behaviour more useful. Is there a way to change it back? I can't see anything in the preferences.

Thanks.
Well spotted Krydahl, I hadn't noticed.
Now you point it out I will look into this. Looks like the sort has been moved to the outer loop, sorting on type instead of the app name. This is a side effect of the work on doing sub-folders I did recently. I will get to it tomorrow evening(Wed).

---

### Post by Krydahl on 2008-07-29
Great, thanks. No hurry.

---

### Post by Malac on 2008-07-30
Just uploaded the fix now. Rev #331.

---

### Post by Krydahl on 2008-07-30
Yep, that did the trick. Thanks.

---

### Post by killerwhale65 on 2008-08-07
hello,

I was wondering how to add my favourite applications to the list?

Also, when i add the "terminal" plugin, i get a "no module named terminal" error.

Is there a list with plugins? It would be wise to be able to select them from a dropdown instead of having to type the name (which you don't know).

And can i add my favourite files and folders as well?

thanks!

Matt

---

### Post by Krydahl on 2008-08-07
> I was wondering how to add my favourite applications to the list?

Which list precisely? You can mark an application that appears in the applications plugin as a favourite (right click on it) and it will appear in your favourites (which you can toggle between and all applications in the applications plugin). 

If that doesn't work for you, you could also set up some shortcuts - that will give you a separate list of your favour apps. To do this, add the shortcuts plugin in your preferences (not forgetting to save the change), then create a launcher to the desired apps on your desktop. (I found it easiest to do this from the standard menu. If, like me, you've removed this from your panel because you're using USP2, just hit ALT+F1.) Now drag you launchers into the shortcuts area in USP. To do that, you need USP pinned. I found it easiest to do that by going into USP preferences and ticking the pin menu box in "main" until I'd finished adding all my shortcuts. (What this does is stop USP from disappearing when you click elsewhere on your desktop which allows you to grab the launchers.)

> Also, when i add the "terminal" plugin, i get a "no module named terminal" error.

The terminal plugin is not enabled by default, it's one of the extras. To get it to work you need to create a link to your extras directory. If you don't know how to do that, type:

```
ln -s ~/downloads/SVN/ubuntu-system-panel/usp-extras/ ~/.usp/plugins
```

in a terminal. Note, however, that you may have to change the path I've specified - the first path should be to wherever you put your USP download when you installed initially. I think what I've specified here matches what the instructions at the Google code site suggests, but you need to check the path you've used to be sure.

Note that I had to remove USP from my panel and then add it again to get it to pick up the new plugins when I did this. There may be a better way to get it to detect the changes, but I don't know it.

> Is there a list with plugins? It would be wise to be able to select them from a dropdown instead of having to type the name (which you don't know).

Yes [here]("http://code.google.com/p/ubuntu-system-panel/wiki/PluginInfo").

> And can i add my favourite files and folders as well?

Any directories/files that you've bookmarked through nautilus will show up in your places list on USP. If you don't have places, just add the places plugin. Note that this can be toggled between places and bookmarks. (Bookmarks show up in bookmarks, obviously).

Hope this helps.

---

### Post by Malac on 2008-08-08
Thanks for fielding this Krydahl.
All good except you don't need to pin the menu as it now supports drag 'n' drop.
If you drag a folder to the USP button on the panel and hold it there USP should open, then move the mouse to the shortcuts plugin and release the left mouse button and it should place it in shortcuts.

Hope this helps.

---

### Post by EnigMattic on 2008-08-08
Thanks! Latest revision excellent!
Can't wait for USP3 -- how's it looking?
Guessing the new USP2 repo release must be nearly done?

---

### Post by Krydahl on 2008-08-08
> **Malac said:**
> Thanks for fielding this Krydahl.
All good except you don't need to pin the menu as it now supports drag 'n' drop.
If you drag a folder to the USP button on the panel and hold it there USP should open, then move the mouse to the shortcuts plugin and release the left mouse button and it should place it in shortcuts.

Hope this helps.

My pleasure - least I could do. Keep up the great work.

---

### Post by killerwhale65 on 2008-08-08
> **Krydahl said:**
> Hope this helps.

Thanks for your extensive manual :)

question1: can i add files to my favourites as well in Nautilus? I only seem to be able to drop folders, but in your explanation you talk about folders/files.

question2: is it possible to have the menu open when i hoover over the menu button? I aks this because i am using AWN, and the only thing left now on my original gnome panel is the USP button. I have my panel behind AWN, but whenever i hit the USP button, it comes to the front and hides AWN. I could make the panel non-expanding, but then i end up with the ugly handels. Or is there any other way to have this working with AWN?

question3: Are you interested in having USP specific themes (not the GTK ones that it currently supports)? I am a graphical designer and would be happy to release design some good looking themes for this applet. 
A pro to use a USP specific theme system, in my opinion is that the USP menu is something where you start almost every task on your PC, and is therefore very often used. And therefore, i find it important to have it look exactly the way you want. 
If interested i could do a mockup.

Thanks!

Matt

---

### Post by Krydahl on 2008-08-08
question1 - my bad. No, you can only bookmark directories in nautilus so far as I know. 

For files, there is a "recent" plugin that you might find useful, but I don't think it handles favourites.

Questions 2 & 3 I'll have to leave for Malac.

---

### Post by Malac on 2008-08-08
> **killerwhale65 said:**
> question1: can i add files to my favourites as well in Nautilus? I only seem to be able to drop folders, but in your explanation you talk about folders/files.
Use the shortcuts plugin. You may have to remove the nautilus by editing the shortcuts 'Exec' property after dropping by right-click and choosing edit.

> **killerwhale65 said:**
> question2: is it possible to have the menu open when i hoover over the menu button? I aks this because i am using AWN, and the only thing left now on my original gnome panel is the USP button. I have my panel behind AWN, but whenever i hit the USP button, it comes to the front and hides AWN. I could make the panel non-expanding, but then i end up with the ugly handels. Or is there any other way to have this working with AWN?
This is possible but may interfere with other functions. I will look into it.

> **killerwhale65 said:**
> question3: Are you interested in having USP specific themes (not the GTK ones that it currently supports)? I am a graphical designer and would be happy to release design some good looking themes for this applet. 
A pro to use a USP specific theme system, in my opinion is that the USP menu is something where you start almost every task on your PC, and is therefore very often used. And therefore, i find it important to have it look exactly the way you want. 
If interested i could do a mockup.
I would definitely be interested. Although we are currently working on a composite version of USP which will use a theme file to do drawing and apply textures, this is stilll some way off so in the meantime it would be great to have USP looking as good as possible.

Hope this helps.


[B]EDIT : I've just uploaded a new version of uspconfig to the SVN that has a pull down list of the available plugins.(Rev #333)
This should hopefully help when adding plugins.[/B]

---

### Post by delfick on 2008-08-08
> **Malac said:**
> [B]EDIT : I've just uploaded a new version of uspconfig to the SVN that has a pull down list of the available plugins.(Rev #333)
This should hopefully help when adding plugins.[/B]

nice :)

---

### Post by killerwhale65 on 2008-08-09
Thanks for the assistance.

I will do a mockup one of these days of a possible theme.

regards,

Matt

---

### Post by killerwhale65 on 2008-08-09
hello,

the terminal plugin is not usefull to start programs for example, because then you cant use it anymore (no prompt anymore), and also i believe the program quits when you close the menu. A variant of Alt-F2 (like the Run thingy, but then included in the menu as plugin) would have been better.

---

### Post by delfick on 2008-08-09
> **killerwhale65 said:**
> Also, the terminal plugin is not usefull to start programs for example, because then you cant use it anymore (no prompt anymore)

if you append the command with an ampersand '&' then it's run as a seperate process and the prompt is still free to be used.

for example, if I were to open a file with gedit but keep the prompt free, then I'd do

gedit file.txt &

:)

---

### Post by killerwhale65 on 2008-08-09
nice, thanks (i am new to linux, can you tell ;-) )


Some more things:

1. when i rightclick a shortcut to edit its preferences, the edit dialog appears behind the menu, so i have to drag it a bit towards the top of my screen to be able to see it.

2. The favorite applications should have an option to hide the generic name, so that a lot of space can be saved.

3. Tab titles are not displayed,instead only a number is displayed (1, 2, 3 ...).

4. Maybe an idea to split the applications plugin into favourites and all apps? So that one can more easily have access to both.

---

### Post by delfick on 2008-08-09
> **killerwhale65 said:**
> nice, thanks (i am new to linux, can you tell ;-) )

that's alright, I was the same two years ago :)


> 2. The favorite applications should have an option to hide the generic name, so that a lot of space can be saved.

there is such an option.

under preferences -> Applications -> "Generic Name below Application"

> 3. Tab titles are not displayed,instead only a number is displayed (1, 2, 3 ...).

you have to define the name of the tab 
I can't remember how to do that off the top of my head however....

---

### Post by killerwhale65 on 2008-08-10
> **Malac said:**
> I would definitely be interested. Although we are currently working on a composite version of USP which will use a theme file to do drawing and apply textures, this is stilll some way off so in the meantime it would be great to have USP looking as good as possible.


Hello,

Attached you can find a possible mockup of a theme for USP. I have kept this one quite simple in design, many more is possible but might have been overkill for the mockup. Remember, its just a possibility, don't haunt me if you don't like the colors, other colors are possible, other themes are possible. This one could be called DarkRed. I can also do a DarkBlue and DarkGreen, and then those 3 but with a light background. Makes 6 themes already. After that i could do something totally different, and i would also be happy to design themes on request.

What do you think?

---

### Post by Malac on 2008-08-10
> **killerwhale65 said:**
> hello,

the terminal plugin is not usefull to start programs for example, because then you cant use it anymore (no prompt anymore), and also i believe the program quits when you close the menu. A variant of Alt-F2 (like the Run thingy, but then included in the menu as plugin) would have been better.
You can start programs in a terminal from the 'applications' plugin entry box if you start the entry with a '$' dollar sign (no quotes) e.g. ```
$sudo nano /etc/X11/xorg.conf
```> **killerwhale65 said:**
> Hello,

Attached you can find a possible mockup of a theme for USP. I have kept this one quite simple in design, many more is possible but might have been overkill for the mockup. Remember, its just a possibility, don't haunt me if you don't like the colors, other colors are possible, other themes are possible. This one could be called DarkRed. I can also do a DarkBlue and DarkGreen, and then those 3 but with a light background. Makes 6 themes already. After that i could do something totally different, and i would also be happy to design themes on request.

What do you think?
At the moment USP uses 'cut-down' or normal GTK themes which would mean this idea would not be possible with it as it would require rendering .
I think it is excellent and is exactly what we are looking to do with the next USP version. (Once I can get a decent rendering engine sorted for the new version.)
You have hit on the exact theme type chanders and myself were looking to incorporate.

Thanks very much for your ideas, we will try to incorporate this possibility into USP3.

---

### Post by Malac on 2008-08-10
> **killerwhale65 said:**
> Some more things:

1. when i rightclick a shortcut to edit its preferences, the edit dialog appears behind the menu, so i have to drag it a bit towards the top of my screen to be able to see it.

This is a bug I am trying to squash at the moment. :)
> **killerwhale65 said:**
> 2. The favorite applications should have an option to hide the generic name, so that a lot of space can be saved.
This is a good idea, I will look into this.
> **killerwhale65 said:**
>  3. Tab titles are not displayed,instead only a number is displayed (1, 2, 3 ...).
Hi delfick, :wave:
> **delfick said:**
> you have to define the name of the tab 
I can't remember how to do that off the top of my head however....

Put the name of the tab after the newtab keyword
e.g.** newtab=Standard Plugins**

Add an Icon in [] square brackets
e.g. **newtab=Standard Plugins[gnome-gmenu]**
or just an icon **newtab=[gnome-gmenu]**

Add HotKey in {} curly brackets
e.g. **newtab=Standard Plugins[gnome-gmenu]{<Ctrl><Super>S}**

This gives:
[ATTACH]81046[/ATTACH]
[B]P.S. More explanations/instructions on USP can be found at the WIKI pages here:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)[/B]
> **killerwhale65 said:**
> 4. Maybe an idea to split the applications plugin into favourites and all apps? So that one can more easily have access to both.
Have you thought of using the shortcuts plugin for your favourite apps instead?

Hope this helps.

---

### Post by delfick on 2008-08-10
> **Malac said:**
> Hi delfick, :wave:

:wave: :)

> 
Put the name of the tab after the newtab keyword
e.g.** newtab=Standard Plugins**

I knew it was something simple :p

---

### Post by killerwhale65 on 2008-08-11
> **Malac said:**
> At the moment USP uses 'cut-down' or normal GTK themes which would mean this idea would not be possible with it as it would require rendering .
I think it is excellent and is exactly what we are looking to do with the next USP version. (Once I can get a decent rendering engine sorted for the new version.)
You have hit on the exact theme type chanders and myself were looking to incorporate.

Thanks very much for your ideas, we will try to incorporate this possibility into USP3.

OK, just let me know when you come to the theming part of USP 3, i will be happy to design some theme's for it.

Thanks for the help.


on [http://code.google.com/p/ubuntu-system-panel/wiki/Themes](http://code.google.com/p/ubuntu-system-panel/wiki/Themes) i read about a thread containing a GTK theme develloped only for USP. That link is dead however. If anyone still has that file, i may be using it as a base to do theme's for USP2?

---

### Post by Malac on 2008-08-11
I will get back to you via pm when we get to that stage. Thanks.
> **killerwhale65 said:**
>  i read about a thread containing a GTK theme develloped only for USP. That link is dead however. If anyone still has that file, i may be using it as a base to do theme's for USP2?

Attached theme file.

---

### Post by killerwhale65 on 2008-08-11
> **Malac said:**
> I will get back to you via pm when we get to that stage. Thanks.
Thanks, i will be looking forward to this.


> **Malac said:**
> Attached theme file.
ok, i will see what i can do with this.

---

### Post by Malac on 2008-08-13
> **killerwhale65 said:**
> question2: is it possible to have the menu open when i hoover over the menu button? 
Added this as an option on Main Tab in Preferences.
Hold mouse over button and menu opens. Hold over again and it closes.
SVN Rev#336

---

### Post by Krydahl on 2008-08-13
Something weird going on. I just did an update to pick up your latest version. Suddenly usp has lost all my preferences. I've copied a backup version of the .usp directory into my home. I've killed the gnome panel and removed and added USP again - still using all the default settings. 

Any suggestions, or do I have to manually set everything up again?

---

### Post by Krydahl on 2008-08-13
I'm an idiot. I couldn't remember the exact syntax to do an update so went to the wiki and cut and pasted the command - except I didn't, I cut and & pasted a fresh install. No doubt this is why I lost my settings. Still don't know why copying in the old .usp folder didn't sort it though.

---

### Post by Malac on 2008-08-14
> **Krydahl said:**
> I'm an idiot. I couldn't remember the exact syntax to do an update so went to the wiki and cut and pasted the command - except I didn't, I cut and & pasted a fresh install. No doubt this is why I lost my settings. Still don't know why copying in the old .usp folder didn't sort it though.
The settings for preferences are not in the .usp folder they are held in the gnome/gconf store. If you backed up your settings using the option in Preferences you can restore them from there too. If you didn't backup the settings then if you have an old backup of your home folder you could find the ~/.gconf/apps/usp directory and copy that back over then logout/reboot.
 
Hope this helps.

---

### Post by Krydahl on 2008-08-14
Yup - tah.

---

### Post by killerwhale65 on 2008-08-14
> **Malac said:**
> Added this as an option on Main Tab in Preferences.
Hold mouse over button and menu opens. Hold over again and it closes.
SVN Rev#336

Thanks, works like a charm!

I am struggling to learn about GTK theming. It takes some time to learn the settings file and where all the theme-images show up in the panel, but i will get there so i will release a theme soon!

---

### Post by killerwhale65 on 2008-08-14
One thing i cant seem to find is what colors the vertical separator. It seems to always have the same color, no matter what theme i use. Is this hard-coded into USP?

---

### Post by Mazza558 on 2008-08-14
Could you please reconsider adding the option for multiple buttons on the taskbar to act as different tabs? If you think about how Ubuntu's default is set up, it has 2 panels, and the top panel has an enormous amount of space to use up. If you did this, it would be possible for USP to replace the current menu Ubuntu uses and improve the experience for everybody. 

This is, of course, dependent on how easy it is to write/modify the code to do this.

---

### Post by Malac on 2008-08-15
> **Mazza558 said:**
> Could you please reconsider adding the option for multiple buttons on the taskbar to act as different tabs? If you think about how Ubuntu's default is set up, it has 2 panels, and the top panel has an enormous amount of space to use up. If you did this, it would be possible for USP to replace the current menu Ubuntu uses and improve the experience for everybody. 
 
This is, of course, dependent on how easy it is to write/modify the code to do this.
I'm not sure what you mean by "the default layout has two panels" and "the top panel has an enormous amount of space to use up", that aside multiple instances of USP would require a complete re-code from the ground up as the original idea was for one button. There is only one instance of the USP entries in gconf and it would be a bit of a 'Heath Robinson' ('Rube Goldberg' ) solution to try and bolt on code to divide this up into a random number of instances using the existing code. Sorry about that. I will look into adding this possibility into USP3.
 
> **killerwhale65 said:**
> One thing i cant seem to find is what colors the vertical separator. It seems to always have the same color, no matter what theme i use. Is this hard-coded into USP?
The vertical separator is a file called dotted.png which is located in /usr/share/usp along with the glade files.
I think it is a bit of a throwback to the original USP and should probably be re-thought. I will look at coding this as part of the GTK layout instead. Though I am busy this weekend I will look at it if I can next week.

---

### Post by killerwhale65 on 2008-08-15
> **Malac said:**
> The vertical separator is a file called dotted.png which is located in /usr/share/usp along with the glade files.
I think it is a bit of a throwback to the original USP and should probably be re-thought. I will look at coding this as part of the GTK layout instead. Though I am busy this weekend I will look at it if I can next week.

OK, no wonder i didnt find this, i never looked for images in that folder. Would indeed be best if everything that has to do with layout would be part of the theme. Thanks!

---

### Post by killerwhale65 on 2008-08-15
ok, i've come to the conclusion that the current GTK theming engine does not really provide in the theming flexibility i am looking for. Therefore i have decided not to make themes for the current USP2, but rather wait to make the themes for USP3, with its own theming engine. 
Please do not hesitate to contact me once you are up to this part of USP3!


As for USP2: 
-i've found that the resources plugin does not work: the CPU shows always 0%, while the memory shows 98% used, but in the system monitor its only 57%.
-i've noticed that the more i use the preferences dialog, the busier my CPU gets. In the end i end up with 100% CPU usage constantly, while i am not doing anything. Once i remove USP from the panel, CPU usage instantly drops to 1-2%. I think this only happens while switching themes constantly (on the main tab, the first textbox). Is it possible that it keeps calculating all themes i have added during this session? For example: i add USP to my panel - it shows theme1, then i enter a new theme (theme2), but it calculates also theme1. I now enter theme3, and it calculates for 3 themes ... In the end i end up with having entered 10 themes, and calculating 10 themes uses all my CPU?

Thanks and have a nice weekend!

Matt

---

### Post by Mazza558 on 2008-08-15
> **Malac said:**
> I'm not sure what you mean by "the default layout has two panels" and "the top panel has an enormous amount of space to use up", that aside multiple instances of USP would require a complete re-code from the ground up as the original idea was for one button. There is only one instance of the USP entries in gconf and it would be a bit of a 'Heath Robinson' ('Rube Goldberg' ) solution to try and bolt on code to divide this up into a random number of instances using the existing code. Sorry about that. I will look into adding this possibility into USP3.
 



I meant the default Ubuntu panel layout - one bar at the top and one at the bottom. Ubuntu's normal menu (the application-places-system thing) would be awesome if each button opened a separate panel. If it requires too much code then that's fair enough. Thanks for considering it in USP3 though.

---

### Post by killerwhale65 on 2008-08-15
BUG: when i add amsn.desktop to the compact list:
-icons from compact list are all gone in frontend (still listed in backend)
-applications plugin height has become 2/3 smaller in frontend, in backend still ok
-clicking "all programs" does nothing anymore (can only display favorites)

EDIT: HELP: i removed USP from panel, now i want to add it again, i click "add" but nothing happens? It does not add to my panel anymore:sad:

---

### Post by Malac on 2008-08-16
> **killerwhale65 said:**
> BUG: when i add amsn.desktop to the compact list:
-icons from compact list are all gone in frontend (still listed in backend)
-applications plugin height has become 2/3 smaller in frontend, in backend still ok
-clicking "all programs" does nothing anymore (can only display favorites)

EDIT: HELP: i removed USP from panel, now i want to add it again, i click "add" but nothing happens? It does not add to my panel anymore:sad:
There may be something in the amsn.desktop file that is causing odd behaviour.
Open a terminal and run:```
usp run-in-window
``` and post any errors it spits out, including what happens when "All Applications" is pressed.
Or in a terminal run:```
uspconfig
``` and remove the entry added for amsn.desktop and see if that sorts out adding USP to panel.
If you want whilst in uspconfig do a backup of your settings and tar then attach it here. 
I would be interested in any errors as I could then trap them for an update patch. Thanks.

Hope this helps.


[B]EDIT 1 : Okay I checked out my theory and a malformed .desktop file will cause the compact list to not display at all. I have uploaded a fix to catch this and display the offending button as an error. I will check the applications plugin for the same thing. SVN Rev# 339

EDIT 2 : Can you also attach the offending amsn.desktop in the tar as I cannot re-create the behaviour in All Applications. I need to know what the file contains to see where the error is occurring.
Did you create the amsn.desktop file yourself or in alacarte or was it installed via synaptic or a downloaded .deb package?
[/B]

---

### Post by killerwhale65 on 2008-08-17
hello,

Thanks for your help.

First of all i should mention that after a reboot USP is still not shown, and i can still not add it to the panel.

Then i ran "usp run-in-window":
```
matt@ubuntu:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
system_management: loaded successfully
shortcuts: loaded successfully
applications: loaded successfully
places: loaded successfully
recent: loaded successfully
terminal: loaded successfully
['file:///home/matt/Documents']
['file:///home/matt/Music']
['file:///home/matt/.themes']
['file:///home/matt/Pictures']
['file:///home/matt/Videos']
Traceback (most recent call last):
  File "/usr/bin/usp", line 1107, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1092, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 785, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 479, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 798, in do_plugin
    self.do_applications_file()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 279, in do_applications_file
    LabelOrder = [ApplicationData[4], ApplicationData[0]]
IndexError: list index out of range

```

Note that nothing more happens then this terminal output. I don't see any USP window so i cant press "all applications".

Then i ran uspconfig from the terminal. This nicely opened the configurator screen. No errors in the terminal. In shortcuts, the amsn.desktop file was not mentioned anymore. I also deleted 2 other programs from the list (gedit and gcalc). I backed up, and together with the amsn.desktop file i have attached it. 
I did not make the amsn.desktop myself, that happened during installation.

Then i downloaded your latest version, but it still does not add to the panel.

Heres once more the output of "usp run-in-window", now with the newest version.
```
matt@ubuntu:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
system_management: loaded successfully
shortcuts: loaded successfully
applications: loaded successfully
places: loaded successfully
recent: loaded successfully
terminal: loaded successfully
['file:///home/matt/Documents']
['file:///home/matt/Music']
['file:///home/matt/.themes']
['file:///home/matt/Pictures']
['file:///home/matt/Videos']
Traceback (most recent call last):
  File "/usr/bin/usp", line 1107, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1092, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 785, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 472, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 798, in do_plugin
    self.do_applications_file()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 279, in do_applications_file
    LabelOrder = [ApplicationData[4], ApplicationData[0]]
IndexError: list index out of range

```

Nothing more happens...


I have then completely uninstalled it, including settings, and reinstalled. Now it works (for now ...).

---

### Post by Malac on 2008-08-17
> **killerwhale65 said:**
> 
Heres once more the output of "usp run-in-window", now with the newest version.
```
matt@ubuntu:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
system_management: loaded successfully
shortcuts: loaded successfully
applications: loaded successfully
places: loaded successfully
recent: loaded successfully
terminal: loaded successfully
['file:///home/matt/Documents']
['file:///home/matt/Music']
['file:///home/matt/.themes']
['file:///home/matt/Pictures']
['file:///home/matt/Videos']
Traceback (most recent call last):
  File "/usr/bin/usp", line 1107, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1092, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 785, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 472, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 798, in do_plugin
    self.do_applications_file()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 279, in do_applications_file
    LabelOrder = [ApplicationData[4], ApplicationData[0]]
IndexError: list index out of range

```Nothing more happens...


I have then completely uninstalled it, including settings, and reinstalled. Now it works (for now ...).
Looks like there was a strange entry in the ~/.usp/applications.list file or the associated .desktop file in ~/.usp/applications folder. The other files you sent are fine and work perfectly on my system. It looks like the un-install and re-install sorted out this by deleting the old applications file/folder on the un-install and re-creating them on the re-install.

Thanks for the error reports this will help me trap this in a patch which I will work on this week.
This should have been caught by me at an earlier stage than this, unfortunately you have been the one that has discovered this bug. Thanks again for taking the time to report and help track it down.

---

### Post by Krydahl on 2008-08-18
Is the hot key (<Ctrl><Alt>U by default) meant to open USP without clicking on the panel icon? If so, it doesn't seem to work for me. What do I need to do to enable it please?

---

### Post by Malac on 2008-08-18
> **Krydahl said:**
> Is the hot key (<Ctrl><Alt>U by default) meant to open USP without clicking on the panel icon? If so, it doesn't seem to work for me. What do I need to do to enable it please?
Check that the "Disable HotKey" checkbox is clear in Preferences, Main Tab.

compiz sometimes uses certain keys for it's effects.
If you remove USP from the panel and run:
```
usp run-in-window
``` it will report a binding error if this is the case.

It should look something like this : 
```
malac@ubuntu:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
Static User Image Used
uspuser: loaded successfully
applications: loaded successfully
recent: loaded successfully
computer: loaded successfully
places: loaded successfully
shortcuts: loaded successfully
uspcalendar: loaded successfully
remind: loaded successfully
system_management: loaded successfully
template: loaded successfully
Static User Image Used
Static User Image Used

** (usp:26529): WARNING **: Binding '<Ctrl><Alt>U' failed!

Binding USP Menu to Hotkey: <Ctrl><Alt>U

```If so try a different key for USP or find the compiz key and change that.

---

### Post by Krydahl on 2008-08-18
Thanks for the response. The "Disable HotKey" checkbox is clear.

I get:

```
Using Standard Menu
places: loaded successfully
shortcuts: loaded successfully
applications: loaded successfully
system_management: loaded successfully

Menu Hotkey Binding Error
Run Hotkey Binding Error
```

Then a little bit later:

```
(usp:27461): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
```

---

### Post by Malac on 2008-08-18
> **Krydahl said:**
> Thanks for the response. The "Disable HotKey" checkbox is clear.

I get:

```
Using Standard Menu
places: loaded successfully
shortcuts: loaded successfully
applications: loaded successfully
system_management: loaded successfully

Menu Hotkey Binding Error
Run Hotkey Binding Error
```Then a little bit later:

```
(usp:27461): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
```

That suggests that the key is already assigned somewhere on your system. As a test try <Shift><Super>U and <Shift><Meta>U and see if either of those works.

If not, can you check that you have file _keybinder.so in /usr/lib/python2.4/site-packages/usp/plugins.
If you have then try manually copying the file from where you downloaded USP SVN then the sub folder '/usr/lib/python2.4/site-packages/usp/plugins' to main folder /usr/lib/python2.4/site-packages/usp/plugins.

If this still does not work try installing tomboy if it is not already installed.
```
sudo apt-get install tomboy
```

---

### Post by Krydahl on 2008-08-18
Tried a couple of key combinations (not <Shift><Meta>U because I'm not sure which key Meta is) but all give the same result:

```
Menu Hotkey Binding Error
Run Hotkey Binding Error

(usp:27942): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
Traceback (most recent call last):
  File "/usr/bin/usp", line 1110, in <module>
    gtk.main()
```

(That last bit may have been me hitting Ctl+C while trying to cut and paste from the terminal)

The file _keybinder.so does exist and I already have tomboy installed and do use it with no problems.

I'll try uninstalling and reinstalling, see if that helps.

---

### Post by Krydahl on 2008-08-18
Nope, tried a complete uninstall, deleted ~/.usp, reinstalled and still get:

```
Using Standard Menu
No User Picture Specified or File Not Found
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
No User Picture Specified or File Not Found
No User Picture Specified or File Not Found
Menu Hotkey Binding Error
Run Hotkey Binding Error

(usp:28518): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition

```

The Bonobo bit takes a couple of minutes before it shows up. Is that related at all, or something else entirely?

---

### Post by Malac on 2008-08-19
> **Krydahl said:**
> Nope, tried a complete uninstall, deleted ~/.usp, reinstalled and still get:

```
Using Standard Menu
No User Picture Specified or File Not Found
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
No User Picture Specified or File Not Found
No User Picture Specified or File Not Found
Menu Hotkey Binding Error
Run Hotkey Binding Error

(usp:28518): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition

```The Bonobo bit takes a couple of minutes before it shows up. Is that related at all, or something else entirely?
The Bonobo -WARNING is unrelated and has been present since USP 0.41 it does not cause any issues.

If it was a key in use then the error should come back as ```
** (usp:12470): WARNING **: Binding '<Shift>Super_L' failed!
``` with your key code in  the single quotes.

The error you're getting suggests it is the keybinder.so driver which is erroring.
I will keep trying to emulate this but have failed so far. I'll try getting some more info out of the bindkey function as to what is erroring.

I have attached a temporary usp which should hopefully report more error information.
Backup the one you have in /usr/bin and then extract replace it with the one in the attached tar file and run usp run-in-window.
Post the errors it reports.
Thanks.

---

### Post by Krydahl on 2008-08-19
OK, done. Gives:

```
Binding USP Menu to Hotkey: <Ctrl><Alt>U
Menu Hotkey Binding Error
Trying to Bind Key Combination :  <Ctrl><Alt>U
Error Report :
global name 'bindkey' is not defined

```

---

### Post by killerwhale65 on 2008-08-19
hello,

Whenever i switch from favorites to all applications, the applications widget becomes slightly wider, only to become smaller again when i switch back to favorites. This is probably because of some items with a long name, however they do not show completely in "all applications" anyway, so there is no need for the widget to become 20px wider, and thats rather annoying.

---

### Post by AJB2K3 on 2008-08-19
Sorry if this been covered but I haven't found the answer in 24 hrs.

How do I install the usp extras?
All I want is the places section.

---

### Post by Krydahl on 2008-08-19
Places doesn't require extras.

To get the places plugin working, right click on the USP icon and select preferences.

On the right hand side of the window you'll see a box labelled "plugins".

Click the "add" button to the right of that. In the popup that appears, use the drop down list to see all the possible plugins - you want 'places'. Click OK.

Use the up and down arrows to get the places plugin where you want it in the list of all plugins. (This will control where it appears in USP.) You may also want to add a new plane (click the button labelled that) as well, this will make places appear in its own column rather than underneath the plugin its underneath in the list.

When you're done, click the save button to the bottom right of the preferences window or your changes will be lost (this step is only necessary when changing which plugins you want to use).

---

### Post by rogerdean on 2008-08-19
best SLED-like menu i've found is pinched from Linux Mint - you can pick it up here

[http://www.linuxmint.com/repository/pool/daryna/m/mintmenu/mintmenu_3.2_i386.deb](http://www.linuxmint.com/repository/pool/daryna/m/mintmenu/mintmenu_3.2_i386.deb)

the icon is /usr/share/pixmaps/mintmenu.png so you can replace that with an ubuntu icon or whatever you like

---

### Post by AJB2K3 on 2008-08-19
> **Krydahl said:**
> Places doesn't require extras.

To get the places plugin working, right click on the USP icon and select preferences.

On the right hand side of the window you'll see a box labelled "plugins".

Click the "add" button to the right of that. In the popup that appears, use the drop down list to see all the possible plugins - you want 'places'. Click OK.

Use the up and down arrows to get the places plugin where you want it in the list of all plugins. (This will control where it appears in USP.) You may also want to add a new plane (click the button labelled that) as well, this will make places appear in its own column rather than underneath the plugin its underneath in the list.

When you're done, click the save button to the bottom right of the preferences window or your changes will be lost (this step is only necessary when changing which plugins you want to use).
Thanks, dunno what I was doing but whenever I click new, it just duplicated a previous option without the drop box.
Also How do I change the icon?

---

### Post by Malac on 2008-08-19
> **AJB2K3 said:**
> Thanks, dunno what I was doing but whenever I click new, it just duplicated a previous option without the drop box.
Also How do I change the icon?
Main USP icon is in Preferences 'Main' tab option 'USP Button Icon'
Each Plugin icon is under Preferences, then Tab with name of plugin second value down.

> **rogerdean said:**
> best SLED-like menu i've found is pinched from Linux Mint - you can pick it up here

[http://www.linuxmint.com/repository/pool/daryna/m/mintmenu/mintmenu_3.2_i386.deb](http://www.linuxmint.com/repository/pool/daryna/m/mintmenu/mintmenu_3.2_i386.deb)

the icon is /usr/share/pixmaps/mintmenu.png so you can replace that with an ubuntu icon or whatever you like
Actually mintMenu is "pinched" (your expression) from USP. Checkout mintMenu About Box.
The guys at Mint have done some great work with there version some of which has made it back into the Main USP too.

> **Krydahl said:**
> OK, done. Gives:

```
Binding USP Menu to Hotkey: <Ctrl><Alt>U
Menu Hotkey Binding Error
Trying to Bind Key Combination :  <Ctrl><Alt>U
Error Report :
global name 'bindkey' is not defined

```Krydahl this is definitely a driver file error.
Either:
The file is corrupt (can't see it after all the re-installs). Did you actually check that the /usr/lib/python2.4/site-packages/usp/plugins folder was deleted on uninstall?
OR:
It is using a different _keybinder.so file that is in your python path earlier than USP folders or it is an old _keybinder.so file.
OR:
The permissions on _keybinder.so are set incorrectly. They should be:
owned by root, readable by all, writeable by root only, _No_ execute permissions.
The /usr/lib/python2.4/site-packages/usp/plugins folder should be the same except with execute permissions for all.

**EDIT : Actually if any of these were the cause you should also receive: ```
*********** Keybind Driver Load Failure **************
``` in your usp run-in-window print out.** **Unless you didn't paste that bit.**

---

### Post by Krydahl on 2008-08-19
The permission look ok. No, I didn't think to check that the reinstall deleted the keybinder file, but I've just copied the downloaded version across and that didn't seem to change anything.

I don't know how to check the python path I'm afraid. A locate on the keybinder files shows I have:

/usr/lib/python-support/glipper/python2.5/glipper/keybinder/_keybinder.so
/usr/lib/python2.4/site-packages/deskbar/core/keybinder/_keybinder.so
/usr/lib/python2.4/site-packages/usp/plugins/_keybinder.so
/usr/lib/python2.5/site-packages/deskbar/core/keybinder/_keybinder.so
/var/lib/python-support/python2.5/glipper/keybinder/_keybinder.so

I'm definitely not seeing:

*********** Keybind Driver Load Failure **************

---

### Post by Malac on 2008-08-20
> **Krydahl said:**
> The permission look ok. No, I didn't think to check that the reinstall deleted the keybinder file, but I've just copied the downloaded version across and that didn't seem to change anything.
 
I don't know how to check the python path I'm afraid. A locate on the keybinder files shows I have:
 
/usr/lib/python-support/glipper/python2.5/glipper/keybinder/_keybinder.so
/usr/lib/python2.4/site-packages/deskbar/core/keybinder/_keybinder.so
/usr/lib/python2.4/site-packages/usp/plugins/_keybinder.so
/usr/lib/python2.5/site-packages/deskbar/core/keybinder/_keybinder.so
/var/lib/python-support/python2.5/glipper/keybinder/_keybinder.so
 
I'm definitely not seeing:
 
*********** Keybind Driver Load Failure **************
Okay that is suggesting that it is pulling in the wrong _keybinder.so file from one of the other locations. Not a scenario I had accounted for I'm afraid. 
Looks like it may be the glipper one but until I get home tonight I can't check this out so hang fire if you can until then and thanks for your patience with this. :)

---

### Post by darcio53 on 2008-08-20
I use usp rev341, here are my ideas, questions and noticed bugs. Thank you for USP ;-)

Bugs:
1. some .desktop files are still not working for example catfish.desktop for me - in gnome-panel's quick-lounge-applet the same desktop file works
2. sometimes bookmarks tab in places plugin doesn't show my favorites from nautilus - after reloading usp plugins they are present again
3. I have also problem with recent plugin - to see for example last 10 recent applications I have to choose in uspconfig 11 visible apps - last recent files doesn't have this bug
4. usp icon in gnome panel sometimes have a gtk theme colour when usp is not used and panel is in transparency mode
5. more applications button is not working for me
6. resources plugin shows in memory section nearly 100% used ram when system monitor shows 360MB/503MB

Ideas for usp:
1. 3 buttons like kbfx - normal, pressed, hoover
2. better displaying icons in rectangular shape - usp should automatic change it's gnome panel space to fit to rectangular icon
3. 2 or more columns in favorite applications section like in mintmenu
4. possibility to change in uspconfig if displayed are comments or generic names for programs
5. possibility to switch off comments and generic names under applications names to save space
6. to add in system management an option under Control Center for Gnome System Monitor or another task manager like in usp2
7. possibility to see usp favorites only with mouse over without pressing it
8. maybe change a location of favorites over all application section and add 7.
9. recently added/installed application section over all applications if possible
10. recently used applications also in applications plugin over all applications 

Questions:
1. why don't you add usp to gnome-files.erg website - more users, more testing, more popularity, more bugs reported
2. I don't see on your google usp site active issues or something like blueprints section - maybe you should add link to your launchpad usp section and start use it - just idea

Greetings

---

### Post by Malac on 2008-08-20
> **darcio53 said:**
> 1. some .desktop files are still not working for example catfish.desktop for me - in gnome-panel's quick-lounge-applet the same desktop file worksI will look into this.
 
> **darcio53 said:**
> 2. sometimes bookmarks tab in places plugin doesn't show my favorites from nautilus - after reloading usp plugins they are present againThis is a known bug that I am trying to catch.
 
> **darcio53 said:**
> 3. I have also problem with recent plugin - to see for example last 10 recent applications I have to choose in uspconfig 11 visible apps - last recent files doesn't have this bugNoted will look into this too
 
> **darcio53 said:**
> 4. usp icon in gnome panel sometimes have a gtk theme colour when usp is not used and panel is in transparency modeI have not tried this but will check it out.
 
> **darcio53 said:**
> 5. more applications button is not working for meLook into this.
 
> **darcio53 said:**
> 6. resources plugin shows in memory section nearly 100% used ram when system monitor shows 360MB/503MBResources shows reserved memory too sysmon shows active memory only but I will check if the difference can be shown in a different colour maybe.
 
> **darcio53 said:**
> 
 
Ideas for usp:
1. 3 buttons like kbfx - normal, pressed, hooverPossible> **darcio53 said:**
> 2. better displaying icons in rectangular shape - usp should automatic change it's gnome panel space to fit to rectangular iconWill look into this
 
> **darcio53 said:**
> 3. 2 or more columns in favorite applications section like in mintmenuAlready planned
 
> **darcio53 said:**
> 4. possibility to change in uspconfig if displayed are comments or generic names for programsAlready planned
 
> **darcio53 said:**
> 5. possibility to switch off comments and generic names under applications names to save spaceAlready planned
 
> **darcio53 said:**
> 6. to add in system management an option under Control Center for Gnome System Monitor or another task manager like in usp2Don't understand what you mean this can be done in usp when "Computer" button is clicked app launched can be changed in uspconfig.
 
> **darcio53 said:**
> 7. possibility to see usp favorites only with mouse over without pressing it.Possible
 
> **darcio53 said:**
> 8. maybe change a location of favorites over all application section and add 7.No, see 10 below
 
> **darcio53 said:**
> 9. recently added/installed application section over all applications if possibleThis would be a new plugin
 
> **darcio53 said:**
> 
10. recently used applications also in applications plugin over all applications
Put the recent apps plugin above applications accomplishes the same thing without changing the plugin for the majority of users
 
> **darcio53 said:**
>  
Questions:
1. why don't you add usp to gnome-files.erg website - more users, more testing, more popularity, more bugs reportedDone :)
 
> **darcio53 said:**
> 
2. I don't see on your google usp site active issues or something like blueprints section - maybe you should add link to your launchpad usp section and start use it - just ideaIssues can be started by anyone with a google code account. (I think).

---

### Post by darcio53 on 2008-08-20
6. to add in system management an option under Control Center for Gnome System Monitor or another task manager like in usp2


I mean that now system_management plugin has only 4 visible and configurable paths - one is Install Software - second is Control Center - third is Lock Screen and fourth is Quit. In my recent post I suggested to add fifth path for System Monitor like I saw in usp2 computer plugin, that's all

Greetings from Poland

---

### Post by darcio53 on 2008-08-20
Correction to last post... I mean it was system management plugin for usp2 not computer plugin, sorry

---

### Post by killerwhale65 on 2008-08-21
new bug: some applications do not start from USP, but do start from the main menu. This is the case for Brasero and xampp control panel. This affects favorites, as well as the regular applications list.

---

### Post by Malac on 2008-08-21
> **killerwhale65 said:**
> new bug: some applications do not start from USP, but do start from the main menu. This is the case for Brasero and xampp control panel. This affects favorites, as well as the regular applications list.
Old bug re-surfacing. :(
Thanks for the report. I am considering trying a complete revamp of the launch system as there are a few .desktop files that are not working with USP which is no use even if it is only a few it is annoying to users.

---

### Post by Malac on 2008-08-22
> **darcio53 said:**
> Correction to last post... I mean it was system management plugin for usp2 not computer plugin, sorry
That was Quikee's re-code of USP. This is in the SVN under usp2 sub-folder it can be installed following the instructions on the forum.
 
Hope this helps.

---

### Post by zniavre on 2008-08-24
hello , bonjour 

i re-installed USP yesterday after a year of non using it 

i works quite well bravo for improvement

i remember i could use terminal/note and ressource plugins but now i can't find the way to enable them into the plugins popup 
i extracted them into ~/.usp/plugins and ~/.usp  but it seems to does not work 

what i did wrong ?

hope usp3 will come soon   :o)


see you , au revoir

---

### Post by Malac on 2008-08-24
> **zniavre said:**
> hello , bonjour 

i re-installed USP yesterday after a year of non using it 

i works quite well bravo for improvement

i remember i could use terminal/note and ressource plugins but now i can't find the way to enable them into the plugins popup 
i extracted them into ~/.usp/plugins and ~/.usp  but it seems to does not work 

what i did wrong ?

hope usp3 will come soon   :o)


see you , au revoir
You will have to logout and back in again for USP to register the addition of the ~/.usp/plugin files.

If this does not work then enter:
```
gksu nautilus
``` into the usp applications box and hit enter.
Choose this folder in the SVN folder you created:
[ATTACH]82652[/ATTACH]
Make a link from the right-click menu:
[ATTACH]82653[/ATTACH]
Then rename the link file "plugins":
[ATTACH]82654[/ATTACH]
Then move that renamed link to ~/.usp

This method means that any updates to the SVN extra plugins are picked up.

Hope this helps.

---

### Post by Malac on 2008-08-26
I have tried a slight reworking of applications.py/recent.py/execute.py launch method can people who have had problems launching apps, such as brasero, et al, try these files instead and report results.(Attached below).

**These are experimental files so please backup the original ones in case they cause errors and you want to revert.**

Thanks in advance.

---

### Post by darcio53 on 2008-08-27
Hello again, on the page 93 I wrote about some bugs, suggestions and ideas for usp. Now it is time for the second part.
Bugs:
1. I wrote in my last post that I've seen the usp icon bug in gnome-panel transparency mode. The bug is active in usp mode Open/close menu on mouse over when I choose an application from usp to start. If I do not choose any application to start and I put mouse over usp icon again the icon becomes transparent like it should. The problem with gnome-panel usp menu icon transparency is only present with option Open/close menu on mouse over. See the picture below.

[http://picasaweb.google.com/pipaceliny/Usp/photo#5239137890009778002](http://picasaweb.google.com/pipaceliny/Usp/photo#5239137890009778002)

2. I also wrote earlier that I've noticed a bug in recent plugin (applications only). For example to see 9 recent applications I had to put 10 i uspconfig recent tab. Today I think it is connected with uninstalling applications. When I choose an application to start and after it is present in usp recent applications and then uninstall this app via package manager I have an empty place for this uninstalled app. This empty place in recent apps is still visible in usp after restart even when I choose new applications from usp applications menu. So this made me to put 10 in uspconfig to see 9 ;-)
3. I've noticed something like a bug in computer plugin. Screen resolution in usp was empty after installation of usp. I chose gnome-display-properties through usp computer plugin, set again the same resolution of my screen and refresh rate and now Screen resolution shows right 1280x1024 resolution but refresh rate is 0 Hz? what do you think about it?
4. I also had a problem with uspconfig option restrict from sending to side pane for template plugin (this option for template plugin is not working). I had to run gconf-editor and check this option in gconf to made it work.
5. After fresh installation of usp computer plugin has not working button Control Center because of gcontrol than gnome-control-center in uspconfig by default.

Ideas:
1. Maybe add upsconfig.desktop to be uspconfig accessible through gnome-control-center.
2. Add Reload Plugins button in uspconfig? over reset button in Main section of uspconfig?
3. Mintmenu after installation is integrated with compiz-fusion effects and has a transparency, what about it?
4. Maybe ubuntu launchpad ppa repo in the future?
5. Maybe a screenshot of usp on your google usp site?
6. And a silly suggestion to change favorites applications icon to something like emblem-favorite.png/emblem-favorite.svg?
7. Like I wrote earlier usp has problem with rectangular icons. Screenshot below.

[http://picasaweb.google.com/pipaceliny/Usp/photo#5239143193870576402](http://picasaweb.google.com/pipaceliny/Usp/photo#5239143193870576402)

8. Recently my mockup of applications plugin, see the picture below - I know I repeat myself ;-)

[http://picasaweb.google.com/pipaceliny/Usp/photo#5239137894628146546](http://picasaweb.google.com/pipaceliny/Usp/photo#5239137894628146546)

Thanks for your attention.

---

### Post by Malac on 2008-08-27
> **darcio53 said:**
> Hello again, on the page 93 I wrote about some bugs, suggestions and ideas for usp. Now it is time for the second part.
Bugs:
1. I wrote in my last post that I've seen the usp icon bug in gnome-panel transparency mode. The bug is active in usp mode Open/close menu on mouse over when I choose an application from usp to start. If I do not choose any application to start and I put mouse over usp icon again the icon becomes transparent like it should. The problem with gnome-panel usp menu icon transparency is only present with option Open/close menu on mouse over. See the picture below.
 
[http://picasaweb.google.com/pipaceliny/Usp/photo#5239137890009778002](http://picasaweb.google.com/pipaceliny/Usp/photo#5239137890009778002)
 
2. I also wrote earlier that I've noticed a bug in recent plugin (applications only). For example to see 9 recent applications I had to put 10 i uspconfig recent tab. Today I think it is connected with uninstalling applications. When I choose an application to start and after it is present in usp recent applications and then uninstall this app via package manager I have an empty place for this uninstalled app. This empty place in recent apps is still visible in usp after restart even when I choose new applications from usp applications menu. So this made me to put 10 in uspconfig to see 9 ;-)
3. I've noticed something like a bug in computer plugin. Screen resolution in usp was empty after installation of usp. I chose gnome-display-properties through usp computer plugin, set again the same resolution of my screen and refresh rate and now Screen resolution shows right 1280x1024 resolution but refresh rate is 0 Hz? what do you think about it?
4. I also had a problem with uspconfig option restrict from sending to side pane for template plugin (this option for template plugin is not working). I had to run gconf-editor and check this option in gconf to made it work.
5. After fresh installation of usp computer plugin has not working button Control Center because of gcontrol than gnome-control-center in uspconfig by default.
 
Ideas:
1. Maybe add upsconfig.desktop to be uspconfig accessible through gnome-control-center.
2. Add Reload Plugins button in uspconfig? over reset button in Main section of uspconfig?
3. Mintmenu after installation is integrated with compiz-fusion effects and has a transparency, what about it?
4. Maybe ubuntu launchpad ppa repo in the future?
5. Maybe a screenshot of usp on your google usp site?
6. And a silly suggestion to change favorites applications icon to something like emblem-favorite.png/emblem-favorite.svg?
7. Like I wrote earlier usp has problem with rectangular icons. Screenshot below.
 
[http://picasaweb.google.com/pipaceliny/Usp/photo#5239143193870576402](http://picasaweb.google.com/pipaceliny/Usp/photo#5239143193870576402)
 
8. Recently my mockup of applications plugin, see the picture below - I know I repeat myself ;-)
 
[http://picasaweb.google.com/pipaceliny/Usp/photo#5239137894628146546](http://picasaweb.google.com/pipaceliny/Usp/photo#5239137894628146546)
 
Thanks for your attention.
Some of the bugs have been fixed in the latest SVN please run ```
./usp_update update 
``` from the folder you downloaded USP SVN to.
 
The open on mouse over is a recent patch and it was likely to throw up some strange behaviour. I will check this out to find the cause.
 
The Screen Resolution issue is caused by GNOME/XORG redoing the way resolution is stored/reported. The Hz is now not reported and the size has to be found in another way, this part should now work. The Hz part may have to be removed as I have yet to find a reliable way of getting this info. from GNOME/XORG.
 
gcontrol was removed from computer and system_management plugins a while back and replaced with gnome-control-center, if the gconf key still showed the old setting then a new install would still pick this old setting up.
 
The others I will get to when I can find the time.
 
Thanks for reporting these. :)

---

### Post by EnigMattic on 2008-08-28
Hi

I was wondering if there's a way to set a 'USP Button Icon' of an irregular shape and if not, could I request this feature for a future release?

I would like to (effectively) skin the Button with the following image:

[IMG]http://img166.imageshack.us/img166/3130/startbutton24db2.png[/IMG]

It is 70x24 pix and the panel I wish to add it to has a height of 24 too.

Currently, when I try and use it, I get this:

[IMG]http://img136.imageshack.us/img136/2451/screenshotzd1.png[/IMG]

Is there a way to make this work?

Cheers!

---

### Post by Krydahl on 2008-08-28
Hi Malac - did you have any luck nailing that hotkey binding bug?

---

### Post by Malac on 2008-08-28
> **Krydahl said:**
> Hi Malac - did you have any luck nailing that hotkey binding bug?
Yes it looks like it is using the glipper keybinder.so file. This could come up again with another app so I have decided to compile my own uspbinder but have run into a few probs but I am on the case.

---

### Post by Krydahl on 2008-08-28
OK, thanks.

---

### Post by Malac on 2008-08-30
> **Krydahl said:**
> OK, thanks.
Sorry Krydahl, I have installed/activated glipper and deskbar and I cannot re-create this bug. USP still loads and uses the correct bindings on my system. I even created a new install on another machine installing glipper and deskbar first then USP but to no avail.

I can only assume this is specific to your system in some way.

This is the relevant line #32 in /usr/bin/usp
```
    from _keybinder import tomboy_keybinder_bind as bindkey
```The process is loading the driver otherwise it should report one of the following:
_Driver not where it should be_```
*********** Keybind Driver Load Failure **************
Error Report :  No module named _keybinder
```_Different format driver file_```
*********** Keybind Driver Load Failure **************
Error Report :  cannot import name tomboy_keybinder_bind
```You are getting the error
```
** WARNING ** - Menu Hotkey Binding Error
Error Report : global name 'bindkey' is not defined
```Unless somehow bindkey from another app is in scope, and I don't see how, this should not be happening.
In a last attempt I have renamed the alias to uspbindkey in the latest SVN update Rev #344
Please update to this and try again.

---

### Post by Krydahl on 2008-08-30
I'm still getting the same error with 344, "global name 'uspbindkey' is not defined".

Interestingly, I've tried this with my laptop installation and it also gives me that error - which rules out glipper because I've never installed it on that machine. It does have the the deskbar applet on it (though I don't recall adding it, so guess it's part of the default installation).

I've also tried completely removing both the deskbar and glipper so that locate now reports:

```
locate _keybinder.so
/home/al/downloads/SVN/ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/_keybinder.so
/home/al/downloads/SVN/ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/.svn/prop-base/_keybinder.so.svn-base
/home/al/downloads/SVN/ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/.svn/text-base/_keybinder.so.svn-base
/usr/lib/python2.4/site-packages/usp/plugins/_keybinder.so
```

and am still seeing the same bug.

Don't know what to try next. I may just have to live without a keyboard shortcut.

---

### Post by Malac on 2008-08-31
This is my last idea Krydahl, try Rev #345

---

### Post by Krydahl on 2008-08-31
Still doesn't work, but I may have some extra info. It now says:

```
$ usp run-in-window
*********** Keybind Driver Load Failure **************
Error Report :  /usr/lib/python2.4/site-packages/usp/plugins/_keybinder.so: wrong ELF class: ELFCLASS32
Using Standard Menu
places: loaded successfully
shortcuts: loaded successfully
applications: loaded successfully
system_management: loaded successfully
Binding USP Menu to Hotkey: <Ctrl><Alt>U
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'uspbindkey' is not defined

```

I don't recall seeing that bit about the ELF class at the top before.

---

### Post by smartboyathome on 2008-08-31
Ah, your running 64 bit? If so, this is installing as 32 bit, and thinks that everything is 32 bit. Since the ELF class on 64 bit systems is ELFCLASS64, and it is looking for ELFCLASS32, it will not work.

---

### Post by Krydahl on 2008-08-31
Ah - excellent! 

How do I fix this? Sorry, not much clue about python. Do I need Malac to put together a version that uses 64bit libraries or can I fix it myself somehow?

---

### Post by smartboyathome on 2008-08-31
You have to compile it from source manually. See the google projects page.

---

### Post by Malac on 2008-09-01
Sorry Krydahl I should have looked at you sig.

" AMD X2 4200+. Running **64 bit** Hardy with Compiz" #-o

I'll get on it tonight.

---

### Post by Krydahl on 2008-09-01
> **Malac said:**
> Sorry Krydahl I should have looked at you sig.

" AMD X2 4200+. Running **64 bit** Hardy with Compiz" #-o

I'll get on it tonight.

Hey, no worries. Thanks for all the time you've put into this one.

---

### Post by Mazza558 on 2008-09-01
Hey,

I'm trying to save a custom set of settings for USP so I can share with other people (one of the most common problems with USP seems to be its default layout), but I'm finding that I can only backup the layout and not the icons/shortcuts etc. This problem is made worse by the fact that USP doesn't seem to recognise "~/" as referring to a home directory. Therefore, If I backup my settings and share them with other people, it won't work as all the shortcuts point to literally my home directory (e.g /home/<name>/.usp/shortcuts) when it should be "~/.usp/shortcuts/", which would enable me to write a script to add these shortcuts to the .usp directory for other people (if that would even work).

I guess what I'm asking for is some kind of backup for all settings in a way that lets me share them easily with other people, meaning all they would need to do is click "restore" in their USP settings to get an identical menu to mine.

---

### Post by Malac on 2008-09-01
@Krydahl
Can you try this for me:
Update to latest SVN Rev# 350
Then run 
```
sudo cp /usr/lib/python2.4/site-packages/usp/plugins/_keybind64.so _keybinder.so
```**NB***If this works, you will need to run this after every update until I get the .debs sorted.

> **Mazza558 said:**
> Hey,

I'm trying to save a custom set of settings for USP so I can share with other people (one of the most common problems with USP seems to be its default layout), but I'm finding that I can only backup the layout and not the icons/shortcuts etc. This problem is made worse by the fact that USP doesn't seem to recognise "~/" as referring to a home directory. Therefore, If I backup my settings and share them with other people, it won't work as all the shortcuts point to literally my home directory (e.g /home/<name>/.usp/shortcuts) when it should be "~/.usp/shortcuts/", which would enable me to write a script to add these shortcuts to the .usp directory for other people (if that would even work).

I guess what I'm asking for is some kind of backup for all settings in a way that lets me share them easily with other people, meaning all they would need to do is click "restore" in their USP settings to get an identical menu to mine.
This is a throw back to chanders naming convention for the files in the .usp directory.

**_EDIT:_**
Okay tried this and it works.
You should be able to copy your ~/.usp folder into their home folder in it's entirety whilst usp isn't running, all other settings (i.e. non-gconf) are stored in there.
Then run :```
sudo chown -hR [COLOR=Gray]*<USERNAME>*[/COLOR]:[COLOR=Gray]*<USERGROUP>*[/COLOR] ~/.usp
```replacing [COLOR=Gray]*<USERNAME>*[/COLOR]:[COLOR=Gray]*<USERGROUP> *[/COLOR]with their user name and group.
Then run uspconfig restore the backup settings.
Delete bookmarks file entry if you use the internet plugin.
The compact list will be a problem if you have personalised shortcuts in that.
bookmarks are the .gtk-bookmarks file in home folder.
That's it you should be good to go.

Hope this helps.

---

### Post by zniavre on 2008-09-03
sorry to answer so late.

malac,  all plugs (allmost all of theme) are working it 's quite nice


big thank again

i keep in touch with USP and can't wait for USP3...

good bye / au revoir et merci

---

### Post by Malac on 2008-09-03
> **zniavre said:**
> sorry to answer so late.
 
malac, all plugs (allmost all of theme) are working it 's quite nice
 
 
big thank again
 
i keep in touch with USP and can't wait for USP3...
 
good bye / au revoir et merci
 Bon chance :)

---

### Post by Krydahl on 2008-09-04
Hi Malac, sorry to take so long getting back to you, I missed your post somehow.

I tried it and it didn't work, but it may just be your instructions that are at fault. Where do you want the _keybind64.so file copied and renamed to? I took you literally. You said do an update (which requires a cd into my usp download directory) and then copy the file. So this put the renamed file into my usp download directory. Seemed unlikely and I wasn't surprised when it didn't work.

Then I tried renaming the 64 bit file to the standard one in /usr/lib/python2.4/site-packages/usp/plugins/

This resulted in the following error message:
```
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
```

I don't know it that's a problem with your 64 bit version or just that I've put the file in the wrong place. Let me know what to try next.

---

### Post by Malac on 2008-09-04
> **Krydahl said:**
> Hi Malac, sorry to take so long getting back to you, I missed your post somehow.
 
I tried it and it didn't work, but it may just be your instructions that are at fault. Where do you want the _keybind64.so file copied and renamed to? I took you literally. You said do an update (which requires a cd into my usp download directory) and then copy the file. So this put the renamed file into my usp download directory. Seemed unlikely and I wasn't surprised when it didn't work.
 
Then I tried renaming the 64 bit file to the standard one in /usr/lib/python2.4/site-packages/usp/plugins/
 
This resulted in the following error message:
```
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
```
 
I don't know it that's a problem with your 64 bit version or just that I've put the file in the wrong place. Let me know what to try next.
Okay this seems to show you're missing some GNOME stuff.
libgnome-desktop-2 should be already installed by default.

---

### Post by Krydahl on 2008-09-04
Yes, I just checked. It **is** installed on my system.

Is the keybinder driver looking in the wrong place because 64 and 32 paths are different maybe?

---

### Post by Malac on 2008-09-05
> **Krydahl said:**
> Yes, I just checked. It **is** installed on my system.

Is the keybinder driver looking in the wrong place because 64 and 32 paths are different maybe?

Unless your own paths are screwed up but then I'd expect other stuff not to work.
Sorry, I don't have a 64-bit machine so can not test this stuff myself.

Should of thought of this before but wasn't thinking.
Try copying the one from :
/usr/lib/python2.4/site-packages/deskbar/core/keybinder/_keybinder.so
to :
/usr/lib/python2.4/site-packages/usp/plugins/_keybinder.so
see if that works, it should be the same file.

Else:
Try each of the ones in the attached file and see if any of them work then note the number down.

Thanks for the testing. :)

---

### Post by Krydahl on 2008-09-05
Will do, but today's going to be a bit hectic. It will probably have to wait for the weekend.

---

### Post by nulall on 2008-09-20
sorry if this is a stupid question, but is there anywhere to get a relatively recent .deb file as opposed to using SVN?  i'd love to have a PPA or some kind of repository to subscribe to that would minimize the work in installing this awesome applet and would auto-update for me.

---

### Post by Malac on 2008-09-21
> **nulall said:**
> sorry if this is a stupid question, but is there anywhere to get a relatively recent .deb file as opposed to using SVN?  i'd love to have a PPA or some kind of repository to subscribe to that would minimize the work in installing this awesome applet and would auto-update for me.
I am going to be doing a .deb package just as soon as I can get to it, probably the end of next week now.
I will try to set up a launchpad repo so that it can be installed through synaptic / apt-get / aptitude as soon as possible after that.

Hope this helps.

---

### Post by nulall on 2008-09-21
That's awesome.
In the meanwhile, I looked into USP a bit more and decided it was worth the time. I love it. Keep up the great work. I can't wait to see this as the default Ubuntu menu (I'm guessing not until "Jaunty Jackalope").

---

### Post by nulall on 2008-09-23
is there any way too adjust the transparency of USP? it's a little too see-through for my liking...

---

### Post by Malac on 2008-09-23
> **nulall said:**
> is there any way too adjust the transparency of USP? it's a little too see-through for my liking...I think in compiz fusion if you hold the mouse over the open menu, press the shift key then use the mouse scroll wheel to adjust it.

---

### Post by delfick on 2008-09-23
> **Malac said:**
> I think in compiz fusion if you hold the mouse over the open menu, press the shift key then use the mouse scroll wheel to adjust it.

actually, it's alt :)

though depending on what version of compiz you're running, that may not be true, and/or enabled.

if that still doesn't solve your problem, then either the [compiz-fusion irc channel](irc://irc.freenode.net/compiz-fusion) or [http://forum.compiz-fusion.org](http://forum.compiz-fusion.org) may help :)

---

### Post by Malac on 2008-09-23
> **delfick said:**
> actually, it's alt :)

though depending on what version of compiz you're running, that may not be true, and/or enabled.

if that still doesn't solve your problem, then either the [compiz-fusion irc channel](irc://irc.freenode.net/compiz-fusion) or [http://forum.compiz-fusion.org](http://forum.compiz-fusion.org) may help :)
Cheers delfick not on ubuntu at the mo'. I'm working on Windows at the mo. :(

---

### Post by Krydahl on 2008-09-23
> **delfick said:**
> actually, it's alt :)

though depending on what version of compiz you're running, that may not be true, and/or enabled.

if that still doesn't solve your problem, then either the [compiz-fusion irc channel](irc://irc.freenode.net/compiz-fusion) or [http://forum.compiz-fusion.org](http://forum.compiz-fusion.org) may help :)

The trouble with this solution is you'll have to change the transparency each time you open USP.

Better:

Open Advanced Desktop Effects.

Select General Options.

Go to the Opacity Settings tab.

In Windows opacities, add, then in the popup box, type:
```
name=usp
```
and set the opacity to whatever suits you. Your USP menu will now always appear at this level of transparency. Obviously, you can do this for other types of window too, you just have to figure out how to uniquely identify the window you want. You can discover this using xprop. See this guide:

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

for more.

---

### Post by nulall on 2008-09-23
> **Malac said:**
> I think in compiz fusion if you hold the mouse over the open menu, press the shift key then use the mouse scroll wheel to adjust it.

wow. it really was that simple (though it's alt for me, not shift). i just never really use that feature and didn't even realize that i could make things LESS transparent if they already started out somewhat see-through. sigh. wasted way too much time googling and poking around gconf for nothing...

---

### Post by delfick on 2008-09-23
> **Malac said:**
> Cheers delfick not on ubuntu at the mo'. I'm working on Windows at the mo. :(

damn....

good luck with that :) :p

---

### Post by delfick on 2008-09-23
> **Krydahl said:**
> The trouble with this solution is you'll have to change the transparency each time you open USP.

Better:

Open Advanced Desktop Effects.

Select General Options.

Go to the Opacity Settings tab.


very true :)

however, depends on version of compiz-fusion :)

(latest version, that has been moved to another plugin, along with brightness and saturation)

---

### Post by Krydahl on 2008-09-24
> **delfick said:**
> very true :)

however, depends on version of compiz-fusion :)

(latest version, that has been moved to another plugin, along with brightness and saturation)

Yeah, I'm afraid I don't keep up with compiz. I'm running off the launchpad compiz repository for Hardy main. It still seems to be in general options in that. I keep thinking about getting into compiling my own, 'cause I'd really like the True ARGB (Color-Keyed Partial Window Transparency) plugin, but I can't find the time necessary to set it all up at the moment. Since I don't even know where to start, I'd have to do a fair bit of background reading.

---

### Post by darcio53 on 2008-10-06
Hello again I have a suggestion. 

I noticed that usp plugin recent has no problem with .desktop files containing for example "Icon=ghex" or "Icon=ghex.png" but usp plugin applications has. Ghex.desktop file has a Icon=ghex and in applications menu in usp has no icon while in recent plugin it has the icon. 

Maybe fix this? ;)

Thanks

---

### Post by Malac on 2008-10-06
> **darcio53 said:**
> Hello again I have a suggestion. 

I noticed that usp plugin recent has no problem with .desktop files containing for example "Icon=ghex" or "Icon=ghex.png" but usp plugin applications has. Ghex.desktop file has a Icon=ghex and in applications menu in usp has no icon while in recent plugin it has the icon. 

Maybe fix this? ;)

Thanks
Thanks for pointing this out. I'll get right on it tomorrow if I can.

---

### Post by darcio53 on 2008-10-08
Hello

I noticed something again ;-). Few days ago I installed wine. I usp menu appeared new section Wine with subsection Programs. When I enter the subsection Programs in section Wine I have problem with going back pressing green arrow (I add a screenshot). Maybe fix this too?


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87723&stc=1&d=1223503632[/IMG]

Ps. New usp rev356 fixed the icon problem in desktop file, thank you!

---

### Post by Malac on 2008-10-09
> **darcio53 said:**
> When I enter the subsection Programs in section Wine I have problem with going back pressing green arrow.....
I'll try and look at this at the weekend.
> **darcio53 said:**
> Ps. New usp rev356 fixed the icon problem in desktop file, thank you!
You're Welcome.

---

### Post by Malac on 2008-10-12
hi darcio53,
I can't seem to replicate this.
When you click the Wine category button this is the sort of thing you should get, 
[ATTACH]88098[/ATTACH]
The Back button should not appear until you press Programs.
Once that Back button is pressed you should get the normal All Applications Menu.

Does this happen all the time or is there a set of button presses that triggers it specifically?
Is your Wine folder a sub-folder itself?

---

### Post by schmolch on 2008-10-18
Followed the install instructions from subversion but the applet does not react to anything.

update: 10m later it works but most of the window is outside the screen-area.

---

### Post by Malac on 2008-10-18
> **schmolch said:**
> Followed the install instructions from subversion but the applet does not react to anything.

update: 10m later it works but most of the window is outside the screen-area.
Sorry you have had a problem.
You may have too many plugins for your screen resolution.
Right-click the applet button and choose Preferences OR:
Open a terminal and run uspconfig
Remove/re-order/resize the plugins to fit your screen.
If you have a low resolution you might consider using the newtab option to create tabs for just a couple of plugins at a time. See the wiki page for help on this. [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

If you have the applet in the middle of the panel then it sometimes will show off screen.
It is usually best to have it positioned on the far left or far right of the panel.

Hope this helps.

P.S.
If none of these help, please post a screenshot and your screen resolution plus, if you could, a backup of your settings using the Backup button in Preferences and I will try to help.

---

### Post by schmolch on 2008-10-18
> **Malac said:**
> 
If you have the applet in the middle of the panel then it sometimes will show off screen.
It is usually best to have it positioned on the far left or far right of the panel.

That was it, putting it left works better. Thx.

---

### Post by Malac on 2008-10-18
> **schmolch said:**
> That was it, putting it left works better. Thx.
You're Welcome. Glad it's resolved.
Think I'll take a look at this as it should really be able to cope better with this situation.

---

### Post by Malac on 2008-10-19
Okay have changed code to allow for applet button in the middle of the taskbar.
The menu will appear aligned to the left of screen rather than aligned to the button in this instance. SVN Rev# 361

---

### Post by darcio53 on 2008-10-23
Hello dear Malac ;-)

I was out of my home. 

Here is my problem in few words. When I enter the subsection Programs in Wine category and then subsection Accessories in Programs I can go back (pushing the back button) to Programs and to view of content of Wine section but the problem is that the other usp2
sections of gnome menu (Accessories, Office, Graphics, Wine, etc) are not visible. They should be visible in the part of usp where is the back button.

When I reload the usp or install a new application with desktop file the usp applications plugin reloads and the gnome menu categories are again visible.

[http://ubuntuforums.org/attachment.php?attachmentid=89355&stc=1&d=1224751283](http://ubuntuforums.org/attachment.php?attachmentid=89355&stc=1&d=1224751283)

The problem is still present in usp rev362.

By the way it was a great idea to add to usp 'add to Desktop' for .desktop files. Thanks

Darek

---

### Post by Dragonlaw on 2008-10-27
Hello,

I just had this problem. I accidentally deleted the old icons from the Favourites slab in USP, and when I try to put them back again it does not appear. However, if I put in new programs I will see them on the Favourite Slab. 

I already tried right clicking the program, pressing add to favourites. But the programs do not appear.

Could anyone help me?

Thanks in advance.

---

### Post by Malac on 2008-10-28
> **Dragonlaw said:**
> Hello,

I just had this problem. I accidentally deleted the old icons from the Favourites slab in USP, and when I try to put them back again it does not appear. However, if I put in new programs I will see them on the Favourite Slab. 

I already tried right clicking the program, pressing add to favourites. But the programs do not appear.

Could anyone help me?

Thanks in advance.
Try opening a terminal and running ```
usp run-in-window
``` then using the button created open that menu and try adding to favourites from that it should print out a message saying:> Application added - /home/*<yourusername>*/.usp/applications/XXXXXXXXXXX.desktop
Added to .usp/applications.list
If this says:>  File Exists!
Then you can try deleting the /home/*<yourusername>*/.usp/applications.list file and /home/*<yourusername>*/.usp/applications folder and starting again.

Hope this helps.

---

### Post by darcio53 on 2008-11-07
Hello Malac

1.I've installed ubuntu 8.10 and 'Add to Desktop' option is not working. Usp r369. Maybe it's because of Desktop folder name change? My Desktop folder is now called in polish Pulpit. 
Please fix this.

2.It would be great to have in usp an option 'Add to Autostart' to put application's .desktop file to /home/user/.config/autostart

Thanks
Darek

---

### Post by Malac on 2008-11-08
> **darcio53 said:**
> Hello Malac

1.I've installed ubuntu 8.10 and 'Add to Desktop' option is not working. Usp r369. Maybe it's because of Desktop folder name change? My Desktop folder is now called in polish Pulpit. 
Please fix this.

2.It would be great to have in usp an option 'Add to Autostart' to put application's .desktop file to /home/user/.config/autostart

Thanks
Darek
I'm going out tonight but I will get on these tomorrow(Sunday). :)

---

### Post by Malac on 2008-11-09
Okay darcio53 all done SVN Rev #371
gconf key /apps/usp/applications/alt_Desktop_loc  (Must be full path .e.g. /home/user/Documents)
or through uspconfig/Preferences, Applications Tab
'Add to Autostart' added to right-click menu also.

---

### Post by darcio53 on 2008-11-09
Dear Mallac

Add to Desktop works!
Add to Autostart works! :-)

You're Great!!!!
Thanks

---

### Post by Malac on 2008-11-10
> **darcio53 said:**
> Dear Mallac

Add to Desktop works!
Add to Autostart works! :-)

You're Great!!!!
Thanks
You're Welcome :D

---

### Post by darcio53 on 2008-11-24
Hello Dear Mallac ;-)

I noticed something in usp2. I have to use onboard onscreen keyboard.
Usp plugin applications have no problem with svg icon pointed in onboard.desktop file but the recent plugin has. There is no icon visible in recent plugin if there is svg pointed. Only the name without icon.
Maybe fix?

Bye
Darek

---

### Post by Malac on 2008-11-25
> **darcio53 said:**
> Hello Dear Mallac ;-)

I noticed something in usp2. I have to use onboard onscreen keyboard.
Usp plugin applications have no problem with svg icon pointed in onboard.desktop file but the recent plugin has. There is no icon visible in recent plugin if there is svg pointed. Only the name without icon.
Maybe fix?

Bye
Darek
I haven't had any time to look at this in depth yet but I will.
Which version are you using as you can see from the attached screenshot in the latest SVN (#374) on my machine it shows up fine?
[ATTACH]94174[/ATTACH]
Are you using a theme which doesn't have a full icon set for OnBoard?

---

### Post by darcio53 on 2008-11-26
Hello Malac

I am using the latest SVN (#374).

Gtk theme Human, icons Human.

Fresh install of Intrepid (new laptop - no old gconf options), fresh install of Usp2 since svn #370

Bye

---

### Post by darcio53 on 2008-11-26
Hello again Malac

I opened onboard.desktop with gedit and realized that there is  this entry:
Icon = /usr/share/onboard/data/onboard.svg
after changing it to
Icon=/usr/share/onboard/data/onboard.svg
everything works.

So it is more problem of this desktop file than usp2.
Sorry for troubling You.

Darek

---

### Post by Malac on 2008-11-26
> **darcio53 said:**
> Hello again Malac

I opened onboard.desktop with gedit and realized that there is  this entry:
Icon = /usr/share/onboard/data/onboard.svg
after changing it to
Icon=/usr/share/onboard/data/onboard.svg
everything works.

So it is more problem of this desktop file than usp2.
Sorry for troubling You.

Darek
Thanks for finding the problem Darek. I'll do a fix for this kind of thing anyway as USP should be able to handle a simple thing like spaces.

---

### Post by santiagoward2000 on 2008-11-29
Hi!
I have a small question. I've added some apps to the Compact List, but now I want to remove them. How can I do this?
Thanks!

_EDIT:_
Oops! I just saw the "Compact List" tab in preferences... Done.
Sorry!

---

### Post by darcio53 on 2008-12-03
Hello Malac

I again have a problem. This time it's a big one ;-).
Few days ago my usp stopped working. It freezes after choosing any application to start. I logged to another user available on my computer and added usp2 to gnome-panel and it works. So the problem is in my home folder. I run usp in window and I've got something like this:

darek@darek-ubuntuos:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
applications: loaded successfully
recent: loaded successfully
system_management: loaded successfully
places: loaded successfully
shortcuts: loaded successfully
Static User Image Used
uspuser: loaded successfully
computer: loaded successfully
resources: loaded successfully
calculator: loaded successfully
uspcalendar: loaded successfully
remind: loaded successfully
notes: loaded successfully
internet: loaded successfully
usptime: loaded successfully
tracker: loaded successfully
terminal: loaded successfully
Static User Image Used
Static User Image Used
Binding USP Menu to Hotkey: <Ctrl><Alt>U
darek@darek-ubuntuos:~$ 

This ends with freeze after choosing any application to start.

In the same time I noticed that ubuntu-tweak also has 'the same' problem. It like usp2 loads with no problem when I login into the other account on my laptop, but on my default account crashes with this output:

darek@darek-ubuntuos:~$ ubuntu-tweak
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Segmentation fault
darek@darek-ubuntuos:~$ 

It has started in the same time after installing of some updates I think. A python problem, or gconf?

Any suggestions?

Please help ;-)

---

### Post by darcio53 on 2008-12-25
Well problem is solved. I removed .face file from my home folder and usp2 is again working. Don't know why it blocked usp. Maybe I edited face icon with other program to set user face in gnome...
Bye

---

### Post by Malac on 2009-01-04
> **darcio53 said:**
> Well problem is solved. I removed .face file from my home folder and usp2 is again working. Don't know why it blocked usp. Maybe I edited face icon with other program to set user face in gnome...
Bye
Glad it was solved, I can only think the file was corrupt somehow and caused this. I think it must have been loading the image okay so was passing the USP error checks as I put in checks for .face files missing, etc. but the failure must have been deeper down in the underlying gtk.Image handling this is suggested by the error message.

---

### Post by SorinN on 2009-01-20
I can't start usp at all today (20 Ian 2009).
I just uninstalled previous versions, removed .usp folder in /home/userland folder and I do a fresh install from SVN (r374). 

No chance to start from gnome-panel then I tried to ..run-in-window. 
Here is the output ( btw. I have Ubuntu 8.10 up to date ):

sorin@SQ2:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
No User Picture Specified or File Not Found
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: ERROR - [Errno 2] No such file or directory: '/home/sorin/.usp/recentapps.list'
New Pane
Directory created
Icon 'web_browser.png' not found, using gtk-file instead.
Icon 'audio_player.png' not found, using gtk-file instead.
Icon 'xterm.png' not found, using gtk-file instead.
Icon 'display-capplet' not found, using gtk-file instead.
Icon 'seamonkey-composer' not found, using gtk-file instead.
Traceback (most recent call last):
  File "/usr/bin/usp", line 1049, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1033, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 732, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 72, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 476, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 979, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 461, in Todos
    self.BuildLowerFiles(child)
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 563, in BuildLowerFiles
    openfile = open( GetFilePath( path ), 'r' )
  File "/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py", line 72, in GetFilePath
    path = urllib.url2pathname(uri) # escape special chars
  File "/usr/lib/python2.5/urllib.py", line 55, in url2pathname
    return unquote(pathname)
  File "/usr/lib/python2.5/urllib.py", line 1153, in unquote
    res = s.split('%')
AttributeError: 'NoneType' object has no attribute 'split'

Thanks in advance ! - and as a post scriptum - a question: - really noone from the Ubuntu board are interested in USP ? - in my view (and I am a designer,  good friend with Usability and GUI design ) USP is actually the best project designed to replace old Gnome start panel / applet. SLED is out - too many click's for a simple task.

---

### Post by Malac on 2009-01-21
> **SorinN said:**
> I can't start usp at all today (20 Ian 2009).
I just uninstalled previous versions, removed .usp folder in /home/userland folder and I do a fresh install from SVN (r374). 

No chance to start from gnome-panel then I tried to ..run-in-window. 
Here is the output ( btw. I have Ubuntu 8.10 up to date ):

sorin@SQ2:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
No User Picture Specified or File Not Found
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: ERROR - [Errno 2] No such file or directory: '/home/sorin/.usp/recentapps.list'
New Pane
Directory created
Icon 'web_browser.png' not found, using gtk-file instead.
Icon 'audio_player.png' not found, using gtk-file instead.
Icon 'xterm.png' not found, using gtk-file instead.
Icon 'display-capplet' not found, using gtk-file instead.
Icon 'seamonkey-composer' not found, using gtk-file instead.
Traceback (most recent call last):
  File "/usr/bin/usp", line 1049, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1033, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 732, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 72, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 476, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 979, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 461, in Todos
    self.BuildLowerFiles(child)
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 563, in BuildLowerFiles
    openfile = open( GetFilePath( path ), 'r' )
  File "/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py", line 72, in GetFilePath
    path = urllib.url2pathname(uri) # escape special chars
  File "/usr/lib/python2.5/urllib.py", line 55, in url2pathname
    return unquote(pathname)
  File "/usr/lib/python2.5/urllib.py", line 1153, in unquote
    res = s.split('%')
AttributeError: 'NoneType' object has no attribute 'split'
This is an error/change of code in python2.5 module 'urllib'. I thought I'd changed the code to catch this but I must have missed one. I will asap at the code.


> **SorinN said:**
> Thanks in advance ! - and as a post scriptum - a question: - really noone from the Ubuntu board are interested in USP ? - in my view (and I am a designer,  good friend with Usability and GUI design ) USP is actually the best project designed to replace old Gnome start panel / applet. SLED is out - too many click's for a simple task.It's on launchpad but is having build problems so I would like to get those ironed out so I could do packages for different architectures and a xubuntu version. It would be great to see it as at least an option in Ubuntu.
Thanks for the vote of confidence.

---

### Post by darcio53 on 2009-01-26
Hello Malac

I had to reinstall system and again I have reached the same problem with the crash of usp and ubuntu-tweak. I think it's connected to specific settings I've chosen, and it is not picture connected.
After choosing any application to start through usp, usp crushes with something like this:


dj@celina:~$ usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Tabbed Menu
applications: loaded successfully
recent: loaded successfully
system_management: loaded successfully
places: loaded successfully
shortcuts: loaded successfully
computer: loaded successfully
resources: loaded successfully
tracker: loaded successfully
notes: loaded successfully
internet: loaded successfully
terminal: loaded successfully
No User Picture Specified or File Not Found
uspuser: loaded successfully
calculator: loaded successfully
remind: loaded successfully
usptime: loaded successfully
uspcalendar: loaded successfully
template: loaded successfully
No User Picture Specified or File Not Found
No User Picture Specified or File Not Found
Binding USP Menu to Hotkey: 
dj@celina:~$ 

I really miss usp ;-). Please help.

Darek

---

### Post by Malac on 2009-01-27
Hi Darek,
Can you try a re-install of all installed python modules listed in Synaptic as this points to a python problem rather than USP.
Have you installed any custom Python modules?

---

### Post by darcio53 on 2009-01-31
Hello Malac

I reinstalled almost all python modules beside these custom:

python-moxml-config
python-gammu
python-uno
python-crontab

and nothing. Usp still freezes.

Do you suggest to remove them?

When I create in gnome another user account and start usp it works great, but when I customize gnome usp and ubuntu tweak refuse to work. Any suggestions?

Thanks.
Darek

---

### Post by darcio53 on 2009-02-01
Hello Again :-)

I did fresh install of usp and now it talks to me this way:

  File "/usr/lib/python2.4/site-packages/usp/plugins/recent.py", line 170, in DoRecent
    if len( self.wTree.get_widget( "RecentBox" ).get_children() ) < self.numentries:
AttributeError: 'NoneType' object has no attribute 'get_children'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 72, in RegenPlugin
    self.do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 154, in do_plugin
    self.do_sizing()
  File "/usr/lib/python2.4/site-packages/usp/plugins/system_management.py", line 120, in do_sizing
    self.wTree.get_widget("install_software").child.get_children()[0].set_property("icon-size", icon_size)
AttributeError: 'NoneType' object has no attribute 'child'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Static User Image Used
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 79, in RegenPlugin
    self.SetSystemStyle(["UserLabel","UserBelowLabel"])
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 133, in SetSystemStyle
    self.wTree.get_widget(items[i]).set_attributes(HeadingStyle)
AttributeError: 'NoneType' object has no attribute 'set_attributes'

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Static User Image Used
Static User Image Used
USP reloaded

(usp:14946): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition

and the problem still exists - freeze after executing applications.
Bye ;-)

---

### Post by HuaiDan on 2009-02-02
After some trouble finally got it installed. Had to manually copy and rename the python file after figuring out what usp's directory was. I don't have a download/SVN directory so that caused a bit of confusion. The I had to add the lines suggested to the application list file, all mentioned 3 or 4 pages ago in this thread.

Great app.

Now, is there anything I can do about the run-in-window part? Is it possible to mount this app so it runs in one of the panels?
Running USP without the run-in-window argument just gives me the API warning message then closes. with the run-in-window it gives me this
> ******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
Fontconfig error: "/etc/fonts/conf.d/51-local.conf", line 7: junk after document element
recent: loaded successfully
Icon 'gnome-settings-sound' not found, using gtk-file instead.
Static User Image Used
Static User Image Used
Binding USP Menu to Hotkey: <Ctrl><Alt>U

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Icon 'gnome-settings-sound' not found, using gtk-file instead.
Static User Image Used
Static User Image Used
USP reloaded

(usp:12185): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition

Reloading Plugins...
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Icon 'gnome-settings-sound' not found, using gtk-file instead.
Static User Image Used
Static User Image Used
USP reloaded



Is it running correctly?

---

### Post by Malac on 2009-02-03
> **HuaiDan said:**
> After some trouble finally got it installed. Had to manually copy and rename the python file after figuring out what usp's directory was. I don't have a download/SVN directory so that caused a bit of confusion. The I had to add the lines suggested to the application list file, all mentioned 3 or 4 pages ago in this thread.

Great app.

Now, is there anything I can do about the run-in-window part? Is it possible to mount this app so it runs in one of the panels?
Running USP without the run-in-window argument just gives me the API warning message then closes. with the run-in-window it gives me this



Is it running correctly?
Yes it is running correctly, run-in-window option is for debugging purposes.

_To Add USP to the panel_:
Right-click on the panel, choose "Add to Panel" option. In the list that opens look for "Ubuntu System Panel", highlight it then click [Add] button. The Menu should be added to the panel.
If "Ubuntu System Panel" is not in the "Add to Panel" list then either reboot or open a terminal and issue  the following command:```
killall gnome-panel
```Your panels will disappear for a second and then return. then do the add to panel routine above.

For further information on USP, including installation and usage, see :
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps.

---

### Post by HuaiDan on 2009-02-03
Did it ever. I didn't even think to check that.


Now, while this app is impressive, it's not nearly as impressive as the support. I would've dropped you an official "thanks" but it appears I'm all out.

Timely support is what makes good apps great. Here's hoping this is included with the next release.

---

### Post by santiagoward2000 on 2009-02-09
Hi there!
I just updated to the new r375 version, but I can't get it working on Xubuntu. I tried running it in window, but I get no errors before it crashes. All I get is:
```
santi@santi-laptop:~$ usp run_in_window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
santi@santi-laptop:~$
```
What can I do?

_EDIT:_
Nevermind. Seems there was a problem with some configuration. I made a backup, deleted the .usp folder, restarted it and it worked! :)

---

### Post by Malac on 2009-02-11
> **santiagoward2000 said:**
> 
```
santi@santi-laptop:~$ usp run_in_window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
santi@santi-laptop:~$
```
The command should be ```
usp run**-**in**-**window
```dashes not underscore

or you can use ```
usp -w
```

---

### Post by santiagoward2000 on 2009-02-11
> **Malac said:**
> The command should be ```
usp run**-**in**-**window
```dashes not underscore

Oops! :oops:
Thanks for the tip!

---

### Post by Malac on 2009-02-12
> **santiagoward2000 said:**
> Oops! :oops:
Thanks for the tip!
No problem :)

---

### Post by darcio53 on 2009-04-28
Hello Malac

I was wondering about translating usp2 into other languages.
If needed I can help with Polish one.

Darek

---

### Post by Malac on 2009-04-29
> **darcio53 said:**
> Hello Malac

I was wondering about translating usp2 into other languages.
If needed I can help with Polish one.

Darek

Hi Darek,
I have uploaded some preliminary .pot files to the SVN.
I have yet to upload the altered usp app code and the .pot file for that.
At the moment the plugin ones are located under :
...../usr/lib/python2.4/site-packages/usp/plugins/locale
however these will be moving to:
...../usr/lib/python2.4/site-packages/usp/locale
due to me having to alter a few things this week. This is where the uspconfig.pot file is located.

I also need to add a few lines that weren't picked up in the extraction process. I will post when they are done.

You could make a start on these files as it should only be a few additions. The changes I am trying to get through should also sort out the applications, favourites and recent names appearing in locale format too.

Hope this helps.

---

### Post by Malac on 2009-05-01
Okay .pot, .po and .mo files have been committed to the SVN 386.
Also the plugins and uspconfig should now be more locale aware.

---

### Post by mikeize on 2009-05-03
Any chance of a .deb file or repo for USP?  I tried doing the SVN install a couple of days ago, and had some trouble.  The menu appeared as a maybe 1-pixel dot on the taskbar, which did nothing when clicked.  I don't know if I did something wrong, but it would be really cool to have a deb for easier install/testing.  Thanks.

---

### Post by Malac on 2009-05-05
> **mikeize said:**
> Any chance of a .deb file or repo for USP?  I tried doing the SVN install a couple of days ago, and had some trouble.  The menu appeared as a maybe 1-pixeln dot on the taskbar, which did nothing when clicked.  I don't know if I did something wrong, but it would be really cool to have a deb for easier install/testing.  Thanks.
I have tried repeatedly to get a .deb file on launchpad.net but unfortunately despite following several guides how to package the files for launchpad they keep 'failing to build'.

I really could do with a hand if anybody knows about this stuff for python programs.

The single pixel bug is a known issue. It only seems to happen under specific circumstances on certain systems.
Unfortunately due to lack of bug information/follow-up it has never been tracked down.
It looks like a change in Python from 2.4 to 2.5 in urllib.py is to blame.
If you wish to help any info is gratefully received as I really want to squash this one.
Please open a terminal and run ```
usp -w
``` and post any output given and I will try to assist.

Thanks.

---

### Post by mikeize on 2009-05-05
```
mike@u-desktop:~/Downloads/SVN/ubuntu-system-panel$ usp -w
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Traceback (most recent call last):
  File "/usr/bin/usp", line 1132, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1116, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 805, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 119, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 548, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 1064, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 514, in Todos
    self.BuildLowerFiles(child)
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 616, in BuildLowerFiles
    openfile = open( GetFilePath( path ), 'r' )
  File "/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py", line 32, in GetFilePath
    path = urllib.url2pathname(uri) # escape special chars
  File "/usr/lib/python2.6/urllib.py", line 56, in url2pathname
    return unquote(pathname)
  File "/usr/lib/python2.6/urllib.py", line 1168, in unquote
    res = s.split('%')
AttributeError: 'NoneType' object has no attribute 'split'
mike@u-desktop:~/Downloads/SVN/ubuntu-system-panel$
```

---

### Post by Malac on 2009-05-07
hi mikeize
Can you try the attached applications.py file in place of the one in /usr/lib/python2.4/site-packages/usp/plugins folder and then run ```
usp -w
``` again.
If this works please let me know and I will upload it to the SVN.
You can log out and back in then add usp to the panel if you removed it after the initial error.

Thanks.

---

### Post by mikeize on 2009-05-07
Here you are:

```
mike@u-desktop:~$ usp -w
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
1
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
1
Errored on Path -  None
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Icon '/home/mike/.local/share/applications/ie.png' not found, using gtk-file instead.
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Icon '/usr/local/Freenet/freenet.ico' not found, using gtk-file instead.
2
Icon '/usr/local/Freenet/freenet.ico' not found, using gtk-file instead.
2
Icon '/usr/local/Freenet/freenet.ico' not found, using gtk-file instead.
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Icon 'gnome-settings-sound' not found, using gtk-file instead.
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Static User Image Used
Static User Image Used
['uspuser', <gtk.VBox object at 0x9a2d84c (GtkVBox at 0x9a6c920)>]
['system_management', <gtk.VBox object at 0x9a2dd4c (GtkVBox at 0x9a6cb30)>]
['applications', <gtk.VBox object at 0x9984964 (GtkVBox at 0x9b15870)>]
['recent', <gtk.VBox object at 0x9a3f75c (GtkVBox at 0x9cc2cc0)>]
Binding USP Menu to Hotkey: <Ctrl><Alt>U
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'uspbindkey' is not defined
mike@u-desktop:~$ usp -w
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
1
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
1
Errored on Path -  None
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Icon '/home/mike/.local/share/applications/ie.png' not found, using gtk-file instead.
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Icon '/usr/local/Freenet/freenet.ico' not found, using gtk-file instead.
2
Icon '/usr/local/Freenet/freenet.ico' not found, using gtk-file instead.
2
Icon '/usr/local/Freenet/freenet.ico' not found, using gtk-file instead.
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Icon 'gnome-settings-sound' not found, using gtk-file instead.
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
2
Static User Image Used
Static User Image Used
['uspuser', <gtk.VBox object at 0x992c84c (GtkVBox at 0x996b920)>]
['system_management', <gtk.VBox object at 0x992cd4c (GtkVBox at 0x996bb30)>]
['applications', <gtk.VBox object at 0x9883964 (GtkVBox at 0x9a29c70)>]
['recent', <gtk.VBox object at 0x993e75c (GtkVBox at 0x9a29e28)>]
Binding USP Menu to Hotkey: <Ctrl><Alt>U
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'uspbindkey' is not defined

(usp:9387): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
```

Running usp -w also produced a little window in the bottom right of my screen.  I enlarged it, and it was the usp menu.  I've attached 2 screenshots.

---

### Post by Malac on 2009-05-08
> **mikeize said:**
> Running usp -w also produced a little window in the bottom right of my screen.  I enlarged it, and it was the usp menu.  I've attached 2 screenshots.
The first is just the menu button detached from the panel and indeed opens the menu.
It looks like there was an error in one of your .desktop files which was throwing usp this is now caught. I have updated the SVN with the corrected code.
Run [./usp_update update] then logout and back in.
You should now be able to add usp to the panel as per normal.

Thanks for getting back to me, your help with this is much appreciated.

Malac

---

### Post by mikeize on 2009-05-08
Malac,

I booted up my computer this morning, and USP was working fine.  This was before I even saw your last post.  I'm going to hold off for now on updating from SVN.  But thanks for your help, and I'm glad I could be of some assistance as well.

-Mike

---

### Post by Malac on 2009-05-11
> **mikeize said:**
> Malac,

I booted up my computer this morning, and USP was working fine.  This was before I even saw your last post.  I'm going to hold off for now on updating from SVN.  But thanks for your help, and I'm glad I could be of some assistance as well.

-MikeYes, the applications.py file I attached had the corrected code in it. It is the same as the one in the SVN but it has some added debug info printing out.
However you may want to update to the SVN as I have just uploaded a new applications file which features a multi-column Favourites menu.

---

### Post by Malac on 2009-05-11
Added multi-column Favourites support to applications.
Favourites can now be dragged into position on the menu.
There is a new setting in uspconfig for number of columns using gconf key /apps/usp/plugins/applications/num_fav_cols

Uploaded to SVN Rev # 390 or later.

Much Thanks to Quikee and the mintMenu guys for their work which I 'borrowed' and adapted. :)

---

### Post by geekcliff on 2009-05-13
> **Malac said:**
> I have tried repeatedly to get a .deb file on launchpad.net but unfortunately despite following several guides how to package the files for launchpad they keep 'failing to build'.

I really could do with a hand if anybody knows about this stuff for python programs.

The single pixel bug is a known issue. It only seems to happen under specific circumstances on certain systems.
Unfortunately due to lack of bug information/follow-up it has never been tracked down.
It looks like a change in Python from 2.4 to 2.5 in urllib.py is to blame.
If you wish to help any info is gratefully received as I really want to squash this one.
Please open a terminal and run ```
usp -w
``` and post any output given and I will try to assist.

Thanks.

You should try speeking to clem at linux mint about building a deb file, they seem to be having great success with your menu, or maybe you could work together on this project, (just a thought):popcorn:

---

### Post by Malac on 2009-05-13
> **geekcliff said:**
> You should try speeking to clem at linux mint about building a deb file, they seem to be having great success with your menu, or maybe you could work together on this project, (just a thought):popcorn:
Thanks for the help geekcliff.
I'm able to build a working .deb file for installation but I'd like it to be available on launchpad as users are familiar with the process of adding stuff to their apt sources.list from there.
With launchpad you have to send them the source and then they auto-build it to the various architectures 64bit, 386, etc. this is the step that is failing and I can't make out where I'm going wrong from the error reports.
I did look at mintMenu's launchpad page but they don't actually host the .debs there so I wasn't able to crib from their source tar.
I've tried a pm to chanders to see if he can help, if not I'll maybe try clem.

Thanks, Malac.

---

### Post by geekcliff on 2009-05-13
Could you not attatch your latest deb to this thread like you used too, or is that not allowed anymore?

---

### Post by geekcliff on 2009-05-13
If not, can you point me in the right direction to install this on ubuntu 9.04:)

---

### Post by Malac on 2009-05-13
> **geekcliff said:**
> If not, can you point me in the right direction to install this on ubuntu 9.04:)[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
On the "Installation" page are full instructions for installing from the SVN.

> **geekcliff said:**
> Could you not attatch your latest deb to this thread like you used too, or is that not allowed anymore?I have held off doing a .deb as I was hoping to get this on launchpad for it's nice and easy installation/updating then through Synaptic. I've been concentrating on that so long it had slipped my mind to do a .deb for here, :oops:.
I will attempt it this week although I am really busy at weekend and all over the place this week and next.

---

### Post by geekcliff on 2009-05-14
Thanks for the link, i thought there might have been a new one for 9.04. Got it installed now, no problems and i must say it seems very stable now, great work all concerned, would be nice to see this as the default menu in ubuntu:p. 

Looking forward to the .deb;)

---

### Post by Malac on 2009-05-14
Please see this post for a deb file of the latest USP

[http://ubuntuforums.org/showpost.php?p=7277941&postcount=6](http://ubuntuforums.org/showpost.php?p=7277941&postcount=6)

---

### Post by geekcliff on 2009-05-15
WOW! (You have been Wasting your time wisely) That was quick, i wish i had waited a day now, i'll have try on a clean install, i dont expect that'll be to far away.

Thank you Malic:D

---

### Post by Malac on 2009-05-15
> **geekcliff said:**
> WOW! (You have been Wasting your time wisely) That was quick, i wish i had waited a day now, i'll have try on a clean install, i dont expect that'll be to far away.

Thank you Malic:D

You're Welcome. :D

I will try and do some test installs myself this weekend but they will have to be on virtual machines as that's all I've got left. Unfortunately this takes extra time in setup.

---

### Post by mikeize on 2009-05-17
So things are well except...  the 'applications' module won't load.  It appears in the menu as:

> Plugin "applications" error
'NoneType' object has no attribute 'connect'

I've tried reloading/rebooting, etc.  Other plugins seem to work fine.  Just 'applications' is failing.

```
usp -w
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
places: loaded successfully
recent: loaded successfully
applications: ERROR - 'NoneType' object has no attribute 'connect'
New Pane
Static User Image Used
Static User Image Used
['uspuser', <gtk.VBox object at 0x939e84c (GtkVBox at 0x93dc920)>]
['system_management', <gtk.VBox object at 0x939ed4c (GtkVBox at 0x93dcb30)>]
['places', <gtk.VBox object at 0x951661c (GtkVBox at 0x947f570)>]
['recent', <gtk.VBox object at 0x937b964 (GtkVBox at 0x9480418)>]
[None, <gtk.VBox object at 0x93b752c (GtkVBox at 0x95ec0b0)>]
Binding USP Menu to Hotkey: <Ctrl><Alt>U
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'uspbindkey' is not defined

```

---

### Post by geekcliff on 2009-05-18
Just tested your .deb on a live disk and all seems fine, see the screenshot, this is default setup. Sorry mikeize i know this wont help you

---

### Post by Malac on 2009-05-18
> **mikeize said:**
> So things are well except...  the 'applications' module won't load.  It appears in the menu as:



I've tried reloading/rebooting, etc.  Other plugins seem to work fine.  Just 'applications' is failing.

```
usp -w
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Static User Image Used
uspuser: loaded successfully
system_management: loaded successfully
places: loaded successfully
recent: loaded successfully
applications: ERROR - 'NoneType' object has no attribute 'connect'
New Pane
Static User Image Used
Static User Image Used
['uspuser', <gtk.VBox object at 0x939e84c (GtkVBox at 0x93dc920)>]
['system_management', <gtk.VBox object at 0x939ed4c (GtkVBox at 0x93dcb30)>]
['places', <gtk.VBox object at 0x951661c (GtkVBox at 0x947f570)>]
['recent', <gtk.VBox object at 0x937b964 (GtkVBox at 0x9480418)>]
[None, <gtk.VBox object at 0x93b752c (GtkVBox at 0x95ec0b0)>]
Binding USP Menu to Hotkey: <Ctrl><Alt>U
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'uspbindkey' is not defined

```
Hi mikeize,
Is this from the .deb file install or SVN?
Open Preferences and backup your current configuration using the Backup Button.
Then remove all but applications from the plugin list and Apply then run: ```
usp -w -v
``` and post the output.
You should restore your settings with the Restore Button in Preferences before logging out or rebooting.

Thanks.

---

### Post by mikeize on 2009-05-18
Thanks for the reply.  This is the latest SVN update as of yesterday, but I still have to use the applications.py file that you gave me earlier.  Anyway, here is the output you requested:

```
usp -w -v
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Traceback (most recent call last):
  File "/usr/bin/usp", line 1132, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1116, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 805, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 119, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 367, in PopulatePlugins
    MyPlugin = X.pluginclass( self )
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 214, in __init__
    self.wTree.get_widget( "applications_button_holder" ).connect( "drag_data_received", self.ReceiveCallback )
AttributeError: 'NoneType' object has no attribute 'connect'
```

---

### Post by Malac on 2009-05-18
> **mikeize said:**
> Thanks for the reply.  This is the latest SVN update as of yesterday, but I still have to use the applications.py file that you gave me earlier.  Anyway, here is the output you requested:

```
usp -w -v
*********** Keybind Driver Load Failure **************
Error Report :  libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
Using Standard Menu
Traceback (most recent call last):
  File "/usr/bin/usp", line 1132, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1116, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 805, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 119, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 367, in PopulatePlugins
    MyPlugin = X.pluginclass( self )
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 214, in __init__
    self.wTree.get_widget( "applications_button_holder" ).connect( "drag_data_received", self.ReceiveCallback )
AttributeError: 'NoneType' object has no attribute 'connect'
```
That is the problem the update has updated the application.glade file which is not compatible with the old applications.py file.
Try running a full update, the new applications.py file should be okay for your system.
Are you saying the latest applications.py file didn't work which is why you are running the old one?

---

### Post by mikeize on 2009-05-18
Yes, that's what I'm saying--I should have been more clear.  I tried updating the SVN yesterday, figuring that you had the updated applications.py file in the SVN.  Unfortunately I had the same problem with the "one-pixel" usp... even after killing gnome-panel and rebooting.  At that point, I again replaced the installed applications.py file with the one from earlier in the post.  After rebooting, everything worked... except the problem with "applications".

---

### Post by Malac on 2009-05-20
> **mikeize said:**
> Yes, that's what I'm saying--I should have been more clear.  I tried updating the SVN yesterday, figuring that you had the updated applications.py file in the SVN.  Unfortunately I had the same problem with the "one-pixel" usp... even after killing gnome-panel and rebooting.  At that point, I again replaced the installed applications.py file with the one from earlier in the post.  After rebooting, everything worked... except the problem with "applications".I have checked the code and when I added the multi-column Favourites I did not update the code to catch your error. I apologise for the oversight and introducing this regression.
I will correct the code tonight as I am away from home today(Wed) and you should be able to update from the SVN.

---

### Post by mikeize on 2009-05-20
Great!  Thanks very much.  I'll be looking forward to the updated SVN.

---

### Post by Malac on 2009-05-20
> **mikeize said:**
> Great!  Thanks very much.  I'll be looking forward to the updated SVN.
Okay updated to SVN.
Any problems let me know, Malac.

---

### Post by mikeize on 2009-05-20
Everything looks great so far... got my "applications".  Thanks malac!

-mike

---

### Post by Malac on 2009-05-21
> **mikeize said:**
> Everything looks great so far... got my "applications".  Thanks malac!

-mike
You're Welcome. :)

---

### Post by Bombenbach on 2009-05-22
Hello Malac,

well done, really like your panel, it actually has everything I need :p

There is only thing concerning applications plugin which makes me a little bit sad:

In Mintmenu the buttons are quite small (concerning the height) , which saves space but in USP they are unfortunately a little big too high for my widescreen. I hope the screenshot makes it a little bit more clear. Probably one should edit a few lines in applications.py or something like that in order to change the minimal height of the buttons. Could you please tell me, what lines are these exactly?

---

### Post by Malac on 2009-05-23
> **Bombenbach said:**
> Hello Malac,

well done, really like your panel, it actually has everything I need :p

There is only thing concerning applications plugin which makes me a little bit sad:

In Mintmenu the buttons are quite small (concerning the height) , which saves space but in USP they are unfortunately a little big too high for my widescreen. I hope the screenshot makes it a little bit more clear. Probably one should edit a few lines in applications.py or something like that in order to change the minimal height of the buttons. Could you please tell me, what lines are these exactly?
Thanks Bombenbach. :)
The code for the buttons looks like this, the second number (in [COLOR=Red]red[/COLOR]) is the height of the button.
I will add a button "padding" setting for a later release.

applications.py lines 854 to 859 approx. depending on version.
or do a search for "MakeAButton" and change the ones you want to.
```
                    if grandchild.get_type() == gmenu.TYPE_DIRECTORY:
                        PlaceName = " "+PlaceName
                        ItemButton = MakeAButton( 200, **[COLOR=Red]35[/COLOR]**, gtk.RELIEF_NONE, "forward", 2, 40, -1, [PlaceName], [DirStyle] )
                    else:
                        ItemButton = MakeAButton( 200, **[COLOR=Red]35[/COLOR]**, gtk.RELIEF_NONE, PlaceIconName, 2, 40, -1, [PlaceName], [AppStyle] )
```Hope this helps.

P.S. Would you by willing to translate USP into your native language?

---

### Post by Malac on 2009-05-23
New Release .deb file available here : [http://ubuntuforums.org/showpost.php?p=7277941&postcount=6](http://ubuntuforums.org/showpost.php?p=7277941&postcount=6)
Version 2.00.02

---

### Post by Bombenbach on 2009-05-24
> **Malac said:**
> Thanks Bombenbach. :)
The code for the buttons looks like this, the second number (in [COLOR=Red]red[/COLOR]) is the height of the button.
I will add a button "padding" setting for a later release. 

Thanks! Worked like a charm!! Now the buttons are really slim enough (height 15) :p


> **Malac said:**
>  P.S. Would you by willing to translate USP into your native language?

If you tell me what files are to be created/edited and how one can change the USP locale,
I'd gladly try to provide some translations (German, Russian, may be also Ukrainian).

---

### Post by Malac on 2009-05-24
> **Bombenbach said:**
> Thanks! Worked like a charm!! Now the buttons are really slim enough (height 15) :p
 
 
 
 
If you tell me what files are to be created/edited and how one can change the USP locale,
I'd gladly try to provide some translations (German, Russian, may be also Ukrainian).
That would be great.
 
There are .pot template files in /usr/lib/python2.4/site-packages/usp/locale for all the main plugins plus uspconfig and usp.
 
The pot files are in the form:
```
#: plugins/applications.py:1327
msgid "Lists all applications and favourites menu"
msgstr ""
 
#: tmp/applications.glade.h:1
msgid "<span size=\"small\">All Applications</span>"
msgstr ""
 
#: tmp/applications.glade.h:2
msgid "<span size=\"small\">Favourites</span>"
msgstr ""
 
#: tmp/applications.glade.h:3
msgid "<span weight=\"bold\">All Applications</span>"
msgstr ""
 
#: tmp/applications.glade.h:4
msgid "<span weight=\"bold\">Favourites</span>"
msgstr ""
```The line(s) in quotes after msgstr is the part that needs replacing with the translation.
You need to include any formatting e.g. <span> </span>, \n, \", etc.
 
This is an example from applications.po en_US.```
#: tmp/applications.glade.h:4
msgid "<span weight=\"bold\">Favourites</span>"
msgstr "<span weight=\"bold\">Favorites</span>"
``` 
 
 
To test usp in different locales run ```
LANGUAGE=en_GB LANG=en_GB.UTF8 python /usr/bin/usp -w
```in a terminal., replacing en_GB with which ever locale you want to check.
 
If you could pm me from the forum and attach any translated files it would be much appreciated and I will make sure they are uploaded to launchpad for inclusion in usp.

---

### Post by Bombenbach on 2009-05-25
Hi Malac,

I'm afraid that's not that easy. Doing a normal install of the latest svn version as described in the wiki doesn't create the locale folder, only ```
/usr/lib/python2.4/site-packages/usp/plugins
``` is created. I've also tried to copy the locale folder to the location you stated but USP somehow seems to ignore any locale files. Even changing .po files in the en_GB/po folder and running 
```
LANGUAGE=en_GB LANG=en_GB.UTF8 python /usr/bin/usp -w
```didn't make USP display new captions. Making a new folder
```
/usr/lib/python2.4/site-packages/usp/locale/de_DE/po
``` with edited .po files and running 
```
 LANGUAGE=de_DE LANG=de_DE.UTF-8 python /usr/bin/usp -w 
```didn't do it either.

Could you perhaps be a little more precise about files and folders which are to be created on order use another language? If you change some captions in po files from
en_GB/po or en_US/po, does your USP display the changes?

---

### Post by Malac on 2009-05-26
> **Bombenbach said:**
> Doing a normal install of the latest svn version as described in the wiki doesn't create the locale folder, only ```
/usr/lib/python2.4/site-packages/usp/plugins
``` is created.I'm sorry I wasn't aware of this. It should install them from the SVN if you run the ```
usp_update install
``` command instead this should not change any of your settings.
> **Bombenbach said:**
> Even changing .po files in the en_GB/po folder and running 
```
LANGUAGE=en_GB LANG=en_GB.UTF8 python /usr/bin/usp -w
```didn't make USP display new captions. Making a new folder
```
/usr/lib/python2.4/site-packages/usp/locale/de_DE/po
``` with edited .po files and running 
```
 LANGUAGE=de_DE LANG=de_DE.UTF-8 python /usr/bin/usp -w 
```didn't do it either.
Sorry, I thought I would need to compile them.
After changing the .po files they need compiling, I didn't think you would want to do that so I didn't explain that part.
The command for the applications plugin for German for example would be:```
 msgfmt -v --output-file=/usr/lib/python2.4/site-packages/usp/locale/de_DE/LC_MESSAGES/applications.mo /usr/lib/python2.4/site-packages/usp/locale/de_DE/po/applications.po
```The folders must exist already.

Running :```
 LANGUAGE=en_GB LANG=en_GB.UTF8 python /usr/bin/usp -w
```Gives me this :[ATTACH]115185[/ATTACH]
and running :```
 LANGUAGE=en_US LANG=en_US.UTF8 python /usr/bin/usp -w
```Gives me this :[ATTACH]115186[/ATTACH]Which you can see from the Control Centre button and the Favourites button is different in each.
Running :```
 LANGUAGE=de_DE LANG=de_DE.UTF8 python /usr/bin/usp -w
```Gives me this :[ATTACH]115191[/ATTACH]Which gives the correct de_DE names in applications and places which are python/gnome standard translations the only thing not translated is the specific usp text. e.g. in this last instance "Favourites", "All Applications", etc. which is what the .po files are for when they are compiled to .mo files.

Sorry I didn't explain fully and Thanks again.

---

### Post by Bombenbach on 2009-05-26
> **Malac said:**
> Sorry I didn't explain fully and Thanks again.

never mind and **thank you** for your detailed explanation. I'm currently working
on the German translation and hope to get it done soon. :)

Then I'll start creating Russian and Ukrainian language files.

---

### Post by geekcliff on 2009-05-28
Hello Malic
   Just installed your new deb on a clean install of ubuntu, and it worked like a charm, restored my settings from my backup file and everything is smelling of roses:popcorn:

---

### Post by Malac on 2009-05-28
> **geekcliff said:**
> Hello Malic
   Just installed your new deb on a clean install of ubuntu, and it worked like a charm, restored my settings from my backup file and everything is smelling of roses:popcorn:
Thanks for the feedback geekcliff, it all helps. Next step inclusion in Ubuntu as standard, then the world. :)

---

### Post by Bombenbach on 2009-05-28
Hi Malac,

the German translation is almost done, but there are, however, some problems:


[LIST]
[*]The menu that appears when right clicking on the USP button in the panel (Preferences-Edit Menu-Reload Plugins-About) doesn't seem to have a po file
[*]In USP configuration, Main tab the captions on "New tab", "New pane" and "Reset" buttons are missing in the uspconfig.po and thus can't be translated
[*]When adding a new plugin the translation of the Text "Plugin Name" is apparently ignored
[*]When adding a new plugin the descriptions can't be translated
[*]The default size of the Preferences Window doesn't fit German text well, as in German (and many other languages too) you can't make certain phrases as short as in English. It would be nice, if one could define the default size in a .po file
[/LIST]

---

### Post by Malac on 2009-05-29
> **Bombenbach said:**
> Hi Malac,

the German translation is almost done, but there are, however, some problems:


[LIST]
[*]The menu that appears when right clicking on the USP button in the panel (Preferences-Edit Menu-Reload Plugins-About) doesn't seem to have a po file
[*]In USP configuration, Main tab the captions on "New tab", "New pane" and "Reset" buttons are missing in the uspconfig.po and thus can't be translated
[*]When adding a new plugin the translation of the Text "Plugin Name" is apparently ignored
[*]When adding a new plugin the descriptions can't be translated
[*]The default size of the Preferences Window doesn't fit German text well, as in German (and many other languages too) you can't make certain phrases as short as in English. It would be nice, if one could define the default size in a .po file
[/LIST]

Thanks Bombenbach, I will look into these today.
I am away at weekend so will not get another chance until Monday.

---

### Post by Malac on 2009-05-30
> **Bombenbach said:**
> 
[LIST]
[*]The menu that appears when right clicking on the USP button in the panel (Preferences-Edit Menu-Reload Plugins-About) doesn't seem to have a po file
[/LIST]
Fixed in usp2.pot

> **Bombenbach said:**
> 
[LIST]
[*]In USP configuration, Main tab the captions on "New tab", "New pane" and "Reset" buttons are missing in the uspconfig.po and thus can't be translated
[/LIST]
Fixed in uspconfig.pot

> **Bombenbach said:**
> 
[LIST]
[*]When adding a new plugin the translation of the Text "Plugin Name" is apparently ignored
[/LIST]
Fixed in uspconfig.pot

> **Bombenbach said:**
> 
[LIST]
[*]When adding a new plugin the descriptions can't be translated
[/LIST]
Fixed in uspconfig.pot

> **Bombenbach said:**
> 
[LIST]
[*]The default size of the Preferences Window doesn't fit German text well, as in German (and many other languages too) you can't make certain phrases as short as in English. It would be nice, if one could define the default size in a .po file
[/LIST]
Unfortunately, as far as I know, this can't be done.

Updates are now in SVN #Rev 410.

Thanks again.

---

### Post by darcio53 on 2009-06-04
Hello Malac

I have two small business to You:

1. I was reading previous posts sent here and I wondered myself that maybe You should look at launchpad and seek for other programs written in python and packaged as deb in launchpad repos and ask for help. I mean here
 - Subdownloader [https://launchpad.net/~subdownloader-developers/+archive/ppa](https://launchpad.net/~subdownloader-developers/+archive/ppa)
 - Wammu [https://launchpad.net/~nijel/+archive/ppa](https://launchpad.net/~nijel/+archive/ppa)
 - Phatch [https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)
Just idea, do not be angry ;-).

2. I am almost ready with Polish translation. I have to translate upsconfig.po only. I am going to Warsaw for 5 days tomorrow and I am made to finish it after these 5 days. So plesae give me Your e-mail adress or write me private message using this forum (if You don't want to publish Your e-mail address) to give me contact address I will send You translated files.

Thanks for working on USP
Darek

---

### Post by Malac on 2009-06-04
^^^^^^
pm sent.

---

### Post by Malac on 2009-06-06
Updated the .deb on New Release thread with German translations.

---

### Post by darcio53 on 2009-06-10
Helo Malac

As I said pl translation is being sent.

Suggestions:

1. Add usp2 screenshot for

[http://code.google.com/p/ubuntu-system-panel/](http://code.google.com/p/ubuntu-system-panel/) main page!

2. Add usp2_2.00.02-7ubuntu1_all.deb or another .deb built on launchpad to 

[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)

3. I suggest also to add an option to usp to set usp language trough Uspconfig - not only default language trough LC_MESSAGES - translating purposes and there will be no need to change language settings for the system - if it is done, sorry for mentioning it.

Greetings from Poland
Darek

---

### Post by Malac on 2009-06-11
> **darcio53 said:**
> As I said pl translation is being sent.Excellent. Thanks Darek.
I will post these to the SVN tonight and upgrade the launchpad repo.
> **darcio53 said:**
> 1. Add usp2 screenshot for

[http://code.google.com/p/ubuntu-system-panel/](http://code.google.com/p/ubuntu-system-panel/) main page!I will look into this.

> **darcio53 said:**
> 2. Add usp2_2.00.02-7ubuntu1_all.deb or another .deb built on launchpad to 

[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list) I will add a set of instructions for adding the launchpad repo to apt sources.list(synaptic repositories) as otherwise I would have to maintain both packages separately.

> **darcio53 said:**
> 3. I suggest also to add an option to usp to set usp language trough Uspconfig - not only default language trough LC_MESSAGES - translating purposes and there will be no need to change language settings for the system - if it is done, sorry for mentioning it.You can launch usp with different language settings "on the fly" by using the following method in a terminal:
```
LANGUAGE=de_DE LANG=de_DE.UTF8 python /usr/bin/usp -w
```and for uspconfig:
```
LANGUAGE=de_DE LANG=de_DE.UTF8 python /usr/bin/uspconfig
```These are for German, just change the de_DE to Polish( I assume pl_PL or just pl ?)
> **darcio53 said:**
>  Greetings from Poland
DarekHope this helps and Thanks again.

---

### Post by geekcliff on 2009-09-10
Hello Malac, what are you planing for usp3, just curious :popcorn:

---

### Post by Malac on 2009-09-11
> **geekcliff said:**
> Hello Malac, what are you planing for usp3, just curious :popcorn:

Hi geekcliff,
Chanders and I have discussed some of the options we have.
I don't think I'm giving too much away by letting out the following.
1/. Full transparency support is one of our goals.
2/. We are looking into completely re-writing the code for the menu & plugins to allow for a new theme "engine". This is to allow all buttons and items to be customised including transparency values. This probably will mean we get rid of gtk.Stuff.
3/. Less reliance on uspconfig for settings.(see 4)
4/. We should have drag'n'drop placement for all plugins. I would also like to see them sized using the mouse too.
5/. We will be incorporating as many as we can of the advances we made in USP2 into the next menu.
6/. We may do away with plugins per se as this was to allow for user written add-ons but, apart from Quikee's Tracker plugin, no-one wrote any :(. 
7/. And finally.....Secret stuff :)

Hope this helps.

---

### Post by geekcliff on 2009-09-17
That sounds great:guitar: i'm looking forward to that,i get a bit concerned sometimes when i see that this thread is a bit quiet, i keep thinking the great USP is gona die before it gets in the repo.:lolflag:

---

### Post by Malac on 2009-09-18
> **geekcliff said:**
> That sounds great:guitar: i'm looking forward to that,i get a bit concerned sometimes when i see that this thread is a bit quiet, i keep thinking the great USP is gona die before it gets in the repo.:lolflag:

You can add it to Synaptic from the launchpad repository that way you will be kept up to date with any bugfixes. Just follow the instructions on the wiki page.
Not sure we'll make it into the main repos as I'm not sure I'll have the time to sort it as we're starting to move the focus on to USP3.
 
Hope this helps.

---

### Post by theZoid on 2009-10-09
USP is my menu of choice....keep up the good work !

---

### Post by detrate on 2009-10-16
[s]I'm on 64bit 9.04, using usp from svn and I'm still getting the error:
```
Error Report :  No module named deskbar.core.keybinder
```

What can I do to resolve this? I'd really like to use the hotkey :)[/s]

got this working by installing from repository... 

I think this bug might have been caused by not having the deskbar applet package installed?


[s]only problem I'm having now is it doesn't focus on USP when I call it via the hotkey.  I thought I'd be able to just type and filter the program I want to use.  Is this not the case?[/s]

Solved by setting the compiz focus stealing from low to off
[http://code.google.com/p/ubuntu-system-panel/wiki/Troubleshooting](http://code.google.com/p/ubuntu-system-panel/wiki/Troubleshooting)


... but now I can't click anything in it, when I do it just hides >_<


Great program btw.
:guitar:

---

### Post by Malac on 2009-10-17
> **theZoid said:**
> USP is my menu of choice....keep up the good work !
Thanks for the feedback theZoid it's much appreciated.
> **detrate said:**
> [s]I'm on 64bit 9.04, using usp from svn and I'm still getting the error:
```
Error Report :  No module named deskbar.core.keybinder
```What can I do to resolve this? I'd really like to use the hotkey :)[/s]

got this working by installing from repository... 

I think this bug might have been caused by not having the deskbar applet package installed?


[s]only problem I'm having now is it doesn't focus on USP when I call it via the hotkey.  I thought I'd be able to just type and filter the program I want to use.  Is this not the case?[/s]

Solved by setting the compiz focus stealing from low to off
[http://code.google.com/p/ubuntu-system-panel/wiki/Troubleshooting](http://code.google.com/p/ubuntu-system-panel/wiki/Troubleshooting)


... but now I can't click anything in it, when I do it just hides >_<


Great program btw.
:guitar:

I'm glad you sorted the deskbar issue I can't remember if this is explained in the install instructions for the SVN if not I will amend them asap. This isn't an issue when installing from deb or repo so I may have forgotten to update the SVN instructions. Sorry. :(

The keyboard issue seems to be on 64 bit machines also some major startup times and lack of response from usp generally on 64 bit. Unfortunately I don't have a 64 bit machine to do any testing on. So I'm a little stuck trying to problem solve these as something that works fine on 32 bit may not on 64 bit. I may just have to invest in a new machine for Xmas. :)

If you could maybe try installing from the repo and see if that solves the problem. At the moment the launchpad repo contains a "stable" release whilst the SVN has some new code in it which is in test phase. Ironically this was an attempt to make the menu *more* navigable using the keyboard instead of the mouse for accessibility reasons.

You can pm me if you want any further help, I will try to find the time to look at the issues you've raised.

Hope this helps.

---

### Post by theZoid on 2009-10-17
> **Malac said:**
> Thanks for the feedback theZoid it's much appreciated.


snip....

s.

It reminds me of TastyMenu that I used to always use in KDE.  A bug though...sometimes my bookmarks or places wouldn't show, just either or.

Also, you really need to get that into the repo's as a 'panel applet'

fwiw

---

### Post by skajoeska on 2009-11-01
According to the USP Google code page it is a Compiz error, not a USP error.

----------------------------------------------------------------------------

I have a strange error while using USP in 9.10 Karmic Koala. I open USP then select whatever and when it closes it leaves behind the drop shadow on my desktop. here's a screen shot of it.

[ATTACH]134023[/ATTACH]

It stays until I logout and log back in. Any help is appreciated. Thanks.

Joe

---

### Post by walterav on 2009-11-05
> **skajoeska said:**
> According to the USP Google code page it is a Compiz error, not a USP error.

----------------------------------------------------------------------------

I have a strange error while using USP in 9.10 Karmic Koala. I open USP then select whatever and when it closes it leaves behind the drop shadow on my desktop. here's a screen shot of it.

[ATTACH]134023[/ATTACH]

It stays until I logout and log back in. Any help is appreciated. Thanks.

Joe

I found a workaround/fix!
I'm using karmic 64 bit and I'm using the version from the repository added according this wiki:
[http://code.google.com/p/ubuntu-system-panel/wiki/APT_Synaptic_Repository](http://code.google.com/p/ubuntu-system-panel/wiki/APT_Synaptic_Repository)

solution:
#go to terminal!
gksu apt-get install compizconfig-settings-manager #very usefull for compiz tweaking...
ccsm #starts compizconfig settings manager, and go to
#Window Decoration>General>Shadow window
any>none #change the word any to none and restart or logout/login

---

### Post by Malac on 2009-11-10
> **walterav said:**
> I found a workaround/fix!
I'm using karmic 64 bit and I'm using the version from the repository added according this wiki:
[http://code.google.com/p/ubuntu-system-panel/wiki/APT_Synaptic_Repository](http://code.google.com/p/ubuntu-system-panel/wiki/APT_Synaptic_Repository)

solution:
#go to terminal!
gksu apt-get install compizconfig-settings-manager #very usefull for compiz tweaking...
ccsm #starts compizconfig settings manager, and go to
#Window Decoration>General>Shadow window
any>none #change the word any to none and restart or logout/login
You can specifically rule out USP from compiz shadow but still shadow other windows by changing the value to ```
!(class=Usp)
```. The capitalisation is important.
Your compiz should read either as above or:```
any & !(class=Usp)
```

Hope this helps.

---

### Post by delfick on 2009-11-10
> **Malac said:**
> You can specifically rule out USP from compiz shadow but still shadow other windows by changing the value to ```
!(class=Usp)
```. The capitalisation is important.
Your compiz should read either as above or:```
any & !(class=Usp)
```

Hope this helps.

Thankyou.

I had the same problem too :)

---

### Post by ageeb on 2009-11-13
after applying this:

```
!(class=Usp)
```I still see this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=1&d=1257048714[/IMG]
[http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=&d=1257048714](http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=&d=1257048714)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=1&d=1257048714[/IMG]

---

### Post by Malac on 2009-11-13
> **ageeb said:**
> after applying this:

```
!(class=Usp)
```I still see this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=1&d=1257048714[/IMG]
[http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=&d=1257048714](http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=&d=1257048714)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134023&thumb=1&d=1257048714[/IMG]
Have you tried the "any & !(class=USP)" option?
Also compiz will need restarting to have this take effect if the shadow is already there.

Hope this helps.

---

### Post by Trespasser on 2009-11-15
Yes, USP is my favorite Menu as well. It's simply the best out there. I see it's advanced quite a bit since the last time I used it. Nice.

Just wanted to express my appreciation for USP's continued development.

Later...

---

### Post by Malac on 2009-11-17
> **Trespasser said:**
> Yes, USP is my favorite Menu as well. It's simply the best out there. I see it's advanced quite a bit since the last time I used it. Nice.
 
Just wanted to express my appreciation for USP's continued development.
 
Later...Thanks. We are still plugging away at it trying to squash bugs and improve performance which is slow on 64-bit machines for some reason.
 
Chanders and I are currently pegging out the framework for the next version. Hopefully we can carry all the work we have done on USP2 over into that version to make a stable version of the next version that bit sooner.

---

### Post by skajoeska on 2009-11-20
Sorry for the late reply.

Adding > & class=!(class=Usp)to the "Shadow Windows" section under "Windows Decoration" worked for me.

Thanks Malac. Love usp. It's the first thing I install after a fresh install of Ubuntu. Yes, even before amarok. ;)

Joe

---

### Post by Malac on 2009-11-21
> **skajoeska said:**
> Sorry for the late reply.

Adding to the "Shadow Windows" section under "Windows Decoration" worked for me.

Thanks Malac. Love usp. It's the first thing I install after a fresh install of Ubuntu. Yes, even before amarok. ;)

Joe
you're welcome.

---

### Post by geekcliff on 2010-01-08
Hello Malac
   I've just installed usp on debian lenny, no dependencies required, and its works well apart from the shut down button dont work, do you know what i need to change the command to in the preferences? i will still use it even if it cant be fixed,it would just be nice to have it all working, but it dont matter none.;)

---

### Post by Malac on 2010-01-10
> **geekcliff said:**
> Hello Malac
   I've just installed usp on debian lenny, no dependencies required, and its works well apart from the shut down button dont work, do you know what i need to change the command to in the preferences? i will still use it even if it cant be fixed,it would just be nice to have it all working, but it dont matter none.;)
I haven't got a Lenny system to hand to try this on so I'll have to try some guesses.

When you say "shut down button dont work" do you mean the Shutdown button on USP doesn't bring up the Shutdown Dialog. In which case the correct command should be ```
gnome-session-save --shutdown-dialog
```Try it in a terminal to check the command itself is working.

Does the Logout button show all the options i.e. Shutdown, Restart, Suspend & Hibernate, as well as Logout & Switch User?
Try opening a terminal and entering:```
gnome-session-save --help
```This will list the options to pull up a dialog.

If the button on the dialog itself is not working this seems to be an issue with Lenny's power management, which handles the shutdown messages.

Sorry for the late reply.
Hope this helps.

---

### Post by geekcliff on 2010-01-13
Hi
   Yes i do mean the usp shutdown button, when i click it, nothing happens at all. I've run the command, gnome-session-save --shutdown-dialog in the terminal and it says something like, unknown command, debian must be using something different, i'll try a bit more googling. I've removed the computer managment plugin for now and replaced it with the shortcuts plugin so its no big deal, thanks for the input though.:D

---

