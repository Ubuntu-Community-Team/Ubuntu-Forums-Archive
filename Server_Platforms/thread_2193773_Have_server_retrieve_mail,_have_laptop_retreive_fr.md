---
title: "Have server retrieve mail, have laptop retreive from server?"
date: 2013-12-14
forum: Server Platforms
---

### Post by pstrick2 on 2013-12-14
I am trying to get my email to function in a very specific way.

Currently, I use an email provider that only allows a few(25) megabytes of space. Because I have such little space in the online account, I use Evolution mail to fetch all the mail from account and delete it from the remote server. So, the only copy of the email is on my laptop.

This is not ideal. It is currently stored on my personal laptop with just one harddrive. I really need to have a backup of my email.

Here's some basic information:
I have a 1U rack server that I use for web/file/etc server. It has unlimited bandwidth.
I use my school's smtp server. **I do not need to send email from the server.**
I am on 10.04, but I will upgrade if necessary.

-----------------
Here is what I want:
I want the server to retreive the email from the mail server.
Then, I want the laptop to retreive the mail from the server in the same way.
-----------------

How would I do this?
I honestly can't find any good information.
Thanks

---

### Post by volkswagner on 2013-12-15
I believe with your current request, sent mail will not be backed up.  Is this your intention?

---

### Post by SeijiSensei on 2013-12-15
You can use [fetchmail](https://library.linode.com/email/fetchmail) to retrieve the messages from your provider and store them on your server.  If you run [dovecot]("https://help.ubuntu.com/community/Dovecot") on the server you can access your mail with IMAP or POP3.

---

### Post by pstrick2 on 2013-12-15
Thanks to both of you.
I hadn't considered not having copies of sent mail. I'll have to figure out a work-around. 

I'll give fetchmail a try and report back here if something goes wrong.

---

### Post by volkswagner on 2013-12-15
If backups are your only/main concern. Backing up your entire /home/username folder or /home/username/.evolution to external drive or cloud service will accomplish your goal.

---

