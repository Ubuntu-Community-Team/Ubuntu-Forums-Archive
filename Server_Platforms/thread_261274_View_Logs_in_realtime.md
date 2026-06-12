---
title: "View Logs in realtime"
date: 2006-09-20
forum: Server Platforms
---

### Post by leach on 2006-09-20
Hi all, I have a problem that I can't seem to find an answer to. I'm doing some stuff with my ftp server running with vsftpd where it would be incredible convenient to see my logs for vsftpd in real time, is there a way to do this? Thanks.

---

### Post by moma on 2006-09-20
Solution 1:
You can employ one of the text consoles (virtual TTYs) to display the log listing.  With a text console  I mean the screens that appear when you press CNTR + ALT + F1 (F1...F6).

An example:

Edit your /etc/inittab and choose eg. /dev/tty5  (ALT + CNTR + F5) for the task.

$ [COLOR="Green"]sudo cp -b /etc/inittab /etc/inittab.backup[/COLOR]
$ [COLOR="Green"]sudo gedit /etc/inittab[/COLOR]

Locate and edit the line for virtual terminal 5.
```
# Virtual terminal 5 will show the last lines of /var/log/messages log.
5:2345:respawn:/usr/bin/tail -f /var/log/messages > /dev/tty5
```

Of course, replace /var/log/messages with the correct log file for the FTP program.
-------------------------------------------------------------------------------------
Solution 2:

Use the 'watch' and 'tail' commands to show the log listing in a normal terminal window (gnome-terminal or xterm).

$ [COLOR="Green"]watch tail -n 20 /var/log/any_log_file[/COLOR]

---

