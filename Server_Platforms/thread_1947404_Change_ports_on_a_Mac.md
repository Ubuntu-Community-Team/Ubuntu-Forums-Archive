---
title: "Change ports on a Mac"
date: 2012-03-26
forum: Server Platforms
---

### Post by gmenfan83 on 2012-03-26
Ok, I have recently set up a Ubuntu virtual server. I read that one of the most secure things I can do is change the port from 22 to something more secure. So I did so but now I cannot ssh into my server from my Mac desktop which tells me I should have to configure my Mac to listen for the corresponding port as my server no? If so, how do I change the port on my Mac to correspond with my server and what would a decent port number be? Is there a rule of thumb or can the port be any set of numerals desired? Thanks.

---

### Post by CharlesA on 2012-03-26
Changing the port is still security thru obscurity.

You just have to tell ssh what port to try connecting on because it defaults to port 22.

```
ssh -p [COLOR="Red"]2222[/COLOR] user@hostname
```

That one will connect on port 2222 instead of port 22. That is the only thing you need to change on the client.

Does the server have ssh access from the internet? If it does, you can set the firewall to do ratelimiting to slow down brute-force attacks on it. If the service isn't accessible from the internet you are fine to leave it as the default.

---

### Post by gmenfan83 on 2012-03-26
Ok, thanks, I can access the server from the internet but I am honestly unsure as to whether or not ssh has internet access. How would i find out? If so could you point me in the right direction as to how I would  go about setting up the firewall? I just want it to be fairly secure, thanks

---

### Post by CharlesA on 2012-03-26
Well, if you can access the server from the internet via SSH, than it's open to the internet. ;)

Just be sure to use a strong password on any account that can login via SSH and take a look at the pages here:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced)

The advanced page covers rate-limiting via iptables.

---

### Post by arrrghhh on 2012-03-26
At some point, you might want to consider disabling password authentication if you need SSH facing externally...  Just use keys.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

That way they can't brute-force into your server.  You can also do things like install denyhosts which will also help mitigate brute-force attempts.

---

### Post by gmenfan83 on 2012-03-26
Thank you very much!

---

