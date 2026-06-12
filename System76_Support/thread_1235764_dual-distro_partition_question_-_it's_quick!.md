---
title: "dual-distro partition question - it's quick!"
date: 2009-08-09
forum: System76 Support
---

### Post by glacialfury on 2009-08-09
I'm planning on installing Ubuntu 8.04 LTS and OpenSUSE 11.1 with the following partition setup.  Let me know if anything is whacky please.

120gb drive

swap: 4 gb (system has 4gb ram)
ubuntu root: 12 gb
opensuse root: 12 gb
single home directory: ~90

My real question is, will I have any problems in sharing a single home directory amongst multiple distros?  Or do they each need their own to avoid application problems?

---

### Post by Jenkins1 on 2009-08-09
erm well I unfortunately can't be much use but I thought the swap was suppose to be twice the size of the ram.

---

### Post by jdb on 2009-08-09
> **glacialfury said:**
> I'm planning on installing Ubuntu 8.04 LTS and OpenSUSE 11.1 with the following partition setup.  Let me know if anything is whacky please.

120gb drive

swap: 4 gb (system has 4gb ram)
ubuntu root: 12 gb
opensuse root: 12 gb
single home directory: ~90

My real question is, will I have any problems in sharing a single home directory amongst multiple distros?  Or do they each need their own to avoid application problems?

Your suspicions are correct, sharing a home directory will likely cause problems.

What I do is use a partion I mount as /data & put links to it in my home directories.
For instance:
```
mkdir /data
mount /dev/sda10 /data
# put an entry to do the above in /etc/fstab

mv ~/.thunderbird/1i5p3q25.default/prefs.js   /data
ln -s /data/prefs.js   ~/.thunderbird/1i5p3q25.default
mv ~/.thunderbird/1i5p3q25.default/abook.mab   /data
ln -s /data/abook.mab   ~/.thunderbird/1i5p3q25.default
mv ~/.thunderbird/1i5p3q25.default/Mail   /data
ln -s /data/Mail   ~/.thunderbird/1i5p3q25.default

mv ~/Desktop   /data
ln -s /data/Desltop   ~/

mv ~/Pictures   /data
ln -s /data/Pictures   ~/

etc.

```

Put your stuff in /data and put links to it in your home directories.
Let each home directory accumulate it's own application configuration stuff.

If you are using the same application in two OSs & you have spent a lot of time configuring it,
you can usually figure out what files to copy from one home directory to the other.

jdb

---

### Post by jdb on 2009-08-09
> **Jenkins1 said:**
> erm well I unfortunately can't be much use but I thought the swap was suppose to be twice the size of the ram.

That used to be the golden rule of thumb.
Now machines have so much ram that swap is rarely used.
The exception is during hibernation when all the ram in use is sent to swap.
So if you are going to use hibernate you need a swap space at least as big as your ram.

jdb

---

### Post by glacialfury on 2009-08-09
Thank you; those are very good answers, and I will follow your advice.

---

