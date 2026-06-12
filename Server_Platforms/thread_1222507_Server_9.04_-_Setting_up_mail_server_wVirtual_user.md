---
title: "Server 9.04 - Setting up mail server w/Virtual users &amp; MySQL"
date: 2009-07-25
forum: Server Platforms
---

### Post by WindowsSurvivor on 2009-07-25
OK I tried posting this at linuxquestions[notanswers].org and 4 days later I still have nothing, so maybe someone here can try to help me?

I'm trying to break away from Windows altogether.  I host my own websites on my own server at home (business internet, static IP, etc.) and I would LOVE to be 100% Linux.  Right now it's just my laptop.  I'm still dependent on a Windows server.

I've managed to get Apache working great.. same with FTP.  Now I just need to set up a mail server.

Because of interactive web applications, I NEED the mail server to be able to handle multiple domains, aliases, forwarding, etc.  You know, typical mail server stuff.  But the big issue for me is I absolutely HAVE to have it based on MySQL.  I need PHP scripts to be able to add/remove/edit/change pw's/change forwardings/etc. on the mail server.  PHP MUST have full control over the mail server.

I've read plenty of tutorials that say it's possible, and I've followed them precisely to a TEE.  I've set up the databases, executed every single instruction, and still NOTHING.

I'm SURE it's a stupid setting on my end... where I didn't put the right value in or something.  The tutorials aren't very clear on what I should use for values, they just say "server1.example.com" and while it's obvious that "example.com" is "mysite.com", what does "server1" mean?  Does it mean the name of my server? (I named it linuxserver) does it mean "linuxserver.mysitename.com"?  does it mean "www.mysitename.com"?  does it mean "mail.mysitename.com"?  Or does it just mean "mysitename.com"?

Anyway, after setting it up, I'd try it and it wouldn't work.  The only error returned from my mail client was "failed to connect" or "login incorrect" (even though the login was fine).  Same with the server-side logs.

When the server would fail, I'd format it and try it all over again.  I've tried it 9 times so far with every possible variation I could think of.  I've tried the following tutorials:

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10)
(yes I know it was for 8.10 and I'm running 9.04 but I figured it couldn't hurt to try)

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

[http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)

[http://howtoforge.org/set-up-ubuntu-server-with-ehcp-lamp-dns-ftp-mail-p2](http://howtoforge.org/set-up-ubuntu-server-with-ehcp-lamp-dns-ftp-mail-p2)

NONE of them have worked for me and I have EXPLICITLY followed the instructions.  I'm SURE it's some stupidity on my part and I'm not setting something up right... 

Now, can someone PLEASE PLEASE PLEASE help me with this???  

Thanks in advance.

---

### Post by WindowsSurvivor on 2009-07-25
Bump

---

### Post by HermanAB on 2009-07-25
Hmm, go to citadel.org and run easy install.  There are also Citadel guides on my web site.

---

### Post by TaTaE on 2009-07-26
Read the logs. They are placed in /var/log/

For example
tail /var/log/syslog

---

### Post by WindowsSurvivor on 2009-07-27
I tried Citadel, didn't care for it... I couldn't even get it to work right.

And the logs aren't showing me anything useful either..  But thanks for the replies!

Am I missing some setting or something? What should my hostname be?  Should I edit the bindings??

---

### Post by kustomjs on 2009-07-28
are you planning using postfix+dovecot+mysql for your email server? if so I know how to set it up.

---

### Post by druhboruch on 2009-07-28
This link may help you a bit:
[http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/](http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/)

---

### Post by cballinger on 2009-07-31
Thanks for the link druhboruch. I saw ubuntu forums referring traffic and tracked it down. If you have any questions on the walk through, WindowsSurvivor, let me know.

---

