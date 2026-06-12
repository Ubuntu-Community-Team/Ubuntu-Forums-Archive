---
title: "how to set passwd file up for dovecot"
date: 2012-06-15
forum: Server Platforms
---

### Post by A2llex on 2012-06-15
# my dovecot 2.0.19, Ubuntu 12.04 LTS


hi, i need your advice, this is from my old dovecot (1x ver. passwd file)  config:

[EMAIL="myemail@domain.tld"]myemail@domain.tld[/EMAIL]:{plain}mypasswd:5000:5000:::


 i tried to use that old passwd file but looks like it doesn't work anymore,
in dovecot logs i see only that bad settings in /etc/dovecot/passwd.

so i tried an alternatives like:
[email]myemail@domain.tld[/email]:mypasswd:5000:5000::/var/mail/virtual/mydomain:/bin/false::
[email]myemail@domain.tld[/email]:{plain}mypasswd:5000:5000::/var/mail/virtual/mydomain 
none of those works.

and this is from dovecot.conf:

passdb {
 args = /etc/dovecot/passwd
 # args = scheme=plain username_format=%u /etc/dovecot/passwd // this was from old config, so i tried it too.
  driver = passwd-file
}

userdb {
  args = /etc/dovecot/passwd
  driver = passwd-file
}


thank you.

---

