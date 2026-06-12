---
title: "How do I direct port 80 to different servers on URL"
date: 2007-05-23
forum: Server Platforms
---

### Post by markymarknz on 2007-05-23
Hi Everyone,

I have been trying to work out a good way to setup my network the way I want it to.
Basically as you can see in the picture(attached) I have a proxy/firewall server which runs off a great opensource project called smoothwall. This then directs/blocks traffic depending on firewall rules.

I have a webserver which works great running in my DMZ and at present all port 80 traffic is allowed through the smoothwall proxy and directed to the webserver.
However my problem is that I now also want to setup a mailserver which also has a web interface (based on another great opensource project called zimbra). So what I am wanting is for http requests to [www.example.com](www.example.com) to go to my webserver and http requests to mail.example.com to go to my webmail interface running on another machine.

I was wondering if there is any smart way of doing this apart from running the webmail interface on a different port. Is there a way to use virtual hosts or something on my webserver to direct traffic to webmail.example.com to my other server?

Cheers

Mark

---

### Post by cantormath on 2007-05-24
you can set the port that zimba serves on to a different port, say 5000, so the address is example.com:5000, and then set a subdomain, ie)webmail.example.com as a cname record to point at example.com:5000, or whatever port you want......that is the way I do it.  

Do you have more then one IP?  If you do, there are other options using virtual machines and apache.......
Also, I believe that you can, with virtual machines, point to a ip directly on the lan.

hope that helps.

---

### Post by markymarknz on 2007-05-24
> **cantormath said:**
> you can set the port that zimba serves on to a different port, say 5000, so the address is example.com:5000, and then set a subdomain, ie)webmail.example.com as a cname record to point at example.com:5000, or whatever port you want......that is the way I do it.  

Do you have more then one IP?  If you do, there are other options using virtual machines and apache.......
Also, I believe that you can, with virtual machines, point to a ip directly on the lan.

hope that helps.

Awesome thanks Cantormath the idea about a cname record was just the trick I was after :)
Updated my DNS records and all looks good now. The thing I like about this solution is that it is transparent to the user so they just enter the normal url in and it automatically changes to another port for them.

Cheers matey :)

---

### Post by MJN on 2007-05-24
I must be missing something here, but how have you configured a CNAME with a port number? After all, DNS has no knowledge of transport-layer ports...

(as I said, I may have the wrong end of the stick here!)

Incidentally, I was going to suggest using the mod_proxy Apache module to enable your 'primary' web server act as a proxy for accesses to your webmail server, but it sounds like you're up-and-running (and I don't know the exact detail, but the archives have many examples of this usage).

Mathew

---

### Post by markymarknz on 2007-05-26
> **MJN said:**
> I must be missing something here, but how have you configured a CNAME with a port number? After all, DNS has no knowledge of transport-layer ports...

(as I said, I may have the wrong end of the stick here!)

Incidentally, I was going to suggest using the mod_proxy Apache module to enable your 'primary' web server act as a proxy for accesses to your webmail server, but it sounds like you're up-and-running (and I don't know the exact detail, but the archives have many examples of this usage).

Mathew

Hi MJN,

Well I ended up not using a CNAME but a port 80 redirection through my DNS host.
I am running this on home broadband where the IP addresses changes regularly so I use no-ip.org to update my IP to my domain. There is a feature with no-ip.org where you can add a new host e.g. webmail.example.com that redirects from port 80 to a specified port.
This way if someone browses to my domain e.g. [www.example.com](www.example.com) it will go to the normal webpage, but if they browse to webmail.example.com it will redirect to say port 5000 and then I will have a rule on my firewall to redirect requests on that port to the second webmail server.
Hope that makes more sense for you ;)

Mark

---

### Post by MJN on 2007-05-26
Yeah it does, thanks! So you're using URL forwarding as opposed to CNAMEs which makes sense (CNAMEs, as mentioned, cannot be used to influence port numbers).

Mathew

---

### Post by twistedtwig on 2007-05-29
The only issue I have found with this solution (which I am using) is that if it is not the default HTTP port (80) it is blocked by some places.  Only place I know of atm is my work that blocks a lot of traffic.

Although it is stealthed to windows.ponywars.com it still gets blocked. :(

I never managed to get forwarding through the hosts to work.  I also have dynamic dns through easydns.com

---

