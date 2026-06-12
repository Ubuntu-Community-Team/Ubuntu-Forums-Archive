---
title: "home email server - how to ??"
date: 2007-02-02
forum: Server Platforms
---

### Post by neill on 2007-02-02
hi

i want to setup a simple home email server (on dapper) to do the following:

1 - periodically download mail (POP3) from a handful email accounts (all of the form [email]account@me.myISP.com[/email])
2 - sort the mail into a series of mbox/mdir (which ?) folders on the server
3 - serve these up to the LAN clients (T'bird and evolution mainly) as IMAP accounts so the mail remains on the server and can be accessed from any PC on the LAN with a suitably configured client

i don't need spam and antiviral filtering (as it's on the gateway - endian firewall) and i don't need to access the server from the wider internet - only the LAN

outgoing mail can go directly from the LAN clients, it doesn't need to go through the mail server - unless of course there's a good reason to do it like that

of course this all needs to be done without exposing myself as a spam relay !!

my reading so far leads me to think that i need fetchmail to do the POP3 bit + dovecot (or similar) to do the IMAP serving

is that correct ? anything else - procmail or postfix ??

if anyone can give me an overall strategy/approach, then i can start working on the details. what i don't want to do is put a lot of effort into something that is fundamentally flawed from the outset

i've looked on the forums and google and there are a lot of howtos but thay are tend to be too detailed/complex for my needs

can anyone help ??

thanks

neill

---

### Post by elst on 2007-02-03
I think you've got the right idea.

Configure your email clients to use a good quality email service for their primary account, and then configure a second account that uses the same SMTP as the primary, but collects mail from the IMAP server that fetchmail is feeding.

MailDir is a better approach than mbox for storing very large quantities of mail, but not all tools support it. mbox files work OK though, so there's nothing wrong with using them and then switching to MailDir later if you need to.

These days I would discourage people from either running their own SMTP services, or relying on the POP/IMAP accounts provided by whatever ISP they currently use. Doing mail handling yourself isn't really cost- or time-effective at all, as the cost of accounts with SMTP, IMAP, POP retrieval etc. is so low,  but if your main account is maintained by FastMail, RunBox or some other reputable provider then you can play around a bit without worrying too much.

---

### Post by neill on 2007-02-03
so do you think fetchmail and dovecot are enough ?

---

### Post by chrisfay on 2007-02-03
You still need an MTA such as Postfix or Exim to handle the delivery of mail locally.

EDIT: Although after re-reading your post, it doesnt look like you'd have any.

---

### Post by elst on 2007-02-03
If you keep using the SMTP server you are currently using for sending mail, then yes.

---

### Post by neill on 2007-02-03
OK cheers that gives me a basis to work from and i'll see how i get on

;-)

---

