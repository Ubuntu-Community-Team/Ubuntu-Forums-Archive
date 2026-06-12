---
title: "Start Menu + Applications"
date: 2013-05-11
forum: Ubuntu Application Development
---

### Post by Chrwc on 2013-05-11
Hello! I still don't have a full grasp on the linux (ubuntu) file system, so I have a simple question:

I'm trying to develop a simple app and to do what I'm trying to do I need to figure out how to find all the files (and where they are stored) used to show applications in the start menu. I'm looking for the file which shows what to execute to start the file and what image should be displayed as the icon.

If you could shed light on whether any differences there are between how this is done on ubuntu and other distributions it would be awesome.

Thanks!

---

### Post by Chrwc on 2013-05-11
I believe I have found my solution. it's in /usr/share/applications/. Thanks anyways!

---

### Post by deadflowr on 2013-05-11
Application launchers can be stored in either the /usr/share/applications folder(system-wide use)
Or the users home directory /home/username/.local/share/applications folder (per user use).

The launcher should have a name, and exec command, and a type(type is application, but there are others)
All other info is optional, like icons or categories.

The file name must use a .desktop extension.

The simplest way to see what a desktop file looks like open gedit and open a desktop file from the usr/share/applications folder.

---

