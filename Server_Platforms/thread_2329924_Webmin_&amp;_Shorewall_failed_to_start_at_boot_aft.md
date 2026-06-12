---
title: "Webmin &amp; Shorewall failed to start at boot after upgrade to 16.04"
date: 2016-07-06
forum: Server Platforms
---

### Post by vonner2 on 2016-07-06
I've upgraded my 14.04 LTS test server to 16.04 LTS, preparatory to eventually upgrading my main server, but found that neither Webmin nor Shorewall (aka Shoreline) firewall were automatically starting at boot.  Googling found lots of hits with the same issue, concluding that the move to systemd in 16.04 had caused this.  So I figured I'd better try and understand a bit about systemd.

I found this page very helpful: [https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

In particular the section "Enabling and Disabling Services":

I ran the commands "**sudo systemctl enable webmin**" and "**sudo systemctl enable shorewall**" which resolved this problem instantly, and now both services start at boot.

I am aware that some users deride webmin and recommend not using it, but I consider it a matter of personal preference, so anyone who does use it should find this useful.

---

### Post by howefield on 2016-07-06
Thread moved to the "*Server Platforms*" forum.

---

