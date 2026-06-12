---
title: "HOWTO: Make a launcher restore an open window (dock-like)"
date: 2007-03-03
forum: Tutorials
---

### Post by tweedledee on 2007-03-03
This outlines an easy method to modify the behavior of select launchers so that when clicked, they open the program if no instance of the program is already running, but restore focus to the program if an instance is already running.  It also allows for the ability to hide the window from the taskbar, so that some launchers become their own icons.  In other words, you can create a custom "icon box" for some programs (which double as launchers), while other programs use the task list.

Current version: 0.52

UPDATE (25 Dec 2007): Posted version 0.52, which should resolve problems with certain programs not responding correctly to arguments.

The current version, allows for minimizing windows, multiple windows, and a few other goodies.  This is still somewhat beta, but should be stable.  Moreover, I hope to much more tightly integrate this into the gnome interface at some point, which would make it much easier to use.
Limitations compared to full-blown dock programs:
1) You must manually apply to all launchers.
2) It does not trap instances launched via some other means (e.g., unmodified launcher, browser link in another program, etc.); however, you can still trigger them to hide by clicking on the launcher if it has the -h option (it will now hide all matching windows, not just those launched from the panel initially).
3) Minimization is dependent on a keyboard shortcut (due to a wmctrl bug), so must be set using the -k option if it is not Alt+F9 (the default for Metacity).

On the other hand, launch-restore integrates into your existing panel (of any type), so does not require a commitment to a full-blown dock.

Installation is simple: just install the attached .deb file, which just installs launch-restore into /usr/local/bin, and downloads wmctrl & xautomation if they are not on your system (needed for window handling).  If you later want to remove the script, just use synpatic or apt-get to remove "launch-restore" and it will undo everything.

In the simplest case, all you need to do is modify the launcher (I only do this to the icons I put on my panel, but you could also modify the menu entries) by inserting```
launch-restore MATCH
``` in front of the program name (and any parameters) already in the launcher.  MATCH is a string specific to each program that wmctrl will use to determine if the program is already running.  MATCH is tested against either the "name" of a window (i.e., the title you see in the title bar) or the "class" (usually something related to the name of the actual executable).  By default, "class" is used, as that is more reliable, but for some programs that won't work.  Note that all matching is case-sensitive.

If you wish to just match against the name, you use the "-n" option.  For example, to match Firefox, your launcher should look like:```
7.04 and earlier: launch-restore -n Firefox firefox %u
7.10: launch-restore -n Firefox-bin firefox %u
```
(The %u is there so you can drag & drop a file onto the Firefox icon and have it open in Firefox.)

To determine the class of a program, run this in a terminal with the application(s) running:
```
wmctrl -lx
```
Which will produce an output something like this (from my system at the moment, running 7.04):
```
0x01800003 -1 panel.fbpanel         desktop panel
0x00c00003 -1 gnome-panel.Gnome-panel  desktop Left Expanded Edge Panel
0x00c00031 -1 gnome-panel.Gnome-panel  desktop Bottom Expanded Edge Panel
0x01000021 -1 desktop_window.Nautilus  desktop Desktop
0x0260007c  0 Gecko.Firefox-bin     desktop Ubuntu Forums - Post New Thread - Firefox
0x02800003  0 mousepad.Mousepad     desktop launch-restore
0x02a00003  1 mousepad.Mousepad     desktop to do.txt
0x03000073  1 Gecko.Mozilla-thunderbird-bin  desktop Inbox for user@domain.com - Thunderbird
0x03400062  0 VCLSalFrame.DocumentWindow.OpenOffice.org 2.0  desktop file.ods - OpenOffice.org Calc
0x02c0001f  0 gnome-terminal.Gnome-terminal  desktop user@desktop: ~
user@desktop:~$ 
```
The first 2 columns are the window ID and desktop, and can be ignored.  The 3rd column is the "class" - you can choose any fragment of it to match against (e.g., "Firefox" for firefox, "thunderbird" for Thunderbird, "OpenOffice" for OpenOffice).  4th column is computer, and can be ignored.  Final column is the "name" (i.e., the title on the titlebar) for each window.  The "class" will be constant for every instance of a particular program, while the "name" frequently changes for most programs, and so "class" is the easier target.  Also, if you happen to be browsing a website with "Thunderbird" in the title, you may end up restoring focus to Firefox instead of Thunderbird if you match on Thunderbird by name instead of class (and for many other cases).

You can pass additional parameters to launch-restore, here are the most interesting (run it in a terminal to see all parameters):
-x : prevents passing of program arguments to program if an instance of program is already running (I use this for shortcuts to files on my panel, as otherwise the running version receive focus, but then a second copy starts anyway).
-h : hides the program from the taskbar (and alt+tab switching - at least in Gnome).  Note that it may very briefly appear before vanishing.
-m: prevents minimization by clicking on the launcher again.
-a & -d: affects how the program deals with multiple windows.
-k to change the minimize key shortcut.
-f to restore focus even when passing arguments (e.g., when dropping a link onto the Firefox launcher).
Use "launch-restore --help" in a terminal for full details of all options.

Examples:
```
launch-restore -h thunderbird-bin mozilla-thunderbird [in 7.04 and ealier]
launch-restore -h Thunderbird-bin thunderbird [in 7.10]
launch-restore Firefox firefox %u [in 7.04 and earlier]
launch-restore Firefox-bin firefox %u [in 7.10]
launch-restore Toplevel /usr/bin/idle
launch-restore -n -k R_Alt,F5 Audacious audacious
launch-restore --a -m -x nautilus.Nautilus /home/user/
```
1 & 2) launches Thunderbird and hides it from the taskbar.
3 & 4) launches Firefox, matching on class (although using "-n" and matching on name would also work with no further changes).
5) launches the python IDLE IDE, and is an example of a program that is difficult to match (the title contains no fixed information at all, and the class is bizarre, but at least "Toplevel" appears to be unqiue on my system).
6) launches audacious, and like Firefox works exactly the same with or without "-n".  The -k option resets the "minimize" keyboard shortcut to the Right Alt + F5; this is just an example, it should match the shortcut for your window manager (Metacity's default shortcut is automatic).
7) launches/restores a Nautilus window to your home folder (only starting 1 instance), prevents it from being minimized when the launcher is clicked again, and will match all windows on the current desktop if multiple windows exist.

Additionally, you could combine this with the "easy" gnome dock approach to enhance the dock behavior for some launchers: [http://www.ubuntuforums.org/showthread.php?t=333322](http://www.ubuntuforums.org/showthread.php?t=333322).

Note that if used with firefox when a window list is still on your panel, you will get a "starting firefox" message in your panel each time you click the launcher; this is due to a bug ("feature") in Gnome, and I cannot make it go away.  In 7.10, this bug also affects Thunderbird.

I'd hoped to integrate this into X better, including replacing the need for wmctrl and xautomation (to execute the keyboard shortcut to minimize windows), and creating a background daemon that would simplify application.  However, upon examining the available tools to do this tasks, I've concluded that it would be a tremendous amount of effort (weeks of full-time effort) for very little gain, as X simply does not allow for some of what I'd like to accomplish, and I'd spend most of my effort on very low-level code to ensure things don't get too slow.  While I may revisit this program over time, and will still make an effort to fix bugs that anyone finds in the current version, I don't anticipate any major updates, as I simply do not have the time required.  The script is released under the GPL, so anyone who wants to spend the time is free to do so.

Please post if you encounter any problems and I will modify the script accordingly.

---

### Post by Mblackwell on 2007-03-25
I've recently been configuring my machine more and more OSX-like (after realizing that the dock was such a genius way to streamline the desktop) and was having a bit of a hassle because I still needed a taskbar SOMEWHERE, but now I can keep the darned thing hidden most of the time thanks to this.

One thing I did notice though is that when you click to restore firefox it seems another window which says "starting firefox" ticks away for a couple seconds (and the "working" mouse icon appears). It disappears, and firefox does focus immediately, but it seems like there should be some way around that. This seems like a good and cheap step to take to make the desktop neater without adding a ton of bells and whistles.

---

### Post by tweedledee on 2007-03-25
> **Mblackwell said:**
> One thing I did notice though is that when you click to restore firefox it seems another window which says "starting firefox" ticks away for a couple seconds (and the "working" mouse icon appears). It disappears, and firefox does focus immediately, but it seems like there should be some way around that. This seems like a good and cheap step to take to make the desktop neater without adding a ton of bells and whistles.

I believe this is related to a bug in the current (Edgy) version of Gnome that has trouble determining when certain programs start (e.g., many "administrative programs" leave that message open long after the window opens).  Of the programs I set up this way, Firefox is the only one that does this, and not always (e.g., clicking on a link in Thunderbird or running "firefox" in a terminal when Firefox is open doesn't trigger that behavior).  I'm hoping it is resolved in Fiesty.  The other problem I have with Firefox is that if you initially open it another way (e.g., via a link in Thunderbird), it doesn't hide properly.  I intend to address that problem when I have some time to sort it out.

---

### Post by Mblackwell on 2007-03-26
It would be great if there was some way to "open all" (show all windows from an app), and also a minimize. I still need the taskbar from time to time, or ALT+TAB. It would be great to get rid of the need entirely. Those two things would pretty much do it I think.

Also I noticed the script has a hard time with file browser things. I tried setting it up so I could open my home folder and it didn't always work (wouldn't always open a new one), and if there was some way to do that and then also view all Nautilus windows (like above) again it would alleviate some trouble.

Maybe there needs to be some extra integration with an applet like "Alltray" ? Then you could even allow new programs to appear on the bar (via the tray).

---

### Post by tweedledee on 2007-03-27
> **Mblackwell said:**
> It would be great if there was some way to "open all" (show all windows from an app), and also a minimize. I still need the taskbar from time to time, or ALT+TAB. It would be great to get rid of the need entirely. Those two things would pretty much do it I think.

Not sure I understand.  For the open all, do you mean something like the Mac's Expose feature?  Or just a way to tell a launcher to instead of showing the first window that matches, show all of them (al the time)?  The first choice is impossible for this level of application; the second might be workable, but gets a little complicated if the windows from the app are on different desktops.  Also, it could cause unpredictable behavior with the focus, as sometimes dialog boxes restrict focus to the rest of the program, but may end up hidden behind the main program window (e.g., the "Save/Open" dialogs).  Some programs would work better than others.

For the minimize, do you basically mean something like Alltray's ability to minimze an app to the system tray?  If so, you'd just need to modify the invocation in the launcher to trigger the Alltray aspect as well (it's been a while since I played with that, I don't remember exactly how it works).

> Also I noticed the script has a hard time with file browser things. I tried setting it up so I could open my home folder and it didn't always work (wouldn't always open a new one), and if there was some way to do that and then also view all Nautilus windows (like above) again it would alleviate some trouble.

Could you post the command you are using, and describe any patterns you've noticed for when it does and doesn't work?

> Maybe there needs to be some extra integration with an applet like "Alltray" ? Then you could even allow new programs to appear on the bar (via the tray).

I see your point, but personally dislike that solution.  I tend to agree with the Gnome developers that the system tray should be reserved for "notification" things, and applications should not hang out there; it really irritates me when programs put themselves there (one of the major reasons I stopped using Opera and dislike KDE).  Of course, I also keep the taskbar because for some programs I find the descriptions to be useful; the others I just hide with the launcher.

---

### Post by Mblackwell on 2007-03-27
I meant just expose all application windows of a specific program.

I tried different things, I tried launchingby checking "File Browser" as a name, and /home/ as the command, also I tried invoking Nautilus and looking for the nautilus.Nautilus class (as well as File Browser).

It seems to be okay if a window already exists, it will restore it. But it doesn't seem to be able to create one as long as "launch-restore" is there.

And no, for minimize I just meant simply that if I click the Firefox button and a Firefox window (or windows) is already open it will minimize it.

---

### Post by tweedledee on 2007-03-29
> **Mblackwell said:**
> I meant just expose all application windows of a specific program.
I think I can implement that - give me a few days.

> I tried different things, I tried launchingby checking "File Browser" as a name, and /home/ as the command, also I tried invoking Nautilus and looking for the nautilus.Nautilus class (as well as File Browser).

It seems to be okay if a window already exists, it will restore it. But it doesn't seem to be able to create one as long as "launch-restore" is there.
```
launch-restore nautilus.Nautilus nautilus
``` works for me.  Just matching "Nautilus" focused the desktop instead (which makes sense, if perhaps being unexpected).

> And no, for minimize I just meant simply that if I click the Firefox button and a Firefox window (or windows) is already open it will minimize it.
Ah.  That is also possible.  I will implement that at the same time as the "all windows."

I see three issues with implementing those features usefully - let me know what you might prefer.

First, should the launcher minimize or restore a window if you are currently focused on another application and click the launcher for the unfocused window (assuming it is not minimized)?

Second, in the event you are using multiple desktops and have windows from the same program spread out (e.g., Firefox), should the launcher only show all of them on the current desktop, or move them all to the current desktop and show them?

Third, when showing all, what visual appearance might work best?  E.g., I could set it to simply bring all the firefox windows to the top of the window stack, giving focus to one, but in the event one or more windows are maximized only a single window will still be visible.  I could make an attempt to tile or otherwise arrange the windows, but that might lead to unpredictable effects, and might get annoying if you have to constantly rearrange windows after showing them.

---

### Post by Mblackwell on 2007-03-30
First off thanks, that piece of code works just dandy.

As far as the issues go:

1) It should probably "restore" the window, since for instance if you have a window (or windows) unfocused but not minimized but buried behind other application windows this would bring the desired application to the front.

2) This is an interesting question. I guess it would depend. If you have an application spread across multiple desktops it should only show the windows on the current desktop, otherwise I would say it if there was a way to switch desktops and restore the application (if it only exists on a single desktop) that would be impressive. Really you should do what's easiest though.

3) I wonder if there's a way to have the "most recent" window brought to the top (or some way of maintaining what the window stack order was). You could also perhaps handle it by saying that if you have minimized windows in an application and click the button those will be "restored"...

Which brings me to an issue you didn't mention, that being that if you click the application button it should check if there's any minimized windows, and restore those.

So I guess it would go something like:

Unfocused Application: Restore All
Focused Application with some minimized windows: Restore All Minimized
Focused Application with nothing minimized: Minimize All

Just by doing that you create an easy workflow because say a window pops open in Firefox but you don't want to use it just then you can minimize it, and when you click the Firefox button it will be brought back to the top.

---

### Post by tweedledee on 2007-04-01
Hm.  I almost have it working, but have run into two snags.  First, it turns out that wmctrl is broken with respect to minimizing windows, and as it hasn't been updated in two years, I'm not optmistic for a fix.  I have a workaround, but it's awkward and needs some tweaking to work exactly right (it currently tends to minimize multiple windows unexpectedly).  As for multiple windows, I've determined it is possible, but awkward and slow with the implementation I have right now.

In short, getting these working is going to take longer than I thought, which means I probably won't finish it for a few weeks due to other pressing matters.  With luck, I should have something working around the end of April.

---

### Post by Mblackwell on 2007-04-03
No hurries. I'd rather have it working correctly than being frustrating :).

---

### Post by Mblackwell on 2007-04-21
Any updates?

---

### Post by tweedledee on 2007-04-21
I had to avoid it for a while to work on other issues (real life!), but I'm back on track.  I've switched to Python, which seems like overkill for this project but actually appears to be faster and has resolved the issue with being able to minimize a window.  I've not yet finished testing of it nor does it deal with the multiple match issue yet, but neither of those should take real long (for the multiple matching, Python should make it easy).  Unless I encounter something expected in reconstructing the stack order of the windows or the upgrade to Fesity disables my primary computer (currently upgrading the secondary to make sure it seems okay), I expect to have something working in the next 24-48 hours.

---

### Post by flankker on 2007-04-22
> **tweedledee said:**
> I had to avoid it for a while to work on other issues (real life!), but I'm back on track.  I've switched to Python, which seems like overkill for this project but actually appears to be faster and has resolved the issue with being able to minimize a window.  I've not yet finished testing of it nor does it deal with the multiple match issue yet, but neither of those should take real long (for the multiple matching, Python should make it easy).  Unless I encounter something expected in reconstructing the stack order of the windows or the upgrade to Fesity disables my primary computer (currently upgrading the secondary to make sure it seems okay), I expect to have something working in the next 24-48 hours.

thanx very much, if u manage to get the minimizing working, this will let me get rid of my panel completely and let me use just the dock.

great work :)

---

### Post by tweedledee on 2007-04-22
There will be Fesity-related delays; the upgrade killed my network connections (multiple computers, multiple network cards).  Once I get that resolved (quite likely by re-installing Edgy, which will cost me a couple of days to get everything working right again), I will resume work on this.

---

### Post by Mblackwell on 2007-04-22
Yes, upgrading to feisty caused my wireless firmware (which isn't a restricted package) to be lost. Since I did an upgrade I had to boot from an edgy live cd and copy the firmware over.

---

### Post by tweedledee on 2007-04-27
Feisty is great and a pain all at once.  But I finally have a much better version posted.  You can copy the script from the original post and replace your existing one.  Note that you will also need to install "xautomation" for the minimize to work.  More notes:
1) Lots of new options for multiple windows, passing arguments, and minimizing.
2) Exisiting launchers will work, with default behavior for multiple windows and minimizing.
3) I consider this seriously beta.  I've tested it somewhat rigorously, but I expect someone will manage to break it.  Let me know and I'll fix it.
4) If the defaults and/or features aren't quite what you had in mind, I may be able to tweak them without too much trouble.
5) I'm hoping to get a much more sophisticated version still up that would avoid the need to modify individual launchers and integrate much better into gnome, but the documentation for that sort of work is very poor, so it will take me a while (possibly months, depending on my free time).  Also, that approach may not work with all window managers, whereas this should, so I will maintain this approach at the same time.

---

### Post by Mblackwell on 2007-04-28
```

Traceback (most recent call last):
  File "/usr/local/bin/launch-restore", line 252, in <module>
    Counts, IDData, DeskData, MinData, CurDesktop, CurWin, StackOrder = GetWinInfo(Match, MatchClass)
  File "/usr/local/bin/launch-restore", line 122, in GetWinInfo
    Stack = Stack[1].split(',')
IndexError: list index out of range

```

Apps wouldn't launch and I couldn't figure out why and so I tried from a terminal to see the error and that's what I got.

Which means as of right now my computer is slightly unusable (because my desktop interface is based off of a fake dock).

And, when trying to run Gedit:

```

Traceback (most recent call last):
  File "/usr/local/bin/launch-restore", line 252, in <module>
    Counts, IDData, DeskData, MinData, CurDesktop, CurWin, StackOrder = GetWinInfo(Match, MatchClass)
  File "/usr/local/bin/launch-restore", line 105, in GetWinInfo
    Hidden = '_NET_WM_STATE_HIDDEN' in os.popen('xprop -id %s | nawk \'/_NET_WM_STATE/ {print $0; exit;}\'' % Split[0]).readlines()[0]
IndexError: list index out of range

```

---

### Post by tweedledee on 2007-04-28
Please run the following commands in a terminal, and post the output from each:
(for the 2nd command, replace the "%s" with the ID from the last line in the output from wmctrl (0x0....).)
```
wmctrl -lx
xprop -id %s | nawk '/_NET_WM_STATE/ {print $0; exit;}'
xprop -root -len 20 | nawk '/_NET_CURRENT_DESKTOP/ {print $0; exit;}'
xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $0; exit;}'
xprop -root | nawk '/_NET_CLIENT_LIST_STACKING/ {print $0; exit;}'
```

If any of the xprop commands give no output, please also run:
```
xprop -root -len 20
xprop -id %s -len 20
```
(again replacing %s w/ a window ID).

---

### Post by Mblackwell on 2007-04-28
```

$ wmctrl -lx
0x03c0001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit
0x0140001f -1 desktop_window.Nautilus  jon Desktop
0x00e00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel
0x00e0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel
0x00e00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel
0x00c00020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~
0x02200003  0 thunar.Thunar         jon jon - File Manager
0x01030a8d  0 Gecko.Firefox-bin     jon Downloads
0x0100006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Page 2 - Ubuntu Forums - Mozilla Firefox
0x0160cf2e  0 gaim.Gaim             jon II Orblivion II

```

```

$ xprop -id 0x03c0001e | nawk '/_NET_WM_STATE/ {print $0; exit;}'
_NET_WM_STATE(ATOM) = _NET_WM_STATE_HIDDEN

```

```

$ xprop -root -len 20 | nawk '/_NET_CURRENT_DESKTOP/ {print $0; exit;}'
_NET_CURRENT_DESKTOP(CARDINAL) = 0

```

```

$ xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $0; exit;}'
_NET_ACTIVE_WINDOW(WINDOW): window id # 0xc00020

```

```

$ xprop -root | nawk '/_NET_CLIENT_LIST_STACKING/ {print $0; exit;}'
_NET_SUPPORTED(ATOM) = _NET_SUPPORTED, _NET_SUPPORTING_WM_CHECK, UTF8_STRING, _NET_CLIENT_LIST, _NET_CLIENT_LIST_STACKING, _NET_ACTIVE_WINDOW, _NET_DESKTOP_VIEWPORT, _NET_DESKTOP_GEOMETRY, _NET_CURRENT_DESKTOP, _NET_NUMBER_OF_DESKTOPS, _NET_SHOWING_DESKTOP, _NET_WORKAREA, _NET_WM_NAME, _NET_WM_STRUT, _NET_WM_STRUT_PARTIAL, _NET_WM_USER_TIME, _NET_FRAME_EXTENTS, _NET_FRAME_WINDOW, _NET_WM_STATE_MODAL, _NET_WM_STATE_STICKY, _NET_WM_STATE_MAXIMIZED_VERT, _NET_WM_STATE_MAXIMIZED_HORZ, _NET_WM_STATE_SHADED, _NET_WM_STATE_SKIP_TASKBAR, _NET_WM_STATE_SKIP_PAGER, _NET_WM_STATE_HIDDEN, _NET_WM_STATE_FULLSCREEN, _NET_WM_STATE_ABOVE, _NET_WM_STATE_BELOW, _NET_WM_STATE_DEMANDS_ATTENTION, _NET_WM_WINDOW_OPACITY, _NET_WM_WINDOW_BRIGHTNESS, _NET_WM_WINDOW_SATURATION, _NET_WM_STATE_DISPLAY_MODAL, _NET_WM_ALLOWED_ACTIONS, _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_SHADE, _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_WINDOW_TYPE, _NET_WM_WINDOW_TYPE_DESKTOP, _NET_WM_WINDOW_TYPE_DOCK, _NET_WM_WINDOW_TYPE_TOOLBAR, _NET_WM_WINDOW_TYPE_MENU, _NET_WM_WINDOW_TYPE_SPLASH, _NET_WM_WINDOW_TYPE_DIALOG, _NET_WM_WINDOW_TYPE_UTILITY, _NET_WM_WINDOW_TYPE_NORMAL, WM_DELETE_WINDOW, _NET_WM_PING, _NET_WM_MOVERESIZE, _NET_MOVERESIZE_WINDOW, _NET_RESTACK_WINDOW

```

---

### Post by tweedledee on 2007-04-28
Thanks.  Revised version posted.  Short version of problem is that the X properties are less consistent across computers than I thought.  Your global problem (most things not working) should be fixed (as well as a few other unrelated bugs I found).  I'm not sure what's causing your gedit problem, but added some debugging lines in there.  Please run it again in a terminal for gedit and pass on the output.

---

### Post by Mblackwell on 2007-04-28
```

['0x03600025', '0', 'gedit.Gedit', 'jon', 'launch-restore (/usr/local/bin) - gedit\n']
* []
Traceback (most recent call last):
  File "/usr/local/bin/launch-restore", line 257, in <module>
    Counts, IDData, DeskData, MinData, CurDesktop, CurWin, StackOrder = GetWinInfo(Match, MatchClass)
  File "/usr/local/bin/launch-restore", line 110, in GetWinInfo
    Hidden = '_NET_WM_STATE_HIDDEN' in os.popen('xprop -id %s | nawk \'/_NET_WM_STATE/ {print $0; exit;}\'' % Split[0]).readlines()[0]
IndexError: list index out of range

```


Also, Thunar isn't working with launch-restore. Using the script causes it to open a window (and multiple instances thereof). On a hunch I ran wmctrl -lx and I noticed the output for the Thunar window was this:

```

0x03800003  0 <unknown>.<unknown>   jon jon - File Manager

```

Just running Thunar alone (via the terminal) wmctrl reports that window correctly (thunar.Thunar).

Edit: I tried "tricking" it by using -n 'File Manager' and got this debug output:

```

['0x03800003', '0', '<unknown>.<unknown>', 'jon', 'jon - File Manager\n']
* []
Traceback (most recent call last):
  File "/usr/local/bin/launch-restore", line 257, in <module>
    Counts, IDData, DeskData, MinData, CurDesktop, CurWin, StackOrder = GetWinInfo(Match, MatchClass)
  File "/usr/local/bin/launch-restore", line 110, in GetWinInfo
    Hidden = '_NET_WM_STATE_HIDDEN' in os.popen('xprop -id %s | nawk \'/_NET_WM_STATE/ {print $0; exit;}\'' % Split[0]).readlines()[0]
IndexError: list index out of range

```

Edit2: Tried Gaim for the heck of it (partially the reason I wanted to be able to handle multiple windows ;)) and got this output:

```

['0x0180005a', '0', 'gaim.Gaim', 'jon', 'Buddy List\n']
* ['_NET_WM_STATE(ATOM) = \n']
['0x0180ae99', '0', 'gaim.Gaim', 'jon', 'FreeFragSGS\n']
* []
Traceback (most recent call last):
  File "/usr/local/bin/launch-restore", line 257, in <module>
    Counts, IDData, DeskData, MinData, CurDesktop, CurWin, StackOrder = GetWinInfo(Match, MatchClass)
  File "/usr/local/bin/launch-restore", line 110, in GetWinInfo
    Hidden = '_NET_WM_STATE_HIDDEN' in os.popen('xprop -id %s | nawk \'/_NET_WM_STATE/ {print $0; exit;}\'' % Split[0]).readlines()[0]
IndexError: list index out of range

```

---

### Post by tweedledee on 2007-04-29
Your last round of output allows to clearly see why it's crashing for you, but I've no idea what the root cause, and can't reproduce it on my machine.  I've posted another version that allows the test for a minimized window to fail without halting the script (but it does spit out a bit of debugging info).  Hopefully this means that while I continue to sort this out, it will work, except that occasionally it will fail to recognize that a window has been minimized (which would prevent you from using the launcher to minimize alll, but it should still restore evertyhing).  Please all give the new terminal output for the same set of programs (Thunar, Gaim, Gedit).

---

### Post by Mblackwell on 2007-04-29
interestingly Gaim now works fine, but Gnome-Terminal does not. It will work if an instance is already open but won't open a new one. It gives this debug output:

```

0x03600020
['0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel\n', '0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x0140001f -1 desktop_window.Nautilus  jon Desktop\n', '0x019ba5c2  0 gaim.Gaim             jon FreeFragSGS\n', '0x0180005a  0 gaim.Gaim             jon Buddy List\n', '0x00c1d1e9  0 gnome-panel.Gnome-panel  jon Launcher Properties\n', '0x03400003  0 <unknown>.<unknown>   jon jon - File Manager\n', '0x03600020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~\n', '0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit\n', '0x03a0006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Ubuntu Forums - Mozilla Firefox\n']
['0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel\n', '0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x0140001f -1 desktop_window.Nautilus  jon Desktop\n', '0x019ba5c2  0 gaim.Gaim             jon FreeFragSGS\n', '0x0180005a  0 gaim.Gaim             jon Buddy List\n', '0x00c1d1e9  0 gnome-panel.Gnome-panel  jon Launcher Properties\n', '0x03400003  0 <unknown>.<unknown>   jon jon - File Manager\n', '0x03600020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~\n', '0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit\n', '0x03a0006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Ubuntu Forums - Mozilla Firefox\n']
['_NET_ACTIVE_WINDOW(WINDOW): window id # 0x3600020\n']
['_NET_CLIENT_LIST_STACKING(WINDOW): window id # 0x140001f, 0x3400003, 0xc0002b, 0x3a0006f, 0x180005a, 0xc00003, 0xc1d1e9, 0x380001e, 0x19ba5c2, 0x3600020, 0xc00030\n']

```

Somehow Thunar still gets classed as <unknown>.<unknown> when launched with launch-restore. Using the -n method I did before I was able to get this debug output:

```

0x03400003
['0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel\n', '0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x0140001f -1 desktop_window.Nautilus  jon Desktop\n', '0x019ba5c2  0 gaim.Gaim             jon (*)[1] FreeFragSGS\n', '0x0180005a  0 gaim.Gaim             jon Buddy List\n', '0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit\n', '0x03a0006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Page 3 - Ubuntu Forums - Mozilla Firefox\n', '0x03400003  0 <unknown>.<unknown>   jon jon - File Manager\n', '0x03600020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~\n', '0x01400255  0 nautilus.Nautilus     jon Trash - File Browser\n']
['0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel\n', '0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x0140001f -1 desktop_window.Nautilus  jon Desktop\n', '0x019ba5c2  0 gaim.Gaim             jon (*)[1] FreeFragSGS\n', '0x0180005a  0 gaim.Gaim             jon Buddy List\n', '0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit\n', '0x03a0006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Page 3 - Ubuntu Forums - Mozilla Firefox\n', '0x03400003  0 <unknown>.<unknown>   jon jon - File Manager\n', '0x03600020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~\n', '0x01400255  0 nautilus.Nautilus     jon Trash - File Browser\n']
['_NET_ACTIVE_WINDOW(WINDOW): window id # 0x3600020\n']
['_NET_CLIENT_LIST_STACKING(WINDOW): window id # 0x140001f, 0x1400255, 0x180005a, 0x19ba5c2, 0x380001e, 0x3400003, 0x3a0006f, 0x3600020, 0xc0002b, 0xc00003, 0xc00030\n']

```

Gedit gives:

```

0x0380001e
['0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel\n', '0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x0140001f -1 desktop_window.Nautilus  jon Desktop\n', '0x019ba5c2  0 gaim.Gaim             jon (*)[1] II Orblivion II\n', '0x0180005a  0 gaim.Gaim             jon Buddy List\n', '0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit\n', '0x03a0006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Page 3 - Ubuntu Forums - Mozilla Firefox\n', '0x03400003  0 <unknown>.<unknown>   jon jon - File Manager\n', '0x03600020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~\n']
['0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel\n', '0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel\n', '0x0140001f -1 desktop_window.Nautilus  jon Desktop\n', '0x019ba5c2  0 gaim.Gaim             jon (*)[1] II Orblivion II\n', '0x0180005a  0 gaim.Gaim             jon Buddy List\n', '0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit\n', '0x03a0006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Page 3 - Ubuntu Forums - Mozilla Firefox\n', '0x03400003  0 <unknown>.<unknown>   jon jon - File Manager\n', '0x03600020  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~\n']
['_NET_ACTIVE_WINDOW(WINDOW): window id # 0x3600020\n']
['_NET_CLIENT_LIST_STACKING(WINDOW): window id # 0x140001f, 0x180005a, 0x3400003, 0x19ba5c2, 0x3a0006f, 0x380001e, 0x3600020, 0xc0002b, 0xc00003, 0xc00030\n']

```

---

### Post by tweedledee on 2007-04-29
Oddly, I WAS able to reproduce the gnome-terminal issue, but still not the others.  The gnome-terminal problem is fixed and posted above (obviously you should ignore the temporary warning line); possibly the same cure solved some of the other problems.  I now also have it spitting out a lot of information each run, so please pass on the output from anything that still isn't working as you expect.  Hopefully it works, but if not I should be able to isolate the problem, as I've at least narrowed down the problem to a very small set of possibilities.

---

### Post by Mblackwell on 2007-04-29
The only one with an issue still that I noticed  is Gedit, in that it won't minimize. Launching it gives this:

```

$ launch-restore Gedit gedit
/usr/local/bin/launch-restore
Gedit
gedit
0x04600003  0 thunar.Thunar         jon jon - File Manager
0x0360006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Ubuntu Forums - Mozilla Firefox
0x01200f1f -1 N/A                   jon N/A
0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel
0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel
0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel
0x0140001f -1 desktop_window.Nautilus  jon Desktop
0x0180005a  0 gaim.Gaim             jon Buddy List
0x019da032  0 gaim.Gaim             jon ReverendTerminX
0x03c00003  0 totem.Totem           jon 10 Red Oyster Cult.m4a
0x03400021  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~

```

and a second time:

```

$ launch-restore Gedit gedit
0x0380001e
_NET_WINDOW_DECOR(INTEGER) = 20061011, 14739549, 12, 6, 28, 6, 12, 6, 28, 6, 108, 0
_NET_WM_ICON_GEOMETRY(CARDINAL) = 1157, 1177, 176, 23
XKLAVIER_STATE(INTEGER) = 0, 0
WM_STATE(WM_STATE):
window state: Normal
icon window: 0x0
_NET_FRAME_EXTENTS(CARDINAL) = 12, 6, 28, 6
_NET_FRAME_WINDOW(WINDOW): window id # 0x1201221
_NET_WM_DESKTOP(CARDINAL) = 0
WM_HINTS(WM_HINTS):
Client accepts input or input focus: True
Initial state is Normal State.
bitmap id # to use for icon: 0x3800021
bitmap id # of mask for icon: 0x3800028
window id # of group leader: 0x3800001
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x10, 0x0, 0x0, 0x0
_NET_WM_ICON(CARDINAL) = 22, 22, 0, 0, 0, 4291076096, 0, 4291076096, 0, 4291076096, 0, 4291076096
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
WM_WINDOW_ROLE(STRING) = "gedit-window-22694-1000-1-1177889461-0@jon"
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_SHADE, _NET_WM_ACTION_CHANGE_DESKTOP
_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 58720288
WM_CLIENT_LEADER(WINDOW): window id # 0x3800001
_NET_WM_PID(CARDINAL) = 22694
WM_LOCALE_NAME(STRING) = "en_US.UTF-8"
WM_CLIENT_MACHINE(STRING) = "jon"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
program specified minimum size: 352 by 201
window gravity: Forget
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "gedit", "Gedit"
WM_ICON_NAME(STRING) = "Unsaved Document 1 - gedit"
_NET_WM_ICON_NAME(UTF8_STRING) = 0x55, 0x6e, 0x73, 0x61, 0x76, 0x65, 0x64, 0x20, 0x44, 0x6f, 0x63, 0x75, 0x6d, 0x65, 0x6e, 0x74, 0x20, 0x31, 0x20, 0x2d, 0x20, 0x67, 0x65, 0x64, 0x69, 0x74
WM_NAME(STRING) = "Unsaved Document 1 - gedit"
_NET_WM_NAME(UTF8_STRING) = 0x55, 0x6e, 0x73, 0x61, 0x76, 0x65, 0x64, 0x20, 0x44, 0x6f, 0x63, 0x75, 0x6d, 0x65, 0x6e, 0x74, 0x20, 0x31, 0x20, 0x2d, 0x20, 0x67, 0x65, 0x64, 0x69, 0x74
0x04600003  0 thunar.Thunar         jon jon - File Manager
0x01200f1f -1 N/A                   jon N/A
0x00c00003 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel
0x00c0002b -1 gnome-panel.Gnome-panel  jon Top Expanded Edge Panel
0x00c00030 -1 gnome-panel.Gnome-panel  jon Bottom Centered Panel
0x0140001f -1 desktop_window.Nautilus  jon Desktop
0x0180005a  0 gaim.Gaim             jon Buddy List
0x019da032  0 gaim.Gaim             jon II Orblivion II
0x03c00003  0 totem.Totem           jon 10 Red Oyster Cult.m4a
0x03400021  0 gnome-terminal.Gnome-terminal  jon jon@jon: ~
0x0380001e  0 gedit.Gedit           jon Unsaved Document 1 - gedit
0x0360006f  0 Gecko.Firefox-bin     jon HOWTO: Make a launcher restore an open window (dock-like) - Page 3 - Ubuntu Forums - Mozilla Firefox

```

---

### Post by tweedledee on 2007-04-29
I wish I could say I'd fixed that, but I'm entirely unable to make Gedit misbehave in any way.  I've posted yet another version that should just output a single letter.  Please tell me which letter is output (and when it did not act as you expect) for three situations: launching initially, restoring focus, and then "sleep 1; launch-restore Gedit gedit" where you use the 1 second delay to switch from the terminal to the Gedit window (so it should minimize).  Then repeat the second and third with 3 additional scenarios:
1) with -a option
2) when terminal window is on desktop 2 and gedit is on desktop 1
3) 1 & 2 together

---

### Post by Mblackwell on 2007-05-01
Well crap. Chalk it up to user error. At some point during restarts I lost the launch-restore call in my Gedit launcher/shortcut. Everything works as of now.

Sorry to give you so much trouble. But at least there were some other bug fixes in the process ;).

---

### Post by Freedreamer on 2007-05-02
Hi, 
can someone post a screenshot or a video about this script?

i'm curios about that...i would like a dock for metacity.

thanks in advance

---

### Post by tweedledee on 2007-05-02
> **Mblackwell said:**
> Well crap. Chalk it up to user error. At some point during restarts I lost the launch-restore call in my Gedit launcher/shortcut. Everything works as of now.

Sorry to give you so much trouble. But at least there were some other bug fixes in the process ;).

Not a problem - the exercise enabled me to find a couple of other subtle bugs while I was trying to figure out the Gedit issue.  I think it's fairly stable now; the newest version is uploaded as a .deb to make installation easier.

---

### Post by tweedledee on 2007-05-02
> **Freedreamer said:**
> Hi, 
can someone post a screenshot or a video about this script?

i'm curios about that...i would like a dock for metacity.

thanks in advance

There's not really anything to show - the script itself is entirely invisible.  You can arrange the panel/launchers however you want, and as long as the launcher command includes the necessary "launch-restore" bit, the launcher then also serves as a window managing icon.  I personally use a mixture of 3 scenarios: launchers that use launch-restore & hide the program from the taskbar; launchers that use launch-restore but don't hide the window (generally text editors, etc. as I want to see multiple document names in the taskbar), and a few launchers I don't use launch-restore at all.

---

### Post by Mblackwell on 2007-05-02
This script came in real handy earlier when I was using GIMP. One button click brought up all of the program windows. I did have a problem though in that sometimes when GIMP would spawn a window (for instance for the Drop Shadow plugin) it was somewhere behind other windows. Clicking the launcher brought it up of course, although not to the front. I doubt it's your fault. Probably something with focus stealing prevention in Metacity (which is what causes anything opened in Thunar to appear in the background).

The Expose feature in Compiz makes the integration work better. You never really REQUIRE a task list. By the same token it WOULD be nice to have another version of the window list applet that only showed program icons instead of the full program name (and could be grouped as well of course). That combined with this would basically give you the "full" doc experience without having to use any external things like kiba or cairo or avant, and would continue to work even if you switch off your composite manager ;).

On another note I do wish there was a way to bring a specific window from an application to the front though easily. I doubt this is possible without some kind of Gnome/GTK integration.

---

### Post by tweedledee on 2007-05-03
> **Mblackwell said:**
> This script came in real handy earlier when I was using GIMP. One button click brought up all of the program windows. I did have a problem though in that sometimes when GIMP would spawn a window (for instance for the Drop Shadow plugin) it was somewhere behind other windows. Clicking the launcher brought it up of course, although not to the front. I doubt it's your fault. Probably something with focus stealing prevention in Metacity (which is what causes anything opened in Thunar to appear in the background).

I'll think about this.  I could easily implement a window sort based on age rather than the X stack order (which would bring new windows like that to the top), but the question is how to implement the choice usefully.  I could build in another switch so that individual programs behaved one way or the other, but I'm not sure that's the best solution.  This may have to await better integration (at which point I might be able to add a right-click menu or something to enable an immediate choice).

> **Mblackwell said:**
> The Expose feature in Compiz makes the integration work better. You never really REQUIRE a task list. By the same token it WOULD be nice to have another version of the window list applet that only showed program icons instead of the full program name (and could be grouped as well of course). That combined with this would basically give you the "full" doc experience without having to use any external things like kiba or cairo or avant, and would continue to work even if you switch off your composite manager ;).

That is precisely my long-term goal; basically something that used the launcher icon if there was one, but added a "task list" icon as necessary as well.  Something somewhat similar to the icon box in XFCE (but that lacks some flexibile I need).  I suspect it can be done using standard python libraries and a new panel tool, so no need to install other programs - even to the point of not needing wmctrl or xautomation any more.

> **Mblackwell said:**
> On another note I do wish there was a way to bring a specific window from an application to the front though easily. I doubt this is possible without some kind of Gnome/GTK integration.

This would come naturally from the above mentioned changes, but I can't think of a way to implement it short of that.

---

### Post by Mblackwell on 2007-05-08
I've noticed when using Gaim that it doesn't always minimize/restore all windows (yeah I'm using the -a switch).

My exact launcher is: 
```

launch-restore -a Gaim gaim

```

---

### Post by tweedledee on 2007-05-13
> **Mblackwell said:**
> I've noticed when using Gaim that it doesn't always minimize/restore all windows (yeah I'm using the -a switch).

I don't use Gaim, but it seems to work okay in my test runs.  Can you give me any more information about when it doesn't work (e.g., is it only when a specific window is open, whenever you have more than 3 windows open, etc.)?  Do most of the windows do it, leaving one, or does it simply fail altogether?  Also, is it only when (un)minimizing, or also when switching to it when another app has focus but minimization isn't an issue?

---

### Post by Mblackwell on 2007-05-16
Only with the Buddy List and tabbed chat window open. What it does is just minimize one or the other (with no certainty as to which). Occasionally it will function correctly. It seems to do the other thing randomly. In fact right before posting this it was doing it but as I'm posting I can't make it perform incorrectly.

---

### Post by tweedledee on 2007-05-20
> **Mblackwell said:**
> Only with the Buddy List and tabbed chat window open. What it does is just minimize one or the other (with no certainty as to which). Occasionally it will function correctly. It seems to do the other thing randomly. In fact right before posting this it was doing it but as I'm posting I can't make it perform incorrectly.

Since I've still not been able to reproduce it, and have been staring at code for > 60 hours already this week so am not likely to have the problem jump out at me, a couple of more questions/requests:
1. If possible, the next time it starts to show this behavior, do a "wmctrl -lx" and compare the Gaim lines to when launch-restore is working properly (just in case it's wmctrl that is the problem).
2. When it is only minimizing one window, what happens the next time you hit the launcher (i.e., does it restore the minimized window, or minimize the other)?  If it is misbehaving, if you manually minimize both windows, does launch-restore bring them both back up?
3. When you say it is "random," does that mean it doesn't correspond to which one has focus at the time?
4. Very long shot - do you have anything set in Gaim that causes it to call attention to itself (e.g., when you receive an IM), and if so does the minimize problem occur during times when Gaim is doing so?

---

### Post by Mblackwell on 2007-05-22
To answer the last two right away:

3. Yes
4. No, not anything beyond the normal window flash/systray icon chainge. Don't think there's any correspondence but I'd have to test it of course.

---

### Post by shame on 2007-06-08
I have been trawling the net trying to find a way to do this (in particular with firefox cos it always launches a new instance/window).

I haven't read through the whole thread yet but I have tried the script.
I'm using it on sidux with kde (I'll be trying it on ubuntu next) and it works exactly as advertised.

Fantastic stuff, thanks. I'll now get on with reading through the whole thread to see all the features.

---

### Post by tweedledee on 2007-06-08
> **shame said:**
> I have been trawling the net trying to find a way to do this (in particular with firefox cos it always launches a new instance/window).

While I'm glad this worked for you, if all you are trying to do is prevent Firefox from spawning endless windows, you can do this instead (or in addition):
1) Set Prferences -> Tabs -> open new windows in tabs
2) point your browser to about:config
3) set "browser.link.open_newwindow" to 3
4) set "browser.link.open_newwindow.restriction" to 0

That combination should eliminate the new window problem, only opening one if you specifically request it.  However, none of the above restores focus to Firefox as launch-restore does.

---

### Post by PurposeOfReason on 2007-09-08
I'm having a bit of trouble with this, I've had it working on my laptop before but I can't get it now. The only difference is this computer is 64bit, but it wasn't an architecture dependent package so that shouldn't matter. I'm trying to get it so when I click a launcher, if it's open, in minimizes. I've done it before but now when I do, for example
```
launch-restore -a amarokapp.Amarokapp amarok %U
```
it brings Amarok to the front, but if I click it again, nothing.

---

### Post by tweedledee on 2007-09-09
> **PurposeOfReason said:**
> I'm having a bit of trouble with this, I've had it working on my laptop before but I can't get it now.

I'm not sure why either 64-bit or Amarok in particular would be an issue, but unfortunately I don't have the time now to troubleshoot (especially as I don't use either by default).  I'm in the middle of writing/defending my dissertation and will be moving and starting a new job immediately after, so it will probably be close the new year before I revisit this and start to address the remaining issues.  All I can immediately suggest is that if it opens but doesn't bring it to the front OR minimize, it's probably a name/class issue; if it does bring it to the front but doesn't minimize, it's probably an issue with interfacing with the window manager, which is a more complicated fix (as it turns out that essentially none of the window managers are truly following all the specifications they are supposed to, and Metacity in particular has several subtle bugs related to window identification).

---

### Post by shame on 2007-11-17
I've been using this method for quite a while and it generally works very well but I'm having trouble getting it to work with VirtualBox when using startup parameters to launch with a particular virtual machine.

I can get it working when starting Vbox with the "VirtualBox" command, but I generally use this command to launch windows xp automatically:  ```
VBoxSDL -vm WinXP
```

wmctrl -lx gives me this: ```
VBoxSDL.VBoxSDL         N/A innotek VirtualBox - WinXP (HWVirtEx)
```

I've tried various combinations with no luck so far.

---

### Post by tweedledee on 2007-11-18
> **shame said:**
> I've been using this method for quite a while and it generally works very well but I'm having trouble getting it to work with VirtualBox when using startup parameters to launch with a particular virtual machine.

I'm assuming from this that you can get it to work without the startup parameters?  If so, please post a couple of the complete commands you've tried with the parameters and I'll see if there's something I can figure out.  If not, it will unfortunately have to wait at least a few more weeks (until I switch from VMware to Virtualbox) or a bit longer (until I have time to really revise the code).

---

### Post by tweedledee on 2007-12-17
An update for those who have posted problems in the last few months.

1. If you have a %u on the end of your launch-restore command line, and do not actually need it (nearly all cases, I'm actually not sure why so many programs have it), removing it may help with inconsistent behavior.  I've noticed, especially in Gutsy, that passing the empty parameter sometimes modifies the program's response to being called.

2. Virtualbox is a problem.  I haven't figured it out yet, but the various VBox utilities do something very odd with the parameters they are invoked with, such that they don't parse correctly when passed by launch-restore.  As I've switched to VBox and like to directly invoke my virtual machine using VBoxManage or other tools, I will be working on this, but can't promise a solution.

Also, as this post should indicate, I am starting to resume active development on this project, and while I hope to have a significantly improved version relatively soon, I can't commit to a deadline.  Some of the improvements will require my learning a new set of programming tools, so that will slow me down a bit.  Please do continue to identify problems and I'll try to resolve those, possibly releasing an intermediate version to deal with them.

---

### Post by atlas95 on 2007-12-17
This seems to be a very good program, but I search how to use for always have only one instance of evolution, could you help me please?

---

### Post by tweedledee on 2007-12-18
> **atlas95 said:**
> This seems to be a very good program, but I search how to use for always have only one instance of evolution, could you help me please?

I don't use Evolution, but my test case of
```
launch-restore evolution evolution
```
worked.  You can add the -h and -a switches to respecitively hide the window list button and have the restore/minize work on all windows.  If it isn't working for you, please post your launch-restore line and the behavior you observe.

---

### Post by tweedledee on 2007-12-25
I've just posted version 0.52, which should resolve the problems with certain programs not responding correctly when passing arguments (e.g., virtualbox).  I'm in the process of rewriting much of it to replace dependency on wmctrl and allow for easier use and configuration, if time allows I will have a radically revised version posted in a few days.

---

### Post by tweedledee on 2007-12-26
Upon further investigation, I've concluded that most of what I want to do is simply not possible without many weeks of dedicated effort, very low-level code (I'm a high-level programmer), and relatively little gain from the user's point of view anyway.  If there is demand, I should be able to implement a fix for the wmctrl bug that requires a keyboard shortcut to minimize, if anyone is having trouble with that aspect, and I'll fix any straightforward bugs that are reported.  Unfortunately, beyond that I simply do not have the time due to the demands required and the incredibly poor documentation available for how to work with X.

---

### Post by shame on 2008-06-15
I've been happily using this for some time but it doesn't seem to want to work with Firefox/Iceweasel 3

It does focus the window but then always opens a new instance as well.

---

### Post by tweedledee on 2008-06-15
> **shame said:**
> I've been happily using this for some time but it doesn't seem to want to work with Firefox/Iceweasel 3

It does focus the window but then always opens a new instance as well.

My limited experience with Firefox 3 suggested it's a more eager than v2 to open new windows in general.  First try modifying the launch-restore command to remove the "%n" (if present) from the launcher command.  You can also try setting the following options in about:config:
```
browser.link.open_newwindow = 3
browser.link.open_newwindow.restriction = 0
```
The first option is equivalent to the "open new pages in tabs" (instead of windows) setting via the Preferences interface; the second is the one more likely to have an impact, as it should supress all automatically spawned new windows.

If none of that works, please post the output of wmctrl -lx when the browser is running and your relevant launch-restore command.  This may motivate me to give rc2 a try, after being put off by the last beta.

---

### Post by Vouyeur on 2012-11-30
are there launch-restore updated version for ubuntu precise?

---

### Post by tweedledee on 2012-12-20
> **Vouyeur said:**
> are there launch-restore updated version for ubuntu precise?

No.  I didn't think anyone was still using this, and since I haven't used Ubuntu in years, I wasn't aware that it was in need of an update (it should still work under Gnome2/MATE/XFCE, which is what it was intended for).  Unless the issue to be fixed is pretty trivial, I doubt I have the time to spend on it.

---

