---
title: "Ubuntu mail server help, newbie"
date: 2012-02-20
forum: Server Platforms
---

### Post by nat45928 on 2012-02-20
Hi,

Im currently hosting 3 domain names (purchased though Godaddy) on my home server (Ubuntu of course :D). I have 4 domains in total (sjspecialties.com (hosted at godaddy), boone-duden.com, truefoodlooks.com, and on-ice.us) and all 4 domains have ultiple emails hosted with godaddy right now. I would like to move all of the email accounts to my home server so i followed [this]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10-p4") tutorial knowing that i have to have virtual users and domains so that i can add new emails without adding new users to the system.

Now ive followed the tutorial using sjspecialties.com as my FQDN (might be the problem) i wasnt sure what to use for this as i only have one server on my network (we have a static external IP) and i can contact the IMAP and SMTP servers fine, but when i try to log in to SquirrelMail i get the error "**ERROR: Connection dropped by IMAP server." **What is happening? How can i go about setting up the DNS records at go daddy to allow mail to be redirected to my home IP instead of godaddys servers?

Thanks, and sorry if this is confusing, im new so take it easy on me.

Nat

---

### Post by nat45928 on 2012-02-20
I found this: [http://flurdy.com/docs/postfix/#ec2_ami](http://flurdy.com/docs/postfix/#ec2_ami) which seems to be a much better tutorial and will start fresh with this tomorrow, wish me luck!

---

### Post by acc61287 on 2012-02-21
> **nat45928 said:**
> Hi,

Im currently hosting 3 domain names (purchased though Godaddy) on my home server (Ubuntu of course :D). I have 4 domains in total (sjspecialties.com (hosted at godaddy), boone-duden.com, truefoodlooks.com, and on-ice.us) and all 4 domains have ultiple emails hosted with godaddy right now. I would like to move all of the email accounts to my home server so i followed [this]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10-p4") tutorial knowing that i have to have virtual users and domains so that i can add new emails without adding new users to the system.

Now ive followed the tutorial using sjspecialties.com as my FQDN (might be the problem) i wasnt sure what to use for this as i only have one server on my network (we have a static external IP) and i can contact the IMAP and SMTP servers fine, but when i try to log in to SquirrelMail i get the error "**ERROR: Connection dropped by IMAP server." **What is happening? How can i go about setting up the DNS records at go daddy to allow mail to be redirected to my home IP instead of godaddys servers?

Thanks, and sorry if this is confusing, im new so take it easy on me.

Nat

Post your /var/log/mail.log mail.err mail.info
-

---

### Post by nat45928 on 2012-02-21
Im starting fresh again from the Flurdy tutorial. So im going to stat with this. Because i have multiple domains and a static external ip, what should i use as my FQDN? should i use my IP and let my router switch the connection to my server based on a port forwarding setup?

Thanks

---

### Post by lisati on 2012-02-21
As an aside, there are several tutorials available for Postfix available at [http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by nat45928 on 2012-02-22
OK, so ive completed the basic mail server and everything seems to be working right, im trying to login via outlook to make sure it can recive mail form the mail server. What should my login be? ive made a user [email]teset@truefoodlooks.com[/email] with a password, what should i use as my login for outlook, these two things?

---

### Post by nat45928 on 2012-02-22
Ok, ive got the mail server to send and recieve mail i tried to download mail in outlook and failed. this is the detail in the mail.log:

Feb 22 18:12:43 SJ-Linux-1 imapd: Connection, ip=[::ffff:127.0.0.1]
Feb 22 18:12:43 SJ-Linux-1 imapd: LOGIN FAILED, user=test@truefoodlooks.com, ip=[::ffff:127.0.0.1]
Feb 22 18:12:48 SJ-Linux-1 imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=38, sent=323

The mySQL logs dont show anything of interest, what could be wrong?

---

