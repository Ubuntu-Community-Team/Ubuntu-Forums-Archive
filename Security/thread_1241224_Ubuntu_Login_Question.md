---
title: "Ubuntu Login Question?"
date: 2009-08-15
forum: Security
---

### Post by JonnySnip3r on 2009-08-15
Hey guys is there a way to edit the ubuntu login screen? i mean is there away i can add extra fields, like you have Username and Password as default but can i add maybe another field requireing summin else a number maybe?

Thanks in advance!

---

### Post by lisati on 2009-08-15
Please forgive me if this seems obvious, but one place to start would be to look at your options at System->Administration->Login Window

---

### Post by JonnySnip3r on 2009-08-15
Thanks for the fast reply dude, i dont mean that i know about the login options i mean when u make one of those login screens your self can you add extra fields to it? Im a windows user mainly and wanna get o know linux a bit better because windows is pis##ng me off at the momet and im use to coding Visual Basic, C# etcso wanna learn how to develop for this and first stop was the login section :)

---

### Post by scorp123 on 2009-08-15
> **JonnySnip3r said:**
> Hey guys is there a way to edit the ubuntu login screen? You can "theme" it. There are instructions out there on how to do it ... 

> **JonnySnip3r said:**
>  i mean is there away i can add extra fields, like you have Username and Password as default but can i add maybe another field requireing summin else a number maybe? And why would you do that? Let's suppose you successfully added an extra-field that takes numbers ... then what? Ubuntu and GNU/Linux in general still just require a valid username + password combination for a successful login. So even if you created a dozen or so extra-fields they would be totally without any relevance to the underlying authentication mechanism that checks the username and password against whatever database the system is defaulting to (usually local usernames and passwords; but NIS, LDAP or Active Directory might also be possible in an office environment).

So instead of starting with the login screen, you'd have to familiarize yourself with Linux' "PAM" (please use Wikipedia for the details), how to write "PAM" modules and profiles and then you'd have to program a totally new authentication scheme that not only asks for a username and password but also expects additional tokens such as numbers, birthdays and what not be entered. That should be your first priority. Adjusting the login screen and give it extra fields is the least of the troubles ahead ....

[http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules](http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules)
[http://linux.die.net/man/8/pam.d](http://linux.die.net/man/8/pam.d)

.
.
.
.

---

