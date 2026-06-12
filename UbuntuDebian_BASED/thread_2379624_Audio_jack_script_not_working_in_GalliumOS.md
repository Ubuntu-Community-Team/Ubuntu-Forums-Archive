---
title: "Audio jack script not working in GalliumOS"
date: 2017-12-07
forum: Ubuntu/Debian BASED
---

### Post by dr4gl0k on 2017-12-07
GalliumOS is an Ubuntu-based OS made specifically for Chromebooks. I'm running it on ASUS C300s BRASWELL.

The audio source does not change from speaker to headphones and vice-versa when headphones are plugged in or removed.
The script location is /etc/acpi/jack.sh. The script is
 ```
#!/bin/sh#
# /etc/acpi/jack.sh
#


event="$*"


headphones_in() {
  #pacmd set-sink-port "alsa_output.platform-cht-bsw-rt5645.HiFi__hw_chtrt5650__sink" "[Out] Headphones"
  /usr/bin/amixer -c 0 cset name='Speaker Channel Switch' off
  /usr/bin/amixer -c 0 cset name='Headphone Channel Switch' on
}


headphones_out() {
  #pacmd set-sink-port "alsa_output.platform-cht-bsw-rt5645.HiFi__hw_chtrt5650__sink" "[Out] Speaker"
  /usr/bin/amixer -c 0 cset name='Headphone Channel Switch' off
  /usr/bin/amixer -c 0 cset name='Speaker Channel Switch' on
}


case "$event" in
  '') ;;
  'jack/headphone HEADPHONE plug')
    logger "jackdetect: handling $event"
    headphones_in
    ;;
  'jack/headphone HEADPHONE unplug')
    logger "jackdetect: handling $event"
    headphones_out
    ;;
  *) logger "jackdetect: ignoring $event" ;;
esac



```

I have tried the command ```
chmod +x /etc/acpi/jack.sh
```
I have tried install acpid.
After this I run ls -l in the acpi directory and my edits to the jack.sh file are not saved.

Any thoughts?

---

### Post by Frogs Hair on 2017-12-07
Moved to *Ubuntu/Debian Based*

---

### Post by dr4gl0k on 2017-12-11
bump

---

### Post by dr4gl0k on 2017-12-12
bump

---

### Post by dr4gl0k on 2017-12-14
bump

---

