---
title: "Howto: newbie nullmailer: esmtp (only sends mail, no forwarding or mail distibution)"
date: 2005-08-11
forum: Tutorials
---

### Post by Tuxbee on 2005-08-11
Hello all,

This is my first post here, and my first Howto in general!
Hope it works for you. ;)
I lost a whole day trying to get this working, now hopefully you wont, after reading.

You want a sendmail compatible mail system
You only need to send mail to the internet

For example: you want to have your local PHP webserver mailing

Go system > administer > synaptic

Uninstall postfix
(your old Mail Delivery Agent)
(choose complete uninstall to get rid of the config files)

Install esmtp; esmtp-run; libesmtp5

The installer asks your internet domain.
If you have no internet domain, supply a fantasy name like "domain.invalid"

Then check the config file /etc/esmtprc
For a basic setup, make it look like this:
```

hostname = mail.myisp.com:25
username = "myself"
password = "secret"
starttls = disabled

mda "/usr/bin/procmail -d %T"

```
Leave the username/password string empty if you don't need authentication.

It should be done!
To send a test mail, you can type
```
echo "test" | sendmail youraddress@hotmailorherever.com
```

I didn't figure how to use TLS for outgoing mail authentication, guess that's difficult because you need a certificate file, and it's all new and still under development.
So, no gmail sending, sorry.

Also check out:
[http://esmtp.sourceforge.net/manual.html](http://esmtp.sourceforge.net/manual.html)
You might want to try sSMTP instead:
[ftp://sunsite.unc.edu/pub/Linux/system/mail/mta/](ftp://sunsite.unc.edu/pub/Linux/system/mail/mta/)
Or nullmailer (in the repository as well, but I didn't get it working)
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

---

### Post by Thunderbird750 on 2006-04-16
Nice Howto!

For folks who may not have configured their outgoing mail lately, a "good guess" for your smtp mail server may be
smtp.{yourIspDomain}
  or
smtp-server.{yourIspDomain}

If neither of those are found, drag up your settings for outgoing mail server in a working mail program (eg: netscape or thunderbird).

---

### Post by mslonik on 2006-10-12
Hello,

This newbie nullmailer is exactly smth that I was looking for.

Additional info to your how-to. One should also install procmail.

My question is, how the output of the example command should look like?

How to interpret the following output:

My code was:
```
maciej@gucek2:/$ sudo echo "test" | sendmail mslonik@poczta.onet.pl
0 (null)
mslonik@poczta.onet.pl: 0 (null)
```

I use Thunderbird as my mail client. In fact nothing was sent to my e-mail :-( Did I miss something?

Kind regards,
Maciej (mslonik)

---

### Post by rsay on 2007-05-13
I just wanted to get system messages about overheating and backups sent to my email account and had a really hard time getting it done until I found this thread. 

Thank You

---

### Post by md5hash on 2007-10-23
i got a broken pipe? how to fix this?
```

yoshi@xterm:~$ cp /etc/esmtprc /home/yoshi/.esmtprc
yoshi@xterm:~$ echo "test" | sendmail alabarda@viva.com.px
File /home/yoshi/.esmtprc must have no more than -rwx--x--- (0710) permissions.
open: /home/yoshi/.esmtprc: Success
bash: echo: write error: Broken pipe

```

---

### Post by md5hash on 2007-10-23
ok got it but im getting 
```

0 (null)
alabarda@viva.com.px: 0 (null)

```

---

### Post by rsay on 2008-09-10
I was getting the 0 (null) error from esmtp apparently because the *from* field in the email was blank. I found out that I could use:

```
echo "test" | sendmail -f your_sending_email@mydomain.com youraddress@hotmailorwherever.com
```

So I added an alias to my .bashrc
```
alias sendmail='sendmail -f your_sending_email@mydomain.com'
```

And now the original command works without the 0 (null) error.

I couldn't figure out how to get it to work from the esmtprc config file though.

---

### Post by jackie001 on 2008-11-07
im trying to use esmtp to relay the mail to the mail server. how to do this?

---

### Post by scottie2212 on 2009-01-04
Hi,

I wish I'd seen this last week! I've spent too many hours trying to get various mailers to work and have ended up with exim4 working but not as I would like.

It seems like esmtp or ssmtp is exactly what I want but I do have a question. This might seem like a simple thing but I am a dumb newbie who doesn't have a clue what he's doing. Anyway, my question is this ...

Will either esmtp or ssmtp send 'root' mail to my personal mail account (on ntlworld). If so, how do I make the necessary config settings?

---

### Post by ChrisBuchholz on 2009-01-25
I've done as descriped but when I try to send a mail, I get the message "SMTP server problem Name or service not known".

One thing I noticed, is that when I installed the 3 packages, I wasn't asked for a internet domain, as you said one will. I don't know if it's because the internet domain is missing, I get the error when trying to mail a message?

---

### Post by ChrisBuchholz on 2009-01-26
No body who can help me with my problem?

---

### Post by jesuspresley on 2011-10-28
Very easy, I was able to install within 5 minutes, thanks. Better then sendmail or nullmailer.

---

### Post by Audiosears on 2011-11-15
Tux,

Thanks for your post!  I had been using Sendmail to do this for a long time, and have had plenty if headaches in the past when updates broke my setup for simply sending PHP mails from my web forms.

Your setup works like a charm, and is FAR simpler! :D

---

