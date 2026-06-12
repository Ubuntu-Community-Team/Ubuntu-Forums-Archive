---
title: "Is this dangerous or nothing to worry about?"
date: 2009-11-19
forum: Security
---

### Post by judge jankum on 2009-11-19
I did an online security test and this is what it gave me...Is this good or bad?  Your computer is connecting to the internet at Altoona, AL, in the US, with an ip of 72.242.143.58   Yes  Your UserAgent is being reported as: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.15) Gecko/2009102815 Ubuntu/9.04 (jaunty) Firefox/3.0.15  Your IP Address is 72.242.143.58  We could not find your Host Name, this is good!  A trace to your phone comes back with an area code of: 205

---

### Post by judge jankum on 2009-11-19
this came from another web test.. Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 Accept-Language: en-us,en;q=0.5 Connection: keep-alive Host: [www.grc.com](www.grc.com) User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.15) Gecko/2009102815 Ubuntu/9.04 (jaunty) Firefox/3.0.15 Cookie: tpag=p02jp2eqma25z; ppag=p02jp2eqma25z; tico=p02jp2eqma25z; pico=p02jp2eqma25z; tcss=p02jp2eqma25z; pcss=p02jp2eqma25z Content-Length: 30 Content-Type: application/x-www-form-urlencoded Accept-Encoding: gzip,deflate Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7 Keep-Alive: 300 FirstParty: [http://www.grc.com](http://www.grc.com) ThirdParty: [http://www.grctech.com](http://www.grctech.com) Secure: [https://www.grc.com](https://www.grc.com) Nonsecure: [http://www.grc.com](http://www.grc.com) Session: smngvekb3pnom

---

### Post by halovivek on 2009-11-19
If you have closed ports and Strong password in your Linux System.
Hacking the system will be very hard.

Some one please...Add some more points..

---

### Post by judge jankum on 2009-11-19
It shows all ports to be closed

---

### Post by Logan1985 on 2009-11-19
Nothing to worry about IMO

All it's doing is seeing what browser you are using and from what Operating System. 

Not sure how to hide this, or if it's even necessary.

If you are concerned about your IP address being tracked then you could look into using a proxy service like Tor - but that will reduce browsing speed considerably.

It's port scans, pings etc that you need to make sure are locked down, which you have said they are.

---

### Post by EJeanmaire on 2009-11-19
> **judge jankum said:**
> I did an online security test and this is what it gave me...Is this good or bad?  Your computer is connecting to the internet at Altoona, AL, in the US, with an ip of 72.242.143.58   Yes  Your UserAgent is being reported as: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.15) Gecko/2009102815 Ubuntu/9.04 (jaunty) Firefox/3.0.15  Your IP Address is 72.242.143.58  We could not find your Host Name, this is good!  A trace to your phone comes back with an area code of: 205

From your IP address alone, it is quite simple to geographically locate you, and derive other things such as a guess to your area code as well... nothing you should be concerned about IMHO.  If you are paranoid, surf the web using Tor/Vidalia/Tor-button.  I think Firefox also has a "surf the web in private" option which might stop Firefox from disclosing to the website your browser/OS; however I haven't tried it so I don't know that for sure.

---

### Post by cdenley on 2009-11-19
The browser/OS is disclosed through the "user agent" string which is used by all browsers. It is sometimes used by websites to check for compatibility and to see what browsers their site is being viewed with. You can change it to whatever you want.
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
Any server you connect to is going to be able to see what IP your connection is coming from. Unless you have configured a proxy to connect to the server for you, that IP is your IP. It can usually be tracked to a geographic region or maybe a city, but only your ISP can link it to you (unless your identity is revealed in your traffic of course).

---

### Post by Slowspeed on 2009-11-22
Web browsers are supposed to pass on some information by design. As earlier mentioned, your ports are closed and hopefully you have a strong password. If you are worried you can use an anonymous proxy. That will slow your browsing down though.

---

### Post by tgalati4 on 2009-11-22
Everytime you visit a website, all of that information is/or can be passed.  It is normal.

---

### Post by OpSecShellshock on 2009-11-23
If you're already disclosing e.g. your age, sex, and location in social networking profiles and the like, then the fact that your location can be gathered from your IP address doesn't really matter.

The technological risk is minimal. By default all incoming traffic should be blocked unless it is a response to an outbound request, which would have to be user-initiated.

---

### Post by reeboker on 2009-11-23
Hey guys, just find some site wich could be useful in this topic. Check it out. [http://showmemyinfo.com/]("showmemyinfo/")

---

### Post by WhiteHorse on 2009-12-14
I think it's very dangerous, personally. I think this could be classified as a Firefox bug. Disclosing your OS version to a remote site is a security risk because the remote site could use that info to exploit your machine if a known vulnerability exists. Theoretically, they could traverse your firewall and begin a tcp/udp scan for services or even send malformed packets causing a remote code exploit to run.

What purpose does it serve a website to know your OS version? Everything should be handled by the browser and content delivered by websites over the www should be independent of OS. 

I use the user agent switcher because I'm sick of disclosing the fact that I have "Ubuntu version X with firefox X build XXXX" to every site I visit.

---

### Post by judge jankum on 2009-12-14
user agent switcher?? what is this? and how does it work?

---

### Post by lisati on 2009-12-14
What I'd worry about is the implication that a random web site could trace you back to a phone line. 

As has been previously mentioned, browsers are designed to disclose *some* information, and *some* geographic information can be inferred from your IP address, but tracing back to your phone? This is a new one on me!

---

### Post by BkkBonanza on 2009-12-15
Not phone number, just area code. It just looks up your city in an area code table.
No big deal at all.
Do you wear an invisibility cloak when you go outside so that people won't know you exist? I just don't see the problem with such generic info. You'll have more problems with sites that don't function properly due to misinformation provided then you'll ever save by hiding it. This isn't personal details.
This is like someone making notes about how many people wear red shirts on Tuesdays at the mall. Or if you prefer Coke or Pepsi. Whatever.

---

### Post by lisati on 2009-12-15
> **judge jankum said:**
> A trace to your phone comes back with an area code of: 205

> **BkkBonaza said:**
> Not phone number, just area code. It just looks up your city in an area code table.
No big deal at all.


It's probably based on the geographic information that can be inferred from the IP address rather than whatever phone line might be associated with the IP address. I would be worried about privacy issues if some random web site identify my phone number from details that browsers supply.

---

### Post by HeadHunter00 on 2009-12-23
No, it's normal.

---

