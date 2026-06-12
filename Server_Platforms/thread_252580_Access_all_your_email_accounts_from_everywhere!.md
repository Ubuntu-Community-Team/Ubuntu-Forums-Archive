---
title: "Access all your email accounts from everywhere!?"
date: 2006-09-07
forum: Server Platforms
---

### Post by swiftman on 2006-09-07
Ok here is the deal...

I have 6 email addresses. I use Linux and Windows on multiple computers. Three of the email addresses support IMAP and the other three dont. I can have all of the emails forward to another place, however.

What I would like to do is start up an email server of some sort on my ubuntu server to collect all my emails from each address. I would then like to be able to use IMAP to view all my email accounts now being hosted on my email server. As an added bonus I also want to set up my email server to be a webmail server as well since I am often away from my computers in a lab somewhere. 

Now... Im sure im not the first one to have this problem/solution. I have googled this problem and havnt found a nice solution. Here is the million dollar question: Does anyone know if there is a nice way to do this?

Thanks,

Swiftman

---

### Post by mssever on 2006-09-07
My solution: Gmail. You can send and receive mail from any email address you own from your Gmail account. If you need an invitation, PM me with your e-mail address and I'll send you one.

Running your own e-mail server isn't easy, because if it's misconfigured, spammers will find out and use it to send spam, wherepon your ISP will drop your account for TOS violations. Remember, in the spam world, it's guilty until proven innocent.

---

### Post by mentecat on 2006-09-07
I think you could set up your mail server and retrive the mail from the various accounts using  [Fetchmail]("http://fetchmail.berlios.de/")

---

### Post by mannheim on 2006-09-07
I did something like this. My personal desktop in my office is on 24/7, so I am using it as a mail server. The software which I installed on this machine was: 

[LIST=1]
[*]postfix (to handle incoming mail)
[*]procmail (to filter my incoming mail, optional)
[*]spamassassin (to spam-filter my incoming mail, optional)
[*]dovecot (an IMAP server)
[/LIST]

postfix is (among other things) an smtp server; so I have my other email accounts forward all mail to "me@my.office.machine". I use procmail to filter this incoming mail and put it into mail folders in maildir format. I can then fetch my mail using any mail client, connecting to my dovecot IMAP server.

Because I am nervous about exposing an smtp server on port 25 to the whole world, I configured postfix to exclude connections from all ip addresses except the addresses of the mail servers which will be forwardig mail. Otherwise, I guess that "me@my.office.machine" might eventually be the target of a disabling amount of spam.

For this whole thing to work, you need a machine that has a static IP address and which is running 24/7, obviously. Otherwise, mentecat's suggesting is better: have your own machine fetch the mail, rather than have the other servers send the mail to your waiting server.

---

### Post by swiftman on 2006-09-07
Hmm, these all sound like good ideas. 

I just read up a little on fetchmail. But im still wondering if it is possible to use fetchmail to retreive my mail from my addresses and store it on the local machine preferably in seperate accounts, if not I can use filtering at the client level. Then use dovecot or any other IMAP or webmail server to view the mail on the fetchmail server?

---

### Post by mentecat on 2006-09-07
Yes, you can put the mail from different remote accounts in different local accounts. If you have 3 emails like [email]bill@yahoo.com[/email], [email]joe@gmail.com[/email] and [email]sam@hotmail.com[/email] and 2 local accounts max and jean you can create a .fetchmailrc file in /home/max with the instructions to retrive the mail from yahoo.com and gmail.com and a .fetchmailrc in /home/jean for [email]sam@hotmail.com[/email]

---

