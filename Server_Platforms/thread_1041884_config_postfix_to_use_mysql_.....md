---
title: "config postfix to use mysql ...."
date: 2009-01-17
forum: Server Platforms
---

### Post by hockey97 on 2009-01-17
Hi, I currently want to know how I can use postfix to use mysql.

I also plan to use php to program my own web page that will grab the users e-mails and other stuff and display it in the page.

I want to provide e-mail service.

So right now I got a working postfix. I can send e-mail to gmail but not to aol,msn,yahoo.

The errors I get was blocked... because I didn't have a static ip and didn't have a proper reverse host lookup.

I want to learn how to master postfix. Meaning how e-mail will flow around.

I also have a automation e-mail that when the users register they get a e-mail from my script to verify there e-mail address. 

I notice that the e-mail address was [email]www-data@mydomain.com[/email] 

how can I change it to like [email]regsiter@mydomain.com[/email] ??

I have 2 websites. I plan to host only 2 e-mail address using domain 1.

and  2  plus all client-users to be using domain 2 

do you have websites that will help me set up such a thing.



Also one more thing... Whats the best way to backup the server and be able to move these files to other hd and have  a exact same copy of the system???

so I can transfer my server to other hard drives. So I can have backup computers systems.

just saying.

I want to know if I should just flat out copy every file on the system? 

or use partimage to make a backup image of the part????


Thanks for your time.

---

### Post by HermanAB on 2009-01-17
Citadel already does all that, only better!

You can get a preconfigured Citadel VM from the VMware web site.  That is the easiest way to manage high availability backup systems.

Cheers,

Herman

---

### Post by martien on 2009-01-17
First you have to own static ip or ddns, because 90% of the mail servers around the world will refuse the mails from your server (because of the reverse resolve)
Then you need to configure postfix and your IMAP client to use mysql and then all things you want are php playing - scripts to add, edit, delete, search, email, etc. For me the writing of the scripts will be the easiest part of the story. But if you don't want or can't write your own scripts, then you can use postfixadmin ;). There are many tutorials how to do that. I also think postfixadmin has public accounts register script with an option to send welcome mail to new users. It's all php-mysql playing and its not so hard.
To backup your clients data (the mails in this case) you must copy the vmail (virtual mail) dir (thats the directory where the clients accounts (each has own dir) and their email msgs are stored). Good luck.

---

### Post by hockey97 on 2009-01-17
oh, ok. I am getting new internet installed dsl. I have to call them after the order is proccessed. My dad forgot to order a static ip. it supposed to cost me 5 bucks.

I am trying to use mysql to hold user names and e-mail addresses.

I want to make a php script that once they register and make a user name it will also make a e-mail address and account with the same user name and password.

So I want postfix to use mysql to grab user data and mail boxes. I assume I can make  folders for e-mails etc for each users.

the php programming is not really a problem. If I don't have to directly need to talk with the postfix software.

---

### Post by spiderbatdad on 2009-01-17
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

