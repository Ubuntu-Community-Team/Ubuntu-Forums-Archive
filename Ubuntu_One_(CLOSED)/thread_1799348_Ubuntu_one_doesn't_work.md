---
title: "Ubuntu one doesn't work"
date: 2011-07-07
forum: Ubuntu One (CLOSED)
---

### Post by Juan Manuel Rivero on 2011-07-07
Hello,

I have the 11.04 version.

I've tried to run Ubuntu One from the Launcher, but it doesn't do anything, so I have to go to the terminal and write sudo ubuntuone-control-panel-gtk
Once it runs, the window opens, and where it should say File Sync is up-to-date it appears in red letters this error:
[COLOR="Red"]File Sync error. (org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1)[/COLOR], next to it I have the option [COLOR="DarkOrange"]Restart[/COLOR], but it doesn't do anything if I click it.

If I go to the section "Cloud Folders" it appears:

[COLOR="Red"]Value could not be retrieved. (DBus exception: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1)[/COLOR]

The folder Ubuntu One that should appear in my Home Folder, doesn't exist.

I've tried to find an answer to this problem in many forums, bug reports, and despite theres one or two that shows a similar problem ([http://ubuntuforums.org/showthread.php?t=1602806](http://ubuntuforums.org/showthread.php?t=1602806), [http://askubuntu.com/questions/9486/...ically-at-boot](http://askubuntu.com/questions/9486/...ically-at-boot)) I can't fix the problem.

Does anyone have an idea of what to do?

I'm new in Linux, so there's a lot of things I don't know how to do.

Thanks

Juan Manuel

---

### Post by duanedesign on 2011-07-11
Could you try ubuntuone-control-panel-gtk without sudo. Ubuntu One does not like to be run as root.

thank you,
duanedesign

---

### Post by Juan Manuel Rivero on 2011-07-14
Thanks, I´ll try it and let you know what happened.

Juan Manuel

---

### Post by Juan Manuel Rivero on 2011-07-18
It didn't work. It didn't even open Ubuntu One without the sudo.

Juan Manuel

---

### Post by duanedesign on 2011-07-18
Does anything get printed to the Terminal after you run the command ubuntuone-control-panel-gtk?

You can get more detailed logs to help in troubleshooting issues by doing the following:

1. Open Applications->Accessories->Terminal and run:
```
echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c
```

2. Copy files into your ~/Ubuntu One folder and let it run for awhile to collect information.

3. Open your home folder

4. Click the View->Show Hidden Files menu option

5. Open the .cache/ubuntuone/ folder

6. Right click on the log/ folder and select "Compress"

7. Click OK and you should have a file named "log.tar.gz" in the .cache/ubuntuone folder, move this file to your Desktop since it's in a hidden folder which can be hard to find in the next step

8. You can attach the log.tar.gz archive to an email to [EMAIL="ubuntuone-support@canonical.com"]Ubuntu One Support[/EMAIL].

respectfully,
duanedesign

---

