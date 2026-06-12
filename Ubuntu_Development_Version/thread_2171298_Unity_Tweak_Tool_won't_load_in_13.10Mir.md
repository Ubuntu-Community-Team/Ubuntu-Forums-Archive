---
title: "Unity Tweak Tool won't load in 13.10/Mir"
date: 2013-08-30
forum: Ubuntu Development Version
---

### Post by perosredo on 2013-08-30
I've only noticed it since I upgraded to Mir a few hours ago but it's possible that one of the last week's dist-upgrades broke it.

It just pretends to load but nothing really happens - last activity in log is from 5 days ago.

---

### Post by speartip on 2013-10-05
I installed 13.10 yesterday, updated & am having the same problem with unity-tweak-tool.
Just pretends to load but never does.
When I run it in a terminal, I get the following:
```
(unity-tweak-tool:14909): GLib-GIO-ERROR **: Settings schema 'org.compiz.unityshell' does not contain a key named 'alt-tab-right'
Trace/breakpoint trap (core dumped)

```
Any help would be appreciated.

---

### Post by Mateusz Stachowski on 2013-10-05
That setting has been moved out of Compiz with recent Unity upgrade and Unity Tweak Tool seems to expect it in that schema and when it desn't find it just crashes. You need to report it to the developers of the tweak tool.


> unity (7.1.1+13.10.20131004-0ubuntu1) saucy; urgency=low

  [ Brandon Schaefer ]
  * Break the bump detection by moving to the first icon, then down 5
    pixels. Since bump detection needs to move in 3 different
    directions.
  * Move the switcher Alt+<ArrowKey> shortcut handling into nux, from
    compiz. Now nux handles these events instead of compiz. This way its
    makes much more sense code wise and we no longer ungrab the arrow
    gets from X... so Alt+LeftArrow will no longer open the hud. (LP:
    #969039)


...

[ Ubuntu daily release ]
  * Automatic snapshot from revision 3554


 -- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Fri, 04 Oct 2013 05:23:43 +0000



---

### Post by grahammechanical on 2013-10-05
These two experiences illustrate what I think is an important point for anyone installing Ubuntu before release date - expect breakage, especially with community developed tools. A couple of weeks ago, Ctrl+Alt+left or right arrow would switch workplaces but Ctrl+Alt+up or down arrow would not switch workplaces. And that is with an official Unity function. That has now been fixed. The point is things break when we use the development version. And often there is no work around but to wait until it is fixed.

Imagine the situation if we were using a rolling development version. We should expect tools that work in stable, released versions to break when installed on a rolling development version.

Regards.

---

### Post by mc4man on 2013-10-05
> **grahammechanical said:**
>  A couple of weeks ago, Ctrl+Alt+left or right arrow would switch workplaces but Ctrl+Alt+up or down arrow would not switch workplaces. And that is with an official Unity function. That has now been fixed. T

You've said that a number of times, it is **not fixed**. However,  in light of the incredible inconsistency & subtle mess that 13.10  is,  some may not see the issue in a fresh current install with the orig. user, add. user(s) & or guest account.

---

### Post by Mateusz Stachowski on 2013-10-05
I've upgraded my 13.04 a couple days ago using the Live image of Final Beta and those shortcuts work. 

Although there is other shortcut that doesn't work as it supposed to work. That is Ctrl+Alt+Del it still summons the logout screen for me but the commands plugin in Compiz is set to Gnome System Monitor processes tab.

Besides that anyone got to work the zoom shortcuts. Those are totally borked for me even when I set them in enchanced zoom plugin of Compiz.

---

### Post by mc4man on 2013-10-05
> **Mateusz Stachowski said:**
> I've upgraded my 13.04 a couple days ago using the Live image of Final Beta and those shortcuts work. 

Although there is other shortcut that doesn't work as it supposed to work. That is Ctrl+Alt+Del it still summons the logout screen for me but the commands plugin in Compiz is set to Gnome System Monitor processes tab.

Besides that anyone got to work the zoom shortcuts. Those are totally borked for me even when I set them in enchanced zoom plugin of Compiz.

As an upgrade I wouldn't expect the binding to change from the correct one (same as 13.04
Try creating a new user or two,  I'd say 50-50 it/they get the correct bindings
(or boot to the current image & try in live session

The sys monitor deal, even though I prefer log out window does seem to be a current bug - 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1235782](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1235782) 
(to'fix', if desired, unset in dconf-editor, then reset to default

---

### Post by Mateusz Stachowski on 2013-10-06
There is a new release of Unity Tweak Tool which resolved the [bug]("https://bugs.launchpad.net/unity-tweak-tool/+bug/1235543") with missing configurations for Alt+Tab actions.

> 
[LIST]
[*]unity-tweak-tool (0.0.6) saucy; urgency=high

  [ Barneedhar Vigneshwar]
  * New upstream bug-fix only release (LP: [#1235752]("https://launchpad.net/bugs/1235752"))
    - Trigger new build of pot files
  * UnityTweakTool/section/spaghetti/unity.py
    - unity-tweak-tool crashed with signal 5 in g_settings_get_value() (LP: [#1235432]("https://launchpad.net/bugs/1235432"))

  [ J Phani Mahesh]
  * UnityTweakTool/__init__.py
    - Fix NameError: name '_formatter' is not defined (LP: [#1232515]("https://launchpad.net/bugs/1232515"))
 -- Barneedhar Vigneshwar <[barneedhar@ubuntu.com]("https://launchpad.net/~barneedhar")>   Sat, 05 Oct 2013 22:45:24 +0530
[/LIST]


---

### Post by cariboo on 2013-10-06
I just got the update to Unity-Tweak, it works as it should for me.

---

### Post by NikTh on 2013-10-06
> **cariboo907 said:**
> I just got the update to [COLOR=#ff0000]Unity-Tweak, it works as it should for me[/COLOR].

And here the same. :)

---

### Post by speartip on 2013-10-06
Same here, problem seems to be solved.

---

### Post by Mateusz Stachowski on 2013-10-09
> **mc4man said:**
> As an upgrade I wouldn't expect the binding to change from the correct one (same as 13.04
Try creating a new user or two,  I'd say 50-50 it/they get the correct bindings
(or boot to the current image & try in live session


The workspace switching with Ctrl+Alt+ Up or Down arrows is now fixed. I tested it in today's daily current image. The fix has been made in ubuntu-settings package and the [bug]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1201405") has fix released status.

> [COLOR=#333333][FONT=Ubuntu Mono]ubuntu-settings (13.10.8) saucy; urgency=low[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono] 
 
* Set the keybindings for workspace up & down switching to only be
    <Ctrl><Alt>Up/Down instead of <Super>Page_Up/Page_Down since
    Compiz sometimes binds the wrong combination. (lp: [#1201405]("https://bugs.launchpad.net/bugs/1201405"))
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono] -- Chris Townsend <christopher.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]townsend@[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]canonical.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]com> Mon, 07 Oct 2013 09:35:58 -0400[/FONT][/COLOR]

---

### Post by Mateusz Stachowski on 2013-10-09
They also [disabled]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1205893") the zoom controls from universal access in Unity because it didn't work. That's a Gnome Shell thing and apparently it needs it's [backend]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/945813") (gnome-mag) to actually zoom in and out. 

The good news is that the Enchanced Zoom plugin in Compiz finally works for me as it should after this change. Before it seemed like it's clashing with the option from gnome-control-center.

---

