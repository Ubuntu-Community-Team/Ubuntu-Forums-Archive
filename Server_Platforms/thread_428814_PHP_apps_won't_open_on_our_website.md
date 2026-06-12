---
title: "PHP apps won't open on our website"
date: 2007-04-30
forum: Server Platforms
---

### Post by TorchlightJay on 2007-04-30
So this is what's wrong. We have a server running Feisty Fawn. We have the latest software on it from synaptic as well. Well the website is setup fine, when we type blah.net it opens the website. However, when we do /phpmyadmin or /squirrelmail, instead of opening the screen in the window, it prompts us if we want to download the php file. It won't open the php in the web browser as a page like it should. I thought it might be my browser so I tried other computers and it did the same. My friend is trying to fix it, he has it working just fine on his Dapper system. he thinks it might be the fact that it's feisty. We actually started in on Edgy but then we upgrade the server. 

And ideas as to what's wrong? The server is apache2 just to let you know. Thanks.

---

### Post by Frosty Cold Drink on 2007-05-01
It sounds like PHP just plain isn't enabled. Check Synaptic to make sure the PHP module for Apache is installed. If it is, try using "sudo a2enmod mod_php". (I haven't seen that one before, just noticed the command in another thread a few minutes ago.)

---

