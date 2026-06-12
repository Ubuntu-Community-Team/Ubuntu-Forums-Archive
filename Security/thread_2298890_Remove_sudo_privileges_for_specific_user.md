---
title: "Remove sudo privileges for specific user"
date: 2015-10-14
forum: Security
---

### Post by mike372 on 2015-10-14
Good day,

It has been brought to my attention that it may be a security vulnerability to have my Ubuntu 12.10 "www" user account to have sudo privileges. Multiple resources indicate to run visudo or to modify /etc/sudoers/, but I do not see the "www" user account listed there. Could this user account be a member of another group or have sudo privileges established via another method? Would any changes disallow my SSH access?

Any additional information or suggestions would be greatly appreciated.
Thanks for your time, assistance, and feedback.
-Mike

---

### Post by Lars Noodén on 2015-10-14
You can check which activities the user *www* can carry out via sudo like this:

```

sudo -u www [color=green]sudo -l[/color]

```

The first sudo runs the second as the user www.  The second sudo only lists the available activities for the current user (which would be www).

---

### Post by Bashing-om on 2015-10-14
mike372; Hello; My welcome to the forum.

In furtherance to Lars Noodén's response, may I add .
As you state:
> 
it may be a security vulnerability to have my Ubuntu 12.10 "
 we can assume that security is of high concern.
Be aware that release 12.10 is End-Of-Life and gets no updates at all  including security updates !

Maybe install a Long Term Support release ( 14.04 ) ?

[INDENT][INDENT]just in passing by
[/INDENT][/INDENT]

---

### Post by Lars Noodén on 2015-10-14
> **Bashing-om said:**
> 
Maybe install a Long Term Support release ( 14.04 ) ?


+1

Thanks for catching that.  Version [12.10 expired back in May 2014](https://wiki.ubuntu.com/Releases) and has no security updates since then.  If you find the machine is compromised, then a fresh install is in order and that calls for an LTS version.  Version 14.04 is good through April 2019.

---

### Post by mike372 on 2015-10-16
Thank you both very much for the extremely helpful information.

The user has permissions (ALL : ALL) ALL, so how would I remove the user's "sudo privileges"? 
Would the command be: sudo deluser www sudo?
Would these changes disallow my SSH access?

I greatly appreciate your time, feedback, and assistance.
May you have a great day!
-Mike

---

### Post by Lars Noodén on 2015-10-16
Check which groups that user is in.  They might be in the group "sudo" or "admin".  If so, remove them from that group.  

Just to check, you did make the user "www" on purpose?

Changes affecting sudo won't affect ssh.

---

### Post by Lars Noodén on 2015-10-16
If the user is "www" is in the group "sudo" then you can remove them from the group using [gpasswd](http://manpages.ubuntu.com/manpages/trusty/en/man1/gpasswd.1.html)

```

sudo gpasswd -d www sudo

```

---

### Post by mike372 on 2015-12-30
Good day,

As a delayed follow-up, the www user was not part of the 'admin' or 'sudo' groups. To resolve, I modified the sudoers file:
1. su root
2. sudo visudo (nano as default editor)
3. Commented out the www user's elevated permissions.

Additional resource used: [URL="https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file-on-ubuntu-and-centos"]https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file-on-ubuntu-and-centos
[/URL]
*Rereading my original post indicates that I had already checked the sudoers file. I think that I made a rookie mistake and overlooked that I needed to scroll further down (go to the next page ^V)  - Doh!

Thanks for your help and collaboration all and I apologize for my oversight.
May you have a great day!

---

### Post by Bashing-om on 2015-12-30
mike372; Hey hey ;

Way to go ! Pleased that you found the problem, and provided to the community the resolution .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

