---
title: "SOCKS / SSH / Proxy Question"
date: 2009-06-30
forum: Server Platforms
---

### Post by wheniwork on 2009-06-30
I have a device (Axis IP Camera) that is able to use a SOCKS server.

Now I am not a guru at SSH Tunnels and proxys etc. But I need to know how to congibure SSH on the proxy/SOCKS side so it will accept the connection from my IP Cam device.

I have included the control panel from the IP Camera web config for reference. 

What do I need to do on the proxy end to get this to work?

Then once it works, how do I access the device from the proxy?

Thanks much for the help.

[IMG]http://www.thisclicks.net/assets/socks.png[/IMG]

---

### Post by jhannah on 2009-06-30
When using SSH as a SOCKS proxy, you generally initiate the SSH connection from the machine that will be making use of the proxy using the -D flag. That being said, you should be able to SSH to the machine you wish to build the proxy on using 'ssh -D :4444 hostname'. This will cause SSH to listen on port 4444 on all available interfaces. At this point, anything else that can reach the machine running SSH should be able to use it as a SOCKS proxy (specifying port 4444 in this example) with no login or password.

Is that what you are looking to accomplish or did I misunderstand your question?

---

