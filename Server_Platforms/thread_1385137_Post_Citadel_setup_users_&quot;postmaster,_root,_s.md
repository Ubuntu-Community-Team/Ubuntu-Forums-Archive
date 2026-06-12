---
title: "Post Citadel setup users &quot;postmaster, root, smmsp&quot;"
date: 2010-01-19
forum: Server Platforms
---

### Post by volkswagner on 2010-01-19
Hi all,

I am running 8.04 Server on a VPS.  I have installed Citadel.  I also have some web pages that use sendmail for contacts.

I see my mail.info logging a lot of the following entries.

```
mail sendmail[14051]: o0GNe7bS014051: from=smmsp, size=404, class=0, nrcpts=1, msgid=<201001162340.o0GNe7bS014051@mail.server.com>, relay=smmsp@localhost
Jan 16 18:40:10 mail citadel: Session started from localhost.localdomain [127.0.0.1]. 
Jan 16 18:40:10 mail citadel: SMTP server: EHLO mail.server.com 
Jan 16 18:40:10 mail citadel: SMTP server: STARTTLS 
Jan 16 18:40:11 mail citadel: SSL/TLS using DHE-RSA-AES256-SHA on TLSv1/SSLv3 (256 of 256 bits) 
Jan 16 18:40:11 mail sendmail[14051]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Jan 16 18:40:11 mail citadel: SMTP server: EHLO mail.server.com 
Jan 16 18:40:11 mail citadel: SMTP server: MAIL From:<smmsp@mail.server.com> SIZE=404 AUTH=smmsp@mail.server.com 
Jan 16 18:40:11 mail citadel: SMTP server: RCPT To:<root@mail.server.com> 
Jan 16 18:40:11 mail sendmail[14051]: o0GNe7bS014051: to=root, ctladdr=smmsp (108/114), delay=00:00:04, xdelay=00:00:01, mailer=relay, pri=30404, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.6, stat=User unknown
Jan 16 18:40:11 mail citadel: SMTP server: DATA 
Jan 16 18:40:11 mail citadel: SMTP server: RSET 
Jan 16 18:40:11 mail sendmail[14051]: o0GNe7bS014051: o0GNe7bT014051: DSN: User unknown
Jan 16 18:40:12 mail citadel: SMTP server: RSET 
Jan 16 18:40:12 mail citadel: SMTP server: MAIL From:<> SIZE=1428 
Jan 16 18:40:12 mail citadel: SMTP server: RCPT To:<smmsp@mail.server.com> 
Jan 16 18:40:12 mail sendmail[14051]: o0GNe7bT014051: to=smmsp, delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=31428, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.6, stat=User unknown
Jan 16 18:40:12 mail citadel: SMTP server: DATA 
Jan 16 18:40:12 mail citadel: SMTP server: RSET 
Jan 16 18:40:12 mail sendmail[14051]: o0GNe7bT014051: o0GNe7bU014051: return to sender: User unknown
Jan 16 18:40:15 mail citadel: SMTP server: RSET 
Jan 16 18:40:16 mail citadel: SMTP server: MAIL From:<> SIZE=2452 
Jan 16 18:40:16 mail citadel: SMTP server: RCPT To:<postmaster@mail.server.com> 
Jan 16 18:40:16 mail sendmail[14051]: o0GNe7bU014051: to=postmaster, delay=00:00:04, xdelay=00:00:01, mailer=relay, pri=32452, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.6, stat=User unknown
Jan 16 18:40:16 mail citadel: SMTP server: DATA 
Jan 16 18:40:16 mail citadel: SMTP server: RSET 
Jan 16 18:40:17 mail sendmail[14051]: o0GNe7bT014051: Saved message in /var/lib/sendmail/dead.letter
Jan 16 18:40:18 mail citadel: SMTP server: QUIT 
Jan 16 18:40:18 mail citadel: Ending SSL/TLS 
Jan 16 18:40:18 mail citadel: [2646] Session ended. 
Jan 16 18:40:39 mail citadel: Created a new thread "SMTP Send" (0xb7764b90). 
Jan 16 18:40:39 mail citadel: SMTP client: processing outbound queue 
Jan 16 18:40:39 mail citadel: SMTP client: queue run completed; 0 messages processed 
Jan 16 18:40:39 mail citadel: Thread "SMTP Send" (0xb7764b90) exited. 
```

I believe the smmsp entries are due to a cron job to verify sendmail is running.  Does anyone know if I am supposed to create the other users?  I have tried to add them as aliases to may main account, yet I did not get any of the mail directed there.

I was told via Citadel irc that the above users should go directly to the Aide room.  I am having an issue with that room, which may be for another thread.

So what do the folks here running Citadel do with the above users?

Is it ok to use sendmail, or is there a better solution to call citadel for web contact pages?

Cheers!

---

### Post by HermanAB on 2010-01-19
Howdy,

Simply add those users as aliases to your account on Citadel in the Address Book Edit Contact information screen:

```
Primary Internet e-mail address
herman@aeronetworks.ca

Internet e-mail aliases
herman@aerospacesoftware.com 
postmaster@aerospacesoftware.com 
postmaster@aeronetworks.ca 
```

Then all that undeliverable mail will come to you.

---

### Post by volkswagner on 2010-01-19
> **HermanAB said:**
> Howdy,

Simply add those users as aliases to your account on Citadel in the Address Book Edit Contact information screen: ... Then all that undeliverable mail will come to you.

Yes, I did try that, but then removed the entries.  Perhaps I made an error, or perhaps I did not add my FQDN to the host alias, all of which I thought I did do.  I will try again and double check my entries.

I'll post back on the results.

Any comment on having sendmail run for Apache pages, or is there a better way via citadel?

Thanks for the help.

---

### Post by volkswagner on 2010-01-20
Well, after adding the FQDN host name and the aliases, I do have a slight change.

The mail sent to postmaster is now forwarded to Aide room.  The alias is not being honored.  Still better than not finding user=postmaster.  If my Aide room was not broken this would not be a big deal, yet I would still prefer to have it sent to my user account, so reading via Evolution would be easy.

I really thought Citadel was more popular, yet very little input on this thread.  I realize perhaps this is not necessarily an Ubuntu issue.  Citadel documents are very generic as it is designed to run on any distro.  Differentiating if the issue is distro specific is difficult.

I have really been struggling with the documentation available on the Citadel site.

So do I try to fix the Aide room issue, or do I try to force the mentioned users to an alias vs. Aide room?

Does anyone have better or Ubuntu specific documents for running Citadel?

It is only easy if you know how!

---

### Post by HermanAB on 2010-01-20
Well, Citadel usually 'Just Works'.  I have been running Citadel for many years and haven't seen your problem.  You should ask on Art Cancro's site [http://uncensored.citadel.org](http://uncensored.citadel.org) in the Citadel room whether there is a way to debug the issue.  Art occationally trolls the Ubuntu forums, but you would be much better off asking on the real support site.

---

