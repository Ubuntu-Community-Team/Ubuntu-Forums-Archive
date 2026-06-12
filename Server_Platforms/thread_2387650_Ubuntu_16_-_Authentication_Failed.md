---
title: "Ubuntu 16 - Authentication Failed"
date: 2018-03-22
forum: Server Platforms
---

### Post by razzkulz on 2018-03-22
Hello,

I have a dedicated server running Ubuntu 16. I installed XenForo on a subdomain, which is forums.xxx.com, and it has a built-in feature to send outgoing mail using a SMTP server. Now I host my mail at [https://mail.zoho.com](https://mail.zoho.com), which provides the SMTP settings automatically ([click here]("https://www.zoho.com/mail/help/zoho-smtp.html")). I've filled these in the settings of my XenForo forum, but when I try to send a test outgoing email, it keeps giving me the same authentication failed error. Here are the errors and stack traces. This is a clean Ubuntu install with no Postfix or Dovecot installed or configured, and if I use these SMTP settings in a mailing program such as Outlook, it works fine. So it seems to be something with my system, but I've got no idea where to look. Any ideas?

```
++ Starting Swift_SmtpTransport<< 220 mx.zohomail.com SMTP Server ready March 21, 2018 6:50:04 PM PDT


>> EHLO forums.novafivegaming.net


<< 250-mx.zohomail.com Hello forums.novafivegaming.net (ns551115.ip-142-44-142.net (142.44.142.129))
250-AUTH LOGIN PLAIN
250 SIZE 53477376


>> AUTH LOGIN


<< 334 VXNlcm5hbWU6


>> ZG9ub3RyZXBseUBub3ZhZml2ZWdhbWluZy5uZXQ=


<< 334 UGFzc3dvcmQ6


>> ZmFEUzgyaWZPdkFHRjQwUmNy


<< 535 Authentication Failed


!! Expected response code 235 but got code "535", with message "535 Authentication Failed
" (code: 535)
>> RSET


<< 250 state reset OK


>> AUTH PLAIN ZG9ub3RyZXBseUBub3ZhZml2ZWdhbWluZy5uZXQAZG9ub3RyZXBseUBub3ZhZml2ZWdhbWluZy5uZXQAZmFEUzgyaWZPdkFHRjQwUmNy


<< 535 Authentication Failed


!! Expected response code 235 but got code "535", with message "535 Authentication Failed
" (code: 535)
>> RSET


<< 250 state reset OK
```

```
#0 src/vendor/swiftmailer/swiftmailer/lib/classes/Swift/Transport/EsmtpTransport.php(332): Swift_Transport_Esmtp_AuthHandler->afterEhlo(Object(Swift_SmtpTransport))#1 src/vendor/swiftmailer/swiftmailer/lib/classes/Swift/Transport/AbstractSmtpTransport.php(118): Swift_Transport_EsmtpTransport->_doHeloCommand()
#2 src/XF/Mail/Mailer.php(276): Swift_Transport_AbstractSmtpTransport->start()
#3 src/XF/Mail/Mail.php(335): XF\Mail\Mailer->send(Object(Swift_Message), Object(Swift_SmtpTransport))
#4 src/XF/Admin/Controller/Tools.php(246): XF\Mail\Mail->send(Object(Swift_SmtpTransport))
#5 src/XF/Mvc/Dispatcher.php(249): XF\Admin\Controller\Tools->actionTestEmail(Object(XF\Mvc\ParameterBag))
#6 src/XF/Mvc/Dispatcher.php(88): XF\Mvc\Dispatcher->dispatchClass('XF:Tools', 'TestEmail', 'html', Object(XF\Mvc\ParameterBag), 'tools', Object(XF\Admin\Controller\Tools), NULL)
#7 src/XF/Mvc/Dispatcher.php(41): XF\Mvc\Dispatcher->dispatchLoop(Object(XF\Mvc\RouteMatch))
#8 src/XF/App.php(1891): XF\Mvc\Dispatcher->run()
#9 src/XF.php(328): XF\App->run()
#10 admin.php(13): XF::runApp('XF\\Admin\\App')
#11 {main}
```

```
array(4) {  ["url"] => string(27) "/admin.php?tools/test-email"
  ["referrer"] => string(60) "https://forums.novafivegaming.net/admin.php?tools/test-email"
  ["_GET"] => array(1) {
    ["tools/test-email"] => string(0) ""
  }
  ["_POST"] => array(2) {
    ["email"] => string(18) "blankemail@gmail.com"
    ["_xfToken"] => string(8) "********"
  }
```

---

### Post by volkswagner on 2018-03-23
The link you provided to zoho shows using SSL or TLS, but it appears you 
are using plainAuth?

You need to make sure your web application is using SSL or TLS.

---

