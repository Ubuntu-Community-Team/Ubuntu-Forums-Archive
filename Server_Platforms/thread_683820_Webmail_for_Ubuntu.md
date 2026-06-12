---
title: "Webmail for Ubuntu"
date: 2008-01-31
forum: Server Platforms
---

### Post by elvinatom on 2008-01-31
I got a mail- and webserver running in my domain (gutsy-server) and wonder if there is a webmail package that work well with apache2.  Any suggestions on this?

---

### Post by quietas on 2008-01-31
If you are looking for just mail, I'd recommend [Squirrel Mail]("http://www.squirrelmail.org/"). It's quick, easy, and works. At work I use PHPGroupware a groupware app, it works, but it's a bit clunky. Many people recommend Citadel as it is a turnkey all in one groupware and mail app.

Zimbra and Scalix are a couple others. Really decent free open source versions, as well as great paid versions.

---

### Post by HermanAB on 2008-01-31
Roundcube is nicer than Squirrel.  I think Squirrel is really terribly fugly...

---

### Post by MJN on 2008-01-31
I like SquirrelMail. It works well, and works fast. Highly configurable too with the multitude of plugins available. I agree - it's not the prettiest, but then I want to send/receive mail not look at nice graphics... ;)

Mathew

---

### Post by elvinatom on 2008-01-31
well thank you guys, i think i might check them all out, pretty is great since i just need basic functionality, but speed might be of more importance to me than looks.

---

### Post by elvinatom on 2008-01-31
just noticed about squirrel - it runs on top off imap.  i got pop though and don't want to fiddle with my (finally perfectly working) mail setup.  I guess squirrel is a no-go unfortunately, unless there is a work-around ...

---

### Post by elvinatom on 2008-01-31
Looking deeper into it, I guess I have to add imap in order to do anything more then receiving mail to the inbox.  I guess I get that started before worrying about webmail.  Thanks for your input though.

---

### Post by bmathis on 2008-02-01
I use squirrelmail with the Squirrelmail Outlook theme, (see screenshot!)

Download: [http://sourceforge.net/projects/squirreloutlook/]("http://sourceforge.net/projects/squirreloutlook/")

If you're using courier for pop, then install courier-imap and imap should set itself up with no configuration (if youre not using virtual domains). 

Enjoy

[IMG]http://www.brianmathis.net/squirreloutlook.jpg[/IMG]

---

### Post by MJN on 2008-02-01
There are some very examples of how Squrreilmail can look/work at [www.nutsmail.com](www.nutsmail.com) (commercial). I hesitate to use the term 'skin' because it is more in-depth than that (like SquirrelOutlook I guess) but does show you can have the best of both worlds if aesthetics are important.

Elvinatom, don't be too concerned about the realisation of requiring IMAP - it shouldn't be too difficult too introduce abd the benefits of the protocol are vast. In no time at all you will wonder how you ever did without it!

Mathew

---

### Post by artcancro on 2008-02-01
> **elvinatom said:**
> Looking deeper into it, I guess I have to add imap in order to do anything more then receiving mail to the inbox.  I guess I get that started before worrying about webmail.  Thanks for your input though.

If you want a great looking mail/webmail server that is easy to install, check out [Citadel]("http://www.citadel.org").  The installation is a breeze and it will give your system a high-performance POP/IMAP/SMTP server plus a gorgeous webmail interface, plus calendars and address books and all sorts of other goodies.

Sorry HermanAB, beat ya to the punch this time :)

Anyway, the idea of installing Zimbra is a scary one these days -- they're owned by Yahoo and it looks like a hostile takeover by Microsoft is about to occur, so Zimbra will likely be orphaned very soon.

---

### Post by ubnuturero on 2008-02-02
I use squirrelmail  it's simple  works  and  even works on my cell phone ..

---

### Post by elvinatom on 2008-02-03
Oh wow, that's great info from all of you - so here's my news:

Thanks artcancro, but I already did install courier-imap as advised and as promised, it just works right out of the box.  I also installed squirrel, cause it seemed to be easy to setup and fast - i can confirm that too.

Squirrel is indeed quite 'fugly' - but i'm happy that I have webmail running at all.  My question would have been: "Is there a convenient way to change the login logo and to remove the 'SquirrelMail'-link in the mail-interface", but the outlook-theme already answered that (thanks bmathis - though I must say I can't do MS-themes, it would be a shame to make linux look like [*insert insult here*]).

Next thing on the to-do list is to find a nice theme that is pretty and unique.

Thanks for you input.

---

### Post by bmathis on 2008-02-04
you can easily change the logo and the link by using the squirrelmail config utility and selecting "1. Organization Preferences" > sudo squirrelmail-configure 

For themes, there's the outlook theme that I recommended, you can buy one from [http://nutsmail.com]("http://nutsmail.com") for $29 to $199, and I just found [http://lm32.com/]("http://lm32.com/"). Do a search for squirrelmail themes and you'll come up with something.

---

### Post by qrwe on 2008-02-04
Another advantage worth noting with Squirrelmail is that it's not relying on Javascript and/or similar. This is not a problem for most users, but there are some cases when it could be a struggle to have those features enabled, especially if you're somewhat into security.

---

### Post by elvinatom on 2008-02-04
Yes bmathis, the lm32-site looks pretty slick, that's what I had in mind, thanks a bunch.  Btw, I didn't mean to criticize you on the outlook theme before (I actually really liked it) - it's just me and my silly pride for running Linux.

Qrwe, i agree with you and even I'm only running the default skin on squirrel right now, I'd rather stick with it then using other solutions that come with bells and whistles that I won't ever take advantage of.  Fast and reliable is what I like - eye-candy is certainly (very) cool but not a deal-breaker.

---

### Post by bmathis on 2008-02-08
> **elvinatom said:**
> Yes bmathis, the lm32-site looks pretty slick, that's what I had in mind, thanks a bunch.  Btw, I didn't mean to criticize you on the outlook theme before (I actually really liked it) - it's just me and my silly pride for running Linux.

no offense taken :)

---

