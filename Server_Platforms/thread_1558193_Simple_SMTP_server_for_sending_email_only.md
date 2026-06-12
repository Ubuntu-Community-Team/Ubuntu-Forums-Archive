---
title: "Simple SMTP server for sending email only?"
date: 2010-08-21
forum: Server Platforms
---

### Post by dkirkdrei on 2010-08-21
We are currently using this [SMTP server by Argosoft]("http://www.argosoft.com/rootpages/MailServerNet/Default.aspx") for sending emails from various web applications running on different servers throughout our network. This thing runs great but I would like to ditch the windows based app and set up a VM running Ubuntu 10.04 as a replacement. All I need is a simple SMTP server to handle sending emails, it does not need to receive but it does need to send mail from other servers on the network. I've googled around a bit but everything seems to be more complex than what I need. Can anyone recommend a good "How-To" article on setting up a SMTP server such as this? Thanks in advance for any help you can offer.

---

### Post by s1gnAl on 2010-08-22
Take a look at ssmtp. I've used it in the past with good results, but it's been a while since I've touched it. 

Might fit the bill for what you are looking for.

---

### Post by CharlesA on 2010-08-22
I use exim4 as a relay to gmail to send emails. It's not the best, but it works for what I want to do.

[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

---

### Post by josheby on 2010-10-11
I was looking for a similar solution as the original poster and I tried out ssmtp... I was able to get it installed and even sent mail via my gmail account using the ssmtp command via the terminal...

However I was unable to get Evolution to be able to send mail... I get the following error:

Could not connect to localhost: Connection refused

Any ideas why?

---

