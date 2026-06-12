---
title: "Server hanging intermittently"
date: 2012-04-07
forum: Server Platforms
---

### Post by MiniStephan on 2012-04-07
I'm running Ubuntu Server 11.10 on an HP Proliant tower I recently acquired. I am using I headless most of the time but I have been having a recurring issue that I am unsure of the source.

 While attempting to access the server via ssh (putty), ftp (filezilla), etc, the server becomes unresponsive after I enter my password. Today, after successfully connecting via VNC, upon entering my password on the lock screen the screen sat there "Checking..." indefinitely. 

Every time this happens I am forced to hard restart the server. 

Does anyone have any idea what is happening? I'm honestly clueless. I will provide other information as requested, but I don't even know where to start looking here.

---

### Post by roelforg on 2012-04-08
I believe either your network, your nic or the nic kmodule is having trouble.

---

