---
title: "Why the need for FF and Chrome to hijack dev domains?"
date: 2018-04-09
forum: The Cafe
---

### Post by Gottier on 2018-04-09
For years I have used a setup on my development machines where [http://dev](http://dev) is an index that links me up to all of the projects I'm working on, and common stuff like phpinfo.

I'm sure you're aware, but now you can't use dev domains without a security certificate, as Firefox and Chrome will force these domains to have a TLS/SSL connection.

So, I just switched to [http://dv](http://dv). I'm not losing sleep over it, but everytime I see it I am very annoyed. Why would Firefox and Chrome expect my local dev machine to have a real security certificate. A self signed on isn't good enough, and I can't bypass it in any way. I can't even set up an Apache redirect in virtualhost. I can't figure out how to bypass this in Firefox config or anything. I feel like they hijacked my domain and for no good reason.

---

### Post by TheFu on 2018-04-09
Let's Encrypt - [https://letsencrypt.org/](https://letsencrypt.org/)  is the normal answer.

But I agree, if what you are saying it true. Browsers are trying to be security for the non-technical users out of the box, while still allowing really insecure things like javascript.

---

### Post by Dragonbite on 2018-04-10
Yikes!

I wonder what this will mean for the Xampp (from Apachefriends) web servers!  Either they will need to run https or Firefox and Chrome will need to be able to determine local servers to bypass or skip this requirement.

I could be wrong, too.  Maybe Xampp already has https set up.

---

### Post by TheFu on 2018-04-10
[https://support.mozilla.org/en-US/questions/1027355](https://support.mozilla.org/en-US/questions/1027355) seems related.
Google is pushing hard for all web traffic to be encrypted. They know best, right? NOT!

---

### Post by Gottier on 2018-04-12
Let's Encrypt might be the "normal answer", but try applying that to a domain like "https://dev". As far as I know, you can't do it because of the domain validation that Let's Encrypt requires. So then you might think that you can use a self signed cert, but that's not good enough for Chrome or Firefox.

---

### Post by &amp;KyT$0P# on 2018-04-12
Does it work to create your own authority certificate with [FONT=Courier New]openssl[/FONT] and use it to sign a certificate for your local dev domain?

---

### Post by Gottier on 2018-04-13
> **halogen2 said:**
> Does it work to create your own authority certificate with [FONT=Courier New]openssl[/FONT] and use it to sign a certificate for your local dev domain?

Nope. I just went through the whole process, and it does not work. Same error regarding self signed certs.

---

### Post by kerry_s on 2018-04-13
what about a hosts file redirect?
like:
192.168.0.1 [http://dev](http://dev)

that's an example, don't do if your router is there, unless you don't need to access your router. ;)

---

### Post by Gottier on 2018-04-13
> **kerry_s said:**
> what about a hosts file redirect?
like:
192.168.0.1 [http://dev](http://dev)

that's an example, don't do if your router is there, unless you don't need to access your router. ;)

There's no sane way around this. They've decided that any domain that ends in "dev", even if it's not a dot dev (.dev) domain, must have a valid security certificate that's not self signed. You can't bypass this, or allow an exception like you normally can for any other website/domain.

---

### Post by kerry_s on 2018-04-13
lol
where there's a will there's a way
just haven't found it yet

---

### Post by &amp;KyT$0P# on 2018-04-14
> **Gottier said:**
> Nope. I just went through the whole process, and it does not work. Same error regarding self signed certs.
Huh?  I just tried it in Chromium 65.0.3325.181 on Xubuntu 18.04 with a local server, and it worked for me.  I can access [FONT=Courier New]https://dev/[/FONT] no problem.

What is the exact error you get?

---

### Post by Gottier on 2018-04-16
> **halogen2 said:**
> Huh?  I just tried it in Chromium 65.0.3325.181 on Xubuntu 18.04 with a local server, and it worked for me.  I can access [FONT=Courier New]https://dev/[/FONT] no problem.

What is the exact error you get?

Sorry, since I use FF for development I had not tried Chrome. Truthfully, I'm just super annoyed with this, because I still find myself clicking links to dev, and I see the error daily. It's just a "Your SSL is self signed and you can't do a dang thing about it" error.

---

### Post by Habitual on 2018-04-18
> **Gottier said:**
> So then you might think that you can use a self signed cert, but that's not good enough for Chrome or Firefox.
I think the browser devs know something we don't.

---

### Post by Gottier on 2018-04-22
> **Habitual said:**
> I think the browser devs know something we don't.

Yeah, like how to hijack domains and get away with it.

---

