---
title: "POP3/IMAP/SMTP Setup?"
date: 2010-03-30
forum: Server Platforms
---

### Post by dgohn on 2010-03-30
I recently stopped using GoDaddy.com's name servers for my domain and on the registrar side input the two nameserver addresses (ns1.mydomain.com & ns2.mydomain.com) into their system.  Thats all working good and dandy.  However, I had my [email]admin@mydomain.com[/email] email address with them using their mail servers and stuff and had all of my settings set up in outlook to retrieve my mail from their servers.  Well since I changed from their name servers to my name servers my mail is no longer working.  I am assuming that is because once you take responsibility of the name servers they no longer host your e-mail?  Or is there something I am missing?  If this is so, can anyone point me in the direction of a detailed setup tutorial to get my e-mail working again on the server side.  I have found several postfix and dovecot tutorials but to no avail as I just wind up breaking everything and having to undo it all.  It all seems pretty complicated to be honest.  Any help, suggestions or ideas are welcomed and greatly appreciated.  Also... would it help by keeping my 2 name servers on the godaddy side of things but also as a third NS add one of theirs?  would that re-enable my email?  Hopefully someone has some experience with this and can help me along.

Thanks!!!

---

### Post by sheic on 2010-03-30
Just Godaddy can answer some of your questions, contact their support.

Just in case they'll still host your mail server, maybe you're just missing the MX record in your DNS?

Test your domain with [www.intodns.com](www.intodns.com)

If you have to host your mail server and you don't have the experience to configure everything, checkout webmin and virtualmin to set it up with webmail and everything.

---

### Post by HermanAB on 2010-03-31
Test your DNS with 'dig' and ensure that you have A, MX and PTR records.

If you want to run your own mail server, use Citadel.  It installs in about 20 minutes and it basically 'Just Works'.  It can do absolutely everything and is very easily configurable.  

There are howtos on my website - been using it for about 10 years with hundreds of users and many hundreds of Gigabytes of mail.

---

### Post by kewlrichie on 2010-03-31
You would need have a hosted MX record with a hosting provider so your domain (mywebsite.com) knows where to resolve to your new mail server. Also your ISP has to not have port 25 blocked or you wont be able to receive mail. If your doing this at home there is work around for ISPs that block 25 port, just do a quick search on the forums or google and there are services like no-ip.com has a service called mail reflector [http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html]("http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html")

---

### Post by cosborne on 2010-04-26
Hi there

I have just done the same thing. In the DNS control panel, you need to set your IP address. For the mail servers, replace the existing goDaddy server details with @ - Viola!

Christopher

---

### Post by windependence on 2010-04-26
Just why you would ever want to purposefully go to your own DNS is beyond me other than to learn, and you can do that on a local DNS server quite well. 

To answer your question, your DNS setup will not affect your mail with them at all. Of course, now YOUR DNS server must accurately resolve the IP address of GoDaddy's mail servers to work correctly. DNS is not something to take lightly. If you don't know what you are doing, you can really screw things up for yourself. This is why I cannot understand why you would want to do this.

-Tim

---

