---
title: "Mail Server Help"
date: 2009-02-13
forum: Server Platforms
---

### Post by blendmaster on 2009-02-13
Hello!

I've got a server that I plan on using to host a couple of websites along with a mail server. I have a registered .com address (which I'll call 'example.com'), which was obtained through 'namecheap.com'. 

Setting up LAMP is no problem for me... I've done it several times and can get sites up in no time. My problem instead lies with setting up a mail server. I have several questions, but I guess I'll ask them as they come up (I'm reinstalling the Ubuntu server as I couldn't manage to properly configure it last install). I'll try to set up the server with Ubuntu's default 'Mail Server' package.

When the installer asks for the 'Hostname', I typically put something like 'MyServer'. What should the proper 'Hostname' be in my scenario (should I use 'example.com' or 'www.example.com' or 'example' or leave it as 'MyServer'? Or does it matter at all what I use)? During my last install, some of the mail software would use 'MyServer' when I would want 'example.com', which is why I'm asking this question.

Thank you!

---

### Post by spiderbatdad on 2009-02-13
I did this for a while and used apache's virtual host file to point to squirrelmail, which was my web interface, with postifx and courier imap. The easiest way I found was to register a second domain name for the mailserver...this is your hostname or ServerName, in the case of apache. Squirrelmail was configured to use port 443 and was listed first in the virtual host file...this seemed necessary. Port 80 was used for my regular web site, had a separate domain name, and was second.

Each site needed it's own DocumentRoot. I did something like /squirrelmail/www, and /var/www

---

### Post by HermanAB on 2009-02-13
You should use the FQDN mail.example.com.

BTW, once your are tired of fighting Postfix, give Citadel a try:
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

I run Apache and Citadel with Webcit on the same machine and the same domain name and IP address.  Apache runs on port 80 for HTTP and Webcit on 443 HTTPS.

Cheers,

Herman

---

### Post by blendmaster on 2009-02-13
> **spiderbatdad said:**
> I did this for a while and used apache's virtual host file to point to squirrelmail, which was my web interface, with postifx and courier imap. The easiest way I found was to register a second domain name for the mailserver...this is your hostname or ServerName, in the case of apache. Squirrelmail was configured to use port 443 and was listed first in the virtual host file...this seemed necessary. Port 80 was used for my regular web site, had a separate domain name, and was second.

Alright, it makes sense to use a virtual host for SquirrelMail. I would like to have both web and mail under one domain (so I could have users email an account like 'support@example.com' for instance), I'll see what I can do to get it that way (and maybe get a second domain if it comes down to that).

Thanks for the help.

> **HermanAB said:**
> You should use the FQDN mail.example.com.

BTW, once your are tired of fighting Postfix, give Citadel a try:
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

I run Apache and Citadel with Webcit on the same machine and the same domain name and IP address.  Apache runs on port 80 for HTTP and Webcit on 443 HTTPS.

Cheers,

Herman

Thanks for the advice. I was thinking of looking into Citadel (it comes up frequently on these forums it seems). If I get tired of trying to work with Postfix (which is getting closer it seems), I'll give Citadel a go.

Thanks guys!

---

### Post by HermanAB on 2009-02-13
Citadel is very mature.  It is positively ancient.  What made it take off suddenly, is the Easy Install script, which makes it almost ridiculously easy to install.  The whole process takes only about 20 minutes and then you have a fully functional mail system.

I bet you have spent several hours on Postfix and it is still not working properly, nevermind web mail, chat and calendars...

Cheers,

Herman

---

### Post by spiderbatdad on 2009-02-13
I too can vouch for citadel's simplicity of set up, and yes it worked perfectly from the start. However the interface looks like it was designed by a kid with a box full of crayons. :P Sorry to say.

---

### Post by HermanAB on 2009-02-13
There is an alternate theme for Webcit somewhere that looks better.  However, you need not use Webcit.  I primarily use it to administer the box - create new user accounts and so on.  The users all use Thunderbird over SSL.  It should also be possible to use an alternate web mail system eg Roundcube with Citadel.

[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

See this for Roundcube on Citadel:
[http://ubuntuforums.org/archive/index.php/t-367430.html](http://ubuntuforums.org/archive/index.php/t-367430.html)
[http://www.mail-archive.com/room_citadel_support@uncensored.citadel.org/msg03497.html](http://www.mail-archive.com/room_citadel_support@uncensored.citadel.org/msg03497.html)

Cheers,

Herman

---

### Post by spiderbatdad on 2009-02-13
Nice tip, thank you.

---

### Post by blendmaster on 2009-02-13
> **HermanAB said:**
> Citadel is very mature.  It is positively ancient.  What made it take off suddenly, is the Easy Install script, which makes it almost ridiculously easy to install.  The whole process takes only about 20 minutes and then you have a fully functional mail system.

I bet you have spent several hours on Postfix and it is still not working properly, nevermind web mail, chat and calendars...

Cheers,

Herman

Yes, I've spent quite a few hours trying to get Postfix to work for me already. I would like to see if I can get it to work just to say I did (I feel like I'm almost there :) )

Citadel looks nice! I'll definitely try that out after I figure out what's up on my current setup.

Currently, I'm getting

```
554 554 5.7.1 <user@example.com>: Relay access denied (state 14).
```

when I try to email my user through my gmail account. I also don't receive emails from my user account on my server.

I don't know if this has something to do with my settings at 'namecheap.com' or if it has to do with my postfix settings. All I know is I can reach Apache and SSH using my domain name.

In the host records section on namecheap, there are fields for Mail Settings, and I simply inputted what values I thought went there (shown in pic). I have no idea if these are correct.

I also followed [this post]("http://www.howtoforge.com/forums/showpost.php?p=4&postcount=2") to (supposedly) set up mailbox settings.

I apologize if this is a very novice mistake on my part.

---

### Post by HermanAB on 2009-02-13
I did some Googling and it looks like there are more themes now:
[http://www.icoss.net/citadel/blue/](http://www.icoss.net/citadel/blue/)

Installing a theme is very easy.  You put it in some directory and la voila.  If it doesn't work properly, just delete it again.

Cheers,

Herman

---

### Post by blendmaster on 2009-02-14
Update on my progress with Postfix (yes I've been up until 2:00 AM doing this :))

The MX records were part of the problem; when I realized that, it kind of made me want to bang my head into the wall.

I can now receive mail from external mail services, but cannot send to them. When I figure out what I'm doing wrong, I'll post back (probably not tonight though :P).

---

### Post by hyper_ch on 2009-02-14
I normally follow the perfect howto setup over at [www.howtoforge.com](www.howtoforge.com) ... that just works.

Hosting your own domain (even on dynamic IP) is also simple. If you can update the dyn IP with your registrar regurarly automatically just point the namservers to  [http://www.everydns.net](http://www.everydns.net) . It's free to use and you can set the dns things there and they provide a cgi or python script that you can use to update your acutal IP. I have that on a server in a small business and update their dyn ip every 30min (once in a while you will have a downtime when the dyn ip changes).

and when you're on a dyn IP then you'll also need to relay the outgoing mail through your provider some other email account that exists.

---

