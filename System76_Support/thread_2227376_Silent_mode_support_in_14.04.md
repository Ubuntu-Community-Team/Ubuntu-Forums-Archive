---
title: "Silent mode support in 14.04"
date: 2014-06-01
forum: System76 Support
---

### Post by belandil on 2014-06-01
My Pangolin Performance has a "Silent Mode" key in the upper left (it's an "M" with a circle [[Reference]("http://ubuntuforums.org/showthread.php?t=1019182") ]). When pressed, it turns down the fan speed, which greatly increases my sanity.  It worked for years when I was using an older version of Ubuntu with the System76 driver, but now that I've upgraded to 14.04, it no longer functions.  

In /var/log/syslog, I get the following error each time I press the button:
```

Jun  1 13:31:07 europa kernel: [12794.422739] atkbd serio0: Unknown key pressed (translated set 2, code 0x81 on isa0060/serio0).
Jun  1 13:31:07 europa kernel: [12794.422749] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
Jun  1 13:31:07 europa kernel: [12794.622845] atkbd serio0: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).

```

Any ideas how to get it to work?  I have the System76 driver installed.

Edit: It appears that silent mode is supported properly.  I have no other way of verifying this other than pressing the button and noticing a change.  The fan may not always change speed depending on the ambient temperature.

---

