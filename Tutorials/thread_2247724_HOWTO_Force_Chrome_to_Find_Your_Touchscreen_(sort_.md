---
title: "HOWTO: Force Chrome to Find Your Touchscreen (sort of)"
date: 2014-10-09
forum: Tutorials
---

### Post by wd5gnr2 on 2014-10-09
Chrome has problems with touchscreens. Most of these go away if you force the touch device. The only thing that continues not to work is selecting items from a menu (see [https://code.google.com/p/chromium/issues/detail?id=350630](https://code.google.com/p/chromium/issues/detail?id=350630))

However, the script below will help if your touchscreen doesn't always enumerate as the same xinput device. Just change maXTouch to something that uniquely identifies your touchscreen when you enter xinput list at a console prompt.

```
#!/bin/bash
SCREEN=`xinput list | awk '/maXTouch/ { gsub(".*id=",""); print $1 }'`
exec google-chrome-beta --touch-devices=$SCREEN



```

1. Run from a command prompt:
```
xinput list
```
Note the name of your touchscreen (not the ID number which can change)

2. Create file /usr/local/bin/tchrome with your favorite editor and sudo (or create it somewhere on your path)
3. Paste the above in it
4. Change /maXTouch/ to whatever you figured out in step 1. For example, if your screen name is Generic Touchscreen you might use /Touchscreen/. Case counts and it needs to be unique. 
5. Save File
6. Make the file executable 
```
sudo chmod +x /usr/local/bin/tchrome
```
7. Optional: Edit your menu or launchers to make Chrome use the new script (depends on your launcher)

---

