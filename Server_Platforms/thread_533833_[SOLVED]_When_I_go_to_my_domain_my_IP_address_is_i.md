---
title: "[SOLVED] When I go to my domain my IP address is in the address bar!"
date: 2007-08-24
forum: Server Platforms
---

### Post by flipjarg on 2007-08-24
**[color=red]UPDATE:[/color] This has been solved... to find out how see the second page, post [#12](http://ubuntuforums.org/showpost.php?p=3256617&postcount=12)**

I've been setting up my first server and have been successful, mostly. I've been using this [Ubuntu Server Guide](http://www.howtoforge.com/perfect_setup_ubuntu704_p3) and a few others.

I've got a question about the part where it tells you to edit **/etc/hosts**. The line where it says to enter: "192.168.0.100   server1.example.com     server1"

would "server1" be the Name Server?

Also, there are two name servers provided by my webhost.. I have free a free web hosting package there. Do I need to install a DNS server then?

Thanks

---

### Post by trtech on 2007-08-24
Well, I don't know if this has anything to do with the title of the thread but...

The hosts file works like the DNS and usually overrides DNS.

So if you have the line:

```
192.168.0.100 server1.example.com server1
``` 

in your hosts file, then when you type [http://server1/](http://server1/) or [http://server1.example.com/](http://server1.example.com/) in the borwser, it will try to load a page from [http://192.168.0.100](http://192.168.0.100).

I don't think this file has anything to do with accessing the server from the outside.

---

### Post by flipjarg on 2007-08-24
I just updated my post above... I was wondering if I have to install a DNS server along with LAMP to get the domain name to show up in the address bar. My web host/domain registrar has a free web hosting package. They provide two name servers. Will I need a DNS server?

Thanks for the reply above.

---

### Post by trtech on 2007-08-24
No, you should not need DNS on your machine. But you do need to have an entry in a DNS server somewhere.

If they are providing the hosting though, then they should be providing the server, and you should not need to set it up.

Are you trying to set up a server at home, and you want some domain name to point to it? What's the host?

---

### Post by flipjarg on 2007-08-24
Yeah I have a desktop computer I am now using as a dedicated server. I've pointed the domain to my IP.

I am with Netfirms.com.

When I connect using a proxy it still brings up the IP address but the index page shows up correctly.

---

### Post by Wim Sturkenboom on 2007-08-25
A line in the hosts file contains three fields:
ip address
canonical hostname
alias (I'm not 100% sure but I think you can multiple alias on the same line)

So server1 is NOT the name server.

Hosting providers usually host a (your) site on their servers and not on yours. They will also take care of the domain name registration. Not 100% sure who handles the DNS, I think it's the registrar.

---

### Post by flipjarg on 2007-08-25
Yes, the host is supposed to handle DNS. I wasn't sure if they would let me use their DNS servers since I have free hosting though. After thinking about it they should. What I am doing is basically the same as setting up a domain name and parking somewhere else... at least as far as I understand.

I just need to know what needs to be done on my server so that when people go to *mydomain.com* it shows *mydomain.com* instead of my IP.

Thanks for the info on aliases. It will come in handy, if I can get it to work. :(

---

### Post by trtech on 2007-08-25
> I just need to know what needs to be done on my server so that when people go to mydomain.com it shows mydomain.com instead of my IP.

To configure your server to "listen" for mydomain.com, you need to change the apache configuration. If this is the only domain on your machine, then you need to edit /etc/apache2/sites-available/default, and possibly /etc/apache2/apache2.conf, then sudo a2ensite default.

You will need a static IP address from your ISP, or you can use a dynamic DNS service (not recommended).

If you have a router, then you need to configure your machine to use a static LAN IP address (e.g. 192.168.1.50) and configure the router to forward web traffic (probably just port 80) to your machine's LAN IP.

---

### Post by trtech on 2007-08-25
> I just need to know what needs to be done on my server so that when people go to mydomain.com it shows mydomain.com instead of my IP.

Are you saying that if someone types [http://mydomain.com](http://mydomain.com) into a their browser, it somehow gets converted to something like [http://12.34.56.78/](http://12.34.56.78/) ?

---

### Post by MrHorus on 2007-08-26
> **trtech said:**
> Are you saying that if someone types [http://mydomain.com](http://mydomain.com) into a their browser, it somehow gets converted to something like [http://12.34.56.78/](http://12.34.56.78/) ?

Yes, that's exactly how it works and simply putting an entry into /etc/hosts will not do this as this is local to every machine.

/etc/hosts is checked for any local entry BEFORE consulting with the resolvers in /etc/resolv.conf

If the OP wants people to be able to type his domain into their browser and view his website then he will need to have his domain hosted on a proper name server.

This could be on his own personal machine but this would depend on his machine accepting incoming connections and being available 24/7.

---

### Post by flipjarg on 2007-08-26
> **trtech said:**
> Are you saying that if someone types [http://mydomain.com](http://mydomain.com) into a their browser, it somehow gets converted to something like [http://12.34.56.78/](http://12.34.56.78/) ?

Yep, you got it. That is exactly what happens.

> **MrHorus said:**
> If the OP wants people to be able to type his domain into their browser and view his website then he will need to have his domain hosted on a proper name server.

My domain is hosted with Netfirms.com right now. All I have to do is configure my home server so that it points to the netfirms name server, right?

I have my router setup perfectly right now. The server has a static IP on the network. I can accept incoming requests on port 80. I've tested it on proxies and other computers (not on my network).

---

### Post by flipjarg on 2007-08-26
On netfirms.com they said it would take up to 24-48 hours for everything to be propigated throughout the internet. I waited for one day, expecting it to happen... i waited two days.... i waited three... i waited four... and now today I just decided to test it. It works fine!!!

The only changes I have made are what I have mentioned in this thread. As was stated in a reply, those changes would not have effected the domain name outside my network.

I did some reading at [HowThingsWork.com](HowThingsWork.com) today about DNS servers and learned quite a bit. That helped me understand some things. I suggest that if you are trying to learn about Domain Name Servers (DNS) you read their article on them.

Thanks for all help everyone. You have helped me better understand how this stuff works.

---

