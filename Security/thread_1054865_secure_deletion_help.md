---
title: "secure deletion help"
date: 2009-01-30
forum: Security
---

### Post by grimey44 on 2009-01-30
ive been looking for a simple way to securely remove or shred all the un-used space on my hard drive. i dont want to delete the files that i use though.

---

### Post by hyper_ch on 2009-01-30
why do you want to securely wipe all unused space?

---

### Post by Tubes6al4v on 2009-01-30
Ok, on second look at this thread, I have an idea. It may take a little while but you could...

- Back up all your data
- Fill the entire partition with random bits
- Restore data

---

### Post by ratmandall on 2009-01-30
[http://www.dban.org/](http://www.dban.org/)

---

### Post by cdenley on 2009-01-30
```

sudo apt-get install secure-delete
sudo sfill /

```
This will take a long time. If you're not patient, look at what options you have to make it faster but less secure.
```

man sfill

```

---

### Post by grimey44 on 2009-01-30
so i install the secure delete 
and then enter

"man sfill" ?

and that code securely deletes the free space on the hard drive without loosing my data?

---

### Post by cdenley on 2009-01-30
> **grimey44 said:**
> so i install the secure delete 
and then enter

"man sfill" ?

and that code securely deletes the free space on the hard drive without loosing my data?

Re-read my post. That command shows you the manpage which you can use as a reference if you want to use options to make it go faster. If the default options work for you, and you don't mind having your computer on for a day or two depending on the speed and free space of your drive/filesystem, and you want to wipe the free space on your root filesystem, then use:
```

sudo sfill /

```

---

### Post by cariboo on 2009-01-30
> man sfil

Is the command to view the sfill manual page, which must be entered in a Applcations-->Accessories-->Terminal.

Jim

---

### Post by cdenley on 2009-01-30
> **cariboo907 said:**
> Is the command to view the sfill manual page, which must be entered in a Applcations-->Accessories-->Terminal.

Jim

Yes. Commands are entered in the terminal.

---

