---
title: "The same sshfs command works fine on one machine but not on another?"
date: 2018-01-03
forum: Server Platforms
---

### Post by gary64 on 2018-01-03
I'm puzzled,

I have two Ubuntu 16.04.03 LTS servers («au» and «hc»), and one Mac («ed»), all different locations. Trying to mount a Mac volume with:

```
sudo sshfs -o allow_other,IdentityFile=~/.ssh/id_rsa.pub user@ed:/Volumes/Incoming/ /mnt/mac
```

This works just fine on «hc», but not on «au». The exact same command doesn't work.

ssh works just fine on both machines without a password: public key of «ed» is present in ~/.ssh/authorized_keys of both «au» and «hc»

On «hc»:
1) the remote directory is mounted without any problem or message

On «au»:
1) it first prompts me to type the password of «ed» and then
2) fails to mount (no error message or else is given; the mount just won’t take place)

Any ideas?

Thanks a lot!

Gary

---

### Post by TheFu on 2018-01-03
Check the .profile and .bashrc for each.  Interactive shell commands sometimes interfere with non-interactive connections.

Also, ensure both Ubuntu systems are patched to the same point.

Probably won't help, but those are just guesses.

Have you checked the logs on all three machines?  When you connect with ssh, does ssh -vvv show anything different that could impact this?

Just gotta ask - have you considered putting the options into the ~/.ssh/config?

---

### Post by gary64 on 2018-01-03
ssh -vvv outputs are *exactly* the same (except path names, etc.)

This must be a permissions issue either with fuse or with sshfs. I'm logged in as root on hc, and as "master" on au. This must have something to do with this.

I already uncommented the [COLOR=#000000][FONT=&quot]user_allow_other[/FONT][/COLOR] in /etc/fuse.conf and I am not prompted to type in the password anymore, that sounds like an improvement. However, the directory is still not mounted. But, the owner:group of the mount point has already changed into 501:dialout; which is also correct.

Any more ideas?

Thanks!

---

### Post by TheFu on 2018-01-03
Don't use root.

I've never needed any options with sshfs, but some things haven't always worked, like symbolic links.  I don't use apple products, so cannot help with that. Sorry.

I'll assume you've looked over all the OSX-related issues with FUSE and with sshfs and verified that the OSX file system should work?

---

### Post by Max303 on 2018-01-11
Does the mount succeed on [COLOR=#000000]«au»[/COLOR] when it is not mounted to [COLOR=#000000]«ed»[/COLOR] on [COLOR=#000000]«hc»[/COLOR]?

---

