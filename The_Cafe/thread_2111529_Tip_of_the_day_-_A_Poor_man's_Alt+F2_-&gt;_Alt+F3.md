---
title: "Tip of the day - A Poor man's Alt+F2 -&gt; Alt+F3"
date: 2013-02-02
forum: The Cafe
---

### Post by MrQuincle on 2013-02-02
If you for any reason, be it security, be it speed, prefer not to use Ubuntu dash, you can create of course your own shortcut.

sudo apt-get install zenity

Store this script under e.g. ~/myscripts/alt_f2.sh
```
#!/bin/bash

program=$(zenity --entry --text "Please, enter program to execute:" --title "Run command... (Alt+F2)")

if [ $? == 0 ]; then
	$program &
fi

```
Test it on the command-line.

Go to:
[LIST]
[*]System Settings -> Keyboard (under Hardware) -> Shortcuts
[*]Custom Shortcuts
[*]The +-box at the bottom.
[/LIST]

Name: "Poor man Alt+F2" or whatever you like, Command: ~/myscripts/alt_f2.sh. Click the thing after you created and assign the Alt+F3 command.

Of course, this is trivial to anyone who has more than a few months experience with Ubuntu. However, maybe you were caught up in other things. I really hate to use the mouse. Just typing "google-chrome" in a box is much quicker for me than navigating the menus or waiting for the Dash. Especially, when it has bugs that applications are not actually started because I don't type slow enough... 

Also very important to me to: Alt+F3 is very close to Alt+F2, so I had to readjust my fine motor skills only slightly. And it's quicker than typing Ctrl+Alt+T, background the processing, and closing the terminal again. :D

Edit: By the way if setting the key shortcut doesn't work because of some quirk of Ubuntu. You can use for example "ccsm" to create this shortcut. Be careful though, "ccsm" can break your system, so don't start fooling around. In General - Commands - Command line 0 you can set the link to the script, and in the tab "Key Bindings" you can set the Alt+F3 key.

---

### Post by urukrama on 2013-02-02
Why not use [gmrun]("http://packages.ubuntu.com/search?keywords=gmrun") instead? It has more features that this script, as you can use its searchable history of commands and it can autocomplete commands (press TAB).

---

