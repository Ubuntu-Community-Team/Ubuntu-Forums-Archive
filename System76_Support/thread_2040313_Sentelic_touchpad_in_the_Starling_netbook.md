---
title: "Sentelic touchpad in the Starling netbook"
date: 2012-08-10
forum: System76 Support
---

### Post by fredsea on 2012-08-10
Even if it is discontinued, I love the Starling, as it does everything I can do on any of my other computers. One annoying feature, though, is the tendency of the touchpad to record phantom clicks that send the cursor all over the place without warning. It's not the first touchpad where I had this issue, but in this case it's put of control - and, no, I am not touching the touchpad at all (in fact, I am usually typing) when this happens.

The solution is to call up the Sentelic utility ad disable the touch feature. Unfortunately, I have to do it again every time, and I don't see where I could make this change permanent, nor could I locate a configuration file to edit to this effect.

Does anybody have a suggestion? Thanks!!

---

### Post by Dave_L on 2012-08-12
I wrote the following script to enable/disable the touch pad. I use it on a Star3 running Ubuntu 10.04.

If you save the script as ~/touchpad, and make it executable, use the command "~/touchpad 0" to disable the touchpad, or "~/touchpad 1" to enable it.

It could probably be set up as a login script, but I haven't tried that.

```
#!/bin/bash

# Usage:
#   touchpad 1 - Enable touchpad.
#   touchpad 0 - Disable touchpad.

# Identification string for touchpad device.
TOUCHPADSTRING='Sentelic FingerSensingPad'

# sed pattern string
#   .*          - any text
#   \x9         - tab character
#   id=         - literal
#   \(          - begin capture
#   [0-9][0-9]* - one or more decimal digits
#   \)          - end capture
#   \x9         - tab character
#   .*          - any text
# sed replacement string
#   \1          - string captured in pattern
TOUCHPADDEVICE=$(xinput --list | grep -i "$TOUCHPADSTRING" | sed 's/.*\x9id=\([0-9][0-9]*\)\x9.*/\1/')

if [ -n "$TOUCHPADDEVICE" ]; then
	echo The touchpad device is "$TOUCHPADDEVICE".

	if [ "$1" == '1' ]; then
		echo Enabling touchpad...
		xinput --set-prop "$TOUCHPADDEVICE" 'Device Enabled' 1
	elif [ "$1" == '0' ]; then
		echo Disabling touchpad...
		xinput --set-prop "$TOUCHPADDEVICE" 'Device Enabled' 0
	else
		echo No action performed.
	fi

else
	echo No touchpad device found.
fi


```

---

### Post by fredsea on 2012-08-12
> **Dave_L said:**
> I wrote the following script to enable/disable the touch pad. I use it on a Star3 running Ubuntu 10.04.

If you save the script as ~/touchpad, and make it executable, use the command "~/touchpad 0" to disable the touchpad, or "~/touchpad 1" to enable it.

It could probably be set up as a login script, but I haven't tried that.

```
#!/bin/bash

# sed pattern string
#   .*          - any text
#   \x9         - tab character
#   id=         - literal
#   \(          - begin capture
#   [0-9][0-9]* - one or more decimal digits
#   \)          - end capture
#   \x9         - tab character
#   .*          - any text
# sed replacement string
#   \1          - string captured in pattern
TOUCHPADDEVICE=$(xinput --list | grep -i 'Sentelic FingerSensingPad' | sed 's/.*\x9id=\([0-9][0-9]*\)\x9.*/\1/')

if [ -n "$TOUCHPADDEVICE" ]; then
	echo The touchpad device is "$TOUCHPADDEVICE".

	if [ "$1" == '1' ]; then
		echo Enabling touchpad...
		xinput --set-prop "$TOUCHPADDEVICE" 'Device Enabled' "$1"
	elif [ "$1" == '0' ]; then
		echo Disabling touchpad...
		xinput --set-prop "$TOUCHPADDEVICE" 'Device Enabled' "$1"
	else
		echo No action performed.
	fi

else
	echo No touchpad device found.
fi
```
Thanks! It does not seem to work on my 12.04 installation (no output, and no change in the touchpad status, but no error message either). I guess I'll have to dig into the sed code (not my specialty, but you're never too old to learn, I suppose), but any hint on the way the touchpad is recognized would be very helpful.

---

### Post by Dave_L on 2012-08-12
Try looking at the output from:

```
xinput --list
```

Mine contains this line, which might differ from yours:

> &#9116;   &#8627; FSPPS/2 Sentelic FingerSensingPad       	id=14	[slave  pointer  (2)]


If that doesn't provide the explanation, running the script with debugging options enabled may help:

```
sh -vx ~/touchpad 0
```

---

### Post by Dave_L on 2012-08-13
> **Dave_L said:**
> ```
sh -vx ~/touchpad 0
```

Oops, that should be:

```
bash -vx ~/touchpad 0
```

("sh" uses the default shell, which on my system is dash, which doesn't support some of the script's code.)

---

### Post by isantop on 2012-08-13
We do also have a toggle key built-in. You can turn the touchpad off by hitting Fn+F1. Then, when you need it again, hit it again to toggle it back on.

---

