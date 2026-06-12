---
title: "Postfix unexpected and potentially dangerous behavior when configured as &quot;Local only&quot;"
date: 2007-12-30
forum: Server Platforms
---

### Post by lucatrv on 2007-12-30
Hi all,
As you know Postfix is the preferred Mail Transfer Agent of Ubuntu.
One would expect that configuring Postfix through dpkg-reconfigure as "Local only" (and with "mynetwork=127.0.0.1/8") would mean that Postfix will only manage the transfer of local mail (such as the mail from cron jobs to the main user).
However, that's not true. In fact, also with that configuration Postfix will still be able to send mail to the internet, and the worse is that it will do it directly (not through the use of an SMTP smarthost).
You can try out that with a simple "mail youremail@yourmailccount" command.
I think this could be dangerous in case of an attack by a spammer script, especially because the server administrator could think to have disabled Postfix outbound mail sending with such a configuration.
It should be noted that with exim4, the debian preferred MTA, the dpkg-configure command works as expected, so that when configured for "Local delivery only" it would be unable to send mail to the internet (when doing "mail youremail@yourmailccount" an error message is sent to the local sending user).
I'm not sure if this is a bug or just a subtle difference in how the two MTAs are configured, but anyway I think this should be at least better explained in the dpkg-reconfigure screens or in the online manual pages, because it would be dangerous to leave an MTA free to directly send email without knowing it.
Thanks, bye.
Luca

---

### Post by crouton on 2008-01-03
Per Google Groups ([http://groups.google.com/group/list.postfix.users/browse_frm/thread/50d5e60c8db32471/a1273c0268f87631?lnk=gst&q=local+only+no+remote&rnum=22#a1273c0268f87631):](http://groups.google.com/group/list.postfix.users/browse_frm/thread/50d5e60c8db32471/a1273c0268f87631?lnk=gst&q=local+only+no+remote&rnum=22#a1273c0268f87631):)

> This is not possible, anyone who can submit mail to local users via
sendmail(1), can also submit mail to remote users. The best you can do
is make all remote destinations bounce back to the local sender.

        default_transport = error:External deliveries disabled

This breaks bounces, so you need a separate Postfix instance for local
delivery and incoming mail. The default (/etc/postfix) instance should
be for local delivery and not run smtpd, while the inbound instance
(/etc/postfix-in) should accept only mail for local recipients. 

In essence you can do the above but it would break local delivery failures as well as remote delivery.  If that's not acceptable, you need to break the mail into separate instances.

---

