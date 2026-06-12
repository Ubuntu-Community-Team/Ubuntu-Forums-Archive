---
title: "Qmail or Postfix?"
date: 2007-10-17
forum: Server Platforms
---

### Post by maw1key on 2007-10-17
Hi All,

I am curious as to others working opinions about the two mail servers.  I have been tasked with setting up a new mail server (windows server is dying) and I chose Ubuntu as the OS and for the most part have finished installing and setting it up.

What we need is a mail server that can host 10 to 20 different domains and provide a web interface for the users.

What I want is a mail server that is kept up to date on security fixes and has some form of community to go to for help and possibly be easy to administer.

I have observed that Postfix offers a better community and seems to be more up to date on security vs. Qmail from other posts that I have read.

Any opinions would be greatly appreciated.

Thank you

---

### Post by foxylad on 2007-10-17
Postfix. Qmail has a small but fanatical following, but Postfix is far more popular partly because of the idosyncratic nature of Qmail's developer. 

The other contender is sendmail which was the standard mail server for a long time, but due to it's complexity and some security issues Postfix is the new king of the castle.

---

### Post by MJN on 2007-10-18
Couldn't have put it better myself.

By 'web interface' I assume you're talking about a webmail service in which case I recommend [Squirrelmail](http://www.squirrelmail.org). I'm sure there are prettier ones out there (although this one is skinnable and looking at what  [Nutsmail](http://www.nutsmail.com) have come up with it's got great potential) the beauty in my book for Squirrelmail is how fast it is, good plugin development to customise it to your needs, and reasonably easy to setup and administer.

Mathew

---

### Post by maw1key on 2007-10-18
Thank you Foxylad and MJN for your input.  This is why I am starting to love Ubuntu more and more, great help from the community and a lot of active users.

You were correct in assuming that I meant a webmail service for the users, and I have heard that squirrlmail is the best bet, but I'm open to any other suggestions there too.

Time to go and find that guide on installing Postfix now.

---

### Post by LanDan on 2007-10-19
i can't say anything bad about qmail because i never used it, i have been using postfix for more then a year now and i absolutely love it, so i can give you a positive recomendation on that one

my install is as follows
postfix
dovecot (pop + imap)
clamav
spamassasin
squirrelmail

thinking of trying roundcube instead of squirrel, eventhough squirrel looks ugly and is simple it just works

---

### Post by HermanAB on 2007-10-19
Qmail and Postfix are both very good and can handle millions of users.  However, setting up such a system is very complex, since you need to install the MTA, POP/IMAP, Authentication, Encryption, Web server and junk filters all separately.  This can take a long time to sort out and get to work smoothly.

A few months ago, I transitioned away from a Postfix system to Citadel and I haven't looked back: [http://www.citadel.org](http://www.citadel.org)

The difference is that Citadel is a complete system with a good Easy Install script.  It does absolutely everything out of the box and has a Berkeley database backend, so it is very efficient.  Now my server is just idling and the whole thing is zero maintenance.  It Just Works (TM).

Citadel is actually very old and therefore bug free.  The code is clean and well written ANSI C.  It installs in about 20 minutes so it is well worth a try.  Installing a Postfix, Dovecot and Apache with Roundcube based system will take days (and then you still won't have all the Citadel features!).

Cheers,

Herman

---

### Post by Xenaco on 2007-10-19
I set up virtual users and domains With Postfix, Courier, MySQL, SMTP-AUTH, Quota, SpamAssassin and ClamAV. This setup uses MySQL to store and maintain user names and domains databases.

A great resource for setting up this server with step by step instructions and commentary is:

[[COLOR="Navy"]Virtual Users And Domains With Postfix, Courier And MySQL (+ SMTP-AUTH, Quota, SpamAssassin, ClamAV)[/COLOR]]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier")

---

### Post by tkharris on 2007-10-19
I'll add my vote to Postfix.  Very simple and easy to use ( those who doubt this can go admin a sendmail box.  :) ).

Additionally for piointy haired bosses who don't like being in a mysql console or editing text files on the server there is: [http://sourceforge.net/projects/postfixadmin/](http://sourceforge.net/projects/postfixadmin/) ( I have not personally used this, but it's been vouched for by a number of other admins where I work ).

---

### Post by maw1key on 2007-10-19
Thank you everyone, Postfix it is.  The install went flawlessly, but setup will take a minute more.

I found a link to a guide from flurdy and it looks pretty solid and easy to read for a new linux user/admin.

---

### Post by tkharris on 2007-10-19
Have fun!  Make sure to use SASL authentication - you don't want an open relay!

---

### Post by garba on 2007-10-21
dont' even get me started on telling you how much i love postfix: it's a gem, although it's quite simple to set up take out some time to browse through its documentation and discover all its features, you won't regret it

---

### Post by viulian on 2007-12-02
For me it's qmail. I've been using Dan's tools for a while (very low memory footprint for cheaper VPS).

I decided to go with postfix for the new setup I am working with and it's pain. I mean yea, postfix works with the defaults, but if you try to make virtual mailboxes, you need myriad of tool and you'll spend two days trying to figure them out.

Each tutorial out there uses different tables, different columns, you must use cyrus-sasl for SMTP-AUTH, but then you need to decide weather to use courier-pop via SASL also, or 'standalone' (in which it uses the database itself). Then everyone seems to recommend maildrop as transport, but there's lot of confusion as you need to use it also in the database, where the default from postfix-admin is virtual: and so on.. Tons of messages around the web, try searching for maildrop: invalid username, or postfix trying to deliver mail for nonexisting aliases.
You need to edit around 6-7 configuration files (main.cf, maildroprc, mysql_virtual_*.cfg, master.cf) not mentioning the configs for cyrus/courier (3-4 more files). 
And to add more insult to the injury, even if the setup is prised for ease of configuration and integration, you have to type your database tables/username/password and server in almost all the files above over and over again. Useless.
Logging is also a pain, just a message telling that the message is not stored - then copy/paste and good luck hunting on Google.

For those who decide to still run postfix, the only advice is 'follow one tutorial' and only one! If that doesn't make it happen, trying to figure stuff out from others will most likely confuse you. It did for me.

I just removed all the packages, db, config files, web admin. I'm going back to qmail.

Did you know that qmail is [public domain](http://cr.yp.to/qmail/dist.html) ?
 Everyone will be able to distribute it now. Just a bit and there will be some lovely packages around.

---

### Post by DDuong on 2007-12-02
I recommend Postfix.  And my reason is the community.

---

