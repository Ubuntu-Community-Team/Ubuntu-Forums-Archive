---
title: "One of Linux's Greatest Weaknesses"
date: 2010-01-14
forum: Ubuntu Dev Link Forum
---

### Post by Penguin Guy on 2010-01-14
**In a Nutshell**
[I am basically asking for a specification for storing settings, but with focus on making it cascading.]("http://ubuntuforums.org/showpost.php?p=8977368")

**My History**
I've been messing around making a few minor scripts for Linux and I constantly see this problem coming up. Changing settings. The settings are all over the place: text files, gconf, program generated binary files, etc. It's so complicated to program a simple thing like changing the wallpaper, because each desktop environment does it in a different way.

**The Idea**
I think we should make a system to manage all the settings in a **cascading** and **multi-dimensional** manner. When a program is installed it should store it's settings in the default settings section. A program's default settings can be overwritten in the global settings, which can, in turn, be overwritten by the user's settings.

```

Default Settings
	Global Settings
		John Smith's Settings
		Bob Smith's Settings
		**...**

```

```

Default Settings
	X Settings
		GNOME Settings
		KDE Settings
		**...**
	Console Settings

```


Also:
[LIST]
[*]Admin's should have the ability to **'lock' certain settings** so that users cannot change them.
[*]People should be able to **define custom profiles** (e.g. 'Dark Theme', 'Light Theme' - I often switch a lot between the two and hate having to go through _all_ the settings and change them one by one)
```

Default Settings
	X Settings
		GNOME Settings
			Light Settings
			Dark Settings 
		KDE Settings
		**...**
	Console Settings

```
[/LIST]

**Goals**
[LIST]
[*]Ability to copy/backup your settings
[*]More control over your system
[*]Settings are easier to manage
[*]Settings are all in one place
[/LIST]

**Will This Slow Down Over Time Like the Windows' Registry?**
Not at all, the Windows registry is slow because programs install settings and don't remove them when they become outdated. Ubuntu programs are generally a lot more clever and usually leave very little junk behind. Hopefully, with this system, less junk should be left behind than before - since the settings are all in once place rather than being scattered across the computer.

**What do you Think?**
Please, _post a comment_ - if you don't like this idea then post and tell me what's wrong with it. System admins - how useful do you think this would be. Developers - how hard would this be to implement. Also, any ideas on how this can be improved are welcome.


*Don't understand quite what I mean? Take a look at [Naggobot's post]("http://ubuntuforums.org/showpost.php?p=8988473") - you may find his explanation clearer.*

---

### Post by hthury on 2010-01-14
I was thinking about RAM, memory and all that stuff... could make system slower...

---

### Post by Penguin Guy on 2010-01-15
> **hthury said:**
> I was thinking about RAM, memory and all that stuff... could make system slower...
This isn't a program as such, merely a collective database of settings - so it shouldn't take up any more/less RAM than the existing setup does.

---

### Post by Maheriano on 2010-01-15
1. right click desktop
2. Change wallpaper

Am I missing something?

---

### Post by Penguin Guy on 2010-01-15
> **Maheriano said:**
> 1. right click desktop
2. Change wallpaper

Am I missing something?
Yes: for a computer program it is much, much harder. The system I am proposing will make it easier for programs and administrators to manage settings.


For example, if I were to write a program to set the background in Gnome it would look something like this:
```

import sys, os
desktoptype = os.environ.get('DESKTOP_SESSION')

if 'gnome' in desktoptype:
	import gconf
	client = gconf.client_get_default()
	client.set_string ( "/desktop/gnome/background/picture_filename" , path )
else
	print "Error: Cannot change wallpaper."

```
This only supports GNOME, if I wanted to support all desktop managers the script would be much longer. Now let's see an example script using my system:
```

import sys, os
sys.set.wallpaper = path

```
As you can see, this script is much shorter. This saves programmers time, and the program will work in any desktop environment.

---

### Post by ImmortalSoFar on 2010-03-15
I see this as one of its strengths. What you are describing is the Windows Registry - a massive hodge-podge of outdated, cryptical junk of long-forgotten purpose that once it does get corrupted, takes everything with it.

---

### Post by Tony Flury on 2010-03-15
Your system would be a night mare for installation/upgrade/removal of applications, which is exactly the reason why the Windows registry gets so much rubbish left in it, as upgrades/removals don't clean up properly.

Nothing in your system makes that any better, and instead of under the current system you get a lot of small files that get left around, taking disk space admitedly, but not actually getting accessed, we now have three files - which are complex and slowly growing with every installation, making application start up slower and slower as the system gets older and subject to more changes.

I agree that discrete config files area far better idea - if one of my application starts misbehaving and gets into a state that i can't correct easily - I know i can easily delete the config file for that application, without impacting anything else - and a well written application will recover by applying defaults - Try doing that in windows. Even finding the section that you want to edit in the windows registery sometimes requires knowledge of what programmng language the application was written in.

---

### Post by Penguin Guy on 2010-03-15
@Tony Flurry

I see your point. But what would you think about having three versions of [FONT="Courier New"]/etc/default[/FONT] (default, admin, user)?

---

### Post by djurny on 2010-03-15
this is a good idea, but isnt this already in place with with for example

[LIST]
[*]admin settings (installation defaults)
/usr/share/*app*
[*]default settings (initial setup)
/etc/default/*app*
[*]settings (overrides)
/etc/*app*
[*]user settings (per user)
~/*.app*
[/LIST]

?

---

### Post by Simian Man on 2010-03-15
The frustration that you're running into with your wallpaper example isn't the fact that configuration files don't cascade and it isn't the fact that there are multiple ways of storing/modifying settings.  It's the fact that the various projects don't store settings for the same concept in the same place.

In your registry-like solution, what's to stop Gnome developers from making a "gnome-wallpaper" key, Xfce developers from making a "xfce-wallpaper" key and KDE developers from making a "kallkaper" key?  Then you'd be stuck in the same problem you're in now.

If this is really a problem, and I'm not convinced that it is, then this kind of thing should be handled with a FreeDesktop.org standard and not a new configuration system.

---

### Post by Tony Flury on 2010-03-16
@Penguin Guy

You will still get bloat and rubbish in each of those three big files - and it still has the problem that I cannot easily wipe the config for one of the applications.

You also have an another problem - many applications with complex config will load all of their config into memory, rather than reading off disk, your mechanism now has to have a way of requesting that all apps areload their config, or a very clever mechanism to associate a section of the config with a specific application, and ask it to reload. More complexity is never a good idea in my opinion - especially as the current system works.

An example - I have an application that supports multiple user accounts - so that app has some general config, and then some specific config for each user, each of that config is in a seperate file. To delete a user account and start from scratch is easy - delete one file in ~/.app/<User Name> - bingo.

---

### Post by Penguin Guy on 2010-03-16
> **djurny said:**
> this is a good idea, but isnt this already in place with with for example

[LIST]
[*]admin settings (installation defaults)
/usr/share/*app*
[*]default settings (initial setup)
/etc/default/*app*
[*]settings (overrides)
/etc/*app*
[*]user settings (per user)
~/*.app*
[/LIST]

?
Ah, well actually that's pretty much what I had in mind. But why do we have [FONT="Courier New"]gconf[/FONT] if such a system is already in place?

---

### Post by lykwydchykyn on 2010-03-16
> **Penguin Guy said:**
> Ah, well actually that's pretty much what I had in mind. But why do we have [FONT="Courier New"]gconf[/FONT] if such a system is already in place?

What djurny describes is a convention.  What you're asking for is a specification.

The convention doesn't really scale up well to the complexity of something like GNOME, which is why gconf exists; kde, likewise, has its own filesystem under ~/.kde with specifications for where different configs should go.

I'm not an expert on FreeDesktop.org specs, but I do know that some exist for common configurations, and that KDE and GNOME are both working towards respecting certain common configs.  

You can read more here: [http://www.freedesktop.org/wiki/Specifications](http://www.freedesktop.org/wiki/Specifications)

---

### Post by Penguin Guy on 2010-03-16
> **lykwydchykyn said:**
> What djurny describes is a convention.  What you're asking for is a specification.

The convention doesn't really scale up well to the complexity of something like GNOME, which is why gconf exists; kde, likewise, has its own filesystem under ~/.kde with specifications for where different configs should go.

I'm not an expert on FreeDesktop.org specs, but I do know that some exist for common configurations, and that KDE and GNOME are both working towards respecting certain common configs.  

You can read more here: [http://www.freedesktop.org/wiki/Specifications](http://www.freedesktop.org/wiki/Specifications)
Yeah, sorry for not explaining myself properly, a specification is exactly what I want. Without a specification, we will never have seamless integration between desktop managers.

---

### Post by lykwydchykyn on 2010-03-16
> **Penguin Guy said:**
> Yeah, sorry for not explaining myself properly, a specification is exactly what I want. Without a specification, we will never have seamless integration between desktop managers.

Do we need it?

---

### Post by Simian Man on 2010-03-16
What if someone wanted to have a different wallpaper for each desktop that they use?  That'd be impossible with your proposal.

---

### Post by Penguin Guy on 2010-03-16
> **lykwydchykyn said:**
> Do we need it?
It would be pretty good feature.

> **Simian Man said:**
> What if someone wanted to have a different wallpaper for each desktop that they use?  That'd be impossible with your proposal.
Nah, there's loads of ways you could implement it. Possibly by defining different session types:
```

GNOME Settings
KDE Settings
XFCE Settings
**...**

```
These would all inherit from the default settings.

---

### Post by lykwydchykyn on 2010-03-16
> **Penguin Guy said:**
> It would be pretty good feature.

I'm not sure I see the point, personally.

Apart from changing the wallpaper, what sort of things would you expect to be centrally configured?

---

### Post by Penguin Guy on 2010-03-17
> **lykwydchykyn said:**
> I'm not sure I see the point, personally.

Apart from changing the wallpaper, what sort of things would you expect to be centrally configured?
[LIST]
[*]Font
[*]Cursor blink rate
[*]Screensaver
[*]Lock dialogue
[*]Theme
[*]Icons
[*]Window button positions
[/LIST]
*etc.*

---

### Post by _khAttAm_ on 2010-03-18
I don't get the idea of what you are proposing.

But, I'd really want to see a universal theme management control center for Ubuntu, in which you can change font sizes, plymouth themes and everything included in the default installation. It is not currently impossible using various utilities and editing config files or replacing certain files, but it would be better if we had all of them in the same control center. Also, creating universal theme (tar.gz or whatever renamed to something like .gtheme or .utheme) packages, which can change the overall look of the system would be great (something like compiz-config-settings-manager or gnome-control-center but theme centric).

About the control center thing, universal control center for configuring various system settings for gnome is available (gnome-control-center). Also there is gconf-editor which lets various settings of various gnome applications. But maybe you're looking for something else.

Please share your views.

---

### Post by Penguin Guy on 2010-03-18
> **_khAttAm_ said:**
> About the control center thing, universal control center for configuring various system settings for gnome is available (gnome-control-center). Also there is gconf-editor which lets various settings of various gnome applications. But maybe you're looking for something else.
No, what I'm looking for is something that is shared by the entire system. For example - in most cases you will want the font of your shell to be the same as that of your gnome terminal, yet there are two separate settings.

---

### Post by Naggobot on 2010-03-18
I shall offer a greener perspective on matter.

I agree whole heartedly that Windows registry is not the way to go and individual configuration files have definite advantages.

On the other hand as a person who does not know where those files are and is not familiar with every nuances I think can also feel for Penguin Guy even though he probably does not have this particular problem.

Now we already have package management and if I understand correctly, it should know where the configuration files are and keep track of them so they can be removed. Why not enforce this feature and make it possible to change configuration through standardized interface in package management.

Idea is as follows

Application may or may not support configuration through pakage management interface. Support to application is built by adding a separate file which defines the configuration file format and available options. This would have the benefit that anyone who is familiar with the configuration can define the interface and that the creator of the program does not need to be familiar with the system configuration interface. When the package manager installs the interfacefile it reads the program configuration interface and makes the keys available to the system for use by other applications in standardized format.

Now if programmer or administrator wants to change configuration he just simply sends the request to the package manager interface which will find the relevant configuration configuration files and make the relevant changes to the configuration files of the program.

Now if you would like to change the background for every desktop you would set
System.Desktop.Background = image.jpg

For Specific environment
System.Desktop.Background.Gnome = image2.jpg

For specific user

System.Desktop.Background.Gnome.simon = image3.jpg

Lets imagine that we want to set the default browser for Simon home page to [http://intranet.html](http://intranet.html)
and lets imagine that the keypath to Simons browser would be System.User.Simon.Browser.Firefox.Homepage 
So we would set
System.User.Simon.Browser.Firefox.Homepage = [http://intranet.html](http://intranet.html)

Alternatively we could set
System.Programs.Firefox.Homepage = [http://intranet.html](http://intranet.html)
which would affect all users who have not yet set the home page for Firefox but it would not affect Simon. 

Or we could just set
System.Browser.Homepage = [http://intranet.html](http://intranet.html)
which would affect all users. 

In practice the last setting would tell the package manager to find all compatible browser configuration files 
and set home page parameter to [http://intranet.html](http://intranet.html). Now for firefox the native format might be 

Homepage = ULR:[http://intranet.html](http://intranet.html)

For Seamonkey it might be

BrowserHomePage = ([http://intranet.html](http://intranet.html))

and I would not need to care. Also I would not need to care where the files are and how many there are or how many 
users there are. All would be changed with one command. Of course if I would like to know then the interface would be able 
to tell me if I asked.  
 
Now the hierarchy of the system may be totally different of what i describe but the main point is that the 
1. Pakage manager would not store the settings
2. Pakage manager does not care what the settings are, it just reads or writes the setting as specified for it. 
3. With out specific request the package manager would not do anything to configuration.
4. It does not need to be package manager but some method of keeping track of the configuration files would be needed.

---

### Post by Penguin Guy on 2010-03-18
@Naggobot

Thanks. Your explanation was a lot clearer than mine, I've updated my original post and added a link to yours.

---

### Post by Naggobot on 2010-03-19
This is just loosely related to the subject but I comment it here anyhow

It just came to my mind that it would be neat if the package manager could be run on separate server for whole enterprise network (I do not actually know if this is true already). Now with integrated configuration management you would be able to change settings for the whole network with one command if you would run the command to the top level of the configuration hierarchy. 

Of course systems like this already exists so probably nothing particularly new here just a new coherent way of controlling settings of all computers and programs on the network. I have no experience on how the current systems are scripted. 

So individual installations would not have package managers installed. Instead the package manager would run on separate server which would install the programs for every computer on the network and configurations could be managed from the server.

---

### Post by Penguin Guy on 2010-03-19
@Naggobot

I don't think it would be possible to have a shared package manager since computers use different hardware and therefore will require slightly different packages. However I _do_ like the idea of sharing settings across a network.

---

### Post by Penguin Guy on 2010-04-04
I've brought up more points in the first post, including the fact that we need a multi-dimensional settings manager and that we need a way to backup our settings.

---

