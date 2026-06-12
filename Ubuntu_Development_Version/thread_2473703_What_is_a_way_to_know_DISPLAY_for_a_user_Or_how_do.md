---
title: "What is a way to know DISPLAY for a user? Or how do I launch a GUI window for a user?"
date: 2022-04-11
forum: Ubuntu Development Version
---

### Post by and-account on 2022-04-11
Hi!

What is a good way to know current DISPLAY values?
Or how do I from a script to be launched as root show an interface of a GUI app for a regular logged in user, if user logged in GUI session?

I have scheduled script to run as root. I want this script to pop up GUI windows with text (Zenity dialogs) if a user is logged in. Now days it is not possible to launch GUI apps as root. I need DISPLAY value in order to launch it:

```
root@host: ~ # DISPLAY=:0 sudo -u user -i zenity --info --text=ABCDEFG
```

In past [FONT=courier new]'who'[/FONT] had value of DISPLAY variable in last column and it was easely extracted from the column. Now days - it's not. [FONT=courier new]'loginctl'[/FONT] and [FONT=courier new]'w'[/FONT] today do not have the value too.

```
$ loginctl list-sessions
SESSION  UID USER SEAT  TTY  
     15 1000 user seat0 tty2


$ loginctl show-session -p Display
Display=

```

How may I launch a GUI app for a user at seat0 without a hardcoded values?

---

### Post by #&amp;thj^% on 2022-04-11
Just so I'm clear  are you asking to run a GUI application as a different user?
```
echo $DISPLAY
:0.0
```

---

### Post by and-account on 2022-04-11
Yes, launch as another user, but when the script is launched not in GUI session or/and as root. Launch by Cron or Systemd timer are not a GUI sessions.

This way DISPLAY is even unset at all:

```
user@host: ~ $ echo $DISPLAY
:0
user@host: ~ $ sudo su -
root@host: ~ # sudo -i -u user bash -c 'echo $DISPLAY'

root@host: ~ # echo $DISPLAY

root@host: ~ # set | grep DISPLAY
root@host: ~ # 

```

---

### Post by The Cog on 2022-04-11
I think that in addition to setting DISPLAY (which I think is always :0), you can only run gui apps as the user that currently owns the display.
Try this (as root):
```

username=$(w | awk '$3==":0"{print $1}')
sudo -u $username DISPLAY=:0 xeyes
```

---

### Post by #&amp;thj^% on 2022-04-11
> **and-account said:**
> Yes, launch as another user, but when the script is launched not in GUI session or/and as root. Launch by Cron or Systemd timer are not a GUI sessions.


you might find some of this useful: [https://gist.github.com/kasunbg/5502cb630429819d07b5dc0cfa26813c](https://gist.github.com/kasunbg/5502cb630429819d07b5dc0cfa26813c)

---

### Post by and-account on 2022-04-11
> **The Cog said:**
> I think that in addition to setting DISPLAY (which I think is always :0), you can only run gui apps as the user that currently owns the display.
Try this (as root):
```

username=$(w | awk '$3==":0"{print $1}')
sudo -u $username DISPLAY=:0 xeyes
```

[FONT=courier new]'w'[/FONT] version is from procps-ng 3.3.17 in Jammy 22.04 and do not provide DISPLAY in third column. I see 'tty2' (it's the tty where GUI is running) in column 'From' instead of DISPLAY. It may allow to distinguish GUI and SSH sessions for a user.

Why DISPLAY expected to be always :0? I do not know exactly how it is evaluated during start. Looking for it too.

Ocasionally :0 may be changed. AFAI notice it may occur in case of GUI reload or in case of errors.

---

