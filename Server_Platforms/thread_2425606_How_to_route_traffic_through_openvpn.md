---
title: "How to route traffic through openvpn?"
date: 2019-08-27
forum: Server Platforms
---

### Post by kennethandrews on 2019-08-27
I have been searching on this for a week now and still can't figure it out. You would figure something as simple as setting up a vpn wouldn't require a masters degree but eh.

Basically all I want to do is route my traffic through a vpn. I have the vpn set up on ubuntu server, but Iftop shows no traffic going through on the tun0 interface.

Ideally I want to route only transmission through tun0 while all other traffic moves forward as normal. However at this point I'm so frustrated I would settle for just having a script run when my vpn is up that changes my default gateway to tun0 and then resets when openvpn is down.

The problem is I can't find a simple guide which explains ip-tables in laymens terms. All I can find is a bunch of copy and paste pseudo gibberish which I'm not about to start pasting into the terminal without understanding. I'm familiar with using the terminal and normally can figure things out on my own, but the iptables syntax is like latin with no good translation.

---

### Post by wildmanne39 on 2019-08-27
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by aljames2 on 2019-08-27
VPNs are not simple and are a delicate configuration between your VPN, router, firewall (ufw with iptables), and client devices.  OpenVPN is well documented and there are some decent tutorials over at Linode and DigitalOcean.  iptables blocks everything by default so it could be the rules are not allowing traffic.  

I run OpenVPN on my pfSense router box (computer I built).  Therefore my router is my OpenVPN server, and my Ubuntu Server and computers are behind that.  My setup doesn't help you other than it demonstrates there are lots of possible configurations and finding a tutorial that exactly meets your needs is unlikely.  I did a google search for “openvpn and iptables” and it turns up some good results to read up on.  

Perhaps others can give you more specific recommendations but you may need to post more specifics on your setup such as your server.conf and iptables rules.

---

### Post by kennethandrews on 2019-08-27
my .ovpn
[http://paste.ubuntu.com/p/xkMm84M9rD/](http://paste.ubuntu.com/p/xkMm84M9rD/)

output for iptables -S 
[http://paste.ubuntu.com/p/mR26g73N6w/](http://paste.ubuntu.com/p/mR26g73N6w/)

/opt/transmission/settings.json
[http://paste.ubuntu.com/p/rD7jD3kq7Q/](http://paste.ubuntu.com/p/rD7jD3kq7Q/)

I havn't made any changes to iptables as I have no understanding of the horrible tutorials out there and don't make a habit of pasting crap into the terminal that I don't understand.

I launch openvpn as root currently for testing purposes with the command "openvpn ipvanish.confg" but I will be launching it with a user created for this purpose when I figure things out.

I launch the transmission daemon with "sudo -u debian-transmission transmission-daemon --config-dir /opt/transmission"

I have no issues with either getting openvpn running and transmission works as intended with access via the web interface. I just can't get transmission to use the tun0 interface which openvpn uses.

Also, I'm unsure why this was moved to the server thread. This isn't a server specific question and would be just the same issue if I were running any version of ubuntu, or manjaro for that matter. I would argue that this is a networking question.

---

### Post by kennethandrews on 2019-09-02
I’m not sure if bumps are allowed but I haven’t gotten any replies in a few days.

---

### Post by Skaperen on 2019-09-02
i do not have a masters degree.  in fact, i have no degree at all.  i'm a college drop-out.  yet, i am accessing [ubuntuforums]("https://ubuntuforums.org/"), and most everything else, through a VPN i set up myself with OpenVPN.  it also includes IPv6 access.

i assume you have access to some remote host, perhaps a server or a friend's host, have started OpenVPN with authentication working.

there are 2 important routes to set up.  they can be set even before OpenVPN starts (your internet will mostly not work until OpenVPN is working when you do this).

0.  all your existing routes need to have a metric value higher than 1, preferably much higher like above 100.  then you pick a number that is lower than all of them, but not lower than 1, for these 2 routes.  your tunnel interface must have a netmask or a netlen for a subnet that includes the remote IP.

1.  a single host route (/32) for the remote host.  the target will be the same as your existing default route.

2.  a new default route (0.0.0.0/0) for the whole internet.  the target will be the IP address of the *remote* side of the tunnel.

your remote interface needs to be set up with NAT MASQUERADE.  that is a variant of NAT that lets the traffic to the internet mimic (masquerade as) the remote hosts IP address.  if this is not set, then the packets you send will have your own local address as the return address, and the responses will never get back to you, if they even get sent back at all, assuming your packets are not filtered out.  i will let you google for how to do this.  OpenVPN can do NAT but its not enough to get the proper packets to it.

i have some setup scripts in python.  let me know if you want to see them.

---

### Post by Skaperen on 2019-09-02
FYI, i am planning to make a script that launches a cloud instance at AWS EC2 to run an OpenVPN tunnel and (if the invoking user has sudo to root authority) connect to it and set up the local routes.  you must have an AWS account and set up an IAM role or user with authority to launch an instance and describe them, with access keys.  the setup will be fed into "user data" so ssh login is not essential but you might want to do that for other reasons.

---

### Post by TheFu on 2019-09-02
It isn't clear if the OP is running the VPN server or connecting to some paid VPN service provided by someone else.
The responses have all assumed running your own VPN server.
Connecting to a VPN that someone else provides doesn't require hardly anything.

[LIST=1]
[*]Install openvpn
[*]Get the service provider's client-side .ovpn config files
[*]Setup any specific cipher keys - my paid provider provides these files ca.rsa.4096.crt and crl.rsa.4096.pem as a separate download from the 40 or so client-config files.
[*]start the openvpn client with the specific config file.
[/LIST]
Routes should be setup automatically. No need for any firewall rules as a client, unless outbound UDP traffic is blocked.
The client config files are just text, so you can look through them and modify some settings for your preferences.  Make of the settings cannot be modified, that's why you pay the VPN service.

```
sudo openvpn /path/to/client.ovpn

```
is how I run mine.  openvpn is in the PATH, but there isn't any automatic way for the client-config file to be found without specifying the correct location.

Now, if you ARE trying to run your own VPN server and setup client stuff too, then things are crazy flexible and having a good understanding of IP networking is needed. Sorry, there's no way around that.  Openvpn is extremely capable and flexible. With that flexibility, comes complexity.

---

