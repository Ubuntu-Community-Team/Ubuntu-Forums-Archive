---
title: "sudoers file"
date: 2011-03-03
forum: Security
---

### Post by tech_soul8 on 2011-03-03
First sorry if i posted in wrong section :)
So, I want to add user to sudoers file to give him permission to del users (to use "userdel command".
I started bash and execute visudo. On the end of file I add new line so it looks like this
"user name" ALL = /usr/sbin/userdel 
save the file and quit.
When I try to execute command as users specified in sudoers file I get error message "userdel: cannot lock /etc/passwd; try again later" and I must use "sudo" to del user.
Where I made mistake? 
Thanks for help :)

---

