---
title: "help with ssl_error_bad_cert_domain error on portal behind security gateway"
date: 2010-06-01
forum: Server Platforms
---

### Post by greavette on 2010-06-01
Hello,

I'm hoping I can get direction on what I need to do with a problem I am having with our Adito (OpenVPN-ALS) portal I've setup behind our Untangle security router.  

Here's what I've done (still setting this up so I'll use example names):

    * We have bought a domain name called example.biz.  We've installed an SSL certificate from Go Daddy on Untantle (our security router) and can now access our router's administration panel using gateway.example.biz.
    * I've now created an Adito (OpenVPN-ALS) server in a VM behind our Untangle router and I have a port forward rule in Untangle to get to this VM on port 8843.
    * I was hoping that by installing an SSL certificate on Untangle this would cover our our connection to the portal, but I was told that I would need another ssl certificate on the portal itself.  I've done this now and have installed a certificate on our portal using a hostname (CU) of portal.example.biz.
    * From within our network, I can access our portal server using [https://portal.example.biz](https://portal.example.biz) and I do not receive a certificate warning message.
    * From outside our network I would use [https://gateway.example.biz:8843](https://gateway.example.biz:8843) and the portforward rule would point to our Adito server.  The problem though is from outside our network, I receive the following error messages:
          [INDENT]o "gateway.example.biz:8843 uses an invalid security certificate." [/INDENT]
          [INDENT]o "The certificate is only valid for portal.example.biz"[/INDENT]
          [INDENT]o (Error code: ssl_error_bad_cert_domain)[/INDENT]


So, what have I done wrong and how do I fix it?  Any help or direction you can provide to me would be greatly appreciated.

Thank You.

---

### Post by arrrghhh on 2010-06-01
You have to sign the cert with a CA like Verisign... did you do that?  You can sign it internally all you want, but it won't make a difference unless it's checked against a 3rd party...

---

### Post by greavette on 2010-06-01
Thanks very much for the reply.  Yes I did buy a certificate from NameCheapcom so that it can be verified.  I've gone through the verification process and successfully installed it on our portal.  From within our network I can access our portal with no ssl certificate warnings, but it's from outside our network that I'm having the problem.

Thanks.

---

### Post by arrrghhh on 2010-06-01
Perhaps it takes some time to propagate?  I looked into this a while ago for my company, but we never went thru with it so I'm not sure.  Have you contacted NameCheapcom to see if it takes some time to propagate?

I know, bad answer.  If that doesn't help you, hopefully someone else knowledgable will chime in.

---

### Post by greavette on 2010-06-01
No problem.  I greatly appreciate your advice.  I will open a ticket with support at Namecheap.com and ask them what I should do.

In the meantime, if anyone else has some ideas of what I've done wrong and how to fix it, please share so we can all learn.

If I find an answer, I will post the solution here.

Thanks!

---

