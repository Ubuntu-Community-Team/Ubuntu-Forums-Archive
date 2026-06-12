---
title: "Update manager-sudo update"
date: 2010-02-27
forum: Security
---

### Post by dogdo on 2010-02-27
Hello

Just got a sudo update from the update manager-does anyone know what this specific update does?

---

### Post by Kevbert on 2010-02-27
Same here. It says that it provides limited superuser privileges to specific users and is a critical update, so just install it. Updated via Synaptic.

---

### Post by -Robert- on 2010-02-27
You can find the update details over here: [http://www.ubuntu.com/usn/USN-905-1](http://www.ubuntu.com/usn/USN-905-1)

---

### Post by OpSecShellshock on 2010-02-27
It's a legitimate update, and is considered critical. Exploitation of the vulnerability seems to require a set of very specific circumstances as well as local access. Essentially, it fixes a problem whereby someone with non-administrative local access could bypass privilege restrictions and execute code that they would ordinarily be restricted from running (but only under certain non-default conditions that there are few reasons to implement). Put another way, the vulnerability is critical, but the risk for most Ubuntu users is zero. Install the update anyway, because it's easy, has been tested, and installing software updates as soon as they are available is a good habit.

---

### Post by Bachstelze on 2010-02-27
And just for the lulz, this is [still not fixed in Debian](http://packages.debian.org/changelogs/pool/main/s/sudo/sudo_1.6.9p17-2/changelog). Who said Debian was the alpha and omega of security?

---

