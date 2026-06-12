---
title: "dyndns  postfix 'n' me"
date: 2005-02-17
forum: Server Platforms
---

### Post by az on 2005-02-17
I do not know what I am doing.

I suppose that my ISP is blocking port 25.  Fair enough, use the ISP as a smarthost.  I have waded through a lot of documentation but I cannot figure how to send an email.

When I can get it to send, I get returned mail:

"This is the Postfix program at host ******.dyndns.org.

I'm sorry to have to inform you that your message could not be
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

			The Postfix program

<*****@yahoo.ca>: host smtphm.sympatico.ca[65.54.191.190] said: 530 5.7.0
    Must issue a STARTTLS command first (in reply to MAIL FROM command)"


Please help.

---

### Post by Rottweiler on 2005-02-17
You might want to post more specific details of what exactly you're trying to do and perhaps post your /etc/postfix/main.cf . I'm also not sure how dyndns figures into it - is that your ISP or someone you're trying to send to.
   
 Anyway, in mine the only thing required to get postfix working as an internal relay agent was to add this to /etc/postfix/main.cf:```
relayhost = smtp.sbcglobal.net
```This works, of course, because I'm on an ADSL from SBC and they are my ISP.

---

### Post by az on 2005-02-18
Right.  From what I read everywhere, it is supposed to be that simple.

I just want to be able to send out an email.

I will not post my conf, since all I have done is dpkg-reconfigure postfix and adding a smarthost and taking the postfix default interfaces (all)

All the mail I send out to anyone gets returned with that error.

I suppose it has something to do with authentification, but I really do not know where to look.  Should I be sending as a particular user?  From a particular email address?

---

### Post by grj on 2005-02-18
Who is your ISP and do they require smtp authorization to send e-mail? Many require authorization as a way to prevent spam from being sent.

---

### Post by az on 2005-02-18
Bell Sympatico.

How do you configure postfix to do authentification?

Most tutorials I find are about making a virtual host mail server.  I do not need that, so I do not know where to start.

---

### Post by Rottweiler on 2005-02-18
[QUOTE=azz]How do you configure postfix to do authentification?[/QUOTE]azz, give this a looksee: [http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html]("http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html")
  
  Please let us know if you get this licked, as it's something I'll need to figure out sooner or later.

---

### Post by az on 2005-02-19
Thanks for the link.  

I really think that my problem is more along the lines of this:
[http://www.postfix.org/TLS_README.html](http://www.postfix.org/TLS_README.html)

Which is covered in the chapter previous to the one you posted:
([http://postfix.state-of-mind.de/patrick.koetter/smtpauth/postfix_tls_support.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/postfix_tls_support.html))

It describes how to make your own certificate.  I cannot get this to work.  As well, I do not know if the certificate will be accepted.  I believe than my ISP authentifies in plaintext, so maybe just sending the STARTLS would be enough.  Regardless, since I am having such a bitch of a time making my own certificate, I would not know if it is because I made it wrong or if it just wouldn't work in the first place.

Anyone's help would be appreciated.

---

### Post by grj on 2005-02-19
I do not know whay ubuntu uses to send mail by default. If you do an
ls /usr/sbin/sendmail -l I believe that will tell you where sendmail is pointing.

man sendmail may also give you some help. Many of the mail commands work similar to below

sendmail -au username -ap password

---

### Post by az on 2005-02-21
Perhaps it is my ISP.  Should I be able to use something like gmail as a smarthost?  Is it as trivial as setting up an email client to send emails?

With my latest progress, I am able to send an email into the universe without it being returned.  It just never is received.

---

### Post by Rottweiler on 2005-02-21
What exactly have you done so far?
 
 I was suprised at you getting into the TLS stuff. I wouldn't think that would be required for simple authentication to an SMTP server. Most ISPs of my experience are still running everything in plaintext mode.
 
 Intended as a constructive comment: are you making this too complicated?

---

### Post by az on 2005-02-21
"are you making this too complicated?"

That is my though too, but I cannot seem to get a simple thing done.  Maybe my ISP does more than block port 25?  Like maybe anything that does not come from outlook or any other mail client is considered spam?  

What I have done so far is
1- try to modify the postfix configuration by hand allow it to talk to the outside world.  Started over by just using the package maintenance scripts (dpkg-reconfigure).  Added smarthost (my isp`s smtp)

2- I cannot send mails: I get the "Must issue a STARTTLS command first (in reply to MAIL FROM command")  Configured AUTH with
[http://postfix.state-of](http://postfix.state-of) mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html

Still no dice.  My mails seem to go out, but are not received or returned.

I need to send out an email through telnet to get a look at the error mesages.  With two young kids, some days I only get about five minutes to myself for this...

If my ISP is the issue, can I use postfix to send through a gmail account?


BTW, thanks for your help.

---

### Post by Rottweiler on 2005-02-21
[QUOTE=azz]"are you making this too complicated?"
 
 That is my though too, but I cannot seem to get a simple thing done. Maybe my ISP does more than block port 25? Like maybe anything that does not come from outlook or any other mail client is considered spam?[/QUOTE]Do you have a simple email client configured to send mail (thunderbird, outlook express, kmail)? Your postfix setup should just replicate that. If you're getting an error message about TLS that may mean they do indeed use secure authentication.
 
 You ISPs support pages about email client setup should be most helpful here.
 
 Don't know much/anything about gmail.

---

### Post by az on 2005-02-23
Right.  Using gmail as a relayhost can be done.  Here are the relevant lines:

/etc/postfix/transport
.****.dyndns.org :
****.dyndns.org :
* smtp:[smtp.gmail.com]:587

/etc/postfix/main.cf
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = ****.dyndns.org
relayhost = smtp.gmail.com
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
#smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
smtp_sasl_security_options =

/etc/postfix/sasl/sasl_passwd
smtp.gmail.com *****@gmail.com:*****
gmail.smtp.google.akadns.net *****@gmail.com:*****


I still cannot get any mail out.  
mail -s 'hello' ****@yahoo.ca

blablabla CTRL-D

It stays queued.  No errors.  (Whimper)

In looking for information on google, this thread came up first!  That must mean something (google: "postfix relayhost gmail")

---

### Post by az on 2005-03-07
Perhaps gmail has changed their protocols, or maybe I am just not smart enough.  I tried to use another ISP email server as a relay.  Now, all my sent mail leaves my machine (this is progrss) but gets "returned" to the isp user's email box.

I would think this is simple to fix, but I cannot find how do do it.

"This is the Postfix program at host xxxx.dyndns.org.

I'm sorry to have to inform you that your message could not be
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                        The Postfix program

<xxxx@yahoo.ca>: host mail.vif.com[216.239.64.153] said: 550 5.7.1
    <xxxx@yahoo.ca>... Relaying denied (in reply to RCPT TO command"

Header info:
Received:   	

    * from xxxx.dyndns.org (modemcable090.119-200-24.mc.videotron.ca [24.200.119.90]) by budah.vif.com (8.12.11/8.12.11) with ESMTP id j27BrgTV017531 for <yyyy@vif.com>; Mon, 7 Mar 2005 06:53:42 -0500 (EST)
    * by xxxx.dyndns.org (Postfix) id 3BAC5820E7; Mon, 7 Mar 2005 06:53:45 -0500 (EST)


I need to rewrite the from so that it thinks it is from the isp, and not postfix at xxxx.dyndns.org.  How do I do this?

I have looked up canonical maps, local header rewrite, address masquerading.  No dice.

---

### Post by Devinci on 2005-03-19
I had the same problem, when I switched to sympatico (man do they suck, they block port 25 and many webpages as well... )

So in order to be able to use postfix, here is what you need to do 

<rant>(I had to figure out by myslef, because when i called sympatico support, (i lied about using winxp and outlook just to get them to talk) I told them i needed to use a different smtp server than the one provided by sympatico. Guess what they cannot help you, they dont have information about it and when i asked if it was blocked he said no it isnt, but i dont have info (he was lying to the mofo).</rant>

so in /etc/postfix/main.cf, just use relayhost=smtp1.sympatico.ca

I know in their documentation they tell you to use smtphm.sympatico.ca, but I havent figured out how to set it up as a relayhost yet, and uite frankly I wont bother.  I will probably change ISP when their deal is over cause they truly suck... Well a first glance at their webpage's name should have ringed a bell...
[http://sympatico](http://sympatico).**msn**.ca/

---

### Post by garyng on 2005-03-19
I believe default installation of ubuntu postfix doesn't support TLS(even the programs are installed). you need to generate the certificate and modify main.cf as mentioned here :

[http://www.aet.tu-cottbus.de/personen/jaenicke/postfix_tls/doc/conf.html](http://www.aet.tu-cottbus.de/personen/jaenicke/postfix_tls/doc/conf.html)

---

### Post by AndrewV on 2005-03-30
I am on sympatico and have no problem with my warty/postfix server setup as a relayhost using their smtp servers.  If you are still having problems let me know and I will dig up my config.

Also, I have never had a problem with sympatico.  Well, other then them and microsoft turfing my passport account.  :-(

---

### Post by az on 2005-03-31
Thanks.

I switched to Videotron.  I have limited bandwith (and they block port 80!) and the website was moved to a real hosting company.  That solved my mail problem really quickly.

My basement is now silent - no more Pentium I humming away on the floor.

I would still be interested in getting mail off an Ubuntu system using Gmail.  That way, I would be able to get mail off any system, regardless of who is hosting.

Would you be able to try using gmail as a smarthost?

---

### Post by garyng on 2005-03-31
follow the link I gave, I have tried gmail. The only attention needed is the port, it use 587(?) for SSL.

---

### Post by dcostelloe on 2005-09-11
[QUOTE=AndrewV]I am on sympatico and have no problem with my warty/postfix server setup as a relayhost using their smtp servers.  If you are still having problems let me know and I will dig up my config.

Also, I have never had a problem with sympatico.  Well, other then them and microsoft turfing my passport account.  :-([/QUOTE]
 I am starting to setup postfix on symaptico I am a true newbie and followed this link to configure everything:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

But I can't get past postfix going to port 25 I need to use port 35 as my router handles the DNS. Also I use EasyDns for my dynamic updates.
I would greatly appreciate any help as the How Do does not work for me on port 25.


Also I followed this for sympatico:
[http://www.wormbytes.ca/articles/postfix-with-sympatico-relay](http://www.wormbytes.ca/articles/postfix-with-sympatico-relay)

Every thing is fixed now with mail etc works great!

Thanks

---

