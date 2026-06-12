---
title: "questionable auth log entries"
date: 2010-03-29
forum: Security
---

### Post by andrewthomas on 2010-03-29
I got some entries in my auth log that I am puzzled by.  What could be the cause?  I was not using my machine at the time of the logging.  Any ideas?
```
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:20 ASUSm3a32MVP su[10582]: pam_unix(su:session): session closed for user andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:20 ASUSm3a32MVP su[10597]: pam_unix(su:session): session closed for user andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:20 ASUSm3a32MVP su[10618]: pam_unix(su:session): session closed for user andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10639]: Successful su for andrew by root
Mar 27 16:43:20 ASUSm3a32MVP su[10639]: + ??? root:andrew
Mar 27 16:43:20 ASUSm3a32MVP su[10639]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:43:21 ASUSm3a32MVP su[10639]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10942]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10957]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10978]: pam_unix(su:session): session closed for user andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: Successful su for andrew by root
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: + ??? root:andrew
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: pam_unix(su:session): session opened for user andrew by (uid=0)
Mar 27 16:57:33 ASUSm3a32MVP su[10999]: pam_unix(su:session): session closed for user andrew
Mar 27 17:00:10 ASUSm3a32MVP gdm-session-worker[1347]: pam_unix(gdm:session): session closed for user andrew
```

---

### Post by EJeanmaire on 2010-03-29
I am no expert but that certainly does look shady.  Type 'finger' and 'w' and see what sessions are logged in currently.  Also type netstat -an | grep "LISTEN" and see if you are listening on any ports that seem unusual.  You could also install Wireshark and monitor all of the traffic coming in and out of the machine.

---

### Post by andrewthomas on 2010-03-29
What I don't understand is:  the root account password should be locked, therefore the su command should not be able to be used, correct?
Why is it in my log?

---

### Post by cdenley on 2010-03-29
> **andrewthomas said:**
> What I don't understand is:  the root account password should be locked, therefore the su command should not be able to be used, correct?
Why is it in my log?

The su command cannot be used to switch to the root user unless you set a root password. The root user can switch to any user without entering a password, which is what those logs indicate happened.

---

### Post by andrewthomas on 2010-03-29
> **cdenley said:**
>  The root user can switch to any user without entering a password, which is what those logs indicate happened.
I certainly didn't to it.  So would you say that my machine has been compromised?

---

### Post by cdenley on 2010-03-29
> **andrewthomas said:**
> I certainly didn't to it.  So would you say that my machine has been compromised?

I don't know. I know there is a cron task that sudo's from root to your admin user, but that doesn't appear to be cron. I don't recally seeing that before. Do you have any unusual software installed that might run as root? Were you doing anything at those particular times? What version of ubuntu are you using?

---

### Post by andrewthomas on 2010-03-29
> **cdenley said:**
> I don't know. I know there is a cron task that sudo's from root to your admin user, but that doesn't appear to be cron. I don't recally seeing that before. Do you have any unusual software installed that might run as root? Were you doing anything at those particular times? What version of ubuntu are you using?
No unusual software.  I was not at the machine at that time.  I am using lucid.

---

### Post by cdenley on 2010-03-29
> **andrewthomas said:**
> No unusual software.  I was not at the machine at that time.  I am using lucid.

If you're beta testing software, then I can't help you. I think there is another section for beta testers. For all I know, some cron task in lucid may be doing that, and that may be normal.

---

### Post by andrewthomas on 2010-03-29
I didn't think that it could have anything to do with lucid, so I didn't post the question to the lucid forum.  I have been running it a while now and I have never seen the message before.  Thanks for your help.

---

