---
title: "Advice for Setting up webmail access using a .pst file"
date: 2006-07-15
forum: Server Platforms
---

### Post by Smandola on 2006-07-15
Hey Everyone, 

I'm a bit confused, and I'm hoping that I have posted this question in the correct place.

Firstly, I have a couple of Xp boxes, I run outlook, however my actual .pst file sits on a linux box (file sharing with Samba).  What I would like to do is to run a webmail service so that I can access my mail from outside of my home network.  I'm not that concerned about sending and receiving from outside of home.  My current setup is that I retrieve mail from my ISP (via outlook), and using the POP3 settings in Outlook I have a .pst file.  I would like to continue to do is to have my ISP as my mail service provider, and would prefer to use outlook on my Xp boxes.

I've reviewed setting up a mail server, however I think its overkill for my requirements.  I also looked into products like Evolution, Dovecot, Courier, and Postfix, but for all of these products, I would need to migrate away from the pst file.  

Can anyone suggest an architecture that could help out?
I know that this is a vague question, but even if I have some suggestions for a big picture point of view, I'll research and read for myself.  I guess I'm just looking for some direction.  Suggestions ?

Thanks in advance.

---

### Post by eentonig on 2006-07-15
For as far as I'm aware of, .pst files are MS propriety files for Outlook. No  known solution to read (let alone change) them via another mail application. The best you can do is indeed convert away from Ms *.pst.

Or use the Microsoft Webmail service?

---

### Post by remukoul on 2008-06-04
Hi... Its seems that the problem you are facing is not as smaal as it seems .. think of a situation You are not at your desk and need to access your pst.. Wat then ??? Lets try and get deeper into it .. :guitar:

---

### Post by wdaniels on 2008-06-04
It was about 2 years ago when I ditched Windows completely, and I had all my work email in a pst file. I searched for *days* to find something that could even read it but all I found at that time was an outdated utility somewhere on sourceforge which I couldn't get to work.

I haven't looked since, but I sincerely doubt that you'll find anything new to read pst files on Linux, let alone use them as a mail source in a webmail app.

---

