---
title: "General Server Questions"
date: 2013-05-02
forum: Server Platforms
---

### Post by IngloriousGoblin on 2013-05-02
Alright, so I have been scouring the library at my university and online and everyone seems to be saying different things about a Mail server. My intention is to maintain a mail server at my house. I currently have a home network including an ftp, lamp, among others. I use OpenSSh as well. Do i need to host my own DNS and I am aware I need two, an authoritative and another. However, among all of the resources it is not clear to me what the differentiation is between the two type, or categories. My confusion could stem from asking the wrong questions. So, if anyone could correct my course of thinking here, I have configured the Mail server however I am unsure of how to obtain the FQDN and such because I have no idea of what I am doing. I have BIND 9th ed. at my disposal but i am unsure which parts apply. Anyway, Please help. Postfix, Courier, IMAP, and MySQL. If my spam filter choices affect I can add those. Also, TLS encryption.

---

### Post by daredent on 2013-05-03
Lets just start with the domain issues first.   No you do not _need_ to run your own DNS server.  In fact this will just complicate things from the start.  Your main concern for now is the mail server.

First you will need a domain.   Register a domain with any type of registrar you are comfortable with.   [http://www.godaddy.com](http://www.godaddy.com) or [http://netsol.com](http://netsol.com)  etc...

Now that you have a domain name .. you can add a MX record that points to your FQDN example .. mail.mydomainname.com

This record will point to your mailserver IP address.

You will also want to make sure your reverse DNS for the IP address you are using matches your FQDN.   You can speak to your current ISP in regards to this request.

I would start with these simple steps.

---

### Post by newbie-user on 2013-05-03
Hosting your own local DNS strictly to resolve hostnames within your home network is not a bad idea. For a home network, you don't need a secondary DNS, since the secondaries are more for redundancy. But, as daredent said previously, you don't really need to host your own DNS. I prefer [http://www.networksolutions.com]("http://www.networksolutions.com") over GoDaddy. I use both and GoDaddy is a lot more confusing to use.

Anyway, for the mail server, you need to know a few basics. There are three parts to setting up email service. The first part is the mail user agent (MUA). The MUA is the email client that you use to send/receive email. Email clients include Thunderbird, Evolution, Outlook, etc. The second part is the mail transfer agent (MTA). Postfix is probably the MTA you'll use here. MTAs are responsible for sending email from your mail server to the correct recipient mail servers. The third part is the mail delivery agent (MDA), which is responsible for sorting incoming mail and putting your email in your inbox. Dovecot is an easy MDA to set up.

The MDA and MTA will most likely be on the same server for small networks. Here are some tutorials:
Postfix - [https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")
Dovecot - [https://help.ubuntu.com/community/Dovecot]("https://help.ubuntu.com/community/Dovecot")

Sending email uses the SMTP protocol. Postfix does this.
Making the email available to your email client is done by Dovecot, using the IMAP or POP3 protocols.

---

### Post by IngloriousGoblin on 2013-05-31
Good news all, this helped immensely. I am now up and running and it is definitely not worth the hassle trying to set up a DNS. I was operating under very different assumptions but sometimes its best to just ask the question. Cheers.

---

