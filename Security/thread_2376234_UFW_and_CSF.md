---
title: "UFW and CSF"
date: 2017-10-31
forum: Security
---

### Post by jmh72 on 2017-10-31
Hi. I recently tried CSF as a firewall, and I couldn't get it to work. So I used uninstall.sh and re-enabled ufw.

Now, every time I reboot, ufw's status is always inactive.

I have no idea what system changes CSF made, and I can not figure out why UFW will not persistently remain on.

Can someone please help me with this, because I'm flying blind without a firewall now.

Thank a lot.

---

### Post by TheFu on 2017-11-01
/etc/ufw/ufw.conf has a setting to enable on boot.

BTW, this is common for all daemons - some config file in /etc/ that determines if it is enabled at boot or not.
Sometimes it is in /etc/default/ and other times it goes into the daemon-specific config file, like it does with ufw.

---

### Post by jmh72 on 2017-11-01
How strange. IT was set to no. But I checked it last night before bed, and it said yes. I'll reboot after finishing this movie and update this here.

---

### Post by TheFu on 2017-11-01
> **jmh72 said:**
> How strange. IT was set to no. But I checked it last night before bed, and it said yes. I'll reboot after finishing this movie and update this here.

I've been there with different stuff just like you.  Sometimes I don't figure out what happened. Usually, I was on a different machine when checking.

---

