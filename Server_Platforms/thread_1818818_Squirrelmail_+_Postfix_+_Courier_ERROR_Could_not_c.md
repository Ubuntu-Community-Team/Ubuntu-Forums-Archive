---
title: "Squirrelmail + Postfix + Courier ERROR: Could not complete the reques"
date: 2011-08-05
forum: Server Platforms
---

### Post by johnvliebal on 2011-08-05
Hello all,

I am fairly new to Linux, and this is my first go at setting up a mail server. I followed the following tutorial [http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html) and have only done the very beginning (no authentication or security measures in place at this point. I am able to send mail from my gmail account to the email accounts in the /var/spool/mail/virtual/{username} folder, as well as able to send mail out to the gmail account from an internal root account using the mail command. Since I can do this, I am assuming that all of the postfix settings are correct. Here is my issue

I have configured Courier and am attempting to retrieve the email from squirrelmail. When logging into squirrelmail I would get two error messages. The top says ERROR: Could not complete request. Query: SELECT "INBOX" Reason Given: Unable to open this mailbox. On the left hand side there was an error message that I did fix, but now I have a Folders frame with INBOX under it only, and it is not a link. I have never used squirrelmail so I am not 100% sure what all I should be seeing.

Has anyone run into this issue before, or know something else I can try. I have double check the permissions of all the folders, and have sent test mail to all accounts. Like I said, I am almost certain my issue is with Courier or Squirrelmail and not Postfix as I can send and receive email via CLI. My mail.log file says that the authentication process is fine, and then I get the following two messages back to back.
imapd: LOGIN=[email] [password] ip[]
imapd: LOGOUT=[email][password]ip[]
 If anyone needs more info please let me know. Thanks

---

