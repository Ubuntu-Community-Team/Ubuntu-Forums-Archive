---
title: "uspconfig (Alpha) Test Files"
date: 2007-01-07
forum: Ubuntu System Panel
---

### Post by Malac on 2007-01-07
[B][SIZE=4]USPconfig is now incorporated into usp deb file so please download that from here:
[ _USP2 Alpha Thread_]("http://www.ubuntuforums.org/showthread.php?t=331364")
Or grab the latest SVN Version, details on this thread:
[ _USP2 SVN Thread_]("http://www.ubuntuforums.org/showthread.php?t=231574") [/SIZE][/B]

DO NOT USE with previous usp version 0.41 or below or "old-style" plugins, only use if you are testing the usp 1.9x alpha release.

---

### Post by Malac on 2007-01-07
And the Extra/Add-On plugins.
Again these are for test purposes only and for use with usp 1.9x alpha release.
Use at your own risk.
Some of these will only work with Revision 193 or higher of the SVN version.

If using the tar file:
Extract the files to /home/[COLOR=Gray]<yourusername>[/COLOR]/.usp/plugins
To uninstall just remove them from the folder including the created .pyc and .pyo files

[SIZE=3]**N.B.**[/SIZE] If using the deb file:
You **must** remove any other versions of the plugins from the /home/[COLOR=Gray]<yourusername>[/COLOR]/.usp/plugins folder including the created .pyc and .pyo files or they will take priority over the ones from the deb file.
Then:
dpkg -i usp2_add-on_plugins-1.92_Beta-1_all.deb
From the folder you downloaded it to.
Or double-click in nautilus if you have GDebi installed
To uninstall
dpkg -r usp2-add-on-plugins
Or remove as normal in Synaptic.

The files contain:
[B][SIZE=2] calculator
calrem
internet
notes
remind
resources[/SIZE][/B][SIZE=2] [SIZE=1](This one is still extremely experimental)[/SIZE]
[/SIZE][B][SIZE=2] terminal
uspcalendar
usptime
[/SIZE][/B] Now also contains:
*_In Testing_*
**[SIZE=2]tracker [/SIZE]**(by Quikee)[B][SIZE=2]
[/SIZE][/B] 
The last two have usp at the beginning due to python reserved module names.
**The Terminal uses <Shift><Ctrl>C for copy function and <Shift><Ctrl>V for paste function**.

As with usp 0.41 add them by name to plugins list, the names are all lowercase.
I recommend adding them one at a time through gconf-editor or using uspconfig [Main] tab.

As above, post any errors here stating which plugin you had loaded and the output from "usp run-in-window" and/or "uspconfig".
Enjoy and Thanks

---

### Post by delfick on 2007-01-07
YAYAYAY!!!!! thankyou malac :D

they all seem to be working fine, except....

For example i get this for the Remind plugin (which looks very useful, did we have that one before ???)

> [Quote]iambob@bob-linux:~$ uspconfig
Plugins Without Config Section, With Errors Or Not Found:
remind

> iambob@bob-linux:~$ usp run-in-window
Loading plugin 'applications' : sucessful
Loading plugin 'shortcuts' : sucessful
Loading plugin 'remind' : sucessful
Loading plugin 'terminal' : sucessful
Loading plugin 'notes' : sucessful
[/Quote]

and nothing appears in gconf-editor for it......so i can't seem do anything with it...


another odd thing, is even though it seems to work fine, the same thing happens for the recent plugin...

> iambob@bob-linux:~$ uspconfig
Plugins Without Config Section, With Errors Or Not Found:
recent



once again, thankyou malac :D:D

---

### Post by Malac on 2007-01-07
Hi delfick,
remind is a split of the calrem plugin, just the reminders and, yes, we had that one before. :)
It is to show todays appointments and any outstanding tasks.
There is no uspconfig section for that yet I need to copy it over from calrem and tweak with it a bit.
The settings are:
/apps/usp/plugins/calendar/height
/apps/usp/plugins/calendar/sticky
/apps/usp/plugins/calendar/height_appoints
/apps/usp/plugins/calendar/height_tasks
/apps/usp/plugins/calendar/width
/apps/usp/plugins/calendar/item_font_size
/apps/usp/plugins/calendar/heading_font_size

At the moment the recent plugin has not had the updated uspconfig section put in. And some of the other "standard" plugins will need updating in the deb
 I've sent copies to chanders today but he is really busy with the main app so he probably hasn't had time to re-package the .deb yet.

Thanks for trying the plugins, good to know they work.
Malac.

---

### Post by delfick on 2007-01-08
> **Malac said:**
> remind is a split of the calrem plugin, just the reminders and, yes, we had that one before. :)

k then :D


> At the moment the recent plugin has not had the updated uspconfig section put in. And some of the other "standard" plugins will need updating in the deb
 I've sent copies to chanders today but he is really busy with the main app so he probably hasn't had time to re-package the .deb yet.

k then :D

> Thanks for trying the plugins, good to know they work.
Malac.

(i would say k then :D to continue the trend of the last two answers, but i decide against it, instead...)


cool :D your welcome :D

---

### Post by Malac on 2007-01-08
Added calrem, uspcalendar and remind with uspconfig sections to the post #2 tar file.
Also the above and internet plugin now follow the theme.

---

### Post by Malac on 2007-01-09
Here's a screenshot with the new plugins.
In order:
----------------------------
uspuser
applications
system_management
----------------------------
internet
notes
reminds
----------------------------
usptime
uspcalendar
terminal
calculator
----------------------------

---

### Post by delfick on 2007-01-09
wow. that thing's huge :D :P :D

i think if you had compact system management, and then made the height of the applications and remind plugins line up with the calculator, then it would look even better :D

---

### Post by Malac on 2007-01-10
> **delfick said:**
> wow. that thing's huge :D :P :D
Yeah I know and that's on 1024x768.
I don't actually run it like that, just thought I'd show what they should look like for others. :)

---

### Post by delfick on 2007-01-10
> **Malac said:**
> Yeah I know and that's on 1024x768.
I don't actually run it like that, just thought I'd show what they should look like for others. :)

hmm, maybe you should run it like that :D :D 


maybe we could have it so clicking on the usp button opens up the menu (as it does now)

but also, via some other method of activation, we have a fullscreen usp .....:D

---

### Post by Malac on 2007-01-10
> **delfick said:**
> maybe we could have it so clicking on the usp button opens up the menu (as it does now)

but also, via some other method of activation, we have a fullscreen usp .....:D
Actually for a later release, if I've time to get round to it, I've been thinking about trying tabs for different pages of plugins.
Or maybe a scrollbar if I've got lots of plugins open. :)

---

### Post by delfick on 2007-01-10
> **Malac said:**
> Actually for a later release, if I've time to get round to it, I've been thinking about trying tabs for different pages of plugins.
Or maybe a scrollbar if I've got lots of plugins open. :)

that sounds quite good :D

---

### Post by Malac on 2007-01-11
Okay here is a screenshot of my menu with a scrollbar at the bottom for when you've just got too many plugins. :)
Although this introduces loads of other programming probs for sizing the plugins, etc.
Having tried it out I think separate pages is the way forward.

---

### Post by delfick on 2007-01-11
that looks useful :D

---

### Post by ardchoille42 on 2007-01-12
> **Malac said:**
> Actually for a later release, if I've time to get round to it, I've been thinking about trying tabs for different pages of plugins.
Or maybe a scrollbar if I've got lots of plugins open. :)
 Tabs are good.. here's my vote for tabs. Tabs are your friend :)

---

### Post by hanzomon4 on 2007-01-12
Thanks! 
Ok I noticed two things [list][*]when you type something into the search bar you can't press enter to initiate the search [*]and when you click the search icon usp stays open.[/list] 
I also have a little gap between my usp and the gnome-panel and I can't set it to 0, only 1, which use to fix the gap

---

### Post by ardchoille42 on 2007-01-13
> **hanzomon4 said:**
> Thanks! 
Ok I noticed two things [list][*]when you type something into the search bar you can't press enter to initiate the search [*]and when you click the search icon usp stays open.[/list] 
I also have a little gap between my usp and the gnome-panel and I can't set it to 0, only 1, which use to fix the gap

My USP closes when I click the search button. It is possible that you have the "apps/usp/pin_menu" option enabled in gconf-editor? IF so, uncheck that setting and usp should close when you click the search button - I'm not sure if this requires a restart of usp to take effect or not..

---

### Post by Malac on 2007-01-19
Updated the tar file at post #2 with new usptime.py and usptime.glade files which now feature analog clock, finally got it working.
If someone could test them that would be cool.:D

Thanks.

---

### Post by delfick on 2007-01-19
are you able to add it to the svn version :D

(i'm lazy :D :p....and must leave computer now :( :D)

---

### Post by Malac on 2007-01-20
Just to tantalize you.
I have managed to knock up a USP2 that has tabbed pages of plugins, just for a laugh. There is a bit of a problem with the pin menu button wiping out the files but I'll work on it.
Here are the screenshots.
[ATTACH]23534[/ATTACH][ATTACH]23535[/ATTACH]
At the moment it only has two pages but theoretically it is limitless.

---

### Post by delfick on 2007-01-20
Cool :D

---

### Post by Malac on 2007-01-21
Okay solved the pin menu problem and the reload plugins problem with the tabs.
[ATTACH]23585[/ATTACH][ATTACH]23586[/ATTACH][ATTACH]23587[/ATTACH]
Just thought you might like to see the progress.

---

### Post by delfick on 2007-01-21
that's awsome :D

---

### Post by Malac on 2007-01-22
Moved the tabs to the top I think this should work better.
Also added ability to name the tabs or not.
New screenshots.
[ATTACH]23639[/ATTACH][ATTACH]23640[/ATTACH][ATTACH]23641[/ATTACH]
If we can get transparency I can get rid of the ugly bit at the right of the tabs.

---

### Post by delfick on 2007-01-22
the tabs are much better at the top :D.......

hmmm, speaking of transparency........how about real transparency :D :D :D
(i've really gotta stop asking for that :P)

---

### Post by chanders on 2007-01-22
> **delfick said:**
> speaking of transparency........how about real transparency :D :D :D
(i've really gotta stop asking for that :P)

You will be glad to know that I already have SOME real transparency going ;-)  But I am new to Cairo so it wont be making it's way into USP2 but definitely be making it's way in the future ;-)

---

### Post by delfick on 2007-01-22
> **chanders said:**
> You will be glad to know that I already have SOME real transparency going ;-) 

:D :D :D :D :D 

> But I am new to Cairo so it wont be making it's way into USP2 but definitely be making it's way in the future ;-)

at least the dream is alive :D

---

### Post by Malac on 2007-01-31
I have updated the post #2 tar terminal plugin to fix the "cpu hogging" bug when it is minimized.
Testers Welcome. :)

---

### Post by TheMono on 2007-01-31
AH HA! That's what the bug for me must have been!

---

### Post by delfick on 2007-02-09
can the internet plugin be made to use google bookmarks ??

---

### Post by Malac on 2007-02-09
> **delfick said:**
> can the internet plugin be made to use google bookmarks ??
Depends on the format of the file it uses and if it is stored locally or not. If it follows the XML guidelines for this stuff then yes. If it doesn't then I don't know.
Attach a copy of the file it uses and I'll take a look.

EDIT:
Just checked and all the bookmarks are stored on the Google Servers.
To access these files the plugin would need to know your Google Account Username and Password.
I wouldn't feel particularly happy about having to store that stuff in gconf or have you need to input it every time USP started up.
This would be a potential security hole into your Google Account.

---

### Post by delfick on 2007-02-09
> **Malac said:**
> Depends on the format of the file it uses and if it is stored locally or not. If it follows the XML guidelines for this stuff then yes. If it doesn't then I don't know.
Attach a copy of the file it uses and I'll take a look.

google bookmarks is an online service [www.google.com/bookmarks](www.google.com/bookmarks)

so there is no file :P

if it helps, this plugin for firefox retrieves the bookmarks from it [https://addons.mozilla.org/firefox/2448/](https://addons.mozilla.org/firefox/2448/)

---

### Post by Malac on 2007-02-19
Updated post #2 with new files which are tested and all work under standard Feisty.

---

### Post by Malac on 2007-02-26
[I]Uploaded fixes to calrem and remind recurring events.
This was a pain as evolution seems to have no set format for these events in the file. I hopefully have covered most eventualities but there are probably a few that have slipped through the cracks. :)
Let me know via pm.
[/I]

---

### Post by Malac on 2007-03-10
Updated calrem and remind plugins to handle multiple files, repeat and excluded dates.
Thanks to 4tro for the lend of his file. :)

Changes to these files seem to have halved the CPU usage and a quarter less RAM of USP when opened.

---

### Post by delfick on 2007-03-11
> **Malac said:**
> Changes to these files seem to have halved the CPU usage and a quarter less RAM of USP when opened.

awsome :D

---

### Post by Malac on 2007-03-18
Updated post #2 with new terminal plugin which stops repeated spawning of bash shells on reload plugins.

---

### Post by rolando on 2007-03-21
Hello, 

USP is great!, Nice work! Its what Gnome has been waiting for!  

I am using it and it is speeding up my access to my programs, documents etc.  The terminal plugin is especially handy.

I do have one thing to add regarding the applications tab.

1. In the applications tab, when you have searched for a program name in the search box, pressing tab to take you to the top of the programs found list would be great, then you could type the name, press tab, go down with the arrow keys and press enter to launch a program, instead of having to grab your mouse and click on it.  (Or press tab about 30 times to ge to it)

Apart from that, its awesome, really is!

---

### Post by Malac on 2007-03-25
Added a simple resources monitor to post #2 tar and deb.
[ATTACH]28225[/ATTACH]

---

### Post by delfick on 2007-03-26
> **Malac said:**
> Added a simple resources monitor to post #2 tar and deb.
[ATTACH]28225[/ATTACH]

awsome :D

will test later (don't have time to even read forums atm but i am :D)

---

### Post by Malac on 2007-03-28
Added CPU Usage and Top Process Info. to resources plugin. in .tar and .deb at post #2
At the moment it shows the last Top Process used even if that isn't running at the moment(i.e. the machine is just idling).
I know where the code needs changing, I've just run out of time today. I'll get to it maybe tonight.

---

