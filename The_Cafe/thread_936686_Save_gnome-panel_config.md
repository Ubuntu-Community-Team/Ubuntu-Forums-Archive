---
title: "Save gnome-panel config"
date: 2008-10-03
forum: The Cafe
---

### Post by aschwerin.moses on 2008-10-03
Is it possible to save the config file of gnome-panel?

I did not find any config file in ~/.gnome2/panel2.d apart from the default one.

Helpppppp...

---

### Post by aschwerin.moses on 2008-10-03
no one knows if we can do this???

---

### Post by Sylchat on 2008-10-30
Hi

That's what I'm looking for too. My icons get mixed up sometimes after a reboot and I wanted to check where the config is saved... But this should get saved automatically on gnome logout.

For me, "./panel2.d/default/launchers" contains a few launchers, that's all.

But I guess it's here:
/home/sylchat/.gconf/apps/panel/

Config would be stored in xml files. But there are a few of them:
$ find . | grep -i ".xml"
./%gconf.xml
./global/%gconf.xml
./toplevels/%gconf.xml
./toplevels/panel_1/%gconf.xml
./toplevels/panel_1/background/%gconf.xml
./applets/%gconf.xml
./applets/notification_area_screen0/%gconf.xml
./objects/%gconf.xml
./general/%gconf.xml
(...)

This one ./toplevels/panel_1/%gconf.xml seems to contain some properties about the 1st panel you have.

cheers

---

### Post by gtmarks on 2010-07-29
In Ubuntu 10.04 the application launchers you add to the panel seem to be stored in the directory ~/.gnome2/panel2.d/default/launchers/ .  So I suspect you could run tar and bzip2 on this directory to back it up, and quickly reproduce your panel configuration on a new installation by copying the files (with suffix "desktop") from that directory (though I have not actually tried this myself).

---

### Post by Mr. Picklesworth on 2010-07-29
They're in gconf, under /apps/panel.

So, the directory you can back up is ~/.gconf/apps/panel.

---

### Post by loopduplicate on 2011-03-15
[FONT=Georgia][SIZE=2][SIZE=3]I [/SIZE]made a script for this.  
[SIZE=3]I[/SIZE]t has comments.
[[SIZE=3]S[/SIZE]end me a message if you need more clarity.]("http://ubuntuforums.org/member.php?u=1006936")
[SIZE=3]T[/SIZE]his works as of 10.10.  
[SIZE=3]C[/SIZE]opy and paste the code below to a terminal.  
[SIZE=3]T[/SIZE]o open a terminal window, hit ctrl+alt+T *[COLOR=Black](I may have set this shortcut key myself in the Ubuntu preferences, can't remember so I hope it works for you.)[/COLOR]*
[/SIZE][/FONT]```
#!/bin/sh
# saves gnome panel layout to home folder with today's date in the 
# filename so you can just run this as a backup and it won't overwrite 
# a previous backup

# to load one of these backups use the load argument like this:
# gconftool-2 –load ~/gconfpanelsbackup1299439417_SunMar06_2011_112337.xml
# then make sure to restart gnome-panel to see changes, like this:
# killall gnome-panel
# you might need to restart gnome network monitor applet which dies after killall gnome-panel, like this:
# nm-applet &

# set the date format part of the filename
mycooldateformat=$(date +"%s_%a%b%d_%Y_%H%M%S")
# set the whole path
myfilepath=~/gconfpanelsbackup$mycooldateformat.xml
# backup to the whole path
gconftool-2 --dump /apps/panel > $myfilepath
```:guitar:

---

### Post by cariboo on 2011-03-15
This thread is 3 years old, if a spammer hadn't dug it up in 2010, and someone noticed it, it would still be peacefully sleeping.  @loopduplicate, start a thread in the proper place, because this thread is closed.

---

