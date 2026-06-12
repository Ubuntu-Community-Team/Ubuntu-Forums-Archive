---
title: "SendMail external SMTP username/password"
date: 2009-06-15
forum: Server Platforms
---

### Post by jo282 on 2009-06-15
Hi,

After searching gor about 2 hours without succes, i really need your help to setup my sendmail with my ISP smtp. I will explain my situation :

I bought a PHP script (SocialEngine 3.14) and it have a fonction to send email but i cant get it to work. On their website`s faqs they only tell me my php sendmail is not set up correctly. 

My ISP is blocking port 25 so i NEED to use their server to send mail, here`s the configuration i need to have :

> SMTP (outgoing) : relais.videotron.ca
POP (incoming) : pop.videotron.ca
Username : VL******
Password : ******

I guess i dont relly need the incoming one.

Please, help me! I really need to be able to send email on my website.

Thanks everyone.

---

### Post by hictio on 2009-06-16
Do you have to use Sendmail? There is a very handy program to handle exactly this type of problem called [ssmtp](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/), which is free.

If you have to do it using Sendmail, what you need is called SMART_HOST in Sendmail parlance, and you can read instructions (perhaps a bit towards the Red Hatish side of Linux) here: [Smart Host setup with SMTP Authentication on Sendmail](http://www.dnsexit.com/support/mailrelay/sendmail.html)

---

