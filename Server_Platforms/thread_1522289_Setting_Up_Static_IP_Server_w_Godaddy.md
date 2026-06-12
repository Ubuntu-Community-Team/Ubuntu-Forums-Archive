---
title: "Setting Up Static IP Server w/ Godaddy"
date: 2010-07-02
forum: Server Platforms
---

### Post by ChurroLoco on 2010-07-02
Ok so I got my server running with apache2.  I can access it via the web with my static IP.

I registered on Godaddy for a domain, and sucessfully setup URL forwarding.  When I type in that domain it takes me to my website, but the browser shows the IP address again.  Should I not be using "URL forwarding"?  I'm guessing I have to do something on my server side saying what domain it is but I don't know which file to change and I am scared to touch anything.  Although I'm a programmer, I'm not a network person.

I'm sure this same question has been asked a million times, but I wanted to make sure the answer was somewhat specific to me...  Any thread forwards would be great!

---

### Post by kevin11951 on 2010-07-02
> **ChurroLoco said:**
> Ok so I got my server running with apache2.  I can access it via the web with my static IP.

I registered on Godaddy for a domain, and sucessfully setup URL forwarding.  When I type in that domain it takes me to my website, but the browser shows the IP address again.  Should I not be using "URL forwarding"?  I'm guessing I have to do something on my server side saying what domain it is but I don't know which file to change and I am scared to touch anything.  Although I'm a programmer, I'm not a network person.

I'm sure this same question has been asked a million times, but I wanted to make sure the answer was somewhat specific to me...  Any thread forwards would be great!

Very simple... 

Disable fowarding

Go to your "total MX" records (somewhere on godaddys page) and point your "@" record to your ip... 

Done!

---

### Post by ChurroLoco on 2010-07-02
Ahhh seems simple thank you..

So I also got the "mydomain.net" version.  I'de prefer people to use the .com version so maybe I should set the forwarding on that to go to the .com?

---

### Post by volkswagner on 2010-07-02
For the .net domain you may want to set up a redirect.  Depending on the future use of the .net.  If you think you'll always have it point to you main domain, SEO theory leads me to believe using a 301 redirect is the best solution.

If you go the 301 redirect route, just setup your @ record the same as the .com in godaddy.  Then in Apache2 create a new virtual host.  In the new virtual host create your .htaccess in the web root directory.

---

### Post by ChurroLoco on 2010-07-02
Wow you guys are full of good advice.  I'm going to tap this thread dry with one more question then.

So my-domain.com is now sending my to my server without the IP showing up.  So it is working.

The only problem is I get an error when I try to access [https://my-domain.com/svn](https://my-domain.com/svn), but [https://ip/svn](https://ip/svn) works just fine.  Do I have to do something different with GoDaddy?  I'm using a self signed certificate right now.

The Error:
```
XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/firefox-3.6.3/chrome/browser.jar!/content/browser/certerror/aboutCertError.xhtml
Line Number 59, Column 12:    <title>&certerror.pagetitle;</title>
-----------^
```

---

### Post by ChurroLoco on 2010-07-02
[SIZE="5"]Never Mind![/SIZE]

I think the computer I used just downloaded the key when I was using the IP address for the name instead of the domain... it seems to be working on a different computer though.

SOLVED

Thank you Ubuntu community!

---

