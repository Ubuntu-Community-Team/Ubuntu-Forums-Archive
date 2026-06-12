---
title: "HOWTO: GEDIT history list &amp; line numbering"
date: 2005-01-04
forum: Tutorials
---

### Post by wallijonn on 2005-01-04
**TIPS & Tweaks:**
---------------------------------------------------------------------------------------------------------
Gedit history / recent file number can be increased by 

[COLOR=Blue]Applications -> System Tools -> Configuratoion Editor ->[/COLOR] 
[COLOR=Red]apps -> gedit-2 -> preferences -> ui -> recents ->[/COLOR] 
click the right pane, either double click under the "name" or click once in the "value" box.

I have set mine to 30 just because it seems to scroll all the way down to the bottom of the screen. set according to your preference. 

This should decrease your time searching for a file. Once you open Gedit, just hit "File" on the menu bar and scroll down to open.  

---------------------------------------------------------------------------------------------------------

Another great option is to enable line numbering. 
[COLOR=Red]apps -> gedit-2 -> preferences -> editor -> line_numbers ->[/COLOR]
Check (on) the right panel box.

This will ease the chore of counting lines when searching for an offending line of code.

For example, you've opened [COLOR=Green]/var/log/mail.warn, mail.error and mail.log[/COLOR] One of the error logs shows that Postfix could not start because there is an error at line 84 of the config file. You would then open the offending file and directly look at line 84.

If you work a lot with config files, like XF86Config-4, it soons becomes indispensible.

---

### Post by zenwhen on 2005-01-05
The line numbering tip will come in handy. Thanks.

---

### Post by MestreLion on 2010-10-28
2005 topic, but still useful! Thanks!

I wonder why even in 5 years the Recent File List size is still not editable using gEdit Preferences own GUI. At least Line Numbering is.

Mine is set to 15 now. SO much better!

---

### Post by MichiGreat on 2010-11-09
> **MestreLion said:**
> 2005 topic, but still useful! Thanks!

I wonder why even in 5 years the Recent File List size is still not editable using gEdit Preferences own GUI. At least Line Numbering is.

I totally agree! 5 is just a too low number, I guess the demand to change this value is quite high. Who uses only 5 files in a time period of - let's say - a week? Though this preference could be added as easy as inserting a label and a textbox in /usr/share/gedit-2/gedit-preferences-dialog.ui and do some programming to retrieve and change that setting - the rest has already been done. It would be nice to see that setting soonly. :-)

---

### Post by codeninja1 on 2012-06-06
> **MichiGreat said:**
> I totally agree! 5 is just a too low number,... It would be nice to see that setting soonly. :-)

In Ubuntu 11 you can't even change the gnome setting to increase the "recents" list size.

---

### Post by carwe on 2012-07-30
> **codeninja1 said:**
> In Ubuntu 11 you can't even change the gnome setting to increase the "recents" list size.

You can't? Just tried the suggested solution and it didn't work - still only showing 5 in the recent list. Isn't there anything to do about this? This is a BIG annoyance! (Running Ubuntu 12.10.)

---

### Post by akvenugopal on 2012-08-21
2004 topic. but still very usefull. I was searching for line numbering and came to this thread.. Thanks. 
> **wallijonn said:**
> **TIPS & Tweaks:**
---------------------------------------------------------------------------------------------------------
Gedit history / recent file number can be increased by 

[COLOR=Blue]Applications -> System Tools -> Configuratoion Editor ->[/COLOR] 
[COLOR=Red]apps -> gedit-2 -> preferences -> ui -> recents ->[/COLOR] 
click the right pane, either double click under the "name" or click once in the "value" box.

I have set mine to 30 just because it seems to scroll all the way down to the bottom of the screen. set according to your preference. 

This should decrease your time searching for a file. Once you open Gedit, just hit "File" on the menu bar and scroll down to open.  

---------------------------------------------------------------------------------------------------------

Another great option is to enable line numbering. 
[COLOR=Red]apps -> gedit-2 -> preferences -> editor -> line_numbers ->[/COLOR]
Check (on) the right panel box.

This will ease the chore of counting lines when searching for an offending line of code.

For example, you've opened [COLOR=Green]/var/log/mail.warn, mail.error and mail.log[/COLOR] One of the error logs shows that Postfix could not start because there is an error at line 84 of the config file. You would then open the offending file and directly look at line 84.

If you work a lot with config files, like XF86Config-4, it soons becomes indispensible.

---

