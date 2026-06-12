---
title: "Senmail Config"
date: 2009-11-28
forum: Server Platforms
---

### Post by carthmen on 2009-11-28
Hello,

  I am having a issue with sendmail.  I have a working LAMP server setup with a properly configured domain and dns of i'll say 'something.com'  It is properly connected to the internet, and has not firewall setup as of yet.  I used the sendmailconfig script as attached bellow.  When i do a simple mail someone@gmail.com the mail never arrives.  Any thoughts?  BTW im using sendmail not postfix because I far as i know senmail is the only one that works with php's mail().

Sendmail Configuration
----------------------
By answering the following questions, you can configure sendmail for your
system. Default values are determined either by your existing configuration
or from common usage.

Press [ENTER] 

Mail Name
---------
Your `mail name' is the hostname portion of the address to be shown on
outgoing news and mail messages (following the username and @ sign). This
name will be used by other programs besides sendmail; it should be the single,
full domain name (FQDN) from which mail will appear to originate.

Mail name? [something.com] something.com

Null Client
-----------
A special configuration known as the "null client" can be created for this
host if all mail should be forwarded to a central hub via a local SMTP-based
network. This may be a suitable configuration if you want to forward all of
your mail to your local Internet service provider (ISP) for delivery.

To enable this option, give the name of the host to which all mail should be
forwarded. Otherwise leave the option empty to disable it.
To remove a prior name, use `NONE'.

Null client forward host? [] NONE

Smart Host
----------
A "Smart Host" is one that can deliver mail to external machines.  By using
a "Smart Host", we don't need DNS, or good connectivity ourselves.    This is
most likely what you want if you have a dialup link, or sit behind a firewall.

To enable this option, give the name of the host to which all non-local mail
should be forwarded.  Otherwise leave the option empty.
To remove a prior name, use `NONE'.

Smart Host:? [] NONE

Address Canonification
----------------------
Usually sendmail will canonify all addresses by consulting a name server and
resolving hosts to their fully qualified domain name (FQDN). Under special
circumstances you may want to disable this feature, for example if this
machine acts only as a mail gateway.

Disable address canonification? [N] n

Masquerade Envelope
-------------------
If you want mail envelopes (as well as mail headers) to appear to come from
`something.com', you can enable this option.

Masquerade envelopes? [Y] y

All Masquerade
--------------
If enabled, this feature will cause recipient addresses to also appear to come
from `something.com'. Normally they get the local hostname.
Although this may be right for ordinary users, it can break local aliases. For
example, if you send to "localalias", the originating sendmail will find that
alias and send to all members, but send the message with
"To: localalias@something.com". Since that alias likely does
not exist, replies will fail. Use this feature ONLY if you can guarantee that
the ENTIRE namespace of `something.com' supersets all the
local entries. If in doubt, it is safe to leave this option disabled.

All masquerade? [Y] 

Dont masquerade mail to local users
-----------------------------------
Send mail to local recipients without masquerading.

Dont masquerade local? [N] 

Always Add Domain
-----------------
If enabled, the local host domain is included even on locally delivered mail.
Normally it is not added unless it is already present.

Always add domain? [Y] 

Mail Acceptance
---------------
Sendmail is usually configured to accept mail for your mail name
(something.com). However, under special circumstances you
may not wish sendmail to do this, particularly if (and disabling this option
generally requires that) mail for `something.com' is MXed
to another host. If in doubt, it is safe to leave this option enabled.

Accept mail for `something.com'? [Y] 

Alternate Names
---------------
In addition to the canonical mail name `something.com', you can
add any number of additional alternate names to recognize for receiving mail.
If other hosts are MXed to you for local mail, this is where you should list
them. This list is saved into the file /etc/mail/local-host-names
so it can be changed later as needed.

To answer this question, separate each alternate name with a space, or answer
`NONE' to eliminate all alternate names.

Alternate names? [localhost something.com] NONE

Trusted Users
-------------
Sendmail allows a special group of users to set their envelope "From" address
using the -f option without generating a warning message. If you have
software such as Majordomo installed, you will want to include the usernames
from such software here. Note that "root", "daemon", and "uucp" are included
automatically and do not need to be specified. This list is saved into the
file /etc/mail/trusted-users so it can be changed later as needed.

To answer this question, separate each username with a space, or answer
`NONE' to eliminate all usernames.

Trusted users? [] 

Redirect Feature
----------------
If enabled, this feature will allow you to alias old names to
<new-address>.REDIRECT, causing sendmail to return mail to the sender with
an error but indicating the recipient's new address.

Enable redirect option? [N] 

UUCP Addresses
--------------
Sendmail can be configured to be smart about UUCP addresses, or it can do
nothing special with UUCP addresses at all. If you care about UUCP, you will
need to do some additional configuration, perhaps outside of this script.

*** NOTE *** If you use a smart host or do any kind of forwarding (ie
LUSER_RELAY and LOCAL_RELAY), it is important that you say "Yes"
here to prevent a multi-level relay hole - unless you know for *SURE* that
your smart-host does not deal with UUCP addresses.

(Be safe and just say Y)

Enable UUCP addressing? [Y] 

Sticky Host
-----------
If enabled, mail sent to `user@something.com' is marked as
"sticky" -- that is, the local addresses aren't matched against UDB and don't
go through ruleset 5. This is used if you want a setup where `user' is not
necessarily the same as `user@something.com', e.g., to make
a distinct domain-wide namespace. If in doubt, it is safe to leave this
option disabled.

Enable sticky host option? [N] 

DNS
---
If you are directly connected to the Internet and have access to a domain
name server, you should enable this option.

Enable DNS? [Y] 

Best MX is Local
----------------
If enabled, this option will cause sendmail to accept mail as though locally
addressed for any host that lists this machine as the best possible MX record.
This generates additional DNS traffic, but should be OK for low-to-medium
traffic hosts. N.B.: This feature is fundamentally incompatible with wildcard
MX records. If you have a wildcard MX record that matches your domain, you
cannot use this feature.

Assume best MX is local? [N] 

Mailertable
-----------
If enabled, this option causes sendmail to read mail routing rules from
the text file /etc/mail/mailertable.  This is needed for unusual mailers like
ifmail and fax programs.
More information is in /usr/share/doc/sendmail-doc/op/op.txt.gz.

Enable the mailertable feature? [N] 

Sendmail Restricted Shell
-------------------------
If enabled, this option causes sendmail to use the sendmail restricted shell
program (smrsh) instead of /bin/sh for mailing to programs. This improves your
ability to control what gets run via email; only those programs which appear
in a special directory can be run. If you enable this option, please carefully
read the smrsh(8) man page for further information.

Use the Sendmail Restricted Shell (smrsh)? [Y] n

Message Timeouts
----------------
Sendmail will issue a warning message to the sender if it can't deliver a
message within a reasonable amount of time. It will also send a failure
notification and give up trying to deliver the message if it can't deliver it
after an unreasonable amount of time.

You can configure the message timeouts after which warning and failure
notifications are sent. Sendmail's defaults are 4 hours and 5 days (4h/5d),
respectively, but many people feel warnings after only 4 hours are premature.

Message timeouts? [4h/5d] 

Configuration Complete
----------------------

---

### Post by carthmen on 2009-11-28
hmm..hold that thought, I may have just run across something related. I will check back in a bit.

---

### Post by carthmen on 2009-11-28
well, that was to no avail.  Still any thoughts are welcome.

---

### Post by carthmen on 2009-11-28
I just changed a line in the sendmail.mc and reran sendmailconfig using the mc files. I can not connect to the machine on port 25 bust test emails still not going through.

---

### Post by carl.davis on 2009-11-28
> **carthmen said:**
> I just changed a line in the sendmail.mc and reran sendmailconfig using the mc files. I can not connect to the machine on port 25 bust test emails still not going through.

Install mutt on the sendmail server. From a terminal type:

```
echo "Test" | mail -s "Test from Terminal" someone@gmail.com
```

If it isn't delivered, run mutt on the sendmail server and see if the email bounced back. You can then read the server response as to why it isn't able to deliver.

---

### Post by carthmen on 2009-11-28
Thanks for the reply.

 Well im sure something is wrong now becuase mutt says a /home/name/Mail does not exist.  I did apt-get install sendmail-bin, and sendmailconfig, i figured that the mail should be there.

---

### Post by carthmen on 2009-11-28
Success!  I was supposed to do apt-get install sendmail. not apt-get install sendmail-bin. My bad I remembered wrong :(  Thanks!

---

### Post by voxtechsupport on 2010-07-07
I'm having issues with my sendmail sending mail to anyone but gmail.

I re-ran sendmailconfig and this is what I got:

voxmontr:/usr/sbin# sendmailconfig
Configure sendmail with the existing /etc/mail/sendmail.conf? [Y] y
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Configure sendmail with the existing /etc/mail/sendmail.mc? [Y] y
Updating sendmail environment ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Could not open /etc/mail/databases(No such file or directory), creating it.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...

Checking filesystem, this may take some time - it will not hang!
  ...   Done.
 
Checking for installed MDAs...
hostname: Name or service not known
hostname: Name or service not known
Checking {sendmail,submit}.mc and related databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Use of uninitialized value $smdb_class in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Use of uninitialized value $smdb_flags in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Use of uninitialized value $file in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Use of uninitialized value $smdb_options in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Use of uninitialized value $smdb_class in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Use of uninitialized value $smdb_flags in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Use of uninitialized value $file in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Use of uninitialized value $smdb_options in join or string at /usr/share/sendmail/Parse_mc.pm line 650.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Use of uninitialized value $class in exists at /usr/share/sendmail/update_mk line 141.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Disabling HOST statistics file(/var/lib/sendmail/host_status).
Creating /etc/mail/sendmail.cf...
Creating /etc/mail/submit.cf...
Informational: confCR_FILE file empty: /etc/mail/relay-domains
Informational: confCT_FILE file empty: /etc/mail/trusted-users
Updating /etc/mail/access...
Updating /etc/mail/aliases...
/etc/mail/aliases: 4 aliases, longest 10 bytes, 66 bytes total
Reload the running sendmail now with the new configuration? [Y] y
Reloading sendmail ...
Makefile:12: *** missing separator.  Stop.

Any ideas where I went wrong?

---

