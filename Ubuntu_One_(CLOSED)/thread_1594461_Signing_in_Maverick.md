---
title: "Signing in Maverick"
date: 2010-10-12
forum: Ubuntu One (CLOSED)
---

### Post by Oxwivi on 2010-10-12
I did a fresh install of 10.10 and can't get to sign in Ubuntu One at all. I can sign in fine from the browser, so my password is correct. Anyone know what to do?

---

### Post by dabomb1022 on 2010-10-12
Can you explain in more detail what goes wrong?

---

### Post by Oxwivi on 2010-10-13
I don't know what goes wrong. After I enter the details, the usual 'One moment please...' message shows up and disappears after a while. The Ubuntu One Preferences window remains the same.

---

### Post by jimbo99 on 2010-10-13
What are the results of this program when you run it in a terminal window?

u1sdtool -s

I'm only slightly familiar with it but it could give you a start on tracking down the issue.

---

### Post by Oxwivi on 2010-10-13
```
u1sdtool -s
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
```

Thanks for trying to help.

---

### Post by sgosnell on 2010-10-13
It looks like UbuntuOne doesn't recognize that you have an internet connection, for whatever reason.

---

### Post by Oxwivi on 2010-10-13
Okay, I don't know about that, but after executing that code and posting the result here, I tried to sign in again. And guess what? Bingo!

Dunno what the problem was, but it looks like I got through. Thanks for everything!

---

