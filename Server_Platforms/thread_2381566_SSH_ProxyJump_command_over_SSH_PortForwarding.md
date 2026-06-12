---
title: "SSH ProxyJump command over SSH PortForwarding"
date: 2018-01-02
forum: Server Platforms
---

### Post by azrin.aris on 2018-01-02
[COLOR=#111111][FONT=Ubuntu]I have an Banana Pi behind a 3g router that does not allow port forwarding (ISP Policy)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To solve this issue, I create a reverse port forwarding using SSH -R option listening at port 2022 in my BPI and connect it to my home server called mid-server.com. From the server, now I can ssh to my RP3 using user@localhost -p 2022.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My next task is to connect to my BPI from outside via the mid-server using the ProxyJump option and here is my code
[/FONT][/COLOR]
```
ssh -J user@mid-server.com:2022 admin@mid-server.com
```
[COLOR=#111111][FONT=Ubuntu]
but I received [FONT=inherit]*ssh_exchange_identification*[/FONT] error. FYI, I can connect to my mid-server as normal ssh using[/FONT][/COLOR]

```
ssh admin@mid-server.com
```
[COLOR=#111111][FONT=Ubuntu]
both BPI and my mid-server is using ubuntu 16.04 LTS


Any help is very much appreciated[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you[/FONT][/COLOR]

---

### Post by volkswagner on 2018-01-02
Why not run openVPN server on your home server?
Have the Pi connect as a client with it's LAN routed as well.
Then when you connect to home server using OpenVPN
client on any other device, you should have route
to the pi.

I would think this would offer more persistent/reliable connectivity.

---

### Post by azrin.aris on 2018-01-04
Thank you for your guidance, I'm now studying the OpenVPN but it seem quite complex. Are there any good reference for a newbie?

Thank you

---

### Post by volkswagner on 2018-01-05
Some routers support OpenVPN, what make and model router do you have?

What operating system are you running on your server?

The [OpenVPN website]("https://openvpn.net/index.php/open-source/documentation/howto.html") is an excellent source for documentation.

I suggest 

Digital Ocean has excellent how-to articles as well, [here's one for Ubuntu 14.04]("https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04").

---

