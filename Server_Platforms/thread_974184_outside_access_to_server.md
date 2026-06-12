---
title: "outside access to server"
date: 2008-11-07
forum: Server Platforms
---

### Post by kingpin393 on 2008-11-07
Hi,

I am running Ubuntu Server 8.04 on a machine at home with an apache webserver.

I would like to access the webserver from outside my house.  I setup my router to forward port 80 to the machine running the server.

If I put the IP for my modem in the browser outside my house it works fine.

I own a domain and webspace with 1&1 and would like a subdomain to point to my server.

How can I do this?  I tried putting my modems IP into the cname setting in 1&1's control panel but it wouldn't let me.

Anyone know what I can do to achieve what I want?

Thanks,
Kevin

---

### Post by Thirtysixway on 2008-11-07
You will want to get a dynamicdns name from somewhere like [http://no-ip.com](http://no-ip.com) to point to your IP address.  Then use the CNAME and point the CNAME to that dynamicdns url you create, and it should work.

---

### Post by kingpin393 on 2008-11-07
I actually did that right after I posted.  I setup a domain at dyndns.com and set the cname for the subdomain at 1&1 to the dyndns domain.  It doesn't seem to be working.  The subdomain still goes to webspace.  Maybe it is a 1&1 issue?

In the domain control panel it doesn't allow you to turn off the webspace destination.  It has a seperate DNS option (this is where I setup the CNAME).  1&1 seems to be ignoring the DNS settings and just going to the webspace.

-Kevin

---

### Post by Thirtysixway on 2008-11-07
I'm not 100% sure on this, but I know that with my host I have to send them a support ticket/email to setup a CNAME record.  Perhaps you could try asking your host, as the subdomain option on most webhosts is not a CNAME.

---

### Post by CrucifiedEgo on 2008-11-07
Also, if you give us the subdomain, it's much easier to troubleshoot.  That way we can do dns lookups and tell you right where the problem is (though my experience is that when 1&1 are involved, they are the problem.)

---

