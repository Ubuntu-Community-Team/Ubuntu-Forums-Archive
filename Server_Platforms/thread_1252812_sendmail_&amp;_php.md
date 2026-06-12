---
title: "sendmail &amp; php"
date: 2009-08-29
forum: Server Platforms
---

### Post by magpy on 2009-08-29
Hi all, Having some difficulty getting sendmail to work:

*I've used [COLOR="Red"]xxxxx.xxxxxxxx.@xxxxxx.com[/COLOR] to mask an actual email address.*

Below is the contents of /var/log/mail.log

Aug 29 15:23:55 ublx postfix/pickup[5203]: 40FC74E451D: uid=33 from=<www-data>
Aug 29 15:23:55 ublx postfix/cleanup[5376]: 40FC74E451D: message-id=<20090829142355.40FC74E451D@mail.example.com>
Aug 29 15:23:55 ublx postfix/qmgr[5204]: 40FC74E451D: from=<www-data@mail.example.com>, size=318, nrcpt=1 (queue active)
Aug 29 15:23:55 ublx postfix/smtp[5378]: 40FC74E451D: to=<[COLOR="Red"]xxxxx.xxxxxxxx@xxxxxx.com[/COLOR]>, relay=smtp.dsl.pipex.com[212.74.114.24]:25, delay=0.54, delays=0.26/0.0$
Aug 29 15:23:55 ublx postfix/cleanup[5376]: E4EB14E451E: message-id=<20090829142355.E4EB14E451E@mail.example.com>
Aug 29 15:23:56 ublx postfix/bounce[5379]: 40FC74E451D: sender non-delivery notification: E4EB14E451E
Aug 29 15:23:56 ublx postfix/qmgr[5204]: E4EB14E451E: from=<>, size=2274, nrcpt=1 (queue active)
Aug 29 15:23:56 ublx postfix/qmgr[5204]: 40FC74E451D: removed
Aug 29 15:23:56 ublx postfix/smtp[5378]: E4EB14E451E: to=<www-data@mail.example.com>, relay=smtp.dsl.pipex.com[212.74.114.24]:25, delay=0.62, delays=0.22/0/0$
Aug 29 15:23:56 ublx postfix/qmgr[5204]: E4EB14E451E: removed


Any suggestions much appreciated??:popcorn:

p.s. I have set my relayhost to my actual isp's smtp: smtp.dsl.pipex.com
     
And I've set the path for sendmail in php.ini to:
sendmail_path =/usr/sbin/sendmail -t -i

---

### Post by jay.parnaby on 2009-08-29
The entries in the mail.log are from postfix, not from sendmail.

Have you checked to see if you have received an email from the relay host

---

### Post by magpy on 2009-08-29
Hi Thanks for pointing that out!

How would I be able to check that?:)

---

### Post by jay.parnaby on 2009-08-29
It depends how postfix is configured.

If you have not changed the mailbox type then it will be using mbox, so the mail for all users is located in /var/mail/ - In this case look for a file for www-data.

---

### Post by magpy on 2009-08-29
Hi Thanks again

I've had a look at /var/mail for the www-data file, it was not there.  Any ideas where it may be?:confused:

---

### Post by jay.parnaby on 2009-08-29
Are there any files in the /var/mail directory.

What does this command return?

```
more /etc/postfix/main.cf | grep home_mailbox
```

---

### Post by magpy on 2009-08-29
Hey Thanks

The command, more /etc/postfix/main.cf | grep home_mailbox:

outputs this: home_mailbox = Maildir/

and there are no other files in /var/mail

:KS

---

### Post by jay.parnaby on 2009-08-30
Do you actually use this mail server?

If so then you could try setting up an alias so that any mail for www-data will be delivered to you mail account.

To do this run the following

```

sudo nano /etc/aliases

```

Add the following line to /etc/aliases

```

www-data:   your_username_here

```

Then you need to let postfix know that the alias list has been updated

```

sudo newaliases

```

Once that is done any email for www-data will be delivered to your mailbox

---

### Post by magpy on 2009-08-30
Hi Thanks for your time:

I'll just outline what I'm trying to achieve. I'd like my ubuntu box to be configured so that it can send and receive email for my account.

The most important thing I wanted to be able to do was have postfix take care of any mail sent its way when using the php
mail() function.

I'm using this hackneyed php script:

=================================================================
if (isset($_REQUEST['email']))
//if "email" is filled out, send email
  {
  //send email
  $email = $_REQUEST['email'] ;
  $subject = $_REQUEST['subject'] ;
  $message = $_REQUEST['message'] ;
  mail( "c.humphrey_00@hotmail.co.uk", "Subject: $subject",
  $message, "From: $email" );
  echo "Thank you for using our mail form";
  }
else
//if "email" is not filled out, display the form
  {
  echo "<form method='post' action='mail.php'>
  Email: <input name='email' type='text' /><br />
  Subject: <input name='subject' type='text' /><br />
  Message:<br />
  <textarea name='message' rows='15' cols='40'>
  </textarea><br />
  <input type='submit' />
  </form>";
  }
================================================================

Here is a recent output from the log file:

Aug 30 10:48:19 ublx postfix/pickup[5606]: 351054E4540: uid=33 from=<www-data>
Aug 30 10:48:19 ublx postfix/cleanup[5653]: 351054E4540: message-id=<20090830094819.351054E4540@mail.example.com>
Aug 30 10:48:19 ublx postfix/qmgr[5607]: 351054E4540: from=<www-data@ublx.com>, size=340, nrcpt=1 (queue active)
Aug 30 10:48:20 ublx postfix/smtp[5655]: 351054E4540: to=<c.humphrey_00@hotmail.co.uk>, relay=mx4.hotmail.com[65.55.37.104]:25, delay=1.2, delays=0.23/0/0.76$
Aug 30 10:48:20 ublx postfix/smtp[5655]: 351054E4540: lost connection with mx4.hotmail.com[65.55.37.104] while sending RCPT TO
Aug 30 10:48:20 ublx postfix/cleanup[5653]: 7B7B14E4541: message-id=<20090830094820.7B7B14E4541@mail.example.com>
Aug 30 10:48:20 ublx postfix/bounce[5656]: 351054E4540: sender non-delivery notification: 7B7B14E4541
Aug 30 10:48:20 ublx postfix/qmgr[5607]: 7B7B14E4541: from=<>, size=3181, nrcpt=1 (queue active)
Aug 30 10:48:20 ublx postfix/qmgr[5607]: 351054E4540: removed
Aug 30 10:48:20 ublx postfix/smtp[5655]: 7B7B14E4541: to=<www-data@ublx.com>, relay=none, delay=0.34, delays=0.25/0/0.08/0, dsn=5.4.6, status=bounced (mail f$
Aug 30 10:48:20 ublx postfix/qmgr[5607]: 7B7B14E4541: removed

It looks like the mail is getting stuck, I'm not sure how to overcome this, any ideas?

---

### Post by jay.parnaby on 2009-08-30
OK, if I look at the log file it shows the following

Line 1-3 - Postfix receives the message from www-data (Apache)
Line 4 - Postfix does a DNS lookup for hotmail and connects to mx4.hotmail.com
Line 5 - The connection to mx4.hotmail.com has been dropped, but does not say why
Line 6 - A new message is generated by postfix to inform of delivery failure
Line 10 - A delivery failure notification is sent to [email]www-data@ublx.com[/email], and that message may contain data on why the original email was bounced back.

---

### Post by magpy on 2009-08-30
Hi
Not sure why but I cannot find any files that contain info on the bounced message, nor can I get anything on the www-data user. I think I might have to RTM and see how I go.  Thanks for your help.

After taking a look at the last post it appears the file wass truncated, here is info on why the mail bounced:

Aug 30 12:32:48 ublx postfix/smtp[5197]: D59164E4541: to=<c.humphrey_00@hotmail.co.uk>, relay=mx3.hotmail.com[65.55.37.72]:25, delay=1.7, delays=0.23/0/1.3/0/1.3/0.18, dsn=5.0.0, status=bounced (host mx3.hotmail.com[65.55.37.72] said: 550 DY-001 Mail rejected by Windows Live Hotmail for policy reasons. We generally do not accept email from dynamic IP's as they are not typically used to deliver unauthenticated SMTP e-mail to an Internet mail server. [http://www.spamhaus.org](http://www.spamhaus.org) maintains lists of dynamic and residential IP addresses. If you are not an email/network admin please contact your E-mail/Internet Service Provider for help. Email/network admins, please visit [http://postmaster.live.com](http://postmaster.live.com) for email delivery information and support (in reply to MAIL FROM command))

Can you determine anything from that??:)

---

### Post by jay.parnaby on 2009-08-30
Spamhaus is a service that a lot of ISP's and mail providers use as a measure to prevent spam. Because you have a dynamic IP it is rejecting the message, this is fairly common. Unfortunately there is not much you can do about this unless.

If you are going to run your PHP script on a home server then you will either need to relay your mail through your ISP or see if your ISP will assign you a static IP

---

### Post by magpy on 2009-08-30
Hi Thanks

That's strange, I'm not sure why MSN would express that, I use a static IP for my webserver and net connection at home.  The static ISP was given by my ISP.  Have you experienced anything like this before?  Or got any debugging ideas?
Cheers

---

### Post by jay.parnaby on 2009-08-30
It could be that the IP address your ISP gave you is still part of a DHCP pool but is permenantly assigned to you. You'd need to check with your ISP as spamhaus has it listed as a dynamic address.

You may be able to get the IP removed from spamhaus, best bet is to take a look at the website and see what you can find. Unless you can get the IP removed you are going to have problems, as many ISP's use the spamhaus lists.

---

### Post by magpy on 2009-08-30
Hi Thanks again

I'll check the website, this should mean that things are good to go?  The final piece in the jigsaw to get the IP off from the spamlist and find out what my ISP has to say.  I'll post back with some results:popcorn:

---

### Post by jay.parnaby on 2009-08-30
That should do it. I'd still recommend setting up an alias for www-data to your mail account just in case something like this happens again.

All the best

---

### Post by magpy on 2009-08-30
Hi Thanks :KS

It seems to be working, it appears that spamhaus blocks some ip
address ranges by default even if they are static.  I went to:

[http://www.spamhaus.org/sbl/index.lasso](http://www.spamhaus.org/sbl/index.lasso)

At the bottom of the webpage there is a web form, I looked up my IP address, and the result page returned that my IP address was on the policy block list PBL.

I followed simple instructions and submitted a removal request.  I got a confirmation email saying wait half a hour for the update, did that then ran the same script and it worked, email was sent straight into the inbox not junk folder.  Good all round.  I intend to do some research and more tests.

:guitar:

---

