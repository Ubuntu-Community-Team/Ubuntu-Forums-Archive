---
title: "Does Linux have a Firewall by default?"
date: 2011-03-25
forum: Security
---

### Post by Learning Linux 2011 on 2011-03-25
Does Ubuntu come with a Firewall pre-installed and running?

If so, how can I see if it is working and/or configure it?

If not, are there any out there?

---

### Post by fela on 2011-03-25
Yes, it comes with a firewall by default, as do pretty much all Linux distros, but I must stress, **it is very unlikely that the default settings are unsecure for your situation**.

If however you decide you want to change your firewall, there are many different tools to do so, which are called 'front ends'. They are all interfaces to the same firewall program which is called 'iptables' and is included with Linux.

One of them is GUFW, to install it, use the software centre (you can also search for other firewall tools there), or enter:

```
sudo apt-get install gufw
```

It will appear in the menu somewhere and you can go from there. However, as I said you should be fine with the default setup.

EDIT: just to be clear, if you don't have a firewall configuration tool (such as GUFW), it does NOT mean there is no firewall running, it simply means you have a nice tool to add/change/remove rules from it with :)

---

### Post by The Cog on 2011-03-25
Read the stickies in the security discussions forum. I'll move this thread there. Bodhi.zazen's sticky is well worth reading.

But in short, the firewall is installed, but not enabled as it's not really needed in a default install. If you do want to enable it anyway, the command **sudo ufw enable** will do it.

---

### Post by Arijit_Kundu on 2011-03-25
by default all incoming connections are not allowed in ubuntu, no need for a firewall. ufw firewall is by default disabled in ubuntu. it can be configured following [this]("https://help.ubuntu.com/10.04/serverguide/C/firewall.html").

---

