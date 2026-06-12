---
title: "Redirecting all traffic through HTTP proxy using iptables"
date: 2009-07-09
forum: Security
---

### Post by globemast on 2009-07-09
Hi all,

I would like to redirect all traffic to a known HTTP proxy my ISP owns and which i have access to it.

Is this possible via IPTABLES?

If yes, could you give me a hint on the rules?

Thanks in advance.

---

### Post by Thirtysixway on 2009-07-09
You can set it by going to System > Preferences > Network Proxy

---

### Post by globemast on 2009-07-09
Hi,

Thanks for the prompt response. Is there a way i can do it from the terminal since i will be doing this on a machine without GUI. :)

---

### Post by Cyked on 2009-07-09
Does this help?  I just googled what you asked basically.  No idea of the validity.  Though the first link I provided I found in a thread here on the forum.

[http://wazem.blogspot.com/2008/01/how-to-change-gnome-proxy-settings-on.html](http://wazem.blogspot.com/2008/01/how-to-change-gnome-proxy-settings-on.html)


Or maybe the 2nd reply here....

[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/49727](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/49727)

---

### Post by Dr Small on 2009-07-09
> **globemast said:**
> Hi all,

I would like to redirect all traffic to a known HTTP proxy my ISP owns and which i have access to it.

Is this possible via IPTABLES?

If yes, could you give me a hint on the rules?

Thanks in advance.
This here will give you an idea:
[http://ubuntuforums.org/showthread.php?t=1038761](http://ubuntuforums.org/showthread.php?t=1038761)

You can setup Privoxy to communicate with the HTTP Server at your ISP, and then setup the transproxy script to redirect OUTBOUND connections to Privoxy, thus to the HTTP Proxy.

Dr Small

---

