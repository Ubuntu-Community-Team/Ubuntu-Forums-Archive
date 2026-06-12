---
title: "[SOLVED] Problem Redirecting Mail with Postfix and Viritual Alias Domains"
date: 2008-03-14
forum: Server Platforms
---

### Post by MattUK on 2008-03-14
Hey All,

I've set up postfix to use Virtual Mailboxes, so my maps file looks as follows:
```

[email]user@domain.com[/email] domain.com/mail/user/
[email]info@domain2.com[/email] domain2.com/mail/info

```

In accordance with this:
[http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html) (scroll to this title: Postfix virtual MAILBOX example: separate domains, non-UNIX accounts)

That works perfectly, however I've just tried to add a mail redirect in the maps file like this:

```

[email]user@domain2.com[/email] [email]someaddress@gmail.com[/email]

```

That's amongst the above entries. I ran postmap and tried to send an email, and I found this in the log:

```

Mar 14 11:35:32 servername postfix/virtual[24464]: A57F86C081: to=<someone@domain.com>, relay=virtual, delay=2170, delays=2170/0.01/0/0.1, dsn=4.2.0, status=deferred (delivery failed to mailbox /var/vhosts/someaddress@gmail.com: unable to create lock file /var/vhosts/someaddress@gmail.com.lock: Permission denied)

```

So the obvious problem is that its trying to create a local Maildir for the remote domain, when it should be redirecting to the remote server..

The /var/vhosts/ bit is the virtual_mailbox_base setting from main.cf.

Any ideas why this might happen? As I've said, everything else is working fine.

Any Help Appreciated,
Matt

---

### Post by MattUK on 2008-03-14
Update: While googl'ing I've come across Transports a few times, but it seems unlikely that id have to define a smtp server for every remote address I want to redirect to? or is that what I have to do?

Matt.

---

### Post by MattUK on 2008-03-14
OK I changed the permissions for a sec on the directory, wondering if the file its trying to create is a temporary one.

Just sent another test message, and the file (/var/vhosts/someaddress@gmail.com) is the mail itself.

I also thought id sussed it, and created a seperate aliases file, from my virtual maps file - but that doesn't seem to work either.

It just delivers the mail to the local account and doesn't appear to forward it as the alias file is telling it to.

---

### Post by MattUK on 2008-03-14
Right, somebody hand me the noob cap :p

How I fixed it:

- First I thought the virtual mailbox maps was the file I was supposed to enter redirects in, but that was virtual alias maps!

- Then I created the alias maps, but failed to realise the settings on the main.cf for that are virtual_alias_maps and virtual_alias_domains, where as I had edited alias_maps and alias_domains to point to my files.

Having done that, it all works now :)

---

