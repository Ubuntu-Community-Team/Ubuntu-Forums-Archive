---
title: "N eed to filter some web services"
date: 2009-07-18
forum: Security
---

### Post by razor7 on 2009-07-18
Hello...I manage a little network at work, and I need to filter some webpages and of course, MSN and Yahoo Messenger services.

This little network runs Ubuntu 9.04

I have no clue on where to start researching this, any help will be very appreciated.

Thanks a lot!

---

### Post by Rob_H on 2009-07-18
Many commercial tools and appliances do this, but I assume you're here because you're looking for a free (beer and/or libre) solution. You're in luck because Lifehacker recently did a [round-up]("http://lifehacker.com/5312820/five-best-content-filtering-tools") of popular web filtering services and software. All but one work on Linux. Your best bet is probably [DansGuardian]("http://dansguardian.org/?page=introduction"), as it allows very flexible configuration.

---

### Post by Rob_H on 2009-07-18
Hmmm... after reading your post a second time, I realize what you want goes beyond web filtering. You'll also probably want a firewall to block instant messaging ports. Lots of people recommend [Shorewall]("http://www.shorewall.net/"), but I don't have personal experience with it. So for a complete solution, you'd combine a firewall and web filtering tool.

Your users are gonna love you.

---

### Post by ddrichardson on 2009-07-18
Without installing any software, there are two approaches and two corresponding files: whitelisting (only allowing access to a list of addresses) which uses /etc/hosts.allow and blacklisting which uses /etc/hosts.deny. [Here's a guide]("http://howto-ubuntu.com/2008/11/26/blocking-websites-using-the-hosts-file/").

The other approach is to filter web pages for words and phrases you need to ban. Dansguardian is as good a place to start as any - [http://dansguardian.org/](http://dansguardian.org/)

---

### Post by razor7 on 2009-07-18
Yes...thanks a lot!!! I&#7743; also thinking on use OpenDNS in the company's main router.

Thanks a lot!

PS: Yes, all in the company loves me a lot! They have posters on their walls with my picture, but I'm thinking to give them new copyes, because the current has a lot of strange holes all arround, I don't know why?...

---

### Post by stwschool on 2009-07-18
OpenDNS ought to be sufficient then. You can add addresses for sites on their web interface, and also add the urls of the IM servers to block access to MSN and yahoo. Adding the category chat should disable web versions. Using their services is probably much more effective than doing it yourself as you've then got a whole army of people checking it out for you. I use it to keep things sane at our school.

---

### Post by razor7 on 2009-07-18
thanks a lot stwschool, the answer was allways at my fingertips.

Thanks a lot!

---

### Post by cariboo on 2009-07-18
> PS: Yes, all in the company loves me a lot! They have posters on their walls with my picture, but I'm thinking to give them new copyes, because the current has a lot of strange holes all arround, I don't know why?...

You may want to add a target to the new version of your picture. :) so there won't be any unnecessary holes in the walls. :)

---

### Post by Slashsals on 2009-07-20
Little network, did you say? Less than 20 users? Have you tried [SafeSquid]("http://www.safesquid.com/")?
You can download a full-featured 20 user free edition from [here]("http://www.safesquid.com/html/portal.php?page=126").
A lot of tutorials, HowTos and training videos are available [here]("http://www.safesquid.com/html/portal.php?page=6").

Cheers!

---

### Post by razor7 on 2009-07-20
Thanks a lot Slashsals, i will use openDNS first, and if it doesn't work, i will try the other solutions posted here!

Best regards!

---

