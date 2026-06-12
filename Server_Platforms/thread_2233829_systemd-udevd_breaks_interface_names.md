---
title: "systemd-udevd breaks interface names"
date: 2014-07-11
forum: Server Platforms
---

### Post by minaev on 2014-07-11
Having installed Ubuntu Server 14.04 on one a test server (HP Proliand DL380 G6 with 4 NICs), I was startled to see the interface names mangled in some weird way. What had been eth[0-3] for years became em1, em2, rename4 (not even 3!) and rename5. I spent some time browsing udev rules, but haven't yet found the file where the names could be reverted back.

I have read [http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/), but I could not neither modify the naming scheme, nor disable it completely using the method described there. There is no 80-net-setup-link.rules in /lib/udev/rules.d. 'ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules' didn't help, either. How do I get back ethX interface names?

PS Frankly, I'm really annoyed by the habit of bringing technologies developed for the desktop (this time it's udev) to the servers. Allegedly, udev has to solve a problem with 'unpredictable changing of inteface names'. In twenty years, I never saw this problem. Until udev appeared on my servers. :twisted:

---

### Post by nerdtron on 2014-07-11
Yeah, 14.04 changes the interfaces names. On mine the interfaces are named p4p1 and p5p1 along with the other 2 interfaces em1 and em2. Puzzling....

---

### Post by minaev on 2014-07-11
After one more reboot, interface 'rename4' suddenly turned into 'em3'. Seems to be another case of [https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043](https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043).

---

### Post by capscrew on 2014-07-11
> **minaev said:**
> After one more reboot, interface 'rename4' suddenly turned into 'em3'. Seems to be another case of [https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043](https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043).


See post # 4 [here]("http://ubuntuforums.org/showthread.php?t=2150517").

For more insight as to *why* you can start [here]("https://www.google.com/search?client=ubuntu&channel=fs&q=biosdevname&ie=utf-8&oe=utf-8") and [here]("https://www.google.com/search?client=ubuntu&channel=fs&q=biosdevname+package&ie=utf-8&oe=utf-8").

---

### Post by minaev on 2014-07-11
I added one line to /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=1 biosdevname=0"
and rebooted after update-grub. Now, I've got all my eth's back! Thanks to everyone.

What remains a secret is a reason to install udev by default on servers. Wish there was a really server-oriented Linux distro...

---

### Post by capscrew on 2014-07-11
> **minaev said:**
> I added one line to /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=1 biosdevname=0"
and rebooted after update-grub. Now, I've got all my eth's back! Thanks to everyone.

What remains a secret is a reason to install udev by default on servers. Wish there was a really server-oriented Linux distro...

[This]("http://www.arachnoid.com/linux/network_names/index.html") should answer why it all started.  On the other hand we all know how to eliminate it now anyway.  FYI: This has nothing to do with systemd.

[COLOR="#0000FF"]Edit:  At this time the biodevname=0 fix now works consistently.  The suggestion that it does not in the article above seems to be in error.[/COLOR]

---

### Post by minaev on 2014-07-11
> **capscrew said:**
> [This]("http://www.arachnoid.com/linux/network_names/index.html") should answer why it all started.

The article's author looks just as angry as me :) I'd put my signature under every word of it.

Thanks again.

---

