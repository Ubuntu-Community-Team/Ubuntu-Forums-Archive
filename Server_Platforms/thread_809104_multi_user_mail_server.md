---
title: "multi user mail server"
date: 2008-05-27
forum: Server Platforms
---

### Post by niqmk on 2008-05-27
Hello, Good day.
I don't know if my title fitted with my question.

I've already set the postfix and it works great. But i was wondering about how to create a user between my mail server?
Then I tested using "squirremail". And i've not found any solution. Then I searched a tutorial at google "http://flurdy.com/docs/postfix/" and followed step by step that tutorial but hasn't found any solution.

Anyone here can give me a rtfm for this problem. I want to add more than one user to surf their mail and collect their mail at UBUNTU SERVER.

---

### Post by supremedalek on 2008-05-27
I am a bit confused, which is not hard to happen. So, you have postfix running and want to add more users to it. Are they going to be local users (they will also be able to login to your machine) or virtual ones (they can only connect to your machine to get their mail and that is it)? And, how do you want them to get their email: web interface (say, squirrelmail) or some mail client that speaks imap/pop?

---

### Post by hyper_ch on 2008-05-27
Ok, just some clarification here:

postfix --> a server that receives and sends email
courier/dovecot --> servers that "transfer" emails on the server between server and user by IMAP or POP3 (depending on what you install)
squirrelmail --> a web gui for reading/writing mail (a gui to use in conjunction with courier/dovecot)

---

### Post by supremedalek on 2008-05-31
Yeah, I probably should have been a bit more clear. :) 

In any case, I wonder if the original poster has solved the problem already. A few weeks ago I deployed postfix + dovecot in a centos box. And, to add insult to injury, I even documented what I did down to creating the stupid certs! Jokes apart, I was hoping to find out where he was stuck.

---

