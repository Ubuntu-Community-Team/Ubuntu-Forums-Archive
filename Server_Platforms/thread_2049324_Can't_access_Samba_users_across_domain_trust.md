---
title: "Can't access Samba users across domain trust"
date: 2012-08-28
forum: Server Platforms
---

### Post by Team140 on 2012-08-28
I have an odd problem and my Google-Fu is failing me.

I've recently been tasked with recreating a Remote Desktop Farm with an RDP Gateway. In order to do so, the RDP Gateway requires actual users or groups with actual users for security.

Our current setup: Samba domain handling users and workstations. New AD was created just for the RDP Farm. AD<->Samba trust in place. Verifying the trust on each end completes successfully.

Samba users can log on to a standalone RDP Server using sambadomain\username and access all needed files, network devices, etc. This was accomplished by adding the local Remote Desktop Server's "Authenticated Users" to allowed RDP users. This works fine for our environment as all RDP servers are on a private network.

We want to open this up with a gateway server for people out of the office to access the internal RDP servers. When adding users/groups, I can see the Samba Domain container, but when I choose it, there are no users or groups available to choose from. This also occurs on workstations. No Samba users or groups are shown when you go to change file security in Windows.

Any ideas on this?

---

### Post by Team140 on 2012-08-29
Bueller?

---

