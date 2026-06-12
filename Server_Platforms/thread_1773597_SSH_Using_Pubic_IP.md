---
title: "SSH Using Pubic IP"
date: 2011-06-02
forum: Server Platforms
---

### Post by flyingsuperhigh on 2011-06-02
So, I finally managed to open port 22. The problem was that I had to disable the firewall on my router but I also had to disable it on my modem. Now, I have two further questions:

1)Is it normal that when I am connected on LAN, I cannot SSH into my server using the public IP address?

2)I am trying to host my own website, when I type in the local IP address of the server, I am redirected to my home page. However, when I enter the public IP address, I am redirected to my modem's webpage. How do I go about fixing this?

---

### Post by spynappels on 2011-06-02
This is more than likely because your router does not allow you to access your public IP from inside the LAN, sometimes called IP passthrough. Many routers do not allow this, the only ones I've worked with often which reliably do are Linksys routers. Either you use the LAN IP inside the LAN, or if you use a domain/hostname such as somename.com to access the box, you will need to create an internal DNS entry or add it to the hosts file of each computer manually.

---

### Post by Lars Noodén on 2011-06-02
The redirect for your web page must be set in your modem.  The details vary greatly from brand to brand.  The gist is that you set port forwarding for the web (ports 80 and 443) to the local address of your web server.  After that, the server should be reachable via the external IP address.

---

### Post by CharlesA on 2011-06-02
> **spynappels said:**
> This is more than likely because your router does not allow you to access your public IP from inside the LAN, sometimes called IP passthrough. Many routers do not allow this, the only ones I've worked with often which reliably do are Linksys routers.

That would be my guess as well.

@OP: You can see if your ssh server is visible from the internet by using something like canyouseeme.org

---

### Post by jramshu on 2011-06-02
I'm not sure I've seen a router that doesn't allow port forwarding(Not saying it isn't so). Even el cheapo Belkins have it.

Some ISP's don't allow it though.

What type of router do you have? Look at the manuals for your specific brand and model to see how to set up port forwarding. Then point the ports at a static ip you give to your server. 

On your server it would be best to give it a static ip so if you lose power the router doesn't mess you up when assigning dynamic ones.

---

### Post by spynappels on 2011-06-02
I don't think this is a port forwarding issue. The OP said he'd got the port opened, but was just having problems using his Public IP from inside his LAN. All routers allow port forwarding in one way or another, but that doesn't appear to be the problem.

Like I said, many routers do not allow you to access resources using your Public IP or a domain which resolves to your Public IP from inside your LAN.

Linksys routers definitely do.

---

### Post by flyingsuperhigh on 2011-06-02
Since I have a dynamic IP, I decided to get a free domain name with no-ip.com. It seems to be working as I've asked a friend to visit my site and he is able to do so. Thanks for your suggestions guys. I just had one more question. I am using wordpress and I am trying to link one of the menu items to another web page which I've created. However, each time I click on this menu item, I get a forbidden-you don't have permission to access /filename.php on this server message. I've chmoded the file to 644. I'm not quite sure what the issue is. Any suggestions?

---

### Post by brettg on 2011-06-03
"The OP said he'd got the port opened, but was just having problems using his Public IP from inside his LAN"

Is the server on the public IP or is he using port forwarding to a private address? 

You can't connect to a public IP on your router and then have it NAT forward you back to the LAN you are already on.

---

### Post by hawkmage on 2011-06-03
First of all it is a really bad idea to disable your firewall.  

This is a common problem with a NAT or reverse proxy.  Lets sat you have a client with address C and the external address on the firewall is E and the server address is S.

The client makes a request to make a connection to the address E.  The router sees the request with a source of address of C and hands it off the the address of the server S keeping the original source address of C.  So when the server replies it goes directly to C and not back to E.  When the client gets the response it is expecting from E comming from S it will either drop it or not associate it with the proper connection.  

Some firewalls have the ability to NAT in both directions usually referred to as a SNAT or Secure NAT.  This has disadvantages for things like web server logs since the logged address is always the firewall and not the true source.  It also prevents any source IP based filters/routing.

---

