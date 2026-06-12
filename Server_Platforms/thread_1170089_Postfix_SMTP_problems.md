---
title: "Postfix SMTP problems"
date: 2009-05-25
forum: Server Platforms
---

### Post by chrisab508 on 2009-05-25
Hey guys,
So I went ahead and setup postfix according to this guide: [http://flurdy.com/docs/postfix/edition7.html](http://flurdy.com/docs/postfix/edition7.html)
Everything seemed to go well.  I went to the testing section and tested sending an email via telnet.  I used
[PHP]telnet localhost 25[/PHP]
My connection went through, I then successfully sent an email to my gmail account.
Everything seemed to be working fine so I went ahead and tried to plug my smtp settings into thunderbird to see if I could send mail from there.  Unfortunately I get the following error everytime I try to send an email through Thunderbird:
> Sending of message Failed.
The message could not be sent because connecting to the SMTP server my.server.com failed...etc 
I'm not sure what's causing this so I was wondering if you guys could help me out.  Am I supposed to forward port 25 to my server?  I'm inclined to think that I shouldn't...but I may be wrong.

Thank you in advance,

- Chris

---

### Post by LepeKaname on 2009-05-26
Hi Chris... 

It can be a lot of different things... check your /etc/hosts it may be something wrong, but mainly your postfix main.cf.

I recommend you to spend a little bit more of time with postfix tutorials.

I developed a script to setup postfix/dovecot/clamav/spammassasin in about a minute (depending on your connection) with SASL and TSL authentication.

You can check it here:

[http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

Let me know if it was useful for you.

---

### Post by chrisab508 on 2009-06-01
Thanks a bunch for your response.  I ran your script and everything went smoothly, and it gave me the information at the end.
It told me my server name would be: mail.myserver.com and a test user account which was user: test3125.  I then went into thunderbird and created a new email account with all of the information your script gave me, and tried to send an email but the connection failed.  I'm not sure where to go from here, I think it might have a problem with mail.myserver.com name.

- Chris

---

### Post by chrisab508 on 2009-06-01
NM, I fixed it and it's all working correctly now.  Thank you for the help.

- Chris

---

### Post by madverb on 2009-06-01
How did you fix it?

---

