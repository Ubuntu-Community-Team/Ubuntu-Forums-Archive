---
title: "Apache2 Won't start at boot."
date: 2009-08-13
forum: Server Platforms
---

### Post by modmadmike on 2009-08-13
Im running Apache2 but every time I boot I need to run ```
sudo apache2ctl start
``` or ```
sudo /etc/init.d/apache2 start
```. I have webmin installed and it says that apache2 is enabled at boot and so does System>Administration>Services. When running the Apache2 boot script it yields no errors and starts normally. Any help?

---

### Post by alastair on 2009-08-13
> **modmadmike said:**
> When running the Apache2 boot script it yields no errors and starts normally. Any help?

Hard to say. The scripts in /etc/init.d/ are run if configured (linked) for the various "boot" states you can be in (run-levels). These are links in /etc/rc*.d/

Is apache there?

# sudo find /etc/rc*.d -name '*apache*'

If not, add it :

# sudo update-rc.d apache2 defaults

and recheck if it's there now.

See :

man update-rc.d

"update-rc.d - install and remove System-V style init script links"

But apologies if this is a little arcane and non-GUI. Not sure why your install/webmin is acting up.

Maybe that helps? If not ... come back.

---

### Post by modmadmike on 2009-09-14
NVM i fixed it by editing the apache2.conf (it had the root directory set inside my $HOME directory and i forgot that my homefolder is a .gvfs (its an encrypted folder) so it only mounts when i login... baka me lol   I relocated the root directory into /var/www like it was as default and it works on boot again lol.

---

### Post by modmadmike on 2009-09-14
> **modmadmike said:**
> NVM i fixed it by editing the apache2.conf (it had the root directory set inside my $HOME directory and i forgot that my homefolder is a .gvfs (its an encrypted folder) so it only mounts when i login... baka me lol   I relocated the root directory into /var/www like it was as default and it works on boot again lol.

I REALLY need to enable boot logging so i can find these problems... WHY DOES UBUNTU DISABLE THAT GRRRR..... :P

---

