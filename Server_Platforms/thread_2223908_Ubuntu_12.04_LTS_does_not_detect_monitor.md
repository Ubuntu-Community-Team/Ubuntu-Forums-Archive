---
title: "Ubuntu 12.04 LTS does not detect monitor"
date: 2014-05-13
forum: Server Platforms
---

### Post by edgyeft on 2014-05-13
Hi
I have set up a headless server running Ubuntu 12.04 LTS.
The other day I SSH'ed in, changed something in /etc/network/interfaces and broke something, now I can't get SSH access any more.

To rescue the system I connected up a monitor, but it said no signal.
I attached a USB keyboard, pressed some buttons in the hope of getting it to respond, but nothing.

In the end I had to use SysRq + REISUB to get it to reboot.

As the server rebooted and did its POST, the monitor came to life.

It seems as though if the monitor is disconnected, after re-attaching it you need to reboot the system to get it to pick up the monitor.

How can I get Ubuntu to detect the monitor without rebooting?

Thanks

---

### Post by kosmokramer314 on 2014-05-13
I believe POST is what initiates the monitor being used.  If there is nothing there during the POST then it won't be used if I understand it correctly.  What type of monitor is it?  VGA, HDMI, DVI?

---

### Post by nightfly2 on 2014-05-14
I have almost the same problem with 14.04 LTS on HP ProLiant G4 ML350 machine.
Install went fine and then at the first restart the screen (motherboard graphics with VGA connector -> LCD screen-I've tried at least three) says unsupported resolution...
I tried old 15 inch to 23 inch new screens but nothing.

i cannot SSH/telnet anything...

---

### Post by edgyeft on 2014-05-16
> **kosmokramer314 said:**
> I believe POST is what initiates the monitor being used.  If there is nothing there during the POST then it won't be used if I understand it correctly.  What type of monitor is it?  VGA, HDMI, DVI?

It is a VGA monitor, the box does also support HDMI but I don't expect that to work without X installed, which it isn't due to this being a headless server.

I see what you are saying about POST, but surely it should be possible to attach a monitor and get a picture without having to reboot the server?

I've also tried pressing Ctrl+Alt+F1, F2 etc to change consoles but to no avail.

Thanks

---

