---
title: "ssh - user confined to one dir (disk)"
date: 2009-10-17
forum: Server Platforms
---

### Post by n.l.o on 2009-10-17
Hello

I tried to google this a lot, but didn't find a solution (I thought I did but instead I screwed up the server; did a "sudo chmod o-rwx -R /", I think I have to reinstall everything - good time to upgrade I guess).

Anyway what I want is to add a extra user, who can log in via SSH but should only be allowed to access ONE disk (like "/media/disk1"), so no home-dir either.

How do I do this??!

Magnus

---

### Post by Bachstelze on 2009-10-17
A user will always be able to browse his home dir. If you want to restrict a user to /media/sda1, it's easy: just make it the user's home dir.

---

### Post by Lars Noodén on 2009-10-18
> **n.l.o said:**
> Hello

I tried to google this a lot, but didn't find a solution (I thought I did but instead I screwed up the server; did a "sudo chmod o-rwx -R /", I think I have to reinstall everything - good time to upgrade I guess).


Yes. A re-install of the system might be the easiest way to fix that.  Some files must be available to everybody.  About the most you can do to tighten things down without breaking them, as far as a blanket restriction of permissions goes, is to set umask to 0077 or 0027 in /etc/login.defs, /etc/profile, and /etc/skel/.profile

> **n.l.o said:**
> 
Anyway what I want is to add a extra user, who can log in via SSH but should only be allowed to access ONE disk (like "/media/disk1"), so no home-dir either.

How do I do this??!

Magnus

Make sure that disk is mounted (at least once).  And then limit access to only that mount point using the "ChrootDirectory" directive in [sshd_config](http://manpages.ubuntu.com/manpages/jaunty/en/man5/sshd_config.5.html).  A primitive example below still allows login but those accounts which are members of the group 'ccretemaster' end up chrooted to /var/chroot-test.  

```

Match Group ccretemaster
   ChrootDirectory /var/chroot-test
   AllowTCPForwarding no
   X11Forwarding no

```

If you are providing only SFTP access  then little more needs to be done. Just make sure that the chroot directory points to the mount point for the device you are thinking of.

 [SIZE="1"]PS. "[områden i arbetslivet där datorer har stor betydelse](http://www.expressen.se/ledare/1.1663751/johanna-nylander-microsoft-hotar-var-demokrati)"[/SIZE]

---

### Post by n.l.o on 2009-10-18
Sweet, I will look in to it as soon as I get home. Have to check if I should change server version as well. Great replies.

Thanks!

---

### Post by n.l.o on 2009-10-21
Hello
I have Ubuntu server 8.04 and the modifications to sshd_config did not work. I couldnt even find the "ChrootDirectory" option in the man page of sshd_config.

Is there another way to do this?

Cheers
Magnus

---

### Post by Lars Noodén on 2009-10-21
> **n.l.o said:**
> Hello
I have Ubuntu server 8.04 and the modifications to sshd_config did not work. I couldnt even find the "ChrootDirectory" option in the man page of sshd_config.


I see the problem.  Hardy uses OpenSSH 4.7 and ChrootDirectory was only added starting with 4.9.  Sorry I missed that.  

[http://packages.ubuntu.com/hardy/openssh-server](http://packages.ubuntu.com/hardy/openssh-server)

It was release the same day I was looking for a way to chroot sshd, so from that perspective it has 'always' been there.  
I don't see openssh-server in hardy-[backports](https://help.ubuntu.com/community/UbuntuBackports).  :k

I'd still say that ChrootDirectory is the correct way to do it.  However, that does mean fiddling with [apt-pinning](http://wiki.debian.org/AptPinning) or something like that to get at the newer version of sshd.
[INDENT][http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)[/INDENT]

A more awkward way would be to run a second instance of sshd, with it's own configuration file, keys, the whole nine yards, and chroot that the standard way...

---

