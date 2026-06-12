---
title: "SADMS/AD login question"
date: 2007-04-09
forum: Server Platforms
---

### Post by taliosfalcon on 2007-04-09
I have a school proejct to setup linux active directory integration, i've managed to get the ubuntu machines to join the domain..i think..they passed all the SADMS diagnostics and post install checks and pulled the usernames and shares off of AD, however i'm not sure how to login with those accounts. Just the username and password doesnt work, is it some variation of domain/username or username@domain for the login? or is there some other step i'm missing? any help would be greatly appreciated. :confused:

---

### Post by rsermilik on 2007-04-09
If I use linux at work in our AD windows environment I have to use DOMAIN\username as the username. If your windows domain is school and your username is tali you should use SCHOOL\tali as the username. We use Win2003 env. at work
regards

---

### Post by taliosfalcon on 2007-04-10
ok, doing some more tests it seems like all of my accounts are failing authentication for some reason,
AUTHENTICATION TEST
--------------------------------------------------------------------------------
+AUTHENTICATION
+authenticating gub_oldstar
plaintext password authentication succeeded
challenge/response password authentication succeeded
+authenticating LINDOWS/gub_oldstar
plaintext password authentication succeeded
challenge/response password authentication succeeded
+authenticating LINDOWS.NET/gub_oldstar
plaintext password authentication failed
challenge/response password authentication failed
+impersonating gub_oldstar
su: Authentication service cannot retrieve authentication info.
(Ignored)
uid=11108(gub_oldstar) gid=10513(domain users) groups=10513(domain users),11103(Linux Ubuntu),11104(Windows XP)
ok
+impersonating LINDOWS/gub_oldstar
su: Authentication service cannot retrieve authentication info.
(Ignored)
uid=11108(gub_oldstar) gid=10513(domain users) groups=10513(domain users),11103(Linux Ubuntu),11104(Windows XP)
ok
+SID
+getting security id (sid) for LINDOWS/gub_oldstar
S-1-5-21-160151551-4186340959-228923462-1108
+getting login from LINDOWS/gub_oldstar sid
LINDOWS/gub_oldstar
[OK]

error code was NT_STATUS_NO_SUCH_USER (0xc0000064)
error messsage was: No such user
Could not authenticate user LINDOWS.NET/gub_oldstar%p@ssword1 with plaintext password
error code was NT_STATUS_NO_SUCH_USER (0xc0000064)
error messsage was: No such user
Could not authenticate user LINDOWS.NET/gub_oldstar with challenge/response
authenticating LINDOWS.NET/gub_oldstar failed

is the message it spits out, now the computer has successfully joined the domain at this point and pulls down allt he usernames and accounts, but for whatever reason those accounts arent authenticating with the domain controller. Does anyone know if anything in the above output gives any indication as to why this is? (its all greek to me :( )
edit: it gives the same error/process for any account i try the authentication test with, and i've tried every combination of LINDOWS\username, LINDOWS/username, LINDOWS.NET/username etc. i can think of

---

