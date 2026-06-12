---
title: "Samba &amp; Radius server"
date: 2011-01-23
forum: Server Platforms
---

### Post by JBtje on 2011-01-23
Greetings,
 
For a project (for my student union) I am trying to get a fileserver to work.
Now currently we got access to a radius server, which is able to confirm the username and password of a student. I would like to use this radius server, to confirm the identity of the user.
But, there is more... Not all users that are listed in the radius server, may have access to the samba fileshare. Therefor samba, or any other program, has to check first wherever or not this person has access (checking it with the MySQL database).
 
 
So.
1) User tries to login with username X, password Y
2) Samba receives the username X, password Y
3) Somhow Samba checks if username X may have acces, by checking in the MySQL database
4.1) Person has no access acording to the database -> **login fails**
4.2) Person had access according to the database
5) Samba somhow checks with the Radius server if Username X and password Y are a match
6.1) Radius server replies: No match --> **login fails**
6.2) Radius server replies: Match
7) Person get access to the directories he is sposed to get access to.
 
 
I'm an exelent PHP programmer, and in theory if it is possible for Samba to "communicate" with a PHP script of mine, than i think this all would be possible.
 
But I have no clue how Samba works, nor if this is possible at all. Therefor I would like to know what you guys think of this idea? Would it be possible? is it possible for Samba to communicate with a website (php script)?
 
Also, is it possible to make a PHP script that "writes" the configuration file of Samba? (cuz than I can put all people with access in the MySQL database, and export them to a Samba users(?) file each once in a while)
 
 
Best regards,
Jeffrey

---

