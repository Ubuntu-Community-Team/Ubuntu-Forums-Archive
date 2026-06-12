---
title: "resolving host names!!"
date: 2006-08-30
forum: Server Platforms
---

### Post by dragze on 2006-08-30
Ok i have been searching the web now for hrs trying just about every suggestion found on how to resolve host names, ok first things first my internet connection is all working fine etc and website address resolve fine, the problem im having is resolving local hostnames, i can connect with ip but not when using hostname. 

I do not currently have a linux box acting as a dhcp/dns server, it is all being done by my netgear router. Now my understanding is that windows pc's send each other there host names through netbios?? anyway i installed winbind and was able to ping one of the windows pc's fine by its hostname, but i 
still cant ping any local linux box's by there hostname, only by ip.

Is the only way i can get the linux boxs to connect to each other via hostname by adding each machine in an ip table?? or is there something like netbios for linux?? 

Please help!!  im getting fustrated wid this now! i just want the bloody machines to be able to connect to each other by hostname!

Someone plz tell me what im doing wrong before i shoot myself! :O :P
Thanks in advance,

dragze.

---

### Post by chrisfay on 2006-08-30
Why don't you just install Bind on the linux box, create a master zone for your network and some A records for your pc's on the LAN? Change the DNS settings in your other computers to the IP of your new DNS server and you're good to go. 

All my computers could connect through hostnames in 5 minutes with that setup. Unless I'm misunderstading you....

---

### Post by dazedandconfused on 2006-08-30
Hiya, 

You're right, Windows boxes use Netbios and/or WINS to resolve names to addresses so you really need a local DNS server for your domain.

This involves several steps these being installing bind9:

sudo apt-get install bind9

modifying named.conf (which should be in /etc) and setting up forward and reverse lookup tables in /var/named.

It all seems pretty intimidating at first but it's not too bad once you get over the initial shock of the scary looking config files.

Check here:

[http://foss4all.co.uk/html/server-stuff/centos/centos-dns.html](http://foss4all.co.uk/html/server-stuff/centos/centos-dns.html)

for examples. This is one I wrote to work on CentOS Linux which is a free Redhat EL4 clone but the file structures and layouts should be similar if not identical.
If you get truly stuck, mail me the details of your network and I'll write them up for you. Copy them to right directories on your DNS server and use its IP as the DNS server on your clients.

Cheers,

Jools

BTW the foss4all site will have Ubuntu server setup examples on it as soon as I can justify the time to my spouse ;)

---

### Post by Endwin on 2006-08-30
Another (non bind way) is to modify your /etc/hosts file for each machine. All you do is put in an IP then a name so that when on that machine you just type the name and it goes to that IP. Name resolution goes Hosts file -> DNS.


In windows it is in...

```
C:\winNT\system32\drivers\etc\hosts
```

In linux...

```
/etc/hosts
```


The format is in IP NAME so...

```
192.168.0.10     Server
192.168.0.11     Main
192.168.0.15     Media
```

Note it has things in there for localhost.

Also note you need a static IP for each machine for this to work. You can set this in most routers to asign a static IP by the mac address.

---

### Post by dragze on 2006-08-30
Thankyou all very much for all ur great help!! :D

I think for now i will just do what endwin suggested, i will be setting up a linux server for all these machines soon and when i do i will set them up with the bind method.

I will setup endwin's method tomorrow and see how i get on. :S

Thankyou all once again! keep up the good work!

Cheers,

Dragze.

**I used endwin's method and all works fine, i will setup the bind method soon!

Thanks again to all that helped!**

---

