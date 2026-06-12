---
title: "Azureus from the command line"
date: 2006-11-25
forum: Server Platforms
---

### Post by twistedtwig on 2006-11-25
Hi guys and gals,

I dont have a clue if this is possible exactly to go about it really so thought i would ask.

1) is it possible to control Azureus(2.4.0.2) from the command line rather than the GUI?

2) if so is it possible to write a program (cron job i guess, no idea what language would be needed, guessing actually it could just be a text file with the command scripts in).. anyway, write something that could go check a folder each hour and if it finds a torrent file in there it copies it to another folder and starts the torrent downloading with Azureus???

as i say i have no clue about this but would be cool if it can be done.

thx

Twiggy

---

### Post by Belarios on 2006-11-25
You can either use the repository Azureus, or download just the jar file.  You also need the log4j.jar and commons-cli.jar:

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

There's some weak notes there about using the command line interface.  You can set the download folders and you should be able to set a watch folder.  Instead of the watch folder, I have the HTMLUI plugin installed and control it remotely from a web browser.

---

