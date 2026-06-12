---
title: "Mounting issue"
date: 2010-11-14
forum: Server Platforms
---

### Post by stlsaint on 2010-11-14
I did a upgrade to 10.04 on my server. Then after a reboot i was unable to remotely get into server. Upon connecting the monitor i am greeted with the purple 10.04 boot screen with this text at the bottom:
```

The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery
```

Now i did some googling and the results i came across involved a encrypted drive which i have never even tried to setup so i was of no help. Now if i choose a manual recovery i am dropped to cli which from there i can start networking then ssh into the system and run updates, ping other machines, etc etc) But again this is meant to be a remote access server so everytime i reboot i cant just hit the M key let alone run service networking start!! Any thoughts?

UPDATE: So i commented out the swap entry's in both my /etc/crypttab and /etc/fstab...now i cannot even get to terminal as i could before...now it just loops with no errors!

---

### Post by KB1JWQ on 2010-11-14
What do /etc/fstab and /etc/crypttab say?

---

### Post by stlsaint on 2010-11-15
> **KB1JWQ said:**
> What do /etc/fstab and /etc/crypttab say?

Well due to my latest attempt on which i updated on the first post, I am unable to even get anywhere to be able to see the contents of the file. I know that both of them were trying to mount my swap partitions as encrypted. So i commented them out and now im stuck with my server a a blinking cursor screen.

---

