---
title: "Superuser in samba file server"
date: 2008-06-02
forum: Server Platforms
---

### Post by Earendil27 on 2008-06-02
hi! I'm new to samba. I'm wondering how I can give 1 user account rwx access rights to all files in all directories.  My intention is to make administration of the file system easier-e.g. I can just login to that account and move files and directories wherever I want.

My initial thoughts:
apply setfacl recursively on the entire directory to allow superuser to access all fiels. My concern though is : will this not affect the performance of the system in the long run. especially as more files are added to the directory

Any other suggestions?

Thanks in advanced/

---

### Post by Uluen on 2008-06-02
Any reason why you can't use sudo?

If you're lazy (like me), do a ```
sudo passwd root
``` and su root.

You could also ```
chown -R user:user /folder
```

---

### Post by Earendil27 on 2008-06-02
Sorry for not making myself clear.  What I meant was, a user logging on to the Samba PDC and having rwx access to all of the files.  (I'm not sure if you'd recommend this.)

Actually, I'm in the process of migrating the files from our old netware server to the samba server- and I was trying to do it from a client PC.

Now I realized I can just copy all files to one share in Samba and just fix the access permissions and directory structures from the samba server itself.

However, if what I mentioned in the first paragraph is still doable, I may have some future use for it.

Thanks.

---

