---
title: "problems with mail function"
date: 2011-02-01
forum: Server Platforms
---

### Post by sajansen on 2011-02-01
hi,

system:
i have just installed a normal ubuntu 10.10 with apache2 and php5 and mysql and phpmyadmin and some other stuff for remote connection.

problem:
now is my problem that i have mail functions on my website and thy don't work properly. i don't get an error of nothing...

troubleshooting:
looked up the php.ini file and filed in the smtp server, sender email address and port number...

since i don't get an error i don't know ware to look for the solution...

thanks

---

### Post by SeijiSensei on 2011-02-01
sudo apt-get install bsd-mailx

For some reason known only to the developers, Ubuntu doesn't ship with a version of the command-line "mail" program.

---

### Post by sajansen on 2011-02-01
thanks for the advice.

i installed bsd-mailx but i still can send n email from my site... (or gmial has serious problems receving XD)

---

### Post by SeijiSensei on 2011-02-01
Are you trying to run this over a residential connection?  Your ISP may have blocked outbound connections on port 25.

Try this:

telnet gmail-smtp-in.l.google.com 25

Do you get a response?  If not, you're blocked.

---

### Post by sajansen on 2011-02-01
i use mail.home.nl (the mailserver from my Internet provider) i had used this before when i was using windows to host. (CRAP!!!!! :P) if i chack mail.home.nl i'm connected and get some usles messege that i may not use there server to spam and other stuff...

---

### Post by SeijiSensei on 2011-02-01
First, remove the entries you added to php.ini.  They apply to Windows installations of PHP.

If mail.home.nl will relay mail for you, you need to tell sendmail to use that machine as its "smart host."  Find the sendmail.cf file (it's in either /etc or /etc/mail) and edit the line that begins with DS like this:

```
DSmail.home.nl
```

Note that there's no space between these items.  Restart sendmail with "sudo service sendmail restart" and try again.

Now, it's also possible that mail.home.nl will refuse to forward mail addressed from domains outside their own.  In that case, you'll need to look for another provider or opt for a commercial-grade connection.

---

### Post by sajansen on 2011-02-01
i have only filed in some parameters in php.ini i did started off with the clean one from the ubuntu version, i did copy only the websites and database from windows server...

i installed (3 times) bsd-mialx but when i ask to restart the service it cant recognise the service... and i have no sandmail.cf...i have a mial.cf but that one has no DS****** in it...

and that mail.home.nl refused me would be a bit harsh form them..this server is in my home so in their Internet...

btw. sorry for all the trouble ;)

---

### Post by rudelgurke on 2011-02-01
And why you want to hassle with installing a full SMTP server on your machine just because you want to send mails to an external provider ?

Use msmtp / ssmtp as sendmail dropin replacement and both PHP and you'll be lucky. Easy to configure and PHP will be able to send mails by calling /usr/sbin/sendmail.
Additionally you won't have to care about another additional daemon running on your server that requires an eye to prevent it from being abused.

---

### Post by ingeva on 2011-02-01
> **rudelgurke said:**
> And why you want to hassle with installing a full SMTP server on your machine just because you want to send mails to an external provider ?I really don't understand the problem here. I  install Ubuntu with the postfix server (or install it afterwards, and I can send mail using php mail() from my own computer/server without any specific configuration.
If I want to use an external server I just set it to use port 465 or 587 (TLS or SSL security), and then of course I need to use the username and password.

Besides, my Ubuntu 9.10 AND 10.10 both are equipped with the mail program (someone indicated the opposite) but at least with no specific configuration, it only operates on internal mail, like system messages.

---

### Post by rudelgurke on 2011-02-01
> **ingeva said:**
> I really don't understand the problem here. I  install Ubuntu with the postfix server (or install it afterwards, and I can send mail using php mail() from my own computer/server without any specific configuration.

Because just to provide a sendmail binary for PHP's mail() function a complete SMTP daemon is not required.
In the above setup a simple mail forwarder like msmtp is good enough, simple and working.

---

### Post by sajansen on 2011-02-01
thanks...problem solved

---

### Post by sajansen on 2011-02-02
thanks for the advice everyone :P

---

### Post by vopros on 2011-03-07
e-mail blocked. Computer let me know "software index is broken
this is major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file /etc/apt/sources.list and reload the software information with: sudo apt-get update and sudo apt-get install -f."
I have no idea what is that mean and what i need to do. Help!

---

