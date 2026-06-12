---
title: "networkmanager-openvpn doesn't regen resolv after disconnect?"
date: 2017-10-05
forum: Ubuntu Development Version
---

### Post by mikewiz38 on 2017-10-05
Hi!

I'm testing Ubuntu 17.10 out and had an issue pop up with OpenVPN.  I'm able to connect to my server through OpenVPN just fine and it works great.  I noticed that in /etc/resolv.conf, it will add my connected domain suffix to the search in there.  So, for example, I get this...

```
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53


search foo.org

```
When I disconnect from the OpenVPN connection, it does not remove that "search foo.org" from the file, which prevents my workstation from lookup up anything on that dns name again.  If I remove the line from the resolv.conf file manually, everything works fine again.  
  
I know there's an issue when you run OpenVPN from the command line and DNS not updating properly....but this is when I run it through Gnome and not the command line.  Previous versions of Ubuntu worked fine with this.

I don't know if it's a bug or what and thought this is a good place to start.

Thanks!

---

