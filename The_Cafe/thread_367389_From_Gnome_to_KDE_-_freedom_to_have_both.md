---
title: "From Gnome to KDE - freedom to have both"
date: 2007-02-22
forum: The Cafe
---

### Post by steffen on 2007-02-22
After three years on Gnome, I decided to install Kubuntu on my work-laptop two days ago, just to see what it's like. Is it just me, or does KDE seem more mature?

I'm impressed by the added functionality in KDE. Menus, right-clicking, control panel, visual indicators, and the availability of great programs that run natively - Kate is a decent replacement for Gedit, Konsole is a decent replacement for Terminal, Kopete seems better than Gaim, Ktorrent is miles ahead of any GTK-torrent, remote desktop with Krdc is actually usable, wifi control seems way easier, etc. Overall, my feeling is that I'm now using a DE that is actively developed as opposed to maintained, and that I'm using a DE instead of a GUI to a terminal.

However, there are a few things I'm missing so far...
[LIST][*]I was accustomed to the Gnome applications menu. I must admit that starting a program, home folder, etc. is much more user friendly in Gnome than KDE[*]Gnome is definitely cleaner. In KDE the menus are much more scattered around and the UI doesn't seem as unified[*]Nautilus is easier and cleaner, but lacks functionality and configurability
[/LIST]

Bottom line is that KDE seems way more configurable, and has more functionality, while Gnome is cleaner and easier to use. It seems that KDE is being used by people actually using their computers for a wide array of tasks, whereas Gnome seems to be developed by people who uses Gnome to give to Grandma for basic tasks, but stick to command-line themselves. I'm sure this isn't a fair description, but that's the feeling I'm left with.

My question now is - can I have both? I'd prefer to have a desktop that looks like Gnome, but acts like KDE and is actively developed. For example - a Gnome with Kopete, kwifi, KDE control centre, Ktorrent, KDE bluetooth, Amarok, Krdc, K3B, etc. It seems that the apps that I most frequently use are better maintained by KDE than Gnome - CD-burner, music, movies, networking, chat, etc. I'm probably not the first person asking for this, and I know the Portland project is trying to solve some of it - but my guess is that I won't see any action there soon. I've been trying to find replacements for my GTK-software - Exaile works well instead of Amarok - but it seems that overall the GTK-apps are playing catch-up, while the KDE-apps are moving ahead. It's specifically the active development and control centre that seems missing from Gnome...

And a second question - is there any way of running Opera, K3B, Kopete, KDE-bluetooth, Ktorrent, Krdc, etc. in Gnome without impaired speed?

---

### Post by manmower on 2007-02-22
How about just tweaking KDE's layout to resemble whatever you're used to from Gnome, and editing the menus, panels and toolbars to mimic the Gnome structure, removing entries you don't use anyway. It's how I have my KDE configured, and helps me feel reasonably at home. I'm a Gnome user 90% of the time but like to keep track of KDE development also, and this seems to be the solution for me.

---

### Post by Mark C on 2007-02-22
> I've been trying to find replacements for my GTK-software - Exaile works well instead of Amarok - but it seems that overall the GTK-apps are playing catch-up, while the KDE-apps are moving ahead. It's specifically the active development and control centre that seems missing from Gnome...

Do you know that you can make GNOME apps look native in KDE by installing gtk-qt-engine? Just do that and then search for gtk in the control center, magic huh?
> 
And a second question - is there any way of running Opera, K3B, Kopete, KDE-bluetooth, Ktorrent, Krdc, etc. in Gnome without impaired speed?

They already run full-speed, as far as I can see, but GNOME just has to load the qt libraries first so that makes starting a KDE application slower, but will perform natively after the qt libraries are loaded.

---

### Post by Bloodfen Razormaw on 2007-02-22
> And a second question - is there any way of running Opera, K3B, Kopete, KDE-bluetooth, Ktorrent, Krdc, etc. in Gnome without impaired speed?
I assume that any speed problems you have are with startup times, since run times will be identical for these applications no matter the desktop.  Make dcopserver start with GNOME and you will probably find startup times improve drastically.  Without it, the applications wait for a response from the dcopserver to timeout before proceeding.

---

### Post by steffen on 2007-02-22
> **manmower said:**
> How about just tweaking KDE's layout to resemble whatever you're used to from Gnome, and editing the menus, panels and toolbars to mimic the Gnome structure, removing entries you don't use anyway. It's how I have my KDE configured, and helps me feel reasonably at home. I'm a Gnome user 90% of the time but like to keep track of KDE development also, and this seems to be the solution for me.

Manmower: How did you do that? I don't mean colours, etc. but actual start menu, menu system, nautilus, etc.?

Thanks for the suggestion on dcopserver in Gnome. I'll try that.

How about the KDE-specific desktop deamons, like the wifi-connector, bluetooth, etc. Would they work as well under Gnome as KDE?

---

### Post by lyceum on 2007-02-22
> **steffen said:**
> Manmower: How did you do that? I don't mean colours, etc. but actual start menu, menu system, nautilus, etc.?

Thanks for the suggestion on dcopserver in Gnome. I'll try that.

How about the KDE-specific desktop deamons, like the wifi-connector, bluetooth, etc. Would they work as well under Gnome as KDE?

It you want it to look like Gnome in Ubuntu, just put a bar at the top and a bar at the bottom. Load them how you like, right click and edit. :)

I do not think you can get the "applicationsplaces , systems" though.

---

### Post by steffen on 2007-02-27
I just came across Dolphin (available in repositories). A really good Nautilus-replacement in KDE :)

Here's how my desktop looks currently. I'm pretty pleased with it.

---

### Post by darkhatter on 2007-02-27
> **steffen said:**
> I just came across Dolphin (available in repositories). A really good Nautilus-replacement in KDE :)

thats the new kde 4 file manager

---

### Post by Erunno on 2007-02-27
> **steffen said:**
> And a second question - is there any way of running Opera, K3B, Kopete, KDE-bluetooth, Ktorrent, Krdc, etc. in Gnome without impaired speed?

You'll probably always have a slight delay as the kdelibs have to be loaded into memory the first time you start a KDE application and it will use more memory since backend data from both DEs has to be loaded. Starting DCOP server is a good idea already proposed here, so the applications won't wait for a timeout.

A slightly larger problem will be to get the qt apps fit into the GNOME environment as GNOME lacks the the equivalent of gtk-qt-engines. There's a cross-platform theme (called curves something) which is said to look about the same on both DEs. You'll probably have to install kcontrol though to change the KDE settings.

Apropos, Opera is desktop independent.

---

### Post by steffen on 2007-02-27
> **Erunno said:**
> You'll probably always have a slight delay as the kdelibs have to be loaded into memory the first time you start a KDE application and it will use more memory since backend data from both DEs has to be loaded. Starting DCOP server is a good idea already proposed here, so the applications won't wait for a timeout.

A slightly larger problem will be to get the qt apps fit into the GNOME environment as GNOME lacks the the equivalent of gtk-qt-engines. There's a cross-platform theme (called curves something) which is said to look about the same on both DEs. You'll probably have to install kcontrol though to change the KDE settings.

Apropos, Opera is desktop independent.

I have seen that running KDE (and QT as well, afaiks) apps in Gnome quickly fills up my 1GB RAM. I'd say that's the biggest problem about not caring which DE the application is written for is. That was my main problem with running Gnome.

In addition, I see that my KDE menu loads way faster than the Gnome applications menu. (KDE is instant, Gnome took half a second). Don't know why that is...

---

### Post by bailout on 2007-02-27
Agree totally that kde apps are usually much better than gnome equivelents. Whenever I see people asking which DE to choose I always say to try both and see which apps they mostly prefer and then to use the corresponding DE. If you mostly use kde apps then it seems to make sense to use kde and vice versa. 

You seem to have got quite far in customising the kde layout already. My advice is to alter it to how you want but don't get too obsessed with copying gnome completely. Obviously you are used to the gnome layout but it isn't the only way and you will get used to a slightly different layout quickly. 

I have my desktop very similar to yours but with the top bar on autohide to save some space. I also put quicklaunch buttons to my usual apps as you have done and find that I rarely use the menu at all. 

I also changed the colour scheme and install neovo xt icons from kde-look as I find the kde icons a bit shiny.

Also, don't give up on konq too quickly. It can be customised quite a lot, although this should be made easier. Once you get used to it it does over more than the windows explorer clones such as nautilus/dolphin etc.

---

### Post by steffen on 2007-02-28
This post captures my feeling quite nicely, actually: [http://beranger.org/index.php?article=2484](http://beranger.org/index.php?article=2484)

---

