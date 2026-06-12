---
title: "Passwords"
date: 2010-09-24
forum: Server Platforms
---

### Post by stevanbt on 2010-09-24
Hi,
We have a number of Unix and Linux servers.  What do people use to store root passwords?  We use word and excel documents, but there must be better options out there.

Thanks, Steve.

---

### Post by theozzlives on 2010-09-24
You're not supposed to use the root acct. You use sudo (Super User DO). Obviously you have Windows machines if you're using Office. You can SSH into your server by using winssh.

---

### Post by pricetech on 2010-09-24
> **stevanbt said:**
> Hi,
We have a number of Unix and Linux servers.  What do people use to store root passwords?  We use word and excel documents, but there must be better options out there.

Thanks, Steve.

<farce>
Sticky notes on all the monitors.
</farce>

Seriously, if you're recording passwords, put them under lock and key somewhere, and use sudo as suggested above.

---

### Post by BobVila on 2010-09-24
Print out or write down the root pw when it's changed in your cycle. Seal it in an envelope, keep one yourself, and give one to your boss.

---

### Post by CharlesA on 2010-09-24
You don't store passwords in text files. That's pretty close to leaving the passwords on a sticky note attached to the monitor.

I use keepassx to store passwords.

---

### Post by stevanbt on 2010-09-24
Thanks for the replies.  I guess I should expand a little on our setup.

The majority of our servers are AIX, there's going to be a growing number of linux machines.  There's four of us in the team.  Our desktops are all windows.  So ideally I'd be looking for something that runs on windows (needs to be GPL or free) and can be accessed by all of us at the same time.

It would be extra good if it would store additional metadata, e.g. OS version, ip address...

Thanks, Steve.

---

### Post by CharlesA on 2010-09-24
KeePassX can do that. It's got a section for comments. :)

---

### Post by stevanbt on 2010-09-24
Thanks, I've just installed keepassx.  Looks good, I'll give it a try at work.

Thanks, Steve.

---

