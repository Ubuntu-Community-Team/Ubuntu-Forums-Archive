---
title: "My ubuntu server now has a gui I didnt install and wont let me open terminal"
date: 2021-03-03
forum: Server Platforms
---

### Post by b0g0 on 2021-03-03
I dont know if anyone else has had this problem but i recently moved in with my girlfriend and went to setup my media server in her house. I updated it right before i proceded to move it. There shouldnt be a gui at all as i never downloaded one and now it wont let me access the byobu terminal which is the only available terminal application.

---

### Post by Impavidus on 2021-03-03
Use ctrl+alt+F1 to ctrl+alt+F7 to switch between the TTYs. one of them has the GUI, the others are command line interfaces.

If the GUI was somehow recently installed, it should be in the log files. Try /var/log/dpkg.log.

---

### Post by slickymaster on 2021-03-03
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2021-03-03
Many media servers would assume you want to watch locally, on the machine, so they would install the GUI dependencies.  For example, if you installed Kodi, then it would install GUI libraries.  Media center servers usually have 50+ dependencies.

Which media center have you installed?

To manage any Linux (or Unix) system, the preferred method is over the network using ssh.

I can't help with any problems related to moving in with your girlfriend. That's a different website. ;)

---

