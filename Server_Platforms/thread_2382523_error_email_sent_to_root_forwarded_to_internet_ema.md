---
title: "error email sent to root forwarded to internet email"
date: 2018-01-14
forum: Server Platforms
---

### Post by jfaberna on 2018-01-14
I have configured my headless Ubuntu 16.04 server to send email using a gmail address.  So commands like this work:

echo "This is a test"| mail -s "Test" [email]johnDoe@gmail.com[/email]

So [email]johnDoe@gmail.com[/email] gets an email from the email address I put in the /etc/ssmtp/ssmtp.conf file.

How do I get those system error messages that are normally sent to root@localhost to be sent to an external gmail.com address?

Jim A

---

### Post by SeijiSensei on 2018-01-14
You need to create an aliases file.  I've never used ssmtp, but it appears that it does not use the file /etc/aliases for this purpose, the way sendmail and Postfix do.  Take a look at this article and the comments that follow: [https://possiblelossofprecision.net/?p=591](https://possiblelossofprecision.net/?p=591)  

Apparently you need to install the bsd-mailx package. use mailx instead of mail, and put aliases into /etc/rc.mail.

If you used the default SMTP provider in Ubuntu, Postfix, or the hoary Berkeley sendmail like I do, you could put entries in /etc/aliases like this:
```
root     someone@example.com
```
and root's mail would be forwarded to that account.

---

### Post by jfaberna on 2018-01-15
> **SeijiSensei said:**
> You need to create an aliases file.  I've never used ssmtp, but it appears that it does not use the file /etc/aliases for this purpose, the way sendmail and Postfix do.  Take a look at this article and the comments that follow: [https://possiblelossofprecision.net/?p=591](https://possiblelossofprecision.net/?p=591)  

Apparently you need to install the bsd-mailx package. use mailx instead of mail, and put aliases into /etc/rc.mail.

If you used the default SMTP provider in Ubuntu, Postfix, or the hoary Berkeley sendmail like I do, you could put entries in /etc/aliases like this:
```
root     someone@example.com
```
and root's mail would be forwarded to that account.

I would rather use the default mail handling packages in Ubuntu if I could just to keep things standard as possible.  It's just that I found an article on setting what I wanted up using ssntp.  The goal is simply to use echo statements in cron files to sent out warnings or errors to a real email account.  And also have the root mail messages sent out as well.

How would I do this with just the default mail packages?

jim A

---

### Post by jfaberna on 2018-01-15
Here's an update.  I kind of have stuff working with standard Ubuntu 16.04 repository items.
I install mailutils and ssmtp. Then edited /etc/ssmtp/ssmtp.conf per the instructions at:
[https://help.ubuntu.com/community/EmailAlerts]("https://help.ubuntu.com/community/EmailAlerts")

I can get emails at any email account I've tested and my sender is an account I setup on gmail for the server's use only.

I have the aliases setup in /etc/ssmtp/revaliases per that same example.

What I can't test is what happens if the system sends an error email to root@localhost.

Any way to test that, short of an error in the system??

Jim A

---

### Post by SeijiSensei on 2018-01-15
```
echo test | mail -s test root
```

I'll hold off answering your other question until we see if this works.

On my server running sendmail, that command results in an message in my personal account to which root is aliased in /etc/aliases.

---

### Post by jfaberna on 2018-01-15
Well interesting.  The mail.log indicates that a mail was sent.  However if I use another PC  and login to gmail for the account that I'm using to send email from the server I see emails indicating an error:

Your message wasn't delivered to root@mythbuntu because the domain mythbuntu couldn't be found. Check for typos or unnecessary spaces and try again.

DNS Error: 15185254 DNS type 'mx' lookup of mythbuntu responded with code NXDOMAIN Domain name not found: mythbuntu

So the root account's mail is being forward, but the domain is a problem.  Since this server is on a private network I don't need a register domain outside the local network.

Ideas?

Jim A

---

### Post by SeijiSensei on 2018-01-15
Any mail sent over the public Internet requires RFC822 addresses of the form [email]user@domain.name[/email].  The sender address must have a domain so that the receiving server can send bounce messages to it when necessary.

You might be able to forge the sender address to match an account you own.  I have no idea how to do that with ssmtp.  It's possible with other mail exchangers, but it takes a bit of work.

Using the same address for From as you use for To may not work, as this combination will often run afoul of spam filters.  (Spammers have used this technique for years.) I'm pretty sure GMail, for one, doesn't like that pairing.

---

### Post by jfaberna on 2018-01-15
I guess I have a lot to learn.  It seems that the /etc/ssmtp/revalaises file settings aren't helping:
```
root:johndoe@gmail.com:smtp.gmail.com:587
```

I thought that mail sent to root would really go to [email]johndoe@gmail.com[/email]

---

### Post by jfaberna on 2018-01-15
so I can get email sent out to any internet email address using the 'mail' command without generating any errors.  However, any mail sent to root or jim (my username) will go to the address I setup as the server's gmail address and I also get a gmail mail-daemon email stating that it couldn't send to root@myserver-hostname or jim@myserver-hostname because of no domain called myserver-hostname. based on what I've googled, I've tried /etc/revaliases and /etc/mail.rc but nothing helps.

Any cron program I'm interested in can be modified to use: echo "error message" | mail -s "error log" [email]my-personal-email@gmail.com[/email] without any problems.  So I can get most all of what I want.  I'm just concerned that any email to root will get sent incorrectly.  I don't know if that is a big problem.

Jim A

---

### Post by jfaberna on 2018-01-16
I found out this morning that by putting;
```
MAILTO:myemail@gmail.com
``` 
in /etc/crontab I get the errors that happened in cron programs emailed to me.  That combined with emails I put into cron programs, I'm covered i.e.
 ```
echo "error message" | mail -s "error in program xyz" [email]myemail@gmail.com[/email]
```
I have not seen any emails sent to root@localhost anyway.

Jim A

---

