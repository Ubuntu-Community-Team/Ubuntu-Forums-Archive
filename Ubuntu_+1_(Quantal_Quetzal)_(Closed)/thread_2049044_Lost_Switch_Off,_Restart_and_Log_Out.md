---
title: "Lost Switch Off, Restart and Log Out ?"
date: 2012-08-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cecilpierce on 2012-08-27
Any one have this problem ? I have to go to tty1 and do Ctrl+Alt+Delete to restart or shut down.
Its been like this for a few days now.

---

### Post by VinDSL on 2012-08-27
I lost them in Unity, but not G-S & LXDE.

As it turned out, it's theme related, in my case.

The session buttons have shifted so far to the right, on the panel, that they're sitting outside the visible display area.  If I hover my mouse pointer in the extreme right corner of the display, and click, the sessions panel will pop up.  Otherwise, it's effectively invisible.

Switching the GTK theme to Ambiance brings the session buttons back into view, but as soon as I pick another theme, they disappear again.

Hopefully, that's what you're asking about.  LoL!

If not, ignore the above...  ;)

---

### Post by jerrylamos on 2012-08-27
Oh, yes, with Unity.  I also have a 800x600 wallpaper pasted on the top left of the 1366x768 screen and two sets of switch off, etc. applets, one ending at 800 and the other ending at 1366.  The set ending at 1366 don't work, the set ending at 800 did - at least log off so I could log in to the LXDE desktop I had just installed.  LXDE works fine I don't think they are doing active changes on it like they are on Unity.  No clue what they are doing to Unity, I presume adding more features/code?

Jerry

---

### Post by cecilpierce on 2012-08-27
Sorry I didn't explain better, I see the list but clicking on them does nothing, the only one that works is Guest Session.

---

### Post by jbicha on 2012-08-27
cecil, perhaps you've hit b[ug 861171]("http://pad.lv/861171") Ubuntu silently won't let you shutdown or reboot if other users are logged in.

Yes, indicator-session badly needs to have a fallback icon. I think it's been fixed now, but switching to one of the accessibility themes (like High Contrast) would result in losing the "system" status menu. There are still a bunch of usability problems with activating the accessibility themes. :-(

---

### Post by cecilpierce on 2012-08-27
@jbicha

Thanks, that is the bug, I have another QQ that works fine but one don't, weird !
Ill check the polkit and see what the differance is.

Just looked at both, they are the same, so not sure whats next !
Wait and see...

---

### Post by mc4man on 2012-08-27
Right after the recent indicator-session upgrade the menu dropdown items were visible but non-functional (logout thru shutdown.
It was  resolved by a logout/in & all work

The bug mentioned was initially more about from the greeter, not inside of a session.

When inside a session if more than 1 account is logged in all the choices in the indicator menu work. However when completing either the restart or shutdown choice you'll be brought to the greeter screen instead
(the log out choice would obviously work.

As described here in OP it seemed to be the indicator in a session has these non functioning  items when clicked on

---

### Post by jerrylamos on 2012-08-28
logout - what's the cli for that in Ubuntu?  sudo reboot works, sudo halt works, sudo logout does not.  What I'm trying to do is get back to the login screen so I can switch desktops.

Guess I have to wait for the Unity people to fix the drop down window....
With Ctrl-Alt-F1 can cli stop Unity or is it stopped already?
What's the start commands for other desktops such as openbox or lxde?

Only reason I'm asking is with Uniy/Compiz under active development (have been sarting with Narwhal) sometimes normal drop down windows don't work.  I presume Unity or whatever the follow(s) on will be will be in consant development so it's nice to have some recovery methods.

Thanks, Jerry

---

### Post by pressureman on 2012-08-28
> **jerrylamos said:**
> logout - what's the cli for that in Ubuntu?  sudo reboot works, sudo halt works, sudo logout does not.  What I'm trying to do is get back to the login screen so I can switch desktops.

Why on earth would you need to "sudo" to log out of your *own account?* If you "sudo logout" it'll simply be launching a shell as root and immediately logging out of that shell, dropping you back to where you were. Ditch the sudo. Just logout, exit, or ctrl-D.

If you want to restart the desktop environment, "sudo restart lightdm" should do the trick.

---

### Post by dino99 on 2012-08-28
under gnome-classic i'm using a custom menu icon added by "add to this panel" and indicator-appmenu is installed indeed (adwaita theme)

all fine here ):P

---

### Post by jerrylamos on 2012-08-28
> **pressureman said:**
> Why on earth would you need to "sudo" to log out of your *own account?* If you "sudo logout" it'll simply be launching a shell as root and immediately logging out of that shell, dropping you back to where you were. Ditch the sudo. Just logout, exit, or ctrl-D.

If you want to restart the desktop environment, "sudo restart lightdm" should do the trick.
Thanks.  I did drop down menu logout on LXDE, logged in to Unity.
Still has two sets of applets, one ending at 800 on the screen and the other at 1366.  Yesterday the ones ending at 1366 didn't work, after today's update they did.

When I select the applet star the drop down menu is black, mouse over and the captions appear in sections.

Anyway logout did work from Unity today.

Jerry

---

