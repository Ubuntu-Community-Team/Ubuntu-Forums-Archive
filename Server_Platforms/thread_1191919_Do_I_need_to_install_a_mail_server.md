---
title: "Do I need to install a mail server"
date: 2009-06-19
forum: Server Platforms
---

### Post by cinestar on 2009-06-19
Under Tasksel in ubuntu theres an option to install a mails server.

My question is should I isntall it. I need for my Apache/php/mysql server to be able to send out emails. (like from forms on the site) but i dont think i need any of the pop or smtp stuff. Is installing send mail enough?

Is there a resource out there that details everything i need to get a website fully functional. All i can seem to find is guides for one or the other but not for the whole shebang. Most aticles show how to install lamp, or the individual parts but even when i get the stuff working the sendmail stuff never works.

---

### Post by blackxored on 2009-06-19
No. You don't need a full-stacked mail server. You only need a Mail Transfer Agent such as exim4 or postfix.

---

### Post by blackxored on 2009-06-19
And sorry I missed the second part.

If you need a fully functional website out of box, is almost impossible, but what truly can help you a lot is a CMS like Drupal or Joomla.

---

### Post by hictio on 2009-06-20
How much email do think you'll send? Because there is a handy little program that will let you send email from your box without setting up a lot.

[Sending Email From Your System with sSMTP](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

---

### Post by windependence on 2009-06-21
You can have Postfix working in a few minutes by changing 3 or 4 parameters in the config file.

[http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu](http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu)

-Tim

---

