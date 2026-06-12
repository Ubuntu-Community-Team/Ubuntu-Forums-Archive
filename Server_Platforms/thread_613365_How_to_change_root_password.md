---
title: "How to: change root password?"
date: 2007-11-14
forum: Server Platforms
---

### Post by johnswb on 2007-11-14
OK, I give up... I've looked on the forum for users that had problems with the root account.  I can not do anything.  I just install Ubuntu server 7.10 and now when I do "sudo vi anything" I get the following.
"
john is not in the sudoers file. This incident will be reported.
john@userver:/$ sendmail: fatal: open /etc/postfix/main.cf: No such file ro directory"

if I do "sudo passwd root" I get the same error.

I really do not want to reinstall if I don't have too.  My guess is I will run in to the same problem.

---

### Post by Vitamin-Carrot on 2007-11-14
cant you add test user account to the root usergroup?

---

### Post by johnswb on 2007-11-14
I have an account called john that I created in the beginning and I still get the same thing.

---

### Post by aysiu on 2007-11-14
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by johnswb on 2007-11-14
Thank you for replying, but I was still unable to logon as root or use sudo.  I went ahead and reinstalled and this time I didn't install the mail server.  All is good now.  Again, thank you for replying to a noob.

---

### Post by MrSully on 2007-11-23
Thanks for posting back here John.... I had the same issue and also did a reinstall without the mail server.

Regards,
Sully

---

### Post by vinicius.vbf on 2007-11-23
What if you try:

# su -

?

---

### Post by techno-wiz on 2007-11-23
I had the same problem due to installing the mail server. Reinstalled without it and everything was fine.

---

### Post by trayor on 2007-11-23
Yep, I had the same problem and also re-installed without mailserver.  Works OK.

---

### Post by thegnuguru on 2007-11-23
try booting into recovery mode and then 

adduser yourusernamehere admin

I sometimes get the same thing that always works

---

