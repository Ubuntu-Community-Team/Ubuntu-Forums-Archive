---
title: "How to lock the screen with xubuntu live-cd?"
date: 2012-10-25
forum: Security
---

### Post by schulwitz on 2012-10-25
Password protected locking of the screen in Xubuntu fails.  This is an important security feature that seems to be broken in XUbuntu 12.04 Live CD.

When I click: Settings -> Settings Manager -> Keyboard -> Application Shortcuts, I see that <Primary/Ctrl>+<Alt>+<Delete> is automatically configured to trigger the "xflock4" program.  However, neither this key combination nor Ctrl+Alt+L locks the system.  Running "xflock4" from the command line results in the warning:

```
xscreensaver-command: locking not enabled
```


--- Here's the Workaround ---

1. Open the terminal and create a root password by typing:
"sudo passwd root"

2. Next, reinstall xlock:
"sudo apt-get install xlockmore-gl"

3. To activate a blank screensaver:
"sudo xlock -mode blank"
or
To activate the matrix screensaver:
"sudo xlock -mode matrix"

---

