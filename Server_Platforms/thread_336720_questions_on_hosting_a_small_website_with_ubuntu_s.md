---
title: "questions on hosting a small website with ubuntu server"
date: 2007-01-12
forum: Server Platforms
---

### Post by tr333 on 2007-01-12
I have a small ubuntu server setup with apache2 to host a small website.  This website has a contact form to allow people to send an e-mail to my e-mail address using Perl/CGI.  I am currently thinking of installing postfix to do this, primarily because I don't know of any others.  Is this a good option for what I am trying to do, or is it overkill for a small webserver?

I am hosting this website through my isp account with a dyndns address, so maybe i could just use the isp's smtp server and save some time installing my own?  The main reason for installing my own MTA is to learn how to do it, since sending everything to an isp's server teaches me nothing.

---

### Post by chrisfay on 2007-01-12
> I am hosting this website through my isp account with a dyndns address
Is your ISP acutally hosting the site as a service or are you running it on your own connection from home via your ISP?

> so maybe i could just use the isp's smtp server and save some time installing my own?

But wouldn't you need to install an smtp server in order to configure a relayhost in the first place? You would need to configure smtp_sasl_auth in order to connect and actually communicate from your server to your ISP's. Most won't just relay mail for anyone (Unless as asked previously, you were actually using a web hosting package from your ISP that would allow use of their mail servers without authentication.)

I personally recomend setting up Postfix. I learned a ton while configuring all the aspects of a Postfix virtual mysql setup and am glad I did.

---

### Post by tr333 on 2007-01-12
sorry for not making this clear earlier....

i'm hosting this website on my own server at home, using the internet connection from my isp.

sounds like postfix, while possibly being overkill for this, would be much more interesting to use...

---

### Post by Brazen on 2007-01-12
You'll have to have an MTA on your server, but you will also have to use your ISP as a relayhost (most likely, unless you know port 25 is not blocked by your ISP).

The reasons are:

You will need to use your ISP's smtp server as a relay host because almost every ISP blocks port 25 to home accounts.  They only allow port 25 traffic between the home internet account and the ISP's smtp server.  This is for security reasons caused by poorly configured home email servers, but it's really no problem relaying through the ISP server.

You will need to have an MTA installed on your server, because how else will the email get from your server to the ISP's email server?  Unless I'm mistaken, php does not have any built in smtp capabilities.

---

### Post by tr333 on 2007-01-12
will a default install of postfix use my isp as a relay host?
(i'm new to this sort of thing...)

---

### Post by chrisfay on 2007-01-12
> will a default install of postfix use my isp as a relay host?
No....You will need to configure it to do so. I outlined the steps to do this in Postfix in this thread:

[http://ubuntuforums.org/showthread.php?t=316711](http://ubuntuforums.org/showthread.php?t=316711)

Disregard that the relayhost is an Exchange server, the steps are the same to relay through your ISP.

---

### Post by tr333 on 2007-01-12
i can telnet to my isp's mail server on port 25 without providing any user/pass credentials, so i don't think i would need to provide credentials from my server :confused: 

after searching the forums i found a how-to guide for postfix ([http://flurdy.com/docs/postfix/)](http://flurdy.com/docs/postfix/)), so i might try this and see how it goes.

for a small server like mine sitting behind a router, is it worth installing webmin?  it seems to have been dropped as a package since breezy.

---

### Post by chrisfay on 2007-01-12
> i can telnet to my isp's mail server on port 25 without providing any user/pass credentials

Telneting and actually relaying mail are two different things. No ISP would allow *everyone* access through their smtp server since this would essentially be an open relay for spam. I can guarantee you this is not the case. 

Open relays are either configured on purpose by companies offering such a service, or by inexperienced individuals. This is primarily the reason those ports are blocked by ISP's, to block misconfigured open relays from promoting spam and viruses. 

That being said, some ISP's are lax about credentials when the origin is from within their network. If that is the case, then all you need to do after installing postfix is add the Relayhost = [smtp.server.tld] directive and you'd be good to go.

---

### Post by Brazen on 2007-01-12
> **tr333 said:**
> i can telnet to my isp's mail server on port 25 without providing any user/pass credentials, so i don't think i would need to provide credentials from my server :confused: 

after searching the forums i found a how-to guide for postfix ([http://flurdy.com/docs/postfix/)](http://flurdy.com/docs/postfix/)), so i might try this and see how it goes.

for a small server like mine sitting behind a router, is it worth installing webmin?  it seems to have been dropped as a package since breezy.

I install it on every server I set up. Just download the deb file from webmin.com and install it with dpkg -i.

---

### Post by tr333 on 2007-01-12
> **Brazen said:**
> I install it on every server I set up. Just download the deb file from webmin.com and install it with dpkg -i.

i will give that a try.

thanks for all the help with this :)

---

