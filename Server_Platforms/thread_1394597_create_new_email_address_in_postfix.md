---
title: "create new email address in postfix"
date: 2010-01-30
forum: Server Platforms
---

### Post by dd1313 on 2010-01-30
Hi Guys

Working on ubuntu server for 1st time and need to create a 
new email address.The server has postfix

Please help,not sure how to go about creating the address

Dev

---

### Post by artheus on 2010-01-31
You'll be able to create a new user through the useradd command. Write "man useradd" to know how to use it.

By default procmail will deliver the mail to the file /var/mail/*username*      (*username* will be replaced by the name of the user. So it'll be one file for each user.)

To read the mail through a mail client, you'll have to set up an IMAP or POP3 server. I recommend Dovecot for that.

```
sudo apt-get install dovecot
```

Good luck!

Cheers,
Artheus

---

### Post by dd1313 on 2010-02-01
> **artheus said:**
> You'll be able to create a new user through the useradd command. Write "man useradd" to know how to use it.

By default procmail will deliver the mail to the file /var/mail/*username*      (*username* will be replaced by the name of the user. So it'll be one file for each user.)

To read the mail through a mail client, you'll have to set up an IMAP or POP3 server. I recommend Dovecot for that.

```
sudo apt-get install dovecot
```

Good luck!

Cheers,
Artheus

thank you
 How does one check if dovecot is installed
Thanks
Dev

---

### Post by artheus on 2010-02-01
write the command

```
sudo apt-get install dovecot
```

if it's installed you will see that.

OR

You can browse to the /etc directory and se if there's a dovecot folder inside there. If it is, open it and check if it's empty or not.


GOOD TIP!
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

Cheers,
Artheus

---

### Post by dd1313 on 2010-02-01
thank you

---

