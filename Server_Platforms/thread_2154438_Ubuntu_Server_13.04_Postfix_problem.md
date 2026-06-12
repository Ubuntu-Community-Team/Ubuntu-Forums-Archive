---
title: "Ubuntu Server 13.04 Postfix problem"
date: 2013-06-14
forum: Server Platforms
---

### Post by Bradford1040 on 2013-06-14
I am hosting my own websites and mail server, I have done most everything on this setup with Google searches and figured everything out.

But this one has just stumped me for weeks now and I really need to get it up and working correctly, 
I have 3 or 4 virtual Apache sites all working 100% and can receive mail for them all butt I want to be able to send mail from each .com and I keep getting
stuck with only sending from the main domain my server is running from! I have my web/mail server running on hostname "webserver.example.com" of coarse
example.com is not my dot com but was not sure if my real one would violate the TOS of the forum some how. Now the "webserver" part was a pain to get around as well but
figured it out with a bit of mapping to get it to receive/send mail on "[EMAIL="user@example.com"]user@example.com[/EMAIL]" instead of "[EMAIL="user.webserver@example.com"]user.webserver@example.com[/EMAIL]". 

But I still want too figure out how to get @example + @example1.com + @example2.com + @example3.com with the user name as well!
 
I know it can be done because I had it working before granted there was no security installed and the server was a open book to whomever knew how to just type in
stuff to access pages that weren't clickable links, and I had a real problem a few days after it was up and open as you should expect "duh on me"
 
So if anyone has a good setup page for this exact thing or is willing to give me a hand over the next few days of forum life Please! Help, if you can Thank You in advance!

---

### Post by SeijiSensei on 2013-06-15
Like physical mail, email has two different From addresses.  One is the "envelope sender" which is the address used during the SMTP exchange. It's the email equivalent of the reply address on the outside of the envelope on a piece of postal mail. The other is the sender whose address appears in the From: field within the message itself.  That field is entirely manipulable; you should be able to include a "From: [email]user@randomdomain.com[/email]" in the message headers in the software you are using to compose the message.  Manipulating the envelope sender is a much more difficult task.  I can do it using a "[genericstable]("http://www.madboa.com/geek/sendmail-genericstable/")" in sendmail; I don't know how to handle that in Postfix, though, since I don't use it.

If you have multiple domains, and you end up implementing a solution like this, you should consider adding [SPF records]("http://www.openspf.org/") to each domain's DNS zone file so that receiving servers can verify that smtp.example.com is a valid sending host for randomdomain.com.  You should also ensure that the server's IP address reverse-resolves to its canoncial hostname.  Both these things improve the chances that your message won't be viewed as spam by remote SMTP hosts.

---

