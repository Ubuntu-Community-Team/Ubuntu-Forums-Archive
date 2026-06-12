---
title: "Getting server through Router into the Internet"
date: 2009-03-25
forum: Server Platforms
---

### Post by DesertFox34 on 2009-03-25
Hello all,

I'm very sure this is a common question(s) but I can't seem to find all the questions I need to complete the tinkering with my ubuntu hardy server so I am here with you guys for help.

Ok the idea is this:

[server] -> [router] -> [internet] -> [linux/mac/windows machine]

Here are the things I have preconfigured (hopefully correctly)

-vnc
-a dns host
-webadmin
-LAMP

So now, what I can do now is access my server via LAN (even through the router). I can not, however, fully understand how to get the server through the router to the internet to other pc's.

Where I am stuck is somewhere between static NAT, dmz, and dns because I don't have proficient knowledge in these fields. So, I have a static ip which is linked under the dns.

Now under the server my /etc/hosts is like this:

```

127.0.0.1 localhost
10.32.77.206 server.domain.com domain


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

This is the /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eht0 inet static

address 10.32.77.206
netmask 255.255.225.0
network 192.168.1.45
broadcast 10.32.77.255
gateway 192.168.1.1

```

If there is a problem with the above please say so.

Now for the router, what exactly would setting the server as the dmz do? And do I need to set the router's dns as well? Sorry if it is quite abstract because I can't necessarily show you what I am asking for.

All I need is remote access through the internet and I can be on my way to testing other applications.

Thanks

-Desert Fox

---

### Post by hictio on 2009-03-25
You need to get your public IP address, first of all.
Once you have one, you can start to test if you can reach your server and services.
If all the boxes on your LAN are behind the same router, use one that has a graphical environment, and use a browser to go to:

[http://checkip.dyndns.org/](http://checkip.dyndns.org/)

It will return your public IP address.

After that, you can test to access your Apache web server, for instance, by using that IP address, instead of the 10.xxx.xxx.xxx address you posted.

If it does not work, you'll have to either use port forwarding on your router, and direct the traffic aimed at specific services to the internal (the 10.xxx.xxx.xxx address) of the Linux server.
Or you can place that Linux box on the DMZ, where, basically, it is completely exposed to the Internet, that is, whatever service it has listening (and that your ISP isn't blocking :) )

---

### Post by DesertFox34 on 2009-03-25
> **hictio said:**
> You need to get your public IP address, first of all.
Once you have one, you can start to test if you can reach your server and services.
If all the boxes on your LAN are behind the same router, use one that has a graphical environment, and use a browser to go to:

[http://checkip.dyndns.org/](http://checkip.dyndns.org/)

It will return your public IP address.

After that, you can test to access your Apache web server, for instance, by using that IP address, instead of the 10.xxx.xxx.xxx address you posted.

If it does not work, you'll have to either use port forwarding on your router, and direct the traffic aimed at specific services to the internal (the 10.xxx.xxx.xxx address) of the Linux server.
Or you can place that Linux box on the DMZ, where, basically, it is completely exposed to the Internet, that is, whatever service it has listening (and that your ISP isn't blocking :) )

Thanks for the reply. To clarify, I know that was not my ip, it was used for display purposes. I have my actual ip configured into the server, (/etc/hosts and /etc/network/interfaces) should I configure it anywhere else?

As for dmz, I am not sure how that entirely works, but I assume just have the router use dmz under the server's name and that's it?

-Desert Fox


EDIT***

So I put the server under dmz in the router which looks like this:
```

WAN IP Address :  71.249.1.142

DMZ Host is currently enabled for
webster1.doesntexist.com.

```

I had a friend on a mac machine test out if they can access the server. So, here are the tests ran in the address bar.

71.249.1.142 - timeout
71.249.1.142:10000 - (asks for redirect to the domain because the server is running under ssl)
domain.domain.com (not the real dns) - timeout
domain.domain.com:10000 - time out


So something must be blocked here because we can obviously access the server outside the LAN but can't reach the actual www or webadmin. Any clues?

-Fox

---

### Post by BkkBonanza on 2009-03-25
You don't need the public ip configured anywhere on your internal server machine. It doesn't care about that - just your gateway, which is your internal ip for your router.

If you are just starting then don't bother with DMZ. Just go to NAT in your router (port forwarding) and forward port 80 (http) and 443 (https) to point to your internal server ip, same ports. Usually it wants to know the src port, dest port and dest ip. Plug in values as stated here and enable.

If you will be running other services to the public (like email) then you will want to later config them the same way.

DMZ is used to configure a whole machine to be exposed to the net. But you don't need that now, though it may be one day what you want.

That's it. But you likely won't be able to access your public ip from inside the network so go to a web site like hidemyass.com (proxy) and enter your address, either ip or domain name. That will access your site from outside the lan to check.

---

### Post by DesertFox34 on 2009-03-25
> **BkkBonaza said:**
> You don't need the public ip configured anywhere on your internal server machine. It doesn't care about that - just your gateway, which is your internal ip for your router.

If you are just starting then don't bother with DMZ. Just go to NAT in your router (port forwarding) and forward port 80 (http) and 443 (https) to point to your internal server ip, same ports. Usually it wants to know the src port, dest port and dest ip. Plug in values as stated here and enable.

If you will be running other services to the public (like email) then you will want to later config them the same way.

DMZ is used to configure a whole machine to be exposed to the net. But you don't need that now, though it may be one day what you want.

That's it. But you likely won't be able to access your public ip from inside the network so go to a web site like hidemyass.com (proxy) and enter your address, either ip or domain name. That will access your site from outside the lan to check.

Thank you for your reply. However, DMZ was exactly what I needed. I needed a way to expose the site over the net. I have fixed the problems with webmin and other certain services which can now be viewable over the internet. Yet, I can't get the www front page to show because my ISP blocks port 80 be default.

I have followed [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL) but when I restart apache2 now, I get this:
```

 * Restarting web server apache2                                                
httpd (pid 5907?) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8080
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```

Does this mean my IP address has not been configured into apache? How would I fix this?

-Fox


EDIT***

I fixed the apache problem and have the side redirecting from 8081 (other services use 8080). For now, what I originally asked for is solved. Now I'll work on getting it to be https.

Thanks for the help guys!

-Fox

---

