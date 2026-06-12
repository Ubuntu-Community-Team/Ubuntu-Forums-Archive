---
title: "You have chosen to open index.php"
date: 2007-01-10
forum: Server Platforms
---

### Post by ardugh on 2007-01-10
Hi all,
Now before you say this has been answered, give me a hearing, please.

Software is Kubuntu Edgy with php5,1,6; apache2.0.55-4
I have the "php-refuses-to-be-parsed" issue (on a production server).
I have googled & searched these forums for days.
I have applied all the suggestions I have read - a2enmod, removed, purged & re-installed apache2 and libapache2-mod-php5.
I have tested cgi scripts - they work.
Apache2 is refusing to parse a php page.

I actually have an urgent situation where I'm doing my best to re-instate our e-mail server after a hardware crash and we need php based pages to work.

I'm at my wits end - if anyone has found as solution or an idea, won't you kindly respond

Regards,
ardugh

---

### Post by Modernity on 2007-01-10
OK, lets start from the beginning, shall we. Did you download/install all the packages for PHP (excluding language packs)? Check those first to see what packages you have installed. I am not at my Apache server at the moment, so I couldn't tell you what you need and don't need.

After doing this, confident you have the packages, you might want to post up you Apache config file so we can have a look at it.

---

### Post by ardugh on 2007-01-10
Thanks for your response.
I'm only replying now because, in desperation, I shut down the network, sent everyone packing and re-installed.
After doing an update I installed a LAMP configuration as per the Ubuntu wiki. Apache plays nice and parses the php files :0
Now to do the rest...

Regards,
ardugh

---

