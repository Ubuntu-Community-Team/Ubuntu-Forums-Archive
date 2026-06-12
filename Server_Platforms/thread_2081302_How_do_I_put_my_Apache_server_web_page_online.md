---
title: "How do I put my Apache server web page online?"
date: 2012-11-06
forum: Server Platforms
---

### Post by EXpertBnot on 2012-11-06
I spent many hours searching and reading the forums and Google with the result of many server ideas/configurations, but no solution to my problem. I installed Ubuntu Server 12.04 and the GUI on an old computer then installed Apache2 through the terminal. I was able to get access to the root restricted /var/www/ through the terminal and put my html file there. Now the local host address opens to my web page, but how do I get that online in the internet? I've read that ISPs don't allow home costumers to run web servers so they block port 80. What is that about and how do I open port 80? I went to canyouseeme.org and my port 80 is indeed blocked. Is there some way to get around it with software or some sort of network configuration in my home?

---

### Post by Lars Noodén on 2012-11-06
Welcome to the forums.

Check to see if your ISP allows ports 80 and 443 for HTTP and HTTPS using something like [Canyouseeme](http://www.canyouseeme.org/) or some similar service.  If your ports are not blocked then you can host at home.  If not, then you'll have to find some hosting service on which to put your site.  

If you host at home, you will probably have a dynamic ip address.  In order to find your address each time you'll have to register for a [dynamic domain name service](https://help.ubuntu.com/community/DynamicDNS).  There are several to choose from.  One of them will get you an 'A NAME'  That should be all you need, for basic service.

If you also already have your own domain name, then you can register a 'CNAME' to point at the 'A NAME'.  Then you can give out your domain and people can use it to reach your web server.

---

### Post by Cheesemill on 2012-11-06
Have you set up the port forwarding in your router yet? Until you do this then [http://www.canyouseeme.org/](http://www.canyouseeme.org/) will show port 80 as blocked even if it is allowed by your ISP.

You need to find the port forwarding settings in your routers admin page and set up a rule that forwards all incoming traffic on port 80 to your web servers internal IP address. The method for doing this depends on the model of your router so I can't give you any more specific instructions here but if you go to [http://portforward.com/](http://portforward.com/) they have detailed instructions for a wide range of routers.

Once this is working and you can access your website from outside your network using your external IP address then you can look at the Dynamic DNS services that Lars outlined above.

---

### Post by EXpertBnot on 2012-11-06
> **Cheesemill said:**
> Have you set up the port forwarding in your router yet? Until you do this then [http://www.canyouseeme.org/](http://www.canyouseeme.org/) will show port 80 as blocked even if it is allowed by your ISP.

You need to find the port forwarding settings in your routers admin page and set up a rule that forwards all incoming traffic on port 80 to your web servers internal IP address. The method for doing this depends on the model of your router so I can't give you any more specific instructions here but if you go to [http://portforward.com/](http://portforward.com/) they have detailed instructions for a wide range of routers.

Once this is working and you can access your website from outside your network using your external IP address then you can look at the Dynamic DNS services that Lars outlined above.

Thanks for the link and info I'll look into that. What would my external IP address be? Is it the IP address of the computer my server is installed on?

---

### Post by Cheesemill on 2012-11-06
> **EXpertBnot said:**
> Thanks for the link and info I'll look into that. What would my external IP address be? Is it the IP address of the computer my server is installed on?
That's your internal IP address, your external IP address is the one provided to your router from your ISP. If you don't know what it is you can type the following into your server:
```
curl ifconfig.me
```

---

### Post by Lars Noodén on 2012-11-06
Your external address will be the one your router uses to connect to the Internet.  You can find it looking at your router's settings when you set the port forwarding.  Or you can get it from Canyouseeme or similar sites.

---

### Post by dannyboy79 on 2012-11-06
your external IP can be found out at [http://www.whatsmyip.org/](http://www.whatsmyip.org/). Your internal IP is the one that your server is installed on which you can find out with 

ifconfig

so do you have a router or are you connected directly to a modem?

---

### Post by EXpertBnot on 2012-11-06
> **dannyboy79 said:**
> your external IP can be found out at [http://www.whatsmyip.org/](http://www.whatsmyip.org/). Your internal IP is the one that your server is installed on which you can find out with 

ifconfig

so do you have a router or are you connected directly to a modem?

I'm connected to a router.

---

### Post by EXpertBnot on 2012-11-06
I was configuring my port forwarding settings, but once I hit apply it says "This IP address should be in the same subnet as the LAN IP address". I got my IP by doing the "curel ifconfig.me" in the terminal. Am I somehow using the wrong IP address instead of my external IP address?

---

### Post by Cheesemill on 2012-11-06
> **EXpertBnot said:**
> I was configuring my port forwarding settings, but once I hit apply it says "This IP address should be in the same subnet as the LAN IP address". I got my IP by doing the "curel ifconfig.me" in the terminal. Am I somehow using the wrong IP address instead of my external IP address?
You need to use your servers internal IP address in the port forwarding settings, this is usually something like 192.168.x.x

The external address is what you use to access your website from outside your home network once the port forwarding has been set up.

---

### Post by EXpertBnot on 2012-11-06
> **Cheesemill said:**
> You need to use your servers internal IP address in the port forwarding settings, this is usually something like 192.168.x.x

The external address is what you use to access your website from outside your home network once the port forwarding has been set up.

The IP address I got by using the "curl ifconfig.me" is 69.xxx.xx.xxx and when I looked at the Attached Devices menu on my router's settings it showed 10.0.0.12 for my server that is connected to it. That address (10.0.0.12) worked when I hit Apply for the port forwarding configuration and I am able to connect to the web page using other computers that are connected in my home network. What am I doing wrong exactly on getting my internal/external IP addresses?

---

### Post by Cheesemill on 2012-11-06
> What am I doing wrong exactly on getting my internal/external IP addresses?
Nothing.

10.0.0.12 is correct for your internal IP address (notice I said it is ***usually*** something like 192.168.x.x).

Now your port forwarding is set up your website should be accessable to anyone outside your network if they type your 69.x.x.x address into a browser, If you go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and check again you can see if port 80 is open or not.

---

### Post by EXpertBnot on 2012-11-06
> **Cheesemill said:**
> Nothing.

10.0.0.12 is correct for your internal IP address (notice I said it is ***usually*** something like 192.168.x.x).

Now your port forwarding is set up your website should be accessable to anyone outside your network if they type your 69.x.x.x address into a browser, If you go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and check again you can see if port 80 is open or not.

OH MY GAWD IT WORKS!! Thank you : D. I can't believe my little hurdle was so obvious... Thank you everyone who replied to my thread all your input was read and appreciated.

---

### Post by Cheesemill on 2012-11-06
Brilliant, glad we could help.

As you're on a residential connection your external IP isn't guaranteed to stay the same, take a look at Dynamic DNS for methods to get round this problem:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Can you please mark the thread as solved (click on 'Thread Tools' at the top of the page).

---

### Post by EXpertBnot on 2012-11-06
> **Cheesemill said:**
> Brilliant, glad we could help.

As you're on a residential connection your external IP isn't guaranteed to stay the same, take a look at Dynamic DNS for methods to get round this problem:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Can you please mark the thread as solved (click on 'Thread Tools' at the top of the page).

So, I'm assuming now that my port 80 is open, anyone outside my home network can connect to my website by putting " 69.x.x.x" into their web browser without a ".com", etc?

---

### Post by Cheesemill on 2012-11-06
> **EXpertBnot said:**
> So, I'm assuming now that my port 80 is open, anyone outside my home network can connect to my website by putting " 69.x.x.x" into their web browser without a ".com", etc?
Yes.

---

