---
title: "ssh port forwarding doesn't work on Ubuntu 10.04 LTS"
date: 2012-06-13
forum: Security
---

### Post by fortest_123 on 2012-06-13
I have a problem of dynamic port forwarding on Ubuntu 10.04. I have a Ubuntu 10.04 desktop which connects to internet through a proxy. This machine (machine A) is installed with SSH server. From another machine which is also installed Ubuntu 10.04, I tried to use dynamic port forwarding with the command

ssh -D 9999 <user>@machineA

Then, at the SSH client, I configured firefox to use the SOCKs v5 127.0.0.1:9999 as a proxy but I couldn't access to the internet using dynamic port forwarding. I tried successfully with a CentOS server with SSH server enabled.

Most of documents and articles in the Internet say that it's simply to enable X11Forwarding, AllowTcpForwarding and PermitTunnel on SSH server. I'm not sure if this problem is related to firewall rules, Ubuntu 10.04, etc. Do anyone have an idea how to solve this problem?

Thanks

---

### Post by papibe on 2012-06-13
Hi fortest_123. Welcome to the forums.

I just want make sure what you are trying to do.

If you run this on 'another_machine':
```
ssh -D 9999 user@machineA
```
Then the tunnel 'localhost:9999' will be available on the same machine (another_machine), so you can browse as if you were on machineA.

Is that what you are trying to do?

Regards.

---

### Post by fortest_123 on 2012-06-14
Thank papibe for your reply. That's right, let's say another machine is machine B. From machine B, I run this command but I can't browse the internet as I am in machine A :(. Do you have any ideas?

---

### Post by markbl on 2012-06-14
So on machine A you can browse the web fine?

Try the normal ssh debugging techniques. Look for sshd error messages in /var/log. Also add -vvv to your ssh client command and see what it says.

---

### Post by fortest_123 on 2012-06-14
Yes markbl, but machine A browses internet through a HTTP proxy at port 3128. The wireshark on machine A says that any websites I put in Firefox bar on machine B goes directly to the internet, I think this is why I couldn't access internet from machine B using dynamic port forwarding. 

Do you know how to configure on ssh server to say that the tunnelled packets from machine B must go through a proxy like in machine A?

---

### Post by markbl on 2012-06-14
> **fortest_123 said:**
> 
Do you know how to configure on ssh server to say that the tunnelled packets from machine B must go through a proxy like in machine A?
I had a quick search on google and could not find anything remotely talking about this.

This idea may be off the wall but could you perhaps just add a local port forward to the remote proxy server? I.e. try:
```

ssh -L9999:remote_proxy:3128 user@machineA

```

Then just configure your browser on machineB to use a socks proxy on localhost port 9999 (i.e. just as you were). Should just forward all the requests to the real proxy. Please let me know if this works?

---

### Post by fortest_123 on 2012-06-14
I tried with option -L and it doesn't. Actually, the -L option is not my case acccording to this page :( [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding).

When I look at the wireshark traces on machine A, if I browse the web (ex. google.com) on machine A, I see the HTTP traffic to the proxy with destination port 3128. On the other hand, if I browse the web from machine B through SSH, I see the TCP traffic to IP address of google at port 80. I think this is why it doesn't work. 

I think it works with the CentOS server in my first post since this server has 2 interfaces and one of them has a public IP.

Anyone have an idea how to fix this?

Thanks,

---

### Post by markbl on 2012-06-14
Er, I don't need a reference to the man page. I know what the -L option does.

Did you try what I said - but of course you replaced what I typed as "remote_proxy" with the IP name/address of your actual http proxy that machine A connects to, didn't you?

In that last post above you restated your same comments about wireshark, but that is when you used the sshd dynamic proxy (-D) as per your earlier posts. You won't see that if you tried the -L, unless you did something wrong.

In short, when you use -D9999 the local ssh client creates a http proxy on localhost:9999. In your case the http proxy is actually at remote_proxy:3128 so simply forwarding your localhost port 9999 to that machine + port should work (where again, "remote_proxy" must be set to whatever your real proxy machine is - you don't say it above). This is what -L does.

---

