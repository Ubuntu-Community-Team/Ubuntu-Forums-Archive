---
title: "encfs backups: restoring multiple sources"
date: 2017-09-14
forum: Security
---

### Post by macho3 on 2017-09-14
I'm backing up parts of my Ubuntu system, encrypted using encfs, but restoring from multiple sources doesn't work.

I've backed up ~ without issue, accepting encfs's default options, choosing a strong password, and using its --reverse flag to rsync it to a remote machine. These files are restorable without issue.

But I've had trouble more recently adding a backup of /etc. I again accepted encfs's default options and used the same strong password as for the backup of ~. My understanding is that it is also using the same ~/.encfs6.xml file.

Although the remote machine is populated with what appear to be a properly encrypted tree of /etc, when I try to decrypt it using my general .encfs6.xml and the overarching password, the mounted "decrypted" partition is empty.

Any thoughts on what I'm doing wrong?

Is there a more appropriate forum for encfs questions? 

I'm aware of some of the recent vulnerabilities that have been discussed with this mode of encryption, but I'm not aware of any other mature, free software encryption scheme with the --reverse function to use as an alternative.

Thanks!

---

### Post by macho3 on 2018-02-13
Oops: I was totally wrong about this, another .encfs6.xml file is created in /etc and I have to use that.

---

