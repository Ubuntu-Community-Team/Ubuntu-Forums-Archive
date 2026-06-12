---
title: "PM: hibernation entry"
date: 2020-02-11
forum: Server Platforms
---

### Post by iacoposk8 on 2020-02-11
Hello everyone! I have a small domestic server, it works well but once a month more or less, it goes off, it's not serious but I wanted to try to understand what the cause was. I have opened /var/log/syslog and the last lines are:
```
Feb 11 17:50:34 raspberry NetworkManager[581]: <info>  [1581439834.7583] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Feb 11 17:50:34 raspberry NetworkManager[581]: <info>  [1581439834.7740] manager: NetworkManager state is now ASLEEP
Feb 11 17:50:34 raspberry whoopsie[723]: [17:50:34] offline
Feb 11 17:50:34 raspberry systemd[1]: Reached target Sleep.
Feb 11 17:50:34 raspberry systemd[1]: Starting Hybrid Suspend+Hibernate...
Feb 11 17:50:34 raspberry kernel: [597152.871367] PM: Image not found (code -22)
Feb 11 17:50:34 raspberry systemd-sleep[30140]: Suspending system...
Feb 11 17:50:34 raspberry kernel: [597152.880705] PM: hibernation entry
<0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00><0x00>

```
it says raspberry but it's not a raspberry, I called it just to remember it :)

---

