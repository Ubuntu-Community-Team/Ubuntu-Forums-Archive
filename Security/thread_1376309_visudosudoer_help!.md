---
title: "visudo/sudoer help!"
date: 2010-01-09
forum: Security
---

### Post by dandirk on 2010-01-09
ubuntu 9.10

I would like to run a simple umount and mount -a sh script without needing a password for sudo.  No matter what I do with visudo, running this script prompts for a password.

Be gentle I am still learning ubuntu...

Created the sh/bash script on the desktop

So I ran "sudo su" to enter root, then started visudo

I added the line

htpc ALL=(ALL) NOPASSWD: /home/htpc/Desktop/test.sh

Ctl x to quit visudo, Y to save, then enter...

I ran "sudo bash test.sh" - prompted for htpc user password

I moved sudo into the script before each command - prompted for password

I edited sudoers to htpc ALL=(ALL) NOPASSWD: ALL - prompted for password

I think I have tried almost every combo, post I could find with no joy.

What am I missing here?  I know it has to be something simple....

Thanks

---

### Post by dandirk on 2010-01-09
Sorry, thought this thread would be appropriate.  I see its for updates and notices.

I will repost in the general thread, mods please feel free to delete.

---

### Post by Lars Noodén on 2010-01-09
A couple suggestions to get started with about sudo.  

When you can, assign access to a group.  It makes it easier to manage who can do what since adding or removing users from a group is very easy.  It also makes it easier to debug.  The advantages of this are felt more strongly when you have more users than with just one or two.

If a script is going to be run as root, then make sure that it the script itself is not writable by anyone except root and that the directory it is in and the directories above it are not writable by anyone except root.  Otherwise, the script can be re-written to run anything, including mistakes or malicious actions.

```

# from /etc/sudoers
# allow any in the group unmounters to run the script
**%**unmounters ALL=(ALL) NOPASSWD: /usr/local/bin/test.sh

```

```

$ ls /usr/local/bin/test.sh
-r-xr-xr-x  1 root  admin  218232 Jan 10  2010 /usr/local/bin/test.sh

```

---

