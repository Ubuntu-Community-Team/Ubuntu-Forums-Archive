---
title: "Postfix..."
date: 2008-01-10
forum: Server Platforms
---

### Post by hockey97 on 2008-01-10
I can't setup  postfix right to have postfix use the maildir I made rather than the default one which is in /var/mail/user.

and how could I manage 2 domain's mail.

I have postfix setup right with mysql. 

the only problem is mainly that the mail dosen't get delivered in where I want it. Postfix send is to /var/mail/user.   I wanted it to be in /home/user/domain/user .

How can I mainly change the maildir  to what I want it stored?

I have courier installed.

I can recieve mail to postfix in /var/mail/user the default setting.

I can't send e-mail to well know e-mail providers.

can you please give me any advice on what to do??

Thanks for your time.

---

### Post by ariek on 2008-01-10
Could you please describe first what you are trying to achieve? What is your goal, for one thing?
Secondly, do you have any experience with mail servers? Postfix is a great mail server, with many options, and configuration possibilities. Try to start with the least comlpex config possible.
There are a lot of related howtos at [www.howtoforge.com]("http://www.howtoforge.com").

Good luck.

---

### Post by Swmmrman on 2008-01-10
Most well know emial companies will bounce e-mail from a dynamic ip(90% of us have one) What you will have to do is find out what your ISPs mail server is.  You should be able to setup postfix to send it to them for forwarding after which time it will work normaly.

---

### Post by hockey97 on 2008-01-10
well ok I already have postfix setup I have it using mysql database to support virtuial maps  and mainly can lookp.

I done a test I can send mail from aol.com to my postfix mail server but I edited in main.cf file to make a virtuial mailbox dir to be in/home/user/domain/user .  but what it does is that it some how ignores the config I made to send the mail to that /home dir area and still send the mail at the default area which is /var/mail/user.

I have postfix up and working.  

What I mainly want to do is make a website in php and display e-mails .

I thought if I could setup postfix to some how store e-mail in a mysql database or have mysql store info to where the mail will be stored and would retrieve the e-mail.

I mainly want to provide my user's to have an e-mail account on my website.

I know php and html .  I mainly thought if I can get mysql to store user info and their e-mails then it would be easy to use php to display that e-mail on my website for the user to see their e-mail.

how do you do that thing with my isp???

do you think I can do that without any extra fees to forward it to my isp mailserver then to elsewhere??

---

### Post by MJN on 2008-01-11
It sounds to me like you are trying to reinvent the wheel.
 
Why not use a common, and well-tested, solution like Postfix/Dovecot (or any other IMAP server)/Squirrelmail in order to give you a solid mail platform will full remote access, including via webmail?
 
To save HermanAB the effort (;-)) you could also look at Citadel, particularly if you want it up-and-running yesterday, and with other features besides.
 
Don't take this the wrong way, but if you're falling at the relayhost hurdle the chances are slim that you'll be able to get a roll-your-own PHP mail access frontend working. Don't make life hard for yourself when there's little or no advantage in doing so! In fact, in case you are a PHP wizard consider contributing to a webmail frontend such as Squirrelmail and enable others to share the mutual benefit.
 
Mathew

---

### Post by HermanAB on 2008-01-11
If you wish to run a server at home, then you have to get a 'server' account from your ISP.  For about $10 more per month, your ISP will give you 2 or more static, public IP addresses, remove the port blocks and usually also give you much more bandwidth.  You can then buy a domain at Godaddy and set up their DNS to point to your server, after which you are *really* on the internet.

---

### Post by hockey97 on 2008-01-11
I have a domain already I plan to have 2 websites going one my company and the other a social website with e-mail capability.

I can send e-mail to my postfix mail server but I can't send it to aol and stuff.

right now my server is off.  Right now I am trying to start a website as cheap as possible if I can make money off the website then I will plan to.

I already have the one domain purchased. the website and stuff work.

it's not working becuse my server is off.  I when I say about php I am not inventing the wheel .  I mainly wanted postfix to dump the e-mail to mysql databases  if I can't.  then I will want to then try and make postfix to store each user and their mailbox dir in mysql database then I can open the files with php. 

would that mean I would have to do some programming with postfix to get those done??

squirlmail is a php thing that connects to the maildir and retreives it.

I can mainly do that myself. I mainly want to do that myself so I can design the looks of it myself.

---

### Post by envygeeks on 2008-01-11
> 
I can send e-mail to my postfix mail server but I can't send it to aol and stuff.


Call AOL and ask them to verify an IP ban and reverse DNS. Also check out Postmaster documentation. [http://postmaster.aol.com/selfhelp/index.html](http://postmaster.aol.com/selfhelp/index.html), verify you have port 25 open and that your ISP allows it (I'm sure they do if you are trying to setup a mail server). A lot of ISPs now block domains that don't reverse correctly.

---

### Post by MJN on 2008-01-11
> **hockey97 said:**
> I can send e-mail to my postfix mail server but I can't send it to aol and stuff.

That will likely be the dynamic IP aspect as Swmmrman already said - you need to look at using the [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") directive with your ISP's outgoing mail server.

> I when I say about php I am not inventing the wheel . It sounds to me like you are - you are intending on coding a means of enabling users to access their e-mail using a webmail interface. In doing this you are requiring the implementation of a method of accessing user's mail, handling the sending of mail, and presenting this over HTTP for use in a browser. That's the Squirrelmail project in a nutshell (but with a whole load of other features besides).

> I mainly wanted postfix to dump the e-mail to mysql databases  if I can't.  then I will want to then try and make postfix to store each user and their mailbox dir in mysql database then I can open the files with php.So you're sidestepping POP and IMAP and introducing your own mail storage and retrieval environment? How will 'standard' e-mail clients (e.g. Outlook, Thunderbird etc) interact with this mail storage? Or will you not let users use a client of their choice?

> squirlmail is a php thing that connects to the maildir and retreives it.Yes, and it's a model that works very very well. Furthermore, it's fast, reliable, secure and feature-packed too.

> I can mainly do that myself. I mainly want to do that myself so I can design the looks of it myself.If appearance is your main priority then just skin Squirremail - [Nutsmail]("http://www.nutsmail.com/") have some good examples of what's achievable.

Mathew

---

### Post by hockey97 on 2008-01-11
How it supposed to look is important. I have the website still designing the art. but  I mainly what the e-mail service to blend in with the over all website. If it dosen't blend in then it would look odd. How would you like to see hotmail  and aol have the same art or have squirrel mail.

I am mainly going for a professional look and a look that one one could have so my website dosen't look like some amature or hobbiest made the site.
 
that's my main concern.  If I can have mysql take the e-mails or at least store where the mail dir is for each member then with php it won't be a problem.

the main problem I have right now is that postfix still uses the defaul location for maildir.

---

### Post by MJN on 2008-01-12
Sigh. You're not listening to what I'm saying but that's fine - each to his own.

Good luck anyway.

Mathew

---

### Post by hockey97 on 2008-01-12
I am using  Postfix/Dovecot /. It sounds like you think I am planning to make my own mail server??

I want postfix to interact with mysql. php already can interact with mysql.

I want to mainly create my own web page where I can display the e-mails in . If I can get postfix to send the mail to mysql it would be great if not then I will have to at least put the maildir where mail is stored in mysql and use that to have php able to display. 

I am doing noting to mod the mail server nor make a mail server.

I just want  to create my own php to mainly have a user able to check and send e-mail.

that's it. squirl mail is written in php and if I used that it will set off the over look.

I mainly don't want to use a 3rd party scripts to show the e-mails to the users becuse it would look odd.

if hotmail or aol  use squirl mail it would look odd in the overall layout.

the page where I want the users to see their e-mail I also want to show my ads and also have button links to other applications I will make.

so I am not reinventing the wheel. I mainly want to create my own wheel becuse so that wheel will fit nicely on my car.

---

### Post by MJN on 2008-01-13
I know exactly what you want to do - create a PHP 'webmail' frontend for your users to access their e-mail.

What I am saying is that this is a mammoth task and one which such projects as Squirrelmail have been working on for years - there is more to a functional webmail system then simply allowing users to read their mail.

I understand that the aesthetics is important to you - and that's fine - but I am trying to tell you that as you are PHP savvy you would have no problem in skinning (or even rewriting) Squirrelmail to look exactly how you wish and making it fit seamlessly into your website. My ISP offers a webmail service to those customers that desire it and I happen to know it uses Squirrelmail - but you would have a hard time knowing this from how it looks as it appears nothing like the standard Squirrelmail appearance, layout and functionality.

I don't know why I'm trying so hard to convince you, but part of me does feel a responsibility to warn you that based on your questions thus far what you are trying to achieve is *considerably* more difficult than you think.

This will be my last post on the topic as the choice is yours at the end of the day.

Mathew

---

