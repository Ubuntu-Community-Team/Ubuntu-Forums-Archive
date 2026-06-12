---
title: "karmic server: Cannot SSH into server until I login?"
date: 2009-11-05
forum: Server Platforms
---

### Post by icedfusion on 2009-11-05
Hi,

I have setup a ubuntu karmic server and installed the LAMP and openssh.
I also enabled encryption and partitioned using LVM.

So my problem:

I have setup SSH ok (like i have done on my Jaunty desktops) and put the key in the /home/user/.ssh directory.

If I then remote start the server, I can see from the server screen that it sits at a prompt waiting for someone to login (as you would expect) However, i cannot ssh into the server when it is in this state. I have to manually login at the server, why is this?

The server will be moved to my garage and there will be no keyboard/monitor attached so this is not good for me. Any ideas how I can login to the server via ssh remotely without having to first be at the server to login?

Cheers

ice.

---

### Post by Lars Noodén on 2009-11-06
Is the home directory of the account encrypted?

---

### Post by icedfusion on 2009-11-06
Hi, 
thanks for the reponse, yes it is encrypted.

I finally found an answer (I will try it when I get home tonight and mark it solved if it works), my original search terms were not bringing up any relevant responses.


This 'bug' has been posted:
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12)

Which basically gives the following solution:

```

Right, sorry, typed the wrong commands.

Here is an exact cut-and-paste. I left out a few details in the last
one, as it was merely pseudo code.

 $ /sbin/umount.ecryptfs_private
 $ cd $HOME
 $ chmod 700 .
 $ mkdir -m 700 .ssh
 $ chmod 500 .
 $ echo $YOUR_REAL_PUBLIC_KEY > .ssh/authorized_keys
 $ /sbin/mount.ecryptfs_private

Note that you should not have *any* other programs running between
those umount and mount commands, as all of your home directory will be
unreadable by those programs. If you're on a graphical desktop, log
out of all sessions and either ssh in, or login on the tty terminal.

```

Cheers

ice.

---

