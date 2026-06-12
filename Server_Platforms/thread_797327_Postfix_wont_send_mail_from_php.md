---
title: "Postfix wont send mail from php?"
date: 2008-05-17
forum: Server Platforms
---

### Post by Johnsie on 2008-05-17
Hi I'm having some problems  getting php to send mail. I've installed postfix from the repository and am using apache2 amd php5 from the reposiory.

My php is as follows:

> 

<?php
$to = "steekyjim@yahoo.com";
$subject = "Test mail";
$message = "Hello! This is a simple email message.";
$from = "support@steeky.com";
$headers = "From: $from";
mail($to,$subject,$message,$headers);

?>


In theory this should send an email out but nothing is happening. I have postfix configured as "Internet Site"

Is there any way I can check to see what's going wrong?

---

### Post by Johnsie on 2008-05-17
post no longer relevent

---

### Post by Monicker on 2008-05-17
Check your postfix and apache logs.  If there is a problem with the php you should be seeing an error in your apache error log.


Also, how are you running this?  If you do the following following from a command line, do you get a specific error?

```
php -f script.php
```


You may need to install the php cli package for the above to work.

---

### Post by Johnsie on 2008-05-17
The script seems to be working ok. I can send internal emails within my domain with this script without any problem... My server just cant seem to send anything to email addresses outside my domain.

---

### Post by Johnsie on 2008-05-17
It works ok when I select "Internet Site with smarthost" and enter my isps smtp. But I don't really want to use my isps smtp.

---

### Post by Monicker on 2008-05-17
> **Johnsie said:**
> It works ok when I select "Internet Site with smarthost" and enter my isps smtp. But I don't really want to use my isps smtp.

You probably don't have a choice.  Its very common for an isp to block any outbound smtp connections which are not going to their mail servers.  This is in large part due to many viruses which attempt to spread via email.

---

### Post by solcott on 2008-05-17
On some internet providers using your own SMTP just won't work outside of a LAN.

For example I'm on RoadRunner cable in the US and unless I relay everything through my ISP's SMTP my mail isn't going anywhere unless it's from a local box addresses to a local box.

Try doing this from the server:
```

telnet localhost 25
EHLO hostname.domain

```

And this from some machine connecting to the server from internet land:
```

telnet hostname.domain 25
EHLO hostname.domain

```

If you get a response connecting to localhost and not from internetland port 25 is being blocked.

/EDIT: Oh, shucky-darn Monicker beat me to the punch :-)

---

### Post by Johnsie on 2008-05-17
do I need to make port 25 accessible from outside my network?

I just tried running a windows smtp server(argosoft) to see if it was soemthing wrong with my linux machine. When I tried to send an email I got a link to a google page with the following message: 

> 
In order to prevent spam, Gmail refuses mail when the sending IP address does not match the sending domain. To send mail from your server to Gmail, we suggest using the SMTP relay provided by your ISP. Please note that we are unable to whitelist IP addresses or otherwise make exceptions at this time.


---

### Post by solcott on 2008-05-17
Yes, it needs to be accessible from outside of your LAN, unless all of the mail happening is going to be internal.

The error that GMail is giving you is a problem with reverse DNS.  For example the IP 1.2.3.4 reversing to residentialcustomer.someisp.com instead of 1.2.3.4 reversing to the-domain-you-are-trying-to-send-from.com

It seems that your options are either to smarthost through your ISP, or not be able to send mail to anyone with a properly configured mail server (and by that I mean behaving pretty much the same way that the GMail mail server just did)

---

### Post by Johnsie on 2008-05-17
From inside the lan

> john@st4:/var/mail$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 st4 ESMTP Postfix (Ubuntu)
EHLO gmail.com
250-st4
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
421 4.4.2 st4 Error: timeout exceeded
Connection closed by foreign host.


I ran a "relay test" from [http://www.abuse.net/relay.html](http://www.abuse.net/relay.html) and got the following results:

> 
Connecting to *****.com for anonymous test ...

<<< 220 st4 ESMTP Postfix (Ubuntu)
>>> HELO [www.abuse.net](www.abuse.net)
<<< 250 st4
Relay test 1
>>> RSET
<<< 250 2.0.0 Ok
>>> MAIL FROM:<spamtest@abuse.net>
<<< 250 2.1.0 Ok
>>> RCPT TO:<securitytest@abuse.net>
<<< 554 5.7.1 <securitytest@abuse.net>: Relay access denied



I also tried dusing telnet to send an email:

> john@st4:/var/mail$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 st4 ESMTP Postfix (Ubuntu)
helo steeky.com
250 st4
mail from:john@steeky.com
250 2.1.0 Ok
rcpt to:steekyjim@gmail.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
testing
.
250 2.0.0 Ok: queued as 5B1BD43E91



So from what I can gather:
 -My smtp server is can be connected to from outside
 -It wont allow outsiders to relay mail (good)

---

### Post by solcott on 2008-05-17
in the EHLO command you wouldn't use gmail.com, you would use whatever your hostname is.  The command basically says to the server "Hello server, I'm going to be sending some mail from {domain}"

So lets say you own somedomain.com the command would be EHLO somedomain.com

The 421 error on the end means that service for the domain you are trying to send mail as (in that log you posted it would be gmail.com) is not available.

---

### Post by Johnsie on 2008-05-17
> 
220 st4 ESMTP Postfix (Ubuntu)
EHLO *****.com
250-st4
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN




So from what I've posted you can tell that I cannot run an smtp server on my machine?

---

### Post by solcott on 2008-05-17
That log coming from localhost is the way it should look, if you get the same thing connecting through the internet instead of LAN everything is set to go.  If get nothing connecting from internet, that means 25 (going out) is blocked.

You can run a SMTP, it's jsut that the functionality will be best if you use the smarthost feature.  To connecting clients they will see that they are connecting to you, not your ISP.  If 25 is not blocked you can run SMTP and relay yourself instead of using a smarthost, *but* most mail servers will refuse to accept mail from you.  Using a smarthost your mail will go through just fine.

It's really just an articifial limitation that ISP's put on their clients to "reduce spam" / make the clients pay for an improved service that removes that limitation.

---

### Post by Johnsie on 2008-05-17
Thanks for your help. I think I'll just stick with smarthost untul I get more traffic.

---

