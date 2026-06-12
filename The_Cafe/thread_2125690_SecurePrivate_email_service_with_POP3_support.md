---
title: "Secure/Private email service with POP3 support"
date: 2013-03-14
forum: The Cafe
---

### Post by linuxyogi on 2013-03-14
Hi,

A newsletter came to my email a/c (the source I dont remember) saying that Google reads all our emails.

Is this true ? 

I dont really send emails to anybody. All I get is notifications of replies posted in various forums & also my daily horoscope report.

Is there a free email service which is free/private/secure with POP3 support ?

---

### Post by QIII on 2013-03-14
I doubt it, unless they recently hired 100,000 new employees!

:)

---

### Post by linuxyogi on 2013-03-14
> **QIII said:**
> I doubt it, unless they recently hired 100,000 new employees!

:)

[http://www.crn.com/blogs-op-ed/the-chart/202300583/microsofts-ballmer-google-reads-your-mail.htm](http://www.crn.com/blogs-op-ed/the-chart/202300583/microsofts-ballmer-google-reads-your-mail.htm)

---

### Post by mike acker on 2013-03-14
> **linuxyogi said:**
> Hi,

A newsletter came to my email a/c (the source I dont remember) saying that Google reads all our emails.

Is this true ? 

I dont really send emails to anybody. All I get is notifications of replies posted in various forums & also my daily horoscope report.

Is there a free email service which is free/private/secure with POP3 support ?

I use CoreComm Service.  It's like 15USD/quarter for a home account including your own domain, a bunch of free software, 5GB website, and like 25 e/mail addresses . and their privacy statement says they do not monotor your activity  . their e/mail generally works better than the free servicies,--

so get Thunderbird and learn to use GPG 

now: IF your computer is virus free and you are using GPG with Thunderbird there are not likely many spooks who can read your messages

as we know: the MOST COMMON way hackers steal information is by compromising the endpoints . just for grins: suggested reading :
[http://arstechnica.com/tech-policy/2013/03/rat-breeders-meet-the-men-who-spy-on-women-through-their-webcams/](http://arstechnica.com/tech-policy/2013/03/rat-breeders-meet-the-men-who-spy-on-women-through-their-webcams/)

I am fascinated by the monolithic v microkernel debate in o/s design -- and the implications for the differences in security (and performance) of Linux v Windows

it occurs to me that those who have become enamoured with microkernel operating software have lost contact with the main objective of the kernel and have allowed themselves to be distracted into building an o/s that is really a system of applications that serve as services .

"fwiw" i think industry as well as the user community will be taking a real hard look at various o/s systems, particularly evaluating whether a particular system protects itself and its assets effectively .  any o/s that fails in this regard will be marginalized, -- of necessity .

---

### Post by Irihapeti on 2013-03-14
Probably the most likely way that emails will fall into the wrong hands is through someone forwarding them, or CCing them, to other people, and even encryption won't prevent that.

---

### Post by Paqman on 2013-03-15
> **linuxyogi said:**
> 
A newsletter came to my email a/c (the source I dont remember) saying that Google reads all our emails.

Is this true ? 


Yes and no.

There aren't people at Google sitting and reading your emails. What they're probably referring to is that Google runs spiders through your mail so that it can display ads in Gmail relevant to the content. This is no different to anything on the web really, this page will be spidered by Google. The difference between them spidering web pages and your email is that the results of your email being scanned are only used to target stuff to you, it's not accessible to anyone else.

So yes, a machine belonging to Google does "read" your email, but it doesn't really understand the content any more than you could say a calculator understands the equations punched into it.

---

### Post by mike acker on 2013-03-15
> **Irihapeti said:**
> Probably the most likely way that emails will fall into the wrong hands is through someone forwarding them, or CCing them, to other people, and even encryption won't prevent that.

you can set "eyes only " option

there's a way around this but it will likely stop carless errors

---

### Post by cozski on 2013-03-15
I've been using Hushmail, paid service, seems to integrate well with Thunderbird/POP3, at least I haven't had any issues with it. Worth a look?

---

### Post by Lars Noodén on 2013-03-15
Also, you can avoid POP3 easily enough and go with IMAPS.  The default is to leave the messages on the server, but you can also configure your IMAPS client to download the messages instead.

---

### Post by mike acker on 2013-03-15
> **cozski said:**
> I've been using Hushmail, paid service, seems to integrate well with Thunderbird/POP3, at least I haven't had any issues with it. Worth a look?

"IMHO" security is something each of us as an individual ought best attend to.  

if you go get Phil Zimmerman's Original Essay on PGP and then read the section on Protecting Public Keys from Tampering you will have the best explanation of this topic I know of
[http://www.pa.msu.edu/reference/pgpdoc1.html#section-7.6](http://www.pa.msu.edu/reference/pgpdoc1.html#section-7.6)

the current concept: "We'll secure it for you" hasn't worked and I don't think it's going to .

MSFT/Security Bulliteins are currently the Best Example I'm aware of:  you need to go to MSFT, get their public key, bring it into your system and then sign it -- before you will get the green bar on their messages .

remember: impersonation | false identity is the #1 problem in computer security today .  the solution has been available since Zimmerman released PGP around 1992 but the industry has laughed at it saying "too complex for ordionary people to bother with "

meanwhile hackers are off to another Banner Year

make you wonder who the real hackers are

---

### Post by linuxyogi on 2013-03-17
> **Paqman said:**
> Yes and no.

There aren't people at Google sitting and reading your emails. What they're probably referring to is that Google runs spiders through your mail so that it can display ads in Gmail relevant to the content. This is no different to anything on the web really, this page will be spidered by Google. The difference between them spidering web pages and your email is that the results of your email being scanned are only used to target stuff to you, it's not accessible to anyone else.

So yes, a machine belonging to Google does "read" your email, but it doesn't really understand the content any more than you could say a calculator understands the equations punched into it.

I will continue with Gmail :p

---

### Post by RaHorakhty on 2013-03-17
> remember: impersonation | false identity is the #1 problem in computer security today . the solution has been available since Zimmerman released PGP around 1992 but the industry has laughed at it saying "too complex for ordionary people to bother with "




Most consumers depend on ISPs and services like gmail for encryption.  SSL is what these services swear by, which can be comprised if its not configured using the proper certificates.  ISPs and services like google use the information you upload to their servers for demographic research.  So, they might not read it but they can use it for research and the only real protection out there is SSL.  I don't think we'll ever see the general public use services like pgp or third party encryption software.....

---

