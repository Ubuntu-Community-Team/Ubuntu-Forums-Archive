---
title: "view another users history?"
date: 2013-09-16
forum: Server Platforms
---

### Post by bewareofthephog on 2013-09-16
If I want to view the command line history of another user is there a way to do this?

---

### Post by nerdtron on 2013-09-16
You should be the root/admin or a member of the sudoers to be able to do this.
After logging in to the server, change to the "anotheruser" account.
```
root@server:~#su anotheruser
```
Then view his history.
```
history
```

---

### Post by LHammonds on 2013-09-17
Or if you have access to their home folder (such as doing a "sudo su" to gain root access), you can type something like the following:

```

vi /home/username/.bash_history

```

The default permissions on this file are Read/Write for the user only.

LHammonds

---

