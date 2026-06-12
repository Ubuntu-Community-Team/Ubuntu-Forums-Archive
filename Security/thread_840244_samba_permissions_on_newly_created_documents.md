---
title: "samba permissions on newly created documents"
date: 2008-06-25
forum: Security
---

### Post by ffoeg on 2008-06-25
I've configured a Ubuntu 8 computer to act as a Samba server. It's a simple workgroup environment. I've set the two users that I want to access the shares in the same group. Then I set the owner of the shared folders to a user of the main group of the two users. The "group" of the folders to the group that the two users are in. I've even set others to be able to create and delete files to.

On theSamba server side, I've given access to all the users (read/write). I've confirmed that this has been entered into the smb.conf file.

Each share can be accessed by each user. But when a file is created by one user, that user becomes the owner, and the group has read only access, as well as the others.

What mechanism determines the permissions of these files that are created within the shares?

Thanks in advance.

---

### Post by Zulu-Zeffir on 2008-06-25
The solution of this problem is setting a default ACL. The following command ensures that all new files in /home/shared/ have all permissions (including write permissions) set for the group:

setfacl -d -m mask:007 /home/shared/

You should also set the sgid-bit for the directory and choose the wanted group using chgrp:

chgrp the_team /home/shared/
chmod g+s /home/shared/

---

### Post by cdenley on 2008-06-25
> **ffoeg said:**
> I've configured a Ubuntu 8 computer to act as a Samba server. It's a simple workgroup environment. I've set the two users that I want to access the shares in the same group. Then I set the owner of the shared folders to a user of the main group of the two users. The "group" of the folders to the group that the two users are in. I've even set others to be able to create and delete files to.

On theSamba server side, I've given access to all the users (read/write). I've confirmed that this has been entered into the smb.conf file.

Each share can be accessed by each user. But when a file is created by one user, that user becomes the owner, and the group has read only access, as well as the others.

What mechanism determines the permissions of these files that are created within the shares?

Thanks in advance.

```

[myshare]
create mask = 0660
directory mask = 0770

```

---

### Post by ffoeg on 2008-06-25
Thank you Zulu-Zeffir. But when I try the setfacl command, I get "setfacl : /sharename : Operation not supported

Please advise.

Thank you

---

### Post by cdenley on 2008-06-25
> **ffoeg said:**
> Thank you Zulu-Zeffir. But when I try the setfacl command, I get "setfacl : /sharename : Operation not supported

Please advise.

Thank you

By default, filesystems are not mounted with acl support. That is why I posted an alternative solution within samba.

---

### Post by hyper_ch on 2008-06-25
I'd use force user and force group... so it will always be you who is the owner.

---

### Post by ffoeg on 2008-06-25
Thank you. The:
[myshare]
create mask = 0660
directory mask = 0770

worked great. Thank you very much for your help.

---

### Post by hyper_ch on 2008-06-26
```

force user = USER
force group = USER

```

---

