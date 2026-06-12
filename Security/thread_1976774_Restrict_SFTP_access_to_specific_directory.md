---
title: "Restrict SFTP access to specific directory"
date: 2012-05-09
forum: Security
---

### Post by spookybathtub on 2012-05-09
Hi.  I'll start off by saying, I need help with an OS X server.  But the Apple Discussions forum is unlikely to help with this kind of thing, and OpenSSH is exactly the same, so I'm posting here.

I'm trying to setup a few user accounts for restricted SFTP access.  I've read about the ChrootDirectory option in sshd_config, but the trouble is, that requires the chosen directory to be owned by root and non-writable to others.  The way my filesystem is organized, that's not practical.  The directory I'd like to chroot (called CDrips) is on a hard drive not owned by root.  Currently it looks like this:
```
$ pwd
/Volumes/RAID1
$ ls
total 32
drwxrwxr-x    9 server        staff    374 May  5 14:21 ./
drwxrwxrwt@   6 root          admin    204 May  8 23:10 ../
drwxrwxr-x+ 424 radiosharing  staff  14416 May  8 16:21 CDrips/
...
```
Also, CDrips needs to be writable by other users.  From what I've read, it seems like Chroot is not the right thing to do here, but I don't know what else to do.  Any advice would be appreciated.
Thanks.

---

### Post by phaemon on 2012-05-18
In Linux, you can get around this with mount --bind. For OSX, you'll need a utility which you can read about at [http://sizzo.org/wp/2008/12/mount-bind-on-osx](http://sizzo.org/wp/2008/12/mount-bind-on-osx)

Be careful with this. mount bind is *not* a link, so if you try and rm  -rf on it you'll be removing the original files. You need to umount it  first.

Here is the complete procedure for creating a "radio" sftp user on linux  for example. "$" indicates a prompt (type the rest; not the $ sign!). #  indicates a comment follows: you don't have to type those bits.  Adjust  for MacOS as you see fit:
```

$ sudo adduser radio # create a user called "radio"

```Have the following in your /etc/ssh/sshd_config
```

Subsystem sftp internal-sftp
   Match Group sftp
          ChrootDirectory %h
          ForceCommand internal-sftp
          AllowTcpForwarding no

```Then the commands are:
```

$ sudo adduser radio sftp # add radio to the sftp group
$ sudo usermod -s /bin/false radio # don't allow them to get a shell

$ sudo rm /home/radio/.bash* # they don't need these files
$ sudo rm /home/radio/.profile

$ sudo chown root:root /home/radio # made root so chroot works
$ sudo chmod 0755 /home/radio # make sure the permissions are correct

$ sudo mkdir /home/radio/CDrips # make a CDrips dir for them to save into
$ sudo chown radio:radio /home/radio/CDrips # that's owned by them

```
At this point they have a normal chrooted sftp setup, with a "CDrips" dir they can upload to.

Now, bind our "CDrips" dir to the one we want to give access to :
```

$ sudo mount --bind /Volumes/RAID1/CDRips /home/radio/CDrips

```So even though /Volumes/RAID1 isn't owned by root, the chroot will still  work. The dir names don't matter: you could have called it  /home/radio/CDrips if you wanted. Or indeed, nearly anything at all...

---

