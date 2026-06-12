---
title: "Suggestion on a mail server implementation"
date: 2012-06-21
forum: Server Platforms
---

### Post by Debie on 2012-06-21
Hi all,
I'm new to the "mail server world" and I need some tips on a simple but (maybe) not usual configuration:

[LIST]
[*]In our company we use a proprietary mail server hosted on a server farm outside our head quarter and it doesn't support IMAP.
[*]I was instructed to implement an internal mail server, with imap support, that download the emails for each users and store them.
[*]With this configuration each users will download the emails via IMAP from internal server usign various email client (thunderbird, outlook...).
[/LIST]
What configuration you suggest to use in this case?

Thanks

---

### Post by LHammonds on 2012-06-21
There are several ways to skin that cat.  Check my sig for my notes on how I installed Zimbra 7.2.0 on Ubuntu Server 10.04 LTS

LHammonds

---

### Post by Debie on 2012-06-22
Thank you LHammondsfor the replay.
Zibra is absolutely the next step but for now I was thinking to something simple.
Something like:

fetchmail to grab the emails
dovecot or courier for an internal pop3/imap server
postfix with relay configuration to sent email via external smtp server (and to store them)

Is this a right implementation or there is something better?

---

### Post by SeijiSensei on 2012-06-23
> **Debie said:**
> Something like:
fetchmail to grab the emails
dovecot or courier for an internal pop3/imap server
postfix with relay configuration to sent email via external smtp server (and to store them)


That's what I'd use, Debie.  I take it the remote provider supports POP3 but not IMAP?  The simplest configuration would be a server with dovecot, ordinary mbox mailboxes, and ordinary accounts for each user.  You could set that up in a day even if you haven't done this before.  Gotchas to avoid include:

1)  [Removing]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#inet_interfaces") the limitations in the default Postfix configuration that has it listening only on the localhost (127.0.0.1) interface and [enabling]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from") it to accept mail from machines on the local network.

2)  Configuring the server's [hostname]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#myhostname") and [domain]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydomain").

2)  Developing a method to add/remove users from the server.  If everything is run by you or a small number of competent admins, then you could use either the command-line adduser/passwd commands, or the graphical user account manager if you have a GUI desktop environment installed.  (By default, Ubuntu server has no GUI, though you can add one.)  Another option is to install Webmin and manage the server via a browser.

4)  Mapping from the external accounts to internal accounts.  If the external server has a single POP box that has all your domain's mail, then you just tell fetchmail to download that account's mail and deliver messages addressed to "joecool@example.com" to the "joecool" account on the local server.  If each person has an individual remote account, then you'd need multiple fetchmail instances that poll each account.

5)  Spam/virus filtering.  If this is done by the remote provider, then you're all set.  If all you get is the raw unfiltered mail, you'll probably need to add local filtering.  If you need to do that, I can give you some suggestions.

---

### Post by kennethconn on 2012-06-23
SeijiSensei, is your suggested set-up possible for a small business scenario that have domain email hosted by a provider but who only have a dynamically assigned IP address at their site as their connection to Internet. What else would be required?
 
I want to implement a mail server sytem locally that stores all emails for all users of a domain (as a backup only).
 
Also, in relation to new users, can the process be automated in any way, or is it a case of add a new user in your control panel of email provider, then also add the user on the server, set up fetchmail or getmail to poll the new account.
 
Manually doing so would not be a problem, as it is only a small number of users, but I am trying to think about the best way to implement it (that could also apply to a larger organisation if needed).

---

### Post by SeijiSensei on 2012-06-23
> **kennethconn said:**
> SeijiSensei, is your suggested set-up possible for a small business scenario that have domain email hosted by a provider but who only have a dynamically assigned IP address at their site as their connection to Internet. What else would be required?

I want to implement a mail server sytem locally that stores all emails for all users of a domain (as a backup only).
 
If you use fetchmail it really doesn't matter what your IP is.  It just works as a mail client like any other.  It logs into one or more remote mailboxes, fetches the messages, delivers them locally.

> Also, in relation to new users, can the process be automated in any way, 

Well if the task is simply archiving messages, you could probably run fetchmail as root, have it poll your users' mailboxes sequentially, and store the result in root-owned mailbox on your server.  Then you'd only need to add each user's remote address and remote password to some file that fetchmail uses.  You might need to write a bash script to do this, one that iterates over the account:password list, logs in as that user, and backs up the mail.  If the script runs as root you could set 600 permissions on the password list for privacy, or even encrypt it locally with a root-owned key stashed somewhere with 600 permissions.

If you're handy with PHP or another scripting language like perl or Python you could write a small application to handle this.  In PHP, for instance, if the mail host supports IMAP, I'd use the built-in [IMAP functions]("http://www.php.net/manual/en/book.imap.php") in PHP to manage this task.  I'd put the username/password combos in an SQL database (I prefer PostgreSQL myself), after encrypting each password with something like AES256.  I written a couple of simple PHP functions that use a combination of serialize(), the mcrypt functions, and base64_encode() to encrypt or decrypt entire PHP arrays and store them as plain text.  A function like that with an array of usernames and password would work well.  Then you'd just iterate over the accounts as before and use the IMAP functions to take a snapshot of the remote mail store.

---

### Post by Debie on 2012-06-24
> **SeijiSensei said:**
> That's what I'd use, Debie.  I take it the remote provider supports POP3 but not IMAP?  

Right.

> The simplest configuration would be a server with dovecot, ordinary mbox mailboxes, and ordinary accounts for each user. Why mbox and not maildir?

> 
2)  Configuring the server's [hostname]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#myhostname") and [domain]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydomain").Actually each email address are something like [EMAIL="user@company.com"]user@company.com[/EMAIL] and users download emails using their own user and password on the pop3 external server (webmail.company.com).

I want that every email (also emails from one local user to another local use) are always sent via the external smtp server.

What is the domain I suppose to set in this situation?

> 
3) ** Developing a method to add/remove users from the server**.  If everything is run by you or a small number of competent admins, then you could use either the command-line adduser/passwd commands, or the graphical user account manager if you have a GUI desktop environment installed.  (By default, Ubuntu server has no GUI, though you can add one.)  Another option is to install Webmin and manage the server via a browser.Server mail will be an ubuntu server (textual) virtual machine on a proxmox cluster.

I need that another guy (not so much competent to do that in textual mode) can easily add/remove/modify users (maybe in some web interface).

Do you suggest to use webmin?
As far as I know webmin is not in the ubuntu official repository.
Is that gonna be a problem?

> 
4) ** Mapping from the external accounts to internal accounts**.  If the external server has a single POP box that has all your domain's mail, then you just tell fetchmail to download that account's mail and deliver messages addressed to "joecool@example.com" to the "joecool" account on the local server.  If each person has an individual remote account, then you'd need multiple fetchmail instances that poll each account.Like I said each user has his own pop3 access.

In this case I understand I need to use multiple fetchmail instance. 
How can I do that?
25 contemporary users may be a problem for the server (CPU E7600, 2TB HD SATA 7200 RPM dedicated to email storage)?

Moreover If a user change his password on the external webmail how can I make he able to do that also in the internal mail server?

> 5)  **Spam/virus filtering**.  If this is done by the remote provider, then you're all set.  If all you get is the raw unfiltered mail, you'll probably need to add local filtering.  If you need to do that, I can give you some suggestions.Spam and antivirus filters are not necessary (at least for now).

Thanks so much for helped me in this (maybe) not-so-usual configuration!

---

### Post by SeijiSensei on 2012-06-24
First I need an overview.

Your users now have individual user@domain mailboxes on a remote POP3 server.  Are you intending to maintain this arrangement after you build the new server?  Will your users now begin using the new server for incoming mail (and essentially ignoring their current POP3 mailboxes) while continuing to use your provider's SMTP server for outgoing mail?  I think that's a summary of what you said.

Going with that model for the moment, let's talk about each side of the mail service.

For ***incoming*** mail, you would need to run fetchmail periodically and have it poll each person's mailbox.  I haven't done that myself so I don't know if you can configure fetchmail to iterate like that.  If not, you could write a simple bash script to iterate over the list of users and run a fetchmail session for each mailbox.  You'd create a root-owned cron job to run the script every few minutes.  In terms of load, depending on the pace of email traffic, many of these fetchmail connections will consist of logging in and disconnecting after discovering no new mail.

However I'm going to suggest an entirely different approach, one that I think would be much easier for you to manage.  I suggest you replace the individual user mailboxes with a ***single mailbox that accepts all mail addressed to [email]user@domain.name[/email]***.  Fetchmail was designed from the beginning to poll a domain's collective mailbox, split up the messages by recipient, and deliver them to the corresponding local mailboxes.  

If your service provider requires each of your users to log in to send mail, that's another incentive for getting rid of your users' individual accounts.  Suppose you just have a single mailbox for domain.name that you log into as "[noparse]admin@domain.name[/noparse]" with POP3.  If you can also use that account to send outbound mail with SMTP, then you can configure postfix to ***relay outbound mail through the external provider*** by logging in as the admin account. Your local clients would then talk directly to the postfix server for SMTP.

Under this arrangement, you only need to maintain the one admin username and password on the external provider's machine.  ***Your local user accounts and passwords will be set up on the Linux server***.  You could use [Webmin](http://www.webmin.com/deb.html) for this.  (The link points to the Ubuntu instructions.)  Webmin also provides a graphical interface for other aspects of the mail service like aliasing.  However I really think using the command line for simple tasks like adding and deleting users is best done with a terminal.  Open a terminal, or use SSH, type "sudo adduser username", enter the password and other information when prompted and you're done.  

So the model here is a Linux server running IMAP with dovecot, SMTP with postfix, and using fetchmail to poll a single remote mailbox for domain.name.  This server maintains all the local user accounts and local storage.  

Fetchmail polls the remote mailbox every few minutes and downloads any new mail.  It hands these messages to postfix for delivery.  (I recommend installing [procmail]("http://packages.ubuntu.com/precise/procmail") as the final delivery agent, if it's not installed by one of the other packages.  It has a rather [arcane syntax]("http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=procmailex") but is also very powerful.)

Clients send outgoing mail by connecting to the Linux server with SMTP.  You can choose whether to require them to log in or not.  I usually just have the server bind to port 25 on 127.0.0.1 and the machine's LAN interface and let any client on the LAN send mail.  Postfix on the server will be configured to deliver mail for domain.name locally and relay all other mail to the external provider's SMTP server using the admin username and password.

***At the end of the day you're paying for one mailbox, not 25***.  Bosses like to hear things like that.  You've consolidated all the username and password management on the local machine and hidden the complexities of the mail system from the users.  You can use the same server name for inbound and outbound mail making configuration of your mail clients easier.  If you use Thunderbird and run a local DNS server on this box as well, you can point the local MX record for the domain to the Linux box.  If you then add a "[noparse]user@domain.name[/noparse]" account in Thunderbird, it will look at the local server and pretty much configure itself.

> **Debie said:**
> Why mbox and not maildir?

Convenience.  Configuring the server to use maildir takes more work.  By default everything will use mbox.  The one major advantage of maildir that I see is if you export the mailboxes with NFS, because maildir is more robust against file locking problems.  Other than that they're pretty equivalent in my eyes.  I've only ever used mbox.  I like the convenience of running commands like 
```
sudo grep ^Subject /var/spool/mail/joecool
```
but I could the same thing by grepping Maildir/joecool/*.

Who knows, maybe you'll decide to dump the external provider altogether and just run your own mail.  There's a lot to be said for subbing out the task of virus and spam filtering to somone else though.

---

### Post by kennethconn on 2012-06-24
Thanks for the info with my response.
 
> **SeijiSensei said:**
>  
However I'm going to suggest an entirely different approach, one that I think would be much easier for you to manage. I suggest you replace the individual user mailboxes with a ***single mailbox that accepts all mail addressed to [EMAIL="user@domain.name"]user@domain.name[/EMAIL]***. Fetchmail was designed from the beginning to poll a domain's collective mailbox, split up the messages by recipient, and deliver them to the corresponding local mailboxes. 

 
Just so it is clear in my mind, assume that the single mailbox is for [noparse]admin@mydomain.com[/noparse]. If someone outside the company sends an email to [noparse]user1@mydomain.com[/noparse] or [noparse]user2@mydomain.com[/noparse], it gets delivered because of the mydomain.com section. Fetchmail (on the LAN server) will then ensure delivery to the correct individual. Correct?
 
Always learn something from your replies, SeijiSensei, many thanks.

---

### Post by Debie on 2012-06-25
> **SeijiSensei said:**
> First I need an overview.

Your users now have individual user@domain mailboxes on a remote POP3 server.  Are you intending to maintain this arrangement after you build the new server?  Will your users now begin using the new server for incoming mail (and essentially ignoring their current POP3 mailboxes) while continuing to use your provider's SMTP server for outgoing mail?  I think that's a summary of what you said.

That's correct.

> 
For ***incoming*** mail, you would need to run fetchmail periodically and have it poll each person's mailbox.  I haven't done that myself so I don't know if you can configure fetchmail to iterate like that.  If not, you could write a simple bash script to iterate over the list of users and run a fetchmail session for each mailbox.  You'd create a root-owned cron job to run the script every few minutes.  In terms of load, depending on the pace of email traffic, many of these fetchmail connections will consist of logging in and disconnecting after discovering no new mail.

This is what I want to do.
The big problem is to study the right fetchmail implementation (a bash script or multiple fetchmail instance, etc...).

> However I'm going to suggest an entirely different approach[...]

The external mail server is on a proprietary software and we have no such admin account.
The idea is to avoid a change in the actual environment introducing simply an internal "proxy/backup mail server".
In case of problem we can always go back to the previous arrangement using the external mail server.

> You could use [Webmin]("http://www.webmin.com/deb.html") for this.  (The link points to the Ubuntu instructions.)  Webmin also provides a graphical interface for other aspects of the mail service like aliasing.  However I really think using the command line for simple tasks like adding and deleting users is best done with a terminal.  Open a terminal, or use SSH, type "sudo adduser username", enter the password and other information when prompted and you're done.  

I never use webmin for my server and I prefer command line too but I need webmin to let not-admin people to manage some configurations.

 > (I recommend installing [procmail]("http://packages.ubuntu.com/precise/procmail") as the final delivery agent, if it's not installed by one of the other packages.  It has a rather [arcane syntax]("http://www.gsp.com/cgi-bin/man.cgi?section=5&topic=procmailex") but is also very powerful.)

Are you saying I need fetchmail, postfix, dovecot and procmail too?

> ***At the end of the day you're paying for one mailbox, not 25***.It can sounds strange but we pay an annual fee to have the external mail server without distinction of the mail box numbers.

Anyway the second big problem is this:
If a user change his email password on the external webmail, how can he change also his password on the internal mail server?
Can I automate this process?
The only way is to setup an internal webmail?

> Who knows, maybe you'll decide to dump the external provider altogether and just run your own mail.  There's a lot to be said for subbing out the task of virus and spam filtering to somone else though.

Maybe this can be a future project and this implementation I'm trying to do is also a sort of test for the future.

Thanks as always.

---

### Post by SeijiSensei on 2012-06-25
I guess I didn't make myself clear.

I would have the external mail provider set up an account for you that collects *all* mail for domain.name.   This is a pretty common option at most mail/DNS providers.  So mail for [noparse]user1@domain.name, user2@domain.name, etc.[/noparse] will all be delivered to the common mailbox.  This is precisely the arrangement that fetchmail was designed to handle.

However it sounds like you don't really intend to have your users interact with the office server, but continue to use the external provider.  If all you want to do is back up the remote accounts, then you just run one fetchmail job overnight that polls the mailboxes.

However as long as the users can maintain individual mailboxes on the remote provider, you're going to have to cope with the password problem.  The single-mailbox solution avoids this since only you, the administrator, needs to manage the password for the single external account.  If you want to let the users keep their individual user accounts, you'll have to either rely on them to keep you up-to-date on changed passwords or establish a company policy that only you (or a delegate) can change their passwords, and all password requests must be made through you.

> Are you saying I need fetchmail, postfix, dovecot and procmail too?

Procmail is an option. If all you're doing is backing up the mail, it doesn't matter.  On a server where you're handling final delivery, it offers a lot of options to the administrator to set up automated folders, pipe messages to scripts, automate archiving, etc.

---

### Post by SeijiSensei on 2012-06-25
> **kennethconn said:**
> Just so it is clear in my mind, assume that the single mailbox is for [noparse]admin@mydomain.com[/noparse]. If someone outside the company sends an email to [noparse]user1@mydomain.com[/noparse] or [noparse]user2@mydomain.com[/noparse], it gets delivered because of the mydomain.com section. Fetchmail (on the LAN server) will then ensure delivery to the correct individual. Correct?

Yes, as I wrote above, most providers will set up an account where all mail for domain.name is delivered to the single mailbox.  

There can be some obscure situations where fetchmail has difficulties determining the actual recipient, particularly listserver mail.  Read the discussion about ["multi-drop" mailboxes]("http://www.fetchmail.info/fetchmail-man.html#43") on the fetchmail site for more details.

---

### Post by kennethconn on 2012-06-25
That new set-up could save me some money on extra mailboxes with the added benefit of a local backup solution.
 
The only problem I see with this is with mobile users when they are out of the office and want to send / receive email.

---

### Post by SeijiSensei on 2012-06-25
> **kennethconn said:**
> That new set-up could save me some money on extra mailboxes with the added benefit of a local backup solution.
 
The only problem I see with this is with mobile users when they are out of the office and want to send / receive email.

Well, there are costs and benefits to supporting mail in-house!  If you have people used to reading their mail on phones, you have some options:

1) Forward messages on your local server to external accounts they can see with a phone.  

You can write .forward files for these people that deliver a copy to the local server and forwards a second copy to the external account.  You no longer have any control over what happens to those messages, so company privacy is an issue.  You also cannot track replies, enforce correct [noparse]user@domain[/noparse] addressing, etc.  I'd consider this a last-resort.

2) Use port-forwarding to let remote users connect directly to the server from outside the office.

This is probably the best solution if your external connection to the Internet has a fixed IP address.  Use your router to forward ports 587 and 998 back to the mail server and let remote clients connect using the secure versions of SMTP and IMAP.  If you use a self-signed certificate, the phone's mail client should complain the first time, but you should be able to accept the certificate and not be bothered again.

3) Run a webmail client like Squirrelmail on a machine that is visible to the outside.

If you have a web server that can see the mail server,  you can install Squirrelmail on the web server and configure it to use the mail server's SMTP and IMAP servers.  Alternatively you could forward your external port 443 back to the mail server, install Apache, PHP, and SquirrelMail, and support your own webmail application with an SSL certificate.

---

### Post by kennethconn on 2012-06-25
The second option sounds like the best fit to me, all things considered. Getting a fixed IP or dynamic DNS purchase would still be better value than the cost of the extra mailboxes.

---

### Post by Debie on 2012-06-25
> **SeijiSensei said:**
> I guess I didn't make myself clear.

I would have the external mail provider set up an account for you that collects *all* mail for domain.name.   This is a pretty common option at most mail/DNS providers.  So mail for [noparse]user1@domain.name, user2@domain.name, etc.[/noparse] will all be delivered to the common mailbox.  This is precisely the arrangement that fetchmail was designed to handle.

Clear. I have to investigate if we can obatin a such account.

> 
However it sounds like you don't really intend to have your users interact with the office server, but continue to use the external provider.  If all you want to do is back up the remote accounts, then you just run one fetchmail job overnight that polls the mailboxes.
I express myself wrong.
The real backup server is the external one (it will have all emails stored on it).
Each lan user (no road warriors, no mobile user) will have the email client configured on the internal mail server.
The reasons of this implementation are:

- Users can use IMAP funcionality with the internal mail server
- In case of a PC failure I can restore a new fresh PC with all software and emails in much much less time.

Emails are a big issue in this company and they don't want to plan to switch to a better external mail server...
In the meantime the choose -me- to make things work. :twisted:

> 
However as long as the users can maintain individual mailboxes on the remote provider, you're going to have to cope with the password problem.  The single-mailbox solution avoids this since only you, the administrator, needs to manage the password for the single external account.  If you want to let the users keep their individual user accounts, you'll have to either rely on them to keep you up-to-date on changed passwords or establish a company policy that only you (or a delegate) can change their passwords, and all password requests must be made through you.

A company policy could be a general (and much simpler) good solution but I don't think this gonna be in my case.

I was thinking to implement an internal webmail (horde, squirrelmail,...) to handle with password changes.
If an user want to chage his password then he'll change it in the external and internal webmail.
How about this solution? Something better to suggest?

Thanks.

---

### Post by SeijiSensei on 2012-06-25
> **kennethconn said:**
> The second option sounds like the best fit to me, all things considered. Getting a fixed IP or dynamic DNS purchase would still be better value than the cost of the extra mailboxes.

Depending on how much it costs to get a static IP, I'd consider renting a [Linode]("http://www.linode.com/") instead.  You can get a virtual Linux server for $20/month with a static IP address. If you set up an OpenVPN tunnel between the Linode and the hypothetical office mail server, you can advertise ports on the Linode that forward back to the office server.  A remote user could connect to the IMAPS port on the Linode and be talking directly to the mail server in your office.

Let's talk for a second about the mail feed itself.  I've put the "multi-drop" POP3 mailbox on the table, but I think you should consider the other alternative, a service like [Postini]("http://www.google.com/postini/") that filters mail and delivers the filtered stream to your office's mail server.  In this model you don't fetch the mail from a POP or IMAP box.  You instead have the all the messages relayed to your central mail server with SMTP.  In the DNS, your MX records point to servers in the psmtp.com domain that belongs to Postini. (A typical record points to domain.name.stuff.psmtp.com.)  Postini filters your mail for spam and viruses and relays the filtered stream to a designated IP address.  This could be the address of your office router or a virtual server.  In either case you'd need to set up port forwarding to send the SMTP mail traffic from Postini to your local mail server.  With a little iptables know-how you can write rules to permit SMTP connections from Postini's relay servers and block everyone else.

Just thought I'd throw a few more complex alternatives out there to really give you something to chew on!

---

### Post by SeijiSensei on 2012-06-26
> **Debie said:**
> I was thinking to implement an internal webmail (horde, squirrelmail,...) to handle with password changes.
If an user want to chage his password then he'll change it in the external and internal webmail.
How about this solution? Something better to suggest?

If your users are okay with it, it's probably the easiest solution.

---

