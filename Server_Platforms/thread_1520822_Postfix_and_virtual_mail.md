---
title: "Postfix and virtual mail"
date: 2010-06-30
forum: Server Platforms
---

### Post by cellarosi on 2010-06-30
I'm trying to set up a mail server. This is what i need.

I have to accept all mail come from @domain1.com and @domain2.com.
I need also to forward the mail in different folder if the user is the same and the domain is different.

I mean, for example: I wanna that [email]info@domain1.com[/email] put the mail on /home/mail/domain1/info/ and [email]info@domain2.com[/email] put the mail on /home/mail/domain2/info/.

Could you give me a little configuration about that. Only a part I need to create a virtual mail.
I tried to follow a postfix manual without succeed. 
I have just configured a "normal" mail server (without virtual mail) and it works so I need also a miss part to make it work the different user in different domain.

Thanks in advance.

---

### Post by cellarosi on 2010-07-01
No one?

---

### Post by cellarosi on 2010-07-02
Up!

---

### Post by volkswagner on 2010-07-02
There are several how to's.  This is not for the faint of heart.  Most folks will tell you when you are done pulling your hair out, just install Citadel or Zimbra.

Here is what you asked for.

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

Here is the one I used back when 8.04 was current.  It has been updated to 10.04

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Enjoy.

---

### Post by cellarosi on 2010-07-02
Thanks for the answer.
But do you think this is a only way to do what am i ask?

It's really strange that posfix doesn't provide anything to do in more easy way.. :P

In any case I'll try Zimbra and I let you know.

Thanks so much for the moment.

---

