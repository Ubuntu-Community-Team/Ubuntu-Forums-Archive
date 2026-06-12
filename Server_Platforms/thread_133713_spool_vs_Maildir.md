---
title: "spool vs Maildir/"
date: 2006-02-20
forum: Server Platforms
---

### Post by My-dial-up on 2006-02-20
Can someone PLEASE help! 

OS: Ubuntu 5.10 in terminal mode.

My server has been working fine for about a week using the Maildir/ format, now all of a sudden it's switched over to /var/spool/mail format. Why? How do I reset it to how I want it?


Thanks.

---

### Post by Glut on 2006-02-21
What mail service are you using?

---

### Post by My-dial-up on 2006-02-21
Postfix + Courier-imap + squirrelmail + procmail

I though the line in main.cf sorted this out;

home_mailbox = Maildir/


but it seems as though it's ignored.

---

### Post by My-dial-up on 2006-02-21
Sorted it by dpkg-reconfigure courier-imap + procmail.


Next question;

When SpamAssassin installs it sets up in procmail;

# All mail tagged as spam (eg. with a score higher than the set threshold)
# is moved to "probably-spam".
:0:
* ^X-Spam-Status: Yes
probably-spam


Is the 'probably-spam' folder created automatically when I receive spam mail, or have I got to create it for EVERY user?

---

### Post by My-dial-up on 2006-02-21
No one?

---

### Post by uopjohnson on 2006-02-21
It is automatically created when it is needed, however if you are using Maildir you will want to put a trailing forward-slash on the name...
"probably-spam/" that is how you tell procmail that you are using maildir.

---

### Post by My-dial-up on 2006-02-22
Many many thanks, that one piece of information about the / makes the whole system work!!!

---

### Post by LordHunter317 on 2006-02-22
And, since you're using procmail for delivery, you have to have it default to delivering to maildirs.  POstfix will only do maildir delivery if procmail totally fails, which is hard to cause.

Add:```
DEFAULT=${HOME}/Maildir/
ORGMAIL=${HOME}/Maildir/
DROPPRIVS=yes
``` to /etc/procmailrc

---

### Post by caraboy on 2006-02-23
I encountered a similar problem this week, postfix was set up to deliver mail in maildir format, but it seems it did not comply to this, after sending a mail to my server it would bounce back with an error message, that I don`t have permission to deliver that mail. After hours of testing, reconfiguring, after setting the home directory permission to 777 it worked. Why so? Sendmail delivers mail under the users permision, isn`t there a way to automatically set the right permission to a users home directory, because after I added a new user to the system, I had to set up the permissions for that user too.

---

### Post by LordHunter317 on 2006-02-23
[QUOTE=caraboy] After hours of testing, reconfiguring, after setting the home directory permission to 777 it worked. [/quote]You don't have to do this.  You had another configuration problem.

---

### Post by caraboy on 2006-02-25
[QUOTE=LordHunter317]You don't have to do this.  You had another configuration problem.[/QUOTE]

I can see that, but I can`t figure it out.... Still searching...

---

