---
title: "Moving SAMA Home Directory(s)"
date: 2009-10-06
forum: Security
---

### Post by bnhcomputing on 2009-10-06
I have setup ubuntu (Hardy) and integrated the server into my Windows Active Directory Domain using the instructions found here:[http://anothersysadmin.wordpress.com/2007/08/03/active-directoy-authentication-with-ubuntu/](http://anothersysadmin.wordpress.com/2007/08/03/active-directoy-authentication-with-ubuntu/)

These worked GREAT!

My question:  Following those instructions, the user's "home" directories are created in /home/domain

I have another volume mounted via /usr2

I would like all home directories to be created in /usr2/home/domain

Any ideas on how to make this change?

I would also ask to provide as much detail as possible because I am a newbie to linux.

Thanks in advance....

---

### Post by cariboo on 2009-10-06
You could create a symlink from the home directories in /ur2 to /home:

```
sudo ln -s /ur2/user /home/user
``` 

That way all the home directories are in /ur2 with links to /home

---

