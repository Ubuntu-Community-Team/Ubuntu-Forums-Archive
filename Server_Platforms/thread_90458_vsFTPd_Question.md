---
title: "vsFTPd Question"
date: 2005-11-15
forum: Server Platforms
---

### Post by hostile on 2005-11-15
Hi Everyone,

I was wondering if anyone knows how to jail vsftpd to a particular directory. In other words, I'm looking for an equivalent directive to that of ProFTPd's "Default Root".

This way, when each user logs into the FTP server, they all see the same dir structure.

TIA.

---

### Post by Nano on 2005-11-15
[QUOTE=hostile]Hi Everyone,

I was wondering if anyone knows how to jail vsftpd to a particular directory. In other words, I'm looking for an equivalent directive to that of ProFTPd's "Default Root".

This way, when each user logs into the FTP server, they all see the same dir structure.

TIA.[/QUOTE]

Well, you can always edit /etc/passwd and set the home directory to the folder you want.

Just do:
sudo gedit /etc/passwd

---

### Post by krewemaynard on 2005-11-16
Here's an HTML version of the vsftpd man page: [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

I use vsftpd at work, and restrict the user from going above the designated home directory. Can't remember the exact setting, but it's in the docs. Good luck :)

---

### Post by hostile on 2005-11-16
Thanks for the replies, guys, but I'm looking for an equivalent to ProFTPd's "DefaultRoot" directive.

There is nothing I have found so far in the vsftpd documentation or on their forums that would indicate such a thing exists.

---

### Post by majikstreet on 2005-11-16
warning: i do not know what i'm doing!

try enabling passwd_chroot_enable and chroot_local_user
then set their home dir in /etc/passwd to where u want them to be chrooted....


i may be wrong.. i've never done it! i just read the file!

[b]EDIT: BETTER IDEA!! local_root
    This option represents a directory which vsftpd will try to change into after a local (i.e. non-anonymous) login. Failure is silently ignored.

    Default: (none) [/b]

---

### Post by spade_shark on 2005-11-18
I liked the set VSFTP to chroot() a user when they log in idea.  Yes I agree with  majikstreet.

---

### Post by chipmonk010 on 2005-11-19
[QUOTE=majikstreet]warning: i do not know what i'm doing!

try enabling passwd_chroot_enable and chroot_local_user
then set their home dir in /etc/passwd to where u want them to be chrooted....


i may be wrong.. i've never done it! i just read the file!

[b]EDIT: BETTER IDEA!! local_root
    This option represents a directory which vsftpd will try to change into after a local (i.e. non-anonymous) login. Failure is silently ignored.

    Default: (none) [/b][/QUOTE]

[a]This is how i do it with my server works quite well, i created a system user (uploads for example) and when that user logs into the ftp they are chroot(ed) to their home dir. 

just uncomment:
chroot_local_user=yes


[B]i also have anonymous ftp setup so if you dont supply a password u end up at the anonymous site, vsftp does a very nice job of this.

---

