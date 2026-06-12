---
title: "Guide to USP2 SVN"
date: 2007-02-19
forum: Ubuntu System Panel
---

### Post by kobewan on 2007-02-19
[This guide is now deprecated; the newest information should be available at the [wiki]("http://code.google.com/p/ubuntu-system-panel/w/list"). Feel free to post any comments or potential improvements in this topic though]

Since there isn't exactly a central place to easily acquire information about USP, I decided to write this little manual to hopefully help some people out. This guide is meant for the SVN version, which will always be the most up-to-date one. 

The guide is going to be laid out in this order:

[Post 2]("http://ubuntuforums.org/showthread.php?p=2178607#post2178607") : General Information
[Post 3]("http://ubuntuforums.org/showthread.php?p=2178643#post2178643") : Installation
[Post 4]("http://ubuntuforums.org/showthread.php?p=2178646#post2178646") : Plugin Information
[Post 5 ]("http://ubuntuforums.org/showthread.php?p=2178649#post2178649"): Tabs
[Post 6]("http://ubuntuforums.org/showthread.php?p=2178650#post2178650") : Themes
[Post 7]("http://ubuntuforums.org/showthread.php?p=2178651#post2178651") : Troubleshooting

The opening post will serve as an index, referencing posts that have miscellaneous tips and tricks.

---

### Post by kobewan on 2007-02-19
1. What is USP and why use it?

1a. What is USP?

USP (short for Ubuntu System Panel) is an alternative (and hopefully an eventual replacement) to Ubuntu's "Main Menu" button (for those more familiar with Windows, its basically a replacement "Start" button/menu). 

1b. Why should I use USP?

So why use would people want to use it instead of the standard menu? It has a host of features that make it much better than the main menu, including support for quick searching of all your installed applications, plugins, tabs and themes (to name a few). It can be used for quick access to more things than just your applications. It's also fully customizable, so you can tweak it to look pretty much exactly like you want it to. Since pictures are worth a thousand words, here are some screenshots of what mine looks like:

[[IMG]http://img02.picoodle.com/img/img02/7/2/19/t_tab1m_7e15474.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/19/f_tab1m_7e15474.png)
[[IMG]http://img02.picoodle.com/img/img02/7/2/19/t_tab2m_20fbaca.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/19/f_tab2m_20fbaca.png)
[[IMG]http://img02.picoodle.com/img/img02/7/2/19/t_tab3fullm_8e82097.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/19/f_tab3fullm_8e82097.png)

If you don't like the way that it looks, remember that you can customize it any way that you please, including creating your own skins for it.

1c. Why should I use the SVN version over USP1 or the .deb?

The SVN version should always be the most up-to-date one, with new patches and fixes applied to it regularly. It supports several new features over USP1, and lots of bugs fixed as. If you use on Ubuntu Edgy, it is very stable -- don't be fooled by the pre-alpha status. It may not work for you under Feisty; a lot of work is being put into it to iron out all the issues. As it is, there are many people who have it working just fine with Feisty. 

1d. What USP won't do (yet). 

-- USP, as far as I know, isn't compatible with any environment except for GNOME. 
-- Certain plugins won't work with Dapper, but otherwise it should be fine.
-- Feisty support is being worked on.
-- USP isn't the most lightweight menu ; it will use about 10-20MB of RAM. That said, most systems will not mind it and it really is worth its weight.
-- Full alpha transparency support is NOT going to be available for USP2. You'll have to wait for USP3 for this.
-- It will not solve hunger or cure cancer. However, from what I understand, the full specs of USP3 haven't been finalized yet so you never know :D.

---

### Post by kobewan on 2007-02-19
2. Installation

Now all you need to do is make sure that you have Subversion, so that you can download the SVN. Run this command: ```
sudo apt-get install subversion
```

Alright, now cd to the directory that you want to download it to. For example, I like to use ~/Downloads/SVN , so that's where I'll go: ```
cd ~/Downloads/SVN
```

now run ```
 svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
```

This should download all the correct files that you need. Now, put in ```
 cd ubuntu-system-panel
``` and then ```
./usp_update install fresh
``` That should install it for you, as well as clearing out the old version! Just a little note here, whenever you want to get the latest SVN version of USP, come back to this directory and type:```
./usp_update update
``` You can also uninstall USP by coming back to this directory and typing in ```
./usp_update uninstall
``` (if you want to uninstall completely, including removing your settings, put in "./usp_update uninstall complete" instead.)

Before you finally get to add the applet to your panel, do this: ```
killall gnome-panel
``` Now you can right click on any empty panel area, and select 'Add to Panel'. You should see 'Ubuntu System Panel' under the 'Miscellaneous' group.

---

### Post by kobewan on 2007-02-19
One of the coolest features of USP is that it has full support for plugins. These can be added in any order that you want, to any place that you. You only have to enable the plugins that you want to use, so you have total control over how your menu will look. These plugins also provide extra functionality which is not available in the standard menu. You can stick all kinds of things into your menu, from a shortcut list to a calculator and even an embedded terminal! Each plugin can also be minimized to the sidepane, so you can customize your look on the fly.

In order to configure all these things, you still have to do one complicated task: right click on the USP button, and click on Preferences (you can configure USP by typing 'uspconfig' in the terminal. In the new window that pops up, there should be a list called "Plugins". This can be used to do all the things that I described above. First, an explanation on how the list works. By default, the plugins will stack so that whatever is at the top of this list will be at the top of the menu. Plugins are also arranged in the menu according to a thing called panes ; this is what stops them from being one large vertical stack and lets them be displayed horizontally. A pane can be created by adding an entry to the list with a value of "newpane" (without the quotation marks). Everything list below the newpane entry will be displayed in a new pane. Be sure to click on the 'Save' button when you're done playing with the list.

For examples, look at the screenshots (which show both the configurations, and the appearance of the menu after the config is applied):
[[IMG]http://img02.picoodle.com/img/img02/7/2/19/t_nopanesm_0b7c55e.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/19/f_nopanesm_0b7c55e.png)
[[IMG]http://img02.picoodle.com/img/img02/7/2/19/t_3panesm_196d260.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/2/19/f_3panesm_196d260.png) 

The layout is fully up to you. You can mix-and-match in any way that you want, putting as many plugins as you like, divided into any number of panes. Also worth noting is the fact that you can minimize plugins to the sidepane. To do this, just click on the plugin title (i.e. the big, bold writing that says Applications or Recent etc.) To unminimize it, just click on the little logo in the sidepane. It will unminimize back to the same location as it minimized from.

Here is a list of the default plugins included with USP2. If you want to use one, make sure to spell and punctuate it in the same way:

(for screenshots, look [here]("http://ubuntuforums.org/attachment.php?attachmentid=25667&d=1171884176"))

1. **uspuser** -- Displays some information about the user that is currently logged in. This includes your login photo, username, and when you logged in. You can also configure it so that it shows a photo which is different from your login photo. It can be used to show an animated .gif . If you are using USP on Feisty, make sure that you have a login photo selected for your user account (System-->Preferences-->Login Photo) or USP won't work.
2. **system_management** --- a small menu which contains buttons for "Install Software", "Control Center", "Lock Screen" and "Quit"
3. **applications** --- the meat of the program, its a way to quickly get to all your applications. The best part of it is that it has a quick search feature built-in. As soon as you start typing, the the application list will start narrowing down based on the search. It searches not only the listed name of the application, but also its description and its command (so, for instance, typing 'gco' will show the name of "Configuration Editor").
4. **shortcuts** --- provides a list of quick shortcuts to anything. To add a shortcut, you have to first pin the menu. The pin button is the iconless button in the sidepane. If your sidepane is hidden, minimize any plugin to bring it up. Once you have pinned the menu, drag an icon from anywhere into the shortcuts plugin. The first icon is a little hard to drag, since the area that you have to drag it into is very small. The area is right underneath the plugin title. If you are dragging in the right place, a thin black line will appear.
Note: If you drag an icon for a **file** from Nautilus (not a folder), it probably won't work. Right click on the shortcut, and then select edit. Now edit  'exec' field for the correct program needed to open it. For example, an HTML document will need you to replace the part of the command that says 'nautilus' with 'firefox', and for a pdf file you should replace 'nautilus' with 'evince'. 
5. **places** --- provides quick shortcuts to either your Nautilus bookmarks, or a standard set of places.
6. **computer** --- this is the plugin with the title of "Settings". It allows easy access to a few useful system settings.
7. **recent** --- a list of either recent documents, or recent applications launched from USP. This plugin is not supported for Dapper.

You can also find extra plugins [here]("http://ubuntuforums.org/showpost.php?p=1981614&postcount=2"). I believe that these plugins are a little less stable than the default ones, but they are still quite stable. More information can be found by look at *the relevant plugin* [here]("http://ubuntuforums.org/showthread.php?t=272372"). 
NOTE: Please don't try downloading the plugins in the previous link (the information link). They are for USP1. Only download your USP2 plugins from [here]("http://ubuntuforums.org/showpost.php?p=1981614&postcount=2"). 

Screenshots of the Extra/Add-On plugins: (worthy of noting: these are all running on Feisty, so USP is able to work fine on Feisty)

1. [Extra/Add-on Plugins ]("http://ubuntuforums.org/attachment.php?attachmentid=25668&d=1171884176")
2. [Internet Bookmarks]("http://ubuntuforums.org/attachment.php?attachmentid=25669&d=1171884176")
3. [Calendar Stuff]("http://ubuntuforums.org/attachment.php?attachmentid=25670&d=1171884176")
4. [All together]("http://ubuntuforums.org/attachment.php?attachmentid=22620&d=1168363901")

---

### Post by kobewan on 2007-02-19
USP2 now supports having tabs! These are extremely useful if you have a laptop or some other low resolution display. Tabs are made in the plugins list in USP Configuration. All you have to do is add an entry with value "newtab" (without the quotes) into the plugins list where you would like a tab to start. To name the tab, make the value like this: "newtab=what-ever-you-want" (without the quotes). To see it in action:
[Screenshot-USP - Configuration]("http://ubuntuforums.org/attachment.php?attachmentid=25278&d=1171483745")
Which gives: [Screenshot-System Panel]("http://ubuntuforums.org/attachment.php?attachmentid=25278&d=1171483745")

Also, tabs now have the ability to have icons along with (or instead of) their titles. This is done by putting the icon name in square brackets '[]' either before or after the text. For example:> newtab=Standard Plugins[gnome-settings.png]
<some plugins and newpanes here>
newtab=[add.png]Extra/Add-On Plugins
<some plugins and newpanes here>
newtab=Internet
<some plugins and newpanes here>
newtab=[tux]
<some plugins and newpanes here>
Would give [this]("http://ubuntuforums.org/attachment.php?attachmentid=25333&d=1171532741"). 

If you just use 'newtab', without any name, the tab will be given a number. Also, full paths to icons can be used too. For example, this is perfectly valid: "newtab=Extra/Add-On Plugins[/home/dave/add.png]"

---

### Post by kobewan on 2007-02-19
USP does not have its own skinning engine, it uses standard GTK 2.x themes. The advantage of this is that there are obviously already a great deal of themes available. You can find several at:

[http://gnome-look.org/](http://gnome-look.org/)

As a matter of fact, most people should already have several GTK2.x themes installed. Open up Theme Manager (just type in 'theme' in USP to find it quickly :D) and click on Theme Details. All the themes that are listed in the "Controls" tab can be applied to USP. To apply them, all you have to do is open up USP Configuration and type the name of the theme that you want to use in the "USP Theme" field.  Make sure to spell it correctly and punctuate it exactly the same as it should be (including upper and lower case letters). 

Some themes will require you to install "gtk2-engines-pixbuf" from Synaptic to display properly.

As far as I know, there has only been one theme so far that has been made exclusively for USP.  You can find it at this [thread]("http://ubuntuforums.org/showthread.php?t=357368"). That thread is also an excellent place to start if you want to make your own theme, since the attached theme (USP-solidWHITE) only includes the files that USP needs (as opposed to the extra files in GTK2.X that USP never uses).  Simply make a copy of the theme, rename it, and then replace the image files with your own appropriate ones.

(The theme in my screenshots is MacOS-X Aqua Theme from GNOME-Look. Even though I generally don't like the way that Macs look, the theme works excellently for USP.)

---

### Post by kobewan on 2007-02-19
**Before you post for help in the forums, please run ```
usp run-in-window
``` This should print out error messages that will be helpful in finding out what the problem is.**

If you changed a setting but nothing happened, try ```
killall gnome-panel
```

Other bugs/errors:

1. *Wine program not launching* - [http://ubuntuforums.org/showpost.php?p=2175127&postcount=91]("http://ubuntuforums.org/showpost.php?p=2175127&postcount=91")

2. Most icons don't support full paths. USP only reads icons inside the "/usr/share" folder (as well as subfolders). You can tell it to use these icons by simply referring to them by name (e.g. instead of "/usr/share/pixmaps/firefox.png" you just use "firefox.png"). As far as I know, you can't make it access any other folders for reading icons. The exception to this is that the icons for tabs allow full paths.

---

### Post by kobewan on 2007-02-19
Alright, I think that's it! :D

Actually, what we really need to get is a wiki. Unfortunately, I have no idea about how to either make or edit a wiki. Anybody else have a clue?

Anyways, if I missed something, post about it and I'll try to add it.

---

### Post by Mateo on 2007-02-19
Nice guide.  In the theme section, maybe you should add how to change the button icon, because I don't *think* full path is supported there.

As far as wikis, I've installed them before and it's no problem.  I don't currently have webspace so I can't do it, but I could help with maintaining it.

---

### Post by kobewan on 2007-02-19
> **Mateo said:**
> Nice guide.  In the theme section, maybe you should add how to change the button icon, because I don't *think* full path is supported there.

As far as wikis, I've installed them before and it's no problem.  I don't currently have webspace so I can't do it, but I could help with maintaining it.

Updated the Toubleshooting section.

Aren't there any free wikis that are halfway decent? I remember hearing about pbwiki, but I don't really know enough about wikis to know what to look for. I just read them :D.

---

### Post by chanders on 2007-02-19
> **kobewan said:**
> Alright, I think that's it! :D

Actually, what we really need to get is a wiki. Unfortunately, I have no idea about how to either make or edit a wiki. Anybody else have a clue?

Anyways, if I missed something, post about it and I'll try to add it.

First of all, let me say I couldnt have put it better. You did an excellent job here man, and I am sure you put a lot of work into it. I am going to set up a wiki now and will add you to the list of Developers. You can be in charge of documentation ;-)

Cant wait to have you guys on baord for USP3, when we make this project official.

---

### Post by kobewan on 2007-02-20
> **chanders said:**
> First of all, let me say I couldnt have put it better. You did an excellent job here man, and I am sure you put a lot of work into it. I am going to set up a wiki now and will add you to the list of Developers. You can be in charge of documentation ;-)

Cant wait to have you guys on baord for USP3, when we make this project official.

Alright, cool. I'll be happy to help in any way that I can with this great piece of software. 

I'm going out of town for a few days right now, but I'll get on it when I com back.

---

### Post by delfick on 2007-02-22
when you get back, you might want to change the "installation" part to reflect this change here [http://www.ubuntuforums.org/showpost.php?p=2191402&postcount=131](http://www.ubuntuforums.org/showpost.php?p=2191402&postcount=131) :D

---

### Post by PsyberOneZero on 2007-02-23
> **delfick said:**
> when you get back, you might want to change the "installation" part to reflect this change here [http://www.ubuntuforums.org/showpost.php?p=2191402&postcount=131](http://www.ubuntuforums.org/showpost.php?p=2191402&postcount=131) :D

Thanks delfick

---

### Post by delfick on 2007-02-23
> **PsyberOneZero said:**
> Thanks delfick

no probs :D

---

### Post by SkiesOfAzel on 2007-02-24
Wow , a  fellow fan of Dr MacNinja ... Are you by the way growing a mustache ???:P . This seems nice  but i tend to use a dock (avant window manager rocks) to launch my apps  and 20 mb seems allot to me for something i will rarely use... What the hell i will give it a try just for MacNinja's sake. Is it written in python btw?

---

### Post by kobewan on 2007-02-25
> **SkiesOfAzel said:**
> Wow , a  fellow fan of Dr MacNinja ... Are you by the way growing a mustache ???:P . This seems nice  but i tend to use a dock (avant window manager rocks) to launch my apps  and 20 mb seems allot to me for something i will rarely use... What the hell i will give it a try just for MacNinja's sake. Is it written in python btw?

Yep, its in Python. Also, 20mb may seem like a lot, but I really think that it's worth that much just for the search function (and I'm a guy who never used docks in Windows because of the extra ~5MB of RAM they took).

Glad to see that somebody recognized MacNinja :D. Had to make that picture really small and its pretty distorted.

---

### Post by travishume on 2007-03-11
I see that you're using google code to host svn, why not create a full google code project to host usp?  You'll have a wiki and bug reporting, see [http://code.google.com/p/fbug/](http://code.google.com/p/fbug/) for an example.

Also, I'm debugging this, but here's what I'm seeing on latest svn checkout on freshly installed feisty system
>  usp run-in-window
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 895, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 885, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 647, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 65, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 424, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 647, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 373, in Todos
    openfile = open( GetFilePath( path ), 'r' )
UnboundLocalError: local variable 'path' referenced before assignment


---

### Post by Malac on 2007-03-11
@travishume ^^

Should be fixed in Revision 170.

I think Bugs can be reported here:
[http://code.google.com/p/ubuntu-system-panel/issues/list](http://code.google.com/p/ubuntu-system-panel/issues/list)

Though you will need a Google Account to create a "New Issue", I'm not sure if we can set it not to require this, chanders would know better.

---

### Post by marcus2004 on 2007-03-12
I can't figure out for the life of me why I am not able to add USP to my gnome panel. 
I get the error:
The panel encountered a problem while loading "OAFIID:GNOME_USP".

I seem to be able to add other applets to the panel just not this one. 

I reinstalled the software (I am using revision 193) reinstalled ubuntu-desktop as I saw in another thread that someone was having similar error and that helped them. 

I have been looking on the forums here and on google and there hasn't been any consistant answers. 

I did run killall gnome-panel and it did just that, but it still will not add. 
Any help would be greatly appreciated.

---

### Post by Malac on 2007-03-13
> **marcus2004 said:**
> I can't figure out for the life of me why I am not able to add USP to my gnome panel. 
I get the error:
The panel encountered a problem while loading "OAFIID:GNOME_USP".

I seem to be able to add other applets to the panel just not this one. 

I reinstalled the software (I am using revision 193) reinstalled ubuntu-desktop as I saw in another thread that someone was having similar error and that helped them. 

I have been looking on the forums here and on google and there hasn't been any consistant answers. 

I did run killall gnome-panel and it did just that, but it still will not add. 
Any help would be greatly appreciated.
Please run:
```
usp run-in-window
```
from a home terminal and post the output.
Thanks.

---

### Post by marcus2004 on 2007-03-13
I did that and nothing happens. I type usp run-in-window and hit enter and it just pauses for 1/2 second and then goes to the next line in terminal.

---

### Post by Malac on 2007-03-13
> **marcus2004 said:**
> I did that and nothing happens. I type usp run-in-window and hit enter and it just pauses for 1/2 second and then goes to the next line in terminal.
Strange :confused:

Can you try running ```
uspconfig
``` in a terminal and see if that loads.
If it does then choose the [Backup] Button
Check to see if the tab marked "**Warnings**" is there, it would be just before the "**About**" tab.
If it is there does it give warnings about plugins.
If so remove that/those plugins from the **Plugins** list on the "**Main**" tab.
Hit [Save] exit uspconfig and try: ```
usp run-in-window
```If that doesn't work remove all plugins from the list except "applications" and try again.

If you can't start uspconfig then there is a problem with the whole install of usp or python, though if it was a python problem like missing modules I would still expect to see an error message.

The other thing to try would be :```
gnome-system-monitor
``` select one of the lines then type "python" (without the quotes)
You should find a process like this:[ATTACH]27322[/ATTACH]
If so end the process by right-clicking and choosing "End Process".
Try launching ```
usp run-in-window
``` again.

---

### Post by al0903 on 2007-03-15
pardon for my noob-ness, but anyone can point me out on how to install the plugins?

i downloaded the USP2 plugins,extracted but unable to use them when i typed into the plugin section (example: usptime) ....it'll give me a warning saying that my plugin is w/o config section, error or not found :confused:

---

### Post by Malac on 2007-03-15
> **al0903 said:**
> pardon for my noob-ness, but anyone can point me out on how to install the plugins?

i downloaded the USP2 plugins,extracted but unable to use them when i typed into the plugin section (example: usptime) ....it'll give me a warning saying that my plugin is w/o config section, error or not found :confused:
If you extract them to /home/[COLOR=DimGray]*<your-user-name>*[COLOR=Black]/.usp/plugins they should be available to usp.
Or use the .deb file.

If that is still not working post the output of :[/COLOR][/COLOR]```
usp run-in-window
```[COLOR=DimGray][COLOR=Black] [/COLOR][/COLOR]

---

### Post by Denseo.Hagakure on 2007-04-23
On Ubuntu France we are much to use USP, we would like much a translation in French. If you a textual file containing gives us all the English sentences we will make a pleasure of returning it to you with the French translation. 

Thank you for all

---

### Post by Malac on 2007-04-23
> **Denseo.Hagakure said:**
> On Ubuntu France we are much to use USP, we would like much a translation in French. If you a textual file containing gives us all the English sentences we will make a pleasure of returning it to you with the French translation. 

Thank you for all
Here is a good place to start:
[http://ubuntuforums.org/showpost.php?p=1329194&postcount=29](http://ubuntuforums.org/showpost.php?p=1329194&postcount=29)
It is for the old 0.3x version but xgettext should still work.

J'espère que ceci aide. :)

---

### Post by Denseo.Hagakure on 2007-04-23
Thank you Malac. you know or is the file which I can modify?

---

### Post by Malac on 2007-04-23
> **Denseo.Hagakure said:**
> Thank you Malac. you know or is the file which I can modify?
```
xgettext /usr/bin/usp -a --language=Python
```Will give you a message.po file that you can use for translations.
It can be run on all the plugins too.

Or you could use my app GITOI which will read the Glade files and let you translate and output an updated Glade file, then just change which file the plugin or usp uses. It's available here :
[http://ubuntuforums.org/showpost.php?p=1526062&postcount=1](http://ubuntuforums.org/showpost.php?p=1526062&postcount=1)

e.g.
```
        # Set the Glade file
        self.gladefile = os.path.join( os.path.dirname( __file__ ), "applications.glade" )

``````
        # Set the Glade file
        self.gladefile = os.path.join( os.path.dirname( __file__ ), "applications_fr.glade" )

```
For main app.
```
        #Set the Glade file
        self.gladefile = "/usr/share/usp/usp2.glade"

``````
        #Set the Glade file
        self.gladefile = "/usr/share/usp/usp2_fr.glade"

```

---

