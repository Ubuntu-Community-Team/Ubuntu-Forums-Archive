---
title: "as admin, how can I access root.."
date: 2012-04-14
forum: Security
---

### Post by Baldrick_NZ on 2012-04-14
from another user on the same PC?

Hi all, on occasion, my wife asks me to (for example) change permissions of a file on her user account.

How can I as admin, from her profile change permissions?

When I try in terminal, and use her password, I get a message saying she doesn't have access to root, which is fine, but I can't work out what I need to do.

Any help would be much appreciated!

---

### Post by bab1 on 2012-04-14
> **Baldrick_NZ said:**
> from another user on the same PC?

Hi all, on occasion, my wife asks me to (for example) change permissions of a file on her user account.

How can I as admin, from her profile change permissions?

When I try in terminal, and use her password, I get a message saying she doesn't have access to root, which is fine, but I can't work out what I need to do.

Any help would be much appreciated!

By accessing root, do you mean using **sudo**?

Edit: Is this using 1 host or remotely via SSH?

---

### Post by sisco311 on 2012-04-14
> **Baldrick_NZ said:**
> from another user on the same PC?

Hi all, on occasion, my wife asks me to (for example) change permissions of a file on her user account.

How can I as admin, from her profile change permissions?

When I try in terminal, and use her password, I get a message saying she doesn't have access to root, which is fine, but I can't work out what I need to do.

Any help would be much appreciated!

You can use **su** to run a shell as your admin user. su will prompt you for your user's password:
```

su - **your_username**
sudo command
whatever
exit #or press Ctrl+d

```

EDIT:

Obviously, you will have to replace **your_username** with your login name.

For more information, please check out:
```

info coreutils 'su invocation'

```

---

### Post by Baldrick_NZ on 2012-04-14
Thanks guys!

I knew it had to be pretty straight forward. :-)

---

