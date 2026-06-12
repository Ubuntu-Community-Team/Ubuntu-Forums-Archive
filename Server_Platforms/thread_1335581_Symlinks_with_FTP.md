---
title: "Symlinks with FTP"
date: 2009-11-23
forum: Server Platforms
---

### Post by trobrock on 2009-11-23
I am trying to get my ftp server working on Ubuntu Server 9.04. I only want certain users to have web hosting, so for those users I create a folder in the /var/www/ dir for that and create a symlink in their home dir /home/USER/www -> /var/www/USER/ but the user cannot change directory into the symlinked folder.  I am using VSFTPD, is there a certain setting that needs set, or is there a different server software package that can handle symlinks?

---

### Post by lloyd_b on 2009-11-23
> **trobrock said:**
> I am trying to get my ftp server working on Ubuntu Server 9.04. I only want certain users to have web hosting, so for those users I create a folder in the /var/www/ dir for that and create a symlink in their home dir /home/USER/www -> /var/www/USER/ but the user cannot change directory into the symlinked folder.  I am using VSFTPD, is there a certain setting that needs set, or is there a different server software package that can handle symlinks?

Generally, FTP servers use a "chroot environment" for security.  No file that is outside of the chroot can be accessed.  In short - symlinks will not work (unless you want to seriously compromise the security of the FTP server).

What you *can* do is "bind" the directory to a new mount point, within the chroot.```
mount --bind /home/USER/www /var/www/USER
```Note that this must be run as root.

To automate this process, you can add the mounts into the "/etc/fstab" file, so that they'll be automatically mounted at system startup.  Just add a line like```
/home/USER/www /var/www/USER none bind 0 0
```

Assuming there aren't too users who need such access, this is a manageable solution.

Lloyd B.

---

### Post by Lars Noodén on 2009-11-24
> **trobrock said:**
> or is there a different server software package that can handle symlinks?

If your goal is to have people upload to the server without compromising the account, then you might look at using the sftp subsystem which is already built into the openssh-server you probably have running.  

Using that method you can also chroot the users right into their individual www subdirectories.

From the ssh server configuration: /etc/ssh/sshd_config
```

Subsystem sftp internal-sftp

Match Group webusers
   ChrootDirectory %h/www
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

```

That allows them to use sftp clients like Filezilla, Konqueror, Dolphin, and so on.

---

