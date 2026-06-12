---
title: "System Not Shutting Down"
date: 2010-06-27
forum: System76 Support
---

### Post by pnjabi on 2010-06-27
Hello - I am getting the following message when I shut down the system. It never shuts down and the message stays on the screen.

Asking all remaining processes to terminate
Reconfiguring network interfaces...
Reconfiguring swap...
Stopping remaining crypto disks...
Stopping early crypto disks...
Will now halt...

Any help is appreciated. Thank You.

Pnjabi
Ubuntu 9.10 | Meerkat Nettop

---

### Post by wilee-nilee on 2010-06-27
Does this happend every time you have tried to shutdown. Here is a link to a soft shutdown or reboot.
[https://secure.wikimedia.org/wikipedia/en/wiki/Reisub](https://secure.wikimedia.org/wikipedia/en/wiki/Reisub)

---

### Post by pnjabi on 2010-06-27
Yes, it happens everytime I shut down. It just started happening this afternoon and I don't remember updating anything.

---

### Post by wilee-nilee on 2010-06-27
> **pnjabi said:**
> Yes, it happens everytime I shut down. It just started happening this afternoon and I don't remember updating anything.

I would run a update to see if anything is loaded, but use the link to shutdown or reboot rather then the power button. I'm not familiar with what the problem may be or how to find out why it's happening, others may know what to look for.

Also what distro's are you using on the computer, is it a dual boot or a wubi install, this information is almost always important to include in a thread.

---

### Post by pnjabi on 2010-06-27
I even tried "shutdown -h now" command but the problem is still there. Btw I am using Ubuntu 9.10.

---

### Post by isantop on 2010-06-28
It looks like your computer has "Shut down" except that the hardware, for whatever reason, does not receive the signal to shut down.

Using the power button should be okay, though I'm not recommending it. On top of that, you should also be able to use that link.

---

### Post by pnjabi on 2010-06-28
I will try the shortcut as mentioned in the link when I get home tonight. But, how do I fix the underlying problem of the computer not shutting down? I ran the Update Manger last night and ensured all packages are updated. 
 
Do I reimage it or upgrade it to 10.04 to see if the problem goes away? Thank You.

---

### Post by isantop on 2010-06-28
You can always try that. Be sure to back up your data in case something goes wrong.

---

### Post by pnjabi on 2010-06-30
I tried sudo fsck commands to check my filesystem. The came clean except I get the following error message while checking the swap partition:

fsck 1.40.2 (12-Jul-2007)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda2
ubuntu@ubuntu:~$ 

Can this be causing the two problems I am having 
1) filesystem checks always happening and 
2) system not shutting down?

---

### Post by msrinath80 on 2010-06-30
I don't think swap partitions are supposed to be fsck'ed? Case in point, there is no **f**ile **s**ystem on the swap partition to be **c**hec**k**ed?

---

### Post by isantop on 2010-06-30
msrinath is correct, I believe. Your swap should come back with that error.

---

### Post by pnjabi on 2010-06-30
So, is there anything else I can try to fix these issues or do I take the plunge and reimage?

---

### Post by isantop on 2010-06-30
Try booting your Live Media and shutting donw in that. If it shuts down, reinstall. If it doesn't, contact us at support...at...system76...dot...com

---

