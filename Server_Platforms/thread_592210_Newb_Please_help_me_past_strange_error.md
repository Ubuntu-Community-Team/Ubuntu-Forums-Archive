---
title: "Newb: Please help me past strange error"
date: 2007-10-26
forum: Server Platforms
---

### Post by Smartin on 2007-10-26
Hi,

I'm trying to install opengroupware from the Debian repo on a Feisty box.

I'm getting:

sudo apt-get install opengroupware.org
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I have no idea what this means or how to get past it.

Can anyone help?

Thanks!

Simon

---

### Post by thelocust on 2007-10-26
Funky, just throwing stuff out there did ya try a reboot.:)
Can you install anything else.

---

### Post by badactress on 2007-10-26
It usually means another process as well as your 'apt-get' is using the debian package manger (dpkg).

If you have Synaptic package manger open & then try to do a 'sudo apt-get install' in the terminal, this is the error that would pop up..

or if you were trying to 'sudo apt-get' in two different terminal windows at the same time..

If none of this applies, then rebooting would be the next step..

Hope this helps :)

---

### Post by Smartin on 2007-10-26
> **thelocust said:**
> Funky, just throwing stuff out there did ya try a reboot.:)
Can you install anything else.

thelocust;3635860,

A reboot was the first thing I tried and the only thing I have done is a system update, not an upgrade to Gutsy though.

Simon

---

### Post by Smartin on 2007-10-26
> **badactress said:**
> It usually means another process as well as your 'apt-get' is using the debian package manger (dpkg).

If you have Synaptic package manger open & then try to do a 'sudo apt-get install' in the terminal, this is the error that would pop up..

or if you were trying to 'sudo apt-get' in two different terminal windows at the same time..

If none of this applies, then rebooting would be the next step..

Hope this helps :)

badactress,

Well done! I had synaptic open at the same time, both before and after the reboot.

Got past the error. Another one to come no doubt... :-)

Thanks!

Simon

---

