---
title: "Can postfix virtual mailboxes deliver to subfolders in UNIX account maildirs?"
date: 2008-11-16
forum: Server Platforms
---

### Post by randomstuff on 2008-11-16
Hi,

My server hosts two different domains (abc.com and xyz.com). I want all emails for abc.com do go to the user abc, and all emails for xyz.com to go to user xyz. This much I can do.

But now I want to increase the complexity a bit. I want each domain to have one main address (e.g. [email]main@abc.com[/email]), emails to these main addresses should go directly to the inbox of the respective users. In addition to the main address I want to have several secondary addresses (or even a catchall) which should be delivered to subfolders in the maildir (either subfolders of the inbox folder, or folders next to the inbox folder).

When I check mail from the abc.com domain, I want to have only a single (UNIX) account, wherein the following folders should exist:

[email]main@abc.com[/email]
- INBOX (contains emails only for [email]main@abc.com[/email])
- secondary (contain emails only for [email]secondary@abc.com[/email])
- catchall (contains mail for all other @abc.com address)
- Sent
- Trash
...

And the same should be the case for xyz.com

Can this be done using postfix virtual mailboxes? I am currently looking at the [postfix documentation on virtual mailboxes]("http://www.postfix.org/VIRTUAL_README.html"). I wonder if it is enough to do something like:

**[COLOR="Red"]EDIT: I have come to realize sorting into folders is better accomplished using dovecot as MDA, instead of making postfix (the MTA) do it. Handling the different domain names is still done by postfix though.[/COLOR]**

I added the following to /etc/postfix/master.cf, in the section for non-postfix commands:

```

dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=mail:mail argv=/usr/lib/dovecot/deliver -f ${sender} -d ${user}@${nexthop}

```

This lets postfix know that there is a dovecot command that can be used to deliver emails into their respective mailboxes.

I added the following to /etc/postfix/main.cf

```

1. virtual_alias_domains = abc.com, xyz.com
2. virtual_alias_maps = hash:/etc/postfix/virtual
3. mailbox_command = /usr/lib/dovecot/deliver
4. dovecot_destination_recipient_limit = 1
5. virtual_transport = dovecot

```

[LIST=1]
[*]Specifies the two "virtual domains" that postfix should map to different UNIX accounts. *[COLOR="Red"]Warning: [/COLOR]*Any domains listed here must not appear in the mydestination line. The mydestination line should only contain the actual hostname of the server running postfix as well as localhost.
[*]Specifies in which file the domain names are mapped to user accounts. 
[*]Specifies which command to use as MDA to deliver the emails.
[*]I'm not sure whether this is required
[*]Specifies that postfix should use the dovecot command from the master.cf file to deliver emails.
[/LIST]

For more information on postfix virtual mailboxes and domains, see the [postfix documentation]("http://www.postfix.org/VIRTUAL_README.html#virtual_alias").

In order for the domain sorting to work, the specified virtual_alias_maps file must be created. This is done by first creating the file ***/etc/postfix/virtual***:

```

@abc.com abc
@xyz.com xyz

```

These lines specify that all email that are sent to any address at abc.com should be delivered to the mailbox for the UNIX account abc, and all email for xyz.com should be delivered to the xyz account.This file must be then transformed into a Berkeley DB file by running the following command:

```
postmap /etc/postfix/virtual
```

This command creates the file ***/etc/postfix/virtual.db*** based on the contents of the ***/etc/postfix/virtual*** file. Everytime you make changes to the domain mapping you must run the above command again.

Finally we must configure dovecot to sort messages into different folders. First we must enable dovecot for use as MDA, this is done by uncommenting and changing the following in ***/etc/dovecot/dovecot.conf***

```

 protocol lda {
  # Address to use when sending rejection mails.
   postmaster_address = postmaster@hostname.com

  # Hostname to use in various parts of sent mails, eg. in Message-Id.
  # Default is the system's real hostname.
  hostname = hostname.com

  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  #mail_plugins = 
  #mail_plugin_dir = /usr/lib/dovecot/modules/lda

  # Binary to use for sending mails.
  sendmail_path = /usr/lib/sendmail

  # UNIX socket path to master authentication server to find users.
  auth_socket_path = /var/run/dovecot/auth-master


  # Enabling Sieve plugin for server-side mail filtering
   mail_plugins = cmusieve
 }

```

All instances of hostname.com should be replaced with the hostname of the server (which in my case is different from either abc.com and xyz.com). The last line enables the sieve plugin, which is used for the actual sorting. Sorting is done by creating a .dovecot.sieve file in the homedir of the user where sorting should be done:

```

1. require "fileinto";
2. if address :is "to" "main@abc.com" {
3.   keep;
4. } else 
5. {
6.   fileinto "catchall";
7. }

```

2+3 Specify that all email directed at "main@abc.com" should be kept in the actual inbox. 
4-7 Specify that all other emails should be sorted into the catchall folder.

For addition configuration options see the [dovecot wiki]("http://wiki.dovecot.org/LDA/Sieve").

---

