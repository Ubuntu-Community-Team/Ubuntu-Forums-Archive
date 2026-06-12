---
title: "WRT54G Blocking Ubuntu Server?"
date: 2008-05-27
forum: Server Platforms
---

### Post by Strychnine45 on 2008-05-27
I have 8.04 server and everything is setup fine, firestarter allowing http to all on port 80, apache2 installed.  My router forwarding port 80 to 192.168.1.100 (server ip), router firewall off, dns @ sending rapidfiregfx.com to my ip address.

And on a separate pc that is on the linksys wireless network it works like a charm, so it tells me its not the server blocking the internet from accessing itself.  Also, when I type rapidfiregfx.com in this separate laptop, it DOES work, but from a proxy or pc that is not on the network, it times out.

Any ideas on what the problem is?  Why is it timing out with the firewall off>?

---

### Post by NateMan on 2008-05-27
wow man turn your router firewall back on! its much better than the software firewall. Your having some sort of dns issue. Mind posting your config files?

---

### Post by NateMan on 2008-05-27
why don't you try turning off your software firewall and just using the router's firewall?

---

### Post by artesvida on 2008-05-27
I agree that it's a DNS issue.  From the external network, have you tried using the public IP address instead of the host name?

---

### Post by Strychnine45 on 2008-05-27
The ip works from within the network but doesnt work from outside.  Like I said I can access the server from within the network by typing either router ip, server local ip, or rapidfiregfx.com

So it tells me its not the server but it is the router, I'm at wits end since everything on the router is disabled and port 80 is forwarded to the server and everything works fine from within the network even the dns for rapidfiregfx.com
Since it works within the network it tells me the port is actually being forwarded and the dns is working.

But outside it times out, as if there is a firewall on the router blocking the outside world

---

### Post by artesvida on 2008-05-28
Do you just have one public IP address (for your router)?

Sorry, I've just done this stuff at work (Sonicwall and Cisco firewalls) and while I own a WRT54G at home I've never set it up with a static public address.

---

### Post by NateMan on 2008-05-28
Its not a router issue. I'm sure its a dns problem. Again did you try using your actual public ip address, not your domain name?

---

### Post by NateMan on 2008-05-28
DNS can work inside of a network and not outside of it, if your dns is linked to your private ip address. You need to look at the dns entries of your actual router, not your server, its dns seems fine. Turn your firewall back on man! The wrt has a good firewall, I used one at home for years and years. Turn that software firewall off too while your at it. Hardware is >  software for firewalls.

---

### Post by artesvida on 2008-05-28
He says the public IP doesn't work from outside.  Plus rapidfiregfx.com resolves (for me at least).

---

### Post by NateMan on 2008-05-28
No he didn't. I don't see a single place where he says that the PUBLIC ip address works or doesn't work. He only talks about private ip addresses. I want to know what the public ip address does when it is pointed to.

---

### Post by NateMan on 2008-05-28
It resolves for me as well, but still doesnt load. I'm at a loss, since if it doesn't appear to be caused by his software or hardware firewall. If it was permissions or a miss setup folder, then it wouldn't work for any part of it. It almost makes me wonder what the isp is doing, firewall wise. I've seen stranger things than an isp blocking webhosting.

---

### Post by windependence on 2008-05-28
Go to [www.canyouseeme.com](www.canyouseeme.com) and see if your port 80 is being blocked by your ISP. Let us know what you find.

-Tim

---

### Post by garethsimpsonuk on 2008-05-28
Just quickly ( sorry not hijackin, it seems the poster may find this useful aswell ) I know a hardware firewall is loads better but should we have a software firewall to?
Everythings behind a router for me.

---

### Post by hyper_ch on 2008-05-28
> **garethsimpsonuk said:**
> I know a hardware firewall is loads better but should we have a software firewall to?

Normally, if you're not on windows, you don't need a software firewall (although you have by default one when using Linux).

Anyway, I don't get the picture of what works and what doesn't can you maybe make an impage of your lan setup and say what works and what doesn't?

As you use a Linksys Wrt54G you may also want to consider to replace the firmware with some other one. DD-Wrt or Tomato-WRT are quite nice.

---

### Post by molotov00 on 2008-05-28
DNS is the simplest explanation. The WRT54G allows you to remotely connect for configuring the router. If I were you, I'd enable this on port 80 or 8080. Then you can try yourpublicip:8080. That way you take the server and local network out of the picture... you're just going to the router.

But first, I'd just figure out your public IP and try connecting to that! It's the most obvious solution. From there you can figure out why the DNS may not be resolving to the correct IP.

M

---

### Post by Strychnine45 on 2008-05-28
The public ip doesnt work from outside, but does work from inside.

The DNS is controlled via my control panel with Godaddy, I just set my @ to my public ip.

As for canuseeme.com, I cant see it, it looks like a default parked domain.  I am using Cox Communications in New England/USA

So my port 80 is being blocked by my isp?
Is there any workaround for this?  
I can forward a different port but I cant specify a port using dns, it just defaults to the public ip....

Anyone have any ideas?

This actually makes me remember that when I setup my wireless cam I could never get port 80 to work so I used port 81...

---

### Post by NateMan on 2008-05-28
Its not canyouseeme.com its canyouseeme.org. Try that out.

---

### Post by Strychnine45 on 2008-05-28
I could not see your service on xxxxxxxxxxxxxxx on port (80)
Reason: Connection timed out

checking out no-ip.com, what it recommends

---

### Post by windependence on 2008-05-28
> **NateMan said:**
> Its not canyouseeme.com its canyouseeme.org. Try that out.
Jeez Nate I must have been really brain dead last night when I wrote that.

His port 80 is blocked just like I thought.


-Tim

---

### Post by NateMan on 2008-05-28
Yeah I had a feeling it was. Now you can turn that firewall back on, and call your isp to see if they offer an account that has port 80 forwarded.

---

### Post by hyper_ch on 2008-05-28
the ISP can't block port 80... otherwise you couldn't surf at all..

---

### Post by windependence on 2008-05-28
Ummm yes they can. I don't know how they do this but they block INCOMING not outgoing requests, but I do a fair amount of them do this. I had to change ISPs because of this.

-Tim

---

### Post by Strychnine45 on 2008-05-28
What I did was tested my webmin, which works

https:rapidfiregfx.com:10000

So the dns is fine, the router is fine, and the server is handling that fine.

Now I try to change my apache2 port to listen on 10001, forward 10001 to the server (in router admin), but apache wont listen on that port, in fact, it seems (on the local network anyways),to be still listening on port 80

Any thoughts on how I can dupe the ISP and set my server to correctly listen on a different port?

---

### Post by NateMan on 2008-05-28
Yeah... its just using a rule that only affects what is coming up to the isp's routers. But blocking of port 80 is very common among isps. It forces the user to pay for a better account and possibly hosting from them. I know that my isp (at&t) doesn't do this, at least for my level of account.

---

### Post by windependence on 2008-05-28
> **Strychnine45 said:**
> What I did was tested my webmin, which works

https:rapidfiregfx.com:10000

So the dns is fine, the router is fine, and the server is handling that fine.

Now I try to change my apache2 port to listen on 10001, forward 10001 to the server (in router admin), but apache wont listen on that port, in fact, it seems (on the local network anyways),to be still listening on port 80

Any thoughts on how I can dupe the ISP and set my server to correctly listen on a different port?

did you restart Apache?

-Tim

---

### Post by Strychnine45 on 2008-05-28
I did not!

Be kind, this is my 2nd day on ubuntu (any edition)

=)


OK, now I am listening on port 90 but godaddy doesnt offer any type of port forwarding so I can only specify my public IP which wont accept a connection on port 80 because my ISP.  

SO, I am attempting to use no-ip.com to redirect my public IP@ port 90 to servertalk.hopto.org,  THEN, I am changing the CNAME in godaddy for www from the @ to servertalk.hopto.org

SO, it SHOULD, and I say should, hit rapidfiregfx.com, point to servertalk.hopto.org then get redirected to my public ip on port 90.

The only downside being no-ip.com puts a banner on the bottom because I am on a free account....


Anyone know of a better way?

---

