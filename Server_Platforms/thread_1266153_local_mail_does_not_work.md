---
title: "local mail does not work"
date: 2009-09-14
forum: Server Platforms
---

### Post by doru001 on 2009-09-14
Local mail, between two users (*root *and *user*) on one Ubuntu machine, does not work. 
I am using mailx as MUA and postfix as MTA. I followed these instructions: 
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
The test worked. 

I see errors in /var/log/mail.info:
postfix/error[8785]: BA64315F9C: to=<root@127.0.0.1>, relay=none, delay=0.32, delays=0.09/0.12/0/0.11, dsn=5.1.3, status=bounced (bad address syntax)

root has no mailbox: 
# ll /var/mail
total 0
-rw-rw---- 1 user mail 0 2009-09-14 12:23 user
# cat /etc/aliases
# See man 5 aliases for format
postmaster:    root
# Added by installer for initial user
root:   user

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
says that I should configure mailx to use ~/mail as mailbox, but I found no way to do that. 

I believe I have installed Ubuntu with full mail server, like [gcornett]("http://ubuntuforums.org/member.php?u=103981") here: [URL="http://ubuntuforums.org/showthread.php?t=1041665&highlight=mailx+local"]http://ubuntuforums.org/showthread.php?t=1041665&highlight=mailx+local
[/URL] The solution gcornett has applied, to reinstall the system with local mail server, is not attractive. I messed up with dpkg-reconfigure postfix and with /etc/postfix/main.cf several times, but in vain. 

I have found the following similar cases: 
 [http://www.experts-exchange.com/OS/Linux/Q_22502033.html](http://www.experts-exchange.com/OS/Linux/Q_22502033.html)
[http://www.experts-exchange.com/OS/Linux/Distributions/Debian/Q_24172709.html](http://www.experts-exchange.com/OS/Linux/Distributions/Debian/Q_24172709.html)

Please post the main.cf and /etc/mail.rc of a working system. 
Any information that would help me find my way around is welcomed.

---

### Post by doru001 on 2009-09-16
To summarize: 

1. It seems that, when one installs Ubuntu server with Internet mail server included, local mail does not work, not to mention Internet mail. When one installs Ubuntu server with local mail server included, local mail works. 
2. Nobody bothered to confirm or contradict the above statement, using their own installation configuration. All one has to do is to: 
mail user 
some test email between two local users, text mode. 
3. Nobody bothered to post his configuration files, /etc/postfix/main.cf and /etc/mail.rc, from a system where local mail works. This would possibly help me avoid reinstall.

---

### Post by doru001 on 2010-02-23
Configuring the mail server under linux is difficult because: 

1. mail servers under linux can do a lot, they can service thousands of  clients over lan and in other configurations, 
2. security certificates are a story of their own, and they need to work  well with the mail server. 

That is why to learn how to configure a mail server under linux takes  weeks rather than days. 

However, I managed to make postfix send mail (but I failed to make  fetchmail receive mail) with this: [https://help.ubuntu.com/community/GmailPostfixFetchmail](https://help.ubuntu.com/community/GmailPostfixFetchmail)

---

