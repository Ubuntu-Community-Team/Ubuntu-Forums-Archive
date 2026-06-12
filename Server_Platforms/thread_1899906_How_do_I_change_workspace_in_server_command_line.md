---
title: "How do I change workspace in server command line"
date: 2011-12-24
forum: Server Platforms
---

### Post by Krahazik on 2011-12-24
I am new to Ubuntu Server and I was wondering how do I change workspaces in the command line. I do not have a GUI installed.
Using Ubuntu Server

---

### Post by Habitual on 2011-12-24
"Workspace" is a resource term reserved for GUI Desktops, not the command-line, sorry.

---

### Post by lensman3 on 2011-12-24
Command "newgrp" with the new group you want to become.

"groups" tell you which groups you belong to.

Not sure what you are asking.  Default group is the same one you login with.

---

### Post by memilanuk on 2011-12-24
Locally, use Ctrl+Alt+F2 to change to the second terminal (tty), Ctrl+Alt+F1 to go back.

Alternately, you can install [screen]("http://www.gnu.org/software/screen/") and have not only a persistent login environment i.e. you can be logged in remotely, working on whatever and if something happens like your network connection drops out (more of a concern back when dial-up was my only connection) when you re-connect and log back in you can resume your work without missing a beat - reconnect to the screen session and everything should be as you left it.  Screen makes it reasonably easy to have one 'window' or 'screen' dedicated to your email client, another to your newsreader, another to an editor, another to a long-running compiler session, etc.

Ubuntu makes available a wrapper for screen called '[byobu]("https://help.ubuntu.com/community/Byobu")' that is a little easier to setup and comes with some nifty status bar features if that is what you want.

HTH,

Monte

---

### Post by a2j on 2011-12-26
Alt+F1, F2, F3, F4 usually works.

---

### Post by rubylaser on 2011-12-26
+1 for screen

---

