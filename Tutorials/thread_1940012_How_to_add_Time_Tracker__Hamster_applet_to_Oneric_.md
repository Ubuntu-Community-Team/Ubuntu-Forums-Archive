---
title: "How to add Time Tracker / Hamster applet to Oneric systray"
date: 2012-03-12
forum: Tutorials
---

### Post by Cicer on 2012-03-12
I recently upgraded to 11.10 and wanted to add the project Hamster/Time Tracker applet back to the systray notification area at the top of the screen. Alberto Milone developed an appindicator to do this. You can read the details [_here_]("http://albertomilone.com/wordpress/?p=502") and [_here_]("http://albertomilone.com/wordpress/?p=518"). They explain everything you have to do, but here's the copy paste version:

First you need to force install a patched version of the hamster applet (Oneric only):

```
sudo apt-get install hamster-applet=2.32.1-0ubuntu3~ppa1
```

Then install the indicator that puts the Time Tracker in the systray

```
sudo apt-get install hamster-applet=2.32.1-0ubuntu3~ppa1
```

To get automatic updates you can add the source to your list of software sources

```
sudo add-apt-repository ppa:albertomilone/hamster-indicator

```

To make the applet launch automatically on startup, search for Startup Applications in the Dash. Click "add" then fill in the name and comment fields and in the "command" field write

```
hamster-indicator
```

Then click "add". You'll need to log out and log back in for it to appear.

Pretty simple but maybe this will help someone else save the time I spent sorting it out.

---

