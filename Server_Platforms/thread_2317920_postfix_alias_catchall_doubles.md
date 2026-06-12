---
title: "postfix alias catchall doubles"
date: 2016-03-21
forum: Server Platforms
---

### Post by lukas34 on 2016-03-21
Hi
I'm trying to forward all my mails sent to *@mydomain to catchall@mydomain BUT leave a copy on *@mydomain as well.
I tried aliases like
```
insert into aliases (source, destination) values ('a@mydomain', 'a@domain,catchall@mydomain');
```
which leads into two mails in catchall@domain even though google tells me that postfix aliases aren't recursive and therefore doubling would make no sense.
Are there any other (easy :) ) ways to achieve that kind of "backup-catchall"?
Cheers, lukas

---

### Post by SeijiSensei on 2016-03-21
If the server contains the mailboxes for mydomain, you can craft a simple solution after installing the **procmail** package.  Create a file called /etc/procmailrc with this "recipe:"
```

:0
* ^TO:.*mydomain
{
    :0c
    /var/mail/catchall
}

```
Now any message delivered to someone@mydomain will create a copy that is stored in /var/mail/catchall, the inbox for the "catchall" account.  Alternatively, you can forward all the messages to another account with the syntax:
```

    :0c 
    ! someone@example.com

```

Procmail is the "Swiss army knife" of mail utilities and should be in the arsenal of anyone running a mail server.

---

### Post by lukas34 on 2016-03-21
doesnt work for my. must be a stupid thing that I'm doing wrong. Restarted postfix creating the file. Do I need so reload/restart other services/the server?
Just to be sure. I used:

> :0c
* ^TO:.*marketstrategy.de
{
    :0c
    /var/vmail/marketstrategy.de/catchall
}

The second one doesnt work as well.

---

### Post by SeijiSensei on 2016-03-21
If you needed to install the procmail package, then you should first restart Postfix.  Also make sure that /etc/procmail/main.cf now has the line:
```
mailbox_command = procmail -a "$EXTENSION"
```
I don't know whether just installing the procmail package also modifies main.cf.  (I use CentOS on servers which, like all RedHat-flavored distros, includes procmail by default.)

Also I incorrectly included "c" at the top of the recipe; it should only appear in the sub-recipe that is invoked by messages that match the domain in the To field.

You can get a more extensive log of procmail's actions by adding the lines:
```

VERBOSE=on
LOGFILE=/path/to/some/log

```
at the top of /etc/procmailrc.  Since /etc/procmailrc is read by root, you can put the log in /var/log if you like.

I've never used a database or virtual users with Postfix so I'm not sure where the mail gets delivered in that setup.  I'd suggest using the "! catchall" syntax to forward a message to the catchall account.  So here's a corrected recipe for /etc/procmailrc:
```

VERBOSE=on
LOGFILE=/var/log/procmail

:0
* ^TO:.*marketstrategy.de
{
:0c
! catchall
}

```

If you run 
```
echo test | mail -s test catchall
```
does a message appear in the mailbox for that user?  If so, then "! catchall" should work, too.

---

### Post by lukas34 on 2016-03-22
no logfile in /var/log/procmail is created.
simply nothing happens. 
maybe it isn't that simple to put up procmail when using virtualal users...
anyway isnt there a way to get a copy of every mail sent to an catchall account using simple aliases?

I used recipient_bcc_maps and sender_bcc_maps now instead. Works just fine.
Still strange, that procmail istn working at all...

---

