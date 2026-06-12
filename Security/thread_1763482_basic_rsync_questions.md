---
title: "basic rsync questions"
date: 2011-05-20
forum: Security
---

### Post by methodtwo on 2011-05-20
Hi there
I have an OpenBSD and a FreeBSD system and a mac. I also have a Ubuntu server. What i would like to do is back up all these systems to an external hard-drive using rsync when the external usb disk is connected to my Ubuntu box.If i format the external usb disk with cfdisk and the create a non-bootable ext3 file system on this external disk and create and put all the necessary public keys on the Linux box then from the BSD's or the mac issue the command:
Code:

```
#rsync --progress -avhe ssh --delete / user@ubuntuBox:/usb/disk/path/dir/
```

Will this back up the entire systems so that they can be restored in the event of an emergency? I should store each OS just in a separate disk file of the external usb drive each time right??
Because i would rather not have to format the external usb drive for each different OS.
Would this work? and would the restoration command for these BSD's be:

```
rsync -avze ssh UbuntuBox:/usb/disk/path /

```
I just need to know the basics. I'm sure given that i'll be able to automate the process.
Thank you very much for any help or advice. I don't want to clone the disks for forensics. I just want to have a way of restoring to a clean OS. This is the most basic question:All the howto's never mention whether or not you have to have an rsync server running on the machine your backing up to. So do you just push or pull from one end of the connection only or do you have to have a client at one end and a server at the other, as is traditional?
Thank you very much please excuse how much of a n00b i am

---

### Post by CharlesA on 2011-05-20
I don't think you can copy everything from a running system. /dev and /proc are dynamically generated IIRC.

---

### Post by The Cog on 2011-05-20
I think it tries to copy them though, with lots of errors. I think it's best to name the top-level directories. Don't try to backup proc, sys or dev. Also be aware that it cannot copy /home/*/.gvfs folders, and the trying will cause an error which causes it not to perform the --delete action.

---

### Post by SeijiSensei on 2011-05-20
The easiest way to do multiple excludes is to put the "globs" in a file and use --exclude-from like this:

```

cat << EOF > /some/directory/rsync-excludes
/proc/
/sys/
/dev/
EOF

rsync -av .... --exclude-from=/some/directory/rsync-excludes

```

You can use multiple --exclude parameters instead, but I find it easier to put them in a file.  I'll often have other exclusions like "/backup/".

---

