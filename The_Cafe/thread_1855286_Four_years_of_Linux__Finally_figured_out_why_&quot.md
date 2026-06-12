---
title: "Four years of Linux:  Finally figured out why &quot;Preferences&quot; is under &quot;Edit.&quot;"
date: 2011-10-05
forum: The Cafe
---

### Post by ninjaaron on 2011-10-05
I always wondered why program preferences were under 'Edit' in most GTK apps, when the other options in that menu (both on Linux and other desktop platforms) has to do with manipulating content inside of the app.

Finally, after using Arch for a couple of months, I've figured it out.  When you set your preferences, your really just 'editing' a text configuration file with a GUI wrapper.  Unix.  Text is the universal interface.  I'm all hot and bothered for plain text, so this pleases me greatly.

Can anyone confirm or deny my conclusion?

---

### Post by jwbrase on 2011-10-05
I don't think that really has anything to do with it. Different programs will store their preferences in different ways.

I've always thought of it more along the lines of "edit means change, and we're changing preferences".

---

### Post by ninjaaron on 2011-10-05
Well, that's true, but the vast majority of Linux programs still store their user settings in text files, and this was certainly even more the case when the toolkit in question (GTK) was first being developed.

Most of the menus can be used to "change stuff," in any event.

---

### Post by crdlb on 2011-10-05
Well, the most direct cause is the GNOME HIG: [http://developer.gnome.org/hig-book/3.2/menus-standard.html.en#menu-standard-edit](http://developer.gnome.org/hig-book/3.2/menus-standard.html.en#menu-standard-edit) .  However, with the application-based design of gnome-shell, I suspect GNOME will eventually put Preferences in the shell's global app menu (the one that currently only has a 'Quit $APP' entry).

---

### Post by Copper Bezel on 2011-10-05
Yeah, if it was about the file you were editing to change the preferences, which isn't the present file, wouldn't it be under File? = ) Only File and Help are mostly-application- rather than mostly-document-centric.

---

### Post by 3rdalbum on 2011-10-05
Non-*nux platforms use "Edit > Preferences" too. It's nothing to do with text files, it's because you are "editing the preferences".

It's not a good place to put the prefs; the Edit menu should mean "ways to edit this document".

---

### Post by ubupirate on 2011-10-05
> **3rdalbum said:**
> Non-*nux platforms use "Edit > Preferences" too. It's nothing to do with text files, it's because you are "editing the preferences".

Firefox on Windows = Tools->Preferences. :D

---

### Post by vasa1 on 2011-10-05
> **ubupirate said:**
> Firefox on Windows = Tools->Preferences. :D

Not just Firefox. Quite a few programs have Tools > Options rather than Edit > Preferences. The former seems a Windows thing, the latter, Mac and Linux.

---

### Post by Alwimo on 2011-10-05
You go there to edit the preferences, is how I think about it.

---

### Post by kvvv on 2011-10-05
> **ninjaaron said:**
> I always wondered why program preferences were under 'Edit' in most GTK apps, when the other options in that menu (both on Linux and other desktop platforms) has to do with manipulating content inside of the app.

Finally, after using Arch for a couple of months, I've figured it out.  When you set your preferences, your really just 'editing' a text configuration file with a GUI wrapper.  Unix.  Text is the universal interface.  I'm all hot and bothered for plain text, so this pleases me greatly.

Can anyone confirm or deny my conclusion?

Dammit! I have always wondered about the same thing! :)

You are too smart, my friend!

---

### Post by Thewhistlingwind on 2011-10-05
I never really *thought *about it like that, but guessed what you were getting at from the title.

I don't really know, it would make sense though.

---

### Post by ninjaaron on 2011-10-06
> **vasa1 said:**
> Not just Firefox. Quite a few programs have Tools > Options rather than Edit > Preferences. The former seems a Windows thing, the latter, Mac and Linux.I think Mac also has something else, cause I remember thinking it was weird when I switched to Linux after being an OSX user for 5 years.  I think on Mac, the applications name is always in the universal menu, and I think preferences are down there (which is probably a bit more logical and intuitive in the desktop metaphore).

Even many qt apps have something else.  A lot of them have a 'settings' menu.  LibreOffice also has something more like what Windows has (tools>options).  I think the Edit>Preferences is primarily a GTK phenomenon.


> **kvvv said:**
> Dammit! I have always wondered about the same thing! :)

You are too smart, my friend!

Well, at least one person thinks so... or rather two, as I most certainly also think I am too smart. :D

---

### Post by beew on 2011-10-06
I noticed this too. Compare FireFox windows and Linux version. In Linux options are set under Edit whereas in Windows it is under Tools or something (sorry haven't paid attention in anything windows for a while)

---

### Post by el_koraco on 2011-10-06
nah, that's because Gnome copied the HIG from Apple.

---

### Post by SavageWolf on 2011-10-06
Maybe it's something like you are "editing" your environment/interface or something?

---

### Post by ninjaaron on 2011-10-06
> **el_koraco said:**
> nah, that's because Gnome copied the HIG from Apple.

[IMG]http://www.burlyhouse.net/images/burlymail/help/apple-mail/preferences.jpg[/IMG][IMG]http://www.switchingtomac.com/wp-content/uploads/2011/04/Apple-Toolbar-Safari-Preferences.png[/IMG][IMG]http://www.fileinfo.com/images/help/mac-finder-preferences.gif[/IMG][IMG]http://imovie.maccreate.com/files/2010/11/media_1288751042012.png[/IMG][IMG]http://itp.nyu.edu/physcomp/uploads/midi/midi_screen3.png[/IMG][IMG]https://secure.madasafish.com/images/support/internet/browsing/firefox/firefox_mac_osx_config1.jpg[/IMG]

Anyone else want to say this has something to do with Apple?

---

### Post by el_koraco on 2011-10-06
> **ninjaaron said:**
> 

Anyone else want to say this has something to do with Apple?

Well, it's the principle. Every application should have a preferences dialog, and they should all be in the same place. If/when they add the preferences to the running application icon or whatever the stupid thing on the top bar is called, it will be almost the same.

---

### Post by BrokenKingpin on 2011-10-06
> **ninjaaron said:**
> I always wondered why program preferences were under 'Edit' in most GTK apps, when the other options in that menu (both on Linux and other desktop platforms) has to do with manipulating content inside of the app.

Finally, after using Arch for a couple of months, I've figured it out.  When you set your preferences, your really just 'editing' a text configuration file with a GUI wrapper.  Unix.  Text is the universal interface.  I'm all hot and bothered for plain text, so this pleases me greatly.

Can anyone confirm or deny my conclusion?
You are looking way too far into this. It simply means to edit your preference.

---

### Post by Copper Bezel on 2011-10-06
[QUOTE=el_koraco]Well, it's the principle. Every application should have a preferences dialog, and they should all be in the same place. If/when they add the preferences to the running application icon or whatever the stupid thing on the top bar is called, it will be almost the same.[/QUOTE]

Yes, but that's just sensible; *shouldn't* the desktop generally be self-consistent, so that you can find things in new apps? To me, that's no different from following all those nutty VI conventions in terminal apps. It's just a matter of consistency. (For that matter, can we just have Apple's IG in Gnome now? They make sense.)

---

### Post by el_koraco on 2011-10-06
> **Copper Bezel said:**
> Yes, but that's just sensible; *shouldn't* the desktop generally be self-consistent, so that you can find things in new apps? 

It does make sense. I remember sometimes having to search for the preferences/options dialog in Windows, and there were occasions where stuff wasn't so clearly defined (though i can't remember the exact examples). It's just that the whole thing has little to do with a "I edit config files" logic, and more with copying Apple. Gnome doesn't, or rather, didn't, have a global menu entry, and the "Tools" entry isn't there in every application, so it only made sense to put preferences in Edit. The "Help" entry also always has an "About" dialog in every GTK app, like you can find in Apple's global menu, and that has little to do with the terminal "program --version".

---

### Post by ninjaaron on 2011-10-06
> **Copper Bezel said:**
> Yes, but that's just sensible; *shouldn't*To me, that's no different from following all those [s]nutty[/s] *wonderful* VI conventions in terminal apps.

fixed
:p

---

### Post by ninjaaron on 2011-10-06
> **el_koraco said:**
> Well, it's the principle. Every application should have a preferences dialog, and they should all be in the same place. If/when they add the preferences to the running application icon or whatever the stupid thing on the top bar is called, it will be almost the same.

That may be, but it still doesn't answer why "Preferences" ends up under "Edit" when everything else in that menu has to do with editing content.  It makes a lot more sense that you would configure the application with the application menu than the edit menu, unless whomever is writing the HIG is thinking about editing config files (it still doesn't make as much sense, but it at least provides a partial explanation for the craziness).

---

### Post by el_koraco on 2011-10-06
> **ninjaaron said:**
> That may be, but it still doesn't answer why "Preferences" ends up under "Edit" when everything else in that menu has to do with editing content. It makes a lot more sense that you would configure the application with the application menu than the edit menu

What application menu? GTK interfaces have File, Edit, View and Help as a default, and other chime in from time to time. Your interpretation may be true, but I kinda think it's an issue of copying the Apple HIG, and just slapping the preferences anywhere since you don't have the application menu item like in OSX.

---

### Post by ninjaaron on 2011-10-06
> **el_koraco said:**
> What application menu? GTK interfaces have File, Edit, View and Help as a default, and other chime in from time to time. Your interpretation may be true, but I kinda think it's an issue of copying the Apple HIG, and just slapping the preferences anywhere since you don't have the application menu item like in OSX.

I realize that GTK doesn't have an application menu.  I was just saying that Apple's placement has a clearer logic than GTK's.  Of course, they could have designed GTK HIG with an application menu if they really wanted to.  It's not a matter of "not having an application menu" when your the one deciding what the menus will be.

I don't use many QT apps, but those I do use have a "settings" menu, which makes sense.  Tool>Preference/Tools>Options also makes sense.  For the life of me, since I started using Linux, I haven't been able to make out why anyone in their right mind would do edit>preferences.  I feel like I finally found some faint glimmer of design behind it.

DON'T TAKE THAT FROM ME!!

---

### Post by el_koraco on 2011-10-06
> **ninjaaron said:**
>   For the life of me, since I started using Linux, I haven't been able to make out why anyone in their right mind would do edit>preferences.  I feel like I finally found some faint glimmer of design behind it.


I've never been able to figure out a lot of stuff about Gnome. It's like they smoke a lot of weed, then come up with something, and do it.

---

### Post by Copper Bezel on 2011-10-06
To be fair, Gnome's per-app menu bars do have a tighter space constraint than a global menu widget does, so there might have been some pressure to reduce the number of items. 

Scattering application-level functions through the File, Edit, and Help menus was a stupid solution, but the problem *might* have been real. = )

---

