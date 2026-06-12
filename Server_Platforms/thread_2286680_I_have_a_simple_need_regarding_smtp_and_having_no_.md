---
title: "I have a simple need regarding smtp and having no luck."
date: 2015-07-13
forum: Server Platforms
---

### Post by morthawt on 2015-07-13
I have a google apps account and other domains that are using free redirection to my main email account. Then in google I have added "accounts" so that I can send email as if it comes from those domains so that I can actually reply. The problem is every time I send a reply, it has an unprofessional effect where the from address is the email address I use from my google apps. That not only looks really terrible but also gives other information about other addresses that should remain private from such people I am emailing with.

So I am looking for some kind of simple SMTP server that has TLS on it, so in gmail I can set the SMTP server for my reply emails being sent from so that it should have the true from address when the recipient gets it instead of my own highly personal address.

I would appreciate some help with this, I am not a linux expert. I have been using ubuntu on VPS' for a few years but I still have to follow guides for more involved things.

---

### Post by SeijiSensei on 2015-07-14
I need a bit more detail to understand the problem.

In email, there are two From addresses.  There's the From: header that is part of the email message itself, but there is also the "envelope sender" that indicates the origin of the message.  The envelope sender appears in the "Return-Path" header at the top of every message.  It's the email equivalent of the return address on postal mail.  Like postal mail, the external return address need not match the address on the content inside the envelope.

You can change the first of these yourself by telling the email client to use a different address in the From: field.  But you cannot control the envelope sender since that depends on the identity of the sending server itself.  Is this the one that is troubling you, because only that one has any relationship to the SMTP server you are using.  Most recipients will be entirely unaware of the envelope sender and see only whatever you have entered in the From: field.

---

### Post by morthawt on 2015-07-14
The return address is the one I want, but the from address in google shows as my login email I use for another google account to use the SMTP.

---

### Post by SeijiSensei on 2015-07-15
Well I don't think you could continue to use GMail if you intend to relay your mail through an SMTP server to change the Return-Path.  Otherwise you're looking at building a mail server and moving all your domains to it.  If it's that important to you, you might look into pre-packaged servers like iRedMail or Citadel.

I really don't see why you care that much about the envelope address.  No one sees it unless they expose all the headers in your messages.

Some of your issues seem related to using Google mail services.  If you are paying for Google Apps for Business, maybe you should drop a note to their support people?  If you're using free services, then you get what you pay for, I'm afraid.

---

### Post by morthawt on 2015-07-15
> **SeijiSensei said:**
> Well I don't think you could continue to use GMail if you intend to relay your mail through an SMTP server to change the Return-Path.  Otherwise you're looking at building a mail server and moving all your domains to it.  If it's that important to you, you might look into pre-packaged servers like iRedMail or Citadel.

I really don't see why you care that much about the envelope address.  No one sees it unless they expose all the headers in your messages.

Because it just looks bad. It shows up plain as day in gmail when people receive the email. Sure by default the replies go to the right address but they see a [email]bogusaddress@domain.tld[/email] for the from address and it looks just so bad. When I send emails I do not want any other addresses showing up. Privacy is important to me and when I reply from a specific email address, from a specific domain name I do not want to broadcast other private domains and email addresses simply because I use that gmail account for the SMTP. So I just wante a simple, secure SMTP server that I can set for my outgoing accounts added on the gmail page instead of using the gmail SMTP server which forces this idiotic email address to show up on everything I reply to.

---

### Post by SeijiSensei on 2015-07-15
I don't think there is any way you can have "a simple secure SMTP server...added on the gmail page."  You either need to set up a server for your own use, or accept the restrictions of using GMail.

---

### Post by morthawt on 2015-07-15
Yes you can, as I said I had to enter the SMTP details for gmail to use one of my other accounts because it is the only SMTP I have access to. If I run my own SMTP server that has TLS or SSL on it, then I can safely change the SMTP details to my server IP and use my specific credentials that I set on my server. My entire point is I have no SMTP server, which is why I am here hopefully to find some linux guru who knows what to apt-get install and give me some tips on how it would serve my purpose. Maybe if there is a good tutorial on the software that would help.

---

### Post by SeijiSensei on 2015-07-15
I suggested iRedMail and Citadel before.

Otherwise you could just install Postfix or sendmail from the repositories, but I think you'd be better off with a packaged solution.

---

### Post by morthawt on 2015-07-15
Thanks I will have to investigate those. I think I recall seeing something about CItadel having massive requirements that my VPS couldn't even do if it was new with nothing installed on it. I have 512 MB ram 1 CPU 20 GB total SSD space and it's running 3 websites, OpenVPN, secure FTP, LXDE and tightvncserver when I need it. So adding some comprehensive entire mail solution is not viable for me which is where my "simple SMTP server" request stems from. But I will look into both and see what I see. Thanks.

---

### Post by SeijiSensei on 2015-07-15
I'd bump up that memory space to at least a gigabyte.  A machine with 1 GB and equivalent or better specs in the other categories costs $10/month at [Linode](https://www.linode.com/pricing).

Just running sendmail or Postfix as a relay server won't take many resources, though.

---

### Post by morthawt on 2015-07-15
So postfix is a self contained SSL/TLS capable SMTP server? I thought it was some internal only thing that you can put external SMTP details into it?

---

### Post by SeijiSensei on 2015-07-15
Yes, it's a complete SMTP mail exchanger just like sendmail or exim.

---

