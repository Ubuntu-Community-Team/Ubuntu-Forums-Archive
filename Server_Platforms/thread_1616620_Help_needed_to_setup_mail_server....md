---
title: "Help needed to setup mail server..."
date: 2010-11-08
forum: Server Platforms
---

### Post by SINNISTER on 2010-11-08
hey All,

I would like to setup a mail server but not just any old mail server.
I would like to have a mail server that acts like a storage place for my mail.

I run a web developing company and want all my emails to go thru my server.

is there anyway that i can just set up a mail server of some kind that logs into all my mail accounts and stores them on the server until i download them from my server.

The e.g i have in my mind is of a while pool of all my accounts and every 20min it automatically checks for mail. then i connect to the server with my servers IP like if i was logging onto my FTP and then downloading my mail.

The main reason is for back up and also virus/spam scanning...

all help or advice is wanted.....

thanx a million

---

### Post by SeijiSensei on 2010-11-08
Take a look at [fetchmail]("http://fetchmail.berlios.de/").  It's available in the Ubuntu repositories.

---

### Post by craigp84 on 2010-11-08
Hi, if you run a company you've better things to focus on than running a mail server :-) Get some more clients on board!!

Gmail for business is still free for the standard addition. You will struggle to beat it's spam filtering and it now does some virus scanning.

I would still download all emails from gmail for safety (it'd be negligent not to!). That could be as simple as opening a POP client every so often on your desktop machine, or as the previous poster suggested, good ole fashioned fetchmail.

Hope this helps!

---

### Post by SINNISTER on 2010-11-08
thanx guys i think i will try the fetchmail setup.

any video links to setting it up.

just saw the online manual and its just far to much reading to do right now...

hahaha yes i know im lazy :)

---

### Post by HermanAB on 2010-11-08
Citadel of course:
[http://www.citadel.org](http://www.citadel.org)

It only takes about 20 minutes to install and it does everything.

---

### Post by lisati on 2010-11-08
Fetchmail with Postfix is good if you wish to retrieve email from another provider, and if you go this way and want to use an email client (e.g. Evolution or Thunderbird, etc.) then you can use IMAP to access your email.

I haven't used Citadel, but something of that nature might be good.

I have Postfix, Squirrelmail and Roundcube installed on my server, and use IMAP to access most of my email accounts from my laptop, and Squirrelmail and/or Roundcube when using a computer at work.

---

### Post by HermanAB on 2010-11-09
Howdy,

Postfix is good, but the problem is that it is not really a complete solution - it also needs MySQL, Apache, Dovecot, Amavis, Roundcube and more.  It is like telling someone that replacing a VW Beetle engine is easy, since it is fastened with only 4 bolts.  True enough, but to remove the engine you also got to remove the bumper (4 helluvadifficult bolts), the cooling shrouds (about 36 little bolts), the petrol cable, petrol tube, clutch cable, electrical cables... you get the picture.

So, I gave up with Postfix about ten years ago and exclusively use Citadel, which comes with an amazing Easy Install script.  You just run that and about 20 minutes later everything works and you can get on with your life and do what you actually wanted to do.

---

### Post by SINNISTER on 2010-11-09
Awesome, got it to install but battling to configure it.

All i would like to know what is the command to start the server and is the IP 127.0.0.1:2000?

thanks thou guys... you make learning Linux easier....

---

### Post by James78 on 2010-11-09
> **HermanAB said:**
> Howdy,

Postfix is good, but the problem is that it is not really a complete solution - it also needs MySQL, Apache, Dovecot, Amavis, Roundcube and more.  It is like telling someone that replacing a VW Beetle engine is easy, since it is fastened with only 4 bolts.  True enough, but to remove the engine you also got to remove the bumper (4 helluvadifficult bolts), the cooling shrouds (about 36 little bolts), the petrol cable, petrol tube, clutch cable, electrical cables... you get the picture.

So, I gave up with Postfix about ten years ago and exclusively use Citadel, which comes with an amazing Easy Install script.  You just run that and about 20 minutes later everything works and you can get on with your life and do what you actually wanted to do.
I can configure an entire Postfix/Dovecot solution in under 30 minutes, and I expect it to work better and more reliably than Citadel.

---

### Post by HermanAB on 2010-11-09
> I can configure an entire Postfix/Dovecot solution in under 30 minutes, and I expect it to work better and more reliably than Citadel. 

You got a script for that?  
(No I'm not being flippant, I would really like to have one.)

However, Citadel does a whole lot more than mail.

```
-bash-3.2$ uptime
 21:37:17 up 378 days
```
That's reliable enough for me.
;)

---

### Post by SINNISTER on 2010-11-10
Hey guys i managed to install Citadel but now its in the way of my Lampp server...

what is that command to stop or kill citadel or is there somehow i can change the Default URL from Localhost to something else?

thanks

---

### Post by clay7 on 2010-11-20
HermanAB,

I went to the Citadel page and it says it has calendars, chat, etc. While installing, does it give you the option of what components to install? I'd only want the email components.

---

