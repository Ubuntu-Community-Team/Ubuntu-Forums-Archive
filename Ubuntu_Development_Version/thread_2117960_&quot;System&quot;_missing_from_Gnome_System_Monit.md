---
title: "&quot;System&quot; missing from Gnome System Monitor 3.7.5"
date: 2013-02-19
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-02-19
Anybody else notice this?


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-feb-2013-1.png")[/INDENT]


I noticed the "System" tab disappeared from Gnome System Monitor, after I upgraded to version 3.7.5.  I thought it was a shame for them to remove it, but that's been the pattern lately -- removing things.

Tonight, I was over on Softpedia, reading about Gnome System Monitor 3.7.5, and the picture they displayed (which may be an older version) clearly shows the "System" tab.

Which is it?!?!?

Is the "System" tab missing from your Gnome System Monitor?

I didn't see anything in their '[changelog]("http://ftp.acc.umu.se/pub/GNOME/sources/gnome-system-monitor/3.7/gnome-system-monitor-3.7.90.changes")' about removing it...

SOURCE:  [http://news.softpedia.com/news/Gnome-System-Monitor-Updated-to-Fix-Several-Memory-Leaks-326871.shtml](http://news.softpedia.com/news/Gnome-System-Monitor-Updated-to-Fix-Several-Memory-Leaks-326871.shtml)

> Gnome System Monitor, an application that enables users to display basic system information and to monitor system processes, usage of system resources, and file systems, is now at version 3.7.5.

The application shows active processes and how processes are related to each other. It also provides detailed information about individual processes.

Highlights of Gnome System Monitor 3.7.5:

• Incorrect CPU usage chart values were displayed with multiple cores;
• Incorrect quotes in process end/kill dialogs have been repaired;
• An incorrect message in the preferences dialog has been corrected;
• An incorrectly translatable priority string, from the change priority dialog, has been fixed;
• The main window maximized state is now saved in gsettings.
• Several memory leaks have been plugged.

Check the changelog for a complete list of updates and fixes.

Download Gnome System Monitor 3.7.5 right now from Softpedia. Remember that this is a development version and it should NOT be installed on production machines. It is intended for testing purposes only.

It certainly uses a LOT less memory now, but I sorely miss the "System" tab...  :(

---

### Post by jbicha on 2013-02-20
> **VinDSL said:**
> 
Is the "System" tab missing from your Gnome System Monitor?

I didn't see anything in their '[changelog]("http://ftp.acc.umu.se/pub/GNOME/sources/gnome-system-monitor/3.7/gnome-system-monitor-3.7.90.changes")' about removing it...


Yes, but it was removed for 3.7.4. Try the full [changelog]("http://git.gnome.org/browse/gnome-system-monitor/tree/NEWS"). Except for the kernel version, I believe the rest of the information is in the Settings>Details panel which is a better, more discoverable location. (The GNOME version is also missing but that's because of a Ubuntu patch.)

---

### Post by ventrical on 2013-02-20
> **jbicha said:**
> Yes, but it was removed for 3.7.4. Try the full [changelog]("http://git.gnome.org/browse/gnome-system-monitor/tree/NEWS"). Except for the kernel version, I believe the rest of the information is in the Settings>Details panel which is a better, more discoverable location. (The GNOME version is also missing but that's because of a Ubuntu patch.)


@vinDSL ,
Thanks for the heads up. For some reason I still have  3.6.1 on fully updated raring (unless I have to enable pre-leased in repos)! lol

@jbicha

I disagree that developers had to remove that option because it would be more discoverable in System>Details> This is more parsing and ferreting down of Ubuntu as a whole to encapsulate the 'slate' nouveau concept. Beta testers (and most home users) are using hard towers or e-machines that are not usually toted. My feeling is that Ubuntu (or Canonical for that matter) should split out a separate iso for slate machines.

raring-slate-i386.iso, for example would be a lot more comprehensive to phone,pod,pad and tablet users. These slates are *not* desktops!!  This brings to mind again the debate over permissions in nautilus being 'me' and not the name of the owner. Introducing concept changes to tools that are proven workhorses with the intent of slip-sliding a hand-off to slate machines is not infrastructurally of sound logic and will create more complex bugs and more recent machines cycling on to the legacy list.

---

### Post by grahammechanical on 2013-02-20
The system page in System Monitor has been missing for a couple of weeks in my Raring Ubuntu Gnome Remix + 2 x PPAs.

Still got it on standard Ubuntu Raring. How useful was it? I am not sure. It was useful as an easy way to check what kernel version was running. That sort of stuff. Useful for people like us who are tracking the development of one version of Ubuntu into another one but. may be not so useful for ordinary users. System Monitor now looks like a book that is missing its front cover.

Edit: Today's update (21/03/2013) upgraded System Monitor and now the System page is missing in standard Raring. A bit of a shame I think.

Regards.

---

### Post by VinDSL on 2013-02-20
> **grahammechanical said:**
> System Monitor now looks like a book that is missing its front cover.
Well put!  :D

---

### Post by PJs Ronin on 2013-02-21
I love Ubuntu with a passion after being a Windows addict for more years than I care to remember.   I'm also trying my best to keep up with new developments by bumbling my way through Raring occasionally going "oooh, ahhh" and sometimes going "you have GOT to be joking".   The removal of the 'System' tab is one of those head scratch moments.

Let's remember that this is the gnome-system-monitor it should therefore 'monitor' things, particularly about the 'system'.   A one-stop-shop if you will... a source of consistency and information visible at a glance... a place where non-terminal-officionardoes like myself can go to find out wth I've done to my computer.

Splitting an important resource like this into different areas, especially one that may be perceived as a more discoverable location, just doesn't cut it in my book.

I urge the developers to consider two tenets.   1) If it ain't broke, don't fix it.   2)  Unless you're getting 10,000 complaints a day about the location of key elements then don't change the map.   Change for the sake of change is not, imo, progress.   Change to increase productivity should be pursued.

I see no productivity gain in messing with the gnome-system monitor.

---

### Post by rtalcott on 2013-02-21
The System tab was very conveniently located...I hate to see it go...I run multiple machines with various kernels and OS versions so I tend to look at this tab often....

---

### Post by grahammechanical on 2013-02-22
> **rtalcott said:**
> The System tab was very conveniently located...I hate to see it go...I run multiple machines with various kernels and OS versions so I tend to look at this tab often....

Same for me but with only one machine. I saw this change first in Ubuntu Gnome Remix well before it came into Ubuntu Raring, so I guess that this was a change made by the Gnome developers and not the Ubuntu ones.

---

### Post by ventrical on 2013-02-22
Just got it in today. Looks .. awful.  I just did a conversion with a new prospect (customer)..and I really laid the Ubuntu Concepts on really thick. This person is a complete noob .. so it will be tough to explain these changes to noobs after I spent a lot of time familiarizing them with  the standard set.

---

