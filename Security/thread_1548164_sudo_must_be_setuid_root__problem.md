---
title: "sudo: must be setuid root  problem"
date: 2010-08-07
forum: Security
---

### Post by keevill on 2010-08-07
I did a stupid thing and by using the chmod -R recursive switch, I changed the permissions of the sudoers file.
Now when I try to do anything requiring sudo I get the "sudo: must be setuid root".
I have looked around but I can only seem to find the re-install advice.
I just need a quick dirty fix as this machine is my test machine and is not accessed by any other folk.
I am the only idiot using it.

-keevill-

---

### Post by FuturePilot on 2010-08-07
Boot into Recovery Mode and enter a shell prompt. Then run these two commands.

```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

```

Reboot and you should be good.

---

### Post by keevill on 2010-08-07
> **FuturePilot said:**
> Boot into Recovery Mode and enter a shell prompt. Then run these two commands.

```
chwon root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

```

Reboot and you should be good.

I can't get into recovery mode - upon restart it just opens up into the GUI, there is no grub menu for some reason.
-keevill-

---

### Post by 1980spook on 2010-08-07
u could use a live cd too

---

### Post by cavalier911 on 2010-08-07
Hold the shift key down as soon as you poweron the computer. Silly grub2 hides menu by default unless it detects multiple OS.
Check permissions on this:
```
ls -la /etc/sudoers
-r--r----- 1 root root 828 2010-08-03 11:19 /etc/sudoers
```To modify if permissions are wrong:
```
chown root:root /etc/sudoers
``````
chmod 440 /etc/sudoers
```

---

### Post by keevill on 2010-08-07
> **FuturePilot said:**
> Boot into Recovery Mode and enter a shell prompt. Then run these two commands.

```
chwon root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

```

Reboot and you should be good.

That did the trick,
Held shift down to get to grub.
Actually, the chwon command was not accepted - offered some other command - so I went ahead with the chmod 4755 /usr/bin/sudo and that worked upon reboot.
Many thanks,
-keevill-

---

### Post by cavalier911 on 2010-08-07
It wasn't accepted because the command is chown not chwon. :D
Glad you fixed it.

---

### Post by keevill on 2010-08-08
> **cavalier911 said:**
> It wasn't accepted because the command is chown not chwon. :D
Glad you fixed it.

God ! I'm dyslexic as well !!!
Thx,

---

### Post by FuturePilot on 2010-08-08
Oops, silly me making a typo. Sorry! ;)
Fixed for future reference.

---

### Post by keevill on 2010-08-08
> **FuturePilot said:**
> Oops, silly me making a typo. Sorry! ;)
Fixed for future reference.

aha....I can blame somebody else.....
:-)

-keevill-

---

### Post by bodhi.zazen on 2010-08-08
> **FuturePilot said:**
> Oops, silly me making a typo. Sorry! ;)
Fixed for future reference.

Thank you for fixing that, I msityep all the tmie :lolflag:

---

