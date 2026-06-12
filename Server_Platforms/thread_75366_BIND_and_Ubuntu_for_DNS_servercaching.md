---
title: "BIND and Ubuntu for DNS server/caching"
date: 2005-10-13
forum: Server Platforms
---

### Post by herot on 2005-10-13
i installed bind and it seems to run fine.
however, i am trying to learn bind using this: [http://www.tldp.org/HOWTO/DNS-HOWTO.html](http://www.tldp.org/HOWTO/DNS-HOWTO.html)
and it seems that some of the files are in different places in my directory structure after installing bind.  ie: /var/named/root.hints SEEMs to be /etc/bind/db.root
and doesn't have the 
$TTL 3D
@               IN      SOA     ns.linux.bogus. hostmaster.linux.bogus. (
                                1       ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                1D)     ; Minimum TTL
                        NS      ns.linux.bogus.
1                       PTR     localhost.
section, or the 
key rndc_key {
    algorithm "hmac-md5";
    secret "c3Ryb25nIGVub3VnaCBmb3IgYSBtYW4gYnV0IG1hZGUgZm9yIGEgd29tYW4K";
};

options {
    default-server localhost;
    default-key    rndc_key;
};
section.  
perhaps i have missed some important configurations before trying to follow along with this howto?? can some one give me a pointer?

---

### Post by ScatterBrain on 2005-10-13
So exactly how are you going to be using this DNS server?  As a local caching server, or to host your domain?

---

### Post by herot on 2005-10-13
well prolly a little of both! 
its kinda just an experiment right now, i have an end goal of hosting my company's website AT the company as opposed to paying a monthly fee to someone to have it hosted...
does that properly answer your question?

put it this way... i wanna learn how to do it BOTH ways.

---

### Post by Glut on 2005-10-14
Unless you have amazingly high fees for DNS hosting, could I strongly suggest not doing it yourself?
DNS is incredibly important and if you make the slightest mistake your company could lose all name services. This tends to make bosses cranky and may shorten your tenure quite considerably.

If you absolutely must do it, I suggest getting some training first. It's not worth just playing around with it and hoping that it works. Secondly, make sure that you have appropriate hardware. The standard is to have 2 servers, independant of any other services on different power grids with the usual redundancy in place.
Thirdly, you will find that Ubuntu and Debian have *very* similar DNS setups (read identical), there are plenty of Debian How-tos available for this.

---

### Post by ScatterBrain on 2005-10-14
To provide DNS caching - ie, not depend on your ISP's DNS servers to get IP resolution for google.com - then all that you should have to do is install Bind:

```
sudo apt-get install bind9 dnsutils
```

*I always throw in dnsutils for troubleshooting, etc.  When I'm complete, I remove them.*

Once installed, you can point your internal machines to this machine's IP and boom you have an internal caching DNS server.

As for hosting your company's DNS, first be sure to read Glut's post as there are very serious considerations you have to make and he's pointed out several of them.  If after you consider all of that and you decide you still want to go there, I'd start with this document:

[http://www.debian.org/doc/manuals/network-administrator/ch-bind.html]("http://www.debian.org/doc/manuals/network-administrator/ch-bind.html")

That sould give you a pretty good foundation.

---

### Post by herot on 2005-10-14
well cant i set it up at my house and then learn and work on it there that way if i screw something up, the comapny wont be involved...

maybe this will help, right now my company has an isp that we get our DNS hosting from, i guess my question is how can i use BIND to increase performance and/or save the company a little money...

What i am looking at is there is a large college near here and i think they host all their own webservers and DNS servers... Well why cant I do that?

i wanna host my OWN domain

---

### Post by ScatterBrain on 2005-10-14
[QUOTE=herot]Well why cant I do that?

i wanna host my OWN domain[/QUOTE]

Nothing says you can't.  You just need to make sure that it's done right so as to to negatively affect your company, and then your job.

By all means try it at your house.  That will give you experience.  Read the Debain DNS doc I sent you and go for it.  Just be **ready and prepared** when you install it at the office.  DNS is a vital part of what makes TCP/IP work.  You don't want to have your network unable to function, right?

---

### Post by herot on 2005-10-14
yes you are right it needs to be planned out fully
ill give it a go at home thanks :)

---

### Post by LordHunter317 on 2005-10-14
[QUOTE=herot]well cant i set it up at my house and then learn and work on it there that way if i screw something up, the comapny wont be involved...[/quote]That's wonderful, but your company doesn't have the proper resources for Internet facing DNS.

If you don't have two seperate racks on seperate circuits with backup power, and two seperate connections to upstream ISPs with different peering points, you're not equipped to run your own Internet-facing DNS.

End of story.  Understand if DNS goes down, no one on the Internet will beable to access your websites.

> i guess my question is how can i use BIND to increase performanceYou can't.

> and/or save the company a little money...Savings realized will be lost if/when DNS fails.  It's really a 100% uptime service, which is why most of us with experience wiht it tell everyone, "Make it someone else's problem".

> What i am looking at is there is a large college near here and i think they host all their own webservers and DNS servers... Well why cant I do that?Because they have resources and capacity you likely do not.

As for helping you on your quest, I recommend you read the documenation in /usr/share/doc/bind9 first, to understand how Debian's bind9 install is different from a stock bind9 install.  Also, learn how to make it work under chroot.  If you're not running bind9 chroot, you're not qualified to do DNS.

---

### Post by pingswept on 2005-10-15
[QUOTE=herot]i guess my question is how can i use BIND to increase performance and/or save the company a little money...
[/QUOTE]

I work at a small school. I agree with the advice above that it's a terrible idea to try to save money by running your own DNS.

We're running a local caching DNS server on Ubuntu. It also resolves some hostnames in our domain to servers on our intranet. This doesn't save us money at all, as we still have to pay for DNS, but it makes setting up intranet sites easy.

For example, if one of our math teachers wants to put some math stuff he wrote up on a website, so I add math.ourschool.edu to our db.local file, add a virtual host to Apache, and he's ready to go. It's been working well, and it's surprising how much latent desire for websites its uncovered.

Previously, I would give out IP addresses and subdirectories, which people forget. I could do the same thing with our external DNS, but it would require dealing with the hosting company, and for everyone outside our firewall the names, which resolve to addresses in RFC 1918 space, would direct them to the wrong place.

Also, one comment about caching improving performance: I've found that while I lookup times for cached names has gone from around 25 ms down to 5 ms, our response time for non-cached names (for which our server has to go ask someone else) has risen to 70 ms or so. It's not clear to me whether that's a win or not, as I'm not sure how to determine what percentage of our requests are for cached names. It's a win for me personally, as I'm just sitting here clicking refresh on the Ubuntu Forums all day, but for the rest of the school . . .

---

### Post by diebels on 2005-10-26
[QUOTE=LordHunter317]That's wonderful, but your company doesn't have the proper resources for Internet facing DNS.

If you don't have two seperate racks on seperate circuits with backup power, and two seperate connections to upstream ISPs with different peering points, you're not equipped to run your own Internet-facing DNS.

End of story.  Understand if DNS goes down, no one on the Internet will beable to access your websites.
[/QUOTE]I've registered two domains and my registrar provides secondary nameservers free of charge. So if I'm running the primary, and it goes down for a while, the secondary still answers.
Doesn't most registrars provide secondary nameservers free of charge?

---

### Post by LordHunter317 on 2005-10-27
Depends.  Some do, some don't.   Some charge a fee.

If you have hosted secondaries, then yes, running your own primary is fine.  But it still needs to be treated like the 100% uptime service it is.

However at that point for most small companies anyway, I just get totally free DNS for them for one of the many providers and deal with it.

It's only a problem if you need to do zone updates literally all the time (internal DDNS or similiar).  Which probably shouldn't be going on for Internet facing servers.

That's all.  I just don't see the value in most situations (especially for SMB) of  hosting half the job.

---

