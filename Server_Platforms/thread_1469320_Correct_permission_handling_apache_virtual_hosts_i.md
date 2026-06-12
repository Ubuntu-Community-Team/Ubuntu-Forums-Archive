---
title: "Correct permission handling apache virtual hosts in home folder"
date: 2010-05-02
forum: Server Platforms
---

### Post by u3000 on 2010-05-02
Hi all,

i use virtual hosts to develop several web applications. These are located in my home folder under /home/user/projects/project

After a fresh installation, i always get a 403 forbidden error. After googling and reading on this forum, several solutions are mentioned for this problem. But i can hardly believe putting using a chmod 755 on my home folder is a correct solution.

What is the correct way of doing things in this situation?

---

### Post by Bachstelze on 2010-05-02
> **u3000 said:**
> 
But i can hardly believe putting using a chmod 755 on my home folder is a correct solution.

You can add the www-data user to your group and chmod it 750 but either way, you will have to give www-data read access to it.

---

### Post by u3000 on 2010-05-02
I've added myself to www-data group
```
$ sudo adduser USER www-data
```changed the group of my home folder to www-data (non-recursive)```
$ sudo chgrp www-data /home/USER
```and changed the group of my projects folder to www-data as well (recursive)```
$ sudo chgrp -hR www-data /home/USER/projects/
```Is this a secure way of working, given that i gave www-data group read-only access?

---

### Post by Bachstelze on 2010-05-02
> **u3000 said:**
> Is this a secure way of working, given that i gave www-data group read-only access?

Yes, this is fine. Actually, you didn't even have to add yourself to the group: you already have read access to your home dir anyway, since you're the owner.

---

### Post by u3000 on 2010-05-02
All right, thanks for your feedback!

---

### Post by neverthemachineforever on 2010-08-19
Thanks guys this really helped me out.

Just in case anyone has any trouble after trying this, also try changing the group **permissions** as well as the just the group on your /home/USER folder.

I had to:
```
$ chmod g+rx /home/USER
```Just g+r didn't work (I could read the directory after a su www-data, but couldn't enter it), so I presume both are needed.

---

