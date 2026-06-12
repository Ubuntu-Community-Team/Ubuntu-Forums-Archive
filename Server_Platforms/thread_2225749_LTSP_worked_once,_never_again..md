---
title: "LTSP worked once, never again."
date: 2014-05-23
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2014-05-23
LTSP on VM's to test before I buy hardware. Virtualbox from repos. Server vm is Ubuntu server 14.04, all updates. Client is ... well single core, 1024mb of ram and set to boot network only. The client and eth1 of the server are set to internal network. Eth0 of the server is set to NAT. I got this to work 1 time. It loaded up to the login, I logged in and I was staring at an XFCE desktop from the xubuntu-desktop package. Made another user with sudo from the client. ( I think this is the mistake ).

Now. Made the user and attempted to logout then log back in. It kept saying failed. So rebooted client. This time it shows the dhcp aquisition on the pxe boot of POST then it sits there with a solid cursor top left of the screen awhile. Ends up with this. ```
Error: Socket failed: Connection timed out
Exiting.
```

After a minute or 2 it goes through saying all these failed mount operations then sits me at a (initramfs) prompt. It will do this until I reboot the server itself. Reboot the server and restart the client. It loads up to the login screen. I try logging in on my user or the new one I added with sudo. The cursor turns into the spinning circle and that is where it gets stuck. Wait awhile and finally just reboot the client to try again. Back to the solid cursor followed by the timeout error.

Am I doing something wrong or is this one of those things that doesn't tolerate VM's to much? While I doubt it, is the software just buggy and should I look for something else to accomplish the same thing?

---

### Post by Tadaen_Sylvermane on 2014-05-23
Switched server to Debian wheezy. Works fine, just sorting out minor hiccups now.

---

