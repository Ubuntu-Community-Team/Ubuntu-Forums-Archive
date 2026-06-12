---
title: "Ubuntu 17:10 Server - System Policy"
date: 2017-12-30
forum: Server Platforms
---

### Post by jai-2 on 2017-12-30
After installing a Gnome desktop on my VPS Ubuntu 17:10 server, I am unable to make changes to some of my settings in the Ubuntu desktop GUI.
For example, to make changes to my desktop clock **I need to click on the small lock icon** ([COLOR=#ff0000]see image[/COLOR]) before I can make any changes.
The lock is grayed out and when I move my mouse over it I get a message that says - "System Policy Prevents Changes. Contact your system administrator".
This occurs for all users (even root).
I am accessing my VPS desktop via ssh (using NoMachine [SIZE=2]Eterprise[/SIZE] GUI).
What settings need to be changed on my server to fix this problem?
Thanks

---

### Post by LHammonds on 2017-12-30
Try this:

```
gksudo gnome-control-center user-accounts
```

[Reference](https://answers.launchpad.net/ubuntu/+source/gnome-control-center/+question/208473)

LHammonds

---

### Post by jai-2 on 2017-12-30
Thanks but that only gets me into the user accounts and allows me to change the password.  It still has the small lock icon which reads  - "System Policy Prevents Changes. Contact your system administrator".
Something has disabled that small lock icon throughout all settings.
Any other ideas?

---

### Post by jai-2 on 2017-12-31
After doing a number of OS reinstalls and testing different desktops, I found that the ubuntu-gnome-desktop does NOT have the lock icon problem unless you add themes. If I install gnome-shell the problem returns.
All very strange!!! Any ideas as to why this is happening?

---

### Post by jai-2 on 2017-12-31
Not sure if anyone is following this post but I will continue to add clues that may help solve my problem.
It is possibly not related to themes (my last post) but maybe to the restarting of my server (which I sometimes did after installing themes.
When I first install the desktop on my server the lock works but after one or two restarts it doesn't. When I first install the desktop, my display resolution in the settings only has ONE option (800x600) but after one or two restarts many more resolution options appear in my settings and the locks stop working. The two are not related but something is resetting on my server that causes both of those items.
Any ideas?

---

### Post by jai-2 on 2017-12-31
On further research I have found that the problem may be because I am accessing remotly via ssh connection. I just need to find what settings to change in my vps control panel.

---

