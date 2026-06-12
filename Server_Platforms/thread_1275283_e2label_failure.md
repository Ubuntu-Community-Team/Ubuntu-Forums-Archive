---
title: "e2label failure"
date: 2009-09-25
forum: Server Platforms
---

### Post by wareagle on 2009-09-25
I am managing a server with Ubuntu Server 8.10 and can't seem to label a drive correctly.  Here is the output:

```
root@dev:~# e2label /dev/sda1 LOCALBACKUP
root@dev:~# e2label LOCALBACKUP
e2label: No such file or directory while trying to open LOCALBACKUP
Couldn't find valid filesystem superblock.
```

Specifically I want to be able to mount it in fstab with this label.

Any idea why this isn't working?

---

### Post by drs305 on 2009-09-25
I can generate the invalid superblock error message when I don't run the command with "sudo" but it looks like you are already running as root.

You can also try:
```

sudo tune2fs -L LOCALBACKUP /dev/sda1

```
Depending on how you are logged in, "sudo" may not be necessary.

---

### Post by falconindy on 2009-09-25
> **wareagle said:**
> I am managing a server with Ubuntu Server 8.10 and can't seem to label a drive correctly.  Here is the output:

```
root@dev:~# e2label /dev/sda1 LOCALBACKUP
root@dev:~# e2label LOCALBACKUP
e2label: No such file or directory while trying to open LOCALBACKUP
Couldn't find valid filesystem superblock.
```Specifically I want to be able to mount it in fstab with this label.

Any idea why this isn't working?
You ran e2label twice and only once you received error feedback? Were the 2 error messages generated solely by the second execution? 

Running e2label successfully generates no feedback. So, from what you've provided here, you **did **change the label on /dev/sda1.

---

### Post by wareagle on 2009-09-26
Yes, that is the exact output.  I set a label on sda1, but when I try to read drives with that label, it doesn't find it.

---

### Post by drs305 on 2009-09-26
> **wareagle said:**
> Yes, that is the exact output.  I set a label on sda1, but when I try to read drives with that label, it doesn't find it.

I thought you were 'condensing' error messages. But falconindy is correct. If you ran the first one and nothing appeared to happen, the partition should have been labeled correctly.

In this case, terminal would only produce ouptut if there was a failure or error. Since there was no message after you ran the first command, it means the system believes the command was executed properly.

Run this command and see if the label shows up:
```

sudo blkid

```

If the label shows up, tell us how you are trying to read the drives, and provide the command if mounting the drives via terminal.

---

### Post by falconindy on 2009-09-26
> **wareagle said:**
> Yes, that is the exact output.  I set a label on sda1, but when I try to read drives with that label, it doesn't find it.
Then you need to post your relevant entries in /etc/fstab. This isn't an error with e2label at all.

---

### Post by wareagle on 2009-09-28
> **drs305 said:**
> I thought you were 'condensing' error messages. But falconindy is correct. If you ran the first one and nothing appeared to happen, the partition should have been labeled correctly.

In this case, terminal would only produce ouptut if there was a failure or error. Since there was no message after you ran the first command, it means the system believes the command was executed properly.

Run this command and see if the label shows up:
```

sudo blkid

```

If the label shows up, tell us how you are trying to read the drives, and provide the command if mounting the drives via terminal.

It does show up there:

```
/dev/sda1: LABEL="LOCALBACKUP" UUID="bce2e1c7-fccc-48d1-925f-1e11d0c56209" TYPE="ext3"
```

---

### Post by wareagle on 2009-09-28
> **falconindy said:**
> Then you need to post your relevant entries in /etc/fstab. This isn't an error with e2label at all.

Here is the fstab entry:

```
LABEL=LOCALBACKUP               /localbackup            ext3    defaults        0 0
```

---

### Post by drs305 on 2009-09-28
> **wareagle said:**
> 
```
LABEL=LOCALBACKUP  /localbackup  ext3    defaults   0 0
```

And the folder /localbackup exists and is owned by you (or you at least have rights to view it)?

Any errors if you mount it manually:
```

sudo umount -a # Unmount non-system partitions
sudo mount -a  # Checks all auto fstab entries
sudo umount -a
sudo mount -L LOCALBACKUP /localbackup  # Checks manually

```

---

