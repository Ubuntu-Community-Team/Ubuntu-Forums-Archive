---
title: "error backup mysql"
date: 2016-06-21
forum: Server Platforms
---

### Post by kambiz2 on 2016-06-21
Hi,
I've downloaded a script to backup mysql, my knowledge is not enough to write it. When I execute it, I've got the follow error:

[IMG]http://www.tepui.cat/foro/mysql0.jpg[/IMG]
 
The permissions of this user, I believe, are total

[IMG]http://www.tepui.cat/foro/mysql2.jpg[/IMG]

And this is the part of the script with the error:

[IMG]http://www.tepui.cat/foro/mysql3.jpg[/IMG]

Any help please?
Thanks

---

### Post by MAFoElffen on 2016-06-22
See attached... snip of your post showing that We cannot see the picture of your error ... So do not know what to respond about. 

Could you please try to post that picture again?

---

### Post by kambiz2 on 2016-06-23
Thanks for your answer, I can't understand why you can't see this picture, I can. Anyway, I've replaced it in the original post, and here I repeat it again.

[IMG]http://www.tepui.cat/foro/mysql0.jpg[/IMG]

---

### Post by kambiz2 on 2016-06-23
I've discovered the problem. This user has all previleges only for one database, and the backup if for all database.
I've given permissions to this user for all databases and the problem has been resolved

---

### Post by MAFoElffen on 2016-06-24
Good that you found the solution for your problem. 

Now that found an answer, please help others by returning to this thread > select the link in the top right of page "Thread Tools" > Select "Mark as Solved." This helps others to find answers to their similar problems.

---

