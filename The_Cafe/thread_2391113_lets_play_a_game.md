---
title: "lets play a game"
date: 2018-05-06
forum: The Cafe
---

### Post by kerry_s on 2018-05-06
the mission is simple, check a directory for content, if there is content, replace a line in a file.
i'm thinking maybe script run with cron?

how would you do it?

what i'm actually doing is making a trash app/launcher just for the heck of it. i just want a working trash icon on my dash to dock.

the line i want to swap back & fourth
```

Icon=user-trash
to
Icon=user-trash-full

```

my trash.desktop
```

[Desktop Entry]
Type=Application
Name=Trash
Comment=Trash
Icon=user-trash
Exec=nautilus /home/user/.local/share/Trash
Categories=Utility;
Actions=trash;

[Desktop Action trash]
Name=Empty Trash
Exec=/home/user/Documents/trash.sh

```

my trash.sh
```

#!/bin/sh
rm -rf /home/user/.local/share/Trash/*

```
[ATTACH=CONFIG]279591[/ATTACH][ATTACH=CONFIG]279592[/ATTACH]

truth is i haven't done scripting in ages, i'm trying to remember, but my brains just not there. i'm not sure what to use.
maybe something like:
```

#!/bin/sh
path=/home/user/.local/share/Trash
1=Icon=user-trash
2=Icon=user-trash-full
icon=/home/user/.local/share/applications/trash.desktop

if [ ! "$(ls -A $path)" ]
then
    sed -i "/$1/c $2" $icon
else
    sed -i "/$2/c $1" $icon
fi

```

---

### Post by kerry_s on 2018-05-06
working script:

```

#!/bin/sh
cp /home/user/.local/share/applications/trash.desktop /home/user/.local/share/applications/trash.desktop.bak
path=/home/user/.local/share/Trash/files
icon=/home/user/.local/share/applications/trash.desktop
icon2=/home/user/.local/share/applications/trash.desktop.bak

if [ "$(ls -A $path)" ]; then
    sed 's/user-trash/user-trash-full/' $icon2 > $icon
else
    sed 's/user-trash-full/user-trash/' $icon2 > $icon
fi


```

---

### Post by kerry_s on 2018-05-06
alright, i got working trash on my dash to dock. :D
i'm sure there are other ways to do it, this is the way i did it trying to keep it simple with the same results every time, doesn't spawn the same process over & over, doesn't drive the memory up. doesn't screw up the trash.desktop, which is why i dropped sed for cat.
anyways enjoy.

updated i just use 3 files now

i guess i'll star with the scripts.

trash.sh -r <-checks for trash & changes icon
trash.sh -e <- empties trash & changes icon back.
trash.sh -d <-add this to startup

trash.sh
```

#!/bin/bash
path=/home/user/.local/share/Trash/files
icon=/home/user/.local/share/applications/trash.desktop

while getopts "red" opt; do
	case $opt in
    r)
	if [ "$(ls -A $path)" ]; then
		echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash-full\nExec=nautilus /home/user/.local/share/Trash/files\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec=/home/user/Documents/trash.sh -e\n' > $icon
	fi
	;;
    e)
	rm -rf /home/user/.local/share/Trash/files/* && rm -rf /home/user/.local/share/Trash/info/* && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash\nExec=nautilus /home/user/.local/share/Trash/files\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec=/home/user/Documents/trash.sh -e\n' > $icon
	;;
    d)
	while sleep 60; do (/home/user/Documents/trash.sh -r &) ; done
	;;
  esac
done

```

trash.desktop <-this is the applet/application that you would add to dock
```

[Desktop Entry]
Type=Application
Name=Trash
Comment=Trash
Icon=user-trash
Exec=nautilus /home/user/.local/share/Trash/files
Categories=Utility;
Actions=trash;

[Desktop Action trash]
Name=Empty Trash
Exec=/home/user/Documents/trash.sh -e

```

---

### Post by thenailedone on 2018-05-06
I am a tad OCD when it comes to my Recycle Bin. I always delete completely, never send anything there 8-)

---

### Post by kerry_s on 2018-05-06
> **thenailedone said:**
> I am a tad OCD when it comes to my Recycle Bin. I always delete completely, never send anything there 8-)

i use to do that, but now i'm old & make more mistakes. my attention span is all over the place sometimes. ;)

---

### Post by kerry_s on 2018-05-07
i updated post #3 cause i changed from cat file > file to echo > file, getting rid of the 2 spare copies, now i'm down to 4 files to have a working trash icon.

i'd like to combine trash.sh & trash-icon.sh to 1 file if i can.

---

### Post by kerry_s on 2018-05-07
okay i combined trash.sh & trash-icon.sh in to 1 file. i'll fix post #3 with new file.

trash.sh -r <-checks for trash & changes icon
trash.sh -e <- empties trash & changes icon back.

```

#!/bin/bash
path=/home/user/.local/share/Trash/files
icon=/home/user/.local/share/applications/trash.desktop

while getopts "re" opt; do
	case $opt in
    r)
	if [ "$(ls -A $path)" ]; then
		echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash-full\nExec=nautilus /home/user/.local/share/Trash/files\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec=/home/user/Documents/trash.sh\n' > $icon
	fi
	;;
    e)
	rm -rf /home/user/.local/share/Trash/files/* && rm -rf /home/user/.local/share/Trash/info/* && echo -e '[Desktop Entry]\nType=Application\nName=Trash\nComment=Trash\nIcon=user-trash\nExec=nautilus /home/user/.local/share/Trash/files\nCategories=Utility;\nActions=trash;\n\n[Desktop Action trash]\nName=Empty Trash\nExec=/home/user/Documents/trash.sh\n' > $icon
	;;
  esac
done


```

---

### Post by kerry_s on 2018-05-07
i went ahead & added the watch.sh into trash.sh to just make it 2 files for a working trash can app.
[ATTACH=CONFIG]279613[/ATTACH][ATTACH=CONFIG]279614[/ATTACH][ATTACH=CONFIG]279615[/ATTACH]

---

### Post by thenailedone on 2018-05-08
Nice project, well executed :KS

---

### Post by kerry_s on 2018-05-08
> **thenailedone said:**
> Nice project, well executed :KS

thank you, i was just bored & it didn't seem like it would be to complicated. i still had to rtfm cause there are a lot of ways of doing it, i just wanted simple so any 1 could use it just changing the "user" name & maybe path.

i suppose i could make that easier using $user at the top.

i'll fix it later, i gotta go get my weekly blood test, i so hate the smell of hospitals now.

---

### Post by kerry_s on 2018-05-08
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

example:
```


[Desktop Entry]
Type=Application
Name=Trash Icon
Icon=user-trash
Exec=/home/user/Documents/trash.sh -d


```


enjoy your new trash icon for dash. :P :popcorn:

---

### Post by thenailedone on 2018-05-09
I was able to get a similar result from installing KDE ;)

---

### Post by kerry_s on 2018-05-09
> **thenailedone said:**
> I was able to get a similar result from installing KDE ;)

:lolflag:

---

