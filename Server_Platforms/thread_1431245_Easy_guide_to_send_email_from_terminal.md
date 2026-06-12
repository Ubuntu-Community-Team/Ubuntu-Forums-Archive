---
title: "Easy guide to send email from terminal ?"
date: 2010-03-16
forum: Server Platforms
---

### Post by rbalaa on 2010-03-16
Can someone please point me to a guide to be able to configure my server to be able to send an email ? I don't need to be able to receive email on the server, just send. Is there a fairly easy way to do this ?
 
Thanks.

---

### Post by slakkie on 2010-03-16
Postfix.org has plenty of online material to setup a mailserver.

And for sending mail via the terminal, depends on how you want to do it. Alpine can use localhost or remote mailservers (eg your ISP's server), since it is a mail client..

If you want to send directly from the command line, you can do it like this;

echo test | mail -s "test mail from cli" [email]you@e-mail.com[/email]

---

### Post by CharlesA on 2010-03-16
What I've done on mine is set up a local SMTP server that forwards mail to gmail for sending.

I used this guide: [http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

---

### Post by rbalaa on 2010-03-16
> **CharlesA said:**
> What I've done on mine is set up a local SMTP server that forwards mail to gmail for sending.
 
I used this guide: [http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)
 
I will try this tonight. Thanks.

---

### Post by CharlesA on 2010-03-16
> **rbalaa said:**
> I will try this tonight. Thanks.

Be sure to look at the comments as well, I recall having to set something in /etc/exim4/passwd.client

---

### Post by KB1JWQ on 2010-03-16
Install Postfix, start the sevice, and you're largely done; by default Postfix listens to localhost.

Obviously there CAN be a lot more to it, but out of the box this'll send mail.  If you want to go a step further and have it relay all the mail through a specific host, you can add this to main.cf:

relayhost = [your.target.host]

---

### Post by dudumomo on 2010-03-16
Yes, I agree, postfix will be also perfect !

---

### Post by rbalaa on 2010-03-16
> **dudumomo said:**
> Yes, I agree, postfix will be also perfect !
 
Is this a good guide for Postfix ?[http://linux.about.com/od/ubusrv_doc/a/ubusg29t05.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg29t05.htm)
 
It seems like alot of config to just be able to send an email. I don't mind sending mail as a relay from my gmail account, I just need to see if there's an easier guide as I am a newbie with mail configurations. 
 
I will try Postfix again tonight.

---

### Post by KB1JWQ on 2010-03-16
As I said earlier, postfix CAN do a lot, but what it does by default out of the box should be enough for you.  Receiving mail is a bit more challenging, but sending mail more or less requires "install it and turn it on, you're done."

If you get stuck, feel free to ask here or in #postfix on freenode.

---

### Post by dudumomo on 2010-03-16
rbalaa, check my website then.
I've done several tutorials.
I hope it will help you.

---

### Post by rbalaa on 2010-03-16
> **dudumomo said:**
> rbalaa, check my website then.
I've done several tutorials.
I hope it will help you.
 
Very good. I like screenshots! Thanks.

---

### Post by OvR on 2010-03-19
im trying to send an email in my terminal and Ive done it before but for some reason I keep getting Null body errors this is what im typing

mail -s Subject
to:email@address.com
cc:
Body text
ctrl-d out

Null body message, hope thats ok
wtf am I doing wrong

---

