---
title: "Raspberry Pi mounting of Samba share."
date: 2015-03-30
forum: Ubuntu/Debian BASED
---

### Post by stchman on 2015-03-30
Hello, hopefully this is the best place to ask this question.

I recently got a Raspberry Pi and configured it to be my SSH server.  My old SSH server the power supply on it went out and it is a proprietary Dell.

Any rate, I have a hard drive hooked up to my router that acts as a NAS.  My old SSH box was running Ubuntu 13.10 and I used the following line in my fstab to connect to the share.

```

# mount samba share
//192.168.1.1/BOB_STUFF         /mnt/BOB_STUFF         cifs      defaults,rw

```

For some reason the Raspbian does not like this line as this causes the OS to hang on boot at configuring network interfaces.

I have checked the documentation and this appears to be the right syntax.

Thanks.

---

### Post by anaconda on 2015-04-01
Have you installed samba and cifs support for it?

---

### Post by stchman on 2015-04-03
> **anaconda said:**
> Have you installed samba and cifs support for it?

Samba and cifs are installed by default on Raspbian.

I had to use the following line:

```
//192.168.1.1/BOB_STUFF    /mnt/BOB_STUFF     cifs   guest,uid=1001,gid=1004,iocharset=utf8    0    0

```

Raspbian liked that.

---

