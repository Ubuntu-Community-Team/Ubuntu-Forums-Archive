---
title: "Everlasting bug"
date: 2015-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by rodhos-hp on 2015-10-15
Bug 1170647 "After minimizing a Nautilus window of another partition or external media or Trash folder, clicking on the "Files" icon on the Launcher again doesn't restore the minimized window, but opens a new one" is really painfull and is driving me crazy. 
In Natty Narwhal the folder icon was called "Home folder" icon so the people expected the Home folder to open even when a trash folder was open. Moreover it didn't exist the "open new window" option which now appears when the icon is right clicked.
Then Mark Shuttleworth wrote:
"The Home Folder icon on the launcher should always open the Home folder
when clicked. If a previous invocation, or Trash, or other windows are
open and pointed elsewhere, then a new window should open with the Home
folder.
Mark"

Things have changed since then and now this behaviour is inconsistent. Someone provided a patch already but the bug is still alive since 2013-04-19.In my opinion this is embarassing. Are you affected by this bug too? Do you think this is inconsistent or a correct behavior?.

---

### Post by buzzingrobot on 2015-10-16
> **rodhos-hp said:**
> Bug 1170647 "After minimizing a Nautilus window of another partition or external media or Trash folder, clicking on the "Files" icon on the Launcher again doesn't restore the minimized window, but opens a new one"...

That's the default behavior in Gnome. Right click to open one of the existing windows?

---

### Post by rodhos-hp on 2015-10-17
When just one window is open there is not such option. When there is a second window the list of existing windows appears hence you can't restore the minimized window without opening a new one.

---

### Post by rodhos-hp on 2015-10-17
I've found 2 pages with workarounds and 1 thread in this forum closed.

[http://askubuntu.com/questions/463507/open-minimized-nautilus-window-and-not-open-home-in-launcher](http://askubuntu.com/questions/463507/open-minimized-nautilus-window-and-not-open-home-in-launcher)

[http://askubuntu.com/questions/324066/how-to-make-the-nautilus-icon-open-the-existing-window-instead-of-a-new-one](http://askubuntu.com/questions/324066/how-to-make-the-nautilus-icon-open-the-existing-window-instead-of-a-new-one)

[http://ubuntuforums.org/showthread.php?t=2141781](http://ubuntuforums.org/showthread.php?t=2141781)

Now I know there is workarounds but is still being an anoying inconsistent behavior and harms the Unity desktop's quality.

---

### Post by buzzingrobot on 2015-10-17
With some applications it's problematic opening multiple instances. However, if I do something like open a New Message window in Thunderbird, that is reflected in the Launcher and a right click enables me to move to, and from, that and the primary window.

If, for example, I open multiple instances of Terminal, then a right click on its Launcher icon indicates which is currently active and a list of the other open instances I can select, No specific indication is given if an instance is minimized, but the transfer works the same whether it is minimized or not.

With only one Terminal instance open, the right click shows an option to open a new instance. If that one instance happens to be minimized, then selecting the "Terminal" entry re-opens it,

I find the term "minimize" a bit out of place for interfaces like Gnome Shell and Unity, since minimization is a visual metaphor that relies on displaying tiny rectangular shapes in panels to represent minimized windows. Gnome and Unity don't use that kind of panel.

---

### Post by deadflowr on 2015-10-17
and yet no one ever pays attention to the device icon(s) at the bottom of the launcher that actually controls the external partition/trash.
The only "bug I've seen with using that is it doesn't work if the window is minimized in a different workspace.

---

