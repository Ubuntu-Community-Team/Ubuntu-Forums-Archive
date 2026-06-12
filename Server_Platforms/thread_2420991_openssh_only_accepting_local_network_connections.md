---
title: "openssh only accepting local network connections"
date: 2019-06-14
forum: Server Platforms
---

### Post by spvance on 2019-06-14
I've freshly installed an 18.04 LTS server with openssh.  I opened ports 22, 80 and 443 in UFW.  I can only connect to SSH on the local network.  At first, I thought the problem was UFW, but I get the same result with UFW disabled.  I have a 16.04 server on the same network which I can access with no problem; and I can ssh into the 16.04 to get to the 18.04.  Any suggestions?

---

### Post by TheFu on 2019-06-14
Troubleshooting ssh Connections: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has multiple steps.  You've done some already.

```
ssh -vvv userid@ip
```
to see verbose output. Often this will show some odd error.
Also, check the logs on the server. If the connection isn't even getting to the sshd, then it is a client-side issue or firewall somewhere between.

And don't forget trying a different client.

---

### Post by SeijiSensei on 2019-06-14
/var/log/syslog and /var/log/auth.log are your friends along with bumping up the client verbosity as TheFu recommends.

---

### Post by kpatz on 2019-06-14
When you're accessing the servers from "not the local network", is this over the internet?  Via a VPN?  Or do both boxes have public IPs?

What's the error you get when you try?  Try the verbose setting as TheFu asked.

If the boxes have private IPs, some sort of NAT or port forwarding needs to happen to get to them from outside unless you're VPNed in.

It could also be a firewall not allowing access to the new box from outside, even if the IPs are public.

You said you also opened 80 and 443, is there a webserver on the box you can try accessing?  If you can't get to that either, it's probably a firewall in between needing to be configured.

---

