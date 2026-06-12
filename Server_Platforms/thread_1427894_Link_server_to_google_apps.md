---
title: "Link server to google apps"
date: 2010-03-12
forum: Server Platforms
---

### Post by geoffmcc on 2010-03-12
Hello. I am currently running the latest version of ubuntu server. My ISP does not allow sendmail - port 25 is filtered.

I have signed up for google apps and with that get gmail for my domain. I have configured my dns so when i go to mail.mydomain.com it routes me to my google apps email signin page for my domain.

I am trying to find a way to link my server with my google apps email account so i can compose email on my server and receive it

I did some google searching and found some tutorials using ssmtp. tried following them. I was able to get it to work using their example but I want it to work using alpine and I was having trouble.

So next i found one that suggested using postfix and fetchmail tried to follow threw the tutorial but the ones that i am finding arent really that clear.

Has anyone done what I am trying to do and if so did you follow a tutorial? Please point me to an easy to follow one.

I have tried 
[http://freshmeat.net/articles/gmail-on-home-linux-boxes-using-postfix-and-fetchmail](http://freshmeat.net/articles/gmail-on-home-linux-boxes-using-postfix-and-fetchmail)

and

[http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

---

### Post by spynappels on 2010-03-12
I'm not clear what you are trying to do. The GoogleDocs is a hosted email service, you can then connect to it using any IMAP mail client to send and receive email, including from a server mail client.

Do you want to host your own mail server? Then you would be doing away with GoogleDocs and would have to change the DNS for mail.mydomain.com to point to your Public IP.

---

### Post by geoffmcc on 2010-03-12
cant host my own mail server. port blocked by ISP. 

trying to connect and relay mail to smtp.googlemail.com so i can configure cronjobs to send email verification

---

### Post by spynappels on 2010-03-12
Oh, I see.

OK, when I had to do this for a Nagios server, I found a Python script which allowed me to send stuff through a Googledocs SMTP server, so there was no need to set up a mailserver.

If that would be of any use to you, I'll see if I can dig it out.

---

### Post by geoffmcc on 2010-03-12
Actually. Now that I think of it i can deal with this.

Ok. Trying Ssmtp I was able to get mail to transfer correctly using the ssmtp [email]someemail@email.com[/email] method. However when gmail receives the email it removes the custom from address so no matter what user account sends mail it will always have the same reply to address (in this case [email]admin@email.com[/email]) as well as I was not able to send mail using alpine. 

However in the setup of Ssmtp it said that you can use mutt

Now I was able to configure alpine to connect to my google account with imap and smtp but it requires me to input my password whenever i send or receive plus this wont help with having the system send automated email messages (will it?)

Since I wanted to be able to have the system send auto email as well as me be able to send and receive regular email to/from contacts i didn't think what I have accomplished would do me any good. Now that i think of it the Ssmtp will take care of the auto emails and then i can just use alpine to check my email and send regular correspondences, right? Only thing since its going threw imap it wont give me new mail notifications, maybe i can look up configuring alpine for pop. Ok, now im just thinking out loud

---

### Post by spynappels on 2010-03-12
There is always more than one way to do things! Hope you get it to do what you want it to.

---

