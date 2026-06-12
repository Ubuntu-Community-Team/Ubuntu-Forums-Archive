---
title: "Mailing list software. Suggestions?"
date: 2007-05-09
forum: Server Platforms
---

### Post by Nano on 2007-05-09
Hi everybody.
My next goal in my company would be to migrate the newsletters campaigns software to an Ubuntu box (from which I'm typing right now).

Does any of you use software to manage different mailing lists, send newsletters, unsubscribe features, etc?

Something to recommend?

Thanks a lot in advance,

Nano

---

### Post by fakie_flip on 2007-05-09
Use mailman with sendmail.

---

### Post by Bill007 on 2007-05-09
PHP List this is great for managing mail lists and email campaigns

[http://www.phplist.com/ ]("http://www.phplist.com/") 

there is a learning curve but to make this your self hMMMM  I could

but hell why re invent the wheel

Bill007

---

### Post by Brazen on 2007-05-09
[Maillman with Exim4]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html#mailman"), of course.  I use it here at work for mailing lists and newsletters (only newsletter source allowed to email the list).

---

### Post by shane2peru on 2008-04-04
Ok, this looks like some good info, can anyone offer any sort of help setting up phplist?  I currently use it on my webserver, however I always have problems with it, and they offer NO SUPPORT for it.  It is a Linux Server that I pay for, and I'm really interested in setting this up to run off my box, I think that would be better.  Any help would be appreciated.

Shane

---

### Post by jfdill_2 on 2008-04-11
I have managed lists with mailman, the largest list that I have managed has about 45,000 recipients.  My 2c is that mailman is good for interactive discussion lists, but not so great for "post only" announcement / mail campaign type lists.  I have been looking at alternatives and will probably go with phplist, but haven't tested it yet.

As for MTAs, for small lists, exim4 is the easiest to set up.  postfix is easier to work with if you end up needing to tweak for performance or enhance spam filtering etc.  I have managed several sendmail servers, but you have to practically learn a different language to understand more advanced configuraiton.  I typically use postfix with amavis, spamassassin, clamav, and postgrey.  For a simple server with a single domain (and no virtual domains) Kolab looks interesting, I have played with it, but ended up using RavenCore because I needed multiple virtual domains.  RavenCore is more like a configuration management tool, lives in Perl separate from the OS.

Also, if you have more than a few hundred people on the lists, it's important to think about:  a) bandwidth of your internet connection; b) how powerful is your box; c) if your internet provider may place any restrictions on you sending and receiving e-mail via your internet connection.  Also, set up will be easier and more reliable if you have a static IP with proper DNS records (A and MX and SPF) set up for your domain.

I have no idea how things work in Peru, but here in the US, many ISPs will block traffic to / from port 25 except through their relay, and if you send above a certain amount of traffic, they may decide that your box is a spambot and cut you off.  Some Terms of Service for home internet connections may specify that you not run a server.  Generally, you will need a business class connection with a static IP.

PS I am certain that somebody can tell a story how they have mailman with thousands of subscribers running from their home internet connection and how it is all happy sunshine, well good for them, but I would consider myself very lucky in that case, there's no guarantee that your ISP won't decide to crack down on e-mail at some point.

---

### Post by shane2peru on 2008-04-11
> **jfdill_2 said:**
> I have managed lists with mailman, the largest list that I have managed has about 45,000 recipients.  My 2c is that mailman is good for interactive discussion lists, but not so great for "post only" announcement / mail campaign type lists.  I have been looking at alternatives and will probably go with phplist, but haven't tested it yet.

As for MTAs, for small lists, exim4 is the easiest to set up.  postfix is easier to work with if you end up needing to tweak for performance or enhance spam filtering etc.  I have managed several sendmail servers, but you have to practically learn a different language to understand more advanced configuraiton.  I typically use postfix with amavis, spamassassin, clamav, and postgrey.  For a simple server with a single domain (and no virtual domains) Kolab looks interesting, I have played with it, but ended up using RavenCore because I needed multiple virtual domains.  RavenCore is more like a configuration management tool, lives in Perl separate from the OS.

Also, if you have more than a few hundred people on the lists, it's important to think about:  a) bandwidth of your internet connection; b) how powerful is your box; c) if your internet provider may place any restrictions on you sending and receiving e-mail via your internet connection.  Also, set up will be easier and more reliable if you have a static IP with proper DNS records (A and MX and SPF) set up for your domain.

I have no idea how things work in Peru, but here in the US, many ISPs will block traffic to / from port 25 except through their relay, and if you send above a certain amount of traffic, they may decide that your box is a spambot and cut you off.  Some Terms of Service for home internet connections may specify that you not run a server.  Generally, you will need a business class connection with a static IP.

PS I am certain that somebody can tell a story how they have mailman with thousands of subscribers running from their home internet connection and how it is all happy sunshine, well good for them, but I would consider myself very lucky in that case, there's no guarantee that your ISP won't decide to crack down on e-mail at some point.

Wow, that is a lot of info.  I'm only looking for a way to send emails to 100-200 people every month or so.  :)  On my web page I use phplist, however I keep running into problems with it setup there, so I figured I may like to get it setup on my own server.  My ISP doesn't block port 80, so I don't know if that would mean that 25 would be open or not.  It is basically control, being setup on server that currently hosts my web page only allows 100 emails to be sent, so I'm up against a wall there.  If I run it on my own computer (I have a 64 bit setup) I don't think it will drain my system too much, and I will learn more, and have more control over what is going on with it.  Perhaps I'm in over my head?  I have successfully got my server setup as a web server, and am contemplating doubling it as a mail server for this purpose.  Thanks for the response.

Shane

---

### Post by jfdill_2 on 2008-04-11
> **shane2peru said:**
> Wow, that is a lot of info.  I'm only looking for a way to send emails to 100-200 people every month or so.  :)  On my web page I use phplist, however I keep running into problems with it setup there, so I figured I may like to get it setup on my own server.  My ISP doesn't block port 80, so I don't know if that would mean that 25 would be open or not.  It is basically control, being setup on server that currently hosts my web page only allows 100 emails to be sent, so I'm up against a wall there.  If I run it on my own computer (I have a 64 bit setup) I don't think it will drain my system too much, and I will learn more, and have more control over what is going on with it.  Perhaps I'm in over my head?  I have successfully got my server setup as a web server, and am contemplating doubling it as a mail server for this purpose.  Thanks for the response.

Shane

For 100-200 users your box and internet connection should be fine.  If you can set up an e-mail client that uses a "remote" SMTP server for eg. the one at your web host in Thunderbird or Evolution, that should be a good test if you can send mail or not.  I suggest that you check the Terms of Service for your internet connection, just to be on the safe side, that will avoid some nasty surprise later.

If you have more than one recipient at some ISP, sometimes there is a way to "bundle" those messages together so one message goes from your server and then gets "expanded" at the remote server, I forget the precise term for that now, that will cut down a lot on the traffic, I know it works with mailman and postfix, probably some way to do it with phplist.

One other thought is some mail servers will check a Realtime Blackhole List (RBL) that lists DSL providers to block messages that are sent directly from home type DSL connection e.g. to block mail from "spambot" on somebody's home computer, in that case you should get some bounce message, typically with more information about why you are being blocked but not always.  It's just something to keep in mind if somebody complains they do not get your mailing, you might not have that problem at all.

PPS you should definitely set up "postmaster" and "abuse" e-mail address for your domain those are required by RFC, also your ISP may have some mechanism for sending abuse complaints to you, but for only 100-200 recipients that may not be an issue.

---

