---
title: "Web and Mail server on same machine?"
date: 2008-12-03
forum: Server Platforms
---

### Post by quikone8 on 2008-12-03
I am running a mail server on a Dell poweredge 2900 machine which works very well.  Of course it is using Citserver and Webcit to control inside and outside connections.  Is it possible or advisable to have the same machine that is running the mail server also run a webserver, if so, how?  Does anyone have any recomendations?  I do have LAMP on my machine, but I am having trouble with citserver and webcit, they seem to be interfering with mysql.  Do I have other options that would be better.  My goal is to host a few blogs running on Wordpress software.  Would it be better to have the Mail server stay on the physical machine and maybe virtualize the webserver?

Thanks for the responses, this should be fun.

---

### Post by hictio on 2008-12-03
I never used "Citserver and Webcit", but...

I believe you can easily serve both services on the same box, as long as the capacity, or the security concerns are manageable.

- How many email accounts are you going to store?
- What email services are you going to offer (POP3/ IMAP)?
- What about Webmail?

- What type of web content do you offer?
- How many hits do expect to have?

---

### Post by Peter Anselmo on 2008-12-03
I am running both a mail and a webserver off the same machine.  I'm using Postfix for mail, and I havn't run into any conflicts with the LAMP stack.  I would think the the biggest worry would be capacity, not individual program interference.

Just hosting a few blogs shouldn't prove to be too resource intensive - depending on your location, you'll probably be more limited by the upload speed than the computer's capacity.

---

### Post by quikone8 on 2008-12-04
> **hictio said:**
> I never used "Citserver and Webcit", but...

I believe you can easily serve both services on the same box, as long as the capacity, or the security concerns are manageable.

- How many email accounts are you going to store?
- What email services are you going to offer (POP3/ IMAP)?
- What about Webmail?

- What type of web content do you offer?
- How many hits do expect to have?

I don't think the security issues are a concern.  My only issue is localhost/127.0.0.1.  It seems that both the email server and  apache/mysql want to use the same.

Email accounts are minimal 10-20.  Same with webmail.  

The only webcontent will be limited blog activity.

The challenge I am having is that both seem to want to use localhost/127.0.0.1; both seem unwilling to share.

---

### Post by quikone8 on 2008-12-04
> **Peter Anselmo said:**
> I am running both a mail and a webserver off the same machine.  I'm using Postfix for mail, and I havn't run into any conflicts with the LAMP stack.  I would think the the biggest worry would be capacity, not individual program interference.

Just hosting a few blogs shouldn't prove to be too resource intensive - depending on your location, you'll probably be more limited by the upload speed than the computer's capacity.

How do you deal with the fact that the email program and the webserver both wanting to use localhost/127.0.0.1?

There seems to be a conflict in this area, I don't know how to get around this.

For instance;  If I go to a web browser and type 127.0.0.1/localhost, the system does want to go anywhere.  How do you get around this problem?

---

### Post by hictio on 2008-12-04
> **quikone8 said:**
> How do you deal with the fact that the email program and the webserver both wanting to use localhost/127.0.0.1?

There seems to be a conflict in this area, I don't know how to get around this.

For instance;  If I go to a web browser and type 127.0.0.1/localhost, the system does want to go anywhere.  How do you get around this problem?

I don't understand... Every single program/ service will use localhost, in fact, every single service will also use the IP address of your box as well.
What differentiates services are ports, the mail server (SMTP) uses port 25 TCP; and the web server (HTTP) uses port 80.

Where are you typing localhost? If you want to access the web server on your box, the only way that localhost will work is if you open a browser on the same box.
To access it, from another box, type the IP address that the server has.

---

### Post by HermanAB on 2008-12-04
Yes, I do that.  It works fine for a low traffic situation.  I run Webcit on HTTPS port 143 and Apache on HTTP port 80 using a single IP address.

You just need to be careful with which ports you use for what and prevent Apache from glomming onto everything.

Cheers,

H.

---

### Post by hictio on 2008-12-04
> **HermanAB said:**
> I run Webcit on HTTPS port 143 and Apache on HTTP port 80 using a single IP address.


Wouldn't that be port **443** for HTTPS? Or is it a Webcit kinda thing? What happens if you need to have an IMAP server?

---

### Post by quikone8 on 2008-12-04
> **HermanAB said:**
> Yes, I do that.  It works fine for a low traffic situation.  I run Webcit on HTTPS port 143 and Apache on HTTP port 80 using a single IP address.

You just need to be careful with which ports you use for what and prevent Apache from glomming onto everything.

Cheers,

H.

I understand what you are saying, first how do I prevent webcit from glomming too many ports, and second the same for Apache?  I can see in webcit where to specify ports used, but don't remember or (know how in the first place)to specify ports in Citadel or Apache.

Also when on the server and I type localhost or 127.0.0.1 which service comes up?  In other words, is apache going to come up or is webcit?  Can you tell I am confused?

---

### Post by andrewjmonks on 2008-12-04
> **quikone8 said:**
> I understand what you are saying, first how do I prevent webcit from glomming too many ports, and second the same for Apache?  I can see in webcit where to specify ports used, but don't remember or (know how in the first place)to specify ports in Citadel or Apache.

Also when on the server and I type localhost or 127.0.0.1 which service comes up?  In other words, is apache going to come up or is webcit?  Can you tell I am confused?
It depends on what port you're using.  If you're in a web browser, it will probably go to port 80, so it will go to Apache.  If you're in a mail client, it will go to port 143, and you'll get Citadel.  They don't get in eachothers way unless you deliberately use a nonstandard port for something.

---

### Post by quikone8 on 2008-12-04
> **hictio said:**
> Wouldn't that be port **443** for HTTPS? Or is it a Webcit kinda thing? What happens if you need to have an IMAP server?

What's interesting, is the fact that I have port 80, 8080, 3535, 22, 2222 and a variety of other ports allowed through my router, the only one that will respond properly is 443.  When I attempt any other port the server responds access denied.  Why is 443 the only port that allow traffic, ie password accepted.

---

### Post by quikone8 on 2008-12-04
> **andrewjmonks said:**
> It depends on what port you're using.  If you're in a web browser, it will probably go to port 80, so it will go to Apache.  If you're in a mail client, it will go to port 143, and you'll get Citadel.  They don't get in eachothers way unless you deliberately use a nonstandard port for something.

Would the syntax for that be something like the following; localhost:80 or localhost:143?

---

### Post by andrewjmonks on 2008-12-04
> **quikone8 said:**
> Would the syntax for that be something like the following; localhost:80 or localhost:143?
Yes, but you shouldn't need to worry about it unless you're doing something unusual.

---

### Post by HermanAB on 2008-12-04
> **hictio said:**
> Wouldn't that be port **443** for HTTPS? Or is it a Webcit kinda thing? What happens if you need to have an IMAP server?

Yes, typo!

H.

---

### Post by quikone8 on 2008-12-04
> **HermanAB said:**
> Yes, typo!

H.

Hi,
I didn't understand that last response.

---

