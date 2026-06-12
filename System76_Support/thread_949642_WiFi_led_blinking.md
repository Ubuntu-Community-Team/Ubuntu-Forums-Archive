---
title: "WiFi led blinking?"
date: 2008-10-16
forum: System76 Support
---

### Post by Sean-Michael on 2008-10-16
Recently my wifi led light started blinking from the darker orange to the light pinkish color.  I though it wa related to internet usage but seems to do it at random times?  Here's what I got...

> Serval Performance(System76), GeForce 8600M GT 512 MB, AMD64 Ubuntu 8.04, Core 2 Duo T7700 2.4 GHz,

This normal?  Anything for me to worry about?

BTW I love my system76, very good investment!

---

### Post by thomasaaron on 2008-10-16
My shop Serval will be back in the office in a few days, and I'll run some tests.

Does it affect your connectivity at all?
Did it occur after running some updates?

---

### Post by MorphWVUtuba on 2008-10-16
Hey, I started getting this symptom too, right after the most recent kernel upgrade.  This only seems to happen when I'm connected to a wireless network, as right now I am not and I do not have the blinking wifi LED.  Here's what my kernel is:

```
2.6.24-21-generic
```

Let me know what you'd like me to run to help troubleshoot.

---

### Post by darkknight045 on 2008-10-16
My GazP5 is also doing this, I think its the blue tooth functionality...

It doesn't appear to be doing anything noticeable but its strange.

---

### Post by MorphWVUtuba on 2008-10-16
> **darkknight045 said:**
> My GazP5 is also doing this, I think its the blue tooth functionality...

If yours is the bluetooth, then mine has a completely different issue because I have no bluetooth.

I don't have any blueteeth either, thankfully.:biggrin:

---

### Post by thomasaaron on 2008-10-16
I'm getting it on my GazV5. 

I checked, and it definitely came down with the *-21 kernel.
It happens on Carl's DarU1 too, and he is running Intrepid.

I guess it's a bug (or new functionality? -not-).

---

### Post by EtherBunny on 2008-10-16
Mine's blinking too. The wifi works fine, but the LED flashes on and off 3 times every 5-10 seconds. I've got an intel 3945 card. It doesn't seem to affect the function but it's really annoying.

---

### Post by perce on 2008-10-16
I have the impression the wireless led now behaves how it used to behave with the old proprietary driver ipw, so I guess it's a feature and not a bug. Of course not a very useful one...

---

### Post by thomasaaron on 2008-10-17
I think you hit the nail on the head.
Interestingly, mine *mostly* seems to blink when it is communicating with the router in some way. Once I'm connected, it will *eventually* stop blinking for a while and then start back up at random intervals.

As far as I can tell, there is no functionality penalties, so I'm gonna let this one go for now.

If it gets to be too much for anyone, please file a bug report against Ubuntu or Network Manager. Other than contribute to such a bug report, I don't think it is anything that System76 can *fix* (if it even needs fixing).

---

### Post by Sean-Michael on 2008-10-21
Well, so long as nothing is broke I guess ;)

Is annoying not knowing what the signal is supposed to signify but with enough time I guess I'll get a feel for what it's signaling'

Keep Cool'
Sean-Michael.

---

### Post by rumblered on 2008-10-22
It just blinks to indicate network activity.

---

### Post by Quirinius on 2009-02-18
Yah, we know. But I think that everyone should make that decision for him/her self and should not be decided by the whole Ubuntu community.

This problem occured after the last update from 1 or 2 weeks ago, now the question is, how can I disable the blinking? I have found a couple of solutions, but after every reboot or connection to anther network, the blinking starts again.

This reason for me, was to remove Fedora from my laptop and reinstall it with Ubuntu because of the drivers support. Know I will looking for another distribution again if I fail to solve this.

---

### Post by rumblered on 2009-02-18
The LED is 100% software controllable. You can even switch it off and have it come on for certain events, like receiving a message in Pidgin. I'll post directions when I have time later today or tomorrow.

---

### Post by Sean-Michael on 2009-02-18
Very nice, and thank you for offering to share!  The extra options will be nice for when the lids closed.

Sean-Michael.

---

### Post by rumblered on 2009-02-20
OK, all drivers that provide LED control in the standard way provide devices in /sys/class/leds. I took some time to figure out how to get udev to set these up automatically.

Create the file /etc/udev/rules.d/90-led.rules and put the following in it:
```

SUBSYSTEM=="leds", ATTR{trigger}="none", PROGRAM+="/bin/sh -c 'chmod a+rw /sys/$DEVPATH/trigger /sys/$DEVPATH/brightness'"
SUBSYSTEM=="leds", KERNEL=="iwl-phy0:radio", PROGRAM+="/bin/sh -c 'sleep 0.5 && echo 0 > /sys/$DEVPATH/brightness'"

```

The first rule turns off blinking in response to any events and gives access to the leds without requiring sudo. The second rule shuts the led off. I had to put a delay in because something else seems to want to turn the led on and was getting the last word otherwise.

If you look in /sys/class/leds, you may notice the wifi hardware supplies four led devices. I guess some systems might have separate leds to indicate wifi being enabled, association with an access point, receiving, and transmitting status. But on my laptop (gazv5) and probably most others, they're all mapped to the same physical led. Just write to the 'brightness' file to make something happen. Whichever device you set last takes effect, and some make the led do different things. Radio turns it on and off completely, and RX or TX can make it blink at different rates.

For easy custom control of the led, create /usr/local/bin/led:
```

#!/bin/bash

DEVICE=/sys/class/leds/iwl-phy0
case "$1" in
  on)
        echo 255 > $DEVICE:radio/brightness
        ;;
  off)
        echo 0 > $DEVICE:radio/brightness
        ;;
  blink)
        echo 50 > $DEVICE:TX/brightness
        ;;
esac
```

Then make it executable. Now 'led on|off|blink' will set the led accordingly, and you can have scripts trigger that. Now, in Pidgin, I don't use sound notification, so my solution to make it trigger the led was to just set the sound notification method in the preferences to "command" and have Pidgin run 'led on' or 'led blink'. Then just enable sound notifications for any event you want to have trigger the led.

Then, you want something to turn off the led. A quick-and-dirty solution is to put a custom application launcher on the panel that runs 'led off', which you can click to switch off the light. Ideally, support should be added to pidgin-blinklight to make this automatic.

A final note, my laptop quite illogically has a *blue* led for wifi and a *red* led for *Blue*tooth. They're in the same place and when both are lit, it looks purple. Only the wifi led is software-controllable, as far as I know. So the Bluetooth led will still blink if you have Bluetooth and it's actively being used.

---

### Post by Quirinius on 2009-02-22
Looks great!

I will have a look at it in the next couple of days and see if I can fix this on my own laptop.

---

