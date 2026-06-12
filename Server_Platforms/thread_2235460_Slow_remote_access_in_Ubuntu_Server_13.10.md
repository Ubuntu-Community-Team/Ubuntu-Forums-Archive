---
title: "Slow remote access in Ubuntu Server 13.10"
date: 2014-07-21
forum: Server Platforms
---

### Post by h.hittini on 2014-07-21
Hello everyone,

I have Ubuntu Server 13.10 and 3.11 kernel
I have a USB adapter configured as an access point using hostapd
When I start the service my SSH connection becomes very very slow, if I stopped the service it goes back to normal
I believe the command execution is fast, however, echoing the things I type and the output is very slow
I looked at the system load from the login banner and it's 0%
In addition, I connected the computer to a monitor and a keyboard to find it performing really fast!
I thought that it's an SSH issue, I tried the suggestions here [http://unsharptech.com/2009/04/11/fix-slow-connections-to-ubuntu-ssh-servers/](http://unsharptech.com/2009/04/11/fix-slow-connections-to-ubuntu-ssh-servers/) but still it is slow
I also tried telnet and it's slow too
Do you have any suggestions
I'm using my Mac as the SSH client if that makes a difference
Thanks in advance

Regards,

---

### Post by TheFu on 2014-07-21
Is the routing correct and not confusing?  If both wifi and wired connections are active, that can lead to slowness.  Also, try the connections using only IP addresses - this will knock out any name resolution slowdowns.

I don't use Macs can't help there, but when I used one for a few weeks a few years ago, there were a number of bugs that prevented commonly used UNIX and Windows connection protocols from working at all. Are you patched?

Lastly - support for 13.10 ended last week. Move to 14.04 LTS before they close this thread because non-supported OS questions are "off topic" now, at least that is what I've seen recently.

---

### Post by h.hittini on 2014-07-21
> **TheFu said:**
> Is the routing correct and not confusing?  If both wifi and wired connections are active, that can lead to slowness.  Also, try the connections using only IP addresses - this will knock out any name resolution slowdowns.

Routing is fine
I have two wireless connections, and one wired
I'm using the wired one for SSH and the other wireless connections are not doing any activity at all
Even if they did, that doesn't explain the lag only when accessing the machine remotely
I'm also using IP addresses, no DNS is involved here

> **TheFu said:**
> I don't use Macs can't help there, but when I used one for a few weeks a few years ago, there were a number of bugs that prevented commonly used UNIX and Windows connection protocols from working at all. Are you patched?
I actually tried to SSH from another Ubuntu machine and got the same lag, it's probably not a Mac related issue

> **TheFu said:**
> Lastly - support for 13.10 ended last week. Move to 14.04 LTS before they close this thread because non-supported OS questions are "off topic" now, at least that is what I've seen recently.
I'd love to upgrade, but unfortunately, I need to use a software that doesn't work on Ubuntu versions later than 13.10

---

