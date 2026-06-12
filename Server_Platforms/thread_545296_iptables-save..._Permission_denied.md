---
title: "iptables-save... Permission denied"
date: 2007-09-07
forum: Server Platforms
---

### Post by selectron on 2007-09-07
Hi all!

I'm setting up iptables and I want to save iptables rules how it was write in howto: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I edit /etc/network/interfaces file, add follow lines:

pre-up iptables-restore < /etc/iptables.up.rules
post-down iptables-save > /etc/iptables.up.rules

After I reboot I see that /etc/iptables.up.rules file have not been created.

And when I type in cli follow
$ sudo iptables-save > /etc/iptables.up.rules
and push Enter, I get this message "...Permission denied"

What can I do for autosaving my iptables settings?
Thanks.

---

### Post by p_quarles on 2007-09-07
I've found that you need to open a root shell to run that command. Like so:
```
sudo -s
# iptables-save > /etc/iptables.up.rules
exit
```
I don't know precisely why this is. Perhaps someone else can shed some light on this?

---

### Post by selectron on 2007-09-08
Hi!
Thak you, p_quarles :). Now I'm doing that. But I thing that there is method better.

---

### Post by bodhi.zazen on 2007-09-08
For a root shell you should sudo -i (unless you want your user environment in which case sudo -s is fine, but I think sudo -i is prefered by most).

Second in order to re-direct with sudo you need to use the -c flag and quotes:

```
$ sudo sh -c "iptables-save > /etc/iptables.up.rules"
```

Or you can use su :

```
$ sudo su -c "iptables-save > /etc/iptables.up.rules"
```

---

