---
title: "[GUIDE] GFX passthru club - Auto switch monitor input on guest start/stop"
date: 2016-05-28
forum: Virtualisation
---

### Post by KillerKelvUK on 2016-05-28
Read someone's post a year or so back about using DDC/CI to control the monitor settings from the command line, I've faffed on and off but struggled finding a ddc tool that worked until recently.  So decided to write this guide up as this topic doesn't come up often so thought some might find it useful.

Host:  Ubuntu 16.04 | Intel IGP for host only | GTX 970 for passthrough

**Step #1**

Nabbed the ddctool source from [http://www.ddctool.com/](http://www.ddctool.com/), compiled, added my local user to the i2c group.  Couple of dependencies I needed to work through the **** ache being the libxrandr-dev package but that was only because it was new to me.

```

ddctool detect  <--finds and lists the monitors and confirms capability to control them
ddctool capabilities <--lists out all the monitor functions the tool can read and control.  For me Feature 60: (Input Source) has 3 possible values applicable 0x01, 0x03, 0x11 which are my VGA, DVI and HDMI connectors on the monitor. 
ddctool getvcp 60 <--returns the current value/setting for this feature.  For me this returns "VCP code 0x60 (Input Source                  ): DVI-1 (sl=0x03)" as an example
ddctool setvcp 60 0x11  <--switches my monitor input source to HDMI which is what I have my kvm/qemu guest outputting to via the passthru GTX 970.  I had to specify the end value as 0x11 instead of just 11, the ddctool docs say either is valid however just 11 didn't work for me.
ddctool setvcp 60 0x03  <--returns my monitor input source to DVI which is where my ubuntu host desktop is connected to.  Simples!

```

**Step #2**

So to automate the switching of my monitor based on when I start or stop the guest which has a GFX card passed through I used the Hooks feature of libvirt [https://www.libvirt.org/hooks.html](https://www.libvirt.org/hooks.html)

Essentially libvirt hooks are bash or python scripts that are run automatically by libvirt, I'll let you do the reading up but I also find this ([http://www.fragmentationneeded.net/2014/09/making-better-use-of-libvirt-hooks.html](http://www.fragmentationneeded.net/2014/09/making-better-use-of-libvirt-hooks.html)) article helpful.

```

sudo touch /etc/libvirt/hooks/qemu
sudo chmod u+x /etc/libvirt/hooks/qemu

```

The I added the following bash script into /etc/libvirt/hooks/qemu...

```

#!/bin/bash


GUEST=$1
STATUS=$2
POSITION=$3


case "$GUEST" in
    "name-of-my guest" )
        if [ "$STATUS" = "started" ]; then
                        ddctool setvcp 60 0x11
                elif [ "$STATUS" = "stopped" ]; then
                        ddctool setvcp 60 0x03
                fi
    ;;
esac

```

As libvirt will run the /etc/libvirt/hooks/qemu script multiple times per guest the above will need further customisation to fit your build but essentially all its doing is parsing the parameters libvirt sends into the script when it calls it.

That's pretty much it!
:popcorn:

---

