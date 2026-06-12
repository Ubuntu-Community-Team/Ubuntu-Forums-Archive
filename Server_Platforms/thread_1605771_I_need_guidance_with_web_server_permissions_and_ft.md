---
title: "I need guidance with web server permissions and ftp"
date: 2010-10-25
forum: Server Platforms
---

### Post by vick_g on 2010-10-25
Hello.

I have been running my own web server for the last year using ubuntu.
Recently, my friend asked if he can host his site on my server and I said yes, of course!


I created a new user with it's own home directory and I uploaded all the content of his site there. Site is up and running but I have a few questions.

His site is running WordPress
WP needs to have permission to write files to the server and create new directories. 
How do I set these permissions?
I also want him to be locked to his own directory and not have the ability to see my files in my home directory (/home/admin)
I want him to be able to login through ftp using port 21
he does not need ssh access..
just access to his own home directory and permissions to read/write/modify/execute 

Do I need to set the owner to www-data : www-data so wordpress can write files?

please help

any good links that I can read more about thse stuff would be great

---

