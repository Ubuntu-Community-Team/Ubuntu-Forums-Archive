---
title: "Mail Server"
date: 2007-08-04
forum: Server Platforms
---

### Post by fireworksshow on 2007-08-04
I'm new to the server branch of linux. i have mainly just used it as i desktop. I now have to setup a mail server for my rather large local are network. I have a few questions.

Do i have to have a domain name to succesfuly setup such a server?

How would the e-mail addresses look like? user@<ip>??

I'm givig this [how-to ]("https://help.ubuntu.com/7.04/server/C/email-services.html") a try.

---

### Post by Alein on 2007-08-04
The short answer is "Yes".
 
Your mail must originate from and be delivered to [EMAIL="you@adomain."]you@adomain.[/EMAIL][com | org | net] ,etc. This does not mean you have to host the domain yourself. You can coordinate with your ISP and they can host the domain. You can then build your mail server and use the ISP as an upstream mailhost. Your server sends and receives mail through the ISP's mail servers and the whole thing is transparent to your clients. Hope this helps

---

### Post by hockey97 on 2007-08-04
What I heard, and seen, was that you don't have to have a domain name for it, it will look like this root@localhost , that's for local network.

you would have to config it, to root@external ip 

for example: admin@192.168.5.4  

how-ever I hear that if you don't have a domain name  some ISP mail server's won't bother sending mail to you from their user's.

some say aol has such stuff.

they do that becuse they think it could be a spam type of thing or hack.

like it's not a secure thing to do.


that's what I heard. My friend showed me how to set it up.

but my advice is to get a domain name for your mail server and 

make the mx records, for the mail server, that's how you connect the Domain name to your server ect.

---

### Post by Mr. C. on 2007-08-04
Without more information about your requirements, its hard to answer your questions.

You can use a private local domain if you want, even a non-existent one.  The key points are that your clients know which mail server to use, and your mail server knows which mail is considered local (eg. not to be relayed to some other domain / server).

How your addresses will look depends on how you setup your server.  Probably the most natural for users is standard user@domain type addresses.

If you don't have a domain, how are outsiders supposed to reach you ?  Eg.  Your server handles mail for user@domain.  Now, let's say I want to send you email.  How do I find you?  Either the domain must exist and has either an MX record or an A record, or you specifically need to give me your IP address and I have to set up a transport table to know to send email to your server(s).  I dont' think you want to ask all mail server admins in the Internet to setup specific transports!

So, if you want a traditional send/receive MTA, you need a domain name whereby other's can reach you, and other's can perform some basic validations on mail sent from your servers.

MrC

---

### Post by fireworksshow on 2007-08-05
Thanx for you're help guys I'll try to get a domain or find a workaround for this.

---

