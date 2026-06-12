---
title: "scponly chroot jail not working 10.10"
date: 2010-11-03
forum: Security
---

### Post by bwestover on 2010-11-03
In the past on Jaunty and Intrepid, I have used the package 'scponly' to allow users to:

A)Login with SFTP and be jailed to their home directory

B)Copy files to their home directory SCP, again jailed to that directory

C) Not login to a shell, or be able to execute ANY other commands.

I find this to be ideal as SFTP is very convenient for use from a GUI (Filezilla, WinSCP etc) where as SCP is very nice to use from a shell prompt
(i.e. "scp localfile remoteuser@remoteserver:/remotepath/")

I tried to set this up on my 10.10 server, and I'm having a problem.

The user can login via sftp, but they are NOT jailed to their home directory.

Also, the user cannot login via scp at all
```

administrator@util-dr:~$ scp test scponlytest@96.46.148.190:/incoming
scponlytest@96.46.148.190's password:
unknown user 1004
lost connection

```I installed the package from the repository, selected 'YES' on the configure screen to enable the chroot option, and then used the included script "/usr/share/doc/scponly/setup_chroot/setup_chroot.sh" to create the user.

Any ideas?

---

### Post by deksza on 2010-12-04
I have the exact same issue. Have you by chance found a solution for this yet?

---

### Post by cariboo on 2010-12-04
Does your user have an account on the server?

---

### Post by deksza on 2010-12-04
> **cariboo907 said:**
> Does your user have an account on the server?

Yes, everything seems to work except the user can still see all the files on the server. The "chroot jail" part doesn't seem to confine him inside his home folder like it is supposed to.

To setup everything, I was following the instructions I found at [http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

Maybe something has changed since then as I think that was written for version 7.10?

---

### Post by bodhi.zazen on 2010-12-05
I suggest you use ssh keys with forced commands and / or "jailbash"

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

---

### Post by WinstonChurchill on 2010-12-05
Why not use SSH's built-in chroot functionality?

Example: (%u expands to the username of the connecting client)
```

Subsystem sftp internal-sftp

Match Group sshftponly
AllowTcpForwarding no
ChrootDirectory /home/%u
ForceCommand internal-sftp

```This does everything you mentioned, and it's easier to maintain. You can just make the user's shell /bin/false.

**EDIT: **I don't remember if that allows SCP to work, but I think it does... I'll double check.

**EDIT2: **Unfortunately, it does not:
```

debug1: Sending command: scp -v -f -- /test.txt
Sink: This service allows sftp connections only.

```

---

### Post by bwestover on 2010-12-06
Right, I would love to use the built in Match Group feature as it seems more secure and easier to maintain.

However, I really would like to offer SCP to my users as well.

---

### Post by WinstonChurchill on 2010-12-06
The 'sftp' command actually supports the same syntax as SCP:
```

root@Server:~# sftp -i testuser-key testuser@127.0.0.1:/public/OpenBSD48-amd64.iso
Connected to 127.0.0.1.
Fetching /public/OpenBSD48-amd64.iso to OpenBSD48-amd64.iso
/public/OpenBSD48-amd64.iso                                    100%  225MB  56.3MB/s   00:04
root@Server:~# ls -l
total 230536
drwxr-xr-x 2 root root      4096 2010-12-06 13:18 MiscStuff
-rw------- 1 root root      1679 2010-12-06 13:19 testuser-key
-rw-r--r-- 1 root root 236054528 2010-12-06 13:20 OpenBSD48-amd64.iso

```The user "testuser" is configured with the match block from my earlier post.

---

### Post by dmonty on 2011-08-05
I had the "unknown user 1004" error and found that libnsl.so.1 was missing from the jail's lib directory.

If you want to check that you have all the required libs.
cd into the directory of your jail and run the following
```

find . -type f -exec ldd '{}' \; | awk '{print $3}' | sort | uniq | grep -v '('

```
This will give you a list of libraries that need to be in your jail.  Make sure you copy the binary and not just a symlink.

---

### Post by bodhi.zazen on 2011-08-05
> **dmonty said:**
> Make sure you copy the [s]binary[/s] library and not just a symlink.

Fixed that for you =)

---

### Post by sn9ke.eyes on 2011-10-18
> **WinstonChurchill said:**
> The 'sftp' command actually supports the same syntax as SCP:
```

root@Server:~# sftp -i testuser-key testuser@127.0.0.1:/public/OpenBSD48-amd64.iso
Connected to 127.0.0.1.
Fetching /public/OpenBSD48-amd64.iso to OpenBSD48-amd64.iso
/public/OpenBSD48-amd64.iso                                    100%  225MB  56.3MB/s   00:04
root@Server:~# ls -l
total 230536
drwxr-xr-x 2 root root      4096 2010-12-06 13:18 MiscStuff
-rw------- 1 root root      1679 2010-12-06 13:19 testuser-key
-rw-r--r-- 1 root root 236054528 2010-12-06 13:20 OpenBSD48-amd64.iso

```The user "testuser" is configured with the match block from my earlier post.

This is only partially true, as sftp only uses the same syntax when doing a get, not a put.

In your example,

sftp [email]testuser@127.0.0.1:/public/OpenBSD48-amd64.iso[/email] would retrieve the iso file from the remote server, but sftp OpenBSD48-amd64.iso testuser@127.0.0.1:/public/ will not put the iso onto the remote server.

---

### Post by bwestover on 2011-10-18
Does anyone know of a way to both jail a user to their home directory, and provide only SCP and SFTP functionality?   Since we initially provided this support, it has become a requirement, and I'm finding it quite difficult to support it on a current release server version.

---

### Post by dmonty on 2011-10-18
See My August 5th posting in this thread page 1 on how to find and fix the missing libibraries that scponly needs in it's chroot jail.

---

### Post by bwestover on 2011-10-18
> **dmonty said:**
> See My August 5th posting in this thread page 1 on how to find and fix the missing libibraries that scponly needs in it's chroot jail.

 But my issue isn't only that SCP isn't working, but the chroot function isn't working. (A much bigger issue for me). When a user logs in via SFTP, they can read files and folders outside of the jail.  I would like, if at all possible to configure this without using scponly. Is it even being maintained anymore?  Instead, if there was a way to do it with built-in functions of OpenSSH that would be the best. Or some modifications to the users bash profile or something.

---

### Post by dmonty on 2011-10-18
Did you set their /etc/passwd shell from bash to: /usr/sbin/scponlyc

---

### Post by bwestover on 2011-10-18
I think so yeah, but I don't have access to that test rig anymore. 

Would that matter anyway, when the user was connecting with SFTP? Doesn't that use a different binary on the server side, where as SCP uses whatever the current shell is set to?

In any case, I have concerns about using scponly, because I don't see many current references to it. It seems perhaps that its not maintained any longer.

In 2009 when I configured the first server, I used scponly. When I tried it again on 10.10, it didn't work right. Even if I can make it work right on 11.04 or 11.10, I'm less likely to see it continue to work right on each new server release, as something like this doesn't get the same level of testing as built in or common functions (like if I could do it with a configuration native to OpenSSH as an example).

---

### Post by dmonty on 2011-10-19
> **bwestover said:**
> 
Would that matter anyway, when the user was connecting with SFTP? Doesn't that use a different binary on the server side, where as SCP uses whatever the current shell is set to?


Yes this is very important it will not work properly without changing the shell.

> **bwestover said:**
> 
In any case, I have concerns about using scponly, because I don't see many current references to it. It seems perhaps that its not maintained any longer.


Yes the package is maintained and works well.  It hasn't changed much because it is rock solid stable.
[http://packages.ubuntu.com/search?keywords=scponly](http://packages.ubuntu.com/search?keywords=scponly)
We use it all the time for our web servers - give users access to upload data without being able to poke around the web server.

---

