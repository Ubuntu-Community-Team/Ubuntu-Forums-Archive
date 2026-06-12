---
title: "How to determine your IP Address"
date: 2009-11-04
forum: Server Platforms
---

### Post by FZR_Rider on 2009-11-04
Does anyone here know how to determine your outside IP address in Ubuntu Server?  Any help is appreciated!!  Thanks!!

---

### Post by jfmanamtr on 2009-11-04
From a terminal, type in sudo ifconfig. In there will be an eth"#". That will have an IP listed in it. Hope that helps.
 
~John

---

### Post by redmk2 on 2009-11-04
> **FZR_Rider said:**
> Does anyone here know how to determine your [COLOR="Red"]outside[/COLOR] IP address in Ubuntu Server?  Any help is appreciated!!  Thanks!!

Use this```
GET checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

```

This is from [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.debian-administration.org/users/mnaumann/weblog/1").

---

### Post by FZR_Rider on 2009-11-05
Thank you for your help.  I think I asked the wrong question.  The second replay gave me the answer that I thought I wanted, however it's the IP address for my router.  Every time I try to access that IP address it takes me to my router's config.  Any ideas on how to get around that so users can go directly to my server?

---

### Post by windependence on 2009-11-05
You need to turn off remote access in your router. It's dangerous to have it open to the web in the first place. Then, look up port forwarding on Google and read up on it because you are going to be doing a lot of it.

-Tim

---

### Post by allio on 2009-11-05
> **FZR_Rider said:**
> Thank you for your help.  I think I asked the wrong question.  The second replay gave me the answer that I thought I wanted, however it's the IP address for my router.  Every time I try to access that IP address it takes me to my router's config.  Any ideas on how to get around that so users can go directly to my server?

When users on the internet go to that IP, they will go to your server (assuming you have forwarded ports correctly). The rules are a bit different in your internal network - as you've discovered trying to visit your external IP will always take you to your router. You have to use your server's internal IP within your network (the one that showed up in ifconfig).

If you NEED to use your external address within your network, I suggest signing up for something like a dyndns account and then manually pointing that address to your server's local IP in your /etc/hosts file.

---

### Post by redmk2 on 2009-11-05
> **FZR_Rider said:**
> Thank you for your help.  I think I asked the wrong question.  The second replay gave me the answer that I thought I wanted, however it's the IP address for my router.  Every time I try to access that IP address it takes me to my router's config.  Any ideas on how to get around that so users can go directly to my server?

Hmmmm.  There should be only 2 interfaces on your router.  The one facing your LAN and the one facing the public internet.  The one facing the public should not bring you to the config page unless you have set up the router to be remotely controlled (configured).  This is not a good idea.  This would mean anyone could change your settings one they figured out your login/pass combo.

On the subject of how you connect  to a host on your LAN, you need to set up port forwarding if you are using a private IP address (NAT).  See [**_[COLOR="DarkSlateGray"]Port Forwarding[/COLOR]_**]("http://portforward.com/").

EDIT: Note that if there are multiple Ethernet ports, they are actually part of an integrated switch.

---

### Post by redmk2 on 2009-11-05
> **allio said:**
> When users on the internet go to that IP, they will go to your server (assuming you have forwarded ports correctly). The rules are a bit different in your internal network - as you've discovered trying to visit your external IP will always take you to your router. 

But as Tim has pointed out; this is a security breach if you can access the config page. 

> 

You have to use your server's internal IP within your network (the one that showed up in ifconfig).

Not so as pointed out by both Tim and myself.  Edited: You need to forward the packets going to the external IP address using the proper TCP port to the NAT'd address which is the servers internal address.  You can't directly use the internal NAT'd address.> 

If you NEED to use your external address within your network, I suggest signing up for something like a dyndns account and then manually pointing that address to your server's local IP in your /etc/hosts file.
You are confusing DNS with port forwarding.

---

### Post by windependence on 2009-11-05
If you are getting your router from INSIDE your network, you will need to edit your /etc/hosts file and add the address of your server. This is because most home routers don't do NAT reflection, so they can't find your server unless you define it in your local DNS.

```
::1                    localhost
127.0.0.1              localhost  tiburon.dominicanstotheusa.com  
192.168.2.40           dominicanstotheusa.com 

```-Tim

---

### Post by redmk2 on 2009-11-05
> **windependence said:**
> If you are getting your router from INSIDE your network, you will need to edit your /etc/hosts file and add the address of your server. This is because most home routers don't do NAT reflection, so they can't find your server unless you define it in your local DNS.

```
::1                    localhost
127.0.0.1              localhost  tiburon.dominicanstotheusa.com  
192.168.2.40           dominicanstotheusa.com 

```-Tim

And fancy IPv6 I see.  :D

Edit:  Tim, I think the OP is referring to outside users.  See his quote "Any ideas on how to get around that so users can go directly to my server?"

---

### Post by kixome on 2009-11-05
[www.whatismyip.com](www.whatismyip.com)

---

### Post by allio on 2009-11-05
It doesn't mean his router's web interface is internet-facing. Mine certainly isn't, but if I try going to [http://my-external-ip-address](http://my-external-ip-address) I end up there.

Actually it all depends on where's he's using the internet from. If his server is located somewhere other than where he is, you're correct. If he's using a computer on the same network, you're not.

Here's the scenario:

FZR_Rider's router:
- local, LAN IP: 192.168.1.1
- external, WAN IP: 123.123.123.123

FZR_Rider's server
- local, LAN IP: 192.168.1.2

His router is set to forward port 80 to 192.168.1.2.

If anybody on the wider internet tries going to 123.123.123.123, they will not see his router. They'll see the webserver running on his server because the router will direct them to it.

If he, in his local network, tries going to 123.123.123.123, he will see his router's web interface, as port forwarding is not recognised on a LAN.

If for whatever reason he wants to be able to access his server using the same address as people on the wider internet, the *only* way to do it is to assign his IP a domain name, and redirect requests to that name made from within his network to the server's local IP using a hosts file or similar. I had to do this so I could set up a private bittorrent tracker on my server and use it at the same time as internet users.

---

### Post by redmk2 on 2009-11-05
> **allio said:**
> 
It doesn't mean his router's web interface is internet-facing. Mine certainly isn't, but if I try going to [http://my-external-ip-address](http://my-external-ip-address) I end up there.

Actually it all depends on where's he's using the internet from. If his server is located somewhere other than where he is, you're correct. If he's using a computer on the same network, you're not.

Here's the scenario:

FZR_Rider's router:
- local, LAN IP: 192.168.1.1
- external, WAN IP: 123.123.123.123

FZR_Rider's server
- local, LAN IP: 192.168.1.2

His router is set to forward port 80 to 192.168.1.2.

If anybody on the wider internet tries going to 123.123.123.123, they will not see his router. They'll see the webserver running on his server because the router will direct them to it.

If he, in his local network, tries going to 123.123.123.123, he will see his router's web interface, as port forwarding is not recognised on a LAN.



Sure it is if your router understands NAT reflection.  See post #9

> 

If for whatever reason he wants to be able to access his server using the same address as people on the wider internet, the *only* way to do it is to assign his IP a domain name, and redirect requests to that name made from within his network to the server's local IP using a hosts file or similar. I had to do this so I could set up a private bittorrent tracker on my server and use it at the same time as internet users.

As has already been suggested in post #9

---

### Post by FZR_Rider on 2009-11-06
Got it!!!  Thank you everybody for all of your help!!

---

