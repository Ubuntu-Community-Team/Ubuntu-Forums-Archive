---
title: "networking using virtualbox"
date: 2020-04-15
forum: Virtualisation
---

### Post by giliw on 2020-04-15
hi,

been trying to start a mmorpg game on windows 10 image using virtualbox (os ubuntu 18.04).
but i'm getting  the following message:

[IMG]https://i.postimg.cc/k5MWdNGV/Capture.png[/IMG]

there isn't any server check and I shut down the windows firewall.

---

### Post by wildmanne39 on 2020-04-15
Hello and welcome to the forum giliw

Moved to Virtualisation sub-forum.

---

### Post by ajgreeny on 2020-04-15
Do you get network connections for other uses?
Can you use internet browsers as normal?
Are you using a NAT or bridged connection in your Windows guest?

---

### Post by giliw on 2020-04-15
Yes, browsing the internet just fine. NAT.

---

### Post by kneutron on 2020-06-25
See:
[https://www.reddit.com/r/Maplestory/comments/298zer/is_there_any_way_to_play_maplestory_on_a_vm/](https://www.reddit.com/r/Maplestory/comments/298zer/is_there_any_way_to_play_maplestory_on_a_vm/)

---

### Post by TheFu on 2020-06-25
Sometimes we have to go to the manual: [https://www.virtualbox.org/manual/UserManual.html#settings-network](https://www.virtualbox.org/manual/UserManual.html#settings-network)
But definitely check out the stuff posted above first.

---

### Post by SeijiSensei on 2020-06-26
Go to the Settings for this virtual machine and switch the adapter from NAT to bridged. Any better?

---

