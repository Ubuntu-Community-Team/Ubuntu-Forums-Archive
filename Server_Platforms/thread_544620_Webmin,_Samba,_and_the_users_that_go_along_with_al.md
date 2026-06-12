---
title: "Webmin, Samba, and the users that go along with all that..."
date: 2007-09-06
forum: Server Platforms
---

### Post by _SKIN_ on 2007-09-06
I have setup my server using ubuntu server 7.04. I got webmin running, no problem. Got samba running, no problem. I can not however, for the life of me find out how to add users. 

My goal is to have all of my computers access a share on the samba file server. Each of the users will need rights to see their own share and one other "general" share. 

I can see where you change passwords for the unix users, I can see where you add shares.

Is this something you can do solely with webmin or do I need to go cui?

---

### Post by _SKIN_ on 2007-09-07
Bump... Some one just tell me that I am stupid or something. Anything. :confused:

---

### Post by _SKIN_ on 2007-09-07
First create your users in unix. Then under Samba in webmin, go to "Convert Unix users to Samba users". Click convert users. Easy... Now I need to figure out how to setup directory shares. Anyone?

---

### Post by Brazen on 2007-09-07
On the Samba page in Webmin, there is a link at the top for "create a new file share"

---

