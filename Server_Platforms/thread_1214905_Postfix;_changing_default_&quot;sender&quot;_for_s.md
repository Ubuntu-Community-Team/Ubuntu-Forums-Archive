---
title: "Postfix; changing default &quot;sender&quot; for sendmail"
date: 2009-07-16
forum: Server Platforms
---

### Post by Fliggerty on 2009-07-16
Hello all!

Figure it's about time I actually register here and start discussing.  :D

I've been running a web server with Intrepid Ibex for a few weeks now.  It was a completely new experience for me (always been a Windows kinda-guy, just about ready to make the permanent switch!)  It's always been very basic web hosting stuff, just have a general LAMP stack.  I've never had the need for it to send email, and now I do.

I used tasksel to install the default postfix setup.  I don't have a domain, but I did register a subdomain with dyndns.com, so I used that for the hostname.  I was able to send an email from command line, specifying the sender, and it worked just fine.

I installed a simple PHP script to test sending an email with sendmail.  It sent everything just fine, except that the sender was www-data, which is the group that owns /var/www.  How can I change that without affecting other aspects of my server?

Also, while I'm asking email questions, what else do I need to do to actually host a full email server?  I have several sites hosted remotely, and we use email from them.  I intend to eventually save some money and host it all myself.  I'm not really sure what my next step on attaining that goal is though.

TIA!

--Fligg

---

### Post by Fliggerty on 2009-07-17
I still haven't been able to find the solution anywhere.  Any advice on where I might look?

---

### Post by albinootje on 2009-07-17
> **Fliggerty said:**
> 
I installed a simple PHP script to test sending an email with sendmail.  It sent everything just fine, except that the sender was www-data, which is the group that owns /var/www.  How can I change that without affecting other aspects of my server?

One option would be to have the php script set a proper From: address.
> 
what else do I need to do to actually host a full email server? 


I'd recommend postfix + dovecot + squirrelmail for that, see here e.g. :
[http://rimuhosting.com/support/settingupemail.jsp?mta=postfix](http://rimuhosting.com/support/settingupemail.jsp?mta=postfix)
[http://wiki.dovecot.org/HowTo](http://wiki.dovecot.org/HowTo)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)
[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

---

### Post by Fliggerty on 2009-07-17
Ah, thank you.  I will certainly read through those.  I appreciate the reply.

I know that using tasksel installed Postfix, and I think Dovecot as well.  So I wonder if I'm ready to go then?  I know that I will want to get other progs such as ClamAV and SpamAssassin at some point, but for now I just want to ensure basic functionality.

---

### Post by albinootje on 2009-07-17
> **Fliggerty said:**
>  I know that using tasksel installed Postfix, and I think Dovecot as well.  So I wonder if I'm ready to go then?  


Sounds like you have the basic setup almost ready.

You should think about how you want the setup though, e.g. do you want virtual users or not ?

Personally i like having virtual mail users with postfixadmin as web interface for letting users change their passwords and change their forward, or auto-reply.

Here's a howto :
[http://rimuhosting.com/knowledgebase/linux/mail/postfixadmin](http://rimuhosting.com/knowledgebase/linux/mail/postfixadmin)

---

### Post by Fliggerty on 2009-07-17
Ah, ok.  That makes sense, and certainly looks intriguing.   I think that is certainly the way I want to go.  Thank you!  :D

This does bring up one more question though.  I wasn't aware that Postfix used a MySQL database.  I don't seem to have such a database.  Do I need to do something special to set this up?

---

### Post by albinootje on 2009-07-17
> **Fliggerty said:**
> Ah, ok.  That makes sense, and certainly looks intriguing.   I think that is certainly the way I want to go.  Thank you!  :D

This does bring up one more question though.  I wasn't aware that Postfix used a MySQL database.  I don't seem to have such a database.  Do I need to do something special to set this up?

You have several options, for example :

1) postfix + dovecot + regular "UNIX" users (normal users, just like you have on an Ubuntu desktop machine).

2) postfix + dovecot + postfixadmin, which means using mysql (or perhaps postgresql).

3) postfix + dovecot + mysql without postfixadmin, which also means using mysql.

4) postfix + dovecot + LDAP (no "normal" users, no sql database, but LDAP for authenticating the users)

I like option 2) :) but the easiest to start with, by far, is option 1)

---

### Post by Fliggerty on 2009-07-17
Okay, I see now.  Option 2 does sound to be the best for me.  It looks to be the closest to how my current VPS is setup.

The "easiest" way doesn't always appeal to me.  I learned from years and years of being a "Windows Power-User" that "easy" also means "will crash sooner or later."  ;)

Thank you for all of your help.  You've been most kind.

--Fligg

---

