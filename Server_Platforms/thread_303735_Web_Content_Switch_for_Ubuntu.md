---
title: "Web Content Switch for Ubuntu"
date: 2006-11-20
forum: Server Platforms
---

### Post by Roddles on 2006-11-20
Hi

I have been using Kubuntu for a while now and love it. The stability is fantastic, so much so that I now run any Windows machines that I need to run in VMWare Virtual Machines hosted on a Kubuntu Server. 

I would like to take this a bit further and run multiple web servers of varying types on my network - the catch is however, that it all has to come through a single IP address.

I dont want to run virtual web servers on a single machine - what I want to do is run multiple web servers running in different VMWare virtual machines or other physical machines with their own IP Address.

In order to do this - I need some sort of Web Content switch setup which will redirect web based traffic (port 80 and 443) to different web servers (different internal IP Addresses) based on the Host Header of the web request, ie, [www.websiteA.com](www.websiteA.com) will be routed to 192.168.1.100, and [www.websiteB.com](www.websiteB.com) will be routed to 192.168.1.101. These are both different machines.

Is there a package available for Ubuntu/Kubuntu which enables me to set up Web Content Routing based on the Host Header value of a web request on port 80 or port 443?

I have done some searching for this information and know it is possible to do what i want to do - just havent found a package to do it yet. 

My apologies if there is already a post about this - I didnt manage to find one during my searches of the forums.

Any help would be much appreciated.

Regards

Rod.

---

### Post by tturrisi on 2006-11-20
One way to easily do this is to configure the servers and daemons on each machine to use different ports:
```
server		www		ssl		ssh
server1		80		443		22
server2		8080		 444	       3022
```

Then use router port forwarding to route to the target servers.

---

### Post by cyris| on 2006-11-20
yup bind to different ports.

---

### Post by Roddles on 2006-11-20
Everything will be coming through on 1 public ip address, 1 port. ie, the public ip address for site [www.siteA.com](www.siteA.com) is 100.100.100.100 port 80, and the public ip address for [www.siteB.com](www.siteB.com) is Port 100.100.100.100 port 80. 

The internal ip addresses are 192.168.1.100 for [www.siteA.com](www.siteA.com) and 192.168.1.101 for site [www.siteB.com](www.siteB.com) respectively. 

There is only 1 hole in the firewall which allows port 80 through from the public IP Address od 100.100.100.100, so port 8080 etc cant get through. 

The only diffentiating attribute of the request is the Host Header, so I dont think that port forwarding will work - unless there is a way to forward based on the Host Header. 

Can you do this using the method you suggested? If so - where can I find information on how to do this?

Sorry - Im relatively new at this this level on Linux.

Cheers

Rod.

---

### Post by tturrisi on 2006-11-21
If public wan ip = xx.xx.xx.100 & firewall passes port 80 requests, then config router to pass port 80 to server1.  Users outside the lan connect by typing [www.siteA.com/](www.siteA.com/).

Users wishing to connect to serv2 access by typing [www.siteB.com:8080/](www.siteB.com:8080/).

You must config the router to use port forwarding for this to work.

Otherwise, you will need a 3rd computer between the router & a switch, and this comp handles redirects to target servers based on either:
1. virtual host configs
2. form input values

You could also handle this using an html doc on server1.  The default index page on server1 has a table of links that send the user to the desired destination based on what he clicks.  You could also do this automatically using index.php (all traffic must be routed to server1 by default):
```
<php?
if (ereg("www.siteA.com", $_SERVER['HTTP_HOST'])) {
header("Location: /server1-target-folder/");
}
elseif (ereg("www.siteB.com", $_SERVER['HTTP_HOST'])) {
header("Location: http://lan-ip-address-of-server2/target-folder");
}
else {
?>
<html>
<head><title>Index</title></head>
<body>
<h1>Choose:</h1>
<p><a href='/server1-target-folder/'>click here for server1</a><br>
<a href='http://lan-ip-address-of-server2'>click here for server1</a></p>
</body>
</html>
<?php
}
?>
```
Such a script requies that you have a fully qualified domain name and a dns server somewhere that routes theb names to your wan ip.

---

