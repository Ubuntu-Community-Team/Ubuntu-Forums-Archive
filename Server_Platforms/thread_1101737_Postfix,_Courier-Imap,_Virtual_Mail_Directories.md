---
title: "Postfix, Courier-Imap, Virtual Mail Directories"
date: 2009-03-20
forum: Server Platforms
---

### Post by mihamil on 2009-03-20
I am having trouble setting up postfix with courier-imap and virtual mailboxes.  I followed the instructions at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/).  All went well.  I am able to connect to the server via imap.  I can send email, and the logs show email is being received, however postfix doesn't seem to be creating the mailboxes in /var/spool/mail/virtual/.  If I try to connect with outlook express it says "Unable to retrieve unread message count from 'Inbox'.  It also doesn't work from any other mail clients.  There is nothing in /var/spool/mail/virtual.  Any ideas I can try.  If you need any output from commands or config files let me know and I will post them.  Thanks in advance.

---

### Post by volkswagner on 2009-03-20
Hi,

I used the same how to.  I have yet to complete the advanced portion for spam, etc.  There are so many config files where typos can occur.  Did you perform the test where you are asked to tail the mail logs?  Did that go as expected?

So you don't even have the users in  /var/spool/mail/virtual ?

```
ls -alt  /var/spool/mail/virtual/
```

You should at least have  /var/spool/mail/virtual/5000

If you look in the above file, you should see the activity during the test session.

```
sudo cat  /var/spool/mail/virtual/5000
```

Have you checked all relevant logs?

```
cat /var/log/mail.info

```

```
cat /var/log/mail.err
```

```
cat /var/log/mail.log
```

```
cat /var/log/mail.warn
```

---

### Post by HermanAB on 2009-03-21
Building a mail system from all the little Lego pieces is a great way to learn, but it can be very frustrating.  

Note that when you send mail, the client talks to Postfix on port 25 and when the client receives mail, it talks to Courier on port 143.

If a mail client won't connect, check whether the Courier and Postfix servers are running:
# ps -e|grep cour
# ps -e|grep master

Try to connect with telnet and see whether Courier and Postfix give a banner:
# telnet localhost 143
# telnet localhost 25

If it doesn't, restart Courier and/or Postfix.

Hope that helps!

Herman

---

### Post by mihamil on 2009-03-21
I think I have that part figured out now.  I have been trying to send email to [email]root@mydomain.com[/email] however found that for security root doesn't receive email directly.  I set up another user in mysql and it still didn't work because the user was greylisted in postgrey.  I whitelisted and that starting working.  However just from rebooting my server for some reason courier won't start again.

Before rebooting.

ps -e | grep cour
 5012 ?        00:00:00 courierlogger
 5036 ?        00:00:00 courierlogger
 5037 ?        00:00:00 couriertcpd
 5059 ?        00:00:00 courierlogger
 5060 ?        00:00:00 couriertcpd

After rebooting.

ps -e | grep cour
5023 ?        00:00:00 courierlogger

any ideas?

Thanks to both of you for your help

---

### Post by mihamil on 2009-03-21
I think I got it.  Everything seems to be working now. I screwed up the /etc/courier/imapd file.  I managed to get it fixed and Outlook now connects and downloads email.  Thanks for all your help...

---

