---
title: "Security e-mails at root login"
date: 2010-09-08
forum: Security
---

### Post by John Franklin on 2010-09-08
Whenever I login as root, an e-mail with the subject "Security information" is sent out.

Can someone please tell me where the e-mail address for this message is configured? I need to change it (or perhaps disable it).

---

### Post by CharlesA on 2010-09-08
What version of Ubuntu are you using?

Have you tried just typing ***mail*** from the prompt?

---

### Post by John Franklin on 2010-09-08
If I do that from the command prompt, I just get a list of mail packages that could be installed. I just want to configure the system's use of mail messages.

I'm using Ubuntu 10.04.

---

### Post by CharlesA on 2010-09-08
I've not had that occur when I drop to a root shell. I do get a mail message if I am running something from cron.

Is it a clean install of 10.04?

---

### Post by John Franklin on 2010-09-08
It's not a clean install but one that has been gradually upgraded. I seem to recall sometime in the distant past setting an e-mail address somewhere, but I've long forgotten where.

If you get a message using cron, it may use the same configuration setting for its address. Do you know where that is?

---

### Post by CharlesA on 2010-09-08
It sends it to the localhost, since root@thor isn't a valid email address. I'm using Exim4, so that's probably why it's showing up like that for me.

Is it sending an email about which packages need updating or just whenever you login as root?

---

### Post by spjackson on 2010-09-08
I would have a look at /root/.profile /root/.bash_profile /root/.forward /root/.bashrc (Some of these might not exist.) If there's nothing in there that sends the mail, then possibly look for cron jobs or a permanently running process that looks like it might be detecting a root login.

---

### Post by BkkBonanza on 2010-09-08
Mail is often sent by crons started in the /etc/cron.daily directory.

If you type the mail command and see you have heaps of mails you never looked at then that's likely where they came from.

Each cron script can have a MAILTO="" env variable set to disable this or set the address.
Also in crontab you can do the same.

Your post reminded me to check my mail again after so long. I had 3871 msgs...

---

### Post by CharlesA on 2010-09-08
Does the "mail" command work if you don't have any mail server software installed?

From what the OP said, it just returned a bunch of names of packages (so it wasn't installed).

---

### Post by BkkBonanza on 2010-09-08
Ah, forgot he said that. I think it's installed by default though as I certainly never chose to install it and it works here. About once a year I check it. 

My real mail is all done with Thunderbird.

Isn't there some pam option to notify about root logins?

---

