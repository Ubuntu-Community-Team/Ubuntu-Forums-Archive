---
title: "change ownership of files on HFS plus file system"
date: 2008-02-14
forum: Security Discussions
---

### Post by gorilly on 2008-02-14
a friends mac died on him

i put his hard drive into my ubuntu machine because nothing else would seem to read it.

i cant move his documents because i dont have permission to read them, also i am not the owner so there is nothing i can do.

when i sudo chown -hR michael /media/disk it just tells me its a read only file system...

how do i get around this?

thanks!

---

### Post by welsh_spud on 2008-02-16
I just had a similar problem to you, trying to mount a HFS+ disk in Ubuntu, but I think I solved it.

Depending on what your hard disk is called, you can mount the drive by putting into the command line:

```
mkdir ~/Mac
```

then

```
sudo mount -t hfsplus /dev/sda ~/Mac
```

Assuming the disk is called sda...

I found out what my drive was called by using the command line tool 'parted' to list all my drives

```
sudo parted
```

```
print all
```

Should list all the hard disks along with their drive name

If that all works, you should find your disk mounted in your home folder :)

---

