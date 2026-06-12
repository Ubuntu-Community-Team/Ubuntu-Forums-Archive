---
title: "HOWTO make your own status indicator"
date: 2011-08-14
forum: Tutorials
---

### Post by unclouded on 2011-08-14
This example is an indicator that shows the discharge ( or charge) rate of the battery in a laptop, so it's easy to see the effect of switching off the wireless, bluetooth or the nVidia card:

```

#!/usr/bin/env python

import gtk
import gobject
import appindicator


BATTERY_STATE_FILE = "/proc/acpi/battery/BAT1/state"


def rate():
  """
  Provides the discharge ( or charge) rate of the battery.
  """
  f = file( BATTERY_STATE_FILE)
  rate = -1
  for line in f.readlines():
    if line.startswith("present rate:"):
      rate = line.split()[2]
  f.close()
  return int( rate)


i = appindicator.Indicator("Battery rate indicator","battery",appindicator.CATEGORY_APPLICATION_STATUS)
i.set_menu( gtk.Menu()) # the indicator is not visible without this
i.set_status( appindicator.STATUS_ACTIVE)

def tick():
  i.set_label( str(rate() / 1000)+ "W")
  return True  # so this timeout is scheduled again

gobject.timeout_add( 1000, tick)
gtk.main()

```

The above is a working program that demonstrates how straightforward it is to add your own status indicator.

---

