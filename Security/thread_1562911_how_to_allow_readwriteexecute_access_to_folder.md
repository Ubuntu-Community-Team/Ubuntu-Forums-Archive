---
title: "how to allow read/write/execute access to folder"
date: 2010-08-28
forum: Security
---

### Post by trojanworrier on 2010-08-28
Hi friends,

Please advise me how do I allow read, write and execute access to the folder and its all sub folders and files.

ABC@ABC-laptop:RES/NASA$ chmod -R 777 *
chmod: changing permissions of `ABC': Operation not permitted


ABC@ABC-laptop:~$ chmod 777 /RES/NASA
chmod: changing permissions of `/RES/NASA': Operation not permitted

I was executing above commands bout got errors as mentioned. please tell me how do I resolve it, I'm linux newbie.

attached is a screenshot of the folder's properties->permissions tab. as you can see all options are disabled in this tab.

Thanks...

---

### Post by dv3500ea on 2010-08-28
You must run:
```
sudo chmod -R 777 /RES/NASA
```

Note that it is generally not recommended to give files 777 permissions unless you absolutely need all users to have read, write and execute permissions. I will assume that you know what you are doing.

---

### Post by trojanworrier on 2010-08-28
I executed above command but stil getting the same result as shown in my previous attached screenshot :(

---

### Post by cariboo on 2010-08-28
Is this actuall a directory on your computer, or is it a mounted share? If it's a mounted share, then you only have to se the permissions on the mountpoint eg:

> sudo chmod -R 777 /media/<mountpoint>

Another thing to note is if this is a Windows partition, it can't use linux permissions. So setting permissions of the mount point will do what you need.

---

### Post by movieman on 2010-08-28
> **cariboo907 said:**
> Is this actuall a directory on your computer, or is it a mounted share?

Or is it an NFS mount? In that case, you generally can't change permission on files owned by root on the remote system because it's a huge security hole.

---

### Post by cariboo on 2010-08-28
> **movieman said:**
> Or is it an NFS mount? In that case, you generally can't change permission on files owned by root on the remote system because it's a huge security hole.

I agree with you, but should you be sharing directories owned by root via NFS?

---

