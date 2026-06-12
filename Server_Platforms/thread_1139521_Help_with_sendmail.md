---
title: "Help with sendmail"
date: 2009-04-27
forum: Server Platforms
---

### Post by seamusandboo on 2009-04-27
Ok, I've installed Ubuntu 9.04 Server on a box I have at home with a LAMP stack. Everything works fine with the LAMP, but I'm unable to send mail using PHP's mail() function. So I installed sendmail and configured php.ini to use sendmail properly. I know my ISP blocks port 25, but it seems to me that sendmail is already configured to work with ports 25 and 587, as when I try to telnet to it locally on both ports it connects.

So I wrote a little PHP script to test sending mail with the function mail(). I tested it a couple times and I did not receive the mail. I then looked at the sendmail queue and the messages were there, but they could not be sent. Their status is:

Deferred: Connection timed out with mx1.hotmail.com.

Now, is this because sendmail is trying to send it via port 25? If so, how can I force it to send via port 587? If that's not the problem, what could it be then?

I'm also not sure if this is relevant, but when I telnet locally on my server to ports 25 and 587 it does connect, but when I telnet from another computer on my own network, it will not connect.

Any help would be appreciated.

---

### Post by HermanAB on 2009-04-27
Howdy,

Uninstall sendmail and install nullmailer.  Configure nullmailer to forward mail to your ISP mail server.  Nullmailer is soooper simpel.  All you need to configure is who you are and where to send the mail to.  Google for it.

---

### Post by mörgæs on 2010-10-19
I know that it is an old thread. Hopefully someone is reading. 

> **HermanAB said:**
> All you need to configure is who you are...

Does this mean my e-mail address or the IP of my local machine?

In which file do I write these settings?

---

### Post by mörgæs on 2010-10-20
I found out after a long night of experimenting.

The configuration is simply about identifying two machines: Mine (by the external IP) and the smtp machine at my internet provider. Could hardly be easier. The reason for the e-mail not being received was not Nullmailer.

I was trying to send e-mail from a PHP script, and it turned out that all e-mail was sent correctly but ended in the spam filter on receiver side. 

The solution is to be carefull stating the correct headers in the script. An e-mail sent from PHP can easily look like spam if judged by the (missing) headers. Sending through Evolution from the same machine gives a more well-formed e-mail which is more likely to pass the spam filter test.

---

### Post by CharlesA on 2010-10-20
Interesting deal about nullmailer.

I've been using exim to forward stuff to a gmail account and now I wonder if I can just use nullmailer to do that.

---

### Post by SeijiSensei on 2010-10-20
> **mörgæs said:**
> I was trying to send e-mail from a PHP script, and it turned out that all e-mail was sent correctly but ended in the spam filter on receiver side. 

The solution is to be careful stating the correct headers in the script. An e-mail sent from PHP can easily look like spam if judged by the (missing) headers. Sending through Evolution from the same machine gives a more well-formed e-mail which is more likely to pass the spam filter test.

If the PHP script is running under Apache, then the SMTP "envelope sender" will be www-data@yourhost.example.com.  Some spam-filtering software checks that the server's self-identification during the SMTP exchange ("HELO host.example.com") matches the hostname returned from a DNS PTR request using the server's IP address.  Residential and small business systems with dynamically-assigned addresses will routinely fail this test.  In general, if you must send mail reliably you should have proper forward and reverse DNS records for any SMTP sending host.

One easy-to-implement technique that can improve the odds your mail will look "hammy" is to adopt the "[Sender Policy Framework]("http://www.openspf.org/")".  SPF uses the generic DNS TXT record to announce the hostname(s) of servers sending legitimate mail for a domain.  All the domains I host that require automated mail from web applications have TXT records like this in their DNS zone files:
```

@    IN  SOA  domain1.name. support.example.com. (
     [...]
     IN  TXT  "v=spf1 a:smtp1.example.com a:smtp2.example.com ~all"
     [...]

```
which specifies that smtp1.example.com and smtp2.example.com are the legitimate SMTP senders for domain1.name.  Servers that respect SPF records either reject messages from servers not in the list or add extra spamminess points to them.  Messages sent from legitimate servers often get spamminess points deducted as well.

If, like me, you use sendmail and not Postfix, you can employ a fifth parameter in PHP's mail() function that can pass command-line switches to sendmail.  Adding something like "[font=courier][size=2]-f webmaster@domain1.name[/size][/font]' will set the envelope sender to that address, but only if the username the web server runs as (www-data on Ubuntu) is included in the file /etc/mail/trusted-users.  Postfix accepts the "-f" switch as well, but I couldn't tell from reading its documentation if the switch is actually implemented or just accepted for sendmail compatibility but ignored.  There also doesn't seem to be a Postfix equivalent to sendmail's trusted-users file.  It does appear you could use [VERP]("http://www.postfix.org/VERP_README.html") for this purpose which would create envelope senders like "webmaster+joe=example.com@domain1.name".

---

### Post by mörgæs on 2010-10-21
Whoa... sometimes I am pleasantly surprised by the quality of the answers here. Thanks.

I am not sure that I understand everything, but I will try to digest in small bites.

---

### Post by Chuck Ishman on 2010-11-26
> **mörgæs said:**
> I found out after a long night of experimenting.

The configuration is simply about identifying two machines: Mine (by the external IP) and the smtp machine at my internet provider. Could hardly be easier. The reason for the e-mail not being received was not Nullmailer.

I was trying to send e-mail from a PHP script, and it turned out that all e-mail was sent correctly but ended in the spam filter on receiver side. 

The solution is to be carefull stating the correct headers in the script. An e-mail sent from PHP can easily look like spam if judged by the (missing) headers. Sending through Evolution from the same machine gives a more well-formed e-mail which is more likely to pass the spam filter test.
"The spam filter", thanks for pointing that out! I just checked and found 2 of the emails I was looking for hiding in there. Totally forgot about the spam filter. Hopefully now this will no longer be an issue with getting my email from sendmail.

---

