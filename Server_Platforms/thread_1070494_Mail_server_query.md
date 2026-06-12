---
title: "Mail server query"
date: 2009-02-15
forum: Server Platforms
---

### Post by vhinz on 2009-02-15
Guys, a noob in linux here.  

I am trying out to build a mail server but am not successful.  I tried the steps outlined in the server guide but to no avail.  I can not connect through telnet.  

The setup would be--we have a domain and registered it with Live Domains.  What I plan to do is have the emails synchronize (or or download or something like that) using fetchmail. 

Is this possible?

---

### Post by vhinz on 2009-02-15
Guys, I have also seen posts re: Citadel and Zimbra, I checked it out and wonder, can Citadel or Zimbra do the things I entered earlier?

---

### Post by vhinz on 2009-02-18
Bump

@HermanAB,
Any ideas if Citadel have these features? (as the most prominent, persistent promoter of Citadel) :p

But its nice to know that I can easily setup a Citadel system. :D

---

### Post by hyper_ch on 2009-02-18
I don't understand that live domains part. Care to explain? And what do you want to forward or fetch?

---

### Post by vhinz on 2009-02-19
Well, its something like I would like to download the mails which we hosted on [Live Domains]("http://domains.live.com/") (its more of like a Live Hotmail).  What I would like to do, if possible, is to synchronize, download or fetch the mails from there. Hotmail uses HTTP/MAPI to connect to their server.

We are using the Live Domain service because its free and can have 5GB mail space...nothing more. Google Apps on the other hand requires a fee for business/enterprise usage. 

Thanks so much!!
 :D

---

### Post by hyper_ch on 2009-02-19
why not host your server completely? The only restrictions you then have is the harddisks you put in.

Google has two business emails, one is free, the other one is not.

---

### Post by vhinz on 2009-02-19
Figured that one already but the thing is the availability.  On a budget constraint times, we need to have a redundant server--one on the web and other locally.    

I have used Google Apps for my private domain courtesy of co.cc and it is working like a charm.  No server setup has been done, just points it to google server.

It will be my 1st time to setup a mail server...and I would like it on Linux for security purposes.  I have been planning on learning Linux for a long time but it has not took off.  But right now, I am really inspired to learn.  Chosen ubuntu because they said its easy.  

Enough of my hanky-panky.  Just visited Google and businesses should use their Premier Edition.  

Just last evening, I tried Citadel and works, but unfortunately, since we are behind a NAT, I can not still resolve the incoming mails.  Local mails are routed.  

I also think that I have correctly configured postfix pthe last time but the A or MX Records still has to propagate.  On my 1st post in this thread, I specified that telnet on the server I made is failing.  Right now, when I telnet to mail.mychosendomain.co.cc, I can reach the gateway...some configurations on its firewall (I think).

---

### Post by HermanAB on 2009-02-19
Yes, Citadel can fetch mail from another server and deliver to an ISP server (smart host).  Just install and try it.  It only takes a few minutes.

Cheers,

Herman

---

### Post by vhinz on 2009-02-19
Cheers Herman...would like to try it.  Will it fetch Live Hotmail accounts as well?

---

### Post by vhinz on 2009-03-27
Hi Herman...its been a longtime.  I have tried Citadel locally.  Works wonderful but can not pull my mails from Live Mail.  I've read in [lifehacker]("http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide#c") that Windows Live has just enabled the POP3 access to live mails.  Can anyone confirm if they can use citadel with their present hotmail accounts?  if yes, how?  Since there is no port field, I tried the pop3.live.com:995 for the POP Server without success.  Same thing is true even without the port.

> POP server: pop3.live.com (Port 995)
POP SSL required? Yes
User name: Your Windows Live ID, for example [email]yourname@hotmail.com[/email]
Password: The password you usually use to sign in to Hotmail or Windows Live
SMTP server: smtp.live.com (Port 25)
Authentication required? Yes (this matches your POP username and password)
TLS/SSL required? Yes

It indicates that I have to create a new account, which would be useless because we are already using our mails, just started rolling out 2 weeks ago, I've read the article on the 19th.

Help pls?

Thanks!

---

### Post by vhinz on 2009-03-29
Anyone? Thanks!

---

### Post by HermanAB on 2009-03-29
See this:
[http://www.citadel.org/doku.php/faq:favoriteclient:how_do_i_retrieve](http://www.citadel.org/doku.php/faq:favoriteclient:how_do_i_retrieve)

Maybe it works for you.

---

### Post by vhinz on 2009-03-30
tried the Webcit POP put it is not pulling the mails.  Any document on how to use Citadel with Fetchmail? I know fetchmail will have some switches for pop3 protocol and using SSL and to leave the message on the outside pop server.

---

