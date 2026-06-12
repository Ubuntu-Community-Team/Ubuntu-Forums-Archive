---
title: "Instant Messenger Server"
date: 2008-06-30
forum: Server Platforms
---

### Post by Hazardr on 2008-06-30
Hi

Is it possible to create an IM server on Ubuntu 8.04? if yes, which software is used?

Thanks

---

### Post by heebus on 2008-06-30
Check out jabber.  You can find it at [http://www.jabber.org](http://www.jabber.org)

---

### Post by Robstarusa on 2008-06-30
Openfire works _very_ well as well and it is now free. (Not sure if it is OSS)

---

### Post by viniosity on 2008-06-30
I use ejabberd: [http://www.urbanpuddle.com/articles/2008/05/28/setup-ejabberd-on-ubuntu-hardy-heron](http://www.urbanpuddle.com/articles/2008/05/28/setup-ejabberd-on-ubuntu-hardy-heron)

---

### Post by Hazardr on 2008-07-02
I installed Ejabberd but i cannot get gajim to connect to it. Is there a guide on that too? thanks

---

### Post by viniosity on 2008-07-02
I using Pidgin but maybe the settings here can help you:

Protocol: XMPP
username: <your username>
domain: <the domain you setup.. e.g. redplume.foo.com>
Connect Port: 5222
Connect server: <probably the same as domain>
Allow plaintext auth

The tricky thing is the domain. If you didn't use a fully qualified domain name then the user may need to be setup like user@redplume instead of [email]user@redplume.foo.com[/email] or whatever.

---

### Post by abuthemagician on 2008-07-02
We are using openfire here where i work, and i had it up and running in less than the time it takes to install Ubuntu. Its running on a Dell Optiplex GX240 with a 1.6ghz P4 and a gig of ram. We only have 75 users but the system seems to be running really well. The only thing I don't like is the startup with windows option doesn't work, and the client is java based so it takes up about 5-10mb of ram in windows. Although in Ubuntu i just use pigdin which doesn't let me use some of the features, but why do i care?

---

### Post by amenszer on 2008-07-02
I also set up openfire in a corporate setting, have the clients connecting via pidgin. It works well.

I think this is the guide I used to do it:
[http://www.igniterealtime.org/community/thread/28325]("http://www.igniterealtime.org/community/thread/28325")

I used postgreSQL instead of MySQL though...just out of preference.

---

### Post by Hazardr on 2008-07-02
i got it to work, thanx, i used ejabberd with gajim, will try with Pidgin now

---

### Post by FlintZA on 2008-10-10
Hi,
I'm also trying to get ejabberd up and running but I'm having some trouble.

I have installed, configured and started ejabberd on my Gutsy 7.10 Desktop installation. I followed the guides at [http://sysmonblog.co.uk/?p=11](http://sysmonblog.co.uk/?p=11) (without the forced ssl) and [http://www.urbanpuddle.com/articles/2008/05/28/setup-ejabberd-on-ubuntu-hardy-heron](http://www.urbanpuddle.com/articles/2008/05/28/setup-ejabberd-on-ubuntu-hardy-heron). 
With server setup in the .cfg as {hosts, ["mydomain.com"]}.
And user added as ejabberd register username mydomain.com pass123
The server starts up, and viewing the web interface, the user has been added. However when I try to set up and connect pidgin (on the same machine) as below, it reports "username@mydomain.com/Home disconnected: Read Error".
The pidgin logs are empty, can anyone suggest what I may be doing wrong-or where I can look for the ejabberd logs?

My pidgin config:
[Basic]
Protocol: XMPP
Screen name: username
Domain: mydomain.com
Resource: Home
Password: pass123
Local alias: empty
Remember password: checked
[Advanced]
Require SSL/TLS: unchecked
Force old (port 5223) SSL: unchecked
Allow plaintxt auth: unchecked
Connect port: 5222
Connect server: localhost (I have tried the machine's IP here as well, and mydomain.com)

Any help would be greatly appreciated :)

---

### Post by FlintZA on 2008-10-10
Sorry for the double post :/

I just tried setting up a connection from Digsby on my Windows machine, and that does connect. I can't get pidgin to connect though. The difference seems to be that on Digsby I need to specify "No Encryption" and there is no equivalent in pidgin. Any ideas?

---

