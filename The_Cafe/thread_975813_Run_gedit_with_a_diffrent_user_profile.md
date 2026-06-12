---
title: "Run gedit with a diffrent user profile"
date: 2008-11-08
forum: The Cafe
---

### Post by Lanrat on 2008-11-08
Hi. I use gedit as a normal text editor/viewer, and for programing. I would like it so that when gedit it used for opening a file it opens the way it normally would. but then to have some launcher that will open it with different plug-ins and settings when I use it for programing.

How is this possible?
Is there some sort of variable or command line argument I can use to specify a different config directory? The default one is /home/user/.gconf/apps/gedit-2 so would it be possible to specify another one like /home/user/.gedit_programing?

---

### Post by Devport on 2008-11-08
A quick solution that came to my mind is that you could create an extra user, e.g. username_dev, setup gedit to your development needs using that account and then launch gedit as that user using sudo. You could create a launcher using sudo / gksudo to start gedit dev and you could add an entry to nautilus context menu using nautilus-actions.

Just an idea, I didnt try that myself. Its a bit hackish but better than nothing. Funnily your topic title almost matches that solution.

---

### Post by Lanrat on 2008-11-08
I thought of that. But I would really like a way that does not involve making another user. just a diffrent profile. I dont want to need to enter a password everytime I run it and I would also like it to use my home directory and other global settings I have for my acount.

---

### Post by Lanrat on 2008-11-10
bump.

---

### Post by Lanrat on 2008-11-11
Anyone?

Would it be possible to make a link that only a certian instance of gedit would be able to see? a link to a diffrent config directory?

---

### Post by voteforpedro36 on 2008-11-11
> **Lanrat said:**
> Anyone?

Would it be possible to make a link that only a certian instance of gedit would be able to see? a link to a diffrent config directory?

Yeah, it would. First run "gedit -h" from the terminal. This should give you a help screen. Hopefully one of the things it can help you with is a switch to specify a config file. Now that you know that, copy the first config file (you said you found it), and run gedit with that switch pointing to the new config file, and make a shortcut to do that whenever you want to program.

BTW I don't have Gedit installed so I'm not sure what the config file switch is, or if there is one.

---

### Post by Lanrat on 2008-11-11
I have already looked, I do not see what you are talking about. do you mean Session management? I tried it but could not seem to get it to work.

```
gedit --help-all
Usage:
  gedit [OPTION...] [FILE...] - Edit text files

Help Options:
  -?, --help                      Show help options
  --help-all                      Show all help options
  --help-gtk                      Show GTK+ Options
  --help-sm-client                Show session management options

GTK+ Options
  --class=CLASS                   Program class as used by the window manager
  --name=NAME                     Program name as used by the window manager
  --screen=SCREEN                 X screen to use
  --sync                          Make X calls synchronous
  --gtk-module=MODULES            Load additional GTK+ modules
  --g-fatal-warnings              Make all warnings fatal

Session management options:
  --sm-client-disable             Disable connection to session manager
  --sm-client-state-file=FILE     Specify file containing saved configuration
  --sm-client-id=ID               Specify session management ID

Application Options:
  --encoding=ENCODING             Set the character encoding to be used to open the files listed on the command line
  --new-window                    Create a new toplevel window in an existing instance of gedit
  --new-document                  Create a new document in an existing instance of gedit
  --display=DISPLAY               X display to use

```

---

### Post by linkxs on 2008-11-12
use the power of alias command.

---

### Post by Lanrat on 2008-11-12
> **linkxs said:**
> use the power of alias command.

That does not do what Im trying to do. With that I need to have a command that can be entered already. I am not at that point. I was thinking into possibly trying it in chroot. but I have no experience with chroot.

Can anybody advise?

---

### Post by aysiu on 2008-11-12
The sloppy workaround would be to have the command be a shell script like this: ```
#!/bin/bash
mv /home/user/.gconf/apps/gedit-2 /home/user/.gconf/apps/gedit-2.user
mv /home/user/.gedit_programing /home/user/.gconf/apps/gedit-2
gedit &
``` with a corresponding ```
#!/bin/bash
mv /home/user/.gconf/apps/gedit-2 /home/user/.gconf/apps/gedit-2.programing
mv /home/user/.gconf/apps/gedit-2.user /home/user/.gconf/apps/gedit-2
gedit &
```

---

### Post by Lanrat on 2008-11-15
This still does not have the desired effect. This will not allow the 2 "versions" of gedit to run at the same time.

---

