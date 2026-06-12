---
title: "why is httpd.conf empty?"
date: 2006-10-16
forum: Server Platforms
---

### Post by don7777 on 2006-10-16
Hi,

I'm new to running an apache2 web server and I'm  having some problems with additional software which requires me to modify the configuration of "httpd.conf". I'm running apache2 on my Ubuntu6.06 machine and I notice that /etc/apache2/httpd.conf is empty. Is it supposed to be empty? What is /etc/apache2/apache2.conf? is it ubuntu's httpd.conf?

Thanks for any help,
Don

---

### Post by Avarus on 2006-10-16
Check the readme, there it says it is supposed to be an empty file. Don't know why, I've got the same...

---

### Post by MJN on 2006-10-16
It's because the Debian package maintainers have decided that httpd.conf was simply getting far too big - a point I can sympathise with. Hence, now the config is modularised so even as Apache grows even bigger (in terms of functionality) then the modular approach can grow in an ordered fashion with it. I'm not familiar with the mainstream Apache development however it wouldn't surprise me if it caught on there too (if it hasn't already).

Once you get the hang of it it's not too bad and you'll find you're working within a particular sub-file for any one task anyway so you're not drowned by all the other config.

To put it simply, apache2.conf is the 'new httpd.conf' insofar that it carries general (non site-specific) config, conf.d is.. <snip> just noticed it's all in the README (as Averus said) so go check that out! httpd.conf is still present (yet empty) because some packages may expect it to be there and add stuff to it - it gets parsed by default so in theory you could stick all your stuff in there but I wouldn't advise going against the Debian grain - what will work today might not work tomorrow when they start expanding it!

Mathew

---

### Post by OneSeventeen on 2006-10-16
I just wnated to throw my hat in the ring, while the stuff is in the readme, most of the things I change on my server are simply in the site config files, located in the "sites-available" folder.

by default, you just use the "default" file, but as you add sites, you can add more files, and enable them using the "a2ensite" command. (just like you can enable modules using "a2enmod")

I used an ubuntu server to run 5 different websites, using 3 total IP addresses, and this modular approach made it insanely simple!

If you only use one site, just worry about the default, or to have a good backup of the default site, just copy the default file, edit it to your specifications, then type "a2ensite foo" (where "foo" is the name of the file you created by copying the default config)

I hope this made sense... the readme probably does a much better job of it, but trust me, once you are used to it, you will like this much better than the default "one massively long file" approach.

---

