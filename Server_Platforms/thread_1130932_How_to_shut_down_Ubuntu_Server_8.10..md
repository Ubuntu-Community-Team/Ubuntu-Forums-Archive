---
title: "How to shut down Ubuntu Server 8.10."
date: 2009-04-20
forum: Server Platforms
---

### Post by svennam on 2009-04-20
Hi
I have installed Ubuntu Server 8.10 on my desktop. Then I installed desktop environment on it to install Oracle Express Edition Database. Everything is working well at this point. Now, I am unable to shutdown the system either through GUI environment or through command prompt. When I shutdown throgh GUI environment,it is just rebooting. When I shut it down through command mode, it reboting. Can someone please help me how I can shut the server down and turn the system off?

---

### Post by nandemonai on 2009-04-20
```
sudo shutdown -h now
```

---

### Post by albandy on 2009-04-20
or 
sudo poweroff

---

### Post by svennam on 2009-04-20
I tried sudo shutdown -h 0
That did not work.  I used GUI interface.  In both cases, it is just rebootding again and again.

---

### Post by cdenley on 2009-04-20
> **svennam said:**
> I tried sudo shutdown -h 0
That did not work.  I used GUI interface.  In both cases, it is just rebootding again and again.

Who suggested that command? I usually use the first suggestion
```

sudo shutdown -h now

```
You can always check the manual for any of these commands
```

man shutdown
man poweroff
man halt

```

---

