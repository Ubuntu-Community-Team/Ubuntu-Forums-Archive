---
title: "Help with setting up Citadel mail server with Thunderbird front end"
date: 2008-11-27
forum: Server Platforms
---

### Post by greavette on 2008-11-27
Hello,

I've been successful in setting up Citadel in a Virtual appliance in VMware on Hardy 8.04.1...at least it is working and I can send and receive mail.  I've connected Thunderbird to the mail server via Imap.  Some of my users (accounts) within Citadel have web email access and some don't.  When I use webcit, messages can be sent between all users without error.  I'd like to do the same with messages from users who use Thunderbird.  

In Webcit I need to just put in the users account name in the 'To' field and Citadel knows how to send the message.  Messages sent from webcit to a user using Thunderbird get there without a problem.  But in Thunderbird, I get an error since Thunderbird can't send a message back without a FQDN.  I don't know what to put in for a FQDN to my Citadel server?  

I've read through their admin guide, but I'm just not seeing how to do this from the guide.

I've seen some people here on the Ubuntu forums often mention Citadel so hopefully some kind person can point me in the right direction on what I should read to setup this up properly.

Thanks in advance for any help you may provide.

---

### Post by greavette on 2008-11-29
Does no one use Citadel with Thunderbird?  I was hoping someone who has a lot of Citadel knowledge might know how I set my server up properly.

Thanks!

---

### Post by cbaron0185 on 2008-12-09
greavette,
I just wrote a similar post then I came across yours. I am having the same issue I can not get it to use the FQDN either and their documentation is very thin in setting up the email portion. 


> Hey Everyone,

I have setup a Citadel server on Ibex, but I have a question about the setup. I have not seen to much information out there about citadel, the setup is really easy but I can not figure out how to tell the server to send it using my domain instead of the hostname name. for example:

I setup thunder bird and I can send out the email using [email]user@domain.com[/email]
When people go to reply to my message the responding message says they are sending it to me at user@server, instead of [email]user@domain.com[/email]

Does that make sense was I clear?
I am just not sure if I missed something when I set up the Citadel or I am missing a DNS entry.

Thank you everyone.


That is my post, is that the same problem you are having? 

Thank you

---

### Post by cbaron0185 on 2008-12-23
greavette,
What are your hostnames on the server? are they all FQDNs? 

Thank you

---

### Post by HermanAB on 2008-12-23
Sounds like your DNS is misconfigured.  Ensure that the mail server has a FQDN hostname and that it has A, PTR and MX records.

---

### Post by Fooshnik on 2009-12-14
Not sure if this is the exact same problem, but in webcit check the alias under the user account. For some reason on some accounts existing before Citadel installation they can show their address as "User@Servername" instead of "user@mail.yourdomain.com".

---

