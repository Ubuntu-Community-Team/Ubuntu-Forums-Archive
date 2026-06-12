---
title: "persisted sudo privledges"
date: 2009-03-03
forum: Security
---

### Post by hellz99 on 2009-03-03
When I open Synaptic Package Manager, or open up another app that requires me to enter the sudo pw, and I close the app the sudo still persists.  For instance, I can open the same or other app that requires sudo and it will not prompt me it will just open instead with full rights.

Is there a way to have the sudo privileges terminated as soon as I close the app?

---

### Post by bodhi.zazen on 2009-03-03
you need to configure sudo to do this.

By default there is a 15 minute grace period.

You can either ```
sudo -k
``` or use ```
sudo visudo
``` to edit (configure) your /etc/sudoers file.

See these pages:

[http://www.sudo.ws/sudo/man/sudo.html](http://www.sudo.ws/sudo/man/sudo.html)

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

particularly "**timestamp_timeout"** on the second page.

---

### Post by hellz99 on 2009-03-03
Thanks, this is exactly what I as looking for.
Not sure why it wouldn't be defaulted to 0.

---

### Post by bodhi.zazen on 2009-03-03
No good reason really, convenience as the defaults are probably sufficient for most users.

If someone has physical access a default of 0 really does not buy you much except the time it takes to boot a live CD.

IMO you should either log out, lock the work space, or sudo -k before you leave your machine anyways :twisted:

---

