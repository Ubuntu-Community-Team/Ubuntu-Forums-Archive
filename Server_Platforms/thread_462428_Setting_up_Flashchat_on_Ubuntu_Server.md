---
title: "Setting up Flashchat on Ubuntu Server"
date: 2007-06-02
forum: Server Platforms
---

### Post by ntpnick on 2007-06-02
Hello, I am trying to set up Flashchat* on Ubuntu feisty fawn server edition, but seeing as I am a newbie I got stuck on one of the first steps...I have no clue where to place the folder so that it will be accessible through the browser, you know "Index of /" type thing. So any help with placing the folder and with the other steps would be appreciated.

Side note: I have the the Desktop GUI installed.
* [http://www.tufat.com/script2.htm](http://www.tufat.com/script2.htm)

---

### Post by pbw on 2007-06-03
Default public html on ubuntu is located at /var/www .. so place it there if you'd like it to be yoursite.com or make mkdir chat in /var/www and install it there and you'd get yoursite.com/chat

---

### Post by ntpnick on 2007-06-03
Alright it seemed like I didn't have permission to so, I just sudo mv it. Now when I check on the index and click the chat folder this comes up 

> Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required 'var/www/chat/index.php'
(include_path='.:/usr/shar/php:/usr/share?pear') in Unknown on line 0

---

### Post by pbw on 2007-06-03
sudo apt-get install php-pear

sudo chown -R yourusername.users /var/www

sudo /etc/init.d/apache2 restart

See if that helps.

---

### Post by ntpnick on 2007-06-03
Same error come up....

Was anything suppose to come up after the command sudo chown -R yourusername.users /var/www because all that comes up is the shell prompt that contains your user name and the name of the machine.

---

### Post by pbw on 2007-06-03
No, chown just changes ownership of the files, so now you can manipulate files in your public html directory without sudo'ing.

Try changing permissions on your chat files to solve the warning. to solve the error you might like to try installing pear-http. Don't know if it'll help, but here's the brief description - PHP PEAR module for HTTP related stuff

---

### Post by ntpnick on 2007-06-03
I played around with permissions from the properties, and got it it to work. Thanks for your help :D

I have hit another bump though...It failed one part of the server environment tests.
> /bot/programe/src/botinst/ is executable (chmod 755): 	No

What can I do about that?

---

### Post by pbw on 2007-06-03
good stuff ntpnick. In terminal type.. chmod 755 /var/www/chat/bot/programe/src/botinst/

---

### Post by ntpnick on 2007-06-04
Alright thanks.

Another quick question, I was trying to set up a new mysql database for flashchat with the command > mysqladmin create Flashchat_db
but it keeps giving me this output
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'myusername'@'localhost' (using password: NO)'

---

### Post by ntpnick on 2007-06-05
Never mind, I got the whole thing set up now.

---

