---
title: "Mail Server---Why is this such a pain?"
date: 2005-11-09
forum: Server Platforms
---

### Post by jstrubberg on 2005-11-09
Ok, this is beginning to get annoying.


Fresh Breezy server install.

Added the universe and multiverse repos, then updated and upgraded.

Installed courier-IMAP via apt.

postfix -e "home_mailbox = Maildir/"
postfix -e "mailbox_command ="

Can't use mail locally....
Connecting to the server from an evolution client fails everytime.  I get an IMAP error  and the client keeps asking over and over for an IMAP password.  No password I have ever used in my ubuntu career works.


I've been beating my head against this wall for four days now.  I've been through two online howtos on setting up a server for ISP use (which is NOT what I am trying to do) without any luck at all.

I don't need SSL...
I don't need virtual users or domains....
I will never have more than one mail domain...

I just need a farging mail server that will send and receive farging emails!

---

### Post by ranf on 2005-11-09
[QUOTE=jstrubberg]
Installed courier-IMAP via apt.
[/QUOTE]
I've also had a hard time trying to get courier working. By googling around I found `dovecot' mentioned somewhere. A breeze compared to courier.

---

### Post by LordHunter317 on 2005-11-10
Did you create the Maildir?  Courier won't work if there isn't a Maildir in your home directory.

And I think you meant postconf -e, not postfix anyway.

---

### Post by flurdy on 2005-11-10
[Try this howto]("http://ubuntuforums.org/showthread.php?t=40047&highlight=mail+server")

It works perfectly under hoary and with some tweaks under breezy ( i hope)

---

### Post by jstrubberg on 2005-11-10
Lord;

Yes, the Maildir's are in place.  Everytime I try this, I seem to stumble over getting IMAP authentication working.

My goal is to run a phpgroupware server.  Phpgroupware seems to do a very nice job out of the box, with the exception of email.  Therefore, a solid email service is step one.

Maybe I am just dense, but why in the world do we have (at a minimum) three services to deliver email?  Can anyone imagine a scenario where you would have a server receiving mail but not delivering it?  Or a machine you wanted to send mail, but not receive?  If not, then why in the world do we require this many software packages, each with it's own configuration, to do something as simple as deliver an electronic note to someone?

---

### Post by LordHunter317 on 2005-11-10
[QUOTE=jstrubberg]Maybe I am just dense, but why in the world do we have (at  minimum) three services to deliver email?[/quote]You don't.  Mail for your domain is recived via SMTP and placed in your user's mailbox.  They get that mail via POP3 or IMAP.

Since it's two seperate protocols, it makes sense for their to be two seperate daemons handling it.

> Can anyone imagine a scenario where you would have a server receiving mail but not delivering it?Any box doing mail filtering or relaying does this: it recieves mail and forwards it along, but isn't a final destination.  

>  Or a machine you wanted to send mail, but not receive?Most servers and all clients are essentially this. 

> If not, then why in the world do we require this many software packages, each with it's own configuration, to do something as simple as deliver an electronic note to someone?Because as I said, it's multiple protocols involved.  

What does courier say in the logs, exactly?  It ought to giving errors if there is a problem.

---

### Post by jstrubberg on 2005-11-10
You've sort of danced around my question, Lord.

WHY MULTIPLE PROTOCOLS???

We are handling the same data in the same manner, coming or going.   Requiring three protocols to deliver that data is absurd.

---

### Post by LordHunter317 on 2005-11-10
[QUOTE=jstrubberg]You've sort of danced around my question, Lord.

WHY MULTIPLE PROTOCOLS???[/quote]Because that's how the Internet is designed.  At this point, that should be a sufficent answer, really.

> We are handling the same data in the same manner, coming or going. But we're not.  The functionality required when I'm routing mail from it's source to it's destination mailbox **is not** the same when accessing the mailbox.  

Here's some things the routing (SMTP) needs to be worried about:[list][*]Control who can send/recieve mail through a node, by multiple mechanisms[*]Control where mail can be sent/recieved to[*]Deal with all sorts of failure conditions, including downed hosts, hosts that refuse to talk, etc.[list]Here's some things the end-user protocol needs to be worried about:[list][*]Sorting the mail into multiple folders/boxes[*]Deleting mail that's no longer needed[*]Searching the mail[*]User authentication only[/list]As you can see, there's really not that much overlap, besides the fact they deal with mail.

Which is why we deal with multiple protocols.  SMTP is only designed for writing mail.  POP3 or IMAP have features designed for end user needs and concerns.

At this point, those facts are irrelevant though, the protocols are the de facto standards and that's reason enough.

> Requiring three protocols to deliver that data is absurd.There isn't.  It's two at any point.  You just have multiple options on the end user protocols.

In any case, the configuration wouldn't be any less complicated even if you did have one service and one protocol to handle it.

---

### Post by jstrubberg on 2005-11-10
No, No No, No.

All servers do is route mail, period.  Whether that mail is travelling across the office or across the world, every server it touches is doing one of two things....

1.  Send it on to the next node

2.  Hold the transmission until the authorized client requests it, THEN send it on to that client.

Folders, etc are the clients job.  

Good lord, no wonder this is such a mess.  What exactly is the purpose of building client functionality into a communication protocol????

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=jstrubberg]No, No No, No.

All servers do is route mail, period.[/quote]No, that's not true, no matter how much you wish it to be.


IMAP is not a mail routing protocol.  It's a mail access protocol.  The mail isn't ever transported off the server, except in a temporary sense.  The server is the mail's final resting place.


> 2.  Hold the transmission until the authorized client requests it, THEN send it on to that client.

Folders, etc are the clients job. Yes, and that's ***why* POP3 and IMAP4** have support for folders, as they are ***client* protocols**.  And that's ***why* SMTP does not.**

I can't believe you actually don't understand the protocols are different because they're designed to do different things, and can't see the legimiate need.  Either you're ignorant or being obtuse on purpose, and I'm not sure which at this point.

> What exactly is the purpose of building client functionality into a communication protocol????Because how else are you going to store mail on a server?  The server **has** to know where to store it, or it can't do what I want.

Instead of ranting, actually reading on the protocols and their proper differences would suit you.  Having seperate protocols is perfectly valid and a good thing, as there isn't a lot of overlap between POP3 & IMAP & SMTP, besides the fact they all deal with mail.  Having my client access protocols support bounces is silly.

Having SMTP support folders is equally silly.  Hence, seperate protocols.

And even if there was one protocol, it's a red herring anyway, as your complaint is with how difficult it is to setup a mailserver.  One protocol wouldn't make it any eaiser.  Exchange is proof enough of that.

---

### Post by Mr. Electric Wizard on 2005-11-11
It's really a pretty easy concept.
SMTP is for server to server mail routing.
POP3/IMAP is for client access to mail server.

That's it.

---

### Post by jstrubberg on 2005-11-11
I understand the difference in the two protocols.

What I don't understand, what makes zero sense is why you insist on having the server do work that should be the responsibility of the client. 

Mr Wizard, it's not that easy.  If your statement were true, there would be no need for anything other than SMTP on the server.  Somewhere along the line, someone decided to draw a line between routing mail between servers and routing mail to clients.  Why, I can't imagine.  Every mail client on the planet has the ability to sort incoming mail, yet we have a program running server side to do the very same thing.  It's redundant, unnecessary and illogical.

Before you blow up again, stop and think.  Why should a box routing mail care if the next hop is another server or the last hop in the chain?

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=jstrubberg]I understand the difference in the two protocols.[/quote]No, you don't, because you wouldn't go on like this.  Your ignorance is not only obvious, it's quite overwhelming.

SMTP and POP3 or IMAP do not have total overlap.

> What I don't understand, what makes zero sense is why you insist on having the server do work that should be the responsibility of the client.**Because if I want to *store client's mail ON THE SERVER AND ONLY ON THE SERVER*, then there *MUST* be a mechanism to tell the server *WHERE TO STORE IT in a client-accessible fashion***.

Seriously, if IMAP is totally unnecessary, show me how to write a protocol that lets client access their mail on a remote server, keeps it on all the server at all time, and does it only over SMTP.  You won't be able to do it without extending SMTP to have most of IMAP's functionality, or writing a whole new protocol that looks a lot like IMAP.

>   Somewhere along the line, someone decided to draw a line between routing mail between servers and routing mail to clients.  Why, I can't imagine. Because they're not the same thing, no matter how much you wish it was.  SMTP has no concept of folders, mail deletion, or any other of many concepts that must be dealt with when dealing with the client.

> Every mail client on the planet has the ability to sort incoming mail, yet we have a program running server side to do the very same thing.No, you don't have to.  You may choose to, but you don't have to.  Postfix on it's own is totally incapable of delivering to anything other than one mailbox per user.  You're not required to run procmail.

> It's redundant, unnecessary and illogical.No, it isn't.  You've yet to show any of that's true, and I've shown many times there is actually little redundancy between them. 

The only issue is you refuse to accept the fact your abstraction is invalid and that routing mail between servers and handing mail to a client are actually distinct concepts that need to be treated in a distinct manner.

>  Why should a box routing mail care if the next hop is another server or the last hop in the chain?It doesn't, because SMTP stops at the user's mailbox.

After that, we need a protocol to mainpulate that fashion in the way the client desires, and we call that POP3 or IMAP4, depending on your needs.

---

### Post by dalani on 2005-11-12
[QUOTE=jstrubberg]

Maybe I am just dense, but why in the world do we have (at a minimum) three services to deliver email?  Can anyone imagine a scenario where you would have a server receiving mail but not delivering it?  Or a machine you wanted to send mail, but not receive?  If not, then why in the world do we require this many software packages, each with it's own configuration, to do something as simple as deliver an electronic note to someone?[/QUOTE]

I found this thread which confirmed what I suspected : all the tools needed are in a Linux box but scattered in disparate pieces. I sometimes have to wear the IT hat at work . We would like shared email on our small LAN. Right now we have a 'hardened' workstation that serves as sole POP account email recipient operating behind router and firewall with our ISP providing the rest. I can switch to IMAP but unfortunatly Outlook Eprxress does not allow sharing email from a centralized message store and Exchange seems the best bet excpet for the cost. Goal:  That all our LAN boxes can access and send mail with Inbox archived on one computer. Pretty much what our friend is trying to implement. Which is why  I cannot (with limited time) envision proposing something like Ubuntu as an out-of the box plug and play solution yet. So I'm watching this thread to see if it can be solved.


I had been wondering if there was a TURNKEY solution for this with a userfriendly distros like Ubuntu?  My only suggestion is perhaps using centralized GUI like Webmin might help configuration woes.

---

### Post by isaac_golding on 2005-11-13
[QUOTE=jstrubberg]

I just need a farging mail server that will send and receive farging emails![/QUOTE]

Did you try leaving the farging off of the e-mails?

I found when you send mail without a farging attached to them they work much better....


I'm so sorry but I just had to respond to this.  The messaage was just screaming at me to respond in such a manner.  Whats even worse is that have have no actuall constructive support for your problem and can only nod my head and state that I've been through similiar nightmares with "hard to configure & debug" server side apps.

---

### Post by jstrubberg on 2006-12-22
Well, I'm still trying to get this working.

First off, thanks to Lord and other for putting up with my....touchiness.  I've been noodling my way through linux and Ubuntu for about a year and a half now.  Unfortunately, either through my own lack of understanding, resistance from end users to relearn an application or lack of critical functionality I have yet to bring a single linux app into production use.  Patience tends to wear thin after successive failures.

I've really got my mind set on using a linux server to handle email and file sharing for my company.  So, here we go again. 

I need an email server capable of receiving email from the internet and routing it to client machines that connect with outlook express (yes, they are Windows clients.  One battle at a time).  A web client would be acceptable, but redundant.  This will not be a large rollout.  I don't expect to go over 15 users at any time over the next two or three years.

I've been through multiple howto's and so far they have all been extremely complex.  From what I have gathered so far, I need Postfix and Courier to do this.  I would prefer client connect via POP and SMTP  so that I am not dependent on a specific mail client.

I've burned an enormous amount of time on this project.  I think the largest impediments to Linux making a bigger splash in the world at large are it's HUGE requirement for specialized knowledge and the level of difficulty involved in getting even the most ubiquitous of applications up and running.

---

### Post by dannyboy79 on 2006-12-22
> **jstrubberg said:**
> Well, I'm still trying to get this working.

First off, thanks to Lord and other for putting up with my....touchiness.  I've been noodling my way through linux and Ubuntu for about a year and a half now.  Unfortunately, either through my own lack of understanding, resistance from end users to relearn an application or lack of critical functionality I have yet to bring a single linux app into production use.  Patience tends to wear thin after successive failures.

I've really got my mind set on using a linux server to handle email and file sharing for my company.  So, here we go again. 

I need an email server capable of receiving email from the internet and routing it to client machines that connect with outlook express (yes, they are Windows clients.  One battle at a time).  A web client would be acceptable, but redundant.  This will not be a large rollout.  I don't expect to go over 15 users at any time over the next two or three years.

I've been through multiple howto's and so far they have all been extremely complex.  From what I have gathered so far, I need Postfix and Courier to do this.  I would prefer client connect via POP and SMTP  so that I am not dependent on a specific mail client.

I've burned an enormous amount of time on this project.  I think the largest impediments to Linux making a bigger splash in the world at large are it's HUGE requirement for specialized knowledge and the level of difficulty involved in getting even the most ubiquitous of applications up and running.

i have read thru many of these posts and actually feel sorry for ya. i know what it's like trying to get something working everytime you try a how to it seems like it's a little differnt than the last and that maybe you'll understand this one but you just can';t seem to get ti to work. Anyway, I don't myself have an email server, the most I setup is using sendmail to send me emails about my system. I am using logcheck for this, all to send me rkhunter and chkrootkit logs so it was pretty easy. i just use hotmail and roadrunner email. back to the at hand question. i did a google search and found this. I read thru some of it and it seems like it would be pretty easy to follow so I figured i'd let you give it a try. 
[http://www.faqs.org/docs/gazette/mail.html](http://www.faqs.org/docs/gazette/mail.html)
i just hope it's not one that you have already tried. anyway, good luck and stick with it and you'll get it.

or if you're willing to pay for a book and read it, this looks promising: [http://www.bookpool.com/sm/190481137X](http://www.bookpool.com/sm/190481137X)

---

### Post by chrisfay on 2006-12-22
> **jstrubberg said:**
> 
I've burned an enormous amount of time on this project.  I think the largest impediments to Linux making a bigger splash in the world at large are it's HUGE requirement for specialized knowledge and the level of difficulty involved in getting even the most ubiquitous of applications up and running.

I sent you a PM. I'd be glad to help you get it going from start to finish....

---

