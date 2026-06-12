---
title: "a question on multiple ip in a vps"
date: 2013-02-03
forum: Server Platforms
---

### Post by neutron400 on 2013-02-03
hi ,

lets say i have 4 additional ip available for a vps . is there any way to run 4 different apps that uses each specifically assigned ip to communicate with outside world (sending receiving tcp packets )  ?  like a bunch of proxy ?

May be silly a Question?:roll: Pardon My Ignorance 

Thanks

---

### Post by samiux on 2013-02-03
> **neutron400 said:**
> hi ,

lets say i have 4 additional ip available for a vps . is there any way to run 4 different apps that uses each specifically assigned ip to communicate with outside world (sending receiving tcp packets )  ?  like a bunch of proxy ?

May be silly a Question?:roll: Pardon My Ignorance 

Thanks

If the VPS provider does not provide DNS service, you may need to set up your own DNS server which may use up to 2 IP addresses.  Then, the other available IP addresses can be used for other purpose, for example, 2 different web servers with 2 different IP addresses.

Samiux

---

### Post by Cheesemill on 2013-02-03
You can just set up each application to listen on a specific IP address, how this is done varies depending on the application but is usually done by just editing the relevant configuration file.

If you let us know which application(s) you need to do this for then we can give you more help.

---

### Post by neutron400 on 2013-02-03
thanks for the reply 

ok let me be more specific on this , i  am writing some python script that communicate with with external server and fetch json data. i would like to run 4 similar script that takes advantage of those ips . i can easily use proxy but as i have spare ips , i was giving a thought about it .

---

### Post by SeijiSensei on 2013-02-03
Using multiple IPs, typically via interface aliasing, won't improve outbound performance since they will all be sharing the same physical network device.  It would be no different than running four separate instances of your program at the same time.

Multiple IPs can sometimes be valuable for inbound services, particularly if you want to host secure websites.  While it is now possible to share a single IP across multiple SSL virtual hosts, it is often easier to assign each one to a separate IP with its own certificate.

It can also be useful in cases where you want to support the same type of service, say regular HTTP on port 80, but want to have the server handle some requests itself while forwarding others on to servers behind it with proxying.  Then binding one instance of Apache to 10.10.10.10:80 for local files and 10.10.10.11:80 for the proxy might be useful, but you can accomplish the same thing with one IP and name-based virtual hosting.

> **samiux said:**
> you may need to set up your own DNS server which may use up to 2 IP addresses.

I've been running publicly-accessible BIND servers for over fifteen years and have never needed a second IP address.  What am I missing?

---

### Post by neutron400 on 2013-02-03
this is not a web service . its sort of like multiple client (my vps) connecting to a server (external) with different ips .

---

### Post by SeijiSensei on 2013-02-03
> **neutron400 said:**
> this is not a web service . its sort of like multiple client (my vps) connecting to a server (external) with different ips .

[quote=SeijiSensei]Using multiple IPs, typically via interface aliasing, **won't improve outbound performance** since they will all be sharing the same physical network device. It would be no different than running four separate instances of your program at the same time.[/quote]

I don't how I can be much clearer than that.

---

