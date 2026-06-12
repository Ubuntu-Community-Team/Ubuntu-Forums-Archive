---
title: "lose internet with static ip ubuntu-server16"
date: 2019-09-12
forum: Server Platforms
---

### Post by carbu2 on 2019-09-12
Hello to who reads: ... I have given up ... I have not been able to understand why I could not connect to the Internet after having changed my DHCP (dynamic) ip to static parameters. It really should be something simple but there is something that doesn't work for me.

First ... I am testing to understand how the ubuntu 16 server works on an old 32-bit machine. A 2400 sempron with 1GB in ram. I want to do all the possible tests before buying a machine that is 64 bits.

I am testing various CMS for community organizations that seek to use their resources and recycle as much as possible.

With ifconfig -a it gives me the following parameters:
Addr: 201.187.51.57
Bcast: 201.187.63.255
Mask: 255.255.240.0
Inet addr: 127.0.0.1
Mask: 255.0.0.0

with Ip route show

Default via 201.187.48.1 dev enpos4
201.187.48.0/20 dev enp0s4 proto kernel scope link src 201.187.51.57
 

Ip a list
Inet 201.187.51.57/20
 201.187.48.188/20
Brd 201.187.63.255

Ip r
Default via 201.187.48.1 dev enp0s4
201.187.48.0/20 dev enp0s4 proto kernel scope link src 201.187.51.57

With nano /etc/resolv.conf
nameserver 190.96.9.250
nameserver 190.153.164.250

sudo route -n
Destination 0.0.0.0 - 201.187.48.0
Gateway 201.187.48.1 - 0.0.0.0
Genmask 0.0.0.0 - 255.255.255.240

I have done several tests with
sudo nano etc / network / interfaces and I have put, for example the following: ...

# Ethernet interface served by the "static" network management model
# (static network configuration)
eth0 auto
iface eth0 inet static
address 201.187.51.57
netmask 255.255.255.240
gateway 201.187.48.1
broadcast 201.187.63.255
dns-nameservers 8.8.8.8 190.96.9.250 190.153.164.250
post-up echo "Interface enp0s4 successfully raised"
post-down echo "Interface enp0s4 successfully downloaded"

The part from the dns I incorporated them just in case it is a dns problem and that shows me that the system is up or down.

Also (by chance) I have done sudo ip addr flush enp0s4 sudo systemctl restart networking.service

I've done reboot (in case I didn't take the previous command) and it's the same.

With ping -c3 8.8.8.8 or any previous one (or directly) it does not connect. Only once I could do something ... but in the end I did not know what it was exactly (many changes and tests that I no longer remember).

I have seen and read a host of similar situations, I have tried dozens of configurations and I don't find it. Frustration over something that takes away time and energy to keep moving forward in other more urgent things. I want to learn. Thank you

---

### Post by darkod on 2019-09-12
First of all, you can't simply decide to use a static IP unless it was assigned to you to use. If you receive some IP by dynamic, that doesn't mean you can convert the settings in static and continue to use it. The DHCP server will not be aware of this and will assign the same IP to another dynamic client. Which will lead to duplicate IP and errors in network communication.

Second, in your manual settings the netmask is wrong. If you check again your ifconfig -a output, the mask is 255.255.240.0 (which corresponds to /20 subnet). But in your static settings you use 255.255.255.240 which is very different from 255.255.240.0.

But again, even if your static settings work for a short while, you should not be "taking" public IPs and setting them up as static unless they were specifically given to you.

---

### Post by carbu2 on 2019-09-12
I do not understand. It is assumed that when we want to configure a server ... we generally consider using a static ip. A lot of information is given to do so ... and how to do it. So what does it mean to "give an ip" or "assign an ip? This must be assigned by the internet provider (company) ... or does it mean that an IP must be leased to another company. It is obviously possible. There are many companies delivering that service ...

In relation to the netmask ... it's just one of many alternatives I put ... this one in particular comes out of the same ifconfig.

I have finally read and analyzed:

address: enter an IP address of the same range as your network or the router's LAN IP address. The IP addresses reserved for class C networks range from 192.168.0.0 to 192.168.255.255. Therefore in this field we could have chosen other IP
I remember this comment that I put here to capture more the meaning of each part

netmask: 255.255.255.0 &#8221;: I have chosen my netmask to be 255.255.255.0. Almost 100% of home networks use this netmask. The network mask defines the maximum number of computers or hosts our network can have. When using 255.255.255.0 the maximum number will be 254 computers. In the case of needing to build a network of more than 254 computers we would have to mount a class B network that will allow us to have up to 65534 computers.

network: its we provide that, for example, we give a value of 192.168.1.0 will represent all the devices connected to our network. Normally with IPv4 the lowest address in the IP range is reserved to refer to the entire host of the network.

broadcast: this address can be used to communicate and send packets to all equipment that is part of the same network. The broadcast address is the highest address in the network

Regarding netmask is the subnet mask of that IP address. Netmask: Normally, we have the mask 255.255.255.0 or 24. Both are the same but written differently.

Well ... I only put these comments so that it is understood that I have tried to understand what is happening behind what is not seen at first sight.

That is why it catches my attention that it is necessary to "deliver" an ip. When, theoretically, you must choose an IP that is within certain ranges and interrelates with the other addresses chosen.

That's why I put the info that the work commands have given me. To suggest an alternative or refer me to an article that I have not yet read or analyzed.

Finally, I could simply rent a decent hosting and stop looking for more sustainable or recyclable solutions. It's what everyone does and no more problems are made. It is the easy way out. And I don't like it. Greetings and thanks for the comments. I get it.

Me manejo mejor en español ... pero puedo hacerlo en inglés también. Sólo puse ejemplos de comentarios que he encontrado ... tratando de entender en mayor profundidad cómo funciona al aspecto de las ip fijas en servidores ubuntu ... especificamente en Xenial. Saludos cordiales

---

### Post by TheFu on 2019-09-12
Seems some network knowledge is lacking.  Google "security now! ep 25"  Then read/listen to the series of podcasts called "the way the internet works"  - I think it is 3 parts.  [https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm) is the page with the different links.

**You don't get to choose to switch from DHCP to static.  The ISP decides that.**
You don't get to choose the static IP.  The service provider decides that. It will NOT be network-near the DHCP IP.
You don't get to choose the netmask or broadcast settings.  The service provider decides that.
You don't get to choose the gateway setting.  The service provider decides that.

Picking any of these things outside the values provided by the service provider doesn't only harm you, but it harms your network neighbors.

There is no need to specify the broadcast anymore ( and hasn't been for about 10 yrs).  The netmask handles that.

When posting configurations, please do not interpret the data.  Please post the command used, any options AND the relevant output - use copy/paste and **stay with text**. Wrap it all in "code tags" so the output lines up here like it does in the terminal. Avoid images.

No supported version of Ubuntu directly uses the resolv.conf file on Ubuntu Server anymore.  Any changes to it should happen using resolvconf, the dns-nameservers in the interfaces file or one of the netplan config files.

---

### Post by LHammonds on 2019-09-13
Something else to consider:

Regarding the public-facing IP, that is 100% controlled by your ISP and you get what you pay for.  Residential is typically DHCP and the ISP can even block many server-specific ports that will prevent you from hosting servers at home.  Business connections can differ in rules but also come in flavors of DHCP or static.   It can all be negotiated by there is a higher price for static.

Regarding the private-facing IP, that is 100% under your control.  That is the Local Area Network.  You will have an internal router/modem that will be the gateway between your private network and the Internet public network.

The gateway device usually provides DHCP for your private network and you want to make sure the DHCP range does not take up the entire range of IP addresses...only a portion of it.  You can then use the IPs outside the range of your DHCP scope for static use.

When you setup a server you intend on accessing from the Internet, you will need to configure the gateway device to translate a particular port number to an internal IP / port number.  This is called "port forwarding" or Network Address Translation (NAT) depending on how it is done.

If this does not make sense to you, then you need to do enough research until it does because people get paid to do nothing but this kind of stuff and is not something you can just crank out from scratch easily.  If you already have a network setup and working, then you need to know enough to modify what you have but you still need to know the basic components such as finding out what the DHCP scope is, where to record/update static IP addresses (if you have a lot of them), etc.

LHammonds

---

### Post by carbu2 on 2019-09-13
Ok ... I agree with everything. I could have put the images of the commands and their results from the console.

There could also be a lot of pages here that "show how to set a fixed or static ip on a ubuntu16 server", inclusive videos.

I could also have put a debugged analysis of how communication protocols work, quite deeply.

Just to state that I have searched for a simple, simple, clear answer that serves me and many people who have also asked me. And I've done it by analyzing a lot of related information. It is not my area, but I handle myself deeply in certain subjects, enough to also understand certain other subjects of this type.

I deeply value, in a sincere, open and deeply appreciating the knowledge, expertise and patience of many people who have created and built Unix-Linux and free software. I am a fervent defender and promoter of this platform, despite my expertise in areas of biological and social sciences. I'm not going to stop at this, but I could.

The point is that, for example, the same issue of the resolv.conf file (which I did not mention) or the broadcast one (I said it several times) only as an example - among several - of what I had tried. I had even forgotten.

I could make other comments of form and substance, but I don't think they are necessary. I understand the scope of the technical areas and many times they only remain in the hands of advanced users or experts. It happens to me in my area frequently. However, I have a maxim, if I am not able to explain something complex in a simple and simple way that is able to make me understand without so much trouble or make others feel a kind of ignorance ... I am not on the right track . And that considering that I have to relate to thousands of users, of many different conditions.

I had not wanted to ask this question in the forum because I wanted to find the answer for myself. And / or finally go to the department of some university (which I support and share some projects) and solve it and now. But in this case in particular, I wanted to understand how anyone interested in the subject would do it (and that I would find the same material that I found on the web).

Thank you for your patience, for your comments, for Linux - ubuntu. For the free software, For the people who make all this possible. And because this type of knowledge is disseminated and can be used by those who really need it: the communities

---

### Post by TheFu on 2019-09-13
My main confusion comes from not knowing if you just picked IPs/netmasks and subnets without any input from the internet provider.  All the commands above don't help if the initial input data is wrong.

If you post the exact data the ISP/internet provider gave for using static IPs, then we can help.  If they didn't provide the data for a static IP, then we are done here.  There isn't anything to be fixed. Go back the DHCP.

Linux servers aren't meant for end-users to run.  It isn't hard, but it takes time and commitment to learn.  You can master this, if you like.  [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) should cover most things.

---

### Post by carbu2 on 2019-09-13
Yes ... it was something much simpler than I thought. I thought I was doing something wrong. But I understood He had always worked with servers (up to a certain point) as a user with "certain knowledge". I have been able to correct a series of problems and errors with commitment, work and interest. But I fail things that are technically very simple for others, even though I know or understand them ... practice and experience fail me. It is not my area but I have to give my opinion and decide on these issues in a responsible way and with "knowledge of the cause". I want to give the opportunity to free software wherever I am. And this happens because I know it more and more thoroughly.

If I have made comments, it is in order that, to others that something similar happens, they know what to expect. I think it can serve something.

I'm already seeing the static ip with my provider. In passing with all this situation I have learned a lot about centos servers ... trying to find alternatives to ubuntu16 with old 32-bit machines. And I am struggling with arch linux to go deeper.

There is nothing left but to close and give the corresponding thanks. Regards.-

---

