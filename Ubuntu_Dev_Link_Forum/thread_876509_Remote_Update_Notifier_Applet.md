---
title: "Remote Update Notifier Applet"
date: 2008-07-31
forum: Ubuntu Dev Link Forum
---

### Post by survient on 2008-07-31
I'm looking to make a small applet/docklet that will appear in the system tray if updates on a remote system are detected. I have a server with ubuntu on it, but I always forget to check it for updates, so on my desktop(running ubuntustudio, but with kde as the manager) I'd like to make something like the adept update manager or just gnome's update manager, only for managing a remote system instead, probably through an ssh session. I'm new to programming for debian, and linux in general, so I just needed some pointers on which language to look into. I'm fairly well versed in java, C# and php, so I can pick up a language pretty quick. I know of python being a popular one, just wondering what would be the best to use, and any suggestions on an approach to this would be appreciated. Thanks.

---

### Post by tinny on 2008-08-01
> **survient said:**
> I'm looking to make a small applet/docklet that will appear in the system tray if updates on a remote system are detected. I have a server with ubuntu on it, but I always forget to check it for updates, so on my desktop(running ubuntustudio, but with kde as the manager) I'd like to make something like the adept update manager or just gnome's update manager, only for managing a remote system instead, probably through an ssh session. I'm new to programming for debian, and linux in general, so I just needed some pointers on which language to look into. I'm fairly well versed in java, C# and php, so I can pick up a language pretty quick. I know of python being a popular one, just wondering what would be the best to use, and any suggestions on an approach to this would be appreciated. Thanks.

Python is probably the best way to go for a Linux only application.

However if you want platform Independence go with Java. If you are already comfortable with Java then just use that.

FYI:
Java 6 System Tray API.

[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/)

[http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html](http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html)

---

### Post by survient on 2008-08-02
well is anybody familiar with the update system? I'm thinking I just need a way to have a flag sent back via sh that says updates are available to the main program, but I'm not entirely sure. I would go java, but this is intended as a linux only app, at least for now.

---

