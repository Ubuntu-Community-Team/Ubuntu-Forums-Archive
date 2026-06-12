---
title: "fbnotify: Facebook Notifier"
date: 2014-01-04
forum: The Cafe
---

### Post by Kalabasa on 2014-01-04
**fbnotify** is a Facebook notifier for the desktop. :p I used *FBuntu*, a similar program, but now it isn't being maintained and it doesn't work.
[TABLE="width: 600"]
[TR]
[TD="align: center"][IMG]http://i.imgur.com/OFotbMk.png[/IMG]
Notify-OSD notifications[/TD]
[TD="align: center"][IMG]http://i.imgur.com/05dtT1K.png[/IMG]
Application indicator[/TD]
[/TR]
[/TABLE]

 Download the code from [GitHub]("https://github.com/Kalabasa/fbnotify#facebook-notifier") (or download the [zip]("https://github.com/Kalabasa/fbnotify/archive/master.zip"))

Follow the instructions from the project page, or...

> 
Copy everything to any directory.

You need to configure it to listen to your Facebook notifications feed.

First, execute **fbnotify.py**. It will show an error saying **no url found**. This URL, which is your FB feed, is needed by the program.
To get this URL:

[LIST=1]
[*]Go to [www.facebook.com/notifications]("http://www.facebook.com/notifications"). 
[*]Copy the **RSS** link in the **Get notifications via:** part. 
[*]Open the configuration file. See the terminal output for the path. This is usually at **~/.config/fbnotify/fbnotify.conf** 
[*]Paste the URL to the **url** field in the **[feed]** section. 
[/LIST]
 
To run, execute
```
./fbnotify.py
```
It is supposed to be ran in the background.

To stop, use an interrupt signal **Ctrl-C** and wait for it to finish.


Currently messaging menu integration is not yet implemented (You can help implementing it!).

If you want to contribute, just ask me! ;) Help wanted! Bug reports, suggestions, plugins, mono icons, packaging. It is preferrable if you report bugs in the GitHub issue tracker.

---

