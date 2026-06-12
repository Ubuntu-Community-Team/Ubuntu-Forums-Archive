---
title: "SSH key changed, should I be worried?"
date: 2008-06-19
forum: Security
---

### Post by ShiningMasamune on 2008-06-19
Greetings all, total n00b here.  I've recently put together a file server for my family and I've chosen to run Ubuntu on it.  I set most everything up through SSH on a different computer (through much trial and error), so I could run the file server headless.  Everything's been peachy for quite a while now, and the last time I SSH'd in was about a month ago.  But yesterday, I tried to SSH in to make a few changes, and my SSH client went nuts telling me that the server's key had changed and that this usually signifies a man-in-the-middle attack.

Now, the server's on a local network, behind a router, with no ports forwarded to it, but still... this is kind of distressing.  I haven't changed any kind of SSH settings, and in fact I'm pretty sure the file server hasn't even been powered off since last I SSH'd (although I could be wrong about that).  Should I be worried?  What should I do?

---

### Post by Dr Small on 2008-06-19
The Server's known_host key and the clients key do not match, most likely. Probably an IP Address changed on either the server or client end causing a ruckus.

---

### Post by brian_p on 2008-06-19
> **ShiningMasamune said:**
> Greetings all, total n00b here.  I've recently put together a file server for my family and I've chosen to run Ubuntu on it.  I set most everything up through SSH on a different computer (through much trial and error), so I could run the file server headless.  Everything's been peachy for quite a while now, and the last time I SSH'd in was about a month ago.  But yesterday, I tried to SSH in to make a few changes, and my SSH client went nuts telling me that the server's key had changed and that this usually signifies a man-in-the-middle attack.

A complete copy of ssh's message would have been more helpful. Also, you don't say whether you were allowed in - although you imply you weren't.

> Now, the server's on a local network, behind a router, with no ports forwarded to it, but still... this is kind of distressing.  I haven't changed any kind of SSH settings, and in fact I'm pretty sure the file server hasn't even been powered off since last I SSH'd (although I could be wrong about that).  Should I be worried?  What should I do?

Could it have anything to do with the security updated packages for libssl and ssh which happened round about 23 May? One machine received them, the other didn't.

---

### Post by The Cog on 2008-06-19
The update a couple of weeks ago fixed a bug that meant encryption keys generated on Debian and derivatives were not as strong as they should be. Part of the update was to replace the local SSH keys which identify the machine with bug-free ones, thus changing the servers fingerprint.

You can remove the appropriate line in ~/.ssh/known-hosts in your client, or just delete the whole file if you can't figure out whch line it is. Then connect and accept the new key.

---

### Post by Dr Small on 2008-06-19
> **The Cog said:**
> You can remove the appropriate line in ~/.ssh/known-hosts in your client, or just delete the whole file if you can't figure out whch line it is. Then connect and accept the new key.

The SSH error should output the offending line number is .ssh/known_hosts, and it is as simple as editing the file with Vim, move to the offending line number, press 'dd' and then 'esc' ':wq' :D

---

### Post by kevdog on 2008-06-19
I prefer cntrl-ZZ for saving the file :)

---

### Post by hyper_ch on 2008-06-20
normally you should be worreid about changed ssh keys but in this case it was the bug-fix that regenerated all keys.

---

