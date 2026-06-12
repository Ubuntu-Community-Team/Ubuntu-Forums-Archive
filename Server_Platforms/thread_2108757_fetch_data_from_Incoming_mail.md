---
title: "fetch data from Incoming mail"
date: 2013-01-25
forum: Server Platforms
---

### Post by ketan985 on 2013-01-25
I have configured postfix for my kk.com domain successfully. Now I want to add function as described in below example.




  Example: 
  

if someone mail me at [EMAIL="admin@kk.com"]admin@kk.com[/EMAIL], one php script will fetch information  of sender email inside mail details and also  (defined in php script) add and  store in some mysql database and automatically forward this msg to another postfix accout like [EMAIL="rooot@kk.com"]rooot@kk.com[/EMAIL] .  I have little information that I need to config main.cf file in postfix and set some called alliase. I have configured postfix first time and I don't have deep knowledge of it..  



What is this technique called ?  

  How can I make this possible? 

 Help me friends.

---

### Post by volkswagner on 2013-01-25
I think starting with postfix mail filter may help.  Check out [this writeup]("http://blog.thecodingmachine.com/content/triggering-php-script-when-your-postfix-server-receives-mail").

Hope this helps get the ball rolling.

---

### Post by ketan985 on 2013-01-25
Brother I tried this 3 times step by step , Nothing gonna happen and It stops mail functionality.

---

