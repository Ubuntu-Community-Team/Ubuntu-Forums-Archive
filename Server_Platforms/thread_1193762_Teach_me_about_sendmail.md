---
title: "Teach me about: sendmail"
date: 2009-06-21
forum: Server Platforms
---

### Post by Kareeser on 2009-06-21
As I've discovered lately, "sendmail", while popular, is quite difficult to configure and/or customize. Ideally, I'd like to host an email relay or server, but one step at a time!

My extent of knowledge on MTAs and sending mail is thus:
```
sudo apt-get install sendmail
```

That little magical command was enough to download, install, and configure sendmail, so my web applications could send emails across the globe.

However, there doesn't seem to be any way to send mail TO the server in question. That is, if I send an email to [email]kareeser@mydomain.com[/email] (mydomain.com being an example, of course), the sender (in this case, GMail) reports it as sent, but it never arrives in my local mailbox on /var/mail. So, I'm guessing that there needs to be some sort of configuring to be done on the server side so I can receive email?

Be blunt! If the answer is "sendmail is exactly what it says, it SENDS MAIL, you dolt!", then tell me!

I've been looking at other MTAs, like exim4... are they easy to set up?

Teach a newbie sysadmin!

---

### Post by mobj on 2009-06-22
a simple [google search]("http://www.google.ch/search?hl=de&q=sendmail+receive+mail&btnG=Suche&meta=") revealed those:

[http://www.elandsys.com/resources/sendmail/]("http://www.elandsys.com/resources/sendmail/")
[http://www.harker.com/sendmail/accept.local.domain.html]("http://www.harker.com/sendmail/accept.local.domain.html")


HTH

---

### Post by E_K on 2009-06-22
dont bother with sendmail, look into, postfix and dovecot.

If your going to do something do it properyly

just google.... "ubuntu how to 'whatever'"

check if the ports you want to use are open from your ISP, this is VERY annoying, and you might have to use a deflector service such as the one available from no-ip and run your servers from a non standard port.

Even then you may have to use your ISP as your SMTP server ;)

---

### Post by hictio on 2009-06-23
Sendmail by default does not listen on the network interface, it only does on the loopback one (that's one of the reasons why you have been able to send emails from your box)
Since current Sendmail versions only listen for connections on the loopback interface, you'll have to edit the sendmail.mc configuration file, and add the IP address of the ethernet device connected to the network (or remove all the entries, and allow Sendmail to listen on every single one)
Here you can read a very good tutorial on how to it, is it based on Red Hat, but except for the RPM stuff, it'll work

[Configuring Linux Mail Servers](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/sendmail.htm)

---

### Post by windependence on 2009-06-23
Almost no one uses sendmail anymore. Postfix is a drop in replacement for sendmail and is probably the most popular MTA out there today on Unix. 

If you are looking into building a mail server, you may be surprised to learn that it's not a beginner's project. A full mail server requires an MTA and a POP or IMAP server to send and receive e-mail. Many of us who just want to run our own mail server use a bundled package such as Zimbra or Citadel. these packages install all you need in one convenient package and are much easier to configure.

-Tim

---

### Post by Bachstelze on 2009-06-23
> **windependence said:**
> Almost no one uses sendmail anymore. 

[http://www.securityspace.com/s_survey/data/man.200705/mxsurvey.html](http://www.securityspace.com/s_survey/data/man.200705/mxsurvey.html)

---

### Post by windependence on 2009-06-23
> **HymnToLife said:**
> [http://www.securityspace.com/s_survey/data/man.200705/mxsurvey.html](http://www.securityspace.com/s_survey/data/man.200705/mxsurvey.html)

I knew someone was going to do it. Why is it necessary to try to dispute something that is helpful to people, especially n00bs? Even with all the years of experience I have with Linux/Unix, I still don't want to, nor do I know anything about configuring sendmail. Not only that, I won't even get into the security problems with it.

Do you really think it's useful to encourage users (especially new users) to use something extremely difficult to configure and insecure?

I'm not about to get into a pissing match with you on what MTA is most popular as it is irrelevant to the OP's question but it should be pointed out that the survey you quoted is certainly not all inclusive or even necessarily a significant sample of the total mail servers in use. Furthermore, banners are not an accurate indicator for what software is being used, not to mention the survey is over 2 years old. 

Now let's help the user with his problem shall we?

-Tim

---

### Post by Bachstelze on 2009-06-23
> **windependence said:**
> I knew someone was going to do it. Why is it necessary to try to dispute something that is helpful to people, especially n00bs? Even with all the years of experience I have with Linux/Unix, I still don't want to, nor do I know anything about configuring sendmail. Not only that, I won't even get into the security problems with it.

Do you really think it's useful to encourage users (especially new users) to use something extremely difficult to configure and insecure?

I'm not about to get into a pissing match with you on what MTA is most popular as it is irrelevant to the OP's question but it should be pointed out that the survey you quoted is certainly not all inclusive or even necessarily a significant sample of the total mail servers in use. Furthermore, banners are not an accurate indicator for what software is being used, not to mention the survey is over 2 years old. 

Way to not go into a pissing match! You said something that was blatantly wrong, I corrected it. Period. Now until the OP tells us which MTA he chose, we can't really help him about configuring it.

My recommendation: sendmail. I'm running it on two mail servers, it's not nearly as difficult to configure as many people make it look like. As for being "insecure", I shall remind you that, to give just one example, OpenBSD uses it as its default MTA, and the OpenBSD people do not exactly have a reputation for including "insecure" software in the base system.

---

### Post by joeydan1 on 2009-06-23
hihi
i'm the first time to use the sendmail software, now have several questions as below, hope can be answer, thanks.
 
when i typed the command would show this error 
 
[root@localhost]# service sendmail start
Starting sendmail: sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
 
i'm installed the postfix before, but already unstall it by "rpm -e postfix", i don't know why it need the postfix/main.cf file when starting the sendmail, anyone know the reason?
 
daniel~

---

### Post by hictio on 2009-06-23
> **joeydan1 said:**
> hihi
i'm the first time to use the sendmail software, now have several questions as below, hope can be answer, thanks.
 
when i typed the command would show this error 
 
[root@localhost]# service sendmail start
Starting sendmail: sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
 
i'm installed the postfix before, but already unstall it by "rpm -e postfix", i don't know why it need the postfix/main.cf file when starting the sendmail, anyone know the reason?
 
daniel~

rpm? What Linux distribution are you using? Red Hat or CentOS?

---

### Post by windependence on 2009-06-23
> **HymnToLife said:**
> Way to not go into a pissing match! You said something that was blatantly wrong, I corrected it. Period. Now until the OP tells us which MTA he chose, we can't really help him about configuring it.

My recommendation: sendmail. I'm running it on two mail servers, it's not nearly as difficult to configure as many people make it look like. As for being "insecure", I shall remind you that, to give just one example, OpenBSD uses it as its default MTA, and the OpenBSD people do not exactly have a reputation for including "insecure" software in the base system.

Against my better judgment and not intending to start a flame war because we are all on the same side :-) I'm going to respond since I run *BSD on practically every production machine I have.

Two things. Just because an MTA is included in the default install does not mean there is anything special about it. With sendmail it goes more to tradition than anything else. Historically, sendmail has been included in Unix for decades and is expected to be there. 

That being said, You may or may not know that OpenBSD is an operating system. Linux us not. It is a kernel. As such, before any port is added to the default install or as an option in OpenBSD it is audited by the OBSD team to be bullet proof. This is true of all OBSD software and this is why it is one of the most if not THE most secure OS on the planet with only two remote holes in over ten years. That does NOT mean it is any easier for a n00b or even a seasoned professional to configure. 

We can certainly let him make his own choice. There is Exim and several others as an option, however I think you may agree Postfix has a great user community and is very well supported with tons of tutorials on the web. If he should choose Postfix, I'm ready to help.

-Tim

---

### Post by joeydan1 on 2009-06-23
> **hictio said:**
> rpm? What Linux distribution are you using? Red Hat or CentOS?
 
yes, i used the RPM package for the software install, my os is Fedora 8,

---

### Post by Kareeser on 2009-06-24
My apologies for not replying sooner. I was turned off by the smart aleck who told me to google myself some answers (post 2, not 3.), and didn't check back until today.

Thanks for all the clarification, everybody. I ended up choosing exim4, which was fairly straightforward to set up.

One niggling problem, though:
In the debconf autoconfig, I was asked to provide an IP address for the server to listen on, so I faithfully plugged in my public static IP that refers to the server in question.

However, on running the startup script from /etc/init.d, exim4 complained that it couldn't use port 25, even though nothing was using it. (It's not the same error as "Port unavailable"... error message available on request)

I ended up conceeding and allowing exim4 to accept mail from anywhere (essentially, left the option blank)... and that worked, but why couldn't I tie exim4 to my public IP?

P.S.
Seems like postfix is the MTA of choice here - sorry I chose the other contender :)

---

