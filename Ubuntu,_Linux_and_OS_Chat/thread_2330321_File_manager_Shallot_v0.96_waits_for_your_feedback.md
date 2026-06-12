---
title: "File manager Shallot v0.96 waits for your feedback"
date: 2016-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by shallot on 2016-07-10
Hello. 

 I want to announce Shallot, a file manager for Linux (and Windows). It is designed to be very flexible. And it has a plugin api ;)  

It would be great to get some feedback from you! [https://pseudopolis.eu/wiki/pino/projs/shallot/](https://pseudopolis.eu/wiki/pino/projs/shallot/) is the website.   

Greetings 
Josef  

PS: Nearby, there are also some other projects. If you want to give a useful rant about them, feel free of course ;)

---

### Post by QDR06VV9 on 2016-07-10
For those who wait for safety reasons here is a short summary.
> a highly flexible file manager with plugin interface
Shallot is a file manager with the maximum degree of flexibility and customizability. Some features:
* Unlimited number of file panels
* Lots of customization options, e.g.
* directory tree can be hidden and is flexible in behavior
* lots of view options
* program behavior
* ...
* while conserving a good usability
* It nicely works with convoluted file systems, like editing an image in an archive in another archive on a network drive.
* It has a plugin interface which allows one to implement many additional functionality (like new filesystems) with Python scripting, without any compiler hassles.
* It is Qt5 based and plays nicely with modern Linux desktops. See the downloads which other operating systems are supported (maybe with a few slight limitations).
My Effort resulted in this:
```
Selecting previously unselected package libqt5script5:amd64.
(Reading database ... 285273 files and directories currently installed.)
Preparing to unpack .../libqt5script5_5.5.1+dfsg-2build1_amd64.deb ...
Unpacking libqt5script5:amd64 (5.5.1+dfsg-2build1) ...
Selecting previously unselected package libqt5printsupport5:amd64.
Preparing to unpack .../libqt5printsupport5_5.5.1+dfsg-17ubuntu2~2_amd64.deb ...
Unpacking libqt5printsupport5:amd64 (5.5.1+dfsg-17ubuntu2~2) ...
Selecting previously unselected package libdouble-conversion1v5:amd64.
Preparing to unpack .../libdouble-conversion1v5_2.0.1-3ubuntu2_amd64.deb ...
Unpacking libdouble-conversion1v5:amd64 (2.0.1-3ubuntu2) ...
Selecting previously unselected package libqt5qml5:amd64.
Preparing to unpack .../libqt5qml5_5.5.1-2ubuntu8~2_amd64.deb ...
Unpacking libqt5qml5:amd64 (5.5.1-2ubuntu8~2) ...
Selecting previously unselected package libqt5quick5:amd64.
Preparing to unpack .../libqt5quick5_5.5.1-2ubuntu8~2_amd64.deb ...
Unpacking libqt5quick5:amd64 (5.5.1-2ubuntu8~2) ...
Selecting previously unselected package libqt5sql5:amd64.
Preparing to unpack .../libqt5sql5_5.5.1+dfsg-17ubuntu2~2_amd64.deb ...
Unpacking libqt5sql5:amd64 (5.5.1+dfsg-17ubuntu2~2) ...
Selecting previously unselected package shallot.
(Reading database ... 285374 files and directories currently installed.)
Preparing to unpack .../shallot_0.96.2406_amd64.deb ...
Unpacking shallot (0.96.2406) ...
Setting up shallot (0.96.2406) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.10.20160705-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu6) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Warning: mailcap line not starting with a media type in emerald
Problematic line:  application/x-emerald-theme; nametemplate=%s.emerald

```
Installed fine.Screenshot
Have not had a chance to run it extensively though. But will report later.
Regards

---

