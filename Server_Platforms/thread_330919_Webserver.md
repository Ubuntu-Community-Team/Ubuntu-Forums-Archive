---
title: "Webserver"
date: 2007-01-03
forum: Server Platforms
---

### Post by mulligan.can on 2007-01-03
G'day,
I am interested in setting up a couple of spare pc's at home so that they can be used as a web host.

The site needs to be fully accessible from behind my router and at present I have an entry in /etc/hosts to allow this. (I have a rudimentry server up and running to see how well my internet handles it, so far so good :))

Anyway. I would like to be able to have a proper fully qualified domain name pointing to my (regrettably) dynamic ip. 

I am using dyndns to access it remotely through through one of their subdomains.

I was thinking about using there services to buy the domain name and point it to myself however I would rather try and find another alternative at present as I dont have easy access to a credit card and would rather not try and get one and they dont list paypal as a method of payment :(.

anyway, i think i may have not given enough information but any pointers would be nice.

im thinking one pc for a fileserver/dns/email server and one for mysql/apache. i think that would work as at present i am only wanting to devote to pcs (they are fairly old but i was thinking the faster of the two for apache/mysql?) but should be able to handle low amounts of traffic.

is this a good idea? or should i set it up differently? (going to use nfs to share files between machines on the network, is that a good idea?)

thanks :D

---

### Post by kidders on 2007-01-04
Hi there,

> **mulligan.can said:**
> I was thinking about using there services to buy the domain name and point it to myself however I would rather try and find another alternative at present as I dont have easy access to a credit card and would rather not try and get one and they dont list paypal as a method of payment :(.Hmm... *somebody* you know must be willing to let you use theirs. It might be tough to find a company willing to accept other kinds of payments :-( Your plan sounds good though -- although I didn't buy it from them, I'm currently using DynDNS to point a domain name at my dynamic IP, and I'm quite happy.

> **mulligan.can said:**
> im thinking one pc for a fileserver/dns/email server and one for mysql/apache.The only difficulty you might encounter has to do with the fact that, by splitting your services over two machines, you're effectively doubling your failure probability. It might be worth setting up all your services on both PCs, and exploring ways of sharing them out and consolidating them, in the event one of your machines died. If, for instance, you decided you wanted to take one of your computers offline for an hour, it would be nice to be able to quickly transfer all services to the other.

If you install a server version of Ubuntu (or any other distro), you should have no trouble using older machines ... even a 400 or 500MHz PII, for instance, should be well capable of handling a reasonable load. In filesharing terms, there's not a lot wrong with NFS. :-) Depending on the other machines on your network, you may prefer to use Windoze or Apple filesharing ... or combinations of the three.

**Edit:** Since you're thinking of exposing services to the internet using old machines, you might want to give a little thought to how they would handle malicious activity. One undesirable side-effect of using services like DynDNS is that they tend to attract it. :-( While a modern PC might be able to handle it more gracefully, boxes with limited resources can grind to a halt quite quickly when exposed to DoS-style attacks over HTTP or SMTP. You could, for instance:

[LIST]
[*]Limit the amount of CPU time processes like apache or postfix are allowed to gobble up.
[*]Cap the number of child processes they can spawn.
[*]Allocate *lots* of swap (maybe 1GB for a PII with 256MB RAM) to ensure that the kernel won't ever have to kill processes to free up memory during an attack. You would create the swap in two or three chunks, and instruct the kernel to use them sequentially.
[/LIST]

---

### Post by nihilocrat on 2007-01-04
[www.cjb.net](www.cjb.net) is also a decent free DNS service. You should really go for the 'free' route as you just start out. Your situation might be different, but I did the whole 'home server farm' thing when I was in high school and didn't feel like spending money on something perhaps 10 people would visit.

[QUOTE=kidders]
Cap the number of child processes they can spawn.
[/QUOTE]
This seems like the easiest and most sensible thing to do, particularly if you don't forsee the webserver/mailserver being used by more than x number of people at once.

---

### Post by mulligan.can on 2007-01-04
Ok, i was just thinking as i plan on using older machines (ones a p3 500, dont remember the other one) maybe having one as the email/file server and the other to run apache/mysql would lighten the load up a little.

ok, yeah, i didnt give security a great deal of thought, was thinking more along the lines of security by obscurity :S

the main reason i was thinking about using two machines is they are old and fairly slow and so having dns/email/mysql/apache on just the one may slow it down too much. but if you think it would be able to handle may as well just go with one.

could have the web document root, email and mysql databases on another machine and share them via nfs? this fileserver could then have mysql/apache and all that setup on it but latant so that if need be i can just enable all the services and swtich it in as the primary. does this make sense?

---

### Post by kidders on 2007-01-05
> **mulligan.can said:**
> Ok, i was just thinking as i plan on using older machines (ones a p3 500, dont remember the other one) maybe having one as the email/file server and the other to run apache/mysql would lighten the load up a little.I suppose it all depends on your load averages. You could, for instance, start with your 500MHz PIII, and after a day or two, ask for your load stats with **uptime** or something. If you get big ugly numbers, you can add your second box.

Often, old PCs will really show their age when they perform I/O operations ... especially if the hard disks are old too. You might find, for example, that when someone requests a web page from you, and your apache, mysql, etc. all fire up simultaneously, that there's a slight lag. (The "%wa" indicator in **top** might help you see it.) One possible way of improving performance might be to put your /var/lib/mysql on a different physical disk, so it could be accessed in parallel (well ... *almost* in parallel).

It would certainly be worth doing something like that with your swap. For example, if you put 256MB of swap each on three different hard disks, and gave all three partitions the same priority, they would, in theory, operate in parallel.

I guess my point is that, with a little planning, you should be able to add together a whole lot of little performance tweaks to make a tangible difference to how much you can do with a single machine. Nihilocrat's opinion would be interesting, though.

> **mulligan.can said:**
> ok, yeah, i didnt give security a great deal of thought, was thinking more along the lines of security by obscurity :SIt's at least worth paying lip service to the security issue, but there's no need to get preoccupied by it, imo. 

For instance, I wrote a little script that monitors my system logs and does **iptables -I INPUT .... -j DROP** to IP addresses that do stuff like bombard my mail server with crap, or repeatedly fail to log in over SSH. It fires about twice a day. (Japanese, Chinese and Korean IPs are its favourite hehe.)

I wrote it after I got up one day to find that my (carelessly configured) postfix was swimming in crap and was refusing to queue *anything*, thanks to some b*****d using the same ISP as me.  Because it was running on an older box, the kernel had killed quite a few processes (web server, etc.) in a vain attempt to recover enough RAM to deal with the mess. Needless to say, I was ... ehh ... annoyed.


> **mulligan.can said:**
> Could I have the web document root, email and mysql databases on another machine and share them via nfs?Yep... you could certainly do that if you wanted to, although you *might* want to check how MySQL would behave over NFS. Afaik, that specifically is something you shouldn't take for granted.

I once went one step further than that ... mostly for the sake of learning how ... and set up AoE, with RAID1 sitting on top, in a similar situation. That meant that all my machines always had a complete copy of certain data, rather than just one of them. I looked upon it as a handy way of making real-time backups of data that was constantly changing. I imagine it would be totally silly for you to try it though. Hehe.

---

### Post by Brazen on 2007-01-05
Just FYI, you could use a debit card instead of a credit card.  Debit cards take out of your checking account, so you must HAVE the money before you can spend it, which is most peoples problem with a credit card.

However, I too would suggest not wasting money on a little home set up.  Stick with the free services until you are all set up and comfortable with how things work.

---

