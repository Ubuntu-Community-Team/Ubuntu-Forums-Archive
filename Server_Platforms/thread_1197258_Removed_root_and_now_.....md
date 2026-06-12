---
title: "Removed root and now ...."
date: 2009-06-25
forum: Server Platforms
---

### Post by Malcrow on 2009-06-25
Awhile back I created a root account following a tutorial.  I thought it would make it so that you had to be root in order to make changes.  This was not the case.

So anyhow I decided I didn't want the root login anymore so I removed it.  Well now sudo tells me that there is no password for root?

Can this be fixed or did I just really mess up?

Malcrow
BTW: it is server 8.10

---

### Post by Bachstelze on 2009-06-25
Please tell us *exactly* what you did.

---

### Post by Malcrow on 2009-06-26
I followed a tutorial (which I can not find again) that allowed me to login as root.

This did not have the desired effect that I wanted.  I wanted to get rid of the root login so I figured the best way would be to remove it.

I did this by using

sudo userdel -r root

Well now when I try to sudo to do work it says root has no password.

---

### Post by clonne4crw on 2009-06-26
$ su
# passwd
(give root a new password)

---

### Post by Iowan on 2009-06-26
If the rescue CD doesn't help, you can try [tomsrtbt]("http://www.toms.net/rb/"). */etc/passwd* should have a line:```
root:x:0:0:root:/root:/bin/bash

```
You'll also need to add a line in */etc/shadow*

---

