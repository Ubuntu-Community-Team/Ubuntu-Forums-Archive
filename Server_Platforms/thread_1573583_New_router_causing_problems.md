---
title: "New router causing problems"
date: 2010-09-12
forum: Server Platforms
---

### Post by w1ll1am on 2010-09-12
Hello I just got a new router and now i can not access my ubuntu file server from my ubuntu computers windows can access it fine. if i switch back to the old router everything works so ik it is the problem i just do not know how to fix it can anyone help?

when i try to access it it says [B]Unable to mount location: Failed to retrieve share list from server

any help would be nice thanks
[/B]

---

### Post by goinglinux on 2010-09-12
If you haven't tried this already, you might try connecting by using the server's IP address rather than the server name.
[LIST]
[*]In Nautilus, press ctrl+l to display the location bar.
[*]Type the following: smb:///<ipaddress>
[/LIST]
(Replace "<ipaddress>" with the actual IP address of your server.)

---

