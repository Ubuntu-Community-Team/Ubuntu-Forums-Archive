---
title: "Use 6.06 LTS server or wait for 8.04?"
date: 2007-12-19
forum: Server Platforms
---

### Post by lodp on 2007-12-19
Hi,

I saw a very attractive offer from a german hosting company (server4you.de), which had Ubuntu 6.06 as an option.

Now I'm wondering whether I should take that offer now, or wait for 8.04 LTS instead. Upgrading from 6.06 to 8.04 on an up-and-running server is not something that would be advisable, I suppose.

What do you think?

---

### Post by Sef on 2007-12-19
I would wait for 08.04 because it will be supported for 5 years instead of 3 years like Dapper, 6.06.  (Dapper has almost been out for 2 years.)

---

### Post by p_quarles on 2007-12-19
I think it really depends on what you will be doing with with this server.

If it's going to be a database/application server with a lot of complicated setup then, yeah, you're going to want the longest term of support possible. If it's a simple file server, the upgrade cycle is of less concern. 

A couple things to keep in mind: Ubuntu 6.06.1 server edition is currently scheduled for end of life in June 2011. It's entirely possible that your server needs will have changed enough by then that you'll have to reconfigure it anyway. What's more, there's no absolute guarantee that 8.04 will be released on schedule. 6.06 was released two months late, after all. 6.06 also has the advantage of being a time tested distribution, whereas a new release is highly likely to have bugs that will be worked out in the months following its release. 

If you do need indefinite uptime, though, I would recommend a rolling release distro like Debian Stable. It's easy to figure out if you're already used to Ubuntu, and its packages will remain more up-to-date (never bleeding edge, though) than an Ubuntu LTS edition.

---

### Post by PinkFloyd102489 on 2007-12-19
I just went ahead and installed Gutsy for server. I'll upgrade when Hardy comes out.

---

### Post by lodp on 2008-01-10
Thanks for your input on this..

I guess updating a production server from 6.06 to 8.04 eventually is an absolute no-go, isn't it? Do other distros recommend dist-upgrading a production server?

I mean, I could deal with a couple of hours of downtime, even 24h if need be, but anything beyond that would be pretty painful..

EDIT: The tasks of the server will mainly be in the PHP+MySQL arena.

---

### Post by MJN on 2008-01-11
6.06 to 8.04 should, in theory, be relatively painless. However, of course, in theory there is no difference between theory and practice - but in practice there is!
 
Furthermore, given an LTS dist-upgrade (i.e. upgrading a distribution without going via the intermediate releases like 'normal') has never been done before on Ubuntu - the 8.04 LTS release will be the first opportunity to do this en masse.
 
Only you can assess the importance of keeping your server(s) up, with the minimum downtime. And only you know your acceptable long-term timescales of when you want to be up-and-running by - I certainly wouldn't consider going for 8.04 on immediate release if your uptime is mission critical - and indeed your ISP is unlikely to offer it as a supported platform unless their marketing guys get the final word. Remember, downtime is not just a measure of your server being offline, but can ultimately include it not functioning to meet the requirement.
 
Mathew

---

### Post by mmichalik on 2008-01-11
Matthew brings up a couple of good points.

I myself have 2 6.06 servers and I will be upgrading them to 8.04 when it comes out but, only after 1 full calendar quarter has passed.

I figure three months will give enough time to flush out all the major issues with the release.

---

### Post by lodp on 2008-01-22
> **mmichalik said:**
> I myself have 2 6.06 servers and I will be upgrading them to 8.04 when it comes out but, only after 1 full calendar quarter has passed.

So you'll just hit "apt-get dist-upgrade" and hope for the best then?

I'll be getting the 6.06 server soon, and I'll have a couple of days before I put it "live" -- do you think it would be smart to take the opportunity and upgrade to 7.10 at this point?

---

### Post by lodp on 2008-01-24
Didn't get the server at last, turns out you have to be German to get it.

Now I got a nice offer for a server that has 7.10 pre-installed, but only as a "minimal Installation", with only SSH pre-configured. Is setting up LAMP and webmin a big deal? I did set up LAMP on my desktop once, and it was as easy as 1-2-3. But I didn't host any domains or run a DNS server then. Is that hard to do?

---

### Post by mmichalik on 2008-01-26
setting up a LAMP server isn't really any more difficult on the server, then it was to do on your desktop.

Webmin is easier to set up.  All you need to do there is go to [www.webmin.com](www.webmin.com), download the debian pacakage and follow the install instructions.  Super simple.

Adding additional programs, packages and services is easy to do. apt-get or synaptic work very well on the servers.  And don't forget that you can always reload 7.10 onto the new machine (for a full install) or even replace it with 6.06 if you want.

I have a 7.10 machine in our network and it runs fine.  We use it for network storage, backup, database and an ERP program and it hasn't had an issue at all.  And, in the scheme of things, will probably be easier to upgrade to ver. 8 when it comes out.

Setting up the DNS isn't difficult but you do have to understand what you are doing in order to make it work right.  If your network is setup correctly and ready to accept a DNS service, the easiest route is to install the DNS packages (BIND-9, I believe) and then administer it via webmin.

---

### Post by ssam on 2008-01-26
> **lodp said:**
> So you'll just hit "apt-get dist-upgrade" and hope for the best then?

I'll be getting the 6.06 server soon, and I'll have a couple of days before I put it "live" -- do you think it would be smart to take the opportunity and upgrade to 7.10 at this point?

best not to use dist-upgrade.

ubuntu has update manager which makes updating safer
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

it does things like check there is enough free disk space, sorting out source.list, removing superceded packages etc

---

### Post by lodp on 2008-01-26
Thanks so much for your input, people.

I'll be getting my server with 7.10 on Monday. I probably won't have to set up my own DNS server, as the host offers external DNS for a very small fee.

Now, since the host's offer says "Ubuntu 7.10 (minimal installation)" I'm wondering whether it's even possible that a 7.10 system comes without LAMP already set up. The funny thing is the pricing sheet says it explicitly for other distributions (like, "Debian Etch (LAMP)").

If it's not already set up, what packages do I install to get there? On my Desktop, I just downloaded the XAMPP package from apachefriends.org, extracted it to /opt and started it -- i suppose that's not how you do it in the server distribution, is it?

---

### Post by ssam on 2008-01-26
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) should get you started

---

### Post by lodp on 2008-01-30
Thanks for that link, the instructions there helped me a lot.

However, the intructions on PHP there are a bit out-dated. They talk about installing PHP4 (which I need) from the repositories, when in fact it seems all support for PHP4 has been dropped from Feisty onwards. This is quite a surprise for me, now that I've got the server.

---

