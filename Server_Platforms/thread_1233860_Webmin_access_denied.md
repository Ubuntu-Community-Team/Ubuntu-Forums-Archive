---
title: "Webmin access denied"
date: 2009-08-07
forum: Server Platforms
---

### Post by wattaman on 2009-08-07
I've tried to change the webmin password through SSH with no luck, and now when I try to access the webmin login page I got the:
> Error - Access denied. The user has been blocked because of too many authentication failures.
I have ssh access, as webmin has a different user, but don't know what to do.
I'm hoping the restricted users and restricted IPs are stored somewhere in a file so I can delete them, this way being able to access the webmin page again. Any of you can help me on this?
Thanks!

---

### Post by wattaman on 2009-08-08
Sorry I insist, I'm desperate. I suppose the password has changed when I used putty for ssh, at least that's what it wrote there. I can access the webmin login page in browser, but as soon as I try to login I got the message above - so where can I find the restricted user list or how can I clear my restriction?
Thx!

---

### Post by rslrdx on 2009-08-08
hopfully not too late

usually its the same user as you log in to ubuntu.

give it a few minutes, i think the default is 10 minutes for webmin to let you back in.

usually Webmin users are the same as system users, can you give an idea of the users setup?

let me know if its still not working

---

### Post by wattaman on 2009-08-09
Thanks, but doesn't apply. My webmin has different user then the system users, and unfortunatelly I've created only one with all the admin rights - the one that now is blocked.
So must stick with the initial plan (unless there's no other better idea):
- find where the IPs and users restriction are stored and modify them.

Or, just thought about it, how to create an user with admin rights from SSH so I can login using that one?

---

### Post by wattaman on 2009-08-09
K, I got it, finally.
I've changed a few times the username from the file etc/webmin/miniserv.users, then it's password with the */usr/share/webmin/changepass.pl /etc/webmin user pass *command, then changed back the username (because the new didn't had admin rights) and, after restarting webmin, it finally allowed me to login and forgot about the restrictions :)

---

