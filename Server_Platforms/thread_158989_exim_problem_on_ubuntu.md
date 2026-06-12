---
title: "exim problem on ubuntu"
date: 2006-04-12
forum: Server Platforms
---

### Post by alamba on 2006-04-12
Hi All,

Just hit into this really odd request from a friend who I migrated to exim on ubuntu. He run's a small business and would like all mails flowing into and out of his domain to be automatically copied to him. I've spent over a week on google and come up with ziltch so far. Any pointers would be appreciated. Since this is installed on a virtual domain hosting machine, I couldn't find any .forward files to manipulate. 

Maybe there's a way to do it in the .conf file itself.

Akshay

---

### Post by fenix03 on 2006-04-12
Maybe this gets you started:

[http://www.devco.net/archives/2006/03/24/saving_copies_of_all_email_using_exim.php](http://www.devco.net/archives/2006/03/24/saving_copies_of_all_email_using_exim.php)

---

### Post by alamba on 2006-04-13
Hey fenix, thanks for the link. I did see that before too, however, given my limited knowledge of coding, I wasn't able to decipher how to change deliverying the mails to a file to deliverying the mails to a email ID...could you help me out with that?

A

---

### Post by fenix03 on 2006-04-13
I just read it briefly and basically what you need to do is to change the path where the mail is to be saved to your maildir folder instead.

My maildir is located in ~/Maildir so I would change the configuration where it says '/var/mail/domain.com/mailarchive/' to '/home/fenix03/Maildir/domain.com/'

You probably need to create a maildir for every domain.com mail that you want to copy. In my case I would need to do 'maildirmake.dovecot ~/Maildir/domain.com'.

---

### Post by alamba on 2006-04-19
Do you think procmail would do a better job of this?

A

---

### Post by alamba on 2006-04-27
Hi again,

I've spent some time trying to get this fixed and have made some progress. I have the system_filters in place now and the transport in exim.conf. I can see from the logs that the mail is being copied and delivered, however, the delivery itself is a bit of a problem.

My system_filter says:
if <from domain> unseen save /home/admin/mail/domainname/allmails/

where allmails is a seperate email account on that particular domain. 

Exim instead of appending the mail to this file, is creating a directory called "new" in /home/admin/mail/domainname/ and putting each mail in there are a seperate OS file. I can cat the file and see the mail.

How can I deliver this to a valid maildir or email ID?

Appreciate the pointers, it looks like I'm almost through.

A

---

### Post by alamba on 2006-06-18
Fixed. Was using the wrong directive. Should be file rather than directory.

A

---

