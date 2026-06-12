---
title: "Network Configuration, Reserved IP, Virgin Media"
date: 2015-11-25
forum: Server Platforms
---

### Post by Benjaman_Woolner on 2015-11-25
Please help, I have a webless webserver :(

I'm going through [this help guide]("https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p3") to help get my server set up correctly as I'm new to all this. I'm likely to ask a lot of annoying questions so I apologise in advance I just want to get this right. I've spent a couple of days trying on my own to fix this now it's time to concede and accept help.

I'm running into issues from Section 7 Configure The Network. I skipped Section 6 as I use nano.

My ISP is Virgin Media and we have a residential package. I know that I can't get a static IP address unless I pay a fortune out and get a business account so instead I'm attempting to use a Reserved IP but I don't know if this will actually work for a webserver. I know there is a risk of IP's changing this way but the server is mainly for my portfolio rather than all public access.

After the initial install of Ubuntu Server 14.04LTS 32bit my server and my Superhub2 can see each other.

When I try to edit [COLOR=#000000][FONT=Courier New]*/etc/network/interfaces *[/FONT][/COLOR]and then reboot the system neither my server nor my Superhub2 can see each other.

I'm not sure if it's because I change the file from DHCP to static, because I have my details wrong or something else all together.


[HR][/HR]iface eth0 inet static (change DHCP to static)
    address 192.168.0.xxx
     netmask 255.255.255.0 (I assumed this to be Subnet Mask)
     network ???
     broadcast 192.168.0.1 (I assumed this to be the Router IP)
     gateway 192.168.0.1 
     dns-nameservers 192.168.1.200 192.168.1.225 8.8.8.8 (left this unchanged as was unsure)

[HR][/HR]
How do I find out the network address and did I do right leaving the dns-nameservers untouched?

On the next section editing [COLOR=#000000][FONT=Courier New]*/etc/hosts *[/FONT][/COLOR]I changed the IP address to mine and made the rest look the same as in the example provided in the help guide. Looking at the link format used in the guide got me thinking, will all the websites hosted on the server be accessed in that format I.E. server1.mysite1.com, server1.mysite2.com etc. If so is there a way to set it up so it looks more like mysite.com/site1, mysite.com/site2 etc?

When I got to Section 8 Edit /etc/apt/sources.list And Update Your Linux Installation I couldn't find a section that looked like the example given in the help guide. I'm confused by what they mean when the guide says > [COLOR=#474B51][FONT=Tahoma]make sure that the [/FONT][/COLOR][COLOR=black][FONT=Courier New]*universe*[/FONT][/COLOR][COLOR=#474B51][FONT=Tahoma] and [/FONT][/COLOR][COLOR=black][FONT=Courier New]*multiverse*[/FONT][/COLOR][COLOR=#474B51][FONT=Tahoma]repositories are enabled.[/FONT][/COLOR] I geuss that means make sure the're not commented out but the CD bit confuses me totally as I see no mention of it.

If you've made it this far I'd like to thank you for sticking with it and I hope maybe with your help I can get a working server so I can host websites etc.

Thanks

---

### Post by Melnik_Hoogland on 2015-11-25
The way I understand it, a reserved IP is different from a static IP. They have the same concept (letting you have the same IP address every time you connect), but they work in different ways. The major difference -- and this is your problem -- is that reserved IPs still use DHCP, while static IPs don't. The idea with a reserved IP is that when you ask the DHCP server for a IP address, it knows the computer asking for an address is yours and gives you your reserved IP.
Basically, you shouldn't switch to static if you aren't using a static IP. I don't know if you actually have a reserved IP with your ISP, but either way, you should still use DHCP. I don't think you should edit /etc/hosts either; I have a working server and it just has the default hosts file.

As for your questions about section 8, you should be able to just copy and paste the file into sources.list, although you should back your original one up in case it stops you from being able to apt-get anything. Don't forget to do an apt-get update afterwards like the tutorial says.

---

### Post by darkod on 2015-11-25
1. In /etc/network/interfaces delete the network and broadcast entries, they are not needed. They are calculated automatically from the netmask value. And your broadcast value is wrong, it can't be the same as gateway (the router).

2. Not sure what you are trying to do and with which "reserved IP". Your server at home will be behind the virgin router, so only the router will have public IP assigned to it. Whether it will be reserved (always the same) or not, you can't control from your home server or any home PC. That depends on virgin end.

3. The first two nameservers specified look wrong because if you are on 192.168.0.x home subnet, how are you going to communicate with 192.168.1.x nameservers? But the 8.8.8.8 will work, that's google nameserver. Another google nameserver you can use is 8.8.4.4.

See if you have internet and local network connectivity after the above.

Don't worry about repositories for now, and besides I think the universe and multiverse are enabled by default.

PS. About the private IP you are assigning to the server with the address line, make sure it is in your router subnet. You can't simply follow any guide telling you to use 192.168.0.x if your router is in the 192.168.1.x subnet. You understand that?

---

### Post by Benjaman_Woolner on 2015-11-25
Cheers Melnik, your explanation makes a lot of sense so I will test that out tomorrow in the hope that that fixes a lot of my issues.

Darkod as I say I'm new to this so it's good to know that the network/broadcast entries aren't needed. I know the IP and the Gateway addresses are correct as I used the ifconfig command :)

With regards to the reserved ip, if I go into the advanced settings on the Superhub2 I can set the IP as reserved maintaining the address for the server (the only reserved ip I have setup). You've said that only the router will have a public IP so is this going to prevent me setting the server up even if I sorted out my connection issues?

Thank you both for you help/advice so far

---

### Post by darkod on 2015-11-25
Reserving an IP on the router is obsolete if you use static IP configuration on your server. The IP reservation is for the case where you leave the server using dhcp and you assign always the same private IP to it by identifying it from the MAC address for example.

Select a private IP outside the dhcp range and use static setup on the server, you don't need any reservation. For example set the dhcp range to something like 192.168.0.100-192.168.0.150 and set 192.168.0.10 on your server.

When only your router has a public IP from the ISP it does not prevent you from installing servers at home. However, you have to be aware that none of those servers will be reachable directly from the internet because only the router actually has a public IP. So any traffic from the outside reaches only the router.

On many routers, for this case, you can forward ports to a private IP on the internal network. For example, if you want your server to be a web server, using the standard ports 80 and 443, you can forward tcp ports 80 and 443 to 192.168.0.10 (as per my above example of IP choice). In such case the router will pass on traffic arriving on 80 and 443 to the server.

You should also be aware that many ISPs block the standard ports for server services so even if you set up everything good, it might not work. This is done from ISPs to prevent running servers at home. :) So, depending what you want to use it for, and if you want it to be reachable from the internet, you need to do certain setup and it will also depend on the ISP policy/filters.

---

