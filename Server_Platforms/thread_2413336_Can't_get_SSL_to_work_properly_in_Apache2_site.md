---
title: "Can't get SSL to work properly in Apache2 site"
date: 2019-02-24
forum: Server Platforms
---

### Post by astaticskyline on 2019-02-24
I oversee Koha, an open source library system running in Apache2 - Ubuntu 18 LTS. 

I have an SSL cert, I generated the request no problem, and followed a few forums that helped me with the process:
[https://www.codingepiphany.com/2014/11/26/installing-godaddy-ssl-certificate-in-an-ubuntu-server/](https://www.codingepiphany.com/2014/11/26/installing-godaddy-ssl-certificate-in-an-ubuntu-server/) 

Other than the fact that the site is library.conf and not the default [COLOR=#2AA198 !important][FONT=Monaco]000[/FONT][/COLOR][COLOR=#859900 !important][FONT=Monaco]-[/FONT][/COLOR][COLOR=#859900 !important][FONT=Monaco]default[/FONT][/COLOR][COLOR=#DC322F !important][FONT=Monaco].[/FONT][/COLOR][COLOR=#268BD2 !important][FONT=Monaco]conf [/FONT][/COLOR]referenced in the article, I followed these instructions, and verified with other sites, and I'm not sure what i'm missing.

However, there is no change to the site. It loads without SSL. 

Attached is the (edited for privacy) site config. 

Any Apache folks out there who can help?

Thank you in advance!

---

### Post by howefield on 2019-02-24
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by volkswagner on 2019-02-24
Is that your complete configuration file?
You're missing several important sections like servername, documentRoot, <directory>, etc.

Please familiarize yourself with forum posting tools. Use the code tags for posting content, then
review your post for readability. I'm not sure what the gibberish is supposed to be after "not the default".

It's better to post config files, inside the code tags vs. attaching picture.

---

