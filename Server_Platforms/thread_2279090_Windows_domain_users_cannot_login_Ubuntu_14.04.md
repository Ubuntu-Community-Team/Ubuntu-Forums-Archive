---
title: "Windows domain users cannot login Ubuntu 14.04"
date: 2015-05-20
forum: Server Platforms
---

### Post by rob136 on 2015-05-20
[SIZE=2][FONT=arial]Hi all, I've just joined this forum and not sure if this is the right place to ask for this type of help. More than happy if my thread/post is moved to the appropriate area :)

I have an assignment that requires windows domain users to be able log in with their designated username and password, but it's not working for me. And Yes, I have configured the necessary file to allow Ubuntu to show the "manual" log in menu when Ubuntu is booted.
My Ubuntu client machine is already connected to the windows domain. The only thing works are the domain users that I previously created in a separate organization user group folder in windows 2008 server which in this case is I have 3 groups within that seperate user group; Bakers, Management, and Accounting. Bakers has 1 user called/username "Baker" Management has 1 user called "Manager" and a user for Accounting called "Accountant".
What we are required to do is, create a new user in the default "Users" folder in the windows 2008 server r2, with a designated username/password. Then we have to try log in with that new user account into the domain. When attempted to login, it fails for some reason (authentication failed etc...). We have tried all types of login including DOMAINNAME\username or [EMAIL="username@domainname.local/.com"]username@domainname.local/.com[/EMAIL] or just the user name by itself with the designated password. It just won't work.

The baker, manager and accountant domain users all log in successfully since they are part of a different'"Organizational" folder.
My domain name ends in ".local". Yes, I have edited the necessary files to allow Ubuntu to join ".local" domains successfully. Since by default, it does not recognize domains ending in ".local". Only .com 
Anyone know a fix to this? Or why it is happening? Could it be a firewall problem on ubuntu or windows 2008 server? Am I missing something? 

I am using virtualbox to accomodate ubuntu 14.04 LTS and windows server 2008 r2 hpc virtual machines.
If you need some clearer clarification, please just say so, my apologies if my explanation is not clear

Thanks [/FONT][/SIZE]

---

### Post by cariboo on 2015-05-20
Keep in mind we will not do your homework for you, but we can offer suggestions.

---

