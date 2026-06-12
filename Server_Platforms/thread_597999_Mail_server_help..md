---
title: "Mail server help."
date: 2007-10-30
forum: Server Platforms
---

### Post by hockey97 on 2007-10-30
Hi I installed send mail and also post what ever and fetch mail.

I don't fully understand what software I need to have a complete system of sending mail and getting mail, and then storing the mail.

I am making a webpage, and want to by using php, be able to interface my webpage with the mail folders ect, 

just like any e-mail service, where you click a new mail button to open   what new mail the user has, by changing a window like in the middle of the webpage where the user can see the new mail.

So my first concern is what I need to have a complete e-mail system.
and what I should do to keep the spammers away and viirus ect.

I also plan to buy a domain name for this webpage..

Is their any website that would show how to setup a mail server system that at the end I will have a complete secure mail server running and also able to use my domain name.

---

### Post by MrFSL on 2007-10-31
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Oh google thy searches return such great information and quickly.

---

### Post by HermanAB on 2007-10-31
Here you go: [http://www.citadel.org](http://www.citadel.org)

It Just Works (TM)
It installs in about 20 minutes
It does everything, and then some
It can handle terrabytes of email in a fast database

Here is a guide: [http://www.aeronetworks.ca/citadel-howto.html](http://www.aeronetworks.ca/citadel-howto.html)

---

### Post by Railsbuntu on 2007-10-31
Thanks HermanAB for posting about Citadel. i have installed it in around 20 minutes, now I am digging into it. Do you know a forum where people chat about this piece of software?

---

### Post by hockey97 on 2007-10-31
HI, so  if I use citadel, I can use it for a commercial website??

I read the features, like e-mail, instant messaging, and calender, and much more.

I am making a website in php, and want to be able to make my own interface with the mail server, meaning I want my users able to look at their e-mail and stuff just by using my webpage, and I would make my own custom art on how the interface looks. just like aol, or hotmail..
will I be able to use this  for commercial use for free??

I already got send mail and mailman and fetch mail installed on my ubuntu server.

I have the main structure of my webpage just now working on the mail system and also the artwork.

---

### Post by Railsbuntu on 2007-10-31
That might answer your question:

> Citadel is distributed under the terms of the GNU General Public License (GPL), version 3. Plain and simple. It is true open source (or free software, if you prefer that term), not a weird hybrid with free and non-free variants.
Source: [http://www.citadel.org/doku.php/faq:generalquestions:what_source_code_license_do_you_use]("http://www.citadel.org/doku.php/faq:generalquestions:what_source_code_license_do_you_use")

Citadel sounds really great to me :)

---

### Post by songshu on 2007-10-31
it might or might not be what you are looking for, but this is the setup i'm running and after some time digging in to understand whats happening and should happen it is running trouble free ever since and has the specifications you mentioned.
secure
stable
free
customisable
[http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/)

not sure what kind of mail interface you like but you could put any kind on top of this, squirrel is very ugly by default yet very customisable, roundcube i never tried but they say it looks mighty good and there are plenty of others and how you would fit them in your page i can not answer but it should be doable.

---

