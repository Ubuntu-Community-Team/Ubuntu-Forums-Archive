---
title: "Postfix/Dovecot change users mail location"
date: 2011-01-28
forum: Server Platforms
---

### Post by MightyMe on 2011-01-28
I have set up  Postfix and Dovecot according to the 10.04 sever guide with SSL and everything in my own example domain for testing purposes. I have tried with Thunderbird clients and it works well to send and receive.

I would like to have all user mailboxes in one place instead of a 'Maildir/' in each user account. I have created a folder in /srv/mail/ and changed the permissions so everyone can read and write initially to avoid permission errors.

I have mail_location in changed dovecot.conf to /srv/mail/%u/Maildir. 

Mail clients can create their mailboxes here but when sending mail it not delivered to the right place.

Can anyone help me with /etc/postfix/main.cf settings in order to get this to work?

Current setting of home_mailbox is: home_maibox = Maildir/ (which I understand is a relative path in the users home directory)

Any help would be much appreciated.

---

### Post by druhboruch on 2011-01-28
Have a look at this:
[http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/](http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/)

---

### Post by MightyMe on 2011-01-29
Thanks.  Tried with virtual_mailbox_base but it didnt work.

---

