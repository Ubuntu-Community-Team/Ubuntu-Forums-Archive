---
title: "trash can for gnome dash/dash to dock"
date: 2018-05-09
forum: Tutorials
---

### Post by kerry_s on 2018-05-09
alright peoples final script. should be user neutral just place in $HOME/Documents & make executable.

```


#!/bin/bash
icon=$HOME/.local/share/applications/trash.desktop

while getopts "red" opt; do
	case $opt in
    r)
	if [ "$(gio list trash://)" ]; then
		echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash-full\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$HOME/Documents/trash.sh -e'\n' > $icon
	fi
	;;
    e)
	gio trash --empty && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$HOME/Documents/trash.sh -e'\n' > $icon
	;;
    d)
	while sleep 5; do ($HOME/Documents/trash.sh -r &) ; done
	;;
  esac
done


```

once placed in Documents, open a terminal there, run-> trash.sh -e <- this will create trash.desktop in $HOME/.local/share/applications

final piece, you need to add to autostart-> trash.sh -d

example of my ~/.config/autostart/trash-icon.desktop:
```


[Desktop Entry]
Type=Application
Name=Trash Icon
Icon=user-trash
Exec=/home/user/Documents/trash.sh -d


```

enjoy your new trash icon for dash/dash to dock.  

[ATTACH=CONFIG]279637[/ATTACH][ATTACH=CONFIG]279638[/ATTACH][ATTACH=CONFIG]279640[/ATTACH]

[ATTACH]279797[/ATTACH]

---

### Post by kerry_s on 2018-05-14
the command is now "trash.sh -s" to set everything up

```


#!/bin/bash
# trash.sh -s <-create autostart & application

icon=$HOME/.local/share/applications/trash.desktop
start=$HOME/.config/autostart/trash.desktop

while getopts "reds" opt; do
	case $opt in
    r)
	if [ "$(cat $icon | grep Icon=user-trash-full)" ]; then
		exit 0
	elif [ "$(gio list trash://)" ]; then
		echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash-full\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$HOME/Documents/trash.sh -e'\n' > $icon
	fi
	;;
    e)
	gio trash --empty && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$HOME/Documents/trash.sh -e'\n' > $icon
	;;
    d)
	while sleep 30; do ($HOME/Documents/trash.sh -r &) ; done
	;;
    s)
	echo -e '[Desktop Entry]\nType=Application\nName=Trash Icon\nIcon=user-trash\nExec='$HOME/Documents/trash.sh -d'\n' > $start && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$HOME/Documents/trash.sh -e'\n' > $icon
  esac
done




```

---

### Post by logix2 on 2018-05-18
Nice script! One thing though: it shouldn't use the "Documents" folder directly because that's language-specific, so if someone doesn't have Ubuntu installed in English, that won't work. It would probably be better to use something like ```
$(xdg-user-dir DOCUMENTS)
``` (which returns the full path to the Documents folder, so it includes /home/user) instead of ```
$HOME/Documents
```

---

### Post by kerry_s on 2018-05-18
i was actually thinking about putting it in it's own folder "Trash" maybe with the script & the icons. so i can just zip it up & attach. ease of use. 
in some themes user-trash & user-trash-full are the same icon, which is why i think i should put the icons, otherwise there will/might be complaints about icon not changing.

any other thoughts? i been exploring the "gio monitor trash://" but i haven't got a script to work with it yet.

i'll make the changes & attach. i'm switching to solus mate tonight, some things i want to play with. so i probably won't work on any improvements to the script.

---

### Post by kerry_s on 2018-05-18
[ATTACH]279739[/ATTACH]

here's the new file with the changes. unzip in the home folder & enter it, right click-> open terminal here & run ./trash.sh -s

that's it reboot & it's good to go.

---

### Post by Perfect Storm on 2018-05-19
Should be default in Ubuntu.

---

### Post by kerry_s on 2018-05-19
i wouldn't say default, more like an option. 
i think since there doing away with the desktop icons, there should be a option to have those on the dock.

i was looking into maybe doing something for mounted drives/networks. i know there are extensions, but i so hate tiny icons(bad eyes), i'd much rather have it on the dock.
shelved for now, playing with mate+plank, instead of gnome.

---

### Post by logix2 on 2018-05-22
I noticed a bug. The second time you empty the trash, the icon no longer changes and it shows that the trash is full. Edit: I think that's because the icon isn't updated if the trash is emptied from Nautilus, and not from the icon context menu

---

### Post by logix2 on 2018-05-22
I managed to fix it, now the script will work even if the trash is emptied directly from Nautilus:

```

#!/bin/bash# trash.sh -s <-create autostart & application


icon=$(xdg-user-dir)/.local/share/applications/trash.desktop
start=$(xdg-user-dir)/.config/autostart/trash.desktop


while getopts "reds" opt; do
	case $opt in
    r)
	if [ "$(gio list trash://)" ]; then
		echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon='$(xdg-user-dir)/Trash/user-trash-full.svg'\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$(xdg-user-dir)/Trash/trash.sh -e'\n' > $icon
	else
		echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon='$(xdg-user-dir)/Trash/user-trash.svg'\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$(xdg-user-dir)/Trash/trash.sh -e'\n' > $icon
	fi
	;;
    e)
	gio trash --empty && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon='$(xdg-user-dir)/Trash/user-trash.svg'\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$(xdg-user-dir)/Trash/trash.sh -e'\n' > $icon
	;;
    d)
	while sleep 30; do ($(xdg-user-dir)/Trash/trash.sh -r &) ; done
	;;
    s)
	echo -e '[Desktop Entry]\nType=Application\nName=Trash Icon\nIcon='$(xdg-user-dir)/Trash/user-trash.svg'\nExec='$(xdg-user-dir)/Trash/trash.sh -d'\n' > $start && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon='$(xdg-user-dir)/Trash/user-trash.svg'\nExec=nautilus trash://\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec='$(xdg-user-dir)/Trash/trash.sh -e'\n' > $icon
  esac
done

```

I'm attaching the new Trash.zip with the fixed version, for anyone interested.

---

### Post by kerry_s on 2018-05-22
i changed that, that's how i had it before, cause it'll just keep swapping the icon over & over if you don't empty the trash. you can always right click-> empty trash to swap the icon back, whether there is trash or not.

also if you want the icon to change faster you can change the "while sleep 30;" to "while sleep 5;" it'll just cost a few more kib in memory/ram. i have mine set to 5.

for me this is just to remind me i have trash, when i don't empty right away & i always use the icon to empty.

---

### Post by kerry_s on 2018-05-22
[ATTACH]279796[/ATTACH]

here's the fixed version with the exit 0 still there so it don't go into an icon swap loop.

---

### Post by kerry_s on 2018-05-23
somethings wrong with the script, the applications are throbbing. i'll look into it & try to fix.

---

### Post by logix2 on 2018-05-23
I'm guessing this part is wrong:
```
"$(cat $icon | grep Icon=user-trash-full)"
```

... since the icon is used as "Icon='$(xdg-user-dir)/Trash/user-trash-full.svg", and not directly as "Icon=user-trash-full" so that statement is never true. But what would the "exit 0" be for? If the script exists, the while loop is gone and the icon isn't changed again, or am I wrong?

---

### Post by kerry_s on 2018-05-23
the exit 0 is to stop it replacing the icon if it's already been changed, other wise it keeps replacing the icon till it's emptied.

i need to check if it is emptied(from within files) then swap the icon back. same thing i only want it to change the icon once for each instance, 1 time when there's trash & then again if it's empty.

basically i was doing the swap back through the empty from the icon, but like you say it needs to be more automated for people who empty it from files.

i'm running some tests now.

---

### Post by kerry_s on 2018-05-23
[ATTACH]279807[/ATTACH]

i'm going to leave it be, modify as you wish.

warning/headsup: if you empty from within files, than empty the icon to return it to normal.

adding another loop to check if it's empty causes throbbing/flashing application icons. i just want to keep it simple, i'm not going to put in a whole lot of work just for a trash can.

---

### Post by kerry_s on 2018-05-23
alright logix2,

give this 1 a try it should work as expected, whether emptied from files or icon.

[ATTACH]279814[/ATTACH]

let me know what you think or if other problems.

---

### Post by logix2 on 2018-05-24
It works great now, thanks!

---

### Post by kerry_s on 2018-05-24
> **logix2 said:**
> It works great now, thanks!

your welcome, let me know if anything happens. i'm still testing it myself, memory usage seems fine, mine comes out to about 300kib(standard trash daemon runs 2mb), applications look good, there not throbbing/pulsing.

i swear i read at least 75% of gnome dev & freedesktop specs but still can't understand why the simple things are so complicated.

i was thinking about using a similar script for mounted devices, but i think i'm going to pass.

---

### Post by kerry_s on 2018-06-06
this version uses gvfs for other de's/wm's not running gio.
added sound just for fun. :)
same thing, run-> ./trash.sh -s <to setup

[ATTACH]280019[/ATTACH]

this version is for gnome that uses gio.
[ATTACH]280087[/ATTACH]

---

### Post by kerry_s on 2018-06-17
[ATTACH]280147[/ATTACH]

latest for gnome

---

### Post by kerry_s on 2018-06-26
[ATTACH]280227[/ATTACH]

rewrite/change how it's monitored, i think much better than "sleep 5".

---

### Post by kerry_s on 2018-06-27
[ATTACH]280250[/ATTACH]

moved the empty trash sound, so no matter where you empty from you get the sound.
you need inotify-tools
```
sudo apt -y install inotify-tools
```

---

### Post by kerry_s on 2018-06-29
[ATTACH]280248[/ATTACH]

i'm not happy with having to install inotify-tools, i'd prefer it just work on any distro, so i've gone with tail -f to do the monitoring for changes, same realtime effect as inotifywait, but tail is part of every distro so it'll just work.

everything else is same, just run > ./trash.sh -s <in the Trash dir to set everything up, then just reboot & add the trashcan to the dock/panel.
i also put the sound going both ways, cause why not.

**this 1's a dud, for some reason tail -f just dies out.**

---

### Post by q64ceo on 2019-05-16
Can I get an uninstaller, please?

---

### Post by oweck on 2019-11-24
Whooa, works great kerry_s, thank you!!! Maybe, if it is possible - it can has a multilanguage support? I have whole system in my language and between it is EMPTY TRASH command..;)

EDIT:
OK, I just made edits for translations in /.local/share/applications/trash.desktop

---

### Post by asieraccord on 2020-04-25
Fantastic work! 
Works like a charm.
Thanks for your effort, a was looking for something like this.

---

