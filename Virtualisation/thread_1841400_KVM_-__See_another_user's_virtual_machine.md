---
title: "KVM -  See another user's virtual machine"
date: 2011-09-09
forum: Virtualisation
---

### Post by francoflores on 2011-09-09
Hi everybody,

I am new here. I hope to help some day.
But now i need your help.

I have a machine with Ubuntu wich have 2 users (User1 and User2).
I installed KVM while i was login in User1, And I installed WinXP as Virtual Machine.

With the User2 i can see the KVM and Virt-Manager but, I can't see the WinXp Virtual Machine.

How can I do to see the WinXP virtual machine installed by User1?

I  placed users in the same group.

---

### Post by bodhi.zazen on 2011-09-09
Use a VNC server =)

Install a server in windows, and connect from any client.

Just take care not to use VNC over the internet (OK on a LAN).

---

