---
title: "[SOLVED] Cryptsetup prevents loading of services?"
date: 2007-09-25
forum: Server Platforms
---

### Post by EisenPM on 2007-09-25
Hello, I do not run a server, but encryption issues belong to security, I think, so I post my question here. 

I have my root und my home partitions encrypted with cryptsetup-luks. Everything is fine, except that my DHCP is not working automatically anymore. I have to enter "sudo dhclient eth0" after booting in order to be online. Also privoxy and tor are not loaded anymore and my printer does not print (maybe it's a problem with the turboprint driver, but it worked before).

Before, I had only my home partition encrypted and mounted with pam_mount at gdm log in. Then some services did not work, because the system wanted to read data from my encrypted home partition before it was un-encrypted.

But now I am entering the two passwords before gdm is loading. Still, there's some "booting" going on between entering the two passwords.......

Any ideas?

---

### Post by EisenPM on 2007-09-25
Alright, I purged privoxy, tor und my turboprint drivers and reinstalled them. Now it's working again. the file permissions were changed during copying. 

But the DHCP is still not working. But I cant reinstall the dhclient, right? Hm......

---

### Post by cookfromfrozen on 2007-09-26
dhclient is part of the dhcp3-client package, you should be able to reinstall that.

If that doesn't work, check the /etc/network/interfaces file.  It should look something like this:

```

iface eth0 inet dhcp
auto eth0

```

Note the "dhcp" option, which means the system will automatically run dhclient when bringing the interface up. This option may have been removed for some reason.

---

### Post by EisenPM on 2007-09-26
YES! I reinstalled the pakage and now it works. Thanks a lot! Had nothing to do with /etc/network/interfaces.

---

