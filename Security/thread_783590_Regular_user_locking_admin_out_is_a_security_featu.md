---
title: "Regular user locking admin out is a security feature?"
date: 2008-05-05
forum: Security
---

### Post by blastus on 2008-05-05
Can someone please explain to me to how having the ability to lock an administrator (anyone who is a member of the local admin group) out of certain files on an NTFS partition on a local Windows XP machine is a security feature? Am I missing something or does this go completely against the notion that an admin has or should have full access to any user created file in the local file system? If this is true are there any other operating systems except Windows that have this feature?

---

### Post by hyper_ch on 2008-05-06
wouldn't that better be asked in a windows forum or in the windows section here?

---

### Post by rickyjones on 2008-05-06
> **blastus said:**
> Can someone please explain to me to how having the ability to lock an administrator (anyone who is a member of the local admin group) out of certain files on an NTFS partition on a local Windows XP machine is a security feature? Am I missing something or does this go completely against the notion that an admin has or should have full access to any user created file in the local file system? If this is true are there any other operating systems except Windows that have this feature?

Anyone in the "Administrators" group, or who is "Administrator" will be able to access the file, even if the NTFS permissions are set to deny or are set so that the Administrator account is not listed.

How?

Ownership. Administrators can always change ownership of a file or folder. Changing ownership to himself will allow him to modify the permissions.

I had to do that earlier this year at work... 

-Richard

---

