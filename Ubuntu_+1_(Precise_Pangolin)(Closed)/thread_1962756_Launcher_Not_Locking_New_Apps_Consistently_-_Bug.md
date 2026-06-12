---
title: "Launcher Not Locking New Apps Consistently - Bug?"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by LinuxLars on 2012-04-21
Just upgraded to Precise beta 2 - when I run a new application, and select "Lock to Launcher", it persists only during the session. When I logout, and log back in, none of the Launcher application changes have been persisted. (I've had only one or two exceptions where it DID actually remember my change).

I didn't use the Unity interface in 11, but thought I'd try it again. 

Is this a bug? Or is there a different way of persisting choices?

Running on Thinkpad X61s.

Thanks.

---

### Post by t1497f35 on 2012-04-21
Beta 2 is too old, the RC is here, however if you applied the updates its irrelevant.
If the .desktop file of the corresponding Launcher item is being removed then the launcher will not remember it, because well, the Launcher is dumb by design, unlike in win7.
However, I suspect that your issue is different, hence you should try to reproduce it, record it and file a bug.

---

### Post by t1497f35 on 2012-04-21
repost. please delete.

---

### Post by LinuxLars on 2012-04-21
Maybe I misspoke. It's the "latest beta" installed from the website this morning. 

System Settings -> System -> Details only displays "ubuntu 12.04 LTS". 
Running cat /etc/issue returns "Ubuntu 12.04 LTS \n \l". 
Running cat /etc/lsb-release returns:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

I haven't created a .desktop file - I just used "right-click" on the launcher icon when the application was running, and selected "Lock to Launcher". Intuitively, that should save the icon and bind it to the launcher for the next logon.

If this is a duplicate, I'd love to find the original; after 20 minutes of searching I cannot locate this exact case - can you provide a link?

---

