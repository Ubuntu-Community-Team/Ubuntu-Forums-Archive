---
title: "snip.ps and other url-shortening domains"
date: 2013-02-02
forum: Security
---

### Post by mike acker on 2013-02-02
yuk

do we have a preferred method of blocking all url-shortening domains?

i see these as a serious security hazzard as they are most likely bypassing dns standards and all the effort that was put into securing the update process for our dns servers

---

### Post by CharlesA on 2013-02-02
They don't have anything to do with DNS. They just use an HTTP redirect.

[http://rield.com/faq/why-url-shorteners-are-bad](http://rield.com/faq/why-url-shorteners-are-bad)

You can block them on a site-by-site basis, but more and more sites are popping up.

---

### Post by mike acker on 2013-02-03
> **CharlesA said:**
> They don't have anything to do with DNS. They just use an HTTP redirect.

[http://rield.com/faq/why-url-shorteners-are-bad](http://rield.com/faq/why-url-shorteners-are-bad)

You can block them on a site-by-site basis, but more and more sites are popping up.

yep

the Bad Part -- is -- the URL shortener is really another form of DNS service . as such it can direct a browser to a site ... that is a forgery

as we know **a fake site can be an exact replica of the legitimate site **. the viewer cannot distinguish by inspection

which is where  HTTPS is supposed to help: if the site is using HTTPS ( which anything commercial should ) -- then -- the URL address bar shows the little padlock + the https:// type address ...

if you click on the padlock Firefox will access the SSL security data and display it for you

which is all well and good . so far:

from the display i can get right down to the certificate and see the MD5 and SHA-1 fingerprints.  i could check the fingerprints,-- if i had the info to check them with .

but we are in the area where the computer should be covering this chore

what is missing?  

I never signed Verisign's Certificate,-- although I use it a lot, -- one site -- 833 times so far .

why is this a problem?

the re-director ( URL shortener -- or DNS poison ) could have re-directed my browser to a fake site -- with a certificate authorized by some hacker (CA certificate are a major target and have already been hacked -- RSA was one victim, there have been others ) .

the HTTPS and the padlock will all come on OK and look OK -- the problem being -- I don't have a legitimate authentication -- [COLOR=Sienna]**and there is no warning**[/COLOR] .

the reason being: I never checked and signed for Verisign's certificate

if i had the option to check and sign certificates then i could also have the option to red-flag any certificate not signed by a Certificate Authority (e.g. Verisign ) -- which I had not specifically checked and signed for
[B]
this is the Essential Part of Public Key Encryption that has been skipped over by the SSL crowd in their mad dash to pass out Linus Blankets .[/B]

Zimmerman documents this requirement in his original 1992 essay .

and it seems to me most of the security problems we have today are cause by people trying to take short cuts . in our quest to make things easy we have facilitated hacking .

~~~
Amendment 1
Given that some CA have already been hacked I would prefer to sign the certificates for web-sites that I use DIRECTLY rather than relying on a CA's approval . I already do this for MSFT Security Bullitens

how many sites do we actually use that require commercial security ? I have -- maybe 6 .

---

### Post by OpSecShellshock on 2013-02-03
A URL shortener that redirects to a phishing site will still, in the end, display a domain in the address bar that is not the site it's claiming to be. All that the URL shortener has done is provide a temporary layer of obfuscation. It's a separate concern from DNS, because if the problem were with DNS then the domain in the address bar might give the real domain name for a false page. 2 different things.

There is an extension for Firefox called RequestPolicy that, among other things, stops 302 redirects on the fly, displays the address of the final target site, and will not load the page until the user clicks on an Allow button. That should work on all URL shorteners, even the ones we don't know about yet. It will also mess up a lot of other things that are perfectly fine, but that's the choice we all have to make for ourselves.

---

### Post by mike acker on 2013-02-03
> **OpSecShellshock said:**
> A URL shortener that redirects to a phishing site will still, in the end, display a domain in the address bar that is not the site it's claiming to be. All that the URL shortener has done is provide a temporary layer of obfuscation. It's a separate concern from DNS, because if the problem were with DNS then the domain in the address bar might give the real domain name for a false page. 2 different things.

There is an extension for Firefox called RequestPolicy that, among other things, stops 302 redirects on the fly, displays the address of the final target site, and will not load the page until the user clicks on an Allow button. That should work on all URL shorteners, even the ones we don't know about yet. It will also mess up a lot of other things that are perfectly fine, but that's the choice we all have to make for ourselves.

thanks for the tip
i installed RequestPolicy right after I read your note
then i tried to reply.  
but with Request Policy running i can't reply on this forum .

i see on their web page version 1.0 is now current   while version 0.5 something is offered here .  

i think this is probably the best answer we will see for now . so when 1.0 become available i'll give it another try .

---

### Post by Ms. Daisy on 2013-02-03
You can see where the shortened url goes  before clicking on it by using this:

[http://longurl.org/](http://longurl.org/)
[http://urlxray.com/](http://urlxray.com/)

It's not fool-proof but you can weed out the obvious bad redirects.

---

