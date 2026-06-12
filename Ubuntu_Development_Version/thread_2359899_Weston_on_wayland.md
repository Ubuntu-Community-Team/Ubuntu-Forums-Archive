---
title: "Weston on wayland"
date: 2017-04-29
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-04-29
You can run weston in different ways, directly as the main backend or from within another windowing system.

Running within X
You can run weston from within X by calling weston from a xterm session.

   ```
 weston
```

As with X, you can start a weston instance within another, once again just call weston. The following images shows a stack of Weston running within Weston within Weston within X.


Running without X

Now I run weston as my main backend. From one of system's VT call weston launcher.IE "Ctrl Alt Fx"

   ```
 weston-launch
```

Configure Weston

As you should have seen, you can run weston without any extra configuration, however you can set some things to customize and make it better.

```
weston.ini
```

To configure weston you should create/change the weston.ini file, which is usually at ~/.config/weston.ini. Here i will show some options you could use to do such changes.

The core section is used to select the startup compositor modules and general options.
**Again just an example:**
 ```
 [core]
    backend=drm-backend.so
```

The keyboard section is used to select keyboard options, such as layout and variant.
**This is just an example...do not use.**
 ```
   [keyboard]
    keymap_layout=fr
    keymap_model=pc105
    keymap_variant=euro
    keymap_options=grp:alt_shift_toggle
```
    
At the shell section you will set some of the behaviour and visual aspects of the compositor.

 ```
   [shell]
    type=desktop-shell.so
    background-image=/path/to/wallpaper.jpg
    background-color=0xff002200
    panel-color=0x55550000
    locking=true
    animation=zoom
    binding-modifier=ctrl
    num-workspaces=6 
```


Well, so this is it, Wayland is working and you can run Weston from within X, directly or from within another Weston session. There are already more native clients and also ways to run X applications on top of Wayland. It is time to take a look, play around and maybe even develop your own Wayland clients.
[B]EDIT: Well it seems I can't upload screenshots ATM will add when I can. 
EDIT2: URL to Images:[http://imgur.com/a/LVT2z](http://imgur.com/a/LVT2z)
[/B]```
**[SIZE=3]Forbidden[/SIZE]**

 You don't have permission to access /newattachment.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

```
This may useful How to debug Wayland problems:
[URL="https://fedoraproject.org/wiki/How_to_debug_Wayland_problems"]https://fedoraproject.org/wiki/How_to_debug_Wayland_problems


[/URL]

---

