---
title: "Can Someone Help Me With This Script?"
date: 2010-05-23
forum: The Cafe
---

### Post by southzeztpdot on 2010-05-23
Basically im trying to have a script where I can right click a file and have it used as the input for an already prewritten script. 

The command im using in the script to open the other script is "./boxblaze.sh --no-gui  /full/path/to/game.iso". After the --no-gui i assume the place holder for the selected file would go but I dont know what that place holder would be. I can get the script to open with the gui but I would rather have it do it with the no gui method. Can anyone help?

---

### Post by BoneKracker on 2010-05-23
Are you talking about nautilus action scripts?

I think you need to read the nautilus documentation.  I think you would refer to it by some variable exported by nautilus; something like

$PWD/$NAUTILUS_SCRIPT_SELECTED_URIS

Also, in your command, you probably ought to include the path to your shell script and not assume it to be "./", unless every file you intend to use it on happens to be in the same directory

/usr/local/bin/boxblaze.sh --no-gui '$PWD/$NAUTILUS_SCRIPT_SELECTED_URIS'

Disclaimer: I don't know what I'm talking about, because I don't use it.  Seek out the documentation.

---

### Post by xzero1 on 2010-05-23
Place your script in ~/.gnome2/nautilus-scripts. Make it executable and use $1 for your parameter. 

example: mplayer.sh

```
#!/bin/bash

mplayer -vo gl alsa:device=spdif -ac hwdts,hwac3,a52,mad -fs $1
```

---

### Post by BoneKracker on 2010-05-23
Sorry about that.  I guess I was way off on that one.

---

