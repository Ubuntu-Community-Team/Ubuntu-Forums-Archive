---
title: "Adding a remote user securely?"
date: 2009-10-29
forum: Security
---

### Post by hyperyoda on 2009-10-29
What is the best way to add a remote user onto my VPS server?

I want them to have some web space on apache and be able to ssh in and learn but I don't want them able to run any command or get intro trouble (whether deliberately or accidentally!) so I was thinking about chroot but I was wondering what other solutions exist. I don't want this to affect all user accounts only for this one remote user. Thanks.

---

### Post by Lars Noodén on 2009-10-29
If you don't want them to run *any commands at all* then let the sftp subsystem do the work for you and chroot them.  Put them in a group called 'trainingwheels' or another more respectful name.  Then modify sshd_config to chroot them.

The excerpt below goes at the end of sshd_config and allow remote users to access their home directories, and only their home directories.  Further, they cannot run programs on the remote machine and may only work via an sftp client.  Is that what you wanted?  Or were you thinking of setting their login shell to rbash?

```

Subsystem sftp internal-sftp

Match Group trainingwheels
  ChrootDirectory /home/%u
  AllowTCPForwarding no
  X11Forwarding no
  ForceCommand internal-sftp

```

When they no longer need the training wheels, move them out of that group.

---

### Post by hyperyoda on 2009-10-29
> **Lars Noodén said:**
> If you don't want them to run *any commands at all* then let the sftp subsystem do the work for you and chroot them.  Put them in a group called 'trainingwheels' or another more respectful name.  Then modify sshd_config to chroot them.

The excerpt below goes at the end of sshd_config and allow remote users to access their home directories, and only their home directories.  Further, they cannot run programs on the remote machine and may only work via an sftp client.  Is that what you wanted?  Or were you thinking of setting their login shell to rbash?

```

Subsystem sftp internal-sftp

Match Group trainingwheels
  ChrootDirectory /home/%u
  AllowTCPForwarding no
  X11Forwarding no
  ForceCommand internal-sftp

```

When they no longer need the training wheels, move them out of that group.

Thanks Lars. This solution will work great!

---

