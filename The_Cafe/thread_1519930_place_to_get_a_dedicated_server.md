---
title: "place to get a dedicated server"
date: 2010-06-28
forum: The Cafe
---

### Post by ubudog on 2010-06-28
Anyone know of a good place to get a dedicated server? Needs to be cheap, maybe 20$ max a year.

Thanks.

---

### Post by Ocxic on 2010-06-28
even the cheapest web servers are $3-5/mo.

---

### Post by ubudog on 2010-06-28
> **Ocxic said:**
> even the cheapest web servers are $3-5/mo.

Well, I might be able to do that.  Do you know where to get one that cheap?

---

### Post by steveneddy on 2010-06-28
Purpose?

Some people have home servers or professional servers they "lend" space to for alternate reasons.

File server, web server, "cloud" server -

---

### Post by Ocxic on 2010-06-28
[http://www.webhostingchoice.com/](http://www.webhostingchoice.com/)
[http://hosting-review.com/canada.shtml?gclid=CKn1zbmuxKICFURB5godrSPk6w](http://hosting-review.com/canada.shtml?gclid=CKn1zbmuxKICFURB5godrSPk6w)

---

### Post by ubudog on 2010-06-28
It would be a dedicated web server that I could login to via ssh.  It would have my website on it, etc.  I already wrote the html.

---

### Post by ubudog on 2010-06-28
> **Ocxic said:**
> [http://www.webhostingchoice.com/](http://www.webhostingchoice.com/)
[http://hosting-review.com/canada.shtml?gclid=CKn1zbmuxKICFURB5godrSPk6w](http://hosting-review.com/canada.shtml?gclid=CKn1zbmuxKICFURB5godrSPk6w)

Thanks for the links.

---

### Post by Warpnow on 2010-06-29
A dedicated server won't go for that cheap. Why? Because it uses that much in electricity alone. A home computer uses way more than that, and servers use more. There's no possibly way for it to be that cheap.

A true dedicated server, unmanaged, ie, they turn it on for you and that's it, no installs or anything, just a box connected a lan, will cost you, at minimum, like $30 a month, and for that, you'll probably get like a pentium 3 with as much ram as your cell phone...

A decent dedicated server will run you $50-$100 a month unmanaged, and over $100 a month, easily, managed.

You could get a VPS. One of the admin of this forum runs fivebean.com, and there's a coupon code "ubuntu" that gets you a $5 VPS. A virtual private server is a sliver of a dedicated server. You have your own OS, running in a VM, with a dedicated amount of CPU and RAM.

Edit: The links above are for web hosting. All you get is public_html folder basically and a control panel. You can probably log into SSH on alot of them, but you can't run programs. All you can do on your SSH usually is unpack tarballs, change permissions, ect. 

Web Hosts- No control. You upload your HTML and it works. 

VPS- More work, More Control. You configure the OS yourself but hardware is taken care of.

Unmanaged Dedicated Server- You take care of everything. They keep the machine on and powered up, but nothing else.

Managed Dedicated Server- Very expensive. Best of both worlds. Will cost you roughly the same as a car payment, and is very similar. If you want a ford pinto with mismatched doors it can be had pretty cheap. If you want a corvette, you pay for it.

---

### Post by dtfinch on 2010-06-29
A small rackspace cloud server (256mb ram and 10gb disk, or 1/64th a dual processor quad core opteron server with 16gb ram and a 640gb raid 10) is about $11/month plus bandwidth.

---

### Post by Warpnow on 2010-06-29
> **dtfinch said:**
> A small rackspace cloud server (256mb ram and 10gb disk, or 1/64th a dual processor quad core opteron server with 16gb ram and a 640gb raid 10) is about $11/month plus bandwidth.

Yeah, but a cloud is virtualized. He was asking for dedicated. WAsn't saying you can't get hosting affordable, but a dedicated is going to cost way more than $20/year, or $10/month.

---

### Post by Version Dependency on 2010-06-29
I pay around $160/month for my dedicated server.  And that is a pretty good price. 

You won't find a dedicated server for $20/year...and even if you did, would you really want to trust it with your websites?  If you value stability and security at all, I suggest you try to spend a bit more money.

---

### Post by ubudog on 2010-06-29
Guess I could find an old desktop, run a home server.  Wouldn't cost me nearly as much.  Thanks for the help!

---

### Post by samalex on 2010-06-29
If the OP can go with a VPS instead of a dedicated physical box, I'd suggest [Linode]("http://www.linode.com/").  Someone else in here suggested them, and though I haven't signed-up yet I've been in content with them to get a VPS setup for our LUG.  The cheapest plan is like $20/month, which isn't bad.

Or the suggestion to run a home server is another option, that's what I've done for years :) 

Sam

---

### Post by Sporkman on 2010-06-29
> **ubudog said:**
> Guess I could find an old desktop, run a home server.  Wouldn't cost me nearly as much.  Thanks for the help!

You might want to spring for a business internet account with your ISP - that way you could get a static IP address + better bandwidth (and better service overall) if they offer it.

EDIT: If you just use your regular account, make sure port 80 isn't blocked.

---

### Post by McRat on 2010-06-29
We use GoDaddy for the dedicated server.  It's about $90/m IIRC, which was about the cheapest we could find.  We are happy with them.  Keep in mind once you have a dedicated server you can sell space on it.  You can be a ISP yourself and actually show  a profit on it.

---

### Post by ubudog on 2010-06-29
Yeah, I ran a small home server before using an old desktop, but I don't have one anymore.  I'll just have to look for one.  That is probably my best option.  Thanks for all the help!

---

