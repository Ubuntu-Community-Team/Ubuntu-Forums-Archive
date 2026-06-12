---
title: "DNS Reverse Lookup Failing for SSH"
date: 2014-12-04
forum: Server Platforms
---

### Post by thufirhawat2 on 2014-12-04
So I have found a similar problem on some other forums, but it is a bit different in my case. I noticed when I was trying to SFTP from my work computer to my home server (which I have done for years with no problem) and my client would not connect. I could still get to and login to the website I am hosting on that server, and I found that I could use putty to connect via ssh, but the prompt for username and password was abnormally slow with putty. So I tried changing the timeout of my SFTP client and it eventually connects as well, though there is significant lag between the username and password being accepted much as there was with putty. I got into the machine and took a look in the auth.log, and found this:

```
Dec  4 08:25:06 servername sshd[3652]: warning: /etc/hosts.deny, line 18: can't verify hostname: getaddrinfo(tn-###-###-###-###.dyn.embarqhsd.net, AF_INET) failed
```

The ###s are my work public IP address.

So it seems to be a reverse DNS lookup failure. I know I can turn that off in SSH, but I would rather not because I have some fail2ban pattern matching rules that ban IPs based on their hostname (if they have been logged in a past hack attempt on the server). Also, it *only* seems to be doing this from my work IP; with any other IP I can connect remotely with no problems. I am the IT administrator at work, and so I know nothing with our network or public DNS/IP has changed, so I was wondering if anyone had any ideas? Thanks, and don't tell my boss!

---

### Post by SeijiSensei on 2014-12-04
Add an entry for the server to /etc/hosts on the client.

---

