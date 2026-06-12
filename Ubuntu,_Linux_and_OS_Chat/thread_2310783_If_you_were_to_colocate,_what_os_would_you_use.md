---
title: "If you were to colocate, what os would you use?"
date: 2016-01-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Higgins909 on 2016-01-21
I've been using ubuntu server for a good few years, but haven't really used it at a pro level.
I've read that debian is a good one, I got it on my VM host and its running off of 128mb ram and ssh login is very fast vs ubuntu.
(Thats the only pro I know of right now.  Having apt-get issues because of sources)
I've also had a on and off with ubuntu desktop and less with debian mate. (Blew windows away in web browsing speed)

But, I'm here to ask you guys, the ubuntuforum's community.  What os would you use if you colocated or rented a server?
I'm mainly interested in ubuntu server vs debian server vs ?slackware?
But maybe you prefer something else, that's a ok answer too, but both would be better :D

Hmm, This server will be running off of some 4gb ram and a atom cpu. (Just a example)
The server will be hosting a website and have mysql server on it also, keeping all the passwords n user id's.
Some sort of ad site for comercial use, maybe even sell some stuff.

What would be the best at performance, networking, security, ?etc?
I also wonder how well any linux would handle one of them 10gb rj45 networking cards.

Thanks,
Higgins909

---

### Post by newbie-user on 2016-01-22
I'd suggest using whatever distro you're comfy with. I don't know much about slackware, so I won't comment on that. Ubuntu is essentially the same as Debian, except that it's more of a Debian in perpetual beta. Debian is built for stability so it won't always have the latest packages, whereas Ubuntu is built to be more bleeding edge. I personally prefer to use Ubuntu because I find that there is much more help available online.

In terms of security, I think they're all the same, and they'll be as secure as you make them. Performance should be all the same as well.

---

### Post by SeijiSensei on 2016-01-23
I use CentOS, the free clone of RedHat, on servers and Ubuntu on desktops.  I've been building servers on RedHat-flavored machines for two decades so I just know my way around them better.  I don't see much reason to choose Debian over Ubuntu Server since the fundamentals are identical.  If you're comfortable with Ubuntu, go with that. 

I wouldn't choose Slackware over any of these options just for support reasons if no other.

At this point I would never choose to co-locate a physical server as opposed to renting a virtual machine from [Linode]("https://www.linode.com/pricing"). The biggest problem with servers is maintaining the hardware.  I'd much rather pay Linode $10-20/month.  I get a high-speed network connection, a well-maintained infrastructure with reliable power and air conditioning, daily snapshot backups of the entire virtual machine, and no worries about whether a disk drive will fail in the middle of the night.  You can choose just about any Linux distribution you want, too.  For your needs, a machine with 1 GB of memory is more than enough.  GUIs on desktops are memory hungry, but server-side software like MySQL or Apache is not.

---

