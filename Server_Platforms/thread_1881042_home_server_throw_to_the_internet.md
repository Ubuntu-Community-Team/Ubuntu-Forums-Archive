---
title: "home server throw to the internet"
date: 2011-11-14
forum: Server Platforms
---

### Post by barezi6 on 2011-11-14
i am using ubuntu 8.04 LTS  server on one of my pcs and it is working great, but now i need to throw it on the Internet, i searched on google and saw some topics saying, to use no-ip etc etc but i dont saw any good tutorial, i am on the last point to complete my server, if any have some experience or know what i need to do or know some good tutorials etc, i'll be thankful :)

Thanks

---

### Post by spynappels on 2011-11-15
I'm going to make some assumptions here...

Let's assume you have a web server, and that you have taken some basic steps to secure it and that it is on a static LAN IP. Let's al;so assume you have a modem/router which allows you to forward ports.

What you need to do next is open port 80 on your router and forward it to the static IP of your server.

That will allow anyone to access your webserver using your public IP address. If your public IP address can change because you have a Dynamic IP, you can use a service like No-IP or DynDNS to give you a URL which will resolve to your IP. You need to update your IP to the service when it changes, many modem/routers have this ability built in to them.

---

### Post by barezi6 on 2011-11-19
> **spynappels said:**
> I'm going to make some assumptions here...

Let's assume you have a web server, and that you have taken some basic steps to secure it and that it is on a static LAN IP. Let's al;so assume you have a modem/router which allows you to forward ports.

What you need to do next is open port 80 on your router and forward it to the static IP of your server.

That will allow anyone to access your webserver using your public IP address. If your public IP address can change because you have a Dynamic IP, you can use a service like No-IP or DynDNS to give you a URL which will resolve to your IP. You need to update your IP to the service when it changes, many modem/routers have this ability built in to them.


now i have a static ip my data is:

auto eth0
iface eth0 inet static 
      address 192.168.1.80
      netmask 255.255.255.0
      broadcast 192.168.1.255
      gateway 192.168.1.0 

now i need to go to my router and open the port 80 and link with the my server ip right?
and to see on the internet, when i do it i only need to insert my ip on the browser bar and press enter or need to do more things?

Thanks for all the help :)

---

### Post by papibe on 2011-11-19
Take a look at this [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video tutorial from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by barezi6 on 2011-11-19
> **papibe said:**
> Take a look at this [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video tutorial from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

Hope it helps. Let us know how it goes.
Regards.

Thanks very much for the link it is great, tomarrow i will try it and will post here news :)

---

### Post by barezi6 on 2011-11-20
i dont use dyndns because now it isnt free for unlimited time, i am using no-ip.
now i have a static ip my server configuration is above,  and i have opened port 80 of my router and have a no-ip host. but i researched and see that i need to install the no-ip on server, but i cant do it, because the server isnt work on the internet, he said, networking unreachable, and i cant use ping or other command that need the internet, the computer is connected on the internet but he said that dont have internet. i have the 80 port open, and an account on no-ip website with my server ip, have the no-ip DUC, how i can resolve this both problem? the server dont recognizes the internet and when i will have internet what i need to do more to access on my server anywhere.

---

### Post by darkod on 2011-11-20
Look at your post #3, the IP setting of the server.
The gateway would usually be 192.168.1.1, it can't end on .0
This is probably the error why the server has no internet access because the address of the gateway is wrong, and the gateway is your router which is leading to the internet.

Change the gateway IP and either restart the networking services or the whole server for the change to take effect.

---

### Post by PCFreak2 on 2011-11-20
Set a static IP for your Server (you will need the MAC address and Host Name) through the router's GUI
Open port 80 (or whatever port Apache is running on) for the static IP

---

### Post by barezi6 on 2011-11-21
> **darkod said:**
> Look at your post #3, the IP setting of the server.
The gateway would usually be 192.168.1.1, it can't end on .0
This is probably the error why the server has no internet access because the address of the gateway is wrong, and the gateway is your router which is leading to the internet.

Change the gateway IP and either restart the networking services or the whole server for the change to take effect.

lol stupid error :D thanks for the help to both.
now i have internet on the server, and a static ip with my 80 router port opened, i can see the server on all of computers on my network, but i think that it is not on the internet, when i do on the server..ping for the ip of server or for the name of my host (used with no-ip) it works normally, i can do ping 192.168.1.80 or per exemple: ping my_host.com and it works, but when i do, ping google.com or amazon.com he work good but said ahead of the normal ping information, destination host unreachable, and all package is lost. i need to install no-ip on my server?
what should be wrong?

---

### Post by kleverbear on 2011-11-21
> **barezi6 said:**
> lol stupid error :D thanks for the help to both.
now i have internet on the server, and a static ip with my 80 router port opened, i can see the server on all of computers on my network, but i think that it is not on the internet, when i do on the server..ping for the ip of server or for the name of my host (used with no-ip) it works normally, i can do ping 192.168.1.80 or per exemple: ping my_host.com and it works, but when i do, ping google.com or amazon.com he work good but said ahead of the normal ping information, destination host unreachable, and all package is lost. i need to install no-ip on my server?
what should be wrong?

Check with your ISP if port 80 is allowed. Most ISp in the USA will have port 80 blocked to residential accounts.

---

### Post by barezi6 on 2011-11-21
> **kleverbear said:**
> Check with your ISP if port 80 is allowed. Most ISp in the USA will have port 80 blocked to residential accounts.

sorry about that but how i can check my ISP?

---

### Post by barezi6 on 2011-11-22
> **barezi6 said:**
> sorry about that but how i can check my ISP?

up

---

### Post by papibe on 2011-11-22
Use this web page to test access to the ports you want to use: [http://canyouseeme.org/]("http://canyouseeme.org/")

Regards.

---

### Post by barezi6 on 2011-11-22
> **papibe said:**
> Use this web page to test access to the ports you want to use: [http://canyouseeme.org/]("http://canyouseeme.org/")

Regards.

Thank you :)i will test this port with my pc IP because i cant test it with the server

---

### Post by kleverbear on 2011-11-22
Sorry didn't see that you responded, usually if you got your ISP page and under support they have a list of blocked ports, or you could call and ask.

Who is your ISP?

---

### Post by barezi6 on 2011-11-22
> **kleverbear said:**
> Sorry didn't see that you responded, usually if you got your ISP page and under support they have a list of blocked ports, or you could call and ask.

Who is your ISP?

my ISP is MEO

 [http://www.meo.pt/Pages/homepage.aspx](http://www.meo.pt/Pages/homepage.aspx)

---

### Post by kleverbear on 2011-11-23
Were you able to find out if port 80 is blocked for you?

---

### Post by barezi6 on 2011-11-23
> **kleverbear said:**
> Were you able to find out if port 80 is blocked for you?

i tested the por and appear this error:
- Error: I could not see your service on 82.154.202.115 on port (80)
Reason: Connection timed out

---

### Post by kleverbear on 2011-11-23
> **barezi6 said:**
> i tested the por and appear this error:
- Error: I could not see your service on 82.154.202.115 on port (80)
Reason: Connection timed out

Yup that's an ISP block. Do some port forwarding.

---

### Post by darkod on 2011-11-23
Pardon my ignorance, but how are they actually doing that? Can they sense the direction of traffic or what?

If 80 is blocked, how do you get online at all?

---

### Post by kleverbear on 2011-11-23
> **darkod said:**
> Pardon my ignorance, but how are they actually doing that? Can they sense the direction of traffic or what?

If 80 is blocked, how do you get online at all?

Its traffic filtering on the inbound (me to you), but you can still use it for outbound (you to me) traffic for web surfing.

---

### Post by barezi6 on 2011-11-23
> **kleverbear said:**
> Its traffic filtering on the inbound (me to you), but you can still use it for outbound (you to me) traffic for web surfing.

how i can resolve this problem? some ideas?

---

### Post by kleverbear on 2011-11-23
See here 
[http://www.youtube.com/watch?v=pIK-RpVNAM8]("http://www.youtube.com/watch?v=pIK-RpVNAM8")
[HEre]("http://portforward.com/")
and [here]("http://www.wikihow.com/Set-up-Port-Forwarding-on-a-Router")

:popcorn:

[http://www.zeropaid.com/news/6160/introduction_to_port_forwarding/](http://www.zeropaid.com/news/6160/introduction_to_port_forwarding/)

---

### Post by PCFreak2 on 2011-11-23
> **kleverbear said:**
> Check with your ISP if port 80 is allowed. Most ISp in the USA will have port 80 blocked to residential accounts.
My ISP doesn't block any ports
I can open port 80 to my webserver and my friend can view it at:
http://"MY IP ADDRESS":80/

---

### Post by kleverbear on 2011-11-23
> **PCFreak2 said:**
> My ISP doesn't block any ports
I can open port 80 to my webserver and my friend can view it at:
http://"MY IP ADDRESS":80/

:o Who is your ISP???

---

### Post by spynappels on 2011-11-24
They block all inbound traffic on port 80. Traffic out to the net comes from a higher random port and is sent to port 80 on the content server, so port 80 traffic is simply blocked going in one direction only.

---

### Post by barezi6 on 2011-11-24
> **spynappels said:**
> They block all inbound traffic on port 80. Traffic out to the net comes from a higher random port and is sent to port 80 on the content server, so port 80 traffic is simply blocked going in one direction only.

and how we can turn this problem?

---

### Post by barezi6 on 2011-11-26
> **barezi6 said:**
> and how we can turn this problem?

up

---

### Post by PCFreak2 on 2012-02-28
> **kleverbear said:**
> :o Who is your ISP???
Sorry for a really late reply
But it is [http://www.timewarnercable.com/](http://www.timewarnercable.com/)

---

