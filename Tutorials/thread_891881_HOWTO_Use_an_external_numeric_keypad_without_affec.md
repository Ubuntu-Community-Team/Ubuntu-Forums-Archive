---
title: "HOWTO: Use an external numeric keypad without affecting the NumLock of your notebook"
date: 2008-08-16
forum: Tutorials
---

### Post by hyperair on 2008-08-16
**Intro**
One thing I've noticed with some external numeric keypads is that the NumLock on the numeric keypad toggles the numeric keypad of your notebook, and hence enables the notebook's inbuilt numberpad and disabling the letters it occupies [u,i,o,p,j,k,l,m, /, and )]. 

With a little tinkering using xmodmap, I found a way to invert the NumLock status. Hence, the NumLock is officially off, as in your LED is off, but your keys respond as if NumLock is on.

**Begin!**
1. Open the text editor and paste this code in:
```

#!/bin/bash

WORKAROUND=0
function workaround() {
    if [ $WORKAROUND -eq 0 ]; then
        WORKAROUND=1
        echo "workaround"
        xmodmap $HOME/.numpad-daemon/workaround
    fi
}

function reset() {
    if [ $WORKAROUND -eq 1 ]; then
        WORKAROUND=0
        echo "reset"
        xmodmap $HOME/.numpad-daemon/original
    fi
}

function setup() {
    mkdir -p $HOME/.numpad-daemon
    if [ ! -f $HOME/.numpad-daemon/usbid ]; then
        SETUP=1
        rm -rf /tmp/numpad-daemon-*
        echo "Please remove your numeric keypad (if present), then press Enter: "
        read -e
        lsusb > /tmp/numpad-daemon-$$-lsusb-orig
        echo "Please plug in your numeric keypad, then press Enter: "
        read -e
        sleep 1
        lsusb > /tmp/numpad-daemon-$$-lsusb-new
        USBID=`diff /tmp/numpad-daemon-$$-lsusb-{orig,new} | egrep '>'  | sed -re 's|^.*ID ([0-9a-f]{4}:[0-9a-f]{4})(.*)|\1|'`
        echo $USBID > $HOME/.numpad-daemon/usbid
    else
        USBID=`cat $HOME/.numpad-daemon/usbid`
    fi
    if [ ! -f $HOME/.numpad-daemon/original ]; then
        SETUP=1
        xmodmap -pke | egrep 'KP_[0-9]' | sed -re 's|= (KP_[0-9]*) (KP_[^ ]*)|= \2 \1|' > $HOME/.numpad-daemon/original
    fi
    if [ ! -f $HOME/.numpad-daemon/workaround ]; then
        SETUP=1
        sed -re 's|= (KP_[^ ]*) (KP_[0-9])|= \2 \1|' $HOME/.numpad-daemon/original > $HOME/.numpad-daemon/workaround
    fi
}
function run() {
    while [ 1 ]; do
        if [ "`lsusb | grep $USBID`" ]; then
            workaround;
        else
            reset;
        fi
        sleep 1s
    done
}
DAEMONIZE=0
for arg in $@; do
    case $arg in
        -d|--daemonize)
            DAEMONIZE=1
        ;;
        -k|--kill)
            killall `basename $0`
            exit
        ;;
        -r|--reset)
            rm -rf ~/.numpad-daemon
            exit
        ;;
    esac
done
setup;
if [ $DAEMONIZE -eq 1 ]; then
    run &
else
    run
fi

```
2. Save it to /home/<your username here>/bin/numpad-daemon
3. Give it execute permissions:
```

chmod +x $HOME/bin/numpad-daemon

```
4. Run it.
```

$HOME/bin/numpad-daemon

```
4.1 When asked to remove your numeric keypad, remove it, then press enter.
4.2 When asked to plug in your numeric keypad, plug it in, then press enter.
5. Close it (Ctrl+C)
6. Start it from the run dialog by pasting "/home/<your username here>/bin/numpad-daemon" in the run dialog and pressing enter.
7. Start it upon login (optional)
7.1 Go to System->Preferences->Sessions.
7.2 Click the Add button.
7.3 For Name, put "Numberpad Daemon"; For Command, put "/home/<your username here>/bin/numberpad-daemon";

**More options**
Like this: /home/<your username here>/bin/numpad-daemon <option>
-k: kill all instances of numpad-daemon
-r: remove ~/.numpad-daemon (reset all options)
-d: daemonize (fork to background)

**Stuff that doesn't work**
1. If you don't follow the instructions during the setup procedure, all subsequent attempts to use it will produce unpredictable results.
2. During the setup procedure do NOT plug or unplug any other USB devices. This script cannot detect the correct USB ID otherwise.

---

### Post by GNUbee40 on 2010-05-08
Hey! 

I have the problem you mention!

However, your script does not seem to work. 
Is there any way to test what is going wrong?

Regards

---

### Post by hyperair on 2010-05-09
For now, could you describe exactly how you attempted to use the script (terminal output might be nice), what went wrong, and upload a tarball of all the files in ~/.numpad-daemon?

EDIT: I actually just made an edit to switch "elsed:" to "else". I think that might have caused issues. Could you use the new script and see if that works for you?

---

### Post by GNUbee40 on 2010-05-09
Hi again!

Thanks for the awesome script!

I guess it was just the typo screwing everything up.
Before when I started numpad-daemon, it probably did not daemonize and just terminated. I wondered why I never had to use Ctrl-C :)

Now the script works as intended - with one exception: The "." / Del key on the number keypad works as a Del key unless I press numlock - but then the number keys work as navigator keys :)
I guess I have to switch something around... Or maybe I just need to add a line so this key also gets inverted like the rest.

Also pressing Numlock now turns the internal numerical keypad into navigator keys. But I never wanted to use the internal numerical keypad anyway (obviously).

If you can provide some tips how to map this one key right it'd be great. But I am thankful already. 
Linux is so much fun
Cheers
:guitar:

---

### Post by GNUbee40 on 2010-05-09
78,56

Written with my numerical keypad (turned out to be a Belkin) :popcorn:

Adding the , map was easy as pie.

Used xev to identify the key (nr 91 by the way)
then 
```
xmodmap -pke | grep 91
``` 
to find the appropiate mapping
In my case
```
keycode  91 = KP_Delete KP_Separator KP_Delete KP_Separator KP_Delete KP_Separator
```
Then append the line to file named "original" in ~./numpad-daemon 
(don't know it this is necessary)
Append the line to file "workaround" and reverse the first two arguments after "keycode 91 =".
In my case:
```
keycode  91 = KP_Separator KP_Delete KP_Delete KP_Separator KP_Delete KP_Separator
```
Save both files and type "numpad-daemon" again at any prompt.
Done :guitar:

---

### Post by hyperair on 2010-05-09
Cool stuff. Glad it helped someone, even after I stopped using it. =)

---

### Post by shouume on 2012-01-05
This worked for me on my Sony Vaio VPCCW21FX with Targus external key number pad. I have Oneiric Ocelot 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux. ```
System Settings > Keyboard Layout > Options (button in lower right-hand corner) > Misc. compatibility options > Numeric keypad keys work as with Macintosh (check box)
```
"Close"

---

### Post by hyperair on 2012-01-06
Weird. I tried it out and my laptop's keyboard's numlock went berserk when I enabled numlock on the external numpad. It was as if numlock was on for the laptop (laptop numlock LED was on, and [uiojklm.] keys didn't output the alphabets they were meant to), but off at the same time -- instead of generating the keycodes for numberpad numbers, they generated the keycodes for KP_{Home,Up,Prior,...} instead.

---

### Post by Neil Woolford on 2012-05-17
> **shouume said:**
> This worked for me on my Sony Vaio VPCCW21FX with Targus external key number pad. I have Oneiric Ocelot 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux. ```
System Settings > Keyboard Layout > Options (button in lower right-hand corner) > Misc. compatibility options > Numeric keypad keys work as with Macintosh (check box)
```
"Close"

That worked fine for me using a generic Taiwanese external flexible keypad, Teppaz 446062.  I'm running 12.04 64 bit on a laptop.

Now if I could just get an equals key onto the keypad, that would really ease my spreadsheet work.

---

