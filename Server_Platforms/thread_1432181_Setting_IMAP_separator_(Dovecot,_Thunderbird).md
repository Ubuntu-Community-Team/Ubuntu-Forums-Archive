---
title: "Setting IMAP separator (Dovecot, Thunderbird)"
date: 2010-03-17
forum: Server Platforms
---

### Post by Solomoriah on 2010-03-17
I have several customers with Ubuntu servers, more or less stock, running Dovecot for IMAP mail support.  Dovecot uses the "." as a path separator; I can't seem to find any way to set Thunderbird (the preferred client for these educational customers) to use a specific path separator.  Perhaps I'm just stupid, but my Google-fu has failed me here.

Not sure if I need to change Dovecot settings, or somehow access a hidden Thunderbird setting.  Any help would be appreciated.  (Sorry if I've chosen the wrong section for this, not sure if it's a server or a client issue.)

---

### Post by KB1JWQ on 2010-03-17
It's a server issue.

Please paste the output of dovecot -n

---

### Post by Solomoriah on 2010-03-17
Certainly:

# 1.1.11: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.28-18-generic i686 Ubuntu 9.04 
log_timestamp: %Y-%m-%d %H:%M:%S 
protocols: imap imaps pop3 pop3s
disable_plaintext_auth: no
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
mail_privileged_group: mail
mail_executable(default): /usr/lib/dovecot/imap
mail_executable(imap): /usr/lib/dovecot/imap
mail_executable(pop3): /usr/lib/dovecot/pop3
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
auth default:
  passdb:
    driver: pam
  userdb:
    driver: passwd

---

### Post by KB1JWQ on 2010-03-17
Edit your dovecot.conf to resemble this:

> namespace private {
  separator = .
  prefix = INBOX.
  inbox = yes
}

---

### Post by Solomoriah on 2010-03-18
Okay, I tried it on my own network, and when I made that change, suddenly all my folders became subfolders of the Inbox.  I can't do that to my users... they'll FREAK, and that means a lot more work for me.

Can't I have it both ways?  That is, all the folders we already have at the top level, stay there, but we can create subfolders under them?

---

### Post by KB1JWQ on 2010-03-18
Have you taken a look at [http://wiki.dovecot.org/#Migration_from_existing_systems](http://wiki.dovecot.org/#Migration_from_existing_systems) yet?

---

### Post by Solomoriah on 2010-03-19
Yeah, I did.  I just don't understand it.

There doesn't seem to be a page that relates the settings you're talking about to the way the list is presented in an MUA like Thunderbird.  Possibly I'm missing something; probably, I should spend some time making myself familiar with IMAP.

---

### Post by KB1JWQ on 2010-03-19
Most likely.  Drop the INBOX prefix in your dovecot config, see if that helps.

---

