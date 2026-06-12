---
title: "securing /tmp files"
date: 2008-02-26
forum: Security Discussions
---

### Post by SonicSteve on 2008-02-26
Morning folks,
I read this article on techrepublic this morning. I was curious of what you all think. I'm not an expert on permissions and security yet so to me it sounds unnecessary.  Does it have merit?

[http://blogs.techrepublic.com.com/opensource/?p=171&tag=nl.e011](http://blogs.techrepublic.com.com/opensource/?p=171&tag=nl.e011)
> 
On a typical Linux system there will be at least two, if not more, directories or partitions meant to hold temporary files. There is always the /tmp directory, and often a /var/tmp directory as well. With newer Linux kernels, there can also be /dev/shm, which is mounted using the tmpfs filesystem.

One problem with directories meant to store temporary files is that they can often be targeted as places to store bots and rootkits that compromise the system. This is because in most cases, anyone (or any process) can write to these directories. Insecure permissions are problematic as well; most Linux distributions set the sticky bit on directories meant to contain temporary files — this means that user A cannot remove a file belonging to user B, and vice versa. Depending on the permissions of the file itself, user A may be able to view and/or modify the contents of that file, however.

A typical Linux installation will set /tmp as mode 1777, meaning it has the sticky bit set and is readable, writable, and executable by all users. For many, that’s as secure as it gets, and this is mostly because the /tmp directory is just that: a directory, not its own filesystem. The /tmp directory lives on the / partition and, as such, must obey its mount options.

A more secure solution would be to set /tmp on its own partition, so that it can be mounted independent of the / partition and have more restrictive options set. An example /etc/fstab entry for a /tmp partition might look like:

/dev/sda7 /tmp ext3 nosuid,noexec,nodev,rw 0 0

This would set the nosuid, noexec, and nodev options, meaning that no suid programs are permitted, nothing can be executed from that partition, and no device files may exist.

You could then remove the /var/tmp directory and create a symlink pointing to /tmp so that the temporary files in /var/tmp also make use of these restrictive mount options.

The /dev/shm virtual filesystem also needs to be secured as well, and this can be done by changing /etc/fstab. Typically, /dev/shm is simply mounted with the defaults option, which isn’t enough to properly secure it. Like the fstab entry shown for /tmp, it should have more restrictive mount options:

none /dev/shm tmpfs defaults,nosuid,noexec,rw 0 0

Finally, if you don’t have the ability to create a fresh /tmp partition on existing drives, you can use the loopback capabilities of the Linux kernel by creating a loopback filesystem that will be mounted as /tmp and can use the same restrictive mount options. To create a 1GB loopback filesystem, execute:

# dd if=/dev/zero of=/.tmpfs bs=1024 count=1000000

# mke2fs -j /.tmpfs

# cp -av /tmp /tmp.old

# mount -o loop,noexec,nosuid,rw /.tmpfs /tmp

# chmod 1777 /tmp

# mv -f /tmp.old/* /tmp/

# rmdir /tmp.old

Once this is complete, edit /etc/fstab to have the loopback filesystem mounted automatically at boot:

/.tmpfs /tmp ext3 loop,nosuid,noexec,rw 0 0

Little things like ensuring proper permissions and using restrictive mount options will prevent a lot of harm coming to the system. If a bot lands on a filesystem that is unable to execute, that bot is essentially worthless.


---

### Post by SonicSteve on 2008-02-26
I really thought someone would have something to say about this. Are you all apathetic about it? Do you think it's ridiculous?

---

### Post by RedRat on 2008-02-26
I might be naive and perhaps don't understand the problem all that well, being a newbie, but if one were really worried than you should not log in as Administrator but instead created a separate user account. That way, if trouble occurred you could log in as Administrator and remove any and all files.

Have to rely on more Linux experts for their opinion on this.

---

