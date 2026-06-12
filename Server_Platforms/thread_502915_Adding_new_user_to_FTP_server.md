---
title: "Adding new user to FTP server"
date: 2007-07-17
forum: Server Platforms
---

### Post by guilly on 2007-07-17
Either i'm doing something wrong or it's because i'm in standalone mode??

i can't seem to get more then one user authenticated thru my server. In my config i have something like this:

UserAlias sauron userftp
UserAlias Jimbo   user2


<Limit LOGIN>
AllowUser userftp
AllowUser user2
</Limit>


user2 does nto seem to be able to log in, it keeps giving me 530 error saying incorrect password.

is this cause I'm in standalone mode? As i understood it standalone so for servers that are not accepting alot of connections but can still accept multiple connections, did i miss understand?

thanks

---

### Post by xjdriver69 on 2007-07-30
guilly,
  What FTP server are you running?  I use Proftpd and to be honest I dont set up users in the config file.  You can use you local server users for authentication.  No config file to alter.  If you are worried about security you can also jail your users fairly easy in proftpd also.  Just an idea.  good luck

---

### Post by HermanAB on 2007-07-31
I suggest that you leave the default configuration of proftpd or vsftpd alone and if you need another user, simple add a system user using the wizard.

---

