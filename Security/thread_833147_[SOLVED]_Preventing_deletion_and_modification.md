---
title: "[SOLVED] Preventing deletion and modification?"
date: 2008-06-18
forum: Security
---

### Post by daltonlaffs on 2008-06-18
Hello Ubuntu peoples (and other assorted Linux distro peoples),

There's a file on my system that I need to prevent writing and deletion to/of, but still allow reading and executing in Terminal.

I've tried chown-ing the file to Root and chmod-ing the file to 755, but it can still be deleted, and even worse, can't be restored from the Trash.

Is there any way to do this?

Thanks in advance, guys :)

---

### Post by Dr Small on 2008-06-18
```
chmod 775 file
chown root:root file
```

---

### Post by daltonlaffs on 2008-06-18
Nope, it can still be deleted by anyone... any other ideas?

---

### Post by John.Michael.Kane on 2008-06-18
Have you tried.

```
chmod 400 file
```
or
```
chmod 444 file
```

---

### Post by daltonlaffs on 2008-06-18
> **John.Michael.Kane said:**
> Have you tried.

```
chmod 400 file
```
or
```
chmod 444 file
```

Nope, still deletable. I don't think we can pull this off in regular file access, there's got to be some other way...

---

### Post by cdenley on 2008-06-18
The file can be deleted by anyone with write access to the parent directory.

```

cd /path/to/parent
sudo chown root:root .
sudo chmod 755 .

```

---

### Post by brian_p on 2008-06-18
> **daltonlaffs said:**
> There's a file on my system that I need to prevent writing and deletion to/of, but still allow reading and executing in Terminal.

This file is in your home directory?

Which users do you want to be prevented from deleting the file?

---

### Post by Biochem on 2008-06-18
chattr +i file

will prevent even root to accidentally delete or modify the file unless chattr -i is invoked first

works on ext2/3

---

### Post by daltonlaffs on 2008-06-18
Yes!

Thanks to Cdenley and Biochem, I used both of your methods on the folder (not any individual file) and now the entire folder is read and delete-proof!

Thanks a billion, guys! :guitar:

---

### Post by Dr Small on 2008-06-18
> **Biochem said:**
> chattr +i file

will prevent even root to accidentally delete or modify the file unless chattr -i is invoked first

works on ext2/3
Then that's what I need to do to /boot, because last night I accidentially deleted it :D

---

