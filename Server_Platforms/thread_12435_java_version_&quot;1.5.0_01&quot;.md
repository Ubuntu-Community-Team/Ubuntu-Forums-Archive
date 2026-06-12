---
title: "java version &quot;1.5.0_01&quot;"
date: 2005-01-24
forum: Server Platforms
---

### Post by coldcargo on 2005-01-24
Hi!

I have installed java version "1.5.0_01" but it makes my internal IP-address exposed on the Internet. Does anyone know how to fix this?

//ColdCargo

---

### Post by gheorghe_pop on 2005-01-24
how is that? Please be more specific.

---

### Post by gt500 on 2005-01-24
[QUOTE=coldcargo]Hi!

I have installed java version "1.5.0_01" but it makes my internal IP-address exposed on the Internet. Does anyone know how to fix this?

//ColdCargo[/QUOTE]
 Idd, plz be more specific.

A log / site maybe ...

greetz

---

### Post by jdong on 2005-01-24
Your internal IP address has always been "exposed". Instantiating a "Socket" class and binding it to localhost reveals your IP, and so does enumerating networking interfaces.

There's nothing you can do about it, and there's nothing that others can do with your private IP. NAT's built in firewalling behavior protects your internal network.

---

### Post by mendicant on 2005-01-25
You should also be using a non-routable address for your internal network (assuming you don't actually want your internal network to be public).  192.168.0.0/16 is the commonly used one, but there are others, including 10.0.0.0/8 and 172.16.0.0/12:

[http://www.faqs.org/rfcs/rfc1918.html](http://www.faqs.org/rfcs/rfc1918.html)

---

### Post by coldcargo on 2005-01-25
Hi all!

I did the firewall test on this site: [http://www.auditmypc.com/](http://www.auditmypc.com/) and there are some information about this issue, but nothing concreet todo other than patching witch patches I can't find. I beleave that when I was running Mandrake 10.1 and did the same test my IP was not exposed and I am allmost 100% sure that I had Java installed. I need java to be able to read my webmails, and I could do that with mandrake. I don't think that this is an critical issue for me, but it should feel good not to expose the internal IP address.

//coldcargo

---

### Post by jdong on 2005-01-26
[QUOTE=coldcargo]Hi all!

I did the firewall test on this site: [http://www.auditmypc.com/](http://www.auditmypc.com/) and there are some information about this issue, but nothing concreet todo other than patching witch patches I can't find. I beleave that when I was running Mandrake 10.1 and did the same test my IP was not exposed and I am allmost 100% sure that I had Java installed. I need java to be able to read my webmails, and I could do that with mandrake. I don't think that this is an critical issue for me, but it should feel good not to expose the internal IP address.

//coldcargo[/QUOTE]


Untrue... Unless your Mandrake java install didn't have the entire java.net package, it's gonna show your IP. Java.net.Socket has a method for enumerating all adapters and their listening interfaces -- and it's executable by an applet.



> 
I don't think that this is an critical issue for me, but it should feel good not to expose the internal IP address.


That's a false sense of security. Know or not know IP, a hacker can't get behind your NAT router. If he does, he can perform statistical analysis on PING/port-scan response times on your local subnet, which would surely reveal where there's a computer and where there isn't.

---

### Post by coldcargo on 2005-01-26
Thanks everyone for the input. I will stop worry about this.

//ColdCargo

---

