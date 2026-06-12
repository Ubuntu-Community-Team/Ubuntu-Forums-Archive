---
title: "Setting up PHP to send mail (novice)"
date: 2009-09-08
forum: Server Platforms
---

### Post by James M Weir III on 2009-09-08
Ok, I've been pulling out my hair for the last few days trying to figure this out.

Situation:
- Hosting Apache2, PHP5, and MySQL on my home machine.
- Home machine is running Ubuntu 9.04
- Using DynDNS (updating via Linksys router) to sub.domain.tld
- Router has ftp, ssh, www, and smtp forwarding to host machine
- Host's firewall allows incoming traffic from those ports as well

Been trying to setup a WordPress site but the php mail() function is not working (which I need for new user registration, amongst other things).

My php.ini is as follows:

> [mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = [EMAIL="me@example.com"]me@example.com[/EMAIL]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i
I have tried using sendmail, postfix, exim4, and citadel (which was a huge mess).  I cannot seem to find a **simple** way to send mail from the host machine.  I don't need to receive anything, and I don't need users setup.  I just want my sites to be able to send out using mail().

When I try using 'mail -s subject [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL]' it never sends.  I have tried various addresses.

A lot of the documentation I've read involving FQDN's and mail servers gets very complicated very quickly.  I apologize if I'm asking something that seems trivial, but I have been all over this site and google and just end up running around in circles (I think I've installed/removed various MTA's about thirty times).  My last resort is posting to a forum because I like to be proactive, and waiting for a response feels like giving up.

---

### Post by bguebert on 2009-09-08
[http://sourceforge.net/projects/phpmailer/](http://sourceforge.net/projects/phpmailer/)

It's in the repos too. 

sudo aptitude search phpmailer

To use see:

[http://www.askapache.com/php/phpfreaks-eric-rosebrocks-phpmailer-tutorial.html](http://www.askapache.com/php/phpfreaks-eric-rosebrocks-phpmailer-tutorial.html)

Also use someone else's smtp server rather than trying to set up your own. If you just want to send email then it is not worth the trouble.

---

### Post by James M Weir III on 2009-09-08
I'll give this a try, but it says it uses sendmail (which I can't get working on its own).

Also, what do you mean by use someone else's smtp server?  I wasn't aware that there were freely available servers out there I could just use.

---

### Post by bguebert on 2009-09-08
If your ISP offers email service with your internet then they should have given you a host name used to setup smtp for email clients.

I'm not for sure on this, but sendmail gets setup to deliver locally by default and it has to be configured to email externally.

Make sure you tell it to use SMTP instead of sendmail with something like:
$mail->IsSMTP();
$mail->Host = "smtp1.example.com";

I just remember having trouble using the method you described and it worked to use this class instead of trying to configure sendmail to work for external email.

---

### Post by Cardale on 2009-09-09
James your setup sounds exactly the same as mine and at this very moment I'm trying to get my mail function work... :P any way I have been having a issue with my domain not working at certain times.  If you don't mind me asking have you had any problems with this?  If no maybe you could help with my setup a little bit.

I have the same version of Ubuntu using Dyndns updating off a linksys router and port 80 forwarded to the correct computer.

Thanks and if I figure it out ill let you know.

---

### Post by James M Weir III on 2009-09-09
Well this fixed all my problems...

[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

I was able to dig up my ISP's SMTP as well, but they had their own series of authentication hurdles to jump through and Google seemed like a more ideal solution.

Immediately two dozen test messages came flooding into my inbox.  Finally!

As with everything else in linux I learned a thousand new things unrelated to my problem.  Always an experience.

---

