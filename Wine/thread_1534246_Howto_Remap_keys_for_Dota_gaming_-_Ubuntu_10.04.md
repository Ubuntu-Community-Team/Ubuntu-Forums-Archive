---
title: "Howto Remap keys for Dota gaming - Ubuntu 10.04"
date: 2010-07-19
forum: Wine
---

### Post by misse- on 2010-07-19
Hi all,

As a longtime Ubuntu user and Dota player I'd like to share some of my solutions to make Dota more playable under Ubuntu, mainly by binding mouse & keyboard-keys to the inventory so that active items like Kelens, lothars are easier to use in intense situations.

First off: if you want the best solution for running Warcraft III under wine I suggest this guide: [http://shae.me/linux/warcraft-3-wine-and-ubuntu-9-10/](http://shae.me/linux/warcraft-3-wine-and-ubuntu-9-10/), which will give you a patched wine version which will make your Warcraft 3 experience more pleasant.

Also have a look at: [http://drjones.dk/customkeys/generator.php](http://drjones.dk/customkeys/generator.php) which helps you create a customkeys.txt so that you can use whatever keys you want as spell hotkeys.

Now, let's get going:

[SIZE="3"]Imwheel[/SIZE]

Imwheel is a tool to remap mousebuttons to keyboard buttons or combinations. It is started with "imwheel" and it reads it's settings from your "~/.imwheelrc" file.

I've attached my own file and as you can see, it's pretty straight forward.

```

"^Warcraft III" 
None,Thumb1,KP_7
None,Thumb2,KP_8

"^Firefox"
None,Thumb1,Alt_L|Left
None,Thumb2,Alt_L|Right
```

The first line matches the window title against itself. If The window title matches "^Warcraft III", the mouse thumb buttons will be remapped as Keypad 7 resp. Keypad 8. If the title matches "^Firefox" however the buttons will be used as forward or back buttons.

To try this out, save the above text (or the attachment below) to ~/.imwheelrc and run imwheel, start Warcraft 3 and get to a text input area, for example > Local Area Network > Player name. Press your thumb buttons and if all should work correctly they will write out 7's and 8's. If not, check that imwheel is running and check your numlock.

[SIZE="3"]
Xmodmap[/SIZE]

To remap keyboard buttons I'd recommend using xmodmap. 

First off, I'd recommend dumping your current xmodmap to a file so that you have a backup, and a reference.

This will dump your current config to .xmod, open that file with your favorite text editor and search for a key which you would like to use in Warcraft 3. In this example we will use the space button. That line looks like this for me:
```
keycode  65 = KP_4 space space space space nobreakspace
```

Let's break this down, the different "space" represents what will be printed if the button is pressed in combination with modifiers like this:

1  only the key
2  shift + key
3  mode_switch + key
4  mode_switch + shift + key
5  AltGr + key
6  AltGr + shift + key

So, if we change the first space into KP_4 by running: 
```
xmodmap -e "keycode  65 = KP_4 space space space space nobreakspace"
``` 
Pressing space will generate a 4. Shift + Space on the other hand will still print a space.

To bring it back to normal, run:
```
xmodmap -e "keycode  65 = space space space space space nobreakspace"
```

Now you could settle for permanently changing the function of space to kp_4, but that would be kind of impractical. You could of course change shift+space into kp_4 instead, but I'd prefer a solution where you can switch from dotakeys to normal keys with just a keyboard shortcut. 

That's why I created the very simple script "dkeys.sh"

```
#!/bin/bash
case $1 in
	start)
	xmodmap -e "keycode  65 = KP_4 space space space space nobreakspace"
	imwheel > /dev/null 2>&1
	echo start > ~/.dkeys.pid
	/usr/bin/mplayer /usr/share/sounds/KDE-Im-Message-Out.ogg > /dev/null 2>&1 &
;;
	stop)
	xmodmap -e "keycode  65 = space space space space space nobreakspace"
	killall imwheel
	rm ~/.dkeys.pid
        /usr/bin/mplayer /usr/share/sounds/KDE-Im-Message-In.ogg > /dev/null 2>&1 &
;;
	*)
	if [ -f ~/.dkeys.pid ];then
	$0 stop
	else
	$0 start
	fi
;;

esac

```

When you run the script without any arguments like start or stop, it will check if the file ~/.dkeys.pid exists. If it does, it will kill imwheel and set your keyboard back to normal. If it doesn't, it will start imwheel and rebind your space button. 

To let you know what the script just did, it will play a sound when activating and a different when deactivating so that you'll be able to recognize when the keys have been rebound.

With the help of compizconfig-settings-manager > Commands I've assigned a key to run dkeys and thus toggle my keys between regular and dota mode.

Hope this helps someone, please let me know if you improve the script or the .imwheelrc or if I should in any other way update this little howto.

---

### Post by DOCvanROCK on 2010-08-06
> **misse- said:**
> 
So, if we change the first space into KP_4 by running: 
```
xmodmap -e "keycode  65 = space space space space space nobreakspace"
```Pressing space will generate a 4. Shift + Space on the other hand will still print a space.


where in this code is the "KP 4" being mentioned? o0

Nice guide tho :p

---

### Post by choreanz on 2010-08-17
I'm curious, how do you rewrite the keys to inventory slots on dota?  I've been trying to mess with xmodmap for a while, and I can't seem to get anything to work.  Also, the customkeys website you provided seems to only work for windows when it comes to inventory slot reallotments.

  __[URL="http://drjones.dk/customkeys/generator.php"]

[/URL]

---

### Post by misse- on 2010-08-20
> **DOCvanROCK said:**
> where in this code is the "KP 4" being mentioned? o0

Nice guide tho :p

Fixed :)

> **choreanz said:**
> I'm curious, how do you rewrite the keys to inventory slots on dota?  I've been trying to mess with xmodmap for a while, and I can't seem to get anything to work.  Also, the customkeys website you provided seems to only work for windows when it comes to inventory slot reallotments.

  __[URL="http://drjones.dk/customkeys/generator.php"]

[/URL]
The link is only intended to allow you to generate a customkeys.txt for your hero abilities.

As I wrote in the first post (albeit, with some typoes :$) the trick is that you can't use custom keys for the Dota inventory, they have to be the numpad/keypad buttons: KP_1, KP_2, KP_4, KP_5, KP_7 & KP_8. 

With xmodmap I change the function of one key to one of those numpad keys. Which button you choose to emulate which keypadbutton is up to you, but let's say you want the space button to activate the mid left inventory slot. Then all you have to use is this line:
```
xmodmap -e "keycode  65 = KP_4 space space space space nobreakspace"
```
And to change it back:
```
xmodmap -e "keycode  65 = space space space space space nobreakspace"
```

---

