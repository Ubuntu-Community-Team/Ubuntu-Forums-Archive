---
title: "[SOLVED] Giving folder ownership to another user without root"
date: 2008-10-16
forum: Security
---

### Post by ragtag on 2008-10-16
Hi,

 I need to write a shell script that takes a bunch of files and copies them to a server (mounted via NFS), then makes them read only and changes the ownsership, giving it away to another user.

 This last point has me a bit stumped. You need to be a sudoer or root to run chown, and none of the users that will run the script are (or should be). The user that runs the script is the one that owns the file before running the script, but once done he should only have read acces (as a group member) and another user should own them.

 Is there some clever to chown the files on the server that I haven't thought of?

 Cheers,
   ragtag

---

### Post by hyper_ch on 2008-10-16
can't you connect directly as that user through nfs? With sshfs you can set uid and gid.

---

### Post by ilrudie on 2008-10-16
You can edit the sudoers file with visudo and give users than need to run the script the right to run very specific commands as root without giving them full root access.  For instance you could give them permission to run the script as root but not any thing else.  If you did that you must make sure they can't edit the script.  My suggestion would be to make the script root:bin owned and grant r-x permissions to everyone.  Put a check in the script that makes sure they are uid=0 (root) and if that fails print a message about using sudo to run the script.  Put the script in /usr/local/bin or /usr/local/sbin.  Make sure the folder you put the script in is in these user's path.

---

### Post by ragtag on 2008-10-17
Thanks for pointing me in the right direction. That would work for what I need to do (in a ruondabout way).

---

