---
title: "filter  /block some content that some users can see on the lan"
date: 2007-10-02
forum: Server Platforms
---

### Post by twistedtwig on 2007-10-02
Hi all,

I don't know if this is possible and how I would do it.... I am guessing (hoping not as have no idea how to do it!), but guessing I would need ldap or something.... anyway I would like content filtering on my webserver for the lan...

EASY you say... use danguard, willow or squid with squid guard...

and I hear ya!

but what would I do if I say I would like my kids to be filtered on one set of rules and my self and my partner to be filtered on another, if at all.  I don't want it to be a proxy on their browsers as they will figure that out easily.

I have xp and ubuntu desktops within the network.

Thanks for any ideas and thoughts.

Twiggy

---

### Post by HermanAB on 2007-10-02
Dansguardian or SquidGuard can do what you want.  Here is an old guide:
[http://www.aeronetworks.ca/squidguard-howto.html](http://www.aeronetworks.ca/squidguard-howto.html)

Cheers,

Herman

---

### Post by twistedtwig on 2007-10-03
thank you for the info, very helpful.

Can I ask, it says to authentic the user you setup a .htpassword file.  This seems fine for a small number of users but would seem like it could become unmanagable pretty quickly.

Also when you type in the username and password for the first time does it ALWAYS remember it or just for that session.  If you close the browser, or log off.. or reboot the server would it forget it, or is it a once only deal for each user / computer?

---

### Post by twistedtwig on 2007-10-04
bump.... wondered if anyone knew anything about what I asked above.

Thanks

---

### Post by twistedtwig on 2007-10-07
Can I ask, it says to authentic the user you setup a .htpassword file. This seems fine for a small number of users but would seem like it could become unmanagable pretty quickly.

Also when you type in the username and password for the first time does it ALWAYS remember it or just for that session. If you close the browser, or log off.. or reboot the server would it forget it, or is it a once only deal for each user / computer?

---

### Post by HermanAB on 2007-10-07
Anything you do in htaccess can also be done in the main configuration files.  You can also hook Apache into PAM and then use any other authentication method.  

This 'other authentication method' can be Active Directory (gawd forbid), NIS, or a zoo of other methods:
[http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

'Hope that helps!

H.

---

