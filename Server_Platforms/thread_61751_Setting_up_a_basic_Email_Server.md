---
title: "Setting up a basic Email Server?"
date: 2005-09-02
forum: Server Platforms
---

### Post by Elijah on 2005-09-02
I've setup qmail for our MTA ... not sure if it's fully working or not. I've never setup an email server before. 

What else do I need? and how can I be able to create new accounts like [email]newaccount@company.net[/email] using qmail?

---

### Post by amohanty on 2005-09-02
google and first link:
[http://qmail.3va.net/qdp/docs.html](http://qmail.3va.net/qdp/docs.html)



HTH
AM

---

### Post by Elijah on 2005-09-02
Thanks, I've read [http://www.lifewithqmail.org/](http://www.lifewithqmail.org/) ... that's how I managed to setup the qmail install ... but I'm still having trouble adding users, 

I've seen the qmail-users part of the manual but I'm not sure if that's how I could add new email addresses. I found this format for the assign file:

=address:user:uid:gid:directory:dash:extension:

my first attempt, following this man page:  [http://www.die.net/doc/linux/man/man5/qmail-users.5.html](http://www.die.net/doc/linux/man/man5/qmail-users.5.html)
=elijah@server01.phpdevaps.net:elijah:1002:1002:/home/elijah:::

I ran qmail-newu command and got a bad format error in the assign file.

---

### Post by Emnitec on 2005-09-02
Hello Elijah!

I've been struggeling for years setting up a mailserver in Linux but all efforts ended in installing M$ W2K and Mdaemon Mailserver... 'til I found Ubuntu and a post in this forum about a controlpanel for webhosting that claimed to control web/ftp and mail...

I installed it with the script that was posted in the forum and damn! I have a running mailserver with working webmail!! And, adding users is like as hard as put your shoes on..!! The mailserver it installs is Postfix.

The controlpanel is [VHCS](http://www.vhcs.net) and the link to the post is: [FORUMLINK](http://www.ubuntuforums.org/showthread.php?t=25722&highlight=vhcs). Install this and you have a fully working web/ftp/mail-server in minutes.


/Emnitec

---

### Post by Elijah on 2005-09-02
[QUOTE=Emnitec]Hello Elijah!

I've been struggeling for years setting up a mailserver in Linux but all efforts ended in installing M$ W2K and Mdaemon Mailserver... 'til I found Ubuntu and a post in this forum about a controlpanel for webhosting that claimed to control web/ftp and mail...

I installed it with the script that was posted in the forum and damn! I have a running mailserver with working webmail!! And, adding users is like as hard as put your shoes on..!! The mailserver it installs is Postfix.

The controlpanel is [VHCS](http://www.vhcs.net) and the link to the post is: [FORUMLINK](http://www.ubuntuforums.org/showthread.php?t=25722&highlight=vhcs). Install this and you have a fully working web/ftp/mail-server in minutes.


/Emnitec[/QUOTE]
 looks great, thanks =) I think I'll try that.

---

### Post by LordHunter317 on 2005-09-03
Don't use Qmail for new installations, it's obsolete.

Use Postfix or Exim4 instead.

Both can be configured more or less automatically by Ubuntu and VHCS is overkill and not needed.

---

### Post by Beernut on 2005-09-04
If you want something easy install and use with minimal conig try HULA the calendaring isn't ready yet but the email side of the project works like a charm.

[http://www.hula-project.com/Hula_Server](http://www.hula-project.com/Hula_Server)

---

### Post by TheHaunted on 2005-09-07
[QUOTE=Elijah]Thanks, I've read [http://www.lifewithqmail.org/](http://www.lifewithqmail.org/) ... that's how I managed to setup the qmail install ... but I'm still having trouble adding users, 

I've seen the qmail-users part of the manual but I'm not sure if that's how I could add new email addresses. I found this format for the assign file:

=address:user:uid:gid:directory:dash:extension:

my first attempt, following this man page:  [http://www.die.net/doc/linux/man/man5/qmail-users.5.html](http://www.die.net/doc/linux/man/man5/qmail-users.5.html)
=elijah@server01.phpdevaps.net:elijah:1002:1002:/home/elijah:::

I ran qmail-newu command and got a bad format error in the assign file.[/QUOTE]


Adding users will depend where you have asked qmail to look for user database.
is it /etc/passwd database ? or RDBMS like mysql or LDAP ??

I hope this problem might have been solved by now. If not please let me know.

I also suggest using postfix than QMAIL as postfix is lot simpler for setup .

---

### Post by relix42 on 2005-09-08
[QUOTE=LordHunter317]Don't use Qmail for new installations, it's obsolete.[/QUOTE]

Haven't heard this before.  What's obsolete about qmail?

---

### Post by LordHunter317 on 2005-09-08
It's no longer under development, the one person who can legally maintain a full copy of it (DJB) refuses to do so, and it's not very useful OOB anymore for a modern mailing system.

---

