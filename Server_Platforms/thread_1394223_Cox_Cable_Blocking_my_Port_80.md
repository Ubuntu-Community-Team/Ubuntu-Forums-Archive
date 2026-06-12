---
title: "Cox Cable Blocking my Port 80"
date: 2010-01-30
forum: Server Platforms
---

### Post by terrapin893 on 2010-01-30
So first off, it probably seems this question has been asked thousands of times before . . . but I did do a search, mostly archived posts that ended up being something other than a true ip blocking of the port. 

[http://support1.cox.com/sdccommon/asp/contentredirect.asp?sprt_cid=643ad749-1a58-4824-9d1c-8cd5579e132a](http://support1.cox.com/sdccommon/asp/contentredirect.asp?sprt_cid=643ad749-1a58-4824-9d1c-8cd5579e132a)

So my port 80 is truly blocked.  Ive tried setting up the port forwarding on my router, Ive tried manually allowing all traffic on port 80 through ip tables.  Ive even dabbled with setting up something like openDNS to see if that would help.  

So far nothing, Im only available on my local network.  

There has to be some way to do a redirect though . . . . even something as simple as an htaccess file redirecting [http://domain.com](http://domain.com) to [http://domain.com: xxxx](http://domain.com: xxxx) (the space is there to avoid my url being interrupted by a smiley . . .

---

### Post by hessiess on 2010-01-30
If its blocked externally (by the ISP) there is nothing you can do about it unless you have a server outside the network and use a tunnel of some sort.

---

### Post by BkkBonanza on 2010-01-31
You can use an external port redirect such as offered by dyndns to get around this. I think they call their service "WebHop". No doubt there are other DNS services that offer similar. You can't fix this issue on your own server though - it has to be handled before the request gets to your ISP.

You configure your domain to point to their redirect and their redirect to point to port X on your IP. Then on your router you port forward port X back to your port 80. This bypasses the ISP block, assuming they don't block all ports. 

If they do then you could use a reverse tunnel to an outside server but that kind of defeats the reason for having one on your home server.

---

### Post by terrapin893 on 2010-01-31
Thanks Bkk, I knew there was a way.  Ive tried to configure it with OpenDNS and havent had any success so far.  Ill look into dyndns, Ive heard that recommended before.  

I knew that Ive done all I can do on my server.  The routing should be no issue though, I use a similar method with SSH and FTP (using odd external ports for more security).    They dont block all ports, the only ones I can gather are 25 and 80, and I can use 587 for SMTP.

---

### Post by Vegan on 2010-01-31
One fun thing I did was how to beat up in tripod with some simple JavaScript redirects. Those type of redirects can use any post your heart desires.

Another way is with Apache2 redirects on somebody's server. Here the web server does the same job.

Another way around is with an existing domain/~user and put a redirect in there.

Where there is a will there is a way.

My ISP does not block any port, its illegal up here. Instead the price bandwidth for busy servers at higher prices.

I could be bribed to host a redirect too.

---

