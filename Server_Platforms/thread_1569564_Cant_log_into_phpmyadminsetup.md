---
title: "Cant log into phpmyadmin/setup"
date: 2010-09-06
forum: Server Platforms
---

### Post by rollnhvy on 2010-09-06
I had the brilliant idea to make my own web server since i had a silicon mechanics 1u server collecting dust. Ive got apache running. Phpmyadmin is installed but i cant get into the admin panel. When it asks for the user name and password no matter what i use it wont let me log in.

---

### Post by ubunwhat on 2010-09-07
Not to be condescending, but you have to be sure that you are using the root user of the database server in question.  Unless you have changed it the default user name for most server installations is "root".  So unless you configured it differently when you installed the database server you need to use "root" and whatever password you provided when you configured the server.

---

### Post by rollnhvy on 2010-09-08
i found the problem mysql data base wasnt running so there was nothing to connect to :D

---

