---
title: "Maximus Manager"
date: 2010-05-15
forum: Ubuntu Moblin Remix
---

### Post by ichneumon on 2010-05-15
I put together the following script to easily manage the list of windows that do not get auto-maximized by Maximus. It requires wmctrl to be installed.

```

#!/bin/bash

# utility for managing fullscreen apps in maximus
# detect foreground window, and toggle maximized/unmaximized, along with the maximus config for it

EXCLUDE=( Tilda )

PID=$$

# make sure wmctrl is installed
if [ ! `which wmctrl` ]; then
   echo "wmctrl not installed" >&2
   exit 1
fi

# check if previous instance already running
ps ax | grep $0 | grep -v grep | grep -v ^[\ ]*$PID > /dev/null
if [ $? == "0" ]; then
   echo $0 is already running
   exit 1
fi

# get active window class
ACTIVE=`xprop -root | awk '/_NET_ACTIVE_WINDOW\(WINDOW\)/{print $NF}'`
CLASS=`xprop -id $ACTIVE | grep WM_CLASS | sed 's/WM_CLASS(STRING) = ".*", "\([^"]*\)".*/\1/'`

# check if in exclude list
for i in ${EXCLUDE[@]}; do
   if [[ $i == $CLASS ]]; then
       echo "Window on exclude list"
       exit 0
   fi
done

# toggle the window state
wmctrl -i -r $ACTIVE -b toggle,maximized_vert,maximized_horz

# get current maximus exclusion list
CONF=(`gconftool-2 -g /apps/maximus/exclude_class | tr -d "[]" | tr ',' ' '`)
echo $CONF
NEWCONF=""
for i in ${CONF[@]}; do
   if [ $i != $CLASS ]; then
      NEWCONF=$NEWCONF$i,
   fi
done
NEWCONF=${NEWCONF:0:$((${#NEWCONF} - 1))}

# add current window if necessary
xprop -id $ACTIVE | grep MAXIMIZED > /dev/null
if [ $? != "0" ]; then # add to exclusion list
   NEWCONF=$NEWCONF,$CLASS
fi

# update gconf
gconftool-2 -s --type list --list-type=string /apps/maximus/exclude_class [$NEWCONF]

```To use, save a copy of the script somewhere sensible (I keep it in ~/bin/maximanage), and chmod it to +x. Next, add a keyboard shortcut via System/Keyboard Shortcuts (I use ctrl-F11). Then, when a program that should not be maximized starts up fullscreen, hit the shortcut to un-maximize and add it to the Maximus exclusion list. Using the same shortcut again will toggle the maximized state and remove that program from the exclusion list (ie. Maximus will start the program maximized).

If you run the script from a terminal window, it will simply apply itself to Gnome-Terminal, as it operates on the currently active window.

There is one caveat; I have assumed that both spaces and commas are forbidden in values for Gnome's WM_CLASS. If this is not the case, can somebody let me know, and I'll rethink those bits of code.

I'm open to any other improvements and/or criticisms code, or let me know if it works for you!

---

### Post by ichneumon on 2010-05-15
Oops... I hadn't taken account of the leading spaces in the ps result. Code is now corrected, and should work all the time now!

---

### Post by espee838 on 2010-05-16
Awesome....this works for me!  it's a lot easier than manually adding things to the exclusions list.

---

### Post by kernst on 2011-01-27
> **ichneumon said:**
> There is one caveat; I have assumed that both spaces and commas are forbidden in values for Gnome's WM_CLASS. If this is not the case, can somebody let me know, and I'll rethink those bits of code.

I'm open to any other improvements and/or criticisms code, or let me know if it works for you!

I ran into a Mono application (KeePass 2.x) which doesn't provide a CLASS. Maybe all Mono apps don't, I dunno.

Attempting to use [FONT="Courier New"]maximanage[/FONT] on its windows eventually caused maximus' "exclude_class" key to get messed up somehow, which either gconfd or maximus responded to by clearing it entirely. I didn't watch what was happening in gconf-editor as I was doing it, I just fixed the script to ignore windows with no WM_CLASS (and notify you as to why nothing happened):

```
# Add these lines right after "CLASS=`xprop -id $ACTIVE [...]"

# Quit if CLASS comes back empty (this happens with [some?] Mono apps, such
# as KeePass 2.x):
if [[ "z$CLASS" == "z" ]]; then
    echo "Window returned no CLASS. Quitting."
    # Try different forms of notification in order of preference:
    TITLE="maximanage message"
    MESSAGE="Selected window provides no CLASS, ignoring."
    if [ -x /usr/bin/notify-send ]; then
        # notify-send currently ignores "--expire-time" but maybe some day
        # it won't:
        notify-send --urgency=low --icon=dialog-warning --expire-time=1500 \
                    "$TITLE" "$MESSAGE"
    elif [ -x /usr/bin/zenity ]; then
        zenity --warning --text="$MESSAGE" --title="$TITLE"
    elif [ -x /usr/bin/xmessage ]; then
        # xmessage, ugh:
        xmessage -center -timeout 5 "$TITLE:

$MESSAGE"
    fi
    exit 1
fi

```

Hope this helps somebody. I've been dutifully referring other "maximus is great but I wish it could..." threads to this one, because I as well found maximus practically intolerable for use with most applications before discovering this method/script. So thanks!

If only its window exclusion capabilities were more fine-grained, down to the window name/role, like [Openbox is capable of]("http://openbox.org/wiki/Help:Applications"). Maybe it's in the code but just not documented anywhere...

---

### Post by directhex on 2011-01-27
> **kernst said:**
> I ran into a Mono application (KeePass 2.x) which doesn't provide a CLASS. Maybe all Mono apps don't, I dunno

WinForms apps don't (you might consider it a bug worth filing on the Mono bug tracker). GTK# apps do.

---

