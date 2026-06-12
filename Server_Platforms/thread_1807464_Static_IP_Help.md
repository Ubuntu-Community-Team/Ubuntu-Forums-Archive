---
title: "Static IP Help"
date: 2011-07-19
forum: Server Platforms
---

### Post by Compulsed on 2011-07-19
I'm extremely new to networking processes and servers, this is probably why I'm having this problem. I've been searching for hours other resources, videos etc, but to no avail. 

It's probably something obvious I'm missing so a quick look would be amazing.

The question is in the linked  png, any additional questions feel free to ask.
Thanks in advance

~Compulsed

---

### Post by lisati on 2011-07-19
I usually set static IPs via my router's browser-based admin panel. This varies according to make and model of router, and helps avoid conflicts when connecting one of my machines to someone else's network.

Yes, it is possible to tweak the settings at the Ubuntu end, but having never done it myself, I'll defer to the wisdom of others.

---

### Post by Bucky Ball on 2011-07-19
Opposite to Lisati, I never set static IPs on the router, only on the local machines. I leave DHCP server on on the router but limit the IP addresses it can serve to a specific range (for visitors wanting to use the network easily). I then set the static IPs on the local machines outside of that range. For instance.

Router DHCP range = 192.168.1.10 - 192.168.1.20

Then set the static IPs on the local machines below 192.168.1.10 or above 192.168.1.20.

You can ping your router fine so the LAN looks okay. Looks to me that perhaps you haven't got your DNS server addresses right at the Ubuntu end in Network Manager setup (or whatever you happen to be using). You still need to set these up at your end on wired connection if you are using static IPs.

---

### Post by Lampi on 2011-07-19
@Compulsed: you should check the routing to your gateway:

```
route -e
```

You should find the default gw ip in there, if not:

```
sudo route add default gw 192.168.1.1.
```
... should add it

then you should also check /etc/resolv.conf (your DNS lookup server's IP address should be mentioned in there.)

---

### Post by Compulsed on 2011-07-19
@Lampi
I've added the new gateway, although I'm not sure completely sure what's mean to be in  /etc/resolv.conf, what I currently have will be posted in the new attachment 
By the way thanks so much for helping,

@Bucky Ball
"Looks to me that perhaps you haven't got your DNS server addresses right at the Ubuntu end in Network Manager setup (or whatever you happen to be using). You still need to set these up at your end on wired connection if you are using static IPs."

I'm looking into how I edit it now, hopefully all goes well. 
Same, thanks so very much. 


Out of curiosity, why do I need the DNS's?

---

### Post by Compulsed on 2011-07-19
I changed my IP address to 192.168.1.152 and I seem to now be able to download packages but not ping google, or connect using SSH, that is if it may help you.

---

### Post by Lampi on 2011-07-19
> **Compulsed said:**
> @Lampi
I'm not sure completely sure what's mean to be in  /etc/resolv.conf, what I currently have will be posted in the new attachment 
[...]
Out of curiosity, why do I need the DNS's?
DNS = dynamic name server - this server will resolve the url you type to ip addresses. In /etc/resolv.conf you make sure this DNS server itself will be found. If you don't know what server to use you can try the google DNS - it is: 8.8.8.8

But you should ask around (admin, your internet service provider) to figure out the dns ip of your provider.

can you give us the full output of "ifconfig"? I wonder what's up with your localhost.

you can also try to re-initialize the network interface like this

```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by Compulsed on 2011-07-19
By the way I can't explain how grateful I am that you're helping me.

Also I usually used the "sudo /etc/init.d/networking restart" command.

---

### Post by Lampi on 2011-07-19
ifconfig looks good ... I noticed your hostname is UbuntuLaptop>VM< - does this mean you are running inside a virtual machine? If you are can you be more specific about your virtual host setup? Maybe it blocks the route to your gateway?

---

### Post by Compulsed on 2011-07-19
What you said makes perfect sense, I'm intending to learn how to user the server through a VM then apply it to an actual server so if you can't help I may just go directly into making the server and see if it works from there

I got a little happy when it came to typing in 8.8.8.8 
thinking it might have changed something, but it didn't.

---

### Post by Compulsed on 2011-07-19
and by that I mean...

---

### Post by Lampi on 2011-07-19
Can you try bridged networking? I always use bridged, because it's the easiest setup: you bind your virtual network adapter to your host adpater (= bridge)

You can drop the rest of the network settings, they don't make sense to setup in the vm host.

By the way: Please mention stuff like this in your initial posting, it's important to know you where trying to connect a vm, one can't guess these things without a magic eight ball ;-)

---

### Post by Compulsed on 2011-07-19
Any idea as to how I can do that using VMware?

---

### Post by Lampi on 2011-07-19
I'd consider using the ubuntu wiki on Vmware:

[https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)

And there are several howtos in this forum.

Like I said I'd try bridged networking, but maybe that's just me...

---

### Post by Compulsed on 2011-07-19
> **Lampi said:**
> Can you try bridged networking? I always use bridged, because it's the easiest setup: you bind your virtual network adapter to your host adpater (= bridge)

You can drop the rest of the network settings, they don't make sense to setup in the vm host.

By the way: Please mention stuff like this in your initial posting, it's important to know you where trying to connect a vm, one can't guess these things without a magic eight ball ;-)

Yeh, Sorry I knew it was a bad idea not to mention that although I thought it was irrelevance seeing as it sets it'self up. With the new information what can I do?

---

### Post by Compulsed on 2011-07-19
> **Lampi said:**
> I'd consider using the ubuntu wiki on Vmware:

[https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)

And there are several howtos in this forum.

Like I said I'd try bridged networking, but maybe that's just me...

You've been great, by the way I couldn't have asked for a better person to help :)

---

### Post by spynappels on 2011-07-20
Did you set this up on VMware server running on windows or on a VMware ESXi host?

I think the first option but need to just check....

---

### Post by Compulsed on 2011-07-20
I have no idea, if you could tell me how I could check...? but essentially I did it through windows with all standard options.

---

