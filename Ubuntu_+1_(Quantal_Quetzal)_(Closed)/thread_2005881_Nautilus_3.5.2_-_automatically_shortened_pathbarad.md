---
title: "Nautilus 3.5.2 - automatically shortened pathbar/addressbar's item name"
date: 2012-06-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-06-18
[http://iloveubuntu.net/nautilus-352-landed-ubuntu-1210-new-features-and-removals](http://iloveubuntu.net/nautilus-352-landed-ubuntu-1210-new-features-and-removals)

One particular bit "pathbar/addressbar's item names are automatically shortened by inserting dots in their name".

I raised a bug on this please confirm if you agree.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1014645](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1014645)

Thank goodness for ctrl l.

---

### Post by mc4man on 2012-06-18
It's been sent upstream & hopefully be adjusted (I tend to use location here since adding back the up (parent) button

If it languishes, for self builders this was the commit that caused
[http://git.gnome.org/browse/nautilus/commit/?id=79157f5617886401379a724f8c526c430c4876a6](http://git.gnome.org/browse/nautilus/commit/?id=79157f5617886401379a724f8c526c430c4876a6)

---

### Post by hakermania on 2012-06-18
I can't believe this -_-

---

### Post by mc4man on 2012-06-18
Also gone??  are - 
statusbar & twin panes (F3

Can't quite understand removing non default options

(Atm all thumbnails are just generic but that is a bug

---

### Post by ronacc on 2012-06-18
if I'm going  have to rebuild half the system from source being careful what patches I include and hacking things as necessary to get a useable system I might as well just do "linux from scratch" .

---

### Post by mc4man on 2012-06-18
Maybe Quantal is really is a form of b (our way or no way (highway 

Physics
a. Of or relating to a quantum or a quantized system.
b. Existing in only one of two possible states.
2. Biology Of or designating an all-or-none response or effect:


Edit: doesn't seem to be an context menu option to create a new document either

---

### Post by ronacc on 2012-06-18
the two states I've seen so far are broken and uninstallable .

---

### Post by mc4man on 2012-06-18
The deal with creating an Untitled Document from the  context menu > create a new document is you now need to 'activate  Templates' by putting something in the/a Templates folder

Though can't figure how to add a 'text' template that doesn't create 2 options to create the same document
(& can actually create 2 empty document files with the same name in the same location

else wise I just created an empty odt file which then activated the option for Empty Document

(like i know WtF a template is anyway...

Ex. 
> ~/Desktop$ ls |grep Untitled
Untitled Document
Untitled Document 
Untitled Document 2
Untitled Document  2
Untitled Document 3
Untitled Document  3
Untitled Document 4


---

### Post by VinDSL on 2012-06-18
> **philinux said:**
> One particular bit "pathbar/addressbar's item names are automatically shortened by inserting dots in their name".
I never could stand the pathbar/addressbar, e.g. the buttons.  I always use the locationbar.

Anyway, I went to dconf and turned the buttons on.  OMG!!  :shock:

What were they thinking?!?!?!?

Immediately switched back to the locationbar.  Hope they don't get rid of that option!

---

### Post by VinDSL on 2012-06-18
> **mc4man said:**
> Also gone??  twin panes
Now THAT truly stinks!!!

Guess they're trying to copy PacFm (which has tabbed windows now).  LoL!  :D

---

### Post by ronacc on 2012-06-18
how did the buttons get activated in the first place ? I certainly have never chosen them . Is that another "improvement " ?

---

### Post by mc4man on 2012-06-18
For info sake here are 3 of the option removal commits with short explains

New docu - [http://git.gnome.org/browse/nautilus/commit/?id=9538d1a640fda650e4866d2cdcc69b9e1cfa3a35](http://git.gnome.org/browse/nautilus/commit/?id=9538d1a640fda650e4866d2cdcc69b9e1cfa3a35)

panes- [http://git.gnome.org/browse/nautilus/commit/?id=b8d5b4a7bcf47ed34a6343c95bcc3b079255c0a0](http://git.gnome.org/browse/nautilus/commit/?id=b8d5b4a7bcf47ed34a6343c95bcc3b079255c0a0)

status bar - [http://git.gnome.org/browse/nautilus/commit/?id=676b96d2b7d91cc579bbac6e44d9aafc100e67a2](http://git.gnome.org/browse/nautilus/commit/?id=676b96d2b7d91cc579bbac6e44d9aafc100e67a2)

(on a positive the missing thumbnails was fixed quickly (couple of hr's after filing

---

### Post by VinDSL on 2012-06-18
> **ronacc said:**
> how did the buttons get activated in the first place ? I certainly have never chosen them . Is that another "improvement " ?
Heh!  To turn them off...
```
vindsl@Zuul:~$ dconf-editor
```
 org &#10140; gnome &#10140; nautilus &#10140; preferences &#10140; always-use-location-entry

---

### Post by VinDSL on 2012-06-18
~Cool.  Thanks for the links.  ;)

> **mc4man said:**
> panes- [http://git.gnome.org/browse/nautilus/commit/?id=b8d5b4a7bcf47ed34a6343c95bcc3b079255c0a0](http://git.gnome.org/browse/nautilus/commit/?id=b8d5b4a7bcf47ed34a6343c95bcc3b079255c0a0)

**[COLOR="Navy"]Twin-panes didn't play well with touchscreens.  Gotta use cut/copy/paste between windows now.  LoL![/COLOR]**

status bar - [http://git.gnome.org/browse/nautilus/commit/?id=676b96d2b7d91cc579bbac6e44d9aafc100e67a2](http://git.gnome.org/browse/nautilus/commit/?id=676b96d2b7d91cc579bbac6e44d9aafc100e67a2)

**[COLOR="Navy"]Using a floating bar now. I just tested it.  Not bad... it works.[/COLOR]**


---

### Post by philinux on 2012-06-19
> **mc4man said:**
> For info sake here are 3 of the option removal commits with short explains

New docu - [http://git.gnome.org/browse/nautilus/commit/?id=9538d1a640fda650e4866d2cdcc69b9e1cfa3a35](http://git.gnome.org/browse/nautilus/commit/?id=9538d1a640fda650e4866d2cdcc69b9e1cfa3a35)

panes- [http://git.gnome.org/browse/nautilus/commit/?id=b8d5b4a7bcf47ed34a6343c95bcc3b079255c0a0](http://git.gnome.org/browse/nautilus/commit/?id=b8d5b4a7bcf47ed34a6343c95bcc3b079255c0a0)

status bar - [http://git.gnome.org/browse/nautilus/commit/?id=676b96d2b7d91cc579bbac6e44d9aafc100e67a2](http://git.gnome.org/browse/nautilus/commit/?id=676b96d2b7d91cc579bbac6e44d9aafc100e67a2)

(on a positive the missing thumbnails was fixed quickly (couple of hr's after filing

> If you don't use templates we don't want to clutter up the menu.

CLUTTERED wow what a pathetic reason.

Fix is easy. Use gedit and create an empty text file in Templates. Old cluttered menu comes back.

---

### Post by mc4man on 2012-06-19
> **philinux said:**
> CLUTTERED wow what a pathetic reason.

Fix is easy. Use gedit and create an empty text file in Templates. Old cluttered menu comes back.

What I find wierd about that is then I get 2 options to create an empty (untitled) document

Also each option can create the same file in the same place as shown in post 8

What are you naming the template?

anyway have report on for better or worse
[https://bugs.launchpad.net/bugs/1014876](https://bugs.launchpad.net/bugs/1014876)

---

### Post by pressureman on 2012-06-19
As far as I'm concerned, the removal of the status bar is a regression. I know some other OSes no longer have a status bar in file manager windows (even if they provide an option to turn it on).

Where am I supposed to see available space now? Right-clicking on a directory and selecting Properties is not a user-friendly solution. I want to be able to see the available disk space in a window *before* I drag something into that window.

Why is GNOME consistently removing useful features?

---

### Post by philinux on 2012-06-19
> **mc4man said:**
> What I find wierd about that is then I get 2 options to create an empty (untitled) document

Also each option can create the same file in the same place as shown in post 8

What are you naming the template?

anyway have report on for better or worse
[https://bugs.launchpad.net/bugs/1014876](https://bugs.launchpad.net/bugs/1014876)

It got called Untitled Document 1 and yes I get another option to create an empty document.

---

### Post by ronacc on 2012-06-19
> **pressureman said:**
> 
Why is GNOME consistently removing useful features?

I don't dare say dumbing down , they'll slap my fingers for that . * puts on chain mail gloves *:p

---

### Post by cariboo on 2012-06-19
> **ronacc said:**
> I don't dare say dumbing down , they'll slap my fingers for that . * puts on chain mail gloves *:p

Then I'll say it. :) This is getting ridiculous, the first three things I do when first starting nautilus on a new install is enable delete, disable delete notification and turn on the status bar. The first two I can do with dconf-editor, but even setting the status bar to **start-with-status-bar** no longer works.

I have to wonder if these ideas are actually coming from the Gnome devs, or from their employer.

---

### Post by philinux on 2012-06-19
One thing got fixed. [http://iloveubuntu.net/nautilus-removed-addressbars-short-name-dots-ubuntu-1210](http://iloveubuntu.net/nautilus-removed-addressbars-short-name-dots-ubuntu-1210)

---

### Post by EgoGratis on 2012-06-19
> Remove extra panes

Extra Pane mode was somewhat useful before GNOME 3 had side by side window mode. The combination of panes and tabs is just too much. It is inconsistent with the file chooser and doesn't work well with touch.  We would like to add a more explicit copy/move feature shortly.

This one is in the same league removing Dodge Windows was. Pure abuse of users!

---

### Post by mc4man on 2012-06-19
> **philinux said:**
> One thing got fixed. [http://iloveubuntu.net/nautilus-removed-addressbars-short-name-dots-ubuntu-1210](http://iloveubuntu.net/nautilus-removed-addressbars-short-name-dots-ubuntu-1210)

Was a decent update - fixed 3 things,
The recent .. issue
missing thumbnails
And a longstanding issue where nautilus could open on top without focus in certain scenarios (most common was on an empty WS open gnome-terminal, then open nautilus

> nautilus (1:3.5.2-0ubuntu3) quantal; urgency=low

  * debian/nautilus.gsettings-override:
    - dropped deprecated computer-icon-visible key
  * debian/patches/git_icon_no_thumbnail_fix.patch:
    - "icon-view: fix thumbnails not showing regression" (lp: #1014755)
  * debian/patches/05_desktop_menu_export.patch:
    - synced on the new upstream version, those options got dropped:
      hide toolbar, statusbar, extra panes, tree panel, computer location.
  * debian/patches/03_translations_list_update.patch,
    debian/patches/13_translate_unity_launcher.patch:
    - merged, one patch to updates the potfiles is enough
  * debian/patches/21_correct_timestamp_use_fix_focus_issue.patch:
    - "Use the correct timestamp when creating a new nautilus window.",
       that should fix nautilus dialog opening unfocussed,
       thanks Andrea Azzarone (lp: #781931)
  * debian/patches/workaround_ellipsizing_bug.patch:
    - workaround ellipsizing issues in the pathbars (lp: #1014645)
 -- Sebastien Bacher <seb128@ubuntu.com>   Tue, 19 Jun 2012 18:57:52 +0200

Would be nice if they could fix the server deal so these changelogs would be readily available...

---

### Post by EgoGratis on 2012-06-19
> Was a decent update - fixed 3 things,
The recent .. issue
missing thumbnails
And a longstanding issue where nautilus could open on top without focus  in certain scenarios (most common was on an empty WS open  gnome-terminal, then open nautilus

Removing extra pane mode (shortcut F3) fixed this 3 things? I don't see connection?

---

### Post by mc4man on 2012-06-19
> **EgoGratis said:**
> Removing extra pane mode (shortcut F3) fixed this 3 things? I don't see connection?
Oops - I quoted the wrong reply, will fix.

---

### Post by EgoGratis on 2012-06-19
> Oops - I quoted the wrong reply, will fix.

I see no problem.

---

### Post by kevpan815 on 2012-06-20
The one thing that I discovered is the four commands move to home, move to desktop, copy to home, and copy to desktop (when you right click on a file) are gone in 12.10! Just FYI.

---

### Post by EgoGratis on 2012-06-20
> **kevpan815 said:**
> The one thing that I discovered is the four commands move to home, move to desktop, copy to home, and copy to desktop (when you right click on a file) are gone in 12.10! Just FYI.

Obviously if there is remote possibility i use the feature it will be removed. I am just waiting the day Nautilus desktop support is removed. GUI options that have anything to do with the desktop are removed one by one after GNOME 3 was made and the result is not something better but DE that lacks in many areas and I am starting to feel GNOME 3 should have never happened and i am starting to wonder how to fix this mess?

---

### Post by EgoGratis on 2012-06-20
I must say in GNOME 2 time i could never imagine saying this but now i would probably be happy if Ubuntu was based on other DE or if the project would be strong enough to create it's own user centric and powerful/stable DE that would not change every month and would not remove features users use all the time and leave users empty handed.

The "problem" is GNOME is stable and has all this cool technology in back end but front end from user perspective got broken bad and i don't see easy fix for this and don't believe this trend will change anytime soon.

And creating own DE would probably end up the same in distant future (look at Windows OS) but now it's hard to be GNOME user, there is no real vision and delta between Unity and Shell will probably grow and make time harder for both parties and especially users too.

In the end i think the best thing would be if all involved parties would sit down and talk about it where they failed big and how to make it better because it not good right now its bad and i don't know how developers look at the situation or think about it and probably developers think they have something great going on right now but it's just not working from user perspective and i will say it again it's just not working. You just can't decide removing all the stuff users actually use is a great thing and in return give them something back that they don't want to use will make it better.

---

### Post by VinDSL on 2012-06-20
> **EgoGratis said:**
> I am starting to feel GNOME 3 should have never happened and i am starting to wonder how to fix this mess?
Heh!  At this moment in time, for utilitarian purposes, I'm quite happy with this combo:

[LIST]
[*]OS: Ubuntu 12.10
[*]DE: LXDE 
[*]WM: Openbox
[/LIST]

It's the best of all possible worlds!

At boot, LightDM gives me many choices:

Classic
Classic "Lite"
Gnome Shell aka Gnome 3
LXDE/Openbox
Unity 2D
Unity 3D

I could easily add more DEs & WMs to UbuQQ, but that pretty much rounds out the package for me.

Unity is just my sexy mistress. :D

---

