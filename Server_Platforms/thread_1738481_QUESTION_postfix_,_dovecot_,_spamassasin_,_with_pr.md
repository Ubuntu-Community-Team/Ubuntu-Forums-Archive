---
title: "QUESTION: postfix , dovecot , spamassasin , with procmail,"
date: 2011-04-24
forum: Server Platforms
---

### Post by pehden on 2011-04-24
QUESTION: postfix , dovecot , spamassasin , with procmail, I had this all set up and I had an issue with something else so i had removed postfix , well before my email would come into folder /home/pehden/mail     now it keeps going to /var/mail/pehden what do i need to do to fix this back so i can use my webmail lite to check it 

webmail lite is the latest version. when i change what i think i need to for the folder i get account info incorrect.

---

### Post by elico on 2011-04-26
one of both..
or to create a symlink using 
ln -s ...
or to change the maildir location in the postfix main.cf file

---

