---
title: "Edited Sudoers file, big problem"
date: 2012-01-18
forum: Server Platforms
---

### Post by Jefferythewind on 2012-01-18
Hi Everyone,

  So I am running Ubuntu server 10.10. I wanted to add another user to our server who has root privileges.  I made this user, then I wanted to have an "admin" group which all had sudo privileges.  Before I made the admin group, I did the following.

    I just edited the /etc/sudoers file using "sudo -E visudo" and I un-commented this line:

admin ALL=(ALL) ALL

  Originally I was the root user, and now when I run su or sudo, i get an authentication failure, it says that I am not in the sudoers file, and the incident will be reported.  I think I may have caused a big problem.  The default editer for visudo was NANO, and after I un-commented that line, I did ctrl-O, then ctrl-X to exit.

  I also cannot log in as root.

  Can anyone help me fix this problem? Thanks!

---

### Post by sisco311 on 2012-01-18
You will have to boot into recovery mode to fix the problem, see:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by Jefferythewind on 2012-01-19
Thanks, that link looks like it explains exactly how to fix my problem.  I will give it a try tonight and update about how it turns out.  Thanks a lot!

  Yes thanks again, it worked.  I re-wrote the sudoers file and added myself to the admin group, so I am back!

---

