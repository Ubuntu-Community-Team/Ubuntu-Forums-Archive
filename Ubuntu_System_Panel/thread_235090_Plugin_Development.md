---
title: "Plugin Development"
date: 2006-08-12
forum: Ubuntu System Panel
---

### Post by chanders on 2006-08-12
Ok guys, as you know I just released USP with full plugin support. I am hoping that all you talented programmers out ther start coding some plugins!

Some notes:
Plugins and their associated files are stored in ~/.usp/plugins
Plugins must have a .py extension
The **plugin name is the filename** (without the .py extension) for example the time plugin is USPtime.py so the plugin name is USPtime

Here is the structure of the time plugin USPtime.py
```
# Basic USP plugin

import gtk
import gtk.glade
import sys
import os
import gobject
import datetime

class pluginclass:
    """This is the main class for the plugin"""
    """It MUST be named pluginclass"""

    def __init__(self, __usp=False):

        #The Glade file for the plugin
        self.gladefile = os.path.join(os.path.dirname(__file__), "myplugin.glade")

        #Read GLADE file
        self.wTree = gtk.glade.XML(self.gladefile,"window1")

        #These properties are [COLOR="Red"]NECESSARY[/COLOR] to maintain consistency
        #throughout USP

        #Set 'window' property for the plugin (Must be the root widget)
        [COLOR="Red"]self.window[/COLOR] = self.wTree.get_widget("window1")

        #Set 'heading' property for plugin
        [COLOR="Red"]self.heading[/COLOR] = "Time and Date"

        #This should be the first item added to the window in glade
        [COLOR="Red"]self.content_holder[/COLOR] = self.wTree.get_widget("eventbox1")

        #Specify plugin width
        [COLOR="Red"]self.width[/COLOR] = 150

        #Plugin icon
        [COLOR="Red"]self.icon[/COLOR] = 'gnome-set-time'

        #Connect event handlers
        dic = {"on_window1_destroy" : gtk.main_quit}
        self.wTree.signal_autoconnect(dic)
        
        # Set up usp instance pointer
        self.__usp = __usp

        gobject.timeout_add(1000, self.date_time)

    #Actually do something with the plugin
    [COLOR="Red"]def do_plugin(self):[/COLOR]
    	#This is the MAIN section where all the work is done
        pass

    def date_time(self):
    	try:
        	self.wTree.get_widget("label1").set_label('<span size="large" weight="bold">' + datetime.datetime.today().strftime("%m-%d-%Y") + '</span>')
        	self.wTree.get_widget("label2").set_label('<span size="30000" weight="bold">' + datetime.datetime.today().strftime("%H:%M:%S") + '</span>')
        except:
        	pass
        return True
```

self.window - the window object
self.heading - the heading for the plugin in USP
self.content_holder - the container (must be eventbox) holding the plugin
self.width - the default width of the plugin
self.icon - the icon to use for the plugin in the plugin-tray
def do_plugin(self): - the MAIN section of the plugin where the work is done
def __init__(self, __usp=False): - __usp is the main USP object. By being creative in plugin development the user should be able to modify nearly all of the paramaters of the USP window and its children


USP currently offers the following API. It will be extended in the future
Filename 
- easygconf.py

Methods 
- SetGconf(client,type,key,default)
- SetGconfList(client,type,key,default)

client is the default gconf client
type - this is the key type such as string, int, bool
key - the actual key such as /apps/usp/plugins/foo/something
default - the default key to set


Filename
- execute.py

Methods
- Execute(widget,cmd)

widget - widget calling the execute command
cmd - the command to execute in list format, first value is the command and the following is the arguments each as its own item in the list

---

### Post by _profox on 2006-08-12
Wow, this is great!
Okay, any requests? I will do the easiest things first though, so don't make it too hard ;) hehe

---

### Post by Note360 on 2006-08-12
Embedded music player

---

### Post by chanders on 2006-08-12
> **_profox said:**
> Wow, this is great!
Okay, any requests? I will do the easiest things first though, so don't make it too hard ;) hehe

Write a plugin to show an image (resized to fit the pane) from a folder and change every x mins .... ;)

---

### Post by _profox on 2006-08-12
Lol.. good to have the pin option :P you guys want to watch/use the USP to do everything now lol.. music player :) image viewer :)

Although the image viewer is a good idea.. hmm.. or even better.. a background changer

---

### Post by chanders on 2006-08-12
> **_profox said:**
> Lol.. good to have the pin option :P you guys want to watch/use the USP to do everything now lol.. music player :) image viewer :)

Although the image viewer is a good idea.. hmm.. or even better.. a background changer

I love the background changer idea! Think i will toy with it....later though..

---

### Post by Note360 on 2006-08-12
I want a plugin that Browses the internet has a kernel terminal and panel.

---

### Post by _profox on 2006-08-12
I want to see USP built inside of USP ;) !! Now that would rock. (would be funny, yes?)

---

### Post by Note360 on 2006-08-12
LoL ok now we need real ideas

---

### Post by agurk on 2006-08-12
As has been mentioned before, the holy grail would be an Xorg configurator, although that might be a bit much to chew for a first project. ;)
(perhaps it's also better suited for UCC)

---

### Post by _profox on 2006-08-12
agurk: that won't be necessary anymore when I start my own project with SmartGuide ;) but I'm not going to talk about that yet.. I haven't started programming yet, and it will get really though. But alot of common and uncommon hardware configurations will be simplified

---

### Post by delfick on 2006-08-12
personally i want to see full theming support ! :D

and a.....(trying to think of something for some talented develepor to make a plugin about).....

better ideas will probably come to me later...but what about a simple notepad with the ability to save notes...?

that way if u need to quickly write something down...all that needs to be done is open the menu and type....

:D

btw...THANKYOU CHANDERS !!!!!!!
(someone please send chanders a big, shiny medal :D he deserves one)

---

### Post by Note360 on 2006-08-12
maybe a terminal

---

### Post by delfick on 2006-08-12
> **Note360 said:**
> maybe a terminal

that could actually be a good idea :D

.....also is it possible to put the user-defined icons on the toggle pane now?

i.e. the places.....

---

### Post by Note360 on 2006-08-13
Like a quake terminal

---

### Post by mat on 2006-08-13
2 small notes:
[LIST]
[*]The *__usp* variable is for the next release. It will allow your plugin to access the main usp instance to call stuff. It might not be kept in the future, but right now, since some useful stuff lives in the core, it's needed
[*]to load your gladefile, use the following code: self.gladefile = ```
os.path.join(os.path.dirname(__file__), "myplugin.glade")
```Absolute paths must die :-)
[/LIST]

---

### Post by 16777216 on 2006-08-29
A small button to configure USP it's self say in the bottom corner of the system pane.
I would like to find plug-ins but don't know where any are, can anyone give me a hint?
Oh, yeah that would be a good idea to have a plug-in installer option in the above mentioned setup button.
A terminal panel would be a good idea.
And, if you go three button have it where you can change the order of the buttons, maybe even have the possibility of having them on different panels. ( exp. apps and places on the bottom system on the top. )

---

### Post by chanders on 2006-08-29
> **16777216 said:**
> A small button to configure USP it's self say in the bottom corner of the system pane.
I would like to find plug-ins but don't know where any are, can anyone give me a hint?
Oh, yeah that would be a good idea to have a plug-in installer option in the above mentioned setup button.
A terminal panel would be a good idea.
And, if you go three button have it where you can change the order of the buttons, maybe even have the possibility of having them on different panels. ( exp. apps and places on the bottom system on the top. )

USP is fairly young so we havent gotten around to doing a configuration window as yet and also plugins are limited to the ones listed in the New Release thread. 

Having a terminal plugin is a great idea and shouldnt be too difficult to implement.

When we add three/more button support, they would be able to be placed anywhere in any panels..

Hope these answered your questions ;)

---

### Post by 16777216 on 2006-08-29
I don't seem to have any plug-ins, were they left out of 0.41-1?

Nevermind I found and extracted them myself from the deb. ( I wonder why they didn't install? ) :-k

Added the clock, calender and, weather :D but now the menu opens with the right side alighened to the button so that 90% of the menu is off the left side of the screen. ](*,)

Ok, that seems to have fixed it's self. :-D All is good.

---

### Post by linux.photo.geek on 2006-08-31
> **_profox said:**
> Wow, this is great!
Okay, any requests? I will do the easiest things first though, so don't make it too hard ;) hehe

How about a way to embed "DeskBar" into the menu?

Will

---

### Post by cmost on 2006-09-01
How about a small panel depicting the user's login Avatar and username.  Also, it would be nice if the menu applet button could be made transparent when the panel is transparent.  Just my 0.02

---

### Post by Uncle Spellbinder on 2006-09-01
> **cmost said:**
> How about a small panel depicting the user's login Avatar and username. 

LOVE that idea!

---

### Post by alejandrops on 2006-09-01
Deskbar is imperative!!!!!

---

### Post by its_me_gb on 2006-09-02
maybe a list of recently used apps/documents?

---

### Post by chanders on 2006-09-02
> **cmost said:**
> How about a small panel depicting the user's login Avatar and username.

Sounds nice, will try to make it in the next release..

> **linux.photo.geek said:**
> How about a way to embed "DeskBar" into the menu?

Will

Planned, but Deskbar is changing right now so I am waiting for the code to settle in Edgy before including a plugin..

> **its_me_gb said:**
> maybe a list of recently used apps/documents?

Already on the list ;-) Not too sure of the apps though because gnome needs to be patched for that but we will see what we can hack up ;)

---

### Post by Malac on 2006-09-13
Here are my plugins so far: 
Don't forget to backup as some of these files use the same names as the originals.
[ATTACH]15721[/ATTACH]

EDIT:
Re-uploaded tar files with corrected glade file reference.
        self.gladefile = os.path.join(os.path.dirname(__file__), "[SIZE=2]*<filename>*[/SIZE].glade")

[SIZE=2][/SIZE]Get plugins here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by chanders on 2006-09-13
Just a quick note, users who are putting plugins such as USP user in their home directory need to change the gladefile to one such as

self.gladefile = os.path.join(os.path.dirname(__file__), "USPuser.glade")

This will allow the plugin to find the gladefile in its directory

---

### Post by Malac on 2006-09-13
Okay, took me all day but here is my terminal emulator first draught.
it requires libvte4 package.
It creates two keys for width and height under /apps/usp/plugins/terminal
Unfortunately these don't alter dynamically yet but I'll work on it.
Other than that it's a terminal. :)
[ATTACH]15723[/ATTACH]
Edit : new USPterm that allows for colours this can be done through gconf-editor or USPconfig (post #32 page 4).
This requires that USPterm be removed from the plugins list then re-added for the changes to take effect. If that doesn't work try a restart of USP and repeat the above. As you can see from the next attachment it does work. :)
[ATTACH]15884[/ATTACH]
Now does a background picture.

Get plugins here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by spockrock on 2006-09-13
> **Malac said:**
> Here are my plugins so far: 
Don't forget to backup as some of these files use the same names as the originals.
[ATTACH]15665[/ATTACH]

EDIT:
Re-uploaded tar files with corrected glade file reference.
        self.gladefile = os.path.join(os.path.dirname(__file__), "[SIZE=2]*<filename>*[/SIZE].glade")


sorry Malac but what is different about your computer, time and calender, I see that you have an icon for time but what other difference is there?

---

### Post by Malac on 2006-09-14
> **spockrock said:**
> sorry Malac but what is different about your computer, time and calender, I see that you have an icon for time but what other difference is there?
Sorry I should have explained better.
**USPcomputer**.
Can switch off the individual buttons in the settings panel, so if you didn't need the theme button or time button showing it can be hidden under gconf /apps/usp/plugins/computer, e.g. hide_theme, hide_date, etc.
Some minor tweaks with the time part of that so it accesses the time plugin settings in gconf.
**USPtime**
Has options to change the way the time and date are displayed. These can be set under gconf /app/usp/plugins/datetime and are for changing the date font size, date bold text or not, time font size, time bold or not,  displaying the date in word form, showing the day of the week and also I got the eu_date_format to work which shows the date in the format dd-mm-yyyy instead of mm-dd-yyyy.
Plus you can choose your date seperator if you would like a "/" character instead of "-" character.
[B]USPcalendar
[/B]The only difference is that it now opens evolution if you click on the calendar (like when you click on the one that pops up from the clock.
Although it doesn't as yet open on the date clicked as I haven't figured out how to transform the calendars string into one recognised by evolution command line.

Hope this helps.

---

### Post by spockrock on 2006-09-15
> **Malac said:**
> Sorry I should have explained better.
**USPcomputer**.
Can switch off the individual buttons in the settings panel, so if you didn't need the theme button or time button showing it can be hidden under gconf /apps/usp/plugins/computer, e.g. hide_theme, hide_date, etc.
Some minor tweaks with the time part of that so it accesses the time plugin settings in gconf.
**USPtime**
Has options to change the way the time and date are displayed. These can be set under gconf /app/usp/plugins/datetime and are for changing the date font size, date bold text or not, time font size, time bold or not,  displaying the date in word form, showing the day of the week and also I got the eu_date_format to work which shows the date in the format dd-mm-yyyy instead of mm-dd-yyyy.
Plus you can choose your date seperator if you would like a "/" character instead of "-" character.
[B]USPcalendar
[/B]The only difference is that it now opens evolution if you click on the calendar (like when you click on the one that pops up from the clock.
Although it doesn't as yet open on the date clicked as I haven't figured out how to transform the calendars string into one recognised by evolution command line.

Hope this helps.

thank you for clarifying I am definatly gonna update the plugins with yours.

---

### Post by Malac on 2006-09-16
Okay another **"experimental"** plugin.
USPconfig
This has settings to alter USP instead of opening gconf-editor.
It works with my current set of plugins, post #26 and post #28 on page 3 of this thread.
As I don't have an untouched copy of USP 0.41.1 or the standard plugins I haven't tested it on them. Worst case you can still go back to gconf-editor. :)
Here are some screenshots:
[ATTACH]15806[/ATTACH][ATTACH]15807[/ATTACH][ATTACH]15808[/ATTACH][ATTACH]15809[/ATTACH]
I have not done the syscommandx actions on purpose.
I think I've got all the other relevant settings, if I've missed any settings out please let me know.
Hope you enjoy.

Edit: new USPconfig files to work with USPterm plugin (#28 page 3) allowing changing terminal colours as well.
This requires the terminal to be removed from the plugins list then put back in for colour changes to show up. If that doesn't work restart USP and repeat the above as you can see from the pic on the USPterm post (#28 page 3) it does work. :)

**[SIZE=2] Edit Again: This plugin has now been removed see post #66 on page 7 for the application version.[/SIZE]**

---

### Post by delfick on 2006-09-16
> **Malac said:**
> Okay another **"experimental"** plugin.
USPconfig
This has settings to alter USP instead of opening gconf-editor.
It works with my current set of plugins, post #26 and post #28 on page 3 of this thread.
As I don't have an untouched copy of USP 0.41.1 or the standard plugins I haven't tested it on them. Worst case you can still go back to gconf-editor. :)
Here are some screenshots:
[ATTACH]15806[/ATTACH][ATTACH]15807[/ATTACH][ATTACH]15808[/ATTACH][ATTACH]15809[/ATTACH]
I have not done the syscommandx actions on purpose.
I think I've got all the other relevant settings, if I've missed any settings out please let me know.
Hope you enjoy.

that looks awsome :D
how do i install it?

---

### Post by Malac on 2006-09-16
> **delfick said:**
> that looks awsome :D
how do i install it?
Untar the USPconfig.tar.gz into either /home/YOURUSERNAME/.usp/plugins hidden folder or as root in /usr/lib/python2.4/site-packages/usp/plugins.
And add USPconfig to the plugins list in gconf-editor at /apps/usp/plugins_list.

---

### Post by delfick on 2006-09-16
> **Malac said:**
> Untar the USPconfig.tar.gz into either /home/YOURUSERNAME/.usp/plugins hidden folder or as root in /usr/lib/python2.4/site-packages/usp/plugins.
And add USPconfig to the plugins list in gconf-editor at /apps/usp/plugins_list.

I did just that, put it into ~/.usp/plugins and added USPconfig to the plugins list and i get this (see attached screenshot)

---

### Post by Malac on 2006-09-16
> **delfick said:**
> I did just that, put it into ~/.usp/plugins and added USPconfig to the plugins list and i get this (see attached screenshot)
Can you try to put the files in /usr/lib/python2.4/site-packages/usp/plugins 
and see if that works.
If not you may have to install my other plugins as this may rely on them in a way I haven't thought of.

---

### Post by delfick on 2006-09-16
> **Malac said:**
> Can you try to put the files in /usr/lib/python2.4/site-packages/usp/plugins 
and see if that works.
If not you may have to install my other plugins as this may rely on them in a way I haven't thought of.

K then done that....at first it didn't work, but now it does :confused:

o well....good work.
Though is it possible for this to be made seperate to the menu, cause otherwise my menu is too long :p :D (not too long when i click the title, but when i'm trying to configure the panel it takes up to much room)

Also, with the USPterm plugin, can the terminal be made to use the same colours as the menu? cause as you can see from the screenshot, it looks a bit out of place.
and it doesn't like having "exit" being executed in it :p
(other than that, fantastic :D)

and are you (or chanders or whoever) able to add an option to the places plugin so that the places appear as icons in the toggle pane please?

thnx

---

### Post by Malac on 2006-09-17
Posted updated USPterm and USPconfig.
The USPterm now does colour and the USPconfig has been altered to take that into account.
So as not to upload multiple versions I've changed the originals at :
USPterm is at post #28 page 3
USPconfig is at post #32 page 4

---

### Post by chanders on 2006-09-17
> **delfick said:**
> and are you (or chanders or whoever) able to add an option to the places plugin so that the places appear as icons in the toggle pane please?

thnx

The toggle pane is not a plugin per se. It is actually PART of the USP app. If you would like to have a button plugin just so you can have buttons with icons only, just like the toggle pane, I guess we could get a plugin for that. As of now and USP2 you wouldnt be able to add anything to the togglepane not related to the workings of USP.

---

### Post by fantan on 2006-09-17
Hi malac,

Now you see, soon happened exacly I was afraid from.
I've translated the whole USPconfig.glade file, now it is totally in Hungarian in my USP, but today you did a modification (concerning to colorized USPterm), and if I would like to change to the new version of the USPconfig then I'll have to translate the USPconfig.glade file again. I did a comparison of the translated and the new files and  found quite a lot differences. The problem is that I don't know, which part of the new file cut and insert to the translated and translate jutst the inserted part insteed of translate the whole new file again.

Have you got any idea not to repeat the translation every tme after any modification?
 fantan

---

### Post by Malac on 2006-09-17
> **fantan said:**
> Hi malac,

Now you see, soon happened exacly I was afraid from.
I've translated the whole USPconfig.glade file, now it is totally in Hungarian in my USP, but today you did a modification (concerning to colorized USPterm), and if I would like to change to the new version of the USPconfig then I'll have to translate the USPconfig.glade file again. I did a comparison of the translated and the new files and  found quite a lot differences. The problem is that I don't know, which part of the new file cut and insert to the translated and translate jutst the inserted part insteed of translate the whole new file again.

Have you got any idea not to repeat the translation every tme after any modification?
 fantan
Hi fantan,
Sorry about that, attach a copy of the translated (old) USPconfig.glade file to a post here and I will update mine. Then any ones I change in the future will be with the translations.
If you don't mind, I can first send a list of text to you when/if I make any other alterations and if you could translate them, I will put them in the glade file before I upload it.

Hope this helps.

---

### Post by fantan on 2006-09-17
Hi malac,

OK, your idea is very good! Of course it will help in the future.
Now take the translated USPconfig.glade file:

[ATTACH]15894[/ATTACH]

OK, you can send a list of text to me when/if you make any other alterations and I'll translate them, and you can put them in the glade file before upload it.
Do you like this solution?

fantan

---

### Post by chanders on 2006-09-17
> **fantan said:**
> Hi malac,

Now you see, soon happened exacly I was afraid from.
I've translated the whole USPconfig.glade file, now it is totally in Hungarian in my USP, but today you did a modification (concerning to colorized USPterm), and if I would like to change to the new version of the USPconfig then I'll have to translate the USPconfig.glade file again. I did a comparison of the translated and the new files and  found quite a lot differences. The problem is that I don't know, which part of the new file cut and insert to the translated and translate jutst the inserted part insteed of translate the whole new file again.

Have you got any idea not to repeat the translation every tme after any modification?
 fantan

LOL, this is one of the reasons why I thought that translation should come later on when everything is settled down. USP is changing so fast and with so much development going on it would be very difficult to keep up with the translation... but if you guys come up with a method that works for you, great!

---

### Post by delfick on 2006-09-18
> **Malac said:**
> Posted updated USPterm and USPconfig.
The USPterm now does colour and the USPconfig has been altered to take that into account.
So as not to upload multiple versions I've changed the originals at :
USPterm is at post #28 page 3
USPconfig is at post #32 page 4
thnx for that :D much better... :D

> **chanders said:**
> The toggle pane is not a plugin per se. It is actually PART of the USP app. If you would like to have a button plugin just so you can have buttons with icons only, just like the toggle pane, I guess we could get a plugin for that. As of now and USP2 you wouldnt be able to add anything to the togglepane not related to the workings of USP.

could it be made so the toggle pane is broken into three plugins (like one of the panels, except anorexic (thin)) so that i could have the compact_system_management, USPshortcuts (what you suggested, a plugin just to display user-defined shortcuts (icon only)) and the normal plugin toggle part all in the same bar on the left?

that would be awsome

---

### Post by WiLLiE on 2006-09-18
I get the ***Plugin "USPconfig" not found!*** and ***Plugin "USBterm" not found!*** error messages.

I first extracted the files to ~/.usp/plugins, and when that didn't work, I moved them to /usr/lib/python2.4/site-packages/usp/plugins.
Still no go.

Running usp in a window from a term outputs:
```
Warning! - Icon for item not found!
Dir exist
Dir exist
Dir exist
Application added - /home/willie/.usp/applications/firefox.desktop
Application added - /home/willie/.usp/applications/mozilla-thunderbird.desktop
Application added - /home/willie/.usp/applications/gaim.desktop
Application added - /home/willie/.usp/applications/azureus.desktop
Application added - /home/willie/.usp/applications/opera.desktop
Application added - /home/willie/.usp/applications/frozen-bubble.desktop
Application added - /home/willie/.usp/applications/gcompizthemer.desktop
Application added - /home/willie/.usp/applications/listen.desktop
Application added - /home/willie/.usp/applications/totem.desktop
Place added - /home/willie/.usp/places/-home-willie-Desktop-Stuff.desktop
Place added - /home/willie/.usp/places/-home-willie-Done.desktop
Place added - /home/willie/.usp/places/-mnt-Goamania.desktop
Place added - /home/willie/.usp/places/-mnt-Moviez.desktop
Place added - /home/willie/.usp/places/-mnt-Muzax.desktop
Place added - /home/willie/.usp/places/-mnt-Picz.desktop
Place added - /home/willie/.usp/places/-mnt-Share.desktop
RuntimeError: called outside of a mainloop
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:232: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/appgeneric_font_size',self.wTree.get_widget("GenFontSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:235: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/appname_font_size',self.wTree.get_widget("NameFontSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:241: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/apps_icon_size',self.wTree.get_widget("AppIconSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:238: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/plugins/applications/height',self.wTree.get_widget("AppsHSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:244: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/border_width',self.wTree.get_widget("BorderSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:247: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/place_font_size',self.wTree.get_widget("PlaceFontSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:250: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/place_icon_size',self.wTree.get_widget("PlaceIconSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:253: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/plugins/places/height',self.wTree.get_widget("PlacesHSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:354: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/plugins/computer/settings_font_size',self.wTree.get_widget("FontSizeSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:433: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/plugins/user/settings_font_size',self.wTree.get_widget("UserFontSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:442: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/plugins/terminal/width',self.wTree.get_widget("TermWSpin").get_value())
/usr/lib/python2.4/site-packages/usp/plugins/USPconfig.py:445: DeprecationWarning: integer argument expected, got float
  self.client.set_int('/apps/usp/plugins/terminal/height',self.wTree.get_widget("TermHSpin").get_value())
New Pane
New Pane
```

I'm on edgy, and these are the available libvte packages:```
libvte-common - Terminal emulator widget for GTK+ 2.0 - common files
libvte-dev - Terminal emulator widget for GTK+ 2.0 - development files
libvte-doc - Terminal emulator widget for GTK+ 2.0 - development files
libvte9 - Terminal emulator widget for GTK+ 2.0 - runtime files
libvte-cil - CLI binding for VTE
libvte2.0-cil - CLI binding for VTE 0.11
```

So libvte9 is installed (and not libvte4 as Malac wrote).

Usp is version 0.41.

So what could the problem be here?

_My plugin_list looks like this:_
USPuser
system_management
newpane
USPconfig
places
newpane
applications
newpane
USPcomputer
newpane
USPterm

---

### Post by chanders on 2006-09-18
Try removing USPconfig and work with just USPterm. See if it loads...

---

### Post by Malac on 2006-09-18
Hi Fantan,
I think I may have come up with a solution for translating Glade files.
I have done two scripts one called gitout ([COLOR=Red]G[/COLOR]lade-[COLOR=Red]I[/COLOR]nterface-[COLOR=Red]T[/COLOR]ranslation-[COLOR=Red]OUT[/COLOR]put)
Which produces output like this :
```
./gitout USPconfig.glade
USPconfig.glade

Found 64 translatables, 0 blank entries
``` This gives an output file called USPconfig.gitoi which looks like this :
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
Search[crlf]Command:|><|
USP Button Text|><|
Hide USP Button Icon|><|
Generic Font Size|><|
Name Font Size|><|
Application Icon Size|><|
Applications Height|><|
Border Size|><|
Places Font Size|><|
Places Icon Size|><|
Places Height|><|
Hide Search Box|><|
Hide Toggle Pane|><|
Open Showing All Applications|><|
Show More Applications Button|><|
Generic Name Below Application|><|
Use Custom Colors|><|
Custom Main Color|><|
Custom Border Color|><|
Custom Heading Color|><|
Main Section|><|
Network Interface|><|
Font Size|><|
Hide Computer Information|><|
Hide Network Information|><|
Hide Date &amp; Time Information|><|
Hide Theme Information|><|
Hide Screen Resolution Information|><|
Hide Control Center|><|
Plugins|><|
Each plugin must be on a seperate line.[crlf]Please check there are NO blank spaces or lines.|><|
Settings Section|><|
Date|><|
Date Font Size|><|
Date Bold|><|
EU Date Format|><|
Show Date as String|><|
Show Day name if Date as String|><|
Character for Date Seperator|><|
Time|><|
Time Font Size|><|
Time Bold|><|
Show Time in 12 hour format|><|
Hide Seconds|><|
Date/Time|><|
USPuser|><|
(User Information)|><|
User Font Size|><|
User Name Bold|><|
USPterm|><|
(Terminal Emulator)|><|
Terminal Pixel Width|><|
Terminal Pixel Height|><|
Text Color|><|
Background Color|><|
Terminal changes require a restart.|><|
Misc|><|
Move up|><|
Move down|><|
Edit|><|
Insert separator|><|
Insert space|><|
Remove|><|
Add to favourites|><|
``` Simply type in the translations of the phrases before |><| on the same line after the |><| i.e. 
```
Search[crlf]Command:|><|Keres&#337;[crlf]parancs:
USP Button Text|><|USP gomb szövege
.............
``` Then run gitin ([COLOR=Red]G[/COLOR]lade-[COLOR=Red]I[/COLOR]nterface-[COLOR=Red]T[/COLOR]ranslation-[COLOR=Red]IN[/COLOR]put)
Which produces output like this :
```
 #./gitin USPconfig.gitoi
USPconfig.gitoi
Found 64 translatables.
``` And writes a file called USPconfig_gitoi.glade which "should" be a glade file with the labels translated.
The _gitoi part of the file can then be changed to represent the language in the file e.g. USPconfig_hu.glade.
This works with all the glade files I've tried it on but as ever I don't know if it will catch everything.(Long paragraphs,etc...)
The original file is not changed at all, so no harm no foul hopefully. :)
You can use this to extract the hungarian translations from your file too.
This gives :
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT AFTER THE |><| SYMBOLS
#DO NOT REPLACE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
Keres&#337;[crlf]parancs:|><|
USP gomb szövege|><|
USP gomb elrejtése|><|
Általános bet&#369;méret|><|
Név bet&#369;méret|><|
Alkalmazások ikonmérete|><|
"Alkalmazások" panel magassága|><|
Keretvastagság|><|
"Helyek" panel bet&#369;mérete|><|
"Helyek" panel ikonmérete|><|
"Helyek" panel magassága|><|
Keres&#337;sáv elrejtése|><|
Kapcsolópanel elrejtése|><|
Megynyitás a "Minden Alkalmazás" panellel|><|
"További alkalmazások" felirat mutatása|><|
Alkalmazások eredeti nevének mutatása|><|
Saját színek használata|><|
Saját alapszín |><|
Saját keretszín|><|
Panelnév saját színe|><|
Általános|><|
Hálózati csatoló|><|
Bet&#369;méret|><|
Számítógép információk elrejtése|><|
Hálózat információk elrejtése|><|
Dátum &amp; id&#337; információ elrejtése|><|
Téma információ elrejtése|><|
Képerny&#337;felbontás információ elrejtése|><|
Vezérl&#337;központ elrejtése|><|
Beépül&#337;k|><|
Beállítások|><|
Dátum|><|
Dátum bet&#369;méret|><|
Dátum vastag bet&#369;vel|><|
EU dátumformátum|><|
Dátum karakterláncként|><|
Nap nevének mutatása, ha a dátum karakterlánc|><|
Dátum elválasztó karakter|><|
Id&#337;|><|
Id&#337; bet&#369;méret|><|
Id&#337; vastag bet&#369;vel|><|
Id&#337; 12 órás formátumban|><|
Másodpercek elrejtése|><|
Dátum/id&#337;|><|
USP felhasználó|><|
(albert)|><|
Felhasználó bet&#369;méret|><|
Felhasználónév vastag bet&#369;vel|><|
USP terminál|><|
(Terminál)|><|
Terminál pixel-szélesség|><|
Terminál pixel-magasság|><|
A terminálértékek módosítása újraindítást kíván.|><|
Egyéb|><|
Move up|><|
Mozgatás le|><|
Szerkesztés|><|
Elválasztó vonal beszúrása|><|
Üres sor beszúrása|><|
Eltávolítás|><|
Add a Kedvencekhez|><|
``` Which means you should be able to just cut&paste any extras in from the USPconfig.gitoi file to the USPconfig_hu.gitoi file translate them then just run gitin again.

Hope this helps.
Edit:
At the moment the scripts must be in the same directory as the glade files and you must have write permission on that directory.

Edit: Uploaded a Single App Version just called GITOI which does both operations.
[ATTACH]16438[/ATTACH]

---

### Post by fantan on 2006-09-18
Hi malac,

I was out in the last hours and can read your message just now.

I don't undestand your message. My question is: where are the scripts you mention? I mean the following ones:

Glade-Interface-Translation-OUTput (giton)
Glade-Interface-Translation-INput (gitin)

I must see and evaluate them to understand exactly, how they work, how can I get the roper translation.

Reards,

antan

---

### Post by WiLLiE on 2006-09-18
> **chanders said:**
> Try removing USPconfig and work with just USPterm. See if it loads...

Nope, still the same errormessage on USPterm.

---

### Post by delfick on 2006-09-19
hey malac, i have a problem with the USPterm, it doesn't want to remember the colour i give it....

basically when i log in the term is black again when i set it to a different colour,
then i go into gconf-editor and change it back and all is good again
....
untill i logout and go back in :'(

good stuff though :D

---

### Post by Malac on 2006-09-19
> **fantan said:**
> Hi malac,

I was out in the last hours and can read your message just now.

I don't undestand your message. My question is: where are the scripts you mention? I mean the following ones:

Glade-Interface-Translation-OUTput (giton)
Glade-Interface-Translation-INput (gitin)

I must see and evaluate them to understand exactly, how they work, how can I get the roper translation.

Reards,

fantan
Hi Fantan,
Sorry I was so tired and rushed last night I forgot to attach the files to my post. 
 #-o
I've attached them now. =D>
Hope they work for you.

---

### Post by Malac on 2006-09-19
> **WiLLiE said:**
> Nope, still the same errormessage on USPterm.

Sorry WiLLiE,
I think this is my bad.
I think if the values don't exist already in gconf it is throwing up this error as it is trying to read a null instead of an int. (chanders?)
I should probably have used chanders SetGconf() function instead as I think this handles if it doesn't exist.
I will try to amend my code as soon as I have some time.

---

### Post by Malac on 2006-09-19
> **delfick said:**
> hey malac, i have a problem with the USPterm, it doesn't want to remember the colour i give it....

basically when i log in the term is black again when i set it to a different colour,
then i go into gconf-editor and change it back and all is good again
....
untill i logout and go back in :'(

good stuff though :D
Yes me too,
Sometimes it does remember and sometimes it doesn't.
So far the only work around I've found is the one you use.
I'm not sure if this is a vte problem or some sort of interaction with USP.
I will get to checking into it asap.

---

### Post by delfick on 2006-09-19
> **Malac said:**
> Yes me too,
Sometimes it does remember and sometimes it doesn't.
So far the only work around I've found is the one you use.
I'm not sure if this is a vte problem or some sort of interaction with USP.
I will get to checking into it asap.

cool :D

ur awsome! :D

---

### Post by chanders on 2006-09-19
> **Malac said:**
> Sorry WiLLiE,
I think this is my bad.
I think if the values don't exist already in gconf it is throwing up this error as it is trying to read a null instead of an int. (chanders?)
I should probably have used chanders SetGconf() function instead as I think this handles if it doesn't exist.
I will try to amend my code as soon as I have some time.

Yeah, after looking at the code it seems that the values are set correctly. SetGconf() indeed takes care of creating the key if it doesnt exist. I think the error is with USPconfig. By running USP term alone it should have setup all the keys before (dunno why he still had the problem) I will try to edit the code to fix this but   I have my hands full right now with the release of USP2 right around the corner.. Bear in mind I will be going over all the plugins with a fine teeth comb before doing the final release so if it is not done before I will do it then...

@WiLLie - try only USPterm in your pluginlist and post your error..

---

### Post by WiLLiE on 2006-09-19
> **chanders said:**
> @WiLLie - try only USPterm in your pluginlist and post your error..

ok, here it is:

```
Warning! - Icon for item not found!
Dir exist
Dir exist
Dir exist
Application added - /home/willie/.usp/applications/firefox.desktop
Application added - /home/willie/.usp/applications/mozilla-thunderbird.desktop
Application added - /home/willie/.usp/applications/gaim.desktop
Application added - /home/willie/.usp/applications/azureus.desktop
Application added - /home/willie/.usp/applications/opera.desktop
Application added - /home/willie/.usp/applications/frozen-bubble.desktop
Application added - /home/willie/.usp/applications/gcompizthemer.desktop
Application added - /home/willie/.usp/applications/listen.desktop
Application added - /home/willie/.usp/applications/totem.desktop
Place added - /home/willie/.usp/places/-home-willie-Desktop-Stuff.desktop
Place added - /home/willie/.usp/places/-home-willie-Done.desktop
Place added - /home/willie/.usp/places/-mnt-Goamania.desktop
Place added - /home/willie/.usp/places/-mnt-Moviez.desktop
Place added - /home/willie/.usp/places/-mnt-Muzax.desktop
Place added - /home/willie/.usp/places/-mnt-Picz.desktop
Place added - /home/willie/.usp/places/-mnt-Share.desktop
New Pane
```

And in gconf-editor, under usp->plugins, I have a terminal section.
The default values were height:0 and width:0, which I changed to 30 (both).

---

### Post by fantan on 2006-09-20
Hi malac,

I've downloaded the GITOI.tar.gz file and did the translation by your proposal. Success! It works fine.
Now I have the last version of the USPconfig plugin working with translated to Hungarian surface. But the text and background color of the new USPterm doesn't want to change. It doesn't matter, I don't use this terminal at all.

Best regards,

fantan

---

### Post by Malac on 2006-09-20
> **fantan said:**
> Hi malac,

I've downloaded the GITOI.tar.gz file and did the translation by your proposal. Success! It works fine.
Now I have the last version of the USPconfig plugin working with translated to Hungarian surface.
Hi fantan
Glad it worked. You should be able to translate _all_ your glade files now with these scripts for a totally hungarian set of apps. :)
> **fantan said:**
>  But the text and background color of the new USPterm doesn't want to change. It doesn't matter, I don't use this terminal at all.
As delfick and I found out the USPterm colours only take effect if you remove USPterm from the plugins list then add it back once USP has started. I still don't know why this is. Whether it is a vte problem or some weird interaction with USP.
Hopefully I will get it soughted soon.

---

### Post by Malac on 2006-09-20
Hi delfick,
I've posted an updated USPterm at (post 28 page 3) which I *think* now remembers the colour settings.
I think it's a vte issue about order of commands not a USP interaction.
Can you try it out and see if it works for you.

---

### Post by delfick on 2006-09-20
> **Malac said:**
> Hi delfick,
I've posted an updated USPterm at (post 28 page 3) which I *think* now remembers the colour settings.
I think it's a vte issue about order of commands not a USP interaction.
Can you try it out and see if it works for you.

doesn't seem to be working here :'(

I even restarted the computer.........

---

### Post by Malac on 2006-09-20
> **delfick said:**
> doesn't seem to be working here :'(

I even restarted the computer.........
Damn after all that effort I did a trawl of the net and it looks like it's a bug in vte.
If you Add to Panel then remove quickly then add again repeatedly about 1 out of 4 times it's the right colours, the rest it's not.
I'll see if there is a more stable emulator out there.

---

### Post by Malac on 2006-09-21
[SIZE=2]To any and all,
I've made an app out of my translation scripts.
It's called GITOI and info can be found here:
[http://www.ubuntuforums.org/showthread.php?t=262139](http://www.ubuntuforums.org/showthread.php?t=262139)

Sorry for the "minor" hijack. :)[/SIZE]

---

### Post by ayoli on 2006-09-22
wow these plugins look promising :)
would be cool to to have ability to see tasks and appointments as in the gnome clock applet.

---

### Post by Malac on 2006-09-22
> **ayoli said:**
> wow these plugins look promising :)
would be cool to to have ability to see tasks and appointments as in the gnome clock applet.
see my USPcalendar for a slight mod. as it opens up evolution like the gnome clock.
If this is what you mean. :)

---

### Post by ayoli on 2006-09-22
> **Malac said:**
> see my USPcalendar for a slight mod. as it opens up evolution like the gnome clock.
If this is what you mean. :)
i saw that it opens evolution but i didnt mean that (see screenshot) is shown on simple clik on the clock applet.
edit: oops, forgot screenshot, here it is:
[IMG]http://ayozone.org/tmp/Capture.png[/IMG]

---

### Post by Malac on 2006-09-23
Updated USPuser plugin to allow placing username below picture and show/hide logged on time.

/app/usp/plugins/user/name_below
/app/usp/plugins/user/hide_logged_on

Updated USPconfig Application too, I will no longer be maintaining the plugin format of USPconfig. so if you want the app here it is.

Edit : USPconfig App is now at Page 8 Post #73.

---

### Post by WiLLiE on 2006-09-24
Ok, got the terminal plugin to work.
It seemes that python-vte must be installed.

---

### Post by delfick on 2006-09-24
> **WiLLiE said:**
> Ok, got the terminal plugin to work.
It seemes that python-vte must be installed.


not here, python-vte is already installed....

---

### Post by WiLLiE on 2006-09-24
I mean working at all. ;) 
Colors is also a problem here.

---

### Post by delfick on 2006-09-24
> **WiLLiE said:**
> I mean working at all. ;) 
Colors is also a problem here.

ok then.....

congratulations on getting it working then :D

---

### Post by Malac on 2006-09-24
Scratch the "it's a vte bug" thing.
Old bug apparently it's been sorted and it was in another colour function.

Anyone any ideas as I am out.:-k

If I run the exact same vte code in a seperate app it works perfect everytime, right colours, right size.
If I put the same vte code in the USPterm plugin it doesn't work unless you add it after USP has started.
I can only assume that it is tied in some way to the way USP displays the individual plugins.

Slightly odd behaviour too with USPterm, if you add USP using the Add to Panel then remove it, then quickly add it back, the first time it is the default colours but the second(,third, fourth,.....) time it is the right colours.
It is like there is some time delay if you wait five minutes then re-add USP to the panel it's back to the default colours for the terminal.

I am truly flummoxed. :confused:

---

### Post by chanders on 2006-09-24
> **Malac said:**
> Scratch the "it's a vte bug" thing.
Old bug apparently it's been sorted and it was in another colour function.

Anyone any ideas as I am out.:-k

If I run the exact same vte code in a seperate app it works perfect everytime, right colours, right size.
If I put the same vte code in the USPterm plugin it doesn't work unless you add it after USP has started.
I can only assume that it is tied in some way to the way USP displays the individual plugins.

Slightly odd behaviour too with USPterm, if you add USP using the Add to Panel then remove it, then quickly add it back, the first time it is the default colours but the second(,third, fourth,.....) time it is the right colours.
It is like there is some time delay if you wait five minutes then re-add USP to the panel it's back to the default colours for the terminal.

I am truly flummoxed. :confused:

I am looking into it. I am not sure why it wouldnt work though... Will post my findings. Right now I am just polishing up USP2 and trying to get as much requests in before release...

---

### Post by Malac on 2006-09-24
> **chanders said:**
> I am looking into it. I am not sure why it wouldnt work though... Will post my findings. Right now I am just polishing up USP2 and trying to get as much requests in before release...
Cheers chanders,
I better post my latest version of the USPconfig App then. :)
[ATTACH]16268[/ATTACH]

**New Version now posted at post #89 page 9.**

---

### Post by Malac on 2006-09-25
I  think I've found a patch for the USPterm remembering colours.
I've attached a new copy to post#28 page 3
If someone could download and install it then reboot and let me know if it works for them.
I've also added a background picture if you want.
Thanks in advance.

---

### Post by delfick on 2006-09-25
> **Malac said:**
> I  think I've found a patch for the USPterm remembering colours.
I've attached a new copy to post#28 page 3
If someone could download and install it then reboot and let me know if it works for them.
I've also added a background picture if you want.
Thanks in advance.

Well done! :D

that fixed it :D

thnx :D



i don't know if i've asked it before, probably have, but can the USPTerm have real transparency like gnome-terminal has?

---

### Post by Malac on 2006-09-25
> **delfick said:**
> Well done! :D

that fixed it :D

thnx :D

i don't know if i've asked it before, probably have, but can the USPTerm have real transparency like gnome-terminal has?
You'll be pleased to know I'm already looking into it. :)

---

### Post by delfick on 2006-09-25
> **Malac said:**
> You'll be pleased to know I'm already looking into it. :)

AWSOME!!! :D

ur my hero :D :p

---

### Post by Uncle Spellbinder on 2006-09-25
> **Malac said:**
> Cheers chanders,
I better post my latest version of the USPconfig App then. :)
[ATTACH]16268[/ATTACH]

Stupid question, I suppose. How do I get USPconfig to work?

---

### Post by Malac on 2006-09-25
> **Uncle Spellbinder said:**
> Stupid question, I suppose. How do I get USPconfig to work?
Untar the files into /usr/bin/ or /usr/sbin (you need to be root to do this).
At the moment both the files need to be in the same directory.
Make USPconfig executable if it isn't already.

Then run USPconfig from a command line.(note the capital letters, you can change the filename to uspconfig if it bothers you)
Or
Create a launcher in the menu pointing to /[COLOR=Gray]*<where-you-put-the-files*>[/COLOR]/USPconfig

I put an entry in with Alacarte then dragged that onto the USP Applications Menu.
See bottom of attached picture.
[ATTACH]16341[/ATTACH]
Hope this helps.
And just in case anyones interested here is terminal with a picture.
[ATTACH]16342[/ATTACH]

Edit: If, in the unlikely event :), this doesn't work please run from the command line and post any output and I'll try to sort it. Thanks.

---

### Post by Uncle Spellbinder on 2006-09-25
Thanks, *Malac*. Working great!

---

### Post by Malac on 2006-09-26
:oops: Sorry,
Forgot the "Edit" button for plugin names in the previous USPconfig upload.
I've uploaded a new version to post #73 page 8. :oops:

And here is the GITOI translation file.
If anyone wants to translate the phrases, putting the translated phrase after the |><| symbol, then post the result.
I will then run GITOI to create a translated Glade file.

Like so...
```
USP Button Text|><|
Hide USP Button Icon|><|
```becomes this for French translations (please excuse my French :) )
```
USP Button Text|><|Texte de Bouton USP
Hide USP Button Icon|><|Pour Se Cacher l'Icône de Bouton USP
```

---

### Post by Uncle Spellbinder on 2006-09-26
> **Malac said:**
> :oops: Sorry,
Forgot the "Edit" button for plugin names in the previous USPconfig upload.
I've uploaded a new version to post #73 page 8.

Thanks. Got it.  :D

---

### Post by ayoli on 2006-09-26
> **Malac said:**
> 
And here is the GITOI translation file.
If anyone wants to translate the phrases, putting the translated phrase after the |><| symbol, then post the result.
I will then run GITOI to create a translated Glade file.

here is a first try of french translation.

edit: updated, done some spell check.

edit: added one missing translation.

---

### Post by fantan on 2006-09-26
Hi malac,

And here is the Hungarian translation of the USPconfig.glade.

I made it based on the last USPconfig package included in your post #73 page 8. I did the translation with your gitoi script.

Best regards,

fantan

---

### Post by Malac on 2006-09-27
> **ayoli said:**
> here is a first try of french translation.
Here is the French translated Glade file.
It seems to have worked, can you let me know if it hasn't.
I may have to change some of the stock buttons to use actual labels so they translate too, I don't know how gnome handles things like the Save button in French.

To use this change the two lines near the top of USPconfig file that read:
```
self.gladefile=os.path.join(os.path.dirname(__file__),"USPconfig.glade")
```To :
```
self.gladefile=os.path.join(os.path.dirname(__file__),"USPconfig_fr.glade")
```> **fantan said:**
> Hi malac,

And here is the Hungarian translation of the USPconfig.glade.

I made it based on the last USPconfig package included in your post #73 page 8. I did the translation with your gitoi script.

Best regards,

fantan
Thanks fantan, glad it's working for you.

---

### Post by ayoli on 2006-09-27
> **Malac said:**
> Here is the French translated Glade file.
It seems to have worked, can you let me know if it hasn't.
I may have to change some of the stock buttons to use actual labels so they translate too, I don't know how gnome handles things like the Save button in French.

it works :) save button is translated well to my default locale (fr). i see i have some spellcheck and translation improvements to do. I'll post the new file soon.

edit: updated gitoi file with little corrections in previous [post #83]("http://www.ubuntuforums.org/showpost.php?p=1547649&postcount=83")

---

### Post by Malac on 2006-09-27
Sorry it took so long ayoli but I have uploaded a new USPconfig_fr.glade file to post #85 for you to check.
It actually turned up a bit of a bug in the GITOI app which I had to sort out, which is why it took so long. but it is now fixed.(I hope). :)

---

### Post by ayoli on 2006-09-28
> **Malac said:**
> Sorry it took so long ayoli but I have uploaded a new USPconfig_fr.glade file to post #85 for you to check.
It actually turned up a bit of a bug in the GITOI app which I had to sort out, which is why it took so long. but it is now fixed.(I hope). :)

ok, i've updated again my gitoi file in post #83 above (added a missing translation for "hide toggle panel).
i also tried your gitoi app new version, it worked like a charm ;) so, i join here the translated glade file.

---

### Post by Malac on 2006-10-02
Yet another Plugin :)
USPnotes, a sort of quick notes type thing for jotting down text or pasting quickly without opening gedit or something.
[ATTACH]16704[/ATTACH]
Save button writes the file to /home/"user"/Desktop/
The saved filename is in the form yyyymmdd-hh:mm:ss
e.g. 20061002-10:58:03
If you provide a filename in the box this will be prepended to the front of the filename 
e.g. SomeText20061002-10:58:03
Clear Button clears the pad and filename field.

GConf Keys:
/apps/usp/plugins/notes/height
/apps/usp/plugins/notes/width
[SIZE=2][/SIZE]Edit:
I will be adding this to USPconfig as soon as I can.

[B]EDIT:
[/B]Get them here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by Malac on 2006-10-02
USPCalc Plugin
Simple Calculator for USP
No Gconf Settings.
[ATTACH]16733[/ATTACH]
[SIZE=2][/SIZE]Get it here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by chanders on 2006-10-02
^^ One I will be personally using

---

### Post by Malac on 2006-10-03
***Very Basic*** Recent Documents Plugin :smile:

USPrecent
[ATTACH]16816[/ATTACH]
Gconf Keys:
/apps/usp/plugins/height
/apps/usp/plugins/width
/apps/usp/plugins/recent_font_size
/apps/usp/plugins/num_entries

Get it here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by delfick on 2006-10-03
I'm starting to run out of room for these plugins :p

would it be possible to make it so that certain panels are higer than other panels ? 

so the panel would be a bit like the attached screenshot 

if that makes sense.......


hmmmmm, i can't wait till the day real transparency is possible for the usp, then haven't it so big would be no problem at all :D (not that i mind that much :p)

---

### Post by Uncle Spellbinder on 2006-10-04
> **delfick said:**
> ...i can't wait till the day real transparency is possible for the usp, then haven't it so big would be no problem at all.

It *is* possible, when using Beryl. :D

---

### Post by delfick on 2006-10-05
> **Uncle Spellbinder said:**
> It *is* possible, when using Beryl. :D

is that real transparency or just the whole thing transparent?

real transparency being when everything but the text is transparent

look at this [http://delfick755.googlepages.com/panel.jpg](http://delfick755.googlepages.com/panel.jpg)

---

### Post by DerSkw on 2006-10-05
> **delfick said:**
> is that real transparency or just the whole thing transparent?

real transparency being when everything but the text is transparent

look at this [http://delfick755.googlepages.com/panel.jpg](http://delfick755.googlepages.com/panel.jpg)

nope your wrong.
real transparency is when everything in the background is visible through the transparent area.
false transparency is when only the background is visible through the area, but other things like windows are not.

// EDIT: sry didn't see the terminal in the picture
though it is a real transparency

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

### Post by chanders on 2006-10-06
I have requested a sticky so hopefully we should see it show up in a few hrs ;-)

---

### Post by Malac on 2006-10-07
> **chanders said:**
> I have requested a sticky so hopefully we should see it show up in a few hrs ;-)
Cheers :)

---

### Post by Malac on 2006-10-07
Okay finally fixed the calendar to open evolution on the date clicked.
The updated USPcalendar is available here:
[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by Malac on 2006-10-09
USPremind and USPcalrem (a combined USPcalendar & USPremind)
are available here:
[http://www.ubuntuforums.org/showthread.php?t=272372&page=2]("http://www.ubuntuforums.org/showthread.php?t=272372&page=2")

---

### Post by ayoli on 2006-10-09
> **Malac said:**
> USPremind and USPcalrem (a combined USPcalendar & USPremind)
are available here:
[http://www.ubuntuforums.org/showthread.php?t=272372&page=2]("http://www.ubuntuforums.org/showthread.php?t=272372&page=2")

hey !
USPcalrem quite simply rocks, this is the one i wanted :D
thx a lot

---

### Post by Malac on 2006-10-09
> **ayoli said:**
> hey !
USPcalrem quite simply rocks, this is the one i wanted :D
thx a lot

You're Most Welcome, :D

---

### Post by Malac on 2006-10-14
Updated USPterm with transparency and USPconfig to take this into account.
Get them here :
[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

Can someone let me know if the transparency works on beryl/compiz/xgl/whatever as I have never got any of these to work so I don't know.:(

---

### Post by delfick on 2006-10-14
hehehe, nice stuff !

look at the Quick notes part of the usp in the attached screenshot.....(i couldn't resist spreading a message that way again :D)

hmmm, for a second there i thought it was real transparency............i take it that still isn't possible??....:D (the wishful thinking is starting to kick in again that it is possible :D)

---

### Post by Malac on 2006-10-14
> **delfick said:**
> 
hmmm, for a second there i thought it was real transparency............i take it that still isn't possible??....:D (the wishful thinking is starting to kick in again that it is possible :D)
Apparently it requires some sort of hack/patch to libvte to get real transparency which I haven't been able to track down yet. I've no idea when/whether it will be incorporated in future releases of the vte/gnome-terminals as a feature as suggested by some of the blogs I've seen.

As for the whole USP panel transparent without beryl, not sure. I'm only using built in "features" of the GTK widgets so activating terminal transparency wasn't that difficult it just required that precious commodity, at the moment, to do it.......spare time. :)

---

### Post by delfick on 2006-10-14
> **Malac said:**
> Apparently it requires some sort of hack/patch to libvte to get real transparency which I haven't been able to track down yet.
you will eventually :D
>  I've no idea when/whether it will be incorporated in future releases of the vte/gnome-terminals as a feature as suggested by some of the blogs I've seen.

soon :D (wishful thinking)

> As for the whole USP panel transparent without beryl, not sure. I'm only using built in "features" of the GTK widgets so activating terminal transparency wasn't that difficult it just required that precious commodity, at the moment, to do it.......spare time. :)

ur brilliant work is appreciated enough that you don't have to feel pressurred to do this, so don't worry if you can't work on it cause of other things that may constrict your time :D

---

### Post by Malac on 2006-10-17
Uploaded a new version of USPconfig to here.
This was a bug fix for the plugins list in USPconfig re-populating on certain setting changes. It should not have affected USP itself at all.

[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

---

### Post by Malac on 2006-10-25
Bug fix USPrecent, now populates on startup and handles spaces in the URI line.

[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

N.B> An Edgy version of this is on the way as edgy handles recent docs differently.

---

### Post by Malac on 2006-10-25
Okay completely re-coded the recent documents plugin USPrecent to use the Gnome Recent Manager and this should work.
I have a new version to the USPrecent post (URL above) as I haven't tested this on Dapper there is still the original one there called USPrecent_Dapper.tar.gz
If someone running Dapper could let me know if the new one works for them I'll remove the _Dapper version.
Thanks.

---

### Post by Malac on 2006-11-01
New plugin USPclock analog clock. Also added this functionality to USPtime.
Get it here:
[http://www.ubuntuforums.org/showthread.php?p=1699272#post1699272](http://www.ubuntuforums.org/showthread.php?p=1699272#post1699272)

---

### Post by Malac on 2006-11-02
New USPuser plugin which allows custom/animated user picture.
Updated USPconfig Application to allow for this.
GConf-Editor and USPconfig are the only way to change this value as the face chooser does not allow animation.
Get it here:
[http://www.ubuntuforums.org/showthread.php?t=272372]("http://www.ubuntuforums.org/showthread.php?t=272372")

---

### Post by delfick on 2006-11-02
> **Malac said:**
> New USPuser plugin which allows custom/animated user picture.
Updated USPconfig Application to allow for this.
GConf-Editor and USPconfig are the only way to change this value as the face chooser does not allow animation.
Get it here:
[http://www.ubuntuforums.org/showthread.php?t=272372]("http://www.ubuntuforums.org/showthread.php?t=272372")

awsome :D (i recieved your message, thnx :D)

unfortunately i have exams next week (one every day) so i'm busy studying (infact i probably shouldn't even be on my computer, but a break is important every once in a while :D)

i just quickly made a mpeg of my avatar wobbling, which doesn't want to work with the plugin...

whether that's because the mpeg is too big (as in the height and width of the movie) or whether the plugin doesn't accept mpeg i'm unsre and i don't have enough time to play around with it :'(

but thankyou for making this :D 
i'm looking forward to playing around with it when my exams finish :D

---

### Post by Malac on 2006-11-02
> **delfick said:**
> awsome :D (i recieved your message, thnx :D)

unfortunately i have exams next week (one every day) so i'm busy studying (infact i probably shouldn't even be on my computer, but a break is important every once in a while :D)

i just quickly made a mpeg of my avatar wobbling, which doesn't want to work with the plugin...

whether that's because the mpeg is too big (as in the height and width of the movie) or whether the plugin doesn't accept mpeg i'm unsre and i don't have enough time to play around with it :'(

but thankyou for making this :D 
i'm looking forward to playing around with it when my exams finish :D
I've only tried it with animated .gif files I don't think an .mpeg will work as strictly speaking that's a movie not an animated graphic.
Can you save your file in .gif or .png animated form?

---

### Post by delfick on 2006-11-02
> **Malac said:**
> I've only tried it with animated .gif files I don't think an .mpeg will work as strictly speaking that's a movie not an animated graphic.
Can you save your file in .gif or .png animated form?

i'm not sure....

---

### Post by Malac on 2006-11-08
New USPweb
Mozilla Browser Bookmarks
Get it here:
[http://www.ubuntuforums.org/showthread.php?p=1731023#post1731023](http://www.ubuntuforums.org/showthread.php?p=1731023#post1731023)

---

### Post by delfick on 2006-11-10
> **Malac said:**
> New USPweb
Mozilla Browser Bookmarks
Get it here:
[http://www.ubuntuforums.org/showthread.php?p=1731023#post1731023](http://www.ubuntuforums.org/showthread.php?p=1731023#post1731023)

nice :D

only problem is that i put the files into the ~/.usp/plugins folder and then add "USPweb" to the list and it doesn't recognise it as being there......

o well, i don't have enough room in my menu for anything else anyway :p :D

---

### Post by Malac on 2006-11-11
> **delfick said:**
> nice :D

only problem is that i put the files into the ~/.usp/plugins folder and then add "USPweb" to the list and it doesn't recognise it as being there......

o well, i don't have enough room in my menu for anything else anyway :p :D
It may be that your bookmarks.html file is not in the expected location or profiles.ini is in a different format than expected. I based this on my systems layout which I assumed was default. I have uploaded a new version which should trap whether the error is in finding the file and display this in the plugin. If it is, there is now an option to add the location manually to  /apps/usp/plugins/internet/bookmark_file.
I've also updated USPconfig to allow for this.

---

### Post by huviduc on 2006-11-30
edit: previous remarks removed

---

### Post by vitae on 2006-12-19
hi malac,

i like your calrem plugin very much. i am used to view my tasks with the clock applet for evolution.

my suggestion is to make the calrem plugin also to behave like the clock applet.
for instance it is very useful and important that the days are black marked if there is a task. so you don`t have to click every day to see if there is something.

thnx 4 your work :)

---

### Post by Malac on 2006-12-19
> **vitae said:**
> hi malac,

i like your calrem plugin very much. i am used to view my tasks with the clock applet for evolution.

my suggestion is to make the calrem plugin also to behave like the clock applet.
for instance it is very useful and important that the days are black marked if there is a task. so you don`t have to click every day to see if there is something.

thnx 4 your work :)
Hi vitae,
Glad you like the plugin.
I will get round to it as soon as I can. Though at the moment USP2config and plugins are taking most of my free time.

---

