---
title: "Setting up a File Server?"
date: 2006-07-18
forum: Server Platforms
---

### Post by malius on 2006-07-18
Greetings all,

I am about to buy a new machine to use as a file server and have several questions that I hope the community can address.

**Background/Setup:**
I am looking at purchasing the following system: [http://www.newegg.com/product/product.asp?item=N82E16856110030](http://www.newegg.com/product/product.asp?item=N82E16856110030)

The low power consumption and overall cost should be ideal for what I am trying to achieve.

I will be placing 2 identical hard drives into this machine in which I would like to set up a raid 1 (Mirroring) configuration.

**Questions:**
[LIST=1]
[*]Has anyone purchased/used this barebone machine and what are your thoughts?  Are there any issues I should be aware of?
[*]How difficult is it to install a server configuration with raid 1? Any links would greatly be appreciated as search of this forum has turned up varying results (Harware/Software/etc).
[*]Is it absolutely necessary to setup a static IP for the server, or is setting the hostname sufficient?
[/LIST]

**Conclusion**
I have worked out many of the minor details by installing Ubuntu server via VMWare, but the above questions are my main concern at the moment.

---

### Post by inthewayboy on 2006-07-18
Haven't used that exact barebones but I have used several EPIA mobo's which use a similar CPU to the one this has. They are quite and power-friendly, but they are slow too. Of course setting it up as a basic fileserver without a GUI shouldn't be a problem. 

In regards to setting it up with a RAID, you normally create and maintain the RAID Array using the RAID controllers firmware, so when it's all configured your OS will only see the resulting Array. As long as the OS has support for your controller there really isn't anything different than a regular server install. Just to be clear, you need to create and format the Array before installing the OS.

And finally...Static IP is the way to go. There are too many variables with DHCP for something like this. BTW, what would be handling the DHCP. One option that isn't always around is to setup a Static DHCP lease. The end result is the server can be set for DHCP but it will always get the same IP based on the MAC Address. Again, this isn't a popular feature yet in many consumer routers.

If you can install it in VMWare then you should be good to go. Just check in on the RAID controller and if ubuntu has built-in support for it...if it does you shouldn't have to do anything different. The OS should never really know about the RAID Array other than to report if there is an issue with it (HD Failure).

Oh, and a final option, and one that I know nothing about, would be to setup a software RAID Array. But that's out of my league...good luck!

---

### Post by malius on 2006-07-19
Thanks for the reply and information inthewayboy!  Once the machine is available again for purchase, I will post my progress on the installation.

---

