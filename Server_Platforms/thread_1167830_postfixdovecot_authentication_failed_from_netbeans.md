---
title: "postfix/dovecot authentication failed from netbeans application"
date: 2009-05-23
forum: Server Platforms
---

### Post by ej4Kx on 2009-05-23
I install postfix to test sending email among user in localhost. Everything works fine including from the application i make to send email using netbeans. But when i make an application to receive the message and try to authenticate the password of my account (any user of my localhost) i always get :

-ERR Authentication failed.

i don't think there's anything wrong with my code, just i feel like there's something i need to configure more about the postfix. I installed dovecot too to handle the incoming message and the result is still the same. Anyone ever experienced this before? Or have some clue about what's happening? ):P

Regards.

---

### Post by albinootje on 2009-05-23
> **ej4Kx said:**
> Everything works fine including from the application i make to send email using netbeans.

Can you make a little bit more clear what you're trying to do ?

Postfix is smtp software which can receive and send emails.

Dovecot is an imap/pop3 server which can let you access you emails via imap or pop3, and as a bonus dovecot can do authenticated smtp for you, to send out emails for people with a proper username on that system.

And did you follow a specific howto to set up postfix + dovecot ?
If so, which one (please provide the link) ?

---

### Post by ej4Kx on 2009-05-25
I follow this step :
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

I just installed the basic use of it, not including the SSL or SMPT authentication yet. I test it using telnet and everything works well. I also make a simple program with java (from NetBeans) to send email, and without SMTP auth, and it works fine. Until I make a program to receive the email using POP3, everytime I pass my username and password it says that error. Here is the full respon from the server after i pass the username+passwd :

+OK Dovecot ready.
+OK
-ERR Authentication failed.
+OK Logging out

---

