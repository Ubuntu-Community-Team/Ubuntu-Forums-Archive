---
title: "Script: A script to to automatically publish screenshots to your Dropbox-folder"
date: 2010-10-12
forum: The Cafe
---

### Post by erikmy on 2010-10-12
The Script: [http://dl.dropbox.com/u/13096662/ScreenshotAutosave.sh](http://dl.dropbox.com/u/13096662/ScreenshotAutosave.sh)
 
What it does:
 
-Installs Scrot: [http://www.freesoftwaremagazine.com/columns/how_to_take_screenshots_with_scrot](http://www.freesoftwaremagazine.com/columns/how_to_take_screenshots_with_scrot)
 
-Change the gconf entry to save screenshots in the public Dropbox-folder.
 
 
NB! The screenshot will get saved in the Dropbox default public-path: <user>/Dropbox/Public
If this folder does not exist or is located elsewhere, you should change the script to fit your needs.
 
```

#!/bin/sh
sudo aptitude install scrot
key_value=$(gconftool --get /apps/metacity/keybinding_commands/command_screenshot)
gconftool --type String --set /apps/metacity/keybinding_commands/command_screenshot "scrot 'screenshot-%s.png' -e 'mv $f ~/Dropbox/Public'"

```

---

### Post by Ericyue on 2012-04-20
hi , 

i want to ask that is there possible to use scrot on the windows 7 ? 

thanks in advance for the reply

---

### Post by vbabaev on 2012-09-11
Wow! That is very usefull. Thank you.

Instead of "mv" command I use full path in scrot command:

```
gconftool --type String --set /apps/metacity/keybinding_commands/command_screenshot "scrot '~/Dropbox/Public/Scrot/screenshot-%s.png'"
```

But, I have one issue. How can I make and share to dropbox a screenshot of the current window. I have no idea, yet. :(

---

### Post by HermanAB on 2012-09-11
You can also use 'motion' and point it at your Dropbox folder, if you want to capture activity in front of your machine.

---

