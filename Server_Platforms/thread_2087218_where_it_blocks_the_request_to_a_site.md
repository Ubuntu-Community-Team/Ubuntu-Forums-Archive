---
title: "where it blocks the request to a site?"
date: 2012-11-23
forum: Server Platforms
---

### Post by iacoposk8 on 2012-11-23
Hello everyone! I'm doing experiments to run servers generally, with all services.
I need to be able to connect to internet "the PC" connected to the server but I can not.
On the server I installed Linux distribution called smoothwall.
My question however is: how do I test to see what the problem is the connection? in that part of the chain is broken the request to a network site? to see if it is a problem of ports or something?
I have verified that the computer is able to do ping to the server and the other I also verified that the server is able to ping to the internet (with the ip of google)
thanks :)

---

### Post by darkod on 2012-11-23
1. Make sure you have FORWARD policy as ACCEPT on smoothwall (not sure if that's what they call the policy). It needs to allow forwarding through it.

2. You also need to enable ip_forward in /etc/sysctl.conf on the server. I don't know whether smoothwall would do that. Until forwarding is enabled the server will not forward packets between the external and internal interface.

PS. I suggest you use iptables directly, and not smoothwall. It looks good at first glance, but it has some limitations later, depending what you want to do with it. iptables is much more flexible and even easier to set up, although it might not look like that at the start.

---

### Post by iacoposk8 on 2012-11-24
smoothwall default blocks all traffic from the network adapter red to green. I unlocked the door 80 from the traffic from any ip ... but still not enough.
commands that I can run from the terminal to see what is blocking traffic? if ip addresses, firewall etc. ...?
thanks :)

---

### Post by darkod on 2012-11-24
If I remember correctly, red is the external interface and green the internal. Blocking red to green is normal, that's what firewall does.
For a client machine to have internet access through this firewall it's more important the gree to red rule. Is it open?

Allowing port 80 red to green is pointless, you would need it only if hosting web services on the client machine.

As first test whether it's maybe DNS issue, or routing issue, try to ping by IP, and then by domain, something like:
```
ping 8.8.8.8
ping google.com
```

About six months ago I was doing a project with smoothwall but don't remember all the options in the setup exactly now. Anyway I dropped it and used iptables/ufw combination. If I knew what I learned during the process, I would have used only iptables, much better solution.

---

### Post by iacoposk8 on 2012-11-26
thanks for your help, here are the results:
```

ping 74.125.39.104
5 packs transmitted, 5 received, 0% packet loss

ping google.com
ping: unknown host google.com

```

---

### Post by spynappels on 2012-11-26
Is that from the Smoothwall server or from the client connecting through the Smoothwall server?

That definitely suggests DNS issues, but without knowing if this was on the Smoothwall server or not it is hard to see on which side of the Smoothwall box the DNS problem is.

---

### Post by iacoposk8 on 2012-11-26
I do not know if I understand (I'm not very good at English :)), however, the previous commands have been executed by the server (smoothwall) and not from a computer connected to it

---

### Post by spynappels on 2012-11-26
Ok, that means that the Smoothwall server does not have functional DNS essentially.

That could be due to 2 things most likely:
1. No (working) DNS servers specified.
2. Firewall blocking communication with the DNS servers.

Can you please post the output of the following commands from the Smoothwall server?

```
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by iacoposk8 on 2012-11-26
```

cat /etc/resolv.conf
nameserver 127.0.0.1

cat /etc/network/interfaces
cat: /etc/network/interfaces no such file or directory
```

---

### Post by spynappels on 2012-11-26
Ok, that means you have no DNS servers set other than localhost, which is not correct.

Add some working DNS servers using the following commands:

```
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
echo "nameserver 8.8.4.4" >> /etc/resolv.conf
```

or else open /etc/resolv.conf for editing in Nano using sudo 

```
sudo nano /etc/resolv.conf
```

and add the DNS servers manually

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Ctrl+X to quit and select yes to save.

Then try pinging google.com again

```
ping google.com
```

---

### Post by iacoposk8 on 2012-11-26
I says:
-bash: sudo: command not found
but you can not! if i try to install it tells me:
-bash: apt-get: command not found

---

### Post by spynappels on 2012-11-26
Are you logged in to the Smoothwall as root? If so, you can run the commands without sudo, like so:

```
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
echo "nameserver 8.8.4.4" >> /etc/resolv.conf
```

Then try pinging Google.com again.

---

### Post by iacoposk8 on 2012-11-27
I opened resolv.conf with vim and after launching echo I read:
```
nameserver 127.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4
```
hours ping google.com works perfectly except that the PC (ubuntu) connected to the server is unable to connect to the internet: (

if I remove the last two regenerative PC connected to smoothwall back to work

---

### Post by iacoposk8 on 2012-11-27
if I only write resolv.con
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
PC connected to smoothwall connects to the Internet, however, still will not let me see [www.google.com](www.google.com)

---

### Post by darkod on 2012-11-27
Don't remove the DNS nameservers on the server, it should have them so that it connects to the internet correctly.

Put them back, and then do the similar test on the client:
ping 8.8.8.8
ping google.com

See the result returned.

If both don't work (no ping reply), try this:
Disable the smoothwall firewall temporarily, and try the ping again. Post the results in this case.

---

### Post by darkod on 2012-11-27
> **iacoposk8 said:**
> if I only write resolv.con
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
PC connected to smoothwall connects to the Internet, however, still will not let me see [www.google.com](www.google.com)

When you say connects to the internet, how did you check that if it doesn't open websites? Please be more specific, we need info.

Did you check with ping <IP> ?

---

### Post by iacoposk8 on 2012-11-27
you're right, but I do not know what information they can serve you.
However, the PC connected to smoothwall does not show me the arrows of the connection (in the top bar, next to the clock with the symbol of wifi)
if I write
```

nameserver 127.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4
```is not connected to the network

if I write
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```is connected to the network but does not go on google.com

(in both cases, if I do ping google.com on smoothwall works well)

---

### Post by darkod on 2012-11-27
OK, here is what I would do:
1. Drop the 127.0.0.1 from the nameserver list on the server. If the server itself is not DNS I don't see much point in it. In that case the client will have network connection but not internet.

2. After you have done that, as suggested, on the client post the output of:
ping 8.8.8.8
ping google.com

You already said it doesn't work with google.com, lets see if it works with IP.

3. If it doesn't work, disable smoothwall (put all policies to ACCEPT or similar), and try again.

---

### Post by iacoposk8 on 2012-11-27
I put: 127.0.0.1 and I ran the ping
smoothwall server works, and on the computer connected to it should not be either table because it can not connect to the internet (not the arrows appear on the top bar on the right)
now I try to see if I can set smoothwall so as to allow all traffic

---

### Post by iacoposk8 on 2012-11-27
I tried to create a virtual machine with smoothwall and during installation I set the traffic on the "open" but if I put these two lines in resolv.conf smoothwall can do ping google but the computer connected to the server can not connect internet: (

you are very kind, however, if one day you come in Italy I offer you a drink :)

---

### Post by darkod on 2012-11-27
But delete the 127.0.0.1 from resolv.conf on the server. There is no point to use itself as DNS when there is no dns service running.

Delete 127.0.0.1 on the server and check how the pings on the client go.

I don't remember how smoothwall works exactly, I'll have to try it in VM too. It looks like you might have selected some wrong option during install since it's not so difficult to set it up.

---

### Post by iacoposk8 on 2012-11-27
ok, I removed 127.0.0.1 but the pc connected to smoothwall unable to ping google.com (but it works on 8.8.8.8 )
```
ping: unknown host google.com
```

---

### Post by darkod on 2012-11-27
What are the DNS settings on the client? The DNS server it uses needs to be the smoothwall server. Put the IP of the internal intarface (green) of the smoothwall server as primary DNS for the client.

---

### Post by iacoposk8 on 2012-11-27
non così se ho capito, Devo Andare nel client del resolv.con e aggiungere l'ip del server di pareti lisce?

---

### Post by spynappels on 2012-11-27
> **iacoposk8 said:**
> not so if I understand, I have to go in the resolv.con client and add the ip of the server smooth walls?
 Used Google translate on that ;-)

It depends on whether you have a Linux client or a Windows client, it differs depending on what you use. However, even if it is Linux, you probably should not edit resolv.conf manually, but use Network Manager or equivalent to set up the DNS settings.

---

### Post by iacoposk8 on 2012-11-27
use google translate on everything! : D
my English is very poor :)

on client use ubuntu, now I try to do the experiments. in practice, what should I do? add the dns ip of smoothwall?

---

### Post by darkod on 2012-11-27
Yeah, the internal (private) IP of smoothwall, like 192.168.x.x depending what you used, should be the DNS nameserver for the clients. You can also use a public dns server like 8.8.8.8 on the client too.

If you are running ubuntu desktop, you can click the Network Manager icon top right (the arrows symbol), and go into Edit Connections.

In there you can select a DNS server, depending if the machine is using dhcp or manual setup.

---

### Post by spynappels on 2012-11-27
Ok, I'm going to assume you are on Unity, but Gnome Network Manager will be similar.
Click on the two arrows for networking at the top right of the screen. In the drop down menu go to the bottom, to Edit Connections..

Then you can select the Wired Connection 1 or whatever connection you are using, and click Edit

Select IPv4 settings.

If you are using Automatic (DHCP), you may need to change it to Automatic (DHCP) addresses only.

This should allow you to enter the IP address of the Smoothwall box as the DNS server.
Save the settings and see what happens.

---

### Post by spynappels on 2012-11-27
> **darkod said:**
> Yeah, the internal (private) IP of smoothwall, like 192.168.x.x depending what you used, should be the DNS nameserver for the clients. You can also use a public dns server like 8.8.8.8 on the client too.

If you are running ubuntu desktop, you can click the Network Manager icon top right (the arrows symbol), and go into Edit Connections.

In there you can select a DNS server, depending if the machine is using dhcp or manual setup.

Ninja'd!

---

### Post by iacoposk8 on 2012-11-27
I configured everything as well (see picture)

the first image is that of the second is the smoothwall client ubuntu.
still does not work the ping google.com

---

### Post by spynappels on 2012-11-27
Did you save the setting and restart networking? Not sure if that is required... (reboot definitely will restart networking ;-))

You could try using 8.8.8.8 instead of 192.168.0.1 to see if you can use Google's DNS servers from the client.

---

### Post by iacoposk8 on 2012-11-27
I set the two ip addresses restarting the network but still does not work, how is it possible??
be patient, one day we become friends :)

---

### Post by darkod on 2012-11-27
Also, you need to change where it says Automatico DHCP into something like Automatic DHCP address only. Only in that case it uses the manually entered DNS server.

If it doesn't work with 192.168.0.1, try with 8.8.8.8 as already mentioned.

And each time after you edit the settings you need to either reboot or in terminal restart networking:
sudo /etc/init.d/networking restart

---

### Post by darkod on 2012-11-27
I forgot to mention, if that doesn't help, you have to consider the option that your firewall is blocking the dns service (reply). So after you try the setting mentioned above, if it still doesn't work you have to start thinking about the smoothwall rules/policies setup.

---

### Post by iacoposk8 on 2012-11-27
I put Automatic DHCP address only the drop down menu and restart the network ... but still nothing: (

---

### Post by darkod on 2012-11-27
In that case it seems the firewall is blocking you.

I forgot to ask, how do you have the network set up. Is the firewall server the gateway for the client?

Or you have another router in the network which is issuing dhcp leases and serves as gateway?

---

### Post by iacoposk8 on 2012-11-28
I used virtualbox to emulate the PC, so there is no router.
as the settings of the network card I put the client and the server as an internal network of green and red as NAT.
I do not remember how I set up smoothwall during installation but I seem to have set the DHCP (but I could be wrong)

---

### Post by iacoposk8 on 2012-11-28
I installed smoothwall in this same way :)

[https://www.youtube.com/watch?v=2w28gn5nDlM](https://www.youtube.com/watch?v=2w28gn5nDlM)

at 6 minutes and 6.30 the settings used for dhcp

---

### Post by darkod on 2012-11-28
If the smoothwall machine is actually a VM in Virtual Box, I would go into the settings of the VM and in Network I would use Bridge mode instead of NAT. That's better for emulating a machine as if it was in your local network.

Also, to make things more real, I would use IPs from different networks (subnets) on the RED and GREEN interfaces, not in the same network.

Tell us which are the IPs on both smoothwall interfaces? Are they static?

---

### Post by iacoposk8 on 2012-11-28
Now I try to put the bridge mode. the ip address should be static, and should be present in the image I've attached a few posts ago

---

### Post by iacoposk8 on 2012-11-28
I put the bridge mode but now smoothwall fails to ping 8.8.8.8

---

### Post by darkod on 2012-11-28
I think your problem is the networking setup. Also, when installing smoothwall you need to adjust the network settings, not always use the default ones in tutorials.

For example, if you are testing this at home, you probably have an internet router which has dhcp service on it. And it uses a specific private range, like 192.168.1.x or 192.168.0.x.

You have to make sure the smoothwall dhcp does not clash with it (they both can not have the same range).

In fact, for testing you don't even need the smoothwall dhcp enabled. Simply disable it and use static settings on the test client. And use static IP on smoothwall.

It would look something like:
internet router(192.168.1.1) ----- (192.168.1.5)smoothwall VM(10.10.10.1) ---- (10.10.10.100)test client

You just need to sit down and plan the network setup first, and start installing and configuring after that. Adjust it for your needs.

---

### Post by iacoposk8 on 2012-11-28
how do I assign the static ip in virtualbox?

---

### Post by darkod on 2012-11-28
Virtual Box is just a box where you have the VMs. You don't configure the static IP in VBox settings. You do it in the operating system of the virtual machine.

So, since you already have smoothwall installed you need to enter into its network configuration and set up the static IPs you choose for both interfaces.

On a new installation you would set the static IPs during install, but since you already have it installed you can just edit the network settings.

I don't know exactly the menu of smoothwall but it should be easy to find the network section.

---

### Post by iacoposk8 on 2012-11-29
I created a new machine configured with the ip that you have indicated (confirmed by ifconfig) the NIC is set as a "bridge" but if I type ping 8.8.8.8 tells me network is unreachable

---

### Post by darkod on 2012-11-29
Do you have the gateway and DNS information correct?

I gave you only example, it depends what subnet your router uses. Did you set the router IP as gateway for the smoothwall RED interface?

---

