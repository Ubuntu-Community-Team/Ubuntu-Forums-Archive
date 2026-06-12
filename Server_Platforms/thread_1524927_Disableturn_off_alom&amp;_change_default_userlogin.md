---
title: "Disable/turn off alom&amp; change default userlogin Server V240"
date: 2010-07-06
forum: Server Platforms
---

### Post by yanto85 on 2010-07-06
hello, i'm new bie in solaris server.

anybody know how to disable alom. and how to change default user login on server v240.

hope somebody can give me solution. i had search before but can not find in manual book ^^      
thank :popcorn:

---

### Post by clrg on 2010-07-06
Why would you want to disable the ALOM? It's most useful.
And what do you mean by default user account? Root?

---

### Post by yanto85 on 2010-07-06
i know it's useful but my bos ask me to turn off it. 
the reason he gave me, about security risk.
i'm use sun fire v240. --> not support ssh >.<

acount in alom default login name is : **admin** ---> i want to change user login Alom v240.
do u can help me.thank

---

### Post by clrg on 2010-07-06
Honestly, you can't turn it off. You can put a chewing gum on the serial port, if you like. Your boss obviously doesn't know much about IT. The company I work for does hosting for banks, and I assure you, we don't consider alom's a security risk.

I'm not sure about the exact command, but you view all options with "help". You need to add a new user, give him all rights, and then delete "admin".

---

### Post by yanto85 on 2010-07-06
thank u for ur solution add user and delete.... confuse about that :P
btw can i change the alom connection with ssh conection?how?thank u

---

### Post by clrg on 2010-07-06
Here's a step by step guide:

1. Create a new user.
2. Give the new user full rights.
3. Set a password for the new user.
4. Logout
5. Login using the new user (to test the account)
6. Delete the old account

I hope I helped resolve your confusion.

I think you need a serial connection in order to use the ALOM. Our company uses so-called console servers to circumvent the problem. This enables us to connect to the console server using SSH, and then connect to the ALOM of the V240 using a serial connection. Thus eliminating the need for someone to go to the datacenter personally.

---

### Post by yanto85 on 2010-07-12
> **clrg said:**
> Here's a step by step guide:

1. Create a new user.
2. Give the new user full rights.
3. Set a password for the new user.
4. Logout
5. Login using the new user (to test the account)
6. Delete the old account

I hope I helped resolve your confusion.

I think you need a serial connection in order to use the ALOM. Our company uses so-called console servers to circumvent the problem. This enables us to connect to the console server using SSH, and then connect to the ALOM of the V240 using a serial connection. Thus eliminating the need for someone to go to the datacenter personally.

i have made new user and login with that new user buat i can not delete old account ...
do know why.

error : not allowed to delete admin

new account with cuar - full permision i set it.

---

