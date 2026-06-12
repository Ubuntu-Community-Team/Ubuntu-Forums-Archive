---
title: "Can't get past security issue with Google calendar"
date: 2010-08-24
forum: Security
---

### Post by Newbie2910 on 2010-08-24
An app of mine (in development) on Mono won't read or write to my Gmail calendar... I keep getting "Invalid certificate" errors.

I ran mozroots per the Security FAQ.  I also loaded them into the machine per these instructions:
[http://dotnetopenauth.net:8000/wiki/mono](http://dotnetopenauth.net:8000/wiki/mono)

But I think the problem is either Google actually sending a bad certificate, or a bug in Mono making it think the certificate is invalid.

Here's the error:

System.IO.IOException: The authentication or decryption has failed. ---> Mono.Security.Protocol.Tls.TlsException: Invalid certificate received from server. Error code: 0xffffffff80092012
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.validateCertificates (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.ProcessAsTls1 () [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.HandshakeMessage.Process () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMessage:Process ()
  at Mono.Security.Protocol.Tls.ClientRecordProtocol.ProcessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.RecordProtocol.InternalReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 

Help!

BTW my Mono/.Net code works fine running under Windows.

Using Ubuntu 10.04.

Thanks!

---

### Post by wacky_sung on 2010-08-25
Why you don't use your browser to login your gmail account to view the calendar and i am sure you will have no issue with it.

---

### Post by anomie on 2010-08-25
[QUOTE=Newbie2910]But I think the problem is either Google actually sending a bad certificate, or a bug in Mono making it think the certificate is invalid.[/QUOTE]

It's pretty unlikely that Google is feeding you a bad cert. 

Where did you get the CA root cert that you imported using the "mozroots" program?

---

### Post by uRock on 2010-08-25
> **wacky_sung said:**
> Why you don't use your browser to login your gmail account to view the calendar and i am sure you will have no issue with it.
That defeats the purpose when the OP is writing a code to connect and application to his/her calender. I would love to see an app that actually works for google calender in Ubuntu.

---

### Post by Newbie2910 on 2010-08-25
Thanks all.

Yeah I  can access my Gmail calendar just fine with Firefox.  Also, this code will work fine on Windows just not Ubuntu.

uRock, from your comment it sounds like other apps have the same issue?

---

### Post by uRock on 2010-08-25
> **Newbie2910 said:**
> Thanks all.

Yeah I  can access my Gmail calendar just fine with Firefox.  Also, this code will work fine on Windows just not Ubuntu.

uRock, from your comment it sounds like other apps have the same issue?
I am sure that Thunderbird for Windows with the Lightning extension works fine with google calender, but the Ubuntu update for Thunderbird killed Lightening about a month ago, so I am back to pen and paper for date keeping.

---

### Post by Newbie2910 on 2010-08-25
*Sigh*

I need an online calendar that I can put a lot of stuff into... that has an API for CRUD operations.

Yahoo doesn't have their API released, nor does Live (and I prefer to stay away from MS anyway), 30Boxes doesn't appear to have an API (that I can find)... so Google seemed like a good choice.  Works fine on my Win boxes but I soon need some calendar repository to work with Linux.

---

### Post by cariboo on 2010-08-26
@Newbie2910, it may be an idea to start a thread in [Programming Talk]("http:///ubuntuforums.org/forumdisplay.php?f=39"), as there may be someone there that has run into the same problem.

---

### Post by Newbie2910 on 2010-08-26
Thanks, I did but didn't really get anywhere.  I will retry though.

---

### Post by migueldeicaza on 2010-09-08
The solution to your problem is documented here:

[http://www.mono-project.com/UsingTrustedRootsRespectfully](http://www.mono-project.com/UsingTrustedRootsRespectfully)

---

### Post by uRock on 2010-09-08
On a good note, the OP can install the new release of Thunderbird onto the system and have full functionality of Thunderbird with the Lightning extension.

Newbie2910, if you want me to explain the steps for installing the latest version of T-Bird w/Lightning, then please respond here and I will take a minute to type up the steps. It is pretty easy.

uRock

---

