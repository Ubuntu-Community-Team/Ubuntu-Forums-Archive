---
title: "How to create users with admin priviledges?"
date: 2006-08-21
forum: Server Platforms
---

### Post by cocotu on 2006-08-21
Hello, I have 4 users on a LAMP server:

User1
User2
User3
User4

I would like to know how to set these users as admin. (like in Windows). I'm root, but I want them to be able to perform administrative tasks such as making changes to Apache, MySQL, etc.. For MySql do I have to create a separate account for or can they use the same login name?

Thanks for your help

---

### Post by lamego on 2006-08-21
You will need to creat a specific group to include those users and then change the group owner and group permissions on the configuration files as needed.
As for mysql you can setup admin users at the mysql db level, it has nothing to do with their linux id, they can specify the user they want to login with.

Sorry if my post is not very clear, you should  understand how linux ownership/permissions work to be able to perform administrative tasks.

---

