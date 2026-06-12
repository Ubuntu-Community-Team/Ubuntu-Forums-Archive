---
title: "Host a registered domain"
date: 2012-02-04
forum: Server Platforms
---

### Post by aliov_85 on 2012-02-04
Hi
I've registered the domain [ibsapay.com]("http://ibsapay.com") . In the domain name's panel I've set forwarding so it points to my machine whch has a static IP address. When I go to ibsapay.com it displays the ip address instead of domain name. Would you please tell me how can I manage it so the domain name is not replaced with IP address?
I've already created virtual host which didn't help.

Thanks

---

### Post by Vegan on 2012-02-04
sound like your ISP is simply using a redirect rather than s standard A record

---

### Post by Habitual on 2012-02-04
```
host ibsapay.com
``` and 
[http://intodns.com/ibsapay.com](http://intodns.com/ibsapay.com) says it's A Record is 80.74.129.151

ibsapay.com in browser brings up 46.14.187.92

Stale DNS? (I have Google DNS)

```
curl -Is http://46.14.187.92| \grep -E '^Server'
```Server: Apache/2.2.20 (Ubuntu)

```
curl -Is http://ibsapay.com| \grep -E '^Server'
```Server: Apache/2.2.3 (CentOS)

```
curl -Is http://80.74.129.151| \grep -E '^Server'
```Server: Apache/2.2.3 (CentOS)

```
curl -Is http://46.14.187.92| \grep -E '^Server'
```Server: Apache/2.2.20 (Ubuntu)

From public information available and these commands, I could assume you are Norman Kerr and are running Ubuntu at that the mail record(s) changed while I researched even this tiny bit.

HTH.

---

### Post by aliov_85 on 2012-02-05
Thanks for your replies. So what I've to do?

---

### Post by aliov_85 on 2012-02-05
Please help

---

### Post by lukeiamyourfather on 2012-02-05
Whoever registered the domain for you used their own IP address instead of yours. They are simply forwarding users to the IP address you entered in the "control panel" (I assume this is from the people who registered your domain?).

This isn't something you can fix in the "control panel" since that's not the root of the issue. ICANN which is the organization that manages domain names (and DNS) will need to change their registration of your domain to a different IP address. The folks who registered your domain may or may not be able or willing to do this, but start by contacting whoever registered the domain for you.

---

### Post by aliov_85 on 2012-02-05
Ok, Thank you very much.

---

### Post by 51B0RG on 2012-02-05
set the redirect to have masking. a ton easier

that and if you install a board software set the board url as the domain so that the masking stays when you click board links

---

### Post by aliov_85 on 2012-02-05
Here is my admin pannel. I'm wondering how to set the masking instead of redirect.

[IMG]http://46.14.187.92/ibsapay.png[/IMG]

---

### Post by linuxpyro on 2012-02-05
> **aliov_85 said:**
> Hi
I've registered the domain [ibsapay.com]("http://ibsapay.com") . In the domain name's panel I've set forwarding so it points to my machine whch has a static IP address. When I go to ibsapay.com it displays the ip address instead of domain name. Would you please tell me how can I manage it so the domain name is not replaced with IP address?
I've already created virtual host which didn't help.

Thanks

With a redirect, I think, your domain is given a Web forward.  So when someone goes to your domain it tells their browser to go to a different address, in your case your IP.  This is sort of like just typing your IP into the address bar, which is why that's what you see.

What you want to do is create a host (an "A") record that matches your domain (or a host within your domain) with your IP address.  For instance, you could create a record with a host name [www.ibsapay.com](www.ibsapay.com) which points to 1.2.3.4 (or whatever your IP is), and then when a user types [www.ibsapay.com](www.ibsapay.com) into their browser, that's what they see.  You might want to make another record from just ibsapay.com to your IP also, in case someone types that one in.  (Although, for my own domains I usually use a redirect.  So in your case, you'd just have the one record, and then typing ibsapay.com would just redirect you to [www.ibsapay.com](www.ibsapay.com).)

If you're not sure about how to do this check your registrar's FAQ, or contact their support.  They should be able to help you through making the record.

---

### Post by aliov_85 on 2012-02-07
Thank you guys for your advices. I'd to contact the domain registrar and they solved the problem

---

