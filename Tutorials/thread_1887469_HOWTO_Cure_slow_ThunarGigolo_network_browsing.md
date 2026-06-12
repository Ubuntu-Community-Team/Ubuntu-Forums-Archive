---
title: "HOWTO: Cure slow Thunar/Gigolo network browsing"
date: 2011-11-27
forum: Tutorials
---

### Post by Kronalias on 2011-11-27
BACKGROUND
I'm on Xubuntu 11.10 Oneiric and playing with a nice little pink 'n' fluffy headless (as in the only physical connection is for power) Zotac Zbox ID41 which will end up replacing my big ol' hairy grunty full of terrorbites MythTV box. It needs to connect wirelessly to samba network shares, and I hit a problem which seems to be a variant of other moans that I've seen about slow network browsing. The Zbox is administered remotely (usually from my 1280x800 resolution laptop) so I use vino to provide a native display (as in the real display that would show up if a monitor was connected), and vncserver to provide a virtual display of 1280x800 resolution.

PROBLEM
If I vnc into the native display I can start Gigolo and then Thunar pretty instantaneously.
If I vnc into the virtual display I get a 30 second wait if I try to start either Gigolo or Thunar. And sometimes I get two instances of Thunar starting.

FIRST CURE
The first cure is to make sure that Gigolo works. Xubuntu 11.10 ships without gvfs-backends, which Gigolo needs - just check by starting Gigolo and View => Sidepanel. If you can't see a Network tab then:
sudo apt-get install gvfs-backends
Now restart Gigolo and you'll have a Network tab.

SPEED UP THUNAR
When Thunar starts up it stats the network. For some reason this happens pdq if I connect remotely to a native display, but takes an age if I connect to a virtual screen. The cure is to stop Thunar trying to network browse when it starts - this won't do any harm, and still lets Thunar see any network shares that you connect to. 
Edit the file /usr/share/gvfs/mounts/network.mount (as root), and change AutoMount from true to false.

GIGOLO SETUP
Once you've got Gigolo working you need to configure it. This is my setup:
Gigolo => Edit => Preferences => General =>
 File Manager: gvfs-open
 Bookmark Auto-Connect Interval: 60
Edit => Preferences => Interface =>
 Tick Save window position and geometry
 Tick Show status icon in the Notification Area
 Tick Start minimized in the Notification Area
 Tick Show side panel
 Untick Show auto-connect error messages
 Connection List Mode: Detailed List
Edit => Preferences => Toolbar =>
 Tick Show toolbar
 Style: Text
 Orientation: Horizontal
View =>
 Tick Toolbar
 Tick Side Panel
 Tick Status Icon
 Radiobutton On: View as Detailed List
Click the Network tab, browse, click on network share => Click Connect
Service type: Custom Location, click Connect (you should automatically get a URI along the lines: smb://elsie8/media/)
Right click in right pane on a connection and Create Bookmark, Ok
Click the Bookmarks tab, highlight a connection and click Edit Bookmarks.
Higlight a Bookmark in the right pane, right click it and click Edit Bookmark.
Double click on a bookmark (or right click and edit) and tick Autoconnect.
On mine I autoconnect to "media on elsie8", "mythtv-only on elsie8", "storage on elsie8", "downloads on elsie8"

GIGOLO AUTOSTART
There's some sort of timing issue going on that prevents Gigolo starting properly if you just use the command 'gigolo' in an Application Autostart. The fix is to pause for a few seconds while the session starts, and then start Gigolo. This doesn't work as a one-liner, so you need a script.
Create a file (mine's /home/martyn/my/scripts/start-gigolo.sh) with these three lines in it (sleep 5 just pauses things for 5 seconds):
#!/bin/sh
sleep 5
gigolo
Make sure the file is executable and then make it autostart:
Settings => Settings Manager => Session & Startup => Application Autostart
Name: Start Gigolo
Description: Enable network browsing
Command: /home/martyn/my/scripts/start-gigolo.sh

CHECK IT WORKS
Reboot or log out and back in, and look in ~/.gvfs.

This will either be empty if things went wrong, or will have the mounts for your network shares.
Browse to ~.gvfs in Thunar (it's a hidden file because of the dot, so use Ctrl-H to unhide it). Highlight a share, right click, Send To > Side Panel (Create Shortcut).

Reboot or log out and back in. You should now be able to open Thunar and see your shortcut at the bottom of the left hand pane (pain?).

Hope this helps!

---

### Post by nublaii on 2011-12-08
I usually create a symlink to .gvfs on my home dir to quickly acces the mounted shares

```
ln -s ~/.gvfs ~/shares
```

That way I can access them quicker, specially from open/save dialogs ;)

---

