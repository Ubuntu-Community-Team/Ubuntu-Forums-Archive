---
title: "postfix troubleshooting or alternate MTA?"
date: 2006-11-16
forum: Server Platforms
---

### Post by Zaehlas on 2006-11-16
I've used the very detailed and easy to follow documentation to try and set up my mail server located at [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

Anyway, I need an SMTP mail system, POP3, with virtual domains, virtual users, and a setup that is relatively easy to configure.  After following all the instructions, I only run into one major problem. Email is getting "swallowed" by postfix, and is NOT being sent to the virtual directories like it should be.

I've used WireShark to track the communications as they come in, and from what I can see, it acknowledges the incoming email (I used another email account to send test messages), and looks like it recieves it, however nothing ever shows up in the directories.

Is there any way to troubleshoot the interaction between the various postfix daemons?  Once it acknowledges it at the TCP level, I can't see anything that it does, and I have no idea where to find error messages, bad emails, how to configure replies, etc.

Please help!

"Z"

---

### Post by Zaehlas on 2006-11-16
My apologies.  I am a linux newbie, trying to do advanced stuff.  I found the log files, and the postfix help pages, and found that I had major permissions problems (which are not addressed in that HowTo).

Anyway, I got my server up.  =D

---

