---
title: "opensource webmail?"
date: 2007-10-16
forum: The Cafe
---

### Post by leetrefz on 2007-10-16
I'd like to get away from yahoo, gmail & the like. Is there any good linuxy, open-source-ish alternative?

Hushmail & Fastmail don't seem great to me. 

noticed roundcube, squirrelmail & open webmail, but they don't seem to offer accounts. Using them you're supposed to keep your computer on all the time as a server?

---

### Post by motang on 2007-10-16
> **leetrefz said:**
> I'd like to get away from yahoo, gmail & the like. Is there any good linuxy, open-source-ish alternative?

Hushmail & Fastmail don't seem great to me. 

noticed roundcube, squirrelmail & open webmail, but they don't seem to offer accounts. Using them you're supposed to keep your computer on all the time as a server?
That is a very good question and I can't think of any.  And the ones you mentioned all seem to be that you install on your server and for that like you said it needs to be up and running 24/7.  

However you can get a domain (web host) that uses RoundCube as the webmial client.  Check out [RoundCubewebhosting.com]("http://www.roundcubewebhosting.com/").  Maybe this is something what you are looking for.  Hope I was a bit a of help to you.

---

### Post by GSF1200S on 2007-10-16
> **motang said:**
> That is a very good question and I can't think of any.  And the ones you mentioned all seem to be that you install on your server and for that like you said it needs to be up and running 24/7.  

However you can get a domain (web host) that uses RoundCube as the webmial client.  Check out [RoundCubewebhosting.com]("http://www.roundcubewebhosting.com/").  Maybe this is something what you are looking for.  Hope I was a bit a of help to you.

Im thinking about setting up my own server for email. I, however, have a seperate computer to donate to the cause. Is there any avenue to have it be a web/email server without paying per month. Im guess all I would need is the redirect. Any browser/OS could see the web page (is this right?), and the server could be accessed using apache, at least for now. Samba could come along in the future for Windows PC's, but im still green to all of this so I dont know.

Dont mean to jack the thread, but it is on subject. You could buy a cheap computer and run a command line server on it. Im going to do it wireless because my spare comp is a lappy just like my primary, but a land line could be used as well.

---

### Post by southernman on 2007-10-16
> **leetrefz said:**
> I'd like to get away from yahoo, gmail & the like. Is there any good linuxy, open-source-ish alternative?

Hushmail & Fastmail don't seem great to me. 

noticed roundcube, squirrelmail & open webmail, but they don't seem to offer accounts. Using them you're supposed to keep your computer on all the time as a server?
You could do one of a couple things: Both require you to register a domain name of your own

1- Rent server space from a web hosting company... They use (usually) one or more of the open source apps you mention. This way, you have your own domain with any email you want e.g. [email]yourname@yourdomain.com[/email]

2- Setup your own server running off your dsl/cable internet connection. Sign up at a service like Dyndns.com and use their name servers to point to your IP address (usually this is dynamic, which calls for additional software on your server, or you can opt to pay *lease* a static IP from your ISP). This way you have total control, but you also have all the headache associated with running your own web server. While you server doesn't HAVE to be on 24/7, it can't send/receive mail unless it's up and connected... of course!

Personally, I don't see why you would want to torture yourself for a simple thing such as email. Gmail (and even yahoo I suppose *sighsssss*) offer perfectly acceptable products IMO.

---

