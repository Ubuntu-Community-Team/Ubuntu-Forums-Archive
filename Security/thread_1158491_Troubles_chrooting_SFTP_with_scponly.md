---
title: "Troubles chrooting SFTP with scponly"
date: 2009-05-13
forum: Security
---

### Post by DJ_Cyberdance on 2009-05-13
Hi everybody!

I need to replace FTP with SFTP but at the same time chrooting users in their homedir. Shell access should be denied to most users. Obviously, that's what scponly and/or scponlyc are made for.

I pretty much followed this guide:
[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

Unfortunately, I still cannot connect using WinSCP or Filezilla. I turned up the debug level and doing a tail -f /var/log/auth.log gives me the following output:

```

sshd[622]: Accepted password for scponly from xxx.xxx.xxx.xxx port 8779 ssh2
sshd[624]: pam_unix(sshd:session): session opened for user scponly by (uid=0)
scponly[625]: chrooted binary in place, will chroot()
scponly[625]: 1 arguments in total.
scponly[625]: ^Iarg 0 is -scponlyc
scponly[625]: opened log at LOG_AUTHPRIV, opts 0x00000029
scponly[625]: retrieved home directory of "/home/scponly" for user "scponly"
scponly[625]: chrooting to dir: "/home/scponly"
scponly[625]: chdiring to dir: "/"
scponly[625]: chdiring to dir: "/"
scponly[625]: setting uid to 1005
scponly[625]: entering WinSCP compatibility mode [username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22]
scponly[625]: processing request: "groups"
scponly[625]: running: /usr/bin/groups (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[626]: failed: /usr/bin/groups with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[626]: processing request: "pwd"
scponly[626]: running: /bin/pwd (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[631]: failed: /bin/pwd with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[631]: processing request: "pwd"
scponly[631]: running: /bin/pwd (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[632]: failed: /bin/pwd with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[632]: processing request: "pwd"
scponly[632]: running: /bin/pwd (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[633]: failed: /bin/pwd with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[633]: processing request: "pwd"
scponly[633]: running: /bin/pwd (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[634]: failed: /bin/pwd with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[634]: processing request: "ls -la --full-time"
scponly[634]: running: /bin/ls -la --full-time (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[635]: failed: /bin/ls -la --full-time with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[635]: processing request: "pwd"
scponly[635]: running: /bin/pwd (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[636]: failed: /bin/pwd with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[636]: processing request: "ls -la "
scponly[636]: running: /bin/ls -la (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[637]: failed: /bin/ls -la with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[637]: processing request: "pwd"
scponly[637]: running: /bin/pwd (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)
scponly[638]: failed: /bin/pwd with error No such file or directory(2) (username: scponly(1005), IP/port: xxx.xxx.xxx.xxx 8779 22)

```

All those files do exist in the chrooted user's homedir. The server is running Ubuntu 8.04 64bit. Anyone has a clue on how to fix this?

I also have followed these steps (recommended in some other place for 64bit platforms):
```

# mkdir /home/scponly/lib64
# cp /lib64/ld-linux-x86-64.so.2 /home/scponly/lib64/

```
But nothing changed.

---

### Post by kaptengu on 2009-05-14
Maybe have a look at this instead:
[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)

---

### Post by cdenley on 2009-05-14
> **kaptengu said:**
> Maybe have a look at this instead:
[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)

If you have ubuntu 8.10 or 9.04. It won't work on 8.04. Wouldn't it be easier to install an SSL certificate on your existing FTP server?

---

### Post by kaptengu on 2009-05-14
I still think it's easier to install OpenSSH >4.5p1. I've done it on 8.04 using builddep and apt-get source from intrepid repos.

---

### Post by cdenley on 2009-05-14
> **kaptengu said:**
> I still think it's easier to install OpenSSH >4.5p1. I've done it on 8.04 using builddep and apt-get source from intrepid repos.

I would stick with officially supported packages for a production server. The developers are reluctant to backport new versions for a reason. Also, the ChrootDirectory option was introduced in 4.8p1, not 4.5p1.

---

### Post by kaptengu on 2009-05-14
Considering 8.04 is LTS it is probably too risky to backport such a vital part of the OS. I can't see any problems doing this yourself and validate the results carefully.

---

### Post by cdenley on 2009-05-14
> **kaptengu said:**
> Considering 8.04 is LTS it is probably too risky to backport such a vital part of the OS. I can't see any problems doing this yourself and validate the results carefully.

Make sure you keep track of security notices, because your openssh-server package will not be updated by apt since hardy's repo will never have a newer version than your compiled one.

---

### Post by kaptengu on 2009-05-14
> **cdenley said:**
> Make sure you keep track of security notices, because your openssh-server package will not be updated by apt since hardy's repo will never have a newer version than your compiled one.

That's a good point. Thank you.

---

### Post by DJ_Cyberdance on 2009-05-14
Thanks for your support. Funnily, I just repeated the whole procedure. After I had put the 64bit libs in place, it suddenly worked - exactly the way I wanted it to work. Well, there still are limitations. I cannot connect with WinSCP as (that's what some of the howtos say) scponly is not compiled with an option that enables scp support. Nevertheless, it works pretty fine with Filezilla when connecting via SFTP.

But now I face another problem. I need to allow access to directories outside the chrooted environment. According to the howtos that can be achieved by "mount -o bind" which is true and works fine. But what I definitely need is some way of read-only bind so that the "bound" directories are not deleted when doing a rm -r /home/user. Unfortunaltely, simple symlinks don't work. 

There will be a dozen of people who can sudo su, users that are not required any more usually are deleted by rm -r /home/user/ - if there is a directory mounted inside the homedir with bind, it will be deleted as well. I must admit that I found out about that when I removed my test user, the test-directory I mounted before was gone as well. Fortunately, there just was test data inside. I mounted the test directory with the ro option, but for some reason that seems to be ignored. I have read that it can be remounted ro from kernel 2.6.26 on, but unfortunately the server is running 2.6.24. Of course I could try to install a newer kernel, but it is not up to me to take such decisions.

Therefore, I wonder if anyone has an idea of how to prevent those directories from accidentally being deleted by some admin doing housework...?

If openssh won't be updated, I wonder what the security repository is for...?

---

### Post by cdenley on 2009-05-14
> **DJ_Cyberdance said:**
> But now I face another problem. I need to allow access to directories outside the chrooted environment. According to the howtos that can be achieved by "mount -o bind" which is true and works fine. But what I definitely need is some way of read-only bind so that the "bound" directories are not deleted when doing a rm -r /home/user. Unfortunaltely, simple symlinks don't work.

You could use aufs.
```

sudo apt-get install aufs-tools
sudo mount none /home/user/data -o dirs=/usr/share/data=ro -t aufs

```

---

