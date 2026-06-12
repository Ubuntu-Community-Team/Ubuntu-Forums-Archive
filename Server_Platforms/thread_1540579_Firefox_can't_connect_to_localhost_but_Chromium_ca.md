---
title: "Firefox can't connect to localhost but Chromium can"
date: 2010-07-28
forum: Server Platforms
---

### Post by bailewen on 2010-07-28
I'm totally mystified. 

After spending what seems like an eternity trying to learn how to host a couple of webpages on my laptop for no better reason than to practice creating them without paying for a server. . .for the time being, I kept getting the usual errors (stuff I have seen lots of tutorials on) and this time kept getting 

"The connection was refused when attempting to contact localhost"

Just by random chance I happened to open up Chromium for one of my attempts and low and behold, I get the much awaited 
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
I can even login to phpMyAdmin from Chromium. So what's going on with Firefox? Doesn't work in Seamonkey either. 

Thanks in advance for any help. :(

p.s. Using 10.04

---

### Post by cdenley on 2010-07-28
What is this output?
```

getent hosts localhost

```

---

### Post by bailewen on 2010-07-29
Thanks for taking a stab at it. Mysteriously, when I booted up this morning, it was all normal and I could log on with whatever browser I wanted. I wish I knew what happened but now the question has become academic. ;)

Anyways, what were you planning on checking with the getent command? This is what it produces at the moment:

> ::1             localhost ip6-localhost ip6-loopback

---

### Post by bailewen on 2010-07-29
The problem came back. After that last post I shutdown the computer, ran some errands and now when I go to [http://localhost/wordpress/wp-admin/](http://localhost/wordpress/wp-admin/) in Firefox, all I get is:
> Unable to connect

Firefox can't establish a connection to the server at localhost.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

In Chromium I get the logon screen.

 *getent hosts localhost * still returns:

> ::1             localhost ip6-localhost ip6-loopback

---

### Post by cdenley on 2010-07-29
Have you disabled IPv6 in firefox somehow? Try commenting out this line in /etc/hosts.
```
[COLOR="Red"]**#**[/COLOR]::1     localhost ip6-localhost ip6-loopback
```

---

### Post by tacitdynamite on 2010-09-20
I had this bizarre problem after I created a named virtual host in apache and then edited hosts file so that "localdev" was appended to the lines beginning "::1" in /etc/hosts. [http://localdev/](http://localdev/) showed up in Chrome but not in Firefox, even after restarting Firefox. Then I figured it out because Firefox still responded to [http://127.0.0.1/;](http://127.0.0.1/;) Firefox and Chrome parse the /etc/hosts file different. Webkit pays attention to the ::1 line, but Firefox pays attention to the 127.0.0.1 line in /etc/hosts. I appended localdev to the line beginning 127.0.0.1 in /etc/hosts, restarted Firefox, and now it's working.

---

### Post by LightningCrash on 2010-09-20
can you paste the output of
route -n


?

---

### Post by tacitdynamite on 2010-09-22
Does route -n contain sensitive info? I can't tell.

---

