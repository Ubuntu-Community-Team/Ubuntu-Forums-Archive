---
title: "Configure UFW Firewall to allow Transmission"
date: 2012-01-18
forum: Security
---

### Post by meddyuk on 2012-01-18
Can anyone tell me how i should configure GUFW (GUI) to allow my transmission to work. It worked before i installed UFW, and i did enable Port 51413, however, the port is still closed on Transmission.

Any ideas?

Meddy.

---

### Post by claracc on 2012-01-19
You can use gufw for it.

Go to system --> administration --> setting firewall, in the window appearing you click on add and then you can do two things (both will give the same results I think):

* Select preconfigured tab, and select transmission program, then close and close

* Or you can select simple tab (incoming) and fill in the blank space with the number of port 51413 you have to receive.

In transmission previously you'll have select 51413 to receive.

I gave up to use transmission ( now using ktorrent) because it always said the receiving port was closed ( wireless internet) in spite of the port was positively oppened. This problem didn't occurred with wired internet.

---

### Post by meddyuk on 2012-01-19
Yeah i've done all that you said but Transmission states the port is closed. I dont really want to uninstall GUFW, as there must be a way round this

---

### Post by claracc on 2012-01-19
> I gave up to use transmission (now using ktorrent) because it always said the receiving port was closed (wireless internet) in spite of the port was positively oppened. This problem didn't occur with wired internet. 

I think the problem is not gufw or ufw but transmission.

---

### Post by Fernhill Linux Project on 2012-01-19
Have a look at this thread it may help :
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by Lemuriano on 2012-05-09
Hi,

I do not know a lot about this but try 6969/tcp in addition to 51413 and that work for me.

Regards.

---

### Post by Bluenoser81 on 2012-05-15
Anybody get this working yet? I've tried all the tutorials, read them all, messed around with allowing in and out various ports including:   6667:7000 OUT and IN TCP 51413 OUT and IN TCP/UDP  In Transmission I've tried setting the port manually to 6969 and others and hitting the test connection button, and it will say "Status unknown" when I chose any port that isn't 51413 (for that port it will always says "Closed").   I think the answer may lie in problems with being connected to a router. Reading from the Transmission page gives some hints:   [https://trac.transmissionbt.com/wiki/PortForwardingGuide](https://trac.transmissionbt.com/wiki/PortForwardingGuide)  I am going to try these ideas and see if it works. By the way, I'm on a wireless connection.

---

### Post by Toz on 2012-05-16
> **Bluenoser81 said:**
> Anybody get this working yet? I've tried all the tutorials, read them all, messed around with allowing in and out various ports including:   6667:7000 OUT and IN TCP 51413 OUT and IN TCP/UDP  In Transmission I've tried setting the port manually to 6969 and others and hitting the test connection button, and it will say "Status unknown" when I chose any port that isn't 51413 (for that port it will always says "Closed").   I think the answer may lie in problems with being connected to a router. Reading from the Transmission page gives some hints:   [https://trac.transmissionbt.com/wiki/PortForwardingGuide](https://trac.transmissionbt.com/wiki/PortForwardingGuide)  I am going to try these ideas and see if it works. By the way, I'm on a wireless connection.

If you have a router between you and the internet, you will need two things to make this work:
1. the router forwarding the ports to your computer
2. the firewall on your computer (if enabled) allowing those ports through.

Be cautious if the router is providing you with dhcp services as you may not always get the same ip address (and the forwarding will then not work). Most routers have the capability of assigning the same ip address to a dhcp request based on the requestor's mac address - look at setting this up as well.

---

### Post by Bluenoser81 on 2012-05-16
> **Toz said:**
> If you have a router between you and the internet, you will need two things to make this work:
1. the router forwarding the ports to your computer
2. the firewall on your computer (if enabled) allowing those ports through.



Thanks for this! I've successfully added port forwarding to my wireless router. Unfortunately, I don't see this mac address forwarding capability you speak of, but it could be that this router is about ten years old now. I turned on port forwarding to my current ip at 192.168.1.106 (I know I'd have to change if my IP changes, small problem easily fixed though), and allowed 51413 TCP/UDP through to that IP and named it "Trans." For good measure I allowed the range 6667:7000 through on both TCP/UDP to the same IP as some have mentioned 6969 being a port Transmission uses. I've configured, using gUFW, those same ports. 

I've made a bit of progress, but I'm still stuck. Now when I test connection under Transmission tab for "network" I get back that port is 51413 is "Open" :P . Previously, it would say closed. I tried changing the port in Transmission options to 6969, just to see and check its status...it returned "open," which is good, and for good measure I tried known closed ports such as 8000 and 5500--both returned "closed," another good sign. 

While Transmission reports the proper ports are now "open" I still can't get anything to download, and neither will it allow uploads :confused:. I'm thinking Transmission is using other ports than it claims to be (51413 and 6969). How would I monitor what ports Transmission is actually trying to use? Thanks a bunch for getting me this far!

---

### Post by Bluenoser81 on 2012-05-16
Nevermind...fixed! I just restarted the router and voila! Download and upload works according to the settings used in the above post. The only catch is that if my IP changes I will have to log back into the router and change the forwarding IP, but that's a 10 second fix. I really need to get a new router one of these days...

Thanks to the help of a fellow canuck, Toz! ;)

---

### Post by Toz on 2012-05-16
No worries - glad I could help a fellow canuck. 

As for the mac address piece, its not located in the port forwarding section. If your router does have this functionality, it would be located in the section where you configure the DHCP settings for the internal LAN. Feel free to post back the make/model of your router and I'll see if I can find out if the functionality exists and where its located.

---

### Post by Bluenoser81 on 2012-05-16
Looked around a bit more in the web menu and couldn't find it, but if you're willing to try to find that functionality it is a Linksys Wireless-G WRT54G model.

It did find the following from the help section for the port forwarding: "[FONT=Arial]When users send this type  of request to your network via the Internet, the Router will 		forward  those requests to the appropriate PC. Any PC whose port is being 		 forwarded must have its DHCP client function disabled and must have a  new static 		IP address assigned to it because its IP address may change  when using the DHCP function."

I think I understand that, I'm just not sure how to do that in practice. Is that something I could set up for just my computer (there are 3 computers using this wireless, plus 3 mobiles), or would disabling DHCP only be an all-or-none sort of switch? Thanks in advance. 
[/FONT]

---

### Post by Toz on 2012-05-16
Just looking at the manual, and it doesn't look like this router has that functionality (usually called "DHCP Reservation"). However, what you can do is _manually_ set an ip address for your device that is outside the dhcp range and port forward to that address.

If you look at the DHCP tab in the router settings you will see a starting IP address (default = 192.16.8.1.100) and a "Maximum number of dhcp leases" value. This means that all dhcp connections will use the ip addresses in the range of 192.168.1.100 to 192.168.1.xxx where xxx is 100 plus the value in the "Maximum number of dhcp leases" box. In reality, this network subnet can take any address from 192.168.1.2 to 192.168.1.254 so if you manually set and address outside of the dhcp reserved space, you should be ok. 

For example, if the router is set at its default values, the easiest way would be to manually set your computer to:
- ip address = 192.168.1.99
- subnet mask = 255.255.255.0
- gateway = 192.168.1.1 (this should be the address of the router itself)
- dns = 192.168.1.1 (this should also be the address of the router)

And then change the port-forwarding rule to point to 192.168.1.99.

One thing to keep in mind if you end up going with a manual address is that if you connect to different networks/routers and depend on dhcp to do so, you'll need to change your network card from manual to dhcp to make the connection.

---

### Post by Bluenoser81 on 2012-05-17
> **Toz said:**
> 
For example, if the router is set at its default values, the easiest way would be to manually set your computer to:
- ip address = 192.168.1.99
- subnet mask = 255.255.255.0
- gateway = 192.168.1.1 (this should be the address of the router itself)
- dns = 192.168.1.1 (this should also be the address of the router)


Works perfectly (posting now from my new 192.168.1.150 IP ), I didn't know you could do this, this has been a great learning experience! I would like to learn more about networking basics like this in general, what would you recommend for learning? I understand some basics, but find reading the wikis on TCP/IP and networking protocols to be a bit mind boggling for a beginner to be honest. Thanks again!

---

### Post by Toz on 2012-05-17
> **Bluenoser81 said:**
> I would like to learn more about networking basics like this in general, what would you recommend for learning?
I don't really know what to recommend. My knowledge came mostly from internet tidbits and hands-on trial and error. I'm sure you can find alot of free online resources to help understand it.

---

### Post by Ms. Daisy on 2012-05-18
> **Bluenoser81 said:**
> ...I would like to learn more about networking basics like this in general, what would you recommend for learning? I understand some basics, but find reading the wikis on TCP/IP and networking protocols to be a bit mind boggling for a beginner to be honest. Thanks again!
I was able to wrap my mind around the concept using these free tutorials I found:

[http://www.trainsignal.com/blog/free-computer-training-videos/free-networking-training-videos](http://www.trainsignal.com/blog/free-computer-training-videos/free-networking-training-videos)

In particular I liked the "TCP/IP and Networking Fundamentals" which was an 8-part series.

---

