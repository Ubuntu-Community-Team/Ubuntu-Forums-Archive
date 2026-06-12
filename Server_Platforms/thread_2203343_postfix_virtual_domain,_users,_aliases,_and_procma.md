---
title: "postfix virtual domain, users, aliases, and procmail"
date: 2014-02-02
forum: Server Platforms
---

### Post by Troy_Piggins on 2014-02-02
Hi there.  I have had a virtual postfix/dovecot/procmail server set up for some time, and for the most part everything is working fine.  The only quirk that I can’t figure out is some virtual aliases seem to fall through to the virtual domain’s catchall mailbox rather than getting delivered to the intended virtual user.  Not sure if it’s my postfix or procmail settings.
 
I've included below what I think is the relevant parts of the relevant config files. If you need more, let me know.
 
What's happening is that mail getting sent to [EMAIL="troy@example2.com.au"]troy@example2.com.au[/EMAIL] gets correctly delivered to /var/mail/vhosts/example2.com.au/troy
But mail sent to one of the aliases like [EMAIL="info@example2.com.au"]info@example2.com.au[/EMAIL] does not go to /var/mail/vhosts/example2.com.au/troy but rather /var/mail/vhosts
 
What am I missing?
 
### /etc/postfix/main.cf extract ####
mailbox_command = /usr/bin/procmail -a "${EXTENSION}"
home_mailbox = Maildir/
mydestination = dove.example1.local, dove, dove.example1.com, localhost.localdomain, localhost, example1.dyndns.org mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/22 inet_interfaces = all alias_maps = hash:/etc/aliases alias_database = hash:/etc/aliases transport_maps = hash:/etc/postfix/transport relay_domains = $mydestination
 
virtual_mailbox_domains = example1.com example2.com.au virtual_mailbox_base = /var/mail/vhosts virtual_mailbox_maps = hash:/etc/postfix/vmailbox virtual_minimum_uid = 100 virtual_uid_maps = static:5000 virtual_gid_maps = static:5000 virtual_alias_maps = hash:/etc/postfix/virtual
 
virtual_transport = procmail
procmail_destination_recipient_limit = 1 transport_maps = hash:/etc/postfix/transport ########################
 
### /etc/postfix/vmailbox extract ####
[EMAIL="troy@example2.com.au"]troy@example2.com.au[/EMAIL]    example2.com.au/troy/
[EMAIL="info@example2.com.au"]info@example2.com.au[/EMAIL]    example2.com.au/troy/
[EMAIL="accounts@example2.com.au"]accounts@example2.com.au[/EMAIL]        example2.com.au/troy/
[EMAIL="linkedin@example2.com.au"]linkedin@example2.com.au[/EMAIL]        example2.com.au/troy/
[EMAIL="facebook@example2.com.au"]facebook@example2.com.au[/EMAIL]        example2.com.au/troy/
[EMAIL="office@example2.com.au"]office@example2.com.au[/EMAIL]  example2.com.au/troy/
[EMAIL="sysadmin@example2.com.au"]sysadmin@example2.com.au[/EMAIL]        example2.com.au/troy/
[EMAIL="webmaster@example2.com.au"]webmaster@example2.com.au[/EMAIL]       example2.com.au/troy/
 
[EMAIL="dc@example2.com.au"]dc@example2.com.au[/EMAIL]              example2.com.au/jeevan/
[EMAIL="jeevan@example2.com.au"]jeevan@example2.com.au[/EMAIL]  example2.com.au/jeevan/ ########################
 
### /etc/postfix/transport extract ####
example1.com procmail
example2.com.au procmail
########################
 
### /etc/postfix/master.cf extract ####
procmail  unix  -       n       n       -       -       pipe
  flags=DROhu user=vmail argv=/usr/bin/procmail -t -m USER=${user}
  EXTENSION=${extension} NEXTHOP=${nexthop} /etc/postfix/procmailrc.common ########################
 
### /etc/postfix/procmailrc.common extract #### MAILDIR=${HOME}/${NEXTHOP}/${USER}
DEFAULT=${MAILDIR}/
########################

---

