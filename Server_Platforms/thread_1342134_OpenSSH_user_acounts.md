---
title: "OpenSSH user acounts"
date: 2009-11-30
forum: Server Platforms
---

### Post by NertSkull on 2009-11-30
So is there a way to assign user accounts/priviledges based on public/private key settings.

I want to set something up so that people can log into my machine but only have access to directories I specify.  But I don't want to create a bunch of users with different access permissions.

Is there a way to assign public keys I gather from others to only allow that individual to have access to a particular set of directories?

hopefully that made sense.

---

### Post by BkkBonanza on 2009-11-30
I'm not aware of any way to do that but to find out for sure read the docs for sshd.
Type, 
man ssh_config

You may find a simpler solution using Ubuntu One or Dropbox.

---

### Post by NertSkull on 2009-11-30
Yeah I've tried going through the man but haven't found anything that helps. 

How do ISPs do this?  Do they just make lots of user accounts and set permissions that way?  Is that my best option?

And if so, is there a way to make users, but only have certain ones show up in my switch user list/menu?

---

### Post by ktrnka on 2009-11-30
Sounds like you should setup a chrooted ssh jail:

[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny]("http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny")

Then you can link files to the user's jail that you want to allow them access.

---

### Post by hictio on 2009-11-30
Another option you might consider is using Restricted Shell.

[Howto create chrooted Openssh SFTP without shell access through rssh](http://ubuntuforums.org/showthread.php?t=128206)
[How to: Restrict Users to SCP and SFTP and Block SSH Shell Access with rssh](http://www.cyberciti.biz/tips/rhel-centos-linux-install-configure-rssh-shell.html)

---

### Post by Lars Noodén on 2009-12-01
> **hictio said:**
> Another option you might consider is using Restricted Shell.

@hictio: Restricted Shell is [rbash](http://manpages.ubuntu.com/manpages/karmic/en/man1/rbash.1.html), [rksh](http://www.openbsd.org/cgi-bin/man.cgi?query=rksh) or something similar.  They are just regular shells which accept the **-r** restricted option.

**rbash** or **bash -r** is useful when you want to give shell access, but limit which programs are available because only those the search path are available.

---

### Post by Lars Noodén on 2009-12-01
> **NertSkull said:**
> So is there a way to assign user accounts/priviledges based on public/private key settings.

I want to set something up so that people can log into my machine but only have access to directories I specify.  But I don't want to create a bunch of users with different access permissions.

Is there a way to assign public keys I gather from others to only allow that individual to have access to a particular set of directories?

hopefully that made sense.

If you look at the [authorized_keys file format](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd) section in the manual for sshd, you can see a list of the options which can be embedded in the key itself.  Maybe it could be done using **command="/usr/sbin/chroot *something...*"**, but you'd have to add rbash to the chroot jail.

To do any of those safely, you'll have to make the home directory of that user neither owned nor writeable by that user, same with that user's .ssh directory and .ssh/authorized_keys file.  So any configuration files and subdirectories will have to be added to the home directory manually by you, but sub-sub directories can be added by the user.  

However, you'll notice that chroot is missing from those options.  


To chroot a user, you'll need to set **ChrootDirectory** in /etc/ssh/sshd_config.  If you do that for a group, then any user in that group is affected.

```

Subsystem sftp internal-sftp

# members of the group sftp-only, are chrooted to their 
# individual home directory
Match Group **sftp-only**
	ChrootDirectory **%h**
	AllowTCPForwarding no
	X11Forwarding 
	ForceCommand **internal-sftp**

```

Chroot can't go up a level nor use symlinks to go across.  So everything you want them to have access to must be under the hierarchy identified by ChrootDirectory.

```

Subsystem sftp internal-sftp

# members of the group sftp-only, are chrooted to their 
# individual home directory
Match Group **sftp-only**
	ChrootDirectory **/var/www/htdocs**
	AllowTCPForwarding no
	X11Forwarding 
	ForceCommand **internal-sftp**

```

---

### Post by NertSkull on 2009-12-01
Excellent!  I will have to try some of these this weekend when I get the time.  I appreciate the help, I'm sure I'll have more questions come up.

---

### Post by Lars Noodén on 2009-12-02
Of the two, the ChrootDirectory method is practical and easy.

---

