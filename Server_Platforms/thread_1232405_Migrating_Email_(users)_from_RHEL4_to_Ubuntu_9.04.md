---
title: "Migrating Email (users) from RHEL4 to Ubuntu 9.04"
date: 2009-08-05
forum: Server Platforms
---

### Post by AboveTheLogic on 2009-08-05
Here is the scenario...

I have a pretty powerful machine running RedHat Enterprise 4 that acts as a company email server for about 10 active users. This is not a supported version so I'm very limited and do not want to fight with it any longer.

I would like to replace it with Ubuntu server, but I want to make it as seamless to the end users as possible.

My plan is to setup a temporary ubuntu server on a spare machine which will handle emails while I am doing a fresh install of ubuntu server on the nice powerful machine.

I'm sure I can just migrate the users home directories over and they will have their email (most users just use POP so its irrelevant but a few use IMAP), but what about their passwords, can I migrate the  /etc/passwd file over along with their home directories, run the email services and have it work?

If anyone has any ideas or any input at all it will be GREATLY appreciated, thanks!

---

### Post by giggins on 2009-08-05
Well, I'm not familiar enough with RHEL4's mail server functionality to definitively answer your question, but I'm assuming it utilizes either mbox or Maildir formatted mail stores. Depending on what you're migrating to, you may need to [convert the mailboxes]("http://wiki.dovecot.org/Migration/MailFormat").

I would suggest using [dovecot]("https://help.ubuntu.com/9.04/serverguide/C/dovecot-server.html") for the MDA and [postfix]("https://help.ubuntu.com/9.04/serverguide/C/postfix.html") for the MTA. They are both well documented and Ubuntu makes it very easy to get up and running with them both. Both Postfix and Dovecot are capable of supporting virtual users, but by default they just work with local system users (/etc/passwd). This means that copying /etc/passwd entries for users, then their home directories should just work, assuming mail is stored in the home directories using Maildir format.

When you decide what you're going with, let us know. You can get more help with issues as they arise.

---

### Post by AboveTheLogic on 2009-08-05
Dovecot and postfix were what I planned to use. I hope to implement that with procmail and spamassassin, and somehow give the end users access to the filtered email that spamassassin grabs (I'm hoping that squirrelmail will somehow allow this)

It looks like the RHEL4 setup we have now is using Maildir.

---

### Post by giggins on 2009-08-05
Well, it will skew quota usage, but I've used .procmailrc files to move messages marked as spam into a spam folder. Here's a [blog article]("http://standbytux.blogspot.com/2005/07/using-spamassassin-and-procmail-to.html") that helps explain it. That way, users can get to their spam, but don't have to see it. I wrote a script that would kill spam messages in the spam directories of users if its older than X days, but I can't seem to find it. If I find it, I'll post it.

---

### Post by AboveTheLogic on 2009-08-05
thanks I'll check into that, I'm not too concerned about quota usage

Can you or anyone comment on the migrating of the users credentials from one linux machine to another?

I'm still confident that if I simply move the home directories and create users of the same name with the new server that it will work fine, but I would have to send all my users new passwords and I want to avoid that if at all possible.

---

### Post by giggins on 2009-08-05
User (and group) info is stored in four files, '/etc/passwd', '/etc/shadow', '/etc/group', and '/etc/gshadow'. I would not suggest simply overwriting the files on Ubuntu with those from RHEL, as there are likely differences in uid and gid numbers that will break a lot of things. Instead, I suggest you copy the lines you need from those files into the files on the new server. You should be able to identify the lines used by users you created.

After copying the user info, then you should be able to safely copy the home directories. Try using something that will maintain file permissions during the copy process, it'll save you a lot of headaches.

---

### Post by nix4me on 2009-08-05
The UID and GID are going to be different for sure.  One OS starts at 500, the other starts at 1000 for user accounts.  I am not familiar though with migrating user passwords, so im sorry to say i don't know.

---

### Post by AboveTheLogic on 2009-08-05
Thanks for the help guys. I guess the whole issue I was concerned with is copying the hashed password from /etc/passwd from one system to another and still having the user be able to authenticate. I can easily test this anyways. Creating the users and groups is easy enough for me to do manually, its not a complicated setup with that regard.

---

