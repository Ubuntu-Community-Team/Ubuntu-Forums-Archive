---
title: "Sending mails via php on Apache server"
date: 2009-01-19
forum: Server Platforms
---

### Post by ChrisBookwood on 2009-01-19
Hi,

I have set up an Apache server on my main machine, and installed php and mysql also, for the sake of testing my websites before I launch them for the public.

I would like to also send e-mails via php from the apache server. I have created a billing system and when the customer is ready, an email will be fired off to the company and a reciep for the costumer, but as of now, when I fire the php script that handles the email, php doesn't complain about not being able to send the email, it just doesn't send it - well, I think it doesn't send it, because I never recieve it in my inbox.

I have been looking i the ubuntu repo's for something to install, which allows me to send emails from the apache server, but I haven't been able to find anything of such.

Also, the apache server doesn't have a public ip or anything. It not on the internet, if you get it.

---

### Post by cb951303 on 2009-01-19
paste the mail code here and then we can help

---

### Post by ChrisBookwood on 2009-01-19
> **cb951303 said:**
> paste the mail code here and then we can help

I am quite sure it has nothing to do with my php code. I believe it's the apache server that needs some package to be able to forward the emails to the net.

Anyways, you can see the php code at [this link]("http://paste2.org/p/132092").

**UPDATE**
I recieve the $*state equals 1* head up every time I run the app, so it does in fact run the mail-part.

---

### Post by cb951303 on 2009-01-19
I needed to see how you form your msg body and which function do you use to send email.

this may not be the problem but a little quote from php.net

> 
Note: If messages are not received, try using a LF (\n) only. Some poor quality Unix mail transfer agents replace LF by CRLF automatically (which leads to doubling CR if CRLF is used). This should be a last resort, as it does not comply with » RFC 2822.

also, do you know if mail() function uses sendmail daemon? if so you should probably install and setup sendmail first

---

### Post by ChrisBookwood on 2009-01-19
> **cb951303 said:**
> I needed to see how you form your msg body and which function do you use to send email.

this may not be the problem but a little quote from php.net



also, do you know if mail() function uses sendmail daemon? if so you should probably install and setup sendmail first

I can assure you that there's nothing wrong with the php function. I have used mail() a whole lot of times before on other servers, and I have looked through that code and compared it with the one I'm working on now, and everything seems fine.

I don't think I have any sendmail or postfix anything setup. I've just installed apache2, php and mysql. Nothing else, so I guess I need to install those other things.
Can you please, very detailed, tell me what to install and how to set it up, or link to a tutorial or something? Cause I have looked around, but can't find anything, I'm afraid.

---

### Post by cb951303 on 2009-01-19
> **ChrisBookwood said:**
> I can assure you that there's nothing wrong with the php function. I have used mail() a whole lot of times before on other servers, and I have looked through that code and compared it with the one I'm working on now, and everything seems fine.

I don't think I have any sendmail or postfix anything setup. I've just installed apache2, php and mysql. Nothing else, so I guess I need to install those other things.
Can you please, very detailed, tell me what to install and how to set it up, or link to a tutorial or something? Cause I have looked around, but can't find anything, I'm afraid.

No, you don't understand. I'm not saying there is something wrong with your code or with mail() function. I'm saying there is some steps to take according how you implemented the mail sending in your code therefore always include the code with your question.

now the simplest and 100% sure way of installing apache + mysql + php in ubuntu is this

```

sudo tasksel install lamp-server 
```

it installs and set-ups everything for you except userdir support which can be easily enabled with
```

sudo a2enmod userdir

```

I know you already installed/configured apache etc but if you did all that manually I suggest you to remove everything and try this method. This way you'll have better chance not to screw up with configurations.

For mail support
```

sudo tasksel install mail-server 
```
should be enough. I don't think you need any configuration for this since apache and php should be able to communicate directly with postfix daemon.

let me know how it goes:popcorn:

---

### Post by hyper_ch on 2009-01-19
you either need to setup yoru own mailserver on that machine or relay your mail through an email account at a provider.

Best, install mailx and then try to send a mail from the cli:

```
mail -s "Subject" recipient@domain.com[ENTER]
Message[Enter]
[Enter]
[Enter]

```

if you can send mail like this, then you can also with php/apache... but as said you first need to configure outgoing email.

---

### Post by ChrisBookwood on 2009-01-19
It worked perfectly, [cb951303]("http://ubuntuforums.org/member.php?u=64544")!

Thanks...

---

### Post by hyper_ch on 2009-01-19
many mailservers won't accept mail coming from a dynamic ip. Just make sure it works fine... if you are on a dynamic ip have it relayed through your ISP.

---

### Post by cb951303 on 2009-01-19
> **ChrisBookwood said:**
> It worked perfectly, [cb951303]("http://ubuntuforums.org/member.php?u=64544")!

Thanks...

you're welcome
glad I can help

---

### Post by Thirtysixway on 2009-01-19
anyone know how to set it up so gmail is the smtp server that php uses?

---

### Post by pannerrammer on 2009-01-21
> **cb951303 said:**
> you're welcome
glad I can help

My LAMP installation had been missing the 
```
sudo tasksel install mail-server
```bit (and I've been working around the problem for months!). So thanks from me also.

---

