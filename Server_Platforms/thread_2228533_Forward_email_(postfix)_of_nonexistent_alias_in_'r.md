---
title: "Forward email (postfix) of nonexistent alias in 'real' domain"
date: 2014-06-08
forum: Server Platforms
---

### Post by wintermute000 on 2014-06-08
Postfix setup here. Works fine as a normal email server (no LDAP/SQL, just vanilla using system users) with all the appropriate MX/SPF records etc.

I'm trying to forward email to an alias to an external email, and not getting anywhere. 
All I can find are instructions for

- forwarding virtual domains - not applicable, I want to forward [email]X@domain.com[/email] where domain.com is real and I'm not forwarding everything on it. 
- aliases - OK I can easily get the alias forwarded to another user, but I want it sent to external gmail.

Any tips?

---

### Post by wintermute000 on 2014-06-08
OK figured it out - .forward file

---

### Post by SeijiSensei on 2014-06-08
I prefer to put aliases in /etc/aliases so I can manage them centrally:

```
joe:       joe@example.com
```

will forward mail for joe to the remote address.  You must run the command "newaliases" as root after making changes to this file to update the database.

---

### Post by wintermute000 on 2014-06-09
curious. I've made this change

virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf

And created the appropriate tables etc. in mysql, put my production domain in the appropriate table, and all working.

Question is /etc/aliases still in use? When I add something in /etc/aliases, it doesn't seem to work, and I get an unknown user error in my mail log. 

Is it because I've defined my domain in below

virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf

So basically everything going to my @domain is getting looked up in the SQL alias table? And the inference is, etc/aliases will continue to work for anything I have NOT defined in the table referenced in mysql-virtual-mailbox-domains.cf?

---

### Post by SeijiSensei on 2014-06-09
I have no idea.  I never use databases for email servers.  My servers have a small number of users, so I just set up Unix accounts for them.  But if you have all that stuff with virtual maps and the like, then I'm afraid I can't help.

I see people here who report setting up email servers with all sorts of bells and whistles, probably because they are following random guides on the Internet.  These kinds of elaborate systems make sense to me only if you are handling hundreds of accounts.  I've managed email servers in office settings with >200 users; we just gave them Unix accounts with /usr/sbin/nologin as the shell.

---

### Post by wintermute000 on 2014-06-10
This is a pure learning experience including self hosting domain etc. I had everything setup without SQL so I thought I might as well learn to do it properly, and migrated across to virtual maps.
Also, I figured i want the system to be able to handle other domains, which apparently you can't without virtual domains.

Its no different from using apache virtual hosts even if you only have one or two sites? 

If I was doing a system for production, I wouldn't be asking basic questions in a public forum.... Which is why I ask such questions now lol

---

