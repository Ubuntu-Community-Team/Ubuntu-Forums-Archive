---
title: "Need Help please :( :("
date: 2010-07-01
forum: Server Platforms
---

### Post by mohamed sherif on 2010-07-01
hey, i have just installed xampp on my system and it is installed easily, the problem appears when i made a link directory in my home folder "public_html" it work properly and any new folders or files i create there are published in the /opt/lampp/htdocs/mohamed directory
But when accessing the link [http://localhost/mohamed/](http://localhost/mohamed/)
i get the following error message
**Access forbidden!**

            You don't have permission to access the requested directory.     There is either no index document or the directory is  read-protected. 


**Error 403**


so what shall i do to work on my server properly with no problems, plz any one reply me
Thanks in advance
M.sherif

---

### Post by dalitso on 2010-07-01
I believe there are two or more ways to solve this.
1. change the permissions to the web directory
2. change the owner of the web directory to user www-data

Try the first one(1) only by typing in the terminal
```
sudo chmod 777 /opt/lampp/htdocs/mohamed
```

if its still not working do(2)
```
chown www-data:www-data /opt/lampp/htdocs/mohamed
```

---

