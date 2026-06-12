---
title: "HOWTO: Easy win + num window switching (aka unity launcher)"
date: 2013-05-12
forum: Tutorials
---

### Post by mreq on 2013-05-12
We'll need **wmctrl** and **xbindkeys** installed, both avaiable from the repositories. Eg:

```
sudo apt-get install wmctrl xbindkeys
```

We'll use a script for switching. Place it somewhere in your home directory (I did so in **~/scripts/bin/switch_to_app**) and make sure it is executable - in my case **chmod +x petr ~/scripts/bin/switch_to_app**.

Here's the script to save there (improvements are welcome :) ). You don't have to understand it to use it ;):

```

#!/bin/bash
app_name=$1
workspace_number=`wmctrl -d | grep '\*' | cut -d' ' -f 1`
win_list=`wmctrl -lx | grep $app_name | grep " $workspace_number " | awk '{print $1}'`


active_win_id=`xprop -root | grep '^_NET_ACTIVE_W' | awk -F'# 0x' '{print $2}' | awk -F', ' '{print $1}'`
if [ "$active_win_id" == "0" ]; then
    active_win_id=""
fi


# get next window to focus on, removing id active
switch_to=`echo $win_list | sed s/.*$active_win_id// | awk '{print $1}'`
# if the current window is the last in the list ... take the first one
if [ "$switch_to" == "" ];then
    switch_to=`echo $win_list | awk '{print $1}'`
fi


if [[ -n "${switch_to}" ]]
    then
        (wmctrl -ia "$switch_to") &
    else
        if [[ -n "$2" ]]
            then
                ($2) &
        fi
fi


exit 0

```

To use the script, you invoke it by it's name and pass window identifier (see **wmctrl -lx**) as the first argument and an optional command as the second argument. If the script doesn't find the window by identifier and a command is present, it executes it.

Aftewards make a **~/.xbindkeysrc** file with defined shortcuts, syntax is easy:

```

"/home/petr/scripts/bin/switch_to_app 'chromium-browser.Chromium-browser' chromium-browser"
    Mod4 + 1


"/home/petr/scripts/bin/switch_to_app 'sublime_text.sublime-text-2' subl"
    Mod4 + 2


"/home/petr/scripts/bin/switch_to_app 'terminator.Terminator' terminator"
    Mod4 + 3

```

Once **xbindkeys** is loaded, fire your shortcuts at will :) If you have multiple windows of an app opened, the script cycles through them. If you modify **.xbindkeysrc** you can restart **xbindkeys** by **killall xbindkeys && xbindkeys**&#8203;.

PS: Script was written for Xubuntu but should work with any DE. In Xubuntu it filters out other workspaces, which doesn't work with Compiz. Am not sure about Metacity.

---

### Post by MG&amp;TL on 2013-05-12
Impressive! I've been trying to get the workspace filtering to work on compiz, but it's not very easy.

If it helps, here's some code I made while trying to make it work. :)

```

#!/bin/bash

wm_name=$(wmctrl -m | grep "^Name:" | awk '{print $2}')

#Compiz, uh-oh.
if [ "$wm_name" == "Compiz" ]; then
    pixel_offset_x=$(xprop -root _NET_DESKTOP_VIEWPORT | tr ',' ' ' | awk '{print $3}')
    pixel_offset_y=$(xprop -root _NET_DESKTOP_VIEWPORT | tr ',' ' ' | awk '{print $4}')
    display_width=$(xdpyinfo | grep "dimensions" | tr 'x' ' ' | awk '{print $2}')
    display_height=$(xdpyinfo | grep "dimensions" | tr 'x' ' ' | awk '{print $3}')
    workspace_x=$((pixel_offset_x/display_width))
    workspace_y=$((pixel_offset_y/display_height))
else
    #Do something intelligent with another WM here.    
fi


```

Don't know if that helps, but workspace_x and workspace_y then contain the x/y co-ordinates of the desktop.

Nice work, anyway. Added to scripts folder. :)

---

