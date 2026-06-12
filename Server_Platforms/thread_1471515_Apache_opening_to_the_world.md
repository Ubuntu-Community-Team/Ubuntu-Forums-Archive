---
title: "Apache opening to the world"
date: 2010-05-03
forum: Server Platforms
---

### Post by gogic on 2010-05-03
I have installed Ubuntu 10.04 desktop edition. I have installed apache2 and when i test it by going to [http://localhost/](http://localhost/) all works fine.

My pc is connected over router to Internet. I know to find my ip and network ip. I can also open router settings.

I would like to enable ( to some of my friends ) access to my site that is on my pc ( localhost ).

What do i need to do to enable this ?

I tried with something like  [http://my-ip:80](http://my-ip:80) , but it's not working :(

---

### Post by arrrghhh on 2010-05-03
> **gogic said:**
> I have installed Ubuntu 10.04 desktop edition. I have installed apache2 and when i test it by going to [http://localhost/](http://localhost/) all works fine.

My pc is connected over router to Internet. I know to find my ip and network ip. I can also open router settings.

I would like to enable ( to some of my friends ) access to my site that is on my pc ( localhost ).

What do i need to do to enable this ?

I tried with something like  [http://my-ip:80](http://my-ip:80) , but it's not working :(

1) Ubuntu by default closes ALL ports.  Enable UFW and open port 80 to all IPs
2) Your router will also need to forward port 80 from your webserver to the outside world.  Keep in mind your ISP *may* still block the traffic to that port, and you may be forced to use some funky port above 1024...

---

### Post by tgalati4 on 2010-05-03
I presume you set up a port-forward of port 80 from your external IP to your internal IP of your server box.

I presume you set up /etc/apache2.conf to allow all and to listen on port 80 in ports.conf?

---

### Post by gogic on 2010-05-03
I just fowarded port and that is that. It works fine,

I did't do anything to ufw or changed conf file of apatche. ( and as i said all was clean install )

---

### Post by arrrghhh on 2010-05-03
> **gogic said:**
> I just fowarded port and that is that. It works fine,

I did't do anything to ufw or changed conf file of apatche. ( and as i said all was clean install )

Apache by default should be setup to use port 80... but you're saying you didn't have to open the port on Ubuntu with iptables or ufw?!?

---

### Post by gogic on 2010-05-03
As i said, i didn't changed anything in ufw

and here [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) u can see 
"By default UFW is enabled but all ports are left open (otherwise there would be no Internet access following installation). "

---

### Post by arrrghhh on 2010-05-03
> **gogic said:**
> As i said, i didn't changed anything in ufw

and here [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) u can see 
"By default UFW is enabled but all ports are left open (otherwise there would be no Internet access following installation). "

Damn... I figured all ports facing the outside were shut by default.  You can stop inbound traffic without losing internet access...

Doesn't this seem like a bad idea?  I guess I incorrectly assumed Ubuntu came hardened out of the box...  Seems like a Windows thing, leaving stuff open to make it easier (but much less secure) for the end-user...

In that case, PLEASE turn on UFW and setup some basic rules.  I had no idea that Ubuntu by default was left wide open, I think before UFW the opposite was true.  There were rules in IPTABLES to allow access, but anything coming in was blocked... Am I just wrong and thinking of another more secure Linux distro?  Or maybe dreaming of security in my sleep?!?

---

### Post by cariboo on 2010-05-03
Ubuntu indeed does come with no ports listening in a default install. Unless you enable ufw:

```
sudo ufw enable
```

there are no iptables rules enabled either in a default install. As soon as you start installing servers, they are listening on their respective ports.

The op is doing things right, by only forwarding port 80 to his router.

---

### Post by arrrghhh on 2010-05-03
> **cariboo907 said:**
> Ubuntu indeed does come with no ports listening in a default install. Unless you enable ufw:

```
sudo ufw enable
```

there are no iptables rules enabled either in a default install. As soon as you start installing servers, they are listening on their respective ports.

The op is doing things right, by only forwarding port 80 to his router.

OK... So no listening ports by default, I assume because there's no services installed by default?  

Now lets say I install apache or ssh, those listen on 80 and 22 respectively by default.  If you don't enable UFW or setup iptables, will port 80 and 22 be open to the world?  (Let's just assume I have a DMZ setup or something stupid that puts the server straight onto the internet... ;))

---

### Post by tgalati4 on 2010-05-03
If you have a router with a built-in firewall (that allows only ports that you forward) then you really don't need iptables or ufw.  Ubuntu is secure out of the box because not many services are running with the default installation.  As soon as you start loading up services (ssh, mail, web, etc) then the machine will listen and respond to those specific ports for those services.  This allows LAN use without much configuration.  To see these services outside of your LAN, then you have to port-forward each port for each service that you need to access.

To the OP:  I assume that things are working now.

---

