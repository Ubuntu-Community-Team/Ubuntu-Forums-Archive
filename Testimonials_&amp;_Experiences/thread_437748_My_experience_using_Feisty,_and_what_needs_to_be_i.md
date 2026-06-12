---
title: "My experience using Feisty, and what needs to be improved"
date: 2007-05-09
forum: Testimonials &amp; Experiences
---

### Post by dignick on 2007-05-09
I have just installed Ubuntu 7.04, and I must say I am very impressed.  Development is obviously moving rapidly when comparing to 6.06 which is less than a year old.  Congratulations!

However I would not have been able to get the system as I have now if I wasn't so technically minded.  I think there are some problems with Ubuntu that are actually very minor and could easily be resolved.  This is mostly opinion with some possible bugs thrown in, and so is all IMO; don't be insulted by anything I suggest.  If you disagree with it, say.  I may get things wrong too, in which case I apologise.
None of this is a request for support, but if anybody has ideas to progress any of the bugs/issues I have please say.

I will just add that I have used Windows all my life and I'm now moving away from it.  Therefore I have a lot of windows-related ideas below.  Although I dislike most of Windows and many things Microsoft do intensely, there are some UI ideas that the Ubuntu team could learn from.
I believe Linux is the future, and Ubuntu is going to be the most popular distribution by far.  With the Dell deal, there are going to be many more users coming this way.

I have included anything I found in using Ubuntu.  This includes problems with proprietary drivers such as nVidia, and code from other projects.  While this is not the Ubuntu developers fault, I think it is (most of the time) only them who could resolve it through workarounds or negotiation with the respective companies/developers.  I am technically minded, but I have no experience of software development.

Correct me if I'm wrong, but I perceive this distribution is targeted at the majority of computer users.  I think it is safe to assume that the majority of computers will have less than 10 accounts used, and the users won't want to use terminal at all or at least very minimally.  I believe the following changes should be made to reflect this.




UI

In the context menu 'move to deleted items' folder should just read 'Delete' or 'Move to trash'.  System wide, it should be known as either trash (for example in nautilus, 'trash:///') or deleted items.  Consistency is key.

Items should be renameable by clicking on the filename once.

<Super>d should be a keyboard shortcut for show desktop especially if a windows installation has been detected during installation.  The same applies for other windows shortcuts (if otherwise unused)
CTRL+ALT+DEL should open system monitor by default as it isn't used for anything else and is an ubiquitous shortcut.
Beryl should copy existing metacity keyboard shortcuts (if it doesn't)

When an exe is double clicked, the user should be asked if they would like to install wine to attempt to run the application, possibly with an explanation about Windows executables not working in Linux.

Login window should use a face browser by default - windows and os x do.  Users don't like typing their username when it isn't necessary.

gconf-editor should be in system/preferences menu, called simply Gnome configuration.

When an filetype has been opened with an application the application should appear in an 'Open with' submenu similar to how Windows does.

.txt files should open with gedit by default.

I use 4 scripts for nautilus that I think should be in the default context menu:
Set as wallpaper (for images)
Open as root (for folders, executables, scripts, blank space) (only for users that can perform administrative tasks)
Open terminal here (for folders, blank space)
Archiver/Unarchiver (for archives, folders)

When a write operation is requested on an ntfs drive, a prompt should appear asking the user if it should be enabled (ntfs-3g), explaining the potential risks.

Screen real estate - I think this is quite a major issue.  Many things in Gnome are too big - toolbars, buttons, text.  This can easily be resolved, and is quite critical for example when using a laptop.  I think the Gnome panels text should be independent of application text, as I believe it needs to be larger - when you need to find a application window you need large text, but in the application itself that same font size is excessively large.  See the screenshot from the open files dialogue of Azureus on Windows and Ubuntu as an example.
[img]http://nrbrook.googlepages.com/composite.png[/img]

A welcome to Ubuntu video could be produced, introducing the user to some of the basics such as the functions of the panel etc.

Two panels by default seems unnecessary - there is a lot of wasted space in the top panel.  Especially if a user is coming from windows, the setup could instead be as shown below.
[Link, image too wide.]("http://nrbrook.googlepages.com/screenshot2.png")

Font hinting should be enabled by default.  I think I might have read a reason behind why it isn't somewhere, but I can't remember it.

A user's application theme should be applied to all windows that are running as root.

All windows internet shortcuts should open with firefox - they need to be interpreted by nautilus or whatever is responsible for that kind of thing and then opened.



Technical

When a photo is viewed in eog directly from a memory card and delete is pressed and confirmed, eog tries to move it to the trash on the removable drive, and therefore can't.  It should be permanently deleted or moved to the local trash.

When I installed Ubuntu, the correct resolution for my monitor was not detected - 1280x1024.  I decided to go ahead and install the restricted nVidia driver and beryl.  After a restart the correct resolution was still not detected or available in screen resolution.  I edited xorg.conf to add the correct monitor resolution, but for some reason the resolution still didn't appear in screen resolution even after restarting X.  I ran nvidia-xconfig where I could select the correct resolution.  After applying to check it worked, I clicked to write the values to xorg.conf.  After a restart, the screen was the correct resolution, but the nvidia-xconfig had overwritten all the keyboard language settings etc and basically made a mess of xorg.conf.  Luckily I had the xorg.conf backup beryl had made, so I restored that, edited it a bit and the resolution was still fine.
The point I'm making here is that nvidia-xconfig does not do a good job.  It doesn't modify xorg.conf, it completely replaces it messing up language stuff in the process.  This shouldn't happen, especially as there aren't any language settings in nvidia-xconfig.  I have no idea why editing xorg.conf didn't let me choose the right resolution and nvidia-xconfig did, but the whole situation here needs improving so it just works.

nvidia-xconfig should be added to the system/administration menu when the nvidia driver is installed (although probably not until it works better).

The shared folders dialogue needs to be improved.  It should have more options on, at least enough to set up the configuration detailed below.  I don't think it should write anything to smb.conf unless some configuration is actually changed - I opened it this morning and it broke my configuration, meaning I had to manually edit the config file again.
Samba should be configured by default to mimic windows behaviour, again especially if coming from a windows environment as most are.  This means when samba file sharing is enabled (which should also be titled 'samba (windows)' or similar when the installation dialogue pops up) all shares should be accessible by any computer on the network.  Wins should also be installed and enabled by default.  This will please the majority, the minority who do not require this can manually configure.  My smb.conf is shown below as an example of how I have this set up.

```
[global]

workgroup = HOME

netbios name = study

security = SHARE

auth methods = guest

domain master = No

wins support = yes



load printers = yes	#should be enabled when printer sharing is#

printing = cups		#should be enabled when printer sharing is#

printcap name = cups	#should be enabled when printer sharing is#



[printers]		#should be enabled when printer sharing is#

comment = All Printers

browseable = yes

path = /var/spool/samba

printable = yes

public = yes

guest ok = yes

writable = no

printer admin = guest



[shared]

comment = Shared Folder

path = /media/sda1/Shared

read only = No

guest ok = Yes
```

There may be a better/more secure way to do this, but this is pretty minimal and works for me.

When a USB printer is connected, it should be installed automatically and the user should be notified and asked if they would like to print a test page.  There is no need for a user to have to enter the printing section of administration.  Similarly with scanners and webcams, but instead of a test page, a test scan or view the webcam.
When printer sharing is enabled again it should mimic windows behaviour and printers should be accessible by any computer on the network.  This involves opening the port, which I believe already happens; changing the cups server access permissions (the IP address range could be guessed from the computers IP address); and running cupsaddsmb.

Amarok should be easier to install - to get it working for me, I had to run:
```
dcopserver
sudo apt-get install amarok-engines
sudo chmod -R 777 /home/<username>/.kde
```
Not sure if everyone has this problem.

Many users currently need to use Automatix to install popular proprietary and non-free applications, fonts, codecs etc.  I don't think a user should need to install a new program just to install other new programs.  Everything (or at least most things) in automatix should be in synaptic, probably separated from other packages.  It could be that when ubuntu is installed, the user is asked if they want non-free packages (such as windows fonts, codecs) to be installed.  The restricted drivers manager is obviously a great step towards this.  I assume there are some legal reasons that this has not been done though, although it could be made easier.
A solution might be to group all restricted stuff - non-free drivers, applications, fonts etc into a 'restricted' section of the system/administration menu.  In this, all restricted items could be disabled or enabled and selected.

Standby and Hibernate don't work for me - it always fails on resume.  While this isn't a request for help, it is obviously a hurdle that needs to be overcome before Ubuntu can become even more successful.

Alien should be installed by default and rpm packages should be converted and installed on the fly.

Source code archives should be scanned for configure scripts and ./configure make and make install should be attempted to be run if the user requests installation (possibly in the context menu).  I have heard there could be issues with this, but I'm sure it could work to some extent.  Don't know how possible it is, but the installed application should then be listed in synaptic.

Switch user often doesn't work for me - I can change user, but trying to change back leaves me at a black screen with a mouse.  This could be related to the nVidia driver or possibly beryl, but it is a minor problem I think - if I restart X I see a flash of my desktop before it goes.

I don't see why some applications like gaim cannot be removed due to ubuntu-desktop dependencies.  This restriction is ok for system components, but stuff like gaim, openoffice could happily be removed if there were some workaround to enable it, somehow disabling the relevant dependencies in ubuntu-desktop.  In an operating system that is all about choice, a user should be able to easily choose what and what not to have installed on his system, without it removing the whole desktop environment.
I don't know the technical implications behind this or how possible it is.

All windows-related changes I have suggested could be grouped into some kind of 'windows compatibility' script or something, that would allow the code and settings it involves to be easily enabled or disabled.  Therefore, if a windows installation is found when Ubuntu is installed, all the windows compatibility stuff is enabled.  If there isn't, it is disabled with the option to enable it.  The same applies for mac-related stuff, but as of yet I have no proper experience of using OS X.  I'm getting a Mac in June which will be interesting.



While there are many negatives about my Ubuntu experience listed here, don't get me wrong - it's still very good.  Some things for example the dialogue that pops up when a camera is connected are very nice touches and it's just more of this overall finish that will make Ubuntu Linux the best operating system available.

---

### Post by Monstroxus on 2007-05-09
Great post!

Some thoughts...:

"When an exe is double clicked, the user should be asked if they would like to install wine to attempt to run the application, possibly with an explanation about Windows executables not working in Linux."

I support this suggestion.

"A welcome to Ubuntu video could be produced, introducing the user to some of the basics such as the functions of the panel etc."

Great idea! Put this video on the live cd as well. I don't really care for Nelson Mandela, but that clip can stay... but put a video on the desktop with a nice sexy Ubuntu presentation! (with subtitles in case the sound doesn't work) Again a great idea!

"Two panels by default seems unnecessary - there is a lot of wasted space in the top panel".

Sorry I don't agree, I love it! It is much more flexible working with two panels/taskbars, and this is one of the things that sets Ubuntu apart from Windows.

"Many users currently need to use Automatix to install popular proprietary and non-free applications, fonts, codecs etc. I don't think a user should need to install a new program just to install other new programs. Everything (or at least most things) in automatix should be in synaptic, probably separated from other packages. It could be that when ubuntu is installed, the user is asked if they want non-free packages (such as windows fonts, codecs) to be installed. The restricted drivers manager is obviously a great step towards this. I assume there are some legal reasons that this has not been done though, although it could be made easier."

Well, as far as I know, all these things are available in Synaptic, you only have to search for it a bit longer. I also heard ppl say that it is better to use Synaptic instead of Automatix.

Thank you for your suggestions!

---

### Post by weblordpepe on 2007-05-09
You gotta be kidding me. That first post has got to be the most interesting thing I have read all week. What a great post. I think your suggestions are well thought out and appropriate. I'm obviously a noob around here but I was quite impressed.

A side note: I totally agree about Gnome taking up room by default. I actually have the Redmond theme for the controls/buttons/etc which is basically Windows-2000ish. Its much better.
EDIT: Moderators you might want to move this to the ideas pool thread I would think? Or at least reference it there.

---

### Post by dignick on 2007-05-10
Thanks for the words of support.

The ideas I listed just seemed like common sense, but I guess nobody has really considered them before.

I hope at least a few of my ideas make it in some form anyway! :grin:

---

### Post by jdriessen on 2007-05-10
great post!!

this is exactly the kind of critical thinking that could get ubuntu up there as one of the leading OSes...


I hope these points will be worked on in the near future... the sooner the better!

---

### Post by entangled on 2007-05-10
Dignick's post has a lot of interesting ideas and I am in favour of most. In general I think the idea is that the software needs to incorporate a bit more 'common sense', rather than mostly unwanted flexibility. I definitely think the screen layout and artwork needs a bit more design effort to give it some style. This would probably be more effective than changing software behaviour.

---

### Post by kelvin spratt on 2007-05-10
positive ideas are what is needed and embrasing automatix  and get deb. Also because the software is updated as and when bugs appear and if it is offered it should not be condemed people want the latest
not wait 6 months for it, that would also make developers work harder to make improvements cause as it is they are going at Llinux pace and thats to slow, also they need to do a bit better skin wise and so does gnome and kde its only the glitter that makes windows popular

ps don't comment on my writing inside is a genius trying to get out

---

### Post by 3rdalbum on 2007-05-11
Some good suggestions, some strange ones too - AmaroK should just work, not sure why it didn't in your case.

With the general gist of the post though, I think Ubuntu is already moving in that direction as fast as it can. I just installed Feisty after being a Dapper user, and I'm amazed at how much the Ubuntu devs are integrating the standard tools together.

---

### Post by dignick on 2007-05-11
> **entangled said:**
> I definitely think the screen layout and artwork needs a bit more design effort to give it some style. This would probably be more effective than changing software behaviour.

I think Ubuntu definitely needs a change of style; I am all in favour of a theme change, I don't like the coffee/orange look.  But I think it is personal preference.  I like the default Windows XP 'Fisher price' theme even less than the default Ubuntu theme, but millions of people cope with it every day (or simply don't care how it looks), and so I don't think my opinion here or even the default theme itself matters all that much.

But software behaviour is key to user experience, much more so than how it looks IMO.  Many of the things I suggested are simply to remove dependency on the terminal to get things set up, and using the terminal isn't using a UI at all.


> **3rdalbum said:**
> Some good suggestions, some strange ones too - AmaroK should just work, not sure why it didn't in your case.


Me neither, but it didn't.  I guess this is a bug, but a bug in what I don't know.

> **3rdalbum said:**
> With the general gist of the post though, I think Ubuntu is already moving in that direction as fast as it can. I just installed Feisty after being a Dapper user, and I'm amazed at how much the Ubuntu devs are integrating the standard tools together.

I totally agree I think they are putting a lot of effort into the whole experience and it is rapidly improving.  Like you and I mentioned: comparing 7.04 to 6.06, which is just 10 months older, the difference is quite amazing.  This post is intended to help them out with some constructive criticism/suggestions for improvement.

Thanks for the replies!

---

### Post by airtonix on 2007-05-15
the only thing ubuntu needs more if is this : 

users who bother to become familiar with their enviroment.....much like ahunter does with their hunting grounds...its just plain logical you dont walk around like you own the place if you dont know where stuff is!  

more config guis that simply modify the current text files. keep both noobs and guru camps happy.

more kernel support for hardware, so more of your dongles and wierd things work by just pluggin them in.

a theme editor gui for gnome-icon-theme-suites, GTK control sets and  metacity themes. (im thinking about doing this myself)

guis for co-odinating deb-mirror and local-network software updates for local ubuntu machines.

port the  "advanced visualisation library" && "advanced visualisation studio" from winamp 2.91 to gstreamer or even just to xmms....the others are pathetic.

beryl-virtual-layers for gdeskets.... like macos does for its widgets.


other than all that i can replicate : 
  vista theming effects 1:1. blurs, shadows,  tiltings, etc.
  macosx theming effects 1:1. blurs, shadows,  tiltings, etc.

but i get to keep the good bits about ubuntu gnome interface. which is the intention of ubuntu...you customise it yourself....

if you think you can make money by selling customised versions then do so but you can only charge for your portion and services. 

can you do that with windows?

ps maybe try using gmusicbrowser. there are debs and a repo for feisty.. as i dont use the appleos on my ipod video its perfect for i use rockbox so i can use my ipod immeaiatly with out itunes interferring.

---

### Post by PhilipGanchev on 2007-05-19
I like your critical observations, and especially your understanding that functionality is much more important than the colors of the desktop and the title bars.  Would you care to post your ideas as bug reports at [https://bugs.launchpad.net/](https://bugs.launchpad.net/) ?

As for the CLI, I disagree somewhat.  The CLI (command line interface) is a UI (user interface).  In its current form, it is very efficient for many tasks, once you know the commands.  See Jef Raskin's book The Humane Interface.  Obviously, there is a need for additional programs for things like image viewing and manipulation, different fonts, etc.  What we need is to make it easy to discover the command the user needs at any time, so that the user does not need to memorize command names.  This would remove the need to navigate menus and remember which menu has the item you need.  The CLI should be redesigned and integrated into the whole environment.  See the Deskbar project for ideas.

---

### Post by 3rdalbum on 2007-05-19
Just a couple more comments on the OP:

Wine is not supported, and Wine's support for Windows programs is kinda minimal, so I think it would be best not to include a "Would you like to install Wine?" box in case people think that it's saying that the program WILL work in Wine.

Also, Mark Shuttleworth doesn't want Ubuntu to be seen as "A cheap copy of Windows".

A face browser doesn't work so well for corporate desktops, which is one area where Ubuntu is making inroads. I didn't even notice its lack-by-default - I find it quicker to just type my username than move the mouse. You've got to go back to the keyboard anyway.

Compiling source code is rarely as simple as what you say, so adding that feature would almost never actually compile anything. Stick to the repos, please!

Two Gnome panels use only as much space as KDE's one panel. I've used Linux Mint, where there's only one Gnome panel, and there's just not enough space on an ordinary monitor to be able to see the names of the windows in the taskbar. The top panel gives you room to put launchers, the bottom panel gives you enough space to see all your running programs.

Gconf-editor is not something that users should open and use without careful instruction. Its closest Windows relative is Regedit, and you never see that on any OEM's default Start menu; too dangerous to let newbies play around with that.

Are you aware that some of your suggestions actually already happen?

---

