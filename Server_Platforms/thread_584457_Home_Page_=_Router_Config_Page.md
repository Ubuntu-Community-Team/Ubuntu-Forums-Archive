---
title: "Home Page = Router Config Page"
date: 2007-10-21
forum: Server Platforms
---

### Post by dbmayur on 2007-10-21
Hi Guys,
I have Gutsy on my PC and have installed Apache2. When I type localhost I am getting the default page. 
When I try to connect to <username>.homeip.net, I am being redirected to my router config page.

So I know the request is getting to my router, but how do I get my homepage to be displayed rather than the router config page?

Thanks in advance.

Cheers,
Mayur

---

### Post by conjur3r on 2007-10-21
You will need to log into your router and forward port 80 TCP to your computer running apache.  It's usually a good idea to ensure your internal computer doesn't change its IP address otherwise you will have to continue to edit your router setting.  Some people use static IP addresses for this reason.

---

### Post by MJN on 2007-10-21
You may also need to set your router to use a port other than 80 for its configuration - not doing so may not allow the port to be 'freed up' for forwarding elsewhere.

In fact, you may wish to disable the router's configuration page entirely to outsiders as unless you need it it could be a security vulnerability (given that home routers are generally based on rather flaky software).

Mathew

---

### Post by dbmayur on 2007-10-21
Thanks for your suggestions...I did that and now I am facing another problem.

When i type local host on the machine running the apache server or when I access the page from the LAN, the Web page appears.
BUT,
when I type <username>.homeip.net, I get a page not found.

I have forwarded UDP and TCP requests on port 80 to the IP address of my server...what could be wrong now?

Thanks for the prompt responses...

---

### Post by Whiffle on 2007-10-21
Make sure that the address of your apache server isn't being set by DHCP, and that the static IP you have set for it is outside of the range that the DCHP server assigns.

---

### Post by conjur3r on 2007-10-22
Try looking at the apache access logs to see if your requests are actually getting through the router to your server when testing the <username>.homeip.net address.  The file should be in /var/log/, use something like the following:

 # tail -f /var/log/FILENAME

So that the screen will refresh the contents as it changes.  If the file doesn't change, then it is not receiving the request.  Check your homeip mapping and/or router port forwarding.

Depending on the router, sometimes you will need to test from an external connection as the router may not understand internal re-routing.  You can accomplish this by getting a friend of yours to test, or by using a public proxy server.

---

### Post by dmizer on 2007-10-22
to access the page from inside your local network, add:

```
ip.address.of.server          <username>.homeip.net
```
to the /etc/hosts file of the computer attempting to access the server.

---

