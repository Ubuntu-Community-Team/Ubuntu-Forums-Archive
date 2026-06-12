---
title: "Trying to get PDF Annotator 2 working..."
date: 2009-07-01
forum: Wine
---

### Post by autumnraine on 2009-07-01
[LEFT]Hi, there's a couple of us who have been trying to get PDF Annotator 2 to work, in this thread: [http://ubuntuforums.org/showthread.php?p=7547479#post7547479](http://ubuntuforums.org/showthread.php?p=7547479#post7547479). So far it isn't working. The program's own installer seems to run alright, but then it says that you need to install missing windows components, and something called InstallAWARE begins to run. It runs for 20 seconds or so and then says "Runtime error in install: Cannot open AVI", and then the install just stops. That's when Wine is emulating XP. I tried running it Vista mode and then the program won't run and brings up this message. "Missing Required Windows Service. Please ensure that the required 'TabletInputService' is running." Can somebody help us with this. This program is really important to a lot of students because there's no adequate native pdf annotator in linux, and the lack of this program is the only thing preventing me from being able to run Ubuntu full-time on my IBM X41 tablet.
[/LEFT]

---

### Post by Favux on 2009-07-01
Hi autumnraine,

Have you tried the PDF annotate feature in Xournal?  It's under File>Annotate PDF.

---

### Post by autumnraine on 2009-07-02
Yes, it's what I'm using in the meantime until I can get this program running. It's great for what it is, but it's not an actual pdf annotator... It does however work in the meantime. PDF Annotator just has more customizable configurations, such as hotkeying the pen, highlighter, etc. tools to your laptop buttons, which I haven't been able to do in Xournal. Also the fact that the highlighter in Xournal isn't fully transparent is kind of frustrating.

---

### Post by autumnraine on 2009-07-04
So looks like I need to run "TabletInputService" to get it working. Does anyone know how to run a Windows service in Wine?

---

