---
title: "nvidia drivers unavailable"
date: 2009-04-24
forum: System76 Support
---

### Post by darkknight045 on 2009-04-24
Just installed Jaunty:
I can't install any nvidia drivers on my GazP5; it nothing available for drivers.


Help!

---

### Post by formol on 2009-04-25
anything in the restricted driver?

or you can manually install the one from nVidia

download it
ctrl-alt-f1
log in
stop gnome with : sudo etc/init.d/gdm stop
install the driver : sudo sh ./name_of_the_driver
restart gnome : sudo etc/init.d/gdm start

---

### Post by darkknight045 on 2009-04-25
There was nothing available in the restricted drivers page.  I loaded the live cd, and on there it showed them as a available.

I reinstalled and everything is fine now!

---

