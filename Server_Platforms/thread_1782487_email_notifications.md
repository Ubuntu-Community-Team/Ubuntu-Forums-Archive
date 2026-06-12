---
title: "email notifications"
date: 2011-06-14
forum: Server Platforms
---

### Post by sdmike6 on 2011-06-14
I'm running a server with Ubuntu Natty x64 and I want to get email notifications from the server sent to my gmail. What is the best way to set this up?

I was looking at this [LINK]("http://www.timashley.me/node/370") but I wasn't sure if this was the best way to go about this.

---

### Post by BkkBonanza on 2011-06-14
That page descibes doing it with postifx mail server and relaying thru that. It seems to me like a lot of work just to send an email. I'm pretty sure you can find a simpler approach.

I have a PHP script for sending email via a smtp server and I've used it with SSL to gmail for years now. It's actually quite easy but I haven't looked at re-writing it in shell script so it depends on PHP being present. I'm sure there must be some similar shell script around that can just send via smtp. That would be ideal and should work.

Edit - a bit more googling turns up **nail** as a possible quick solution for you. It allows sending a msg thru an smtp server. [See here]("http://www.linuxquestions.org/questions/linux-server-73/syntax-using-nail-mailx-for-smtp-without-postfix-or-sendmail-560929/") or [here]("http://ubuntuforums.org/showthread.php?p=4531994").

Update - In Ubuntu nail is now provided by [heirloom-mailx]("http://manpages.ubuntu.com/manpages/lucid/en/man1/nail.1.html") pkg. Maybe [this tutorial]("http://klenwell.com/is/UbuntuCommandLineGmail") will help.

Or I see in the repos there is a perl script to send emails called **sendemail** which may be easy to install and use (says it's designed to be use in bash scripts easily).

---

### Post by rubylaser on 2011-06-14
I just would use sSMTP for this.  It's very simple to setup and light on system resources.
[http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/]("http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/")

---

### Post by BkkBonanza on 2011-06-14
Reading up on **ssmtp** it sounds like it would work fine for a single user but maybe isn't well designed if you need to have multiple users.

I read a bit more on **msmtp** and as far as I can see you can use it fine standalone just like ssmtp. So even though I haven't tried it you probably don't need to have mailx or sendmail present to just send msgs from a cron or shell script. But having it present allows for more traditional mail handling to work by having mailx pass it onto msmtp. Apparently msmtp allows for per user conf files so it works if you have multiple users.

---

