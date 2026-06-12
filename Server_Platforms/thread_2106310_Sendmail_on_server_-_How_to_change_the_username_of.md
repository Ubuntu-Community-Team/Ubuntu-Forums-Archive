---
title: "Sendmail on server - How to change the username of mailer"
date: 2013-01-18
forum: Server Platforms
---

### Post by beagless on 2013-01-18
Hi Guys
i'm setting up sendmail with amazon aws and i have the mail sending ok but when i send the mail i want to change the local user name.
i.e when i send the mail it shows the right email address i choose using

FEATURE(masquerade_envelope)dnl
FEATURE(`genericstable')dnl
GENERICS_DOMAIN(`localhost.localdomain')dnl


but the name of the email is still ubuntu can i change the "name" shown on the mail for example to webmaster or admin.
Could  i have the configuration wrong  in generics tab or do i have to use virtuisertable ?

all help welcome thanks guys

Beag

---

### Post by dpurgert on 2013-01-18
so, what you're getting is the sender being "ubuntu@yourserver.com"?  or is the subject of the mail "Ubuntu"?

---

### Post by beagless on 2013-01-18
when i get the mail its just "from" ubuntu

in the genericstable file i have

ubuntu [email]verfiedaddress@domin.org[/email]
root     [email]verfiedaddress@domin.org[/email]

so i want all mails to come from the same address which they do but the "from" field says ubuntu 

i want to change the id or sender info i suppose the email address they come from works fine 

is it possible to configure an alias for ubuntu ? that is used as the sender name ?

---

### Post by CharlesA on 2013-01-18
I've looked into it and I gave up dealing with it as it seems you are unable to modify the headers with sendmail or something like that.

I've got logwatch reports mailed from root, and stuff run as my user mailed to me as my username.

I just leave it alone.

---

### Post by SeijiSensei on 2013-01-19
You need to understand the distinction between the From address used in the SMTP transaction, the "envelope sender," and the one used in the headers of the message itself.  Ordinary postal mail makes the same distinction.  The return address on an envelope need not match the address used by the sender on the letter inside.

Sendmail can rewrite the sender in the SMTP transaction with the remote server, but it cannot change the From field in the message header.  That is created by the application sending the message itself.  Quite often the SMTP sender bears no relationship to the From field in the message. 

Listservers are a good example.  The envelope sender is usually something like "owner-listname@example.com" while the distributed message includes the From address of the person who actually wrote the message.

The only way to control the From field within the message is to have the application sending the mail generate the correct From header along with To and Subject.

---

### Post by beagless on 2013-01-19
hi SeijiSensei
thanks for that, i was a bit unsure as to where i needed to look at. so its the header i need to change do you know of a way to rewrite the header when its sending ?

its mainly for alerts from tiger/aide and some other stuff so they would use root to send the mail out. is it possible to change the default sendmail command to include the choosen email address or would a rewrite rule be needed somewhere 

i know sendmail -f [EMAIL="email@doamin.com"]email@doamin.com[/EMAIL] from the command line will put the correct header, how do i get the system to auto sendmail -f 

again thanks for your insight :-)

---

### Post by CharlesA on 2013-01-19
You could change the symlink if you are using mail:

```
ls -l $(which mail)
lrwxrwxrwx 1 root root 22 Apr 28  2012 /usr/bin/mail -> /etc/alternatives/mail

```

I have mailutils installed instead of sendmail, which might make a difference.

---

### Post by beagless on 2013-01-19
would postfix or exim be any easier or be able to rewrite the header ?

---

### Post by CharlesA on 2013-01-19
They are just the mail server, they don't actually have a client to send mail.

---

### Post by SeijiSensei on 2013-01-19
> **beagless said:**
> its mainly for alerts from tiger/aide and some other stuff so they would use root to send the mail out.

What's wrong with mail from root?  Most admin notices I receive are sent by the root user as [email]root@host.domain.name[/email].

As I said, the MTA, be it sendmail, exim, or Postfix, won't change the entry in the message's From field.  Sendmail's -f parameter just sets the envelope sender.

---

### Post by beagless on 2013-01-23
Hi Folks for anyone interested there is an easy way to change the display name by 
editing /etc/passwd and putting a name in the GECOS field (field 5)

ubuntu:x:1000:1000:**display name you want**:/home/ubuntu:/bin/bash

worked fine for me, and nothing to do with sendmail, i have an email address in the GECOS so using this and sendmail genericstable all works and looks good using amazon ses 

thanks for all your help and suggestions folks ):P):P):P):P

---

### Post by CharlesA on 2013-01-23
That sounds like a nasty "hax" but if it works, if works.

---

### Post by SeijiSensei on 2013-01-23
It's not a hack.  It's where the user's full name is stored in the /etc/passwd record.  I never realized that the full name was used when mail is sent from the command line, but a quick test shows it does.  The message is sent from 

```
"John H. Smith" <jhsmith@host.domain.name>
```

This is using sendmail and the standard command-line "mail" program.  Perhaps the program itself grabs the full name and creates the complete address, or maybe sendmail does.  If the latter, then that should solve the OP's problem.

Learn something new every day!

---

### Post by CharlesA on 2013-01-23
I had hax in quotes cuz it isn't really a hack per say but it might have unintended side effects.

It is actually pretty nice that mail/sendmail can read that information. I didn't know it did that. Does that also change the name shown if you have a GUI installed?

---

### Post by SeijiSensei on 2013-01-23
> **CharlesA said:**
> I had hax in quotes cuz it isn't really a hack per say but it might have unintended side effects.

I've had full names in /etc/passwd records for as long as I've used Linux.  I cannot think of any "unintended side effects."

> It is actually pretty nice that mail/sendmail can read that information. I didn't know it did that. Does that also change the name shown if you have a GUI installed?

If you're asking about a mail client like Thunderbird, then no, it doesn't use /etc/passwd at all as far as I know.  You create the full name field for outbound messages when you configure the account in TBird.  TBird allows you to have multiple outbound identities that are selectable from the composition window.  That wouldn't be possible if it relied on /etc/passwd to compose the From.

I ran a test where I piped a message to sendmail itself.  It arrived with my full name, so the composition of the From field must be happening at the MTA level and not the client.

---

### Post by CharlesA on 2013-01-23
> **SeijiSensei said:**
> If you're asking about a mail client like Thunderbird, then no, it doesn't use /etc/passwd at all as far as I know.  You create the full name field for outbound messages when you configure the account in TBird.  TBird allows you to have multiple outbound identities that are selectable from the composition window.  That wouldn't be possible if it relied on /etc/passwd to compose the From.

I was thinking more along the line of it showing up as the login name in the GUI if you are running a GUI (which I am not).

> I ran a test where I piped a message to sendmail itself.  It arrived with my full name, so the composition of the From field must be happening at the MTA level and not the client.

Thanks for that. I've not tried storing extra information like that, but it sounds handy.

---

### Post by SeijiSensei on 2013-01-23
> **CharlesA said:**
> I was thinking more along the line of it showing up as the login name in the GUI if you are running a GUI (which I am not).

I don't know.  I use KDE which doesn't show my login name anywhere by default.

---

### Post by CharlesA on 2013-01-23
> **SeijiSensei said:**
> I don't know.  I use KDE which doesn't show my login name anywhere by default.

Gotcha. Thanks for the info. I don't usually use a GUI, so I wasn't sure. :lolflag:

---

