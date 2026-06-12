---
title: "re-disabling root account"
date: 2008-02-15
forum: Security Discussions
---

### Post by rouble on 2008-02-15
Hi All,

I messed up my sudoers file, and so I had to enable my root account to fix stuff.

Anywayz, now whenever I use sudo, it tries to use the roots environment. 

For eg. if I try to do ssh using sudo (to forward privileged ports):
```
~$ sudo ssh -L 80:localhost:80 hostname

Could not create directory '/home/root/.ssh'.
```

Or if I just try to use gvim:
```
~$ sudo gvim

Could not create per-user gnome configuration directory `/home/root/.gnome2/': No such file or directory
```

Earlier sudo gvim would just use the current user's environment.

I tired re-disabling the root account as mentioned here:
[https://help.ubuntu.com/community/RootSudo#head-c625ac47fd3adc6178d573a652c589bf4ebedab5](https://help.ubuntu.com/community/RootSudo#head-c625ac47fd3adc6178d573a652c589bf4ebedab5)

But that doesn't stop sudo from trying to load root's environment. Any ideas on how to fix this?

tia,
rouble

---

### Post by cdenley on 2008-02-15
Post your /etc/sudoers file, and the output of alias.

---

### Post by rouble on 2008-02-17
Thanks cdenley.

I figured it out. When you enable root, ubuntu sets root's home directory as /home/root (in hardy). But, /home/root does not exist.

Now, if you disable root, some sudo commands will not work, because they won't find /home/root.

This might be a ubuntu bug.

Anyway, I fixed this by setting root's home dir as /root like this:
```
sudo usermod -d /root root
```

tia,
rouble

---

