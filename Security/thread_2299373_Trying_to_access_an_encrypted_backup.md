---
title: "Trying to access an encrypted backup"
date: 2015-10-17
forum: Security
---

### Post by x34460 on 2015-10-17
Hi.
Earlier this year, I installed a new drive in my laptop and copied the contents of my encrypted home directory to an external drive, installing the latest version of Ubuntu on the new drive.
It is now necessary to access that backup, but I can not. It says that I am not the owner and I am unable to change permissions because of this.

Does anyone know of a solution to this problem?

Thank you.

---

### Post by ian-weisser on 2015-10-18
Whom does your system say is the owner?

---

### Post by x34460 on 2015-10-18
Thanks for your reply.

Owner and group are both root.

---

### Post by x34460 on 2015-10-18
Logged in as root and changed ownership of folder and sub-folders to my primary username but when I log in as that user, it still shows root as owner.

Any ideas?

Thanks.

---

### Post by x34460 on 2015-10-18
chown -R newuser /path/to/dir seems to have solved the problem.

thanks.

---

