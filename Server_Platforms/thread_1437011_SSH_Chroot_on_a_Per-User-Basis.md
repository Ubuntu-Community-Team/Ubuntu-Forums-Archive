---
title: "SSH Chroot on a Per-User-Basis"
date: 2010-03-23
forum: Server Platforms
---

### Post by samurailink3 on 2010-03-23
Heya! I'm attempting to give a few buddies encrypted storage space through sftp using truecrypt. I have it worked out to the point where the truecrypt volume is automatically mounted when the user logs on, and dismounted when they log off.

I would like to restrict each person to their individual home folders. This way, I can control exactly how much space each user is able to use (through the size of the truecrypt volume), while maintaining security through the network due to using SFTP.

I've been looking around, and the only thing I can see is restricting a large group of users to a single directory, this won't work, I need each person to be locked down to their personal home directory.

My end goal is to have these volumes "mountable" in Windows through the use of Windows network drives (on a wide network, not through samba on local), or by using expandrive or a similar program.

Any ideas on how I can lock these users to their respective home folders?

---

### Post by cdenley on 2010-03-23
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

Using "ChrootDirectory /home/%u" chroots all users within that scope to their home directory, assuming it is /home/<username>. I'm assuming you're using ubuntu 9.10?
```

lsb_release -id

```

---

### Post by sublimation on 2010-03-23
[This thread]("http://ubuntuforums.org/showthread.php?t=1432043") was actually looking to do more specific chrooting than you.

You should have no problem doing what you want:
i.e by editing */etc/ssh/sshd_config* and adding
```
Match Group restricted_users
    ChrootDirectory %h
    AllowTcpForwarding no
```
might be the way to go.
Just add all users you want locked into their home directories to the group *restricted_users* and they'll be locked home.

just make sure your OpenSSH is fairly up-to-date. I think the feature showed up in 5.0


Edit: Just saw cdenley's link, good article. Follow that.

---

### Post by samurailink3 on 2010-03-24
Thank you both very very much!! These articles are extremely helpful. I believe I have everything set correctly, but I'm still getting an error message:
> 
root@spaghetti:~# sftp bob@localhost
Connecting to localhost...
"When someone asks you if you're a god, you say YES!"
Winston Zeddemore - Ghostbusters (1984)
bob@localhost's password:

```

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

UsePAM yes

DenyUsers mediabuddy

Match group shroud_users
        X11Forwarding no
        AllowTcpForwarding no
        ChrootDirectory /home/%u
        ForceCommand internal-sftp

```

And, yes, I am on 9.10 x64, and I believe that openssh-server is on 5.1.

```

root@spaghetti:~# apt-cache policy openssh-server
openssh-server:
  Installed: 1:5.1p1-6ubuntu2
  Candidate: 1:5.1p1-6ubuntu2
  Version table:
 *** 1:5.1p1-6ubuntu2 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by cdenley on 2010-03-24
Where did that ghostbusters quote come from, and where is the error message? It was prompting for bob's password. Did you enter it?

---

### Post by samurailink3 on 2010-03-24
Wow.. I failed at copy/paste...

The quote was from the banner message I have set up, the error was:
```

Couldn't read packet: Connection reset by peer

```

Just figured it out, too!
Home folder must be owned by root.root and may not be writable by other users (I currently have 755 permissions set).
This article helped a ton: [http://undeadly.org/cgi?action=article&sid=20080220110039]("http://undeadly.org/cgi?action=article&sid=20080220110039")

---

### Post by sublimation on 2010-03-24
Glad we were able to help, and that your errors weren't so hard to fix. Let us know if there's anything else we can help with!

Don't forget to mark it Solved when you're satisfied ;)

---

### Post by samurailink3 on 2010-03-24
Seems that with the 755 permission set, with root as the owner, I can read files just fine, but I can't edit/delete/create them (obviously) (DOH!).

I'm trying different things out, any ideas?

Right now, I've got a new folder inside of the TrueCrypt volume that has bob as the owner, this seems to work out perfectly, but I'd rather have the root of the home directory writable by bob. Let me know if you have any ideas.

---

### Post by cdenley on 2010-03-24
> **samurailink3 said:**
> Seems that with the 755 permission set, with root as the owner, I can read files just fine, but I can't edit/delete/create them (obviously) (DOH!).

I'm trying different things out, any ideas?

The users cannot write to the chroot directory.
> 
**ChrootDirectory**
             Specifies a path to chroot(2) to after authentication.  This
             path, and all its components, must be root-owned directories that
             are not writable by any other user or group.

You can allow them to write to subdirectories, though.

---

### Post by sublimation on 2010-03-24
try setting /home to the chrooted directory. Then ensure that each /home/username is owned by that user and you could give that 700 permissions if you like.

Another option would be to chroot them to their home as you are now, but give them ownership of all subdirectories, so they can't actually add anything to /home/username but they can do whatever they want to the subdirectories.

Edit: whoops I guess I was a bit too late =\

---

### Post by samurailink3 on 2010-03-24
Yea... I guess I could create some kind of directory structure for them, try to keep things organized. But since I'm setting this up for each individual user by hand (more or less), I'm trying to save time (I should just write a script for it...). In the end, it should work out nicely in the end.

Just out of curiosity, know of any open source software for mounting sftp drives as network drives in Windows?

Either way, you guys have been a HUGE help to me. Thanks a ton! Each time I come to this community, I leave smarter than when I entered. Thanks again!

---

