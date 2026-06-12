---
title: "Setting up external web server access"
date: 2007-07-14
forum: Server Platforms
---

### Post by zuccs on 2007-07-14
hey guys,

I have read through just about every related thread on this forum, but I still can't quite get this working..

I have LAMP running on feisty, and when I enter [http://localhost/](http://localhost/) on the server it displays the correct default page...

When I type in [http://192.168.2.10](http://192.168.2.10) from another computer on my internal network, it works fine also. 

Now I have setup a dyndns account, and set my router to automatically keep this up to date. When I type in my URL that they gave me, this goes to my router config page. 

I know it has something to do with port forwarding, but I have never done this before.

I have forwarded port 80 on TCP and UDP to my internal server IP (192.168.2.10). Is that all I should have to do? Is apache set to default to port 80? 

The only thing I can gather from reading is that my ISP is blocking port 80 so I cannot host a website. What are the ways around this? Am I doing everything else correctly?

Thanks for any responses guys...

---

### Post by Footballkid4 on 2007-07-14
Chances are that your router has remote administration/management enabled on port 80.  If you do want to keep remote administration on (I don't think you should, but you can if you choose), change it to another port such as 8080, and if possible, do it over an https connection.

I believe remote administration takes precedence over port forwarding.

---

### Post by zuccs on 2007-07-14
So the inbound port will be 8080 and the private port will be 80 (on my server: 192.168.2.10) ? Is that correct? Do I need to set it up for both TCP and UDP?

---

### Post by zuccs on 2007-07-14
UPDATE: I tried what you said, and even restarted router and still same problem...

I think it will just be something simple like this. Perhaps my ISP is blocking me from doing this, or does the 8080 thing get around that too?

---

### Post by lenaubry on 2007-07-14
Not being too savvy with routing myself, I use [http://www.portforward.com/routers.htm]("http://www.portforward.com/routers.htm")

---

### Post by zuccs on 2007-07-14
Hmm... thats a great site, and I followed the instructions and forwarded ports 80 and 443 for apache to work, but still the same problem...

any other ideas guys?

---

### Post by Mr. C. on 2007-07-14
Zuccs,

Your router may not support NAT loopback with port forwarding.

You need to use your WAN IP from the WAN, not from your LAN.  If you use your WAN IP while on your LAN, you will end up at your router's web interface.  Have someone remotely try your URL (send me a PM if you want me to test and you don't want to share your URL).

From your test, you cannot determine if your ISP blocks port 80 inbound, as your requests never get to your ISP - your router internally recognizes its WAN IP and simple forward those requests to itself.  You'll need an outsider to test.

MrC

---

### Post by zuccs on 2007-07-14
aah, thanks for the reply mate.

can I just test it through a web proxy then? Is that the same thing? If not I will drop you a PM.

Thanks for your reply, thats starting to make more sense.

---

### Post by Mr. C. on 2007-07-14
The requirement is that the requesting IP must come from the WAN, so that your router can correctly NAT/PAT to your web server.

MrC

---

### Post by zuccs on 2007-07-14
NAT enabling is turned ON in my router settings by the way too...

---

### Post by bukwirm on 2007-07-14
So, make sure:
1. Your router's Remote Administration is turned OFF.
2. You have forwarded port 80 to port 80 on your server.

NOTE: If you want to forward a different external port (such as 8080), make sure you include the port number in the URL.

If it still doesn't appear to work, you could post the URL here so we can tell you what we see.

What router do you have, by the way?

---

### Post by zuccs on 2007-07-15
Ok I have it working!! I can view it via :8080 through a web proxy.

Thanks for all your replies...very much appreciated!

Another question, obviously the default directory for apache is /var/www/, now I have mapped another directory and this works via the dyndns URL too, but how can I change the default URL to be this other directory?

If this doesn't make sense, what I want to do, is keep my web files on a separate (removable) hard drive, and not store them on the ubuntu hard drive.

@bukwirm: its a belkin wireless router (if it still matters..)

---

### Post by Mr. C. on 2007-07-15
The easiest way to do this is either:

a) a virtual host directive in apache
b) change your ServerRoot (eg. ServerRoot "/usr/local/httpd") in your httpd.conf file
c) replace /var/www with a symbolic link which points to a directory on another file system.

Restart the server if you choose (a) or (b).

MrC

---

### Post by zuccs on 2007-07-15
Ok, I will give that a shot, thanks.

Another on topic question...

How do I set a private static IP address? I currently have DHCP enabled, and when the server gets disconnected or something, sometimes the last digit might change. How can I ensure this is always kept the same so I do not have to keep mapping drives on other computers? Is this a router specific thing? Do I need to turn DHCP off, and set an IP address for each computer individually?

---

### Post by dysolve on 2007-07-15
what brand of router do you have??

The easiest way to set a static internal ip is to do it in ubuntu.
 but if you tell me your router brand and model I can let you know what to do in that router to reg static ips working and also a few other handy tips..

---

### Post by zuccs on 2007-07-15
Its a belkin F5D8230-4... thanks bud.

---

### Post by Mr. C. on 2007-07-15
There are a couple things you can do:

1) if your router supports DHCP with static assignments based on MAC address, you can configure DHCP to give the same IP each time to the assigned hardware.

2) Static IP

3) Setup your Ubuntu system to use a static IP, but obtain DHCP information for the other information  (such as DNS servers, domainname, etc.)

DCHP servers are supposed to provide the same IP for lease renewal, and clients are required to ask for the same address.  However, if the network is not brought down correctly such that the DHCP RELEASE message is not sent to or received by the DHCP server, the server will not give the same IP, and you'll see a new IP for your station.

The general, almost universal, rule of thumb you should follow is to provide static IPs for servers that provide services to other stations.  The IPs should never change.

MrC

---

### Post by zuccs on 2007-07-17
Hey, I would love to go with option #1, but I don't think my router can do this, or I just don't know how. I went through every page in the config, and there is nothing similar to this...

I don't really want to disable DHCP, because it will be a pain adding computers down the track. And Option #3 sounds a little too complicated for me. Is it?

Do you know where any good instructions are for this? I have searched for private static IP but can't find anything helpful. Thanks agian.

---

### Post by Mr. C. on 2007-07-18
You can set your Ubuntu station to use a static IP outside the range of your DHCP IPs given out by the DHCP server.  There is no reason to disable DHCP on the router.  This gives you the best of both worlds.

Say your router provides 192.168.0.1 - 192.168.0.100 as the DHCP range (this is typically configurable in the router).  Then, just give you Ubuntu station a static IP as 192.168.0.201 and set the netmask and broadcast address.  Its pretty trivial and not worth the time mucking with the dhclient.conf file.

MrC

---

### Post by zuccs on 2007-07-25
Thanks for all your replies guys... I actually managed to get the server going nicely, and VNC'd from over the internet ;)

I just put a new NIC in, and obviously I never fixed that static IP problem, and my server got assigned a new IP address..

Mr. C. can you explain how to do this in ubuntu?

I have gone to System > Admin > Network

Clicked on Wired Connection, set that to Static IP Address, entered 192.168.2.20, subnet: 255.255.255.0, and gateway address as 192.168.2.1 (is that right?)

In your post you suggested that I set the broadcast address? Where is this? Am I doing everything wrong?

Appreciate your response, thanks.

---

### Post by zuccs on 2007-07-25
Oh wow I'm stupid! I just read your post again, and decided to change it to .222 which is OUTSIDE the range! Apparently if you try to use one that is not being used, but inside the range it won't assign it! Thanks. I will let you know how this all goes.

---

