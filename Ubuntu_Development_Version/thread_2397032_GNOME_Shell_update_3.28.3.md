---
title: "GNOME Shell update 3.28.3"
date: 2018-07-24
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2018-07-24
Is anyone having problems with this afternoon's update of GNOME Shell?

Prior to opening an application everything appears to work correctly with regards to Activities, searching for applications and Showing the installed applications. But once an application has been opened "Show Applications", pressing the super key or clicking on "Activities" clears the screen but I can't see my open application again. It's also impossible to search for applications or display all applications installed.

I can close applications by using the launcher but I can't display them. Normality is restored after logging out and back in again. Well, until I use the super key again etc.

I have three users set up on this PC. All have the same problem so i can't see that it's a settings issue. My two spare users are only used when I want to test something. I started to see the problems immediately after installing the update. And yes I have rebooted, switched to a Wayland session and back to Xorg, and played around with various settings relating to workspaces.

I've reported a bug - [#1783363]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1783363").

Anyone else?

---

### Post by harry332 on 2018-07-24
Same bug here, exactly.
You have to downgrade to the earlier version 3.28.2-0ubuntu1 and all is well again.
I did it manually from here:
[https://launchpad.net/ubuntu/+source/gnome-shell/3.28.2-0ubuntu1](https://launchpad.net/ubuntu/+source/gnome-shell/3.28.2-0ubuntu1)

---

### Post by PaulW2U on 2018-07-24
Thanks for your reply harry332 and for confirming the bug report.

I considered downgrading but didn't want to make things worse until someone else confirmed that they were also affected. I'm sure an updated package will be released sometime tomorrow due to the severity of the issue.

---

### Post by PaulW2U on 2018-07-25
Bug fixed within the last hour. New package - **gnome-shell - 3.28.3-0ubuntu2**

---

