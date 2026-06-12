---
title: "PHP mail() not working"
date: 2010-02-09
forum: Server Platforms
---

### Post by anuvnu387 on 2010-02-09
Hello Everyone,

I am using ubuntu since Intrepid Ibex. Since then I have learnt a lot and just recently setup my own home/web server. 

I am running my LAMP server on Karmic. I have been slowly transferring my website from my current hosting company to my server. Got everything working except the PHP mail() function is not working. I do not get any error messages but the mail does not reach. /etc/log/mail.log is blank. 

I basically clueless about where to start. I did not install a mail server. Is this the reason? 
Should I check something in phpinfo() or the php.conf?

I do not have sendmail/postfix installed. Do I need any of these?

I have attached a screenshot of what is install (in case it helps).

I would really appreciate if some can provide hints on where to start.  

thank you very much.

---

### Post by anuvnu387 on 2010-02-14
Nobody answered. May be I did not post in the appropriate category/website.

Anyway, just wanted to update the thread in case someone looks for such information. 

I solved the problem using nullmailer and following this thread: [http://ubuntuforums.org/showthread.php?t=56077](http://ubuntuforums.org/showthread.php?t=56077)

For a simple form mailer kind of work nullmailer works. Something advanced may require postfix or other mail transfer agents.

---

### Post by Vegan on 2010-02-14
I use the corporate oriented postfix, IBM backs it so there is lots of documentation available if you know how to use search engines properly.

There are lots of choices, each is strengths and weaknesses.

---

