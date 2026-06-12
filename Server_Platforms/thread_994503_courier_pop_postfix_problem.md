---
title: "courier pop postfix problem"
date: 2008-11-26
forum: Server Platforms
---

### Post by bluethundr on 2008-11-26
Hi guys, 

 I've given up on my pursuit of setting up exim and switched to postfix.

 I really do need to setup  a mailserver as a smarthost. 

 If I telnet mail.mydomain.com 110 in order to test pop, I try logging in but am unable.

 I enter my password (which comes up in cleartext so I am sure that I am typing it correctly) and I get an authentication error.

-------------------------------

-ERR chdir Maildir failed


------------------------------

can someone please help me to resolve this issue? :confused:

---

### Post by Drezard on 2008-11-27
Check this:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

I know theres something in there about setting up Maildirs correctly.

---

### Post by bluethundr on 2008-11-27
Thanks for the tip! That was actually the exact guide I was using to set everything up! :lolflag: Just not sure where I was going wrong!

I _DID_ do some more reading.. and I came across the maildirmake command.


But I couldn't find a decent example of it's usage. 

for instance, should I be typing maildirmake thunderboltha ?

If so, what if any options should I be using in that directive? Also, instead of just a user name I am wondering if I need to enter a full path or which path I should specify? Also, when this step is done, won't I need to change my postfix conf file some where either with the postconf -e command or by editing the file directly?

Thanks in advance

---

### Post by eric_stewart on 2008-11-28
> **bluethundr said:**
> Thanks for the tip! That was actually the exact guide I was using to set everything up! :lolflag: Just not sure where I was going wrong!

I _DID_ do some more reading.. and I came across the maildirmake command.


But I couldn't find a decent example of it's usage. 

for instance, should I be typing maildirmake thunderboltha ?

If so, what if any options should I be using in that directive? Also, instead of just a user name I am wondering if I need to enter a full path or which path I should specify? Also, when this step is done, won't I need to change my postfix conf file some where either with the postconf -e command or by editing the file directly?

Thanks in advance

Just go to the mail user's directory and type in the command there.  It automatically sets up the appropriate directories.  Make sure you change the directories and files' owner to the user's.

/Eric

---

### Post by bluethundr on 2008-11-28
Thanks for the reply. I went to my home directory and typed maildirmake username. When I ls -l'd I saw :

drwx------ 2 username username 4096 2008-11-22 20:14 Mail

and no change in result. :mad: this is driving me NUTS! Any other hints?

I'd appreciate any advice.

---

### Post by bluethundr on 2008-11-28
in addendum. After creating Mail in /home/username I also issued the following commaind:

sudo /etc/init.d/postfix restart
sudo /etc/init.d/courier-pop restart
sudo /etc/initd/courier-authdaemon restart

NO LOVE. Same error. Epic fail.:(

---

### Post by hyper_ch on 2008-11-28
any reason why you use POP3 over IMAP?

---

### Post by bluethundr on 2008-11-28
Well, the reason I'm using pop 3 is that it's not for me. :) I want other people to use this system, and for my mail to be easily usable pop3 has to work. But so does IMAP. I want to get both working!

---

### Post by hyper_ch on 2008-11-28
IMAP with Maildir support and you won't have a 2gb problem as each message will be stored in an individual file.

---

### Post by bluethundr on 2008-11-28
Manually added Maildir to my home directory. Changed mode to 700. Voila!Both POP and IMAP now work. :)


:guitar::guitar::guitar:

---

