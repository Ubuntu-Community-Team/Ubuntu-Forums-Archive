---
title: "postfix in local mode, forward all messages"
date: 2009-03-27
forum: Server Platforms
---

### Post by chrismo on 2009-03-27
ehlo

i have installed the packages postfix + courier for my local developing environment. this works great if recipient address is myuser@mycomputer. but my software (php) sends mails to lots of other destinations. is there a way to tell postfix to accept *every* email from localhost, no matter what domain, and forward it to my maildir?


i have searched several hours, but found no working solution :)

---

### Post by wkulecz on 2009-03-27
If you don't mind haveing all your outgoing mail appear to come from your gmail acount, you can do what I did here:

[http://ubuntuforums.org/showthread.php?t=1097249](http://ubuntuforums.org/showthread.php?t=1097249)

Google postfix mail relay, lots of good turorials out there.  Any machine or user on my local subnet can send Email via my gmail account using my local Ubuntu 6.06 box as the smtp host.  Only thing is it all comes from my gmail account, so if you need replies, you are out of luck if your Reply-To setting in outgoing mail doesn't work.

--wally.

---

### Post by chrismo on 2009-04-01
hm, very creative, and it works ;)

but is there realy no other way? something like a "act as mailtrap"-switch anywhere?

---

### Post by HermanAB on 2009-04-01
If you just need mail forwarding, then nullmailer is much easier to set up than a whole Postfix system.

---

