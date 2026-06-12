---
title: "Cant access qjackctl gui at all, broken tray icon, only way to exit=kill process"
date: 2013-12-14
forum: Ubuntu Studio
---

### Post by onerose on 2013-12-14
If I click on qjackctl icon on the Launcher it just opens one more instance. I tried uninstalling using purge and reinstalling to no avail. Help.
The icon is supposed to show a menu from the tray upon clicking but it is broken.... [ATTACH=CONFIG]248590[/ATTACH]
There is no way to exit unless I kill the process. I cant even access gui to set it up because there is no option "bring to front" in system monitor. I think I messed it up myself on accident because I allowed several instances and since then I cant access gui to correct it. The tray icon was broken from the start though. I uninstalled and reinstalled, it is the same.
I am trying to set jack up so I can run ardour... it kept freezing because jack isnt running at all or something else is wrong with it. I talk to other users on irc and they said after a few tests that jack isnt running right or at all. Thanks in advance, I normally use ubuntu for everything but when it comes to sound I want to pull my hair.

---

### Post by jejeman on 2013-12-14
Try to reset your settings. Move the file from ~/.config/rncbc.org.

---

### Post by onerose on 2013-12-14
That worked! I can access the gui now, thank you.
If someone else has tray menu working and it is not the same as mine, please post here so I know whether it is some official bug or it happens just to me due to something on my system. I will try now to setup jack as other users on the forum instructed it should be done.

Edit: Ardour is now not freezing, I successfully recorded audio in it now, unticked Realtime in jack setup and that worked for me! Thanks everyone. About the tray, maybe there is no menu supposed to be there, just the icon to indicate that jack is on. Anyways that is a minor issue. I dont have sound on my headphones since installing Ardour, but it works on speakers... I will try now with editing alsa settings as meddling with alsamixer didnt work.

---

### Post by chocalopix on 2014-11-20
I have the same issue.

---

