---
title: "multi-user Linux - who around here does that?"
date: 2019-08-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-08-09
i ran Ubuntu 14.04 and 16.04 and now Xubuntu 18.04 with multiple users concurrently logged on.  this works under Unity and Xfce, which both use *lightdm* to manage the display.  it's a bit stronger security through compartmentalization.  there may be other reasons people do this.

[B]i'm wondering how many UbuntuForums participants do this in some way.
[/B]
i want to look at boosting the security a bit and put each user in a container.  or maybe i could use a virtual machine get even more security.

---

### Post by oldrocker99 on 2019-08-09
I was on a UNIX server 29 years ago, and no user had access to any other's /home folder. Each user's /home folder is pretty damn secure already with a password required to get access. Others might give you better advice, but that's how I see it.

---

### Post by SeijiSensei on 2019-08-10
Like oldrocker said, Linux, like Unix and all its derivatives, provides ample security out of the box.  Each user can only write to his or her home directory and to /tmp.

One thing that I would do is remove the group and other read and execute privileges from each person's home directory so they are entirely private. Ubuntu has a "sharing" ethic and by default creates home directories that are listable and readable by all users.  So instead of the default 755 privileges on /home/username, I'd make them all 700. (This is the default on "enterprise" distributions like RedHat.)

You can make that the default by editing (as root with sudo) /etc/adduser.conf and change the line
```
DIR_MODE=0755
```
to
```
DIR_MODE=0700
```
Then when you create new users with the adduser command, their home directories will have 700 privileges by default.

For even greater security you can change the default UMASK in /etc/login.defs from 022 to 077.  Then all files a user creates will only be accessible by that user.

The downside to these changes is that it makes it difficult for users to share files with other users, especially if you change the umask.  One solution is to change the DIR_MODE but leave the UMASK at 022, then create a directory where people can place files they want to let other users see.  Suppose I create a directory called "/shared" with permissions similar to /tmp

```
sudo mkdir /shared
sudo chmod 1777 /shared

```

The 1 in the permissions sets the "sticky bit," which prohibits users from deleting or modifying files or directories created by another user.

You can make it easier for users to find the shared directory by including a symbolic link to it in /etc/skel, which contains the files copied to each new user's home directory when it is created.

```

cd /etc/skel
sudo ln -s /shared

```

Now every new user will have a "shared" entry in his or her home directory.

If you do an "ls" on /etc/skel you won't see anything by default. That's because all the files there are "hidden" with a "." prefix like .bash_profile. To see the contents of /etc/skel, use "ls -a".

For a discussion on why Ubuntu has a more open security ethic read this thread: [https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734](https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734) with contributions from a variety of notables including Mark Shuttlesworth himself.

---

### Post by TheFu on 2019-08-10
At my little company, we have 3 users logged in and working together on a single system multiple times a week.
None are physically at the system, they are all network connected, usually over ssh.

---

### Post by Skaperen on 2019-08-10
> **oldrocker99 said:**
> I was on a UNIX server 29 years ago, and no user had access to any other's /home folder. Each user's /home folder is pretty damn secure already with a password required to get access. Others might give you better advice, but that's how I see it.
that was back when no one had their own unix(-like) system at home where they are (usually) the one using all or most userids (unless their dog gets to use the system, too).

---

### Post by Skaperen on 2019-08-10
i do have my various userids set up to read-share their home directories.  if i need to change something in a different home directory, i just switch user to it.  the day i let other people use my system, then i will need to make things tighter, possibly using groups.

some of the general complications are things like keeping the music playing when i switch users.  for now i run pulseaudio in system-mode.  but i have read that it is possible to do this without system mode and be more secure about it.  i just wonder if others might have similar issues and even how many people understand how such multi-user usage is done.

---

