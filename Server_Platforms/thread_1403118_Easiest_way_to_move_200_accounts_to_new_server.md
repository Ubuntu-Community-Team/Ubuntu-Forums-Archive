---
title: "Easiest way to move 200 accounts to new server?"
date: 2010-02-09
forum: Server Platforms
---

### Post by hsweet on 2010-02-09
I'm in the middle of moving my lab to a new server in the middle of the school year.. and need to copy all the user accounts to the new box, hopefully with all the student's passwords and contents of their folders intact.   And since we are using the system daily, I need to do it all in an hour or 2.  

I'm thinking I can just

1. diff /etc/passwd and /etc/shadow from the old the new  
2. copy all the student folders to new /home
3. write a script to set the permissions on all the new /home folders to match the user names.

It seems easy and safe so long as I back up the 2 existing files..

Any reason not to try?  Or is there an easier way?

thanks

---

### Post by NumPy on 2010-02-09
All I could say is if your moving the files and folders over, why not copy them preserving permissions with an '-a' in the copy string, THEN run a script to just double check permissions. 

That way your not blindly changing perms with a script. I have had issue with that ONCE, and learned my lesson well.

---

