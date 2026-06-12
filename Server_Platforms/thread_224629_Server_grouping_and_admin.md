---
title: "Server grouping and admin"
date: 2006-07-28
forum: Server Platforms
---

### Post by Tadhg on 2006-07-28
My webserver is running apache, and has two admin, myself and a friend. We're using ssh and scp to add files, change the webpage etc. I want to make sure i have the permissions set up right so that our two profiles cant mess with system files but can only add files to our seperate home dir's and add webfiles to /var/www leaving the root for changing configs etc.

Is this the best way to go about things? Should i put our two accounts in a usergroup and set ther permissions that way? Or is this overly complicated?

---

### Post by rbalfour on 2006-07-28
> 
Is this the best way to go about things? Should i put our two accounts in a usergroup and set ther permissions that way? Or is this overly complicated?


That is the best way to go. Really easy to maintain and setup.

---

