---
title: "sudo access no longer available"
date: 2006-09-11
forum: Server Platforms
---

### Post by dbtx on 2006-09-11
I recently installed 6.0.6.  Having tried Ubuntu before, I knew the root account is disabled, but never liked the fact that the first user's password becomes the sudo password.

So with this install, I decided to be clever and create another account first to use as the sudo password.  This way, other people using the computer could  be able to administer it without needing my password.

Worked great.  But then I saw when setting up my account, the ability to set my own account with administrator rights using the "Executing system administration tasks" on my account.  When I did that, it did let me use my own password using sudo, but then noticed I couldn't use the password from the first account that was set up (even though it has the "Executing system administration tasks" checked on it's account).

So I thought that by unchecking it on my own account, this would transfer the sudo password back to the first account.  Wrong!  Now I can't get into and sudo accessibility with either password.  And now have no way to administer the computer.  :( 

How do I get it back without having to reinstall from scratch?

---

### Post by aysiu on 2006-09-11
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) should help.

---

### Post by Metacarpal on 2006-09-11
Once you have the administrator privileges restored:

Each account that has the Perform Administrative Tasks box checked uses its own password for sudo/gksudo tasks.  You don't need to create a single, unified administrative password for each user account to use.

---

