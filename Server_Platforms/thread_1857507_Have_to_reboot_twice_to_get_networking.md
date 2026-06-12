---
title: "Have to reboot twice to get networking"
date: 2011-10-10
forum: Server Platforms
---

### Post by fizgig on 2011-10-10
Running 10.04 server on a headless desktop machine.  Every time I reboot it, I lose networking on it.  The server will reboot just fine and I'd even see a login prompt if I connected a monitor to it but if I typed "ifconfig", I'd only see the loopback device.

Anyhow, I've learned that I need to reboot it one more time and it everything will work great from that point on - until I need to reboot it for whatever reason where this process restarts.

Can anyone help me troubleshoot why this happens?

---

### Post by Krupski on 2011-10-10
> **fizgig said:**
> Running 10.04 server on a headless desktop machine.  Every time I reboot it, I lose networking on it.  The server will reboot just fine and I'd even see a login prompt if I connected a monitor to it but if I typed "ifconfig", I'd only see the loopback device.

Anyhow, I've learned that I need to reboot it one more time and it everything will work great from that point on - until I need to reboot it for whatever reason where this process restarts.

Can anyone help me troubleshoot why this happens?

Go to the **[COLOR="Blue"]/etc/udev/rules.d[/COLOR]** directory and delete the file "**[COLOR="Blue"]70-persistent-net.rules[/COLOR]**" file.

You may have an old MAC address in that file linked to the eth0 device.

When you reboot, that file will be recreated with the info for your current NIC.

Hope this helps.

-- Roger

---

### Post by fizgig on 2011-10-10
Thanks for the suggestion.  Tried that.  Still not working after reboot.  Had to reboot again.

---

### Post by Krupski on 2011-10-10
> **fizgig said:**
> Thanks for the suggestion.  Tried that.  Still not working after reboot.  Had to reboot again.

Oh well, I tried. Sorry.  :)

---

