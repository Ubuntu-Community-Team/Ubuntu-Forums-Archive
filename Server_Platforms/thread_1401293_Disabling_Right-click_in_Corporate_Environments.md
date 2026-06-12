---
title: "Disabling Right-click in Corporate Environments"
date: 2010-02-07
forum: Server Platforms
---

### Post by nobrac on 2010-02-07
I've come across a lot questions about how to disable right-clicking on the desktop in corporate environments, but no answers. I found a simple method to enable/disable right-clicking using xmodmap: 

```

#!/bin/bash

case $1 in
  off)
    /usr/bin/xmodmap -e "pointer = default"
    /usr/bin/xmodmap -e "keycode 117 = Menu"
  ;;
  *)
    /usr/bin/xmodmap -e "pointer = 1 2 32 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 3"
    /usr/bin/xmodmap -e "keycode 117 ="
  ;;
esac

```

Save the script as /usr/local/bin/mouse_map (or whatever), then run:
```
sudo chmod 755 /usr/local/bin/mouse_map
```

The xmodmap command requires that all 32 potential mouse buttons be mapped. What the script does is swap mouse button 3 with mouse button 32, which likely does not exist. The script also disables the menu button on en_us keyboards, which by default also brings up the property sheet. Everything else, such as the scroll wheel,  continues to work normally.
 
"mouse_map off" will enable right-click, but "mouse_map" on its own will disable it. We call "mouse_map" from System > Preferences > Startup Applications to disable right-clicking by unpriveleged users when they log in.

I'm posting this because it's not obvious how to disable the right mouse button, and doing so a requirement in many corporate environments.

---

### Post by Sporkman on 2010-02-08
What's the purpose of disabling the right mouse button?

---

### Post by gobbledigook on 2010-02-08
its is useful in corporate environments (work!) where admin's don't want people like me to change settings they shouldn't :)

---

### Post by bluefrog on 2010-02-09
people not able to right click in openoffice (to mention only that one)?
hum, looks like not having a computer in the first place wouldn't hurt that much.

---

### Post by Bachstelze on 2010-02-09
All hail the almighty Menu key!

---

### Post by nobrac on 2010-02-09
> **Bachstelze said:**
> All hail the almighty Menu key!

The script disables the Menu key by mapping the menu key to nothing: /usr/bin/xmodmap -e "keycode 117 ="

---

