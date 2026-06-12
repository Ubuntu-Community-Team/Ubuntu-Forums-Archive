---
title: "VHCS2 and DNS Management"
date: 2007-07-10
forum: Server Platforms
---

### Post by dmjedli on 2007-07-10
Hello everyone...

I'm stuck and could use a little help.  I've got a setup with VHCS2 installed and working properly.  I'm using a residential cable broadband connection.  I've got a firewall between my VHCS2 server and the Internet.  There is a script that updates my everydns.net zones with my dynamic IP.  So far everything works great, and has for some time.

Today, I modified my MX entries (at everydns.net) to use Google's hosted apps for domains. (Email, Calendar and other fun stuff.)

Does any one know how to convince the VHCS2 server that the mail for that domain is hosted on a different server?  Or at the least, where can I edit my zone entries on the VHCS2 bind server?

I've modified the zone files in /etc/vhcs2/bind/working and in /var/cache/bind.  Neither of those edits are working after restarting bind.  

This all stems from a formmail php script that should send mail using the MX records.  But instead the local postfix installation removes the message from the queue everytime....

Jul  9 23:25:46 ******* postfix/cleanup[4120]: D32B0FBA96: message-id=<20070710032546.D32B0FBA96@********>

Jul  9 23:25:47 ******* postfix/qmgr[3867]: D32B0FBA96: from=<www-data@********l>, size=767, nrcpt=1 (queue active)

Jul  9 23:25:47 ******* postfix/virtual[4122]: D32B0FBA96: to=<services@********.com>, relay=virtual, delay=1, status=bounced (unknown user: "services@**********.com")

Jul  9 23:25:47 ******* postfix/cleanup[4120]: 207FFFBA97: message-id=<20070710032547.207FFFBA97@*******>

Jul  9 23:25:47 ******* postfix/qmgr[3867]: 207FFFBA97: from=<>, size=2380, nrcpt=1 (queue active)

Jul  9 23:25:47 ******* postfix/qmgr[3867]: D32B0FBA96: removed

So what happens, postfix thinks that the domain mail is being hosted locally, but it should really be sending it using the correct MX records.

I'm at a loss and I've been at this for about 12 hours.  I admit that I'm not a postfix expert (at all) and it could be something VERY simple.  

Thanks in advance for any help!

---

### Post by Mr. C. on 2007-07-10
I know nothing about the VHCS2 setup, but we can start by looking at postfix's config.  Show the output from:

postconf -n

The postfix "virtual" relay is rejecting the mail because the user is an unknown virtual user.  This implies that you have your domain listed as a virtual domain.

MrC

---

### Post by dmjedli on 2007-07-10
> **Mr. C. said:**
> I know nothing about the VHCS2 setup, but we can start by looking at postfix's config.  Show the output from:

postconf -n

The postfix "virtual" relay is rejecting the mail because the user is an unknown virtual user.  This implies that you have your domain listed as a virtual domain.

MrC

Work is getting in the way of me getting the configuration!  I won't be able to get it until after 5pm Central.  Thanks for replying!

---

### Post by dmjedli on 2007-07-10
Here's the postconf -n output:

alias_database = hash:/etc/aliases
append_at_myorigin = yes
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
inet_interfaces = all
local_destination_recipient_limit = 1
local_recipient_maps = unix:passwd.byname $alias_database
local_transport = local
mail_spool_directory = /var/mail
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = $myhostname, $mydomain
mydomain = midweb2.local
myhostname = midweb2
mynetworks_style = host
myorigin = $mydomain
setgid_group = postdrop
smtpd_banner = $myhostname VHCS2 2.4 Spartacus Managed ESMTP 2.4.7.1
smtpd_recipient_restrictions = permit_sasl_authenticated,   permit_mynetworks,   reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = vhcs.net
smtpd_sasl_security_options = noanonymous
transport_maps = hash:/etc/postfix/vhcs2/transport
virtual_alias_maps = hash:/etc/postfix/vhcs2/aliases
virtual_gid_maps = static:8
virtual_mailbox_base = /var/mail/virtual
virtual_mailbox_domains = hash:/etc/postfix/vhcs2/domains
virtual_mailbox_limit = 0
virtual_mailbox_maps = hash:/etc/postfix/vhcs2/mailboxes
virtual_minimum_uid = 1001
virtual_transport = virtual
virtual_uid_maps = static:1001


From this, it looks like postfix gets the domains and  /etc/postfix/vhcs2/domains.

Sure enough, the domain is listed in that file.  I know that VHCS2 maintains this configuration.  So, if we get this working (essentially disabling mail for the domain on that server), I need to make sure that VHCS2 doesn't overwrite manual changes.... I'll have a poke around the database tonight to see what's acutally stored in there.

---

### Post by universal4 on 2007-10-23
I am very interested in the outcome of this.

Was a solution found?

Rick

---

### Post by Some_Bored_Dude on 2007-10-23
Generally I've found mailservers do not like dynamic IP's, and blocks them.

If you enter your IP into the spam database lookup on [http://member.dnsstuff.com/pages/tools.php](http://member.dnsstuff.com/pages/tools.php) you might find the ip blocked.

Last thing is dns delegation. some dns can take up to 48 hours to update. I have a vhcs2 setup and a static ip block. If I change something here, my isp doesnt recognize the update for a few hours, same later on.


I know its not really a solution, but its just my 2c. I havnt done much with dynamic ip's and mail servers. Good luck with it though.

---

### Post by dmjedli on 2008-04-11
I'm fairly sure that no one has been back to this thread, but I just plain forgot that I even asked on the forums about this....

> **Some_Bored_Dude said:**
> Generally I've found mailservers do not like dynamic IP's, and blocks them.

I know its not really a solution, but its just my 2c. I havnt done much with dynamic ip's and mail servers. Good luck with it though.

You're right... my dynamic IP was being blocked by most mail servers, that's why I was switching to google apps for domains... Since I do host a couple of live websites, I want to be able to offer email.  With google groups, smtp/pop3/imap/webmail is all handled with Google and not my dynamic ip based ispconfig install.  It's a win win!

> **universal4 said:**
> I am very interested in the outcome of this.

Was a solution found?

Rick

It turns out that for the domain, there are two places in ispconfig domain menus that you have to click check boxes to enable alternate mail servers.  I'll try to get the check boxes this weekend and post them here.  Once I checked those two boxes, it worked like a charm...

---

