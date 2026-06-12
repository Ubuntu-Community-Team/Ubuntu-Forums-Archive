---
title: "Courier MySQL question"
date: 2006-12-07
forum: Server Platforms
---

### Post by Porrly on 2006-12-07
Howdy,

I have installed Courier IMAP, mysql and courier authmysql. (Amongst other things)

I wish to be able to log in to any one account with ALL of the following scenarios:

a) Username: user
   Password: supplied

b) Username: [email]user@domain.com[/email]
   Password: supplied

c) Username: [email]user@mail.domain.com[/email]
   Password: supplied

I currently have tables set up in mysql to authenicate [email]user@domain.com[/email].

I wish to have some method that takes 'user' and appends '@domain.com' before doing authentication.

I also wish to have a method that takes 'user@mail.domain.com' and converts it to 'user@domain.com'.

Can anyone provide details on how to do what I wish (bearing in mind that I want the system to autmatically recognise the username format entered and work with it accordingly)?

Thanks in anticipation.

Paul

---

### Post by Porrly on 2006-12-09
Bumpety boing!

---

