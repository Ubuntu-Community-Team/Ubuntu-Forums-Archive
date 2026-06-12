---
title: "Installing NIS in ubuntu"
date: 2016-07-12
forum: Server Platforms
---

### Post by jason-cordero on 2016-07-12
Dear Ubuntu community,

I am currently trying to set up a NIS server and I get stucked at the beggining of the following tutorial: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

At step 3) ```
sudo apt-get install portmap nis
``` I'm told > Note, selecting 'rpcbind' instead of 'portmap' That would be fine if rpcbind were in the /etc/default/ directory, but it is not. Therefore, I don't know how I can continue. Furthermore if I remove and install portmap and nis as before, I am not asked for the name of my NIS domain, which sounds odd.

I would appreciate any help on this issue, since I've already tried unsuccessfully other tutorials.

Thanks in advance

---

### Post by howefield on 2016-07-12
Thread moved to the "*Server Platforms*" forum.

---

### Post by TheFu on 2016-07-16
Cannot help with this specific issue, but felt someone should point out the security of NIS is lacking. I've been temped to use it at home, but even there, the security concerns are just too great for my comfort.

These days, I'd strongly suggest using LDAP for the same purpose. There are guides for setting up LDAP in this way (posix schema needed) and the PAM settings to hook everything aren't that hard. Vaguely recall doing this around 2010 with Ubuntu both as the server and the client.

If you want a more complete solution, check out FreeIPA [https://www.freeipa.org/page/Main_Page](https://www.freeipa.org/page/Main_Page) . I've only seen it on Redhat servers, but thought it had been ported to Debian/Ubuntu recently.

Anyway, sorry I can't help with NIS.

---

