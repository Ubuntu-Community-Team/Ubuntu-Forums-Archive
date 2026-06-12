---
title: "Unable to connect a device to my VPS via PPTP"
date: 2024-07-15
forum: Server Platforms
---

### Post by un533n on 2024-07-15
Good day everyone.

I have a VPS running on Ubuntu 18.04 and I've managed to set up a PPTP server on it. The PPTP VPN works fine when I connect to it using my computer, there is internet access, and when I use a "what's my IP" service it shows the server's IP. However, I am unable to make my intercom panel establish a connection to my server using the same credentials. The intercom panel mentioned here is a device used as a doorbell with a camera. The idea is to connect it via a PPTP server so that I can receive notifications when someone rings the doorbell even when I'm not connected to my home Wi-Fi. Here is what my server logs show when my intercom panel is trying to connect:

```
GRE: read(fd=6,buffer=55ca789e14c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
CTRL: PTY read or GRE write failed (pty,gre)=(6,7)

```


Params that i've added to **iptables** to make PPTP work:
```

iptables -I INPUT -p tcp --dport 1723 -m state --state NEW -j ACCEPT
iptables -I INPUT -p gre -j ACCEPT
iptables -t nat -I POSTROUTING -o ens3 -j MASQUERADE
iptables -I FORWARD -p tcp --tcp-flags SYN,RST SYN -s 192.168.100.0/24 -j TCPMSS  --clamp-mss-to-pmtu


sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

```


Params that i've added to **/etc/ppp/pptpd-options**
```

8.8.8.8
8.8.4.4


mtu 1400
mru 1400

```

Enabled [COLOR=#0000ff]net.ipv4.ip_forward=1[/COLOR] in **/etc/sysctl.conf**


I am very new to Linux. Perhaps there is something else I should add on the server side to enable my Intercom panel to connect. Maybe some additional iptable parameters?

I should also probably mention a few more things in case they might cause problems:

[LIST]
[*]The Intercom panel uses 8.8.8.8 as a secondary DNS
[*]Prior to installing and configuring PPTP on my VPS, I used Amnezia VPN to set up the VPN
[/LIST]

Hope someone can help figure this out. I will try to provide any additional information if needed. Thanks in advance.

---

### Post by TheFu on 2024-07-15
Please do a web-search for "pptp shouldn't be used anymore" and read a few of the results.  pptp has been effectively cracked since 2005-ish.

If you care anything about security or privacy, PPTP isn't the protocol to use.  If you control the client AND the server, wireguard is easy and much more secure to setup.  If you don't have ESM support, 18.04 is long out of support and a safety hazard for all systems on the same network.  24.04 is the current, supported, LTS Ubuntu release.  If you fear having something "too new" like me, 22.04 Server is supported until 2027.

---

### Post by un533n on 2024-07-16
> **TheFu said:**
> Please do a web-search for "pptp shouldn't be used anymore" and read a few of the results.  pptp has been effectively cracked since 2005-ish.

If you care anything about security or privacy, PPTP isn't the protocol to use.  If you control the client AND the server, wireguard is easy and much more secure to setup.  If you don't have ESM support, 18.04 is long out of support and a safety hazard for all systems on the same network.  24.04 is the current, supported, LTS Ubuntu release.  If you fear having something "too new" like me, 22.04 Server is supported until 2027.
I'm not using PPTP for surfing, I only need PPTP to connect to my doorbell to receive notifications when I'm not at home, i.e. when I'm not connected to my home Wi-Fi. The VPS where PPTP was set up is used exclusively by me.

---

### Post by TheFu on 2024-07-17
> **un533n said:**
> The VPS where PPTP was set up is used exclusively by me.

That's your hope.  The problem with using PPTP remains, but it is your choice.

---

### Post by currentshaft on 2024-07-17
> **TheFu said:**
> Please do a web-search for "pptp shouldn't be used anymore" and read a few of the results.  pptp has been effectively cracked since 2005-ish.

He's securing a doorbell camera, i.e. a view into a public space.

Let's stop pretending like everything needs to be secured like a Mission Impossible NOC list.

That being said, OP, you don't need VPN to do this. Just use SSH port forwarding, this will let you expose a local port externally on your VPS. You could also use a reverse SSH tunnel but that's slightly more complicated and probably not required for this.

---

### Post by un533n on 2024-07-20
> **currentshaft said:**
> He's securing a doorbell camera, i.e. a view into a public space.

Let's stop pretending like everything needs to be secured like a Mission Impossible NOC list.

That being said, OP, you don't need VPN to do this. Just use SSH port forwarding, this will let you expose a local port externally on your VPS. You could also use a reverse SSH tunnel but that's slightly more complicated and probably not required for this.
First of all, thank you very much for this tip. Initially, I didn't understand much from your advice but I asked ChatGPT for help and with its guidance I managed to set up SSH forwarding &#128517;
It all worked, and I now receive notifications for doorbell rings outside of my home internet connection. However, there's an issue: I'm not receiving the video image from my doorbell camera on my Android app, even though I've opened the RTSP port on my router. Here's how my SSH command looks:

**ssh -R 5000:192.168.1.100:5000 -R 8080:192.168.1.100:80 -R 8054:192.168.1.100:554 user@myvps**

Ports used by my doorbell:
- 5000 is a data port used for video data transmission.
- 80 is the HTTP port.
- 554 is the RTSP port.


I have forwarded all of these ports in my router.


There is no issue receiving the video image when my doorbell is connected locally.


I used VLC to play my doorbell camera via the link **rtsp://192.168.1.100:554/av0_1**, and it works fine.


However, it doesn't work when I try to play the camera via VPS using **rtsp://myvps:8054/av0_1**.


What could be the problem? Do you have any ideas or tips?

---

### Post by TheFu on 2024-07-20
ssh only forwards TCP traffic. Often, RTSP is UDP.  

Dealing with ssh port forwards on Android is a bit of a hassle, which is why I suggested wireguard.  There are free wireguard setups available, if you want to trust other people. Then you wouldn't need any VPS at all.  I think **tailscale** is one. There are others.  I've never used any, but that's a personal trust issue I have with most cloudy offers. Eventually, they always want money (and they should).

---

### Post by un533n on 2024-07-21
> **TheFu said:**
> 
Dealing with ssh port forwards on Android is a bit of a hassle.The issue is not just with Android. When I try to open the stream on my local machine via VLC using this link: **rtsp://myvps:8054/av0_1**, the stream doesn't open. However, it does show a video image when I open it locally using the **rtsp://192.168.1.100:554/av0_1** link.

While trying to open the **rtsp://myvps:8054/av0_1** link via VLC on my local machine, I used the** sudo tcpdump -i any port 8054 -v** command on my VPS.

I was receiving these log messages:
```
14:39:23.708554 IP (tos 0x0, ttl 110, id 56611, offset 0, flags [DF], proto TCP (6), length 52)
    my-ip.26089 > my-vps.8054: Flags [S], cksum 0xb96a (correct), seq 2159986368, win 64240, options [mss 1440,nop,wscale 8,nop,nop,sackOK], length 0
14:39:23.708635 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40)
    my-vps.8054 > my-ip.26089: Flags [R.], cksum 0xf506 (correct), seq 0, ack 2159986369, win 0, length 0

```
[SIZE=1][COLOR=#696969]*I replaced my IP and server IP with "my-ip" and "my-vps" respectively*[/COLOR]

[/SIZE]Any ideas what they could mean?

This is what ChatGPT told me about these logs:

[LIST]
[*]*The tcpdump output indicates that when VLC is trying to connect to the RTSP stream on your VPS, the VPS is immediately sending a TCP reset (RST) packet back to the client. This typically means that there is nothing listening on the port on the VPS, or that the port is being blocked by a firewall.*
[/LIST]

But this is confusing because when I use **sudo netstat -tuln | grep 8054**, the port is listed as listening, and the firewall is not active.

> **TheFu said:**
> 
ssh only forwards TCP traffic. Often, RTSP is UDP

Actually, there's an option in my doorbell settings that allows you to choose the transfer protocol for the RTSP port (between TCP and UDP). I configured it to work only on TCP, and the forwarded ports in the router were also set to use TCP.

> **TheFu said:**
> 
which is why I suggested wireguard. There are free wireguard setups available, if you want to trust other people. Then you wouldn't need any VPS at all. I think **tailscale** is one. There are others. I've never used any, but that's a personal trust issue I have with most cloudy offers.

To be honest, I don't understand how WireGuard would help me (not being ironic or sarcastic). The reason I chose PPTP to connect with my doorbell is that there's an option for it in the doorbell settings. The VPS is solely used by me, I pay for it, and I need it for VPN purposes (using Amnezia).

Doorbell NET settings:
[IMG]https://i.imgur.com/e26MICe.jpeg[/IMG]

---

### Post by currentshaft on 2024-07-21
Your VPS provider may have a firewall in place which is controlled through the admin portal - not from the host itself. In AWS, they're known as Security Groups, for example.

Good on you for using an LLM to troubleshoot. Wish more people had the sense to do that.

---

